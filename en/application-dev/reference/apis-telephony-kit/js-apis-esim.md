# @ohos.telephony.esim (eSIM Management)
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @Fanyl8-->
<!--Designer: @ghxbob-->
<!--Tester: @weitiantian-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4f8760cdae422e4c4515ece5a32cd4a968efd09f translatedAt=2026-11-03T03:51:23.214Z pushedAt=2026-11-03T08:57:51.511Z nl=1 -->

This module provides basic eSIM card management capabilities, including checking whether a specified card slot supports the eSIM function and, if supported, allowing users to add a single profile.

> **NOTE**
>
> The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>

## Modules to Import

```ts
import { eSIM } from '@kit.TelephonyKit';
```

## eSIM.isSupported

isSupported\(slotId: number\): boolean

Checks whether a specified card slot supports the eSIM function. In the debug version, **eSIM.isSupported** always returns **false**. In the release version, it returns a value based on the actual device support.

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| slotId | number | Yes  | Card slot ID. <br>- **0**: card slot 1.<br>- **1**: card slot 2|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| boolean | Whether the specified card slot supports the eSIM function. If yes, **true** is returned. If no, **false** is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID             | Error Message                          |
| --------------------- | ---------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.   |
|3120001| Service connection failed. |
|3120002| System internal error.     |

**Example**

```ts
import { eSIM } from '@kit.TelephonyKit';

let isSupported: boolean = eSIM.isSupported(1);
console.info(`the esim is Supported:` + isSupported);
```

## eSIM.addProfile

addProfile\(profile: DownloadableProfile\): Promise\<boolean\>

When a user needs to activate a new eSIM (for example, when opening a new account or changing cards), call this API to guide the process of downloading and adding a profile.

**Required permissions**: ohos.permission.SET_TELEPHONY_ESIM_STATE_OPEN

**System capability**: SystemCapability.Telephony.CoreService.Esim

**Parameters**

| Name| Type                                           | Mandatory| Description                                  |
| ------ |-----------------------------------------------| ---- | -------------------------------------- |
| profile | [DownloadableProfile](#downloadableprofile) | Yes  | Profile that can be downloaded.|

**Returns**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<boolean\> | Promise used to return the result of adding a single profile. The value **true** indicates success, and **false** indicates failure. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID             | Error Message                          |
| --------------------- | ---------------------------------- |
| 201 | Permission denied.           |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.     |
| 801 | Capability not supported.    |
|3120001| Service connection failed. |
|3120002| System internal error.     |

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

eSIM.addProfile(profile).then((result: boolean) => {
    console.info(`addProfile invoking succeeded.`);
}).catch((err: BusinessError) => {
    console.error(`addProfile, promise: err->${JSON.stringify(err)}`);
});
```

## DownloadableProfile

Defines a downloadable profile.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Type                                  |  Read-Only| Optional| Description|
| ----- |--------------------------------------| ----- | ---- | -----|
| activationCode   | string                               |  No |  No | Activation code. For a profile that does not require an activation code, the value may be left empty.|
| confirmationCode | string                               |  No  |  Yes  | Confirmation code. This parameter is an empty string by default when no value is passed in. |
| carrierName      | string                               |  No  |  Yes  | Subscription name. This parameter is an empty string by default when no value is passed in.   |
| accessRules      | Array\<[AccessRule](#accessrule20)\> |  No  |  Yes  | Array of access rules. This parameter is an empty array by default when no value is passed in. |

## AccessRule<sup>20+</sup>

Defines access rules.

**System capability**: SystemCapability.Telephony.CoreService.Esim

| Name| Type| Read-Only| Optional| Description|
| ----- | ----- |----|----| -----|
| certificateHashHexStr | string  | No  | No  | Certificate hash in the form of a Hexadecimal string. The value contains 40 or 64 characters, consisting of digits 0-9 and letters a-f (or A-F) only. |
| packageName           | string  | No | No | Package name.|
| accessType            | number  | No | No | Rule type.|