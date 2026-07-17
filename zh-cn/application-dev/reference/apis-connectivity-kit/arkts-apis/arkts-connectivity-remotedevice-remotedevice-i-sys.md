# RemoteDevice

远程设备操作方法。

**起始版本：** 26.0.0

<!--Device-remoteDevice-interface RemoteDevice--><!--Device-remoteDevice-interface RemoteDevice-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## cancelDevicePairing

```TypeScript
cancelDevicePairing(): Promise<void>
```

取消正在进行的配对请求。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-cancelDevicePairing(): Promise<void>--><!--Device-RemoteDevice-cancelDevicePairing(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100099 | Operation failed. |

## connect

```TypeScript
connect(): Promise<void>
```

连接所有允许的profile。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-connect(): Promise<void>--><!--Device-RemoteDevice-connect(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 将profile连接结果作为Promise返回。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100099 | Operation failed. |

## disconnect

```TypeScript
disconnect(): Promise<void>
```

断开所有已连接的profile。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-disconnect(): Promise<void>--><!--Device-RemoteDevice-disconnect(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 将profile连接结果作为Promise返回。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100099 | Operation failed. |

## getDeviceAlias

```TypeScript
getDeviceAlias(): string
```

获取远程设备的别名。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-getDeviceAlias(): string--><!--Device-RemoteDevice-getDeviceAlias(): string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回远程设备的别名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100099 | Operation failed. |

## getDeviceModel

```TypeScript
getDeviceModel(): DeviceModel
```

获取远端设备的型号信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-getDeviceModel(): DeviceModel--><!--Device-RemoteDevice-getDeviceModel(): DeviceModel-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DeviceModel](arkts-connectivity-remotedevice-devicemodel-i-sys.md) | 返回远程设备的型号信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100099 | Operation failed. |

## getRssiValue

```TypeScript
getRssiValue(): Promise<number>
```

获取远程设备的RSSI值。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-getRssiValue(): Promise<int>--><!--Device-RemoteDevice-getRssiValue(): Promise<int>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | 返回RSSI值的promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100099 | Operation failed. |

## removePairedDevice

```TypeScript
removePairedDevice(): Promise<void>
```

删除已配对的远端设备。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-removePairedDevice(): Promise<void>--><!--Device-RemoteDevice-removePairedDevice(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100099 | Operation failed. |

## setConnectionInterval

```TypeScript
setConnectionInterval(interval: ConnectionInterval): void
```

设置与远端设备的连接时间间隔。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-setConnectionInterval(interval: ConnectionInterval): void--><!--Device-RemoteDevice-setConnectionInterval(interval: ConnectionInterval): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interval | [ConnectionInterval](arkts-connectivity-remotedevice-connectioninterval-t-sys.md) | 是 | 要设置的连接间隔 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100099 | Operation failed. |

## setDeviceAlias

```TypeScript
setDeviceAlias(alias: string): void
```

设置远端设备的别名。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-setDeviceAlias(alias: string): void--><!--Device-RemoteDevice-setDeviceAlias(alias: string): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alias | string | 是 | 远端设备的别名<br>最大长度为64且不能为空。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100046 | String exceeds maximum length. |
| 36100099 | Operation failed. |

## setPairingConfirmation

```TypeScript
setPairingConfirmation(accept: boolean): void
```

设置配对请求的确认信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-setPairingConfirmation(accept: boolean): void--><!--Device-RemoteDevice-setPairingConfirmation(accept: boolean): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accept | boolean | 是 | 如果配对请求被接受，则设置为true。否则，设置为false |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100099 | Operation failed. |

## setPairingPasscode

```TypeScript
setPairingPasscode(passcode: string): Promise<void>
```

如果配对类型为通行码，配对时设置通行码

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-setPairingPasscode(passcode: string): Promise<void>--><!--Device-RemoteDevice-setPairingPasscode(passcode: string): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| passcode | string | 是 | 用户输入的通行码。必须是6位数字<br>长度必须为6，6个10以内数字。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100045 | Passcode must be a 6-digit number. |
| 36100099 | Operation failed. |

## startCrediblePairing

```TypeScript
startCrediblePairing(): Promise<void>
```

发起与可信的远端星闪设备的配对。该接口不触发对话框，不需要用户授权。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoteDevice-startCrediblePairing(): Promise<void>--><!--Device-RemoteDevice-startCrediblePairing(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100099 | Operation failed. |

