## Cluster Upgrade

### Master Node

1. **Master Node'u Boşaltın:**
```sh
kubectl drain k8s-master --ignore-daemonsets
```
2. **Kubernetes Paket Deposu Dosyasını Güncelleyin:**

```sh
   sudo vim /etc/apt/sources.list.d/kubernetes.list
```
Bu dosyayı açtığınızda, aşağıdaki satırı ekleyin veya mevcutsa güncelleyin:

```plaintext
deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /
```

3. **Paket Bilgilerini Güncelleyin:**
```sh
   sudo apt update
```
4. **Kubeadm Yükseltme:**
```sh
   sudo apt-cache madison kubeadm
```
```sh
   sudo apt-get install kubeadm=1.29.0-1.1
```
5. **Kubeadm ile Master Node'u Yükseltme:**
```sh
  sudo kubeadm upgrade plan v1.29.0
```
```sh
   sudo kubeadm upgrade apply v1.29.0
```
6. **Kubelet Yükseltme ve Yeniden Başlatma:**
```sh
  sudo apt-get install kubelet=1.29.0-1.1
```
```sh
   sudo systemctl daemon-reload
```
```sh
   sudo systemctl restart kubelet
```
7. **Master Node'u Tekrar Kullanıma Açma:**
```sh
   kubectl uncordon k8s-master
```

### Worker Node

1. **Worker Node'u Boşaltın:**
```sh
kubectl drain k8s-worker --ignore-daemonsets
```
2. **Kubernetes Paket Deposu Dosyasını Güncelleyin:**

```sh
   sudo vim /etc/apt/sources.list.d/kubernetes.list
```
Bu dosyayı açtığınızda, aşağıdaki satırı ekleyin veya mevcutsa güncelleyin:

```plaintext
deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /
```

3. **Paket Bilgilerini Güncelleyin:**
```sh
   sudo apt update
```
4. **Kubeadm ve Kubelet Yükseltme:**
```sh
   sudo apt-cache madison kubeadm
```
```sh
  sudo apt-get install kubeadm=1.29.0-1.1
```
```sh
  sudo kubeadm upgrade node
```
```sh
  sudo apt-get install kubelet=1.29.0-1.1
```
```sh
  sudo systemctl daemon-reload
```
```sh
  sudo systemctl restart kubelet
```
5. **Worker Node'u Tekrar Kullanıma Açma:**
```sh
   kubectl uncordon k8s-worker
```





