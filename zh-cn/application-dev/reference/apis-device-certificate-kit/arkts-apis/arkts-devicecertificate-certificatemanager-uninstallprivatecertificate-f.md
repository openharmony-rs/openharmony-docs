# uninstallPrivateCertificate

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## uninstallPrivateCertificate

```TypeScript
function uninstallPrivateCertificate(keyUri: string, callback: AsyncCallback<void>): void
```

卸载指定的私有凭据，使用Callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function uninstallPrivateCertificate(keyUri: string, callback: AsyncCallback<void>): void--><!--Device-certificateManager-function uninstallPrivateCertificate(keyUri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyUri | string | 是 | 表示待卸载凭据的唯一标识符，长度限制256字节以内。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当卸载私有凭据成功时，err为null，否则为错误对象。 |

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

let uri: string = 'test'; /* 业务删除私有凭据，需要使用凭据的唯一标识符，此处省略 */
try {
  certificateManager.uninstallPrivateCertificate(uri, (err, result) => {
    if (err != null) {
      console.error(`Failed to uninstall private certificate. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in uninstalling private certificate.');
    }
  });
} catch (error) {
  console.error(`Failed to uninstall private certificate. Code: ${error.code}, message: ${error.message}`);
}

```


## uninstallPrivateCertificate

```TypeScript
function uninstallPrivateCertificate(keyUri: string): Promise<void>
```

表示卸载指定的私有凭据。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function uninstallPrivateCertificate(keyUri: string): Promise<void>--><!--Device-certificateManager-function uninstallPrivateCertificate(keyUri: string): Promise<void>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyUri | string | 是 | 表示待卸载凭据的唯一标识符，长度限制256字节以内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

let uri: string = 'test'; /* 业务删除私有凭据，需要使用凭据的唯一标识符，此处省略 */
try {
  certificateManager.uninstallPrivateCertificate(uri).then((cmResult) => {
    console.info('Succeeded in uninstalling private certificate.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to uninstall private certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to uninstall private certificate. Code: ${error.code}, message: ${error.message}`);
}

```

