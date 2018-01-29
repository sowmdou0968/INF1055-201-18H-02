Download Ubuntu 16.04 Image

```
$ cd /run/shm  
$ wget http://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-disk1.img
```

Creer l'image dans Glance

```
$ openstack image create \
         --disk-format qcow2 \
         --container-format bare \
         --public \
         --file xenial-server-cloudimg-amd64-disk1.img \
         "Ubuntu-16.04 LTS"
+------------------+------------------------------------------------------+
| Field            | Value                                                |
+------------------+------------------------------------------------------+
| checksum         | 08c3de1e35df735d7cbb699e5711ef1f                     |
| container_format | bare                                                 |
| created_at       | 2018-01-24T21:33:57Z                                 |
| disk_format      | qcow2                                                |
| file             | /v2/images/d9796c28-6841-413e-92b2-ab6b835ce7b9/file |
| id               | d9796c28-6841-413e-92b2-ab6b835ce7b9                 |
| min_disk         | 0                                                    |
| min_ram          | 0                                                    |
| name             | Ubuntu-16.04 LTS                                     |
| owner            | 11dbd32de6a4421b8f973e8b59699aea                     |
| protected        | False                                                |
| schema           | /v2/schemas/image                                    |
| size             | 288686080                                            |
| status           | active                                               |
| tags             |                                                      |
| updated_at       | 2018-01-24T21:33:58Z                                 |
| virtual_size     | None                                                 |
| visibility       | public                                               |
+------------------+------------------------------------------------------+
```

Lancer l'image

```
$ docker-machine --debug create --driver openstack \
     --openstack-flavor-name m1.small \
     --openstack-image-name "Ubuntu-16.04 LTS" \
     --openstack-ssh-user "ubuntu" \
     --openstack-floatingip-pool public \
     --openstack-sec-groups default  \
     --openstack-nova-network \
     --openstack-net-name nova \
     --openstack-domain-name Default \
     --openstack-tenant-id <changer le tenant ID> \
     INF1055
```

```
$ nova boot --flavor m1.tiny --image "Ubuntu-16.04 LTS" --nic net-id=<NET_ID> --key-name <KEY_PAIR> instancetest1
$ ssh -i <KEY_PAIR> ubuntu@<INSTANCE_FLOATING_IP>
```

```
$  openstack image delete "Ubuntu-16.04 LTS"
```
