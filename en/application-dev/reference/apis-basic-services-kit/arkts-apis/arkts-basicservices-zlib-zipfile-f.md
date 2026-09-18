# zipFile

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## zipFile

```TypeScript
function zipFile(inFile: string, outFile: string, options: Options): Promise<void>
```

Zips a file. The execution result is returned after the compression is complete. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [compressFile](arkts-basicservices-zlib-compressfile-f.md)(inFile: string, outFile: string, options: Options, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.BundleManager.Zlib

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inFile | string | Yes | Path of the folder or file to zip. The path must be an application sandbox path, which can be obtained from the context. For details about the context, see FA Model and Stage Model. |
| outFile | string | Yes | Path of the zipped file. The file name extension is .zip. |
| options | [Options](arkts-basicservices-zlib-options-i.md) | Yes | Optional parameters for the zip operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
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
