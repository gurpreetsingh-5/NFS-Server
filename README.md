# NFS-Server
## using RHEL 9 OS

```
sudo dnf install nfs-utils -y
sudo systemctl enable --now nfs-server
sudo systemctl status nfs-server
sudo mkdir -p /mnt/nfs_share
sudo chmod 777 /mnt/nfs_share

sudo vi /etc/exports
/mnt/nfs_share  client_ip(rw,sync,no_subtree_check,no_root_squash)

eplace client_ip with:
A specific IP (e.g., 192.168.1.100)
A subnet (e.g., 192.168.1.0/24)

sudo exportfs -arv
sudo exportfs -v

sudo dnf install firewalld -y
sudo firewall-cmd --permanent --add-service=nfs
sudo firewall-cmd --permanent --add-service=mountd
sudo firewall-cmd --permanent --add-service=rpc-bind
sudo firewall-cmd --reload
sudo firewall-cmd --list-services | grep nfs
for Client---

sudo dnf install nfs-utils -y
showmount -e 3.83.150.54
sudo mkdir -p /mnt/nfs_client
sudo mkdir -p /mnt/nfs_client
sudo mount -t nfs server_ip:/mnt/nfs_share /mnt/nfs_client
df -h | grep nfs
```
