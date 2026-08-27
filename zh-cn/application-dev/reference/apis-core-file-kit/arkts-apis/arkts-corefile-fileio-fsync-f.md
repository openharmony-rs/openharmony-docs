# fsync

## 导入模块

```TypeScript
```

## fsync

```TypeScript
declare function fsync(fd: number): Promise<void>
```

同步文件数据，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fsync](arkts-corefile-file-fs-fsync-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待同步文件的文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回值。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
let fd = fileio.openSync(filePath);
fileio.fsync(fd).then(() => {
  console.info("sync data succeed");
}).catch((err: BusinessError) => {
  console.error("sync data failed with error:" + err);
});
```


## fsync

```TypeScript
declare function fsync(fd: number, callback: AsyncCallback<void>): void
```

同步文件数据，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fsync](arkts-corefile-file-fs-fsync-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待同步文件的文件描述符。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步将文件数据同步之后的回调。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
let fd = fileio.openSync(filePath);
fileio.fsync(fd, (err: BusinessError) => {
  // do something
});
```
