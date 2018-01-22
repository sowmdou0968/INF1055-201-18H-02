# KVM 

## Modify kernel settings

* edit sysctl.conf file

```
$ sudo vi /etc/sysctl.conf
net.ipv4.ip_forward=1
net.ipv4.conf.all.rp_filter=0
net.ipv4.conf.default.rp_filter=0
```

* enable kernel changes without rebooting

```
$ sudo sysctl -p
```

## Kernel-Based Virtual Machine

https://www.linux-kvm.org/page/Main_Page
