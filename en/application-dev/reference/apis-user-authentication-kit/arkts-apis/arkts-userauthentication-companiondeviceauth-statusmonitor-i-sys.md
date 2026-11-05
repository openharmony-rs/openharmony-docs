# StatusMonitor (System API)

```TypeScript
interface StatusMonitor
```

Status monitor object. It is used to listen for or obtain information such as the template status, continuous authentication status, and available device status. This object can be obtained by calling [getStatusMonitor](arkts-userauthentication-companiondeviceauth-getstatusmonitor-f-sys.md).

**Since:** 23

<!--Device-companionDeviceAuth-interface StatusMonitor--><!--Device-companionDeviceAuth-interface StatusMonitor-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## getTemplateStatus

```TypeScript
getTemplateStatus(): Promise<TemplateStatus[]>
```

Obtains the status of the companion device template. This API is used to query the status of all registered companion device authentication templates of the current user, including the template validity, supported services, and associated device status. This API uses a promise to return the result.

Data source: returns an in-memory snapshot of the template status maintained by the system service (UserIAM), rather than a real-time cross-device query.

Difference from **onTemplateChange**: **getTemplateStatus** is used to obtain a one-time snapshot of the current template status and is suitable for proactive querying, whereas **onTemplateChange** is used to continuously subscribe to template status changes and is suitable for real-time responses. Use **getTemplateStatus** when the status needs to be obtained only once, and use **onTemplateChange** when changes need to be continuously monitored.

**Since:** 23

**Required permissions:** ohos.permission.USE_USER_IDM

**Model restriction:** This API can be used only in the stage model.

<!--Device-StatusMonitor-getTemplateStatus(): Promise<TemplateStatus[]>--><!--Device-StatusMonitor-getTemplateStatus(): Promise<TemplateStatus[]>-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[TemplateStatus](arkts-userauthentication-companiondeviceauth-templatestatus-i-sys.md)[]&gt; | Promise used to return the status list of all templates of the current user. The status of each template contains the template ID, validity, and device information. If the operation fails, an error code is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-system-service-not-working-properly) | The system service is not working properly. Please try again later. |

## offAvailableDeviceChange

```TypeScript
offAvailableDeviceChange(callback?: AvailableDeviceStatusCallback): void
```

Unsubscribes from the available companion device status change. The **callback** parameter specifies the callback to unregister. If no callback is passed, all registered callbacks are unregistered.

**Since:** 23

**Required permissions:** ohos.permission.USE_USER_IDM

**Model restriction:** This API can be used only in the stage model.

<!--Device-StatusMonitor-offAvailableDeviceChange(callback?: AvailableDeviceStatusCallback): void--><!--Device-StatusMonitor-offAvailableDeviceChange(callback?: AvailableDeviceStatusCallback): void-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AvailableDeviceStatusCallback](arkts-userauthentication-companiondeviceauth-availabledevicestatuscallback-t-sys.md) | No | Callback registered through **onAvailableDeviceChange**. If this parameter is specified, only this callback is unregistered; if this parameter is omitted, all registered callbacks are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-system-service-not-working-properly) | The system service is not working properly. Please try again later. |

## offContinuousAuthChange

```TypeScript
offContinuousAuthChange(callback?: ContinuousAuthStatusCallback): void
```

Unsubscribes from the continuous authentication status change event of the companion device. After unsubscription, the application no longer receives continuous authentication status change notifications. The **callback** parameter specifies the callback to unregister. If no callback is passed, all registered callbacks are unregistered.

**Since:** 23

**Required permissions:** ohos.permission.USE_USER_IDM

**Model restriction:** This API can be used only in the stage model.

<!--Device-StatusMonitor-offContinuousAuthChange(callback?: ContinuousAuthStatusCallback): void--><!--Device-StatusMonitor-offContinuousAuthChange(callback?: ContinuousAuthStatusCallback): void-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ContinuousAuthStatusCallback](arkts-userauthentication-companiondeviceauth-continuousauthstatuscallback-t-sys.md) | No | Callback previously registered through **onContinuousAuthChange**. If this parameter is specified, only this callback is canceled; if it is omitted, all registered callbacks are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-system-service-not-working-properly) | The system service is not working properly. Please try again later. |

## offTemplateChange

```TypeScript
offTemplateChange(callback?: TemplateStatusCallback): void
```

Unsubscribes from template status changes.

**Since:** 23

**Required permissions:** ohos.permission.USE_USER_IDM

**Model restriction:** This API can be used only in the stage model.

