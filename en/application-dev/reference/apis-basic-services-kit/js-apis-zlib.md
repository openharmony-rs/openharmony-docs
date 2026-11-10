# @ohos.zlib (Zip)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b33c416f2dabc1fc4149b71a7ef553e301b3c3cc translatedAt=2026-11-10T04:27:57.038Z pushedAt=2026-11-10T07:10:14.413Z nl=1 -->

This module is developed based on the zlib library and provides file compression and decompression capabilities. It uses the DEFLATE algorithm and supports data processing in zlib, deflate, and gzip formats.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```javascript
import { zlib } from '@kit.BasicServicesKit';
```

## zlib.zipFile<sup>(deprecated)</sup>
zipFile(inFile: string, outFile: string, options: Options): Promise&lt;void&gt;

Zips a file. The execution result is returned after the compression is complete. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [zlib.compressFile](#zlibcompressfile9) instead.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile  | string              | Yes   | Folder path or file path to be compressed. The path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md). |
| outFile | string              | Yes   | File path of the compressed file (with the .zip extension). The path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md).                  |
| options | [Options](#options) | Yes  | Optional parameters for the zip operation.                                            |

**Return value**

| Type          | Description                                                        |
| -------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
// The path used in the code must be an application sandbox path, for example, /data/storage/el2/base/temp. You can obtain the path through the context.
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/data/storage/el2/base/temp/filename.xxx';
let outFile = '/data/storage/el2/base/temp/xxx.zip';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  memLevel: zlib.MemLevel.MEM_LEVEL_DEFAULT,
  strategy: zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY
};

zlib.zipFile(inFile, outFile, options).then((data: void) => {
  console.info('zipFile result is ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error('error is ' + JSON.stringify(err));
});
```

## zlib.unzipFile<sup>(deprecated)</sup>

unzipFile(inFile:string, outFile:string, options: Options): Promise&lt;void&gt;

Unzips a file. The execution result is returned after the decompression is complete. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [zlib.decompressFile](#zlibdecompressfile9) instead.
>
> The name of the zipped file or zipped folder cannot contain two consecutive periods and a slash (../). Otherwise, the error code -1 is returned.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile  | string              | Yes   | File path of the file to be decompressed. The path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md). If the .zip file to be decompressed contains Chinese file names or directory names, use UTF-8 encoding to avoid garbled Chinese characters in the file names or directory names during decompression. |
| outFile | string              | Yes   | Path of the decompressed file. The path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md).                                         |
| options | [Options](#options) | Yes  | Optional parameters for the unzip operation.                                            |

**Return value**

| Type          | Description                                                        |
| -------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
// The path used in the code must be an application sandbox path, for example, /data/storage/el2/base/temp. You can obtain the path through the context.
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/data/storage/el2/base/temp/xxx.zip';
let outFile = '/data/storage/el2/base/temp/xxx';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  memLevel: zlib.MemLevel.MEM_LEVEL_DEFAULT,
  strategy: zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY
};

zlib.unzipFile(inFile, outFile, options).then((data: void) => {
  console.info('unzipFile result is ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error('error is ' + JSON.stringify(err));
})
```

## zlib.compressFile<sup>9+</sup>

compressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback\<void>): void

Compresses a file. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> To avoid path traversal, the input parameters of **inFile** and **outFile** cannot contain two consecutive periods and a slash (../) since API version 13. Otherwise, error codes 900001 and 900002 are returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name                 | Type               | Mandatory| Description                                                        |
| ----------------------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile                  | string              | Yes   | Folder path or file path to be compressed. The path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md). The folder to be compressed cannot be empty; otherwise, an error is reported when [decompressFile](#zlibdecompressfile9) is used to decompress the compressed file. |
| outFile                 | string              | Yes   | File path of the compression result. The path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md). When multiple compression tasks are executed concurrently, the outFile of each task must be different; otherwise, compression may fail or the output file may be corrupted.                                             |
| options                 | [Options](#options) | Yes  | Compression parameters.                                              |
| callback | AsyncCallback\<void>            | Yes  | Callback used to return the result. If the operation is successful, **null** is returned; otherwise, a specific error code is returned.            |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                              |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 900001   | The input source file is invalid.      |
| 900002   | The input destination file is invalid. |

**Example**

```ts
// The path used in the code must be an application sandbox path, for example, /data/storage/el2/base/temp. You can obtain the path through the context.
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/data/storage/el2/base/temp/filename.xxx';
let outFile = '/data/storage/el2/base/temp/xxx.zip';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  memLevel: zlib.MemLevel.MEM_LEVEL_DEFAULT,
  strategy: zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY
};

try {
  zlib.compressFile(inFile, outFile, options, (errData: BusinessError) => {
    if (errData) {
      console.error(`compressFile errData is errCode:${errData.code}  message:${errData.message}`);
    } else {
      console.info(`compressFile success.`);
    }
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`compressFile errData is errCode:${code}  message:${message}`);
}
```

## zlib.compressFile<sup>9+</sup>

compressFile(inFile: string, outFile: string, options: Options): Promise\<void>

Compresses a file. This API uses a promise to return the result.

> **NOTE**
>
> To avoid path traversal, the input parameters of **inFile** and **outFile** cannot contain two consecutive periods and a slash (../) since API version 13. Otherwise, error codes 900001 and 900002 are returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile  | string              | Yes   | Folder path or file path to be compressed. The path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md). The folder to be compressed cannot be empty; otherwise, an error is reported when [decompressFile](#zlibdecompressfile9) is used to decompress the compressed file. |
| outFile | string              | Yes   | File path of the compression result. The path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md). When multiple compression tasks are executed concurrently in multiple threads, the outFile of each task must be different; otherwise, compression may fail or the output file may be corrupted.                                           |
| options | [Options](#options) | Yes  | Compression parameters.                                              |

**Return value**

| Type          | Description                   |
| -------------- | ----------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                              |
| -------- | ------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 900001   | The input source file is invalid.      |
| 900002   | The input destination file is invalid. |

**Example**

```ts
// The path used in the code must be an application sandbox path, for example, /data/storage/el2/base/temp. You can obtain the path through the context.
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/data/storage/el2/base/temp/filename.xxx';
let outFile = '/data/storage/el2/base/temp/xxx.zip';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  memLevel: zlib.MemLevel.MEM_LEVEL_DEFAULT,
  strategy: zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY
};

try {
  zlib.compressFile(inFile, outFile, options).then((data: void) => {
    console.info('compressFile success. data: ' + JSON.stringify(data));
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```

## zlib.decompressFile<sup>9+</sup>

decompressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback\<void>): void

Decompresses a file. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> To avoid path traversal, the input parameters of **inFile** and **outFile** cannot contain two consecutive periods and a slash (../) since API version 13. Otherwise, error codes 900001 and 900002 are returned.
>
> The name of the zipped file or zipped folder cannot contain two consecutive periods and a slash (../). Otherwise, the error code 900003 is returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name                 | Type               | Mandatory| Description                                                        |
| ----------------------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile                  | string              | Yes   | File path of the file to decompress. The file name extension must be .zip. The file path must be a sandbox path, which can be obtained through the context. For details, see [Stage Model](../apis-ability-kit/js-apis-inner-application-context.md). If the .zip file to decompress contains Chinese file names or directory names, encode them in UTF8 to avoid garbled Chinese characters in the file names or directory names after decompression. |
| outFile                 | string              | Yes   | Path of the folder to which the file is decompressed. The folder path must exist in the system; otherwise, decompression fails. The path must be a sandbox path, which can be obtained through the context. For details, see [Context (Context Base Class of the Stage Model)](../apis-ability-kit/js-apis-inner-application-context.md) or [Context (Context Base Class of the FA Model)](../apis-ability-kit/js-apis-inner-app-context.md). If a file or folder to decompress already exists under the target path, the file with the same name or the file with the same name in the folder with the same name is overwritten. When multiple compression tasks are executed concurrently in multiple threads, the outFile of each task must be different; otherwise, compression may fail or the output file may be corrupted. |
| options                 | [Options](#options) | Yes  | Decompression parameters.                                            |
| callback | AsyncCallback\<void>            | Yes  | Callback used to return the result. If the operation is successful, **null** is returned; otherwise, a specific error code is returned.                                            |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                              |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 900001   | The input source file is invalid.      |
| 900002   | The input destination file is invalid. |
| 900003 | The input source file is not in ZIP format or is damaged. <br>Applicable version: 10+ |

**Example**

```ts
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
    if (errData) {
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

## zlib.decompressFile<sup>9+</sup>

decompressFile(inFile: string, outFile: string, options?: Options): Promise\<void>

Decompresses a file. This API uses a promise to return the result.

> **NOTE**
>
> To avoid path traversal, the input parameters of **inFile** and **outFile** cannot contain two consecutive periods and a slash (../) since API version 13. Otherwise, error codes 900001 and 900002 are returned.
>
> The name of the zipped file or zipped folder cannot contain two consecutive periods and a slash (../). Otherwise, the error code 900003 is returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile  | string              | Yes   | File path of the file to decompress. The file name extension must be .zip. The file path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md). If the .zip file to decompress contains Chinese file names or directory names, encode them in UTF-8 to avoid garbled Chinese characters in the file names or directory names after decompression. |
| outFile | string              | Yes   | Path of the folder to which the file is decompressed. The folder directory path must exist in the system; otherwise, decompression fails. The path must be a sandbox path, which can be obtained through the context. For details, see [Context (base class of the context in the stage model)](../apis-ability-kit/js-apis-inner-application-context.md) or [Context (base class of the context in the FA model)](../apis-ability-kit/js-apis-inner-app-context.md). If a file or folder to decompress already exists in the decompression path, the file with the same name, or the file with the same name in the folder with the same name, is overwritten. When multiple threads decompress files at the same time, the outFile values must be different; otherwise, the decompressed data may overwrite each other or the files may be corrupted. When multiple threads concurrently execute multiple compression tasks, the outFile values of the tasks must be different; otherwise, compression may fail or the output files may be corrupted. |
| options | [Options](#options) | No   | Configuration parameters for decompression. If this parameter is not passed, the default configuration is used.                                           |

**Return value**

| Type          | Description                   |
| -------------- | ----------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                              |
| ------ | ------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 900001 | The input source file is invalid.      |
| 900002 | The input destination file is invalid. |
| 900003 | The input source file is not in ZIP format or is damaged. <br>Supported since: 10+ |

**Example**

```ts
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

## zlib.decompressFile<sup>10+</sup>

decompressFile(inFile: string, outFile: string, callback: AsyncCallback\<void\>): void

Decompresses a file. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> To avoid path traversal, the input parameters of **inFile** and **outFile** cannot contain two consecutive periods and a slash (../) since API version 13. Otherwise, error codes 900001 and 900002 are returned.
>
> The name of the zipped file or zipped folder cannot contain two consecutive periods and a slash (../). Otherwise, the error code 900003 is returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name                 | Type               | Mandatory| Description                                                        |
| ----------------------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile                  | string              | Yes   | File path of the file to decompress. The file name extension must be .zip. The file path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md). If the .zip file to decompress contains Chinese file names or directory names, encode them in UTF8 to avoid garbled Chinese characters in the file names or directory names after decompression. |
| outFile                 | string              | Yes   | Path of the folder to which the file is decompressed. The folder directory path must exist in the system; otherwise, decompression fails. The path must be a sandbox path, which can be obtained through the context. For details, see [Context (base class of the Stage model context)](../apis-ability-kit/js-apis-inner-application-context.md) or [Context (base class of the FA model context)](../apis-ability-kit/js-apis-inner-app-context.md). If a file or folder to decompress already exists in the decompressed path, the file with the same name or the file with the same name in the folder with the same name is overwritten. When multiple threads decompress files at the same time, outFile must be different for each thread; otherwise, the decompressed data may overwrite each other or the files may be corrupted. When multiple threads concurrently execute multiple compression tasks, outFile must be different for each task; otherwise, compression may fail or the output files may be corrupted. |
| callback | AsyncCallback\<void>            | Yes  | Callback used to return the result. If the operation is successful, **null** is returned; otherwise, a specific error code is returned.                                            |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                              |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 900001   | The input source file is invalid.      |
| 900002   | The input destination file is invalid. |
| 900003 | The input source file is not in ZIP format or is damaged. |

