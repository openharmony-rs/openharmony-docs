# @ohos.FusionConnectivity.PartnerAgentExtensionAbility (支持设备状态通知的ExtensionAbility组件)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

PartnerAgentExtensionAbility是外设互通扩展能力的基础类，提供设备发现与设备下线的通知功能。，需要应用继承实现。应用模块级配置文件[module.json5](../../quick-start/module-configuration-file.md) 中的[extensionabilities](../../quick-start/module-configuration-file.md#extensionabilities标签)的type属性应该配置为partnerAgent。

> **说明：**
>
> - 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { PartnerAgentExtensionAbility, partnerAgent } from '@kit.ConnectivityKit';
```
## PartnerDeviceAddress

type PartnerDeviceAddress = partnerAgent.PartnerDeviceAddress

描述设备地址信息。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**： 此接口仅可在Stage模型下使用。

| 类型                  | 说明                  |
| ------------------- | ------------------- |
| [partnerAgent.PartnerDeviceAddress](js-apis-fusionConnectivity-partnerAgent.md#partneragentpartnerdeviceaddress) | 信息互通设备的地址信息。 |

## PartnerAgentExtensionAbilityDestroyReason

type PartnerAgentExtensionAbilityDestroyReason = partnerAgent.PartnerAgentExtensionAbilityDestroyReason

描述PartnerAgentExtensionAbility被销毁的原因。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**： 此接口仅可在Stage模型下使用。

| 类型                  | 说明                  |
| ------------------- | ------------------- |
| [partnerAgent.PartnerAgentExtensionAbilityDestroyReason](js-apis-fusionConnectivity-partnerAgent.md#partneragentpartneragentextensionabilitydestroyreason) | PartnerAgentExtensionAbility被销毁的原因。 |

## PartnerAgentExtensionAbility 
PartnerAgentExtensionAbility是外设互通扩展能力的基础类，提供设备发现与设备下线的通知功能，需要应用继承实现。本能力继承自[ExtensionAbility](../apis-ability-kit/js-apis-app-ability-extensionAbility.md)。

### 属性

**系统能力**： SystemCapability.Communication.FusionConnectivity.Core

**模型约束**： 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| context | [PartnerAgentExtensionContext](js-apis-fusionConnectivity-partnerAgentExtensionContext.md)  | 否 | 否 | PartnerAgentExtensionAbility的上下文。|

### onDestroyWithReason

onDestroyWithReason(reason: PartnerAgentExtensionAbilityDestroyReason): void

外设互通扩展能力被销毁时触发的方法回调。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**： 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| reason | [PartnerAgentExtensionAbilityDestroyReason](js-apis-fusionConnectivity-partnerAgent.md#partneragentpartneragentextensionabilitydestroyreason) | 是 | 通知销毁该应用的原因。 |

**示例：**

```ts
export default class PartnerAgentExtAbility extends PartnerAgentExtensionAbility {
  onDestroyWithReason(reason: partnerAgent.PartnerAgentExtensionAbilityDestroyReason): void {
    console.info(`onDestroyWithReason is: ${reason}`);
  }
}
```

### onDeviceDiscovered

onDeviceDiscovered(deviceAddress: PartnerDeviceAddress): void

当已注册的设备被发现时，系统会调用此回调方法。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**： 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| deviceAddress | [PartnerDeviceAddress](js-apis-fusionConnectivity-partnerAgent.md#partneragentpartnerdeviceaddress) | 是 | 应用注册的设备地址信息。<br>应用需在PartnerDeviceAddress类型中设置bluetoothAddress选项。 |

**示例：**

```ts
export default class PartnerAgentExtAbility extends PartnerAgentExtensionAbility {
  onDeviceDiscovered(deviceAddress: partnerAgent.PartnerDeviceAddress): void {
    console.info(`onDeviceDiscovered success: ${deviceAddress.bluetoothAddress}`);
  }
}
```