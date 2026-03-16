# @ohos.FusionConnectivity.PartnerAgentExtensionAbility (ExtensionAbility Component Supporting Device Status Notifications)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

As the base class of the peripheral interconnection extension capability, **PartnerAgentExtensionAbility** provides the device discovery and device offline notification features. This class needs to be inherited by the application. The **type** attribute of [extensionAbilities](../../quick-start/module-configuration-file.md#extensionabilities) in the module-level configuration file [module.json5](../../quick-start/module-configuration-file.md) must be set to **partnerAgent**.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { PartnerAgentExtensionAbility, partnerAgent } from '@kit.ConnectivityKit';
```
## PartnerDeviceAddress

type PartnerDeviceAddress = partnerAgent.PartnerDeviceAddress

Describes the device address information.

**System capability**: SystemCapability.Communication.FusionConnectivity.Core

**Model restriction**: This API can be used only in the stage model.

| **Type**                 | **Description**                 |
| ------------------- | ------------------- |
| [partnerAgent.PartnerDeviceAddress](js-apis-fusionConnectivity-partnerAgent.md#partneragentpartnerdeviceaddress) | Address of the device to be interconnected.|

## PartnerAgentExtensionAbilityDestroyReason

type PartnerAgentExtensionAbilityDestroyReason = partnerAgent.PartnerAgentExtensionAbilityDestroyReason

Describes the reason why **PartnerAgentExtensionAbility** is destroyed.

**System capability**: SystemCapability.Communication.FusionConnectivity.Core

**Model restriction**: This API can be used only in the stage model.

| **Type**                 | **Description**                 |
| ------------------- | ------------------- |
| [partnerAgent.PartnerAgentExtensionAbilityDestroyReason](js-apis-fusionConnectivity-partnerAgent.md#partneragentpartneragentextensionabilitydestroyreason) | Reason why **PartnerAgentExtensionAbility** is destroyed.|

## PartnerAgentExtensionAbility 
As the base class of the peripheral interconnection extension capability, **PartnerAgentExtensionAbility** provides the device discovery and device offline notification features. This class needs to be inherited by the application. It is inherited from [ExtensionAbility](../apis-ability-kit/js-apis-app-ability-extensionAbility.md).

### Attribute

**System capability**: SystemCapability.Communication.FusionConnectivity.Core

**Model restriction**: This API can be used only in the stage model.

| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| -------- | -------- | -------- | -------- | -------- |
| context | [PartnerAgentExtensionContext](js-apis-fusionConnectivity-partnerAgentExtensionContext.md)  | No| No| Context of **PartnerAgentExtensionAbility**.|

### onDestroyWithReason

onDestroyWithReason(reason: PartnerAgentExtensionAbilityDestroyReason): void

Called when the peripheral interconnection extension capability is destroyed.

**System capability**: SystemCapability.Communication.FusionConnectivity.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| reason | [PartnerAgentExtensionAbilityDestroyReason](js-apis-fusionConnectivity-partnerAgent.md#partneragentpartneragentextensionabilitydestroyreason) | Yes| Destruction reason.|

**Example**

```ts
export default class PartnerAgentExtAbility extends PartnerAgentExtensionAbility {
  onDestroyWithReason(reason: partnerAgent.PartnerAgentExtensionAbilityDestroyReason): void {
    console.info(`onDestroyWithReason is: ${reason}`);
  }
}
```

### onDeviceDiscovered

onDeviceDiscovered(deviceAddress: PartnerDeviceAddress): void

Called when a registered device is discovered.

**System capability**: SystemCapability.Communication.FusionConnectivity.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| deviceAddress | [PartnerDeviceAddress](js-apis-fusionConnectivity-partnerAgent.md#partneragentpartnerdeviceaddress) | Yes| Address information of the device registered by the application.<br>The application must be configured with the **bluetoothAddress** option of the **PartnerDeviceAddress** type.|

**Example**

```ts
export default class PartnerAgentExtAbility extends PartnerAgentExtensionAbility {
  onDeviceDiscovered(deviceAddress: partnerAgent.PartnerDeviceAddress): void {
    console.info(`onDeviceDiscovered success: ${deviceAddress.bluetoothAddress}`);
  }
}
```
