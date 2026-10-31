i2pd-openwrt
===

That repository contains package source for OpenWRT SDK build system.

OUTDATED !!! `release` folder contain sources for building package against tagged version of i2pd using release tarball and it's hash.

`trunk` folder contain sources with usage of git and commit hash used for building. To adjust build to latest commit update `PKG_SOURCE_DATE` and `PKG_SOURCE_VERSION` variables to your need. For example, values
```
PKG_SOURCE_DATE:=2026-10-30
PKG_SOURCE_VERSION:=6b214f74d2c1b9d892cda29119f0942097cbfd85
PKG_RELEASE:=1
```
will use commit [6b214f7](https://github.com/PurpleI2P/i2pd/commit/6b214f74d2c1b9d892cda29119f0942097cbfd85) and mark package version using date `2026-10-30`, so resulting package name since OpenWrt 25.12 will like `i2pd-2026.10.30~6b214f74-r1.apk`.
