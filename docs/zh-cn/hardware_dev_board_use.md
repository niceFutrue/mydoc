###开发板使用

#### 1、ST17H66开发板是否集成 LED driver 芯片？

我司出厂的ST17H66开发板中含有 LED driver 芯片。

#### 2、开发板运行发热过高如何改善？

- 降低功耗: 如果摄像头并非实时开启，ST17H66可以周期传输，空闲时间可以进入休眠模式降低功耗。
- 增大散热面积: 可以通过在ST17H66芯片上方增加散热片来实现。

#### 3、开发板不使用 USB 供电，如何使用管脚供电？

- 第一种方法：”3V3 连接 3V3” + “GND 连接 GND”（如果开发板存在非 3.3V 供电的器件，则该器件将无法使用）
- 第二种方法：”5V 连接 5V” + “GND 连接 GND”

**注解**

供电电流需要满足 500mA。

#### 4、ST17H66开发板连接手机热点，出现如下报错，有哪些原因？

bluetooth: state : 0 -> 2 (b0)

bluetooth: state : 2 -> 0 (200)

Simple Bluetooth : Disconnect reason : 2

- 请检查外接天线状态，路由器是否存在与 SSID 是否正确。

#### 5、开发板XXXXX 中 XXXX 芯片音频数据通过什么协议与XXXX 交互？

- 开发板XXXXX中，XXXX 的音频数据是通过 SPI 传给XXXXX的。

#### 6、是否有支持 POE 供电的以太网开发板？

- XXXXX是支持 POE 供电的以太网开发板。

#### 7、XXXX 中为什么 Audio 和 Camera 不能共用？

- Camera 和 Audio 都使用了 I2S 接口进行通讯，而 XXXX只有 1 路 I2S。
- 并且 Camera 使用并行 I2S， 而 Audio Codec 使用串行 I2S，这两种模式不能一起工作，因此不能通过 CS 线来分时复用，必须重新配置。

#### 8、XXXX是否支持蓝牙语音？

- XXXX使用的芯片为XXXXX，该芯片不支持蓝牙功能，您可以选择使用 XXXX的开发板或芯片进行相关功能的开发。

#### 9、XXXX上的XXXX芯片是否自带功放？最大支持外接多大功率的喇叭？

- XXXX使用的 XXXX 芯片内部未集成功放，XXXXX 芯片仅可以驱动低阻抗耳机。
- 因此开发板集成了一颗型号为 NS415 的 PA，最大可输出功率为 3W （典型值），推荐使用 5V 4欧 的扬声器。

#### 10、XXXX 是否有并行 LCD 接口？如果有，硬件上需要如何使用？

- XXXX上有并行 LCD 接口，但是目前暂时没有提供配套的屏幕。
- 您可能需要设计相关的屏幕来进行接口兼容匹配。您可以选择使用音频板上的排母接口或是底板上的 FPC（未贴）来连接并口屏，或是通过底板两侧的排针通过杜邦线来连接并口屏幕。

#### 11、XXXX是否支持 USB 调试？

- XXXX所有版本均内置了 FT2232HL，该芯片自带 USB - JTAG Bridge 以使用 JTAG 调试功能。
- 您需要切换拨码开关来连接 JTAG 相关引脚，在 idf menuconfig 中打开 JTAG 调试功能，并且确保 efsue 没有禁用 JTAG 调试。
- 安装 openocd 以支持 JTAG 调试之后，您便可以使用 idf.py openocd gdb 、 idf.py openocd gdbgui 等命令进行调试。

#### 12、XXXX中为什么需要多加一块数字 mic 芯片，不可以直接使用 ADC 采集吗？

- XXXX可以直接使用内部或外部的 ADC采集模拟麦克风的信号，但是您可能需要自行设计相关电路。
- XXXX贴了数字麦和模拟麦两种 MIC，XXXX只贴了模拟麦。使用两种麦克风的原因是便于您对不同种类的麦克风进行评估。
- 数字麦克风引脚直接与 ESP32 管脚连接，通过 I2S 进行通讯。
- 模拟麦克风连接到了 Audio Codec IC，由 Codec IC 内部的 ADC 进行采样，并通过 Codec IC 的I2S 接口进行通讯。
- XXXX使用的 Codec IC 同时支持音频的编码和解码，您可以同时使用音频采集和播放功能，而无需使用额外的 ADC 及相关的转换调理电路。

