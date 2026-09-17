# getProfile

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getProfile

```TypeScript
function getProfile(profileId: ProfileId): A2dpSourceProfile | HandsFreeAudioGatewayProfile
```

通过ProfileId，获取profile的对象实例。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getProfileInstance](arkts-connectivity-bluetoothmanager-getprofileinstance-f.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| profileId | [ProfileId](arkts-connectivity-bluetooth-profileid-e.md) | 是 | 表示profile的枚举值，例如：PROFILE_A2DP_SOURCE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [A2dpSourceProfile](arkts-connectivity-bluetooth-a2dpsourceprofile-i.md) &#124; [HandsFreeAudioGatewayProfile](arkts-connectivity-bluetooth-handsfreeaudiogatewayprofile-i.md) | 对应的profile的对象实例，当前支持A2dpSourceProfile，HandsFreeAudioGatewayProfile。 |

**示例**

```TypeScript
let a2dpSrc : bluetooth.A2dpSourceProfile = bluetooth.getProfile(bluetooth.ProfileId.PROFILE_A2DP_SOURCE) as bluetooth.A2dpSourceProfile;
```
