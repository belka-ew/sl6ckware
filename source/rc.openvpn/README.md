Copy `templates/openvpn-vpnname` and `templates/openvpn-vpnname-log` to
this directory and replace all instances of `vpnname` (including the
services name) with the name of your VPN (or anything really). We will
use `myvpn` here as an example.

```sh
cp -r templates/openvpn-vpnname source/rc.openvpn/openvpn-myvpn
cp -r templates/openvpn-vpnname-log source/rc.openvpn/openvpn-myvpn-log
sed -i 's/vpnname/myvpn/g' \
    $(grep -rl vpnname source/rc.openvpn/openvpn-myvpn* | tr '\n' ' ')
```

Next, edit `openvpn-myvpn/env/CONF_PATH` and make sure it points to the
location of your VPN's OpenVPN config file.

Lastly, add that `openvpn-myvpn` service to
`source/bundles/openvpn/contents` if you want to start it at boot time.

```sh
echo openvpn-myvpn >> source/bundles/openvpn/contents
```
