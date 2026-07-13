# getOriginalSize

## getOriginalSize

```TypeScript
function getOriginalSize(compressedFile: string): Promise<number>
```

获取压缩文件的原始大小。使用Promise异步回调。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| compressedFile | string | 是 | 指定的压缩文件的文件路径，只支持zip格式压缩文件。文件路径必须为沙箱路径，沙箱路径可以通过context获取，可参考[FA模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-depr-i.md)，[Stage模型](../../apis-ability-kit/arkts-apis/arkts-ability-context-depr-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回压缩文件的原始大小，单位字节。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are leftunspecified; 2. Incorrect parameter types. |
| [900001](../../apis-basic-services-kit/errorcode-zlib.md#900001-传入的源文件错误) | The input source file is invalid. |
| [900003](../../apis-basic-services-kit/errorcode-zlib.md#900003-传入的源文件格式错误或者已损坏) | The input source file is not in ZIP format or is damaged. |

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

