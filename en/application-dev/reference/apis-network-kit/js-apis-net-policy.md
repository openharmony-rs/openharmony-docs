# @ohos.net.policy (Network Policy Management)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

The **policy** module provides APIs for managing network policies, which allow you to use firewall technology to control and manage the data traffic used.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { policy } from '@kit.NetworkKit';
```

## NetBearType

type NetBearType = connection.NetBearType

Network type.

**System capability**: SystemCapability.Communication.NetManager.Core

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [connection.NetBearType](./js-apis-net-connection.md#netbeartype) | Network type.|

## policy.showAppNetPolicySettings<sup>22+</sup>

showAppNetPolicySettings(context: Context): Promise\<void>

This API is used to set whether the current application can connect to the Wi-Fi or cellular network. You can call this API to open the network connection settings screen of the current app and set the network connection permission of the application. This API uses a promise to return the result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Model restriction**: This API can be used only in the stage model.

**Device behavior differences**: This API can be called on phones, 2-in-1 devices, and tablets, but does not take effect on other devices.


**Parameters**

| **Name**| Type  | **Mandatory**| Description          |
| ------ | ------ | ---- | -------------- |
| context    | [Context](../apis-ability-kit/js-apis-inner-application-context.md) | Yes  | Application context of the stage model. (Only UIAbilityContext and ExtensionContext are supported.)|

**Return value**

| Type                                                   | Description                         |
| ------------------------------------------------------- | ----------------------------- |
| Promise\<void>  |Promise used to return the result. Promise that returns no value.|

**Example:**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
import { policy } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
policy.showAppNetPolicySettings(context).then(() => {
    console.info("showAppNetPolicySettings success");
}).catch(() => {
    console.error("showAppNetPolicySettings failed");
    }
)
```
