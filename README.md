[dreampkgs](https://github.com/nix-community/dreampkgs)
is a collection of software packages managed with
[dream2nix](https://github.com/nix-community/dream2nix), a framework for automated packaging.

Both dream2nix and dreampkgs are unstable at this point.

The goal of this repo is to test and improve dream2nix.

See hydra jobs here: https://hydra.ngi0.nixos.org/jobset/dreampkgs/main#tabs-jobs

To interact with the CLI, use nix 2.4+ with enabled experimental features nix-command + flakes.

# Packaging workflow

### clone repo
```shell
git clone https://github.com/nix-community/dreampkgs
cd dreampkgs
```

### list existing packages
```shell
nix flake show
```

### build a package
```shell
nix build .#{package-name}
```

### modify the build recipe of a package or dependency
Open `./overrides/{subsystem}/default.nix` and add or modify entries.
See the documentation for the [Override System](https://github.com/nix-community/dream2nix/blob/main/docs/override-system.md)


# Developing/Debugging dream2nix
## Use dreampkgs with a local checkout of dream2nix
Temporarily override the dream2nix input of dreampkgs via:
```shell
nix flake lock --override-input dream2nix path:///$HOME/path/to/dream2nix
```
This command needs to be re-executed after each change on dream2nix.
