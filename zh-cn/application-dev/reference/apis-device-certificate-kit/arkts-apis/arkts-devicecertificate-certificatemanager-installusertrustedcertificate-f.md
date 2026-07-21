# installUserTrustedCertificate

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

<a id="installusertrustedcertificate"></a>
## installUserTrustedCertificate

```TypeScript
function installUserTrustedCertificate(certificate: CertBlob) : Promise<CMResult>
```

安装用户CA证书。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_ENTERPRISE_USER_TRUSTED_CERT or ohos.permission.ACCESS_USER_TRUSTED_CERT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-certificateManager-function installUserTrustedCertificate(certificate: CertBlob) : Promise<CMResult>--><!--Device-certificateManager-function installUserTrustedCertificate(certificate: CertBlob) : Promise<CMResult>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| certificate | [CertBlob](arkts-devicecertificate-certificatemanager-certblob-i.md) | 是 | 表示证书信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMResult&gt; | Promise对象，返回安装用户CA证书的结果，返回值为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的uri属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.<br>The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter verification failed. Possible causes:<br>the certData parameter is empty or exceeds the maximum length . |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500003](../errorcode-certManager.md#17500003-证书或凭据无效) | Indicates that the certificate is in an invalid format. |
| [17500004](../errorcode-certManager.md#17500004-证书或凭据数量达到上限) | Indicates that the number of certificates reaches the maximum allowed. |
| [17500007](../errorcode-certManager.md#17500007-设备进入坚盾守护模式) | Indicates that the device enters advanced security mode.<br>In this mode, the user CA certificate cannot be installed. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* 安装的CA证书数据需要业务赋值，本例数据非CA证书数据 */
let certData: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
try {
  let certBlob: certificateManager.CertBlob = {
    certData: certData,
    certFormat: certificateManager.CertFileFormat.PEM_DER,
    certScope: certificateManager.CertScope.CURRENT_USER
  };
  certificateManager.installUserTrustedCertificate(certBlob).then((cmResult) => {
    let uri: string = cmResult.uri ?? '';
    console.info('Succeeded in installing user trusted certificate.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to install user trusted certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to install user trusted certificate. Code: ${error.code}, message: ${error.message}`);
}

```

