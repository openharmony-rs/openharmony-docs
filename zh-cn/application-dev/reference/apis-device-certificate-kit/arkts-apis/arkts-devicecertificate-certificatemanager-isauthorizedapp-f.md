# isAuthorizedApp

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## isAuthorizedApp

```TypeScript
function isAuthorizedApp(keyUri: string): Promise<boolean>
```

表示当前应用是否由指定的用户凭据授权。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function isAuthorizedApp(keyUri: string): Promise<boolean>--><!--Device-certificateManager-function isAuthorizedApp(keyUri: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyUri | string | 是 | 表示用户授权给应用使用的凭据的唯一标识符，长度限制256字节以内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象，返回查询应用是否被授权的结果，true为已授权，false为未授权。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri: string = 'test'; /* 用户授权给应用使用的凭据的唯一标识符，此处省略 */
try {
  certificateManager.isAuthorizedApp(uri).then((res) => {
    if (res) {
      console.info('The application is authorized by the user.');
    } else {
      console.info('The application is not authorized by the user.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to check if the application is authorized. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to check if the application is authorized. Code: ${error.code}, message: ${error.message}`);
}

```

