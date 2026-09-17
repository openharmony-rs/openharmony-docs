# getProfileConnState

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getProfileConnState

```TypeScript
function getProfileConnState(profileId: ProfileId): ProfileConnectionState
```

依据ProfileId获取指定profile的连接状态。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getProfileConnectionState](arkts-connectivity-bluetoothmanager-getprofileconnectionstate-f.md)

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| profileId | [ProfileId](arkts-connectivity-bluetooth-profileid-e.md) | 是 | 表示profile的枚举值，例如：PROFILE_A2DP_SOURCE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ProfileConnectionState](arkts-connectivity-bluetooth-profileconnectionstate-e.md) | profile的连接状态。 |

**示例**

```TypeScript
let result : bluetooth.ProfileConnectionState = bluetooth.getProfileConnState(bluetooth.ProfileId.PROFILE_A2DP_SOURCE);
```
