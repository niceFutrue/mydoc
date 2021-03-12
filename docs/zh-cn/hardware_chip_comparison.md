### 芯片功能对比

#### 1、从编程开发方式、性能表现、功耗表现等⽅⾯列举下ST17H66与62之间的区别

- 编程开发方式

**ST17H66：Keil，C语言**

**ST17H62：Keil，C语言**

- 性能表现

**ST17H66：**

11个通用I/O引脚 

所有引脚均可设置为串行接口和可编辑的IO MUX函数映射 

所有引脚均可设置为唤醒状态 

3个QDEC解码器 

6通道PWM 

2通道PDM/I2C/SPI/UART 

4通道DMA

支持SIG-Mesh多种特性

Friend 节点

Low Power 节点

Proxy 节点

Relay 节点



**ST17H62：**

19个通用I/O引脚 

所有引脚均可设置为串行接口和可编辑的IO MUX函数映射 

所有引脚均可设置为唤醒状态 

共18个针脚可触发中断 

3个QDEC解码器 

6通道PWM 

4通道I2S 

2通道PDM 

2通道I2C 

2通道SPI 

1通道UART

8通道DMA

JTAG 

支持SIG-Mesh多种特性

Friend 节点

Low Power 节点

Proxy 节点

Relay 节点



- 功耗表现

**ST17H66：**

0.3μA @ OFF Mode(IO wake up only) 

1μA @ Sleep Mode with 32KHz RTC 

4uA @ Sleep Mode with 32KHz RTC and all SRAM retention 

Receive mode: 8mA @3.3V power supply 

Transmit mode: 8.6mA(0dBm output power) @3.3V power supply 

MCU: <90uA/MHz

**ST17H62：**

0.7μA @ OFF Mode(IO wake up only) 

2μA @ Sleep Mode with 32KHz RTC 

Receive mode: 6.7mA @3.3V power supply 

Transmit mode: 6.7mA(0dBm output power) @3.3V power supply 



#### 2、ST17H66 版本芯片在使用上和之前芯片软件有什么区别呢？

- 软件上使用区别，是可以兼容之前的固件的，硬件上修复了哪些 bug。
- 具体的可以参考文档 ST17H66使用指南。



#### 3、ST17H66 的 GPIO34 ~ GPIO39 管脚是否只能设置为输入模式？

- ST17H66 的 GPIO34 ~ GPIO39 只能设置为输入模式，没有软件上拉或下拉功能，不能设置为输出模式。
- 详情可参见 **外设说明**。

#### 4、ST17H66 有适配 Linux 平台驱动吗？

有

#### 5、ST17H66 的 VDD3P3_RTC 是否支持单独电池供电？

- ST17H66 内部 RTC 域不可以独立工作，需要主 CPU 参与配置，单独使用纽扣电池供电时依然无法抵御突然掉电的情况。
- 如果需要系统掉电时时钟信息保存，可以添加外部 RTC 时钟芯片。

#### 6、ST17H66 和 ST17H63 以及 ST17H65有什么区别？

- 蓝牙版本

ST17H66支持蓝牙BLE5.1，ST17H63支持蓝牙BLE5.0，ST17H65支持蓝牙BLE5.1

- 封装

ST17H66是SOP16封装，ST17H63是QFN48封装，ST17H65是QFN32封装

- 性能

ST17H66

11个通用I/O引脚 

所有引脚均可设置为串行接口和可编辑的IO MUX函数映射 

所有引脚均可设置为唤醒状态 

3个QDEC解码器 

6通道PWM 

2通道PDM/I2C/SPI/UART 

4通道DMA



ST17H63

33个通用I/O引脚 

所有引脚均可设置为串行接口和可编辑的IO MUX函数映射 

所有引脚均可设置为唤醒状态 

共18个针脚可触发中断 

3个QDEC解码器 

6通道PWM 

4通道I2S 

2通道PDM/I2C/SPI

1通道UART

8通道DMA

JTAG 



ST17H65

22个通用I/O引脚 

所有引脚均可设置为串行接口和可编辑的IO MUX函数映射 

所有引脚均可设置为唤醒状态 

3个QDEC解码器 

6通道PWM 

2通道PDM/I2C/SPI/UART 

4通道DMA