# getAllUserTrustedCertificates

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

<a id="getallusertrustedcertificates"></a>
## getAllUserTrustedCertificates

```TypeScript
function getAllUserTrustedCertificates(): Promise<CMResult>
```

表示获取当前用户和设备公共位置的所有用户根CA证书列表。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function getAllUserTrustedCertificates(): Promise<CMResult>--><!--Device-certificateManager-function getAllUserTrustedCertificates(): Promise<CMResult>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMResult&gt; | Promise对象，返回获取用户根CA证书列表的结果，返回值为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的certList属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  certificateManager.getAllUserTrustedCertificates().then((cmResult) => {
    if (cmResult === undefined) { // 用户根CA证书个数为0时，返回cmResult为undefined。
      console.info('The count of the user trusted certificates is 0.');
    } else if (cmResult.certList == undefined) {
      console.info('The result of getting all user trusted certificates is undefined.');
    } else {
      let list = cmResult.certList;
      console.info('Succeeded in getting all user trusted certificates.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get all user trusted certificates. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get all user trusted certificates. Code: ${error.code}, message: ${error.message}`);
}

```


<a id="getallusertrustedcertificates-1"></a>
## getAllUserTrustedCertificates

```TypeScript
function getAllUserTrustedCertificates(scope: CertScope): Promise<CMResult>
```

表示根据证书的位置获取用户根CA证书列表。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function getAllUserTrustedCertificates(scope: CertScope): Promise<CMResult>--><!--Device-certificateManager-function getAllUserTrustedCertificates(scope: CertScope): Promise<CMResult>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scope | [CertScope](arkts-devicecertificate-certificatemanager-certscope-e.md) | 是 | 表示证书的位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMResult&gt; | Promise对象，返回获取用户根CA证书列表的结果，返回值为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的certList属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  /* 获取当前用户下的用户根CA证书列表; 如果需要获取设备公共位置的用户根CA列表，则传入GLOBAL_USER */
  let scope: certificateManager.CertScope = certificateManager.CertScope.CURRENT_USER;
  certificateManager.getAllUserTrustedCertificates(scope).then((cmResult) => {
    if (cmResult === undefined) { // 用户根CA证书个数为0时，返回cmResult为undefined。
      console.info('The count of the user trusted certificates is 0.');
    } else if (cmResult.certList == undefined) {
      console.info('The result of getting current user trusted certificates is undefined.');
    } else {
      let list = cmResult.certList;
      console.info('Succeeded in getting current user trusted certificates.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get current user trusted certificates. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get current user trusted certificates. Code: ${error.code}, message: ${error.message}`);
}

```

