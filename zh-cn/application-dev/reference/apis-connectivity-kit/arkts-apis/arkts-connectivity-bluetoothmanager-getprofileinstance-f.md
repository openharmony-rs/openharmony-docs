# getProfileInstance

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## getProfileInstance

```TypeScript
function getProfileInstance(
    profileId: ProfileId
  ): A2dpSourceProfile | HandsFreeAudioGatewayProfile | HidHostProfile | PanProfile
```

通过ProfileId，获取profile的对象实例，API9新增了HidHostProfile，PanProfile。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| profileId | [ProfileId](arkts-connectivity-bluetoothmanager-profileid-e.md) | 是 | 表示profile的枚举值，例如：PROFILE_A2DP_SOURCE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [A2dpSourceProfile](arkts-connectivity-bluetoothmanager-a2dpsourceprofile-i.md) &#124; [HandsFreeAudioGatewayProfile](arkts-connectivity-bluetoothmanager-handsfreeaudiogatewayprofile-i.md) &#124; [HidHostProfile](arkts-connectivity-bluetoothmanager-hidhostprofile-i.md) &#124; [PanProfile](arkts-connectivity-bluetoothmanager-panprofile-i.md) | 对应的profile的对象实例，当前支持A2 dpSourceProfile/HandsFreeAudioGatewayProfile/HidHostProfile/PanProfile。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
try {
    let hidHost: bluetoothManager.HidHostProfile = bluetoothManager.getProfileInstance(bluetoothManager.ProfileId.PROFILE_HID_HOST);
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```
