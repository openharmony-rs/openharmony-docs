# completelyDelete（系统接口）

## completelyDelete

```TypeScript
function completelyDelete(uri: string): void
```

Permanently deletes a file or directory from the **Recently deleted** list.

**起始版本：** 10

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | URI of the file or directory. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**示例：**

```TypeScript
let fileinfos = trash.listFile();
let uri = fileinfos[0].uri;
trash.completelyDelete(uri);

```

