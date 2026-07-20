# getOriginalFileName

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

<a id="getoriginalfilename"></a>
## getOriginalFileName

```TypeScript
function getOriginalFileName(fileName: string): string
```

获取指定DLP文件名的原始文件名。该接口为同步接口。

根据原始文件名后缀判断文件类型，选择对应的应用打开。

**起始版本：** 10

<!--Device-dlpPermission-function getOriginalFileName(fileName: string): string--><!--Device-dlpPermission-function getOriginalFileName(fileName: string): string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileName | string | 是 | 指定要查询的DLP文件名。长度不超过255字节，超出此范围抛出错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回DLP文件的原始文件名。例如：DLP文件名为test.txt.dlp，则返回的原始文件名为test.txt。不超过255字节。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let originalFileName = dlpPermission.getOriginalFileName('test.txt.dlp'); // 获取原始文件名。
console.info('originalFileName:', originalFileName);

```

