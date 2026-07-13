# init

## init

```TypeScript
function init(authUri: string, spec: CMSignatureSpec, callback: AsyncCallback<CMHandle>): void
```

使用凭据进行签名、验签的初始化操作，是签名验签流程的第一步，后续需依次调用update和finish接口完成操作。使用Callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authUri | string | 是 | 表示使用凭据的唯一标识符，长度限制256字节以内。 |
| spec | CMSignatureSpec | 是 | 表示签名、验签的属性。 |
| callback | AsyncCallback&lt;CMHandle&gt; | 是 | 回调函数。当签名、验签的初始化操作成功时，err为null，data为获取到的CMHandle；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permissionrequired to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-证书不存在) | The certificate does not exist. |
| [17500005](../errorcode-certManager.md#17500005-应用未经用户授权) | The application is not authorized by the user.Please call [openAuthorizeDialog](arkts-devicecertificate-openauthorizedialog-f.md#openauthorizedialog-1)method to request user authorization for the certificate or credential.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

let uri: string = 'test'; /* 业务使用凭据进行签名、验签的初始化操作，需要使用凭据的唯一标识符，此处省略 */
const req: certificateManager.CMSignatureSpec = {
  purpose: certificateManager.CmKeyPurpose.CM_KEY_PURPOSE_SIGN,
  padding: certificateManager.CmKeyPadding.CM_PADDING_PSS,
  digest: certificateManager.CmKeyDigest.CM_DIGEST_SHA256
}
try {
  certificateManager.init(uri, req, (err, cmHandle) => {
    if (err != null) {
      console.error(`Failed to init. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in initiating.');
    }
  })
} catch (error) {
  console.error(`Failed to init. Code: ${error.code}, message: ${error.message}`);
}

```


## init

```TypeScript
function init(authUri: string, spec: CMSignatureSpec): Promise<CMHandle>
```

使用凭据进行签名、验签的初始化操作。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authUri | string | 是 | 表示使用凭据的唯一标识符，长度限制256字节以内。 |
| spec | CMSignatureSpec | 是 | 表示签名、验签的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMHandle&gt; | Promise对象，返回签名、验签的初始化操作结果，返回值为CMHandle对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permissionrequired to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-证书不存在) | The certificate does not exist. |
| [17500005](../errorcode-certManager.md#17500005-应用未经用户授权) | The application is not authorized by the user.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri: string = 'test'; /* 业务使用凭据进行签名、验签的初始化操作，需要使用凭据的唯一标识符，此处省略 */
const req: certificateManager.CMSignatureSpec = {
  purpose: certificateManager.CmKeyPurpose.CM_KEY_PURPOSE_VERIFY,
  padding: certificateManager.CmKeyPadding.CM_PADDING_PSS,
  digest: certificateManager.CmKeyDigest.CM_DIGEST_MD5
}
try {
  certificateManager.init(uri, req).then((handle) => {
    console.info('Succeeded in initiating.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to init. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to init. Code: ${error.code}, message: ${error.message}`);
}

```

