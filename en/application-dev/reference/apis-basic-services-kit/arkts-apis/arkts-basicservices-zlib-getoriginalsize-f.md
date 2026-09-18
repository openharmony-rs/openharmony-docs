# getOriginalSize

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## getOriginalSize

```TypeScript
function getOriginalSize(compressedFile: string): Promise<number>
```

Obtains the original size of a compressed file. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| compressedFile | string | Yes | Specifies the path of the compressed file. Only .zip files are supported. The path must be an application sandbox path, which can be obtained from the context. For details about the context, see FA Model and Stage Model. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise object, which returns the original size of the compressed file, in bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [900001](../errorcode-zlib.md#900001-invalid-source-file) | The input source file is invalid. |
| [900003](../errorcode-zlib.md#900003-source-file-in-incorrect-format-or-damaged) | The input source file is not in ZIP format or is damaged. |

**Examples**

```TypeScript
// The path used in the code must be an application sandbox path, for example, /data/storage/el2/base/temp. You can obtain the path through the context.
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let compressedFile = '/data/storage/el2/base/temp/test.zip';

try {
  zlib.getOriginalSize(compressedFile).then((data: number) => {
    console.info(`getOriginalSize success. getOriginalSize: ${data}`);
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```
