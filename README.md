OpenWrt Third-Party Packages
============================

## Add to OpenWrt package folder

```
git clone --recursive https://github.com/redchenjs/openwrt-packages.git package/3rd
```

## Update an existing repository

```
cd package/3rd
git pull && git submodule update --init --recursive
```
