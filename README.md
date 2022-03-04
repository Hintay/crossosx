# CrossOSX

macOS Pre-compiled Cross Toolchain for Linux

## About The Project

### Build With

- [tpoechtrager/osxcross](https://github.com/tpoechtrager/osxcross)
- [phracker/MacOSX-SDKs](https://github.com/phracker/MacOSX-SDKs)
- [Github Action](https://github.com/features/actions)

CrossOSX is a pre-compiled [osxcross](https://github.com/tpoechtrager/osxcross) toolchain using Github Action with SDK taken from [phracker/MacOSX-SDKs](https://github.com/phracker/MacOSX-SDKs). Built on the latest Ubuntu, provided in `gzip` and `zstd` (recommend).

## Installation

### Prerequisites

- clang
- glibc (libc6) 2.31+

### Manual Installation

Download the latest version and extract it.

```bash
curl -L https://github.com/Hintay/crossosx/releases/latest/download/crossosx.tar.zst -o crossosx.tar.zst
tar xvaf crossosx.tar.zst
```

Add `lib/` folder of CrossOSX to `LD_LIBRARY_PATH`, and add `bin/` folder of CrossOSX to `PATH`

```bash
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$(pwd)/crossosx/lib/
export PATH=$(pwd)/crossosx/bin/:$PATH
```

### Github Actions Example

```yaml
- name: Install darwin cross compiler
  run: |
    curl -L https://github.com/Hintay/crossosx/releases/latest/download/crossosx.tar.zst -o crossosx.tar.zst
    tar xvaf crossosx.tar.zst
    echo "LD_LIBRARY_PATH=$(pwd)/crossosx/lib/" >> $GITHUB_ENV
    echo "PATH=$(pwd)/crossosx/bin/:$PATH" >> $GITHUB_ENV
```

## Usage

You can use `o64-clang` / `o64-clang++` to target for `X86_64` devices, and use `oa64-clang` / `oa64-clang++` to target for `arm64` (Apple silicon, M1+) devices. For more information, please see [osxcross usage examples](https://github.com/tpoechtrager/osxcross#usage-examples).

## Acknowledgments

- [varbhat/crossmac](https://github.com/varbhat/crossmac) (Pre-compiled osxcross for Void Linux)
- [plentico/osxcross-target](https://github.com/plentico/osxcross-target) (Pre-compiled osxcross, but with older libcrypto)

## License

This project is provided under a MIT license that can be found in the [LICENSE](LICENSE) file. By using, distributing, or contributing to this project, you agree to the terms and conditions of this license.
