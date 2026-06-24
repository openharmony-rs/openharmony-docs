# getTotalSize

## getTotalSize

```TypeScript
function getTotalSize(path: string): Promise<number>
```

异步方法获取指定文件系统总字节数，以Promise形式返回结果。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 需要查询的文件系统的文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回总字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900031](../../errorcode-universal.md#13900031-Function) | Function not implemented |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900038](../../errorcode-universal.md#13900038-Value) | Value too large for defined data type |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let path = context.filesDir;
statfs.getTotalSize(path).then((number: number) => {
  console.info("Succeeded in getting total size: " + number);
}).catch((err: BusinessError) => {
  console.error("Failed to get total size. Code: " + err.code + ", message: " + err.message);
});

```


## getTotalSize

```TypeScript
function getTotalSize(path: string, callback: AsyncCallback<number>): void
```

异步方法获取指定文件系统总字节数，使用callback形式返回结果。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 需要查询的文件系统的文件路径。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 异步获取总字节数之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900031](../../errorcode-universal.md#13900031-Function) | Function not implemented |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900038](../../errorcode-universal.md#13900038-Value) | Value too large for defined data type |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let path = context.filesDir;
statfs.getTotalSize(path, (err: BusinessError, number: number) => {
  if (err) {
    console.error("Failed to get total size. Code: " + err.code + ", message: " + err.message);
  } else {
    console.info("Succeeded in getting total size: " + number);
  }
});

```

