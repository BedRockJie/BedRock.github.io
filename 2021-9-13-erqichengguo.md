|点亮技能| 开发者 | 简介|
| :---:| :----: | :---: |
|[自适应MIPI屏幕-240*32](https://bbs.aw-ol.com/topic/405/)| IAMLIUBO |实现**修改dts文件驱动自己的屏幕**！制作转接板，根据厂商驱动修改设备树节点，进行初始化，成功点亮！|
|[扩展板的设计](https://bbs.aw-ol.com/topic/385/)| xfdr0805 | 借鉴树莓派，给哪吒设计制作一个**扩展板**，可以充分利用哪吒引出的外设引脚|
|[扩展版实现-SPI-LCD](https://bbs.aw-ol.com/topic/417/)|xfdr0805 | 在扩展板上使用引出的SPI1接口**驱动屏幕**，同时用3屏:hushed: |
|[扩展版实现-IIC-OLED](https://bbs.aw-ol.com/topic/415/)|xfdr0805 | 在**应用层操作OLED**，实现IIC应用层写数据，并**移植u8g2GUI框架**|
|[扩展版实现-红外发送与接收](https://bbs.aw-ol.com/topic/416/)|xfdr0805 | 利用芯片内置的ir实现**红外的发射与接收**|
|[扩展版实现-按键与旋转编码器](https://bbs.aw-ol.com/topic/413/)|xfdr0805 |使用扩展芯片引出脚做按键检测，**配置设备dts添加设备**，提供按键与编码器的测试程序|
|[扩展版实现-点灯](https://bbs.aw-ol.com/topic/414/)|xfdr0805 | 分别使用**LEDC子系统**与**GPIO系统** **点灯**，同时展示了多种特效，**呼吸效果**，**定时效果**，并提供了测试代码|
|[DLNA客户端投屏](https://bbs.aw-ol.com/topic/411/)|逸俊晨晖|可以实现**网络投屏**！给哪吒适配DLNA客户端，并支持gsteamer硬解视频流，可支持同一网络下投屏使用，显示帧率够用|
|[D1使用gstreamer硬件解码视频](https://bbs.aw-ol.com/topic/410/)| 逸俊晨晖 | **提高视频播放流畅性**软件进行视频播放浪费CPU计算资源且播放卡顿不流畅，使用插件调用libcedar进行视频硬件解码，会非常流畅|
|[D1使用lvgl8和lvgl7](https://bbs.aw-ol.com/topic/409/)|逸俊晨晖|**移植LVGL官方显示框架**，使用cmake构建项目，使用软件刷屏，帧率不高，资源占用大|
|[哪吒3D打印外壳](https://bbs.aw-ol.com/topic/406/)|whycan转载|隐藏哪吒霸气的PCB，**可以直接3D打印的 stl 模型文件**|
|[SSH和VNC的远程桌面访问](https://bbs.aw-ol.com/topic/119/)|liangdi | **远程桌面连接**！基于RVBoards Debian 系统，开启远程访问，摆脱鼠标键盘显示器|
|[Fedora 系统在D1上运行](https://bbs.aw-ol.com/topic/393/)| tigger | Fedora 是知名的Linux操作系统，是由全球社区爱好者构建的面向日常应用的快速、稳定、强大的操作系统。**提供系统镜像，可直接dd烧录**|
|[LVGL7移植](https://bbs.aw-ol.com/topic/303/)|whycan|使用官方仓库构建，提供移植好的**源码固件，可直接编译使用**|
|[D1 F133 DXP封装](https://bbs.aw-ol.com/topic/284/)|tigger | 对**硬件**感兴趣的同学可以看这里！目前缺少D1原理图库文件，后续会补充上来|
|[D1双屏异显](https://bbs.aw-ol.com/topic/362/)|BedRock | 在D1上实现**两个屏幕同时播放不同应用**！HDMI播放视频，MIPI做UI交互，附固件及食用方法|
|[D1驱动树莓派dsi屏幕](https://bbs.aw-ol.com/topic/311/)| mangogeek | **哪吒点亮树莓派屏幕**。详细修改踩坑过程，非常具有参考性|
|[D1驱动IIC OLED屏幕](https://bbs.aw-ol.com/topic/348/)| BedRock | **哪吒点亮IIC OLED屏幕**，借鉴单片机驱动显示方法，直接在应用层操作设备|
|[D1 外设GPIO应用层食用](https://bbs.aw-ol.com/topic/349/)|BedRock  | **在应用层操作GPIO使用方法**，模仿单片机操作方法。对比上面的模块是使用增加dts设备方法|
|[用D1实现提醒器](https://bbs.aw-ol.com/topic/339/)|qianhao |制作：**web服务器加LVGL及传感器数据读取**，能够根据设置实现定时报警功能，附有详细DIY教程！|
|[openEuler烧录安装使用](https://bbs.aw-ol.com/topic/335/)| 中科院软件所 | openEuler 是基于 CentOS 的 Linux 发行版，**为企业量身定做**！**能够使用 JAVA 编程**，并能使用该系统的特性|
|[SPI-NAND性能优化](https://bbs.aw-ol.com/topic/266/)|Banquo| 针对SPI NAND读写中的思考，**还有优化空间**，目前优化一点搬运过程钟的时间|
|[D1哪吒开发板做一个卡牌识别机](https://bbs.aw-ol.com/topic/223/)|BedRock | 使用ncnn LVGL 实时视像头推理，**能够实现卡牌识别**，记录详细过程，并附有开源链接可二次开发！|
|[D1 openssl 加密CE](https://bbs.aw-ol.com/topic/321/)|DOT小文哥 | **用来加密个人APP**，SDK直接提供，打上pach,可以直接用来测试|
|[D1开发板4GNAS使用](https://bbs.aw-ol.com/topic/308/)| WM_CH |**摆脱网盘泄密风险，打造自己的NAS**，使用官方软件包，使用和宇宙4G模组，可外网访问NAS|
|[D1 Tina 升级gstreamer](https://bbs.aw-ol.com/topic/256/)| DOT小文哥 | **Tina中的播放器插件**，支持D1RV架构，连接到显示插件，支持g2d硬件旋转|
|[交叉编译opencv](https://bbs.aw-ol.com/topic/227/)| BedRock |**在哪吒上使用Opencv做图像处理第一步，交叉编译**！ 整理帖，完全步骤，很详细|