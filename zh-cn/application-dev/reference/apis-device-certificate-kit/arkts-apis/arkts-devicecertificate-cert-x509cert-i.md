# X509Cert

提供用于X.509证书操作的API。

**起始版本：** 9

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
```

## checkValidityWithDate

```TypeScript
checkValidityWithDate(date: string): void
```

表示校验X.509证书有效期。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | string | 是 | 表示日期，日期采用ASN.1 UTCTime或GeneralizedTime格式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |
| [19030003](../errorcode-cert.md#19030003-证书尚未生效) | The certificate has not taken effect. |
| [19030004](../errorcode-cert.md#19030004-证书过期) | The certificate has expired. |

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

    let date = '231001000001Z';
    // Verify the certificate validity period.
    try {
      x509Cert.checkValidityWithDate(date);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`checkValidityWithDate failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getBasicConstraints

```TypeScript
getBasicConstraints(): number
```

表示获取X.509证书基本约束。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 表示X.509证书基本约束。 |

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
    let basicConstraints = x509Cert.getBasicConstraints();
    console.info('basicConstraints = ' + basicConstraints);
  }
});
```

## getCertSerialNumber

```TypeScript
getCertSerialNumber(): bigint
```

表示获取X.509证书序列号。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 表示X.509证书序列号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |

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
    try {
      let serialNumber = x509Cert.getCertSerialNumber();
      console.info('serialNumber = ' + serialNumber);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getCertSerialNumber failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getCRLDistributionPoint

```TypeScript
getCRLDistributionPoint(): DataArray
```

获取X.509证书CRL的分发点统一资源标识符。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | 表示X.509证书CRL的分发点统一资源标识符。 |

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
  'MIIB/jCCAaSgAwIBAgICA+gwCgYIKoZIzj0EAwIwLDELMAkGA1UEBhMCQ04xDTAL\n' +
  'BgNVBAoMBHRlc3QxDjAMBgNVBAMMBXN1YmNhMB4XDTIzMTAwNzA0MDEwOFoXDTMz\n' +
  'MTAwNDA0MDEwOFowLDELMAkGA1UEBhMCQ04xDTALBgNVBAoMBHRlc3QxDjAMBgNV\n' +
  'BAMMBWxvY2FsMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEZDPvdlJI6Yv4fiaR\n' +
  'nQHcusXVbukk90mQ0rBGOYRikFvgvm5cjTdaUGcQKEtwYIKDQl5n6Pf7ElCJ7GRz\n' +
  'raWZ+qOBtTCBsjAJBgNVHRMEAjAAMCwGCWCGSAGG+EIBDQQfFh1PcGVuU1NMIEdl\n' +
  'bmVyYXRlZCBDZXJ0aWZpY2F0ZTAdBgNVHQ4EFgQU63Gbl8gIsUn0VyZ4rya3PCjm\n' +
  'sfEwHwYDVR0jBBgwFoAU77mynM0rz1SD43DQjleWM7bF+MEwNwYDVR0fBDAwLjAs\n' +
  'oCqgKIYmaHR0cDovL3Rlc3QudGVzdENSTGRwLmNvbS9DUkxfRFBfMS5jcmwwCgYI\n' +
  'KoZIzj0EAwIDSAAwRQIhAISKHH9u221mBgdDWfll3loLvEHJ3or9NUO5Zn6SrX6L\n' +
  'AiAtRlOa6/mTD68faQTdhsAaQP955QfW34B4yFqU2Bq72A==\n' +
  '-----END CERTIFICATE-----\n';

// 证书二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certGetCRLDistributionPoint() {
  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    let point = x509Cert.getCRLDistributionPoint();
    console.info('point = ' + point.data);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509Cert failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

## getEncoded

```TypeScript
getEncoded(callback: AsyncCallback<EncodingBlob>): void
```

表示获取X.509证书序列化数据。使用Callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md)&gt; | 是 | 回调函数。当获取X.509证书序列化数据成功时，err为undefined，data为 获取到的X.509证书序列化数据；否则为错误对象。 |

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

表示获取X.509证书序列化数据。使用Promise方式返回结果。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md)&gt; | Promise对象，返回X.509证书序列化数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
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

## getExtensionsObject

```TypeScript
getExtensionsObject(): CertExtension
```

获取证书扩展对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CertExtension](arkts-devicecertificate-cert-certextension-i.md) | 证书扩展对象。 |

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

## getExtKeyUsage

```TypeScript
getExtKeyUsage(): DataArray
```

表示获取X.509证书扩展密钥用途。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | 表示X.509证书扩展密钥用途。 |

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

// 证书二进制数据，需业务自行赋值。
let certData = '-----BEGIN CERTIFICATE-----\n' +
    'MIIDNDCCAhygAwIBAgIUJBLt/gmdgnDAq21wWU4R7rzgE5cwDQYJKoZIhvcNAQEL\n' +
    'BQAwGjEYMBYGA1UEAwwPRXhhbXBsZSBSb290IENBMB4XDTI1MTAzMDAyMzMxOVoX\n' +
    'DTI2MTAzMDAyMzMxOVowGjEYMBYGA1UEAwwPRXhhbXBsZSBSb290IENBMIIBIjAN\n' +
    'BgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA0p3wb2jK23w+mihsah0w4wRaJ1TC\n' +
    'YC20ODjSHyyCL75XfR6n87DdXvb15a71hkD/1cdgDRxIO91hNu04Ru4MFL0CqgTM\n' +
    'ERSwZZGVo9DzJSG5q22FgbIFPi+XpTPtKk7mOCggPsfIrV1G0OH9zTREWoZ2/fJD\n' +
    'Pj0MiaPlYtS4Jolu0qDnRZjgP8yVdaV4Upvni1PNX60rZfhf5YC4yvkMmpnyoUOZ\n' +
    'IS3I/QucXZaiwXAO4ziHjYXtlp2aeUnrWSoRs3sFrsIVGB9x0ZYjwCwiih9TqaBK\n' +
    'SY1CKSQE5xjVP1uY5JwJ6A5N648J3JjGosYEsXT+WieJ4SGHafGa2DGd2wIDAQAB\n' +
    'o3IwcDAdBgNVHQ4EFgQUDyuOK1aix/tBR3QViD7TYdrDUQEwHwYDVR0jBBgwFoAU\n' +
    'DyuOK1aix/tBR3QViD7TYdrDUQEwDwYDVR0TAQH/BAUwAwEB/zAdBgNVHSUEFjAU\n' +
    'BggrBgEFBQcDAQYIKwYBBQUHAwIwDQYJKoZIhvcNAQELBQADggEBAC0A7HqO/OL0\n' +
    'Ve8HTUqM31hFxXYiqDum/gPiegXDA+9ixEP2Fjz8vmhe75FX5XOvCk0+FWRayoVw\n' +
    'lc7TD7SfV/oHRZVY58H8+Qxe5Rf4xQfOBNpG81uz73gfq3zIbzfJXxWlUpnBs6Tf\n' +
    'P44NZboLpgaA0eMI7NwZJyomZ98qOK3PmxBL9qATmDep2GM6VlOuapYh2fo8wFhY\n' +
    'DSp2EmcbIN9F+RPNrP+BvM/x2ZBtBoSFLh8jQ+GnP6g26DL57JBuBemt00BuYLOg\n' +
    'fF00YBUgwK9tIFfI5IAfrwEF8Y49XIzpXrHuMZZXbuESzQMBsAZAYqIgi2p5dAon\n' +
    'gdg3C4I6QRY=\n' +
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
    try {
      let extKeyUsage = x509Cert.getExtKeyUsage();
      console.info('extKeyUsage = ' + extKeyUsage.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getExtKeyUsage failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getIssuerAltNames

```TypeScript
getIssuerAltNames(): DataArray
```

表示获取X.509证书颁发者可选名称。

> **说明：**
> 
> 获取到的X.509证书颁发者可选名称数据带字符串结束符。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | 表示X.509证书颁发者可选名称。 |

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

// 证书二进制数据，需业务自行赋值。
let certData = '-----BEGIN CERTIFICATE-----\n' +
    'MIIC9zCCAd+gAwIBAgIUS3GIfzu10vWzw2RSLbxTxxMfz/wwDQYJKoZIhvcNAQEL\n' +
    'BQAwGjEYMBYGA1UEAwwPRXhhbXBsZSBSb290IENBMB4XDTI1MTAzMDAyNDkzNFoX\n' +
    'DTI2MTAzMDAyNDkzNFowGjEYMBYGA1UEAwwPRXhhbXBsZSBSb290IENBMIIBIjAN\n' +
    'BgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAvKGnKn9NZoFOzdffrCIE01dTCiIo\n' +
    'XPweKanLs49ZaxpEJ48OCP4vs8qmedsW1pUMpe7kQQyRINZ5tvXyFbiBS1u4clN/\n' +
    'nU+E8rhNMa+2LA2YOUH/fC1ikussXq+acqjEqRbM900QdkmPzJX3NcloGYwdVfAe\n' +
    '3ENEXHaXvj1qrf6pF5mbdelnlp1TrjpnXT4sSQaKbFjZrNl+zTT4xbIxTHR0cB8S\n' +
    'oOVc3jI57rtP6x0FcLWzE/LX1E8eUkCIHEapPjqsGzLNtJTJI8z9QLinFIRmjdSI\n' +
    '0xS8Qj/QitrOswzjHie2fgaz1LZx76CZGExC5f6f3Em5hJx6rjYysmEZBQIDAQAB\n' +
    'ozUwMzAxBgNVHRIEKjAogRJpc3N1ZXJAZXhhbXBsZS5jb22CEmlzc3Vlci5leGFt\n' +
    'cGxlLmNvbTANBgkqhkiG9w0BAQsFAAOCAQEAI5UjPssP3VzV2m47ke2nytAsTt9Y\n' +
    'DNYKhqM4qZVVaIj5BRmca1jJXnWAgV4uUbad92E7R8askfSuJkBVtLJD5kSMTQrK\n' +
    '5vYPbZ/WSRKthSbMotcynz/vWjBh4XY7bmiZC71ZNBCq9ybWRNzv61D9N1CJOlr6\n' +
    'W+1zCYq9dFDYf1nJ60qvkYHmzX3o0a1LHdiTHHvUZIIFXkJ50+NDIbruh8j8Lijk\n' +
    'Eed63QMcrSfLuIIAgoPoWo8WK2+AmA3k3EoTRvci5Ck+HDlLULBhyCrp+QUvn6OR\n' +
    'B7ZBoW+U/OIpNTI4rvsn3rcdkZAVcwRI0vV04IDB52jRzUArSi+08ggCiQ==\n' +
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
    try {
      let issuerAltNames = x509Cert.getIssuerAltNames();
      console.info('issuerAltNames = ' + issuerAltNames.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getIssuerAltNames failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getIssuerName

```TypeScript
getIssuerName(): DataBlob
```

表示获取X.509证书颁发者名称。

> **说明：**
> 
> - 获取的X.509证书颁发者名称末尾包含一个NUL终止符（值为0），请根据业务需求决定是否去除该终止符。
> - 获取的证书颁发者名称为ASCII编码，转换为字符串后，是以斜杠（/）开始，以斜杠（/）分隔相对可分辨名称的可分辨名称字符串。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示X.509证书颁发者名称。 |

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
    try {
      let issuerName = x509Cert.getIssuerName();
      console.info('issuerName = ' + issuerName.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getIssuerName failed, errCode: ${e.code}, errMsg: ${e.message}`);
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
    try {
      let issuerName = x509Crl.getIssuerName();
      console.info('issuerName = ' + issuerName.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getIssuerName failed, errCode: ${e.code}, errMsg: ${e.message}`);
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
      let issuerName = x509CRL.getIssuerName();
      console.info('issuerName = ' + issuerName.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getIssuerName failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getIssuerName

```TypeScript
getIssuerName(encodingType: EncodingType): string
```

表示根据编码类型获取X.509证书颁发者名称。

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
| string | 表示X.509证书颁发者名称，以逗号（,）分隔。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
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

// 证书二进制数据，需业务自行赋值。
let certData = '-----BEGIN CERTIFICATE-----\n' +
    'MIIDgTCCAmmgAwIBAgIGAXKnJjrAMA0GCSqGSIb3DQEBCwUAMFcxCzAJBgNVBAYT\n' +
    'AkNOMQ8wDQYDVQQIDAbpmZXopb8xDzANBgNVBAcMBuilv+WuiTEPMA0GA1UECgwG\n' +
    '5rWL6K+VMRUwEwYDVQQDDAzkuK3mlofmtYvor5UwHhcNMjUwMzA1MDk1MTIzWhcN\n' +
    'MzUwMzAzMDk1MTIzWjBXMQswCQYDVQQGEwJDTjEPMA0GA1UECAwG6ZmV6KW/MQ8w\n' +
    'DQYDVQQHDAbopb/lrokxDzANBgNVBAoMBua1i+ivlTEVMBMGA1UEAwwM5Lit5paH\n' +
    '5rWL6K+VMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAkonJ4UIuxRzX\n' +
    'gr8fLU1PjadDWJp/GrxkYGe30TXqQHDh7O14Rc0xxacj3aLMNffzj+rhxUzl3C9p\n' +
    'wLzIVO2e3iC3Fx2csRzOSIdbimR8879/3uaW8CPkgqlKQw8FDwrGk0S26sdDV8of\n' +
    '8AAHlrnUO2yyL53rAunn4ZKo4EyxHrvHmZKuv006onj0SByu8RNHx97v+4KaaY7p\n' +
    'HngTC55F0KVALiNGygJHeKP7GGxS7kpYV/CvBuABpA00WMqc7nmo2vCa4yC/mIk2\n' +
    '5CF7l860rQ50HLjrmlDYJHpc8p88NJ2BEyHQWiN4YkSKDAKNr+SssD3Tf2wHSYxA\n' +
    'UwdgsatGlwIDAQABo1MwUTAdBgNVHQ4EFgQUMFEfTXLVm7D6fsC7LYtTMhIgVQUw\n' +
    'HwYDVR0jBBgwFoAUMFEfTXLVm7D6fsC7LYtTMhIgVQUwDwYDVR0TAQH/BAUwAwEB\n' +
    '/zANBgkqhkiG9w0BAQsFAAOCAQEABCr9+iK30OSp67ksK1qhkKCzwKYDH2E5KEF4\n' +
    '1E1/o4haXIR14V+5DGcX/1OH3Znd863TecQdNnCFMGArWygq8j7O0uStbWMb3Rhu\n' +
    '+7RJ9GOCbBSeR3v2fC6+T3LI0Sm1G77xIYADmHGt33IW0DRKr44iOalwi6IbcqzD\n' +
    's9XlNO8e6ht2apeL656fjv1gCo/PA7e+A0QHn6zapggzEccEwKdFixCsw5ZMZaHm\n' +
    'adGz3lBCK+0QKYXYL1CtX/6wcDgQ9PuZSgdQgrudLKRN+843m3LJSUJ7AIyL1kQW\n' +
    'kY1ah7eSx4wwaKrLOM06ZkzORMnY5GAy8Aup+UCh6mWU3dPv3w==\n' +
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
    try {
      let issuerName = x509Cert.getIssuerName(cert.EncodingType.ENCODING_UTF8);
      console.info('issuerName output is ' + issuerName);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getIssuerName failed, errCode: ${e.code}, errMsg: ${e.message}`);
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
  'MIIByzCBtAIBATANBgkqhkiG9w0BAQsFADBXMQswCQYDVQQGEwJDTjEPMA0GA1UE\n' +
  'CAwG6ZmV6KW/MQ8wDQYDVQQHDAbopb/lrokxDzANBgNVBAoMBua1i+ivlTEVMBMG\n' +
  'A1UEAwwM5Lit5paH5rWL6K+VFw0yNDEwMTYwODUwMDlaFw0yNDExMTUwODUwMDla\n' +
  'MBkwFwIGAXKnJjrAFw0yNDEwMTYwODQ5NDBaoA4wDDAKBgNVHRQEAwIBADANBgkq\n' +
  'hkiG9w0BAQsFAAOCAQEAU0JPK/DnGmjCi5lKyun506JE+FVDuQsEWuF5CZPqE2um\n' +
  'hA04Qffi+8AfwLpG2KPBaAYTteU4fx30y8Wm0kLutalk32FgrbQX0VQ7EaCOmkMU\n' +
  '2dnQMmFmaFiVcOTaRzgqDOYKuzSAptCo6hqtk9kgjbda5HnsNiVC7dNMRp1Jlzwr\n' +
  'k/42mqZ3fFIy3wYLaxRlq368BX3u94J9Cx754V2V/XEApiRI/FsiSRzRX+jfUBa4\n' +
  '+wwu3WhWxisQj6z3bBkQD4RTg3S+ic8hhP44wt/1MmSLG946Dc9uVYJKUVZqTco9\n' +
  'QDoDwYfBJBzcXjManSkPsGCb7RfTAr5HqcEtIHsK+w==\n' +
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
      let issuerName = x509CRL.getIssuerName(cert.EncodingType.ENCODING_UTF8);
      console.info('issuerName output = ' + issuerName);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getIssuerName failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getIssuerX500DistinguishedName

```TypeScript
getIssuerX500DistinguishedName(): X500DistinguishedName
```

获取X.509证书颁发者的X.500可分辨名称。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md) | X.500可分辨对象。 |

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

