# @ohos.telephony.esim (eSIM Management) (System API)
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @yangyannanyangyannan-->
<!--Designer: @ghxbob-->
<!--Tester: @weitiantian-->
<!--Adviser: @zhang_yixin13-->

The **esim** module provides APIs for eSIM management and eSIM services.

> **NOTE**
>
> The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.telephony.esim (eSIM Management)](js-apis-esim.md).

## Modules to Import

```ts
import { eSIM } from '@kit.TelephonyKit';
```

## eSIM.getEid<sup>18+</sup>

getEid\(slotId: number\): Promise\<string\>

Obtains the EID of the embedded universal integrated circuit card (eUICC) in the specified slot.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type  | Mandatory| Description                                    |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | number | Yes  | Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2  |

**Returns**

| Type                 | Description                               |
| --------------------- | ---------------------------------- |
| Promise\<string\> | EID of the eUICC in the specified slot.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                        |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { eSIM } from '@kit.TelephonyKit';

try {
    let eid: string = eSIM.getEid(1);
    console.info(`the EID is:` + eid);
} catch (err) {
    console.err(`getEid, promise: err->${JSON.stringfy(err)}`)
}
```

## eSIM.getOsuStatus<sup>18+</sup>

getOsuStatus\(slotId: number\): Promise\<OsuStatus\>

Obtains the OS upgrade status for the eSIM in the specified slot. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | number | Yes  | Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[OsuStatus](#osustatus18)\> |  Promise used to return the OS upgrade status.<br> 1. Updating.<br>   2. Update failed.<br>  3. Update succeeded.<br>  4. Already the latest version.<br> 5. Update service unavailable.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.getOsuStatus(1).then(() => {
    console.info(`getOsuStatus invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`getOsuStatus, promise: err->${JSON.stringify(err)}`);
});
```

## eSIM.startOsu<sup>18+</sup>

startOsu\(slotId: number\): Promise\<OsuStatus\>

Upgrades the OS if the OS version of the eSIM in the specified slot is not the latest. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.SET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | number | Yes  | Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[OsuStatus](#osustatus18)\> |  Promise used to return the OS upgrade status.<br> 1. Updating.<br>   2. Update failed.<br>  3. Update succeeded.<br>  4. Already the latest version.<br> 5. Update service unavailable.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.startOsu(1).then(() => {
    console.info(`startOsu invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`startOsu, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.getDownloadableProfileMetadata<sup>18+</sup>

getDownloadableProfileMetadata\(slotId: number, portIndex: number, profile: DownloadableProfile, forceDisableProfile: boolean\): Promise\<GetDownloadableProfileMetadataResult\>

Obtains the metadata of the downloadable profile. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.SET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description                                                                                                  |
| ------ | ------ | ----- |------------------------------------------------------------------------------------------------------|
| slotId              | number                                        | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2                                                                     |
| portIndex           | number                                        | Yes| Port index of the slot.                                                                                            |
| profile             | [DownloadableProfile](./js-apis-esim.md#downloadableprofile18) | Yes| Downloadable profile.                                                                                         |
| forceDisableProfile | boolean | Yes| Whether to forcibly deactivate the current profile during profile switching.<br> **true**: The current profile is forcibly deactivated, and profile switching can be directly performed.<br> **false**: An error is returned, and profile switching can be performed only after the user authorization is obtained.|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[GetDownloadableProfileMetadataResult](#getdownloadableprofilemetadataresult18)\> | Promise used to return the metadata of the downloadable profile.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

let profile: eSIM.DownloadableProfile = {
  activationCode:'1',
  confirmationCode:'1',
  carrierName:'test',
  accessRules:[{
    certificateHashHexStr:'test',
    packageName:'com.example.testcoreservice',
    accessType:0
  }]
};

eSIM.getDownloadableProfileMetadata(1, 0, profile, true).then((data: eSIM.GetDownloadableProfileMetadataResult) => {
    console.info(`getDownloadableProfileMetadata, GetDownloadableProfileMetadataResult: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`getDownloadableProfileMetadata, GetDownloadableProfileMetadataResult: err->${JSON.stringify(err)}`);
});
```

## eSIM.getDownloadableProfiles<sup>18+</sup>

getDownloadableProfiles\(slotId: number, portIndex: number,
forceDisableProfile: boolean\): Promise\<GetDownloadableProfilesResult\>

Obtains the list of downloadable profiles. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ----- | ----- |
| slotId              | number  | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|
| portIndex           | number  | Yes| Port index of the slot.|
| forceDisableProfile | boolean | Yes| Whether to forcibly deactivate the current profile during profile switching.<br> **true**: The current profile is forcibly deactivated, and profile switching can be directly performed.<br> **false**: An error is returned, and profile switching can be performed only after the user authorization is obtained.|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[GetDownloadableProfilesResult](#getdownloadableprofilesresult18)\> | Promise used to return the list of downloadable profiles.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.getDownloadableProfiles(1, 0, true).then((data: eSIM.GetDownloadableProfilesResult) => {
    console.info(`getDownloadableProfiles, GetDownloadableProfilesResult: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`getDownloadableProfiles, GetDownloadableProfilesResult: err->${JSON.stringify(err)}`);
});
```

## eSIM.downloadProfile<sup>18+</sup>

downloadProfile\(slotId: number, portIndex: number, profile: DownloadableProfile,
configuration: DownloadConfiguration\): Promise\<DownloadProfileResult\>

Downloads a profile. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.SET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ----- | ----- |
| slotId        | number                                            | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|
| portIndex     | number                                            | Yes| Port index of the slot.|
| profile       | [DownloadableProfile](./js-apis-esim.md#downloadableprofile18)     | Yes| Downloadable profile.|
| configuration | [DownloadConfiguration](#downloadconfiguration18) | Yes| Download configuration.|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[DownloadProfileResult](#downloadprofileresult18)\> | Promise used to return the profile download result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

let profile: eSIM.DownloadableProfile = {
  activationCode:'1',
  confirmationCode:'1',
  carrierName:'test',
  accessRules:[{
    certificateHashHexStr:'test',
    packageName:'com.example.testcoreservice',
    accessType:0
  }]
};

let configuration: eSIM.DownloadConfiguration = {
  switchAfterDownload: true,
  forceDisableProfile: true,
  isPprAllowed: true,
};

eSIM.downloadProfile(1, 0, profile, configuration).then((data: eSIM.DownloadProfileResult) => {
    console.info(`downloadProfile, DownloadProfileResult: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`downloadProfile, DownloadProfileResult: err->${JSON.stringify(err)}`);
});
```

## eSIM.getEuiccProfileInfoList<sup>18+</sup>

getEuiccProfileInfoList\(slotId: number\): Promise\<GetEuiccProfileInfoListResult\>

Obtains the profile information list. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ----- | ----- |
| slotId | number | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[GetEuiccProfileInfoListResult](#geteuiccprofileinfolistresult18)\> | Promise used to return the profile information list.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.getEuiccProfileInfoList(1).then((data: eSIM.GetEuiccProfileInfoListResult) => {
    console.info(`getEuiccProfileInfoList, GetEuiccProfileInfoListResult: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`getEuiccProfileInfoList, GetEuiccProfileInfoListResult: err->${JSON.stringify(err)}`);
});
```

## eSIM.getEuiccInfo<sup>18+</sup>

getEuiccInfo\(slotId: number\): Promise\<EuiccInfo\>

Obtains eUICC information. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ----- | ----- |
| slotId | number | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[EuiccInfo](#euiccinfo18)\> | Promise used to return the eUICC information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.getEuiccInfo(1).then((data: eSIM.EuiccInfo) => {
    console.info(`getEuiccInfo, EuiccInfo: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`getEuiccInfo, EuiccInfo: err->${JSON.stringify(err)}`);
});
```

## eSIM.deleteProfile<sup>18+</sup>

deleteProfile\(slotId: number, iccid: string\): Promise\<ResultCode\>

Deletes a profile. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.SET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ----- | ----- |
| slotId | number | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|
| iccid  | string | Yes| Profile ID.|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode18)\> | Promise used to return the operation result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.deleteProfile(1, 'testId').then(() => {
    console.info(`deleteProfile invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`deleteProfile, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.switchToProfile<sup>18+</sup>

switchToProfile\(slotId: number, portIndex: number, iccid: string,
forceDisableProfile: boolean\): Promise\<ResultCode\>

Switches to the specified profile. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.SET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ----- | ----- |
| slotId              | number  | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|
| portIndex           | number  | Yes| Port index of the slot.|
| iccid               | string  | Yes| Profile ID.  |
| forceDisableProfile | boolean | Yes| Whether to forcibly deactivate the current profile during profile switching.<br> **true**: The current profile is forcibly deactivated, and profile switching can be directly performed.<br> **false**: An error is returned, and profile switching can be performed only after the user authorization is obtained.|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode18)\> | Promise used to return the operation result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.switchToProfile(1, 0, 'testId', true).then(() => {
    console.info(`switchToProfile invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`switchToProfile, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.setProfileNickname<sup>18+</sup>

setProfileNickname\(slotId: number, iccid: string, nickname: string\): Promise\<ResultCode\>

Sets a nickname for the specified profile. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.SET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ----- | ----- |
| slotId   | number | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|
| iccid    | string | Yes| Profile ID.|
| nickname | string | Yes| Profile nickname.|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode18)\> | Promise used to return the operation result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.setProfileNickname(1, 'testId', 'testName').then(() => {
    console.info(`setProfileNickname invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`setProfileNickname, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.resetMemory<sup>18+</sup>

resetMemory\(slotId: number, options?: ResetOption\): Promise\<ResultCode\>

Clears all specific profiles and resets the eUICC. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.SET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ----- | ----- |
| slotId  | number                        | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|
| options | [ResetOption](#resetoption18) | No| Reset options.|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode18)\> | Promise used to return the operation result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.resetMemory(1).then(() => {
    console.info(`resetMemory invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`resetMemory, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.reserveProfilesForFactoryRestore<sup>18+</sup>

reserveProfilesForFactoryRestore\(slotId: number\): Promise\<ResultCode\>

Restores factory settings and retains profiles. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.SET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ----- | ----- |
| slotId | number | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode18)\> | Promise used to return the operation result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.reserveProfilesForFactoryRestore(1).then(() => {
    console.info(`reserveProfilesForFactoryRestore invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`reserveProfilesForFactoryRestore, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.setDefaultSmdpAddress<sup>18+</sup>

setDefaultSmdpAddress\(slotId: number, address: string\): Promise\<ResultCode\>

Sets or updates the default SM-DP+ address stored in the eUICC. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.SET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ----- | ----- |
| slotId  | number | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|
| address | string | Yes| Default SM-DP+ address.|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode18)\> | Promise used to return the operation result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.setDefaultSmdpAddress(1, 'testAddress').then(() => {
    console.info(`setDefaultSmdpAddress invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`setDefaultSmdpAddress, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.getDefaultSmdpAddress<sup>18+</sup>

getDefaultSmdpAddress\(slotId: number\): Promise\<string\>

Obtains the default SM-DP+ address stored in the eUICC. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ----- | ----- |
| slotId | number | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<string\> | Promise used to return the SM-DP+ address.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs. |
| 401 | Invalid parameter value.|
| 801 | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.getDefaultSmdpAddress(1).then((data: string) => {
    console.info(`getDefaultSmdpAddress, result: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`getDefaultSmdpAddress, ErrorState: err->${JSON.stringify(err)}`);
});
```

## eSIM.cancelSession<sup>18+</sup>

cancelSession\(slotId: number, transactionId: string, cancelReason: CancelReason\): Promise\<ResultCode\>

Cancels a session. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.SET_TELEPHONY_ESIM_STATE

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ----- | ----- |
| slotId        | number                          | Yes| Card slot ID.<br>- **0**: card slot 1.<br>- **1**: card slot 2|
| transactionId | string                          | Yes| Service ID.|
| cancelReason  | [CancelReason](#cancelreason18) | Yes| Reason for canceling the session.|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<[ResultCode](#resultcode18)\> | Promise used to return the operation result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                | Error Message                              |
| --------------------- | ---------------------------------- |
| 201   | Permission denied. |
| 202   | Non-system applications use system APIs. |
| 401   | Invalid parameter value.|
| 801   | Capability not supported. |
|3120001| Service connection failed. |
|3120002| System internal error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

let transactionId = '';
eSIM.cancelSession(1, transactionId, eSIM.CancelReason.CANCEL_REASON_END_USER_REJECTION)
  .then((data: eSIM.ResultCode) => {
    console.info(`cancelSession, result: data->${JSON.stringify(data)}`);
  })
  .catch((err: BusinessError<void>) => {
    console.error(`cancelSession execution failed: err->${JSON.stringify(err)}`);
  });
```

