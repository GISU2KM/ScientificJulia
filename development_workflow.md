# Development Workflow

## Keeping local packages outside of julia directory

Keeping personal packages outside of `Pkg.dir()` is convinient for many reasons. For instance, you may want to manage your git workflow and allow `Pkg.update()` ignore such packages. To do so, you can add to the path to your .juliarc file 

```julia
const LOCAL_PACKAGES = expanduser("~/src/julia-local-packages/")
push!(LOAD_PATH, LOCAL_PACKAGES)
```

When generating local packages, you can now specify your local path

```
import PkgDev
PkgDev.generate("MyPkg", "MIT"; path = joinpath(LOCAL_PACKAGES, "MyPkg"))
```

Finally, testing packages outside the julia directory (before Pkg3) can be done using [RoguePkg.jl](https://github.com/tpapp/RoguePkg.jl)

```julia
Pkg.test(pkg_for"MyPkg")
```

## Autoreloading code

[Revise.jl](https://github.com/timholy/Revise.jl) tracks changes to loaded modules and autoreloads when necessary.  It handles most changes, except for type redefinitions. It is very useful during development phase and it works botth in the REPL and Jupyter Notebooks.
