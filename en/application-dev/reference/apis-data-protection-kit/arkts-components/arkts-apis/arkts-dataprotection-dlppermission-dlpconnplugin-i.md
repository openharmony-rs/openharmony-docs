# DlpConnPlugin

```TypeScript
export interface DlpConnPlugin
```

Registers the callback capability with the system ability (SA). This API is used in the **registerPlugin** API.

> **NOTE:** 
> 
> [registerPlugin](arkts-dataprotection-dlppermission-dlpconnmanager-c.md#registerplugin) requires identical parameters to this API.
> [connectServer](#connectserver) is called by the SA and the parameters are
> returned through the callback.

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## connectServer

```TypeScript
connectServer(requestId: string, requestData: string, callback: Callback<string>): void
```

This API is called by the SA. After the request of connecting to the cloud server is processed, the result is returned the SA using a callback.

This API can be used in enterprise account authentication and cloud permission verification to enable communication between the SA and the cloud server.

> **NOTE:** 
> 
> **connectServer** indicates a call from the system capability side to the frontend.

**Since:** 21

**Required permissions:** 
- API version 26 and later: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE
- API version 25: N/A
- API versions 21 to 24: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| requestId | string | Yes | ID of the request transferred by the SA. No value range restriction is specified. |
| requestData | string | Yes | Data transferred by the SA. No value range restriction is specified. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | Yes | API transferred by the SA, which is used for callback. No value range restriction is specified. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.0.1 and later |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { Callback } from '@kit.BasicServicesKit';

export default class DataCapsulePlugin implements dlpPermission.DlpConnPlugin {
  constructor() {
  }

  connectServer(requestId: string, requestData: string, callback: Callback<string>): void {
    let callbackJson = JSON.stringify({
      'requestId': requestId,
    }); // Construct callback JSON data.
    callback(callbackJson);  // Use a callback to return the result.
  }
}

let plugin: dlpPermission.DlpConnPlugin = new DataCapsulePlugin();
```
