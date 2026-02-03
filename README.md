# omniedge-openwrt

> Latest version: 2.2.3

OpenWrt package for [omniedge](https://github.com/omniedgeio/omniedge)

## Usage

1. Download ipk releasted to your arch, and copy it to your router
2. Install it by running `opkg install omniedge*.ipk`
3. Generate Security-key, and get the Virtual Network ID from [Dashboard](https://connect.omniedge.io/dashboard)
4. Add your Security key and virtual network id to `/etc/init.d/omniedge`:

```bash
security_key=OMNIEDGE_SECURITY_KEY
virtual_network_id=OMNIEDGE_VIRUTALNETWORK_ID
```
5. running Omniedge by: 

```bash
/etc/init.d/omniedge enable
/etc/init.d/omniedge start
```