## GetDownloadableProfileMetadataResult<sup>18+</sup>

Obtains the metadata of the downloadable profile.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Type                                       | Read-Only| Optional| Description|
| ----- |-------------------------------------------|---| ---- | -----|
| downloadableProfile | [DownloadableProfile](./js-apis-esim.md#downloadableprofile18) | No| No| Downloadable profile.  |
| pprType             | number                     | No| No| Profile policy rule type.|
| pprFlag             | boolean                    | No| No| Whether the profile has a policy rule. The value **true** indicates that the the profile has a policy rule, and the value **false** indicates the opposite.|
| iccid               | string                     | No| No| Profile ICCID.   |
| serviceProviderName | string                     | No| No| Service provider name.|
| profileName         | string                     | No| No| Profile name.|
| profileClass        | [ProfileClass](#profileclass18)        | No| No| Profile class. |
| solvableErrors      | [SolvableErrors](#solvableerrors18)      | No| No| Solvable errors.|
| responseResult      | [ResultCode](#resultcode18)         | No| No| Operation result code. |

## GetDownloadableProfilesResult<sup>18+</sup>

Obtains the list of default downloadable profiles.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Type                                               | Read-Only| Optional| Description|
| ----- |---------------------------------------------------|---| ----- | -----|
| responseResult       | [ResultCode](#resultcode18)                   | No| No| Promise used to return the operation result.    |
| downloadableProfiles | Array\<[DownloadableProfile](./js-apis-esim.md#downloadableprofile18)\> | No| No| Downloadable file array.|

## DownloadProfileResult<sup>18+</sup>

Defines the profile download result.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Type                                 | Read-Only| Optional| Description|
| ----- |-------------------------------------|----|---| -----|
| responseResult | [ResultCode](#resultcode18)         | No | No| Operation result code.|
| solvableErrors | [SolvableErrors](#solvableerrors18) | No | No| Solvable errors.|
| cardId         | number                | No | No| Card ID.|

## GetEuiccProfileInfoListResult<sup>18+</sup>

Obtains the profile information list.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Type                                    | Read-Only| Optional| Description  |
| ----- |----------------------------------------|---| ---- |------|
| responseResult  | [ResultCode](#resultcode18)            | No| No| Promise used to return the operation result.   |
| profiles        | Array\<[EuiccProfile](#euiccprofile18)\> | No| No| Profile array.    |
| isRemovable     | boolean                      | No| No| Whether the eUICC is removable. The value **true** indicates that the eUICC is removable, and the value **false** indicates the opposite.|

## OperatorId<sup>18+</sup>

Obtains information about the eUICC chip or device.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Type| Read-Only| Optional| Description|
| ----- | ----- |---| ----- | -----|
| mcc  | string | No| No| Mobile country code (MCC).|
| mnc  | string | No| No| Network code.   |
| gid1 | string | No| No| Group ID level 1. |
| gid2 | string | No| No| Group ID level 2. |

## EuiccProfile<sup>18+</sup>

Profile information.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Type                                                   | Read-Only| Optional| Description|
| ----- |-------------------------------------------------------|---|---- |  -----|
| iccid               | string                                                | No| No| Profile ICCID.|
| nickName            | string                                                | No| No| Profile nickname.|
| serviceProviderName | string                                                | No| No| Service provider name.|
| profileName         | string                                                | No| No| Profile name.  |
| state               | [ProfileState](#profilestate18)                       | No| No| Profile status.|
| profileClass        | [ProfileClass](#profileclass18)                       | No| No| Profile class.    |
| operatorId          | [OperatorId](#operatorid18)                           | No| No| Operation ID of the profile.|
| policyRules         | [PolicyRules](#policyrules18)                         | No| No| Profile policy rules.  |
| accessRules         | Array\<[AccessRule](./js-apis-esim.md#accessrule20)\> | No| No| Profile access rules.  |

## EuiccInfo<sup>18+</sup>

Defines the eUICC information.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Type| Read-Only| Optional| Description|
| ----- | ----- |----|----| -----|
| osVersion | string | No | No | OS version.|

## ResetOption<sup>18+</sup>

Defines the reset options.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Value| Description|
| ----- | ----- | ----- |
|DELETE_OPERATIONAL_PROFILES       | 1      | Deletion of all operational profiles.|
|DELETE_FIELD_LOADED_TEST_PROFILES | 1 << 1 | Deletion of the downloaded test profiles.|
|RESET_DEFAULT_SMDP_ADDRESS        | 1 << 2 | Resetting of the default SM-DP+ address.|

## OsuStatus<sup>18+</sup>

Defines the OS upgrade status.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Value| Description|
| ----- | ----- | ----- |
|EUICC_UPGRADE_IN_PROGRESS         | 1 | Upgrading.|
|EUICC_UPGRADE_FAILED              | 2 | Upgrade failed.|
|EUICC_UPGRADE_SUCCESSFUL          | 3 | Update succeeded.|
|EUICC_UPGRADE_ALREADY_LATEST      | 4 | Already the latest version.|
|EUICC_UPGRADE_SERVICE_UNAVAILABLE | 5 | Update service unavailable.|

## ResultCode<sup>18+</sup>

Enumerates the result codes.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Value| Description|
| ----- | ----- | ----- |
| RESULT_SOLVABLE_ERRORS                                   | -2  | Solving of the solvable errors required.       |
| RESULT_MUST_DISABLE_PROFILE                              | -1  | Disabling of the active profile required.|
| RESULT_OK                                                | 0   | Operation success.|
| RESULT_GET_EID_FAILED                                    | 201 | Failed to obtain the EID.|
| RESULT_ACTIVATION_CODE_CHANGED                           | 203 | Activation code changed upon user confirmation.  |
| RESULT_ACTIVATION_CODE_INVALID                           | 204 | Invalid activation code. |
| RESULT_SMDP_ADDRESS_INVALID                              | 205 | Invalid SM-DP+ server address.|
| RESULT_EUICC_INFO_INVALID                                | 206 | Invalid eUICC information.     |
| RESULT_TLS_HANDSHAKE_FAILED                              | 207 | TLS handshake failed.         |
| RESULT_CERTIFICATE_IO_ERROR                              | 208 | Certificate network connection error.     |
| RESULT_CERTIFICATE_RESPONSE_TIMEOUT                      | 209 | Invalid certificate address or response timeout.|
| RESULT_AUTHENTICATION_FAILED                             | 210 | Authentication failed.    |
| RESULT_RESPONSE_HTTP_FAILED                              | 211 | HTTP response failed.|
| RESULT_CONFIRMATION_CODE_INCORRECT                       | 212 | Incorrect confirmation code.|
| RESULT_EXCEEDED_CONFIRMATION_CODE_TRY_LIMIT              | 213 | Maximum confirmation code retries reached.     |
| RESULT_NO_PROFILE_ON_SERVER                              | 214 | No downloadable profile available on the server.|
| RESULT_TRANSACTION_ID_INVALID                            | 215 | Invalid transaction ID.   |
| RESULT_SERVER_ADDRESS_INVALID                            | 216 | Invalid server address.|
| RESULT_GET_BOUND_PROFILE_PACKAGE_FAILED                  | 217 | Failed to obtain the BPP.   |
| RESULT_USER_CANCEL_DOWNLOAD                              | 218 | Download cancelled by the user.  |
| RESULT_SERVER_UNAVAILABLE                                | 220 | Carrier server unavailable.|
| RESULT_PROFILE_NON_DELETE                                | 223 | File deletion not allowed by the PPR rule.   |
| RESULT_SMDP_ADDRESS_INCORRECT                            | 226 | Incorrect SMDP server address.  |
| RESULT_ANALYZE_AUTHENTICATION_SERVER_RESPONSE_FAILED     | 228 | Failed to parse the server authentication response.|
| RESULT_ANALYZE_AUTHENTICATION_CLIENT_RESPONSE_FAILED     | 229 | Failed to parse the client authentication response.|
| RESULT_ANALYZE_AUTHENTICATION_CLIENT_MATCHING_ID_REFUSED | 231 | Failed to parse the client authentication response because the matching ID was rejected.|
| RESULT_PROFILE_TYPE_ERROR_AUTHENTICATION_STOPPED         | 233 | Authentication stopped due to incorrect profile type.    |
| RESULT_CARRIER_SERVER_REFUSED_ERRORS                     | 249 | Rejection cause code of the carrier server, which is 3.8.|
| RESULT_CERTIFICATE_INVALID                               | 251 | Invalid certificate.|
| RESULT_OUT_OF_MEMORY                                     | 263 | Failed to install the profile due to insufficient memory.|
| RESULT_PPR_FORBIDDEN                                     | 268 | Operation not allowed by the PPR rule.|
| RESULT_NOTHING_TO_DELETE                                 | 270 | No configuration file for deletion.|
| RESULT_PPR_NOT_MATCH                                     | 276 | PPR rule mismatch.  |
| RESULT_CAT_BUSY                                          | 283 | Session in progress.  |
| RESULT_PROFILE_EID_INVALID                               | 284 | eSIM profile in use or invalid.|
| RESULT_DOWNLOAD_TIMEOUT                                  | 287 | Download timeout.                  |
| RESULT_SGP_22_OTHER                                      | 400 | Other errors defined in SGP.22.     |

## CancelReason<sup>18+</sup>

Reason for canceling the session.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Value| Description|
| ----- | ----- | ----- |
|CANCEL_REASON_END_USER_REJECTION | 0 | The user has rejected the download.         |
|CANCEL_REASON_POSTPONED          | 1 | The download has been delayed. You can restart it later.|
|CANCEL_REASON_TIMEOUT            | 2 | The download has timed out. You can restart it later.|
|CANCEL_REASON_PPR_NOT_ALLOWED    | 3 | The installation cannot be performed because the authorization table or other installed profile on the eUICC does not allow its policy rules.|

## ProfileState<sup>18+</sup>

Enumerates the profile states.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Value| Description|
| ----- | ----- | ----- |
|PROFILE_STATE_UNSPECIFIED | -1 | Profile status unspecified.|
|PROFILE_STATE_DISABLED    | 0  | Profile disabled.  |
|PROFILE_STATE_ENABLED     | 1  | Profile enabled.|

## ProfileClass<sup>18+</sup>

Enumerates the profile classes.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Value| Description|
| ----- | ----- | ----- |
|PROFILE_CLASS_UNSPECIFIED  | -1 | Profile class unspecified.          |
|PROFILE_CLASS_TEST         | 0  | Test profile.              |
|PROFILE_CLASS_PROVISIONING | 1  | Profile preloaded to the eUICC.  |
|PROFILE_CLASS_OPERATIONAL  | 2  | Profile that can be preloaded or downloaded.|

## PolicyRules<sup>18+</sup>

Enumerates the profile policy rules.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Value| Description|
| ----- | ----- | ----- |
|POLICY_RULE_DISABLE_NOT_ALLOWED | 1      | A profile cannot be disabled after being enabled.|
|POLICY_RULE_DELETE_NOT_ALLOWED  | 1 << 1 | The profile cannot be deleted.         |
|POLICY_RULE_DISABLE_AND_DELETE  | 1 << 2 | A profile must be deleted immediately after being enabled.     |

## SolvableErrors<sup>18+</sup>

Enumerates the solvable errors.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Value| Description|
| ----- | ----- | ----- |
|SOLVABLE_ERROR_NEED_CONFIRMATION_CODE | 1 << 0 | The user needs to enter the confirmation code during the download.               |
|SOLVABLE_ERROR_NEED_POLICY_RULE       | 1 << 1 | The download process requires user consent to allow the profile policy rules.|

## DownloadConfiguration<sup>18+</sup>

Defines the download configuration.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Type| Read-Only| Optional| Description|
| ----- | ----- |----| ----- | -----|
|switchAfterDownload | boolean | No | No| Whether to enable the profile after successful download. The value **true** means to enable the default profile, and the value **false** means the opposite.|
|forceDisableProfile | boolean | No | No| Whether to forcibly deactivate the current profile during profile switching.<br> **true**: The current profile is forcibly deactivated, and profile switching can be directly performed.<br> **false**: An error is returned, and profile switching can be performed only after the user authorization is obtained.|
|isPprAllowed        | boolean | No | No| Whether user authorization is obtained to implement the profile policy rule. The value **true** indicates that user authorization is obtained, and the value **false** indicates the opposite.|
