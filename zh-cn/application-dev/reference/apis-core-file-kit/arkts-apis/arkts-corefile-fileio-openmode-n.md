# OpenMode

open接口flags参数常量。文件打开标签。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-fileIo-namespace OpenMode--><!--Device-fileIo-namespace OpenMode-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 汇总

### 常量

| 名称 | 说明 |
| --- | --- |
| [READ_ONLY](arkts-corefile-openmode-con.md#READ_ONLY) | 只读打开。 |
| [WRITE_ONLY](arkts-corefile-openmode-con.md#WRITE_ONLY) | 只写打开。 |
| [READ_WRITE](arkts-corefile-openmode-con.md#READ_WRITE) | 读写打开。 |
| [CREATE](arkts-corefile-openmode-con.md#CREATE) | 若文件不存在，则创建文件。 |
| [TRUNC](arkts-corefile-openmode-con.md#TRUNC) | 如果文件存在且以只写或读写的方式打开，则将其长度裁剪为零。 |
| [APPEND](arkts-corefile-openmode-con.md#APPEND) | 以追加方式打开，后续写将追加到文件末尾。 |
| [NONBLOCK](arkts-corefile-openmode-con.md#NONBLOCK) | 如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续IO进行非阻塞操作。 |
| [DIR](arkts-corefile-openmode-con.md#DIR) | 如果path不指向目录，则出错。 |
| [NOFOLLOW](arkts-corefile-openmode-con.md#NOFOLLOW) | 如果path指向符号链接，则出错。 |
| [SYNC](arkts-corefile-openmode-con.md#SYNC) | 以同步IO的方式打开文件。 |
| [UNCACHE](arkts-corefile-openmode-con.md#UNCACHE) | UNCACHE IO。 |

