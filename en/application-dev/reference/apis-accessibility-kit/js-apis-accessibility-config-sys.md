# @ohos.accessibility.config (System Accessibility Configuration) (System API)

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=16a51cad246d07c6caba5c76444e9d073c5d43d6 translatedAt=2026-08-03T09:38:49.906Z pushedAt=2026-08-04T07:47:02.104Z -->

The **accessibility.config** module provides APIs for configuring system accessibility features, including accessibility extension, high-contrast text, mouse buttons, and captions.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module are system APIs.

## Modules to Import

```ts
import { config } from '@kit.AccessibilityKit';
```

## Properties

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                                | Type                                                                                    | Read-Only| Optional| Description                        |
|------------------------------------|--------------------------------------------------------------------------------------------| -------- | -------- |-----------------------------------------------------------|
| highContrastText                   | [Config](#config)\<boolean>                                                                | No| No| Whether to enable high-contrast text. The value **true** indicates that high-contrast text is enabled, and **false** indicates the opposite.<br>Default value: **false**                                          |
| invertColor                        | [Config](#config)\<boolean>                                                                | No| No| Whether to enable color inversion. The value **true** indicates that color inversion is enabled, and **false** indicates the opposite.<br>Default value: **false**                                            |
| daltonizationState<sup>11+</sup>   | [Config](#config)\<boolean>                                                                | No | No | Indicates the color correction feature status. Used together with daltonizationColorFilter. The value **true** indicates that color correction is enabled, and **false** indicates that it is disabled. The default value is **false**.                |
| daltonizationColorFilter           | [Config](#config)&lt;[DaltonizationColorFilter](#daltonizationcolorfilter)&gt;             | No | No | Indicates the color correction filter configuration. Used together with daltonizationState. This configuration takes effect only when daltonizationState is set to **true**. The default value is Normal, indicating the standard type.                                               |
| contentTimeout                     | [Config](#config)\<number>                                                                 | No | No | Indicates the content display suggested duration configuration, which is used to set the duration for which accessibility prompts and other content remain displayed on the screen. The value ranges from 0 to 5000, in milliseconds. The default value is **0**.                             |
| animationOff                       | [Config](#config)\<boolean>                                                                | No| No| Whether to disable animation. The value **true** indicates that animation is disabled, and **false** indicates the opposite.<br>Default value: **false**                                            |
| brightnessDiscount                 | [Config](#config)\<number>                                                                 | No | No | Indicates the brightness discount configuration, which is used to proportionally adjust the screen display brightness. The value ranges from 0 to 1.0, where **0** indicates no brightness discount (original brightness) and **1.0** indicates the maximum brightness discount. The default value is **0.0**.                                      |
| mouseKey                           | [Config](#config)\<boolean>                                                                | No| No| Whether to enable the mouse button. The value **true** indicates that the mouse button is enabled, and **false** indicates the opposite. <br>Default value: **false**                                             |
| mouseAutoClick                     | [Config](#config)\<number>                                                                 | No | No | Indicates the configuration for the mouse auto-click operation. The value ranges from 0 to 5000, in milliseconds. **0** indicates that the feature is disabled, and other values indicate the duration of mouse hovering that triggers the auto-click operation. The default value is **0**.                |
| shortkey                           | [Config](#config)\<boolean>                                                                | No | No | Indicates the accessibility extension shortcut key feature status. Used together with shortkeyTarget. The value **true** indicates that the accessibility extension shortcut key feature is enabled, and **false** indicates that it is disabled. The default value is **false**.                                          |
| shortkeyTarget                     | [Config](#config)\<string>                                                                 | No | No | Indicates the target configuration of the accessibility extension shortcut key. The value is the name of the accessibility extension app, in the format 'bundleName/abilityName'. If the format is incorrect or the name is invalid, the setting does not take effect.   |
| captions                           | [Config](#config)\<boolean>                                                                | No| No| Whether to enable captions. The value **true** indicates that caption is enabled, and **false** indicates the opposite.<br>Default value: **false**                                            |
| captionsStyle                      | [Config](#config)\<[accessibility.CaptionsStyle](js-apis-accessibility.md#captionsstyle8)> | No | No | Indicates the configuration of the caption style.                                                |
| audioMono<sup>10+</sup>            | [Config](#config)\<boolean>                                                                | No | No | Indicates the mono audio feature status. The value **true** indicates that the mono audio feature is enabled, and **false** indicates that it is disabled. The default value is **false**.                                            |
| audioBalance<sup>10+</sup>         | [Config](#config)\<number>                                                                 | No | No | Indicates the configuration for left and right channel volume balance. **-1.0** indicates output from the left channel only; **0.0** indicates balanced output from both channels; **1.0** indicates output from the right channel only. Intermediate values represent a linear ratio of the left and right channel volumes. The value ranges from -1.0 to 1.0. The default value is **0.0**.                                |
| shortkeyMultiTargets<sup>11+</sup> | [Config](#config)&lt;Array&lt;string&gt;&gt;                                                    | No | No | Indicates the multi-target list configuration of the accessibility extension shortcut key. The value is the name of the accessibility extension app, in the format ['bundleName/abilityName']. If the format is incorrect or the name is invalid, the setting does not take effect. |
| clickResponseTime<sup>11+</sup>    | [Config](#config)&lt;[ClickResponseTime](#clickresponsetime11)&gt;                         | No| No| Length of time required for a click.                                            |
| ignoreRepeatClick<sup>11+</sup>    | [Config](#config)\<boolean>                                                                | No| No| Whether to ignore repeated clicks. This parameter must be used together with **repeatClickInterval**. The value **true** indicates that the feature of ignoring repeated clicks is enabled, and **false** indicates the opposite.<br>Default value: **false**                  |
| repeatClickInterval<sup>11+</sup>  | [Config](#config)&lt;[RepeatClickInterval](#repeatclickinterval11)&gt;                     | No | No | Indicates the configuration for the interval of ignoring repeated clicks. Used together with ignoreRepeatClick. This configuration takes effect only when ignoreRepeatClick is set to **true**. The default value is Shortest, indicating the shortest interval.                                             |

## config.enableAbility

enableAbility(name: string, capability: Array&lt;accessibility.Capability&gt;): Promise&lt;void&gt;

Enables an accessibility extension. This API must be used together with [config.disableAbility](#configdisableability). This API uses a promise to return the result.

Compared with [config.enableAbilityWithCallback](#configenableabilitywithcallback23), this API only enables the accessibility extension without listening for connection state changes. To listen for disconnection events of the accessibility extension, use [config.enableAbilityWithCallback](#configenableabilitywithcallback23).

**System API**: This is a system API.

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type                                                                          | Mandatory| Description|
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| name | string | Yes | Name of the accessibility extension app, in the format of 'bundleName/abilityName'. |
| capability | Array&lt;[accessibility.Capability](js-apis-accessibility.md#capability)&gt; | Yes | Capability attributes of the accessibility extension app. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300001 | Invalid bundle name or ability name.  |
| 9300002 | Target ability already enabled. |

**Example**

```ts
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';
let capability: accessibility.Capability[] = ['retrieve'];

config.enableAbility(name, capability).then(() => {
  console.info(`Succeeded in enabling ability, name is ${name}, capability is ${capability}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to enable ability. Code: ${err.code}, message: ${err.message}`);
});
```

## config.enableAbility

enableAbility(name: string, capability: Array&lt;accessibility.Capability&gt;, callback: AsyncCallback&lt;void&gt;): void

Enables an accessibility extension. This API must be used together with [config.disableAbility](#configdisableability). This API uses an asynchronous callback to return the result.

Compared with [config.enableAbilityWithCallback](#configenableabilitywithcallback23), this API only enables the accessibility extension without listening for connection state changes. To listen for disconnection events of the accessibility extension, use [config.enableAbilityWithCallback](#configenableabilitywithcallback23).

**System API**: This is a system API.

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type                                                                             | Mandatory| Description|
| -------- |---------------------------------------------------------------------------------| -------- | -------- |
| name | string | Yes | Name of the accessibility extension app, in the format of 'bundleName/abilityName'. |
| capability | Array&lt;[accessibility.Capability](js-apis-accessibility.md#capability)&gt; | Yes | Capability attribute of the accessibility extension app. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the accessibility extension is enabled successfully, **err** is undefined; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300001 | Invalid bundle name or ability name.  |
| 9300002 | Target ability already enabled. |

**Example**

```ts
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';
let capability: accessibility.Capability[] = ['retrieve'];

config.enableAbility(name, capability, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to enable ability. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in enabling ability, name is ${name}, capability is ${capability}`); 
});
```

## config.enableAbilityWithCallback<sup>23+</sup>

enableAbilityWithCallback(name: string, capability: Array&lt;accessibility.Capability&gt;, connectCallback: ConnectCallback): Promise&lt;void&gt;

Enables an accessibility extension and specifies [ConnectCallback](#connectcallback23) as the callback for disconnection events of the accessibility extension. This API uses a promise to return the result.

When the accessibility extension process is abnormally disconnected, the onDisconnect callback of ConnectCallback will be triggered. This API must be used together with [config.disableAbility](#configdisableability).

**System API**: This is a system API.

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                                          | Mandatory| Description|
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| name | string                                                                       | Yes| Name of the accessibility extension ability, in the format of **'*bundleName*/*abilityName*'**.|
| capability | Array&lt;[accessibility.Capability](js-apis-accessibility.md#capability)&gt; | Yes| Capabilities of the auxiliary extension ability.|
| connectCallback | [ConnectCallback](#connectcallback23)                             | Yes | Callback invoked when an accessibility extension app is disconnected, used to listen for disconnection events of the accessibility extension. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300001 | Invalid bundle name or ability name.  |
| 9300002 | Target ability already enabled. |

**Example**

```ts
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';
let capability: accessibility.Capability[] = ['retrieve'];
let connectCallback: config.ConnectCallback = {
  onDisconnect: () => {
    console.info(`Ability is disconnected.`);
  }
};

config.enableAbilityWithCallback(name, capability, connectCallback).then(() => {
  console.info(`Succeeded in enabling ability, name is ${name}, capability is ${capability}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to enable ability. Code: ${err.code}, message: ${err.message}`);
});
```

## config.disableAbility

disableAbility(name: string): Promise&lt;void&gt;

Disables an accessibility extension. This API must be used together with [config.enableAbility](#configenableability) or [config.enableAbilityWithCallback](#configenableabilitywithcallback23). This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes | Name of the accessibility extension application, in the format 'bundleName/abilityName'. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300001 | Invalid bundle name or ability name.  |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';

config.disableAbility(name).then(() => {
  console.info(`Succeeded in disabling ability, name is ${name}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to disable ability. Code: ${err.code}, message: ${err.message}`);
});
```

## config.disableAbility

disableAbility(name: string, callback: AsyncCallback&lt;void&gt;): void

Disables an accessibility extension. This API must be used together with [config.enableAbility](#configenableability) or [config.enableAbilityWithCallback](#configenableabilitywithcallback23). This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes | Name of the accessibility extension app, in the format of 'bundleName/abilityName'. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the accessibility extension is disabled successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 9300001 | Invalid bundle name or ability name.  |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';

config.disableAbility(name, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to disable ability. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in disabling, name is ${name}`);
});
```

## config.on('enabledAccessibilityExtensionListChange')

on(type: 'enabledAccessibilityExtensionListChange', callback: Callback&lt;void&gt;): void

Adds a listener for changes in the list of enabled accessibility extensions. This API uses an asynchronous callback to return the result.

This API must be used together with [config.off('enabledAccessibilityExtensionListChange')](#configoffenabledaccessibilityextensionlistchange). Call off to unregister the listener when it is no longer needed to avoid resource leaks.

**System API**: This is a system API.

**Required permissions:** ohos.permission.READ_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes | The parameter is fixed to 'enabledAccessibilityExtensionListChange', which specifies the event type for listening to the list change of enabled accessibility extensions. |
| callback | Callback&lt;void&gt; | Yes| Callback invoked when the list of enabled accessibility extension abilities changes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';

config.on('enabledAccessibilityExtensionListChange', () => {
  console.info('subscribe enabled accessibility extension list change state success');
});
```

## config.off('enabledAccessibilityExtensionListChange')

off(type: 'enabledAccessibilityExtensionListChange', callback?: Callback&lt;void&gt;): void

Cancels the listener for changes in the list of enabled accessibility extensions. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions:** ohos.permission.READ_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes | The parameter is fixed to 'enabledAccessibilityExtensionListChange', specifying that the event type to unsubscribe from is the change of the enabled accessibility extension list. |
| callback | Callback&lt;void&gt; | No| Callback function used to cancel the event response of the specified callback object. The value must be the same as the value of **callback** in **on('enabledAccessibilityExtensionListChange')**. If this parameter is not specified, all registered events will be unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';

let callback = () => {
  console.info('subscribe enabled accessibility extension list change state success');
};
config.on('enabledAccessibilityExtensionListChange', callback);
config.off('enabledAccessibilityExtensionListChange', callback);
```

## config.on('installedAccessibilityListChange')<sup>12+</sup>

on(type: 'installedAccessibilityListChange', callback: Callback&lt;void&gt;): void

Adds a listener for changes in the list of installed accessibility extensions. This API uses an asynchronous callback to return the result.

This API must be used together with [config.off('installedAccessibilityListChange')](#configoffinstalledaccessibilitylistchange12). Call off to unregister the listener when it is no longer needed to avoid resource leaks.

**System API**: This is a system API.

**Required permissions:** ohos.permission.READ_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Listening type. The value is fixed at **'installedAccessibilityListChange'**, indicating listening for changes in the list of installed accessibility extension abilities.|
| callback | Callback&lt;void&gt; | Yes| Callback invoked when the list of installed accessibility extension abilities changes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';

config.on('installedAccessibilityListChange', () => {
  console.info('subscribe installed accessibility extension list change state success');
});
```

## config.off('installedAccessibilityListChange')<sup>12+</sup>

off(type: 'installedAccessibilityListChange', callback?: Callback&lt;void&gt;): void

Cancels the listener for changes in the list of installed accessibility extensions. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions:** ohos.permission.READ_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes | The value is fixed at 'installedAccessibilityListChange', which specifies that the event type to unsubscribe from is changes in the list of installed accessibility extensions. |
| callback | Callback&lt;void&gt; | No| Callback function used to cancel the event response of the specified callback object. The value must be the same as the value of **callback** in **on('installedAccessibilityListChange')**. If this parameter is not specified, all registered events will be unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';

let callback = () => {
  console.info('subscribe installed accessibility extension list change state success');
};
config.on('installedAccessibilityListChange', callback);
config.off('installedAccessibilityListChange', callback);
```

## config.setMagnificationState<sup>20+</sup>

setMagnificationState(state: boolean): void

Sets the enabled state of the magnification effect. The magnification effect depends on the magnification gesture feature. This API takes effect only when the magnification gesture feature is enabled.

**System API**: This is a system API.

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| state | boolean | Yes | Indicates the enabled state of the magnification effect.<br>- **true**: indicates that the magnification effect is enabled.<br>- **false**: indicates that the magnification effect is disabled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 9300007  | Trigger magnification failed. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  config.setMagnificationState(true);
} catch (err) {
  let e = err as BusinessError;
  console.error(`Failed to set magnification. Code: ${e.code}, message: ${e.message}`);
}
```

## config.setSeniorModeStateForApp

setSeniorModeStateForApp(appSeniorModeInfos: Array&lt;AppSeniorModeInfo&gt;): Promise&lt;void&gt;

Sets the senior mode state for an app. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type                                                                           | Mandatory | Description |
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| appSeniorModeInfos | Array&lt;[AppSeniorModeInfo](#appseniormodeinfo)&gt; | Yes | Senior mode state information of the app to modify. Each object in the array contains three properties: bundleName, appIndex, and seniorModeState. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300000 | System abnormality.  |
| 9300008 | The appIndex is invalid. Possible causes: 1. The appIndex is out of the valid range. 2. The application corresponding to the appIndex does not exist. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let infos: config.AppSeniorModeInfo[] = [{
  bundleName: 'com.example.myapplication',
  appIndex: 0,
  seniorModeState: true
}];

config.setSeniorModeStateForApp(infos).then(() => {
  console.info(`Succeeded in setting seniorModeState for App.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set seniorModeState for app. Code: ${err.code}, message: ${err.message}`);
});
```

## config.getSeniorModeStateForApp

getSeniorModeStateForApp(bundleName: string, appIndex?: number): Promise&lt;boolean&gt;

Queries the senior mode state of an app. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.READ_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type                                                                           | Mandatory | Description |
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| bundleName | string | Yes | Bundle name of the app whose senior mode state is to be queried. |
| appIndex | number | No | Clone index of the app bundle.<br>Value range: an integer greater than or equal to 0. If not specified, the default value is **0**. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the senior mode is enabled for the app, and **false** indicates that the senior mode is not enabled for the app.|

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300000 | System abnormality.  |
| 9300008 | The appIndex is invalid. Possible causes: 1. The appIndex is out of the valid range. 2. The application corresponding to the appIndex does not exist. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

config.getSeniorModeStateForApp('com.example.myapplication', 0).then((data: boolean) => {
  console.info(`Succeeded in getting seniorModeState for app, data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get seniorModeState for app. Code: ${err.code}, message: ${err.message}`);
});
```

## config.onSeniorModeStateChangeForApp

onSeniorModeStateChangeForApp(callback: Callback&lt;AppSeniorModeInfo&gt;): void

Listens for senior mode state change events of all apps. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - The callback parameter for registration should use a named function instead of an anonymous function, otherwise a new underlying object will be created each time it is called, causing memory leaks.
> - After calling this method, be sure to use [config.offSeniorModeStateChangeForApp](#configoffseniormodestatechangeforapp) to cancel the listener before the component instance is destroyed (for example, in the aboutToDisappear lifecycle), otherwise crashes may occur.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name   | Type                    | Mandatory | Description                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[AppSeniorModeInfo](#appseniormodeinfo)&gt; | Yes | Callback invoked to return the modified senior mode information of the app.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.|
| 202 | Permission verification failed. A non-system application calls a system API.|

**Example**

```ts
import { config } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback = (data: config.AppSeniorModeInfo) => {
    console.info(`callback data, name: ${data.bundleName}, appIndex: ${data.appIndex}, seniorModeState: ${data.seniorModeState}`);
  }

  aboutToAppear(): void {
    config.onSeniorModeStateChangeForApp(this.callback);
  }

  aboutToDisappear(): void {
    config.offSeniorModeStateChangeForApp(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## config.offSeniorModeStateChangeForApp

offSeniorModeStateChangeForApp(callback?: Callback\<AppSeniorModeInfo>): void

Cancels the listener for senior mode state change events of all apps. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.READ_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name   | Type                    | Mandatory | Description                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[AppSeniorModeInfo](#appseniormodeinfo)&gt; | No   | Callback function used to cancel the event response of the specified callback object. The value must be the same as the value of **callback** in [config.onSeniorModeStateChangeForApp](#configonseniormodestatechangeforapp). If this parameter is not specified, all registered events will be unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback = (data: config.AppSeniorModeInfo) => {
    console.info(`callback data, name: ${data.bundleName}, appIndex: ${data.appIndex}, seniorModeState: ${data.seniorModeState}`);
  }

  aboutToAppear(): void {
    config.onSeniorModeStateChangeForApp(this.callback);
  }

  aboutToDisappear(): void {
    config.offSeniorModeStateChangeForApp(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## config.startBlinking

startBlinking(mode: BlinkingMode, scenario: BlinkingScenario): BlinkResultCode

Enables the flash or screen for blinking reminders.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type                                                                           | Mandatory | Description |
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| mode | [BlinkingMode](#blinkingmode) | Yes | Blinking mode, indicating screen blinking or flash blinking. |
| scenario | [BlinkingScenario](#blinkingscenario) | Yes | Scenario that triggers blinking. |

**Return value**

| Type | Description |
| -------- | -------- |
| [BlinkResultCode](#blinkresultcode) | Result code returned by the API call.|

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300000 | System abnormality. Possible causes: <br>1. Internal operation failed. <br>2. Failed to obtain the required service or client object (null pointer).<br>3. IPC communication failed. <br>4. Failed to obtain the accessibility service proxy.|

**Example**

```ts
import { config } from '@kit.AccessibilityKit';

try {
  let code: config.BlinkResultCode = config.startBlinking(config.BlinkingMode.SINGLE_BLINK, config.BlinkingScenario.ALARM);
  console.info(`Succeeded in startBlinking, result code: ${code}`);
} catch (err) {
  console.error(`Failed to call startBlinking, code is ${err.code}, message is ${err.message}`);
}
```

## config.stopBlinking

stopBlinking(mode: BlinkingMode, scenario: BlinkingScenario): BlinkResultCode

Stops flash blinking or screen blinking.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type                                                                           | Mandatory | Description |
| -------- |------------------------------------------------------------------------------| -------- | -------- |
| mode | [BlinkingMode](#blinkingmode) | Yes | Blinking mode, indicating screen blinking or flash blinking. |
| scenario | [BlinkingScenario](#blinkingscenario) | Yes | Scenario that triggers blinking. |

**Return value**

| Type | Description |
| -------- | -------- |
| [BlinkResultCode](#blinkresultcode) | Result code returned by the API call.|

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Accessibility Error Codes](errorcode-accessibility.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 9300000 | System abnormality. Possible causes: <br>1. Internal operation failed. <br>2. Failed to obtain the required service or client object (null pointer).<br>3. IPC communication failed. <br>4. Failed to obtain the accessibility service proxy.|

**Example**

```ts
import { config } from '@kit.AccessibilityKit';

try {
  let code: config.BlinkResultCode = config.stopBlinking(config.BlinkingMode.SINGLE_BLINK, config.BlinkingScenario.ALARM);
  console.info(`Succeeded in stopBlinking, result code: ${code}`);
} catch (err) {
  console.error(`Failed to call stopBlinking, code is ${err.code}, message is ${err.message}`);
}
```

## Config

Implements configuration, acquisition, and listening for properties.

### set

set(value: T): Promise&lt;void&gt;

Sets the value of a property. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes | Attribute value to set. The value type is consistent with the type of the corresponding Config attribute. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let value: boolean = true;

config.highContrastText.set(value).then(() => {
  console.info(`succeeded in setting highContrastText value is ${value}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set highContrastText. Code: ${err.code}, message: ${err.message}`);
});
```

### set

set(value: T, callback: AsyncCallback&lt;void&gt;): void

Sets the property value. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes | Attribute value to set. The value type is the same as that of the corresponding Config attribute. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let value: boolean = true;

config.highContrastText.set(value, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set highContrastText. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in setting highContrastText, value is ${value}`);
});
```

### get

get(): Promise&lt;T&gt;

Obtains the value of a property. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;T&gt; | Promise used to return the value obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

config.highContrastText.get().then((data: boolean) => {
  console.info(`succeeded in getting highContrastText, data is ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get highContrastText. Code: ${err.code}, message: ${err.message}`);
});
```

### get

get(callback: AsyncCallback&lt;T&gt;): void

Obtains the property value. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;T&gt; | Yes | Callback used to return the result. If the attribute is obtained successfully, **err** is **undefined** and **data** is the attribute value; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

config.highContrastText.get((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`Failed to get highContrastText. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting highContrastText, data is ${data}`);
});
```

### on

on(callback: Callback&lt;T&gt;): void

Adds a listener for property changes. This API uses an asynchronous callback to return the result.

This API must be used together with [off](#off). Call off to unregister the listener when it is no longer needed to avoid resource leaks.

**System API**: This is a system API.

**Required permissions:** ohos.permission.READ_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;T&gt; | Yes| Callback invoked when the property changes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';

config.highContrastText.on((data: boolean) => {
  console.info(`subscribe highContrastText success, result: ${JSON.stringify(data)}`);
});
```

### off

off(callback?: Callback&lt;T&gt;): void

Cancels the listener for property changes. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions:** ohos.permission.READ_ACCESSIBILITY_CONFIG

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;T&gt; | No| Callback used to unregister. The value must be the same as the value of **callback** in **on()**. If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201  | Permission verification failed. The application does not have the permission required to call the API.  |
| 202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import { config } from '@kit.AccessibilityKit';

let callback = (data: boolean) => {
  console.info(`subscribe highContrastText success, result: ${JSON.stringify(data)}`);
};
config.highContrastText.on(callback);
config.highContrastText.off(callback);
```

## ConnectCallback<sup>23+</sup>

Callback provided when enabling an accessibility extension app through the [config.enableAbilityWithCallback](#configenableabilitywithcallback23) API. The callback is invoked when the connection to the accessibility extension app is disconnected.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Model restriction**: This API can be used only in the stage model.

| Name         | Type                                         | Read Only | Optional | Description                                     |
| ------------ | -------------------------------------------- | ---- | ---- | ---------------------------------------- |
| onDisconnect | [OnDisconnectCallback](#ondisconnectcallback23) | No   | No   | Callback invoked when the connection to the accessibility extension app is disconnected. |

## OnDisconnectCallback<sup>23+</sup>

type OnDisconnectCallback = () => void

Describes the callback to be invoked when the connection to **AccessibilityExtensionAbility** is disconnected.

**System API:** This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Model restriction:** This API can be used only in the stage model.

## DaltonizationColorFilter

Color correction filters for different types of color vision deficiency.

The configuration takes effect when the daltonization feature is enabled ([daltonizationState](#properties) is set to **true**). When the daltonization feature is disabled ([daltonizationState](#properties) is set to **false**), the standard type is displayed.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name| Description|
| -------- | -------- |
| Normal | Standard color vision.|
| Protanomaly | Red-weak color vision deficiency. |
| Deuteranomaly | Green-weak color vision deficiency. |
| Tritanomaly  | Blue-weak color vision deficiency. |

## ClickResponseTime<sup>11+</sup>

Click duration of different lengths.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name         | Description        |
|-------------|------------|
| Short       | Indicates short (default).  |
| Medium      | Medium.      |
| Long        | Long.      |

## RepeatClickInterval<sup>11+</sup>

Ignore repeated clicks at different time intervals.

The configuration takes effect when the ignore repeated click feature is enabled ([ignoreRepeatClick](#properties) is set to **true**). When the ignore repeated click feature is disabled ([ignoreRepeatClick](#properties) is set to **false**), the configuration does not take effect.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name      | Description   |
|----------|-------|
| Shortest | Shortest.|
| Short    | Short. |
| Medium   | Medium. |
| Long     | Long. |
| Longest  | Longest.|

## AppSeniorModeInfo

Senior mode state information of an app.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name         | Type                                         | Read Only | Optional | Description                                     |
| ------------ | -------------------------------------------- | ---- | ---- | ---------------------------------------- |
| bundleName | string | No   | No   | Bundle name of the app, used to identify the app, in the format of **'com.example.myapplication'**. |
| appIndex | number | No   | Yes   | Clone index of the app bundle. The value is an integer greater than or equal to 0. If not specified, the default value is **0**.|
| seniorModeState | boolean | No   | No   | Senior mode enabled state of the app. The value **true** indicates enabled, and **false** indicates disabled.|

## BlinkingMode

Enumerates the blinking modes.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                        | Value   | Description                     |
| -------------------------- | ---- | ------------------------ |
| SINGLE_BLINK                       |  1 | Single blink.         |
| CONTINUOUS_BLINK                |  2 | Continuous blink.         |

## BlinkingScenario

Enumerates the blinking scenarios.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                        | Value   | Description                     |
| -------------------------- | ---- | ------------------------ |
| ALARM                       |  1 | Blinking triggered by an alarm.         |
| NOTIFICATION                |  2 | Blinking triggered by a notification.         |
| CALL                        |  3 | Blinking triggered by an incoming call.         |
| TESTING                     |  4 | Blinking triggered by a test scenario.     |

## BlinkResultCode

Enumerates the result codes of blinking operations.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                        | Value   | Description                     |
| -------------------------- | ---- | ------------------------ |
| SUCCESS                         |  0 | The blinking API is executed successfully.          |
| ALREADY_FLASHING                |  1 | The device is already blinking.       |
| DEVICE_IN_USE                   |  2 | The device is in use.     |
| FLASH_BLINKING_UNSUPPORTED      |  3 | The device does not support flash blinking.   |
| SCREEN_BLINKING_UNSUPPORTED     |  4 | The device does not support screen blinking.     |
| FEATURE_DISABLED                |  5 | The blinking feature is not enabled. |