# @ohos.busManager.serial

串口管理

**起始版本：** 26.0.0

**系统能力：** SystemCapability.BusManager.Serial

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getSerialPortList](arkts-basicservices-getserialportlist-f.md#getserialportlist-1) | 获取串口列表。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addPortAuthorization](arkts-basicservices-addportauthorization-f-sys.md#addportauthorization-1) | 添加应用访问串口端口的权限仅面向串口授权弹窗系统应用开放 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [SerialConfigs](arkts-basicservices-serialconfigs-i.md) | 串口通信配置 |
| [SerialPort](arkts-basicservices-serialport-i.md) | 串口对象，提供串口设备信息和通信相关能力 |
| [SerialPortInfo](arkts-basicservices-serialportinfo-i.md) | 串口设备信息 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DataBits](arkts-basicservices-databits-e.md) | 串口通信中的数据位 |
| [Parity](arkts-basicservices-parity-e.md) | 串口通信中的校验位 |
| [StopBits](arkts-basicservices-stopbits-e.md) | 串口通信中的停止位 |

