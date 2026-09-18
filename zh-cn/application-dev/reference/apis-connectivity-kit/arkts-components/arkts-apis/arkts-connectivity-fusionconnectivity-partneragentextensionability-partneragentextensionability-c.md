# PartnerAgentExtensionAbility

PartnerAgentExtensionAbility提供设备发现与扩展能力销毁的通知功能，本能力继承自[ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)，需要应用继承实现。

**继承/实现关系：** PartnerAgentExtensionAbility extends [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)

**起始版本：** 23

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

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

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core