**Example**

```ts
// The path used in the code must be an application sandbox path, for example, /data/storage/el2/base/temp. You can obtain the path through the context.
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/data/storage/el2/base/temp/xxx.zip';
let outFileDir = '/data/storage/el2/base/temp';

try {
  zlib.decompressFile(inFile, outFileDir, (errData: BusinessError) => {
    if (errData) {
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

## zlib.getOriginalSize<sup>12+</sup>

getOriginalSize(compressedFile: string): Promise\<number>

Obtains the original size of a compressed file. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| compressedFile  | string              | Yes   | File path of the specified compressed file. Only ZIP-format compressed files are supported. The file path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md). |

**Return value**

| Type          | Description                   |
| -------------- | ----------------------- |
| Promise\<number> | Promise object, which returns the original size of the compressed file, in bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                              |
| ------ | ------------------------------------- |
| 401 | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 900001 | The input source file is invalid.      |
| 900003 | The input source file is not in ZIP format or is damaged. |

**Example**

```ts
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

## zlib.compressFiles<sup>12+</sup>

compressFiles(inFiles: Array&lt;string&gt;, outFile: string, options: Options): Promise&lt;void&gt;

Compresses multiple specified files. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFiles | Array&lt;string&gt; | Yes | Folder path or file path to be compressed. The path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md). The folder to be compressed cannot be empty; otherwise, an error is reported when [decompressFile](#zlibdecompressfile9) is used to decompress the compressed file. |
| outFile | string | Yes | File path of the compression result. The path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md). When multiple threads compress files at the same time, outFile cannot be the same; otherwise, the compressed data may overwrite each other or the file may be damaged. When multiple threads concurrently execute multiple compression tasks, outFile of each task cannot be the same; otherwise, compression may fail or the output file may be damaged. |
| options | [Options](#options) | Yes  | Compression parameters.                                            |

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 900001   | The input source file is invalid.                            |
| 900002   | The input destination file is invalid.                       |

**Example**

```typescript
// The path used in the code must be an application sandbox path, for example, /data/storage/el2/base/temp. You can obtain the path through the context.
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/data/storage/el2/base/temp/filename.xxx';
let pathDir = '/data/storage/el2/base/temp/xxx';
let outFile = '/data/storage/el2/base/temp/xxx.zip';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  memLevel: zlib.MemLevel.MEM_LEVEL_DEFAULT,
  strategy: zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY
};

try {
  zlib.compressFiles([inFile, pathDir], outFile, options).then(() => {
    console.info('compressFiles success.');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  });
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```

## zlib.createChecksum<sup>12+</sup>

createChecksum(): Promise&lt;Checksum&gt;

Creates this checksum object. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                                  | Description                           |
| -------------------------------------- | ------------------------------- |
| Promise&lt;[Checksum](#checksum12)&gt; | Promise used to return the created checksum object.|

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';

zlib.createChecksum().then((data) => {
  console.info('createChecksum success');
})
```

## zlib.createChecksumSync<sup>12+</sup>

createChecksumSync():  Checksum

Creates this checksum object. A checksum instance is returned upon a success.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                   | Description          |
| ----------------------- | -------------- |
| [Checksum](#checksum12) | Checksum object instance used to calculate and verify data checksums. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';

let checksum = zlib.createChecksumSync()
```

## Checksum<sup>12+</sup>

Checksum object.

### adler32<sup>12+</sup>

adler32(adler: number, buf: ArrayBuffer): Promise&lt;number&gt;

Calculates the Adler-32 checksum. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type       | Mandatory| Description                    |
| ------ | ----------- | ---- | ------------------------ |
| adler  | number      | Yes  | Initial value of the Adler-32 checksum.|
| buf    | ArrayBuffer | Yes  | Data buffer for calculating the checksum.  |

**Return value**

| Type                 | Description                                     |
| --------------------- | ----------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the calculated Adler-32 checksum.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                              |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(12);
let data = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  data[i] = str.charCodeAt(i);
}

let checksum = zlib.createChecksumSync()

checksum.adler32(0, arrayBufferIn).then(data => {
  console.info('adler32 success', data);
})
```

### adler32Combine<sup>12+</sup>

adler32Combine(adler1: number, adler2: number, len2: number): Promise&lt;number&gt;

Combines two Adler-32 checksums. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type  | Mandatory| Description                                |
| ------ | ------ | ---- | ------------------------------------ |
| adler1 | number | Yes  | The first Adler-32 checksum to be combined.      |
| adler2 | number | Yes  | The second Adler-32 checksum to be combined.      |
| len2   | number | Yes   | Length of the second data block for the Adler-32 checksum, in bytes. |

**Return value**

| Type                 | Description                                     |
| --------------------- | ----------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the combined Adler-32 checksum.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                              |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(12);
  let data = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    data[i] = str.charCodeAt(i);
  }
  let checksum = zlib.createChecksumSync()
  let adler1 = 0;
  let adler2 = 1;
  await checksum.adler32(0, arrayBufferIn).then(data => {
    console.info('adler32 success', data);
    adler1 = data;
  })
  await checksum.adler32(1, arrayBufferIn).then(data => {
    console.info('adler32 success', data);
    adler2 = data;
  })
  await checksum.adler32Combine(adler1, adler2, 12).then((data) => {
    console.info('adler32Combine success', data);
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### crc32<sup>12+</sup>

crc32(crc: number, buf: ArrayBuffer): Promise&lt;number&gt;

Updates a CRC-32 checksum. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type       | Mandatory| Description                |
| ------ | ----------- | ---- | -------------------- |
| crc    | number      | Yes  | Initial value of the CRC-32 checksum.|
| buf    | ArrayBuffer | Yes  | Data buffer for calculating the checksum.|

**Return value**

| Type                 | Description                                 |
| --------------------- | ------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the updated CRC-32 checksum.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                              |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(12);
let data = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  data[i] = str.charCodeAt(i);
}

let checksum = zlib.createChecksumSync()

checksum.crc32(0, arrayBufferIn).then((data) => {
  console.info('crc32 success', data);
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

### crc32Combine<sup>12+</sup>

crc32Combine(crc1: number, crc2: number, len2: number): Promise&lt;number&gt;

Combines two CRC-32 checksums. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type  | Mandatory| Description                            |
| ------ | ------ | ---- | -------------------------------- |
| crc1 | number | Yes  | The first CRC-32 checksum to be combined.      |
| crc2 | number | Yes  | The second CRC-32 checksum to be combined.      |
| len2 | number | Yes | Length of the second data block for CRC-32 checksum, in bytes. |

**Return value**

| Type                 | Description                                 |
| --------------------- | ------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the combined CRC-32 checksum.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                              |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(12);
  let data = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    data[i] = str.charCodeAt(i);
  }
  let checksum = zlib.createChecksumSync()
  let crc1 = 0;
  let crc2 = 1;
  await checksum.crc32(0, arrayBufferIn).then(data => {
    console.info('crc32 success', data);
    crc1 = data;
  })
  await checksum.crc32(1, arrayBufferIn).then(data => {
    console.info('crc32 success', data);
    crc2 = data;
  })
  await checksum.crc32Combine(crc1, crc2, 12).then((data) => {
    console.info('crc32Combine success', data);
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### crc64<sup>12+</sup>

crc64(crc: number, buf: ArrayBuffer): Promise&lt;number&gt;

Updates a CRC-64 checksum. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type       | Mandatory| Description                |
| ------ | ----------- | ---- | -------------------- |
| crc    | number      | Yes  | Initial value of the CRC-64 checksum.|
| buf    | ArrayBuffer | Yes  | Data buffer for calculating the checksum.|

**Return value**

| Type                 | Description                                 |
| --------------------- | ------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the updated CRC-64 checksum.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                              |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(12);
let data = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  data[i] = str.charCodeAt(i);
}

let checksum = zlib.createChecksumSync()

checksum.crc64(0, arrayBufferIn).then((data) => {
  console.info('crc64 success', data);
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

### getCrcTable<sup>12+</sup>

getCrcTable(): Promise&lt;Array&lt;number&gt;&gt;

Obtains this CRC-32 checksum table. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                              | Description                           |
| ---------------------------------- | ------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the CRC-32 checksum table.|

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let checksum = zlib.createChecksumSync()

checksum.getCrcTable().then((data) => {
  console.info('getCrcTable success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

### getCrc64Table<sup>12+</sup>

getCrc64Table(): Promise&lt;Array&lt;number&gt;&gt;

Obtains this CRC-64 checksum table. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                              | Description                           |
| ---------------------------------- | ------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the CRC-64 checksum table.|

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let checksum = zlib.createChecksumSync()

checksum.getCrc64Table().then((data) => {
  console.info('getCrc64Table success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

## zlib.createZip<sup>12+</sup>

createZip(): Promise&lt;Zip&gt;

Creates this **Zip** instance. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                        | Description                                 |
| ---------------------------- | ------------------------------------- |
| Promise&lt;[Zip](#zip12)&gt; | Promise used to return the **Zip** instance created.|

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

zlib.createZip().then(data => {
  console.info('createZip success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

## zlib.createZipSync<sup>12+</sup>

createZipSync(): Zip

Creates this **Zip** instance. A **Zip** instance is returned upon a success.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type         | Description                    |
| ------------- | ------------------------ |
| [Zip](#zip12) | **Zip** instance created.|

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();
```

## Zip<sup>12+</sup>

Defines the **Zip** instance. It provides APIs to zip or unzip data in Zlib, Deflate, or Gzip format.

### getZStream<sup>12+</sup>

getZStream(): Promise&lt;ZStream&gt;

Obtains and returns a ZStream stream object instance. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                                | Description                     |
| ------------------------------------ | ------------------------- |
| Promise&lt;[ZStream](#zstream12)&gt; | Promise used to return the data stream management object for compression and decompression, which is used to manage the data streams during compression and decompression. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.getZStream().then(data => {
  console.info('getZStream success');
})
```

### zlibVersion<sup>12+</sup>

zlibVersion(): Promise&lt;string&gt;

Obtains the version information of this zlib library connected. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                 | Description                                   |
| --------------------- | --------------------------------------- |
| Promise&lt;string&gt; | Promise used to return the version of the current zlib library.|

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.zlibVersion().then((data) => {
  console.info('zlibVersion success')
})
```

### zlibCompileFlags<sup>12+</sup>

zlibCompileFlags(): Promise&lt;number&gt;

