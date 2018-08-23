# Change the default Lan Network

## USG eth and port mapping

### USG

```text
eth0 = WAN1
eth1 = LAN1 
eth2 = WAN2/LAN2
```

### USG-PRO-4

```text
eth0 = LAN1
eth1 = LAN2 
eth2 = WAN1 
eth3 = WAN2 
```

{% hint style="info" %}
 Replace ethX

USG: eth1 

USG-PRO-4: eth0
{% endhint %}

Change the LAN default IP & DHCP Servers range

```
configure

edit interfaces ethernet ethX
set address 10.3.2.1/24
delete interfaces ethernet ethX address 192.168.1.1/24
commit
save


delete service dhcp-server shared-network-name LAN_192.168.1.0-24
set service dhcp-server shared-network-name LAN_10.3.2.0-24 subnet 10.3.2.0/24 start 10.3.2.100 stop 10.3.2.199
set service dhcp-server shared-network-name LAN_10.3.2.0-24 subnet 10.3.2.0/24 default-router 10.3.2.1
set service dhcp-server shared-network-name LAN_10.3.2.0-24 subnet 10.3.2.0/24 dns-server 10.3.2.1
commit
save
```



