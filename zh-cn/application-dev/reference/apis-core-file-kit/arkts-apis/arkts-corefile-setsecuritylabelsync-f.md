# setSecurityLabelSync

## setSecurityLabelSync

```TypeScript
function setSecurityLabelSync(path: string, type: DataLevel): void
```

以同步方法设置文件或目录的数据安全等级。数据安全等级仅可由低向高或平级设置。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件路径。 |
| type | DataLevel | 是 | 数据安全等级，只支持"s0","s1","s2","s3","s4"。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900007 | Arg list too long |
| 13900015 | File exists |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900037 | No data available |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**示例：**

```TypeScript
let filePath = pathDir + '/test.txt';
securityLabel.setSecurityLabelSync(filePath, "s0");

```

