# decompressFile

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## decompressFile

```TypeScript
function decompressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback<void>): void
```

Decompresses a file. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> To avoid path traversal, the input parameters of **inFile** and **outFile** cannot contain two consecutive
> periods and a slash (../) since API version 13. Otherwise, error codes 900001 and 900002 are returned.
> 
> The name of the zipped file or zipped folder cannot contain two consecutive periods and a slash (../). Otherwise,
> the error code 900003 is returned.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inFile | string | Yes | Path of the file to decompress. The file name extension must be .zip. The path must be an application sandbox path, which can be obtained from the context. For details about the context, see FA Model and Stage Model. If the.zip file to be unzipped contains Chinese file names or folder names, use UTF-8 to encode them. Otherwise, garbled characters may be displayed after unzipping. |
| outFile | string | Yes | Path of the decompressed file. The path must exist in the system. Otherwise, the decompression fails. The path must be an application sandbox path, which can be obtained from the context. For details about the context, see FA Model and Stage Model. If a file or folder with the same name already exists in the path, they will be overwritten. When multiple threads decompress files at the same time, the values of **outFile** must be different. |
| options | [Options](arkts-basicservices-zlib-options-i.md) | Yes | Decompression parameters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **null** is returned; otherwise, a specific error code is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [900001](../errorcode-zlib.md#900001-invalid-source-file) | The input source file is invalid. |
| [900002](../errorcode-zlib.md#900002-invalid-destination-file) | The input destination file is invalid. |
| [900003](../errorcode-zlib.md#900003-source-file-in-incorrect-format-or-damaged) | The input source file is not in ZIP format or is damaged.<br>**Applicable version:** 10 and later |

**Examples**

```TypeScript
// The path used in the code must be an application sandbox path, for example, /data/storage/el2/base/temp. You can obtain the path through the context.
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/data/storage/el2/base/temp/xxx.zip';
let outFileDir = '/data/storage/el2/base/temp';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  parallel: zlib.ParallelStrategy.PARALLEL_STRATEGY_PARALLEL_DECOMPRESSION
};

try {
  zlib.decompressFile(inFile, outFileDir, options, (errData: BusinessError) => {
    if (errData !== null) {
      console.error(`decompressFile errData is errCode:${errData.code}  message:${errData.message}`);
    } else {
      console.info(`decompressFile success.`);
    }
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`decompressFile errData is errCode:${code}  message:${message}`);
}
```


<a id="decompressfile-1"></a>

## decompressFile

```TypeScript
function decompressFile(inFile: string, outFile: string, callback: AsyncCallback<void>): void
```

Decompresses a file. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> To avoid path traversal, the input parameters of **inFile** and **outFile** cannot contain two consecutive
> periods and a slash (../) since API version 13. Otherwise, error codes 900001 and 900002 are returned.
> 
> The name of the zipped file or zipped folder cannot contain two consecutive periods and a slash (../). Otherwise,
> the error code 900003 is returned.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inFile | string | Yes | Path of the file to decompress. The file name extension must be .zip. The path must be an application sandbox path, which can be obtained from the context. For details about the context, see FA Model and Stage Model. If the.zip file to be unzipped contains Chinese file names or folder names, use UTF-8 to encode them. Otherwise, garbled characters may be displayed after unzipping. |
| outFile | string | Yes | Path of the decompressed file. The path must exist in the system. Otherwise, the decompression fails. The path must be an application sandbox path, which can be obtained from the context. For details about the context, see FA Model and Stage Model. If a file or folder with the same name already exists in the path, they will be overwritten. When multiple threads decompress files at the same time, the values of **outFile** must be different. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **null** is returned; otherwise, a specific error code is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [900001](../errorcode-zlib.md#900001-invalid-source-file) | The input source file is invalid. |
| [900002](../errorcode-zlib.md#900002-invalid-destination-file) | The input destination file is invalid. |
| [900003](../errorcode-zlib.md#900003-source-file-in-incorrect-format-or-damaged) | The input source file is not in ZIP format or is damaged. |

**Examples**

```TypeScript
// The path used in the code must be an application sandbox path, for example, /data/storage/el2/base/temp. You can obtain the path through the context.
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/data/storage/el2/base/temp/xxx.zip';
let outFileDir = '/data/storage/el2/base/temp';

try {
  zlib.decompressFile(inFile, outFileDir, (errData: BusinessError) => {
    if (errData !== null) {
      console.error(`decompressFile failed. code is ${errData.code}, message is ${errData.message}`);
    } else {
      console.info(`decompressFile success.`);
    }
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`decompressFile failed. code is ${code}, message is ${message}`);
}
```


<a id="decompressfile-2"></a>

## decompressFile

```TypeScript
function decompressFile(inFile: string, outFile: string, options?: Options): Promise<void>
```

Decompresses a file. This API uses a promise to return the result.

> **NOTE:** 
> 
> To avoid path traversal, the input parameters of **inFile** and **outFile** cannot contain two consecutive
> periods and a slash (../) since API version 13. Otherwise, error codes 900001 and 900002 are returned.
> 
> The name of the zipped file or zipped folder cannot contain two consecutive periods and a slash (../). Otherwise,
> the error code 900003 is returned.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inFile | string | Yes | Path of the file to decompress. The file name extension must be .zip. The path must be an application sandbox path, which can be obtained from the context. For details about the context, see FA Model and Stage Model. If the.zip file to be unzipped contains Chinese file names or folder names, use UTF-8 to encode them. Otherwise, garbled characters may be displayed after unzipping. |
| outFile | string | Yes | Path of the decompressed file. The path must exist in the system. Otherwise, the decompression fails. The path must be an application sandbox path, which can be obtained from the context. For details about the context, see FA Model and Stage Model. If a file or folder with the same name already exists in the path, they will be overwritten. When multiple threads decompress files at the same time, the values of **outFile** must be different. |
| options | [Options](arkts-basicservices-zlib-options-i.md) | No | Decompression parameters. |

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
| [900003](../errorcode-zlib.md#900003-source-file-in-incorrect-format-or-damaged) | The input source file is not in ZIP format or is damaged.<br>**Applicable version:** 10 and later |

**Examples**

```TypeScript
// The path used in the code must be an application sandbox path, for example, /data/storage/el2/base/temp. You can obtain the path through the context.
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/data/storage/el2/base/temp/xxx.zip';
let outFileDir = '/data/storage/el2/base/temp';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION
};

try {
  zlib.decompressFile(inFile, outFileDir, options).then((data: void) => {
    console.info('decompressFile success. data: ' + JSON.stringify(data));
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```
