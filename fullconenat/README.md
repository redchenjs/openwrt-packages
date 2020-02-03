RFC3489-compatible full cone SNAT
=================================

## Firewall

```
iptables -t nat -A zone_wan_prerouting -j FULLCONENAT
iptables -t nat -A zone_wan_postrouting -j FULLCONENAT
```
