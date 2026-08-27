# lstat

## 导入模块

```TypeScript
```

## lstat

```TypeScript
declare function lstat(path: string): Promise<Stat>
```

获取链接信息，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [lstat](arkts-corefile-file-fs-lstat-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目标文件的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Stat](arkts-corefile-fileio-stat-depr-i.md)&gt; | promise对象，返回文件对象，表示文件的具体信息，详情见stat。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
fileio.lstat(filePath).then((stat: fileio.Stat) => {
  console.info("get link status succeed, the size of file is" + stat.size);
}).catch((err: BusinessError) => {
  console.error("get link status failed with error:" + err);
});
```


## lstat

```TypeScript
declare function lstat(path: string, callback: AsyncCallback<Stat>): void
```

获取链接信息，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [lstat](arkts-corefile-file-fs-lstat-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目标文件的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Stat](arkts-corefile-fileio-stat-depr-i.md)&gt; | 是 | 回调函数，返回文件的具体信息。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let filePath = pathDir + "/test.txt";
fileio.lstat(filePath, (err: BusinessError, stat: fileio.Stat) => {
  // do something
});
```
