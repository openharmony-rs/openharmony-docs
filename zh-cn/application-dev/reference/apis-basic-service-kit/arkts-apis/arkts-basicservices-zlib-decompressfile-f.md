# decompressFile

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

<a id="decompressfile"></a>
## decompressFile

```TypeScript
function decompressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback<void>): void
```

解压文件，解压的结果。使用callback异步回调。

> **说明：**  
>  
> 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。  
>  
> 传入的压缩包内部文件或者文件夹名称不能包含“../”，否则会返回900003错误码。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-zlib-function decompressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback<void>): void--><!--Device-zlib-function decompressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inFile | string | 是 | 指定的待解压缩文件的文件路径，文件后缀需要以.zip结尾。文件路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)，[Stage模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。如果待解压的.zip文件中包含中文的文件名或目录名，需使用UTF8进行编码，避免解压时文件名或目录名出现中文乱码。 |
| outFile | string | 是 | 指定的解压后的文件夹路径，文件夹目录路径需要在系统中存在，不存在则会解压失败。路径必须为沙箱路径，沙箱路径可以通过context获取，具体方法可参考[application/context（Stage模型）](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)或 [app/context（FA模型）](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。如果待解压的文件或文件夹在解压后的路径下已经存在，则会直接覆盖同名文件或同名文件夹中的同名文件。多个线程同时解压文件时，outFile不能相同。 |
| options | [Options](arkts-basicservices-zlib-options-i.md) | 是 | 解压的配置参数。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步获取解压结果之后的回调。成功返回null，失败返回错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [900001](../../apis-basic-services-kit/errorcode-zlib.md#900001-传入的源文件错误) | The input source file is invalid. |
| [900002](../../apis-basic-services-kit/errorcode-zlib.md#900002-传入的目标文件错误) | The input destination file is invalid. |
| [900003](../../apis-basic-services-kit/errorcode-zlib.md#900003-传入的源文件格式错误或者已损坏) | The input source file is not in ZIP format or is damaged.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/temp,也可以通过context获取。
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

解压文件，解压的结果。使用callback异步回调。

> **说明：**  
>  
> 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。  
>  
> 传入的压缩包内部文件或者文件夹名称不能包含“../”，否则会返回900003错误码。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-zlib-function decompressFile(inFile: string, outFile: string, callback: AsyncCallback<void>): void--><!--Device-zlib-function decompressFile(inFile: string, outFile: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inFile | string | 是 | 指定的待解压缩文件的文件路径，文件后缀需要以.zip结尾。文件路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)，[Stage模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。如果待解压的.zip文件中包含中文的文件名或目录名，需使用UTF8进行编码，避免解压时文件名或目录名出现中文乱码。 |
| outFile | string | 是 | 指定的解压后的文件夹路径，文件夹目录路径需要在系统中存在，不存在则会解压失败。路径必须为沙箱路径，沙箱路径可以通过context获取，具体方法可参考[application/context（Stage模型）](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)或 [app/context（FA模型）](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。如果待解压的文件或文件夹在解压后的路径下已经存在，则会直接覆盖同名文件或同名文件夹中的同名文件。多个线程同时解压文件时，outFile不能相同。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步获取解压结果之后的回调。成功返回null，失败返回错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [900001](../../apis-basic-services-kit/errorcode-zlib.md#900001-传入的源文件错误) | The input source file is invalid. |
| [900002](../../apis-basic-services-kit/errorcode-zlib.md#900002-传入的目标文件错误) | The input destination file is invalid. |
| [900003](../../apis-basic-services-kit/errorcode-zlib.md#900003-传入的源文件格式错误或者已损坏) | The input source file is not in ZIP format or is damaged. |

**示例：**

```TypeScript
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/temp,也可以通过context获取。
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

解压文件，解压的结果。使用Promise异步回调。

> **说明：**  
>  
> 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。  
>  
> 传入的压缩包内部文件或者文件夹名称不能包含“../”，否则会返回900003错误码。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-zlib-function decompressFile(inFile: string, outFile: string, options?: Options): Promise<void>--><!--Device-zlib-function decompressFile(inFile: string, outFile: string, options?: Options): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inFile | string | 是 | 指定的待解压缩文件的文件路径，文件后缀需要以.zip结尾。文件路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)，[Stage模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。如果待解压的.zip文件中包含中文的文件名或目录名，需使用UTF8进行编码，避免解压时文件名或目录名出现中文乱码。 |
| outFile | string | 是 | 指定的解压后的文件夹路径，文件夹目录路径需要在系统中存在，不存在则会解压失败。路径必须为沙箱路径，沙箱路径可以通过context获取，具体方法可参考[application/context（Stage模型）](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)或 [app/context（FA模型）](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。如果待解压的文件或文件夹在解压后的路径下已经存在，则会直接覆盖同名文件或同名文件夹中的同名文件。多个线程同时解压文件时，outFile不能相同。 |
| options | [Options](arkts-basicservices-zlib-options-i.md) | 否 | 解压时的配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [900001](../../apis-basic-services-kit/errorcode-zlib.md#900001-传入的源文件错误) | The input source file is invalid. |
| [900002](../../apis-basic-services-kit/errorcode-zlib.md#900002-传入的目标文件错误) | The input destination file is invalid. |
| [900003](../../apis-basic-services-kit/errorcode-zlib.md#900003-传入的源文件格式错误或者已损坏) | The input source file is not in ZIP format or is damaged.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/temp,也可以通过context获取。
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

