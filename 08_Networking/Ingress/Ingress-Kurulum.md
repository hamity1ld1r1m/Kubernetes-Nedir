# NGINX Ingress Controller’ı Helm ile Kurma Adımları
**Helm** uygulamasının Ubuntu 22.04 ortamında kurulumu adımlarına buradan ulaşabilirsiniz.

## 1. Helm Kurulumu 

```shell
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
```
```shell
sudo apt-get install apt-transport-https --yes
```

```shell
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
```
```shell
sudo apt-get update
```
```shell
sudo apt-get install helm
```


## **2:** MetalLB Kurulumu
### kube-proxy yapılandırmasını düzenleyin
```shell
kubectl edit configmap -n kube-system kube-proxy
```
### aşağıdaki gibi değiştirilmelidir.

```shell
mode: "ipvs"
ipvs:
  strictARP: true
```
### Değişiklikleri kontrol edin

```shell
kubectl get configmap kube-proxy -n kube-system -o yaml | \
sed -e "s/strictARP: false/strictARP: true/" | \
kubectl diff -f - -n kube-system
```

### Değişiklikleri uygulayın
```shell
kubectl get configmap kube-proxy -n kube-system -o yaml | \
sed -e "s/strictARP: false/strictARP: true/" | \
kubectl apply -f - -n kube-system
```
## MetalLB yükleyin

```shell
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.13.9/config/manifests/metallb-native.yaml
```
### IP hesaplama aracı yükleyin

```shell
sudo apt install sipcalc
```
```shell
ip a
```

### Kullanılabilir IP aralığını bulun
```shell
sipcalc 192.168.18.11/24
```
### MetalLB yapılandırmasını oluşturun
```shell
 metallb-config.yaml
 ```
```yaml
apiVersion: metallb.io/v1beta1
kind: IPAddressPool
metadata:
  name: first-pool
  namespace: metallb-system
spec:
  addresses:
  - 192.168.18.1-192.168.18.254
---
apiVersion: metallb.io/v1beta1
kind: L2Advertisement
metadata:
  name: default
  namespace: metallb-system
spec:
  ipAddressPools:
  - default
```
### Yapılandırmayı uygulayın
```shell
kubectl apply -f metallb-config.yaml
```


## **3:** Ingress-NGINX Kurulumu

```shell
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
```
```shell
helm repo update
```
```shell
helm install ingress-controller ingress-nginx/ingress-nginx
```
```shell
helm ls
```
```shell
kubectl get deployments
```

```shell
# HTTP ve HTTPS portlarını görmek için
kubectl --namespace default get services -o wide -w ingress-controller-ingress-nginx-controller
```

### Portları test etmek için, HTTP 404 hatası döndürmesi gerekiyor.

```shell
curl http://192.168.199.51:31035
```
```shell
curl --insecure https://192.168.199.51:32381
```

*Örnek dağıtım ve servis yapılandırması*

```shell
vi sample-deployment.yaml
```

```shell
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    run: nginx
  name: nginx-deploy
spec:
  replicas: 1
  selector:
    matchLabels:
      run: nginx
  template:
    metadata:
      labels:
        run: nginx
    spec:
      containers:
      - image: nginx
        name: nginx
---
apiVersion: v1
kind: Service
metadata:
  labels:
    run: nginx
  name: nginx-deploy
spec:
  ports:
  - port: 80
    protocol: TCP
    targetPort: 80
  selector:
    run: nginx
  type: ClusterIP
```
### Yapılandırmayı uygulayın
```shell
kubectl apply -f sample-deployment.yaml
```
### Servisi dışa açın
```shell
kubectl expose deploy nginx-deploy --port 80
```
## Ingress yapılandırması
```shell
vi ingress.yaml
```
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: nginx-deploy
  namespace: default
spec:
  ingressClassName: nginx
  rules:
    - host: hamityldrm.com
      http:
        paths:
        - backend:
            service:
              name: nginx-deploy
              port:
                number: 80
          path: /
          pathType: ImplementationSpecific
```
### Ingress yapılandırmasını uygulayın

```shell
kubectl apply -f ingress.yaml
```
### /etc/hosts dosyasını düzenleyin

```shell
sudo nano /etc/hosts
```
### Aşağıdaki satırı ekleyin
```shell
192.168.18.1  hamityldrm.com
```

### Tarayıcınızdan http://hamityldrm.com adresine gidin ya da aşağıdaki komutu çalıştırın

```shell
curl http://hamityldrm.com
```
