# createRandomAccessFileSync

## createRandomAccessFileSync

```TypeScript
declare function createRandomAccessFileSync(file: string | File, mode?: number,
  options?: RandomAccessFileOptions): RandomAccessFile
```

基于文件路径或文件对象创建RandomAccessFile对象。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| File | 是 | 文件的应用沙箱路径或已打开的File对象。 |
| mode | number | 否 | 创建文件RandomAccessFile对象的<br/>[选项](../../../../reference/apis-core-file-kit/js-apis-file-fs.md#openmode)，仅当传入文件沙箱路径时生效，必须指定如下选项中的一个，默认以只读方式创建：<br/>- OpenMode.READ_ONLY(0o0)：只读创建。<br/>- OpenMode.WRITE_ONLY(0o1)：只写创建。<br/>- OpenMode.READ_WRITE(0o2)：读写创建。<br/>给<br/>定如下功能选项，以按位或的方式追加，默认不给定任何额外选项：<br/>- OpenMode.CREATE(0o100)：若文件不存在，则创建文件。<br/>- OpenMode.TRUNC(0o1000)：如果<br/>RandomAccessFile对象存在且对应文件具有写权限，则将其长度裁剪为零。<br/>- OpenMode.APPEND(0o2000)：以追加方式打开，后续写将追加到RandomAccessFile对象末尾。<br/><br/>- OpenMode.NONBLOCK(0o4000)：如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续IO进行非阻塞操作。<br/>- OpenMode.DIR(0o200000)：如果path不指向<br/>目录，则出错。不允许附加写权限。<br/>- OpenMode.NOFOLLOW(0o400000)：如果path指向符号链接，则出错。<br/>- OpenMode.SYNC(0o4010000)：以同步IO的方式创建<br/>RandomAccessFile对象。 |
| options | RandomAccessFileOptions | 否 | 支持如下选项：<br/>- start，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读。<br/>-<br/>end，number类型，表示期望读取结束的位置，单位为Byte。可选，默认文件末尾。<br/>此选项仅对[getreadstream](arkts-corefile-randomaccessfile-i.md#getReadStream-1)及<br/>[getwritestream](arkts-corefile-randomaccessfile-i.md#getWriteStream-1)获取的文件流对象生效。 [since 12] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RandomAccessFile | 返回RandomAccessFile对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900006](../../errorcode-universal.md#13900006-No) | No such device or address |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900014](../../errorcode-universal.md#13900014-Device) | Device or resource busy |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900017](../../errorcode-universal.md#13900017-No) | No such device |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900022](../../errorcode-universal.md#13900022-Too) | Too many open files |
| [13900023](../../errorcode-universal.md#13900023-Text) | Text file busy |
| [13900024](../../errorcode-universal.md#13900024-File) | File too large |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900027](../../errorcode-universal.md#13900027-Readonly) | Read-only file system |
| [13900029](../../errorcode-universal.md#13900029-Resource) | Resource deadlock would occur |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900034](../../errorcode-universal.md#13900034-Operation) | Operation would block |
| [13900038](../../errorcode-universal.md#13900038-Value) | Value too large for defined data type |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |
| [13900044](../../errorcode-universal.md#13900044-Network) | Network is unreachable&lt;br&gt;**适用版本：** 12+ |

