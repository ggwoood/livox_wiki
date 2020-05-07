# 1 Livox SDK API

Livox SDK API provides a set of C style functions which can be conveniently integrated in C/C++ programs. Please refer to the [Livox SDK API Reference](https://livox-sdk.github.io/Livox-SDK/) for further information.

## 1.1 Installation
The installation procedures in Ubuntu 16.04/14.04 32-bit LTS and Mac are shown here as examples.
### 1.1.1 Ubuntu 16.04/14.04 32-bit LTS
#### Dependencies
Livox SDK requires [CMake 3.0.0+](https://cmake.org/), [Apache Portable Runtime (APR) 1.61+](http://apr.apache.org/) and [Boost 1.54+](https://www.boost.org/) as dependencies. You need to install boost, cmake using apt:
```
sudo apt install cmake libboost-atomic-dev libboost-system-dev
```
And download the newest apr linux source file in [Apache Portable Runtime (APR) 1.61+](http://apr.apache.org/):
```
tar -zxvf apr-1.X.X.tar.gz
cd apr-1.X.X
./configure --prefix=/usr/local/apr --disable-lfs
make && sudo make install
```
#### Compile Livox SDK
In the Livox SDK directory, run the following commands to compile the project:
```
git clone https://github.com/Livox-SDK/Livox-SDK.git
cd Livox-SDK/build
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/apr/lib/pkgconfig/ && export PKG_CONFIG_PATH
cmake ..
make
sudo make install
```
As the PKG_CONFIG_PATH will only take effect on the current terminal, you will need to run `PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/apr/lib/pkgconfig/ && export PKG_CONFIG_PATH` on every new shell, unless you add this line to your .bashrc as an environment variable.

### 1.1.2 Mac
#### Dependencies
Livox SDK requires [CMake 3.0.0+](https://cmake.org/), [Apache Portable Runtime (APR) 1.61+](http://apr.apache.org/) and [Boost 1.54+](https://www.boost.org/) as dependencies. You can install these packages using brew:
```
brew install cmake apr boost
```
Then, you need to run the following command:
```
brew info apr
```
And you can see the following message and get the apr path:
```
apr: stable 1.X.X (bottled) [keg-only]
Apache Portable Runtime library
https://apr.apache.org/
/usr/local/Cellar/apr/1.X.X (XX files, X.XMB)
  Poured from bottle on XXXX-XX-XX at XX:XX:XX
From: https://mirrors.ustc.edu.cn/homebrew-core.git/Formula/apr.rb
==> Caveats
apr is keg-only, which means it was not symlinked into /usr/local,
because Apple's CLT package contains apr.

If you need to have apr first in your PATH run:
  echo 'export PATH="/usr/local/opt/apr/bin:$PATH"' >> ~/.bash_profile
```
#### Compile Livox SDK
In the Livox SDK directory, run the following commands to compile the project:
```
git clone https://github.com/Livox-SDK/Livox-SDK.git
cd Livox-SDK/build
export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/Cellar/apr/1.X.X/libexec/lib/pkgconfig
cmake ..
make
sudo make install
```
As the PKG_CONFIG_PATH will only take effect on the current terminal, you will need to run the following command on every new iterm, unless you add this line to your .bash_profile as an environment variable. 