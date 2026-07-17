# copyFileSync

## copyFileSync

```TypeScript
declare function copyFileSync(src: string | number, dest: string | number, mode?: number): void
```

以同步方法复制文件。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:copyFileSync](arkts-corefile-file-fs-copyfilesync-f.md#copyfilesync-1)

<!--Device-unnamed-declare function copyFileSync(src: string | number, dest: string | number, mode?: number): void--><!--Device-unnamed-declare function copyFileSync(src: string | number, dest: string | number, mode?: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string \| number | 是 | 待复制文件的路径或待复制文件的描述符。 |
| dest | string \| number | 是 | 目标文件路径或目标文件描述符。 |
| mode | number | 否 | mode提供覆盖文件的选项，当前仅支持0，且默认为0。<br/>0：完全覆盖目标文件，未覆盖部分将被裁切掉。 |

