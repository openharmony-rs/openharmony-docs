# @ohos.enterprise.browser (Browser Management)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima; @weizai16-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=5a568794ad7ad869a67daecc62f8915341ba0a9a translatedAt=2026-11-04T01:36:38.685Z pushedAt=2026-11-04T03:24:28.504Z nl=1 -->

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

Sets a browser sub-policy for a specified browser. This API is applicable to scenarios where an enterprise needs to manage employees' browser behavior in a unified manner.<!--RP1--><!--RP1End-->

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
| policyName  | string                                                  | Yes  | Browser sub-policy name, which is agreed upon by the API caller and the specified browser. If the value is an empty string, the browser policy corresponding to **appId** is to be set.|
| policyValue | string                                                  | Yes  | Browser sub-policy value, which is agreed upon by the API caller and the specified browser. If the value is an empty string, the policy corresponding to the policy name is removed.|

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
  // Replace it based on the actual situation.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Replace the value of the appId parameter with the application ID of the browser specified by the developer.
let appId: string = 'com.example.******_******/******5t5CoBM=';
// Browser policy name.
let policyName: string = 'InsecurePrivateNetworkRequestsAllowed';
// Browser policy value.
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

Obtains the policy set for a specified browser by appId. This API is applicable to scenarios where the current browser policy configuration is queried, for example, displaying policy details in an enterprise device management application and verifying whether a policy takes effect.<!--RP1--><!--RP1End-->

This API queries the policy set by the corresponding enterprise device management application by passing in **Want**. To query the policy that actually takes effect, use the [browser.getPoliciesSync](#browsergetpoliciessync-1) API.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type                                                    | Mandatory | Description                     |
| ------ | ------------------------------------------------------- | ---- | ------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| appId  | string                                                  | Yes   | Application ID, used to specify the browser. For details, see [What Is appId](../../quick-start/common-problem-of-application.md#what-is-appid). |

**Return value**

| Type   | Description         |
| ------ | ------------ |
| string | Browser policy. |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
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

try {
  let result: string = browser.getPoliciesSync(wantTemp, appId);
  console.info(`Succeeded in getting browser policies, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get browser policies. Code is ${err.code}, message is ${err.message}`);
}
```


## browser.getPoliciesSync

getPoliciesSync(admin: Want | null, appId: string): string

Obtains the policy set for a specified browser based on **appid**. This API is applicable to scenarios where the current browser policy configuration needs to be queried, for example, displaying policy details in an enterprise device administrator application and verifying whether a policy has taken effect.<!--RP1--><!--RP1End-->

**Since**: 26.0.0

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                    |
| ------ | ------------------------------------------------------- | ---- | ------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Mandatory   | Enterprise device management extension component. The Want must contain the abilityName of the Enterprise Device Management Extension Ability and the bundleName of the host application.<br>When multiple MDM applications exist on the device, passing Want queries the policy set by the corresponding enterprise device management application, and passing null queries the policy that actually takes effect.|
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
> In a multi-MDM application scenario, for the same policy of the same browser, once it is configured and takes effect by the first Admin, other Admins cannot configure it.
>
> In a multi-MDM application scenario, the same policy of the same browser application is [exclusive](../../mdm/mdm-kit-multi-mdm.md#rule-2-policy-exclusivity); policies of different browsers and different policies of the same browser are [merged](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging).

**Required permissions**: ohos.permission.ENTERPRISE_SET_BROWSER_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description                                                        |
| ----------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin       | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| bundleName  | string                                                  | Yes  | Application bundle name, which is used to specify the browser. It uniquely identifies an application.                                    |
| policyName  | string                                                  | Yes  | Browser policy name, which is agreed upon by the API caller and the specified browser.|
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

Obtains the policy of a specified browser based on the application bundle name. This API is applicable to scenarios where the current browser policy configuration needs to be queried, for example, displaying policy details in an enterprise device administrator application and verifying whether a policy has taken effect.

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

Obtains the browser policy version of the current device.

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

Obtains the browser policy of the current device.

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