# @ohos.busManager.serial

本模块提供串口通信管理功能，适用于需要与串口设备进行数据交互的场景，如工业控制、传感器数据采集、嵌入式设备通信等。支持获取串口设备列表、 打开和关闭串口、读写数据、硬件流控信号管理等功能，帮助开发者便捷地实现与外部串口设备的通信，提高设备互联效率。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

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
| [getSerialPortList](arkts-basicservices-serial-getserialportlist-f.md) | 查询串口设备列表，返回[SerialPort](arkts-basicservices-serial-serialport-i.md)对象数组。使用Promise异步回调。用于需要识别可用串口设备的场景，如工业设备连接、物联网设备管理、嵌入式系统调试等场景。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addPortAuthorization](arkts-basicservices-serial-addportauthorization-f-sys.md) | 添加应用访问串口的权限。此函数通过将应用的Token ID与串口设备ID关联，建立应用的串口访问权限关系。适用于系统管理类应用为第三方应用授予串口访问权限的场景，如设备管理工具为工业数据采集应用分配串口权限。 仅用于会弹出串口授权弹窗的系统应用，在用户授权后，权限信息将持久化存储。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [SerialConfigs](arkts-basicservices-serial-serialconfigs-i.md) | 串口通信配置参数。 |
| [SerialPort](arkts-basicservices-serial-serialport-i.md) | 串口对象，提供串口设备的信息和通信能力。 |
| [SerialPortInfo](arkts-basicservices-serial-serialportinfo-i.md) | 串口设备信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DataBits](arkts-basicservices-serial-databits-e.md) | 表示数据位的枚举。 |
| [Parity](arkts-basicservices-serial-parity-e.md) | 表示校验位的枚举。 |
| [StopBits](arkts-basicservices-serial-stopbits-e.md) | 表示停止位的枚举。 |

