# getUserTrustedCertificate

## getUserTrustedCertificate

```TypeScript
function getUserTrustedCertificate(certUri: string): Promise<CMResult>
```

表示获取用户根CA证书的详细信息。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| certUri | string | 是 | 表示用户根CA证书的唯一标识符，长度限制256字节以内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMResult&gt; | Promise对象，返回获取用户根CA证书详细信息的结果，返回值为[CMResult](arkts-devicecertificate-cmresult-i.md)对象中的certInfo属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permissionrequired to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-证书不存在) | The certificate does not exist. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let certUri: string = 'testUserCert'; /* 用户获取用户根CA证书详情，需要使用CA证书的唯一标识符，此处省略 */
try {
  certificateManager.getUserTrustedCertificate(certUri).then((cmResult) => {
    if (cmResult?.certInfo == undefined) {
      console.info('The result of getting user trusted certificate is undefined.');
    } else {
      let cert = cmResult.certInfo;
      console.info('Succeeded in getting user trusted certificate.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get user trusted certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get user trusted certificate. Code: ${error.code}, message: ${error.message}`);
}

```

