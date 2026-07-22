# getUriFromPath

## 导入模块

```TypeScript
import { fileUri } from '@kit.CoreFileKit';
```

## getUriFromPath

```TypeScript
function getUriFromPath(path: string): string
```

通过应用沙箱内的文件路径生成URI。路径中的中文及非数字字母的特殊字符会进行百分号编码。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-fileUri-function getUriFromPath(path: string): string--><!--Device-fileUri-function getUriFromPath(path: string): string-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 应用沙箱内的文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回通过文件路径生成的URI。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalidPossible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |

**示例：**

```TypeScript
let pathDir = this.context.filesDir; // 获取应用沙箱路径。
let filePath = pathDir + '/test';
let uri = fileUri.getUriFromPath(filePath);

```

