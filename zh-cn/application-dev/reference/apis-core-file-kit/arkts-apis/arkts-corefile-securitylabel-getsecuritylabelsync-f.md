# getSecurityLabelSync

## getSecurityLabelSync

```TypeScript
function getSecurityLabelSync(path: string): string
```

以同步方法获取文件或目录的数据安全等级。若未设置过数据安全等级则默认返回“s3”。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回数据安全等级。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900007](../../errorcode-universal.md#13900007-Arg) | Arg list too long |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900037](../../errorcode-universal.md#13900037-No) | No data available |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |

**示例：**

```TypeScript
let filePath = pathDir + '/test.txt';
let type = securityLabel.getSecurityLabelSync(filePath);
console.info("Succeeded in getting security label, Label: " + type);

```

