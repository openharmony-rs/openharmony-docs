# init

## init

```TypeScript
function init(authUri: string, spec: CMSignatureSpec, callback: AsyncCallback<CMHandle>): void
```

ʹ��ƾ�ݽ���ǩ������ǩ�ĳ�ʼ����������ǩ����ǩ���̵ĵ�һ�������������ε���update��finish�ӿ���ɲ�����ʹ��Callback�첽�ص���

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authUri | string | 是 | ��ʾʹ��ƾ�ݵ�Ψһ��ʶ������������256�ֽ����ڡ� |
| spec | CMSignatureSpec | 是 | ��ʾǩ������ǩ�����ԡ� |
| callback | AsyncCallback&lt;CMHandle&gt; | 是 | �ص���������ǩ������ǩ�ĳ�ʼ�������ɹ�ʱ��errΪnull��dataΪ��ȡ����CMHandle������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/><br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../../errorcode-universal.md#17500001-Internal) | Internal error. Possible causes: 1. IPC communication failed;<br/><br/>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../../errorcode-universal.md#17500002-The) | The certificate does not exist. |
| [17500005](../../errorcode-universal.md#17500005-The) | The application is not authorized by the user.<br/>Please call [openAuthorizeDialog](arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md#openAuthorizeDialog-1)<br/>method to request user authorization for the certificate or credential.&lt;br&gt;**适用版本：** 12+ |

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

ʹ��ƾ�ݽ���ǩ������ǩ�ĳ�ʼ��������ʹ��Promise�첽�ص���

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authUri | string | 是 | ��ʾʹ��ƾ�ݵ�Ψһ��ʶ������������256�ֽ����ڡ� |
| spec | CMSignatureSpec | 是 | ��ʾǩ������ǩ�����ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMHandle&gt; | Promise���󣬷���ǩ������ǩ�ĳ�ʼ���������������ֵΪCMHandle���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/><br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../../errorcode-universal.md#17500001-Internal) | Internal error. Possible causes: 1. IPC communication failed;<br/><br/>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../../errorcode-universal.md#17500002-The) | The certificate does not exist. |
| [17500005](../../errorcode-universal.md#17500005-The) | The application is not authorized by the user.&lt;br&gt;**适用版本：** 12+ |

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

