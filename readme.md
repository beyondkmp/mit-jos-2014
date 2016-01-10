## lab1 report

## 在OSX 10.11中编译安装gcc

安装相关依赖
```
brew deps gcc
brew install gmp isl libmpc mpfr xz
```

编译安装gcc

```
brew fetch gcc
cd /Library/Caches/Homebrew
tar xvf gcc-5.3.0.el_capitan.tar.bz2
cd gcc-5.3.0
mkdir build              # GCC will not compile correctly unless you build in a separate directory
cd build
../configure --prefix=/usr/local  --target=i386-jos-elf --disable-werror  --disable-libssp --disable-libmudflap --with-newlib  --without-headers --enable-languages=c --with-gmp=/usr/local/Cellar/gmp/6.1.0 --with-mpfr=/usr/local/Cellar/mpfr/3.1.3/ --with-mpc=/usr/local/Cellar/libmpc/1.0.3
make all-gcc
make install-gcc
make all-target-libgcc
make install-target-libgcc
```

编译安装gdb

```
brew fetch gdb
cd /Library/Caches/Homebrew
tar xvf gdb-7.8.3.tar.bz2
cd gdb-7.8.3
./configure --prefix=/usr/local --target=i386-jos-elf --program-prefix=i386-jos-elf- --disable-werror
make all
make install
```

编译安装qemu

```
git clone https://github.com/geofft/qemu.git -b 6.828-1.7.0
./configure --disable-kvm --disable-sdl --target-list="i386-softmmu x86_64-softmmu"
make
make install
```

## 参考
1. [Report for lab1, Shian Chen](https://github.com/Clann24/jos/tree/master/lab1)
2. [MIT 操作系统实验 MIT JOS lab1](http://blog.csdn.net/cinmyheart/article/details/39754269)
