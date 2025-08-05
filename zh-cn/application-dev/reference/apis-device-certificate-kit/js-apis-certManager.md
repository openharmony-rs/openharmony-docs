# @ohos.security.certManager (证书管理模块)

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @chaceli-->
<!--SE: @chande-->
<!--TSE: @zhangzhi1995-->

证书管理主要提供系统级的证书管理能力，实现证书全生命周期（安装，存储，使用，销毁）的管理和安全使用。

> **说明：**
>
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## CmKeyPurpose

表示密钥使用目的的枚举，用于签名、验签。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称       | 值 |  说明      |
| ---------- | ------ | --------- |
| CM_KEY_PURPOSE_SIGN | 4      | 签名。 |
| CM_KEY_PURPOSE_VERIFY | 8      | 验签。 |

## CmKeyDigest

表示签名、验签使用的摘要算法的枚举。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称       | 值 |  说明      |
| ---------- | ------ | --------- |
| CM_DIGEST_NONE | 0      | 不需要摘要算法，选用此项时，需要业务传入已经计算过摘要的数据进行签名、验签。 |
| CM_DIGEST_MD5 | 1      | MD5摘要算法。 |
| CM_DIGEST_SHA1 | 2      | SHA1摘要算法。 |
| CM_DIGEST_SHA224 | 3      | SHA224摘要算法。 |
| CM_DIGEST_SHA256 | 4      | SHA256摘要算法。 |
| CM_DIGEST_SHA384 | 5      | SHA384摘要算法。 |
| CM_DIGEST_SHA512 | 6      | SHA512摘要算法。 |
| CM_DIGEST_SM3<sup>18+</sup> | 7 | SM3摘要算法。 |

## CmKeyPadding

表示签名、验签使用的填充方式的枚举。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称       | 值 |  说明      |
| ---------- | ------ | --------- |
| CM_PADDING_NONE | 0      | 无填充。 |
| CM_PADDING_PSS | 1      | PSS方式填充。 |
| CM_PADDING_PKCS1_V1_5 | 2      | PKCS1_V1_5方式填充。 |

## CMSignatureSpec

