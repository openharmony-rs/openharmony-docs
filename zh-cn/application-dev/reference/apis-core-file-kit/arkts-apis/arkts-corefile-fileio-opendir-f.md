# opendir

## 导入模块

```TypeScript
```

## opendir

```TypeScript
declare function opendir(path: string): Promise<Dir>
```

打开文件目录，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [listFile](arkts-corefile-file-fs-listfile-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待打开文件目录的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Dir](arkts-corefile-fileio-dir-depr-i.md)&gt; | Promise对象。返回Dir对象。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let dirPath = pathDir + "/testDir";
fileio.opendir(dirPath).then((dir: fileio.Dir) => {
  console.info("opendir succeed");
}).catch((err: BusinessError) => {
  console.error("opendir failed with error:" + err);
});
```


## opendir

```TypeScript
declare function opendir(path: string, callback: AsyncCallback<Dir>): void
```

打开文件目录，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [listFile](arkts-corefile-file-fs-listfile-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待打开文件目录的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Dir](arkts-corefile-fileio-dir-depr-i.md)&gt; | 是 | 异步打开文件目录之后的回调。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
fileio.opendir(pathDir, (err: BusinessError, dir: fileio.Dir) => {
  // example code in Dir struct
  // use read/readSync/close
});
```
