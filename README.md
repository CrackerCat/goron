# goron
Yet another llvm based obfuscator.

当前支持特性：
 - 混淆过程间相关
 - 间接跳转,并加密跳转目标

## 下载
```
git clone https://github.com/amimo/goron.git -b llvm-7.1.0
```

## 编译

```
cd goron
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release -DLLVM_ENABLE_ASSERTIONS=ON -DLLVM_ENABLE_PROJECTS=clang -G "Unix Makefiles" ../llvm
make -j12
```

## 使用
跟ollvm类似,可通过编译选项开启相应混淆.
如启用间接跳转混淆
```
$ path_to_the/build/bin/clang -mllvm -irobf -mllvm --irobf-indbr test.c
```
对于使用autotools的工程
```
$ CC=path_to_the/build/bin/clang or CXX=path_to_the/build/bin/clang
$ CFLAGS+="-mllvm -irobf -mllvm --irobf-indbr" or CXXFLAGS+="-mllvm -irobf -mllvm --irobf-indbr" (or any other obfuscation-related flags)
$ ./configure
$ make
```