# getTotalBytes

## getTotalBytes

```TypeScript
function getTotalBytes(path: string, callback: AsyncCallback<number>): void
```

异步方法获取指定文件系统总字节数，使用callback形式返回结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getTotalBytes

<!--Device-Statfs-function getTotalBytes(path: string, callback: AsyncCallback<number>): void--><!--Device-Statfs-function getTotalBytes(path: string, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 需要查询的文件系统的文件路径 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 异步获取总字节数之后的回调 |

**示例：**

```TypeScript
import common from '@ohos.app.ability.common';
import { BusinessError } from '@ohos.base';
let context = getContext(this) as common.UIAbilityContext;
let path = context.filesDir;
statfs.getTotalBytes(path, (err: BusinessError, totalBytes:Number) => {
    if (err) {
        console.error('getTotalBytes callback failed');
    } else {
        console.info('getTotalBytes callback success' + totalBytes);
    }
});

```


## getTotalBytes

```TypeScript
function getTotalBytes(path: string): Promise<number>
```

异步方法获取指定文件系统总字节数，以Promise形式返回结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getTotalBytes

<!--Device-Statfs-function getTotalBytes(path: string): Promise<number>--><!--Device-Statfs-function getTotalBytes(path: string): Promise<number>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 需要查询的文件系统的文件路径 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | 返回总字节数 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';
let path = "/dev";
statfs.getTotalBytes(path).then((number: number) => {
  console.info("getTotalBytes promise successfully:" + number);
}).catch((err: BusinessError) => {
  console.error("getTotalBytes failed with error:" + JSON.stringify(err));
});

```

