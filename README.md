# OVH-FailoverIP (Debian/Ubuntu)

Use this network configuration, to set up a failover IP on Debian/Ubuntu.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address <FAILOVER IP>
        netmask 255.255.255.255
        broadcast <FAILOVER IP>
        post-up route add <HOST IP> dev eth0
        post-up route add default gw <HOST IP>
        pre-down route del <HOST IP> dev eth0
        pre-down route del default gw <HOST IP>
        dns-nameservers 1.1.1.1
```
