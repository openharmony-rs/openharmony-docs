# @ohos.busManager.serial

串口管理

**起始版本：** 26.0.0

<!--Device-unnamed-declare namespace serial--><!--Device-unnamed-declare namespace serial-End-->

**系统能力：** SystemCapability.BusManager.Serial

## 导入模块

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getSerialPortList](arkts-basicservices-serial-getserialportlist-f.md#getserialportlist) | 获取串口列表。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addPortAuthorization](arkts-basicservices-serial-addportauthorization-f-sys.md#addportauthorization) | 添加应用访问串口端口的权限仅面向串口授权弹窗系统应用开放 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [SerialConfigs](arkts-basicservices-serial-serialconfigs-i.md) | 串口通信配置 |
| [SerialPort](arkts-basicservices-serial-serialport-i.md) | 串口对象，提供串口设备信息和通信相关能力 |
| [SerialPortInfo](arkts-basicservices-serial-serialportinfo-i.md) | 串口设备信息 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DataBits](arkts-basicservices-serial-databits-e.md) | 串口通信中的数据位 |
| [Parity](arkts-basicservices-serial-parity-e.md) | 串口通信中的校验位 |
| [StopBits](arkts-basicservices-serial-stopbits-e.md) | 串口通信中的停止位 |

