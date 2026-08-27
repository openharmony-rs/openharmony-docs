# rmdir

## 导入模块

```TypeScript
```

## rmdir

```TypeScript
declare function rmdir(path: string): Promise<void>
```

删除目录，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [rmdir](arkts-corefile-file-fs-rmdir-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待删除目录的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回值。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let dirPath = pathDir + '/testDir';
fileio.rmdir(dirPath).then(() => {
  console.info("rmdir succeed");
}).catch((err: BusinessError) => {
  console.error("rmdir failed with error:" + err);
});
```


## rmdir

```TypeScript
declare function rmdir(path: string, callback: AsyncCallback<void>): void
```

删除目录，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [rmdir](arkts-corefile-file-fs-rmdir-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待删除目录的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步删除目录之后的回调。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let dirPath = pathDir + '/testDir';
fileio.rmdir(dirPath, (err: BusinessError) => {
  // do something
  console.info("rmdir succeed");
});
```
