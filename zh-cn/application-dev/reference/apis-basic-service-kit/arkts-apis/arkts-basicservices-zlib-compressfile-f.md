# compressFile

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## compressFile

```TypeScript
function compressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback<void>): void
```

压缩文件，压缩的结果。使用callback异步回调。

> **说明：**  
>  
> 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-zlib-function compressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback<void>): void--><!--Device-zlib-function compressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inFile | string | 是 | 指定压缩的文件夹路径或者文件路径，路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)，[Stage模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。待压缩的文件夹不可为空，否则使用[decompressFile](arkts-basicservices-zlib-decompressfile-f.md#decompressfile-1)对压缩后的文件解压时会报错。 |
| outFile | string | 是 | 指定的压缩结果的文件路径。多个线程同时压缩文件时，outFile不能相同。 |
| options | [Options](arkts-basicservices-zlib-options-i.md) | 是 | 压缩的配置参数。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 异步获取压缩结果之后的回调。成功返回null，失败返回错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [900001](../../apis-basic-services-kit/errorcode-zlib.md#900001-传入的源文件错误) | The input source file is invalid. |
| [900002](../../apis-basic-services-kit/errorcode-zlib.md#900002-传入的目标文件错误) | The input destination file is invalid. |

**示例：**

```TypeScript
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/temp,也可以通过context获取。
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
    if (errData !== null) {
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


## compressFile

```TypeScript
function compressFile(inFile: string, outFile: string, options: Options): Promise<void>
```

压缩文件，压缩的结果。使用Promise异步回调。

> **说明：**  
>  
> 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-zlib-function compressFile(inFile: string, outFile: string, options: Options): Promise<void>--><!--Device-zlib-function compressFile(inFile: string, outFile: string, options: Options): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inFile | string | 是 | 指定压缩的文件夹路径或者文件路径，路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)，[Stage模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。待压缩的文件夹不可为空，否则使用[decompressFile](arkts-basicservices-zlib-decompressfile-f.md#decompressfile-1)对压缩后的文件解压时会报错。 |
| outFile | string | 是 | 指定的压缩结果的文件路径。多个线程同时压缩文件时，outFile不能相同。 |
| options | [Options](arkts-basicservices-zlib-options-i.md) | 是 | 压缩的配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [900001](../../apis-basic-services-kit/errorcode-zlib.md#900001-传入的源文件错误) | The input source file is invalid. |
| [900002](../../apis-basic-services-kit/errorcode-zlib.md#900002-传入的目标文件错误) | The input destination file is invalid. |

**示例：**

```TypeScript
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/temp,也可以通过context获取。
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

