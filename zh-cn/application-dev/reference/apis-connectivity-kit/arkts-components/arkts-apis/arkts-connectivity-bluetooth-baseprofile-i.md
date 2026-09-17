# BaseProfile

profile基类。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [BaseProfile](arkts-connectivity-bluetoothmanager-baseprofile-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getConnectionDevices

```TypeScript
getConnectionDevices(): Array<string>
```

获取已连接设备列表。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getConnectionDevices](arkts-connectivity-bluetoothmanager-baseprofile-i.md#getconnectiondevices)

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回已连接设备的地址列表。 |

**示例**

```TypeScript
let a2dpSrc : bluetooth.A2dpSourceProfile = bluetooth.getProfile(bluetooth.ProfileId.PROFILE_A2DP_SOURCE) as bluetooth.A2dpSourceProfile;
let retArray : Array<string> = a2dpSrc.getConnectionDevices();
```

## getDeviceState

```TypeScript
getDeviceState(device: string): ProfileConnectionState
```

获取设备profile的连接状态。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getDeviceState](arkts-connectivity-bluetoothmanager-baseprofile-i.md#getdevicestate)

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | string | 是 | 远端设备地址。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ProfileConnectionState](arkts-connectivity-bluetooth-profileconnectionstate-e.md) | 返回profile的连接状态。 |

**示例**

```TypeScript
let a2dpSrc : bluetooth.A2dpSourceProfile = bluetooth.getProfile(bluetooth.ProfileId.PROFILE_A2DP_SOURCE) as bluetooth.A2dpSourceProfile;
let ret : bluetooth.ProfileConnectionState = a2dpSrc.getDeviceState('XX:XX:XX:XX:XX:XX');
```
