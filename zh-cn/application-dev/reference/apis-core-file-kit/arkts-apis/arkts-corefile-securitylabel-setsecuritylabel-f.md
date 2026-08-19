# setSecurityLabel

## 导入模块

```TypeScript
import { securityLabel } from '@kit.CoreFileKit';
```

## setSecurityLabel

```TypeScript
function setSecurityLabel(path: string, type: DataLevel): Promise<void>
```

设置文件或目录的数据安全等级，用于实现文件的分级管理和访问控制。使用Promise异步回调。

**起始版本：** 23

<!--Device-securityLabel-function setSecurityLabel(path: string, type: DataLevel): Promise<void>--><!--Device-securityLabel-function setSecurityLabel(path: string, type: DataLevel): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径。 |
| type | [DataLevel](arkts-corefile-securitylabel-datalevel-t.md) | 是 | 数据安全等级，只支持"s0","s1","s2","s3","s4"。<br>注意：数据安全等级仅可由低向高或同级设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900037 | No data available |
| 13900007 | Arg list too long |
| 13900001 | Operation not permitted |
| 13900015 | File exists |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let filePath = pathDir + '/test.txt';
securityLabel.setSecurityLabel(filePath, "s0").then(() => {
  console.info("Succeeded in setting security label.");
}).catch((err: BusinessError) => {
  console.error("Failed to set security label. Code: " + err.code + ", message: " + err.message);
});
```


## setSecurityLabel

```TypeScript
function setSecurityLabel(path: string, type: DataLevel, callback: AsyncCallback<void>): void
```

设置文件或目录的数据安全等级，用于实现文件的分级管理和访问控制。使用callback异步回调。

**起始版本：** 23

<!--Device-securityLabel-function setSecurityLabel(path: string, type: DataLevel, callback: AsyncCallback<void>): void--><!--Device-securityLabel-function setSecurityLabel(path: string, type: DataLevel, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径。 |
| type | [DataLevel](arkts-corefile-securitylabel-datalevel-t.md) | 是 | 数据安全等级，只支持"s0","s1","s2","s3","s4"。<br>注意：数据安全等级仅可由低向高或同级设置。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当设置数据安全等级成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900037 | No data available |
| 13900007 | Arg list too long |
| 13900001 | Operation not permitted |
| 13900015 | File exists |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let filePath = pathDir + '/test.txt';
securityLabel.setSecurityLabel(filePath, "s0", (err: BusinessError) => {
  if (err) {
    console.error("Failed to set security label. Code: " + err.code + ", message: " + err.message);
  } else {
    console.info("Succeeded in setting security label.");
  }
});
```

