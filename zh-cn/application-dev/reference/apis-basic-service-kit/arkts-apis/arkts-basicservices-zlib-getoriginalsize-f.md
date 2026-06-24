# getOriginalSize

## getOriginalSize

```TypeScript
function getOriginalSize(compressedFile: string): Promise<number>
```

获取压缩文件的原始大小。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| compressedFile | string | 是 | 指定的压缩文件的文件路径，只支持zip格式压缩文件。文件路径必须为沙箱路径，沙箱路径可以通过context获取，可参考<br/>[FA模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-depr-i.md#Context)，[Stage模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-depr-i.md#Context)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回压缩文件的原始大小，单位字节。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The parameter check failed. Possible causes: 1. Mandatory parameters are left<br/>unspecified; 2. Incorrect parameter types. |
| [900001](../../errorcode-universal.md#900001-The) | The input source file is invalid. |
| [900003](../../errorcode-universal.md#900003-The) | The input source file is not in ZIP format or is damaged. |

**示例：**

```TypeScript
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