#### 13、XXXX中的 speaker 与 Audio_Out 接口是否支持同时输出？

- XXXXX中的 speaker 与 Audio_Out 接口可以同时输出。
- 如果您使用模拟麦克风，那么您只需要将麦克风的音频 PA 连接至 Codec IC，便可以使用 I2S 与 Codec 进行全双工通讯，同时进行音频采集和播放。
- 如果您使用数字麦克风，那么您只需要将数字麦克风和 Codec IC 连接至XXXXX的 I2S 相关引脚，便可以使用 I2S 进行全双工通讯。

#### 14、XXXX中的 I2C *FPC* CNN 接口如何使用？是否有相关的 Demo？

- 该 FPC 可供您自行开发产品时，通过使用XXXXX底板进行功能评估而无需预先设计主控板，方便进行功能测试，因此没有相关 Demo 提供。

#### 15、XXXX中的 4.3inch *LCD* FPC_CNN 接口是否为并口 LCD 接口？

- 是的，该 FPC 接口可以用于驱动 并口的屏幕。

**注解**

- 该 FPC 默认未贴，需要您自行焊接。
- 由于并口会占用大量的 IO 口，因此，音频板和摄像头的功能都会无法使用，或者需要分时复用。
- 目前暂未提供基于并口的XXXXX LCD Demo，您可能需要自行实现其驱动。

#### 16、XXXX PCB上有很多没有焊接元件的地方是否是运送过程中丢失？

- XXXXX的每个版本上都有一些元件位的焊盘上无元件的情况，这些是处于未来的升级而预留的位置。
- 例如并口屏的 FPC 接口，由于目前暂未使用，因此没有贴。同理，音频板上的 ES7210 也没有贴。

#### 17、XXXX开发板配有摄像头，是否有摄像头的例程可以提供？

- XXXXX开发板示例代码：
- XXXXX开发板摄像头示例：

#### 18、是否可以单独购买 XXXX的子板？

- 目前淘宝店铺暂时没有子板出售，您可以联系商务进行需求咨询。

#### 19、XXXX开发板 LED 灯不亮，设备管理器也无法找到该设备？

- 插上 USB 线之后供电，用万用表测试引脚 VCC 和 GND 是否有电压，检查供电是否正常。
- 是否所有的设备都是这样的现象？检查其他的 XXXXX开发板设备用该 USB 线是否正常。
- 若上面都不可行的话，可以通过 USB 转 TTL 设备去接线，只需接XXXXX的引脚 VCC, GND, TXD ，测试一下芯片是否有问题，用串口助手看是否有打印信息出来。
- 如果可以，请测试串口驱动芯片是否有电压，可以参考XXXXX 原理图 。

#### 20、文档中有提到 EN 按键，但在购买的开发板上没有找到该按键？

建议检查开发板是否有 Reset 按键，由于 EN 常用做复位功能，部分开发板丝印会标记为 Reset 按键。

#### 21、使用XXXX开发板，连接 Windwos 电脑后未在设备管理器中找到串口，有哪些原因？

- 通常情况下出现该原因是未安装设备驱动，可在下载安装 FT232R USB [UART 驱动](https://www.usb-drivers.org/ft232r-usb-uart-driver.html)。
- 若驱动安装后问题依然存在，可逐步检查设备供电，USB 线材等。

1. 使用 XXXXX音频开发板，长按 Boot 按键也很难进入下载模式，是什么原因？

- 正确的做法是：长按 Boot 按键 ，然后按 RST 按键（此时 Boot 按键不松开 ），然后松开 RST 按键（此时 Boot 依然不松开），当进入下载模式开始 Download 后，Boot 按键可松开了。