# OsAccountSubProfileManager (System API)

Defines an OS account sub-profile manager.

**Since:** 26.0.0

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## createOsAccountSubProfile

```TypeScript
createOsAccountSubProfile(osAccountLocalId: number): Promise<OsAccountSubProfile>
```

Creates an OS account sub-profile. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| osAccountLocalId | number | Yes | Local ID of the target OS account.<br>The value range is all integers. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OsAccountSubProfile](arkts-basicservices-osaccount-osaccountsubprofile-i-sys.md)&gt; | Promise used to return the created sub-profile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | The OS account not found. |
| [12300008](../errorcode-account.md#12300008-restricted-account) | Restricted OS account. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Service busy. Possible causes: The target OS account is being operated. |
| [12300402](../errorcode-account.md#12300402-number-of-os-account-sub-profiles-has-reached-the-upper-limit) | The number of sub-profiles under the OS account has reached limit. |

**Examples**

```TypeScript
Create an OS account sub-profile whose ID is 100.
```

## deleteOsAccountSubProfile

```TypeScript
deleteOsAccountSubProfile(osAccountLocalId: number, subProfileId: number): Promise<void>
```

Deletes an OS account sub-profile. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| osAccountLocalId | number | Yes | Local ID of the target OS account.<br>The value range is all integers. |
| subProfileId | number | Yes | Sub-profile ID.<br>The value range is all integers. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Service busy. Possible causes: The OS account or sub-profile is being operated. |
| [12300401](../errorcode-account.md#12300401-os-account-sub-profile-not-found) | Sub-profile not found. |
| [12300403](../errorcode-account.md#12300403-restricted-os-account-sub-profile) | Restricted sub-profile cannot be deleted. |
| [12300404](../errorcode-account.md#12300404-foreground-sub-profile-of-the-os-account-cannot-be-deleted) | The foreground sub-profile cannot be deleted. |

**Examples**

```TypeScript
Delete the sub-profile whose ID is 100001 from OS account 100.
```

## getOsAccountForegroundSubProfileId

```TypeScript
getOsAccountForegroundSubProfileId(): Promise<number>
```

Obtains the foreground sub-profile ID of the OS account of the caller. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the foreground sub-profile ID of the OS account. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300401](../errorcode-account.md#12300401-os-account-sub-profile-not-found) | Sub-profile not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subProfileManager: osAccount.OsAccountSubProfileManager = osAccount.getOsAccountSubProfileManager();
try {
  subProfileManager.getOsAccountForegroundSubProfileId().then((subProfileId: number) => {
    console.info('getOsAccountForegroundSubProfileId successfully, subProfileId: ' + subProfileId);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountForegroundSubProfileId failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountForegroundSubProfileId exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
Obtain the foreground sub-profile ID of OS account 100.
```

## getOsAccountForegroundSubProfileId

```TypeScript
getOsAccountForegroundSubProfileId(osAccountLocalId: number): Promise<number>
```

Obtains the foreground sub-profile ID of the specified OS account. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| osAccountLocalId | number | Yes | Local ID of an OS account.<br>The value range is all integers. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the foreground sub-profile ID of the OS account. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | OS account not found. |
| [12300401](../errorcode-account.md#12300401-os-account-sub-profile-not-found) | The foreground sub-profile not found. |

**Examples**

See [getOsAccountForegroundSubProfileId](#getosaccountforegroundsubprofileid)

## getOsAccountLocalIdForSubProfile

```TypeScript
getOsAccountLocalIdForSubProfile(subProfileId: number): Promise<number>
```

Obtains the local ID of the OS account of a sub-profile. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subProfileId | number | Yes | Sub-profile ID.<br>The value should be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the local ID of the OS account of the sub-profile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300401](../errorcode-account.md#12300401-os-account-sub-profile-not-found) | Sub-profile not found. |

**Examples**

```TypeScript
Obtains the local ID of the OS account of the sub-profile whose ID is 100001.
```

## getOsAccountSubProfile

```TypeScript
getOsAccountSubProfile(subProfileId: number): Promise<OsAccountSubProfile>
```

Obtains the sub-profile of the OS account of the caller. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subProfileId | number | Yes | Sub-profile ID.<br>The value should be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OsAccountSubProfile](arkts-basicservices-osaccount-osaccountsubprofile-i-sys.md)&gt; | Promise used to return the sub-profile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300401](../errorcode-account.md#12300401-os-account-sub-profile-not-found) | Sub-profile not found. |

**Examples**

```TypeScript
Obtains the sub-profile whose ID is 100001.
```

```TypeScript
Obtain the sub-profile whose ID is 100001 of OS account 100.
```

## getOsAccountSubProfile

```TypeScript
getOsAccountSubProfile(osAccountLocalId: number, subProfileId: number): Promise<OsAccountSubProfile>
```

Obtains the sub-profile of the specified OS account. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_LOCAL_ACCOUNTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| osAccountLocalId | number | Yes | Local ID of an OS account.<br>The value should be an integer. |
| subProfileId | number | Yes | Sub-profile ID.<br>The value should be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OsAccountSubProfile](arkts-basicservices-osaccount-osaccountsubprofile-i-sys.md)&gt; | Promise used to return the sub-profile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300401](../errorcode-account.md#12300401-os-account-sub-profile-not-found) | Sub-profile not found. |

**Examples**

See [getOsAccountSubProfile](#getosaccountsubprofile)

## getOsAccountSubProfileIds

```TypeScript
getOsAccountSubProfileIds(): Promise<number[]>
```

Obtains the sub-profile IDs of the OS account of the caller. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_LOCAL_ACCOUNT_IDENTIFIERS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number[]&gt; | Promise used to return the sub-profile IDs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subProfileManager: osAccount.OsAccountSubProfileManager = osAccount.getOsAccountSubProfileManager();
try {
  subProfileManager.getOsAccountSubProfileIds().then((subProfileIds: number[]) => {
    console.info('getOsAccountSubProfileIds successfully, subProfileIds: ' + subProfileIds);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountSubProfileIds failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountSubProfileIds exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
Obtain the sub-profile IDs of OS account 100.
```

## getOsAccountSubProfileIds

```TypeScript
getOsAccountSubProfileIds(osAccountLocalId: number): Promise<number[]>
```

Obtains the sub-profile IDs of the specified OS account. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_LOCAL_ACCOUNT_IDENTIFIERS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| osAccountLocalId | number | Yes | Local ID of an OS account.<br>The value range is all integers. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number[]&gt; | Promise used to return the sub-profile IDs of the specified OS account. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | OS account not found. |

**Examples**

See [getOsAccountSubProfileIds](#getosaccountsubprofileids)

## offOsAccountSubProfileEvent

```TypeScript
offOsAccountSubProfileEvent(callback?: Callback<OsAccountSubProfileEventData>): void
```

Unsubscribes from OS account sub-profile events. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[OsAccountSubProfileEventData](arkts-basicservices-osaccount-osaccountsubprofileeventdata-i-sys.md)&gt; | No | Callback to unsubscribe from. By default, no value is passed, which means all callbacks are unsubscribed from. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subProfileManager: osAccount.OsAccountSubProfileManager = osAccount.getOsAccountSubProfileManager();
try {
  subProfileManager.offOsAccountSubProfileEvent();
} catch (e) {
  const err = e as BusinessError;
  console.error(`offOsAccountSubProfileEvent failed, code is ${err.code}, message is ${err.message}`);
}
```

## onOsAccountSubProfileEvent

```TypeScript
onOsAccountSubProfileEvent(
      events: OsAccountSubProfileEvent[],
      callback: Callback<OsAccountSubProfileEventData>): void
```

Subscribes to OS account sub-profile events. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| events | [OsAccountSubProfileEvent](arkts-basicservices-osaccount-osaccountsubprofileevent-e-sys.md)[] | Yes | Array of events to be subscribed to. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[OsAccountSubProfileEventData](arkts-basicservices-osaccount-osaccountsubprofileeventdata-i-sys.md)&gt; | Yes | Callback invoked when the event occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid event. |

**Examples**

```TypeScript
Subscribe to an OS account sub-profile creation event.
```

## switchOsAccountSubProfile

```TypeScript
switchOsAccountSubProfile(osAccountLocalId: number, subProfileId: number): Promise<void>
```

Switches to an OS account sub-profile. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| osAccountLocalId | number | Yes | Local ID of an OS account.<br>The value range is all integers. |
| subProfileId | number | Yes | Sub-profile ID.<br>The value range is all integers. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Service busy. Possible causes: The OS account or sub-profile is being operated. |
| [12300401](../errorcode-account.md#12300401-os-account-sub-profile-not-found) | Sub-profile not found. |
| [12300403](../errorcode-account.md#12300403-restricted-os-account-sub-profile) | Restricted sub-profile cannot be switched to foreground. |
| [12300405](../errorcode-account.md#12300405-foreground-sub-profile-with-a-logged-in-distributed-account-cannot-be-directly-switched-to-the-background) | The foreground sub-profile bound with a logged-in distributed account cannot be directly switched to background. |

**Examples**

```TypeScript
Switch from the current sub-profile of OS account 100 to the sub-profile whose ID is 100001.
```
