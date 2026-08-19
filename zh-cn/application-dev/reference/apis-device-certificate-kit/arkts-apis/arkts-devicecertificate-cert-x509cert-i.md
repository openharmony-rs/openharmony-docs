# X509Cert

提供用于X.509证书操作的API。

**起始版本：** 23

<!--Device-cert-interface X509Cert--><!--Device-cert-interface X509Cert-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { certificateManager } from '@kit.DeviceCertificateKit';
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## checkValidityWithDate

```TypeScript
checkValidityWithDate(date: string): void
```

表示校验X.509证书有效期。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-checkValidityWithDate(date: string): void--><!--Device-X509Cert-checkValidityWithDate(date: string): void-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | string | 是 | 表示日期，日期采用ASN.1 UTCTime或GeneralizedTime格式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19030003](../errorcode-cert.md#19030003-证书尚未生效) | The certificate has not taken effect. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |
| [19030004](../errorcode-cert.md#19030004-证书过期) | The certificate has expired. |

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

function TestCheckValidityWithDate() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      let date = '231001000001Z';
      // Verify the certificate validity period.
      if (x509Cert != undefined) {
        try {
          x509Cert.checkValidityWithDate(date);
          console.info("checkValidityWithDate result: success.");
        } catch (error) {
          let e: BusinessError = error as BusinessError;
          console.error('checkValidityWithDate failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getBasicConstraints

```TypeScript
getBasicConstraints(): int
```

表示获取X.509证书基本约束。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getBasicConstraints(): int--><!--Device-X509Cert-getBasicConstraints(): int-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 表示X.509证书基本约束。 |

**示例**

ArkTS-Dyn示例：

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

function TestGetBasicConstraints() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let basicConstraints = x509Cert.getBasicConstraints();
          console.info('basicConstraints = ' + basicConstraints);
          console.info('getBasicConstraints result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error(`getBasicConstraints failed, ${e.code}, ${e.message}`);
        }
      }
    }
  });
}
```

## getCRLDistributionPoint

```TypeScript
getCRLDistributionPoint(): DataArray
```

获取X.509证书CRL的分发点统一资源标识符。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getCRLDistributionPoint(): DataArray--><!--Device-X509Cert-getCRLDistributionPoint(): DataArray-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | 表示X.509证书CRL的分发点统一资源标识符。 |

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

let certData = "-----BEGIN CERTIFICATE-----\n" +
  "MIIB/jCCAaSgAwIBAgICA+gwCgYIKoZIzj0EAwIwLDELMAkGA1UEBhMCQ04xDTAL\n" +
  "BgNVBAoMBHRlc3QxDjAMBgNVBAMMBXN1YmNhMB4XDTIzMTAwNzA0MDEwOFoXDTMz\n" +
  "MTAwNDA0MDEwOFowLDELMAkGA1UEBhMCQ04xDTALBgNVBAoMBHRlc3QxDjAMBgNV\n" +
  "BAMMBWxvY2FsMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEZDPvdlJI6Yv4fiaR\n" +
  "nQHcusXVbukk90mQ0rBGOYRikFvgvm5cjTdaUGcQKEtwYIKDQl5n6Pf7ElCJ7GRz\n" +
  "raWZ+qOBtTCBsjAJBgNVHRMEAjAAMCwGCWCGSAGG+EIBDQQfFh1PcGVuU1NMIEdl\n" +
  "bmVyYXRlZCBDZXJ0aWZpY2F0ZTAdBgNVHQ4EFgQU63Gbl8gIsUn0VyZ4rya3PCjm\n" +
  "sfEwHwYDVR0jBBgwFoAU77mynM0rz1SD43DQjleWM7bF+MEwNwYDVR0fBDAwLjAs\n" +
  "oCqgKIYmaHR0cDovL3Rlc3QudGVzdENSTGRwLmNvbS9DUkxfRFBfMS5jcmwwCgYI\n" +
  "KoZIzj0EAwIDSAAwRQIhAISKHH9u221mBgdDWfll3loLvEHJ3or9NUO5Zn6SrX6L\n" +
  "AiAtRlOa6/mTD68faQTdhsAaQP955QfW34B4yFqU2Bq72A==\n" +
  "-----END CERTIFICATE-----\n";

// 证书二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certGetCRLDistributionPoint() {
  let x509Cert: cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    let point = x509Cert.getCRLDistributionPoint();
    console.info('point = ' + point.data);
    console.info('getCRLDistributionPoint result: success.');
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('createX509Cert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## getCertSerialNumber

```TypeScript
getCertSerialNumber(): bigint
```

表示获取X.509证书序列号。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getCertSerialNumber(): bigint--><!--Device-X509Cert-getCertSerialNumber(): bigint-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 表示X.509证书序列号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |

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

function TestGetCertSerialNumber() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let serialNumber = x509Cert.getCertSerialNumber();
          console.info('serialNumber = ' + serialNumber);
          console.info('getCertSerialNumber result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getCertSerialNumber failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getEncoded

```TypeScript
getEncoded(callback: AsyncCallback<EncodingBlob>): void
```

表示获取X.509证书序列化数据。使用Callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getEncoded(callback: AsyncCallback<EncodingBlob>): void--><!--Device-X509Cert-getEncoded(callback: AsyncCallback<EncodingBlob>): void-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md)&gt; | 是 | 回调函数。当获取X.509证书序列化数据成功时，err为undefined，data为 获取到的X.509证书序列化数据；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

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
function TestGetEncoded() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        x509Cert.getEncoded((error, _data) => {
        if (error) {
          console.error('getEncoded failed, errCode: ' + error.code + ', errMsg: ' + error.message);
        } else {
          console.info('getEncoded result: success.');
        }
       });
      }
    }
  });
}
```

