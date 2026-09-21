# changeAppCloudSwitch (System API)

## Modules to Import

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## changeAppCloudSwitch

```TypeScript
function changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean): Promise<void>
```

Changes the device-cloud file sync switch for an application. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | Account ID. |
| bundleName | string | Yes | Bundle name. |
| status | boolean | Yes | State of the cloud-device file sync switch to set. The value **true** means to enable this function; the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let bundleName: string = "com.example.bundle";
cloudSyncManager.changeAppCloudSwitch(accountId, bundleName, true).then(() => {
  console.info("changeAppCloudSwitch successfully");
}).catch((err: BusinessError) => {
  console.error("changeAppCloudSwitch failed with error message: " + err.message + ", error code: " + err.code);
});
```


<a id="changeappcloudswitch-1"></a>

## changeAppCloudSwitch

```TypeScript
function changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean, callback: AsyncCallback<void>): void
```

Changes the device-cloud file sync switch for an application. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | Account ID. |
| bundleName | string | Yes | Bundle name of the application. |
| status | boolean | Yes | State of the cloud-device file sync switch to set. The value **true** means to enable this function; the value **false** means the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result of changing the device-cloud file sync switch for an application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let bundleName: string = "com.example.bundle";
cloudSyncManager.changeAppCloudSwitch(accountId, bundleName, true, (err: BusinessError) => {
  if (err) {
    console.error("changeAppCloudSwitch failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("changeAppCloudSwitch successfully");
  }
});
```