表示签名、验签操作使用的参数集合，包括密钥使用目的、填充方式和摘要算法。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称           | 类型                              | 只读 | 可选 | 说明                                                         |
| -------------- | --------------------------------- | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| purpose          | [CmKeyPurpose](#cmkeypurpose)                       | 否  | 否  | 表示密钥使用目的的枚举。 |
| padding        | [CmKeyPadding](#cmkeypadding)                       | 否   | 是  | 表示填充方式的枚举。 |
| digest        | [CmKeyDigest](#cmkeydigest)                       | 否   | 是  | 表示摘要算法的枚举。 |


## CertInfo

表示证书详细信息。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称           | 类型                              | 只读 | 可选 | 说明                                                         |
| -------------- | --------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| uri          | string         | 否   | 否  | 表示证书的唯一标识符，最大长度为256字节。 |
| certAlias          | string   | 否  | 否  | 表示证书的别名，最大长度为128字节。 |
| state          | boolean     | 否  | 否  | 表示证书的状态，true为启用状态、false为禁用状态。 |
| issuerName          | string         | 否  | 否  | 表示证书的颁发者名称，最大长度为256字节。 |
| subjectName          | string   | 否  | 否  | 表示证书的使用者名称，最大长度为1024字节。 |
| serial          | string     | 否  | 否  | 表示证书的序列号，最大长度为64字节。 |
| notBefore          | string         | 否  | 否  | 表示证书有效期起始日期，最大长度为32字节。 |
| notAfter          | string   | 否  | 否  | 表示证书有效期截止日期，最大长度为32字节。 |
| fingerprintSha256     | string     | 否  | 否  | 表示证书的指纹值，最大长度为128字节。 |
| cert          | Uint8Array         | 否  | 否  | 表示证书二进制数据，最大长度为8196字节。 |

## CertAbstract

表示证书简要信息。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称           | 类型                              | 只读 | 可选 | 说明                                                         |
| -------------- | --------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| uri          | string         | 否  | 否  | 表示证书的唯一标识符，最大长度为256字节。 |
| certAlias          | string   | 否  | 否  | 表示证书的别名，最大长度为128字节。 |
| state          | boolean     | 否  | 否  | 表示证书的状态，true为启用状态、false为禁用状态。 |
| subjectName          | string   | 否  | 否  | 表示证书的使用者名称，最大长度为1024字节。 |

## Credential

表示凭据详细信息。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称           | 类型                              | 只读 | 可选 | 说明                                                         |
| -------------- | --------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| type          | string         | 否  | 否  | 表示凭据的类型，最大长度为8字节。 |
| alias          | string   | 否  | 否  | 表示凭据的别名，最大长度为128字节。 |
| keyUri          | string     | 否  | 否  | 表示凭据的唯一标识符，最大长度为256字节。 |
| certNum          | number         | 否  | 否  | 表示凭据中包含的证书个数。 |
| keyNum          | number   | 否  | 否  | 表示凭据中包含的密钥个数。 |
| credentialData          | Uint8Array   | 否  | 否  | 表示凭据二进制数据，最大长度为24588字节。 |

## CredentialAbstract

表示凭据的简要信息。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称           | 类型                              | 只读 | 可选 | 说明                                                         |
| -------------- | --------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| type          | string         | 否 | 否  | 表示凭据的类型，最大长度为8字节。 |
| alias          | string   | 否  | 否  | 表示凭据的别名，最大长度为128字节。 |
| keyUri          | string     | 否  | 否  | 表示凭据的唯一标识符，最大长度为256字节。 |

## CMResult

表示接口的返回结果。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称           | 类型                              | 只读 | 可选 | 说明                                                         |
| -------------- | --------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| certList          | Array<[CertAbstract](#certabstract)> | 否  | 是   | 表示证书简要信息的列表。 |
| certInfo          | [CertInfo](#certinfo) | 否  | 是   | 表示证书详情。 |
| credentialList          | Array<[CredentialAbstract](#credentialabstract)> | 否  | 是   | 表示凭据简要信息的列表。 |
| credential         | [Credential](#credential) | 否  | 是   | 表示凭据详情。 |
| appUidList        | Array\<string>     | 否  | 是   | 表示授权应用列表。 |
| uri         | string    | 否  | 是   | 表示证书或凭据的唯一标识符，最大长度为256字节。 |
| outData         | Uint8Array    | 否  | 是   | 表示签名结果。 |

## CMHandle

表示签名、验签的初始化操作句柄。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称           | 类型                              | 只读 | 可选 | 说明                                                         |
| -------------- | --------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| handle         | Uint8Array        | 否  | 否   | 签名、验签的初始化操作句柄，最大长度为8字节。 |

## CMErrorCode

表示调用证书管理相关API的错误码。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称       | 值 |  说明      |
| ---------- | ------ | --------- |
| CM_ERROR_NO_PERMISSION   | 201      | 表示应用程序无权限调用接口。 |
| CM_ERROR_INVALID_PARAMS   | 401      | 表示输入参数无效。 |
| CM_ERROR_GENERIC  | 17500001      | 表示调用接口时发生内部错误。 |
| CM_ERROR_NO_FOUND  | 17500002      | 表示证书或凭据不存在。 |
| CM_ERROR_INCORRECT_FORMAT  | 17500003      | 表示输入证书或凭据的数据格式无效。 |
| CM_ERROR_MAX_CERT_COUNT_REACHED<sup>12+</sup>  | 17500004      | 表示证书或凭据数量达到上限。 |
| CM_ERROR_NO_AUTHORIZATION<sup>12+</sup>  | 17500005      | 表示应用未经用户授权。 |
| CM_ERROR_DEVICE_ENTER_ADVSECMODE<sup>18+</sup> | 17500007 | 表示设备进入坚盾守护模式。 |
| CM_ERROR_STORE_PATH_NOT_SUPPORTED<sup>20+</sup> | 17500009 | 表示不支持指定的证书存储路径。   |

## CertType<sup>18+</sup>

表示证书类型。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称       | 值 |  说明      |
| ---------- | ------ | --------- |
| CA_CERT_SYSTEM   | 0      | 表示系统CA证书。 |
| CA_CERT_USER   | 1      | 表示用户CA证书。 |

## CertScope<sup>18+</sup>

表示证书的位置。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称       | 值 |  说明      |
| ---------- | ------ | --------- |
| CURRENT_USER   | 1      | 表示当前用户。 |
| GLOBAL_USER   | 2      | 表示设备公共，即所有用户都可以访问的位置。 |

## CertAlgorithm<sup>20+</sup>

表示证书的算法类型。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称            | 值 | 说明                       |
|---------------| ------ |--------------------------|
| INTERNATIONAL | 1      | 表示国际密码算法，如RSA、NIST ECC等。 |
| SM            | 2      | 表示商用密码算法，如SM2、SM4等。      |

## CertStoreProperty<sup>18+</sup>

表示获取证书存储位置的参数集合，包括证书的类型及证书的位置。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称        | 类型                                | 只读 | 可选 | 说明                                          |
|-----------|-----------------------------------| ---- | ------------------------------------------------------------ |---------------------------------------------|
| certType  | [CertType](#certtype18)           | 否  | 否  | 表示证书的类型。                                    |
| certScope | [CertScope](#certscope18)         | 否   | 是  | 表示证书的存储位置。当证书类型为CA_CERT_USER时，此项为必选项。       |
| certAlg<sup>20+</sup>   | [CertAlgorithm](#certalgorithm20) | 否   | 是  | 表示证书算法类型。仅当certType为CA_CERT_SYSTEM时有效，默认值为INTERNATIONAL。 |

## AuthStorageLevel<sup>18+</sup>

表示凭据的存储级别。

**系统能力：** SystemCapability.Security.CertificateManager

| 名称         | 值   | 说明                                       |
| ------------ | ---- | ------------------------------------------ |
| EL1  | 1    | EL1级别，表示设备启动后可以访问。               |
| EL2  | 2    | EL2级别，表示设备首次解锁后可以访问。           |
| EL4  | 4    | EL4级别，表示设备解锁时可以访问。             |

## certificateManager.installPrivateCertificate

installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, callback: AsyncCallback\<CMResult>): void

表示安装私有凭据，使用Callback回调异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| keystore | Uint8Array                   | 是   | 表示带有密钥对和证书的密钥库文件，最大长度为20480字节。 |
| keystorePwd | string | 是   | 表示密钥库文件的密码，长度限制32字节以内。 |
| certAlias | string | 是   | 表示用户输入的凭据别名，当前仅支持传入数字、字母或下划线，长度建议32字节以内。 |
| callback | AsyncCallback\<[CMResult](#cmresult)> | 是   | 回调函数。当安装私有凭据成功时，err为null，data为[CMResult](#cmresult)对象中的uri属性；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.     |
| 17500003 | The keystore is in an invalid format or the keystore password is incorrect. |
| 17500004 | The number of certificates or credentials reaches the maximum allowed. |

**示例**：
```ts
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
      let uri: string = (cmResult?.uri == undefined) ? '' : cmResult.uri;
      console.info('Succeeded in installing private certificate.');
    }
  });
} catch (error) {
  console.error(`Failed to install private certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.installPrivateCertificate

installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string): Promise\<CMResult>

表示安装私有凭据，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| keystore | Uint8Array                   | 是   | 表示带有密钥对和证书的密钥库文件，最大长度为20480字节。 |
| keystorePwd | string | 是   | 表示密钥库文件的密码，长度限制32字节以内。 |
| certAlias | string | 是   | 表示用户输入的凭据别名，当前仅支持传入数字、字母或下划线，长度建议32字节以内。 |

**返回值**：

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](#cmresult)> | Promise对象。表示安装私有凭据的结果，返回值为[CMResult](#cmresult)对象中的uri属性。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.     |
| 17500003 | The keystore is in an invalid format or the keystore password is incorrect. |
| 17500004 | The number of certificates or credentials reaches the maximum allowed. |

**示例**：

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* 安装的凭据数据需要业务赋值，本例数据非凭据数据 */
let keystore: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
let keystorePwd: string = "123456";
try {
  certificateManager.installPrivateCertificate(keystore, keystorePwd, 'test').then((cmResult) => {
    let uri: string = (cmResult?.uri == undefined) ? '' : cmResult.uri;
    console.info('Succeeded in installing private certificate.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to install private certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to install private certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.installPrivateCertificate<sup>18+</sup>

installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, level: AuthStorageLevel): Promise\<CMResult>

表示安装私有凭据并指定凭据的存储级别。使用Promise异步回调。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名      | 类型       | 必填 | 说明                                                         |
| ----------- | ---------- | ---- | ------------------------------------------------------------ |
| keystore    | Uint8Array | 是   | 表示带有密钥对和证书的密钥库文件，最大长度为20480字节。                           |
| keystorePwd | string     | 是   | 表示密钥库文件的密码。<br>长度限制：32字节以内。                   |
| certAlias   | string     | 是   | 表示用户输入的凭据别名，当前仅支持传入数字、字母或下划线。<br>长度建议：32字节以内。 |
| level   | [AuthStorageLevel](#authstoragelevel18)   | 是   | 表示凭据的存储级别。 |

**返回值：**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](#cmresult)> | Promise对象。表示安装私有凭据的结果，返回值为[CMResult](#cmresult)对象中的uri属性。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID               | 错误信息                                                     |
| ---------------------- | ------------------------------------------------------------ |
| 201                    | Permission verification failed. The application does not have the permission required to call the API. |
| 401                    | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.                                              |
| 17500003               | The keystore is in an invalid format or the keystore password is incorrect. |
| 17500004               | The number of certificates or credentials reaches the maximum allowed. |

**示例：**

```ts
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
    let uri: string = (cmResult?.uri == undefined) ? '' : cmResult.uri;
    console.info('Succeeded in installing private certificate.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to install private certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to install private certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getPrivateCertificate

getPrivateCertificate(keyUri: string, callback: AsyncCallback\<CMResult>): void

表示获取私有凭据的详细信息，使用Callback回调异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| keyUri | string                   | 是   | 表示待获取凭据的唯一标识符，长度限制256字节以内。 |
| callback | AsyncCallback\<[CMResult](#cmresult)> | 是   | 回调函数。当获取私有凭据的详细信息成功时，err为null，data为[CMResult](#cmresult)对象中的credential属性；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |
| 17500002 | The certificate does not exist. |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';

let uri: string = 'test'; /* 业务安装凭据，返回唯一标识符，此处省略 */
try {
  certificateManager.getPrivateCertificate(uri, (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to get private certificate. Code: ${err.code}, message: ${err.message}`);
    } else {
      if (cmResult?.credential == undefined) {
        console.info('The result of getting private certificate is undefined.');
      } else {
        let list = cmResult.credential;
        console.info('Succeeded in getting private certificate.');
      }
    }
  });
} catch (error) {
  console.error(`Failed to get private certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getPrivateCertificate

getPrivateCertificate(keyUri: string): Promise\<CMResult>

表示获取私有凭据详情，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| keyUri | string                   | 是   | 表示待获取凭据的唯一标识符，长度限制256字节以内。 |

**返回值**：

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](#cmresult)> | Promise对象。表示获取私有凭据详细信息的结果，返回值为[CMResult](#cmresult)对象中的credential属性。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |
| 17500002 | The certificate does not exist. |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri: string = 'test'; /* 业务安装凭据，返回唯一标识符，此处省略 */
try {
  certificateManager.getPrivateCertificate(uri).then((cmResult) => {
    if (cmResult?.credential == undefined) {
      console.info('The result of getting private certificate is undefined.');
    } else {
      let list = cmResult.credential;
      console.info('Succeeded in getting private certificate.');
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get private certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get private certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.uninstallPrivateCertificate

uninstallPrivateCertificate(keyUri: string, callback: AsyncCallback\<void>): void

表示卸载指定的私有凭据，使用Callback回调异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| keyUri | string                   | 是   | 表示待卸载凭据的唯一标识符，长度限制256字节以内。 |
| callback | AsyncCallback\<void> | 是   | 回调函数。当卸载私有凭据成功时，err为null，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |
| 17500002 | The certificate does not exist. |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';

let uri: string = 'test'; /* 业务安装凭据，返回唯一标识符，此处省略 */
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

## certificateManager.uninstallPrivateCertificate

uninstallPrivateCertificate(keyUri: string): Promise\<void>

表示卸载指定的私有凭据，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| keyUri | string                   | 是   | 表示待卸载凭据的唯一标识符，长度限制256字节以内。 |

**返回值**：

| 类型                                        | 说明                 |
| ------------------------------------------- | -------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |
| 17500002 | The certificate does not exist. |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri: string = 'test'; /* 业务安装凭据，返回唯一标识符，此处省略 */
try {
  certificateManager.uninstallPrivateCertificate(uri).then((cmResult) => {
    console.info('Succeeded in uninstalling private certificate.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to uninstall private certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to uninstall private certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.installUserTrustedCertificateSync<sup>18+</sup>

installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope) : CMResult

表示安装用户CA证书。

**需要权限：** ohos.permission.ACCESS_ENTERPRISE_USER_TRUSTED_CERT<!--Del-->或ohos.permission.ACCESS_USER_TRUSTED_CERT<!--DelEnd-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名       | 类型                         | 必填 | 说明           |
|-----------|----------------------------|----|--------------|
| cert      | Uint8Array                 | 是  | 表示CA证书数据，最大长度为8196字节。    |
| certScope | [CertScope](#certscope18)  | 是  | 表示CA证书安装的位置。 |

**返回值**：

| 类型                    | 说明                                |
|-----------------------|-----------------------------------|
| [CMResult](#cmresult) | 表示CA证书的安装结果，返回值CMResult对象中的uri属性。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID                  | 错误信息                                                                                                                                            |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API.                                          |
| 401                    | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.                                                                                                                                 |
| 17500003               | Indicates that the certificate is in an invalid format.                                                                                         |
| 17500004               | Indicates that the number of certificates reaches the maximum allowed.                                                                          |
| 17500007               | Indicates that the device enters advanced security mode. In this mode, the user CA certificate cannot be installed.                             |

**示例**：

```ts
import {certificateManager} from '@kit.DeviceCertificateKit';

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
        console.info("Successed to install user trusted certificate.");
    }
} catch (error) {
    console.error(`Failed to install user trusted certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.uninstallUserTrustedCertificateSync<sup>18+</sup>

uninstallUserTrustedCertificateSync(certUri: string) : void

表示删除用户CA证书。

**需要权限：** ohos.permission.ACCESS_ENTERPRISE_USER_TRUSTED_CERT<!--Del-->或ohos.permission.ACCESS_USER_TRUSTED_CERT<!--DelEnd-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名       | 类型                         | 必填 | 说明           |
|-----------|----------------------------|----|--------------|
| certUri     | string                 | 是  | 表示待卸删除证书的唯一标识符，长度限制256字节以内。    |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID                  | 错误信息                                                                                                                                            |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API.                                          |
| 401                    | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.                                                                                                                                 |
| 17500002               | Indicates that the certificate does not exist.                                                                                                  |

**示例**：

```ts
import {certificateManager} from '@kit.DeviceCertificateKit';

let certUri: string = "test"; /* 业务安装证书，返回唯一标识符，此处省略 */
try {
    certificateManager.uninstallUserTrustedCertificateSync(certUri);
} catch (error) {
    console.error(`Failed to uninstall user trusted certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.init

init(authUri: string, spec: CMSignatureSpec, callback: AsyncCallback\<CMHandle>): void

表示使用凭据进行签名、验签的初始化操作，使用Callback回调异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| authUri | string                   | 是   | 表示使用凭据的唯一标识符，长度限制256字节以内。 |
| spec | [CMSignatureSpec](#cmsignaturespec) | 是   | 表示签名、验签的属性。 |
| callback | AsyncCallback\<[CMHandle](#cmhandle)> | 是   | 回调函数。当签名、验签的初始化操作成功时，err为null，data为获取到的CMHandle；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |
| 17500002 | The certificate does not exist. |
| 17500005<sup>12+</sup> | The application is not authorized by the user. |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';

let uri: string = 'test'; /* 业务安装凭据，返回唯一标识符，此处省略 */
const req: certificateManager.CMSignatureSpec = {
  purpose: certificateManager.CmKeyPurpose.CM_KEY_PURPOSE_SIGN,
  padding: certificateManager.CmKeyPadding.CM_PADDING_PSS,
  digest: certificateManager.CmKeyDigest.CM_DIGEST_SHA256
}
try {
  certificateManager.init(uri, req, (err, cmHandle) => {
    if (err != null) {
      console.error(`Failed to init. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in initiating.');
    }
  })
} catch (error) {
  console.error(`Failed to init. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.init

init(authUri: string, spec: CMSignatureSpec): Promise\<CMHandle>

表示使用凭据进行签名、验签的初始化操作，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| authUri | string                   | 是   | 表示使用凭据的唯一标识符，长度限制256字节以内。 |
| spec | [CMSignatureSpec](#cmsignaturespec) | 是   | 表示签名、验签的属性。 |

**返回值**：

| 类型                                        | 说明                 |
| ------------------------------------------- | -------------------- |
| Promise\<[CMHandle](#cmhandle)> | Promise对象。表示签名、验签的初始化操作结果，返回CMHandle对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |
| 17500002 | The certificate does not exist. |
| 17500005<sup>12+</sup> | The application is not authorized by the user. |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri: string = 'test'; /* 业务安装凭据，返回唯一标识符，此处省略 */
const req: certificateManager.CMSignatureSpec = {
  purpose: certificateManager.CmKeyPurpose.CM_KEY_PURPOSE_VERIFY,
  padding: certificateManager.CmKeyPadding.CM_PADDING_PSS,
  digest: certificateManager.CmKeyDigest.CM_DIGEST_MD5
}
try {
  certificateManager.init(uri, req).then((handle) => {
    console.info('Succeeded in initiating.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to init. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to init. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.update

update(handle: Uint8Array, data: Uint8Array, callback: AsyncCallback\<void>): void

表示签名、验签的数据更新操作，使用Callback回调异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| handle | Uint8Array                   | 是   | 表示初始化操作返回的句柄，最大长度为8字节。 |
| data | Uint8Array                   | 是   | 表示待签名、验签的数据。 |
| callback | AsyncCallback\<void> | 是   | 回调函数。当签名、验签的数据更新操作成功时，err为null，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.     |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';

/* cmHandle为业务调用init接口的返回值，此处仅为示例 */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
let srcData: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.update(cmHandle, srcData, (err, result) => {
    if (err != null) {
      console.error(`Failed to update. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in updating.');
    }
  });
} catch (error) {
  console.error(`Failed to update. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.update

update(handle: Uint8Array, data: Uint8Array): Promise\<void>

表示签名、验签的数据更新操作，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| handle | Uint8Array                   | 是   | 表示初始化操作返回的句柄，最大长度为8字节。 |
| data | Uint8Array                   | 是   | 表示待签名、验签的数据。 |

**返回值**：

| 类型                                        | 说明                 |
| ------------------------------------------- | -------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.     |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* cmHandle为业务调用init接口的返回值，此处仅为示例 */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
let srcData: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.update(cmHandle, srcData).then((result) => {
    console.info('Succeeded in updating.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to update. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to update. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.finish

finish(handle: Uint8Array, callback: AsyncCallback\<CMResult>): void

表示完成签名的操作，Callback回调异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| handle | Uint8Array                   | 是   | 表示初始化操作返回的句柄，最大长度为8字节。 |
| callback | AsyncCallback\<[CMResult](#cmresult)> | 是   | 回调函数。当签名成功时，err为null，data为[CMResult](#cmresult)对象中的outData属性，表示签名数据；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.     |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';

/* cmHandle为业务调用init接口的返回值，此处仅为示例 */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.finish(cmHandle, (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to finish. Code: ${err.code}, message: ${err.message}`);
    } else {
      if (cmResult?.outData != undefined) {
        let signRes: Uint8Array = cmResult.outData;
        console.info('Succeeded in finishing.');
      } else {
        console.info('The result of finishing is undefined.');
      }
    }
  });
} catch(error) {
  console.error(`Failed to finish. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.finish

finish(handle: Uint8Array, signature: Uint8Array, callback: AsyncCallback\<CMResult>): void

表示完成验签的操作，使用Callback回调异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| handle | Uint8Array                   | 是   | 表示初始化操作返回的句柄，最大长度为8字节。 |
| signature | Uint8Array                   | 是   | 表示签名数据。 |
| callback | AsyncCallback\<[CMResult](#cmresult)> | 是   | 回调函数。当验签成功时，err为null；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.     |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';

/* cmHandle为业务调用init接口的返回值，此处仅为示例 */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
let signRes: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.finish(cmHandle, signRes, (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to finish. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in finishing.');
    }
  });
} catch(error) {
  console.error(`Failed to finish. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.finish

finish(handle: Uint8Array, signature?: Uint8Array): Promise\<CMResult>

表示完成签名、验签的操作，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| handle | Uint8Array                   | 是   | 表示初始化操作返回的句柄，最大长度为8字节。 |
| signature | Uint8Array                   | 否   | 表示签名数据。 |

**返回值**：

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](#cmresult)> | Promise对象。执行签名操作时，表示签名的结果，返回值为[CMResult](#cmresult)对象中的outData属性；执行验签操作时，无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.     |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* cmHandle为业务调用init接口的返回值，此处仅为示例 */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  /* 签名的finish操作 */
  certificateManager.finish(cmHandle).then((cmResult) => {
    if (cmResult?.outData != undefined) {
      let signRes1: Uint8Array = cmResult.outData;
      console.info('Succeeded in finishing signature.');
    } else {
      console.info('The result of signature is undefined.');
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to finish signature. Code: ${err.code}, message: ${err.message}`);
  })

  /* 签名的结果 */
  let signRes: Uint8Array = new Uint8Array([
    0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
  ]);
  /* 验签的finish操作 */
  certificateManager.finish(cmHandle, signRes).then((cmResult) => {
    console.info('Succeeded in finishing verification.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to finish verification. Code: ${err.code}, message: ${err.message}`);
  })
} catch(error) {
  console.error(`Failed to finish. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.abort

abort(handle: Uint8Array, callback: AsyncCallback\<void>): void

表示中止签名、验签的操作，使用Callback回调异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| handle | Uint8Array                   | 是   | 表示初始化操作返回的句柄，最大长度为8字节。 |
| callback | AsyncCallback\<void> | 是   | 回调函数。当中止签名、验签成功时，err为null，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.     |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';

/* cmHandle为业务调用init接口的返回值，此处仅为示例 */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.abort(cmHandle, (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to abort. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in aborting.');
    }
  });
} catch(error) {
  console.error(`Failed to abort. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.abort

abort(handle: Uint8Array): Promise\<void>

表示中止签名、验签的操作，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| handle | Uint8Array                   | 是   | 表示初始化操作返回的句柄，最大长度为8字节。 |

**返回值**：

| 类型                                        | 说明                 |
| ------------------------------------------- | -------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.     |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* cmHandle为业务调用init接口的返回值，此处仅为示例 */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.abort(cmHandle).then((result) => {
    console.info('Succeeded in aborting.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to abort. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to abort. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getPublicCertificate<sup>12+</sup>

getPublicCertificate(keyUri: string): Promise\<CMResult>

表示获取用户公共凭据的详细信息，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| keyUri | string                   | 是   | 表示用户公共凭据的唯一标识符，长度限制256字节以内。 |

**返回值**：

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](#cmresult)> | Promise对象。表示获取用户公共凭据详细信息的结果，返回值为[CMResult](#cmresult)对象中的credential属性。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |
| 17500002 | The certificate does not exist. |
| 17500005 | The application is not authorized by the user. |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri: string = 'test'; /* 用户安装公共凭据返回的唯一标识符，此处省略 */
try {
  certificateManager.getPublicCertificate(uri).then((cmResult) => {
    if (cmResult?.credential == undefined) {
      console.info('The result of getting public certificate is undefined.');
    } else {
      let cred = cmResult.credential;
      console.info('Succeeded in getting Public certificate.');
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get Public certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get Public certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.isAuthorizedApp<sup>12+</sup>

isAuthorizedApp(keyUri: string): Promise\<boolean>

表示当前应用是否由指定的用户凭据授权，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| keyUri | string                   | 是   | 表示用户授权给应用使用的凭据的唯一标识符，长度限制256字节以内。 |

**返回值**：

| 类型              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| Promise\<boolean> | Promise对象。表示查询应用是否被授权的结果，true为已授权，false为未授权。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri: string = 'test'; /* 用户授权给应用使用的凭据的唯一标识符，此处省略 */
try {
  certificateManager.isAuthorizedApp(uri).then((res) => {
    if (res) {
      console.info('The application is authorized by the user.');
    } else {
      console.info('The application is not authorized by the user.');
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get Public certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get Public certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getAllUserTrustedCertificates<sup>12+</sup>

getAllUserTrustedCertificates(): Promise\<CMResult>

表示获取当前用户和设备公共位置的所有用户根CA证书列表，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**返回值**：

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](#cmresult)> | Promise对象。表示获取用户根CA证书列表的结果，返回值[CMResult](#cmresult)对象中的certList属性。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  certificateManager.getAllUserTrustedCertificates().then((cmResult) => {
    if (cmResult == undefined) { // 用户根CA证书个数为0时，返回cmResult为undefined。
      console.info('the count of the user trusted certificates is 0');
    } else if (cmResult.certList == undefined) {
      console.info('The result of getting all user trusted certificates is undefined.');
    } else {
      let list = cmResult.certList;
      console.info('Succeeded in getting all user trusted certificates.');
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get all user trusted certificates. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get all user trusted certificates. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getAllUserTrustedCertificates<sup>18+</sup>

getAllUserTrustedCertificates(scope: CertScope): Promise\<CMResult>

表示根据证书的位置获取用户根CA证书列表，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名 | 类型                      | 必填 | 说明             |
| ------ | ------------------------- | ---- | ---------------- |
| scope  | [CertScope](#certscope18) | 是   | 表示证书的位置。 |

**返回值**：

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](#cmresult)> | Promise对象。表示获取用户根CA证书列表的结果，返回值[CMResult](#cmresult)对象中的certList属性。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error.                                              |

**示例**：

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  /* 获取当前用户下的用户根CA证书列表; 如果需要获取设备公共位置的用户根CA列表，则传入GLOBAL_USER */
  let scope: certificateManager.CertScope = certificateManager.CertScope.CURRENT_USER;
  certificateManager.getAllUserTrustedCertificates(scope).then((cmResult) => {
    if (cmResult == undefined) { // 用户根CA证书个数为0时，返回cmResult为undefined。
      console.info('the count of the user trusted certificates is 0');
    } else if (cmResult.certList == undefined) {
      console.info('The result of getting current user trusted certificates is undefined.');
    } else {
      let list = cmResult.certList;
      console.info('Succeeded in getting current user trusted certificates.');
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get current user trusted certificates. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get current user trusted certificates. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getUserTrustedCertificate<sup>12+</sup>

getUserTrustedCertificate(certUri: string): Promise\<CMResult>

表示获取用户根CA证书的详细信息，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                              | 必填 | 说明                       |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| certUri | string                   | 是   | 表示用户用户根CA证书的唯一标识符，长度限制256字节以内。 |

**返回值**：

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](#cmresult)> | Promise对象。表示获取用户根CA证书详细信息的结果，返回值为[CMResult](#cmresult)对象中的certInfo属性。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |
| 17500002 | The certificate does not exist. |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let certUri: string = 'testUserCert'; /* 用户安装用户根CA证书返回的唯一标识符，此处省略 */
try {
  certificateManager.getUserTrustedCertificate(certUri).then((cmResult) => {
    if (cmResult?.certInfo == undefined) {
      console.info('The result of getting user trusted certificate is undefined.');
    } else {
      let cert = cmResult.certInfo;
      console.info('Succeeded in getting user trusted certificate.');
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get user trusted certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get user trusted certificate. Code: ${error.code}, message: ${error.message}`);
}
```
## certificateManager.getPrivateCertificates<sup>13+</sup>

getPrivateCertificates(): Promise\<CMResult>

表示获取应用安装的凭据列表，使用Promise方式异步返回结果。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**返回值**：

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](#cmresult)> | Promise对象。表示获取应用安装的凭据列表的结果，返回值[CMResult](#cmresult)对象中的credentialList属性。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |

**示例**：
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  certificateManager.getPrivateCertificates().then((cmResult) => {
    if (cmResult == undefined) { // 应用安装的凭据个数为0时，返回cmResult为undefined。
      console.info('the count of the private certificates is 0');
    } else if (cmResult.credentialList == undefined) {
      console.info('The result of getting all private certificates installed by the application is undefined.');
    } else {
      let list = cmResult.credentialList;
      console.info('Succeeded in getting all private certificates installed by the application.');
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get all private certificates installed by the application. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get all private certificates installed by the application. Code: ${error.code}, message: ${error.message}`);
}
```
## certificateManager.getCertificateStorePath<sup>18+</sup>

getCertificateStorePath(property: CertStoreProperty): string;

表示获取证书的存储路径。

**系统能力：** SystemCapability.Security.CertificateManager

**参数**：

| 参数名   | 类型                                      | 必填 | 说明                             |
| -------- | ----------------------------------------- | ---- | -------------------------------- |
| property | [CertStoreProperty](#certstoreproperty18) | 是   | 表示获取证书存储路径的参数集合。 |

**返回值**：

| 类型   | 说明                 |
| ------ | -------------------- |
| string | 表示证书的存储路径。 |

**错误码：**

以下错误码的详细介绍请参见[证书管理错误码](errorcode-certManager.md)。

| 错误码ID    | 错误信息      |
|----------| ------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |
| 17500009 | The device does not support the specified certificate store path, such as the overseas device does not support the certificate which algorithm is SM. |

**示例**：
```ts
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