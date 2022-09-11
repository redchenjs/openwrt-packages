OpenWrt Third-Party Packages
============================

## Add to OpenWrt package folder

```
git clone --recursive https://github.com/redchenjs/openwrt-packages.git package/openwrt-packages
```

## Update an existing repository

```
cd package/openwrt-packages
git pull && git submodule update --init --recursive
```
