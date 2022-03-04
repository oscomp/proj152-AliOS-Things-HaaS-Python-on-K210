# 项目描述

K210是集成机器视觉（卷积神经网络加速处理器KPU）与机器听觉多模态识别（音频信号处理器APU）的系统级芯片（SoC），具备视听一体的能力，算力达1TOPS，可广泛应用于智能家居、智能园区、智能能耗和智能农业等场景。

[AliOS Things](https://www.aliyun.com/product/aliosthings)是阿里云IoT事业部发布的面向IoT领域的、高可伸缩的物联网操作系统。拥有弹性内核Rhino，和丰富的云端一体的IoT组件，以及HaaS Python、HaaS JavaScript框架以支持利用Python/JS语言进行开发。目前已被广泛应用于智能音箱、IP摄像头等智能家居、安防等领域。 其中内核Rhino是用C语言自主设计实现的，主要包括调度、任务管理、内存管理、任务同步（互斥量、信号量、事件）、消息队列、时间管理、软件定时器等功能。[HaaS云端一体智能设备开发框架](https://haas.iot.aliyun.com/)是开源世界中应用很广泛的开发框架（在蓝牙/Wi-Fi、4G等多种类型的开发板可以使用），可以让物联网设备快速上云并大大降低开发者的入门门槛。

本文旨在为K210提供HaaS Python的开发模式，让视觉/听觉类智能设备上云更加方便，设备端应用开发更加高效。


# 所属赛道

2022全国大学生操作系统比赛的“OS功能挑战”赛道

# 参赛要求

以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的学生（本科生/研究生均可）
如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖
请遵循“2022国大学生操作系统比赛”的章程和技术方案要求

# 项目导师

吴相楠
email: wuxiangnan.wxn@alibaba-inc.com
github id：

# 难度

中等

# 参考思路
本文的最终目标是要让HaaS Python运行在K210平台上，有两种实现思路：
1. 在K210平台上实现[HaaS Python标准的API](https://haas.iot.aliyun.com/haasapi/index.html#/)（可优先完成aliyunIoT、bleNetConfig、littlevgl等，语言不限）

2. 将AliOS Things运行在K210平台上，HaaS Python天然就可以运行了。AliOS Things仓库中hardware目录下包含了已支持的硬件平台，可供参考。[AliOS Things仓库](https://github.com/alibaba/AliOS-Things)中documentation/coding/coding_style.md提供了AliOS Things的代码风格规范。

# License
Apache 2.0 license

# 预期目标

注意：下面的内容是建议内容，不要求必须全部完成。选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标。

## 方式1 - 在K210平台上运行AliOS Thigns操作系统

### 第一题：从零开始
[AliOS Things](https://github.com/alibaba/AliOS-Things)在K210开发板上成功运行， 保证Rhino中的调度（必选FIFO调度策略，可选RR/CFS调度）、任务管理、内存管理、互斥量、信号量、消息队列、时间管理模块可用。
对接UART设备驱动，保证控制台输入输出可用。
内核测试用例测试通过。

### 第二题：设备驱动
K210外设GPIO、I2C、SPI、flash、watchdog、PWM对接到AliOS Things驱动框架。
提供各类型外设驱动的测试用例，覆盖VFS API和AliOS Things自有的AOS API。

### 第三题：SMP支持
支持AliOS Things在K210双核上运行。重点实现SMP调度器和SMP自旋锁。

## 方式2 - 在K210平台上实现[HaaS Python标准的API

### 第一题：从零开始
将MicroPython引擎在K210上运行起来，需要支持micropython标准API，通过micropython标准API的自测用例。

### 第二题：在K210上支持aliyunIoT HaaS Pyhton的API
通过阿里云IoT团队aliyunIoT类的自测用例

### 第三题：K210扩展HaaS Python AI API
阿里云IoT已经发布了[HaaS AI API的标准](https://haas.iot.aliyun.com/haasapi/index.html#/Python/docs/zh-CN/haas_extended_api/AI)，参赛者可以在此基础上根据K210功能对此API进行扩展
