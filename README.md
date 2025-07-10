# ZSF GitHub Actions Runner Fork

This is a fork of [actions/runner](https://github.com/actions/runner) with
patches to make it run on more architectures. It is meant to be used with a .NET
SDK from [ziglang/dotnet-builds](https://github.com/ziglang/dotnet-builds). This
repository is periodically rebased on upstream and force-pushed.

## Usage

```bash
git clone https://github.com/ziglang/runner.git
git checkout $arch
cd src
./dev.sh layout Release linux-$arch
./dev.sh package Release linux-$arch
```

Where `$arch` is one of:

* `arm`
* `arm64`
* `loongarch64`
* `ppc64le`
* `riscv64`
* `s390x`
* `x64`

This will download all dependencies (including the ZSF .NET SDK package), build
the runner, and create a package at:

```
runner/_package/actions-runner-linux-$arch-$version.tar.gz
```

The `package` step can be omitted if the runner is going to be used directly
from the `runner/_layout` directory.
