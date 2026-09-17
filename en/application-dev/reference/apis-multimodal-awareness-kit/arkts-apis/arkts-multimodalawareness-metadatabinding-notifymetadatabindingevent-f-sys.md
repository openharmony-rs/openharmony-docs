# notifyMetadataBindingEvent (System API)

## Modules to Import

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## notifyMetadataBindingEvent

```TypeScript
function notifyMetadataBindingEvent(bundleName: string): Promise<string>
```

Transfers metadata to the application or service that calls the encoding API. This API uses a promise to return the result.

**Since:** 18

**System capability:** SystemCapability.MultimodalAwareness.MetadataBinding

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name used to obtain the application link. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the application link information of the current page. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission check failed. A non-system application uses the system API. |
| [32100001](../errorcode-metadataBinding.md#32100001-file-creation-failed) | Internal handling failed. |

**Examples**

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = '';
metadataBinding.notifyMetadataBindingEvent(bundleName).then((appLink:string)=>{
  console.info("notify metadata:" + appLink);
}).catch((error: BusinessError) => {
  console.error("notify metadata error" + error);
});
```
