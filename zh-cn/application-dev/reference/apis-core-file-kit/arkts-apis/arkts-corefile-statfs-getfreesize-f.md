# getFreeSize

## 导入模块

```TypeScript
import { statfs } from '@kit.CoreFileKit';
```

## getFreeSize

```TypeScript
function getFreeSize(path: string): Promise<long>
```

获取指定文件或目录所在文件系统的空闲字节数。使用Promise异步回调。

**起始版本：** 23

<!--Device-statfs-function getFreeSize(path: string): Promise<long>--><!--Device-statfs-function getFreeSize(path: string): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象，返回空闲字节数，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900018 | Not a directory |
| 13900030 | File name too long |
| 13900031 | Function not implemented |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900038 | Value too large for defined data type |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |
| 13900011 | Out of memory |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let path = context.filesDir;
statfs.getFreeSize(path).then((freeSize: number) => {
  console.info("Succeeded in getting free size: " + freeSize);
}).catch((err: BusinessError) => {
  console.error("Failed to get free size. Code: " + err.code + ", message: " + err.message);
});
```


## getFreeSize

```TypeScript
function getFreeSize(path: string, callback: AsyncCallback<long>): void
```

获取指定文件或目录所在文件系统的空闲字节数。使用callback异步回调。

**起始版本：** 23

<!--Device-statfs-function getFreeSize(path: string, callback: AsyncCallback<long>): void--><!--Device-statfs-function getFreeSize(path: string, callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数，返回空闲字节数，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900018 | Not a directory |
| 13900030 | File name too long |
| 13900031 | Function not implemented |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900038 | Value too large for defined data type |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |
| 13900011 | Out of memory |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let path = context.filesDir;
statfs.getFreeSize(path, (err: BusinessError, freeSize: number) => {
  if (err) {
    console.error("Failed to get free size. Code: " + err.code + ", message: " + err.message);
  } else {
    console.info("Succeeded in getting free size: " + freeSize);
  }
});
```

