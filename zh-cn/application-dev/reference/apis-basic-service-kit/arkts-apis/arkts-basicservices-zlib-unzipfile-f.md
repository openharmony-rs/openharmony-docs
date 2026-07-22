# unzipFile

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## unzipFile

```TypeScript
function unzipFile(inFile: string, outFile: string, options: Options): Promise<void>
```

解压文件，解压完成后返回执行结果。使用Promise异步回调。
> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃。建议使用  
> [zlib.decompressFile](arkts-basicservices-zlib-decompressfile-f.md#decompressfile)  
> 替代。  
>  
> 传入的压缩包内部文件或者文件夹名称不能包含“../”，否则会返回-1错误码。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [decompressFile(inFile:](arkts-basicservices-zlib-decompressfile-f.md#decompressfile)

<!--Device-zlib-function unzipFile(inFile: string, outFile: string, options: Options): Promise<void>--><!--Device-zlib-function unzipFile(inFile: string, outFile: string, options: Options): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inFile | string | 是 | 指定的待解压缩文件的文件路径，路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-t.md)，[Stage模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-t.md)。如果待解压的.zip文件中包含中文的文件名或目录名，需使用UTF8进行编码，避免解压时文件名或目录名出现中文乱码。 |
| outFile | string | 是 | 指定的解压文件路径。 |
| options | [Options](arkts-basicservices-zlib-options-i.md) | 是 | 解压的可选参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回值。 |

**示例：**

```TypeScript
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/temp,也可以通过context获取。
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

