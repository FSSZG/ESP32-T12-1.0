# ESP32 T12烙铁 1.0

#### 介绍
基于ESP32开发的便携式T12电烙铁焊笔 ，拥有PD100W诱骗，OLED显示， 温度可调，姿态唤醒，多功能设置，断电存储，自动休眠，OTA等功能
主控为ESP32-PICO-D4，发热芯为T12发热芯，通过INA190采样热电偶电势来获取烙铁温度，0.91寸OLED屏幕显示各种信息；2个微动开关来操作, EEPROM保存用户设置，TYPE-C接口供电65W（20V3A），手柄是用solidwork设计在嘉立创打的样
1. 设定温度0到450℃   （T12热电偶分度表资料太少  精度没条件测）
2. PWM占空比 1到100%可设置，超过将不在增加PWM占空比
3. 0.91寸OLED数显，有多个主界面和设置界面，分别显示对应的各种信息
4. 休眠时间1到60分钟可调，达到休眠设定时间没有使用将关闭加热休眠，晃动手柄或按最下方按键即可退出休眠模式开始加热到设定温度
5. 插入电源开机自动读取设置然后自动加热  采样显示各种信息
6. CH224K快充诱骗最大到PD100W  平时PD65W (20v 3A)足够  普通5V USB也可以使用   就是加热有点慢
7. LIS3DHTR 加速度传感器 负责采集运动姿态负责触碰休眠唤醒 提供芯片温度
8. T12温度采集 使用PMOS控制 电源开关给发热芯加热 当PMOS关闭就让 ADC引脚去采集 INA190A5IRSWR 放大500倍的热电偶电压信号

####  程序下载
1. 程序基于Arduino IDE 开发  并把相关库添加好，使用串口模块连接PCB预留的下载触点 选择EAP32 Pico -Kit型号和对应串口编译上传即可
2. OTA升级我这是使用Arduino IDE直接上传的模式 需要通过串口模块有线连接先下载一个带有OTA升级程序才能后续通过网络下载 详细信息自行百度
3. OTA升级需要把程序里的WIFI账号密码改为自己使用的 或是开个WIFI热点改成烙铁对应WIFI账号密码
4. 下载需要引脚 P0拉低和EN拉低一下来进入下载模式或是使用带有一键下载功能的串口模块（https://oshwhub.com/FJ956391150/ch340c-chuan-kou-mu-kuai）
5. 程序和功能都不是很完善 等以后有空在升级下  程序和依赖库在附件内 

#### 菜单选项
1. 主界面显示温度  电压  PWM 热电偶电压等参数
2. PWM功率 设置界面 
3. 休眠时间设置界面
4. 屏幕显示方向设置
5. LED辅助照明开关
6. OTA升级开关
7. 在主界面两个按键分别控制设定温度加减  
8. 同时按下两个按键切换界面 单独按设定参数

####  注意事项
1. PCB 打样  2层  1.6板厚  元件参数以原理图为准 嘉立创没有的元件上淘宝
2. 烙铁主要由PCBA  3D打印的外壳 盖板 T12烙铁芯组成    3D打印文件在附件内
3. 手柄连接烙铁芯处可能有些热尽量选用耐高温材质打印外壳
4. 有两个不同版本功能的外壳  但都需要底部盖板（推荐使用3D打印的盖板） 组装好建议连接处都打点胶
5. 1.0版外壳带有LED辅助照明功能 额外需要 LED灯小板和 两个普通测试针（型号看图我也不知道）
6. 1.1版外壳 需要有普通T12烙铁的头套不需要其他的
7. T12烙铁芯通过8个 **侧贴** 的天线弹片和PCB相连

#### 参与贡献
熵 2022 6 26
立创开源平台：https://oshwhub.com/FJ956391150/t12-lao-tie-1-0


![输入图片说明](IMG_20220618_211708.jpg)
![输入图片说明](IMG_20220624_174009.jpg)
![输入图片说明](IMG_20220626_161250.jpg)
![输入图片说明](IMG_20220626_161237.jpg)



