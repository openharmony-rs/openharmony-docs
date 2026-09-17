# A2dpSinkProfile

管理a2dp sink业务。

**继承/实现关系：** A2dpSinkProfile extends [BaseProfile](arkts-connectivity-a2dp-baseprofile-t.md)

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { a2dp } from '@kit.ConnectivityKit';
```

## connect

```TypeScript
connect(deviceId: string): void
```

向远端设备发起A2DP sink连接。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID。例如，“11:22:33:AA:BB:FF”。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Internal system error. For example, IPC error. Detailed error messages can be used to assist in locating the problem. |
| 2904000 | The a2dp sink service is not running. |
| 2904002 | The connection is rejected due to the connection policy. For example connection limit restrictions. |

## disconnect

```TypeScript
disconnect(deviceId: string): void
```

断开与远端设备的A2DP sink连接。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID。例如，“11:22:33:AA:BB:FF”。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Internal system error. For example, IPC error. Detailed error messages can be used to assist in locating the problem. |
| 2904000 | The a2dp sink service is not running. |

## getPlayingState

```TypeScript
getPlayingState(deviceId: string): PlayingState
```

获取设备播放状态。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID。例如，“11:22:33:AA:BB:FF”。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PlayingState](arkts-connectivity-a2dp-playingstate-e.md) | 返回播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Internal system error. For example, IPC error. Detailed error messages can be used to assist in locating the problem. |
| 2904001 | The a2dp sink not connected. |
