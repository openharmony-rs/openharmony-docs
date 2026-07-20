# getCertificateStorePath

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

<a id="getcertificatestorepath"></a>
## getCertificateStorePath

```TypeScript
function getCertificateStorePath(property: CertStoreProperty): string
```

表示获取证书的存储路径。

**起始版本：** 18

<!--Device-certificateManager-function getCertificateStorePath(property: CertStoreProperty): string--><!--Device-certificateManager-function getCertificateStorePath(property: CertStoreProperty): string-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [CertStoreProperty](arkts-devicecertificate-certificatemanager-certstoreproperty-i.md) | 是 | 表示获取证书存储路径的参数集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示证书的存储路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. For example, CertStoreProperty.certType is set to CA_CERT_USER, but CertStoreProperty.certScope is not specified. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500009](../errorcode-certManager.md#17500009-不支持指定的证书存储路径) | The device does not support the specified certificate storage path,For example, the device outside China does not support the certificate that uses SM algorithm.<br>**适用版本：** 20+ |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

try {
  /* 获取系统CA的存储位置 */
  let property1: certificateManager.CertStoreProperty = {
    certType: certificateManager.CertType.CA_CERT_SYSTEM,
  }
  let systemCAPath = certificateManager.getCertificateStorePath(property1);
  console.info(`Success to get system ca path: ${systemCAPath}`);

  /* 获取当前用户的用户CA存储位置 */
  let property2: certificateManager.CertStoreProperty = {
    certType: certificateManager.CertType.CA_CERT_USER,
    certScope: certificateManager.CertScope.CURRENT_USER,
  }
  let userCACurrentPath = certificateManager.getCertificateStorePath(property2);
  console.info(`Success to get current user's user ca path: ${userCACurrentPath}`);

  /* 获取设备公共的用户CA存储位置 */
  let property3: certificateManager.CertStoreProperty = {
    certType: certificateManager.CertType.CA_CERT_USER,
    certScope: certificateManager.CertScope.GLOBAL_USER,
  }
  let globalCACurrentPath = certificateManager.getCertificateStorePath(property3);
  console.info(`Success to get global user's user ca path: ${globalCACurrentPath}`);

  /* 获取SM算法系统CA的存储位置 */
  let property4: certificateManager.CertStoreProperty = {
    certType: certificateManager.CertType.CA_CERT_SYSTEM,
    certAlg: certificateManager.CertAlgorithm.SM,
  }
  let smSystemCAPath = certificateManager.getCertificateStorePath(property4);
  console.info(`Success to get SM system ca path: ${smSystemCAPath}`);
} catch (error) {
  console.error(`Failed to get store path. Code: ${error.code}, message: ${error.message}`);
}

```