## getEncoded

```TypeScript
getEncoded(): Promise<EncodingBlob>
```

表示获取X.509证书序列化数据。使用Promise方式返回结果。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getEncoded(): Promise<EncodingBlob>--><!--Device-X509Cert-getEncoded(): Promise<EncodingBlob>-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md)&gt; | Promise对象，返回X.509证书序列化数据。 |

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
  try {
    let x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    try {
      await x509Cert.getEncoded();
      console.info('getEncoded result: success.');
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`getEncoded failed, ${e.code}, ${e.message}`);
    }
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509Cert failed, ${e.code}, ${e.message}`);
  }
}
```

## getExtKeyUsage

```TypeScript
getExtKeyUsage(): DataArray
```

表示获取X.509证书扩展密钥用途。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getExtKeyUsage(): DataArray--><!--Device-X509Cert-getExtKeyUsage(): DataArray-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | 表示X.509证书扩展密钥用途。 |

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

function TestGetExtKeyUsage() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let extKeyUsage = x509Cert.getExtKeyUsage();
          console.info('extKeyUsage = ' + extKeyUsage.data);
          console.info('getExtKeyUsage result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getExtKeyUsage failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getExtensionsObject

```TypeScript
getExtensionsObject(): CertExtension
```

获取证书扩展对象。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getExtensionsObject(): CertExtension--><!--Device-X509Cert-getExtensionsObject(): CertExtension-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CertExtension](arkts-devicecertificate-cert-certextension-i.md) | 证书扩展对象。 |

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

let certData = "-----BEGIN CERTIFICATE-----\n" +
  "MIID1TCCAr2gAwIBAgIITXr1++kFUU4wDQYJKoZIhvcNAQELBQAwcDELMAkGA1UE\n" +
  "BhMCQ04xEjAQBgNVBAgTCWd1YW5nZG9uZzERMA8GA1UEBxMIc2hlbnpoZW4xEjAQ\n" +
  "BgNVBAoTCXRlc3RTZWNDYTESMBAGA1UECxMJdGVzdFNlY0NhMRIwEAYDVQQDEwl0\n" +
  "ZXN0U2VjQ2EwHhcNMjMxMjIxMDAwMDAwWhcNMjcxMjIwMjM1OTU5WjBxMQswCQYD\n" +
  "VQQGEwJDTjEOMAwGA1UECBMFZ2Fuc3UxEDAOBgNVBAcTB2xhbnpob3UxFDASBgNV\n" +
  "BAoTC3Rlc3RUaGlyZENhMRQwEgYDVQQLEwt0ZXN0VGhpcmRDYTEUMBIGA1UEAxML\n" +
  "dGVzdFRoaXJkQ2EwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDJMKSq\n" +
  "Fn4G4EJATauw+4s+n/JbINBAiuhzURzzdt2T8JJQLDV9RHj4mZt84yv6lqEpl2fm\n" +
  "gIClfu173pEV51/PSq5IaV481u/Dz/OTy9TwfxmIXAWdNpyodDOg4I9K7LC01ge8\n" +
  "xxyKFi7k7m2eTGA4dYQM0E0AEXzCpg2JN3IIIPhzHCIVJmYjcbVxiaFkvT4ZFFUk\n" +
  "4rDSbAQdn6dJ29msrFm8iGhMGC/bzq9Bii38Qg4y4o89QYiboRWCxv3XfuibT+jw\n" +
  "O3pmfsFuT8/bKOWVm94FmRxiKuj6iE8UVewxtByzDgAsBtJKDjaCv3IkqfbIu+sq\n" +
  "/eeJkVJRJXAP3ZpLAgMBAAGjcjBwMA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYE\n" +
  "FIxvPSwEmjOMW10H+gn2gy5HvMmMMAsGA1UdDwQEAwIBBjARBglghkgBhvhCAQEE\n" +
  "BAMCAAcwHgYJYIZIAYb4QgENBBEWD3hjYSBjZXJ0aWZpY2F0ZTANBgkqhkiG9w0B\n" +
  "AQsFAAOCAQEAWu0u72g5y1weexPoJQnUgcwVtuC+/tTS9YvyCtKYE91gn97LSWn9\n" +
  "mXXGmLceU27B8JwhER9JeiQO1SUdDcvlfb5vt6eB+5cbZcgeERUBP8t0znh7DbMg\n" +
  "4TFjt9gZ970PZ1OlTBNPoZNRBKIox61KVUhiVKTVSbXlVP1yUF1uSlSq+0NYayHw\n" +
  "MnX1BeLxbAcAsTPYHjoeFJIrGkKlydLyt/8hDQzpLRW5uEUTjjqLh7vef0OaOP80\n" +
  "MmADt6ojRYvwdMDHF0ASJyupLQ+hiRLVadciK8Z5W34JGN2jwEw5X3nXyAgErIJZ\n" +
  "pqdTflnFLnSwy5M3QHB+xjYAcS9l1br2LA==\n" +
  "-----END CERTIFICATE-----\n";

