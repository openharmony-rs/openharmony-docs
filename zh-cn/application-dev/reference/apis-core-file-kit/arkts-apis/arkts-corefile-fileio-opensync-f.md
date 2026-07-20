# openSync

<a id="opensync"></a>
## openSync

```TypeScript
declare function openSync(path: string, flags?: number, mode?: number): number
```

以同步方法打开文件。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:openSync](arkts-corefile-file-fs-opensync-f.md#opensync-1)

<!--Device-unnamed-declare function openSync(path: string, flags?: number, mode?: number): number--><!--Device-unnamed-declare function openSync(path: string, flags?: number, mode?: number): number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待打开文件的应用沙箱路径。 |
| flags | number | 否 | 打开文件的选项，必须指定如下选项中的一个，默认以只读方式打开：<br/>-?0o0：只读打开。<br/>-?0o1：只写打开。<br/>-?0o2：读写打开。<br/>同时，也可给定如下选项，以按位或的方式追加，默认不给定任何额外选项：<br/>-?0o100：若文件不存在，则创建文件。使用该选项时必须指定第三个参数?mode。<br/>-?0o200：如果追加了0o100选项，且文件已经存在，则出错。<br/>-?0o1000：如果文件存在且文件具有写权限，则将其长度裁剪为零。<br/>-?0o2000：以追加方式打开，后续写将追加到文件末尾。<br/>-?0o4000：如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续?IO?进行非阻塞操作。<br/>-?0o200000：如果path不指向目录，则出错。<br/>-?0o400000：如果path指向符号链接，则出错。<br/>-?0o4010000：以同步IO的方式打开文件。 |
| mode | number | 否 | 若创建文件，则指定文件的权限，可给定如下权限，以按位或的方式追加权限，默认给定0o660。<br/>-?0o660：所有者具有读、写权限，所有用户组具有读、写权限。<br/>-?0o640：所有者具有读、写权限，所有用户组具有读权限。<br/>-?0o700：所有者具有读、写及可执行权限。<br/>-?0o400：所有者具有读权限。<br/>-?0o200：所有者具有写权限。<br/>-?0o100：所有者具有可执行权限。<br/>-?0o070：所有用户组具有读、写及可执行权限。<br/>-?0o040：所有用户组具有读权限。<br/>-?0o020：所有用户组具有写权限。<br/>-?0o010：所有用户组具有可执行权限。<br/>-?0o007：其余用户具有读、写及可执行权限。<br/>-?0o004：其余用户具有读权限。<br/>-?0o002：其余用户具有写权限。<br/>-?0o001：其余用户具有可执行权限。<br/>创建出的文件权限受umask影响，umask随进程启动确定，其修改当前不开放。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 打开文件的文件描述符。 |

