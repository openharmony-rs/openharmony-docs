# @ohos.zlib (Zip模块)

本模块提供压缩解压缩文件的能力。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```javascript
import { zlib } from '@kit.BasicServicesKit';
```

## zlib.zipFile<sup>(deprecated)</sup>
zipFile(inFile: string, outFile: string, options: Options): Promise\<void>

压缩接口，压缩完成后返回执行结果，使用Promise异步返回。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用[zlib.compressFile](#zlibcompressfile9)。

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名  | 类型                | 必填 | 说明                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile  | string              | 是   | 指定压缩的文件夹路径或者文件路径，路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../apis-ability-kit/js-apis-inner-app-context.md)，[Stage模型](../apis-ability-kit/js-apis-inner-application-context.md)。 |
| outFile | string              | 是   | 指定压缩结果的文件路径（文件的扩展名zip）。                  |
| options | [Options](#options) | 是   | 压缩的可选参数。                                             |

**返回值：**

| 类型           | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise对象，无返回值。 |

**示例：**

```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xxx/filename.xxx';
let outFile = '/xxx/xxx.zip';
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

unzipFile(inFile:string, outFile:string, options: Options): Promise\<void>

解压文件，解压完成后返回执行结果，使用Promise异步返回。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用[zlib.decompressFile](#zlibdecompressfile9)。
>
> 传入的压缩包内部文件或者文件夹名称不能包含“..”或者以“/”为开头，否则会返回-1错误码。

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名  | 类型                | 必填 | 说明                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile  | string              | 是   | 指定的待解压缩文件的文件路径，路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../apis-ability-kit/js-apis-inner-app-context.md)，[Stage模型](../apis-ability-kit/js-apis-inner-application-context.md)。如果待解压的.zip文件中包含中文的文件名或目录名，需使用UTF8进行编码，避免解压时文件名或目录名出现中文乱码。 |
| outFile | string              | 是   | 指定的解压文件路径。                                         |
| options | [Options](#options) | 是   | 解压的可选参数。                                             |

**返回值：**

| 类型           | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise对象，无返回值。 |

**示例：**

```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xx/xxx.zip';
let outFile = '/xxx';
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

压缩文件，压缩的结果，使用callback异步回调返回。成功返回null，失败返回错误码。

> **说明：**
>
> 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名                  | 类型                | 必填 | 说明                                                         |
| ----------------------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile                  | string              | 是   | 指定压缩的文件夹路径或者文件路径，路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../apis-ability-kit/js-apis-inner-app-context.md)，[Stage模型](../apis-ability-kit/js-apis-inner-application-context.md)。待压缩的文件夹不可为空，否则使用[decompressFile](#zlibdecompressfile9)对压缩后的文件解压时会报错。 |
| outFile                 | string              | 是   | 指定的压缩结果的文件路径。多个线程同时压缩文件时，outFile不能相同。                                           |
| options                 | [Options](#options) | 是   | 压缩的配置参数。                                               |
| callback | AsyncCallback\<void>            | 是   | 异步获取压缩结果之后的回调。成功返回null，失败返回错误码。             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                               |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 900001   | The input source file is invalid.      |
| 900002   | The input destination file is invalid. |

**示例：**

ArkTS-Dyn:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xxx/filename.xxx';
let outFile = '/xxx/xxx.zip';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  memLevel: zlib.MemLevel.MEM_LEVEL_DEFAULT,
  strategy: zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY
};

try {
  zlib.compressFile(inFile, outFile, options, (errData: BusinessError) => {
    if (errData !== null) {
      console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
    }
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xxx/filename.xxx';
let outFile = '/xxx/xxx.zip';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  memLevel: zlib.MemLevel.MEM_LEVEL_DEFAULT,
  strategy: zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY
};

try {
  zlib.compressFile(inFile, outFile, options, (errData: BusinessError | null) => {
    if (errData !== null) {
      console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
    }
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```

## zlib.compressFile<sup>9+</sup>

compressFile(inFile: string, outFile: string, options: Options): Promise\<void>

压缩文件，压缩的结果，使用Promise异步返回。成功时返回null，失败时返回错误码。

> **说明：**
>
> 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                | 必填 | 说明                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile  | string              | 是   | 指定压缩的文件夹路径或者文件路径，路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../apis-ability-kit/js-apis-inner-app-context.md)，[Stage模型](../apis-ability-kit/js-apis-inner-application-context.md)。待压缩的文件夹不可为空，否则使用[decompressFile](#zlibdecompressfile9)对压缩后的文件解压时会报错。 |
| outFile | string              | 是   | 指定的压缩结果的文件路径。多个线程同时压缩文件时，outFile不能相同。                                           |
| options | [Options](#options) | 是   | 压缩的配置参数。                                               |

**返回值：**

| 类型           | 说明                    |
| -------------- | ----------------------- |
| Promise\<void> | Promise对象，无返回值。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                               |
| -------- | ------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 900001   | The input source file is invalid.      |
| 900002   | The input destination file is invalid. |

**示例：**

ArkTS-Dyn:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xxx/filename.xxx';
let outFile = '/xxx/xxx.zip';
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xxx/filename.xxx';
let outFile = '/xxx/xxx.zip';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  memLevel: zlib.MemLevel.MEM_LEVEL_DEFAULT,
  strategy: zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY
};

try {
  zlib.compressFile(inFile, outFile, options).then(() => {
    console.info('compressFile success.');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```

## zlib.decompressFile<sup>9+</sup>

decompressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback\<void>): void

解压文件，解压的结果，使用callback异步回调返回。成功时返回null，失败时返回错误码。

> **说明：**
>
> 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。
>
> 传入的压缩包内部文件或者文件夹名称不能包含“..”或者以“/”为开头，否则会返回900003错误码。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名                  | 类型                | 必填 | 说明                                                         |
| ----------------------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile                  | string              | 是   | 指定的待解压缩文件的文件路径，文件后缀需要以.zip结尾。文件路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../apis-ability-kit/js-apis-inner-app-context.md)，[Stage模型](../apis-ability-kit/js-apis-inner-application-context.md)。如果待解压的.zip文件中包含中文的文件名或目录名，需使用UTF8进行编码，避免解压时文件名或目录名出现中文乱码。 |
| outFile                 | string              | 是   | 指定的解压后的文件夹路径，文件夹目录路径需要在系统中存在，不存在则会解压失败。路径必须为沙箱路径，沙箱路径可以通过context获取，具体方法可参考[application/context（Stage模型）](../apis-ability-kit/js-apis-inner-application-context.md)或 [app/context（FA模型）](../apis-ability-kit/js-apis-inner-app-context.md)。如果待解压的文件或文件夹在解压后的路径下已经存在，则会直接覆盖同名文件或同名文件夹中的同名文件。多个线程同时解压文件时，outFile不能相同。 |
| options                 | [Options](#options) | 是   | 解压的配置参数。                                             |
| callback | AsyncCallback\<void>            | 是   | 异步获取解压结果之后的回调。成功返回null，失败返回错误码。                                             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                               |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 900001   | The input source file is invalid.      |
| 900002   | The input destination file is invalid. |
| 900003 | The input source file is not in ZIP format or is damaged. |

**示例：**

ArkTS-Dyn:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xx/xxx.zip';
let outFileDir = '/xxx';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  parallel: zlib.ParallelStrategy.PARALLEL_STRATEGY_PARALLEL_DECOMPRESSION
};

try {
  zlib.decompressFile(inFile, outFileDir, options, (errData: BusinessError) => {
    if (errData !== null) {
      console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
    }
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xx/xxx.zip';
let outFileDir = '/xxx';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  parallel: zlib.ParallelStrategy.PARALLEL_STRATEGY_PARALLEL_DECOMPRESSION
};

try {
  zlib.decompressFile(inFile, outFileDir, options, (errData: BusinessError | null) => {
    if (errData !== null) {
      console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
    }
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```

## zlib.decompressFile<sup>9+</sup>

decompressFile(inFile: string, outFile: string, options?: Options): Promise\<void>

解压文件，解压的结果，使用Promise异步返回，成功时返回null，失败时返回错误码。

> **说明：**
>
> 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。
>
> 传入的压缩包内部文件或者文件夹名称不能包含“..”或者以“/”为开头，否则会返回900003错误码。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                | 必填 | 说明                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile  | string              | 是   | 指定的待解压缩文件的文件路径，文件后缀需要以.zip结尾。文件路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../apis-ability-kit/js-apis-inner-app-context.md)，[Stage模型](../apis-ability-kit/js-apis-inner-application-context.md)。如果待解压的.zip文件中包含中文的文件名或目录名，需使用UTF8进行编码，避免解压时文件名或目录名出现中文乱码。 |
| outFile | string              | 是   | 指定的解压后的文件夹路径，文件夹目录路径需要在系统中存在，不存在则会解压失败。路径必须为沙箱路径，沙箱路径可以通过context获取，具体方法可参考[application/context（Stage模型）](../apis-ability-kit/js-apis-inner-application-context.md)或 [app/context（FA模型）](../apis-ability-kit/js-apis-inner-app-context.md)。如果待解压的文件或文件夹在解压后的路径下已经存在，则会直接覆盖同名文件或同名文件夹中的同名文件。多个线程同时解压文件时，outFile不能相同。 |
| options | [Options](#options) | 否   | 解压时的配置参数。                                           |

**返回值：**

| 类型           | 说明                    |
| -------------- | ----------------------- |
| Promise\<void> | Promise对象，无返回值。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                               |
| ------ | ------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 900001 | The input source file is invalid.      |
| 900002 | The input destination file is invalid. |
| 900003 | The input source file is not in ZIP format or is damaged. |

**示例：**

ArkTS-Dyn:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xx/xxx.zip';
let outFileDir = '/xxx';
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xx/xxx.zip';
let outFileDir = '/xxx';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION
};

try {
  zlib.decompressFile(inFile, outFileDir, options).then(() => {
    console.info('decompressFile success.');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```

## zlib.decompressFile<sup>10+</sup>

decompressFile(inFile: string, outFile: string, callback: AsyncCallback\<void\>): void

解压文件，解压的结果，使用callback异步回调返回。成功时返回null，失败时返回错误码。

> **说明：**
>
> 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。
>
> 传入的压缩包内部文件或者文件夹名称不能包含“..”或者以“/”为开头，否则会返回900003错误码。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名                  | 类型                | 必填 | 说明                                                         |
| ----------------------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFile                  | string              | 是   | 指定的待解压缩文件的文件路径，文件后缀需要以.zip结尾。文件路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../apis-ability-kit/js-apis-inner-app-context.md)，[Stage模型](../apis-ability-kit/js-apis-inner-application-context.md)。如果待解压的.zip文件中包含中文的文件名或目录名，需使用UTF8进行编码，避免解压时文件名或目录名出现中文乱码。 |
| outFile                 | string              | 是   | 指定的解压后的文件夹路径，文件夹目录路径需要在系统中存在，不存在则会解压失败。路径必须为沙箱路径，沙箱路径可以通过context获取，具体方法可参考[application/context（Stage模型）](../apis-ability-kit/js-apis-inner-application-context.md)或 [app/context（FA模型）](../apis-ability-kit/js-apis-inner-app-context.md)。如果待解压的文件或文件夹在解压后的路径下已经存在，则会直接覆盖同名文件或同名文件夹中的同名文件。多个线程同时解压文件时，outFile不能相同。 |
| callback | AsyncCallback\<void>            | 是   | 异步获取解压结果之后的回调。成功返回null，失败返回错误码。                                             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                               |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 900001   | The input source file is invalid.      |
| 900002   | The input destination file is invalid. |
| 900003 | The input source file is not in ZIP format or is damaged. |

**示例：**

ArkTS-Dyn:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xx/xxx.zip';
let outFileDir = '/xxx';

try {
  zlib.decompressFile(inFile, outFileDir, (errData: BusinessError) => {
    if (errData !== null) {
      console.error(`decompressFile failed. code is ${errData.code}, message is ${errData.message}`);
    }
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`decompressFile failed. code is ${code}, message is ${message}`);
}
```
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xx/xxx.zip';
let outFileDir = '/xxx';

try {
  zlib.decompressFile(inFile, outFileDir, (errData: BusinessError | null) => {
    if (errData !== null) {
      console.error(`decompressFile failed. code is ${errData.code}, message is ${errData.message}`);
    }
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`decompressFile failed. code is ${code}, message is ${message}`);
}
```

## zlib.getOriginalSize<sup>12+</sup>

ArkTS-Dyn: getOriginalSize(compressedFile: string): Promise\<number><br>
ArkTS-Sta: getOriginalSize(compressedFile: string): Promise\<long>

获取压缩文件的原始大小，使用Promise异步返回。成功时返回压缩文件的原始大小，失败时返回错误码。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                | 必填 | 说明                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| compressedFile  | string              | 是   | 指定的压缩文件的文件路径，只支持zip格式压缩文件。文件路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../apis-ability-kit/js-apis-inner-app-context.md)，[Stage模型](../apis-ability-kit/js-apis-inner-application-context.md)。 |

**返回值：**

| 类型           | 说明                    |
| -------------- | ----------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象，返回压缩文件的原始大小，单位字节。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                               |
| ------ | ------------------------------------- |
| 401 | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 900001 | The input source file is invalid.      |
| 900003 | The input source file is not in ZIP format or is damaged. |

**示例：**

ArkTS-Dyn: 
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/temp，也可以通过context获取。
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
ArkTS-Sta: 
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/temp，也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let compressedFile = '/data/storage/el2/base/temp/test.zip';

try {
  zlib.getOriginalSize(compressedFile).then((data: long) => {
    console.info(`getOriginalSize success. getOriginalSize: ${data}`);
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```

## zlib.compressFiles<sup>12+</sup>

compressFiles(inFiles: Array\<string>, outFile: string, options: Options): Promise\<void>

压缩指定的多个文件，使用Promise异步返回。成功时返回null，失败时返回错误码。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                | 必填 | 说明                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| inFiles | Array\<string> | 是   | 指定压缩的文件夹路径或者文件路径，路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../apis-ability-kit/js-apis-inner-app-context.md)，[Stage模型](../apis-ability-kit/js-apis-inner-application-context.md)。待压缩的文件夹不可为空，否则使用[decompressFile](#zlibdecompressfile9)对压缩后的文件解压时会报错。 |
| outFile | string              | 是   | 指定的压缩结果的文件路径。多个线程同时压缩文件时，outFile不能相同。 |
| options | [Options](#options) | 是   | 压缩的配置参数。                                             |

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise\<void> | Promise对象，无返回值。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 900001   | The input source file is invalid.                            |
| 900002   | The input destination file is invalid.                       |

**示例：**

ArkTS-Dyn:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/temp，也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xxx/filename.xxx';
let pathDir = '';
let outFile = '/xxx/xxx.zip';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  memLevel: zlib.MemLevel.MEM_LEVEL_DEFAULT,
  strategy: zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY
};

try {
  zlib.compressFiles([inFile, pathDir, pathDir], outFile, options).then((data: void) => {
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/temp，也可以通过context获取。
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let inFile = '/xxx/filename.xxx';
let pathDir = '';
let outFile = '/xxx/xxx.zip';
let options: zlib.Options = {
  level: zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
  memLevel: zlib.MemLevel.MEM_LEVEL_DEFAULT,
  strategy: zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY
};

try {
  zlib.compressFiles([inFile, pathDir, pathDir], outFile, options).then(() => {
    console.info('compressFiles success.');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```

## zlib.createChecksum<sup>12+</sup>

createChecksum(): Promise\<Checksum>

创建校验对象，使用Promise异步返回。成功时返回Checksum对象实例。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                   | 说明                            |
| -------------------------------------- | ------------------------------- |
| Promise\<[Checksum](#checksum12)> | Promise对象。返回校验对象实例。 |

**示例：**

ArkTS-Dyn:
```ts
import { zlib } from '@kit.BasicServicesKit';

zlib.createChecksum().then((data) => {
  console.info('createChecksum success');
})
```
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

zlib.createChecksum().then((data: zlib.Checksum) => {
  console.info('createChecksum success');
}).catch((errData: Error) => {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
})
```

## zlib.createChecksumSync<sup>12+</sup>

createChecksumSync():  Checksum

创建校验对象。成功时返回Checksum对象实例。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                    | 说明           |
| ----------------------- | -------------- |
| [Checksum](#checksum12) | 校验对象实例。 |

**示例：**

```ts
import { zlib } from '@kit.BasicServicesKit';

let checksum = zlib.createChecksumSync()
```

## Checksum<sup>12+</sup>

校验对象。

### adler32<sup>12+</sup>

ArkTS-Dyn: adler32(adler: number, buf: ArrayBuffer): Promise\<number><br>
ArkTS-Sta: adler32(adler: long, buf: ArrayBuffer): Promise\<long>

计算Adler-32校验和，使用Promise异步返回。成功时返回计算后的Adler-32校验和，失败时返回错误码。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型        | 必填 | 说明                     |
| ------ | ----------- | ---- | ------------------------ |
| adler  | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | Adler-32校验和的初始值。 |
| buf    | ArrayBuffer | 是   | 计算校验和数据缓冲区。   |

**返回值：**

| 类型                  | 说明                                      |
| --------------------- | ----------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象。返回计算后的Adler-32校验和。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                               |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(12);
let data = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  data[i] = str.charCodeAt(i);
}

let checksum = zlib.createChecksumSync()

checksum.adler32(0, arrayBufferIn).then((data: long) => {
  console.info('adler32 success', data);
}).catch((errData: Error) => {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
})
```

### adler32Combine<sup>12+</sup>

ArkTS-Dyn: adler32Combine(adler1: number, adler2: number, len2: number): Promise\<number><br>
ArkTS-Sta: adler32Combine(adler1: long, adler2: long, len2: long): Promise\<long>

将两个Adler-32校验和合并，使用Promise异步返回。成功时返回合并后的Adler-32校验和，失败时返回错误码。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                                 |
| ------ | ------ | ---- | ------------------------------------ |
| adler1 | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 第一个要合并的Adler-32校验和。       |
| adler2 | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 第二个要合并的Adler-32校验和。       |
| len2   | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 第二个Adler-32校验和的数据块的长度。 |

**返回值：**

| 类型                  | 说明                                      |
| --------------------- | ----------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象。返回合并后的Adler-32校验和。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                               |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  let adler1: long = 0;
  let adler2: long = 1;
  await checksum.adler32(0, arrayBufferIn).then((data: long) => {
    console.info('adler32 success', data);
    adler1 = data;
  })
  await checksum.adler32(1, arrayBufferIn).then((data: long) => {
    console.info('adler32 success', data);
    adler2 = data;
  })
  try {
    await checksum.adler32Combine(adler1, adler2, 12).then((data: long) => {
      console.info('adler32Combine success', data);
    }).catch((errData: Error) => {
      console.error(`adler32Combine errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
    })
  } catch (errData) {
    console.error(`adler32Combine errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  }
}
```

### crc32<sup>12+</sup>

ArkTS-Dyn: crc32(crc: number, buf: ArrayBuffer): Promise\<number><br>
ArkTS-Sta: crc32(crc: long, buf: ArrayBuffer): Promise\<long>

更新CRC-32校验，使用Promise异步返回。成功时返回更新后的CRC-32校验，失败时返回错误码。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型        | 必填 | 说明                 |
| ------ | ----------- | ---- | -------------------- |
| crc    | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | CRC-32校验的初始值。 |
| buf    | ArrayBuffer | 是   | 计算校验数据缓冲区。 |

**返回值：**

| 类型                  | 说明                                  |
| --------------------- | ------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象。返回更新后的CRC-32校验。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                               |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(12);
let data = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  data[i] = str.charCodeAt(i);
}

let checksum = zlib.createChecksumSync()

checksum.crc32(0, arrayBufferIn).then((data: long) => {
  console.info('crc32 success', data);
}).catch((errData: Error) => {
  console.error(`crc32 errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
})
```

### crc32Combine<sup>12+</sup>

ArkTS-Dyn: crc32Combine(crc1: number, crc2: number, len2: number): Promise\<number><br>
ArkTS-Sta: crc32Combine(crc1: long, crc2: long, len2: long): Promise\<long>

将两个CRC-32校验合并，使用Promise异步返回。成功时返回合并后的CRC-32校验，失败时返回错误码。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                             |
| ------ | ------ | ---- | -------------------------------- |
| crc1 | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 第一个要合并的CRC-32校验。       |
| crc2 | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 第二个要合并的CRC-32校验。       |
| len2 | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 第二个CRC-32校验的数据块的长度。 |

**返回值：**

| 类型                  | 说明                                  |
| --------------------- | ------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象。返回合并后的CRC-32校验。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                               |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  let crc1: long = 0;
  let crc2: long = 1;
  await checksum.crc32(0, arrayBufferIn).then((data: long) => {
    console.info('crc32 success', data);
    crc1 = data;
  })
  await checksum.crc32(1, arrayBufferIn).then((data: long) => {
    console.info('crc32 success', data);
    crc2 = data;
  })
  try {
    await checksum.crc32Combine(crc1, crc2, 12).then((data: long) => {
      console.info('crc32Combine success', data);
    }).catch((errData: Error) => {
      console.error(`crc32Combine errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
    })
  } catch (errData) {
    console.error(`crc32Combine errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  }
}
```

### crc64<sup>12+</sup>

ArkTS-Dyn: crc64(crc: number, buf: ArrayBuffer): Promise\<number><br>
ArkTS-Sta: crc64(crc: long, buf: ArrayBuffer): Promise\<long>

更新CRC-64校验，使用Promise异步返回。成功时返回更新后的CRC-64校验，失败时返回错误码。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型        | 必填 | 说明                 |
| ------ | ----------- | ---- | -------------------- |
| crc    | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | CRC-64校验的初始值。 |
| buf    | ArrayBuffer | 是   | 计算校验数据缓冲区。 |

**返回值：**

| 类型                  | 说明                                  |
| --------------------- | ------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象。返回更新后的CRC-64校验。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                               |
| -------- | --------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(12);
let data = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  data[i] = str.charCodeAt(i);
}

let checksum = zlib.createChecksumSync()

checksum.crc64(0, arrayBufferIn).then((data: long) => {
  console.info('crc64 success', data);
}).catch((errData: Error) => {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
})
```

### getCrcTable<sup>12+</sup>

ArkTS-Dyn: getCrcTable(): Promise\<Array\<number>><br>
ArkTS-Sta: getCrcTable(): Promise\<Array\<long>>

输出CRC-32校验表，使用Promise异步返回。成功时返回CRC-32校验表。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                               | 说明                            |
| ---------------------------------- | ------------------------------- |
| ArkTS-Dyn: Promise\<Array\<number>><br>ArkTS-Sta: Promise\<Array\<long>> | Promise对象。返回CRC-32校验表。 |

**示例：**

ArkTS-Dyn:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let checksum = zlib.createChecksumSync()

checksum.getCrcTable().then((data) => {
  console.info('getCrcTable success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let checksum = zlib.createChecksumSync()

checksum.getCrcTable().then((data: Array<long>) => {
  console.info('getCrcTable success');
}).catch((errData: Error) => {
  console.error(`getCrcTable errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
})
```

### getCrc64Table<sup>12+</sup>

ArkTS-Dyn: getCrc64Table(): Promise\<Array\<number>><br>
ArkTS-Sta: getCrc64Table(): Promise\<Array\<long>>

输出CRC-64校验表，使用Promise异步返回。成功时返回CRC-64校验表。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                               | 说明                            |
| ---------------------------------- | ------------------------------- |
| ArkTS-Dyn: Promise\<Array\<number>><br>ArkTS-Sta: Promise\<Array\<long>> | Promise对象。返回CRC-64校验表。 |

**示例：**

ArkTS-Dyn:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let checksum = zlib.createChecksumSync()

checksum.getCrc64Table().then((data) => {
  console.info('getCrc64Table success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let checksum = zlib.createChecksumSync()

checksum.getCrc64Table().then((data: Array<long>) => {
  console.info('getCrc64Table success');
}).catch((errData: Error) => {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
})
```

## zlib.createZip<sup>12+</sup>

createZip(): Promise\<Zip>

创建压缩解压缩对象实例，使用Promise异步返回，成功时返回压缩解压缩对象实例。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                         | 说明                                  |
| ---------------------------- | ------------------------------------- |
| Promise\<[Zip](#zip12)> | Promise对象。返回压缩解压缩对象实例。 |

**示例：**

ArkTS-Dyn:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zlib.createZip().then(data => {
  console.info('createZip success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zlib.createZip().then((data: zlib.Zip) => {
  console.info('createZip success');
}).catch((errData: Error) => {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
})
```

## zlib.createZipSync<sup>12+</sup>

createZipSync(): Zip

创建压缩解压缩对象实例，成功时返回压缩解压缩对象实例。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型          | 说明                     |
| ------------- | ------------------------ |
| [Zip](#zip12) | 返回压缩解压缩对象实例。 |

**示例：**

```ts
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();
```

## Zip<sup>12+</sup>

压缩解压缩对象实例，支持以zlib、deflate、gzip格式对数据进行压缩与解压。

### getZStream<sup>12+</sup>

ArkTS-Dyn: getZStream(): Promise\<ZStream><br>
ArkTS-Sta: getZStream(): Promise\<ZStream | undefined>

输出流，使用Promise异步返回。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                 | 说明                      |
| ------------------------------------ | ------------------------- |
| ArkTS-Dyn: Promise\<[ZStream](#zstream12)><br>ArkTS-Sta: Promise\<[ZStream](#zstream12)> \| undefined | Promise对象。返回ZStream流。 |

**示例：**

ArkTS-Dyn:
```ts
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.getZStream().then(data => {
  console.info('getZStream success');
})
```
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.getZStream().then((data: zlib.ZStream | undefined) => {
  console.info('getZStream success');
}).catch((errData: Error) => {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
})
```

### zlibVersion<sup>12+</sup>

zlibVersion(): Promise\<string>

获取当前链接的zlib库的版本信息，使用Promise异步返回。成功时返回当前zlib库的版本信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明                                    |
| --------------------- | --------------------------------------- |
| Promise\<string> | Promise对象。返回当前zlib库的版本信息。 |

**示例：**

ArkTS-Dyn:
```ts
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.zlibVersion().then((data) => {
  console.info('zlibVersion success')
})
```
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.zlibVersion().then((data: string) => {
  console.info('zlibVersion success')
}).catch((errData: Error) => {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
})
```

### zlibCompileFlags<sup>12+</sup>

ArkTS-Dyn: zlibCompileFlags(): Promise\<number><br>
ArkTS-Sta: zlibCompileFlags(): Promise\<int>

返回指示编译时选项的标志，使用Promise异步返回。成功时返回指示编译时选项的标志。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明                                    |
| --------------------- | --------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象。返回指示编译时选项的标志。 |

**示例：**

ArkTS-Dyn:
```ts
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.zlibCompileFlags().then((data) => {
  console.info('zlibCompileFlags success')
})
```
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

zip.zlibCompileFlags().then((data: int) => {
  console.info('zlibCompileFlags success')
}).catch((errData: Error) => {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
})
```

### compress<sup>12+</sup>

ArkTS-Dyn: compress(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise\<ZipOutputInfo><br>
ArkTS-Sta: compress(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: long): Promise\<ZipOutputInfo>

将源缓冲区压缩到目标缓冲区，使用Promise异步返回。成功时返回结果状态和目标缓冲区的总大小。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型        | 必填 | 说明           |
| --------- | ----------- | ---- | -------------- |
| dest      | ArrayBuffer | 是   | 目标缓冲区。   |
| source    | ArrayBuffer | 是   | 源数据缓冲区。 |
| sourceLen | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否   | 源数据长度。默认值为0。   |

**返回值：**

| 类型                                             | 说明                                            |
| ------------------------------------------------ | ----------------------------------------------- |
| Promise\<[ZipOutputInfo](#zipoutputinfo12)> | Promise对象。返回结果状态和目标缓冲区的总大小。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800007 | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**示例：**

ArkTS-Dyn:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
}

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

zip.compress(arrayBufferOut, arrayBufferIn, 20).then((data) => {
  console.info('compress success:');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
}

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

try {
  zip.compress(arrayBufferOut, arrayBufferIn, 20).then((data: zlib.ZipOutputInfo) => {
    console.info('compress success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
} catch (errData) {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
}
```

### compress2<sup>12+</sup>

ArkTS-Dyn: compress2(dest: ArrayBuffer, source: ArrayBuffer, level: CompressLevel, sourceLen?: number): Promise\<ZipOutputInfo><br>
ArkTS-Sta: compress2(dest: ArrayBuffer, source: ArrayBuffer, level: CompressLevel, sourceLen?: long): Promise\<ZipOutputInfo>

将源缓冲区压缩到目标缓冲区，使用Promise异步返回。成功时返回结果状态和目标缓冲区的总大小。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型          | 必填 | 说明                                          |
| --------- | ------------- | ---- | --------------------------------------------- |
| dest      | ArrayBuffer   | 是   | 目标缓冲区。                                  |
| source    | ArrayBuffer   | 是   | 源数据缓冲区。                                |
| level     | CompressLevel | 是   | 参考[CompressLevel枚举定义](#compresslevel)。 |
| sourceLen | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否   | 源数据长度。默认值为0。                                  |

**返回值：**

| 类型                                             | 说明                                            |
| ------------------------------------------------ | ----------------------------------------------- |
| Promise\<[ZipOutputInfo](#zipoutputinfo12)> | Promise对象。返回结果状态和目标缓冲区的总大小。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800007 | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**示例：**

ArkTS-Dyn:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
}

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

zip.compress2(arrayBufferOut, arrayBufferIn, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data) => {
  console.info('compress2 success');
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
}

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

try {
  zip.compress2(arrayBufferOut, arrayBufferIn, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ZipOutputInfo) => {
    console.info('compress2 success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
} catch (errData) {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
}
```

### uncompress<sup>12+</sup>

ArkTS-Dyn: uncompress(dest:ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise\<ZipOutputInfo><br>
ArkTS-Sta: uncompress(dest:ArrayBuffer, source: ArrayBuffer, sourceLen?: long): Promise\<ZipOutputInfo>

将压缩后的数据解压缩为原始的未压缩形式，使用Promise异步返回。成功时返回结果状态和目标缓冲区的总大小。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型        | 必填 | 说明           |
| --------- | ----------- | ---- | -------------- |
| dest      | ArrayBuffer | 是   | 目标缓冲区。   |
| source    | ArrayBuffer | 是   | 源数据缓冲区。 |
| sourceLen | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否   | 源数据长度。默认值为0。   |

**返回值：**

| 类型                                             | 说明                                            |
| ------------------------------------------------ | ----------------------------------------------- |
| Promise\<[ZipOutputInfo](#zipoutputinfo12)> | Promise对象。返回结果状态和目标缓冲区的总大小。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800005 | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |
| 17800007 | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  try {
    await zip.compress(arrayBufferOut, arrayBufferIn, 12).then((data: zlib.ZipOutputInfo) => {
      console.info('compress success');
    }).catch((errData: Error) => {
      console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
    })
  } catch (errData) {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  }
  try {
    await zip.uncompress(arrayBufferIn, arrayBufferOut, 20).then((data: zlib.ZipOutputInfo) => {
      console.info('uncompress success');
    }).catch((errData: Error) => {
      console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
    })
  } catch (errData) {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  }
}
```

### uncompress2<sup>12+</sup>

ArkTS-Dyn: uncompress2(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise\<DecompressionOutputInfo><br>
ArkTS-Sta: uncompress2(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: long): Promise\<DecompressionOutputInfo>

将压缩后的数据解压缩为原始的未压缩形式，使用Promise异步返回。成功时返回结果状态、目标缓冲区的总大小和源数据长度。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型        | 必填 | 说明           |
| --------- | ----------- | ---- | -------------- |
| dest      | ArrayBuffer | 是   | 目标缓冲区。   |
| source    | ArrayBuffer | 是   | 源数据缓冲区。 |
| sourceLen | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否   | 源数据长度。默认值为0。   |

**返回值：**

| 类型                                                         | 说明                                                        |
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| Promise\<[DecompressionOutputInfo](#decompressionoutputinfo12)> | Promise对象。返回结果状态、目标缓冲区的总大小和源数据长度。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800005 | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |
| 17800007 | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  try {
    await zip.compress2(arrayBufferOut, arrayBufferIn, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ZipOutputInfo) => {
      console.info('compress2 success');
    }).catch((errData: Error) => {
      console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
    })
  } catch (errData) {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  }
  try {
    await zip.uncompress2(arrayBufferIn, arrayBufferOut, 20).then((data: zlib.DecompressionOutputInfo) => {
      console.info('uncompress2 success');
    }).catch((errData: Error) => {
      console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
    })
  } catch (errData) {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  }
}
```

### compressBound<sup>12+</sup>

ArkTS-Dyn: compressBound(sourceLen: number): Promise\<number><br>
ArkTS-Sta: compressBound(sourceLen: int): Promise\<int>

计算返回压缩大小的上限，使用Promise异步返回。成功时返回压缩大小的上限。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型   | 必填 | 说明         |
| --------- | ------ | ---- | ------------ |
| sourceLen | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 源数据长度。 |

**返回值：**

| 类型                  | 说明                              |
| --------------------- | --------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象。返回压缩大小的上限。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |

**示例：**

ArkTS-Dyn:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
}

let zip = zlib.createZipSync();

zip.compressBound(str.length).then((data) => {
  console.info('compressBound success')
}).catch((errData: BusinessError) => {
  console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
})
```
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
}

let zip = zlib.createZipSync();

try {
  zip.compressBound(str.length).then((data: int) => {
    console.info('compressBound success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
} catch (errData) {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
}
```

### inflateValidate<sup>12+</sup>

ArkTS-Dyn: inflateValidate(strm: ZStream, check: number): Promise\<ReturnStatus><br>
ArkTS-Sta: inflateValidate(strm: ZStream, check: int): Promise\<ReturnStatus>

验证压缩流结构内部的校验和，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |
| check  | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 预期的校验和。                  |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateValidate({ availableIn: 1 }, 1).then((data: zlib.ReturnStatus) => {
    console.info('inflateValidate success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateSyncPoint<sup>12+</sup>

inflateSyncPoint(strm: ZStream): Promise\<ReturnStatus>

查找当前解压缩流的同步点，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateSyncPoint({ availableIn: 1 }).then((data: zlib.ReturnStatus) => {
    console.info('inflateSyncPoint success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateSync<sup>12+</sup>

inflateSync(strm: ZStream): Promise\<ReturnStatus>

跳过无效的压缩数据，直到找到一个可能的完整刷新点为止，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800005 | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |
| 17800007 | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit({}, zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.deflate({ nextIn: arrayBufferIn, availableIn: 3, nextOut: arrayBufferOut, availableOut: 100 }, zlib.CompressFlushMode.FULL_FLUSH).then((data: zlib.ReturnStatus) => {
    console.info('deflate success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.deflate({ availableIn: 11 }, zlib.CompressFlushMode.FINISH).then((data: zlib.ReturnStatus) => {
    console.info('deflate success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.deflateEnd({}).then((data: zlib.ReturnStatus) => {
    console.info('deflateEnd success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateInit({ nextIn: arrayBufferOut, availableIn: 2 }).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflate({ nextOut: arrayBufferIn, availableOut: 28 }, zlib.CompressFlushMode.NO_FLUSH).then((data: zlib.ReturnStatus) => {
    console.info('inflate success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateSync({ availableIn: 26 }).then((data: zlib.ReturnStatus) => {
    console.info('inflateSync success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateEnd({ nextOut: arrayBufferOut }).then((data: zlib.ReturnStatus) => {
    console.info('inflateEnd success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateResetKeep<sup>12+</sup>

inflateResetKeep(strm: ZStream): Promise\<ReturnStatus>

重置解压缩流的状态，以保留分配的霍夫曼解码树和预设字典，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateResetKeep({ availableIn: 1 }).then((data: zlib.ReturnStatus) => {
    console.info('inflateResetKeep success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateSetDictionary<sup>12+</sup>

inflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise\<ReturnStatus>

从给定的未压缩字节序列初始化解压缩字典，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型        | 必填 | 说明                            |
| ---------- | ----------- | ---- | ------------------------------- |
| strm       | ZStream     | 是   | 参考[ZStream定义](#zstream12)。 |
| dictionary | ArrayBuffer | 是   | 字典数据。                      |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800005 | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |

**示例：**

ArkTS-Dyn:
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
  let dictionary = 'hello'
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
ArkTS-Sta:
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
  let dictionary = 'hello'
  let dictionarybuf = new ArrayBuffer(dictionary.length);
  let dictionarybufdata = new Uint8Array(dictionarybuf);
  for (let i = 0, j = dictionary.length; i < j; i++) {
    dictionarybufdata[i] = str.charCodeAt(i);
  }
  await zip.deflateInit({}, zlib.CompressLevel.COMPRESS_LEVEL_BEST_COMPRESSION).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.deflateSetDictionary({}, dictionarybuf).then((data: zlib.ReturnStatus) => {
    console.info('deflateSetDictionary success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.deflate({ nextIn: arrayBufferIn, availableIn: 14, nextOut: arrayBufferOut, availableOut: 100 }, zlib.CompressFlushMode.FINISH).then((data: zlib.ReturnStatus) => {
    console.info('deflate success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.deflateEnd({}).then((data: zlib.ReturnStatus) => {
    console.info('deflateEnd success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateInit({ nextIn: arrayBufferOut, availableIn: 100 }).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflate({ nextOut: arrayBufferIn, availableOut: 28 }, zlib.CompressFlushMode.NO_FLUSH).then((data: zlib.ReturnStatus) => {
    console.info('inflate success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateSetDictionary({}, dictionarybuf).then((data: zlib.ReturnStatus) => {
    console.info('inflateSetDictionary success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateEnd({ nextOut: arrayBufferOut }).then((data: zlib.ReturnStatus) => {
    console.info('inflateEnd success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateReset2<sup>12+</sup>

ArkTS-Dyn: inflateReset2(strm: ZStream, windowBits: number): Promise\<ReturnStatus><br>
ArkTS-Sta: inflateReset2(strm: ZStream, windowBits: int): Promise\<ReturnStatus>

从给定的未压缩字节序列初始化解压缩字典，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型    | 必填 | 说明                            |
| ---------- | ------- | ---- | ------------------------------- |
| strm       | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |
| windowBits | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 控制内存窗口的大小，并指定数据的格式（zlib、gzip、raw deflate）。取值如下：<br />zlib格式：[1, 15]。<br />gzip格式：大于15。<br />raw deflate格式：[-15, -1]。   |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateReset2({ availableOut: 8 }, 15).then((data: zlib.ReturnStatus) => {
    console.info('inflateReset2 success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateReset<sup>12+</sup>

inflateReset(strm: ZStream): Promise\<ReturnStatus>

这个函数相当于先调用inflateEnd再调用inflateInit，但是并不会释放和重新分配内部解压缩状态，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateReset({ availableIn: 1, availableOut: 8 }).then((data: zlib.ReturnStatus) => {
    console.info('inflateReset success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflatePrime<sup>12+</sup>

ArkTS-Dyn: inflatePrime(strm: ZStream, bits: number, value: number): Promise\<ReturnStatus><br>
ArkTS-Sta: inflatePrime(strm: ZStream, bits: int, value: int): Promise\<ReturnStatus>

从给定的未压缩字节序列初始化解压缩字典，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |
| bits   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 提供的位。                      |
| value  | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 提供的值。                      |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflatePrime({ nextOut: arrayBufferOut }, 5, 2).then((data: zlib.ReturnStatus) => {
    console.info('inflatePrime success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateMark<sup>12+</sup>

ArkTS-Dyn: inflateMark(strm: ZStream): Promise\<number><br>
ArkTS-Sta: inflateMark(strm: ZStream): Promise\<int>

用于标记输入数据中的位置以供随机访问，使用Promise异步返回。成功时返回位置信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                  | 说明                        |
| --------------------- | --------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象。返回位置信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateMark({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }).then((data: int) => {
    console.info('inflateMark success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateInit2<sup>12+</sup>

ArkTS-Dyn: inflateInit2(strm: ZStream, windowBits: number): Promise\<ReturnStatus><br>
ArkTS-Sta: inflateInit2(strm: ZStream, windowBits: int): Promise\<ReturnStatus>

初始化内部流状态以进行解压缩，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型    | 必填 | 说明                            |
| ---------- | ------- | ---- | ------------------------------- |
| strm       | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |
| windowBits | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 控制内存窗口的大小，并指定数据的格式（zlib、gzip、raw deflate）。取值如下：<br />zlib格式：[1, 15]。<br />gzip格式：大于15。<br />raw deflate格式：[-15, -1]。   |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
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
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
}

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

zip.inflateInit2({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }, 28
).then((data: zlib.ReturnStatus) => {
  console.info('inflateInit2 success');
}).catch((errData: Error) => {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
})
```

### inflateInit<sup>12+</sup>

inflateInit(strm: ZStream): Promise\<ReturnStatus>

初始化内部流状态以进行解压缩，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |

**示例：**

ArkTS-Dyn:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
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
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

let str = 'hello world!';
let arrayBufferIn = new ArrayBuffer(str.length);
let byteArray = new Uint8Array(arrayBufferIn);

for (let i = 0, j = str.length; i < j; i++) {
  byteArray[i] = str.charCodeAt(i)
}

let arrayBufferOut = new ArrayBuffer(100);
let zip = zlib.createZipSync();

zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
).then((data: zlib.ReturnStatus) => {
  console.info('inflateInit success');
}).catch((errData: Error) => {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
})
```

### inflateGetHeader<sup>12+</sup>

inflateGetHeader(strm: ZStream, header: GzHeader): Promise\<ReturnStatus>

用于在解压缩数据前设置gzip文件头部信息，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                    | 必填 | 说明                             |
| ------ | ----------------------- | ---- | -------------------------------- |
| strm   | ZStream                 | 是   | 参考[ZStream定义](#zstream12)。  |
| header | [GzHeader](#gzheader12) | 是   | 从压缩数据流中提取的gzip头信息。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit2 success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateGetHeader({ availableIn: 1, availableOut: 1 }, { isText: true, os: 1, time: 1, xflags: 1, extra: arrayBufferIn, extraLen: 12, name: arrayBufferIn, comment: arrayBufferOut, hcrc: true, done: true }).then((data: zlib.ReturnStatus) => {
    console.info('inflateGetHeader success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateGetDictionary<sup>12+</sup>

inflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise\<DictionaryOutputInfo>

获取当前解压缩流中使用的解压缩字典内容及其长度，使用Promise异步返回。成功时返回结果状态和字典的长度。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型        | 必填 | 说明                            |
| ---------- | ----------- | ---- | ------------------------------- |
| strm       | ZStream     | 是   | 参考[ZStream定义](#zstream12)。 |
| dictionary | ArrayBuffer | 是   | 接收解压缩字典的实际内容。      |

**返回值：**

| 类型                                                         | 说明                                    |
| ------------------------------------------------------------ | --------------------------------------- |
| Promise\<[DictionaryOutputInfo](#dictionaryoutputinfo12)> | Promise对象。返回结果状态和字典的长度。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit2 success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateGetDictionary({ nextOut: arrayBufferOut }, arrayBufferOut).then((data: zlib.DictionaryOutputInfo) => {
    console.info('inflateGetDictionary success:')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateEnd<sup>12+</sup>

inflateEnd(strm: ZStream): Promise\<ReturnStatus>

解压流的所有动态分配的数据结构都被释放，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflate({ nextOut: arrayBufferOut, availableOut: 1 }, zlib.CompressFlushMode.NO_FLUSH).then((data: zlib.ReturnStatus) => {
    console.info('inflate success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateEnd({ nextOut: arrayBufferOut }).then((data: zlib.ReturnStatus) => {
    console.info('inflateEnd success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateCopy<sup>12+</sup>

inflateCopy(source: Zip): Promise\<ReturnStatus>

复制解压流，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明                    |
| ------ | ---- | ---- | ----------------------- |
| source | Zip  | 是   | 参考[Zip定义](#zip12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
  await zip.inflateCopy(zip).then((data) => {
    console.info('inflateCopy success')
  }).catch((errData: BusinessError) => {
    console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
  })
}
```
ArkTS-Sta:
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
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateCopy(zip).then((data: zlib.ReturnStatus) => {
    console.info('inflateCopy success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateCodesUsed<sup>12+</sup>

ArkTS-Dyn: inflateCodesUsed(strm: ZStream): Promise\<number><br>
ArkTS-Sta: inflateCodesUsed(strm: ZStream): Promise\<long>

当前解压缩流中使用的霍夫曼编码树的数量，使用Promise异步返回。成功时返回已使用的霍夫曼编码树的数量。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                  | 说明                                          |
| --------------------- | --------------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象。返回已使用的霍夫曼编码树的数量。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateCodesUsed({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 8 }).then((data: long) => {
    console.info('inflateCodesUsed success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### inflateBackInit<sup>12+</sup>

ArkTS-Dyn: inflateBackInit(strm: ZStream, windowBits: number, window: ArrayBuffer): Promise\<ReturnStatus><br>
ArkTS-Sta: inflateBackInit(strm: ZStream, windowBits: long, window: ArrayBuffer): Promise\<ReturnStatus>

使用inflateBack()函数前初始化内部流状态以进行解压缩，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型        | 必填 | 说明                                          |
| ---------- | ----------- | ---- | --------------------------------------------- |
| strm       | ZStream     | 是   | 参考[ZStream定义](#zstream12)。               |
| windowBits | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 控制内存窗口的大小，并指定数据的格式（zlib、gzip、raw deflate）。取值如下：<br />zlib格式：[1, 15]。<br />gzip格式：大于15。<br />raw deflate格式：[-15, -1]。 |
| window     | ArrayBuffer | 是   | 预设的窗口缓冲区。                            |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

参考[inflateBack](#inflateback12)中的示例代码。

### inflateBackEnd<sup>12+</sup>

inflateBackEnd(strm: ZStream): Promise\<ReturnStatus>

inflateBackInit()函数分配的所有内存都被释放，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

参考[inflateBack](#inflateback12)中的示例代码。

### inflateBack<sup>12+</sup>

ArkTS-Dyn: inflateBack(strm: ZStream, backIn: InflateBackInputCallback, inDesc: object, backOut: InflateBackOutputCallback, outDesc: object): Promise\<ReturnStatus><br>
ArkTS-Sta: inflateBack(strm: ZStream, backIn: InflateBackInputCallback, inDesc: RecordData, backOut: InflateBackOutputCallback, outDesc: RecordData): Promise\<ReturnStatus>

实现原始解压缩，采用回调接口来处理输入和输出，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                      | 必填 | 说明                                                         |
| ------- | ------------------------- | ---- | ------------------------------------------------------------ |
| strm    | ZStream                   | 是   | 参考[ZStream定义](#zstream12)。                              |
| backIn  | InflateBackInputCallback  | 是   | 一种函数，用于从末尾解压缩数据，以从输入源读取原始压缩数据。 |
| inDesc  | ArkTS-Dyn: object<br>ArkTS-Sta: RecordData | 是   | 通用对象。                                                   |
| backOut | InflateBackOutputCallback | 是   | 将解压缩的数据写入目标输出。                                 |
| outDesc | ArkTS-Dyn: object<br>ArkTS-Sta: RecordData | 是   | 通用对象。                                                   |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified. <br />2. Incorrect parameter types. <br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
        if (last != 31 || (NEXT2() != 139 && last >= 157 && last <= 157)) {
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
ArkTS-Sta:
```ts
import { zlib, BusinessError, RecordData } from '@kit.BasicServicesKit';

async function demo() {
  let readIn: (inDesc: RecordData) => ArrayBuffer = (inDesc: RecordData): ArrayBuffer => {
    console.info("inDesc = ", JSON.stringify(inDesc));
    let buffer = new ArrayBuffer(26)
    let array = new Uint8Array(buffer);
    array.set([31, 139, 8, 0, 0, 0, 0, 0, 0, 10, 243, 72, 205, 201, 201, 231, 2, 0, 22, 53, 150, 49, 6, 0, 0, 0]);
    return buffer;
  }

  let writeOut: (outDesc: RecordData, buffer: ArrayBuffer, length: int) => int = (outDesc: RecordData, buffer: ArrayBuffer, length: int): int => {
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
  let NEXT2: () => int = (): int => {
    let o6: object = new Object()
    if (!have) {
      arrayBuffer = readIn(o6)
      next = new Uint8Array(arrayBuffer);
      console.info('readIn next = ', next.length)
      have = next.length;
    }
    if (have) {
      have--;
      last = next[index] as int;
      index++;
    }
    else {
      last = -1;
    }
    return last;
  }

  let inflateBackTest: () => Promise<void> = (async () => {
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
      try {
        await sr.inflateBackInit({}, 15, buffer).then((result: zlib.ReturnStatus) => {
          console.info('inflateBackInit Call result res', result)
        }).catch((errData: Error) => {
          console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
        })
      } catch (errData) {
        console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
      }
      let ret = 0;
      for (; ;) {
        if (NEXT2() == -1) {
          ret = 0;
          console.info('inflateBackTest Call result NEXT2() == -1')
          break;
        }
        console.info('have =  last = ', have, last)
        if (last != 31 || (NEXT2() != 139 && last >= 157 && last <= 157)) {
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
          { },
          writeOut,
          { }).then((result: zlib.ReturnStatus) => {
            ret = result;
            console.info('inflateBack Call result res', result)
          }).catch((errData: Error) => {
            console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
          })
        if (ret == 1) {
          console.info('inflateBackTest Call result success')
          break;
        }
      }
      await sr.inflateBackEnd({}).then((result: zlib.ReturnStatus) => {
        console.info('inflateBackEnd Call result res', result)
      }).catch((errData: Error) => {
        console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
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

ArkTS-Dyn: type InflateBackInputCallback = (inDesc: object) => ArrayBuffer<br>
ArkTS-Sta: type InflateBackInputCallback = (inDesc: RecordData) => ArrayBuffer

用于输入数据的回调函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明               |
| ------ | ------ | ---- | ------------------ |
| inDesc | ArkTS-Dyn: object<br>ArkTS-Sta: RecordData | 是   | 用户定义数据对象。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| ArrayBuffer | 从输入数据源成功读取的内容缓冲区。 |

### InflateBackOutputCallback<sup>12+</sup>

ArkTS-Dyn: type InflateBackOutputCallback = (outDesc: object, buf: ArrayBuffer, length: number) => number<br>
ArkTS-Sta: type InflateBackOutputCallback = (outDesc: RecordData, buf: ArrayBuffer, length: int) => int

用于输出数据的回调函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型        | 必填 | 说明                   |
| ------- | ----------- | ---- | ---------------------- |
| outDesc | ArkTS-Dyn: object<br>ArkTS-Sta: RecordData | 是   | 用户定义数据对象。     |
| buf     | ArrayBuffer | 是   | 用于存储要写入的数据。 |
| length  | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 写入输出缓冲区的长度。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | 输出缓冲区的字节数。 |

### inflate<sup>12+</sup>

inflate(strm: ZStream, flush: CompressFlushMode): Promise\<ReturnStatus>

解压数据，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型              | 必填 | 说明                                                |
| ------ | ----------------- | ---- | --------------------------------------------------- |
| strm   | ZStream           | 是   | 参考[ZStream定义](#zstream12)。                     |
| flush  | CompressFlushMode | 是   | 参考[CompressFlushMode定义](#compressflushmode12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800005 | The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.deflate({ availableOut: 8 }, zlib.CompressFlushMode.FINISH).then((data: zlib.ReturnStatus) => {
    console.info('deflate success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.deflateEnd({ nextOut: arrayBufferOut }).then((data: zlib.ReturnStatus) => {
    console.info('deflateEnd success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateInit({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }
  ).then((data: zlib.ReturnStatus) => {
    console.info('inflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflate({ nextOut: arrayBufferOut, availableOut: 1 }, zlib.CompressFlushMode.NO_FLUSH).then((data: zlib.ReturnStatus) => {
    console.info('inflate success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.inflateEnd({ nextOut: arrayBufferOut }).then((data: zlib.ReturnStatus) => {
    console.info('inflateEnd success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### deflateInit<sup>12+</sup>

deflateInit(strm: ZStream, level: CompressLevel): Promise\<ReturnStatus>

初始化内部流状态以进行压缩，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型          | 必填 | 说明                                          |
| ------ | ------------- | ---- | --------------------------------------------- |
| strm   | ZStream       | 是   | 参考[ZStream定义](#zstream12)。               |
| level  | CompressLevel | 是   | 参考[CompressLevel枚举定义](#compresslevel)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### deflateInit2<sup>12+</sup>

ArkTS-Dyn: deflateInit2(strm: ZStream, level: CompressLevel, method: CompressMethod, windowBits: number, memLevel: MemLevel, strategy: CompressStrategy): Promise\<ReturnStatus><br>
ArkTS-Sta: deflateInit2(strm: ZStream, level: CompressLevel, method: CompressMethod, windowBits: int, memLevel: MemLevel, strategy: CompressStrategy): Promise\<ReturnStatus>

初始化内部流状态以进行压缩，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型             | 必填 | 说明                                                |
| ---------- | ---------------- | ---- | --------------------------------------------------- |
| strm       | ZStream          | 是   | 参考[ZStream定义](#zstream12)。                     |
| level      | CompressLevel    | 是   | 参考[CompressLevel枚举定义](#compresslevel)。       |
| method     | CompressMethod   | 是   | 参考[CompressMethod枚举定义](#compressmethod12)。   |
| windowBits | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 控制内存窗口的大小，并指定数据的格式（zlib、gzip、raw deflate）。取值如下：<br />zlib格式：[1, 15]。<br />gzip格式：大于15。<br />raw deflate格式：[-15, -1]。                       |
| memLevel   | MemLevel         | 是   | 参考[MemLevel枚举定义](#memlevel)。                 |
| strategy   | CompressStrategy | 是   | 参考[CompressStrategy枚举定义](#compressstrategy)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
    zlib.MemLevel.MEM_LEVEL_DEFAULT, zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY).then((data: zlib.ReturnStatus) => {
      console.info('deflateInit2 success');
    }).catch((errData: Error) => {
      console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
    })
}
```

### deflate<sup>12+</sup>

deflate(strm: ZStream, flush: CompressFlushMode): Promise\<ReturnStatus>

压缩数据，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型              | 必填 | 说明                                                |
| ------ | ----------------- | ---- | --------------------------------------------------- |
| strm   | ZStream           | 是   | 参考[ZStream定义](#zstream12)。                     |
| flush  | CompressFlushMode | 是   | 参考[CompressFlushMode定义](#compressflushmode12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800007 | The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.deflate({ availableOut: 8 }, zlib.CompressFlushMode.FINISH).then((data: zlib.ReturnStatus) => {
    console.info('deflate success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### deflateEnd<sup>12+</sup>

deflateEnd(strm: ZStream): Promise\<ReturnStatus>

压缩流的所有动态分配的数据结构都被释放，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.deflate({ availableOut: 8 }, zlib.CompressFlushMode.FINISH).then((data: zlib.ReturnStatus) => {
    console.info('deflate success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
  await zip.deflateEnd({ nextOut: arrayBufferOut }).then((data: zlib.ReturnStatus) => {
    console.info('deflateEnd success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  })
}
```

### deflateBound<sup>12+</sup>

ArkTS-Dyn: deflateBound(strm: ZStream, sourceLength: number): Promise\<number><br>
ArkTS-Sta: deflateBound(strm: ZStream, sourceLength: long): Promise\<int>

计算压缩大小的上限，使用Promise异步返回。成功时返回压缩大小的上限。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型    | 必填 | 说明                            |
| --------- | ------- | ---- | ------------------------------- |
| strm      | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |
| sourceLength | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 源数据长度。                    |

**返回值：**

| 类型                  | 说明                              |
| --------------------- | --------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象。返回压缩大小的上限。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
  try {
    await zip.deflateBound({ nextOut: arrayBufferOut }, 12).then((data: int) => {
      console.info('deflateBound success')
    }).catch((errData: Error) => {
      console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
    })
  } catch (errData) {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  }
}
```

### deflateSetHeader<sup>12+</sup>

deflateSetHeader(strm: ZStream, head: GzHeader): Promise\<ReturnStatus>

当deflateInit2()请求gzip流时，提供gzip标头信息，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                    | 必填 | 说明                             |
| ------ | ----------------------- | ---- | -------------------------------- |
| strm   | ZStream                 | 是   | 参考[ZStream定义](#zstream12)。  |
| head   | [GzHeader](#gzheader12) | 是   | 从压缩数据流中提取的gzip头信息。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
    zlib.MemLevel.MEM_LEVEL_DEFAULT, zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY).then((data: zlib.ReturnStatus) => {
      console.info('deflateInit2 success');
    }).catch((errData: Error) => {
      console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
    })
  await zip.deflateSetHeader({ nextIn: arrayBufferIn, availableIn: 1, nextOut: arrayBufferOut, availableOut: 1 }, { isText: true, os: 1, time: 1, xflags: 1, extra: arrayBufferIn, extraLen: 12, name: arrayBufferIn, comment: arrayBufferOut, hcrc: true, done: true }).then((data: zlib.ReturnStatus) => {
    console.info('deflateSetHeader success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
}
```

### deflateCopy<sup>12+</sup>

deflateCopy(source: Zip): Promise\<ReturnStatus>

复制压缩流，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明                    |
| ------ | ---- | ---- | ----------------------- |
| source | Zip  | 是   | 参考[Zip定义](#zip12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
  await zip.deflateCopy(zip).then((data: zlib.ReturnStatus) => {
    console.info('deflateCopy success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
}
```

### deflateSetDictionary<sup>12+</sup>

deflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise\<ReturnStatus>

从给定的字节序列初始化压缩字典，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型        | 必填 | 说明                            |
| ---------- | ----------- | ---- | ------------------------------- |
| strm       | ZStream     | 是   | 参考[ZStream定义](#zstream12)。 |
| dictionary | ArrayBuffer | 是   | 字典数据。                      |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
  await zip.deflateSetDictionary({ nextOut: arrayBufferOut }, arrayBufferOut).then((data: zlib.ReturnStatus) => {
    console.info('deflateSetDictionary success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
}
```

### deflateGetDictionary<sup>12+</sup>

deflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise\<DictionaryOutputInfo>

获取当前解压缩流中使用的解压缩字典内容及其长度，使用Promise异步返回。成功时返回结果状态和字典的长度。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型        | 必填 | 说明                            |
| ---------- | ----------- | ---- | ------------------------------- |
| strm       | ZStream     | 是   | 参考[ZStream定义](#zstream12)。 |
| dictionary | ArrayBuffer | 是   | 接收解压缩字典的实际内容。      |

**返回值：**

| 类型                                                         | 说明                                    |
| ------------------------------------------------------------ | --------------------------------------- |
| Promise\<[DictionaryOutputInfo](#dictionaryoutputinfo12)> | Promise对象。返回结果状态和字典的长度。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
  await zip.deflateSetDictionary({ nextOut: arrayBufferOut }, arrayBufferOut).then((data: zlib.ReturnStatus) => {
    console.info('deflateSetDictionary success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
  await zip.deflateGetDictionary({ nextOut: arrayBufferOut }, arrayBufferOut).then((data: zlib.DictionaryOutputInfo) => {
    console.info('deflateGetDictionary success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
}
```

### deflateTune<sup>12+</sup>

ArkTS-Dyn: deflateTune(strm: ZStream, goodLength: number, maxLazy: number, niceLength: number, maxChain: number): Promise\<ReturnStatus><br>
ArkTS-Sta: deflateTune(strm: ZStream, goodLength: int, maxLazy: int, niceLength: int, maxChain: int): Promise\<ReturnStatus>

微调deflate的内部压缩参数，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型    | 必填 | 说明                            |
| ---------- | ------- | ---- | ------------------------------- |
| strm       | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |
| goodLength | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 匹配的长度阈值。                |
| maxLazy    | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 压缩算法在构建哈夫曼树时的延迟匹配策略，取值范围为0到4的整数。1到4，值越大，算法越‘懒’，匹配过程越慢，但可能生成更优的压缩结果。0：禁用懒惰匹配，算法会尽快构建哈夫曼树，压缩速度快，但压缩率低。  |
| niceLength | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 适合的延迟长度阈值。              |
| maxChain   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 最大链条长度。                    |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
  await zip.deflateTune({ nextOut: arrayBufferOut }, 2, 2, 2, 2).then((data: zlib.ReturnStatus) => {
    console.info('deflateTune success:')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
}
```

### deflateReset<sup>12+</sup>

deflateReset(strm: ZStream): Promise\<ReturnStatus>

这个函数相当于先调用deflateEnd再调用deflateInit，但是并不会释放和重新分配内部解压缩状态，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
  await zip.deflateReset({ nextOut: arrayBufferOut }).then((data: zlib.ReturnStatus) => {
    console.info('deflateReset success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
}
```

### deflateResetKeep<sup>12+</sup>

deflateResetKeep(strm: ZStream): Promise\<ReturnStatus>

重置初始化的deflate压缩流，但保留其设置的压缩参数和字典，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
  await zip.deflateResetKeep({ nextOut: arrayBufferOut }).then((data: zlib.ReturnStatus) => {
    console.info('deflateResetKeep success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
}
```

### deflatePending<sup>12+</sup>

deflatePending(strm: ZStream): Promise\<DeflatePendingOutputInfo>

返回已生成但尚未在可用输出中提供的输出的字节数和位数，使用Promise异步返回。成功时返回结果状态、输出位数和输出字节数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |

**返回值：**

| 类型                                                         | 说明                                              |
| ------------------------------------------------------------ | ------------------------------------------------- |
| Promise\<[DeflatePendingOutputInfo](#deflatependingoutputinfo12)> | Promise对象。返回结果状态、输出位数和输出字节数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
  await zip.deflatePending({ nextOut: arrayBufferOut }).then((data: zlib.DeflatePendingOutputInfo) => {
    console.info('deflatePending success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
}
```

### deflateParams<sup>12+</sup>

deflateParams(strm: ZStream, level: CompressLevel, strategy: CompressStrategy): Promise\<ReturnStatus>

动态更新压缩级别和压缩策略，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型             | 必填 | 说明                                                |
| -------- | ---------------- | ---- | --------------------------------------------------- |
| strm     | ZStream          | 是   | 参考[ZStream定义](#zstream12)。                     |
| level    | CompressLevel    | 是   | 参考[CompressLevel枚举定义](#compresslevel)。       |
| strategy | CompressStrategy | 是   | 参考[CompressStrategy枚举定义](#compressstrategy)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
  await zip.deflateParams(zStream, zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION, zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY).then((data: zlib.ReturnStatus) => {
    console.info('deflateParams success')
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
}
```

### deflatePrime<sup>12+</sup>

ArkTS-Dyn: deflatePrime(strm: ZStream, bits: number, value: number): Promise\<ReturnStatus><br>
ArkTS-Sta: deflatePrime(strm: ZStream, bits: int, value: int): Promise\<ReturnStatus>

在压缩流中插入位和值，使用Promise异步返回。成功时返回结果状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                            |
| ------ | ------- | ---- | ------------------------------- |
| strm   | ZStream | 是   | 参考[ZStream定义](#zstream12)。 |
| bits   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 要插入的位数，取值范围在0~16。  |
| value  | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 与位数相对应的位值。            |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象。返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
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
  await zip.deflateInit(zStream, zlib.CompressLevel.COMPRESS_LEVEL_BEST_SPEED).then((data: zlib.ReturnStatus) => {
    console.info('deflateInit success');
  }).catch((errData: Error) => {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
  })
  try {
    await zip.deflatePrime({ nextOut: arrayBufferOut }, 5, 2).then((data: zlib.ReturnStatus) => {
      console.info('deflatePrime success')
    }).catch((errData: Error) => {
      console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
    })
  } catch (errData) {
    console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
  }
}
```

## Options

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

| 名称     | 类型             | 只读 | 可选 | 说明                                                       |
| -------- | ---------------- | ---- | ---------------------------------------------------------- | ---- |
| level    | [CompressLevel](#compresslevel)         | 否   | 是  | 参考[CompressLevel枚举定义](#compresslevel)。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 7<br>**ArkTS-Sta起始版本：** 23 |
| memLevel | [MemLevel](#memlevel)                   | 否   | 是  | 参考[MemLevel枚举定义](#memlevel)。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 7<br>**ArkTS-Sta起始版本：** 23 |
| strategy | [CompressStrategy](#compressstrategy)   | 否   | 是  | 参考[CompressStrategy枚举定义](#compressstrategy)。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 7<br>**ArkTS-Sta起始版本：** 23 |
| parallel | [ParallelStrategy](#parallelstrategy18) | 否   | 是  | 参考[ParallelStrategy枚举定义](#parallelstrategy18)。<br>**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 18<br>**ArkTS-Sta起始版本：** 23 |

## CompressLevel

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

| 名称                               | 值   | 说明              |
| ---------------------------------- | ---- | ----------------- |
| COMPRESS_LEVEL_NO_COMPRESSION      | 0    | 压缩率为0压缩等级。 |
| COMPRESS_LEVEL_BEST_SPEED          | 1    | 最佳速度压缩等级。  |
| COMPRESS_LEVEL_BEST_COMPRESSION    | 9    | 最佳压缩等级。      |
| COMPRESS_LEVEL_DEFAULT_COMPRESSION | -1   | 默认压缩等级。      |

## MemLevel

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

| 名称              | 值   | 说明                             |
| ----------------- | ---- | -------------------------------- |
| MEM_LEVEL_MIN     | 1    | zlib接口在压缩过程中最小使用内存。 |
| MEM_LEVEL_MAX     | 9    | zlib接口在压缩过程中最大使用内存。 |
| MEM_LEVEL_DEFAULT | 8    | zlib接口在压缩过程中默认使用内存。 |

## CompressStrategy

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

| 名称                               | 值   | 说明                     |
| ---------------------------------- | ---- | ------------------------ |
| COMPRESS_STRATEGY_DEFAULT_STRATEGY | 0    | 常规数据策略。             |
| COMPRESS_STRATEGY_FILTERED         | 1    | 过滤器产生的数据压缩策略。 |
| COMPRESS_STRATEGY_HUFFMAN_ONLY     | 2    | 霍夫曼编码格式压缩策略。   |
| COMPRESS_STRATEGY_RLE              | 3    | 游标编码压缩策略。         |
| COMPRESS_STRATEGY_FIXED            | 4    | 固定的压缩策略。           |

## ParallelStrategy<sup>18+</sup>

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

| 名称                                     | 值   | 说明                      |
| ---------------------------------------- | ---- | ------------------------ |
| PARALLEL_STRATEGY_SEQUENTIAL             | 0    | 默认值，串行压缩/解压策略。|
| PARALLEL_STRATEGY_PARALLEL_DECOMPRESSION | 1    | 并行解压策略。            |

## ErrorCode<sup>(deprecated)<sup>

> **说明：**
> 
> 本模块首批接口从API version 7 开始支持。
> 
> 从API Version 9开始，该模块不再维护。

**系统能力：** SystemCapability.BundleManager.Zlib

| 名称             | 值   | 说明         |
| ---------------- | ---- | ------------ |
| ERROR_CODE_OK    | 0    | 函数调用成功。 |
| ERROR_CODE_ERRNO | -1   | 函数调用失败。 |

## CompressFlushMode<sup>12+</sup>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称          | 值   | 说明                                         |
| ------------- | ---- | -------------------------------------------- |
| NO_FLUSH      | 0    | 默认值，表示正常操作。                       |
| PARTIAL_FLUSH | 1    | 在流中生成部分刷新点。                       |
| SYNC_FLUSH    | 2    | 在保持压缩流状态的同时强制输出所有压缩数据。 |
| FULL_FLUSH    | 3    | 重置压缩状态。                               |
| FINISH        | 4    | 压缩或解压缩过程结束。                       |
| BLOCK         | 5    | 允许更精确的控制。                           |
| TREES         | 6    | 实施过程中有特殊目的。                       |

## CompressMethod<sup>12+</sup>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称     | 值   | 说明       |
| -------- | ---- | ---------- |
| DEFLATED | 8    | 压缩方法。 |

## ReturnStatus<sup>12+</sup>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

| 名称       | 值   | 说明                                           |
| ---------- | ---- | ---------------------------------------------- |
| OK         | 0    | 函数调用成功。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| STREAM_END | 1    | 函数调用成功，表示已处理了整个数据。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| NEED_DICT  | 2    | 函数调用成功，表示需要预设字典才能继续解压缩。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| ERRNO        | -1 | 函数调用失败，表示文件操作错误。<br>**ArkTS-Dyn起始版本：** 21<br>**ArkTS-Sta起始版本：** 23 |
| STREAM_ERROR | -2 | 函数调用失败，表示压缩或解压缩流错误。<br>**ArkTS-Dyn起始版本：** 21<br>**ArkTS-Sta起始版本：** 23 |
| DATA_ERROR   | -3 | 函数调用失败，表示输入数据不正确。<br>**ArkTS-Dyn起始版本：** 21<br>**ArkTS-Sta起始版本：** 23 |
| MEM_ERROR    | -4 | 函数调用失败，表示内存分配失败。<br>**ArkTS-Dyn起始版本：** 21<br>**ArkTS-Sta起始版本：** 23 |
| BUF_ERROR    | -5 | 函数调用失败，表示输入缓冲区不正确。<br>**ArkTS-Dyn起始版本：** 21<br>**ArkTS-Sta起始版本：** 23 |

## ZStream<sup>12+</sup>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称         | 类型        | 只读 | 可选 | 说明                                                         |
| ------------ | ----------- | ---- | ---- | ------------------------------------------------------------ |
| nextIn       | ArrayBuffer | 否   | 是   | 需要压缩的输入字节。                                           |
| availableIn  | ArkTS-Dyn: number<br>ArkTS-Sta: int  | 否   | 是   | nextIn可用的字节数。                                           |
| totalIn      | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否   | 是   | 到目前为止读取的输入字节总数。                                 |
| nextOut      | ArrayBuffer | 否   | 是   | 压缩后的输出字节。                                             |
| availableOut | ArkTS-Dyn: number<br>ArkTS-Sta: int  | 否   | 是   | nextOut的剩余可用字节数。                                      |
| totalOut     | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否   | 是   | 到目前为止输出字节总数。                                       |
| dataType     | ArkTS-Dyn: number<br>ArkTS-Sta: int  | 否   | 是   | 关于数据类型的最佳猜测：deflate的二进制或文本，或inflate的解码状态。 |
| adler        | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否   | 是   | 未压缩数据的Adler-32或CRC-32值。                               |

## ZipOutputInfo<sup>12+</sup>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称    | 类型         | 只读 | 可选 | 说明                                          |
| ------- | ------------ | ---- | ---- | --------------------------------------------- |
| status  | ReturnStatus | 否   | 否   | 参考[ReturnStatus枚举定义](#returnstatus12)。 |
| destLen | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否   | 否   | 目标缓冲区的总长度。                          |

## DictionaryOutputInfo<sup>12+</sup>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称             | 类型         | 只读 | 可选 | 说明                                          |
| ---------------- | ------------ | ---- | ---- | --------------------------------------------- |
| status           | ReturnStatus | 否   | 否   | 参考[ReturnStatus枚举定义](#returnstatus12)。 |
| dictionaryLength | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否   | 否   | 字典的长度。                                  |

## DecompressionOutputInfo<sup>12+</sup>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称         | 类型         | 只读 | 可选 | 说明                                          |
| ------------ | ------------ | ---- | ---- | --------------------------------------------- |
| status       | ReturnStatus | 否   | 否   | 参考[ReturnStatus枚举定义](#returnstatus12)。 |
| destLength   | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否   | 否   | 目标缓冲区的长度。                            |
| sourceLength | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否   | 否   | 源缓冲区的长度。                              |

## DeflatePendingOutputInfo<sup>12+</sup>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称    | 类型         | 只读 | 可选 | 说明                                          |
| ------- | ------------ | ---- | ---- | --------------------------------------------- |
| status  | ReturnStatus | 否   | 否   | 参考[ReturnStatus枚举定义](#returnstatus12)。 |
| pending | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否   | 否   | 已生成的输出字节数。                          |
| bits    | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否   | 否   | 已生成的输出位数。                            |

## GzHeader<sup>12+</sup>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称     | 类型        | 只读 | 可选 | 说明                                 |
| -------- | ----------- | ---- | ---- | ------------------------------------ |
| isText   | boolean     | 否   | 是   | 标识压缩数据是否为文本，True表示是文本，False表示非文本。 |
| os       | ArkTS-Dyn: number<br>ArkTS-Sta: int  | 否   | 是   | 操作系统。                           |
| time     | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否   | 是   | 修改时间。                           |
| xflags   | ArkTS-Dyn: number<br>ArkTS-Sta: int  | 否   | 是   | 额外标志。                           |
| extra    | ArrayBuffer | 否   | 是   | 额外字段。                           |
| extraLen | ArkTS-Dyn: number<br>ArkTS-Sta: int  | 否   | 是   | 额外字段的长度。                     |
| name     | ArrayBuffer | 否   | 是   | 文件名。                             |
| comment  | ArrayBuffer | 否   | 是   | 注释。                               |
| hcrc     | boolean     | 否   | 是   | 如果存在crc标头，则为True。          |
| done     | boolean     | 否   | 是   | 读取gzip标头后为True。               |

## zlib.createGZip<sup>12+</sup>

createGZip(): Promise\<GZip>

创建GZip对象，使用Promise异步返回。成功时返回Gzip对象实例。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                           | 说明                            |
| ------------------------------ | ------------------------------- |
| Promise\<[GZip](#gzip12)> | Promise对象。返回GZip对象实例。 |

**示例：**

ArkTS-Dyn:
```ts
import { zlib } from '@kit.BasicServicesKit';

zlib.createGZip().then((data) => {
  console.info('createGZip success');
})
```
ArkTS-Sta:
```ts
import { zlib, BusinessError } from '@kit.BasicServicesKit';

zlib.createGZip().then((data: zlib.GZip) => {
  console.info('createGZip success');
}).catch((errData: Error) => {
  console.error(`errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`)
})
```

## zlib.createGZipSync<sup>12+</sup>

createGZipSync():  GZip

创建GZip对象。成功时返回GZip对象实例。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型            | 说明           |
| --------------- | -------------- |
| [GZip](#gzip12) | GZip对象实例。 |

**示例：**

```ts
import { zlib } from '@kit.BasicServicesKit';

let gzip = zlib.createGZipSync();
```

## GZip<sup>12+</sup>

Gzip相关接口。

### gzdopen<sup>12+</sup>

ArkTS-Dyn: gzdopen(fd: number, mode: string): Promise\<void><br>
ArkTS-Sta: gzdopen(fd: int, mode: string): Promise\<void>

将gzFile与文件描述符fd相关联，打开文件，用于进行读取并解压缩，或者压缩并写入。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| fd     | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 文件描述符。通常情况下，通过系统调用“open”或其他方法获得的。 |
| mode   | string | 是   | 用于指定访问模式。                                           |

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise\<void> | Promise对象，无返回值。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800002 | No such file or access mode error.                           |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzdopenDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzdopen");
  let path = pathDir + "/gzdopen/test.gz";
  let file = fs.openSync(path, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
  let gzip = zlib.createGZipSync();
  await gzip.gzdopen(file.fd, "wb");
  await gzip.gzclose();
}
```

### gzbuffer<sup>12+</sup>

ArkTS-Dyn: gzbuffer(size: number):Promise\<number><br>
ArkTS-Sta: gzbuffer(size: long):Promise\<int>

为当前库函数设置内部缓冲区尺寸。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| size   | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 需要设置的内部缓冲区尺寸。 |

**返回值：**

| 类型                  | 说明                         |
| --------------------- | ---------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象，成功时，返回0。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800009   | Internal structure error. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { fileIo as fs } from '@kit.CoreFileKit';
import { zlib } from '@kit.BasicServicesKit';

async function gzbufferDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzbuffer");
  let path = pathDir + "/gzbuffer/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let result = await gzip.gzbuffer(648);
  await gzip.gzclose();
}
```

### gzopen<sup>12+</sup>

gzopen(path: string, mode: string): Promise\<void>

打开位于指定路径的gzip(.gz)文件，用于进行读取并解压缩，或者压缩并写入。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                 |
| ------ | ------ | ---- | -------------------- |
| path   | string | 是   | 需要打开的文件路径。 |
| mode   | string | 是   | 指定文件打开方法。   |

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise\<void> | Promise对象，无返回值。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800002 | No such file or access mode error.                           |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzopenDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzopen");
  let path = pathDir + "/gzopen/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
}
```

### gzeof<sup>12+</sup>

ArkTS-Dyn: gzeof(): Promise\<number><br>
ArkTS-Sta: gzeof(): Promise\<int>

检查gzip压缩文件的读取位置是否已到达文件的末尾。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明                                                         |
| --------------------- | ------------------------------------------------------------ |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象，如果在读取时设置了文件的文件结束指示符，则返回1。 |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzeofDemo() {
  let pathDir = "/xxx";
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
```

### gzdirect<sup>12+</sup>

ArkTS-Dyn: gzdirect(): Promise\<number><br>
ArkTS-Sta: gzdirect(): Promise\<int>

检查指定的gzip文件句柄文件是否直接访问原始未压缩数据，重新分配缓冲区。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明                                               |
| --------------------- | -------------------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象，如果直接访问原始未压缩数据，则返回1。 |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzdirectDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzdirect");
  let path = pathDir + "/gzdirect/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let directNum = await gzip.gzdirect();
  await gzip.gzclose();
}
```

### gzclose<sup>12+</sup>

gzclose(): Promise\<ReturnStatus>

清除文件的所有挂起输出，如有必要，关闭文件和释放（解）压缩状态。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象，返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                  |
| -------- | ------------------------- |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800006 | Memory allocation failed. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzcloseDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzclose");
  let path = pathDir + "/gzclose/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
}
```

### gzclearerr<sup>12+</sup>

gzclearerr(): Promise\<void>

清除文件的错误和文件结束标志。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise\<void> | Promise对象，无返回值。 |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzclearerrDemo() {
  let pathDir = "/xxx";
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
```

### gzerror<sup>12+</sup>

gzerror(): Promise\<GzErrorOutputInfo>

文件上发生的最后一个错误的错误消息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                     | 说明                                                      |
| -------------------------------------------------------- | --------------------------------------------------------- |
| Promise\<[GzErrorOutputInfo](#gzerroroutputinfo12)> | Promise对象，返回结果状态和出现的最后一个状态的状态消息。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息       |
| -------- | -------------- |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzerrorDemo() {
  let pathDir = "/xxx";
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
```

### gzgetc<sup>12+</sup>

ArkTS-Dyn: gzgetc(): Promise\<number><br>
ArkTS-Sta: gzgetc(): Promise\<int>

从文件中读取并解压缩一个字节。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明                                 |
| --------------------- | ------------------------------------ |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象，返回读取字符的ASCII值。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                  |
| -------- | ------------------------- |
| 17800009 | Internal structure error. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzgetcDemo() {
  let pathDir = "/xxx";
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
```

### gzflush<sup>12+</sup>

gzflush(flush: CompressFlushMode): Promise\<ReturnStatus>

将所有挂起的输出刷新到文件中。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型              | 必填 | 说明                                                         |
| ------ | ----------------- | ---- | ------------------------------------------------------------ |
| flush  | CompressFlushMode | 是   | 控制刷新操作的行为，参考[CompressFlushMode枚举](#compressflushmode12)的定义。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象，返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzflushDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzflush");
  let path = pathDir + "/gzflush/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let flushNum = await gzip.gzflush(zlib.CompressFlushMode.NO_FLUSH);
  await gzip.gzclose();
}
```

### gzfwrite<sup>12+</sup>

ArkTS-Dyn: gzfwrite(buf: ArrayBuffer, size: number, nitems: number): Promise\<number><br>
ArkTS-Sta: gzfwrite(buf: ArrayBuffer, size: long, nitems: long): Promise\<long>

将大小为size，数量为nitems的数据块从buf压缩并写入文件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型        | 必填 | 说明                   |
| ------ | ----------- | ---- | ---------------------- |
| buf    | ArrayBuffer | 是   | 要将数据写入的缓冲区。 |
| size   | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 单个数据块中的字节数。 |
| nitems | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 要写入的数据块数。     |

**返回值：**

| 类型                  | 说明                                                |
| --------------------- | --------------------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象，返回写入大小为size的完整数据块的数目。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**示例：**

ArkTS-Dyn:
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
  let resulit = await gzip.gzfwrite(bufferWithData, 8, 2)
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzfwriteDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzfwrite");
  let path = pathDir + "/gzfwrite/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let bufferWithData = new ArrayBuffer(16);
  let uint8View = new Uint8Array(bufferWithData);
  for (let i = 0; i < uint8View.length; i++) {
    uint8View[i] = i;
  }
  let resulit = await gzip.gzfwrite(bufferWithData, 8, 2)
  await gzip.gzclose();
}
```

### gzfread<sup>12+</sup>

ArkTS-Dyn: gzfread(buf: ArrayBuffer, size: number, nitems: number): Promise\<number><br>
ArkTS-Sta: gzfread(buf: ArrayBuffer, size: long, nitems: long): Promise\<long>

从gzip压缩文件中解压缩并读取数据。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型        | 必填 | 说明                           |
| ------ | ----------- | ---- | ------------------------------ |
| buf    | ArrayBuffer | 是   | 用于存储读取结果的目标缓冲区。 |
| size   | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 单个数据块中的字节数。         |
| nitems | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 要写入的数据块数。             |

**返回值：**

| 类型                  | 说明                                                |
| --------------------- | --------------------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象，返回读取大小为size的完整数据块的数目。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzfreadDemo() {
  let pathDir = "/xxx";
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
```

### gzclosew<sup>12+</sup>

gzclosew(): Promise\<ReturnStatus>

与gzclose()功能相同，仅适用于写入或追加时。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象，返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                  |
| -------- | ------------------------- |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800006 | Memory allocation failed. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzclosewDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzclosew");
  let path = pathDir + "/gzclosew/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclosew();
}
```

### gzcloser<sup>12+</sup>

gzcloser(): Promise\<ReturnStatus>

与gzclose()功能相同，仅适用于读取时。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象，返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息       |
| -------- | -------------- |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzcloserDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzcloser");
  let path = pathDir + "/gzcloser/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  await gzip.gzcloser();
}
```

### gzwrite<sup>12+</sup>

ArkTS-Dyn: gzwrite(buf: ArrayBuffer, len: number): Promise\<number><br>
ArkTS-Sta: gzwrite(buf: ArrayBuffer, len: long): Promise\<long>

将buf中的len长度的未压缩字节进行压缩并将其写入文件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 参数名 | 类型        | 必填 | 说明                         |
| ------ | ----------- | ---- | ---------------------------- |
| buf    | ArrayBuffer | 是   | 对象指向要写入的数据缓冲区。 |
| len    | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 未压缩字节长度。             |

**返回值：**

| 类型                  | 说明                                  |
| --------------------- | ------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象，返回写入的未压缩字节数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzwriteDemo() {
  let pathDir = "/xxx";
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
```

### gzungetc<sup>12+</sup>

ArkTS-Dyn: gzungetc(c: number): Promise\<number><br>
ArkTS-Sta: gzungetc(c: int): Promise\<int>

将c推回到流中，以便在下次读取文件时将作为第一个字符读取。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 参数名 | 类型   | 必填 | 说明                     |
| ------ | ------ | ---- | ------------------------ |
| c      | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 回退到输入流之前的字符。 |

**返回值：**

| 类型                  | 说明                          |
| --------------------- | ----------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象，返回推送的字符。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzungetcDemo() {
  let pathDir = "/xxx";
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
```

### gztell<sup>12+</sup>

ArkTS-Dyn: gztell(): Promise\<number><br>
ArkTS-Sta: gztell(): Promise\<long>

返回文件中下一个gzread或gzwrite的起始位置。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明                                                     |
| --------------------- | -------------------------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象，返回文件种下一个gzread或gzwrite的起始位置。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                  |
| -------- | ------------------------- |
| 17800009 | Internal structure error. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gztellDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gztell");
  let path = pathDir + "/gztell/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gztell();
  await gzip.gzclose();
}
```

### gzsetparams<sup>12+</sup>

gzsetparams(level: CompressLevel, strategy: CompressStrategy): Promise\<ReturnStatus>

动态更新文件的压缩级别和压缩策略。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型             | 必填 | 说明                                                         |
| -------- | ---------------- | ---- | ------------------------------------------------------------ |
| level    | CompressLevel    | 是   | 压缩级别，参考[CompressLevel枚举定义](#compresslevel)。      |
| strategy | CompressStrategy | 是   | 压缩策略，参考[CompressStrategy枚举定义](#compressstrategy)。 |

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象，返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzsetparamsDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzsetparams");
  let path = pathDir + "/gzsetparams/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzsetparams(zlib.CompressLevel.COMPRESS_LEVEL_DEFAULT_COMPRESSION,
    zlib.CompressStrategy.COMPRESS_STRATEGY_DEFAULT_STRATEGY);
  await gzip.gzclose();
}
```

### gzseek<sup>12+</sup>

ArkTS-Dyn: gzseek(offset: number, whence: OffsetReferencePoint): Promise\<number><br>
ArkTS-Sta: gzseek(offset: long, whence: OffsetReferencePoint): Promise\<long>

将起始位置设置为相对于文件中下一个gzread或gzwrite的偏移位置。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                 | 必填 | 说明                                                         |
| ------ | -------------------- | ---- | ------------------------------------------------------------ |
| offset | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 目标偏移位置。                                               |
| whence | OffsetReferencePoint | 是   | 定义偏移的参考点，参考[OffsetReferencePoint枚举定义](#offsetreferencepoint12)。 |

**返回值：**

| 类型                  | 说明                                                         |
| --------------------- | ------------------------------------------------------------ |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象，返回从未压缩流开始以字节为单位测量的结果偏移位置。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzseekDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzseek");
  let path = pathDir + "/gzseek/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzseek(2, zlib.OffsetReferencePoint.SEEK_CUR);
  await gzip.gzclose();
}
```

### gzrewind<sup>12+</sup>

gzrewind(): Promise\<ReturnStatus>

将文件指针重新定位到文件的开头，此功能仅用于读取。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                           | 说明                        |
| ---------------------------------------------- | --------------------------- |
| Promise\<[ReturnStatus](#returnstatus12)> | Promise对象，返回结果状态。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                  |
| -------- | ------------------------- |
| 17800009 | Internal structure error. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzrewindDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzrewind");
  let path = pathDir + "/gzrewind/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  await gzip.gzclose();
  await gzip.gzopen(path, "rb");
  let result = await gzip.gzrewind();
  await gzip.gzclose();
}
```

### gzread<sup>12+</sup>

ArkTS-Dyn: gzread(buf: ArrayBuffer): Promise\<number><br>
ArkTS-Sta: gzread(buf: ArrayBuffer): Promise\<long>

从文件中读取最多len个未压缩字节并将其解压缩到buf中。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型        | 必填 | 说明           |
| ------ | ----------- | ---- | -------------- |
| buf    | ArrayBuffer | 是   | 目标偏移位置。 |

**返回值：**

| 类型                  | 说明                                      |
| --------------------- | ----------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象，返回实际读取的未压缩字节数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzreadDemo() {
  let pathDir = "/xxx";
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
```

### gzputs<sup>12+</sup>

ArkTS-Dyn: gzputs(str: string): Promise\<number><br>
ArkTS-Sta: gzputs(str: string): Promise\<int>

压缩给定的以null结尾的字符串并将其写入文件，不包括终止的null字符。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                   |
| ------ | ------ | ---- | ---------------------- |
| str    | string | 是   | 格式化描述符和纯文本。 |

**返回值：**

| 类型                  | 说明                            |
| --------------------- | ------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象，返回写入的字符数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzputsDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzputs");
  let path = pathDir + "/gzputs/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzputs("hello");
  await gzip.gzclose();
}
```

### gzputc<sup>12+</sup>

ArkTS-Dyn: gzputc(ch: number): Promise\<number><br>
ArkTS-Sta: gzputc(ch: int): Promise\<int>

将转换为无符号字符的c压缩并写入文件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明            |
| ------ | ------ | ---- | --------------- |
| char   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 写入字符ASCII。 |

**返回值：**

| 类型                  | 说明                          |
| --------------------- | ----------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象，返回已写入的值。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzputcDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzputc");
  let path = pathDir + "/gzputc/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzputc(0);
  await gzip.gzclose();
}
```

### gzprintf<sup>12+</sup>

ArkTS-Dyn: gzprintf(format: string, ...args: Array\<string | number>): Promise\<number><br>
ArkTS-Sta: gzprintf(format: string, ...args: Array\<string | number>): Promise\<int>

在字符串格式的控制下，将参数转换和格式化后，压缩并写入文件，如fprintf中所示。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                          | 必填 | 说明                   |
| ------ | ----------------------------- | ---- | ---------------------- |
| format | string                        | 是   | 格式化描述符和纯文本。 |
| ...args   | Array\<string \| number> | 否   | 可变参数列表。         |

**返回值：**

| 类型                  | 说明                                      |
| --------------------- | ----------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象，返回实际写入的未压缩字节数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800004 | Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure. |
| 17800009 | Internal structure error.                                    |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzprintfDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzprintf");
  let path = pathDir + "/gzprintf/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzprintf("name is %s, age is %d", "Tom", 23);
  await gzip.gzclose();
}
```

### gzoffset<sup>12+</sup>

ArkTS-Dyn: gzoffset(): Promise\<number><br>
ArkTS-Sta: gzoffset(): Promise\<long>

返回文件的当前压缩（实际）读或写偏移量。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明                                                  |
| --------------------- | ----------------------------------------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<long> | Promise对象，返回文件的当前压缩（实际）读或写偏移量。 |

**错误码：**

以下错误码的详细介绍请参见[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                  |
| -------- | ------------------------- |
| 17800009 | Internal structure error. |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzoffsetDemo() {
  let pathDir = "/xxx";
  fs.mkdirSync(pathDir + "/gzoffset");
  let path = pathDir + "/gzoffset/test.gz";
  let gzip = zlib.createGZipSync();
  await gzip.gzopen(path, "wb");
  let result = await gzip.gzoffset();
  await gzip.gzclose();
}
```

### gzgets<sup>12+</sup>

gzgets(buf: ArrayBuffer): Promise\<string>

从文件中读取字节并将其解压缩到buf中，直到读取len-1字符，或者直到读取换行符并将其传输到buf，或者遇到文件结束条件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型        | 必填 | 说明               |
| ------ | ----------- | ---- | ------------------ |
| buf    | ArrayBuffer | 是   | 存储读取的行数据。 |

**返回值：**

| 类型                  | 说明                                  |
| --------------------- | ------------------------------------- |
| Promise\<string> | Promise对象，返回以null结尾的字符串。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.zlib错误码](./errorcode-zlib.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The parameter check failed. Possible causes: <br />1. Mandatory parameters are left unspecified;<br />2. Incorrect parameter types;<br />3. Parameter verification failed. |
| 17800009 | Internal structure error.                                    |

**示例：**

ArkTS-Dyn:
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
ArkTS-Sta:
```ts
// 代码中使用的路径需为应用的沙箱路径，如/data/storage/el2/base/haps,也可以通过context获取。
import { zlib } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

async function gzgetsDemo() {
  let pathDir = "/xxx";
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
```

## GzErrorOutputInfo<sup>12+</sup>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称      | 类型         | 只读 | 可选 | 说明                                         |
| --------- | ------------ | ---- | ---- | -------------------------------------------- |
| status    | ReturnStatus | 否   | 否   | 返回zlib文件状态码，参考ReturnStatus的定义。 |
| statusMsg | string       | 否   | 否   | zlib文件上发生的最后一个状态的状态消息。     |

## OffsetReferencePoint<sup>12+</sup>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称     | 值   | 说明             |
| -------- | ---- | ---------------- |
| SEEK_SET | 0    | 从文件开头查找。 |
| SEEK_CUR | 1    | 从当前位置查找。 |