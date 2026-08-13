# OpenMode

open接口flags参数常量，用于指定文件打开模式（如只读、只写、读写、创建等）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-namespace OpenMode--><!--Device-fileIo-namespace OpenMode-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 汇总

### 常量

| 名称 | 说明 |
| --- | --- |
| [READ_ONLY](arkts-na-openmode-con.md#READ_ONLY) | 只读打开。值为 0o0。 |
| [WRITE_ONLY](arkts-na-openmode-con.md#WRITE_ONLY) | 只写打开。值为 0o1。 |
| [READ_WRITE](arkts-na-openmode-con.md#READ_WRITE) | 读写打开。值为 0o2。 |
| [CREATE](arkts-na-openmode-con.md#CREATE) | 若文件不存在，则创建文件。值为 0o100。 |
| [TRUNC](arkts-na-openmode-con.md#TRUNC) | 如果文件存在且以只写或读写的方式打开，则将其长度裁剪为零。值为 0o1000 |
| [APPEND](arkts-na-openmode-con.md#APPEND) | 以追加方式打开，后续写将追加到文件末尾。值为 0o2000。 |
| [NONBLOCK](arkts-na-openmode-con.md#NONBLOCK) | 如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续 IO 进行非阻塞操作。值为 0o4000。 |
| [DIR](arkts-na-openmode-con.md#DIR) | 如果path不指向目录，则出错。值为 0o200000。 |
| [NOFOLLOW](arkts-na-openmode-con.md#NOFOLLOW) | 如果path指向符号链接，则出错。值为 0o400000。 |
| [SYNC](arkts-na-openmode-con.md#SYNC) | 以同步IO的方式打开文件。值为 0o4010000。 |
| [UNCACHE](arkts-na-openmode-con.md#UNCACHE) | 读写文件不进行页缓存。值为 0o10000000000。 |

