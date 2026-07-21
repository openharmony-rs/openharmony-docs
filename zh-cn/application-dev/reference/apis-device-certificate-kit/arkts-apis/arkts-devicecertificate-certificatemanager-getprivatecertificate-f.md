# getPrivateCertificate

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

<a id="getprivatecertificate"></a>
## getPrivateCertificate

```TypeScript
function getPrivateCertificate(keyUri: string, callback: AsyncCallback<CMResult>): void
```

获取私有凭据的详细信息，使用Callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function getPrivateCertificate(keyUri: string, callback: AsyncCallback<CMResult>): void--><!--Device-certificateManager-function getPrivateCertificate(keyUri: string, callback: AsyncCallback<CMResult>): void-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyUri | string | 是 | 表示待获取凭据的唯一标识符，长度限制256字节以内。 |
| callback | AsyncCallback&lt;CMResult&gt; | 是 | 回调函数。当获取私有凭据的详细信息成功时，err为null，data为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的credential属性；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-证书不存在) | The certificate does not exist. Possible causes:1. The certificate URI is incorrect;2. The certificate has been uninstalled. Please check the certificate URI. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

let uri: string = 'test'; /* 业务获取私有凭据详情，需要使用凭据的唯一标识符，此处省略 */
try {
  certificateManager.getPrivateCertificate(uri, (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to get private certificate. Code: ${err.code}, message: ${err.message}`);
    } else {
      if (cmResult?.credential == undefined) {
        console.info('The result of getting private certificate is undefined.');
      } else {
        let list = cmResult?.credential;
        console.info('Succeeded in getting private certificate.');
      }
    }
  });
} catch (error) {
  console.error(`Failed to get private certificate. Code: ${error.code}, message: ${error.message}`);
}

```


<a id="getprivatecertificate-1"></a>
## getPrivateCertificate

```TypeScript
function getPrivateCertificate(keyUri: string): Promise<CMResult>
```

获取私有凭据详情。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function getPrivateCertificate(keyUri: string): Promise<CMResult>--><!--Device-certificateManager-function getPrivateCertificate(keyUri: string): Promise<CMResult>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyUri | string | 是 | 表示待获取凭据的唯一标识符，长度限制256字节以内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMResult&gt; | Promise对象，返回获取私有凭据详细信息的结果，返回值为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的credential属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-证书不存在) | The certificate does not exist. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri: string = 'test'; /* 业务获取私有凭据详情，需要使用凭据的唯一标识符，此处省略 */
try {
  certificateManager.getPrivateCertificate(uri).then((cmResult) => {
    if (cmResult?.credential == undefined) {
      console.info('The result of getting private certificate is undefined.');
    } else {
      let list = cmResult.credential;
      console.info('Succeeded in getting private certificate.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get private certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get private certificate. Code: ${error.code}, message: ${error.message}`);
}

```

