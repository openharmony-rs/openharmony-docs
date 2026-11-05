# PartnerAgentExtensionAbility

```TypeScript
export default declare class PartnerAgentExtensionAbility extends ExtensionAbility
```

PartnerAgentExtensionAbility提供设备发现与扩展能力销毁的通知功能，本能力继承自[ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)，需要应用继承实现。

**继承/实现关系：** PartnerAgentExtensionAbility extends [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)

**起始版本：** 23

<!--Device-unnamed-export default declare class PartnerAgentExtensionAbility extends ExtensionAbility--><!--Device-unnamed-export default declare class PartnerAgentExtensionAbility extends ExtensionAbility-End-->

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## ExtensionAbility使用限制

为保障系统安全性和稳定性，防止PartnerAgentExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

## 导入模块

```TypeScript
import { PartnerAgentExtensionAbility } from '@kit.ConnectivityKit';
```

## onDestroyWithReason

```TypeScript
onDestroyWithReason(reason: PartnerAgentExtensionAbilityDestroyReason): void
```

外设互通扩展能力被销毁时触发的方法回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartnerAgentExtensionAbility-onDestroyWithReason(reason: PartnerAgentExtensionAbilityDestroyReason): void--><!--Device-PartnerAgentExtensionAbility-onDestroyWithReason(reason: PartnerAgentExtensionAbilityDestroyReason): void-End-->

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | [PartnerAgentExtensionAbilityDestroyReason](arkts-connectivity-partneragentextensionabilitydestroyreason-t.md) | 是 | 通知销毁该外设互通扩展能力的原因。不同枚举值代表不同的销毁场景，应用可根据不同的销毁原因执行相应的资源释放或状态保存逻辑，枚举值的具体含义请参考[PartnerAgentExtensionAbilityDestroyReason](arkts-connectivity-partneragent-partneragentextensionabilitydestroyreason-e.md)。 |

**示例**

```TypeScript
export default class PartnerAgentExtAbility extends PartnerAgentExtensionAbility {
  onDestroyWithReason(reason: partnerAgent.PartnerAgentExtensionAbilityDestroyReason): void {
    console.info(`onDestroyWithReason is: ${reason}`);
  }
}
```

## onDeviceDiscovered

```TypeScript
onDeviceDiscovered(deviceAddress: PartnerDeviceAddress): void
```

当已注册的设备被发现时，系统会调用此回调方法。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartnerAgentExtensionAbility-onDeviceDiscovered(deviceAddress: PartnerDeviceAddress): void--><!--Device-PartnerAgentExtensionAbility-onDeviceDiscovered(deviceAddress: PartnerDeviceAddress): void-End-->

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceAddress | [PartnerDeviceAddress](arkts-connectivity-partnerdeviceaddress-t.md) | 是 | 应用注册的设备地址信息。应用需在PartnerDeviceAddress类型中设置bluetoothAddress选项。 |

**示例**

```TypeScript
export default class PartnerAgentExtAbility extends PartnerAgentExtensionAbility {
  onDeviceDiscovered(deviceAddress: partnerAgent.PartnerDeviceAddress): void {
    console.info(`onDeviceDiscovered success: ${deviceAddress.bluetoothAddress}`);
  }
}
```

## context

```TypeScript
context: PartnerAgentExtensionContext
```

PartnerAgentExtensionAbility的上下文。

**类型：** [PartnerAgentExtensionContext](arkts-connectivity-fusionconnectivity-partneragentextensioncontext-partneragentextensioncontext-c.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartnerAgentExtensionAbility-context: PartnerAgentExtensionContext--><!--Device-PartnerAgentExtensionAbility-context: PartnerAgentExtensionContext-End-->

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## 附录

PartnerAgentExtensionAbility不支持以下模块的引用。

| Kit | 模块 |
| --- | --- |
| Background Tasks Kit | [@ohos.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager.md) |
| Connectivity Kit | [@ohos.connectedTag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-connectedtag.md) |
| Background Tasks Kit | [@ohos.resourceschedule.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-backgroundtaskmanager.md) |
| Location Kit | [@ohos.geolocation](../../apis-location-kit/arkts-apis/arkts-location-geolocation.md) |
| Location Kit | [@ohos.geoLocationManager](../../apis-location-kit/arkts-apis/arkts-location-geolocationmanager.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Camera Kit | [@ohos.multimedia.cameraPicker](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camerapicker.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
| Media Library Kit | [multimedia.movingphotoview](../../apis-media-library-kit/arkts-apis/arkts-multimedia-movingphotoview.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-cardemulation.md) |
| Connectivity Kit | [@ohos.nfc.controller](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-controller.md) |
| Connectivity Kit | [@ohos.nfc.tag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-tag.md) |
| Connectivity Kit | [tagSession](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-tagsession.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Connectivity Kit | [@ohos.wifiext](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifiext.md) |
| Connectivity Kit | [@ohos.wifiManager](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanager.md) |
| Connectivity Kit | [@ohos.wifiManagerExt](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanagerext.md) |
