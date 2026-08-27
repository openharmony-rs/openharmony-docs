# X509CRLEntry

证书吊销条目。

**起始版本：** 11

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
```

## getCertIssuer

```TypeScript
getCertIssuer(): DataBlob
```

表示获取被吊销证书的颁发者名称。

> **说明：**
> 
> 获取到的被吊销证书的颁发者名称数据带字符串结束符。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示被吊销证书的颁发者名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

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

cert.createX509Crl(encodingBlob, (err, x509Crl) => {
  if (err) {
    console.error(`createX509Crl failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('create x509 crl result: success.');

    try {
      let serialNumber = 1000;
      let crlEntry = x509Crl.getRevokedCert(serialNumber);
      let issuer = crlEntry.getCertIssuer();
      console.info('issuer = ' + issuer.data);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getRevokedCert or getCertIssuer failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

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

## getCertIssuer

```TypeScript
getCertIssuer(encodingType: EncodingType): string
```

根据编码类型获取被吊销证书的颁发者名称。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

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
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19020003](../errorcode-cert.md#19020003-参数检查失败) | Parameter check failed. Possible causes:  1. The value of encodingType is not in the EncodingType enumeration range. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

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

## getCertIssuerX500DistinguishedName

```TypeScript
getCertIssuerX500DistinguishedName(): X500DistinguishedName
```

获取被吊销证书的颁发者的X.500可分辨名称对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md) | X.500可分辨名称对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

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

## getEncoded

```TypeScript
getEncoded(callback: AsyncCallback<EncodingBlob>): void
```

表示获取证书吊销条目的序列化数据。使用Callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md)&gt; | 是 | 回调函数。当获取证书吊销条目序列化数据成功时，err为undefined， data为获取到的证书吊销条目序列化数据；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';

