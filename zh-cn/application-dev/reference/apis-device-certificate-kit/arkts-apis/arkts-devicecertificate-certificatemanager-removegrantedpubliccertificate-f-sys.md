# removeGrantedPublicCertificate（系统接口）

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## removeGrantedPublicCertificate

```TypeScript
function removeGrantedPublicCertificate(keyUri: string, clientAppUid: number) : Promise<void>
```

移除应用使用用户公共凭据的权限，仅证书管理应用调用。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-certificateManager-function removeGrantedPublicCertificate(keyUri: string, clientAppUid: int) : Promise<void>--><!--Device-certificateManager-function removeGrantedPublicCertificate(keyUri: string, clientAppUid: int) : Promise<void>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyUri | string | 是 | 表示用户公共凭据的唯一标识符。 |
| clientAppUid | number | 是 | 表示应用UID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.<br> The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed.<br> Possible causes: the URI is null or the URI format is wrong. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-证书不存在) | Indicates that the certificate does not exist. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyUri: string = 'test'; /* 用户公共凭据的唯一标识符 */
let clientAppUid: number = 1001; /* 应用UID */
try {
  certificateManager.removeGrantedPublicCertificate(keyUri, clientAppUid).then(() => {
    console.info('Succeeded in removing granted public certificate.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to remove granted public certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to remove granted public certificate. Code: ${error.code}, message: ${error.message}`);
}

```

