Ubuntu 16.04 Image

```
$ cd /run/shm  
$ wget http://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-disk1.img
$ openstack image create \
         --disk-format qcow2 \
         --container-format bare \
         --public \
         --file xenial-server-cloudimg-amd64-disk1.img \
         "Ubuntu-16.04 LTS"
$ nova boot --flavor m1.tiny --image "Ubuntu-16.04 LTS" --nic net-id=<NET_ID> --key-name <KEY_PAIR> instancetest1
$ ssh -i <KEY_PAIR> ubuntu@<INSTANCE_FLOATING_IP>
```

```
$  openstack image delete "Ubuntu-16.04"
```
