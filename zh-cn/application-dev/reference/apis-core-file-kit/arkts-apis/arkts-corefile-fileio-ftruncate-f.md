# ftruncate

## 导入模块

```TypeScript
```

## ftruncate

```TypeScript
declare function ftruncate(fd: number, len?: number): Promise<void>
```

基于文件描述符截断文件，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [truncate](arkts-corefile-file-fs-truncate-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待截断文件的文件描述符。 |
| len | number | 否 | 文件截断后的长度，单位为Byte。默认为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回值。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
let fd = fileio.openSync(filePath);
fileio.ftruncate(fd, 5).then(() => {
  console.info("truncate file succeed");
}).catch((err: BusinessError) => {
  console.error("truncate file failed with error:" + err);
});
```


## ftruncate

```TypeScript
declare function ftruncate(fd: number, callback: AsyncCallback<void>): void
```

基于文件描述符截断文件，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [truncate](arkts-corefile-file-fs-truncate-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待截断文件的文件描述符。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
let fd = fileio.openSync(filePath);
fileio.ftruncate(fd, 5).then(() => {
  console.info("truncate file succeed");
}).catch((err: BusinessError) => {
  console.error("truncate file failed with error:" + err);
});
```

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
let fd = fileio.openSync(filePath);
let len = 5;
fileio.ftruncate(fd, 5, (err: BusinessError) => {
  // do something
});
```


## ftruncate

```TypeScript
declare function ftruncate(fd: number, len: number, callback: AsyncCallback<void>): void
```

基于文件描述符截断文件，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [truncate](arkts-corefile-file-fs-truncate-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待截断文件的文件描述符。 |
| len | number | 是 | 文件截断后的长度，单位为Byte。默认为0。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |

**示例**

参见 [ftruncate](#ftruncate)
