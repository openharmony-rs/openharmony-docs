# rename

## 导入模块

```TypeScript
```

## rename

```TypeScript
declare function rename(oldPath: string, newPath: string): Promise<void>
```

重命名文件，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [rename](arkts-corefile-file-fs-rename-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldPath | string | 是 | 目标文件的当前应用沙箱路径。 |
| newPath | string | 是 | 目标文件的新应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回值。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let srcFile = pathDir + "/test.txt";
let dstFile = pathDir + '/new.txt';
fileio.rename(srcFile, dstFile).then(() => {
  console.info("rename succeed");
}).catch((err: BusinessError) => {
  console.error("rename failed with error:" + err);
});
```


## rename

```TypeScript
declare function rename(oldPath: string, newPath: string, callback: AsyncCallback<void>): void
```

重命名文件，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [rename](arkts-corefile-file-fs-rename-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldPath | string | 是 | 目标文件的当前应用沙箱路径。 |
| newPath | string | 是 | 目标文件的新应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步重命名文件之后的回调。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let srcFile = pathDir + "/test.txt";
let dstFile = pathDir + '/new.txt';
fileio.rename(srcFile, dstFile, (err: BusinessError) => {
});
```
