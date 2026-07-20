# getSecurityLabelSync

## 导入模块

```TypeScript
import { securityLabel } from '@kit.CoreFileKit';
```

<a id="getsecuritylabelsync"></a>
## getSecurityLabelSync

```TypeScript
function getSecurityLabelSync(path: string): string
```

以同步方法获取文件或目录的数据安全等级。若未设置过数据安全等级则默认返回“s3”。

**起始版本：** 9

<!--Device-securityLabel-function getSecurityLabelSync(path: string): string--><!--Device-securityLabel-function getSecurityLabelSync(path: string): string-End-->

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
let type = securityLabel.getSecurityLabelSync(filePath);
console.info("Succeeded in getting security label, Label: " + type);

```

