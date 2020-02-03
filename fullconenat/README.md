RFC3489-compatible full cone SNAT
=================================

## Firewall

```
iptables -t nat -D zone_wan_postrouting -m comment --comment "!fw3" -j MASQUERADE
iptables -t nat -A zone_wan_prerouting -j FULLCONENAT
iptables -t nat -A zone_wan_postrouting -j FULLCONENAT
```