<!--Device-StatusMonitor-offTemplateChange(callback?: TemplateStatusCallback): void--><!--Device-StatusMonitor-offTemplateChange(callback?: TemplateStatusCallback): void-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [TemplateStatusCallback](arkts-userauthentication-companiondeviceauth-templatestatuscallback-t-sys.md) | No | Callback for the template status event. If this parameter is specified, only this callback is unregistered; if it is omitted, all registered callbacks are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-system-service-not-working-properly) | The system service is not working properly. Please try again later. |

## onAvailableDeviceChange

```TypeScript
onAvailableDeviceChange(callback: AvailableDeviceStatusCallback): void
```

Subscribes to the events for status changes of companion devices that can be added. This API uses an asynchronous callback to return the result.

Trigger mechanism: the callback is triggered when the list of companion devices that can be added changes (for example, a new device comes online, a device goes offline, or a device binding relationship changes). The current list is pushed once immediately upon subscription.

**Since:** 23

**Required permissions:** ohos.permission.USE_USER_IDM

**Model restriction:** This API can be used only in the stage model.

<!--Device-StatusMonitor-onAvailableDeviceChange(callback: AvailableDeviceStatusCallback): void--><!--Device-StatusMonitor-onAvailableDeviceChange(callback: AvailableDeviceStatusCallback): void-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AvailableDeviceStatusCallback](arkts-userauthentication-companiondeviceauth-availabledevicestatuscallback-t-sys.md) | Yes | Callback invoked when the available device status changes. Triggered when the list of addable devices changes (for example, a new device comes online or a device goes offline). The callback parameter is the device status list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-system-service-not-working-properly) | The system service is not working properly. Please try again later. |

## onContinuousAuthChange

```TypeScript
onContinuousAuthChange(param: ContinuousAuthParam, callback: ContinuousAuthStatusCallback): void
```

Subscribes to the events for continuous authentication status of companion devices. This API uses an asynchronous callback to return the result.

Continuous authentication: The continuous authentication status indicates whether the companion device holds a valid authentication token. The status changes and the callback is triggered when a token is issued (authentication succeeds), a token times out, the associated device goes offline, or a token is revoked. **authTrustLevel** is the highest authentication trust level among the currently valid tokens. Notification is sent only when the authentication trust level changes. The current status is pushed once immediately upon subscription.

**Since:** 23

**Required permissions:** ohos.permission.USE_USER_IDM

**Model restriction:** This API can be used only in the stage model.

<!--Device-StatusMonitor-onContinuousAuthChange(param: ContinuousAuthParam, callback: ContinuousAuthStatusCallback): void--><!--Device-StatusMonitor-onContinuousAuthChange(param: ContinuousAuthParam, callback: ContinuousAuthStatusCallback): void-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [ContinuousAuthParam](arkts-userauthentication-companiondeviceauth-continuousauthparam-i-sys.md) | Yes | Subscription parameters, which can specify the target template through the templateId field. |
| callback | [ContinuousAuthStatusCallback](arkts-userauthentication-companiondeviceauth-continuousauthstatuscallback-t-sys.md) | Yes | Callback invoked when the continuous authentication status changes. The callback parameters are the authentication result (**isAuthPassed**) and the authentication trust level (**authTrustLevel**). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-system-service-not-working-properly) | The system service is not working properly. Please try again later. |
| [32600002](../errorcode-useriam.md#32600002-template-not-found) | The template is not found. |

## onTemplateChange

```TypeScript
onTemplateChange(callback: TemplateStatusCallback): void
```

Subscribes to template status change events. This API uses an asynchronous callback to return the result.

Trigger timing: triggered when the template status changes, including changes to the enabled business ID, validity changes, associated device online/offline or status changes, and templates being added to or removed from the IDM. A snapshot of the current status is pushed once immediately upon subscription; no repeated notification is sent when the status remains unchanged.

**Since:** 23

**Required permissions:** ohos.permission.USE_USER_IDM

**Model restriction:** This API can be used only in the stage model.

<!--Device-StatusMonitor-onTemplateChange(callback: TemplateStatusCallback): void--><!--Device-StatusMonitor-onTemplateChange(callback: TemplateStatusCallback): void-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [TemplateStatusCallback](arkts-userauthentication-companiondeviceauth-templatestatuscallback-t-sys.md) | Yes | Callback invoked when the template status changes (for example, addition, deletion, or validity change). The callback parameter is a list of template statuses. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-system-service-not-working-properly) | The system service is not working properly. Please try again later. |
