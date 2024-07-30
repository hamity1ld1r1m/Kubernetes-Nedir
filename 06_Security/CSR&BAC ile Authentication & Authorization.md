## Özel Anahtar Oluşturma

```sh
openssl genrsa -out hamit.key 2048
```
## Sertifika İsteği Oluşturma
```sh
openssl req -new -key hamit.key -out hamit.csr
```
## CSR Dosyası Oluşturma
```yaml
apiVersion: certificates.k8s.io/v1
kind: CertificateSigningRequest
metadata:
  name: hamit
spec:
  request: <base64-encoded-csr>
  signerName: kubernetes.io/kube-apiserver-client
  expirationSeconds: 86400
  usages:
  - client auth
```
## CSR'yi Onaylama
```sh
kubectl certificate approve hamit
```
## Sertifikayı Alma ve Kaydetme
```sh
kubectl get csr hamit -o jsonpath='{.status.certificate}' | base64 -d > hamit.crt
```
## Rol Oluşturma
```sh
kubectl create role developer --verb=create --verb=get --verb=list --verb=update --verb=delete --resource=pods
```
## Rol Bağlantısı Oluşturma
```sh
kubectl create rolebinding developer-binding-hamit --role=developer --user=hamit --namespace=default
```
## Kubeconfig Dosyasını Ayarlama
```sh
kubectl config set-credentials hamit --client-key=hamit.key --client-certificate=hamit.crt --embed-certs=true
```
```sh
kubectl config set-context hamit --cluster=kubernetes --user=hamit
```
## Kubeconfig İçeriğini Görüntüleme ve Kullanma
```sh
kubectl config get-contexts
```
```sh
kubectl config use-context hamit
```
## Kubernetes Kaynaklarını Görüntüleme
```sh
kubectl get pods
```
## Yetkilendirme Kontrolü Yapma
```sh
kubectl auth can-i get nodes -A
```
```sh
kubectl auth can-i --list
```
## Kullanıcı Hesabı Oluşturma
```sh
sudo adduser hamit --disabled-password
```
```sh
sudo su - hamit
```
## Kubeconfig Dosyasını Oluşturma
```sh
touch $HOME/.kube/config
```