Returns the flags indicating compile-time options. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                 | Description                                   |
| --------------------- | --------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the flags indicating compile-time options.|

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.zlibCompileFlags().then((data) => {
  console.info('zlibCompileFlags success')
})
```

### compress<sup>12+</sup>

compress(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise&lt;ZipOutputInfo&gt;

Compresses the source buffer into the destination buffer. This API uses a promise to return the result. The compressed data can be decompressed using the uncompress method.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name   | Type       | Mandatory| Description          |
| --------- | ----------- | ---- | -------------- |
| dest      | ArrayBuffer | Yes  | Destination buffer.  |
| source    | ArrayBuffer | Yes  | Source buffer.|
| sourceLen | number      | No   | Length of the source data, in bytes. Value range: [0, source.byteLength]. If this parameter is not passed, source.byteLength is used by default.   |

**Return value**

| Type                                            | Description                                           |
| ------------------------------------------------ | ----------------------------------------------- |
| Promise&lt;[ZipOutputInfo](#zipoutputinfo12)&gt; | Promise used to return the result status and the total size of the destination buffer.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800007 | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**Example**

```ts
import { util } from '@kit.ArkTS';
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world! Hello, world!';
const enc = util.TextEncoder.create('utf-8');
const u8 = enc.encodeInto(str);
const arrayBufferIn = u8.buffer.slice(u8.byteOffset, u8.byteOffset + u8.byteLength);

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

