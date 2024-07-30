## Metrics Server Kurulum

1. **Metrics Server'ı Yükleme:**
   ```sh
   kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```
2. **Deployment'ı Düzenleme:**
   ```sh
   kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```
Aşağıdaki satırları `spec: containers:` bölümüne ekleyin veya mevcutsa güncelleyin:

```yaml
spec:
  containers:
  - args:
    - --cert-dir=/tmp
    - --secure-port=4443
    - --kubelet-preferred-address-types=InternalIP,ExternalIP,Hostname
    - --kubelet-use-node-status-port
    - --metric-resolution=15s
    - --kubelet-insecure-tls=true       # Eklenmelidir.
    image: registry.k8s.io/metrics-server/metrics-server:v0.6.3
```
3. **Node'lar ve Pod'lar için Metric'leri Görüntüleme:**
```sh
kubectl top nodes
```
```sh
kubectl top pods
```
