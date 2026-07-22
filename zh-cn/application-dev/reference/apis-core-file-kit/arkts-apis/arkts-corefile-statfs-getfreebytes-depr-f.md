# getFreeBytes

## getFreeBytes

```TypeScript
function getFreeBytes(path: string, callback: AsyncCallback<number>): void
```

异步方法获取指定文件系统空闲字节数，使用callback形式返回结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getFreeBytes](arkts-corefile-statfs-getfreebytes-depr-f.md#getfreebytes)

<!--Device-Statfs-function getFreeBytes(path: string, callback: AsyncCallback<number>): void--><!--Device-Statfs-function getFreeBytes(path: string, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 需要查询的文件系统的文件路径 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 异步获取空闲字节数之后的回调 |

**示例：**

```TypeScript
import common from '@ohos.app.ability.common';
import { BusinessError } from '@ohos.base';
let context = getContext(this) as common.UIAbilityContext;
let path = context.filesDir;
statfs.getFreeBytes(path, (err: BusinessError, freeBytes:Number) => {
    if (err) {
        console.error('getFreeBytes callback failed');
    } else {
        console.info('getFreeBytes callback success' + freeBytes);
    }
});

```


## getFreeBytes

```TypeScript
function getFreeBytes(path: string): Promise<number>
```

异步方法获取指定文件系统空闲字节数，以Promise形式返回结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getFreeBytes](arkts-corefile-statfs-getfreebytes-depr-f.md#getfreebytes)

<!--Device-Statfs-function getFreeBytes(path: string): Promise<number>--><!--Device-Statfs-function getFreeBytes(path: string): Promise<number>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 需要查询的文件系统的文件路径 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 返回空闲字节数 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';
let path = "/dev";
statfs.getFreeBytes(path).then((number: number) => {
  console.info("getFreeBytes promise successfully:" + number);
}).catch((err: BusinessError) => {
  console.error("getFreeBytes failed with error:" + JSON.stringify(err));
});

```

