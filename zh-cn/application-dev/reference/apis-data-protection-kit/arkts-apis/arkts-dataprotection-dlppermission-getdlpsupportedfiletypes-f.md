# getDLPSupportedFileTypes

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

<a id="getdlpsupportedfiletypes"></a>
## getDLPSupportedFileTypes

```TypeScript
function getDLPSupportedFileTypes(): Promise<Array<string>>
```

查询当前可支持权限设置和校验的文件扩展名类型列表。调用成功后返回支持的文件类型列表，用于判断哪些文件类型可进行DLP权限管理。使用Promise异步回调。

该接口用于获取支持DLP权限管理的文件类型列表，以便决定当前文件是否可以进行加密。

**起始版本：** 10

<!--Device-dlpPermission-function getDLPSupportedFileTypes(): Promise<Array<string>>--><!--Device-dlpPermission-function getDLPSupportedFileTypes(): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象。返回当前可支持权限设置和校验的文件扩展名类型列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getDLPSupportedFileTypes().then((fileTypes) => { // 获取支持DLP的文件类型。
  console.info('fileTypes', JSON.stringify(fileTypes));
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});

```


<a id="getdlpsupportedfiletypes-1"></a>
## getDLPSupportedFileTypes

```TypeScript
function getDLPSupportedFileTypes(callback: AsyncCallback<Array<string>>): void
```

查询当前可支持权限设置和校验的文件扩展名类型列表。调用成功后返回支持的文件类型列表，用于判断哪些文件类型可进行DLP权限管理。使用callback异步回调。

该接口用于获取支持DLP权限管理的文件类型列表，以便决定当前文件是否可以进行加密。

**起始版本：** 10

<!--Device-dlpPermission-function getDLPSupportedFileTypes(callback: AsyncCallback<Array<string>>): void--><!--Device-dlpPermission-function getDLPSupportedFileTypes(callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数。err为undefined时表示查询成功；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getDLPSupportedFileTypes((err, fileTypes) => {
  if (err != undefined) {
    console.error('getDLPSupportedFileTypes error', err.code, err.message);
  } else {
    console.info('fileTypes', JSON.stringify(fileTypes));
  }
}); // 获取支持DLP的文件类型。

```