// string转Uint8Array。
function stringToUint8Array(str: string): Uint8Array {
  let arr: Array<number> = [];
  for (let i = 0, j = str.length; i < j; i++) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

// 证书二进制数据，需业务自行赋值。
let certData = '-----BEGIN CERTIFICATE-----\n' +
  'MIIBHTCBwwICA+gwCgYIKoZIzj0EAwIwGjEYMBYGA1UEAwwPRXhhbXBsZSBSb290\n' +
  'IENBMB4XDTIzMDkwNTAyNDgyMloXDTI2MDUzMTAyNDgyMlowGjEYMBYGA1UEAwwP\n' +
  'RXhhbXBsZSBSb290IENBMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEHjG74yMI\n' +
  'ueO7z3T+dyuEIrhxTg2fqgeNB3SGfsIXlsiUfLTatUsU0i/sePnrKglj2H8Abbx9\n' +
  'PK0tsW/VgqwDIDAKBggqhkjOPQQDAgNJADBGAiEApVZno/Z7WyDc/muRN1y57uaY\n' +
  'Mjrgnvp/AMdE8qmFiDwCIQCrIYdHVO1awaPgcdALZY+uLQi6mEs/oMJLUcmaag3E\n' +
  'Qw==\n' +
  '-----END CERTIFICATE-----\n';

let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509Cert(encodingBlob, (error, x509Cert) => {
  if (error) {
    console.error(`createX509Cert failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createX509Cert result: success.');
    x509Cert.getEncoded((error, _data) => {
      if (error) {
        console.error(`getEncoded failed, errCode: ${error.code}, errMsg: ${error.message}`);
      } else {
        console.info('getEncoded result: success.');
      }
    });
  }
});
```

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';

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

// 证书吊销列表二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509Crl(encodingBlob, (error, x509Crl) => {
  if (error) {
    console.error(`createX509Crl failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createX509Crl result: success.');
    x509Crl.getEncoded((error, _data) => {
      if (error) {
        console.error(`getEncoded failed, errCode: ${error.code}, errMsg: ${error.message}`);
      } else {
        console.info('getEncoded result: success.');
      }
    });
  }
});
```

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';

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

// 证书吊销列表二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob, (error, x509CRL) => {
  if (error) {
    console.error(`createX509CRL failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createX509CRL result: success.');
    x509CRL.getEncoded((error, _data) => {
      if (error) {
        console.error(`getEncoded failed, errCode: ${error.code}, errMsg: ${error.message}`);
      } else {
        console.info('getEncoded result: success.');
      }
    });
  }
});
```

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

cert.createX509Crl(encodingBlob, (err, x509Crl) => {
  if (err) {
    console.error(`createX509Crl failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('create x509 crl result: success.');

    try {
      let serialNumber = 1000;
      let crlEntry = x509Crl.getRevokedCert(serialNumber);
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

## getEncoded

```TypeScript
getEncoded(): Promise<EncodingBlob>
```

表示获取证书吊销条目的序列化数据。使用Promise方式返回结果。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md)&gt; | Promise对象，返回证书吊销条目的序列化数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

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

// 证书二进制数据，需业务自行赋值。
let certData = '-----BEGIN CERTIFICATE-----\n' +
  'MIIBLzCB1QIUO/QDVJwZLIpeJyPjyTvE43xvE5cwCgYIKoZIzj0EAwIwGjEYMBYG\n' +
  'A1UEAwwPRXhhbXBsZSBSb290IENBMB4XDTIzMDkwNDExMjAxOVoXDTI2MDUzMDEx\n' +
  'MjAxOVowGjEYMBYGA1UEAwwPRXhhbXBsZSBSb290IENBMFkwEwYHKoZIzj0CAQYI\n' +
  'KoZIzj0DAQcDQgAEHjG74yMIueO7z3T+dyuEIrhxTg2fqgeNB3SGfsIXlsiUfLTa\n' +
  'tUsU0i/sePnrKglj2H8Abbx9PK0tsW/VgqwDIDAKBggqhkjOPQQDAgNJADBGAiEA\n' +
  '0ce/fvA4tckNZeB865aOApKXKlBjiRlaiuq5mEEqvNACIQDPD9WyC21MXqPBuRUf\n' +
  'BetUokslUfjT6+s/X4ByaxycAA==\n' +
  '-----END CERTIFICATE-----\n';

// 证书二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};
cert.createX509Cert(encodingBlob).then(x509Cert => {
  console.info('createX509Cert result: success.');
  x509Cert.getEncoded().then(_result => {
    console.info('getEncoded result: success.');
  }).catch((error: BusinessError) => {
    console.error(`getEncoded failed, errCode: ${error.code}, errMsg: ${error.message}`);
  });
}).catch((error: BusinessError) => {
  console.error(`createX509Cert failed, errCode: ${error.code}, errMsg: ${error.message}`);
});
```

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

// 证书吊销列表二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509Crl(encodingBlob).then(x509Crl => {
  console.info('createX509Crl result: success.');
  x509Crl.getEncoded().then(_result => {
    console.info('getEncoded result: success.');
  }).catch((error: BusinessError) => {
    console.error(`getEncoded failed, errCode: ${error.code}, errMsg: ${error.message}`);
  });
}).catch((error: BusinessError) => {
  console.error(`createX509Crl failed, errCode: ${error.code}, errMsg: ${error.message}`);
});
```

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

// 证书吊销列表二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob).then(x509CRL => {
  console.info('createX509CRL result: success.');
  x509CRL.getEncoded().then(_result => {
    console.info('getEncoded result: success.');
  }).catch((error: BusinessError) => {
    console.error(`getEncoded failed, errCode: ${error.code}, errMsg: ${error.message}`);
  });
}).catch((error: BusinessError) => {
  console.error(`createX509CRL failed, errCode: ${error.code}, errMsg: ${error.message}`);
});
```

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

cert.createX509Crl(encodingBlob, (err, x509Crl) => {
  if (err) {
    console.error(`createX509Crl failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('create x509 crl result: success.');

    try {
      let serialNumber = 1000;
      let crlEntry = x509Crl.getRevokedCert(serialNumber);
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

## getExtensions

```TypeScript
getExtensions(): DataBlob
```

表示获取DER格式的CRL条目的扩展数据。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示CRL条目的扩展数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

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

// 证书吊销列表二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob, (error, x509CRL) => {
  if (error) {
    console.error(`createX509CRL failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createX509CRL result: success.');
    try {
      let extensions = x509CRL.getExtensions();
      console.info('extensions = ' + extensions.data);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getExtensions failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

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

## getExtensionsObject

```TypeScript
getExtensionsObject(): CertExtension
```

获取CRL条目的扩展对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CertExtension](arkts-devicecertificate-cert-certextension-i.md) | CRL条目的扩展对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

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

let certData = '-----BEGIN CERTIFICATE-----\n' +
  'MIID1TCCAr2gAwIBAgIITXr1++kFUU4wDQYJKoZIhvcNAQELBQAwcDELMAkGA1UE\n' +
  'BhMCQ04xEjAQBgNVBAgTCWd1YW5nZG9uZzERMA8GA1UEBxMIc2hlbnpoZW4xEjAQ\n' +
  'BgNVBAoTCXRlc3RTZWNDYTESMBAGA1UECxMJdGVzdFNlY0NhMRIwEAYDVQQDEwl0\n' +
  'ZXN0U2VjQ2EwHhcNMjMxMjIxMDAwMDAwWhcNMjcxMjIwMjM1OTU5WjBxMQswCQYD\n' +
  'VQQGEwJDTjEOMAwGA1UECBMFZ2Fuc3UxEDAOBgNVBAcTB2xhbnpob3UxFDASBgNV\n' +
  'BAoTC3Rlc3RUaGlyZENhMRQwEgYDVQQLEwt0ZXN0VGhpcmRDYTEUMBIGA1UEAxML\n' +
  'dGVzdFRoaXJkQ2EwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDJMKSq\n' +
  'Fn4G4EJATauw+4s+n/JbINBAiuhzURzzdt2T8JJQLDV9RHj4mZt84yv6lqEpl2fm\n' +
  'gIClfu173pEV51/PSq5IaV481u/Dz/OTy9TwfxmIXAWdNpyodDOg4I9K7LC01ge8\n' +
  'xxyKFi7k7m2eTGA4dYQM0E0AEXzCpg2JN3IIIPhzHCIVJmYjcbVxiaFkvT4ZFFUk\n' +
  '4rDSbAQdn6dJ29msrFm8iGhMGC/bzq9Bii38Qg4y4o89QYiboRWCxv3XfuibT+jw\n' +
  'O3pmfsFuT8/bKOWVm94FmRxiKuj6iE8UVewxtByzDgAsBtJKDjaCv3IkqfbIu+sq\n' +
  '/eeJkVJRJXAP3ZpLAgMBAAGjcjBwMA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYE\n' +
  'FIxvPSwEmjOMW10H+gn2gy5HvMmMMAsGA1UdDwQEAwIBBjARBglghkgBhvhCAQEE\n' +
  'BAMCAAcwHgYJYIZIAYb4QgENBBEWD3hjYSBjZXJ0aWZpY2F0ZTANBgkqhkiG9w0B\n' +
  'AQsFAAOCAQEAWu0u72g5y1weexPoJQnUgcwVtuC+/tTS9YvyCtKYE91gn97LSWn9\n' +
  'mXXGmLceU27B8JwhER9JeiQO1SUdDcvlfb5vt6eB+5cbZcgeERUBP8t0znh7DbMg\n' +
  '4TFjt9gZ970PZ1OlTBNPoZNRBKIox61KVUhiVKTVSbXlVP1yUF1uSlSq+0NYayHw\n' +
  'MnX1BeLxbAcAsTPYHjoeFJIrGkKlydLyt/8hDQzpLRW5uEUTjjqLh7vef0OaOP80\n' +
  'MmADt6ojRYvwdMDHF0ASJyupLQ+hiRLVadciK8Z5W34JGN2jwEw5X3nXyAgErIJZ\n' +
  'pqdTflnFLnSwy5M3QHB+xjYAcS9l1br2LA==\n' +
  '-----END CERTIFICATE-----\n';

// 证书二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certGetExtensionsObject() {
  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    x509Cert.getExtensionsObject();
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509Cert failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

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
    'MIIB6DCB0QIBATANBgkqhkiG9w0BAQsFADCBjjELMAkGA1UEBhMCUlUxFTATBgNV\n' +
    'BAgMDNCc0L7RgdC60LLQsDELMAkGA1UECgwC0K8xCzAJBgNVBAsMAtCvMSowKAYD\n' +
    'VQQDDCHQlNC80LjRgtGA0LjQuSDQkdC10LvRj9Cy0YHQutC40LkxIjAgBgkqhkiG\n' +
    '9w0BCQEWE2JlbGRtaXRAZXhhbXBsZS5jb20XDTE3MDQyNDEzMjUzMVoXDTE3MDUy\n' +
    'NDEzMjUzMVqgDjAMMAoGA1UdFAQDAgEBMA0GCSqGSIb3DQEBCwUAA4IBAQCF5eX+\n' +
    '1BM/BxoHU2/3pQHJgPSKevN0/K/daiFHiJl7Kb9GCwKY14B1RvbN2rUP/58Mt+aq\n' +
    'jvauf1yBzlaJQeJKZcsCmG9p6Tr1y0BJXhrq5kC0SLyNDsfGUTfuxnwmo+clHXRU\n' +
    '+gKuk+h0WkJL022ZYbJ38w588k4NT3CWVHeE23EDC264p942mlDE7en6MyL152Pe\n' +
    'Ld9YrWiq5iOIOrIbQLErq0EjwxvHG9sMiYFUa6VrwmRf26nyZ7u9RKJDP+o2dltw\n' +
    'diBaSXC3Qt3pZ8BIfv/l81lwp8Dr63SwCII2pIRplyICdQqmX/a+1q8kThXIP2Kx\n' +
    '+X48g7VE2o2X4cfy\n' +
    '-----END X509 CRL-----\n';

// 证书吊销列表二进制数据，需业务自行赋值。
let crlEncodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function crlGetExtensionsObject() {
  let x509Crl: cert.X509CRL = {} as cert.X509CRL;
  try {
    x509Crl = await cert.createX509CRL(crlEncodingBlob);
    console.info('createX509CRL result: success.');
    x509Crl.getExtensionsObject();
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509CRL failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

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

## getRevocationDate

```TypeScript
getRevocationDate(): string
```

表示获取证书被吊销的日期。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示证书被吊销的日期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

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

cert.createX509Crl(encodingBlob, (err, x509Crl) => {
  if (err) {
    console.error(`createX509Crl failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('create x509 crl result: success.');

    try {
      let serialNumber = 1000;
      let crlEntry = x509Crl.getRevokedCert(serialNumber);
      let date = crlEntry.getRevocationDate();
      console.info('date = ' + date);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getRevokedCert or getRevocationDate failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

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

## getSerialNumber

```TypeScript
getSerialNumber(): bigint
```

表示获取被吊销的证书的序列号。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 表示证书吊销条目的序列号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

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

## hasExtensions

```TypeScript
hasExtensions(): boolean
```

表示判断CRL条目是否有扩展。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true则表示CRL条目有扩展，返回false则表示无扩展。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

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

## hashCode

```TypeScript
hashCode(): Uint8Array
```

获取DER格式数据的哈希值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | DER格式数据的哈希值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

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

let certData = '-----BEGIN CERTIFICATE-----\n' +
  'MIID1TCCAr2gAwIBAgIITXr1++kFUU4wDQYJKoZIhvcNAQELBQAwcDELMAkGA1UE\n' +
  'BhMCQ04xEjAQBgNVBAgTCWd1YW5nZG9uZzERMA8GA1UEBxMIc2hlbnpoZW4xEjAQ\n' +
  'BgNVBAoTCXRlc3RTZWNDYTESMBAGA1UECxMJdGVzdFNlY0NhMRIwEAYDVQQDEwl0\n' +
  'ZXN0U2VjQ2EwHhcNMjMxMjIxMDAwMDAwWhcNMjcxMjIwMjM1OTU5WjBxMQswCQYD\n' +
  'VQQGEwJDTjEOMAwGA1UECBMFZ2Fuc3UxEDAOBgNVBAcTB2xhbnpob3UxFDASBgNV\n' +
  'BAoTC3Rlc3RUaGlyZENhMRQwEgYDVQQLEwt0ZXN0VGhpcmRDYTEUMBIGA1UEAxML\n' +
  'dGVzdFRoaXJkQ2EwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDJMKSq\n' +
  'Fn4G4EJATauw+4s+n/JbINBAiuhzURzzdt2T8JJQLDV9RHj4mZt84yv6lqEpl2fm\n' +
  'gIClfu173pEV51/PSq5IaV481u/Dz/OTy9TwfxmIXAWdNpyodDOg4I9K7LC01ge8\n' +
  'xxyKFi7k7m2eTGA4dYQM0E0AEXzCpg2JN3IIIPhzHCIVJmYjcbVxiaFkvT4ZFFUk\n' +
  '4rDSbAQdn6dJ29msrFm8iGhMGC/bzq9Bii38Qg4y4o89QYiboRWCxv3XfuibT+jw\n' +
  'O3pmfsFuT8/bKOWVm94FmRxiKuj6iE8UVewxtByzDgAsBtJKDjaCv3IkqfbIu+sq\n' +
  '/eeJkVJRJXAP3ZpLAgMBAAGjcjBwMA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYE\n' +
  'FIxvPSwEmjOMW10H+gn2gy5HvMmMMAsGA1UdDwQEAwIBBjARBglghkgBhvhCAQEE\n' +
  'BAMCAAcwHgYJYIZIAYb4QgENBBEWD3hjYSBjZXJ0aWZpY2F0ZTANBgkqhkiG9w0B\n' +
  'AQsFAAOCAQEAWu0u72g5y1weexPoJQnUgcwVtuC+/tTS9YvyCtKYE91gn97LSWn9\n' +
  'mXXGmLceU27B8JwhER9JeiQO1SUdDcvlfb5vt6eB+5cbZcgeERUBP8t0znh7DbMg\n' +
  '4TFjt9gZ970PZ1OlTBNPoZNRBKIox61KVUhiVKTVSbXlVP1yUF1uSlSq+0NYayHw\n' +
  'MnX1BeLxbAcAsTPYHjoeFJIrGkKlydLyt/8hDQzpLRW5uEUTjjqLh7vef0OaOP80\n' +
  'MmADt6ojRYvwdMDHF0ASJyupLQ+hiRLVadciK8Z5W34JGN2jwEw5X3nXyAgErIJZ\n' +
  'pqdTflnFLnSwy5M3QHB+xjYAcS9l1br2LA==\n' +
  '-----END CERTIFICATE-----\n';

// 证书二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certHashCode() {
  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    console.info('certHashCode success: ' + x509Cert.hashCode());
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509Cert failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

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

// 证书吊销列表二进制数据，需业务自行赋值。
let crlEncodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function crlHashCode() {
  let x509Crl: cert.X509CRL = {} as cert.X509CRL;
  try {
    x509Crl = await cert.createX509CRL(crlEncodingBlob);
    console.info('createX509CRL result: success.');
    console.info('crlHashCode success: ' + x509Crl.hashCode());
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509CRL failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

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

let certChainData = '-----BEGIN CERTIFICATE-----\n' +
  'MIIGVjCCBT6gAwIBAgIQBMO0W3CU9LWVw1bE/jqYojANBgkqhkiG9w0BAQsFADBE\n' +
  'MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMRGlnaUNlcnQgSW5jMR4wHAYDVQQDExVH\n' +
  'ZW9UcnVzdCBSU0EgQ04gQ0EgRzIwHhcNMjMwMzIzMDAwMDAwWhcNMjQwNDIyMjM1\n' +
  'OTU5WjB1MQswCQYDVQQGEwJDTjERMA8GA1UECBMIemhlamlhbmcxETAPBgNVBAcT\n' +
  'CGhhbmd6aG91MSwwKgYDVQQKEyNOZXRFYXNlIChIYW5nemhvdSkgTmV0d29yayBD\n' +
  'by4sIEx0ZDESMBAGA1UEAwwJKi4xNjMuY29tMIIBIjANBgkqhkiG9w0BAQEFAAOC\n' +
  'AQ8AMIIBCgKCAQEAwELks0Q1Z81u1OpbGdEFE2Snm/WpLfmiC5YFj5nFrinSX+UZ\n' +
  'MIk42euBdjYSsWFxbljmWDdUCjstMhG8vRAjz3Nt1QniMCunHHFGujR5rSNLWYHE\n' +
  'vCPhfptIhqOaE/rvkWGZZr2KjTQQN0dRf8dm9Oewy8DHu95c9jW6c9AVgKWUVOni\n' +
  'tTOcJCnrndWjgCIPfKmKgrwaNaMnuQyy5nPIUHl/5EGzuGHrwjwlF+w+cT+Fwdix\n' +
  'C3msEOCwX6wzo6baDs4og2EzuPNyTp4n4UqH5aHhLePgBFboOAyJwWp3+XJNpNGw\n' +
  'GkU56cUUy7+AAn268EVvUNr7uQ65t2t+Ys32bQIDAQABo4IDETCCAw0wHwYDVR0j\n' +
  'BBgwFoAUJG+RP4mHhw4ywkAY38VM60/ISTIwHQYDVR0OBBYEFD1HyRYJ5jqkvYL7\n' +
  'C6TSt8/y3e7hMB0GA1UdEQQWMBSCCSouMTYzLmNvbYIHMTYzLmNvbTAOBgNVHQ8B\n' +
  'Af8EBAMCBaAwHQYDVR0lBBYwFAYIKwYBBQUHAwEGCCsGAQUFBwMCMD0GA1UdHwQ2\n' +
  'MDQwMqAwoC6GLGh0dHA6Ly9jcmwuZGlnaWNlcnQuY24vR2VvVHJ1c3RSU0FDTkNB\n' +
  'RzIuY3JsMD4GA1UdIAQ3MDUwMwYGZ4EMAQICMCkwJwYIKwYBBQUHAgEWG2h0dHA6\n' +
  'Ly93d3cuZGlnaWNlcnQuY29tL0NQUzBxBggrBgEFBQcBAQRlMGMwIwYIKwYBBQUH\n' +
  'MAGGF2h0dHA6Ly9vY3NwLmRpZ2ljZXJ0LmNuMDwGCCsGAQUFBzAChjBodHRwOi8v\n' +
  'Y2FjZXJ0cy5kaWdpY2VydC5jbi9HZW9UcnVzdFJTQUNOQ0FHMi5jcnQwCQYDVR0T\n' +
  'BAIwADCCAX4GCisGAQQB1nkCBAIEggFuBIIBagFoAHUA7s3QZNXbGs7FXLedtM0T\n' +
  'ojKHRny87N7DUUhZRnEftZsAAAGHDSE15QAABAMARjBEAiBRpmsJ3F9AI8wFxqOQ\n' +
  'bHp+RL6F8cvNydajQ0Bqxjvd3AIgefAU/po3jBm+96dFVdbX+AG1uss67DL3VL5I\n' +
  'nUmVva8AdgBz2Z6JG0yWeKAgfUed5rLGHNBRXnEZKoxrgBB6wXdytQAAAYcNITZS\n' +
  'AAAEAwBHMEUCID/sUP12odF7uTTEyE0PjCpKo3nF7A3ba3b5wJJsZrDrAiEAxrat\n' +
  'W2eeZTD458LPSPrMMBb1/o6zibWXqJCQye+bVFwAdwBIsONr2qZHNA/lagL6nTDr\n' +
  'HFIBy1bdLIHZu7+rOdiEcwAAAYcNITYeAAAEAwBIMEYCIQCCJ2ktM1F+d1I5mQju\n' +
  'Tn7oDYxy3GCGyG3u/yhu8k7EaAIhANSP8cAaMQFV6y8B2tubKY5eSQtgkF3a6NNq\n' +
  'QJjtPnoHMA0GCSqGSIb3DQEBCwUAA4IBAQC8dK/G4nvs/SyQe/mnK+rUYIdSFs+4\n' +
  'lgzatmq8V/I1tBly+Sv/FPhnn4F3iCrqy9j8y202FP51ev95DGbjlJRTIFPqVAO8\n' +
  'ywYrLhvl1SJhV0b/8NF0Pr3dZVnK5Vfn11+LSBUg0cBB2hcVV30nv3IuVhz3d12n\n' +
  'P+VseYQgMpQf7ad+ttpZtA7yqHzrUm4fzr03G7q88GztACRSHoYiPbOlz99SeTgW\n' +
  '7bzZl1I4taxy2Q3b0ZBGfUt/kPY05tpKzKwDTbbqSErYszCt5X1RfVvf3coxF8Mo\n' +
  '9bHbs2wYIzQBdujDQ/hU0u6ItERer3SUItZoxaSIxdrZ9eXFwVvXsT/g\n' +
  '-----END CERTIFICATE-----\n' +
  '-----BEGIN CERTIFICATE-----\n' +
  'MIIFDzCCA/egAwIBAgIQCxNitu5qnT6WiTDxbiB9OTANBgkqhkiG9w0BAQsFADBh\n' +
  'MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMRGlnaUNlcnQgSW5jMRkwFwYDVQQLExB3\n' +
  'd3cuZGlnaWNlcnQuY29tMSAwHgYDVQQDExdEaWdpQ2VydCBHbG9iYWwgUm9vdCBD\n' +
  'QTAeFw0yMDAzMDQxMjA0NDBaFw0zMDAzMDQxMjA0NDBaMEQxCzAJBgNVBAYTAlVT\n' +
  'MRUwEwYDVQQKEwxEaWdpQ2VydCBJbmMxHjAcBgNVBAMTFUdlb1RydXN0IFJTQSBD\n' +
  'TiBDQSBHMjCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBANA1OZJJtZUI\n' +
  '7zj4qFHT79g+Otks4TEfmUEDhrNKBEEjb/i29GBfnpvFdT36azCg2VODJRSjIzFn\n' +
  '4qADcc84EmfKiDEM97HFsQPp9RRkqxH5cB51EU2eBE9Ua95x+wQp/KSdCqITCQ/v\n' +
  'yvm3J4Upjl0wlW8wRCPCWcYw3pKClGRkNzVtI1KXnfpn7fG3N84n7wlBb9IGKJFa\n' +
  'c/6+hxvZx2qnfLsxdIKR0Q/biGoU6Z8Iy/R/p7GoPO8vamV090+QHEL5AdSzKtEh\n' +
  'U9vdvcuWjjLxVnaJLfj/6WoGZj8UWn3zFbEoTVaAfp2xqdzW7yRvi2r148m9ev7l\n' +
  'jDqHo8UX69sCAwEAAaOCAd4wggHaMB0GA1UdDgQWBBQkb5E/iYeHDjLCQBjfxUzr\n' +
  'T8hJMjAfBgNVHSMEGDAWgBQD3lA1VtFMu2bwo+IbG8OXsj3RVTAOBgNVHQ8BAf8E\n' +
  'BAMCAYYwHQYDVR0lBBYwFAYIKwYBBQUHAwEGCCsGAQUFBwMCMBIGA1UdEwEB/wQI\n' +
  'MAYBAf8CAQAwMwYIKwYBBQUHAQEEJzAlMCMGCCsGAQUFBzABhhdodHRwOi8vb2Nz\n' +
  'cC5kaWdpY2VydC5jbjBABgNVHR8EOTA3MDWgM6Axhi9odHRwOi8vY3JsLmRpZ2lj\n' +
  'ZXJ0LmNuL0RpZ2lDZXJ0R2xvYmFsUm9vdENBLmNybDCB3QYDVR0gBIHVMIHSMIHF\n' +
  'BglghkgBhv1sAQEwgbcwKAYIKwYBBQUHAgEWHGh0dHBzOi8vd3d3LmRpZ2ljZXJ0\n' +
  'LmNvbS9DUFMwgYoGCCsGAQUFBwICMH4MfEFueSB1c2Ugb2YgdGhpcyBDZXJ0aWZp\n' +
  'Y2F0ZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9mIHRoZSBSZWx5aW5nIFBhcnR5\n' +
  'IEFncmVlbWVudCBsb2NhdGVkIGF0IGh0dHBzOi8vd3d3LmRpZ2ljZXJ0LmNvbS9y\n' +
  'cGEtdWEwCAYGZ4EMAQICMA0GCSqGSIb3DQEBCwUAA4IBAQCzkcXq0TN0oSn4UeXp\n' +
  'FBW7U8zrHBIhH9MXHNBp+Yy/yN19133UY05uuHXHaU2Uv0hxefckjPdkaX7ARso+\n' +
  'O3Ar6nf7YfBwCqSpqsNckKT7KKtf3Ot95wYFpKDa64jcRUfxzRWnmq12IVzczqHI\n' +
  'sIvUZQINw/UHSQcWekdUnMg58bQSHyTjwkj9jcX2RURxaVZkr15wxo/Z3Ydo2PVK\n' +
  '3afEr0/vcuFvE7QeGXiI2DJdVt3JefatZ3rj4VTW2aUZwHGUiWWIUudBfQKR0JEp\n' +
  'lJ8MFaKDh4/A2VEJnXILu1iwvc1m3jCaPuzZKdoHM/1234bznJI2aAfhfIhoHw90\n' +
  'tPO+\n' +
  '-----END CERTIFICATE-----\n';

// 证书链二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certChainData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM、FORMAT_DER和FORMAT_PKCS7。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certChainHashCode() {
  let x509CertChain: cert.X509CertChain = {} as cert.X509CertChain;
  try {
    x509CertChain = await cert.createX509CertChain(encodingBlob);
    console.info('createX509CertChain result: success.');
    console.info('hashCode success: ' + x509CertChain.hashCode());
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX509CertChain failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

## toString

```TypeScript
toString(): string
```

获取对象的字符串类型数据。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 对象的字符串类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

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

let certData = '-----BEGIN CERTIFICATE-----\n' +
  'MIID1TCCAr2gAwIBAgIITXr1++kFUU4wDQYJKoZIhvcNAQELBQAwcDELMAkGA1UE\n' +
  'BhMCQ04xEjAQBgNVBAgTCWd1YW5nZG9uZzERMA8GA1UEBxMIc2hlbnpoZW4xEjAQ\n' +
  'BgNVBAoTCXRlc3RTZWNDYTESMBAGA1UECxMJdGVzdFNlY0NhMRIwEAYDVQQDEwl0\n' +
  'ZXN0U2VjQ2EwHhcNMjMxMjIxMDAwMDAwWhcNMjcxMjIwMjM1OTU5WjBxMQswCQYD\n' +
  'VQQGEwJDTjEOMAwGA1UECBMFZ2Fuc3UxEDAOBgNVBAcTB2xhbnpob3UxFDASBgNV\n' +
  'BAoTC3Rlc3RUaGlyZENhMRQwEgYDVQQLEwt0ZXN0VGhpcmRDYTEUMBIGA1UEAxML\n' +
  'dGVzdFRoaXJkQ2EwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDJMKSq\n' +
  'Fn4G4EJATauw+4s+n/JbINBAiuhzURzzdt2T8JJQLDV9RHj4mZt84yv6lqEpl2fm\n' +
  'gIClfu173pEV51/PSq5IaV481u/Dz/OTy9TwfxmIXAWdNpyodDOg4I9K7LC01ge8\n' +
  'xxyKFi7k7m2eTGA4dYQM0E0AEXzCpg2JN3IIIPhzHCIVJmYjcbVxiaFkvT4ZFFUk\n' +
  '4rDSbAQdn6dJ29msrFm8iGhMGC/bzq9Bii38Qg4y4o89QYiboRWCxv3XfuibT+jw\n' +
  'O3pmfsFuT8/bKOWVm94FmRxiKuj6iE8UVewxtByzDgAsBtJKDjaCv3IkqfbIu+sq\n' +
  '/eeJkVJRJXAP3ZpLAgMBAAGjcjBwMA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYE\n' +
  'FIxvPSwEmjOMW10H+gn2gy5HvMmMMAsGA1UdDwQEAwIBBjARBglghkgBhvhCAQEE\n' +
  'BAMCAAcwHgYJYIZIAYb4QgENBBEWD3hjYSBjZXJ0aWZpY2F0ZTANBgkqhkiG9w0B\n' +
  'AQsFAAOCAQEAWu0u72g5y1weexPoJQnUgcwVtuC+/tTS9YvyCtKYE91gn97LSWn9\n' +
  'mXXGmLceU27B8JwhER9JeiQO1SUdDcvlfb5vt6eB+5cbZcgeERUBP8t0znh7DbMg\n' +
  '4TFjt9gZ970PZ1OlTBNPoZNRBKIox61KVUhiVKTVSbXlVP1yUF1uSlSq+0NYayHw\n' +
  'MnX1BeLxbAcAsTPYHjoeFJIrGkKlydLyt/8hDQzpLRW5uEUTjjqLh7vef0OaOP80\n' +
  'MmADt6ojRYvwdMDHF0ASJyupLQ+hiRLVadciK8Z5W34JGN2jwEw5X3nXyAgErIJZ\n' +
  'pqdTflnFLnSwy5M3QHB+xjYAcS9l1br2LA==\n' +
  '-----END CERTIFICATE-----\n';

// 证书二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certToString() {
  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    console.info('certToString success: ' + x509Cert.toString());
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509Cert failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

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

// 证书吊销列表二进制数据，需业务自行赋值。
let crlEncodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function crlToString() {
  let x509Crl: cert.X509CRL = {} as cert.X509CRL;
  try {
    x509Crl = await cert.createX509CRL(crlEncodingBlob);
    console.info('createX509CRL result: success.');
    console.info('crlToString success: ' + x509Crl.toString());
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509CRL failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

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

let certChainData = '-----BEGIN CERTIFICATE-----\n' +
  'MIIGVjCCBT6gAwIBAgIQBMO0W3CU9LWVw1bE/jqYojANBgkqhkiG9w0BAQsFADBE\n' +
  'MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMRGlnaUNlcnQgSW5jMR4wHAYDVQQDExVH\n' +
  'ZW9UcnVzdCBSU0EgQ04gQ0EgRzIwHhcNMjMwMzIzMDAwMDAwWhcNMjQwNDIyMjM1\n' +
  'OTU5WjB1MQswCQYDVQQGEwJDTjERMA8GA1UECBMIemhlamlhbmcxETAPBgNVBAcT\n' +
  'CGhhbmd6aG91MSwwKgYDVQQKEyNOZXRFYXNlIChIYW5nemhvdSkgTmV0d29yayBD\n' +
  'by4sIEx0ZDESMBAGA1UEAwwJKi4xNjMuY29tMIIBIjANBgkqhkiG9w0BAQEFAAOC\n' +
  'AQ8AMIIBCgKCAQEAwELks0Q1Z81u1OpbGdEFE2Snm/WpLfmiC5YFj5nFrinSX+UZ\n' +
  'MIk42euBdjYSsWFxbljmWDdUCjstMhG8vRAjz3Nt1QniMCunHHFGujR5rSNLWYHE\n' +
  'vCPhfptIhqOaE/rvkWGZZr2KjTQQN0dRf8dm9Oewy8DHu95c9jW6c9AVgKWUVOni\n' +
  'tTOcJCnrndWjgCIPfKmKgrwaNaMnuQyy5nPIUHl/5EGzuGHrwjwlF+w+cT+Fwdix\n' +
  'C3msEOCwX6wzo6baDs4og2EzuPNyTp4n4UqH5aHhLePgBFboOAyJwWp3+XJNpNGw\n' +
  'GkU56cUUy7+AAn268EVvUNr7uQ65t2t+Ys32bQIDAQABo4IDETCCAw0wHwYDVR0j\n' +
  'BBgwFoAUJG+RP4mHhw4ywkAY38VM60/ISTIwHQYDVR0OBBYEFD1HyRYJ5jqkvYL7\n' +
  'C6TSt8/y3e7hMB0GA1UdEQQWMBSCCSouMTYzLmNvbYIHMTYzLmNvbTAOBgNVHQ8B\n' +
  'Af8EBAMCBaAwHQYDVR0lBBYwFAYIKwYBBQUHAwEGCCsGAQUFBwMCMD0GA1UdHwQ2\n' +
  'MDQwMqAwoC6GLGh0dHA6Ly9jcmwuZGlnaWNlcnQuY24vR2VvVHJ1c3RSU0FDTkNB\n' +
  'RzIuY3JsMD4GA1UdIAQ3MDUwMwYGZ4EMAQICMCkwJwYIKwYBBQUHAgEWG2h0dHA6\n' +
  'Ly93d3cuZGlnaWNlcnQuY29tL0NQUzBxBggrBgEFBQcBAQRlMGMwIwYIKwYBBQUH\n' +
  'MAGGF2h0dHA6Ly9vY3NwLmRpZ2ljZXJ0LmNuMDwGCCsGAQUFBzAChjBodHRwOi8v\n' +
  'Y2FjZXJ0cy5kaWdpY2VydC5jbi9HZW9UcnVzdFJTQUNOQ0FHMi5jcnQwCQYDVR0T\n' +
  'BAIwADCCAX4GCisGAQQB1nkCBAIEggFuBIIBagFoAHUA7s3QZNXbGs7FXLedtM0T\n' +
  'ojKHRny87N7DUUhZRnEftZsAAAGHDSE15QAABAMARjBEAiBRpmsJ3F9AI8wFxqOQ\n' +
  'bHp+RL6F8cvNydajQ0Bqxjvd3AIgefAU/po3jBm+96dFVdbX+AG1uss67DL3VL5I\n' +
  'nUmVva8AdgBz2Z6JG0yWeKAgfUed5rLGHNBRXnEZKoxrgBB6wXdytQAAAYcNITZS\n' +
  'AAAEAwBHMEUCID/sUP12odF7uTTEyE0PjCpKo3nF7A3ba3b5wJJsZrDrAiEAxrat\n' +
  'W2eeZTD458LPSPrMMBb1/o6zibWXqJCQye+bVFwAdwBIsONr2qZHNA/lagL6nTDr\n' +
  'HFIBy1bdLIHZu7+rOdiEcwAAAYcNITYeAAAEAwBIMEYCIQCCJ2ktM1F+d1I5mQju\n' +
  'Tn7oDYxy3GCGyG3u/yhu8k7EaAIhANSP8cAaMQFV6y8B2tubKY5eSQtgkF3a6NNq\n' +
  'QJjtPnoHMA0GCSqGSIb3DQEBCwUAA4IBAQC8dK/G4nvs/SyQe/mnK+rUYIdSFs+4\n' +
  'lgzatmq8V/I1tBly+Sv/FPhnn4F3iCrqy9j8y202FP51ev95DGbjlJRTIFPqVAO8\n' +
  'ywYrLhvl1SJhV0b/8NF0Pr3dZVnK5Vfn11+LSBUg0cBB2hcVV30nv3IuVhz3d12n\n' +
  'P+VseYQgMpQf7ad+ttpZtA7yqHzrUm4fzr03G7q88GztACRSHoYiPbOlz99SeTgW\n' +
  '7bzZl1I4taxy2Q3b0ZBGfUt/kPY05tpKzKwDTbbqSErYszCt5X1RfVvf3coxF8Mo\n' +
  '9bHbs2wYIzQBdujDQ/hU0u6ItERer3SUItZoxaSIxdrZ9eXFwVvXsT/g\n' +
  '-----END CERTIFICATE-----\n' +
  '-----BEGIN CERTIFICATE-----\n' +
  'MIIFDzCCA/egAwIBAgIQCxNitu5qnT6WiTDxbiB9OTANBgkqhkiG9w0BAQsFADBh\n' +
  'MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMRGlnaUNlcnQgSW5jMRkwFwYDVQQLExB3\n' +
  'd3cuZGlnaWNlcnQuY29tMSAwHgYDVQQDExdEaWdpQ2VydCBHbG9iYWwgUm9vdCBD\n' +
  'QTAeFw0yMDAzMDQxMjA0NDBaFw0zMDAzMDQxMjA0NDBaMEQxCzAJBgNVBAYTAlVT\n' +
  'MRUwEwYDVQQKEwxEaWdpQ2VydCBJbmMxHjAcBgNVBAMTFUdlb1RydXN0IFJTQSBD\n' +
  'TiBDQSBHMjCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBANA1OZJJtZUI\n' +
  '7zj4qFHT79g+Otks4TEfmUEDhrNKBEEjb/i29GBfnpvFdT36azCg2VODJRSjIzFn\n' +
  '4qADcc84EmfKiDEM97HFsQPp9RRkqxH5cB51EU2eBE9Ua95x+wQp/KSdCqITCQ/v\n' +
  'yvm3J4Upjl0wlW8wRCPCWcYw3pKClGRkNzVtI1KXnfpn7fG3N84n7wlBb9IGKJFa\n' +
  'c/6+hxvZx2qnfLsxdIKR0Q/biGoU6Z8Iy/R/p7GoPO8vamV090+QHEL5AdSzKtEh\n' +
  'U9vdvcuWjjLxVnaJLfj/6WoGZj8UWn3zFbEoTVaAfp2xqdzW7yRvi2r148m9ev7l\n' +
  'jDqHo8UX69sCAwEAAaOCAd4wggHaMB0GA1UdDgQWBBQkb5E/iYeHDjLCQBjfxUzr\n' +
  'T8hJMjAfBgNVHSMEGDAWgBQD3lA1VtFMu2bwo+IbG8OXsj3RVTAOBgNVHQ8BAf8E\n' +
  'BAMCAYYwHQYDVR0lBBYwFAYIKwYBBQUHAwEGCCsGAQUFBwMCMBIGA1UdEwEB/wQI\n' +
  'MAYBAf8CAQAwMwYIKwYBBQUHAQEEJzAlMCMGCCsGAQUFBzABhhdodHRwOi8vb2Nz\n' +
  'cC5kaWdpY2VydC5jbjBABgNVHR8EOTA3MDWgM6Axhi9odHRwOi8vY3JsLmRpZ2lj\n' +
  'ZXJ0LmNuL0RpZ2lDZXJ0R2xvYmFsUm9vdENBLmNybDCB3QYDVR0gBIHVMIHSMIHF\n' +
  'BglghkgBhv1sAQEwgbcwKAYIKwYBBQUHAgEWHGh0dHBzOi8vd3d3LmRpZ2ljZXJ0\n' +
  'LmNvbS9DUFMwgYoGCCsGAQUFBwICMH4MfEFueSB1c2Ugb2YgdGhpcyBDZXJ0aWZp\n' +
  'Y2F0ZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9mIHRoZSBSZWx5aW5nIFBhcnR5\n' +
  'IEFncmVlbWVudCBsb2NhdGVkIGF0IGh0dHBzOi8vd3d3LmRpZ2ljZXJ0LmNvbS9y\n' +
  'cGEtdWEwCAYGZ4EMAQICMA0GCSqGSIb3DQEBCwUAA4IBAQCzkcXq0TN0oSn4UeXp\n' +
  'FBW7U8zrHBIhH9MXHNBp+Yy/yN19133UY05uuHXHaU2Uv0hxefckjPdkaX7ARso+\n' +
  'O3Ar6nf7YfBwCqSpqsNckKT7KKtf3Ot95wYFpKDa64jcRUfxzRWnmq12IVzczqHI\n' +
  'sIvUZQINw/UHSQcWekdUnMg58bQSHyTjwkj9jcX2RURxaVZkr15wxo/Z3Ydo2PVK\n' +
  '3afEr0/vcuFvE7QeGXiI2DJdVt3JefatZ3rj4VTW2aUZwHGUiWWIUudBfQKR0JEp\n' +
  'lJ8MFaKDh4/A2VEJnXILu1iwvc1m3jCaPuzZKdoHM/1234bznJI2aAfhfIhoHw90\n' +
  'tPO+\n' +
  '-----END CERTIFICATE-----\n';

// 证书链二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certChainData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM、FORMAT_DER和FORMAT_PKCS7。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certChainToString() {
  let x509CertChain: cert.X509CertChain = {} as cert.X509CertChain;
  try {
    x509CertChain = await cert.createX509CertChain(encodingBlob);
    console.info('createX509CertChain result: success.');
    console.info('toString success: ' + x509CertChain.toString());
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX509CertChain failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```
