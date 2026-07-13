# getPublicCertificate

## getPublicCertificate

```TypeScript
function getPublicCertificate(keyUri: string): Promise<CMResult>
```

表示获取用户公共凭据的详细信息。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyUri | string | 是 | 表示用户公共凭据的唯一标识符，长度限制256字节以内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMResult&gt; | Promise对象，返回获取用户公共凭据详细信息的结果，返回值为[CMResult](arkts-devicecertificate-cmresult-i.md)对象中的credential属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permissionrequired to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-证书不存在) | The certificate does not exist. |
| [17500005](../errorcode-certManager.md#17500005-应用未经用户授权) | The application is not authorized by the user. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri: string = 'test'; /* 用户获取公共凭据详情，需要使用凭据的唯一标识符，此处省略 */
try {
  certificateManager.getPublicCertificate(uri).then((cmResult) => {
    if (cmResult?.credential == undefined) {
      console.info('The result of getting public certificate is undefined.');
    } else {
      let cred = cmResult.credential;
      console.info('Succeeded in getting Public certificate.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get Public certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get Public certificate. Code: ${error.code}, message: ${error.message}`);
}

```

