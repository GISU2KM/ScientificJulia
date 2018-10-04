# Development Workflow

## Keeping local packages outside of julia directory

In Julia 1.0 when developing packages you want to be using `Pkg.dev` instead of `Pkg.add`. This will tell the package manager to treat the package differently in to main ways:

* The package manager will never touch these files. Git operations are the user responsability
* The project will be stateful. That is , its state depends on the current content of the files at the path

[Link](https://docs.julialang.org/en/v1/stdlib/Pkg/index.html#Developing-packages-1) to the relevant section of the documentation discussing how to use the package manager for your own projects.

Example of adding a package to use for development:

```
(v1.0) pkg> dev BioServices
```

By default these packages/projects are cloned to ~/.julia/dev/. To chnage such path simply change the related envaronment variable in julia's startup script. i.e,

```
echo 'ENV["JULIA_PKG_DEVDIR"] = "~/julia_dev"' > ~/.julia/config/startup.jl
```

When generating local packages, you can now specify your local path

????

Finally, testing dev packages 

???

## Autoreloading code
