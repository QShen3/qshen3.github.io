---
title: 自己编译的Qt5静态链接库
date: 2020-09-07 01:35:05
tags:
    - Qt5
    - static build
    - package
categories: 阿加斯城
keywords:
    - Qt
    - Qt5
    - package
    - 静态编译
    - Windows
    - Linux
    - macOS
    - ARM
    - X64
excerpt: 提供各个平台的下载
---

# 简要说明
　　Qt官方只提供了源代码和动态链接库，没有提供静态链接库，所以如果你的项目依赖了Qt，并且想静态编译的话，就需要Qt的静态链接库了。我之前有过这个需求，并且将来有可能还会有这个需求，正好之前配好了自己的Gitlab，那不如就用Qt来试一试Gitlab的CI好不好用。干脆就把所有能搞到的平台都编了一个遍。目前官方最新的LTS版本是5.12.9，目测会持续很长一段时间。至于5.15 LTS，应该只有付费用户才能享受了。期待后续官方可以给Qt6加入Conan的支持，这样就不需要我再自己配置编译了。

# 下载地址
## Linux
　　Linux的编译平台为官方推荐的Ubuntu 16.04 LTS，尽量保证兼容性。只编译了64位，现在32位用得应该很少了。
### x64
#### GCC
　　编译器版本为5.4.0

