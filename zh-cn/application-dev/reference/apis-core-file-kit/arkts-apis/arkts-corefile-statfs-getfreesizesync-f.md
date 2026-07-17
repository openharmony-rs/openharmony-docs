# getFreeSizeSync

## 导入模块

```TypeScript
import { statfs } from '@kit.CoreFileKit';
```

## getFreeSizeSync

```TypeScript
function getFreeSizeSync(path: string): number
```

以同步方法获取指定文件系统空闲字节数。

**起始版本：** 10

<!--Device-statfs-function getFreeSizeSync(path: string): long--><!--Device-statfs-function getFreeSizeSync(path: string): long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 需要查询的文件系统的文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回空闲字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900030 | File name too long |
| 13900031 | Function not implemented |
| 13900033 | Too many symbolic links encountered |
| 13900038 | Value too large for defined data type |
| 13900042 | Unknown error |

**示例：**

```TypeScript
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let path = context.filesDir;
let freeSize = statfs.getFreeSizeSync(path);
console.info("Succeeded in getting free size: " + freeSize);

```