// 证书二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certGetExtensionsObject() {
  let x509Cert: cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    x509Cert.getExtensionsObject();
    console.info('getExtensionsObject result: success.');
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('createX509Cert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## getIssuerAltNames

```TypeScript
getIssuerAltNames(): DataArray
```

表示获取X.509证书颁发者可选名称。 > **说明：** > > 获取到的X.509证书颁发者可选名称数据带字符串结束符。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getIssuerAltNames(): DataArray--><!--Device-X509Cert-getIssuerAltNames(): DataArray-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | 表示X.509证书颁发者可选名称。 |

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

function TestGetIssuerAltNames() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let issuerAltNames = x509Cert.getIssuerAltNames();
          console.info('issuerAltNames = ' + issuerAltNames.data);
          console.info('getIssuerAltNames result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getIssuerAltNames failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getIssuerName

```TypeScript
getIssuerName(): DataBlob
```

表示获取X.509证书颁发者名称。 > **说明：** > > - 获取的X.509证书颁发者名称末尾包含一个NUL终止符（值为0），请根据业务需求决定是否去除该终止符。 > - 获取的证书颁发者名称为ASCII编码，转换为字符串后，是以斜杠（/）开始，以斜杠（/）分隔相对可分辨名称的可分辨名称字符串。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getIssuerName(): DataBlob--><!--Device-X509Cert-getIssuerName(): DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示X.509证书颁发者名称。 |

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

function TestGetIssuerName() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let issuerName = x509Cert.getIssuerName();
          console.info('issuerName = ' + issuerName.data);
          console.info('getIssuerName result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getIssuerName failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getIssuerName

```TypeScript
getIssuerName(encodingType: EncodingType): string
```

表示根据编码类型获取X.509证书颁发者名称。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getIssuerName(encodingType: EncodingType): string--><!--Device-X509Cert-getIssuerName(encodingType: EncodingType): string-End-->

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
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19020003](../errorcode-cert.md#19020003-参数检查失败) | Parameter check failed. Possible causes: <br>1. The value of encodingType is not in the EncodingType enumeration range. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

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

function TestGetIssuerName() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let issuerName = x509Cert.getIssuerName(cert.EncodingType.ENCODING_UTF8);
          console.info('issuerName output is ' + issuerName);
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getIssuerName failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getIssuerX500DistinguishedName

```TypeScript
getIssuerX500DistinguishedName(): X500DistinguishedName
```

获取X.509证书颁发者的X.500可分辨名称。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getIssuerX500DistinguishedName(): X500DistinguishedName--><!--Device-X509Cert-getIssuerX500DistinguishedName(): X500DistinguishedName-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md) | X.500可分辨对象。 |

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

let certData = "-----BEGIN CERTIFICATE-----\n" +
  "MIID1TCCAr2gAwIBAgIITXr1++kFUU4wDQYJKoZIhvcNAQELBQAwcDELMAkGA1UE\n" +
  "BhMCQ04xEjAQBgNVBAgTCWd1YW5nZG9uZzERMA8GA1UEBxMIc2hlbnpoZW4xEjAQ\n" +
  "BgNVBAoTCXRlc3RTZWNDYTESMBAGA1UECxMJdGVzdFNlY0NhMRIwEAYDVQQDEwl0\n" +
  "ZXN0U2VjQ2EwHhcNMjMxMjIxMDAwMDAwWhcNMjcxMjIwMjM1OTU5WjBxMQswCQYD\n" +
  "VQQGEwJDTjEOMAwGA1UECBMFZ2Fuc3UxEDAOBgNVBAcTB2xhbnpob3UxFDASBgNV\n" +
  "BAoTC3Rlc3RUaGlyZENhMRQwEgYDVQQLEwt0ZXN0VGhpcmRDYTEUMBIGA1UEAxML\n" +
  "dGVzdFRoaXJkQ2EwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDJMKSq\n" +
  "Fn4G4EJATauw+4s+n/JbINBAiuhzURzzdt2T8JJQLDV9RHj4mZt84yv6lqEpl2fm\n" +
  "gIClfu173pEV51/PSq5IaV481u/Dz/OTy9TwfxmIXAWdNpyodDOg4I9K7LC01ge8\n" +
  "xxyKFi7k7m2eTGA4dYQM0E0AEXzCpg2JN3IIIPhzHCIVJmYjcbVxiaFkvT4ZFFUk\n" +
  "4rDSbAQdn6dJ29msrFm8iGhMGC/bzq9Bii38Qg4y4o89QYiboRWCxv3XfuibT+jw\n" +
  "O3pmfsFuT8/bKOWVm94FmRxiKuj6iE8UVewxtByzDgAsBtJKDjaCv3IkqfbIu+sq\n" +
  "/eeJkVJRJXAP3ZpLAgMBAAGjcjBwMA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYE\n" +
  "FIxvPSwEmjOMW10H+gn2gy5HvMmMMAsGA1UdDwQEAwIBBjARBglghkgBhvhCAQEE\n" +
  "BAMCAAcwHgYJYIZIAYb4QgENBBEWD3hjYSBjZXJ0aWZpY2F0ZTANBgkqhkiG9w0B\n" +
  "AQsFAAOCAQEAWu0u72g5y1weexPoJQnUgcwVtuC+/tTS9YvyCtKYE91gn97LSWn9\n" +
  "mXXGmLceU27B8JwhER9JeiQO1SUdDcvlfb5vt6eB+5cbZcgeERUBP8t0znh7DbMg\n" +
  "4TFjt9gZ970PZ1OlTBNPoZNRBKIox61KVUhiVKTVSbXlVP1yUF1uSlSq+0NYayHw\n" +
  "MnX1BeLxbAcAsTPYHjoeFJIrGkKlydLyt/8hDQzpLRW5uEUTjjqLh7vef0OaOP80\n" +
  "MmADt6ojRYvwdMDHF0ASJyupLQ+hiRLVadciK8Z5W34JGN2jwEw5X3nXyAgErIJZ\n" +
  "pqdTflnFLnSwy5M3QHB+xjYAcS9l1br2LA==\n" +
  "-----END CERTIFICATE-----\n";

// 证书二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certGetIssuerX500DistinguishedName() {
  let x509Cert: cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    x509Cert.getIssuerX500DistinguishedName();
    console.info('getIssuerX500DistinguishedName result: success.');
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('createX509Cert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## getItem

```TypeScript
getItem(itemType: CertItemType): DataBlob
```

表示获取X.509证书对应的字段。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getItem(itemType: CertItemType): DataBlob--><!--Device-X509Cert-getItem(itemType: CertItemType): DataBlob-End-->

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
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

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

function TestGetItem() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let tbs = x509Cert.getItem(cert.CertItemType.CERT_ITEM_TYPE_TBS);
          console.info('tbs = ' + tbs.data);
          let pubKey = x509Cert.getItem(cert.CertItemType.CERT_ITEM_TYPE_PUBLIC_KEY);
          console.info('pubKey = ' + pubKey.data);
          console.info('getItem result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getItem failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getKeyUsage

```TypeScript
getKeyUsage(): DataBlob
```

表示获取X.509证书密钥用途。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getKeyUsage(): DataBlob--><!--Device-X509Cert-getKeyUsage(): DataBlob-End-->

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

function TestGetKeyUsage() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let keyUsage = x509Cert.getKeyUsage();
          console.info('keyUsage = ' + keyUsage.data);
          console.info('getKeyUsage result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getKeyUsage failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getNotAfterTime

```TypeScript
getNotAfterTime(): string
```

表示获取X.509证书过期时间。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getNotAfterTime(): string--><!--Device-X509Cert-getNotAfterTime(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示X.509证书过期时间，日期采用ASN.1 UTCTime或GeneralizedTime格式。 |

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

function TestGetNotAfterTime() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let notAfter = x509Cert.getNotAfterTime();
          console.info('notAfter = ' + notAfter);
          console.info('getNotAfterTime result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getNotAfterTime failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getNotBeforeTime

```TypeScript
getNotBeforeTime(): string
```

表示获取X.509证书生效时间。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getNotBeforeTime(): string--><!--Device-X509Cert-getNotBeforeTime(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示X.509证书生效时间，日期采用ASN.1 UTCTime或GeneralizedTime格式。 |

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

function TestGetNotBeforeTime() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let notBefore = x509Cert.getNotBeforeTime();
          console.info('notBefore = ' + notBefore);
          console.info('getNotBeforeTime result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getNotBeforeTime failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getPublicKey

```TypeScript
getPublicKey(): cryptoFramework.PubKey
```

表示获取X.509证书公钥。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getPublicKey(): cryptoFramework.PubKey--><!--Device-X509Cert-getPublicKey(): cryptoFramework.PubKey-End-->

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
function TestGetPublicKey() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          x509Cert.getPublicKey();
          console.info('getPublicKey result: success.');
        } catch (error) {
          let e: BusinessError = error as BusinessError;
          console.error('getPublicKey failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getSerialNumber

```TypeScript
getSerialNumber(): number
```

表示获取X.509证书序列号。 > **说明：** > > 从API version 9开始支持，从API version 10开始废弃，建议使用 > [X509Cert.getCertSerialNumber()](#getcertserialnumber)替代。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [getCertSerialNumber](#getcertserialnumber)

<!--Device-X509Cert-getSerialNumber(): number--><!--Device-X509Cert-getSerialNumber(): number-End-->

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

## getSignature

```TypeScript
getSignature(): DataBlob
```

表示获取X.509证书签名数据。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getSignature(): DataBlob--><!--Device-X509Cert-getSignature(): DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示X.509证书签名数据。 |

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

function TestGetSignature() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let signature = x509Cert.getSignature();
          console.info('signature = ' + signature.data);
          console.info('getSignature result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getSignature failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getSignatureAlgName

```TypeScript
getSignatureAlgName(): string
```

表示获取X.509证书签名算法名称。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getSignatureAlgName(): string--><!--Device-X509Cert-getSignatureAlgName(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示X.509证书签名算法名称。 |

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

function TestGetSignatureAlgName() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let sigAlgName = x509Cert.getSignatureAlgName();
          console.info('sigAlgName = ' + sigAlgName);
          console.info('getSignatureAlgName result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getSignatureAlgName failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getSignatureAlgOid

```TypeScript
getSignatureAlgOid(): string
```

表示获取X.509证书签名算法的对象标识符（OID）。OID由国际标准化组织（ISO）分配。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getSignatureAlgOid(): string--><!--Device-X509Cert-getSignatureAlgOid(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示签名算法OID。当长度超过127字节时会被截断。 |

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

function TestGetSignatureAlgOid() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let sigAlgOid = x509Cert.getSignatureAlgOid();
          console.info('sigAlgOid = ' + sigAlgOid);
          console.info('getSignatureAlgOid result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getSignatureAlgOid failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getSignatureAlgParams

```TypeScript
getSignatureAlgParams(): DataBlob
```

表示获取X.509证书签名算法参数。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getSignatureAlgParams(): DataBlob--><!--Device-X509Cert-getSignatureAlgParams(): DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示X.509证书签名算法参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

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

function TestGetSignatureAlgParams() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let sigAlgParams = x509Cert.getSignatureAlgParams();
          console.info('sigAlgParams = ' + sigAlgParams.data);
          console.info('getSignatureAlgParams result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getSignatureAlgParams failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getSubjectAltNames

```TypeScript
getSubjectAltNames(): DataArray
```

表示获取X.509证书主体可选名称。 > **说明：** > > 获取到的X.509证书主体可选名称数据带字符串结束符。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getSubjectAltNames(): DataArray--><!--Device-X509Cert-getSubjectAltNames(): DataArray-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | 表示X.509证书主体可选名称。 |

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

function TestGetSubjectAltNames() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let subjectAltNames = x509Cert.getSubjectAltNames();
          console.info('subjectAltNames = ' + subjectAltNames.data);
          console.info('getSubjectAltNames result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getSubjectAltNames failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getSubjectName

```TypeScript
getSubjectName(encodingType?: EncodingType): DataBlob
```

表示获取X.509证书主体名称。 > **说明：** > > - 若不设置encodingType参数，获取的证书主体名称末尾包含一个NUL终止符（值为0），请根据业务需求决定是否去除该终止符。 > - 若不设置encodingType参数，获取的证书主体名称为ASCII编码，转换为字符串后，是以斜杠（/）开始，以斜杠（/）分隔相对可分辨名称的 > 可分辨名称字符串。 > - 建议设置encodingType参数为EncodingType.ENCODING_UTF8，获取的证书主体名称是以逗号（,）分隔相对可分辨名称的可分辨名称字符串。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getSubjectName(encodingType?: EncodingType): DataBlob--><!--Device-X509Cert-getSubjectName(encodingType?: EncodingType): DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encodingType | [EncodingType](arkts-devicecertificate-cert-encodingtype-e.md) | 否 | 表示编码类型。设置该参数时，获取UTF-8格式的主体名称； 不设置时，默认获取ASCII编码格式的主体名称。<br>该参数从API version 12开始可用。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 表示X.509证书主体名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Incorrect parameter types; <br>2. Parameter verification failed.<br>**适用版本：** 12+ |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

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

function TestGetSubjectName() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        try {
          let subjectName = x509Cert.getSubjectName();
          console.info('subjectName = ' + subjectName.data);
          console.info('getSubjectName result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getSubjectName failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
        try {
          let subjectNameutf8 = x509Cert.getSubjectName(cert.EncodingType.ENCODING_UTF8);
          console.info('subjectNameutf8 = ' + subjectNameutf8.data);
          console.info('getSubjectName result: success.');
        } catch (err) {
          let e: BusinessError = err as BusinessError;
          console.error('getSubjectNameUtf8 failed, errCode: ' + e.code + ', errMsg: ' + e.message);
        }
      }
    }
  });
}
```

## getSubjectX500DistinguishedName

```TypeScript
getSubjectX500DistinguishedName(): X500DistinguishedName
```

获取X.509证书主体的X.500可分辨名称。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getSubjectX500DistinguishedName(): X500DistinguishedName--><!--Device-X509Cert-getSubjectX500DistinguishedName(): X500DistinguishedName-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md) | X.500可分辨对象。 |

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

let certData = "-----BEGIN CERTIFICATE-----\n" +
  "MIID1TCCAr2gAwIBAgIITXr1++kFUU4wDQYJKoZIhvcNAQELBQAwcDELMAkGA1UE\n" +
  "BhMCQ04xEjAQBgNVBAgTCWd1YW5nZG9uZzERMA8GA1UEBxMIc2hlbnpoZW4xEjAQ\n" +
  "BgNVBAoTCXRlc3RTZWNDYTESMBAGA1UECxMJdGVzdFNlY0NhMRIwEAYDVQQDEwl0\n" +
  "ZXN0U2VjQ2EwHhcNMjMxMjIxMDAwMDAwWhcNMjcxMjIwMjM1OTU5WjBxMQswCQYD\n" +
  "VQQGEwJDTjEOMAwGA1UECBMFZ2Fuc3UxEDAOBgNVBAcTB2xhbnpob3UxFDASBgNV\n" +
  "BAoTC3Rlc3RUaGlyZENhMRQwEgYDVQQLEwt0ZXN0VGhpcmRDYTEUMBIGA1UEAxML\n" +
  "dGVzdFRoaXJkQ2EwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDJMKSq\n" +
  "Fn4G4EJATauw+4s+n/JbINBAiuhzURzzdt2T8JJQLDV9RHj4mZt84yv6lqEpl2fm\n" +
  "gIClfu173pEV51/PSq5IaV481u/Dz/OTy9TwfxmIXAWdNpyodDOg4I9K7LC01ge8\n" +
  "xxyKFi7k7m2eTGA4dYQM0E0AEXzCpg2JN3IIIPhzHCIVJmYjcbVxiaFkvT4ZFFUk\n" +
  "4rDSbAQdn6dJ29msrFm8iGhMGC/bzq9Bii38Qg4y4o89QYiboRWCxv3XfuibT+jw\n" +
  "O3pmfsFuT8/bKOWVm94FmRxiKuj6iE8UVewxtByzDgAsBtJKDjaCv3IkqfbIu+sq\n" +
  "/eeJkVJRJXAP3ZpLAgMBAAGjcjBwMA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYE\n" +
  "FIxvPSwEmjOMW10H+gn2gy5HvMmMMAsGA1UdDwQEAwIBBjARBglghkgBhvhCAQEE\n" +
  "BAMCAAcwHgYJYIZIAYb4QgENBBEWD3hjYSBjZXJ0aWZpY2F0ZTANBgkqhkiG9w0B\n" +
  "AQsFAAOCAQEAWu0u72g5y1weexPoJQnUgcwVtuC+/tTS9YvyCtKYE91gn97LSWn9\n" +
  "mXXGmLceU27B8JwhER9JeiQO1SUdDcvlfb5vt6eB+5cbZcgeERUBP8t0znh7DbMg\n" +
  "4TFjt9gZ970PZ1OlTBNPoZNRBKIox61KVUhiVKTVSbXlVP1yUF1uSlSq+0NYayHw\n" +
  "MnX1BeLxbAcAsTPYHjoeFJIrGkKlydLyt/8hDQzpLRW5uEUTjjqLh7vef0OaOP80\n" +
  "MmADt6ojRYvwdMDHF0ASJyupLQ+hiRLVadciK8Z5W34JGN2jwEw5X3nXyAgErIJZ\n" +
  "pqdTflnFLnSwy5M3QHB+xjYAcS9l1br2LA==\n" +
  "-----END CERTIFICATE-----\n";

// 证书二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certGetSubjectX500DistinguishedName() {
  let x509Cert: cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    x509Cert.getSubjectX500DistinguishedName();
    console.info('getSubjectX500DistinguishedName result: success.');
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('createX509Cert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## getVersion

```TypeScript
getVersion(): int
```

表示获取X.509证书版本号。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-getVersion(): int--><!--Device-X509Cert-getVersion(): int-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 表示X.509证书版本号。 |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

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

function TestGetVersion() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');
      if (x509Cert != undefined) {
        let version = x509Cert.getVersion();
        console.info('version = ' + version);
        console.info('getVersion result: success.');
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

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-hashCode(): Uint8Array--><!--Device-X509Cert-hashCode(): Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | DER格式数据的哈希值。 |

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

let certData = "-----BEGIN CERTIFICATE-----\n" +
  "MIID1TCCAr2gAwIBAgIITXr1++kFUU4wDQYJKoZIhvcNAQELBQAwcDELMAkGA1UE\n" +
  "BhMCQ04xEjAQBgNVBAgTCWd1YW5nZG9uZzERMA8GA1UEBxMIc2hlbnpoZW4xEjAQ\n" +
  "BgNVBAoTCXRlc3RTZWNDYTESMBAGA1UECxMJdGVzdFNlY0NhMRIwEAYDVQQDEwl0\n" +
  "ZXN0U2VjQ2EwHhcNMjMxMjIxMDAwMDAwWhcNMjcxMjIwMjM1OTU5WjBxMQswCQYD\n" +
  "VQQGEwJDTjEOMAwGA1UECBMFZ2Fuc3UxEDAOBgNVBAcTB2xhbnpob3UxFDASBgNV\n" +
  "BAoTC3Rlc3RUaGlyZENhMRQwEgYDVQQLEwt0ZXN0VGhpcmRDYTEUMBIGA1UEAxML\n" +
  "dGVzdFRoaXJkQ2EwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDJMKSq\n" +
  "Fn4G4EJATauw+4s+n/JbINBAiuhzURzzdt2T8JJQLDV9RHj4mZt84yv6lqEpl2fm\n" +
  "gIClfu173pEV51/PSq5IaV481u/Dz/OTy9TwfxmIXAWdNpyodDOg4I9K7LC01ge8\n" +
  "xxyKFi7k7m2eTGA4dYQM0E0AEXzCpg2JN3IIIPhzHCIVJmYjcbVxiaFkvT4ZFFUk\n" +
  "4rDSbAQdn6dJ29msrFm8iGhMGC/bzq9Bii38Qg4y4o89QYiboRWCxv3XfuibT+jw\n" +
  "O3pmfsFuT8/bKOWVm94FmRxiKuj6iE8UVewxtByzDgAsBtJKDjaCv3IkqfbIu+sq\n" +
  "/eeJkVJRJXAP3ZpLAgMBAAGjcjBwMA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYE\n" +
  "FIxvPSwEmjOMW10H+gn2gy5HvMmMMAsGA1UdDwQEAwIBBjARBglghkgBhvhCAQEE\n" +
  "BAMCAAcwHgYJYIZIAYb4QgENBBEWD3hjYSBjZXJ0aWZpY2F0ZTANBgkqhkiG9w0B\n" +
  "AQsFAAOCAQEAWu0u72g5y1weexPoJQnUgcwVtuC+/tTS9YvyCtKYE91gn97LSWn9\n" +
  "mXXGmLceU27B8JwhER9JeiQO1SUdDcvlfb5vt6eB+5cbZcgeERUBP8t0znh7DbMg\n" +
  "4TFjt9gZ970PZ1OlTBNPoZNRBKIox61KVUhiVKTVSbXlVP1yUF1uSlSq+0NYayHw\n" +
  "MnX1BeLxbAcAsTPYHjoeFJIrGkKlydLyt/8hDQzpLRW5uEUTjjqLh7vef0OaOP80\n" +
  "MmADt6ojRYvwdMDHF0ASJyupLQ+hiRLVadciK8Z5W34JGN2jwEw5X3nXyAgErIJZ\n" +
  "pqdTflnFLnSwy5M3QHB+xjYAcS9l1br2LA==\n" +
  "-----END CERTIFICATE-----\n";

// 证书二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certHashCode() {
  let x509Cert: cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    console.info('certHashCode success: ' + x509Cert.hashCode());
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('createX509Cert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## match

```TypeScript
match(param: X509CertMatchParameters): boolean
```

判断证书是否与输入参数匹配。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-match(param: X509CertMatchParameters): boolean--><!--Device-X509Cert-match(param: X509CertMatchParameters): boolean-End-->

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

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

async function createX509Cert(): Promise<cert.X509Cert | undefined> {
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

  let x509Cert: cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('createX509Cert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
    return undefined;
  }
  return x509Cert;
}

async function matchX509Cert() {
  const x509Cert = await createX509Cert();
  if (x509Cert != undefined) {
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
}
```

## toString

```TypeScript
toString(): string
```

获取对象的字符串类型数据。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-toString(): string--><!--Device-X509Cert-toString(): string-End-->

**系统能力：** SystemCapability.Security.Cert

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 对象的字符串类型数据。 |

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

let certData = "-----BEGIN CERTIFICATE-----\n" +
  "MIID1TCCAr2gAwIBAgIITXr1++kFUU4wDQYJKoZIhvcNAQELBQAwcDELMAkGA1UE\n" +
  "BhMCQ04xEjAQBgNVBAgTCWd1YW5nZG9uZzERMA8GA1UEBxMIc2hlbnpoZW4xEjAQ\n" +
  "BgNVBAoTCXRlc3RTZWNDYTESMBAGA1UECxMJdGVzdFNlY0NhMRIwEAYDVQQDEwl0\n" +
  "ZXN0U2VjQ2EwHhcNMjMxMjIxMDAwMDAwWhcNMjcxMjIwMjM1OTU5WjBxMQswCQYD\n" +
  "VQQGEwJDTjEOMAwGA1UECBMFZ2Fuc3UxEDAOBgNVBAcTB2xhbnpob3UxFDASBgNV\n" +
  "BAoTC3Rlc3RUaGlyZENhMRQwEgYDVQQLEwt0ZXN0VGhpcmRDYTEUMBIGA1UEAxML\n" +
  "dGVzdFRoaXJkQ2EwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDJMKSq\n" +
  "Fn4G4EJATauw+4s+n/JbINBAiuhzURzzdt2T8JJQLDV9RHj4mZt84yv6lqEpl2fm\n" +
  "gIClfu173pEV51/PSq5IaV481u/Dz/OTy9TwfxmIXAWdNpyodDOg4I9K7LC01ge8\n" +
  "xxyKFi7k7m2eTGA4dYQM0E0AEXzCpg2JN3IIIPhzHCIVJmYjcbVxiaFkvT4ZFFUk\n" +
  "4rDSbAQdn6dJ29msrFm8iGhMGC/bzq9Bii38Qg4y4o89QYiboRWCxv3XfuibT+jw\n" +
  "O3pmfsFuT8/bKOWVm94FmRxiKuj6iE8UVewxtByzDgAsBtJKDjaCv3IkqfbIu+sq\n" +
  "/eeJkVJRJXAP3ZpLAgMBAAGjcjBwMA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYE\n" +
  "FIxvPSwEmjOMW10H+gn2gy5HvMmMMAsGA1UdDwQEAwIBBjARBglghkgBhvhCAQEE\n" +
  "BAMCAAcwHgYJYIZIAYb4QgENBBEWD3hjYSBjZXJ0aWZpY2F0ZTANBgkqhkiG9w0B\n" +
  "AQsFAAOCAQEAWu0u72g5y1weexPoJQnUgcwVtuC+/tTS9YvyCtKYE91gn97LSWn9\n" +
  "mXXGmLceU27B8JwhER9JeiQO1SUdDcvlfb5vt6eB+5cbZcgeERUBP8t0znh7DbMg\n" +
  "4TFjt9gZ970PZ1OlTBNPoZNRBKIox61KVUhiVKTVSbXlVP1yUF1uSlSq+0NYayHw\n" +
  "MnX1BeLxbAcAsTPYHjoeFJIrGkKlydLyt/8hDQzpLRW5uEUTjjqLh7vef0OaOP80\n" +
  "MmADt6ojRYvwdMDHF0ASJyupLQ+hiRLVadciK8Z5W34JGN2jwEw5X3nXyAgErIJZ\n" +
  "pqdTflnFLnSwy5M3QHB+xjYAcS9l1br2LA==\n" +
  "-----END CERTIFICATE-----\n";

// 证书二进制数据，需业务自行赋值。
let encodingBlob: cert.EncodingBlob = {
  data: stringToUint8Array(certData),
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

async function certToString() {
  let x509Cert: cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    console.info('certToString success: ' + x509Cert.toString());
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('createX509Cert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## toString

```TypeScript
toString(encodingType: EncodingType): string
```

根据编码类型获取对象的字符串类型数据。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-toString(encodingType: EncodingType): string--><!--Device-X509Cert-toString(encodingType: EncodingType): string-End-->

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
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes: <br>1. Memory copy failed; <br>2. A null pointer occurs inside the system; <br>3. Failed to obtain the native object or convert parameters. |
| [19020003](../errorcode-cert.md#19020003-参数检查失败) | Parameter check failed. Possible causes: <br>1. The value of encodingType is not in the EncodingType enumeration range. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

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
  let x509Cert: cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    console.info('certToString success: ' + x509Cert.toString(cert.EncodingType.ENCODING_UTF8));
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error('createX509Cert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

## verify

```TypeScript
verify(key: cryptoFramework.PubKey, callback: AsyncCallback<void>): void
```

表示对证书验签。使用Callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-verify(key: cryptoFramework.PubKey, callback: AsyncCallback<void>): void--><!--Device-X509Cert-verify(key: cryptoFramework.PubKey, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | cryptoFramework.PubKey | 是 | 用于验签的公钥对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当验签成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

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
function TestVerify() {
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
      console.error('createX509Cert failed, errCode: ' + error.code + ', errMsg: ' + error.message);
    } else {
      console.info('createX509Cert result: success.');

      // 业务需通过上级X509Cert证书对象（或当前证书对象为自签名的证书）的getPublicKey获取PubKey。
      try {
        if (x509Cert != undefined) {
          let pubKey = x509Cert.getPublicKey();

          // 验证证书签名。
          x509Cert.verify(pubKey, (err, _data) => {
            if (err) {
              console.error('verify failed, errCode: ' + err.code + ', errMsg: ' + err.message);
            } else {
              console.info('verify result: success.');
            }
          });
        }
      } catch (error) {
        let e: BusinessError = error as BusinessError;
        console.error('getPublicKey failed, errCode: ' + e.code + ', errMsg: ' + e.message);
      }
    }
  });
}
```

## verify

```TypeScript
verify(key: cryptoFramework.PubKey): Promise<void>
```

表示对证书验签。使用Promise方式返回结果。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509Cert-verify(key: cryptoFramework.PubKey): Promise<void>--><!--Device-X509Cert-verify(key: cryptoFramework.PubKey): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | cryptoFramework.PubKey | 是 | 用于验签的公钥对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

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
async function TestVerify() {
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
  try {
    let x509Cert = await cert.createX509Cert(encodingBlob);
    console.info('createX509Cert result: success.');
    try {
      // 业务需通过上级X509Cert证书对象（或当前证书对象为自签名的证书）的getPublicKey获取PubKey。
      let pubKey = x509Cert.getPublicKey();
      await x509Cert.verify(pubKey);
      console.info('verify result: success.');
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`verify failed, ${e.code}, ${e.message}`);
    }
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createX509Cert failed, ${e.code}, ${e.message}`);
  }
}
```

