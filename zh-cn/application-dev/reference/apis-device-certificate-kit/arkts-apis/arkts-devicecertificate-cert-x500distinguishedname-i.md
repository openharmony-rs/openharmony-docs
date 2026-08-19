# X500DistinguishedName

提供X.500可分辨名称操作的API。

**起始版本：** 23

<!--Device-cert-interface X500DistinguishedName--><!--Device-cert-interface X500DistinguishedName-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { certificateManager } from '@kit.DeviceCertificateKit';
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## getEncoded

```TypeScript
getEncoded(): EncodingBlob
```

获取X.500可分辨名称的DER编码数据。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X500DistinguishedName-getEncoded(): EncodingBlob--><!--Device-X500DistinguishedName-getEncoded(): EncodingBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md) | X.500可分辨名称的DER编码数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let nameStr = '/CN=Example CA/OU=test cert/O=test/L=XA/ST=SX/C=CN/CN=RSA CA/CN=XTS';
async function getEncoded() {
  try {
    cert.createX500DistinguishedName(nameStr)
      .then((data) => {
        console.info('createX500DistinguishedName result: success.');
        let encodingBlobData = data.getEncoded();
        console.info('encodingBlobData = ' + encodingBlobData.data);
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

let nameStr = '/CN=Example CA/OU=test cert/O=test/L=XA/ST=SX/C=CN/CN=RSA CA/CN=XTS';
async function getEncoded() {
  try {
    let data = await cert.createX500DistinguishedName(nameStr);
    console.info('createX500DistinguishedName result: success.');
    let encodingBlobData = data.getEncoded();
    console.info('getEncoded result: success.');
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX500DistinguishedName catch, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## getName

```TypeScript
getName(): string
```

获取可分辨名的字符串。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X500DistinguishedName-getName(): string--><!--Device-X500DistinguishedName-getName(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 可分辨名的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let nameDer =
  new Uint8Array([48, 41, 49, 11, 48, 9, 6, 3, 85, 4, 3, 12, 2, 67, 65, 49, 13, 48, 11, 6, 3, 85, 4, 10, 12, 4, 116,
    101, 115, 116, 49, 11, 48, 9, 6, 3, 85, 4, 6, 19, 2, 67, 78]);

async function getName() {
  try {
    cert.createX500DistinguishedName(nameDer)
      .then((data) => {
        console.info('createX500DistinguishedName result: success.');
        console.info('createX500DistinguishedName getName: ' + data.getName());
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

async function getName() {
  try {
    let data = await cert.createX500DistinguishedName(nameDer);
    console.info('createX500DistinguishedName result: success.');
    console.info('createX500DistinguishedName getName: ' + data.getName());
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX500DistinguishedName catch, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## getName

```TypeScript
getName(encodingType: EncodingType): string
```

根据指定编码格式获取可分辨名称的字符串。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X500DistinguishedName-getName(encodingType: EncodingType): string--><!--Device-X500DistinguishedName-getName(encodingType: EncodingType): string-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encodingType | [EncodingType](arkts-devicecertificate-cert-encodingtype-e.md) | 是 | 表示编码格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示可分辨名称的字符串，使用逗号分隔相对可分辨名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19020003](../errorcode-cert.md#19020003-参数检查失败) | Parameter check failed. Possible causes: <br>1. The value of encodingType is not in the EncodingType enumeration range. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let nameStr = '/CN=陕西@西安/OU=IT Department/O=ACME Inc./L=San Francisco/ST=California/C=US/CN=ALN C/CN=XTS';
async function getName() {
  try {
    cert.createX500DistinguishedName(nameStr)
      .then((data) => {
        console.info('createX500DistinguishedName result: success.');
        console.info('createX500DistinguishedName getName: ' + data.getName(cert.EncodingType.ENCODING_UTF8));
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

let nameStr = '/CN=陕西@西安/OU=IT Department/O=ACME Inc./L=San Francisco/ST=California/C=US/CN=ALN C/CN=XTS';
async function getName() {
  try {
    let data = await cert.createX500DistinguishedName(nameStr);
    console.info('createX500DistinguishedName result: success.');
    console.info('createX500DistinguishedName getName: ' + data.getName(cert.EncodingType.ENCODING_UTF8));
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX500DistinguishedName catch, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## getName

```TypeScript
getName(type: string): Array<string>
```

按指定类型获取相对可分辨名称的字符串。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X500DistinguishedName-getName(type: string): Array<string>--><!--Device-X500DistinguishedName-getName(type: string): Array<string>-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 指定类型的名称。如"CN"、"OU"等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 相对可分辨名称的字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let nameStr = '/CN=Example CA/OU=test cert/O=test/L=XA/ST=SX/C=CN/CN=RSA CA/CN=XTS';
async function getName() {
  try {
    cert.createX500DistinguishedName(nameStr)
      .then((data) => {
        console.info('createX500DistinguishedName result: success.');
        console.info('createX500DistinguishedName getName: ' + data.getName("CN"));
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

let nameStr = '/CN=Example CA/OU=test cert/O=test/L=XA/ST=SX/C=CN/CN=RSA CA/CN=XTS';
async function getName() {
  try {
    let data = await cert.createX500DistinguishedName(nameStr);
    console.info('createX500DistinguishedName result: success.');
    console.info('createX500DistinguishedName getName: ' + data.getName("CN"));
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX500DistinguishedName catch, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## getName

```TypeScript
getName(type: string, encodingType: EncodingType): Array<string>
```

根据指定类型和编码格式获取相对可分辨名称的字符串数组。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-X500DistinguishedName-getName(type: string, encodingType: EncodingType): Array<string>--><!--Device-X500DistinguishedName-getName(type: string, encodingType: EncodingType): Array<string>-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 指定类型的名称。如"CN"、"OU"等。 |
| encodingType | [EncodingType](arkts-devicecertificate-cert-encodingtype-e.md) | 是 | 表示编码格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 相对可分辨名称的字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19020003](../errorcode-cert.md#19020003-参数检查失败) | Parameter check failed. Possible causes: <br>1. The value of encodingType is not in the EncodingType enumeration range. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let nameStr = '/CN=Example CA/OU=test cert/O=test/L=XA/ST=SX/C=CN/CN=RSA CA/CN=测试';
async function getName() {
  try {
    cert.createX500DistinguishedName(nameStr)
      .then((data) => {
        console.info('createX500DistinguishedName result: success.');
        console.info('createX500DistinguishedName getName: ' + data.getName("CN", cert.EncodingType.ENCODING_UTF8));
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
import { BusinessError } from '@kit.BasicServicesKit';

let nameStr = '/CN=Example CA/OU=test cert/O=test/L=XA/ST=SX/C=CN/CN=RSA CA/CN=测试';
async function getName() {
  try {
    let data = await cert.createX500DistinguishedName(nameStr);
    console.info('createX500DistinguishedName result: success.');
    console.info('createX500DistinguishedName getName: ' + data.getName("CN", cert.EncodingType.ENCODING_UTF8));
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX500DistinguishedName failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

