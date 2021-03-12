###安卓应用

#### 1、为什么APP无法连接蓝牙设备？

- Android 6.0 之后的系统需要申请位置权限（android.permission.ACCESS_FINE_LOCATION）
- Android 9.0 之后的系统除了申请位置权限，还需要打开 GPS

#### 2、为什么蓝牙信号需要位置权限？

APP 有可能通过解析 Wi-Fi 和蓝牙信息来获取您当前所在的位置，Google 为了您的隐私考虑，Android 6.0 之后的相关 API 加入了位置权限需求

#### 3、APP需要继承第三方库中的APPlication类，但同时需要继承MultiDexApplication怎么办？



#### 4、APP发送http请求报错是为什么？



#### 5、怎么把APP的签名文件迁移到pkcs12？



#### 6、在不安装Android Studio的情况下怎么查看APP的log输出？