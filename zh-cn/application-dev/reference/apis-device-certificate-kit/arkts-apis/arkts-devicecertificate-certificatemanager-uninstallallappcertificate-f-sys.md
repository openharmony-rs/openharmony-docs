# uninstallAllAppCertificate（系统接口）

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## uninstallAllAppCertificate

```TypeScript
function uninstallAllAppCertificate() : Promise<void>
```

卸载所有系统应用凭据和用户公共凭据，仅证书管理应用调用。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL and ohos.permission.ACCESS_SYSTEM_APP_CERT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-certificateManager-function uninstallAllAppCertificate() : Promise<void>--><!--Device-certificateManager-function uninstallAllAppCertificate() : Promise<void>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.<br> The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  certificateManager.uninstallAllAppCertificate().then(() => {
    console.info('Succeeded in uninstalling all app certificates.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to uninstall all app certificates. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to uninstall all app certificates. Code: ${error.code}, message: ${error.message}`);
}

```

