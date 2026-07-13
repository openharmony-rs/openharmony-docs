# listFileSync

## listFileSync

```TypeScript
declare function listFileSync(
  path: string,
  options?: ListFileOptions
): string[]
```

默认以同步方式列出当前目录下所有文件名和目录名。支持过滤。

可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| options | ListFileOptions | 否 | 文件过滤选项。默认不进行过滤。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 返回文件名数组，默认以'utf-8'编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900018 | Not a directory |
| 13900042 | Unknown error |