zip.compress(arrayBufferOut, arrayBufferIn, 20).then((data) => {
  console.info('compress success:');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

### compress2<sup>12+</sup>

compress2(dest: ArrayBuffer, source: ArrayBuffer, level: CompressLevel, sourceLen?: number): Promise&lt;ZipOutputInfo&gt;

Compresses the source buffer into the destination buffer. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name   | Type         | Mandatory| Description                                         |
| --------- | ------------- | ---- | --------------------------------------------- |
| dest      | ArrayBuffer   | Yes  | Destination buffer.                                 |
| source    | ArrayBuffer   | Yes  | Source buffer.                               |
| level     | [CompressLevel](#compresslevel) | Yes   | Refer to [CompressLevel](#compresslevel). |
| sourceLen | number        | No  | Length of the source data. The default value is **0**.                                 |

**Return value**

| Type                                            | Description                                           |
| ------------------------------------------------ | ----------------------------------------------- |
| Promise&lt;[ZipOutputInfo](#zipoutputinfo12)&gt; | Promise used to return the result status and the total size of the destination buffer.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800007 | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**Example**

```ts
import { util } from '@kit.ArkTS';
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world! Hello, world!';
const enc = util.TextEncoder.create('utf-8');
const u8 = enc.encodeInto(str);
const arrayBufferIn = u8.buffer.slice(u8.byteOffset, u8.byteOffset + u8.byteLength);

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

zip.compress2(arrayBufferOut, arrayBufferIn, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
  console.info('compress2 success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

### uncompress<sup>12+</sup>

uncompress(dest:ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise&lt;ZipOutputInfo&gt;

Decompresses the compressed data into the raw data. This API uses a promise to return the result.


> **NOTE**
>
> Compared with [uncompress2](#uncompress212), this API returns ZipOutputInfo, which contains the result status and the total size of the destination buffer. uncompress2 returns DecompressionOutputInfo, which additionally contains the source data length information, and is suitable for scenarios where the source data length needs to be obtained at the same time.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name   | Type       | Mandatory| Description          |
| --------- | ----------- | ---- | -------------- |
| dest      | ArrayBuffer | Yes  | Destination buffer.  |
| source    | ArrayBuffer | Yes  | Source buffer.|
| sourceLen | number      | No   | Length of the source data, in bytes. Value range: [0, source.byteLength]. If this parameter is not passed, source.byteLength is used by default.   |

**Return value**

| Type                                            | Description                                           |
| ------------------------------------------------ | ----------------------------------------------- |
| Promise&lt;[ZipOutputInfo](#zipoutputinfo12)&gt; | Promise used to return the result status and the total size of the destination buffer.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800005 | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |
| 17800007 | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.compress(arrayBufferOut, arrayBufferIn, 12).then((data) => {
    console.info('compress success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.uncompress(arrayBufferIn, arrayBufferOut, 20).then((data) => {
    console.info('uncompress success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### uncompress2<sup>12+</sup>

uncompress2(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise&lt;DecompressionOutputInfo&gt;

Decompresses the compressed data into the raw data. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name   | Type       | Mandatory| Description          |
| --------- | ----------- | ---- | -------------- |
| dest      | ArrayBuffer | Yes  | Destination buffer.  |
| source    | ArrayBuffer | Yes  | Source buffer.|
| sourceLen | number      | No   | Length of the source data, in bytes. Value range: [0, source.byteLength]. If this parameter is not passed, source.byteLength is used by default.   |

**Return value**

| Type                                                        | Description                                                       |
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| Promise&lt;[DecompressionOutputInfo](#decompressionoutputinfo12)&gt; | Promise used to return the result status, total size of the destination buffer, and the length of the source data.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800005 | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |
| 17800007 | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.compress2(arrayBufferOut, arrayBufferIn, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('compress2 success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.uncompress2(arrayBufferIn, arrayBufferOut, 20).then((data) => {
    console.info('uncompress2 success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### compressBound<sup>12+</sup>

compressBound(sourceLen: number): Promise&lt;number&gt;

Calculates the maximum size of the compressed data to be returned. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name   | Type  | Mandatory| Description        |
| --------- | ------ | ---- | ------------ |
| sourceLen | number | Yes  | Length of the source data.|

**Return value**

| Type                 | Description                             |
| --------------------- | --------------------------------- |
| Promise&lt;number&gt; | Promise used to return the maximum size of the compressed data.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i);
}

let zip = zlib.createZipSync();

zip.compressBound(str.length).then((data) => {
  console.info('compressBound success')
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

### inflateValidate<sup>12+</sup>

inflateValidate(strm: ZStream, check: number): Promise&lt;ReturnStatus&gt;

Validates the checksum inside the compression stream. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |
| check  | number  | Yes  | Expected checksum.                 |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateValidate({ availableIn: 1 }, 1).then(data => {
    console.info('inflateValidate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflateSyncPoint<sup>12+</sup>

inflateSyncPoint(strm: ZStream): Promise&lt;ReturnStatus&gt;

Finds the synchronization point of a decompression stream. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateSyncPoint({ availableIn: 1 }).then(data => {
    console.info('inflateSyncPoint success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflateSync<sup>12+</sup>

inflateSync(strm: ZStream): Promise&lt;ReturnStatus&gt;

Skips invalid compressed data until a possible complete refresh point is found. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800005 | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |
| 17800007 | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello, hello!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.deflateInit({}, zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflate({ nextIn: arrayBufferIn, availableIn: 3, nextOut: arrayBufferOut, availableOut: 100 }, zlib.CompressFlushMode.FULL_FLUSH).then((data) => {
    console.info('deflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflate({ availableIn: 11 }, zlib.CompressFlushMode.FINISH).then((data) => {
    console.info('deflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateEnd({}).then(data => {
    console.info('deflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  try {
    await zip.inflateInit({ nextIn: arrayBufferOut, availableIn: 2 }).then(data => {
      console.info('inflateInit2 success')
    })
  } catch (errData) {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  }
  await zip.inflate({ nextOut: arrayBufferIn, availableOut: 28 }, zlib.CompressFlushMode.NO_FLUSH).then((data) => {
    console.info('inflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateSync({ availableIn: 26 }).then(data => {
    console.info('inflateSync success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateEnd({ nextOut: arrayBufferOut }).then((data) => {
    console.info('inflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflateResetKeep<sup>12+</sup>

inflateResetKeep(strm: ZStream): Promise&lt;ReturnStatus&gt;

Resets the state of the decompression stream to retain the allocated Huffman tree and preset dictionary. This API uses a promise to return the result.


> **NOTE**
>
> Compared with [inflateReset](#inflatereset12) and [inflateReset2](#inflatereset212): this API retains the Huffman decoding tree and the preset dictionary, and is suitable for scenarios where the same decompression configuration needs to be maintained. inflateReset completely resets the decompression stream. inflateReset2 can set the window size and specify the data format.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateResetKeep({ availableIn: 1 }).then(data => {
    console.info('inflateResetKeep success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflateSetDictionary<sup>12+</sup>

inflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise&lt;ReturnStatus&gt;

Initializes the dictionary content of a decompression stream based on the given dictionary data. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name    | Type       | Mandatory| Description                           |
| ---------- | ----------- | ---- | ------------------------------- |
| strm       | [ZStream](#zstream12)     | Yes   | Data stream management object for zlib compression and decompression. |
| dictionary | ArrayBuffer | Yes  | Dictionary data.                     |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800005 | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello, hello!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  let dictionary = 'hello';
  let dictionarybuf = new ArrayBuffer(dictionary.length);
  let dictionarybufdata = new Uint8Array(dictionarybuf);
  for (let i = 0, j = dictionary.length; i < j; i++) {
    dictionarybufdata[i] = str.charCodeAt(i);
  }
  await zip.deflateInit({}, zlib.CompressLevel.COMPRESS_LEVEL_BEST_COMPRESSION).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflateSetDictionary({}, dictionarybuf).then((data) => {
    console.info('deflateSetDictionary success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflate({ nextIn: arrayBufferIn, availableIn: 14, nextOut: arrayBufferOut, availableOut: 100 }, zlib.CompressFlushMode.FINISH).then((data) => {
    console.info('deflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflateEnd({}).then(data => {
    console.info('deflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  try {
    await zip.inflateInit({ nextIn: arrayBufferOut, availableIn: 100 }).then(data => {
      console.info('inflateInit success')
    })
  } catch (errData) {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  }
  await zip.inflate({ nextOut: arrayBufferIn, availableOut: 28 }, zlib.CompressFlushMode.NO_FLUSH).then((data) => {
    console.info('inflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.inflateSetDictionary({}, dictionarybuf).then((data) => {
    console.info('inflateSetDictionary success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.inflateEnd({ nextOut: arrayBufferOut }).then((data) => {
    console.info('inflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
}
```

### inflateReset2<sup>12+</sup>

inflateReset2(strm: ZStream, windowBits: number): Promise&lt;ReturnStatus&gt;

Resets the status of the specified decompression stream and updates the window size to start a new decompression operation. The internal buffer is not released or reallocated. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name    | Type   | Mandatory| Description                           |
| ---------- | ------- | ---- | ------------------------------- |
| strm       | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |
| windowBits | number  | Yes   | Controls the size of the memory window and specifies the data format (zlib, gzip, or raw deflate). The value range is as follows:<br>zlib format: [8, 15].<br>gzip format: [24, 31].<br>raw deflate format: [-15, -8].   |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateReset2({ availableOut: 8 }, 15).then(data => {
    console.info('inflateReset2 success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflateReset<sup>12+</sup>

inflateReset(strm: ZStream): Promise&lt;ReturnStatus&gt;

Resets the status of the specified decompression stream to the initial state to start a new decompression operation. The internal buffer is not released or reallocated. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateReset({ availableIn: 1, availableOut: 8 }).then(data => {
    console.info('inflateReset success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflatePrime<sup>12+</sup>

inflatePrime(strm: ZStream, bits: number, value: number): Promise&lt;ReturnStatus&gt;

Sets the initial number of bits and bit value in the specified decompression stream to pre-fill the bit buffer at the beginning of the decompression stream to correctly process the data. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |
| bits   | number  | Yes   | Number of bits to write to the bit buffer. Value range: [0, 16].                      |
| value  | number  | Yes   | Bit value used to fill the bit buffer. Value range: [0, 2^bits-1].                      |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflatePrime({ nextOut: arrayBufferOut }, 5, 2).then(data => {
    console.info('inflatePrime success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflateMark<sup>12+</sup>

inflateMark(strm: ZStream): Promise&lt;number&gt;

Marks the location of the input data for random access. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                 | Description                       |
| --------------------- | --------------------------- |
| Promise&lt;number&gt; | Promise used to return the current location.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateMark({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }).then(data => {
    console.info('inflateMark success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflateInit2<sup>12+</sup>

inflateInit2(strm: ZStream, windowBits: number): Promise&lt;ReturnStatus&gt;

Initializes a decompression stream with the specified **windowBits**. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name    | Type   | Mandatory| Description                           |
| ---------- | ------- | ---- | ------------------------------- |
| strm       | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |
| windowBits | number  | Yes   | Controls the size of the memory window and specifies the data format (zlib, gzip, or raw deflate). The value ranges are as follows:<br>zlib format: [8, 15].<br>gzip format: [24, 31].<br>raw deflate format: [-15, -8].   |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i);
}

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

zip.inflateInit2({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }, 28
).then(data => {
  console.info('inflateInit2 success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

### inflateInit<sup>12+</sup>

inflateInit(strm: ZStream): Promise&lt;ReturnStatus&gt;

Initializes a decompression stream. This API uses a promise to return the result. You need to call this API first to initialize the decompression stream, then call **inflate** to decompress, and finally call **inflateEnd** to release resources.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i);
}

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
).then(data => {
  console.info('inflateInit success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```

### inflateGetHeader<sup>12+</sup>

inflateGetHeader(strm: ZStream, header: GzHeader): Promise&lt;ReturnStatus&gt;

Obtains the header information of a gzip file before decompressing data. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type                   | Mandatory| Description                            |
| ------ | ----------------------- | ---- | -------------------------------- |
| strm   | [ZStream](#zstream12)                 | Yes   | Data stream management object for zlib compression and decompression.  |
| header | [GzHeader](#gzheader12) | Yes  | Header information of a gzip file extracted from the compressed data stream.|

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit2({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }, 28
  ).then(data => {
    console.info('inflateInit2 success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateGetHeader({ availableIn: 1, availableOut: 1 }, { isText: true, os: 1, time: 1, xflags: 1, extra: arrayBufferIn, extraLen: 12, name: arrayBufferIn, comment: arrayBufferOut, hcrc: true, done: true }).then(data => {
    console.info('inflateGetHeader success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflateGetDictionary<sup>12+</sup>

inflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise&lt;DictionaryOutputInfo&gt;

Obtains the content and length of the decompression dictionary used in a decompression stream. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name    | Type       | Mandatory| Description                           |
| ---------- | ----------- | ---- | ------------------------------- |
| strm       | [ZStream](#zstream12)     | Yes   | Data stream management object for zlib compression and decompression. |
| dictionary | ArrayBuffer | Yes  | Receives the actual contents of the decompression dictionary.     |

**Return value**

| Type                                                        | Description                                   |
| ------------------------------------------------------------ | --------------------------------------- |
| Promise&lt;[DictionaryOutputInfo](#dictionaryoutputinfo12)&gt; | Promise used to return the result status and length of the dictionary.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit2({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }, 28
  ).then(data => {
    console.info('inflateInit2 success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateGetDictionary({ nextOut: arrayBufferOut }, arrayBufferOut).then((data) => {
    console.info('inflateGetDictionary success:')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflateEnd<sup>12+</sup>

inflateEnd(strm: ZStream): Promise&lt;ReturnStatus&gt;

Releases all dynamically allocated data structs of a decompression stream. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflate({ availableIn: 8, availableOut: 8 }, 0).then((data) => {
    console.info('inflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateEnd({ nextOut: arrayBufferOut }).then((data) => {
    console.info('inflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflateCopy<sup>12+</sup>

inflateCopy(source: Zip): Promise&lt;ReturnStatus&gt;

Copies a decompression stream. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type| Mandatory| Description                   |
| ------ | ---- | ---- | ----------------------- |
| source | [Zip](#zip12)  | Yes   | Instance of the object to compress or decompress. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  let destZip = zlib.createZipSync();
  await destZip.inflateCopy(zip).then((data) => {
    console.info('inflateCopy success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflateCodesUsed<sup>12+</sup>

inflateCodesUsed(strm: ZStream): Promise&lt;number&gt;

Describes the number of Huffman trees used in a decompression stream. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                 | Description                                         |
| --------------------- | --------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the number of Huffman trees that have been used.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zip = zlib.createZipSync();
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateCodesUsed({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 8 }).then(data => {
    console.info('inflateCodesUsed success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### inflateBackInit<sup>12+</sup>

inflateBackInit(strm: ZStream, windowBits: number, window: ArrayBuffer): Promise&lt;ReturnStatus&gt;

Initializes the internal stream state for decompression before using the **inflateBack()** function. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name    | Type       | Mandatory| Description                                         |
| ---------- | ----------- | ---- | --------------------------------------------- |
| strm       | [ZStream](#zstream12)     | Yes   | Data stream management object for zlib compression and decompression.               |
| windowBits | number      | Yes   | Controls the size of the memory window and specifies the data format (zlib, gzip, or raw deflate). The value ranges are as follows:<br>zlib format: [8, 15].<br>gzip format: [24, 31].<br>raw deflate format: [-15, -8]. |
| window     | ArrayBuffer | Yes  | Preset window buffer.                           |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

For details about the sample code, see [inflateBack](#inflateback12).

### inflateBackEnd<sup>12+</sup>

inflateBackEnd(strm: ZStream): Promise&lt;ReturnStatus&gt;

Releases all memory allocated by the **inflateBackInit()** function. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

For details about the sample code, see [inflateBack](#inflateback12).

### inflateBack<sup>12+</sup>

inflateBack(strm: ZStream, backIn: InflateBackInputCallback, inDesc: object, backOut: InflateBackOutputCallback, outDesc: object): Promise&lt;ReturnStatus&gt;

Implements decompression and uses callbacks to process input and output data. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name | Type                     | Mandatory| Description                                                        |
| ------- | ------------------------- | ---- | ------------------------------------------------------------ |
| strm    | [ZStream](#zstream12)                   | Yes   | Data stream management object for zlib compression and decompression.                              |
| backIn  | [InflateBackInputCallback](#inflatebackinputcallback12)  | Yes   | Function used to read raw compressed data from the input source for decompressing data from the end. |
| inDesc  | object                    | Yes  | Common object.                                                  |
| backOut | [InflateBackOutputCallback](#inflatebackoutputcallback12) | Yes   | Writes the decompressed data to the target output.                                 |
| outDesc | object                    | Yes  | Common object.                                                  |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let readIn: (inDesc: object) => ArrayBuffer = (inDesc: object): ArrayBuffer => {
    console.info("inDesc = ", JSON.stringify(inDesc));
    let buffer = new ArrayBuffer(26)
    let array = new Uint8Array(buffer);
    array.set([31, 139, 8, 0, 0, 0, 0, 0, 0, 10, 243, 72, 205, 201, 201, 231, 2, 0, 22, 53, 150, 49, 6, 0, 0, 0]);
    return buffer;
  }

  let writeOut: (outDesc: object, buffer: ArrayBuffer, length: number) => number = (outDesc: object, buffer: ArrayBuffer, length: number): number => {
    console.info("outDesc = ", outDesc);
    console.info("buffer = ", buffer);
    console.info("length = ", length);
    let array = new Uint8Array(buffer);
    let dataString = "";
    for (let i = 0; i < length; i++) {
      dataString += String.fromCharCode(array[i]);
    }
    console.info('writeOut ', dataString);
    return 0;
  }

  let have = 0;
  let first = 1;
  let arrayBuffer = new ArrayBuffer(26);
  let next = new Uint8Array(arrayBuffer);
  let last = 0;
  let index = 0;
  let flags = 0;
  let NEXT2: () => number = (): number => {
    let o6: object = new Object()
    if (!have) {
      arrayBuffer = readIn(o6)
      next = new Uint8Array(arrayBuffer);
      console.info('readIn next = ', next.length)
      have = next.length;
    }
    if (have) {
      have--;
      last = next[index];
      index++;
    }
    else {
      last = -1;
    }
    return last;
  }

  let inflateBackTest: () => void = (async () => {
    try {
      have = 0;
      first = 1;
      arrayBuffer = new ArrayBuffer(26);
      next = new Uint8Array(arrayBuffer);
      last = 0;
      index = 0;
      flags = 0;
      let sr = zlib.createZipSync();
      let buffer = new ArrayBuffer(1024)
      await sr.inflateBackInit({}, 15, buffer).then((result) => {
        console.info('inflateBackInit Call result res', result)
      })
      let ret = 0;
      for (; ;) {
        if (NEXT2() == -1) {
          ret = 0;
          console.info('inflateBackTest Call result NEXT2() == -1')
          break;
        }
        console.info('have =  last = ', have, last)
        if (last != 31 || NEXT2() != 139 ) {
          ret = first ? -3 : -1;
          console.info('inflateBackTest Call result last != 31 || (NEXT2() != 139 && last != 157)')
          break;
        }
        first = 0;
        ret = -5;
        if (NEXT2() != 8) {
          if (last < 0) {
            console.info('inflateBackTest Call result 1 last == -1')
            break;
          }
        }
        flags = NEXT2();
        NEXT2();
        NEXT2();
        NEXT2();
        NEXT2();
        NEXT2();
        NEXT2();
        if (last < 0) {
          console.info('inflateBackTest Call result 2 last == -1')
          break;
        }
        console.info('index =  have = ', next[index], have)
        let newArrayBuffer = new ArrayBuffer(have);
        let newNext = new Uint8Array(newArrayBuffer);
        for (let i = 0; i < have; i++) {
          newNext[i] = next[26 - have + i];
        }
        console.info('newArrayBuffer.length = ', newArrayBuffer.byteLength)
        console.info('newNext.length = ', newNext.length)
        let zStream: zlib.ZStream = {
          nextIn: newArrayBuffer,
          availableIn: have,
        };
        await sr.inflateBack(
          zStream,
          readIn,
          { fileName: 'test.gz' },
          writeOut,
          { fileName: 'test.gz' }).then((result) => {
            ret = result;
            console.info('inflateBack Call result res', result)
          })
        if (ret == 1) {
          console.info('inflateBackTest Call result success')
          break;
        }
      }
      await sr.inflateBackEnd({}).then((result) => {
        console.info('inflateBackEnd Call result res', result)
      })
    }
    catch (errData) {
      console.error(`errData is message:${errData}`);
    }
  })
  inflateBackTest();
}
```

### InflateBackInputCallback<sup>12+</sup>

type InflateBackInputCallback = (inDesc: object) => ArrayBuffer

Inputs data.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| inDesc | object | Yes  | User-defined data object.|

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| ArrayBuffer | Content buffer that is successfully read from the input data source.|

### InflateBackOutputCallback<sup>12+</sup>

type InflateBackOutputCallback = (outDesc: object, buf: ArrayBuffer, length: number) => number

Outputs data.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name | Type       | Mandatory| Description                  |
| ------- | ----------- | ---- | ---------------------- |
| outDesc | object      | Yes  | User-defined data object.    |
| buf     | ArrayBuffer | Yes  | Stores the data to be written.|
| length  | number      | Yes  | Length of the data written to the output buffer.|

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| number | Number of bytes in the output buffer.|

### inflate<sup>12+</sup>

inflate(strm: ZStream, flush: CompressFlushMode): Promise&lt;ReturnStatus&gt;

Inflates data. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type             | Mandatory| Description                                               |
| ------ | ----------------- | ---- | --------------------------------------------------- |
| strm   | [ZStream](#zstream12)           | Yes   | Data stream management object for zlib compression and decompression.                     |
| flush  | [CompressFlushMode](#compressflushmode12) | Yes   | Data flush strategy during compression or decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800005 | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflate({ availableOut: 8 }, zlib.CompressFlushMode.FINISH).then((data) => {
    console.info('deflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflateEnd({ nextOut: arrayBufferOut }).then(data => {
    console.info('deflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then(data => {
    console.info('inflateInit success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflate({ availableIn: 8, availableOut: 8 }, 0).then((data) => {
    console.info('inflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.inflateEnd({ nextOut: arrayBufferOut }).then((data) => {
    console.info('inflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### deflateInit<sup>12+</sup>

deflateInit(strm: ZStream, level: CompressLevel): Promise&lt;ReturnStatus&gt;

Initializes a compression stream and sets the specified compression level. This API uses a promise to return the result. You need to call this API first to initialize the compression stream, then call **deflate** to compress, and finally call **deflateEnd** to release resources.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type         | Mandatory| Description                                         |
| ------ | ------------- | ---- | --------------------------------------------- |
| strm   | [ZStream](#zstream12)       | Yes   | Data stream management object for zlib compression and decompression.               |
| level  | [CompressLevel](#compresslevel) | Yes   | See [CompressLevel enum definition](#compresslevel). |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
}
```

### deflateInit2<sup>12+</sup>

deflateInit2(strm: ZStream, level: CompressLevel, method: CompressMethod, windowBits: number, memLevel: MemLevel, strategy: CompressStrategy): Promise&lt;ReturnStatus&gt;

Initializes a compression stream with the specified compression level, compression method, window size, memory level, and compression strategy. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name    | Type            | Mandatory| Description                                               |
| ---------- | ---------------- | ---- | --------------------------------------------------- |
| strm       | [ZStream](#zstream12)          | Yes   | Data stream management object for zlib compression and decompression.                     |
| level      | [CompressLevel](#compresslevel)    | Yes   | For details, see [CompressLevel enum definition](#compresslevel).       |
| method     | [CompressMethod](#compressmethod12)   | Yes   | Enum type of the compression algorithm, specifying the DEFLATED compression method.   |
| windowBits | number           | Yes  | Memory window size. The value is restricted in certain range based on the data formats. The options are as follows:<br>Zlib: [1, 15]<br>Gzip: (15, +∞)<br>Raw Deflate: [-15, -1]                      |
| memLevel   | [MemLevel](#memlevel)         | Yes   | For details, see [MemLevel enum definition](#memlevel).                 |
| strategy   | [CompressStrategy](#compressstrategy) | Yes   | For details, see [CompressStrategy enum definition](#compressstrategy). |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync()
  await zip.deflateInit2(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED, zlib.CompressMethod.DEFLATED, 28,
    zlib.MemLevel.MEM_LEVEL_DEFAULT, zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY).then((data) => {
      console.info('deflateInit2 success');
    }).catch((errData: BusinessError) => {
      console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
    })
}
```

### deflate<sup>12+</sup>

deflate(strm: ZStream, flush: CompressFlushMode): Promise&lt;ReturnStatus&gt;

Deflates data. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type             | Mandatory| Description                                               |
| ------ | ----------------- | ---- | --------------------------------------------------- |
| strm   | [ZStream](#zstream12)           | Yes   | Data stream management object for zlib compression and decompression.                     |
| flush  | [CompressFlushMode](#compressflushmode12) | Yes   | Data flush strategy during compression or decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800007 | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflate({ availableOut: 8 }, zlib.CompressFlushMode.FINISH).then((data) => {
    console.info('deflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
}
```

### deflateEnd<sup>12+</sup>

deflateEnd(strm: ZStream): Promise&lt;ReturnStatus&gt;

Releases all dynamically allocated data structs of a compression stream. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflate({ availableOut: 8 }, zlib.CompressFlushMode.FINISH).then((data) => {
    console.info('deflate success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
  await zip.deflateEnd({ nextOut: arrayBufferOut }).then(data => {
    console.info('deflateEnd success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### deflateBound<sup>12+</sup>

deflateBound(strm: ZStream, sourceLength: number): Promise&lt;number&gt;

Calculates the maximum size of the compressed data. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name   | Type   | Mandatory| Description                           |
| --------- | ------- | ---- | ------------------------------- |
| strm      | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |
| sourceLength | number  | Yes  | Length of the source data.                   |

**Return value**

| Type                 | Description                             |
| --------------------- | --------------------------------- |
| Promise&lt;number&gt; | Promise used to return the maximum size of the compressed data.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateBound({ nextOut: arrayBufferOut }, 12).then((data) => {
    console.info('deflateBound success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### deflateSetHeader<sup>12+</sup>

deflateSetHeader(strm: ZStream, head: GzHeader): Promise&lt;ReturnStatus&gt;

Provides the header information of a gzip file when **deflateInit2()** requests a gzip stream. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type                   | Mandatory| Description                            |
| ------ | ----------------------- | ---- | -------------------------------- |
| strm   | [ZStream](#zstream12)                 | Yes   | Data stream management object for zlib compression and decompression.  |
| head   | [GzHeader](#gzheader12) | Yes  | Header information of a gzip file extracted from the compressed data stream.|

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync()
  await zip.deflateInit2(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED, zlib.CompressMethod.DEFLATED, 28,
    zlib.MemLevel.MEM_LEVEL_DEFAULT, zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY).then((data) => {
      console.info('deflateInit2 success');
    }).catch((errData: BusinessError) => {
      console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
    })
  await zip.deflateSetHeader({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }, { isText: true, os: 1, time: 1, xflags: 1, extra: arrayBufferIn, extraLen: 12, name: arrayBufferIn, comment: arrayBufferOut, hcrc: true, done: true }).then((data) => {
    console.info('deflateSetHeader success');
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`)
  })
}
```

### deflateCopy<sup>12+</sup>

deflateCopy(source: Zip): Promise&lt;ReturnStatus&gt;

Copies a compression stream. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type| Mandatory| Description                   |
| ------ | ---- | ---- | ----------------------- |
| source | [Zip](#zip12)  | Yes   | Instance of the object to compress or decompress. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateCopy(zip).then((data) => {
    console.info('deflateCopy success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### deflateSetDictionary<sup>12+</sup>

deflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise&lt;ReturnStatus&gt;

Initializes the compression dictionary from the given byte sequence. This API uses a promise to return the result. It must be called after the compression stream is initialized by **deflateInit** or **deflateInit2**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name    | Type       | Mandatory| Description                           |
| ---------- | ----------- | ---- | ------------------------------- |
| strm       | [ZStream](#zstream12)     | Yes   | Data stream management object for zlib compression and decompression. |
| dictionary | ArrayBuffer | Yes  | Dictionary data.                     |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateSetDictionary({ nextOut: arrayBufferOut }, arrayBufferOut).then((data) => {
    console.info('deflateSetDictionary success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### deflateGetDictionary<sup>12+</sup>

deflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise&lt;DictionaryOutputInfo&gt;

Obtains the content and length of the compression dictionary used in a compression stream. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name    | Type       | Mandatory| Description                           |
| ---------- | ----------- | ---- | ------------------------------- |
| strm       | [ZStream](#zstream12)     | Yes   | Data stream management object for zlib compression and decompression. |
| dictionary | ArrayBuffer | Yes  | Buffer that receives the actual contents of the decompression dictionary.     |

**Return value**

| Type                                                        | Description                                   |
| ------------------------------------------------------------ | --------------------------------------- |
| Promise&lt;[DictionaryOutputInfo](#dictionaryoutputinfo12)&gt; | Promise used to return the result status and length of the dictionary.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateSetDictionary({ nextOut: arrayBufferOut }, arrayBufferOut).then((data) => {
    console.info('deflateSetDictionary success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateGetDictionary({ nextOut: arrayBufferOut }, arrayBufferOut).then((data) => {
    console.info('deflateGetDictionary success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### deflateTune<sup>12+</sup>

deflateTune(strm: ZStream, goodLength: number, maxLazy: number, niceLength: number, maxChain: number): Promise&lt;ReturnStatus&gt;

Fine-tunes the internal compression parameters of deflate. This API uses a promise to return the result. It must be called after the compression stream is initialized by **deflateInit** or **deflateInit2**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name    | Type   | Mandatory| Description                           |
| ---------- | ------- | ---- | ------------------------------- |
| strm       | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |
| goodLength | number  | Yes  | Matched length threshold.               |
| maxLazy    | number  | Yes   | Delay matching strategy used when the compression algorithm builds a Huffman tree. The value is an integer ranging from 0 to 4. A larger value indicates a lazier algorithm, which performs a slower matching process but generates a better compression result. 0: Lazy matching is disabled. The algorithm builds a Huffman tree as soon as possible. The compression speed is fast, but the compression ratio is low.  |
| niceLength | number  | Yes  | Appropriate delay length threshold.             |
| maxChain   | number  | Yes  | Maximum chain length.                   |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateTune({ nextOut: arrayBufferOut }, 2, 2, 2, 2).then((data) => {
    console.info('deflateTune success:')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### deflateReset<sup>12+</sup>

deflateReset(strm: ZStream): Promise&lt;ReturnStatus&gt;

Equivalent to call the **deflateEnd** API and then the **deflateInit** API. However, this API does not release or reallocate the internal compression state. This API uses a promise to return the result.


> **NOTE**
>
> Compared with [deflateResetKeep](#deflateresetkeep12), this API completely resets the compression stream without retaining any parameters. **deflateResetKeep** retains the compression parameters and dictionary, and is suitable for scenarios where recompression needs to be performed with the same compression configuration.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateReset({ nextOut: arrayBufferOut }).then((data) => {
    console.info('deflateReset success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### deflateResetKeep<sup>12+</sup>

deflateResetKeep(strm: ZStream): Promise&lt;ReturnStatus&gt;

Resets the initialized compression stream, but retains the compression parameters and dictionaries set by it. This API uses a promise to return the result.


> **NOTE**
>
> Compared with [deflateReset](#deflatereset12), this API retains the compression parameters and dictionary, and is suitable for scenarios where recompression needs to be performed with the same compression configuration. **deflateReset** completely resets the compression stream without retaining any parameters.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateResetKeep({ nextOut: arrayBufferOut }).then((data) => {
    console.info('deflateResetKeep success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### deflatePending<sup>12+</sup>

deflatePending(strm: ZStream): Promise&lt;DeflatePendingOutputInfo&gt;

Returns the number of bytes and bits of output that has been generated but not yet provided in the available output. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |

**Return value**

| Type                                                        | Description                                             |
| ------------------------------------------------------------ | ------------------------------------------------- |
| Promise&lt;[DeflatePendingOutputInfo](#deflatependingoutputinfo12)&gt; | Promise used to return the result status, and number of bits and bytes for output.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflatePending({ nextOut: arrayBufferOut }).then((data) => {
    console.info('deflatePending success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### deflateParams<sup>12+</sup>

deflateParams(strm: ZStream, level: CompressLevel, strategy: CompressStrategy): Promise&lt;ReturnStatus&gt;

Dynamically updates the compression level and compression strategy. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name  | Type            | Mandatory| Description                                               |
| -------- | ---------------- | ---- | --------------------------------------------------- |
| strm     | [ZStream](#zstream12)          | Yes   | Data stream management object for zlib compression and decompression.                     |
| level    | [CompressLevel](#compresslevel)    | Yes   | See [CompressLevel enum definition](#compresslevel).       |
| strategy | [CompressStrategy](#compressstrategy) | Yes   | See [CompressStrategy enum definition](#compressstrategy). |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync()
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflateParams(zStream, zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION, zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY).then((data) => {
    console.info('deflateParams success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

### deflatePrime<sup>12+</sup>

deflatePrime(strm: ZStream, bits: number, value: number): Promise&lt;ReturnStatus&gt;

Inserts bits and a value into the compression stream. This API uses a promise to return the result. It must be called after the compression stream is initialized by **deflateInit** or **deflateInit2**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type   | Mandatory| Description                           |
| ------ | ------- | ---- | ------------------------------- |
| strm   | [ZStream](#zstream12) | Yes   | Data stream management object for zlib compression and decompression. |
| bits   | number  | Yes   | Number of bits to insert. Value range: [0, 16].  |
| value  | number  | Yes   | Bit value corresponding to the number of bits. The value range is determined by bits.            |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result status.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

async function demo() {
  let str = 'hello world!';
  let arrayBufferIn = new ArrayBuffer(str.length);
  let byteArray = new Uint8Array(arrayBufferIn);
  for (let i = 0, j = str.length; i < j; i++) {
    byteArray[i] = str.charCodeAt(i)
  }
  let arrayBufferOut = new ArrayBuffer(100);
  let zStream: zlib.ZStream = {
    nextIn: arrayBufferIn,
    availableIn: 1,
    nextOut: arrayBufferOut,
    availableOut: 1
  };
  let zip = zlib.createZipSync();
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
    console.info('deflateInit success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
  await zip.deflatePrime({ nextOut: arrayBufferOut }, 5, 2).then((data) => {
    console.info('deflatePrime success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```

## Options

Defines options used to compress or decompress a ZIP file.

**System capability**: SystemCapability.BundleManager.Zlib

| Name    | Type            | Read-Only| Optional| Description                                                      |
| -------- | ---------------- | ---- | ---------------------------------------------------------- | ---- |
| level    | [CompressLevel](#compresslevel)     | No   | Yes  | Compression level specified during compression or decompression. The default value is COMPRESS_LEVEL_DEFAULT_COMPRESSION.<br>**Atomic service API:** This API is supported in atomic services since API version 11.       |
| memLevel | [MemLevel](#memlevel)         | No   | Yes  | Memory level specified during compression. The default value is MEM_LEVEL_DEFAULT.<br>**Atomic service API:** This API is supported in atomic services since API version 11.                        |
| strategy | [CompressStrategy](#compressstrategy) | No   | Yes  | Compression strategy specified during compression. The default value is COMPRESS_STRATEGY_DEFAULT_STRATEGY.<br>**Atomic service API:** This API is supported in atomic services since API version 11.        |
| parallel<sup>18+</sup> | [ParallelStrategy](#parallelstrategy18) | No   | Yes  | Serial or parallel strategy specified during compression or decompression. The default value is PARALLEL_STRATEGY_SEQUENTIAL.<br>**Atomic service API:** This API is supported in atomic services since API version 18.        |
| pathSeparatorStrategy<sup>21+</sup> | [PathSeparatorStrategy](#pathseparatorstrategy21) | No   | Yes  | Strategy for handling the separator in the file path within the archive during decompression. The default value is PATH_SEPARATOR_STRATEGY_DEFAULT.<br>**Atomic service API:** This API is supported in atomic services since API version 21.        |
| keepTopLevelFolder | boolean | No   | Yes  | Whether to retain the top-level folder in the archive when compressing a folder. The value true means to retain the top-level folder, and false means not to retain it. The default value is false.<br/>**Since:** 26.0.0 <br/>**Atomic service API:** This API is supported in atomic services since API version 26.0.0.<br>**Model restriction:** This API can be used only in the stage model.        |

## CompressLevel

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.BundleManager.Zlib

| Name                              | Value  | Description             |
| ---------------------------------- | ---- | ----------------- |
| COMPRESS_LEVEL_NO_COMPRESSION      | 0    | Compression level with a compression ratio of 0. It applies to scenarios where data is not compressed, such as already compressed images or video files. |
| COMPRESS_LEVEL_BEST_SPEED          | 1    | Completes compression at the fastest speed with a lower compression ratio. It is suitable for scenarios with high real-time requirements.  |
| COMPRESS_LEVEL_BEST_COMPRESSION    | 9    | Completes compression at the highest compression ratio with a slower compression speed. It is suitable for scenarios sensitive to storage space.      |
| COMPRESS_LEVEL_DEFAULT_COMPRESSION | -1   | Default compression level, which balances compression speed and compression ratio. It is suitable for most scenarios.      |

## MemLevel

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.BundleManager.Zlib

| Name             | Value  | Description                            |
| ----------------- | ---- | -------------------------------- |
| MEM_LEVEL_MIN     | 1    | Uses the minimum memory for compression. It has the slowest compression speed but the lowest memory usage, and is suitable for memory-constrained scenarios. |
| MEM_LEVEL_MAX     | 9    | Uses the maximum memory for compression. It has the fastest compression speed but the highest memory usage, and is suitable for scenarios with sufficient memory. |
| MEM_LEVEL_DEFAULT | 8    | Default memory level. It strikes a balance between compression speed and memory usage, and is suitable for most scenarios. |

## CompressStrategy

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.BundleManager.Zlib

| Name                              | Value  | Description                    |
| ---------------------------------- | ---- | ------------------------ |
| COMPRESS_STRATEGY_DEFAULT_STRATEGY | 0    | Default data strategy, applicable to most data types and providing balanced compression performance.             |
| COMPRESS_STRATEGY_FILTERED         | 1    | Compression strategy for data produced by a filter. Applicable to preprocessed or filtered data, such as delta-encoded data. |
| COMPRESS_STRATEGY_HUFFMAN_ONLY     | 2    | Huffman coding compression strategy. Uses only Huffman coding without string matching, applicable to scenarios that require fast compression.   |
| COMPRESS_STRATEGY_RLE              | 3    | Run-length encoding compression strategy. Applicable to data containing a large number of repeated bytes, such as bitmap images.         |
| COMPRESS_STRATEGY_FIXED            | 4    | Fixed compression strategy. Uses fixed Huffman coding, applicable to scenarios that require fixed encoded output.           |

## ParallelStrategy<sup>18+</sup>

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.BundleManager.Zlib

| Name                                    | Value  | Description                     |
| ---------------------------------------- | ---- | ------------------------ |
| PARALLEL_STRATEGY_SEQUENTIAL             | 0    | Default value. Sequential compression/decompression strategy that processes files one by one in order, suitable for small files or single-core processor scenarios.|
| PARALLEL_STRATEGY_PARALLEL_DECOMPRESSION | 1    | Parallel decompression strategy that uses multiple cores for parallel processing to improve the decompression speed of large files.            |

## PathSeparatorStrategy<sup>21+</sup>

Enumerates the strategies for handling the separator in the file path of the target archive during decompression.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.BundleManager.Zlib

| Name                                     | Value  | Description                                      |
| ----------------------------------------- | ---- | ----------------------------------------- |
| PATH_SEPARATOR_STRATEGY_DEFAULT           | 0    | Default value, indicating that separators in the file path of the compressed package are not processed.   |
| PATH_SEPARATOR_STRATEGY_REPLACE_BACKSLASH | 1    | Backslashes (\) in the file path of the package are replaced with slashes (/).|

## ErrorCode<sup>(deprecated)</sup>

> **NOTE**
>  
> This API is supported since API version 7 and deprecated since API version 9. No substitute is provided.

**System capability**: SystemCapability.BundleManager.Zlib

| Name            | Value  | Description        |
| ---------------- | ---- | ------------ |
| ERROR_CODE_OK    | 0    | The API is successfully called.|
| ERROR_CODE_ERRNO | -1   | Failed to call the API.|

## CompressFlushMode<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

| Name         | Value  | Description                                        |
| ------------- | ---- | -------------------------------------------- |
| NO_FLUSH      | 0    | Default value, indicating a normal operation.                      |
| PARTIAL_FLUSH | 1    | Generates a partial flush point in the stream. This is applicable to scenarios where a synchronization point is required so that the decompression stream can be recovered.                       |
| SYNC_FLUSH    | 2    | Forces all compressed data to be output while maintaining the state of the compression stream. This is applicable to scenarios where compressed data needs to be output in real time, such as network transmission. |
| FULL_FLUSH    | 3    | Resets the compression state. This is applicable to scenarios where the compression stream needs to be completely reset, such as compressing multiple independent data blocks.                               |
| FINISH        | 4    | Ends the compression or decompression process. This is applicable to the final step of the compression process to ensure that all data is completely output.                       |
| BLOCK         | 5    | Allows more precise control.                          |
| TREES         | 6    | Implements special purposes.                      |

## CompressMethod<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

| Name    | Value  | Description      |
| -------- | ---- | ---------- |
| DEFLATED | 8 | Uses the DEFLATE algorithm for compression, which is the standard compression method of the zlib library. |

## ReturnStatus<sup>12+</sup>

**System capability**: SystemCapability.BundleManager.Zlib

| Name      | Value  | Description                                          |
| ---------- | ---- | ---------------------------------------------- |
| OK         | 0    | The API is successfully called. This API is supported for use in atomic services.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| STREAM_END | 1    | The API is successfully called, indicating that the entire data has been processed.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| NEED_DICT  | 2    | The API is successfully called, indicating that a preset dictionary is required to continue decompression.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| ERRNO<sup>23+</sup>| -1 | The API fails to be called, indicating that the file operation is incorrect.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| STREAM_ERROR<sup>23+</sup>| -2 | The API fails to be called, indicating that the compression or decompression stream is incorrect.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| DATA_ERROR<sup>23+</sup>| -3 | The API fails to be called, indicating that the input data is incorrect.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| MEM_ERROR<sup>23+</sup>| -4 | The API fails to be called, indicating that the memory allocation fails.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| BUF_ERROR<sup>23+</sup>| -5 | The API fails to be called, indicating that the input buffer is incorrect.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|

## ZStream<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

| Name        | Type       | Read-Only| Optional| Description                                                        |
| ------------ | ----------- | ---- | ---- | ------------------------------------------------------------ |
| nextIn       | ArrayBuffer | No  | Yes  | Input bytes to be compressed.                                          |
| availableIn  | number      | No  | Yes  | Number of bytes available for **nextIn**.                                          |
| totalIn      | number      | No  | Yes  | Total number of input bytes read so far.                                |
| nextOut      | ArrayBuffer | No  | Yes  | Output bytes after compression.                                            |
| availableOut | number      | No  | Yes  | Number of remaining bytes available for **nextOut**.                                     |
| totalOut     | number      | No  | Yes  | Total number of output bytes.                                      |
| dataType     | number      | No  | Yes  | Binary or text of **deflate**, or decoding state of **inflate**.|
| adler        | number      | No  | Yes  | Adler-32 or CRC-32 value of uncompressed data.                              |

## ZipOutputInfo<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

| Name   | Type        | Read-Only| Optional| Description                                         |
| ------- | ------------ | ---- | ---- | --------------------------------------------- |
| status  | [ReturnStatus](#returnstatus12) | No   | No   | Enum type of the result of the compression or decompression function, including the success status and various error codes. |
| destLen | number       | No  | No  | Total length of the destination buffer.                         |

## DictionaryOutputInfo<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

| Name            | Type        | Read-Only| Optional| Description                                         |
| ---------------- | ------------ | ---- | ---- | --------------------------------------------- |
| status           | [ReturnStatus](#returnstatus12) | No   | No   | Enum type of the result of the compression or decompression function, including the success status and various error codes. |
| dictionaryLength | number       | No  | No  | Length of a dictionary.                                 |

## DecompressionOutputInfo<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

| Name        | Type        | Read-Only| Optional| Description                                         |
| ------------ | ------------ | ---- | ---- | --------------------------------------------- |
| status       | [ReturnStatus](#returnstatus12) | No   | No   | Enum type of the result of the compression or decompression function, including the success status and various error codes. |
| destLength   | number       | No  | No  | Length of the destination buffer.                           |
| sourceLength | number       | No  | No  | Length of the source buffer.                             |

## DeflatePendingOutputInfo<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

| Name   | Type        | Read-Only| Optional| Description                                         |
| ------- | ------------ | ---- | ---- | --------------------------------------------- |
| status  | [ReturnStatus](#returnstatus12) | No   | No   | Enum type of the execution result of the compression or decompression function, including the success status and various error codes. |
| pending | number       | No  | No  | Number of output bytes that have been generated.                         |
| bits    | number       | No  | No  | Number of output bits that have been generated.                           |

## GzHeader<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

| Name    | Type       | Read-Only| Optional| Description                                |
| -------- | ----------- | ---- | ---- | ------------------------------------ |
| isText   | boolean     | No   | Yes   | Whether the compressed data is text. true indicates that the compressed data is considered text, and false indicates that it is not. |
| os       | number      | No  | Yes  | Operating system.                          |
| time     | number      | No  | Yes  | Modification time.                          |
| xflags   | number      | No  | Yes  | Extra flag.                          |
| extra    | ArrayBuffer | No  | Yes  | Extra field.                          |
| extraLen | number      | No  | Yes  | Length of the extra field.                    |
| name     | ArrayBuffer | No  | Yes  | File name.                            |
| comment  | ArrayBuffer | No  | Yes  | Comment.                              |
| hcrc     | boolean     | No   | Yes   | Whether a CRC header exists. true indicates that a CRC header exists, and false indicates that it does not. |
| done     | boolean     | No   | Yes   | Whether the gzip header has been read. true indicates that the gzip header has been read, and false indicates that it has not.    |

## zlib.createGZip<sup>12+</sup>

createGZip(): Promise&lt;GZip&gt;

Creates this **GZip** object. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                          | Description                           |
| ------------------------------ | ------------------------------- |
| Promise&lt;[GZip](#gzip12)&gt; | Promise used to return the **GZip** object created.|

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';

zlib.createGZip().then((data) => {
  console.info('createGZip success');
})
```

## zlib.createGZipSync<sup>12+</sup>

createGZipSync():  GZip

Creates this **GZip** object. A **GZip** instance is returned upon a success.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type           | Description          |
| --------------- | -------------- |
| [GZip](#gzip12) | gzip object instance.|

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';

let gzip = zlib.createGZipSync();
```

## GZip<sup>12+</sup>

Describes gzip-related APIs.

### gzdopen<sup>12+</sup>

gzdopen(fd: number, mode: string): Promise&lt;void&gt;

Associates gzip file with the file descriptor (fd) and opens the file for reading and decompressing, or compressing and writing. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| fd     | number | Yes  | File descriptor. Generally, the value is obtained by calling the **open** method or other methods.|
| mode   | string | Yes  | Specifies the access mode. For details, see the description of [gzopen](#gzopen12).           |

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800002 | No such file or access mode error.                           |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzdopenDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzdopen");
  let path = pathDir + "/gzdopen/test.gz";
  let file = fs.openSync(path, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
  let gzip = zlib.createGZipSync();
  await gzip.gzdopen(file.fd, "wb");
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzdopenDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzbuffer<sup>12+</sup>

gzbuffer(size: number):Promise&lt;number&gt;

Sets the size of the internal buffer for the current library function. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| size   | number | Yes  | Size of the internal buffer to be set.|

**Return value**

| Type                 | Description                        |
| --------------------- | ---------------------------- |
| Promise&lt;number&gt; | Promise used to return the result. If the operation is successful, **0** is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800009   | Internal structure error. |

**Example**

```ts
import { fileIo as fs } from '@kit.CoreFileKit';
import { zlib } from '@kit.BasicServicesKit';

async function gzbufferDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzbuffer");
  let path = pathDir + "/gzbuffer/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let result = await gzip.gzbuffer(648);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzbufferDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzopen<sup>12+</sup>

gzopen(path: string, mode: string): Promise&lt;void&gt;

Opens the .gz file in the specified path for reading and decompressing, or compressing and writing. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| path   | string | Yes  | File path to open. The path must be a sandbox path, which can be obtained through the context. For details, see [Stage model](../apis-ability-kit/js-apis-inner-application-context.md).                                         |
| mode   | string | Yes  | Specifies a mode for opening a file.<br>Basic modes (one of the following must be selected):<br>- **"r"** or **"rb"**: read mode. The system automatically detects and decompresses the gzip file. If the file is not in gzip format, the original data is directly read.<br>- **"w"** or **"wb"**: write mode. The system creates a new file and compresses data.<br>- **"a"** or **"ab"**: append mode. The system appends a new gzip stream to the end of the existing file without verifying the format of the original file.<br>Optional function parameters (can be used together):<br>- Compression level: **0** (no compression) to **9** (maximum compression). The default compression level is **6**. This parameter must be used together with the write or append mode.<br>- Compression strategy: **"f"** (filtering strategy), **"h"** (Huffman coding strategy), **"R"** (RLE compression strategy), or **"F"** (fixed encoding strategy). You can only select one of the strategies.<br>- Transparent mode: **"T"**. In this mode, data is not compressed and no gzip header is generated during writing (a common file is generated). This parameter is mutually exclusive with the compression strategy parameter.<br>- Exclusive creation: **"x"**. The file fails to be opened if it already exists. This parameter must be used together with the write or append mode.<br>- Close-on-exec flag: **"e"**. This parameter is used to set the **FD_CLOEXEC** property of the file descriptor (system-dependent).<br>Examples:<br>- **"r"**: read mode. Data is read in binary format.<br>- **"rb"**: read mode. Data is read in binary format.<br>- **"wb6"**: write mode. Data is written in binary format with the compression level of 6.<br>- **"wb9f"**: write mode. Data is written in binary format with the maximum compression level and filtering strategy.<br>- **"wbT"**: write mode. Data is not compressed and a common file is generated.<br>- **"wbx"**: write mode. Data is written to the exclusively created file in binary format.<br>- **"abx"**: append mode. Data is appended and written to the exclusively created file in binary format.|

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800002 | No such file or access mode error.                           |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzopenDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzopen");
  let path = pathDir + "/gzopen/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzopenDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzeof<sup>12+</sup>

gzeof(): Promise&lt;number&gt;

Checks whether the position from which data is read has reached the end of the gzip file. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                 | Description                                                        |
| --------------------- | ------------------------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the result. If the end-of-file indicator is set while reading, **1** is returned.|

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzeofDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzeof");
  let path = pathDir + "/gzeof/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let writeBufferWithData = new ArrayBuffer(16);
  let uint8View = new Uint8Array(writeBufferWithData);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  let writeNum = await gzip.gzwrite(writeBufferWithData, 16)
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let readBufferWithData = new ArrayBuffer(20);
  let readNum = await gzip.gzread(readBufferWithData);
  let eofNum = await gzip.gzeof();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzeofDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzdirect<sup>12+</sup>

gzdirect(): Promise&lt;number&gt;

Checks whether the specified gzip file handle directly accesses the original uncompressed data and reallocates the buffer. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                 | Description                                              |
| --------------------- | -------------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result. If the original uncompressed data is directly accessed, **1** is returned.|

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzdirectDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzdirect");
  let path = pathDir + "/gzdirect/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let directNum = await gzip.gzdirect();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzdirectDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzclose<sup>12+</sup>

gzclose(): Promise&lt;ReturnStatus&gt;

Clears all pending output of the file. Closes the file and releases the decompression or compression state if necessary. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                 |
| -------- | ------------------------- |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800006 | Memory allocation failed. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzcloseDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzclose");
  let path = pathDir + "/gzclose/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzcloseDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzclearerr<sup>12+</sup>

gzclearerr(): Promise&lt;void&gt;

Clears the errors and end-of-file flags of a file. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzclearerrDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzclearerr");
  let path = pathDir + "/gzclearerr/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let writeBufferWithData = new ArrayBuffer(16);
  let uint8View = new Uint8Array(writeBufferWithData);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  let writeNum = await gzip.gzwrite(writeBufferWithData, 16)
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let readBufferWithData = new ArrayBuffer(20);
  let readNum = await gzip.gzread(readBufferWithData);
  let eofNum = await gzip.gzeof();
  await gzip.gzclearerr();
  let eofNumClear = await gzip.gzeof();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzclearerrDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzerror<sup>12+</sup>

gzerror(): Promise&lt;GzErrorOutputInfo&gt;

Obtains the error message and status message of the last error that occurred on the file. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                                                    | Description                                                     |
| -------------------------------------------------------- | --------------------------------------------------------- |
| Promise&lt;[GzErrorOutputInfo](#gzerroroutputinfo12)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message      |
| -------- | -------------- |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzerrorDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzerror");
  let path = pathDir + "/gzerror/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let writeBufferWithData = new ArrayBuffer(16);
  let uint8View = new Uint8Array(writeBufferWithData);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  try {
    await gzip.gzwrite(writeBufferWithData, -1);
  } catch (errData) {
    await gzip.gzerror().then((GzErrorOutputInfo) => {
      console.info('errCode', GzErrorOutputInfo.status);
      console.info('errMsg', GzErrorOutputInfo.statusMsg);
    })
  }
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzerrorDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzgetc<sup>12+</sup>

gzgetc(): Promise&lt;number&gt;

Reads and decompresses a byte from a file. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                 | Description                                |
| --------------------- | ------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                 |
| -------- | ------------------------- |
| 17800009 | Internal structure error. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzgetcDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzgetc");
  let path = pathDir + "/gzgetc/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzputc(1);
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let result = await gzip.gzgetc();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzgetcDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzflush<sup>12+</sup>

gzflush(flush: CompressFlushMode): Promise&lt;ReturnStatus&gt;

Flushes all pending output into a compressed file. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type             | Mandatory| Description                                                        |
| ------ | ----------------- | ---- | ------------------------------------------------------------ |
| flush  | [CompressFlushMode](#compressflushmode12) | Yes   | Data flushing strategy during compression or decompression. |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzflushDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzflush");
  let path = pathDir + "/gzflush/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let flushNum = await gzip.gzflush(zlib.CompressFlushMode.NO_FLUSH);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzflushDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzfwrite<sup>12+</sup>

gzfwrite(buf: ArrayBuffer, size: number, nitems: number): Promise&lt;number&gt;

Compresses data blocks that are declared with size and nitems from the buffer and writes the data blocks to a file. This API uses a promise to return the result.


> **NOTE**
>
> Compared with [gzwrite](#gzwrite12), this API writes data in blocks and is suitable for writing fixed-size data blocks. gzwrite directly specifies the number of bytes to write and is suitable for writing data of any length.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type       | Mandatory| Description                  |
| ------ | ----------- | ---- | ---------------------- |
| buf    | ArrayBuffer | Yes   | Buffer that contains the data to write. |
| size   | number      | Yes  | Number of bytes in a single data block.|
| nitems | number      | Yes  | Number of data blocks to be written.    |

**Return value**

| Type                 | Description                                               |
| --------------------- | --------------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzfwriteDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzfwrite");
  let path = pathDir + "/gzfwrite/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let bufferWithData = new ArrayBuffer(16);
  let uint8View = new Uint8Array(bufferWithData);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  let result = await gzip.gzfwrite(bufferWithData, 8, 2)
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzfwriteDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzfread<sup>12+</sup>

gzfread(buf: ArrayBuffer, size: number, nitems: number): Promise&lt;number&gt;

Decompresses and reads data from a gzip file. This API uses a promise to return the result.


> **NOTE**
>
> Compared with [gzread](#gzread12), this API reads data in blocks and is suitable for reading fixed-size data blocks. gzread reads data of the buffer size and is suitable for reading data of any length.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type       | Mandatory| Description                          |
| ------ | ----------- | ---- | ------------------------------ |
| buf    | ArrayBuffer | Yes  | Destination buffer for storing read results.|
| size   | number      | Yes  | Number of bytes in a single data block.        |
| nitems | number | Yes | Number of data blocks to read. |

**Return value**

| Type                 | Description                                               |
| --------------------- | --------------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzfreadDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzfread");
  let path = pathDir + "/gzfread/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let writeBuffer = new ArrayBuffer(16);
  let uint8View = new Uint8Array(writeBuffer);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  await gzip.gzfwrite(writeBuffer, 8, 2);
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let readBuffer = new ArrayBuffer(16);
  let result = await gzip.gzfread(readBuffer, 8, 2);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzfreadDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzclosew<sup>12+</sup>

gzclosew(): Promise&lt;ReturnStatus&gt;

Implements the same functions as that of **gzclose()** for writing or appending. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                 |
| -------- | ------------------------- |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800006 | Memory allocation failed. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzclosewDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzclosew");
  let path = pathDir + "/gzclosew/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclosew();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzclosewDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzcloser<sup>12+</sup>

gzcloser(): Promise&lt;ReturnStatus&gt;

Implements the same functions as that of **gzclose()** for reading only. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message      |
| -------- | -------------- |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzcloserDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzcloser");
  let path = pathDir + "/gzcloser/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  await gzip.gzcloser();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzcloserDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzwrite<sup>12+</sup>

gzwrite(buf: ArrayBuffer, len: number): Promise&lt;number&gt;

Compresses the uncompressed bytes of the length specified by **len** in **buf** and writes them to a file. This API uses a promise to return the result. Note: This method can be used only in the write mode ("w" or "wb") of gzopen.


> **NOTE**
>
> Compared with [gzfwrite](#gzfwrite12), this API directly specifies the number of bytes to write and is suitable for writing data of any length. gzfwrite writes data in blocks and is suitable for writing fixed-size data blocks.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type       | Mandatory| Description                        |
| ------ | ----------- | ---- | ---------------------------- |
| buf    | ArrayBuffer | Yes   | Buffer to which data is written. |
| len    | number      | Yes   | Length of the uncompressed data, in bytes. Value range: [0, min(buf.byteLength, 2147483647)).             |

**Return value**

| Type                 | Description                                 |
| --------------------- | ------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzwriteDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzwrite");
  let path = pathDir + "/gzwrite/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let bufferWithData = new ArrayBuffer(16);
  let uint8View = new Uint8Array(bufferWithData);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  let result = await gzip.gzwrite(bufferWithData, 16);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzwriteDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzungetc<sup>12+</sup>

gzungetc(c: number): Promise&lt;number&gt;

Pushes **c** back into the input stream so that it will be read as the first character the next time the file is read. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type  | Mandatory| Description                    |
| ------ | ------ | ---- | ------------------------ |
| c      | number | Yes  | Characters before being pushed into the input stream.|

**Return value**

| Type                 | Description                         |
| --------------------- | ----------------------------- |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzungetcDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzungetc");
  let path = pathDir + "/gzungetc/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  await gzip.gzread(new ArrayBuffer(1));
  let result = await gzip.gzungetc(1);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzungetcDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gztell<sup>12+</sup>

gztell(): Promise&lt;number&gt;

Returns the start position of the next **gzread** or **gzwrite** in the file. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                 | Description                                                    |
| --------------------- | -------------------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the start position of the next gzread or gzwrite in the file. |

**Error codes**

For details about the error codes, see [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                 |
| -------- | ------------------------- |
| 17800009 | Internal structure error. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gztellDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gztell");
  let path = pathDir + "/gztell/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gztell();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gztellDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzsetparams<sup>12+</sup>

gzsetparams(level: CompressLevel, strategy: CompressStrategy): Promise&lt;ReturnStatus&gt;

Dynamically updates the compression level and compression strategy of a file. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name  | Type            | Mandatory| Description                                                        |
| -------- | ---------------- | ---- | ------------------------------------------------------------ |
| level    | [CompressLevel](#compresslevel)    | Yes   | Compression level. For details, see [CompressLevel](#compresslevel).      |
| strategy | [CompressStrategy](#compressstrategy) | Yes   | Compression strategy. For details, see [CompressStrategy](#compressstrategy). |

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzsetparamsDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzsetparams");
  let path = pathDir + "/gzsetparams/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzsetparams(zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
    zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzsetparamsDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzseek<sup>12+</sup>

gzseek(offset: number, whence: OffsetReferencePoint): Promise&lt;number&gt;

Sets the start position to the offset position relative to the next **gzread** or **gzwrite** in the file. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type                | Mandatory| Description                                                        |
| ------ | -------------------- | ---- | ------------------------------------------------------------ |
| offset | number               | Yes   | Target offset position, in bytes.                                               |
| whence | [OffsetReferencePoint](#offsetreferencepoint12) | Yes   | Enum type of the starting position for file seeking. |

**Return value**

| Type                 | Description                                                        |
| --------------------- | ------------------------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzseekDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzseek");
  let path = pathDir + "/gzseek/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzseek(2, zlib.OffsetReferencePoint.SEEK_CUR);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzseekDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzrewind<sup>12+</sup>

gzrewind(): Promise&lt;ReturnStatus&gt;

Repositions the file pointer to the beginning of the file. This feature is applied only for reading. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                                          | Description                       |
| ---------------------------------------------- | --------------------------- |
| Promise&lt;[ReturnStatus](#returnstatus12)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                 |
| -------- | ------------------------- |
| 17800009 | Internal structure error. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzrewindDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzrewind");
  let path = pathDir + "/gzrewind/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let result = await gzip.gzrewind();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzrewindDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzread<sup>12+</sup>

gzread(buf: ArrayBuffer): Promise&lt;number&gt;

Reads uncompressed bytes from the file and decompresses them into **buf**. The number of bytes to read is determined by the length of the **buf** buffer. This API uses a promise to return the result. Note: This method can be used only in the read mode ("r" or "rb") of gzopen.


> **NOTE**
>
> Compared with [gzfread](#gzfread12), this API reads data of the buffer size and is suitable for reading data of any length. gzfread reads data in blocks and is suitable for reading fixed-size data blocks.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type       | Mandatory| Description          |
| ------ | ----------- | ---- | -------------- |
| buf    | ArrayBuffer | Yes   | Target buffer used to store the read result. |

**Return value**

| Type                 | Description                                     |
| --------------------- | ----------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzreadDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzread");
  let path = pathDir + "/gzread/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let writeBuffer = new ArrayBuffer(16);
  let uint8View = new Uint8Array(writeBuffer);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  await gzip.gzwrite(writeBuffer, 16);
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let readBuffer = new ArrayBuffer(16);
  let result = await gzip.gzread(readBuffer);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzreadDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzputs<sup>12+</sup>

gzputs(str: string): Promise&lt;number&gt;

Compresses the given null-terminated strings and writes them to the file, excluding the null operator. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | ---------------------- |
| str    | string | Yes   | String to write into the file. |

**Return value**

| Type                 | Description                           |
| --------------------- | ------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzputsDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzputs");
  let path = pathDir + "/gzputs/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzputs("hello");
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzputsDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzputc<sup>12+</sup>

gzputc(ch: number): Promise&lt;number&gt;

Compresses **ch** converted to an unsigned character and writes it to a file. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type  | Mandatory| Description           |
| ------ | ------ | ---- | --------------- |
| ch   | number | Yes  | Write character ASCII.|

**Return value**

| Type                 | Description                         |
| --------------------- | ----------------------------- |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzputcDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzputc");
  let path = pathDir + "/gzputc/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzputc(0);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzputcDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzprintf<sup>12+</sup>

gzprintf(format: string, ...args: Array&lt;string | number&gt;): Promise&lt;number&gt;

Converts and formats the parameters under the control of the string format and then compresses and writes them into a file, as shown in the **fprintf()**. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type                         | Mandatory| Description                  |
| ------ | ----------------------------- | ---- | ---------------------- |
| format | string                        | Yes  | Format descriptors and plain text.|
| ...args   | Array&lt;string \| number&gt; | No  | List of variable parameters. If variable parameters are passed, for example, **gzprintf("name is %s, age is %d", "Tom", 23)**, the content **"name is Tom, age is 23"** is written. If no variable parameter is passed, for example, **gzprintf("name is %s, age is %d")**, the content **"name is %s, age is %d"** is written.     |

**Return value**

| Type                 | Description                                     |
| --------------------- | ----------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800009 | Internal structure error.                                    |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzprintfDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzprintf");
  let path = pathDir + "/gzprintf/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzprintf("name is %s, age is %d", "Tom", 23);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzprintfDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzoffset<sup>12+</sup>

gzoffset(): Promise&lt;number&gt;

Returns the current compressed read or write offset of the file. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Return value**

| Type                 | Description                                                 |
| --------------------- | ----------------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                 |
| -------- | ------------------------- |
| 17800009 | Internal structure error. |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzoffsetDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzoffset");
  let path = pathDir + "/gzoffset/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzoffset();
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzoffsetDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### gzgets<sup>12+</sup>

gzgets(buf: ArrayBuffer): Promise&lt;string&gt;

Reads bytes from a compressed file until a newline character is read and transferred to a buffer, or an end-of-file condition is encountered. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

**Parameters**

| Name| Type       | Mandatory| Description              |
| ------ | ----------- | ---- | ------------------ |
| buf    | ArrayBuffer | Yes  | Stores the read row data.|

**Return value**

| Type                 | Description                                 |
| --------------------- | ------------------------------------- |
| Promise&lt;string&gt; | Promise used to return a string ended with **null**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [zlib Error Codes](./errorcode-zlib.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**Example**

```ts
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzgetsDemo(pathDir: string) {
  fs.mkdirSync(pathDir + "/gzgets");
  let path = pathDir + "/gzgets/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzputs("hello");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let bufferWithData = new ArrayBuffer(16);
  let result = await gzip.gzgets(bufferWithData);
  await gzip.gzclose();
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('test gzip interface')
          .type(ButtonType.Capsule)
          .height(60)
          .width(200)
          .onClick(() => {
            let pathDir = this.getUIContext()?.getHostContext()?.cacheDir;
            if (typeof pathDir === 'string') {
              gzgetsDemo(pathDir);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## GzErrorOutputInfo<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

| Name     | Type        | Read-Only| Optional| Description                                        |
| --------- | ------------ | ---- | ---- | -------------------------------------------- |
| status    | [ReturnStatus](#returnstatus12) | No   | No   | Enum type of the result of the compression or decompression function, including the success status and various error codes. |
| statusMsg | string       | No  | No  | The last status message reported on the zlib file.    |

## OffsetReferencePoint<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.Zlib

| Name    | Value  | Description            |
| -------- | ---- | ---------------- |
| SEEK_SET | 0    | Searches from the beginning of a file.|
| SEEK_CUR | 1    | Searches from the current location.|
