# X509CRLEntry

证书吊销条目。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-cert-interface X509CRLEntry--><!--Device-cert-interface X509CRLEntry-End-->

**系统能力：** SystemCapability.Security.Cert

## getCertIssuer

```TypeScript
getCertIssuer(): DataBlob
```

表示获取被吊销证书的颁发者名称。 > **说明：** > > 获取到的被吊销证书的颁发者名称数据带字符串结束符。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLEntry-getCertIssuer(): DataBlob--><!--Device-X509CRLEntry-getCertIssuer(): DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示被吊销证书的颁发者名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因： <br>1. 内存拷贝失败； <br>2. 系统内部出现空指针； <br>3. 获取Native对象失败或参数转换失败。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 不支持该操作。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

## 示例

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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
  'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
  'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
  'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
  '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
  'eavsH0Q3\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob, (err, x509CRL) => {
  if (err) {
    console.error(`createX509CRL failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('createX509CRL result: success.');

    try {
      let serialNumber = BigInt(1000);
      let crlEntry = x509CRL.getRevokedCert(serialNumber);
      let issuer = crlEntry.getCertIssuer();
      console.info('issuer = ' + issuer.data);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getRevokedCert or getCertIssuer failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
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

function TestGetCertIssuer() {
  let crlData = '-----BEGIN X509 CRL-----\n' +
    'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
    'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
    'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
    'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
    '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
    'eavsH0Q3\n' +
    '-----END X509 CRL-----\n';

  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(crlData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  cert.createX509CRL(encodingBlob, (err, x509CRL) => {
    if (err) {
      console.error('createX509CRL failed, errCode: ' + err.code + ', errMsg: ' + err.message);
    } else {
      console.info('create x509 CRL result: success.');
      try {
        let serialNumber = BigInt(1000);
        if (x509CRL != undefined) {
          let crlEntry = x509CRL.getRevokedCert(serialNumber);
          let issuer = crlEntry.getCertIssuer();
          console.info('issuer = ' + issuer.data);
          console.info('getCertIssuer result: success.');
        }
      } catch (error) {
        let e: BusinessError = error as BusinessError;
        console.error('getRevokedCert or getCertIssuer failed, errCode: ' + e.code + ', errMsg: ' + e.message);
      }
    }
  });
}
```

## getCertIssuer

```TypeScript
getCertIssuer(encodingType: EncodingType): string
```

根据编码类型获取被吊销证书的颁发者名称。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLEntry-getCertIssuer(encodingType: EncodingType): string--><!--Device-X509CRLEntry-getCertIssuer(encodingType: EncodingType): string-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encodingType | [EncodingType](arkts-devicecertificate-cert-encodingtype-e.md) | 是 | 表示编码类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示被吊销证书的颁发者名称，使用逗号分隔相对可分辨名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因： <br>1. 内存拷贝失败； <br>2. 系统内部出现空指针； <br>3. 获取Native对象失败或参数转换失败。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 不支持该操作。 |
| [19020003](../errorcode-cert.md#19020003-参数检查失败) | 参数检查失败。可能的原因： <br>1. encodingType的值不在EncodingType枚举范围内。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

## 示例

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

 let crlData = '-----BEGIN X509 CRL-----\n' +
    'MIIBTDCBtgIBATANBgkqhkiG9w0BAQsFADBZMQswCQYDVQQGEwJDTjEPMA0GA1UE\n' +
    'CAwG6ZmV6KW/MQ8wDQYDVQQHDAbopb/lrokxDzANBgNVBAoMBua1i+ivlTEXMBUG\n' +
    'A1UEAwwO5Lit5paH5rWL6K+VIyMXDTI1MDMyNDA5MTExNVoXDTI1MDQyMzA5MTEx\n' +
    'NVowGTAXAgYBcqcmOsAXDTI1MDIyMDA2MTMwM1qgDjAMMAoGA1UdFAQDAgECMA0G\n' +
    'CSqGSIb3DQEBCwUAA4GBACedFnn4unfYLiRCl1ZAFXx6LFdX6U+IZ/buW44xKAWi\n' +
    'fyvcSxKIeGtMVjmQSs4HeNfNujIjaDN1+/J2nLSmHPiQ/c0LAc47zefVt2VnFuR4\n' +
    'TMUJEDUlnekYfDMxQqtihAO/Bpw33twK6otDvaAPm9vJoCu8JmGXxt6g+8vbYuNT\n' +
    '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob, (err, x509CRL) => {
  if (err) {
    console.error(`createX509CRL failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('createX509CRL result: success.');

    try {
      let serialNumber = BigInt(1591942200000);
      let crlEntry = x509CRL.getRevokedCert(serialNumber);
      let issuer = crlEntry.getCertIssuer(cert.EncodingType.ENCODING_UTF8);
      console.info('issuer output = ' + issuer);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getRevokedCert or getCertIssuer failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
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

function TestGetCertIssuer() {
  let crlData = '-----BEGIN X509 CRL-----\n' +
    'MIIBTDCBtgIBATANBgkqhkiG9w0BAQsFADBZMQswCQYDVQQGEwJDTjEPMA0GA1UE\n' +
    'CAwG6ZmV6KW/MQ8wDQYDVQQHDAbopb/lrokxDzANBgNVBAoMBua1i+ivlTEXMBUG\n' +
    'A1UEAwwO5Lit5paH5rWL6K+VIyMXDTI1MDMyNDA5MTExNVoXDTI1MDQyMzA5MTEx\n' +
    'NVowGTAXAgYBcqcmOsAXDTI1MDIyMDA2MTMwM1qgDjAMMAoGA1UdFAQDAgECMA0G\n' +
    'CSqGSIb3DQEBCwUAA4GBACedFnn4unfYLiRCl1ZAFXx6LFdX6U+IZ/buW44xKAWi\n' +
    'fyvcSxKIeGtMVjmQSs4HeNfNujIjaDN1+/J2nLSmHPiQ/c0LAc47zefVt2VnFuR4\n' +
    'TMUJEDUlnekYfDMxQqtihAO/Bpw33twK6otDvaAPm9vJoCu8JmGXxt6g+8vbYuNT\n' +
    '-----END X509 CRL-----\n';

  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(crlData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  cert.createX509CRL(encodingBlob, (err, x509CRL) => {
    if (err) {
      console.error('createX509CRL failed, errCode: ' + err.code + ', errMsg: ' + err.message);
    } else {
      console.info('create x509 CRL result: success.');

      try {
        let serialNumber = BigInt(1591942200000);
        if (x509CRL != undefined) {
          let crlEntry = x509CRL.getRevokedCert(serialNumber);
          let issuer = crlEntry.getCertIssuer(cert.EncodingType.ENCODING_UTF8);
          console.info('issuer output = ' + issuer);
        }
      } catch (error) {
        let e: BusinessError = error as BusinessError;
        console.error('getRevokedCert or getCertIssuer failed, errCode: ' + e.code + ', errMsg: ' + e.message);
      }
    }
  });
}
```

## getCertIssuerX500DistinguishedName

```TypeScript
getCertIssuerX500DistinguishedName(): X500DistinguishedName
```

获取被吊销证书的颁发者的X.500可分辨名称对象。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLEntry-getCertIssuerX500DistinguishedName(): X500DistinguishedName--><!--Device-X509CRLEntry-getCertIssuerX500DistinguishedName(): X500DistinguishedName-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md) | X.500可分辨名称对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因： <br>1. 内存拷贝失败； <br>2. 系统内部出现空指针； <br>3. 获取Native对象失败或参数转换失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

## 示例

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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
  'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
  'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
  'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
  '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
  'eavsH0Q3\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certGetCertIssuerX500DistinguishedName() {
  let x509Crl: cert.X509CRL = {} as cert.X509CRL;
  try {
    x509Crl = await cert.createX509CRL(encodingBlob);
    console.info('createX509CRL result: success.');
    x509Crl.getRevokedCert(BigInt(1000)).getCertIssuerX500DistinguishedName();
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX509CRL failed, errCode: ${e.code}, errMsg: ${e.message}`);
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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
  'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
  'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
  'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
  '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
  'eavsH0Q3\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certGetCertIssuerX500DistinguishedName() {
  let x509Crl: cert.X509CRL;
  try {
    x509Crl = await cert.createX509CRL(encodingBlob);
    console.info('createX509CRL result: success.');
    x509Crl.getRevokedCert(BigInt(1000)).getCertIssuerX500DistinguishedName();
    console.info('getCertIssuerX500DistinguishedName result: success.');
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX509CRL failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## getEncoded

```TypeScript
getEncoded(callback: AsyncCallback<EncodingBlob>): void
```

表示获取证书吊销条目的序列化数据。使用Callback异步回调。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLEntry-getEncoded(callback: AsyncCallback<EncodingBlob>): void--><!--Device-X509CRLEntry-getEncoded(callback: AsyncCallback<EncodingBlob>): void-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md)&gt; | 是 | 回调函数。当获取证书吊销条目序列化数据成功时，err为undefined， data为获取到的证书吊销条目序列化数据；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因： <br>1. 内存拷贝失败； <br>2. 系统内部出现空指针； <br>3. 获取Native对象失败或参数转换失败。 |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因： <br>1. 必填参数未指定； <br>2. 参数类型不正确； |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

## 示例

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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
  'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
  'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
  'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
  '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
  'eavsH0Q3\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob, (err, x509CRL) => {
  if (err) {
    console.error(`createX509CRL failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('create x509 CRL result: success.');

    try {
      let serialNumber = BigInt(1000);
      let crlEntry = x509CRL.getRevokedCert(serialNumber);
      crlEntry.getEncoded((error, _data) => {
        if (error) {
          console.error(`getEncoded failed, errCode: ${error.code}, errMsg: ${error.message}`);
        } else {
          console.info('getEncoded result: success.');
        }
      });
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getRevokedCert failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
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

function TestGetEncoded() {
  let crlData = '-----BEGIN X509 CRL-----\n' +
    'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
    'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
    'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
    'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
    '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
    'eavsH0Q3\n' +
    '-----END X509 CRL-----\n';

  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(crlData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  cert.createX509CRL(encodingBlob, (err, x509CRL) => {
    if (err) {
      console.error('createX509CRL failed, errCode: ' + err.code + ', errMsg: ' + err.message);
    } else {
      console.info('create x509 CRL result: success.');
      try {
        let serialNumber = BigInt(1000);
        if (x509CRL != undefined) {
          let crlEntry = x509CRL.getRevokedCert(serialNumber);
          crlEntry.getEncoded((error, _data) => {
            if (error) {
              console.error('getEncoded failed, errCode: ' + error.code + ', errMsg: ' + error.message);
            } else {
              console.info('getEncoded result: success.');
            }
          });
        }
      } catch (error) {
        let e: BusinessError = error as BusinessError;
        console.error('getRevokedCert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
      }
    }
  });
}
```

## getEncoded

```TypeScript
getEncoded(): Promise<EncodingBlob>
```

表示获取证书吊销条目的序列化数据。使用Promise方式返回结果。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLEntry-getEncoded(): Promise<EncodingBlob>--><!--Device-X509CRLEntry-getEncoded(): Promise<EncodingBlob>-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md)&gt; | Promise对象，返回证书吊销条目的序列化数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因： <br>1. 内存拷贝失败； <br>2. 系统内部出现空指针； <br>3. 获取Native对象失败或参数转换失败。 |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因： <br>1. 必填参数未指定； <br>2. 参数类型不正确； |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

## 示例

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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
  'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
  'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
  'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
  '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
  'eavsH0Q3\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob, (err, x509CRL) => {
  if (err) {
    console.error(`createX509CRL failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('create x509 CRL result: success.');

    try {
      let serialNumber = BigInt(1000);
      let crlEntry = x509CRL.getRevokedCert(serialNumber);
      crlEntry.getEncoded().then(_result => {
        console.info('getEncoded result: success.');
      }).catch((error: BusinessError) => {
        console.error(`getEncoded failed, errCode: ${error.code}, errMsg: ${error.message}`);
      });
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getRevokedCert failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
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

async function TestGetEncoded() {
  let crlData = '-----BEGIN X509 CRL-----\n' +
    'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
    'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
    'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
    'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
    '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
    'eavsH0Q3\n' +
    '-----END X509 CRL-----\n';

  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(crlData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };
  try {
    let x509CRL = await cert.createX509CRL(encodingBlob);
    let serialNumber = BigInt(1000);
    if (x509CRL != undefined) {
      let crlEntry = x509CRL.getRevokedCert(serialNumber);
      try {
        let result = await crlEntry.getEncoded();
        console.info('result = ' + result.data);
        console.info('getEncoded result: success.');
      } catch (err) {
        let e: BusinessError = err as BusinessError;
        console.error(`getEncoded failed, ${e.code}, ${e.message}`);
      }
    }
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('getRevokedCert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## getExtensions

```TypeScript
getExtensions(): DataBlob
```

表示获取DER格式的CRL条目的扩展数据。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLEntry-getExtensions(): DataBlob--><!--Device-X509CRLEntry-getExtensions(): DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示CRL条目的扩展数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因： <br>1. 内存拷贝失败； <br>2. 系统内部出现空指针； <br>3. 获取Native对象失败或参数转换失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

## 示例

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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIIBjjB4AgEBMA0GCSqGSIb3DQEBCwUAMBIxEDAOBgNVBAMMB1Jvb3QgQ0EXDTI0\n' +
  'MDMxOTAyMDQwN1oXDTI0MDQxODAyMDQwN1owIjAgAgEEFw0yNDAzMTkwMjA0MDZa\n' +
  'MAwwCgYDVR0VBAMKAQGgDjAMMAoGA1UdFAQDAgEAMA0GCSqGSIb3DQEBCwUAA4IB\n' +
  'AQCbjvmHxC8dW6WCS/ga73kx2b7f8I/2eVuDYyReuBiGWeJ9vDmGqimJ9VwOk+ph\n' +
  'LvG/2Zvh9I8qXxnOWeseA2C0bEshJGvXpquIjm00OUyLlK6jdfRbhXT8OyvDjqZs\n' +
  'e1IsMV7Zo11SUc8nR2d0QQ7EVDCN/XFKPsmoK7PhJnRh5gc8W3FKQ6b8H9kdjgTa\n' +
  'KQUap1OIDReVsjPBmRAbwMMLtbrAMllF7E6x7uHgHTGaK1ZPJDtsnCJ45ur3mk/o\n' +
  'HAJFwHNjNDltiEfvMSs76/X0cwitpeW4dFk6c3QtqhxJrHDD4gl8di+xHOyHXpzX\n' +
  '+i2osvdPWRia0dJCL1PCA14k\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob, (err, x509CRL) => {
  if (err) {
    console.error(`createX509CRL failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('createX509CRL result: success.');

    try {
      let serialNumber = BigInt(4);
      let crlEntry = x509CRL.getRevokedCert(serialNumber);
      let extensions = crlEntry.getExtensions();
      console.info('extensions = ' + extensions.data);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getRevokedCert or getExtensions failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
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

function TestGetExtensions() {
  let crlData = '-----BEGIN X509 CRL-----\n' +
    'MIIBjjB4AgEBMA0GCSqGSIb3DQEBCwUAMBIxEDAOBgNVBAMMB1Jvb3QgQ0EXDTI0\n' +
    'MDMxOTAyMDQwN1oXDTI0MDQxODAyMDQwN1owIjAgAgEEFw0yNDAzMTkwMjA0MDZa\n' +
    'MAwwCgYDVR0VBAMKAQGgDjAMMAoGA1UdFAQDAgEAMA0GCSqGSIb3DQEBCwUAA4IB\n' +
    'AQCbjvmHxC8dW6WCS/ga73kx2b7f8I/2eVuDYyReuBiGWeJ9vDmGqimJ9VwOk+ph\n' +
    'LvG/2Zvh9I8qXxnOWeseA2C0bEshJGvXpquIjm00OUyLlK6jdfRbhXT8OyvDjqZs\n' +
    'e1IsMV7Zo11SUc8nR2d0QQ7EVDCN/XFKPsmoK7PhJnRh5gc8W3FKQ6b8H9kdjgTa\n' +
    'KQUap1OIDReVsjPBmRAbwMMLtbrAMllF7E6x7uHgHTGaK1ZPJDtsnCJ45ur3mk/o\n' +
    'HAJFwHNjNDltiEfvMSs76/X0cwitpeW4dFk6c3QtqhxJrHDD4gl8di+xHOyHXpzX\n' +
    '+i2osvdPWRia0dJCL1PCA14k\n' +
    '-----END X509 CRL-----\n';

  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(crlData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  cert.createX509CRL(encodingBlob, (err, x509CRL) => {
    if (err) {
      console.error('createX509CRL failed, errCode: ' + err.code + ', errMsg: ' + err.message);
    } else {
      console.info('create x509 CRL result: success.');
      try {
        let serialNumber = BigInt(4);
        if (x509CRL != undefined) {
          let crlEntry = x509CRL.getRevokedCert(serialNumber);
          let extensions = crlEntry.getExtensions();
          console.info('extensions = ' + extensions.data);
          console.info('getExtensions result: success.');
        }
      } catch (error) {
        let e: BusinessError = error as BusinessError;
        console.error('getRevokedCert or getExtensions failed, errCode: ' + e.code + ', errMsg: ' + e.message);
      }
    }
  });
}
```

## getExtensionsObject

```TypeScript
getExtensionsObject(): CertExtension
```

获取CRL条目的扩展对象。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLEntry-getExtensionsObject(): CertExtension--><!--Device-X509CRLEntry-getExtensionsObject(): CertExtension-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CertExtension](arkts-devicecertificate-cert-certextension-i.md) | CRL条目的扩展对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因： <br>1. 内存拷贝失败； <br>2. 系统内部出现空指针； <br>3. 获取Native对象失败或参数转换失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

## 示例

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

let crlData = '-----BEGIN X509 CRL-----\n' +
  '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\n' +
  'BsQoO8O2EVpJ54fxKMCSDOkJf1hNCxi3eQ==\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certGetExtensionsObject() {
  let x509Crl: cert.X509CRL = {} as cert.X509CRL;
  try {
    x509Crl = await cert.createX509CRL(encodingBlob);
    console.info('createX509CRL result: success.');
    x509Crl.getRevokedCert(BigInt('14091103387070223745671018446433705560')).getExtensionsObject();
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX509CRL failed, errCode: ${e.code}, errMsg: ${e.message}`);
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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIINlTCCDH0CAQEwDQYJKoZIhvcNAQELBQAwTDELMAkGA1UEBhMCVVMxFTATBgNV\n' +
  'BAoTDERpZ2lDZXJ0IEluYzEmMCQGA1UEAxMdRGlnaUNlcnQgU2VjdXJlIFNpdGUg\n' +
  'Q04gQ0EgRzMXDTI0MDMxMjE4NDQ0NVoXDTI0MDMxOTE4NDQ0NVowggvJMCECEAbk\n' +
  'wC/+N2YXfpw7vgDJ2xAXDTIzMDIwNzA1NTg1OFowIQIQDonqcHww7uhlmWH+OfIe\n' +
  'PhcNMjMwMzA5MDcwMzI1WjAvAhAM4CTrULrJUEinWgT9AFPvFw0yMzAzMjAxOTE4\n' +
  'NTRaMAwwCgYDVR0VBAMKAQQwIQIQBQP4xflKkcRehoJ2NaA/jhcNMjMwMzIyMDk0\n' +
  'NTI5WjAvAhAOmgzoiIqznAaFec53PVPUFw0yMzAzMjcyMDI4MDNaMAwwCgYDVR0V\n' +
  'BAMKAQQwLwIQBaC2Z3D4dcQ/O7HnzFU9KBcNMjMwMzI5MTc1OTQ1WjAMMAoGA1Ud\n' +
  'FQQDCgEFMCECEAlz9Rg1b+9La4oFqsHUc4AXDTIzMDMzMTAyMzk0MVowIQIQD9yW\n' +
  '92pX6BinUKVBVSSTmBcNMjMwNDExMDExNjI5WjAvAhAIIarHUWWee4V9W/Yzm86k\n' +
  'Fw0yMzA0MTQyMDE5MTJaMAwwCgYDVR0VBAMKAQQwIQIQC2OiM3VIJX2dEe8/pf8f\n' +
  'hRcNMjMwNDIxMDMzMDIyWjAhAhAP0ueyg5n/7b2Hotml7f42Fw0yMzA0MjYwMjU3\n' +
  'NDJaMCECEAqMu61nkOEmTOdMbUZTMrkXDTIzMDUxNzAxMzI0NVowLwIQDYv1rt0K\n' +
  'olvP+nQoi5LeLRcNMjMwNTIzMTc0MDE4WjAMMAoGA1UdFQQDCgEEMC8CEA8WMKlw\n' +
  'iCK36PruJvup5bUXDTIzMDUyMzE3NDA1M1owDDAKBgNVHRUEAwoBBDAvAhAJ5uwT\n' +
  'aqwgLzNVpxh4u9EPFw0yMzA1MjUxNzEwNTBaMAwwCgYDVR0VBAMKAQQwIQIQCg0k\n' +
  '5UadwDH5xm14yxcgLRcNMjMwNjA3MDcyNDAwWjAhAhAEByUhbBR6/pZRFUH2PTxE\n' +
  'Fw0yMzA2MDgwMjIwMzBaMCECEATquAQcy3W1kUOkb4VoOvEXDTIzMDYyNjA5MDIw\n' +
  'NlowIQIQBrF5sueIjk1snKdO0ISOXhcNMjMwNjMwMDI0MDA0WjAhAhAJEG72WQtV\n' +
  'lTOYiA0xjVk5Fw0yMzA3MDUwMjEyMzdaMCECEAmXIuCMJv9gllYuKfCHm5EXDTIz\n' +
  'MDcwNTAyMTIzN1owIQIQAotQots0ngzRwACzrS9mCBcNMjMwNzA2MDU0NDU3WjAh\n' +
  'AhAG2hyGc9SfXrLc0Uk2J1BeFw0yMzA3MjQwMTUwNDBaMCECEAJhm5FSlVyTG9UK\n' +
  'zS+ecUgXDTIzMDcyNjA2NDQzM1owIQIQC4mlxBQuFxWC4pF7/P8BDxcNMjMwNzMx\n' +
  'MTAzMjU0WjAhAhADCEp333/avF3m6HZtBImOFw0yMzA3MzExMDMzNTBaMCECEAKd\n' +
  'P7fydlXUcS4v/YnZMMwXDTIzMDczMTEwMzQzOFowIQIQC+m5EUcRd1E0lEIPj17Z\n' +
  'rRcNMjMwODAxMDYwNDE4WjAvAhAF4QcgQQlWpAi4FVflzbKxFw0yMzA4MDMxNjIz\n' +
  'MTdaMAwwCgYDVR0VBAMKAQQwIQIQAn01GEZ50Y5ugIcEuGfF9BcNMjMwODA4MDE1\n' +
  'NzM1WjAhAhAFHj3FDKeP9q9CM924d8RIFw0yMzA4MDgwMTU5NDhaMC8CEAnkNPSD\n' +
  'U5yiMsV3fU06a6oXDTIzMDgwODE5MjIwMlowDDAKBgNVHRUEAwoBBDAvAhAETU4z\n' +
  '13iMKiwQujsxJDRhFw0yMzA4MTAyMDU4NDdaMAwwCgYDVR0VBAMKAQQwIQIQB1oD\n' +
  'M2mOYuse7e/nTqx+8xcNMjMwOTA0MDUwOTU3WjAhAhALf3Bp63so6O+R5QbWPWu6\n' +
  'Fw0yMzEwMDkwNjE5NTVaMCECEAKFHdXcy/zBXRtMj3BVhO0XDTIzMTAwOTA2MTk1\n' +
  'N1owIQIQDNNmVHN4tMu1xth6IAe4ZhcNMjMxMDEyMDc0MjQ1WjAhAhACNNJA2oMM\n' +
  'pr+giIgczvHOFw0yMzEwMTYwNTEyMzdaMCECEAoQun7uSHhvy6GBoxG7XOkXDTIz\n' +
  'MTExNjA3MDAzN1owLwIQA1NsI22PLvohCvKwdtAJwBcNMjMxMjA2MTgyNzUzWjAM\n' +
  'MAoGA1UdFQQDCgEEMCECEAWagozDt4jfBzi+aDGFr88XDTIzMTIxMTA3MjM1OFow\n' +
  'IQIQD1g7NdEk7t05zg6yweYc5hcNMjMxMjExMDcyNTM3WjAhAhAMJnRjUQAzFQFH\n' +
  'kwIguRz2Fw0yMzEyMTEwNzI2NDJaMCECEAT0bVxyPKkeTV8JQuPxfcwXDTIzMTIx\n' +
  'MTA3MjcyNlowIQIQA/5BlE0Ushtw24Ol9L2sexcNMjMxMjExMDcyODA2WjAhAhAL\n' +
  'Ij6FAKVJDnKAwwt19+/RFw0yMzEyMTEwNzI5MDJaMCECEAmPyfX3FuOHgryS2i8c\n' +
  'SrUXDTIzMTIxMTA3Mjk0M1owIQIQC+uGa6tmPRPCB0jW+6WWUhcNMjMxMjExMDcz\n' +
  'MDIzWjAhAhAJCq59mFZj6SWLH/m18Fq2Fw0yMzEyMTEwNzMwNTJaMCECEAp0Po24\n' +
  'WHmdEMTVyp9AMssXDTIzMTIxMTA3MzEyNlowIQIQAcf+793qPEHipkAhjf7MghcN\n' +
  'MjMxMjExMDczMTQ5WjAhAhAElLuCARMBoDIH0Y2D1DpSFw0yMzEyMTEwNzMyMTla\n' +
  'MCECEAWlgWhTXqKOB61zA7Ao8vQXDTIzMTIxMTA3MzI0OFowIQIQAeZqfkFYc/6t\n' +
  'zO7j/FVYwBcNMjMxMjExMDczMzM1WjAhAhAHzftyRhskxV6opTfHb59OFw0yMzEy\n' +
  'MTEwNzM0MDNaMCECEASXrBHdRYUm9VIZ1wN4qAsXDTIzMTIxMTA3MzQyN1owIQIQ\n' +
  'BDFb/OY65CZ1sTdMPAc+IhcNMjMxMjExMDczNTEzWjAhAhAFg7mRyWvWXc+KT014\n' +
  'Ro5AFw0yMzEyMTEwNzM1NDhaMCECEA+wAstqfBUEkSvinYlWeOwXDTIzMTIxMTA3\n' +
  'MzYyNVowIQIQB3Z75ksHGnvGmuHbvwbheRcNMjMxMjExMDczNjU5WjAhAhALfrIn\n' +
  'OGRVeePivKkJ+d1xFw0yMzEyMTEwNzM4MDFaMCECEAnm5NfU36m+FXNlJiUsXpMX\n' +
  'DTIzMTIxMTA3MzgzNVowIQIQCrBoHo4X2md3Amteqh7h3RcNMjMxMjExMDczOTA3\n' +
  'WjAhAhAGxHlqrHu66ifOwTTMhHHFFw0yMzEyMTEwNzM5NDNaMCECEA2BDG1SI7Se\n' +
  '2GAt+b9UnF8XDTIzMTIxMTA3NDAyNFowLwIQDZvl5jkmAwjTweDCtrXbLRcNMjMx\n' +
  'MjExMjA0NDQ3WjAMMAoGA1UdFQQDCgEEMCECEAzgcwGVpyXXZSmLLF4MExQXDTIz\n' +
  'MTIxOTE3MjczMlowIQIQARB9nVoMuE5GSFeb3U553hcNMjMxMjE5MTcyODA1WjAh\n' +
  'AhAD+JIH7lFcX9UNqTogrMcPFw0yMzEyMTkxNzI5MDZaMCECEAux1kd8ugXs4mI+\n' +
  'xMfXgpsXDTIzMTIxOTE3MjkyOFowIQIQCUO5VqAmbxA8Jdly97msLhcNMjMxMjE5\n' +
  'MTcyOTU0WjAhAhAFyzrU1JtsiPNPeWrfdvGvFw0yMzEyMTkxNzMwNDlaMCECEAwT\n' +
  'tMq5EsBTUhQwm6nWhnAXDTIzMTIyMDE3NDc1NlowIQIQBx3qL8rMclE9gxamaa14\n' +
  'xBcNMjMxMjIwMTc0ODM2WjAhAhAOnKUlrCaxs+lRqLrBmk2PFw0yNDAxMzAxOTMw\n' +
  'MTVaMCECEAtYs/5ZRsrMAxQVDA44eWYXDTI0MDIwNjA2MjYwMFowIQIQDjrMV1d3\n' +
  '0NhxngX5rqqxjBcNMjQwMjIxMDc0ODEwWjAhAhAPGohz3+JyS6H4JzHCjLrXFw0y\n' +
  'NDAyMjgyMDQxMjZaMC8CEAqZ2QktAMprzZmtolbOXlgXDTI0MDIyOTE4MDYzMVow\n' +
  'DDAKBgNVHRUEAwoBBDAhAhAMAHgNfiburtKDp8OJuzRCFw0yNDAzMDQwNjA3MzJa\n' +
  'MCECEA/HgrXcSBqkb2JdfrFDAfgXDTI0MDMwNDA2MDczMlqgMDAuMB8GA1UdIwQY\n' +
  'MBaAFETZyEozjtNSjaeSlGEfmsilt+zLMAsGA1UdFAQEAgIFrDANBgkqhkiG9w0B\n' +
  'AQsFAAOCAQEAJ5rSr0Av5sH59J2LXW5hZ8SJTzDbR8ADdi/CCLolbUUnE0oaAZ+2\n' +
  '9z0niAD5m8HQikNz8K+FKAsQatN/CAj4bzRMeF37hQCiZpqNtxP69JDGeWpGPiH2\n' +
  'K/YfpzL9iSbBOxFmosxUX8J/iX36mCUl+3OUHh+qSYeElboxeAmTCnY5Pl5Bq9is\n' +
  'gp0MmzNYCo7GEFrtS03p2msK25uRqQl6Qn0NZS0yGjdUG7RTZe4xua5drjEkB1o/\n' +
  '15f+mtYj6DtWM1twi1q3VYVxhRSsk6XmmS0BViTEl+MT0BRAPwBSdlyt++1Pnnrd\n' +
  'BsQoO8O2EVpJ54fxKMCSDOkJf1hNCxi3eQ==\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certGetExtensionsObject() {
  let x509Crl: cert.X509CRL;
  try {
    x509Crl = await cert.createX509CRL(encodingBlob);
    console.info('createX509CRL result: success.');
    x509Crl.getRevokedCert(BigInt('14091103387070223745671018446433705560')).getExtensionsObject();
    console.info('getExtensionsObject result: success.');
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX509CRL failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## getRevocationDate

```TypeScript
getRevocationDate(): string
```

表示获取证书被吊销的日期。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLEntry-getRevocationDate(): string--><!--Device-X509CRLEntry-getRevocationDate(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示证书被吊销的日期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因： <br>1. 内存拷贝失败； <br>2. 系统内部出现空指针； <br>3. 获取Native对象失败或参数转换失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

## 示例

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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
  'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
  'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
  'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
  '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
  'eavsH0Q3\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob, (err, x509CRL) => {
  if (err) {
    console.error(`createX509CRL failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('createX509CRL result: success.');

    try {
      let serialNumber = BigInt(1000);
      let crlEntry = x509CRL.getRevokedCert(serialNumber);
      let date = crlEntry.getRevocationDate();
      console.info('date = ' + date);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getRevokedCert or getRevocationDate failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
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

function TestGetRevocationDate() {
  let crlData = '-----BEGIN X509 CRL-----\n' +
    'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
    'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
    'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
    'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
    '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
    'eavsH0Q3\n' +
    '-----END X509 CRL-----\n';

  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(crlData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  cert.createX509CRL(encodingBlob, (err, x509CRL) => {
    if (err) {
      console.error('createX509CRL failed, errCode: ' + err.code + ', errMsg: ' + err.message);
    } else {
      console.info('create x509 CRL result: success.');
      try {
        let serialNumber = BigInt(1000);
        if (x509CRL != undefined) {
          let crlEntry = x509CRL.getRevokedCert(serialNumber);
          let date = crlEntry.getRevocationDate();
          console.info('date = ' + date);
          console.info('getRevocationDate result: success.');
        }
      } catch (error) {
        let e: BusinessError = error as BusinessError;
        console.error('getRevokedCert or getRevocationDate failed, errCode: ' + e.code + ', errMsg: ' + e.message);
      }
    }
  });
}
```

## getSerialNumber

```TypeScript
getSerialNumber(): bigint
```

表示获取被吊销的证书的序列号。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLEntry-getSerialNumber(): bigint--><!--Device-X509CRLEntry-getSerialNumber(): bigint-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 表示证书吊销条目的序列号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因： <br>1. 内存拷贝失败； <br>2. 系统内部出现空指针； <br>3. 获取Native对象失败或参数转换失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

## 示例

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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
  'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
  'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
  'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
  '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
  'eavsH0Q3\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob, (err, x509CRL) => {
  if (err) {
    console.error(`createX509Crl failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('createX509CRL result: success.');

    try {
      let serialNumber = BigInt(1000);
      let crlEntry = x509CRL.getRevokedCert(serialNumber);
      serialNumber = crlEntry.getSerialNumber();
      console.info('serialNumber = ' + serialNumber);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getRevokedCert or getSerialNumber failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
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

function TestGetSerialNumber() {
  let crlData = '-----BEGIN X509 CRL-----\n' +
    'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
    'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
    'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
    'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
    '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
    'eavsH0Q3\n' +
    '-----END X509 CRL-----\n';

  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(crlData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  cert.createX509CRL(encodingBlob, (err, x509CRL) => {
    if (err) {
      console.error('createX509Crl failed, errCode: ' + err.code + ', errMsg: ' + err.message);
    } else {
      console.info('create x509 crl result: success.');

      try {
        let serialNumber = BigInt(1000);
        if (x509CRL != undefined) {
          let crlEntry = x509CRL.getRevokedCert(serialNumber);
          serialNumber = crlEntry.getSerialNumber();
          console.info('serialNumber = ' + serialNumber);
          console.info('getSerialNumber result: success.');
        }
      } catch (error) {
        let e: BusinessError = error as BusinessError;
        console.error('getRevokedCert or getSerialNumber failed, errCode: ' + e.code + ', errMsg: ' + e.message);
      }
    }
  })
}
```

## hasExtensions

```TypeScript
hasExtensions(): boolean
```

表示判断CRL条目是否有扩展。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLEntry-hasExtensions(): boolean--><!--Device-X509CRLEntry-hasExtensions(): boolean-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true则表示CRL条目有扩展，返回false则表示无扩展。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因： <br>1. 内存拷贝失败； <br>2. 系统内部出现空指针； <br>3. 获取Native对象失败或参数转换失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

## 示例

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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
  'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
  'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
  'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
  '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
  'eavsH0Q3\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob, (err, x509CRL) => {
  if (err) {
    console.error(`createX509CRL failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('createX509CRL result: success.');

    try {
      let serialNumber = BigInt(1000);
      let crlEntry = x509CRL.getRevokedCert(serialNumber);
      let hasExtensions = crlEntry.hasExtensions();
      console.info('hasExtensions = ' + hasExtensions);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getRevokedCert or hasExtensions failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
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

function TestHasExtensions() {
  let crlData = '-----BEGIN X509 CRL-----\n' +
    'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
    'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
    'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
    'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
    '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
    'eavsH0Q3\n' +
    '-----END X509 CRL-----\n';

  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(crlData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  cert.createX509CRL(encodingBlob, (err, x509CRL) => {
    if (err) {
      console.error('createX509CRL failed, errCode: ' + err.code + ', errMsg: ' + err.message);
    } else {
      console.info('create x509 CRL result: success.');
      try {
        let serialNumber = BigInt(1000);
        if (x509CRL != undefined) {
          let crlEntry = x509CRL.getRevokedCert(serialNumber);
          let hasExtensions = crlEntry.hasExtensions();
          console.info('hasExtensions = ' + hasExtensions);
          console.info('hasExtensions result: success.');
        }
      } catch (error) {
        let e: BusinessError = error as BusinessError;
        console.error('getRevokedCert or hasExtensions failed, errCode: ' + e.code + ', errMsg: ' + e.message);
      }
    }
  });
}
```

## hashCode

```TypeScript
hashCode(): Uint8Array
```

获取DER格式数据的哈希值。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLEntry-hashCode(): Uint8Array--><!--Device-X509CRLEntry-hashCode(): Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | DER格式数据的哈希值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因： <br>1. 内存拷贝失败； <br>2. 系统内部出现空指针； <br>3. 获取Native对象失败或参数转换失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

## 示例

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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
  'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
  'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
  'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
  '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
  'eavsH0Q3\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certHashCode() {
  let x509Crl: cert.X509CRL = {} as cert.X509CRL;
  try {
    x509Crl = await cert.createX509CRL(encodingBlob);
    console.info('createX509CRL result: success.');
    console.info('hashCode success: ' + x509Crl.getRevokedCert(BigInt(1000)).hashCode());
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX509CRL failed, errCode: ${e.code}, errMsg: ${e.message}`);
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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
  'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
  'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
  'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
  '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
  'eavsH0Q3\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certHashCode() {
  let x509Crl: cert.X509CRL;
  try {
    x509Crl = await cert.createX509CRL(encodingBlob);
    console.info('createX509CRL result: success.');
    console.info('hashCode success: ' + x509Crl.getRevokedCert(BigInt(1000)).hashCode());
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX509CRL failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## toString

```TypeScript
toString(): string
```

获取对象的字符串类型数据。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509CRLEntry-toString(): string--><!--Device-X509CRLEntry-toString(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 对象的字符串类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因： <br>1. 内存拷贝失败； <br>2. 系统内部出现空指针； <br>3. 获取Native对象失败或参数转换失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |

## 示例

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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
  'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
  'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
  'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
  '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
  'eavsH0Q3\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certToString() {
  let x509Crl: cert.X509CRL = {} as cert.X509CRL;
  try {
    x509Crl = await cert.createX509CRL(encodingBlob);
    console.info('createX509CRL result: success.');
    console.info('toString success: ' + x509Crl.getRevokedCert(BigInt(1000)).toString());
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX509CRL failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

ArkTS-Dyn示例：

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

let crlData = '-----BEGIN X509 CRL-----\n' +
  'MIHzMF4CAQMwDQYJKoZIhvcNAQEEBQAwFTETMBEGA1UEAxMKQ1JMIGlzc3VlchcN\n' +
  'MTcwODA3MTExOTU1WhcNMzIxMjE0MDA1MzIwWjAVMBMCAgPoFw0zMjEyMTQwMDUz\n' +
  'MjBaMA0GCSqGSIb3DQEBBAUAA4GBACEPHhlaCTWA42ykeaOyR0SGQIHIOUR3gcDH\n' +
  'J1LaNwiL+gDxI9rMQmlhsUGJmPIPdRs9uYyI+f854lsWYisD2PUEpn3DbEvzwYeQ\n' +
  '5SqQoPDoM+YfZZa23hoTLsu52toXobP74sf/9K501p/+8hm4ROMLBoRT86GQKY6g\n' +
  'eavsH0Q3\n' +
  '-----END X509 CRL-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certToString() {
  let x509Crl: cert.X509CRL;
  try {
    x509Crl = await cert.createX509CRL(encodingBlob);
    console.info('createX509CRL result: success.');
    console.info('toString success: ' + x509Crl.getRevokedCert(BigInt(1000)).toString());
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX509CRL failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

