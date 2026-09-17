# addProfile

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## addProfile

```TypeScript
function addProfile(profile: DownloadableProfile): Promise<boolean>
```

Launches the download page for the user to add a single profile. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.SET_TELEPHONY_ESIM_STATE_OPEN

**System capability:** SystemCapability.Telephony.CoreService.Esim

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| profile | [DownloadableProfile](arkts-telephony-esim-downloadableprofile-i.md) | Yes | Profile that can be downloaded. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3120001](../errorcode-telephony.md#3120001-service-connection-error) | Service connection failed. |
| [3120002](../errorcode-telephony.md#3120002-system-internal-error) | System internal error. |

**Examples**

```TypeScript
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

eSIM.addProfile(profile).then(() => {
    console.info(`addProfile invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`addProfile, promise: err->${JSON.stringify(err)}`);
});
```
