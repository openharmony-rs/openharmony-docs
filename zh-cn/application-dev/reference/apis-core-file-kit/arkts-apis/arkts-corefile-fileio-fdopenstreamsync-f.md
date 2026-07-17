# fdopenStreamSync

## fdopenStreamSync

```TypeScript
declare function fdopenStreamSync(fd: number, mode: string): Stream
```

以同步方法基于文件描述符打开文件流。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:fdopenStreamSync](arkts-corefile-file-fs-fdopenstreamsync-f.md#fdopenstreamsync-1)

<!--Device-unnamed-declare function fdopenStreamSync(fd: number, mode: string): Stream--><!--Device-unnamed-declare function fdopenStreamSync(fd: number, mode: string): Stream-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待打开文件的文件描述符。 |
| mode | string | 是 | -?r：打开只读文件，该文件必须存在。<br/>-?r+：打开可读写的文件，该文件必须存在。<br/>-?w：打开只写文件，若文件存在则文件长度清0，即该文件内容会消失。若文件不存在则建立该文件。<br/>-?w+：打开可读写文件，若文件存在则文件长度清0，即该文件内容会消失。若文件不存在则建立该文件。<br/>-?a：以附加的方式打开只写文件。若文件不存在，则会建立该文件，如果文件存在，写入的数据会被加到文件尾，即文件原先的内容会被保留。<br/>-?a+：以附加方式打开可读写的文件。若文件不存在，则会建立该文件，如果文件存在，写入的数据会被加到文件尾后，即文件原先的内容会被保留。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Stream](arkts-corefile-file-fs-stream-i.md) | 返回文件流的结果。 |

