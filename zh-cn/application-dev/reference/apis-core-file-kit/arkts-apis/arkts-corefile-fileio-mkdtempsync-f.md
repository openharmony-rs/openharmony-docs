# mkdtempSync

## mkdtempSync

```TypeScript
declare function mkdtempSync(prefix: string): string
```

以同步的方法创建临时目录。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:mkdtempSync](arkts-corefile-file-fs-mkdtempsync-f.md#mkdtempsync-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| prefix | string | 是 | 用随机产生的字符串替换以“XXXXXX”结尾目录路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 产生的唯一目录路径。 |

