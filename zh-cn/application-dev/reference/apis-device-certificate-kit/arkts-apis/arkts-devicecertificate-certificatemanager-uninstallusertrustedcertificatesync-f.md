# uninstallUserTrustedCertificateSync

## uninstallUserTrustedCertificateSync

```TypeScript
function uninstallUserTrustedCertificateSync(certUri: string): void
```

卸载用户CA证书。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ACCESS_ENTERPRISE_USER_TRUSTED_CERT or ohos.permission.ACCESS_USER_TRUSTED_CERT

<!--Device-certificateManager-function uninstallUserTrustedCertificateSync(certUri: string): void--><!--Device-certificateManager-function uninstallUserTrustedCertificateSync(certUri: string): void-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| certUri | string | 是 | 表示待卸载证书的唯一标识符，长度限制256字节以内 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [17500002](../errorcode-certManager.md#17500002-证书不存在) | Indicates that the certificate does not exist. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed; &lt;br&gt;2. Memory operation error; 3. File operation error. Please try again. |

## 示例

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

let certUri: string = "test"; /* 业务删除证书，需要使用证书的标识符，此处省略 */
try {
  certificateManager.uninstallUserTrustedCertificateSync(certUri);
} catch (error) {
  console.error(`Failed to uninstall user trusted certificate. Code: ${error.code}, message: ${error.message}`);
}
```

