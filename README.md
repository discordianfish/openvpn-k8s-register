# openvpn-k8s-register
This is a openvpn ["learn-address"
script](https://openvpn.net/index.php/open-source/documentation/manuals/65-openvpn-20x-manpage.html)
to register ports on vpn clients as [Kubernetes
endpoints](https://kubernetes.io/docs/concepts/services-networking/service/).

## Example
Point your openvpn server to `openvpn-k8s-register` by specifying
`learn-address`:

```
port 1194
proto tcp
dev tun

learn-address openvpn-k8s-register -p 9100 -p 8080 -a prometheus.io/scrape=true
...
```

This will creates an endpoints object with ports 9100 and 8080 and the
annotation `"prometheus.io/scrape": "true"`. Each VPN client connected will be
added to the endpoints object.
