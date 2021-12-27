i2pd-openwrt
===

That repository contains package source for OpenWRT SDK build system.

`release` folder contain sources for building package against tagged version of i2pd using release tarball and it's hash.

`trunk` folder contain sources with usage of git and commit hash used for building. To adjust build to latest commit update `PKG_SOURCE_DATE` and `PKG_SOURCE_VERSION` variables to your need. For example, values
```
PKG_SOURCE_DATE:=2021-12-25
PKG_SOURCE_VERSION:=1c95c7856f9a637f998882acaba679210bb9cb35
```
will use commit [1c95c78](https://github.com/PurpleI2P/i2pd/commit/1c95c7856f9a637f998882acaba679210bb9cb35) and mark package version using date `2021-12-25`, so resulting package name will like `i2pd_2021-12-25-1c95c785-1_<arch>.ipk`.