　　编译配置参数：
```bash
configure -prefix /usr/local/Qt-5.12-linux-x64-gcc-static -opensource -nomake examples -nomake tests -confirm-license -static -optimize-size -openssl-linked -platform linux-g++
```
　　下载地址：[OneDrive](https://storage.live.com/items/441D3FDA5A491ADA!466629:/Qt-5.12-linux-x64-gcc-static.tar.xz)
#### Clang
　　编译器版本为3.8.0

　　编译配置参数：
```bash
configure -prefix /usr/local/Qt-5.12-linux-x64-clang-static -opensource -nomake examples -nomake tests -confirm-license -static -optimize-size -openssl-linked -platform linux-clang
```
　　下载地址：[OneDrive](https://storage.live.com/items/441D3FDA5A491ADA!466626:/Qt-5.12-linux-x64-clang-static.tar.xz)
#### AOCC
　　编译器版本为1.1.0

　　编译配置参数：
```bash
configure -prefix /usr/local/Qt-5.12-linux-x64-aocc-static -opensource -nomake examples -nomake tests -confirm-license -static -optimize-size -openssl-linked -platform linux-clang
```
　　下载地址：[OneDrive](https://storage.live.com/items/441D3FDA5A491ADA!466624:/Qt-5.12-linux-x64-aocc-static.tar.xz)
#### ICC
　　编译器版本为18.0.3

　　编译配置参数：
```bash
configure -prefix /usr/local/Qt-5.12-linux-x64-icc-static -opensource -nomake examples -nomake tests -confirm-license -static -optimize-size -openssl-linked -platform linux-icc -L /usr/lib/x86_64-linux-gnu -L /usr/lib64 -L /usr/lib32 -L /usr/lib
```
　　下载地址：[OneDrive](https://storage.live.com/items/441D3FDA5A491ADA!466627:/Qt-5.12-linux-x64-icc-static.tar.xz)
### ARM64
#### GCC
　　编译器版本为5.4.0

　　编译配置参数：
```bash
configure -prefix /usr/local/Qt-5.12-linux-arm64-gcc-static -opensource -nomake examples -nomake tests -confirm-license -static -optimize-size -openssl-linked -platform linux-g++
```
　　下载地址：[OneDrive](https://storage.live.com/items/441D3FDA5A491ADA!466621:/Qt-5.12-linux-arm64-gcc-static.tar.xz)
#### Clang
　　编译器版本为3.8.0-2

　　编译配置参数：
```bash
configure -prefix /usr/local/Qt-5.12-linux-arm64-clang-static -opensource -nomake examples -nomake tests -confirm-license -static -optimize-size -openssl-linked -platform linux-clang
```
　　下载地址：[OneDrive](https://storage.live.com/items/441D3FDA5A491ADA!466625:/Qt-5.12-linux-arm64-clang-static.tar.xz)
## Windows
　　编译平台为Windows 10 10240。应该可以兼容以后的Windows 10版本。同样只编译了64位。
### X64
#### MSVC
　　编译器版本为MSVC 19.00.24210（14.0），理论上来说应该兼容后续VS版本。

　　编译参数：
```bat
configure -prefix C:\Qt5\Qt-5.12-windows-x64-msvc-static -opensource -nomake examples -nomake tests -confirm-license -static -release -optimize-size -openssl-linked -icu -opengl desktop -platform win32-msvc -L C:\OpenSSL\lib -I C:\OpenSSL\include -L C:\icu4c\lib -I C:\icu4c\include
```
　　下载地址：[OneDrive](https://storage.live.com/items/441D3FDA5A491ADA!466628:/Qt-5.12-windows-x64-msvc-static.7z)
#### MinGW
　　编译器版本为7.3.0

　　编译参数：
```bat
configure -prefix C:\Qt5\Qt-5.12-windows-x64-mingw-static -opensource -nomake examples -nomake tests -confirm-license -static -release -optimize-size -openssl-linked -icu -opengl desktop -platform win32-g++ -L C:\OpenSSL\lib -I C:\OpenSSL\include -L C:\icu4c\lib -I C:\icu4c\include
```
　　下载地址：[OneDrive](https://storage.live.com/items/441D3FDA5A491ADA!466967:/Qt-5.12-windows-x64-mingw-static.7z)
#### Clang
　　编译器版本为6.0.1

　　编译参数：
```bat
configure -prefix C:\Qt5\Qt-5.12-windows-x64-clang-static -opensource -nomake examples -nomake tests -confirm-license -static -release -optimize-size -openssl-linked -icu -opengl desktop -platform win32-clang-msvc -L C:\OpenSSL\lib -I C:\OpenSSL\include -L C:\icu4c\lib -I C:\icu4c\include
```
　　下载地址：[OneDrive](https://storage.live.com/items/441D3FDA5A491ADA!466622:/Qt-5.12-windows-x64-clang-static.7z)
#### ICC
　　编译器版本为19.1.2.254

　　编译参数：
```bat
configure -prefix C:\Qt5\Qt-5.12-windows-x64-icc-static -opensource -nomake examples -nomake tests -confirm-license -static -release -optimize-size -openssl-linked -icu -opengl desktop -platform win32-icc -L C:\OpenSSL\lib -I C:\OpenSSL\include -L C:\icu4c\lib -I C:\icu4c\include
```
　　下载地址：[OneDrive](https://storage.live.com/items/441D3FDA5A491ADA!466620:/Qt-5.12-windows-x64-icc-static.7z)
### ARM64
　　最后这个ARM64的算是附赠的吧。不过我没有相应的测试平台，所以不保证可以使用。
#### MSVC
　　编译器版本为MSVC 19.27.29111（16.7.2）。因为微软至今还没有推出ARM64平台原生的编译器，所以采用了交叉编译的方式。主机平台为X64。期待后续微软可以推出ARM64平台原生的编译器。

　　编译参数：
```bat
configure -prefix C:\Qt5\Qt-5.12-windows-arm64-msvc-static -opensource -nomake examples -nomake tests -confirm-license -static -release -optimize-size -openssl-linked -icu -platform win32-g++ -xplatform win32-arm64-msvc2017  -L C:\OpenSSL-arm64\lib -I C:\OpenSSL-arm64\include -L C:\icu4c-arm64\lib -I C:\icu4c-arm64\include
```
　　下载地址：[OneDrive](https://storage.live.com/items/441D3FDA5A491ADA!466630:/Qt-5.12-windows-arm64-msvc-static.7z)
## macOS
　　macOS平台可能作用不是很大，毕竟正常发布的话，大家还是会选择官方渠道吧。编译平台为macOS Catalina（10.15.5）
### x64
　　目前只编译了X64版本，苹果那个给开发者准备的ARM套件还是有点贵……
#### Clang
　　编译器版本为11.0.3

　　编译配置参数：
```bash
configure -prefix /usr/local/Qt-5.12-macos-x64-clang-static -opensource -nomake examples -nomake tests -confirm-license -static -release -optimize-size -openssl-linked -platform macx-clang -I /usr/local/opt/openssl/include -L /usr/local/opt/openssl/lib
```
　　下载地址：[OneDrive](https://storage.live.com/items/441D3FDA5A491ADA!466623:/Qt-5.12-macos-x64-clang-static.tar.xz)

　　
