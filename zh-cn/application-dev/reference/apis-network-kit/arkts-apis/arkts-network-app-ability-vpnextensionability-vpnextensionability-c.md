# VpnExtensionAbility

```TypeScript
export default class VpnExtensionAbility
```

VpnExtensionContext是VpnExtensionAbility的上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。

VpnExtensionContext可直接作为VpnExtension的上下文环境，提供允许访问特定于VpnExtensionAbility的资源的能力。

**起始版本：** 11

<!--Device-unnamed-export default class VpnExtensionAbility--><!--Device-unnamed-export default class VpnExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ExtensionAbility使用限制

为保障系统安全性和稳定性，防止VpnExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

## 导入模块

```TypeScript
import { VpnExtensionAbility, VpnExtensionContext } from '@kit.NetworkKit';
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

拓展VPN启动初始化的时候进行回调。

> **说明：** 
> 
> 建议配对调用[onDestroy](#ondestroy)监听拓展VPN的销毁，及时执行资源清理等操作。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VpnExtensionAbility-onCreate(want: Want): void--><!--Device-VpnExtensionAbility-onCreate(want: Want): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 指示要启动的信息。 |

**示例**

```TypeScript
import { VpnExtensionAbility } from '@kit.NetworkKit';
import { Want } from '@kit.AbilityKit';

class MyVpnExtAbility extends VpnExtensionAbility {
    onCreate(want: Want) {
       console.info('MyVpnExtAbility onCreate');
    }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

拓展VPN销毁之前进行回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VpnExtensionAbility-onDestroy(): void--><!--Device-VpnExtensionAbility-onDestroy(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

```TypeScript
import { VpnExtensionAbility } from '@kit.NetworkKit';

class MyVpnExtAbility extends VpnExtensionAbility {
    onDestroy() {
       console.info('MyVpnExtAbility onDestroy');
    }
}
```

## context

```TypeScript
context: VpnExtensionContext
```

指定context。

**类型：** [VpnExtensionContext](arkts-network-vpnextensioncontext-c.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VpnExtensionAbility-context: VpnExtensionContext--><!--Device-VpnExtensionAbility-context: VpnExtensionContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 附录

VpnExtensionAbility不支持以下模块的引用。

| Kit | 模块 |
| --- | --- |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
| Location Kit | [@ohos.geolocation](../../apis-location-kit/arkts-apis/arkts-location-geolocation.md) |
| Location Kit | [@ohos.geoLocationManager](../../apis-location-kit/arkts-apis/arkts-location-geolocationmanager.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| Telephony Kit | [@ohos.telephony.call](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