async function certGetIssuerX500DistinguishedName() {
  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    x509Cert.getIssuerX500DistinguishedName();
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

async function crlGetIssuerX500DistinguishedName() {
  let x509Crl: cert.X509CRL = {} as cert.X509CRL;
  try {
    x509Crl = await cert.createX509CRL(crlEncodingBlob);
    console.info('createX509CRL result: success.');
    x509Crl.getIssuerX500DistinguishedName();
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509CRL failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

## getItem

```TypeScript
getItem(itemType: CertItemType): DataBlob
```

表示获取X.509证书对应的字段。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [CertItemType](arkts-devicecertificate-cert-certitemtype-e.md) | 是 | 表示需要获取的证书字段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示X.509证书对应的字段，返回值为DER格式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
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
    try {
      let tbs = x509Cert.getItem(cert.CertItemType.CERT_ITEM_TYPE_TBS);
      console.info('tbs = ' + tbs.data);
      let pubKey = x509Cert.getItem(cert.CertItemType.CERT_ITEM_TYPE_PUBLIC_KEY);
      console.info('pubKey = ' + pubKey.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getItem failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getKeyUsage

```TypeScript
getKeyUsage(): DataBlob
```

表示获取X.509证书密钥用途。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示X.509证书密钥用途。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
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
    'MIIDIjCCAgqgAwIBAgIUUb7sok900ODOxkyE1FzstJbKCSQwDQYJKoZIhvcNAQEL\n' +
    'BQAwGjEYMBYGA1UEAwwPRXhhbXBsZSBSb290IENBMB4XDTI1MTAzMDAxNTQ0NFoX\n' +
    'DTI2MTAzMDAxNTQ0NFowGjEYMBYGA1UEAwwPRXhhbXBsZSBSb290IENBMIIBIjAN\n' +
    'BgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAv3+V/0Nl4rytCHNcb7PMpRbsxvOX\n' +
    '8zxwfb+5McmJ8ZZj59My3oqF7YgFM1VgZjjwaz8HljXvoaxrUJWQEu6AYjIa5ywN\n' +
    'duySyyNNgfbqiwUOVdUICh3WsEjvvxK+8f55L3xU0LybZxyEf0+31pc15SzCvTvv\n' +
    'E0OC8n3bYr2Nn0mvwtMHIl0Dr6AZbP10B/KKk68oX9UYOlsp4y0GTEXVDt/9bScx\n' +
    'PV2WvaKPWcrQoJVz1ys2RtyUgcwPiWugQdx54xHG6zIAMYptKxDaHgsOEtUR4J1p\n' +
    'xP1Ih7fY2wFZkeyRZG05ivYVqSHzHQV9Z42i+KjzfJUsMQt9TosuSsDi1wIDAQAB\n' +
    'o2AwXjAdBgNVHQ4EFgQUKF6T271JCNpwjwyCSzTSN66T95EwHwYDVR0jBBgwFoAU\n' +
    'KF6T271JCNpwjwyCSzTSN66T95EwDwYDVR0TAQH/BAUwAwEB/zALBgNVHQ8EBAMC\n' +
    'BaAwDQYJKoZIhvcNAQELBQADggEBACa9A6d/cdFb7h8EMmjs0l+3aIAI10EskgRT\n' +
    '+WHZ8zi+Q94/WEsOJW8CXIquJ2SxjXvl/A4UgrnfQyN+4kgEg7hLyuugg1QTk0so\n' +
    'Kj6tlG82Oxr/gjzxf3MMFhkzLpi2nUYu66HnskzAfI1XLuLz995qY0hCj9r2gUiX\n' +
    '6GR0H4p9pO5h9Fx7pbyosr2sn/JZbo9j6fWSuuvqoedjEuIb8aRmB6kbUkjhh/Iz\n' +
    '5htY+aYZz0pRSm2F93WLy6HBhPNdAmWOCpNXrynsRXDgCPKqeIasba8MBjXTsqvI\n' +
    'mgbc4MCLhLciWi34u9NpkAGbkwYVLE6URw/o373mD9fqe214Jdw=\n' +
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
    try {
      let keyUsage = x509Cert.getKeyUsage();
      console.info('keyUsage = ' + keyUsage.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getKeyUsage failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getNotAfterTime

```TypeScript
getNotAfterTime(): string
```

表示获取X.509证书过期时间。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示X.509证书过期时间，日期采用ASN.1 UTCTime或GeneralizedTime格式。 |

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
    try {
      let notAfter = x509Cert.getNotAfterTime();
      console.info('notAfter = ' + notAfter);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getNotAfterTime failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getNotBeforeTime

```TypeScript
getNotBeforeTime(): string
```

表示获取X.509证书生效时间。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示X.509证书生效时间，日期采用ASN.1 UTCTime或GeneralizedTime格式。 |

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
    try {
      let notBefore = x509Cert.getNotBeforeTime();
      console.info('notBefore = ' + notBefore);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getNotBeforeTime failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getPublicKey

```TypeScript
getPublicKey(): cryptoFramework.PubKey
```

表示获取X.509证书公钥。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| cryptoFramework.PubKey | 表示X.509证书公钥对象。该对象仅用于**X509Cert**的**verify()**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
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
    try {
      x509Cert.getPublicKey();
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getPublicKey failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getSerialNumber

```TypeScript
getSerialNumber(): number
```

表示获取X.509证书序列号。

> **说明：**
> 
> 从API version 9开始支持，从API version 10开始废弃，建议使用
> [X509Cert.getCertSerialNumber()](#getcertserialnumber)替代。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [getCertSerialNumber](#getcertserialnumber)

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 表示X.509证书序列号。 |

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
    let serialNumber = x509Cert.getSerialNumber();
    console.info('serialNumber = ' + serialNumber);
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
      serialNumber = crlEntry.getSerialNumber();
      console.info('serialNumber = ' + serialNumber);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getRevokedCert or getSerialNumber failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getSignature

```TypeScript
getSignature(): DataBlob
```

表示获取X.509证书签名数据。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示X.509证书签名数据。 |

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
    try {
      let signature = x509Cert.getSignature();
      console.info('signature = ' + signature.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSignature failed, errCode: ${e.code}, errMsg: ${e.message}`);
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
    try {
      let signature = x509Crl.getSignature();
      console.info('signature = ' + signature.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSignature failed, errCode: ${e.code}, errMsg: ${e.message}`);
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
      let signature = x509CRL.getSignature();
      console.info('signature = ' + signature.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSignature failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getSignatureAlgName

```TypeScript
getSignatureAlgName(): string
```

表示获取X.509证书签名算法名称。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示X.509证书签名算法名称。 |

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
    try {
      let sigAlgName = x509Cert.getSignatureAlgName();
      console.info('sigAlgName = ' + sigAlgName);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSignatureAlgName failed, errCode: ${e.code}, errMsg: ${e.message}`);
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
    try {
      let sigAlgName = x509Crl.getSignatureAlgName();
      console.info('sigAlgName = ' + sigAlgName);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSignatureAlgName failed, errCode: ${e.code}, errMsg: ${e.message}`);
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
      let sigAlgName = x509CRL.getSignatureAlgName();
      console.info('sigAlgName = ' + sigAlgName);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSignatureAlgName failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getSignatureAlgOid

```TypeScript
getSignatureAlgOid(): string
```

表示获取X.509证书签名算法的对象标识符（OID）。OID由国际标准化组织（ISO）分配。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示签名算法OID。当长度超过127字节时会被截断。 |

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
    try {
      let sigAlgOid = x509Cert.getSignatureAlgOid();
      console.info('sigAlgOid = ' + sigAlgOid);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSignatureAlgOid failed, errCode: ${e.code}, errMsg: ${e.message}`);
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
    try {
      let sigAlgOid = x509Crl.getSignatureAlgOid();
      console.info('sigAlgOid = ' + sigAlgOid);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSignatureAlgOid failed, errCode: ${e.code}, errMsg: ${e.message}`);
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
      let sigAlgOid = x509CRL.getSignatureAlgOid();
      console.info('sigAlgOid = ' + sigAlgOid);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSignatureAlgOid failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getSignatureAlgParams

```TypeScript
getSignatureAlgParams(): DataBlob
```

表示获取X.509证书签名算法参数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示X.509证书签名算法参数。 |

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

// 证书二进制数据，需业务自行赋值。
let certData = '-----BEGIN CERTIFICATE-----\n' +
  'MIIEETCCAs6gAwIBAgIUKRqK4hH6D1p3NSuChKOwHnIVx74wOAYJKoZIhvcNAQEK\n' +
  'MCugDTALBglghkgBZQMEAgGhGjAYBgkqhkiG9w0BAQgwCwYJYIZIAWUDBAIBMG0x\n' +
  'CzAJBgNVBAYTAkVOMQ0wCwYDVQQIDAR0ZXN0MQ0wCwYDVQQHDAR4aWFuMQ0wCwYD\n' +
  'VQQKDAR0ZXN0MQ0wCwYDVQQLDAR0ZXN0MQ0wCwYDVQQDDAR0ZXN0MRMwEQYJKoZI\n' +
  'hvcNAQkBFgR0ZXN0MB4XDTI1MTAzMDAxNDAzMVoXDTI2MTAzMDAxNDAzMVowbTEL\n' +
  'MAkGA1UEBhMCRU4xDTALBgNVBAgMBHRlc3QxDTALBgNVBAcMBHhpYW4xDTALBgNV\n' +
  'BAoMBHRlc3QxDTALBgNVBAsMBHRlc3QxDTALBgNVBAMMBHRlc3QxEzARBgkqhkiG\n' +
  '9w0BCQEWBHRlc3QwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDaHZMj\n' +
  'UCQm53hgVYQq+kbmgKOH4e+vrsoAeOaX8KEgCbJfwLVpF7lj3Ld2c52X31JxziJx\n' +
  'D6rmGIk0Tp13/rNA/AZrmhbO/+PKKQiWQJpUbNI4A4scxELn9emLk8B3x76k8KGh\n' +
  'E7Re0XgKxfbZXU4AOZ0+9sXAZrSOPc8hYEfpwkGl09EojRuqQ4uSzjN3ikasfkZx\n' +
  'xM4twRPXiumC34+ep8Z1uxZy6MUClT2plNM8fAdfUwRY0lnKh2RjAJcK1lQBlPlW\n' +
  'Qc7S0/ifFXxgh+sBt+4dq+pphm5R/i6MIMWZ0JUg6tUlh1iY3nLVMVz0Z+LT7JUS\n' +
  '5ILjwwybwhtatFh5AgMBAAGjUzBRMB0GA1UdDgQWBBQM3AOhyH6sHP7CJAB/Z5Xy\n' +
  '4VQxJzAfBgNVHSMEGDAWgBQM3AOhyH6sHP7CJAB/Z5Xy4VQxJzAPBgNVHRMBAf8E\n' +
  'BTADAQH/MDgGCSqGSIb3DQEBCjAroA0wCwYJYIZIAWUDBAIBoRowGAYJKoZIhvcN\n' +
  'AQEIMAsGCWCGSAFlAwQCAQOCAQEAXhXExMyEnkBs9c6syxL4H98b9VtatezhKsMY\n' +
  'c4vTxw5D5IoN+SM+YS6wNKN1fh0fO8nZm7kHmB/KyxtdKja5cwGfhqwsY2NHOkK7\n' +
  'X5jWkbS0hbGPjj0UZkYRfC63d76lEPqz/bvf5Lgsv+W/J3ZFFBCV4tiBVr1ubpEy\n' +
  '/n+C1r2NMxOKfGOEdE8tPa5LiR85/MYFaaAvzHVX4irXsQmzXPJMaMWt2DJAAze3\n' +
  'ro0L1Hcd3VKyh5fYowA6nCDpNkKtQnVG/102SOM8HBH7wMSMHpsDzZbTuWRNJ35J\n' +
  'ach83y13Yx4Td+DVsZgNjl/7yeA+XdusunygAnqHqx2brCTaNw==\n' +
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
    try {
      let sigAlgParams = x509Cert.getSignatureAlgParams();
      console.info('sigAlgParams = ' + sigAlgParams.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSignatureAlgParams failed, errCode: ${e.code}, errMsg: ${e.message}`);
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
    try {
      let sigAlgParams = x509Crl.getSignatureAlgParams();
      console.info('sigAlgParams = ' + sigAlgParams.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSignatureAlgParams failed, errCode: ${e.code}, errMsg: ${e.message}`);
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
      let sigAlgParams = x509CRL.getSignatureAlgParams();
      console.info('sigAlgParams = ' + sigAlgParams.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSignatureAlgParams failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getSubjectAltNames

```TypeScript
getSubjectAltNames(): DataArray
```

表示获取X.509证书主体可选名称。

> **说明：**
> 
> 获取到的X.509证书主体可选名称数据带字符串结束符。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | 表示X.509证书主体可选名称。 |

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

// 证书二进制数据，需业务自行赋值。
let certData = '-----BEGIN CERTIFICATE-----\n' +
    'MIIDRjCCAi6gAwIBAgIUU3RfsnV6Ur2a514YvAygbMvcjaowDQYJKoZIhvcNAQEL\n' +
    'BQAwGjEYMBYGA1UEAwwPRXhhbXBsZSBSb290IENBMB4XDTI1MTAzMDAyNDIyM1oX\n' +
    'DTI2MTAzMDAyNDIyM1owGjEYMBYGA1UEAwwPRXhhbXBsZSBSb290IENBMIIBIjAN\n' +
    'BgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA5yQDXUKnsNTPkqwVzCjtaE+Q8Tla\n' +
    'Qod6tb0fo044DLrYFvly6W10sqfvqZpuEfUuyzh/cs7279SoP8FYjnrykcE3yxqu\n' +
    '3N6vNn6iXm3CQnjlqBVB7ChTcoXv8GEwHNXcjNTaX3FZQW62WAYLLER4I9/ZwE/N\n' +
    'iqf+rJu5O2eRzZ4AFappCLquFSp6Yw5yyhenhNFd026dBf58ggpUs0H9DThxS3N3\n' +
    'GFUs6JDiOJpxjbv+p7ns9MsryqewB8i5TCJjMJkcCg+2YyKFKYDv3mC4eoV71MU0\n' +
    'DVoy7sBhs1naTV7joM+wGSOLcW3ee6K9qCp8zXmqN1tRJOYxm/JkVvi5oQIDAQAB\n' +
    'o4GDMIGAMB0GA1UdDgQWBBTXIqHf66clGd8UhAr2SJSaukwphDAfBgNVHSMEGDAW\n' +
    'gBTXIqHf66clGd8UhAr2SJSaukwphDAPBgNVHRMBAf8EBTADAQH/MC0GA1UdEQQm\n' +
    'MCSCC2V4YW1wbGUuY29tgg93d3cuZXhhbXBsZS5jb22HBH8AAAEwDQYJKoZIhvcN\n' +
    'AQELBQADggEBABI/bnHX9xqw/3RfvEqXp/ocmI0Dm7XwQZ6MS9XlTgYVp9rPYFbz\n' +
    'eS79q47nV1SMKc6LDeLoDcHT04aYGsKrA0O/9VVFhb50S1JBoa3HrEe0Q5WD4k48\n' +
    'GUJE2CaaO+MG3P9ZF4P3qxvPZ1PLoHr2B2YkaIMapjlNDUyTGLyWwPEuJSraBiXj\n' +
    'hnl1C9D5Y7ss8zuh4zzJl8MtU36kk19BbBglZVE0H7KDGGhqqvEbIFBNZmqy2vb3\n' +
    '7xSbXJL0/SQV+nr2Qvv8DU4XZJliJKVJHr3GkrqXRSFVVZ0ADNpEdLxFT0IF1X/T\n' +
    'JiAZrIdZPozWsjUVtQ4KVMJj+D7canRVuCg=\n' +
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
    try {
      let subjectAltNames = x509Cert.getSubjectAltNames();
      console.info('subjectAltNames = ' + subjectAltNames.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSubjectAltNames failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getSubjectName

```TypeScript
getSubjectName(encodingType?: EncodingType): DataBlob
```

表示获取X.509证书主体名称。

> **说明：**
> 
> - 若不设置encodingType参数，获取的证书主体名称末尾包含一个NUL终止符（值为0），请根据业务需求决定是否去除该终止符。
> - 若不设置encodingType参数，获取的证书主体名称为ASCII编码，转换为字符串后，是以斜杠（/）开始，以斜杠（/）分隔相对可分辨名称的
> 可分辨名称字符串。
> - 建议设置encodingType参数为EncodingType.ENCODING_UTF8，获取的证书主体名称是以逗号（,）分隔相对可分辨名称的可分辨名称字符串。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encodingType | [EncodingType](arkts-devicecertificate-cert-encodingtype-e.md) | 否 | 表示编码类型。设置该参数时，获取UTF-8格式的主体名称； 不设置时，默认获取ASCII编码格式的主体名称。该参数从API version 12开始可用。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示X.509证书主体名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Incorrect parameter types;  2. Parameter verification failed.<br>**适用版本：** 12+ |

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
    try {
      let subjectName = x509Cert.getSubjectName();
      console.info('subjectName = ' + subjectName.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSubjectName failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
    try {
      let subjectNameutf8 = x509Cert.getSubjectName(cert.EncodingType.ENCODING_UTF8);
      console.info('subjectNameutf8 = ' + subjectNameutf8.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getSubjectNameUtf8 failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## getSubjectX500DistinguishedName

```TypeScript
getSubjectX500DistinguishedName(): X500DistinguishedName
```

获取X.509证书主体的X.500可分辨名称。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md) | X.500可分辨对象。 |

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

async function certGetSubjectX500DistinguishedName() {
  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    x509Cert.getSubjectX500DistinguishedName();
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509Cert failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

## getVersion

```TypeScript
getVersion(): number
```

表示获取X.509证书版本号。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 表示X.509证书版本号。 |

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
    let version = x509Cert.getVersion();
    console.info('version = ' + version);
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
    let version = x509Crl.getVersion();
    console.info('version = ' + version);
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
    let version = x509CRL.getVersion();
    console.info('version = ' + version);
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

## match

```TypeScript
match(param: X509CertMatchParameters): boolean
```

判断证书是否与输入参数匹配。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [X509CertMatchParameters](arkts-devicecertificate-cert-x509certmatchparameters-i.md) | 是 | 表示需要匹配的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当参数匹配时，该方法返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
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

async function createX509Cert(): Promise<cert.X509Cert> {
  let certData = '-----BEGIN CERTIFICATE-----\n' +
  'MIIDTTCCAjWgAwIBAgIBAzANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDM1NFoXDTM0MDMxNzAyMDM1NFowETEPMA0GA1UEAwwG\n' +
  'ZGV2aWNlMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAuoGk2J0aKWTP\n' +
  'J3D7lS3oFdME3MMA1z0Y0ftthrtUKybE2xh8P90ztMV73bewmgAPqiApqhaWEZM/\n' +
  '6DSLc/MxbOeYjg6njveJIu721gchiuB2PFikDFSWlcLOJNw+CgBx77Ct3KllivHs\n' +
  'oi/gjuxrWiF/3VhbBErPNj/fw9se3pVrFRXIFdkcybtom2mUmkcxDfSg587SO14i\n' +
  'ZzXGM6nhMzYWXxLho6SJrsnzfs4pD6ifksWmY4089zitqsN+9jQXafY1+/sh1mgu\n' +
  'FvAwg9IbigGOBIiF8t5qdNGpqCHXbEHblNCWfT4fVNDV0Vc9pByjZaMYEGMhpz+6\n' +
  'lxlc2CqbNQIDAQABo4GuMIGrMAkGA1UdEwQCMAAwHQYDVR0OBBYEFAEVpuP+pPpg\n' +
  'kr3dA3aV2XdFZ9rGMB8GA1UdIwQYMBaAFHRb+SgJu8O0UYdRBkszePocqxbYMB0G\n' +
  'A1UdJQQWMBQGCCsGAQUFBwMBBggrBgEFBQcDAjALBgNVHQ8EBAMCB4AwMgYIKwYB\n' +
  'BQUHAQEEJjAkMCIGCCsGAQUFBzABhhZodHRwczovLzEyNy4wLjAuMTo5OTk5MA0G\n' +
  'CSqGSIb3DQEBCwUAA4IBAQBjM1agcDcgVHsD0dS39gxtlyRbZRvDcW3YsdwgpN6S\n' +
  'e4wGzdZbhsiZv7y3+PSuozKwp5Yjn+UqnnEz7QuTGJRt/pzHDVY3QceNvlx2HPRe\n' +
  'fECS4bpGLcM5B17oZZjE4HenIrGmigXnnwYL5TjhC4ybtddXPYv/M6z2eFCnfQNa\n' +
  'zFwz8LJ7ukWvf5koBqcHq2zsuVByOIPXLIrAJPtMmBb/pHCFt8hxOxwqujdrxz16\n' +
  'pe5LQUYzvG1YCxw3Ye9OrM1yXJQr/4KYncQC1yQQo+UK7NsDRK30PsMEYxhierLA\n' +
  'JKyPn1xSlOJiGa2rRn/uevmEOhfagj5TtprU9Gu1+nZo\n' +
  '-----END CERTIFICATE-----\n';

  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(certData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509Cert failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
  return x509Cert;
}

async function matchX509Cert() {
  const x509Cert = await createX509Cert();
  try {
    // 需业务自行赋值。
    const param: cert.X509CertMatchParameters = {
      x509Cert,
      validDate: '20241121074700Z',
      keyUsage: [true, false, false, false, false, false, false, false, false],
      publicKeyAlgID: '1.2.840.113549.1.1.1'
    };
    const result = x509Cert.match(param);
    console.info('result = ' + result);
    console.info('call x509Cert match result: success.');
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`call x509Cert match failed, errCode: ${e.code}, errMsg: ${e.message}`);
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

## toString

```TypeScript
toString(encodingType: EncodingType): string
```

根据编码类型获取对象的字符串类型数据。

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
| string | 表示对象的字符串类型数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
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

let certData = '-----BEGIN CERTIFICATE-----\n' +
    'MIIDgTCCAmmgAwIBAgIGAXKnJjrAMA0GCSqGSIb3DQEBCwUAMFcxCzAJBgNVBAYT\n' +
    'AkNOMQ8wDQYDVQQIDAbpmZXopb8xDzANBgNVBAcMBuilv+WuiTEPMA0GA1UECgwG\n' +
    '5rWL6K+VMRUwEwYDVQQDDAzkuK3mlofmtYvor5UwHhcNMjUwMzA1MDk1MTIzWhcN\n' +
    'MzUwMzAzMDk1MTIzWjBXMQswCQYDVQQGEwJDTjEPMA0GA1UECAwG6ZmV6KW/MQ8w\n' +
    'DQYDVQQHDAbopb/lrokxDzANBgNVBAoMBua1i+ivlTEVMBMGA1UEAwwM5Lit5paH\n' +
    '5rWL6K+VMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAkonJ4UIuxRzX\n' +
    'gr8fLU1PjadDWJp/GrxkYGe30TXqQHDh7O14Rc0xxacj3aLMNffzj+rhxUzl3C9p\n' +
    'wLzIVO2e3iC3Fx2csRzOSIdbimR8879/3uaW8CPkgqlKQw8FDwrGk0S26sdDV8of\n' +
    '8AAHlrnUO2yyL53rAunn4ZKo4EyxHrvHmZKuv006onj0SByu8RNHx97v+4KaaY7p\n' +
    'HngTC55F0KVALiNGygJHeKP7GGxS7kpYV/CvBuABpA00WMqc7nmo2vCa4yC/mIk2\n' +
    '5CF7l860rQ50HLjrmlDYJHpc8p88NJ2BEyHQWiN4YkSKDAKNr+SssD3Tf2wHSYxA\n' +
    'UwdgsatGlwIDAQABo1MwUTAdBgNVHQ4EFgQUMFEfTXLVm7D6fsC7LYtTMhIgVQUw\n' +
    'HwYDVR0jBBgwFoAUMFEfTXLVm7D6fsC7LYtTMhIgVQUwDwYDVR0TAQH/BAUwAwEB\n' +
    '/zANBgkqhkiG9w0BAQsFAAOCAQEABCr9+iK30OSp67ksK1qhkKCzwKYDH2E5KEF4\n' +
    '1E1/o4haXIR14V+5DGcX/1OH3Znd863TecQdNnCFMGArWygq8j7O0uStbWMb3Rhu\n' +
    '+7RJ9GOCbBSeR3v2fC6+T3LI0Sm1G77xIYADmHGt33IW0DRKr44iOalwi6IbcqzD\n' +
    's9XlNO8e6ht2apeL656fjv1gCo/PA7e+A0QHn6zapggzEccEwKdFixCsw5ZMZaHm\n' +
    'adGz3lBCK+0QKYXYL1CtX/6wcDgQ9PuZSgdQgrudLKRN+843m3LJSUJ7AIyL1kQW\n' +
    'kY1ah7eSx4wwaKrLOM06ZkzORMnY5GAy8Aup+UCh6mWU3dPv3w==\n' +
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
    console.info('certToString success: ' + x509Cert.toString(cert.EncodingType.ENCODING_UTF8));
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
  'MIIByzCBtAIBATANBgkqhkiG9w0BAQsFADBXMQswCQYDVQQGEwJDTjEPMA0GA1UE\n' +
  'CAwG6ZmV6KW/MQ8wDQYDVQQHDAbopb/lrokxDzANBgNVBAoMBua1i+ivlTEVMBMG\n' +
  'A1UEAwwM5Lit5paH5rWL6K+VFw0yNDEwMTYwODUwMDlaFw0yNDExMTUwODUwMDla\n' +
  'MBkwFwIGAXKnJjrAFw0yNDEwMTYwODQ5NDBaoA4wDDAKBgNVHRQEAwIBADANBgkq\n' +
  'hkiG9w0BAQsFAAOCAQEAU0JPK/DnGmjCi5lKyun506JE+FVDuQsEWuF5CZPqE2um\n' +
  'hA04Qffi+8AfwLpG2KPBaAYTteU4fx30y8Wm0kLutalk32FgrbQX0VQ7EaCOmkMU\n' +
  '2dnQMmFmaFiVcOTaRzgqDOYKuzSAptCo6hqtk9kgjbda5HnsNiVC7dNMRp1Jlzwr\n' +
  'k/42mqZ3fFIy3wYLaxRlq368BX3u94J9Cx754V2V/XEApiRI/FsiSRzRX+jfUBa4\n' +
  '+wwu3WhWxisQj6z3bBkQD4RTg3S+ic8hhP44wt/1MmSLG946Dc9uVYJKUVZqTco9\n' +
  'QDoDwYfBJBzcXjManSkPsGCb7RfTAr5HqcEtIHsK+w==\n' +
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
    console.info('crlToString success: ' + x509Crl.toString(cert.EncodingType.ENCODING_UTF8));
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509CRL failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

## verify

```TypeScript
verify(key: cryptoFramework.PubKey, callback: AsyncCallback<void>): void
```

表示对证书验签。使用Callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | cryptoFramework.PubKey | 是 | 用于验签的公钥对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当验签成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
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
  // 根据encodingBlob的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509Cert(encodingBlob, (error, x509Cert) => {
  if (error) {
    console.error(`createX509Cert failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createX509Cert result: success.');

    // 业务需通过上级X509Cert证书对象（或当前证书对象为自签名的证书）的getPublicKey获取PubKey。
    try {
      let pubKey = x509Cert.getPublicKey();

      // 验证证书签名。
      x509Cert.verify(pubKey, (err, _data) => {
        if (err) {
          console.error(`verify failed, errCode: ${err.code}, errMsg: ${err.message}`);
        } else {
          console.info('verify result: success.');
        }
      });
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`getPublicKey failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
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

let pubKeyData = new Uint8Array([
  0x30, 0x81, 0x9F, 0x30, 0x0D, 0x06, 0x09, 0x2A, 0x86, 0x48, 0x86, 0xF7, 0x0D, 0x01, 0x01, 0x01,
  0x05, 0x00, 0x03, 0x81, 0x8D, 0x00, 0x30, 0x81, 0x89, 0x02, 0x81, 0x81, 0x00, 0xDC, 0x4C, 0x2D,
  0x57, 0x49, 0x3D, 0x42, 0x52, 0x1A, 0x09, 0xED, 0x3E, 0x90, 0x29, 0x51, 0xF7, 0x70, 0x15, 0xFE,
  0x76, 0xB0, 0xDB, 0xDF, 0xA1, 0x2C, 0x6C, 0x67, 0x95, 0xDA, 0x63, 0x3D, 0x4F, 0x71, 0x48, 0x8C,
  0x3E, 0xFA, 0x24, 0x79, 0xE9, 0xF2, 0xF2, 0x20, 0xCB, 0xF1, 0x59, 0x6B, 0xED, 0xC8, 0x72, 0x66,
  0x6E, 0x31, 0xD4, 0xF3, 0xCE, 0x0B, 0x12, 0xC4, 0x17, 0x39, 0xB4, 0x52, 0x16, 0xD3, 0xE3, 0xC0,
  0xF8, 0x48, 0xB3, 0xF6, 0x40, 0xD5, 0x47, 0x23, 0x30, 0x7F, 0xA7, 0xC5, 0x5A, 0x5A, 0xBB, 0x5C,
  0x7B, 0xEF, 0x69, 0xE2, 0x74, 0x35, 0x24, 0x22, 0x25, 0x45, 0x7E, 0xFC, 0xE8, 0xC4, 0x52, 0x65,
  0xA0, 0x4E, 0xBC, 0xFD, 0x3F, 0xD9, 0x85, 0x14, 0x8A, 0x5A, 0x93, 0x02, 0x24, 0x6C, 0x19, 0xBA,
  0x81, 0xBE, 0x65, 0x2E, 0xCB, 0xBB, 0xE9, 0x91, 0x7B, 0x7C, 0x47, 0xC2, 0x61, 0x02, 0x03, 0x01,
  0x00, 0x01
]);

let priKeyData = new Uint8Array([
  0x30, 0x82, 0x02, 0x77, 0x02, 0x01, 0x00, 0x30, 0x0D, 0x06, 0x09, 0x2A, 0x86, 0x48, 0x86, 0xF7,
  0x0D, 0x01, 0x01, 0x01, 0x05, 0x00, 0x04, 0x82, 0x02, 0x61, 0x30, 0x82, 0x02, 0x5D, 0x02, 0x01,
  0x00, 0x02, 0x81, 0x81, 0x00, 0xDC, 0x4C, 0x2D, 0x57, 0x49, 0x3D, 0x42, 0x52, 0x1A, 0x09, 0xED,
  0x3E, 0x90, 0x29, 0x51, 0xF7, 0x70, 0x15, 0xFE, 0x76, 0xB0, 0xDB, 0xDF, 0xA1, 0x2C, 0x6C, 0x67,
  0x95, 0xDA, 0x63, 0x3D, 0x4F, 0x71, 0x48, 0x8C, 0x3E, 0xFA, 0x24, 0x79, 0xE9, 0xF2, 0xF2, 0x20,
  0xCB, 0xF1, 0x59, 0x6B, 0xED, 0xC8, 0x72, 0x66, 0x6E, 0x31, 0xD4, 0xF3, 0xCE, 0x0B, 0x12, 0xC4,
  0x17, 0x39, 0xB4, 0x52, 0x16, 0xD3, 0xE3, 0xC0, 0xF8, 0x48, 0xB3, 0xF6, 0x40, 0xD5, 0x47, 0x23,
  0x30, 0x7F, 0xA7, 0xC5, 0x5A, 0x5A, 0xBB, 0x5C, 0x7B, 0xEF, 0x69, 0xE2, 0x74, 0x35, 0x24, 0x22,
  0x25, 0x45, 0x7E, 0xFC, 0xE8, 0xC4, 0x52, 0x65, 0xA0, 0x4E, 0xBC, 0xFD, 0x3F, 0xD9, 0x85, 0x14,
  0x8A, 0x5A, 0x93, 0x02, 0x24, 0x6C, 0x19, 0xBA, 0x81, 0xBE, 0x65, 0x2E, 0xCB, 0xBB, 0xE9, 0x91,
  0x7B, 0x7C, 0x47, 0xC2, 0x61, 0x02, 0x03, 0x01, 0x00, 0x01, 0x02, 0x81, 0x80, 0x5A, 0xCF, 0x0F,
  0xF5, 0xA6, 0x1C, 0x19, 0x65, 0x8C, 0x94, 0x40, 0xF6, 0x84, 0x28, 0x74, 0x40, 0x42, 0x34, 0xDE,
  0xC3, 0x00, 0x5E, 0x72, 0x4D, 0x96, 0xE9, 0x4C, 0xBD, 0xC9, 0xDB, 0x14, 0x9F, 0xD5, 0xBB, 0xA9,
  0x0C, 0x20, 0xC2, 0xBE, 0x7A, 0x80, 0x89, 0xEC, 0x99, 0x04, 0xF0, 0xEE, 0x7B, 0x83, 0x20, 0x1D,
  0x37, 0x19, 0x55, 0x85, 0xF6, 0x8E, 0x3B, 0xFB, 0x16, 0xF3, 0xD3, 0x6F, 0xEE, 0x73, 0x12, 0x53,
  0xCA, 0x77, 0xD7, 0x6C, 0x29, 0xF5, 0x08, 0xA3, 0x09, 0x01, 0x0B, 0x00, 0x05, 0x57, 0xAD, 0x4D,
  0xF0, 0x92, 0xB2, 0x5A, 0x8B, 0x19, 0x09, 0x81, 0x86, 0xFE, 0x66, 0xB9, 0x33, 0x88, 0x28, 0xF3,
  0x37, 0x73, 0x09, 0x5F, 0xD7, 0xC9, 0xC6, 0xFA, 0x13, 0x74, 0xFE, 0xAE, 0x53, 0xA9, 0x71, 0x67,
  0xCE, 0x3A, 0xE6, 0x8D, 0x35, 0xD1, 0xB8, 0xFD, 0x6F, 0x0D, 0x43, 0xC2, 0xD1, 0x02, 0x41, 0x00,
  0xF7, 0x33, 0xE5, 0x6C, 0x29, 0x5A, 0x30, 0x58, 0xA4, 0x52, 0x65, 0xA0, 0x39, 0xC2, 0xE8, 0xAE,
  0x5F, 0xA3, 0x2D, 0x0C, 0x65, 0xB1, 0x7B, 0xFD, 0x92, 0xBF, 0x47, 0x87, 0x97, 0x40, 0xCB, 0x54,
  0xF9, 0xBB, 0x50, 0x27, 0x70, 0x51, 0xD0, 0xD8, 0x48, 0x0D, 0xC6, 0x47, 0x60, 0xF8, 0x4E, 0x0A,
  0x32, 0x76, 0x6D, 0xA4, 0xBA, 0x40, 0xE5, 0x58, 0xF8, 0x4A, 0x39, 0x4E, 0xF8, 0x3F, 0x4E, 0x2D,
  0x02, 0x41, 0x00, 0xE4, 0x23, 0x2A, 0x5F, 0x59, 0xCF, 0x7C, 0x91, 0x24, 0x0D, 0xA2, 0x44, 0x17,
  0xCD, 0x37, 0xDE, 0x1F, 0x53, 0x4D, 0x33, 0x9F, 0x90, 0x4D, 0xD9, 0x72, 0x64, 0x25, 0xBA, 0xAB,
  0x47, 0x91, 0xC4, 0x99, 0x95, 0x86, 0xB5, 0x8A, 0xEA, 0x77, 0xF7, 0x64, 0x72, 0x5E, 0xB7, 0xBB,
  0x16, 0xA1, 0x64, 0xA4, 0xE1, 0x2D, 0x76, 0x6D, 0xEF, 0xB1, 0x5E, 0xD6, 0x17, 0xE8, 0xAA, 0xB6,
  0xA0, 0xD9, 0x85, 0x02, 0x41, 0x00, 0xDF, 0xC8, 0x5B, 0x28, 0x4F, 0x47, 0x15, 0xFD, 0x28, 0xC4,
  0x6E, 0xBB, 0x5D, 0x8E, 0xD4, 0x95, 0x06, 0x7E, 0xF1, 0x89, 0x07, 0x86, 0x64, 0x78, 0x69, 0x20,
  0x3F, 0xE0, 0xBF, 0x4C, 0x28, 0xC6, 0x04, 0x4D, 0x4D, 0x82, 0x66, 0x6B, 0xAA, 0x64, 0x20, 0xD6,
  0x57, 0x68, 0xC6, 0xA0, 0x02, 0x05, 0xB9, 0x28, 0xFC, 0x98, 0xE3, 0x03, 0x5C, 0x9B, 0xEE, 0x29,
  0x43, 0x37, 0xFA, 0x03, 0x55, 0x01, 0x02, 0x40, 0x69, 0x5B, 0x7C, 0x24, 0x10, 0xDB, 0xEB, 0x91,
  0x33, 0xEF, 0x3F, 0xF2, 0xE6, 0x73, 0x15, 0xCB, 0xF4, 0xF7, 0x89, 0x7D, 0xBF, 0xC0, 0xEA, 0xD2,
  0xF3, 0x2B, 0x20, 0xE9, 0x76, 0x54, 0x55, 0x13, 0x50, 0x42, 0x67, 0xB5, 0xCB, 0x73, 0xC0, 0xF7,
  0x75, 0x62, 0x04, 0x30, 0x21, 0xAC, 0xAF, 0xD8, 0x44, 0xF4, 0xE1, 0x04, 0x02, 0x7D, 0x61, 0x92,
  0x84, 0x99, 0x02, 0x10, 0x64, 0xCB, 0x1F, 0xE9, 0x02, 0x41, 0x00, 0xAB, 0x4B, 0x7D, 0x90, 0x7C,
  0x57, 0x08, 0x6B, 0xC0, 0x43, 0x72, 0x09, 0x8A, 0x18, 0x35, 0x36, 0x64, 0x9D, 0x84, 0x8D, 0xF1,
  0x84, 0x94, 0x48, 0xC6, 0x80, 0x9D, 0xB9, 0xA2, 0x58, 0x0A, 0x4D, 0x0A, 0xCA, 0x1E, 0xD6, 0x05,
  0x55, 0x5B, 0xFE, 0xD7, 0xAA, 0x70, 0xED, 0x76, 0xB3, 0x40, 0x2E, 0xA0, 0xB3, 0x32, 0x37, 0xB0,
  0xA0, 0xB9, 0x96, 0x2D, 0xC4, 0x70, 0xE9, 0x99, 0x10, 0x67, 0x8D
]);

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
    try {
      let keyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024|PRIMES_3');
      console.info('createAsyKeyGenerator result: success.');
      let priEncodingBlob: cryptoFramework.DataBlob = {
        data: priKeyData
      };
      let pubEncodingBlob: cryptoFramework.DataBlob = {
        data: pubKeyData
      };
      keyGenerator.convertKey(pubEncodingBlob, priEncodingBlob, (e, keyPair) => {
        if (e) {
          console.error(`convert key failed, errCode: ${e.code}, errMsg: ${e.message}`);
        } else {
          console.info('convert key result: success.');
          x509Crl.verify(keyPair.pubKey, (err, _data) => {
            if (err) {
              console.error(`verify failed, errCode: ${err.code}, errMsg: ${err.message}`);
            } else {
              console.info('verify result: success.');
            }
          });
        }
      });
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`get pubKey failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
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

let pubKeyData = new Uint8Array([
  0x30, 0x81, 0x9F, 0x30, 0x0D, 0x06, 0x09, 0x2A, 0x86, 0x48, 0x86, 0xF7, 0x0D, 0x01, 0x01, 0x01,
  0x05, 0x00, 0x03, 0x81, 0x8D, 0x00, 0x30, 0x81, 0x89, 0x02, 0x81, 0x81, 0x00, 0xDC, 0x4C, 0x2D,
  0x57, 0x49, 0x3D, 0x42, 0x52, 0x1A, 0x09, 0xED, 0x3E, 0x90, 0x29, 0x51, 0xF7, 0x70, 0x15, 0xFE,
  0x76, 0xB0, 0xDB, 0xDF, 0xA1, 0x2C, 0x6C, 0x67, 0x95, 0xDA, 0x63, 0x3D, 0x4F, 0x71, 0x48, 0x8C,
  0x3E, 0xFA, 0x24, 0x79, 0xE9, 0xF2, 0xF2, 0x20, 0xCB, 0xF1, 0x59, 0x6B, 0xED, 0xC8, 0x72, 0x66,
  0x6E, 0x31, 0xD4, 0xF3, 0xCE, 0x0B, 0x12, 0xC4, 0x17, 0x39, 0xB4, 0x52, 0x16, 0xD3, 0xE3, 0xC0,
  0xF8, 0x48, 0xB3, 0xF6, 0x40, 0xD5, 0x47, 0x23, 0x30, 0x7F, 0xA7, 0xC5, 0x5A, 0x5A, 0xBB, 0x5C,
  0x7B, 0xEF, 0x69, 0xE2, 0x74, 0x35, 0x24, 0x22, 0x25, 0x45, 0x7E, 0xFC, 0xE8, 0xC4, 0x52, 0x65,
  0xA0, 0x4E, 0xBC, 0xFD, 0x3F, 0xD9, 0x85, 0x14, 0x8A, 0x5A, 0x93, 0x02, 0x24, 0x6C, 0x19, 0xBA,
  0x81, 0xBE, 0x65, 0x2E, 0xCB, 0xBB, 0xE9, 0x91, 0x7B, 0x7C, 0x47, 0xC2, 0x61, 0x02, 0x03, 0x01,
  0x00, 0x01
]);

let priKeyData = new Uint8Array([
  0x30, 0x82, 0x02, 0x77, 0x02, 0x01, 0x00, 0x30, 0x0D, 0x06, 0x09, 0x2A, 0x86, 0x48, 0x86, 0xF7,
  0x0D, 0x01, 0x01, 0x01, 0x05, 0x00, 0x04, 0x82, 0x02, 0x61, 0x30, 0x82, 0x02, 0x5D, 0x02, 0x01,
  0x00, 0x02, 0x81, 0x81, 0x00, 0xDC, 0x4C, 0x2D, 0x57, 0x49, 0x3D, 0x42, 0x52, 0x1A, 0x09, 0xED,
  0x3E, 0x90, 0x29, 0x51, 0xF7, 0x70, 0x15, 0xFE, 0x76, 0xB0, 0xDB, 0xDF, 0xA1, 0x2C, 0x6C, 0x67,
  0x95, 0xDA, 0x63, 0x3D, 0x4F, 0x71, 0x48, 0x8C, 0x3E, 0xFA, 0x24, 0x79, 0xE9, 0xF2, 0xF2, 0x20,
  0xCB, 0xF1, 0x59, 0x6B, 0xED, 0xC8, 0x72, 0x66, 0x6E, 0x31, 0xD4, 0xF3, 0xCE, 0x0B, 0x12, 0xC4,
  0x17, 0x39, 0xB4, 0x52, 0x16, 0xD3, 0xE3, 0xC0, 0xF8, 0x48, 0xB3, 0xF6, 0x40, 0xD5, 0x47, 0x23,
  0x30, 0x7F, 0xA7, 0xC5, 0x5A, 0x5A, 0xBB, 0x5C, 0x7B, 0xEF, 0x69, 0xE2, 0x74, 0x35, 0x24, 0x22,
  0x25, 0x45, 0x7E, 0xFC, 0xE8, 0xC4, 0x52, 0x65, 0xA0, 0x4E, 0xBC, 0xFD, 0x3F, 0xD9, 0x85, 0x14,
  0x8A, 0x5A, 0x93, 0x02, 0x24, 0x6C, 0x19, 0xBA, 0x81, 0xBE, 0x65, 0x2E, 0xCB, 0xBB, 0xE9, 0x91,
  0x7B, 0x7C, 0x47, 0xC2, 0x61, 0x02, 0x03, 0x01, 0x00, 0x01, 0x02, 0x81, 0x80, 0x5A, 0xCF, 0x0F,
  0xF5, 0xA6, 0x1C, 0x19, 0x65, 0x8C, 0x94, 0x40, 0xF6, 0x84, 0x28, 0x74, 0x40, 0x42, 0x34, 0xDE,
  0xC3, 0x00, 0x5E, 0x72, 0x4D, 0x96, 0xE9, 0x4C, 0xBD, 0xC9, 0xDB, 0x14, 0x9F, 0xD5, 0xBB, 0xA9,
  0x0C, 0x20, 0xC2, 0xBE, 0x7A, 0x80, 0x89, 0xEC, 0x99, 0x04, 0xF0, 0xEE, 0x7B, 0x83, 0x20, 0x1D,
  0x37, 0x19, 0x55, 0x85, 0xF6, 0x8E, 0x3B, 0xFB, 0x16, 0xF3, 0xD3, 0x6F, 0xEE, 0x73, 0x12, 0x53,
  0xCA, 0x77, 0xD7, 0x6C, 0x29, 0xF5, 0x08, 0xA3, 0x09, 0x01, 0x0B, 0x00, 0x05, 0x57, 0xAD, 0x4D,
  0xF0, 0x92, 0xB2, 0x5A, 0x8B, 0x19, 0x09, 0x81, 0x86, 0xFE, 0x66, 0xB9, 0x33, 0x88, 0x28, 0xF3,
  0x37, 0x73, 0x09, 0x5F, 0xD7, 0xC9, 0xC6, 0xFA, 0x13, 0x74, 0xFE, 0xAE, 0x53, 0xA9, 0x71, 0x67,
  0xCE, 0x3A, 0xE6, 0x8D, 0x35, 0xD1, 0xB8, 0xFD, 0x6F, 0x0D, 0x43, 0xC2, 0xD1, 0x02, 0x41, 0x00,
  0xF7, 0x33, 0xE5, 0x6C, 0x29, 0x5A, 0x30, 0x58, 0xA4, 0x52, 0x65, 0xA0, 0x39, 0xC2, 0xE8, 0xAE,
  0x5F, 0xA3, 0x2D, 0x0C, 0x65, 0xB1, 0x7B, 0xFD, 0x92, 0xBF, 0x47, 0x87, 0x97, 0x40, 0xCB, 0x54,
  0xF9, 0xBB, 0x50, 0x27, 0x70, 0x51, 0xD0, 0xD8, 0x48, 0x0D, 0xC6, 0x47, 0x60, 0xF8, 0x4E, 0x0A,
  0x32, 0x76, 0x6D, 0xA4, 0xBA, 0x40, 0xE5, 0x58, 0xF8, 0x4A, 0x39, 0x4E, 0xF8, 0x3F, 0x4E, 0x2D,
  0x02, 0x41, 0x00, 0xE4, 0x23, 0x2A, 0x5F, 0x59, 0xCF, 0x7C, 0x91, 0x24, 0x0D, 0xA2, 0x44, 0x17,
  0xCD, 0x37, 0xDE, 0x1F, 0x53, 0x4D, 0x33, 0x9F, 0x90, 0x4D, 0xD9, 0x72, 0x64, 0x25, 0xBA, 0xAB,
  0x47, 0x91, 0xC4, 0x99, 0x95, 0x86, 0xB5, 0x8A, 0xEA, 0x77, 0xF7, 0x64, 0x72, 0x5E, 0xB7, 0xBB,
  0x16, 0xA1, 0x64, 0xA4, 0xE1, 0x2D, 0x76, 0x6D, 0xEF, 0xB1, 0x5E, 0xD6, 0x17, 0xE8, 0xAA, 0xB6,
  0xA0, 0xD9, 0x85, 0x02, 0x41, 0x00, 0xDF, 0xC8, 0x5B, 0x28, 0x4F, 0x47, 0x15, 0xFD, 0x28, 0xC4,
  0x6E, 0xBB, 0x5D, 0x8E, 0xD4, 0x95, 0x06, 0x7E, 0xF1, 0x89, 0x07, 0x86, 0x64, 0x78, 0x69, 0x20,
  0x3F, 0xE0, 0xBF, 0x4C, 0x28, 0xC6, 0x04, 0x4D, 0x4D, 0x82, 0x66, 0x6B, 0xAA, 0x64, 0x20, 0xD6,
  0x57, 0x68, 0xC6, 0xA0, 0x02, 0x05, 0xB9, 0x28, 0xFC, 0x98, 0xE3, 0x03, 0x5C, 0x9B, 0xEE, 0x29,
  0x43, 0x37, 0xFA, 0x03, 0x55, 0x01, 0x02, 0x40, 0x69, 0x5B, 0x7C, 0x24, 0x10, 0xDB, 0xEB, 0x91,
  0x33, 0xEF, 0x3F, 0xF2, 0xE6, 0x73, 0x15, 0xCB, 0xF4, 0xF7, 0x89, 0x7D, 0xBF, 0xC0, 0xEA, 0xD2,
  0xF3, 0x2B, 0x20, 0xE9, 0x76, 0x54, 0x55, 0x13, 0x50, 0x42, 0x67, 0xB5, 0xCB, 0x73, 0xC0, 0xF7,
  0x75, 0x62, 0x04, 0x30, 0x21, 0xAC, 0xAF, 0xD8, 0x44, 0xF4, 0xE1, 0x04, 0x02, 0x7D, 0x61, 0x92,
  0x84, 0x99, 0x02, 0x10, 0x64, 0xCB, 0x1F, 0xE9, 0x02, 0x41, 0x00, 0xAB, 0x4B, 0x7D, 0x90, 0x7C,
  0x57, 0x08, 0x6B, 0xC0, 0x43, 0x72, 0x09, 0x8A, 0x18, 0x35, 0x36, 0x64, 0x9D, 0x84, 0x8D, 0xF1,
  0x84, 0x94, 0x48, 0xC6, 0x80, 0x9D, 0xB9, 0xA2, 0x58, 0x0A, 0x4D, 0x0A, 0xCA, 0x1E, 0xD6, 0x05,
  0x55, 0x5B, 0xFE, 0xD7, 0xAA, 0x70, 0xED, 0x76, 0xB3, 0x40, 0x2E, 0xA0, 0xB3, 0x32, 0x37, 0xB0,
  0xA0, 0xB9, 0x96, 0x2D, 0xC4, 0x70, 0xE9, 0x99, 0x10, 0x67, 0x8D
]);

// 证书吊销列表二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob, (error, x509CRL) => {
  if (error) {
    console.error(`createX509Crl failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createX509Crl result: success.');
    try {
      let keyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024|PRIMES_3');
      console.info('createAsyKeyGenerator result: success.');
      let priEncodingBlob: cryptoFramework.DataBlob = {
        data: priKeyData
      };
      let pubEncodingBlob: cryptoFramework.DataBlob = {
        data: pubKeyData
      };
      keyGenerator.convertKey(pubEncodingBlob, priEncodingBlob, (e, keyPair) => {
        if (e) {
          console.error(`convert key failed, errCode: ${e.code}, errMsg: ${e.message}`);
        } else {
          console.info('convert key result: success.');
          x509CRL.verify(keyPair.pubKey, (err, _data) => {
            if (err) {
              console.error(`verify failed, errCode: ${err.code}, errMsg: ${err.message}`);
            } else {
              console.info('verify result: success.');
            }
          });
        }
      });
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`get pubKey failed, errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});
```

## verify

```TypeScript
verify(key: cryptoFramework.PubKey): Promise<void>
```

表示对证书验签。使用Promise方式返回结果。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | cryptoFramework.PubKey | 是 | 用于验签的公钥对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
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

cert.createX509Cert(encodingBlob).then(x509Cert => {
  console.info('createX509Cert result: success.');

  try {
    // 业务需通过上级X509Cert证书对象（或当前证书对象为自签名的证书）的getPublicKey获取PubKey。
    let pubKey = x509Cert.getPublicKey();
    x509Cert.verify(pubKey).then(_result => {
      console.info('verify result: success.');
    }).catch((error: BusinessError) => {
      console.error(`verify failed, errCode: ${error.code}, errMsg: ${error.message}`);
    });
  } catch (error) {
    console.error(`getPublicKey failed: errCode: ${error.code}, errMsg: ${error.message}`);
  }
}).catch((error: BusinessError) => {
  console.error(`createX509Cert failed, errCode: ${error.code}, errMsg: ${error.message}`);
});
```

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
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

let pubKeyData = new Uint8Array([
  0x30, 0x81, 0x9F, 0x30, 0x0D, 0x06, 0x09, 0x2A, 0x86, 0x48, 0x86, 0xF7, 0x0D, 0x01, 0x01, 0x01,
  0x05, 0x00, 0x03, 0x81, 0x8D, 0x00, 0x30, 0x81, 0x89, 0x02, 0x81, 0x81, 0x00, 0xDC, 0x4C, 0x2D,
  0x57, 0x49, 0x3D, 0x42, 0x52, 0x1A, 0x09, 0xED, 0x3E, 0x90, 0x29, 0x51, 0xF7, 0x70, 0x15, 0xFE,
  0x76, 0xB0, 0xDB, 0xDF, 0xA1, 0x2C, 0x6C, 0x67, 0x95, 0xDA, 0x63, 0x3D, 0x4F, 0x71, 0x48, 0x8C,
  0x3E, 0xFA, 0x24, 0x79, 0xE9, 0xF2, 0xF2, 0x20, 0xCB, 0xF1, 0x59, 0x6B, 0xED, 0xC8, 0x72, 0x66,
  0x6E, 0x31, 0xD4, 0xF3, 0xCE, 0x0B, 0x12, 0xC4, 0x17, 0x39, 0xB4, 0x52, 0x16, 0xD3, 0xE3, 0xC0,
  0xF8, 0x48, 0xB3, 0xF6, 0x40, 0xD5, 0x47, 0x23, 0x30, 0x7F, 0xA7, 0xC5, 0x5A, 0x5A, 0xBB, 0x5C,
  0x7B, 0xEF, 0x69, 0xE2, 0x74, 0x35, 0x24, 0x22, 0x25, 0x45, 0x7E, 0xFC, 0xE8, 0xC4, 0x52, 0x65,
  0xA0, 0x4E, 0xBC, 0xFD, 0x3F, 0xD9, 0x85, 0x14, 0x8A, 0x5A, 0x93, 0x02, 0x24, 0x6C, 0x19, 0xBA,
  0x81, 0xBE, 0x65, 0x2E, 0xCB, 0xBB, 0xE9, 0x91, 0x7B, 0x7C, 0x47, 0xC2, 0x61, 0x02, 0x03, 0x01,
  0x00, 0x01
]);

let priKeyData = new Uint8Array([
  0x30, 0x82, 0x02, 0x77, 0x02, 0x01, 0x00, 0x30, 0x0D, 0x06, 0x09, 0x2A, 0x86, 0x48, 0x86, 0xF7,
  0x0D, 0x01, 0x01, 0x01, 0x05, 0x00, 0x04, 0x82, 0x02, 0x61, 0x30, 0x82, 0x02, 0x5D, 0x02, 0x01,
  0x00, 0x02, 0x81, 0x81, 0x00, 0xDC, 0x4C, 0x2D, 0x57, 0x49, 0x3D, 0x42, 0x52, 0x1A, 0x09, 0xED,
  0x3E, 0x90, 0x29, 0x51, 0xF7, 0x70, 0x15, 0xFE, 0x76, 0xB0, 0xDB, 0xDF, 0xA1, 0x2C, 0x6C, 0x67,
  0x95, 0xDA, 0x63, 0x3D, 0x4F, 0x71, 0x48, 0x8C, 0x3E, 0xFA, 0x24, 0x79, 0xE9, 0xF2, 0xF2, 0x20,
  0xCB, 0xF1, 0x59, 0x6B, 0xED, 0xC8, 0x72, 0x66, 0x6E, 0x31, 0xD4, 0xF3, 0xCE, 0x0B, 0x12, 0xC4,
  0x17, 0x39, 0xB4, 0x52, 0x16, 0xD3, 0xE3, 0xC0, 0xF8, 0x48, 0xB3, 0xF6, 0x40, 0xD5, 0x47, 0x23,
  0x30, 0x7F, 0xA7, 0xC5, 0x5A, 0x5A, 0xBB, 0x5C, 0x7B, 0xEF, 0x69, 0xE2, 0x74, 0x35, 0x24, 0x22,
  0x25, 0x45, 0x7E, 0xFC, 0xE8, 0xC4, 0x52, 0x65, 0xA0, 0x4E, 0xBC, 0xFD, 0x3F, 0xD9, 0x85, 0x14,
  0x8A, 0x5A, 0x93, 0x02, 0x24, 0x6C, 0x19, 0xBA, 0x81, 0xBE, 0x65, 0x2E, 0xCB, 0xBB, 0xE9, 0x91,
  0x7B, 0x7C, 0x47, 0xC2, 0x61, 0x02, 0x03, 0x01, 0x00, 0x01, 0x02, 0x81, 0x80, 0x5A, 0xCF, 0x0F,
  0xF5, 0xA6, 0x1C, 0x19, 0x65, 0x8C, 0x94, 0x40, 0xF6, 0x84, 0x28, 0x74, 0x40, 0x42, 0x34, 0xDE,
  0xC3, 0x00, 0x5E, 0x72, 0x4D, 0x96, 0xE9, 0x4C, 0xBD, 0xC9, 0xDB, 0x14, 0x9F, 0xD5, 0xBB, 0xA9,
  0x0C, 0x20, 0xC2, 0xBE, 0x7A, 0x80, 0x89, 0xEC, 0x99, 0x04, 0xF0, 0xEE, 0x7B, 0x83, 0x20, 0x1D,
  0x37, 0x19, 0x55, 0x85, 0xF6, 0x8E, 0x3B, 0xFB, 0x16, 0xF3, 0xD3, 0x6F, 0xEE, 0x73, 0x12, 0x53,
  0xCA, 0x77, 0xD7, 0x6C, 0x29, 0xF5, 0x08, 0xA3, 0x09, 0x01, 0x0B, 0x00, 0x05, 0x57, 0xAD, 0x4D,
  0xF0, 0x92, 0xB2, 0x5A, 0x8B, 0x19, 0x09, 0x81, 0x86, 0xFE, 0x66, 0xB9, 0x33, 0x88, 0x28, 0xF3,
  0x37, 0x73, 0x09, 0x5F, 0xD7, 0xC9, 0xC6, 0xFA, 0x13, 0x74, 0xFE, 0xAE, 0x53, 0xA9, 0x71, 0x67,
  0xCE, 0x3A, 0xE6, 0x8D, 0x35, 0xD1, 0xB8, 0xFD, 0x6F, 0x0D, 0x43, 0xC2, 0xD1, 0x02, 0x41, 0x00,
  0xF7, 0x33, 0xE5, 0x6C, 0x29, 0x5A, 0x30, 0x58, 0xA4, 0x52, 0x65, 0xA0, 0x39, 0xC2, 0xE8, 0xAE,
  0x5F, 0xA3, 0x2D, 0x0C, 0x65, 0xB1, 0x7B, 0xFD, 0x92, 0xBF, 0x47, 0x87, 0x97, 0x40, 0xCB, 0x54,
  0xF9, 0xBB, 0x50, 0x27, 0x70, 0x51, 0xD0, 0xD8, 0x48, 0x0D, 0xC6, 0x47, 0x60, 0xF8, 0x4E, 0x0A,
  0x32, 0x76, 0x6D, 0xA4, 0xBA, 0x40, 0xE5, 0x58, 0xF8, 0x4A, 0x39, 0x4E, 0xF8, 0x3F, 0x4E, 0x2D,
  0x02, 0x41, 0x00, 0xE4, 0x23, 0x2A, 0x5F, 0x59, 0xCF, 0x7C, 0x91, 0x24, 0x0D, 0xA2, 0x44, 0x17,
  0xCD, 0x37, 0xDE, 0x1F, 0x53, 0x4D, 0x33, 0x9F, 0x90, 0x4D, 0xD9, 0x72, 0x64, 0x25, 0xBA, 0xAB,
  0x47, 0x91, 0xC4, 0x99, 0x95, 0x86, 0xB5, 0x8A, 0xEA, 0x77, 0xF7, 0x64, 0x72, 0x5E, 0xB7, 0xBB,
  0x16, 0xA1, 0x64, 0xA4, 0xE1, 0x2D, 0x76, 0x6D, 0xEF, 0xB1, 0x5E, 0xD6, 0x17, 0xE8, 0xAA, 0xB6,
  0xA0, 0xD9, 0x85, 0x02, 0x41, 0x00, 0xDF, 0xC8, 0x5B, 0x28, 0x4F, 0x47, 0x15, 0xFD, 0x28, 0xC4,
  0x6E, 0xBB, 0x5D, 0x8E, 0xD4, 0x95, 0x06, 0x7E, 0xF1, 0x89, 0x07, 0x86, 0x64, 0x78, 0x69, 0x20,
  0x3F, 0xE0, 0xBF, 0x4C, 0x28, 0xC6, 0x04, 0x4D, 0x4D, 0x82, 0x66, 0x6B, 0xAA, 0x64, 0x20, 0xD6,
  0x57, 0x68, 0xC6, 0xA0, 0x02, 0x05, 0xB9, 0x28, 0xFC, 0x98, 0xE3, 0x03, 0x5C, 0x9B, 0xEE, 0x29,
  0x43, 0x37, 0xFA, 0x03, 0x55, 0x01, 0x02, 0x40, 0x69, 0x5B, 0x7C, 0x24, 0x10, 0xDB, 0xEB, 0x91,
  0x33, 0xEF, 0x3F, 0xF2, 0xE6, 0x73, 0x15, 0xCB, 0xF4, 0xF7, 0x89, 0x7D, 0xBF, 0xC0, 0xEA, 0xD2,
  0xF3, 0x2B, 0x20, 0xE9, 0x76, 0x54, 0x55, 0x13, 0x50, 0x42, 0x67, 0xB5, 0xCB, 0x73, 0xC0, 0xF7,
  0x75, 0x62, 0x04, 0x30, 0x21, 0xAC, 0xAF, 0xD8, 0x44, 0xF4, 0xE1, 0x04, 0x02, 0x7D, 0x61, 0x92,
  0x84, 0x99, 0x02, 0x10, 0x64, 0xCB, 0x1F, 0xE9, 0x02, 0x41, 0x00, 0xAB, 0x4B, 0x7D, 0x90, 0x7C,
  0x57, 0x08, 0x6B, 0xC0, 0x43, 0x72, 0x09, 0x8A, 0x18, 0x35, 0x36, 0x64, 0x9D, 0x84, 0x8D, 0xF1,
  0x84, 0x94, 0x48, 0xC6, 0x80, 0x9D, 0xB9, 0xA2, 0x58, 0x0A, 0x4D, 0x0A, 0xCA, 0x1E, 0xD6, 0x05,
  0x55, 0x5B, 0xFE, 0xD7, 0xAA, 0x70, 0xED, 0x76, 0xB3, 0x40, 0x2E, 0xA0, 0xB3, 0x32, 0x37, 0xB0,
  0xA0, 0xB9, 0x96, 0x2D, 0xC4, 0x70, 0xE9, 0x99, 0x10, 0x67, 0x8D
]);

// 证书吊销列表二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509Crl(encodingBlob).then(x509Crl => {
  console.info('createX509Crl result: success.');

  try {
    // 生成公钥对象。
    let keyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024|PRIMES_3');
    console.info('createAsyKeyGenerator result: success.');
    let priEncodingBlob: cryptoFramework.DataBlob = {
      data: priKeyData
    };
    let pubEncodingBlob: cryptoFramework.DataBlob = {
      data: pubKeyData
    };
    keyGenerator.convertKey(pubEncodingBlob, priEncodingBlob).then((keyPair) => {
      console.info('convert key result: success.');
      x509Crl.verify(keyPair.pubKey).then(_result => {
        console.info('verify result: success.');
      }).catch((error: BusinessError) => {
        console.error(`verify failed, errCode: ${error.code}, errMsg: ${error.message}`);
      });
    }).catch((error: BusinessError) => {
      console.error(`convert key failed, errCode: ${error.code}, errMsg: ${error.message}`);
    });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`get pubKey failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}).catch((error: BusinessError) => {
  console.error(`createX509Crl failed, errCode: ${error.code}, errMsg: ${error.message}`);
});
```

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
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

let pubKeyData = new Uint8Array([
  0x30, 0x81, 0x9F, 0x30, 0x0D, 0x06, 0x09, 0x2A, 0x86, 0x48, 0x86, 0xF7, 0x0D, 0x01, 0x01, 0x01,
  0x05, 0x00, 0x03, 0x81, 0x8D, 0x00, 0x30, 0x81, 0x89, 0x02, 0x81, 0x81, 0x00, 0xDC, 0x4C, 0x2D,
  0x57, 0x49, 0x3D, 0x42, 0x52, 0x1A, 0x09, 0xED, 0x3E, 0x90, 0x29, 0x51, 0xF7, 0x70, 0x15, 0xFE,
  0x76, 0xB0, 0xDB, 0xDF, 0xA1, 0x2C, 0x6C, 0x67, 0x95, 0xDA, 0x63, 0x3D, 0x4F, 0x71, 0x48, 0x8C,
  0x3E, 0xFA, 0x24, 0x79, 0xE9, 0xF2, 0xF2, 0x20, 0xCB, 0xF1, 0x59, 0x6B, 0xED, 0xC8, 0x72, 0x66,
  0x6E, 0x31, 0xD4, 0xF3, 0xCE, 0x0B, 0x12, 0xC4, 0x17, 0x39, 0xB4, 0x52, 0x16, 0xD3, 0xE3, 0xC0,
  0xF8, 0x48, 0xB3, 0xF6, 0x40, 0xD5, 0x47, 0x23, 0x30, 0x7F, 0xA7, 0xC5, 0x5A, 0x5A, 0xBB, 0x5C,
  0x7B, 0xEF, 0x69, 0xE2, 0x74, 0x35, 0x24, 0x22, 0x25, 0x45, 0x7E, 0xFC, 0xE8, 0xC4, 0x52, 0x65,
  0xA0, 0x4E, 0xBC, 0xFD, 0x3F, 0xD9, 0x85, 0x14, 0x8A, 0x5A, 0x93, 0x02, 0x24, 0x6C, 0x19, 0xBA,
  0x81, 0xBE, 0x65, 0x2E, 0xCB, 0xBB, 0xE9, 0x91, 0x7B, 0x7C, 0x47, 0xC2, 0x61, 0x02, 0x03, 0x01,
  0x00, 0x01
]);

let priKeyData = new Uint8Array([
  0x30, 0x82, 0x02, 0x77, 0x02, 0x01, 0x00, 0x30, 0x0D, 0x06, 0x09, 0x2A, 0x86, 0x48, 0x86, 0xF7,
  0x0D, 0x01, 0x01, 0x01, 0x05, 0x00, 0x04, 0x82, 0x02, 0x61, 0x30, 0x82, 0x02, 0x5D, 0x02, 0x01,
  0x00, 0x02, 0x81, 0x81, 0x00, 0xDC, 0x4C, 0x2D, 0x57, 0x49, 0x3D, 0x42, 0x52, 0x1A, 0x09, 0xED,
  0x3E, 0x90, 0x29, 0x51, 0xF7, 0x70, 0x15, 0xFE, 0x76, 0xB0, 0xDB, 0xDF, 0xA1, 0x2C, 0x6C, 0x67,
  0x95, 0xDA, 0x63, 0x3D, 0x4F, 0x71, 0x48, 0x8C, 0x3E, 0xFA, 0x24, 0x79, 0xE9, 0xF2, 0xF2, 0x20,
  0xCB, 0xF1, 0x59, 0x6B, 0xED, 0xC8, 0x72, 0x66, 0x6E, 0x31, 0xD4, 0xF3, 0xCE, 0x0B, 0x12, 0xC4,
  0x17, 0x39, 0xB4, 0x52, 0x16, 0xD3, 0xE3, 0xC0, 0xF8, 0x48, 0xB3, 0xF6, 0x40, 0xD5, 0x47, 0x23,
  0x30, 0x7F, 0xA7, 0xC5, 0x5A, 0x5A, 0xBB, 0x5C, 0x7B, 0xEF, 0x69, 0xE2, 0x74, 0x35, 0x24, 0x22,
  0x25, 0x45, 0x7E, 0xFC, 0xE8, 0xC4, 0x52, 0x65, 0xA0, 0x4E, 0xBC, 0xFD, 0x3F, 0xD9, 0x85, 0x14,
  0x8A, 0x5A, 0x93, 0x02, 0x24, 0x6C, 0x19, 0xBA, 0x81, 0xBE, 0x65, 0x2E, 0xCB, 0xBB, 0xE9, 0x91,
  0x7B, 0x7C, 0x47, 0xC2, 0x61, 0x02, 0x03, 0x01, 0x00, 0x01, 0x02, 0x81, 0x80, 0x5A, 0xCF, 0x0F,
  0xF5, 0xA6, 0x1C, 0x19, 0x65, 0x8C, 0x94, 0x40, 0xF6, 0x84, 0x28, 0x74, 0x40, 0x42, 0x34, 0xDE,
  0xC3, 0x00, 0x5E, 0x72, 0x4D, 0x96, 0xE9, 0x4C, 0xBD, 0xC9, 0xDB, 0x14, 0x9F, 0xD5, 0xBB, 0xA9,
  0x0C, 0x20, 0xC2, 0xBE, 0x7A, 0x80, 0x89, 0xEC, 0x99, 0x04, 0xF0, 0xEE, 0x7B, 0x83, 0x20, 0x1D,
  0x37, 0x19, 0x55, 0x85, 0xF6, 0x8E, 0x3B, 0xFB, 0x16, 0xF3, 0xD3, 0x6F, 0xEE, 0x73, 0x12, 0x53,
  0xCA, 0x77, 0xD7, 0x6C, 0x29, 0xF5, 0x08, 0xA3, 0x09, 0x01, 0x0B, 0x00, 0x05, 0x57, 0xAD, 0x4D,
  0xF0, 0x92, 0xB2, 0x5A, 0x8B, 0x19, 0x09, 0x81, 0x86, 0xFE, 0x66, 0xB9, 0x33, 0x88, 0x28, 0xF3,
  0x37, 0x73, 0x09, 0x5F, 0xD7, 0xC9, 0xC6, 0xFA, 0x13, 0x74, 0xFE, 0xAE, 0x53, 0xA9, 0x71, 0x67,
  0xCE, 0x3A, 0xE6, 0x8D, 0x35, 0xD1, 0xB8, 0xFD, 0x6F, 0x0D, 0x43, 0xC2, 0xD1, 0x02, 0x41, 0x00,
  0xF7, 0x33, 0xE5, 0x6C, 0x29, 0x5A, 0x30, 0x58, 0xA4, 0x52, 0x65, 0xA0, 0x39, 0xC2, 0xE8, 0xAE,
  0x5F, 0xA3, 0x2D, 0x0C, 0x65, 0xB1, 0x7B, 0xFD, 0x92, 0xBF, 0x47, 0x87, 0x97, 0x40, 0xCB, 0x54,
  0xF9, 0xBB, 0x50, 0x27, 0x70, 0x51, 0xD0, 0xD8, 0x48, 0x0D, 0xC6, 0x47, 0x60, 0xF8, 0x4E, 0x0A,
  0x32, 0x76, 0x6D, 0xA4, 0xBA, 0x40, 0xE5, 0x58, 0xF8, 0x4A, 0x39, 0x4E, 0xF8, 0x3F, 0x4E, 0x2D,
  0x02, 0x41, 0x00, 0xE4, 0x23, 0x2A, 0x5F, 0x59, 0xCF, 0x7C, 0x91, 0x24, 0x0D, 0xA2, 0x44, 0x17,
  0xCD, 0x37, 0xDE, 0x1F, 0x53, 0x4D, 0x33, 0x9F, 0x90, 0x4D, 0xD9, 0x72, 0x64, 0x25, 0xBA, 0xAB,
  0x47, 0x91, 0xC4, 0x99, 0x95, 0x86, 0xB5, 0x8A, 0xEA, 0x77, 0xF7, 0x64, 0x72, 0x5E, 0xB7, 0xBB,
  0x16, 0xA1, 0x64, 0xA4, 0xE1, 0x2D, 0x76, 0x6D, 0xEF, 0xB1, 0x5E, 0xD6, 0x17, 0xE8, 0xAA, 0xB6,
  0xA0, 0xD9, 0x85, 0x02, 0x41, 0x00, 0xDF, 0xC8, 0x5B, 0x28, 0x4F, 0x47, 0x15, 0xFD, 0x28, 0xC4,
  0x6E, 0xBB, 0x5D, 0x8E, 0xD4, 0x95, 0x06, 0x7E, 0xF1, 0x89, 0x07, 0x86, 0x64, 0x78, 0x69, 0x20,
  0x3F, 0xE0, 0xBF, 0x4C, 0x28, 0xC6, 0x04, 0x4D, 0x4D, 0x82, 0x66, 0x6B, 0xAA, 0x64, 0x20, 0xD6,
  0x57, 0x68, 0xC6, 0xA0, 0x02, 0x05, 0xB9, 0x28, 0xFC, 0x98, 0xE3, 0x03, 0x5C, 0x9B, 0xEE, 0x29,
  0x43, 0x37, 0xFA, 0x03, 0x55, 0x01, 0x02, 0x40, 0x69, 0x5B, 0x7C, 0x24, 0x10, 0xDB, 0xEB, 0x91,
  0x33, 0xEF, 0x3F, 0xF2, 0xE6, 0x73, 0x15, 0xCB, 0xF4, 0xF7, 0x89, 0x7D, 0xBF, 0xC0, 0xEA, 0xD2,
  0xF3, 0x2B, 0x20, 0xE9, 0x76, 0x54, 0x55, 0x13, 0x50, 0x42, 0x67, 0xB5, 0xCB, 0x73, 0xC0, 0xF7,
  0x75, 0x62, 0x04, 0x30, 0x21, 0xAC, 0xAF, 0xD8, 0x44, 0xF4, 0xE1, 0x04, 0x02, 0x7D, 0x61, 0x92,
  0x84, 0x99, 0x02, 0x10, 0x64, 0xCB, 0x1F, 0xE9, 0x02, 0x41, 0x00, 0xAB, 0x4B, 0x7D, 0x90, 0x7C,
  0x57, 0x08, 0x6B, 0xC0, 0x43, 0x72, 0x09, 0x8A, 0x18, 0x35, 0x36, 0x64, 0x9D, 0x84, 0x8D, 0xF1,
  0x84, 0x94, 0x48, 0xC6, 0x80, 0x9D, 0xB9, 0xA2, 0x58, 0x0A, 0x4D, 0x0A, 0xCA, 0x1E, 0xD6, 0x05,
  0x55, 0x5B, 0xFE, 0xD7, 0xAA, 0x70, 0xED, 0x76, 0xB3, 0x40, 0x2E, 0xA0, 0xB3, 0x32, 0x37, 0xB0,
  0xA0, 0xB9, 0x96, 0x2D, 0xC4, 0x70, 0xE9, 0x99, 0x10, 0x67, 0x8D
]);

// 证书吊销列表二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(crlData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

cert.createX509CRL(encodingBlob).then(x509CRL => {
  console.info('createX509Crl result: success.');

  try {
    // 生成公钥对象。
    let keyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024|PRIMES_3');
    console.info('createAsyKeyGenerator result: success.');
    let priEncodingBlob: cryptoFramework.DataBlob = {
      data: priKeyData
    };
    let pubEncodingBlob: cryptoFramework.DataBlob = {
      data: pubKeyData
    };
    keyGenerator.convertKey(pubEncodingBlob, priEncodingBlob).then((keyPair) => {
      console.info('convert key result: success.');
      x509CRL.verify(keyPair.pubKey).then(_result => {
        console.info('verify result: success.');
      }).catch((error: BusinessError) => {
        console.error(`verify failed, errCode: ${error.code}, errMsg: ${error.message}`);
      });
    }).catch((error: BusinessError) => {
      console.error(`convert key failed, errCode: ${error.code}, errMsg: ${error.message}`);
    });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`get pubKey failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}).catch((error: BusinessError) => {
  console.error(`createX509Crl failed, errCode: ${error.code}, errMsg: ${error.message}`);
});
```
