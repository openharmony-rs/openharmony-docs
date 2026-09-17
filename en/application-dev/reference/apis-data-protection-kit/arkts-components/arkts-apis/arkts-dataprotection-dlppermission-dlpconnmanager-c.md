# DlpConnManager

Calls **registerPlugin** and **unregisterPlugin** to register or unregister callback capabilities in the SA.

> **NOTE:** 
> 
> **registerPlugin** registers callback capabilities in the SA, and **unregisterPlugin** unregisters callback
> capabilities from the SA.

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## constructor

```TypeScript
constructor()
```

Represents a constructor for instantiating [DlpConnManager](arkts-dataprotection-dlppermission-dlpconnmanager-c.md).

**Since:** 21

**Required permissions:** 
- API version 26 and later: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE
- API version 25: N/A
- API versions 21 to 24: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let dlpConnManager: dlpPermission.DlpConnManager = new dlpPermission.DlpConnManager();
```

## registerPlugin

```TypeScript
static registerPlugin(plugin: DlpConnPlugin): number
```

Registers a callback with the SA.

> **NOTE:** 
> 
> **registerPlugin** registers the callback with the SA.

**Since:** 21

**Required permissions:** 
- API version 26 and later: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE
- API version 25: N/A
- API versions 21 to 24: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| plugin | [DlpConnPlugin](arkts-dataprotection-dlppermission-dlpconnplugin-i.md) | Yes | Callback plugin object, which is used to register the callback capability with the SA. The **DlpConnPlugin** API needs to be inherited and the **connectServer** method needs to be implemented so that the processing result can be returned using a callback when the API is called on the SA. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Registration result. The unique ID of the callback is returned. The value range is [0, 2&lt;sup&gt;53&lt;/sup&gt;-1]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100002](../errorcode-dlp.md#19100002-encryption-and-decryption-error) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../errorcode-dlp.md#19100003-encryptiondecryption-timeout) | Credential task time out. |
| [19100004](../errorcode-dlp.md#19100004-credential-service-error) | Credential service error. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { Callback } from '@kit.BasicServicesKit';

export default class DataCapsulePlugin implements dlpPermission.DlpConnPlugin {
  private accountId: string;
  private accountName: string;
  constructor() {
    this.accountId = 'accountId'; // Initialize account information.
    this.accountName = 'accountName';
  }

  connectServer(requestId: string, requestData: string, callback: Callback<string>): void {
    let callbackJson = JSON.stringify({
      'requestId': requestId,
    });
    callback(callbackJson);
  }
}
  
let pluginId: number = dlpPermission.DlpConnManager.registerPlugin(new DataCapsulePlugin());
```

## unregisterPlugin

```TypeScript
static unregisterPlugin(): void
```

Unregisters a callback from the SA.

This API unregisters a callback and releases resources when an application exits.

> **NOTE:** 
> 
> **unregisterPlugin** unregisters a plug-in from the SA.

**Since:** 21

**Required permissions:** 
- API version 26 and later: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE
- API version 25: N/A
- API versions 21 to 24: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100002](../errorcode-dlp.md#19100002-encryption-and-decryption-error) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../errorcode-dlp.md#19100003-encryptiondecryption-timeout) | Credential task time out. |
| [19100004](../errorcode-dlp.md#19100004-credential-service-error) | Credential service error. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.DlpConnManager.unregisterPlugin();
```
