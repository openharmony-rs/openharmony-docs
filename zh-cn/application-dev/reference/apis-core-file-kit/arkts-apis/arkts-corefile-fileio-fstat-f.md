# fstat

## 导入模块

```TypeScript
```

## fstat

```TypeScript
declare function fstat(fd: number): Promise<Stat>
```

基于文件描述符获取文件状态信息，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [stat](arkts-corefile-file-fs-stat-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待获取文件状态的文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Stat](arkts-corefile-fileio-stat-depr-i.md)&gt; | Promise对象。返回表示文件状态的具体信息。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
let fd = fileio.openSync(filePath);
fileio.fstat(fd).then((stat: fileio.Stat) => {
  console.info("fstat succeed, the size of file is " + stat.size);
}).catch((err: BusinessError) => {
  console.error("fstat failed with error:" + err);
});
```


## fstat

```TypeScript
declare function fstat(fd: number, callback: AsyncCallback<Stat>): void
```

基于文件描述符获取文件状态信息，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [stat](arkts-corefile-file-fs-stat-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待获取文件状态的文件描述符。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Stat](arkts-corefile-fileio-stat-depr-i.md)&gt; | 是 | 异步获取文件状态信息之后的回调。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
let fd = fileio.openSync(filePath);
fileio.fstat(fd, (err: BusinessError) => {
  // do something
});
```
