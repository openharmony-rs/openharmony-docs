# truncate

## 导入模块

```TypeScript
```

## truncate

```TypeScript
declare function truncate(path: string, len?: number): Promise<void>
```

基于文件路径截断文件，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [truncate](arkts-corefile-file-fs-truncate-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待截断文件的应用沙箱路径。 |
| len | number | 否 | 文件截断后的长度，单位为Byte。默认为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回值。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
let len = 5;
fileio.truncate(filePath, len).then(() => {
  console.info("truncate file succeed");
}).catch((err: BusinessError) => {
  console.error("truncate file failed with error:" + err);
});
```


## truncate

```TypeScript
declare function truncate(path: string, callback: AsyncCallback<void>): void
```

基于文件路径截断文件，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [truncate](arkts-corefile-file-fs-truncate-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待截断文件的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
let len = 5;
fileio.truncate(filePath, len).then(() => {
  console.info("truncate file succeed");
}).catch((err: BusinessError) => {
  console.error("truncate file failed with error:" + err);
});
```

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
let len = 5;
fileio.truncate(filePath, len, (err: BusinessError) => {
  // do something
});
```


## truncate

```TypeScript
declare function truncate(path: string, len: number, callback: AsyncCallback<void>): void
```

基于文件路径截断文件，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [truncate](arkts-corefile-file-fs-truncate-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待截断文件的应用沙箱路径。 |
| len | number | 是 | 文件截断后的长度，单位为Byte。默认为0。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |

**示例**

参见 [truncate](#truncate)
