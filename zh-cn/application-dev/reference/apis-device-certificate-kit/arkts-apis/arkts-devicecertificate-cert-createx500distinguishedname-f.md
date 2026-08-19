# createX500DistinguishedName

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { certificateManager } from '@kit.DeviceCertificateKit';
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## createX500DistinguishedName

```TypeScript
function createX500DistinguishedName(nameStr: string): Promise<X500DistinguishedName>
```

表示使用字符串格式的名称创建X500DistinguishedName对象。使用Promise方式返回结果。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-cert-function createX500DistinguishedName(nameStr: string): Promise<X500DistinguishedName>--><!--Device-cert-function createX500DistinguishedName(nameStr: string): Promise<X500DistinguishedName>-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| nameStr | string | 是 | 使用斜杠"/"分隔的可分辨名称字符串格式，每个相对可分辨名称为“属性=值”形式， 常用属性包括CN（通用名）、O（组织名）、OU（组织单位）、C（国家/地区）、ST（省/州）、L（市/区）。 例如：/CN=example.com/O=Example/C=CN。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md)&gt; | Promise对象，返回X500DistinguishedName实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19030002](../errorcode-cert.md#19030002-证书签名验证错误) | The certificate signature verification failed. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19030003](../errorcode-cert.md#19030003-证书尚未生效) | The certificate has not taken effect. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |
| [19030006](../errorcode-cert.md#19030006-证书的密钥用途不含证书签名) | The key cannot be used for signing a certificate. |
| [19030007](../errorcode-cert.md#19030007-证书的密钥用途不含数字签名) | The key cannot be used for a digital signature. |
| [19030004](../errorcode-cert.md#19030004-证书过期) | The certificate has expired. |
| [19030005](../errorcode-cert.md#19030005-无法获取证书的颁发者) | Failed to obtain the certificate issuer. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// string转Uint8Array。
function stringToUint8Array(str: string): Uint8Array {
  let arr: Array<number> = [];
  for (let i = 0, j = str.length; i < j; i++) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

let nameStr = '/CN=John Doe/OU=IT Department/O=ACME Inc./L=San Francisco/ST=California/C=US/CN=ALN C/CN=XTS';
async function createX500DistinguishedName() {
  try {
    cert.createX500DistinguishedName(nameStr)
      .then((_data) => {
        console.info('createX500DistinguishedName result: success.');
      })
      .catch((err: BusinessError) => {
        console.error(`createX500DistinguishedName failed, errCode: ${err.code}, errMsg: ${err.message}`);
      });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX500DistinguishedName failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@ohos.base';

// string转Uint8Array。
function stringToUint8Array(str: string): Uint8Array {
  let arr: Array<number> = [];
  for (let i = 0, j = str.length; i < j; i++) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

let nameStr = '/CN=John Doe/OU=IT Department/O=ACME Inc./L=San Francisco/ST=California/C=US/CN=ALN C/CN=XTS';
async function createX500DistinguishedName() {
  try {
    await cert.createX500DistinguishedName(nameStr);
    console.info('createX500DistinguishedName result: success.');
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX500DistinguishedName catch, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```


## createX500DistinguishedName

```TypeScript
function createX500DistinguishedName(nameDer: Uint8Array): Promise<X500DistinguishedName>
```

表示使用DER格式的名称创建X500DistinguishedName对象。使用Promise方式返回结果。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-cert-function createX500DistinguishedName(nameDer: Uint8Array): Promise<X500DistinguishedName>--><!--Device-cert-function createX500DistinguishedName(nameDer: Uint8Array): Promise<X500DistinguishedName>-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| nameDer | Uint8Array | 是 | DER格式的X.500可分辨名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md)&gt; | Promise对象，返回X500DistinguishedName实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19030002](../errorcode-cert.md#19030002-证书签名验证错误) | The certificate signature verification failed. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19030003](../errorcode-cert.md#19030003-证书尚未生效) | The certificate has not taken effect. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |
| [19030006](../errorcode-cert.md#19030006-证书的密钥用途不含证书签名) | The key cannot be used for signing a certificate. |
| [19030007](../errorcode-cert.md#19030007-证书的密钥用途不含数字签名) | The key cannot be used for a digital signature. |
| [19030004](../errorcode-cert.md#19030004-证书过期) | The certificate has expired. |
| [19030005](../errorcode-cert.md#19030005-无法获取证书的颁发者) | Failed to obtain the certificate issuer. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let nameDer =
  new Uint8Array([48, 41, 49, 11, 48, 9, 6, 3, 85, 4, 3, 12, 2, 67, 65, 49, 13, 48, 11, 6, 3, 85, 4, 10, 12, 4, 116,
    101, 115, 116, 49, 11, 48, 9, 6, 3, 85, 4, 6, 19, 2, 67, 78]);

async function createX500DistinguishedName() {
  try {
    cert.createX500DistinguishedName(nameDer)
      .then((_data) => {
        console.info('createX500DistinguishedName result: success.');
      })
      .catch((err: BusinessError) => {
        console.error(`createX500DistinguishedName failed, errCode: ${err.code}, errMsg: ${err.message}`);
      });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX500DistinguishedName failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@ohos.base';

let nameDer =
  new Uint8Array([48, 41, 49, 11, 48, 9, 6, 3, 85, 4, 3, 12, 2, 67, 65, 49, 13, 48, 11, 6, 3, 85, 4, 10, 12, 4, 116,
    101, 115, 116, 49, 11, 48, 9, 6, 3, 85, 4, 6, 19, 2, 67, 78]);

async function createX500DistinguishedName() {
  try {
    cert.createX500DistinguishedName(nameDer);
    console.info('createX500DistinguishedName result: success.');
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX500DistinguishedName catch, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

