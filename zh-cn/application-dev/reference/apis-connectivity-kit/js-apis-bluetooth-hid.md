# @ohos.bluetooth.hid (蓝牙hid模块)

hid模块提供了访问蓝牙hid相关功能的方法。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。



## 导入模块

```js
import { hid } from '@kit.ConnectivityKit';
```


## BaseProfile

type BaseProfile = baseProfile.BaseProfile

基础Profile接口定义。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| [baseProfile.BaseProfile](js-apis-bluetooth-baseProfile.md#ohosbluetoothbaseprofile-蓝牙baseprofile模块) | 基础Profile接口定义。 |


## BluetoothAddress<sup>23+</sup>

type BluetoothAddress = common.BluetoothAddress

描述蓝牙设备地址信息的参数结构，包括地址与地址类型。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 类型                  | 说明                  |
| ------------------- | ------------------- |
| [common.BluetoothAddress](js-apis-bluetooth-common.md#bluetoothaddress) | 蓝牙设备的地址信息。 |


## hid.createHidHostProfile

createHidHostProfile(): HidHostProfile

创建hid profile实例。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| HidHostProfile | 返回该profile的实例。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |


**示例：**

```js
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let hidHostProfile = hid.createHidHostProfile();
    console.info('hidHost success');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## hid.createHidDeviceProfile<sup>23+</sup>

createHidDeviceProfile(): HidDeviceProfile

创建蓝牙[HID Device](../../connectivity/terminology.md#hid-device)实例。通过该实例可使用本端作为HID Device的接口，如：获取和其他设备间的蓝牙HID连接状态。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| [HidDeviceProfile](#hiddeviceprofile23) | 返回HID Device实例。<br>- 该类继承于[BaseProfile](#baseprofile)，因此可以使用其父类中的方法。<br>- 和该实例角色相对应的是[HID Host](../../connectivity/terminology.md#hid-host)角色。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|801 | Capability not supported.          |

**示例：**

```js
try {
    let hidDeviceProfile = hid.createHidDeviceProfile();
    console.info('hidDevice success');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```


## HidDeviceProfile<sup>23+</sup>

该实例表示蓝牙HID通信中的[HID Device](../../connectivity/terminology.md#hid-device)角色。
- 该类继承于[BaseProfile](#baseprofile)，因此可以使用其父类中的方法。
- 使用该类的方法前，需通过[createHidDeviceProfile](#hidcreatehiddeviceprofile23)方法构造该类的实例。
- 通过该实例可以操作设备端的行为，如注册HID设备([registerHidDevice](#registerhiddevice23))，发送报告([sendReport](#sendreport23))等。
- 和该实例角色相对应的是[HID Host](../../connectivity/terminology.md#hid-host)。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23


## HidDeviceSdp<sup>23+</sup>

描述HID设备在服务发现协议([SDP](../../connectivity/terminology.md#sdp))中的服务注册配置。该结构定义了HID设备的身份标识、能力描述和协议特征，是HID主机发现、识别和连接HID设备的关键参数。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称      | 类型                  |只读   |可选   | 说明                                     |
| --------- | ----------------------- | ---- | ---- | ------------------------------ |
| name  |  string       | 否 | 否 | HID设备的名称，要求长度范围：[1, 50]，单位：Byte。    |
| description  | string | 否 | 否 | HID设备的描述信息，要求长度范围：[1, 50]，单位：Byte。  |
| provider  | string | 否 | 否 | 描述HID设备的制造商信息，要求长度范围：[1, 50]，单位：Byte。  |
| subclass  | [Subclass](#subclass23) | 否 | 否 | 表示HID设备具体类型。  |
| descriptors  | Uint8Array | 否 | 否 | 标识与蓝牙HID设备功能定义描述符。描述符会为每个支持的报告分配一个唯一的ID， 并详细定义该ID下报告的长度、结构与各字段含义。填写时需要遵循[USB HID](https://www.usb.org/hid)规范。  |

## HidDeviceQos<sup>23+</sup>

描述HID设备服务质量(Qos)参数。该结构定义了HID数据传输通道的流量控制、延迟保证和可靠性策略，用于优化蓝牙传输性能，确保设备的实时响应性。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称      | 类型                  |只读   |可选   | 说明                                     |
| --------- | ----------------------- | ---- | ---- | ------------------------------ |
| serviceType  |  [ServiceType](#servicetype23)   | 否 | 是 | 服务类型，默认为SERVICE_BEST_EFFORT。    |
| tokenRate  | number | 否 | 是 | 单位时间内允许传输的平均数据量，单位为Byte/s，默认为0，表示没有平均数据量限制。  |
| tokenBucketSize  | number | 否 | 是 | 允许短时间内超过tokenRate的最大数据量，默认为0，表示没有最大数据量限制。  |
| peakBandwidth  | number | 否 | 是 | 最大传输速率限制，单位为Byte/s，默认为0，表示没有传输速率限制。  |
| latency  | number | 否 | 是 | 最大允许延迟时间，单位为μs，默认为-1，表示没有延迟限制。  |
| delayVariation  | number | 否 | 是 | 允许的延迟波动范围，单位为μs，默认为-1，表示没有延迟波动范围限制。  |

## GetReportData<sup>23+</sup>

描述HID主机向HID设备发送的[GET_REPORT](../../connectivity/terminology.md#hid)传输请求事件的信息。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称       | 类型  | 只读 | 可选   | 说明      |
| -------- | ------ |---- |---- | ----------- |
| type | [ReportType](#reporttype23)   | 否 |  否    | 报告类型。 |
| id | number | 否 |  否    | 对应HID设备注册时通过[HidDeviceSdp](#hiddevicesdp23)提供的描述符中定义的报告ID，用于标识报告类型，对于不带ID的简单设备，此参数应设置为0。对于定义了多个报告ID的设备，此处应传入对应的ID值，该ID值必须与描述符中定义的值保持一致。 |
| bufferSize | number   | 否 |  否    | 收到数据的长度，单位为Byte。 |

## SetReportData<sup>23+</sup>

描述HID主机向HID设备发送的[SET_REPORT](../../connectivity/terminology.md#hid)传输请求事件的信息。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称       | 类型  | 只读 | 可选   | 说明          |
| -------- | ------ |---- |---- | ----------- |
| type | [ReportType](#reporttype23)   | 否 |  否    | 报告类型。 |
| id | number | 否 |  否    | 对应HID设备注册时通过[HidDeviceSdp](#hiddevicesdp23)提供的描述符中定义的报告ID，用于标识报告类型，对于不带ID的简单设备，此参数应设置为0。对于定义了多个报告ID的设备，此处应传入对应的ID值，该ID值必须与描述符中定义的值保持一致。 |
| data | Uint8Array   | 否 |  否    | 配置数据。其内容长度和解析方式必须严格匹配描述符中为该报告ID定义的格式。 |

## InterruptData<sup>23+</sup>

描述从主机收到的中断数据。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称       | 类型  | 只读 | 可选   | 说明          |
| -------- | ------ |---- |---- | ----------- |
| id | number | 否 |  否    | 对应HID设备注册时通过[HidDeviceSdp](#hiddevicesdp23)提供的描述符中定义的报告ID，用于标识报告类型，对于不带ID的简单设备，此参数应设置为0。对于定义了多个报告ID的设备，此处应传入对应的ID值，该ID值必须与描述符中定义的值保持一致。 |
| data | Uint8Array   | 否 |  否    | 中断数据。其内容长度和解析方式必须严格匹配HID设备注册时通过[HidDeviceSdp](#hiddevicesdp23)提供的描述符中为该报告ID定义的格式。 |

## ProtocolData<sup>23+</sup>

描述从HID主机接收的通信协议数据。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称       | 类型  | 只读 | 可选   | 说明          |
| -------- | ------ |---- |---- | ----------- |
| protocol | [ProtocolType](#protocoltype23)   | 否 |  否    | 主机的不同通信协议类型。 |

## Subclass<sup>23+</sup>

枚举，HID设备的具体类型。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称                      | 值   | 说明          |
| --------------------------| ----| --------------|
| SUBCLASS_UNCATEGORIZED    |  0  | 未分类HID设备。  |
| SUBCLASS_JOYSTICK         |  1  | 摇杆设备。       |
| SUBCLASS_GAMEPAD          |  2  | 游戏手柄设备。   |
| SUBCLASS_REMOTE_CONTROL   |  3  | 遥控器设备。     |
| SUBCLASS_SENSING_DEVICE   |  4  | 传感设备。       |
| SUBCLASS_DIGITIZER_TABLET |  5  | 数位板设备。     |
| SUBCLASS_CARD_READER      |  6  | 读卡器设备。     |
| SUBCLASS_KEYBOARD         | 64  | 标准键盘设备。   |
| SUBCLASS_MOUSE            | 128 | 标准鼠标设备。   |
| SUBCLASS_COMBO            | 192 | 组合输入设备。   |

## ReportType<sup>23+</sup>

枚举，报告类型。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称                | 值| 说明                    |
| --------------------| --| -----------------------|
| REPORT_TYPE_INPUT   | 1 | 输入报告，表示由本端向HID主机发送的数据。|
| REPORT_TYPE_OUTPUT  | 2 | 输出报告，表示HID这几向本端发送的数据。  |
| REPORT_TYPE_FEATURE | 3 | 特征报告，表示双向传输的配置数据。       |

## ServiceType<sup>23+</sup>

枚举，描述HID设备与主机之间连接的服务类型。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称                 | 值| 说明              |
| --------------------| --| ----------------- |
| SERVICE_NO_TRAFFIC  | 0 | 低功耗模式，仅维持连接，不传输应用数据，功耗最低。   |
| SERVICE_BEST_EFFORT | 1 | 高速模式，传输速率最快，但是数据包可能丢失或乱序，适用于对延迟敏感但对丢包不敏感的场景。   |
| SERVICE_GUARANTEED  | 2 | 可靠模式，传输速度稍慢，但是保证数据正确送达，适用于文件传输等场景。   |


## ErrorReason<sup>23+</sup>

枚举，描述错误原因。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称                   | 值 | 说明                  |
| -----------------------| --| --------------------- |
| RSP_SUCCESS            | 0 | 成功无异常。           |
| RSP_NOT_READY          | 1 | 设备未准备好处理请求。建议主机稍后重试。  |
| RSP_INVALID_REPORT_ID  | 2 | 无效的报告ID。建议主机确认当前支持的ID列表，并使用正确的ID重发消息。         |
| RSP_UNSUPPORTED_REQ    | 3 | 当前请求不支持，建议主机检查当前请求类型或报告类型是否在当前协议模式下被本端支持。       |
| RSP_INVALID_PARAM      | 4 | 无效参数。建议主机检查请求中的参数是否超出本端声明的范围或不符合报告描述符的定义。             |
| RSP_UNKNOWN            |14 | 未知错误原因。建议主机记录错误上下文并重试。         |

## ProtocolType<sup>23+</sup>

枚举，HID设备与主机的通信协议类型。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称                                | 值    | 说明              |
| ------------------------------------| ------| ---------------- |
| PROTOCOL_BOOT_MODE  | 0 |  兼容模式，确保设备在系统启动阶段和所有平台都能被识别为基本输入设备，兼容性最好但功能有限，适用于如键盘鼠标简单外设开发。  |
| PROTOCOL_REPORT_MODE | 1 | 完整的报告协议模式，允许设备使用完整的HID描述符和所有报告类型，适用于如游戏手柄、触摸屏等需要丰富功能与自定义数据格式的复杂外设。  |
