# compressFiles

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## compressFiles

```TypeScript
function compressFiles(inFiles: Array<string>, outFile: string, options: Options): Promise<void>
```

Compresses multiple specified files. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inFiles | Array&lt;string&gt; | Yes | Path of the folder or file to compress. The path must be an application sandbox path, which can be obtained from the context. For details about the context, see FA Model and Stage Model. The folder to compress cannot be empty. Otherwise, an error will be reported when [decompressFile](arkts-basicservices-zlib-decompressfile-f.md) is used to decompress the folder. |
| outFile | string | Yes | Path of the compressed file. When multiple threads compress files at the same time, the values of **outFile** must be different. |
| options | [Options](arkts-basicservices-zlib-options-i.md) | Yes | Compression parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [900001](../errorcode-zlib.md#900001-invalid-source-file) | The input source file is invalid. |
| [900002](../errorcode-zlib.md#900002-invalid-destination-file) | The input destination file is invalid. |

**Examples**

```TypeScript
// The path used in the code must be an application sandbox path, for example, /data/storage/el2/base/temp. You can obtain the path through the context.
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/data/storage/el2/base/temp/filename.xxx';
let pathDir = 'data/storage/el2/base/temp/xxx';
let outFile = '/data/storage/el2/base/temp/xxx.zip';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  memLevel: zlib.MemLevel.MEM_LEVEL_DEFAULT,
  strategy: zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY
};

try {
  zlib.compressFiles([inFile, pathDir], outFile, options).then((data: void) => {
    console.info('compressFiles success. data: ' + JSON.stringify(data));
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```
