# installPrivateCertificate

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

<a id="installprivatecertificate"></a>
## installPrivateCertificate

```TypeScript
function installPrivateCertificate(
    keystore: Uint8Array,
    keystorePwd: string,
    certAlias: string,
    callback: AsyncCallback<CMResult>
  ): void
```

安装私有凭据。使用Callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function installPrivateCertificate(
    keystore: Uint8Array,
    keystorePwd: string,
    certAlias: string,
    callback: AsyncCallback<CMResult>
  ): void--><!--Device-certificateManager-function installPrivateCertificate(
    keystore: Uint8Array,
    keystorePwd: string,
    certAlias: string,
    callback: AsyncCallback<CMResult>
  ): void-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keystore | Uint8Array | 是 | 表示带有密钥对和证书的密钥库文件，* <br>最大长度为20480字节。 |
| keystorePwd | string | 是 | 表示密钥库文件的密码，长度限制32字节以内。 |
| certAlias | string | 是 | 表示用户输入的凭据别名，当前仅支持传入数字、字母或下划线，长度建议32字节以内。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;CMResult&gt; | 是 | 回调函数。当安装私有凭据成功时，err为null，data为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的uri属性；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500003](../errorcode-certManager.md#17500003-证书或凭据无效) | The keystore is in an invalid format or the keystore password is incorrect. |
| [17500004](../errorcode-certManager.md#17500004-证书或凭据数量达到上限) | The number of certificates or credentials reaches the maximum allowed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

/* 安装的凭据数据需要业务赋值，本例数据非凭据数据 */
let keystore: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
let keystorePwd: string = "123456";
try {
  certificateManager.installPrivateCertificate(keystore, keystorePwd, "test", (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to install private certificate. Code: ${err.code}, message: ${err.message}`);
    } else {
      let uri: string = cmResult?.uri ?? '';
      console.info('Succeeded in installing private certificate.');
    }
  });
} catch (error) {
  console.error(`Failed to install private certificate. Code: ${error.code}, message: ${error.message}`);
}

```


<a id="installprivatecertificate-1"></a>
## installPrivateCertificate

```TypeScript
function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string): Promise<CMResult>
```

安装私有凭据。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string): Promise<CMResult>--><!--Device-certificateManager-function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string): Promise<CMResult>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keystore | Uint8Array | 是 | 表示带有密钥对和证书的密钥库文件，<br>最大长度为20480字节。 |
| keystorePwd | string | 是 | 表示密钥库文件的密码，长度限制32字节以内。 |
| certAlias | string | 是 | 表示用户输入的凭据别名，当前仅支持传入数字、字母或下划线，长度建议32字节以内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMResult&gt; | Promise对象，返回安装私有凭据的结果，返回值为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的uri属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500003](../errorcode-certManager.md#17500003-证书或凭据无效) | The keystore is in an invalid format or the keystore password is incorrect. |
| [17500004](../errorcode-certManager.md#17500004-证书或凭据数量达到上限) | The number of certificates or credentials reaches the maximum allowed.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* 安装的凭据数据需要业务赋值，本例数据非凭据数据 */
let keystore: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
let keystorePwd: string = "123456";
try {
  certificateManager.installPrivateCertificate(keystore, keystorePwd, 'test').then((cmResult) => {
    let uri: string = cmResult?.uri ?? '';
    console.info('Succeeded in installing private certificate.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to install private certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to install private certificate. Code: ${error.code}, message: ${error.message}`);
}

```


<a id="installprivatecertificate-2"></a>
## installPrivateCertificate

```TypeScript
function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, level: AuthStorageLevel): Promise<CMResult>
```

表示安装私有凭据并指定凭据的存储级别。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, level: AuthStorageLevel): Promise<CMResult>--><!--Device-certificateManager-function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, level: AuthStorageLevel): Promise<CMResult>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keystore | Uint8Array | 是 | 表示带有密钥对和证书的密钥库文件，最大长度为20480字节。 |
| keystorePwd | string | 是 | 表示密钥库文件的密码。<br>长度限制：32字节以内。 |
| certAlias | string | 是 | 表示用户输入的凭据别名，当前仅支持传入数字、字母或下划线。<br>长度建议：32字节以内。 |
| level | [AuthStorageLevel](arkts-devicecertificate-certificatemanager-authstoragelevel-e.md) | 是 | 表示凭据的存储级别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMResult&gt; | Promise对象，返回安装私有凭据的结果，返回值为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的uri属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500003](../errorcode-certManager.md#17500003-证书或凭据无效) | The keystore is in an invalid format or the keystore password is incorrect. |
| [17500004](../errorcode-certManager.md#17500004-证书或凭据数量达到上限) | The number of certificates or credentials reaches the maximum allowed. |

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
  /* 安装凭据在首次解锁设备后可以使用。 */
  let level = certificateManager.AuthStorageLevel.EL2;
  certificateManager.installPrivateCertificate(keystore, keystorePwd, 'test', level).then((cmResult) => {
    let uri: string = cmResult.uri ?? '';
    console.info('Succeeded in installing private certificate.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to install private certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to install private certificate. Code: ${error.code}, message: ${error.message}`);
}

```

