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

Defines the network type.

**System capability**: SystemCapability.Communication.NetManager.Core

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [connection.NetBearType](./js-apis-net-connection.md#netbeartype) | Network type.|

## policy.showAppNetPolicySettings<sup>22+</sup>

showAppNetPolicySettings(context: Context): Promise\<void>

Sets whether the current application can connect to the Wi-Fi or cellular network. You can call this API to open the network access settings page of the current application and set the network access permission of the application. This API uses a promise to return the result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Model restriction**: This API can be used only in the stage model.

**Device behavior differences**: This API can be called on phones, 2-in-1 devices, and tablets, but does not take effect on other devices.


**Parameters**

| **Name**| Type  | **Mandatory**| Description          |
| ------ | ------ | ---- | -------------- |
| context    | [Context](../apis-ability-kit/js-apis-inner-application-context.md) | Yes  | Application context of the stage model. (Only **UIAbilityContext** and **ExtensionContext** are supported.)|

**Return value**

| Type                                                   | Description                         |
| ------------------------------------------------------- | ----------------------------- |
| Promise\<void>  |Promise that returns no value.|

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

## policy.getNetAccessPolicy

getNetAccessPolicy(): Promise\<NetAccessPolicy>

Queries the network access policy of an application (whether cellular or Wi-Fi network access is allowed). You can check the policy by choosing **Settings** > **Mobile network** > **Manage data usage** > **Network access**. This API uses a promise to return the result.

**Since**: 26.0.0

**System capability**: SystemCapability.Communication.NetManager.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type                                                   | Description                         |
| ------------------------------------------------------- | ----------------------------- |
| Promise\<[NetAccessPolicy](#netaccesspolicy)>  |Promise used to return the network access policy of the application.|

**Error codes**:

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md).

| Error Code| Message                                    |
| --------- | -------------------------------------------- |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error, such as nullptr.    |


**Example:**
```ts
import { policy } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

policy.getNetAccessPolicy().then((policyInfo: policy.NetAccessPolicy) => {
  console.info(`getNetAccessPolicy success. WiFi: ${policyInfo.allowWiFi}, Cellular: ${policyInfo.allowCellular}`);
}).catch((err: BusinessError) => {
  console.error(`getNetAccessPolicy fail. error info: ${err.code} - ${err.message}`);
});
```


## NetAccessPolicy

Defines the network access policy information.

**Since**: 26.0.0

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name| Type  | Read-Only| Optional| Description|
| ------ | ------ | --- |---|------------------------- |
| allowWiFi    | boolean | No| No|Whether to allow Internet access over Wi-Fi.<br>**true**: yes;<br>**false**: no.|
| allowCellular  | boolean | No| No|Whether to allow Internet access over the cellular network.<br>**true**: yes.<br>**false**: no.|
