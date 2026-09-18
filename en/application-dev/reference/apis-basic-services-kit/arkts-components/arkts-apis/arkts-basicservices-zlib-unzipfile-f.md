# unzipFile

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## unzipFile

```TypeScript
function unzipFile(inFile: string, outFile: string, options: Options): Promise<void>
```

Unzips a file. The execution result is returned after the decompression is complete. This API uses a promise to return the result.

> **NOTE:** 
> 
> The name of the zipped file or zipped folder cannot contain two consecutive periods and a slash (../). Otherwise,
> the error code -1 is returned.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [decompressFile](arkts-basicservices-zlib-decompressfile-f.md)(inFile: string, outFile: string, options: Options, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inFile | string | Yes | Path of the file to unzip. The path must be an application sandbox path, which can be obtained from the context. For details about the context, see FA Model and Stage Model. If the.zip file to be unzipped contains Chinese file names or folder names, use UTF-8 to encode them. Otherwise, garbled characters may be displayed after unzipping. |
| outFile | string | Yes | Path of the unzipped file. |
| options | [Options](arkts-basicservices-zlib-options-i.md) | Yes | Optional parameters for the unzip operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
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
