# createReadStream

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## createReadStream

```TypeScript
declare function createReadStream(path: string, options?: ReadStreamOptions): ReadStream
```

以同步方法打开文件可读流。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件路径。 |
| options | [ReadStreamOptions](arkts-corefile-file-fs-readstreamoptions-i.md) | 否 | 支持如下选项：   - start，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读。   - end， number类型，表示期望读取结束的位置，单位为Byte。可选，默认文件末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ReadStream](arkts-corefile-file-fs-readstream-c.md) | 文件可读流。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900017 | No such device |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900024 | File too large |
| 13900030 | File name too number |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900044 | Network is unreachable |

**示例**

```TypeScript
// 创建文件可读流
const rs = fileIo.createReadStream(`${pathDir}/read.txt`);
// 创建文件可写流
const ws = fileIo.createWriteStream(`${pathDir}/write.txt`);
// 暂停模式拷贝文件
rs.on('readable', () => {
  const data = rs.read();
  if (!data) {
    return;
  }
  ws.write(data);
});
```
