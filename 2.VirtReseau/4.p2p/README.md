# P2P (Peer to Peer - VM access)

Taken from chapter 6 - OpenStack In Action (i.e. p2p1 Client Network)

* Edit the `/etc/network/interfaces` file and add the `enp9s0` interface

```
# The VM network interface
auto enp9s0
iface enp9s0 inet manual
```

* refresh the network settings

```
$ sudo ifdown enp9s0 && sudo ifup enp9s0
```

* Connect the OVS external bridge and Neutron virtual interfaces to the physical network

```
$ sudo ovs-vsctl add-port br-ex enp9s0
$ sudo ovs-vsctl br-set-external-id br-ex bridge-id br-ex 
```

* check the result

```
$ sudo ovs-vsctl show
```

