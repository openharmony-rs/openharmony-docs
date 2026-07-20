# CertExtension

证书扩展域段类。

**起始版本：** 10

<!--Device-cert-interface CertExtension--><!--Device-cert-interface CertExtension-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

<a id="checkca"></a>
## checkCA

```TypeScript
checkCA(): number
```

表示校验证书是否为CA证书。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertExtension-checkCA(): int--><!--Device-CertExtension-checkCA(): int-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当证书扩展域段中密钥用途扩展包含keyCertSign位，并且基本约束中cA字段为true时，表示证书为CA证书。如果证书不是CA证书，则返回-1；否则返回基本约束中的路径长度。如果证书是CA证书，但是基本约束中未给定路径长度，则返回-2，表示无路径长度限制。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

**示例：**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 证书扩展域段二进制数据，需业务自行赋值。
let extData = new Uint8Array([
  0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
  0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
  0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
  0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
  0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
  0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
  0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
  0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
  0xD9, 0xE4
]);

let encodingBlob: cert.EncodingBlob = {
  data: extData,
  // 根据encodingData的格式进行赋值，仅支持FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_DER
};
cert.createCertExtension(encodingBlob, (error, certExt) => {
  if (error) {
    console.error(`createCertExtension failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createCertExtension result: success.');
    try {
      let res = certExt.checkCA();
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`ext checkCA failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});

```

<a id="getencoded"></a>
## getEncoded

```TypeScript
getEncoded(): EncodingBlob
```

表示获取证书扩展域段序列化数据。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertExtension-getEncoded(): EncodingBlob--><!--Device-CertExtension-getEncoded(): EncodingBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md) | 表示证书扩展域段序列化数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

**示例：**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 证书扩展域段二进制数据，需业务自行赋值。
let extData = new Uint8Array([
  0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
  0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
  0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
  0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
  0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
  0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
  0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
  0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
  0xD9, 0xE4
]);

let encodingBlob: cert.EncodingBlob = {
  data: extData,
  // 根据encodingData的格式进行赋值，仅支持FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_DER
};

cert.createCertExtension(encodingBlob, (error, certExt) => {
  if (error) {
    console.error(`createCertExtension failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createCertExtension result: success.');
    try {
      let extEncodedBlob = certExt.getEncoded();
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`ext getEncoded failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});

```

<a id="getentry"></a>
## getEntry

```TypeScript
getEntry(valueType: ExtensionEntryType, oid: DataBlob): DataBlob
```

表示获取证书扩展域段对象信息。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertExtension-getEntry(valueType: ExtensionEntryType, oid: DataBlob): DataBlob--><!--Device-CertExtension-getEntry(valueType: ExtensionEntryType, oid: DataBlob): DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| valueType | [ExtensionEntryType](arkts-devicecertificate-cert-extensionentrytype-e.md) | 是 | 表示证书扩展域段获取的类型。 |
| oid | [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | 是 | 表示证书扩展域段获取的对象标识符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | 表示证书扩展域段对象的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

**示例：**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 证书扩展域段二进制数据，需业务自行赋值。
let extData = new Uint8Array([
  0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
  0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
  0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
  0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
  0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
  0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
  0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
  0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
  0xD9, 0xE4
]);

let encodingBlob: cert.EncodingBlob = {
  data: extData,
  // 根据encodingData的格式进行赋值，仅支持FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_DER
};

cert.createCertExtension(encodingBlob, (error, certExt) => {
  if (error) {
    console.error(`createCertExtension failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createCertExtension result: success.');
    let oid = new Uint8Array([0x32, 0x2e, 0x35, 0x2e, 0x32, 0x39, 0x2e, 0x31, 0x35]);
    let oidBlob: cert.DataBlob = {
      data: oid
    }
    try {
      let entry = certExt.getEntry(cert.ExtensionEntryType.EXTENSION_ENTRY_TYPE_ENTRY, oidBlob);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`ext getEntry failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});

```

<a id="getoidlist"></a>
## getOidList

```TypeScript
getOidList(valueType: ExtensionOidType): DataArray
```

表示获取证书扩展域段对象标识符列表。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertExtension-getOidList(valueType: ExtensionOidType): DataArray--><!--Device-CertExtension-getOidList(valueType: ExtensionOidType): DataArray-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| valueType | [ExtensionOidType](arkts-devicecertificate-cert-extensionoidtype-e.md) | 是 | 表示证书扩展域段对象标识符类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | 表示证书扩展域段对象标识符列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

**示例：**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 证书扩展域段二进制数据，需业务自行赋值。
let extData = new Uint8Array([
  0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
  0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
  0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
  0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
  0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
  0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
  0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
  0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
  0xD9, 0xE4
]);

let encodingBlob: cert.EncodingBlob = {
  data: extData,
  // 根据encodingData的格式进行赋值，仅支持FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_DER
};

cert.createCertExtension(encodingBlob, (error, certExt) => {
  if (error) {
    console.error(`createCertExtension failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createCertExtension result: success.');
    try {
      let oidList = certExt.getOidList(cert.ExtensionOidType.EXTENSION_OID_TYPE_ALL);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`ext getOidList failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});

```

<a id="hasunsupportedcriticalextension"></a>
## hasUnsupportedCriticalExtension

```TypeScript
hasUnsupportedCriticalExtension(): boolean
```

判断是否存在不支持的关键扩展。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertExtension-hasUnsupportedCriticalExtension(): boolean--><!--Device-CertExtension-hasUnsupportedCriticalExtension(): boolean-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当存在不支持的关键扩展时，该方法返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

**示例：**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let encodingData = new Uint8Array([
  0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
  0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
  0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
  0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
  0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
  0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
  0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
  0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
  0xD9, 0xE4
]);
let encodingBlob: cert.EncodingBlob = {
  data: new Uint8Array(encodingData),
  encodingFormat: cert.EncodingFormat.FORMAT_DER
};

cert.createCertExtension(encodingBlob).then((extensionObj) => {
  console.info('createCertExtension result: success.');
  const result = extensionObj.hasUnsupportedCriticalExtension()
  console.info('has unsupported critical extension result =' + result);
}).catch((err: BusinessError) => {
  console.error(`createCertExtension failed, errCode: ${err.code}, errMsg: ${err.message}`);
});

```

