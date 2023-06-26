# UltraMCR录像机

## 录制时码

+ LTC In：所有录制文件的时码均来源于LTC In输入的时码

+ SDI In：录制文件的时码来源于各自SDI信号内嵌的时码

+ Internal：录制文件的时码来源于设备内部自发生的时码

## 4种控制模式

+ 单机手动：手动控制设备录制、播放相关功能
+ 单机定时：设备处于定时录制状态，不支持手动启动录制，也不支持启动播放操作。但可以手动强制停止正在录制的任务。
+ 级联主：手动控制设备启动、停止录制，可以带动从机同时启动、停止录制。
+ 级联从：接收主机命令，做出跟随主机的操作。

##  锁相输入和UNSYNC报警

+ 输入信号没有被锁相信号（Ref In）锁定时，可以不必给机器接入锁相信号，机器会自动帧同步
+ 输入信号已经和锁相信号锁定时，建议接入ref in，机器会遵循接入的锁相信号工作
+ 当检测到输入信号与Ref In不同步，画面会提示UNSYNC

## 多台设备级联控制

将多台设备的LTC接口串接起来，第一级设备为主，往后为从。将主设置为级联主，从设置为级联从。

1. 要想实现多台设备的录制文件全都具有相同的内部时码

   >需配置所有设备的时码来源为Internal，并设定同样的初始时码值

2. 要想实现多台设备的录制文件全都具有相同的外部LTC时码

   > 要将主备接入外部LTC时码源
   >
   > 配置所有设备录制时码来源为LTC In

**要想实现多台设备的录制文件全部具有相同的时长**，还需要将多台设备接入统一的Ref信号，以保证多台设备工作在同一时钟频率下。

1. 如果您的现场环境里有 Ref信号源，需要将多台设备接入统一的Ref信号，以保证多台设备工作在同一时钟频率下。
2. 由于UltraMCR自带了 Ref输出，您也可以只在第1级 UltraMCR接入外部的Ref In，将第1 级的 Ref Out 接入第2 级的UltraMCR的Ref In，将第 2级的 UltraMCR的 Ref Out接入第 3 级的 Ref In…
3. 如果您的现场环境里没有Ref信号源，也没有关系。UltraMCR自带了 Ref Out，您可以将第1级的UltraMCR的Ref Out接入第2级的UltraMCR的Ref In，将 第2级的UltraMCR的Ref Out接入第3级的Ref In…， 此时， 所有的UltraMCR都会工作在第1级的UltraMCR的时钟频率上。

## NAS和SSD

+ 连接NAS

  接入控制软件，左上角设备，配置网络；把网络ip和NAS设置成同一网段，输入用户名密码地址连接

  nas1://192.168.100.14/NAS		user		Redlink123

  ![image-20230619161400252](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20230619161400252.png)

  ![image-20230619162203136](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20230619162203136.png)

+ 按键menu，设置Storage，选择NAS
