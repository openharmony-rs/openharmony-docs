# getDLPSuffix

## getDLPSuffix

```TypeScript
function getDLPSuffix(): string
```

获取DLP文件扩展名。调用成功后返回DLP文件扩展名（如'.dlp'）。接口为同步接口。

用于获取DLP文件的标准扩展名，便于构建DLP文件名或进行文件类型判断。

**起始版本：** 10

**系统能力：** SystemCapability.Security.DataLossPrevention

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回DLP文件扩展名。例如：原文件"test.txt"，加密后的DLP文件名为"test.txt.dlp"，返回扩展名为".dlp"。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let dlpSuffix = dlpPermission.getDLPSuffix(); // 获取DLP扩展名。
console.info('dlpSuffix:', dlpSuffix);

```

