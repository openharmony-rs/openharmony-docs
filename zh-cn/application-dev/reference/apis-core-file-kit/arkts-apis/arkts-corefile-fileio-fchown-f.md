# fchown

## 导入模块

```TypeScript
```

## fchown

```TypeScript
declare function fchown(fd: number, uid: number, gid: number): Promise<void>
```

基于文件描述符改变文件所有者，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待改变文件的文件描述符。 |
| uid | number | 是 | 文件所有者的UID。 |
| gid | number | 是 | 文件所有组的GID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回值。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
let fd = fileio.openSync(filePath);
let stat = fileio.statSync(filePath);
fileio.fchown(fd, stat.uid, stat.gid).then(() => {
  console.info("chown succeed");
}).catch((err: BusinessError) => {
  console.error("chown failed with error:" + err);
});
```


## fchown

```TypeScript
declare function fchown(fd: number, uid: number, gid: number, callback: AsyncCallback<void>): void
```

基于文件描述符改变文件所有者，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待改变文件的文件描述符。 |
| uid | number | 是 | 文件所有者的UID。 |
| gid | number | 是 | 文件所有组的GID。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步改变文件所有者之后的回调。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
let fd = fileio.openSync(filePath);
let stat = fileio.statSync(filePath);
fileio.fchown(fd, stat.uid, stat.gid, (err: BusinessError) => {
  // do something
});
```
