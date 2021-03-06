# Introduction
此项目参考了b站稚晖君的Link-Card项目，但是在其基础上做了修改，采用STM32和ST95HF芯片，预期将实现NFC Reader/Tag/Emulation等功能，一张卡可模拟多张卡，包括门禁、公交等场景。

# Version iteration
## V1.0
* 主控芯片：32L051K8U6
* NFC芯片：ST95HF
* 显示屏：1.54inch墨水屏

### 2020.12.15
* 上传PCB工程 NFCV1.0.zip

### 2020.12.25
* 板子焊接完后，初步测试通过。

### 2020.12.28
* 发现STM32在使用内部2M时钟时，点灯可正常运行。使用内部16M时钟时，在调试模式下通过打断点方式，观察到可正常运行，但是退出调试模式，重新上电后就会卡住，LED也没反应。
* 可能的原因：
	1. 芯片问题，芯片在焊接时，被破坏了
	2. 电源问题，电流可能不够
	3. 软件问题，硬件都正常的情况下，STM32在16M时，进入了Sleep状态，需要被唤醒

### 2020.12.30
* 此版本暂时放一边，准备使用ST95官方的硬件方案，用STM32F103RGT6作为MCU，另外预留出STM32L051K8U6的位置。

## V1.1
* MCU：STM32F103RGT6
* NFC芯片：ST95HF
* 显示屏：1.54inch墨水屏

### 2021.01.08 
* 上传PCB工程 NFCV1.1(修正了投板PCB上的错误)

### 2021.01.09
* 板子焊接大部分焊接完成，初步测试通过。

### 2021.01.11
* 开始移植程序，使用STM32CubeMX生成的demo,能正常读到ST95HF的设备ID

### 2021.01.25
* 上传ST95HF修改过的demo ` EVAL-ST95HF_FW_V3.7.3`
* 读UID

### 2021.02.01
* 能检测到卡的类型，但是不能读取NDEF

* 发送命令：

  ```c
  >>>04 03 30 01 28
  ```

* 返回数据如下：

  ```c
  <<<90 04 04 24 00 00
  ```

* Hurt7 forked U  

