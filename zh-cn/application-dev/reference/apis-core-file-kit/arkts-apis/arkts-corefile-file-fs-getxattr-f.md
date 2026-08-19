# getxattr

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
import { fileIo } from '@kit.CoreFileKit'
import { ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, TaskSignal } from '@kit.CoreFileKit';
```

## getxattr

```TypeScript
declare function getxattr(path: string, key: string): Promise<string>
```

获取文件或目录的扩展属性。使用promise异步回调。

**起始版本：** 12

<!--Device-unnamed-declare function getxattr(path: string, key: string): Promise<string>--><!--Device-unnamed-declare function getxattr(path: string, key: string): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径。 |
| key | string | 是 | 扩展属性的key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回扩展属性的value。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types. |
| 13900037 | No data available |
| 13900038 | Value too large for defined data type |
| 13900007 | Arg list too long |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900031 | Function not implemented |
| 13900042 | Unknown error |

