# @ohos.userIAM.companionDeviceAuth (Companion Device Authentication) (System API)
<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->
The **companionDeviceAuth** module provides capabilities such as companion device query, subscription, and service scope management for system applications.

A companion device is an identity authentication credential added by a user on the main device. If the conditions are met, the companion device can interact with the main device to authenticate the user identity. The companion device can be applied in such scenarios as a watch as a companion device to unlock a mobile phone or a headset as a companion device to execute voice commands without unlocking the mobile phone.

> **NOTE**
> 
> - The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## BusinessId

A service ID uniquely identifies a service scenario supported by the companion device. The supported service scenarios vary with the authentication security of companion devices. For example, a smart watch as a companion device can unlock the screen, unlock the application, and execute voice commands on the lock screen, while a headset as a companion device can only execute voice commands on the lock screen.

The companion device relationships of different service IDs are independent of each other and do not interfere with each other. They can be added, deleted, and authenticated independently.

Currently, the services of the companion device module include the default services of OpenHarmony, screen unlocking, application unlocking, and identity authentication before voice commands are executed on the lock screen.

Adding services has requirements on the scenarios supported by the server device. For example, the multi-screen collaboration service requires that the server device support the agency authentication scenario.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

| **Name**| **Value**| **Description**|
| ----------- | ---- | ---------- |
| DEFAULT | 0 | Default service ID.|
| VENDOR_BEGIN | 10000 | Start value of the service ID defined by the vendor. The actual value must be greater than or equal to 10000 to avoid conflicts with the reserved values of the system.|

## DeviceIdType

Enumerates device ID types.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

| **Name**| **Value**| **Description**|
| ----------------- | ----- | ------------------------------------------------------------ |
| UNIFIED_DEVICE_ID | 1 | Unified device ID.|
| VENDOR_BEGIN | 10000 | Start value of the service ID defined by the vendor. The actual value must be greater than or equal to 10000 to avoid conflicts with the reserved values of the system.|

## SelectPurpose

Selects the purpose of the companion device.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

| **Name**| **Value**| **Description**|
| ----------- | ---- | ---------- |
| SELECT_ADD_DEVICE | 1 | Selects the companion device for adding a template.|
| SELECT_AUTH_DEVICE | 2 | Selects the companion device that provides the authentication capability.|
| VENDOR_BEGIN | 10000 | Start value of the service ID defined by the vendor. The actual value must be greater than or equal to 10000 to avoid conflicts with the reserved values of the system.|

## DeviceKey

