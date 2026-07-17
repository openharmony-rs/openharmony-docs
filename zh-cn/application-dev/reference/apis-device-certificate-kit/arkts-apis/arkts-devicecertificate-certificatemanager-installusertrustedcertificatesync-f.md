# installUserTrustedCertificateSync

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## installUserTrustedCertificateSync

```TypeScript
function installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope): CMResult
```

安装用户CA证书。

**起始版本：** 18

**需要权限：** ohos.permission.ACCESS_ENTERPRISE_USER_TRUSTED_CERT or ohos.permission.ACCESS_USER_TRUSTED_CERT

<!--Device-certificateManager-function installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope): CMResult--><!--Device-certificateManager-function installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope): CMResult-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cert | [Uint8Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8array-c.md) | 是 | 表示CA证书数据，<br>最大长度为8196字节。 |
| certScope | [CertScope](arkts-devicecertificate-certificatemanager-certscope-e.md) | 是 | 表示CA证书安装的位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) | 表示CA证书的安装结果，返回值为CMResult对象中的uri属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500003](../errorcode-certManager.md#17500003-证书或凭据无效) | Indicates that the certificate is in an invalid format. |
| [17500004](../errorcode-certManager.md#17500004-证书或凭据数量达到上限) | Indicates that the number of certificates reaches the maximum allowed. |
| [17500007](../errorcode-certManager.md#17500007-设备进入坚盾守护模式) | Indicates that the device enters advanced security mode. In this mode, the user CA certificate cannot be installed. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

/* 安装的CA证书数据需要业务赋值，本例数据非CA证书数据 */
let certData: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
try {
  let result: certificateManager.CMResult = certificateManager.installUserTrustedCertificateSync(certData, certificateManager.CertScope.CURRENT_USER);
  let certUri = result.uri;
  if (certUri === undefined) {
    console.error("The result of install user trusted certificate is undefined.");
  } else {
    console.info("Succeeded to install user trusted certificate.");
  }
} catch (error) {
  console.error(`Failed to install user trusted certificate. Code: ${error.code}, message: ${error.message}`);
}

```

