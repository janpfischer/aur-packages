# Arch User Repository (AUR) Packages

This repository contains a collection of packages which are kept up to date with [Renovate Bot][1].
Once an upstream release got's an update an automatic Push Request is generated and once this is accepted a pipeline is triggered to create the makepkg file and publish the package to the [AUR][2].

This repository is based on the very helpful blog post by [Jamie Magee][3] about exactly this approach and his [template][4].

## How it works

1. Renovate Bot will check the upstream repository which is given as an annotation in the `PKGBUILD` file.
1. Once the upstream repository publishes a new package (for now only based on semver) a Pull Request is created to update the `pkgver`.
1. A GitHub Action (which is triggered on the creation of a PR) will update the checksums of the packages and changes the values in the `.SRCINFO` file.
1. Once the PR is accepted a GitHub Action will publish the package to the [(AUR)](2).

## License

All code in this repository is licensed under [the MIT license][6].
See the `license` property in each `PKGBUILD` for the license under which each package is distributed.

[1]: https://github.com/apps/renovate
[2]: https://wiki.archlinux.org/title/Arch_User_Repository
[3]: https://github.com/jamieMagee/aur-packages
[4]: https://jamiemagee.co.uk/blog/maintaining-aur-packages-with-renovate
[5]: https://opensource.org/license/mit/