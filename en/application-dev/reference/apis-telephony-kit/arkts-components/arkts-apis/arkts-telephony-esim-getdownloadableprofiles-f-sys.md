# getDownloadableProfiles (System API)

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## getDownloadableProfiles

```TypeScript
function getDownloadableProfiles(slotId: number, portIndex: number,
                                   forceDisableProfile: boolean): Promise<GetDownloadableProfilesResult>
```

Obtains the list of downloadable profiles. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.GET_TELEPHONY_ESIM_STATE

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |
| portIndex | number | Yes | Port index of the slot. |
| forceDisableProfile | boolean | Yes | Whether to forcibly deactivate the current profile during profile switching.<br> **true**: The current profile is forcibly deactivated, and profile switching can be directly performed. <br> **false**: An error is returned, and profile switching can be performed only after the user authorization is obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[GetDownloadableProfilesResult](arkts-telephony-esim-getdownloadableprofilesresult-i-sys.md)&gt; | Promise used to return the list of downloadable profiles. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3120001](../errorcode-telephony.md#3120001-service-connection-error) | Service connection failed. |
| [3120002](../errorcode-telephony.md#3120002-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.getDownloadableProfiles(1, 0, true).then((data: eSIM.GetDownloadableProfilesResult) => {
    console.info(`getDownloadableProfiles, GetDownloadableProfilesResult: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`getDownloadableProfiles, GetDownloadableProfilesResult: err->${JSON.stringify(err)}`);
});
```
