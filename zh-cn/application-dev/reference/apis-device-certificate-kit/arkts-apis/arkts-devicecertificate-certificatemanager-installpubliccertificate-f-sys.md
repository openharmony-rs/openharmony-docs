# installPublicCertificate（系统接口）

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

<a id="installpubliccertificate"></a>
## installPublicCertificate

```TypeScript
function installPublicCertificate(keystore: Uint8Array, keystorePwd: string) : Promise<CMResult>
```

安装用户的公共凭据，仅证书管理应用调用。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-certificateManager-function installPublicCertificate(keystore: Uint8Array, keystorePwd: string) : Promise<CMResult>--><!--Device-certificateManager-function installPublicCertificate(keystore: Uint8Array, keystorePwd: string) : Promise<CMResult>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keystore | Uint8Array | 是 | 表示带有密钥对和证书的密钥库文件，仅支持P12格式。 |
| keystorePwd | string | 是 | 表示密钥库文件的密码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMResult&gt; | Promise对象，返回安装用户公共凭据的结果，返回值为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的uri属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.<br>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter verification failed. Possible causes:<br>the keystore parameter is empty or exceeds the maximum length. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500003](../errorcode-certManager.md#17500003-证书或凭据无效) | Indicates that the certificate is in an invalid format. |
| [17500004](../errorcode-certManager.md#17500004-证书或凭据数量达到上限) | Indicates that the number of certificates reaches the maximum allowed. |
| [17500008](../errorcode-certManager.md#17500008-密码错误) | Indicates that the password is error. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* 安装的凭据数据需要业务赋值，本例数据非凭据数据。 */
let keystore: Uint8Array = new Uint8Array([
    0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
let keystorePwd: string = "123456";
try {
  certificateManager.installPublicCertificate(keystore, keystorePwd).then((cmResult: certificateManager.CMResult) => {
    let uri: string = (cmResult?.uri == undefined) ? '' : cmResult.uri;
    console.info('Succeeded in installing public certificate.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to install public certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to install public certificate. Code: ${error.code}, message: ${error.message}`);
}

```

