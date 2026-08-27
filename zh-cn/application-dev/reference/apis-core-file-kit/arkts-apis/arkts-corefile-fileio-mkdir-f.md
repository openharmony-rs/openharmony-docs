# mkdir

## 导入模块

```TypeScript
```

## mkdir

```TypeScript
declare function mkdir(path: string, mode?: number): Promise<void>
```

创建目录，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [mkdir](arkts-corefile-file-fs-mkdir-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待创建目录的应用沙箱路径。 |
| mode | number | 否 | 创建目录的权限，可给定如下权限，以按位或的方式追加权限，默认给定0o775。   - 0o775：所有者具有读、写及可执行权限，其余用户具有读及可执行权限。   - 0o7 00：所有者具有读、写及可执行权限。   - 0o400：所有者具有读权限。   - 0o200：所有者具有写权限。   - 0o100：所有者具有可执行权限。   - 0o070：所有用户组具有读、写及可执行 权限。   - 0o040：所有用户组具有读权限。   - 0o020：所有用户组具有写权限。   - 0o010：所有用户组具有可执行权限。   - 0o007：其余用户具有读、写及可执行权限。   - 0o004：其余用户具有读权限。   - 0o002：其余用户具有写权限。   - 0o001：其余用户具有可执行权限。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回值。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let dirPath = pathDir + '/testDir';
fileio.mkdir(dirPath).then(() => {
  console.info("mkdir succeed");
}).catch((error: BusinessError) => {
  console.error("mkdir failed with error:" + error);
});
```


## mkdir

```TypeScript
declare function mkdir(path: string, callback: AsyncCallback<void>): void
```

创建目录，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [mkdir](arkts-corefile-file-fs-mkdir-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待创建目录的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步创建目录操作完成之后的回调。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let dirPath = pathDir + '/testDir';
fileio.mkdir(dirPath).then(() => {
  console.info("mkdir succeed");
}).catch((error: BusinessError) => {
  console.error("mkdir failed with error:" + error);
});
```

```TypeScript
import { BusinessError } from '@ohos.base';
let dirPath = pathDir + '/testDir';
fileio.mkdir(dirPath, (err: BusinessError) => {
  console.info("mkdir succeed");
});
```


## mkdir

```TypeScript
declare function mkdir(path: string, mode: number, callback: AsyncCallback<void>): void
```

创建目录，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [mkdir](arkts-corefile-file-fs-mkdir-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待创建目录的应用沙箱路径。 |
| mode | number | 是 | 创建目录的权限，可给定如下权限，以按位或的方式追加权限，默认给定0o775。   - 0o775：所有者具有读、写及可执行权限，其余用户具有读及可执行权限。   - 0o7 00：所有者具有读、写及可执行权限。   - 0o400：所有者具有读权限。   - 0o200：所有者具有写权限。   - 0o100：所有者具有可执行权限。   - 0o070：所有用户组具有读、写及可执行 权限。   - 0o040：所有用户组具有读权限。   - 0o020：所有用户组具有写权限。   - 0o010：所有用户组具有可执行权限。   - 0o007：其余用户具有读、写及可执行权限。   - 0o004：其余用户具有读权限。   - 0o002：其余用户具有写权限。   - 0o001：其余用户具有可执行权限。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步创建目录操作完成之后的回调。 |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
let dirPath = pathDir + '/testDir';
fileio.mkdir(dirPath, (err: BusinessError) => {
  console.info("mkdir succeed");
});
```
