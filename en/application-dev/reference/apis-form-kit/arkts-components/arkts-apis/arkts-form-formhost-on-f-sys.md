# on (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## on("formUninstall")

```TypeScript
function on(type: "formUninstall", callback: Callback<string>): void
```

Subscribes to widget uninstall events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Widget uninstall is different from widget removal. When an application is uninstalled, the corresponding widget
> is automatically uninstalled.

**Since:** 9

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | "formUninstall" | Yes | Event type. The value **"formUninstall"** indicates a widget uninstall event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | Yes | Callback used to return the widget ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |


## on('formOverflow')

```TypeScript
function on(type: 'formOverflow', callback: Callback<formInfo.OverflowRequest>): void
```

Subscribes to the interactive widget animation request event. This API uses an asynchronous callback to return the result.

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'formOverflow' | Yes | Event callback. The supported event is **'formOverflow'**, indicating the interactive widget animation request. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.OverflowRequest](arkts-form-forminfo-overflowrequest-i-sys.md)&gt; | Yes | Callback used by the widget host to process the animation request. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |


## on('changeSceneAnimationState')

```TypeScript
function on(type: 'changeSceneAnimationState', 
    callback: Callback<formInfo.ChangeSceneAnimationStateRequest>): void
```

Subscribes to the event of switching the interactive widget state. An interactive widget can be in the active or inactive state. In the inactive state, the interactive widget is the same as a common widget. In the active state, the interactive widget can start the **LiveFormExtensionAbility** process developed by the widget host to implement interactive widget animations. This API uses an asynchronous callback to return the result.

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'changeSceneAnimationState' | Yes | Event type. The event **'changeSceneAnimationState'** is triggered when the interactive widget state is switched. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.ChangeSceneAnimationStateRequest](arkts-form-forminfo-changesceneanimationstaterequest-i-sys.md)&gt; | Yes | Callback function, which is used by the widget host to process the state switching request. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |


## on('getFormRect')

```TypeScript
function on(type: 'getFormRect', callback: formInfo.GetFormRectInfoCallback): void
```

Subscribes to the event of requesting widget position and dimension. This API uses an asynchronous callback to return the result.

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'getFormRect' | Yes | Event callback type. The supported event is **'getFormRect'**, indicating requesting widget position and dimension. |
| callback | [formInfo.GetFormRectInfoCallback](arkts-form-forminfo-getformrectinfocallback-t-sys.md) | Yes | Callback function used by the widget host to process the request and return the position and dimension of the widget relative to the upper-left corner of the screen. The unit is vp. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |


## on('getLiveFormStatus')

```TypeScript
function on(type: 'getLiveFormStatus',  callback: formInfo.GetLiveFormStatusCallback): void
```

Listens to the event of get live form status.

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'getLiveFormStatus' | Yes | Indicates event type. |
| callback | [formInfo.GetLiveFormStatusCallback](arkts-form-forminfo-getliveformstatuscallback-t-sys.md) | Yes | The callback of get live form status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
