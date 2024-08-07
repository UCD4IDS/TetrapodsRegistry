# TetrapodsRegistry

Julia package registry, public and private, for UCD4IDS

## Using the registry

### Install the registry

If this is your first time using the registry, you need to add it to Julia:

```
using Pkg
pkg"registry add git@github.com:UCD4IDS/TetrapodsRegistry.git"
```

### Add a package for the first time

To add a new package `MyFavPkg` to the registry,

- first make sure you have installed `LocalRegistry`: `pkg"add LocalRegistry"`
- next you'll need `MyFavPkg` as a git repo using `dev`: `pkg"dev git@github.com:path/to/MyFavPkg.git"`
- make sure your registries are up to date: `pkg"registry up"`

Then we can run:
 
```
using LocalRegistry, MyFavPkg
register(MyFavPkg, registry="~/.julia/registries/Tetrapods/", repo="git@github.com:path/to/MyFavPkg.git")
```

if it is private, see [this tutorial](https://github.com/GunnarFarneback/LocalRegistry.jl/blob/master/docs/ssh_keys.md). Primarily, the repo must be the ssh version.

### Update an existing package

To just upload a new version of `MyFavPkg` to the registry,

- push all of the new work you want to be included in that version up to the repo url for `MyFavPkg`
- make sure you've included a version bump, so that the new version is greater than the existing one
- make sure you have the git repo for `MyFavPkg`, e.g.: `pkg"dev git@github.com:path/to/MyFavPkg.git"` 
- make sure your registries are up to date: `pkg"registry up"`

Then we can run:

```
using LocalRegistry, MyFavPkg
register(MyFavPkg)
```

If you want to follow the registry's version of `MyFavPkg` from now on instead of your local git repo version, you may now `free` it: `pkg"free MyFavPkg"`
