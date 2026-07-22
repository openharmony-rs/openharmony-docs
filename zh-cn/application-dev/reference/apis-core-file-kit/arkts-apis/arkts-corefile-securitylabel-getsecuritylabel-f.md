# getSecurityLabel

## 导入模块

```TypeScript
import { securityLabel } from '@kit.CoreFileKit';
```

## getSecurityLabel

```TypeScript
function getSecurityLabel(path: string): Promise<string>
```

获取文件或目录的数据安全等级。若未设置过数据安全等级则默认返回“s3”。使用Promise异步回调。

**起始版本：** 9

<!--Device-securityLabel-function getSecurityLabel(path: string): Promise<string>--><!--Device-securityLabel-function getSecurityLabel(path: string): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 返回数据安全等级。 |

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
import { BusinessError } from '@kit.BasicServicesKit';
let filePath = pathDir + '/test.txt';
securityLabel.getSecurityLabel(filePath).then((type: string) => {
  console.info("Succeeded in getting security label, Label: " + type);
}).catch((err: BusinessError) => {
  console.error("Failed to get security label. Code: " + err.code + ", message: " + err.message);
});

```


## getSecurityLabel

```TypeScript
function getSecurityLabel(path: string, callback: AsyncCallback<string>): void
```

获取文件或目录的数据安全等级。若未设置过数据安全等级则默认返回“s3”。使用callback异步回调。

**起始版本：** 9

<!--Device-securityLabel-function getSecurityLabel(path: string, callback: AsyncCallback<string>): void--><!--Device-securityLabel-function getSecurityLabel(path: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 异步获取数据安全等级之后的回调。 |

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
import { BusinessError } from '@kit.BasicServicesKit';
let filePath = pathDir + '/test.txt';
securityLabel.getSecurityLabel(filePath, (err: BusinessError, type: string) => {
  if (err) {
    console.error("Failed to get security label. Code: " + err.code + ", message: " + err.message);
  } else {
    console.info("Succeeded in getting security label, Label: " + type);
  }
});

```

