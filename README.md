# TetrapodsRegistry

Julia package registry, public and private, for UCD4IDS

## Using the registry

First, to install the registry, run

```
using Pkg
pkg"registry add https://github.com/UCD4IDS/TetrapodsRegistry.git"
```

To add a new package `MyFavPkg` to the registry, first make sure you have installed `LocalRegistry`, and then run

```
using LocalRegistry, MyFavPkg
register(MyFavPkg, registry="~/.julia/registries/Tetrapods/", repo="<url of MyFavPkg>")
```

if it is private, see [this tutorial](https://github.com/GunnarFarneback/LocalRegistry.jl/blob/master/docs/ssh_keys.md). Primarily, the repo must be the ssh version.

To just upload a new version of `MyFavPkg` to the registry, first

- push all of the new work you want to be included in that version up to the repo url for `MyFavPkg`
- make sure you've included a version bump, so that the new version is greater than the existing one

And run

```
using LocalRegistry, MyFavPkg
register(MyFavPkg)
```
