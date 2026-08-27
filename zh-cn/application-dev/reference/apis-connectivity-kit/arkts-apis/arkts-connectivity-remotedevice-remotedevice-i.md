# RemoteDevice

提供远端设备的操作方法，使用前需要使用[remoteDevice.createRemoteDevice](arkts-connectivity-remotedevice-createremotedevice-f.md)方法创建一个远端设备 [RemoteDevice](#remotedevice)实例。一个设备只需要创建一次，无需多次创建。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## getAcbState

```TypeScript
getAcbState(): AcbState
```

获取和远端设备的逻辑链路连接状态。适用于需要确认逻辑链路是否就绪的场景，如在进行数据传输或消息通信前检查逻辑链路状态。与 [getConnectionState](#getconnectionstate)获取设备层级连接状态不同，本接口获取逻辑链路（ACB）层级的连接状态。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AcbState | 和远端设备的逻辑链路连接状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## getConnectionState

```TypeScript
getConnectionState(): ConnectionState
```

获取本端设备和远端设备的连接状态。与[getAcbState](#getacbstate)获取逻辑链路（ACB）层级连接状态不同，本接口获取设备层级的连接状态。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ConnectionState | 本端设备和远端设备的连接状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## getDeviceClass

```TypeScript
getDeviceClass(): DeviceClass
```

获取远端设备类型。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DeviceClass | 远端设备类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## getDeviceInformation

```TypeScript
getDeviceInformation(): DeviceInformation
```

获取远端设备的设备信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DeviceInformation](arkts-connectivity-remotedevice-deviceinformation-i.md) | 远端设备的设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## getDeviceName

```TypeScript
getDeviceName(): string
```

获取远端设备名称。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 远端设备名称。最大长度为30个字符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## getPairingState

```TypeScript
getPairingState(): PairingState
```

获取和远端设备的配对状态。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PairingState | 和远端设备的配对状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## startPairing

```TypeScript
startPairing(): Promise<void>
```

发起与远端设备的配对。使用Promise异步回调。发起配对后，将依据本端与远端设备的输入输出能力标识（即设备是否具备显示、键盘输入等能力）弹出不同类型的弹窗，需使用者进一步确认。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
