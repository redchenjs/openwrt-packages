KMS Emulator in C
=================

## Usage

```
vlmcsd -i /etc/vlmcsd.ini -j /etc/vlmcsd.kmd -L 0.0.0.0:1688
```

## Firewall

```
iptables -A input_rule -p tcp --dport 1688 -j ACCEPT
```
