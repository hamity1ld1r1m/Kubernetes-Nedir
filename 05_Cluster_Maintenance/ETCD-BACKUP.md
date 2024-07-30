## ETCDCTL API Ortam Değişkenini Ayarlama

```sh
export ETCDCTL_API=3
```
## ETCD Yedeğini Alma

```sh
etcdctl snapshot save /opt/etcd-backup.db \
  --endpoints=https://127.0.0.1:2379 \
  --cacert=/etc/kubernetes/pki/etcd/ca.crt \
  --cert=/etc/kubernetes/pki/etcd/server.crt \
  --key=/etc/kubernetes/pki/etcd/server.key
```
## Yedeklemenin Durumunu Kontrol Etme

```sh
etcdctl snapshot status /opt/etcd-backup.db
```