Defines the device key.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| ------------ | ---------- | ---- | ---- | -------------------- |
| deviceIdType | number | No| No| Device ID type. You can customize the extension based on [DeviceIdType](#deviceidtype).|
| deviceId | string | No| No| Device ID.|
| deviceUserId | number | No| No| Device user ID.|

## DeviceStatus

Defines the device status information.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| -------------------- | ------------------------- | ---- | ---- | ---------------------- |
| deviceKey | [DeviceKey](#devicekey) | No| No| Device key.|
| deviceUserName | string | No| No| Device user name.|
| deviceModelInfo | string | No| No| Device model information.|
| deviceName | string | No| No| Device name.|
| isOnline | boolean | No| No| Device online status. The options are as follows: **true**: The device is online. **false**: The device is offline.|
| supportedBusinessIds | number[] | No| No| List of service IDs supported by the device.|

## TemplateStatus

Provides the template status maintained by the **companionDeviceAuth** module.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| ------------------ | ------------------------------- | ---- | ---- | -------------------- |
| templateId | Uint8Array | No| No| Template ID.|
| isConfirmed | boolean | No| No| Whether the data is real-time data. The options are as follows: **true**: The data is real-time data. **false**: The data is cached data.|
| isValid | boolean | No| No| Whether the template is valid. The options are as follows: **true**: The template is valid. **false**: The template is invalid.|
| localUserId | number | No| No| Local user ID.|
| addedTime | Date | No| No| Template adding time. The value is a Unix timestamp, that is, the number of milliseconds elapsed since the Unix epoch.|
| enabledBusinessIds | number[] | No| No| List of supported service IDs.|
| deviceStatus | [DeviceStatus](#devicestatus) | No| No| Device status information.|

## TemplateStatusCallback

type TemplateStatusCallback = (templateStatusList: TemplateStatus[]) => void

Defines the callback used to receive the template status.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type** | **Mandatory**| **Description**|
| ------------------ | ------------------------------------- | ---- | -------------- |
| templateStatusList | [TemplateStatus](#templatestatus)[] | Yes| Template status list.|

## ContinuousAuthStatusCallback

type ContinuousAuthStatusCallback = (isAuthPassed: boolean, authTrustLevel?: UserAuth.AuthTrustLevel) => void

Defines the callback used to receive the continuous authentication status.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------------- | ----------------------- | ---- | ------------------------------------------------------------ |
| isAuthPassed | boolean | Yes| Whether the authentication is successful. The options are as follows: **true**: yes; **false**: no.|
| authTrustLevel | [UserAuth.AuthTrustLevel](./js-apis-useriam-userauth.md#authtrustlevel8) | No| Authentication trust level, that is, the trust level of identity authentication required for typical operations. For details, see [Principles for Classifying Biometric Authentication Trust Levels](../../security/UserAuthenticationKit/user-authentication-overview.md#principles-for-classifying-biometric-authentication-trust-levels).|

## AvailableDeviceStatusCallback

type AvailableDeviceStatusCallback = (deviceStatusList: DeviceStatus[]) => void

Defines the callback used to receive the changes of the list of devices that can be added.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| ---------------- | --------------------------------- | -------------- | -------------- |
| deviceStatusList | [DeviceStatus](#devicestatus)[] | Yes| Device status list.|

## ContinuousAuthParam

Defines the continuous authentication parameter.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| ---------- | ---------- | ---- | ---- | -------------------------------------------- |
| templateId | Uint8Array | No| Yes| Template ID. If this parameter is not specified, all templates of the current user are subscribed to by default.|

## StatusMonitor

Defines the object for listening to or obtaining the template or continuous authentication status.

### getTemplateStatus

getTemplateStatus(): Promise&lt;TemplateStatus[]&gt;

Obtains the status of the companion device template. This API uses a promise to return the result.

**Required permissions**: ohos.permission.USE_USER_IDM

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Return value**

| **Type**| **Description**|
| ------------------------------------- | ------------------------------------------------------ |
| Promise&lt;[TemplateStatus](#templatestatus)[]&gt;| Promise used to return the list of all template states.|

**Error codes**

For details about the error codes, see [User Authentication Error Codes](errorcode-useriam.md).

| **ID**| **Error Message**|
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const localUserId = 100;
const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
statusMonitor.getTemplateStatus()
  .then((templateStatus) => {
    console.info(`templateStatus: ${JSON.stringify(templateStatus)}`);
  })
  .catch((error: BusinessError) => {
    console.error(`error has been captured: message:${error?.message}`);
  })
```

### onTemplateChange

onTemplateChange(callback: TemplateStatusCallback): void

Subscribes to template status change events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.USE_USER_IDM

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | --------------------------------------------------- | ---- | ---------------------------- |
| callback | [TemplateStatusCallback](#templatestatuscallback) | Yes| Callback used to receive the template status.|

**Error codes**

For details about the error codes, see [User Authentication Error Codes](errorcode-useriam.md).

| **ID**| **Error Message**|
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const localUserId = 100;
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const handler = (templates: companionDeviceAuth.TemplateStatus[]): void => {
    console.info('template status updated');
  };
  statusMonitor.onTemplateChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

### offTemplateChange

offTemplateChange(callback?: TemplateStatusCallback): void

Unsubscribes from template status change events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.USE_USER_IDM

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [TemplateStatusCallback](#templatestatuscallback) | No| Callback to unregister. If this parameter is not specified, all callbacks corresponding to the event type are unsubscribed.|

**Error codes**

For details about the error codes, see [User Authentication Error Codes](errorcode-useriam.md).

| **ID**| **Error Message**|
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const localUserId = 100;
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const handler = (templates: companionDeviceAuth.TemplateStatus[]): void => {
    console.info('template status updated');
  };
  statusMonitor.onTemplateChange(handler);
  statusMonitor.offTemplateChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

### onAvailableDeviceChange

onAvailableDeviceChange(callback: AvailableDeviceStatusCallback): void

Subscribes to the events for status changes of companion devices that can be added. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.USE_USER_IDM

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | ------------------------------------------------------------ | ---- | ---------------------------- |
| callback | [AvailableDeviceStatusCallback](#availabledevicestatuscallback) | Yes| Callback used to return the available device status.|

**Error codes**

For details about the error codes, see [User Authentication Error Codes](errorcode-useriam.md).

| **ID**| **Error Message**|
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const localUserId = 100;
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const handler = (deviceStatusList: companionDeviceAuth.DeviceStatus[]): void => {
    console.info('available device changed');
  };
  statusMonitor.onAvailableDeviceChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

### offAvailableDeviceChange

offAvailableDeviceChange(callback?: AvailableDeviceStatusCallback): void

Unsubscribes from the events for status changes of companion devices that can be added. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.USE_USER_IDM

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [AvailableDeviceStatusCallback](#availabledevicestatuscallback) | No| Callback to unregister. If this parameter is not specified, all callbacks corresponding to the event type are unsubscribed.|

**Error codes**

For details about the error codes, see [User Authentication Error Codes](errorcode-useriam.md).

| **ID**| **Error Message**|
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const localUserId = 100;
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const handler = (deviceStatusList: companionDeviceAuth.DeviceStatus[]): void => {
    console.info('available device changed');
  };
  statusMonitor.onAvailableDeviceChange(handler);
  statusMonitor.offAvailableDeviceChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

### onContinuousAuthChange

onContinuousAuthChange(param: ContinuousAuthParam, callback: ContinuousAuthStatusCallback): void

Subscribes to the events for continuous authentication status of companion devices. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.USE_USER_IDM

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------------- |
| param | [ContinuousAuthParam](#continuousauthparam) | Yes| Device for which the events are subscribed to.|
| callback | [ContinuousAuthStatusCallback](#continuousauthstatuscallback) | Yes| Called when the continuous authentication status of the device changes.|

**Error codes**

For details about the error codes, see [User Authentication Error Codes](errorcode-useriam.md).

| **ID**| **Error Message**|
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |
| 32600002 | The template is not found. |

**Example**

```ts
import { osAccount, BusinessError } from '@kit.BasicServicesKit';

const localUserId = 100;
try {
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const continuousAuthParam: companionDeviceAuth.ContinuousAuthParam = {
    templateId: new Uint8Array([])
  };
  const handler = (isAuthPassed: boolean, authTrustLevel?: osAccount.AuthTrustLevel): void => {
    console.info('continuous auth changed');
    console.info(`isAuthPassed: ${isAuthPassed}`);
    if (authTrustLevel !== undefined) {
      console.info(`authTrustLevel: ${authTrustLevel}`);
    }
  };

  statusMonitor.onContinuousAuthChange(continuousAuthParam, handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

### offContinuousAuthChange

offContinuousAuthChange(callback?: ContinuousAuthStatusCallback): void

Unsubscribes from the events for continuous authentication status of companion devices. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.USE_USER_IDM

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [ContinuousAuthStatusCallback](#continuousauthstatuscallback) | No| Callback to unregister. If this parameter is not specified, all callbacks corresponding to the event type are unsubscribed.|

**Error codes**

For details about the error codes, see [User Authentication Error Codes](errorcode-useriam.md).

| **ID**| **Error Message**|
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**Example**

```ts
import { osAccount, BusinessError } from '@kit.BasicServicesKit';

const localUserId = 100;
try {
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const continuousAuthParam: companionDeviceAuth.ContinuousAuthParam = {
    templateId: new Uint8Array([])
  };
  const handler = (isAuthPassed: boolean, authTrustLevel?: osAccount.AuthTrustLevel): void => {
    console.info('continuous auth changed');
    console.info(`isAuthPassed: ${isAuthPassed}`);
    if (authTrustLevel !== undefined) {
      console.info(`authTrustLevel: ${authTrustLevel}`);
    }
  };

  statusMonitor.onContinuousAuthChange(continuousAuthParam, handler);
  statusMonitor.offContinuousAuthChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

## companionDeviceAuth.getStatusMonitor

getStatusMonitor(localUserId: number): StatusMonitor

Obtains the status listener, which is used to query and subscribe to companion template information.

**Required permissions**: ohos.permission.USE_USER_IDM

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| ----------- | ---- | ---- | ------------ |
| localUserId | number | Yes| Local user ID.|

**Return value**

| **Type**| **Description**|
| --------------------------------- | ------------------------------ |
| [StatusMonitor](#statusmonitor) | Promise used to return the status listener.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| **ID**| **Error Message**|
| -------- | ------------------------------------------------------------ |
| 201 | Permission denied. |
| 202 | Not system application. |
| 32600001 | The system service is not working properly. Please try again later. |
| 32600002 | The local user is not found. |

**Example**

```ts
import { osAccount, BusinessError } from '@kit.BasicServicesKit';

const localUserId = 100;
try {
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const continuousAuthParam: companionDeviceAuth.ContinuousAuthParam = {
    templateId: new Uint8Array([])
  };
  const handler = (isAuthPassed: boolean, authTrustLevel?: osAccount.AuthTrustLevel): void => {
    console.info('continuous auth changed');
    console.info(`isAuthPassed: ${isAuthPassed}`);
    if (authTrustLevel !== undefined) {
      console.info(`authTrustLevel: ${authTrustLevel}`);
    }
  };

  statusMonitor.onContinuousAuthChange(continuousAuthParam, handler);
  statusMonitor.offContinuousAuthChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

## DeviceSelectResult

Returns the result of companion device selection.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| ---------------- | --------------------------- | ---- | ---- | ------------------------------------------ |
| deviceKeys | [DeviceKey](#devicekey)[] | No| No| Device information list.|
| selectionContext | Uint8Array | No| Yes| Device selection context, which carries extended information in JSON format.|

## DeviceSelectCallback

type DeviceSelectCallback = (selectPurpose: number) => DeviceSelectResult

Defines the callback of companion device selection.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| ------------- | ---- | ---- | ------------------------------------------------------------ |
| selectPurpose | number | Yes| Selection purpose. For details about the values, see [SelectPurpose](#selectpurpose). The value can be customized.|

**Return value**

| **Type**| **Description**|
| ------------------------------------------- | -------------------- |
| [DeviceSelectResult](#deviceselectresult) | Device selection result.|

## companionDeviceAuth.registerDeviceSelectCallback

registerDeviceSelectCallback(callback: DeviceSelectCallback): void

Registers the callback for companion device selection.

**Required permissions**: ohos.permission.USE_USER_IDM

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | ----------------------------------------------- | ---- | -------------------- |
| callback | [DeviceSelectCallback](#deviceselectcallback) | Yes| Callback used to return the companion device selection result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| **ID**| **Error Message**|
| -------- | ------------------------------------------------------------ |
| 201 | Permission denied. |
| 202 | Not system application. |
| 32600001 | The system service is not working properly. Please try again later. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  companionDeviceAuth.registerDeviceSelectCallback((purpose) => {
    const addDeviceId = 'addDeviceId';
    const otherDeviceId = 'otherDeviceId';
    const addDeviceUserId = 100;
    const otherDeviceUserId = 100;
    if (purpose === companionDeviceAuth.SelectPurpose.SELECT_ADD_DEVICE) {
      return {
        deviceKeys: [{
          deviceIdType: companionDeviceAuth.DeviceIdType.UNIFIED_DEVICE_ID,
          deviceId: addDeviceId,
          deviceUserId: addDeviceUserId
        }]
      };
    }
    return {
      deviceKeys: [{
        deviceIdType: companionDeviceAuth.DeviceIdType.UNIFIED_DEVICE_ID,
        deviceId: otherDeviceId,
        deviceUserId: otherDeviceUserId
      }]
    };
  })
} catch (error) {
  const err = error as BusinessError;
  console.error(`error has been captured: ${err.code} ${err.message}`);
}
```

## companionDeviceAuth.unregisterDeviceSelectCallback

unregisterDeviceSelectCallback(): void

Unregisters the callback for companion device selection.

**Required permissions**: ohos.permission.USE_USER_IDM

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| **ID**| **Error Message**|
| -------- | ------------------------------------------------------------ |
| 201 | Permission denied. |
| 202 | Not system application. |
| 32600001 | The system service is not working properly. Please try again later. |

**Example**
<!--code_no_check-->

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  companionDeviceAuth.unregisterDeviceSelectCallback();
} catch (error) {
  const err = error as BusinessError;
  console.error(`error has been captured: ${err.code} ${err.message}`);
}
```

## companionDeviceAuth.updateEnabledBusinessIds

updateEnabledBusinessIds(templateId: Uint8Array, enabledBusinessIds: number[]): Promise&lt;void&gt;

Updates the service scope supported by the specified companion device template. This API uses a promise to return the result.

**Required permissions**: ohos.permission.USE_USER_IDM

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API**: This is a system API.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| ------------------ | ---------- | ---- | ------------------------ |
| templateId | Uint8Array | Yes| ID of the target template.|
| enabledBusinessIds | number[] | Yes| ID set of services supported by the template.|

**Return value**

| **Type**               | **Description**           |
| ------------------- | --------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| **ID**| **Error Message**|
| -------- | ------------------------------------------------------------ |
| 201 | Permission denied. |
| 202 | Not system application. |
| 32600001 | The system service is not working properly. Please try again later. |
| 32600002 | The template is not found. |
| 32600003 | The business ID is invalid. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const templateId = new Uint8Array([1, 2, 3]);
companionDeviceAuth.updateEnabledBusinessIds(templateId, [companionDeviceAuth.BusinessId.DEFAULT])
  .then(() => {
    console.info('business scope updated');
  })
  .catch((err: BusinessError) => {
    console.error(`error has been captured: code: ${err.code}, message: ${err.message}`);
  })
```
