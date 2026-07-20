# RemoteDevice

远程设备操作方法。

**起始版本：** 26.0.0

<!--Device-remoteDevice-interface RemoteDevice--><!--Device-remoteDevice-interface RemoteDevice-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

<a id="getacbstate"></a>
## getAcbState

```TypeScript
getAcbState(): AcbState
```

获取ACB连接状态。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-getAcbState(): AcbState--><!--Device-RemoteDevice-getAcbState(): AcbState-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AcbState](arkts-connectivity-nearlinkconstant-acbstate-e.md) | 返回ACB连接状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

<a id="getconnectionstate"></a>
## getConnectionState

```TypeScript
getConnectionState(): ConnectionState
```

获取profile连接状态。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-getConnectionState(): ConnectionState--><!--Device-RemoteDevice-getConnectionState(): ConnectionState-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ConnectionState](arkts-connectivity-remotedevice-connectionstate-t.md) | 返回连接状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

<a id="getdeviceclass"></a>
## getDeviceClass

```TypeScript
getDeviceClass(): DeviceClass
```

获取星闪设备的类型。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-getDeviceClass(): DeviceClass--><!--Device-RemoteDevice-getDeviceClass(): DeviceClass-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DeviceClass](arkts-connectivity-nearlinkconstant-deviceclass-e.md) | 星闪设备的类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

<a id="getdeviceinformation"></a>
## getDeviceInformation

```TypeScript
getDeviceInformation(): DeviceInformation
```

获取远端设备信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-getDeviceInformation(): DeviceInformation--><!--Device-RemoteDevice-getDeviceInformation(): DeviceInformation-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DeviceInformation](arkts-connectivity-remotedevice-deviceinformation-i.md) | 返回远端设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

<a id="getdevicename"></a>
## getDeviceName

```TypeScript
getDeviceName(): string
```

获取星闪设备的名称。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-getDeviceName(): string--><!--Device-RemoteDevice-getDeviceName(): string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回设备名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

<a id="getpairingstate"></a>
## getPairingState

```TypeScript
getPairingState(): PairingState
```

获取配对状态。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-getPairingState(): PairingState--><!--Device-RemoteDevice-getPairingState(): PairingState-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PairingState](arkts-connectivity-remotedevice-pairingstate-t.md) | 返回配对状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

<a id="startpairing"></a>
## startPairing

```TypeScript
startPairing(): Promise<void>
```

启动与远端星闪设备的配对。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-startPairing(): Promise<void>--><!--Device-RemoteDevice-startPairing(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

