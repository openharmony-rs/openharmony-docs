# getDLPGatheringPolicy (System API)

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## getDLPGatheringPolicy

```TypeScript
function getDLPGatheringPolicy(): Promise<GatheringPolicyType>
```

Obtains the DLP sandbox gathering policy. This API uses a promise to return the result.

This API is used to obtain the DLP sandbox gathering policy of the current system.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[GatheringPolicyType](arkts-dataprotection-dlppermission-gatheringpolicytype-e-sys.md)&gt; | Promise used to return the DLP sandbox gathering policy obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getDLPGatheringPolicy().then((gatheringPolicy: dlpPermission.GatheringPolicyType) => {
  console.info('gatheringPolicy: ', JSON.stringify(gatheringPolicy));
}).catch((error: BusinessError) => {
  console.error(`Failed to get DLPGatheringPolicy. Code: ${error.code}, message: ${error.message}`);
}); // Obtain the sandbox gathering policy.
```

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getDLPGatheringPolicy((err, gatheringPolicy) => {
  if (err) {
    console.error(`Failed to get DLPGatheringPolicy. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('gatheringPolicy: ', JSON.stringify(gatheringPolicy));
  }
}); // Obtain the sandbox gathering policy.
```


## getDLPGatheringPolicy

```TypeScript
function getDLPGatheringPolicy(callback: AsyncCallback<GatheringPolicyType>): void
```

Obtains the DLP sandbox gathering policy. This API uses an asynchronous callback to return the result.

This API is used to obtain the DLP sandbox gathering policy of the current system.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[GatheringPolicyType](arkts-dataprotection-dlppermission-gatheringpolicytype-e-sys.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

See [getDLPGatheringPolicy](#getdlpgatheringpolicy)
