# @ohos.enterprise.browser (Browser Management)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima; @weizai16-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=48705cd83be49ad2e9cc7b69c4b522c4d41e00e4 translatedAt=2026-11-03T04:58:00.299Z pushedAt=2026-11-03T12:08:25.521Z nl=1 -->

The **browser** module provides browser management, including setting, canceling, and obtaining browser policies. It is applicable to scenarios such as enterprise device management, employee online behavior management, and security compliance audit.

Browser policies are a collection of rules and settings that govern how a browser behaves, ensuring security, compliance, performance optimization, and a consistent user experience.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see [MDM Kit Development](../../mdm/mdm-kit-guide.md).

## Modules to Import

```ts
import { browser } from '@kit.MDMKit';
```

## browser.setPolicySync

setPolicySync(admin: Want, appId: string, policyName: string, policyValue: string): void

Sets a browser policy for a specified browser based on **appId**. This API is applicable to scenarios where an enterprise manages employees' browser behavior in a unified manner.<!--RP1--><!--RP1End-->The policy takes effect automatically after being set.

> **NOTE**
>
> In a multi-MDM application scenario, the same policy of the same browser application is [exclusive](../../mdm/mdm-kit-multi-mdm.md#rule-2-policy-exclusivity); different browsers and different policies of the same browser are [merged](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging).

**Required permissions**: ohos.permission.ENTERPRISE_SET_BROWSER_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description                                                        |
| ----------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin       | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| appId       | string                                                  | Yes  | Application ID, which uniquely identifies an application. This ID is used to specify the browser. For details, see [What Is appid](../../quick-start/common-problem-of-application.md#what-is-appid).                                                               |
| policyName  | string                                                  | Yes   | Browser policy name, agreed upon by the API caller and the specified browser. <!--RP2--><!--RP2End--><br/>The meanings of the value combinations of policyName and policyValue are as follows:<br/>- policyName is not an empty string and policyValue is an empty string: cancels the policy with the policy name corresponding to the browser of the application appId.<br/>- Both policyName and policyValue are empty strings: cancels all policies set through this API for the browser corresponding to the application appId. |
| policyValue | string                                                  | Yes   | Browser policy value, agreed upon by the API caller and the specified browser.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { browser } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Replace the value of appId with the specified application ID of the browser.
let appId: string = 'com.example.******_******/******5t5CoBM=';
// Browser policy name. Replace it with the actual browser policy name.
let policyName: string = 'InsecurePrivateNetworkRequestsAllowed';
// Browser policy value. Replace it with the actual browser policy value.
let policyValue: string = '{"level":"mandatory","scope":"machine","source":"platform","value":true}';

try {
  browser.setPolicySync(wantTemp, appId, policyName, policyValue);
  console.info('Succeeded in setting browser policies.');
} catch (err) {
  console.error(`Failed to set browser policies. Code is ${err.code}, message is ${err.message}`);
}
```

## browser.getPoliciesSync

getPoliciesSync(admin: Want, appId: string): string

Obtains the policy set for a specified browser through [browser.setPolicySync](#browsersetpolicysync) based on **appId**. This API is applicable to scenarios where the current browser policy configuration needs to be queried, for example, displaying policy details and verifying whether a policy is effective in a device management application.

This API queries the policy set by the corresponding enterprise device management application by passing in **Want**. To query the policy that actually takes effect, use the [browser.getPoliciesSync](#browsergetpoliciessync-1) API.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Parameter Name | Type                                                    | Mandatory | Description                     |
| ------ | ------------------------------------------------------- | ---- | ------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Enterprise device management extension component. The **Want** must contain the **abilityName** of the enterprise device management extension capability and the **bundleName** of the application where it resides.|
| appId  | string                                                  | Yes   | Application ID, used to specify the browser. For details, see [What Is appId](../../quick-start/common-problem-of-application.md#what-is-appid). |

**Return value**

| Type   | Description         |
| ------ | ------------ |
| string | Browser policy. |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { browser } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it based on the actual situation.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Replace the value of the appId parameter with the application ID of the browser specified by the developer.
let appId: string = 'com.example.******_******/******5t5CoBM=';

try {
  let result: string = browser.getPoliciesSync(wantTemp, appId);
  console.info(`Succeeded in getting browser policies, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get browser policies. Code is ${err.code}, message is ${err.message}`);
}
```


## browser.getPoliciesSync

getPoliciesSync(admin: Want | null, appId: string): string

Obtains, by appId, the policy set for a specified browser through [browser.setPolicySync](#browsersetpolicysync). This API is applicable to scenarios where the current browser policy configuration needs to be queried, for example, displaying policy details in a device management application and verifying whether the policy takes effect.

**Since:** 26.0.0

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                    |
| ------ | ------------------------------------------------------- | ---- | ------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Required   | Enterprise device management extension component. The Want must contain the abilityName of the enterprise device management extension capability and the bundleName of the application where it resides.<br>When multiple MDM applications exist on the device, passing Want queries the policy set by the corresponding enterprise device management application, and passing null queries the policy that actually takes effect.|
| appId  | string                                                  | Yes  | Application ID, which is used to specify the browser. For details, see [What is appId?](../../quick-start/common-problem-of-application.md#what-is-appid).|

**Return value**

| Type  | Description        |
| ------ | ------------ |
| string | Browser policy obtained.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { browser } from '@kit.MDMKit';

// Replace the value of appId with the specified application ID of the browser.
let appId: string = 'com.example.******_******/******5t5CoBM=';

try {
  // Replace the parameters based on the actual situation.
  let result: string = browser.getPoliciesSync(null, appId);
  console.info(`Succeeded in getting browser policies, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get browser policies. Code is ${err.code}, message is ${err.message}`);
}
```
## browser.setManagedBrowserPolicy<sup>15+</sup>

setManagedBrowserPolicy(admin: Want, bundleName: string, policyName: string, policyValue: string): void

Sets a browser policy for a specified browser. This API is applicable to scenarios where an enterprise needs to manage employees' browser behavior in a unified manner, such as configuring browser security policies. After the setting is successful, the system common event [COMMON_EVENT_MANAGED_BROWSER_POLICY_CHANGED](../apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_managed_browser_policy_changed) is released.

> **NOTE**
>
> The browser policy set through this API requires adaptation by the browser. The corresponding browser needs to listen for the [COMMON_EVENT_MANAGED_BROWSER_POLICY_CHANGED](../apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_managed_browser_policy_changed) common event and call [browser.getSelfManagedBrowserPolicyVersion](#browsergetselfmanagedbrowserpolicyversion15) to check whether the browser policy version has changed. If the version has changed, the browser calls [browser.getSelfManagedBrowserPolicy](#browsergetselfmanagedbrowserpolicy15) to obtain the latest browser policy and updates the browser policy configuration by itself.
>
> In multi-MDM application scenarios, once a policy for a specific browser is configured and takes effect by the first admin, it can no longer be configured by other admins.
>
> In multi-MDM application scenarios, the same policy of the same browser application is [exclusive](../../mdm/mdm-kit-multi-mdm.md#rule-2-policy-exclusivity); policies of different browsers and different policies of the same browser are [merged](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging).

**Required permissions**: ohos.permission.ENTERPRISE_SET_BROWSER_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description                                                        |
| ----------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin       | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| bundleName  | string                                                  | Yes  | Application bundle name, which is used to specify the browser. It uniquely identifies an application.                                    |
| policyName  | string                                                  | Yes   | Name of the browser policy, agreed upon by the API caller and the specified browser. <!--RP2--><!--RP2End--> |
| policyValue | string                                                  | Yes  | Browser policy value. If the value is an empty string, the policy corresponding to the policy name is removed.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { browser } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
// Browser application bundle name.
let bundleName: string = 'com.example.testbrowser';
// Browser policy name.
let policyName: string = 'InsecurePrivateNetworkRequestsAllowed';
// Browser policy value.
let policyValue: string = '{"level":"mandatory","scope":"machine","source":"platform","value":true}';

try {
  browser.setManagedBrowserPolicy(wantTemp, bundleName, policyName, policyValue);
  console.info('Succeeded in setting managed browser policy.');
} catch (err) {
  console.error(`Failed to set managed browser policy. Code is ${err.code}, message is ${err.message}`);
}
```

## browser.getManagedBrowserPolicy<sup>15+</sup>

getManagedBrowserPolicy(admin: Want, bundleName: string): ArrayBuffer

Obtains, by application bundle name, the browser policy set for a specified browser through [browser.setManagedBrowserPolicy](#browsersetmanagedbrowserpolicy15). This API is applicable to scenarios where the current browser policy configuration needs to be queried, for example, displaying policy details in a device management application and verifying whether the policy takes effect.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description                    |
| ----------- | ------------------------------------------------------- | ---- | ------------------------ |
| admin       | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.          |
| bundleName  | string                                                  | Yes  | Application bundle name, which is used to specify the browser.|

**Return value**

| Type       | Description        |
| ----------- | ------------ |
| ArrayBuffer | Browser policy obtained.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { browser } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { util } from '@kit.ArkTS';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleName: string = 'com.example.testbrowser';

try {
  let buffer: ArrayBuffer = browser.getManagedBrowserPolicy(wantTemp, bundleName);
  let intBuffer: Uint8Array = new Uint8Array(buffer);
  let decoder: util.TextDecoder = util.TextDecoder.create('utf-8');
  let stringData: string = decoder.decodeToString(intBuffer);
  console.info(`Succeeded in getting managed browser policy, result : ${stringData}`);
} catch (err) {
  console.error(`Failed to get managed browser policy. Code is ${err.code}, message is ${err.message}`);
}
```

## browser.getSelfManagedBrowserPolicyVersion<sup>15+</sup>

getSelfManagedBrowserPolicyVersion(): string

Obtains the browser policy version of the current device. This API is applicable to scenarios where a browser checks whether the policy version has changed, and is used together with [browser.getSelfManagedBrowserPolicy](#browsergetselfmanagedbrowserpolicy15) to update the browser policy configuration.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description        |
| ------ | ------------ |
| string | Browser policy version.|

**Example**

```ts
import { browser } from '@kit.MDMKit';

try {
  let version: string = browser.getSelfManagedBrowserPolicyVersion();
  console.info(`Succeeded in getting self managed browser policy version, result : ${version}`);
} catch (err) {
  console.error(`Failed to get self managed browser policy version. Code is ${err.code}, message is ${err.message}`);
}
```

## browser.getSelfManagedBrowserPolicy<sup>15+</sup>

getSelfManagedBrowserPolicy(): ArrayBuffer

Obtains the browser policy of the current device. This API is applicable to scenarios where a browser queries the browser policy set through [browser.setManagedBrowserPolicy](#browsersetmanagedbrowserpolicy15), and the browser can update its own browser policy configuration based on the query result.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type       | Description        |
| ----------- | ------------ |
| ArrayBuffer | Browser policy obtained.|

**Example**

```ts
import { browser } from '@kit.MDMKit';
import { util } from '@kit.ArkTS';

try {
  let buffer: ArrayBuffer = browser.getSelfManagedBrowserPolicy();
  let intBuffer: Uint8Array = new Uint8Array(buffer);
  let decoder: util.TextDecoder = util.TextDecoder.create('utf-8');
  let stringData: string = decoder.decodeToString(intBuffer);
  console.info(`Succeeded in getting self managed browser policy, result : ${stringData}`);
} catch (err) {
  console.error(`Failed to get self managed browser policy. Code is ${err.code}, message is ${err.message}`);
}
```