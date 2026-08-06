# mmapSync

## mmapSync

```TypeScript
function mmapSync(file: int | File, mode: MappingMode, offset: long, size: int): FileMapping
```

以同步方法基于文件描述符或文件对象创建文件映射对象，实现文件的高效读写访问。 > **说明：** > > 1. 仅支持对常规文件（regular file）进行内存映射，不支持管道、socket、设备文件等非常规文件类型。可通过[statSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取文件属性后调用 > [Stat.isFile()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_判断文件是否为常规文件。 > > 2. 若映射范围超过原始文件大小且文件具有写权限，将自动扩展映射文件大小。 > > 3. 对于外部存储或网络文件等，由于底层文件系统的差异，映射的建立及对映射内存的访问行为不做保证，可能导致应用异常终止。建议此类场景优先使用[read]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、 > [write]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_或[Stream]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_等其他文件访问接口。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-fileIo-function mmapSync(file: int | File, mode: MappingMode, offset: long, size: int): FileMapping--><!--Device-fileIo-function mmapSync(file: int | File, mode: MappingMode, offset: long, size: int): FileMapping-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | int \| File | 是 | 已打开的File对象或已打开的文件描述符fd。 |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 创建文件内存映射对象的选项，必须指定如下选项中的一个：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_   - MappingMode.READ\_\_\_ESCAPED\_UNDERSCORE\_\_\_ONLY(0)：只读映射模式。文件映射区不可写，修改会抛出异常。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_   - MappingMode.READ\_\_\_ESCAPED\_UNDERSCORE\_\_\_WRITE(1)：读写映射模式。修改会写入文件映射区，后续由操作系统同步到文件（非实时）。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_   - MappingMode.PRIVATE(2)：私有映射模式。是一种写时复制的映射机制，对映射区的修改仅对当前进程可见，不会影响原始文件。 |
| offset | long | 是 | 文件映射区的起始位置，单位为Byte。 |
| size | int | 是 | 文件映射区的大小，取值范围(0, INT32\_\_\_ESCAPED\_UNDERSCORE\_\_\_MAX]，单位为Byte。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 创建的文件映射对象。返回的对象初始状态：position为0，limit和capacity均等于size。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900020 | Invalid argument |
| 13900021 | File table overflow |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900038 | Value too large for defined data type |
| 13900050 | Internal resource error |
| 13900056 | Mmap does not support mapping this file |

