# 在哪吒上便宜SDL庫

SDL庫主要是很多UI都基于此来进行开发的，尤其是游戏模拟器，也是基于此来开发的，查看了Tina 中 的SDL库，打开编译并能不能通过编译，所以只能自己下载来进行编译

目前缺少两个 头文件的包含

分别是： #include <esd.h>

 #include <pulse/pulseaudio.h>

办法：将这个模块 disable 掉

```
 ./configure --prefix=$PWD/install --host=riscv64-unknown-linux-gnu --disable-pulseaudio --disable-esd
```

编译完成
