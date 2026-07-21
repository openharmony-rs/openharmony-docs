# CertChainValidator

证书链校验器对象。

**起始版本：** 9

<!--Device-cert-interface CertChainValidator--><!--Device-cert-interface CertChainValidator-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

<a id="validate"></a>
## validate

```TypeScript
validate(certChain: CertChainData, callback: AsyncCallback<void>): void
```

表示校验X509证书链。使用Callback异步回调。

由于端侧系统时间不可信，证书链校验不包含对证书有效时间的校验。如果需要检查证书的时间有效性，可使用X509证书的[checkValidityWithDate](arkts-devicecertificate-cert-x509cert-i.md#checkvaliditywithdate)方法进行检查。详见[证书规格](../../../security/DeviceCertificateKit/certificate-framework-overview.md#证书规格)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidator-validate(certChain: CertChainData, callback: AsyncCallback<void>): void--><!--Device-CertChainValidator-validate(certChain: CertChainData, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| certChain | [CertChainData](arkts-devicecertificate-cert-certchaindata-i.md) | 是 | 表示X509证书链序列化数据。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当校验成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |
| [19030002](../errorcode-cert.md#19030002-证书签名验证错误) | 证书签名验证错误。 |
| [19030003](../errorcode-cert.md#19030003-证书尚未生效) | 证书尚未生效。 |
| [19030004](../errorcode-cert.md#19030004-证书过期) | 证书过期。 |
| [19030005](../errorcode-cert.md#19030005-无法获取证书的颁发者) | 无法获取证书的颁发者。 |
| [19030006](../errorcode-cert.md#19030006-证书的密钥用途不含证书签名) | 证书的密钥用途不含证书签名。 |
| [19030007](../errorcode-cert.md#19030007-证书的密钥用途不含数字签名) | 证书的密钥用途不含数字签名。 |

**示例：**

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

// 证书链二进制数据。
let certPem = '-----BEGIN CERTIFICATE-----\n' +
  'MIIDTjCCAjagAwIBAgIBBDANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDQwMVoXDTM0MDMxNzAyMDQwMVowEjEQMA4GA1UEAwwH\n' +
  'ZGV2aWNlMjCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAMIXL3e7UE/c\n' +
  'Z1dPVgRZ5L8gsQ/azuYVBvoFf7o8ksYrL7G1+qZIJjVRqZkuTirLW4GicbkIkPNW\n' +
  'eix5cDhkjkC+q5SBCOrSSTTlvX3xcOY1gMlA5MgeBfGixFusq4d5VPF2KceZ20/a\n' +
  'ygwGD0Uv0X81OERyPom/dYdJUvfaD9ifPFJ1fKIj/cPFG3yJK/ojpEfndZNdESQL\n' +
  'TkoDekilg2UGOLtY6fb9Ns37ncuIj33gCS/R9m1tgtmqCTcgOQ4hwKhjVF3InmPO\n' +
  '2BbWKvD1RUX+rHC2a2HHDQILOOtDTy8dHvE+qZlK0efrpRgoFEERJAGPi1GDGWiA\n' +
  '7UX1c4MCxIECAwEAAaOBrjCBqzAJBgNVHRMEAjAAMB0GA1UdDgQWBBQbkAcMT7ND\n' +
  'fGp3VPFzYHppZ1zxLTAfBgNVHSMEGDAWgBR0W/koCbvDtFGHUQZLM3j6HKsW2DAd\n' +
  'BgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwCwYDVR0PBAQDAgeAMDIGCCsG\n' +
  'AQUFBwEBBCYwJDAiBggrBgEFBQcwAYYWaHR0cHM6Ly8xMjcuMC4wLjE6OTk5OTAN\n' +
  'BgkqhkiG9w0BAQsFAAOCAQEAF1OTzTmbklFOdZCxrF3zg9owUPJR5RB+PbuBlUfI\n' +
  '8tkGXkMltQ8PN1dv6Cq+d8BluiJdWEzqVoJa/e5SHHJyYQSOhlurRG0GBXllVQ1I\n' +
  'n1PFaI40+9X2X6wrEcdC5nbzogR1jSiksCiTcARMddj0Xrp5FMrFaaGY8M/xqzdW\n' +
  'LTDl4nfbuxtA71cIjnE4kOcaemly9/S2wYWdPktsPxQPY1nPUOeJFI7o0sH3rK0c\n' +
  'JSqtgAG8vnjK+jbx9RpkgqCsXgUbIahL573VTgxrNrsRjCuVal7XVxl/xOKXr6Er\n' +
  'Gpc+OCrXbHNZkUQE5fZH3yL2tXd7EASEb6J3aEWHfF8YBA==\n' +
  '-----END CERTIFICATE-----';

let caPem = '-----BEGIN CERTIFICATE-----\n' +
  'MIIC/zCCAeegAwIBAgIBATANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDIyNFoXDTM0MDMxNzAyMDIyNFowEjEQMA4GA1UEAwwH\n' +
  'Um9vdCBDQTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALxI5SDvRfKU\n' +
  '6XaTeyh2LHlUK0rVSeYfXkYf5Mc3Pgucg+ewzQjxkACMx5NYaW1zfGDNPG1i5IZl\n' +
  'cPeWNz1Tm2g6wTd+LyNoNOOmwfLV8pLXSfAukgNrBREf3BzVrbu7hvPd2MmLH23H\n' +
  'OBM9uDPTIqu3n2CDN2EzwULjaSk2g+jvhVKsDLInu5uKPmZBFhs1FWKgcnVnlbi1\n' +
  'AyAx4efheits6EO70oV6UufCEtS1VsBXQHZRAG4ogshWldRBVNxkU6yHAfg0mM/5\n' +
  'EhrZsfh51fWqlrhNWrInjgNV3xIt5ebTIgKZWUlSVHEA/UqDoGfY+CsAJdteZWOW\n' +
  'KjsrC/DK2O0CAwEAAaNgMF4wHQYDVR0OBBYEFHRb+SgJu8O0UYdRBkszePocqxbY\n' +
  'MB8GA1UdIwQYMBaAFHRb+SgJu8O0UYdRBkszePocqxbYMA8GA1UdEwEB/wQFMAMB\n' +
  'Af8wCwYDVR0PBAQDAgEGMA0GCSqGSIb3DQEBCwUAA4IBAQAKOT1ObfQNMN2wdfHq\n' +
  'PQgFDDp6rBMbZe70LswPirSXljo4S/vfbG+gBoWCdu/SfsV+lyP75kg1wX0IQvzW\n' +
  'xYNh864dgqPmGd0v8TIfM0UT0PpnowUyBHQ+E7LNYIOh/kjHbl3oERdEFA2PUyE9\n' +
  'j3GLdg8oe/LqhEQCSAlH+v2RQgBZ9eVN+mSdUxwywm9U3acb0uqVkGiWK/ywumpg\n' +
  'AmIZLMJtMVvg8uDkfy16Z4lChTEdNaJVUqPczUNk2kHXIF4we4be9HoOuTVz/SD/\n' +
  'IsOhXn/BjS3jnhyS9fxo+opJf9zVTWI02Hlh1WVVtH/m3nIZblyAJhcjCHA2wZSz\n' +
  'sSus\n' +
  '-----END CERTIFICATE-----';

let certPemData = stringToUint8Array(certPem);
let caPemData = stringToUint8Array(caPem);

let certPemDataLenData = new Uint8Array(new Uint16Array([certPemData.length]).buffer)
let caPemDataLenData = new Uint8Array(new Uint16Array([caPemData.length]).buffer)

let certChainBuff =
  new Uint8Array(certPemDataLenData.length + certPemData.length + caPemDataLenData.length + caPemData.length)
certChainBuff.set(certPemDataLenData)
certChainBuff.set(certPemData, certPemDataLenData.length)
certChainBuff.set(caPemDataLenData, certPemDataLenData.length + certPemData.length)
certChainBuff.set(caPemData, certPemDataLenData.length + certPemData.length + caPemDataLenData.length)

let certChainData: cert.CertChainData = {
  data: certChainBuff,
  // 证书链包含的证书个数，需业务自行赋值。
  count: 2,
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

try {
  let validator = cert.createCertChainValidator('PKIX');
  validator.validate(certChainData, (error, data) => {
    if (error) {
      console.error(`validate failed, errCode: ${error.code}, errMsg: ${error.message}`);
    } else {
      console.info('validate result: success.');
    }
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`validate failed, errCode: ${e.code}, errMsg: ${e.message}`);
}

```

<a id="validate-1"></a>
## validate

```TypeScript
validate(certChain: CertChainData): Promise<void>
```

表示校验X509证书链。使用Promise方式返回结果。

由于端侧系统时间不可信，证书链校验不包含对证书有效时间的校验。如果需要检查证书的时间有效性，可使用X509证书的[checkValidityWithDate](arkts-devicecertificate-cert-x509cert-i.md#checkvaliditywithdate)方法进行检查。详见[证书规格](../../../security/DeviceCertificateKit/certificate-framework-overview.md#证书规格)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidator-validate(certChain: CertChainData): Promise<void>--><!--Device-CertChainValidator-validate(certChain: CertChainData): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| certChain | [CertChainData](arkts-devicecertificate-cert-certchaindata-i.md) | 是 | 表示X509证书链序列化数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数校验失败。 |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |
| [19030002](../errorcode-cert.md#19030002-证书签名验证错误) | 证书签名验证错误。 |
| [19030003](../errorcode-cert.md#19030003-证书尚未生效) | 证书尚未生效。 |
| [19030004](../errorcode-cert.md#19030004-证书过期) | 证书过期。 |
| [19030005](../errorcode-cert.md#19030005-无法获取证书的颁发者) | 无法获取证书的颁发者。 |
| [19030006](../errorcode-cert.md#19030006-证书的密钥用途不含证书签名) | 证书的密钥用途不含证书签名。 |
| [19030007](../errorcode-cert.md#19030007-证书的密钥用途不含数字签名) | 证书的密钥用途不含数字签名。 |

**示例：**

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

// 证书链数据。
let certPem = '-----BEGIN CERTIFICATE-----\n' +
  'MIIDTjCCAjagAwIBAgIBBDANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDQwMVoXDTM0MDMxNzAyMDQwMVowEjEQMA4GA1UEAwwH\n' +
  'ZGV2aWNlMjCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAMIXL3e7UE/c\n' +
  'Z1dPVgRZ5L8gsQ/azuYVBvoFf7o8ksYrL7G1+qZIJjVRqZkuTirLW4GicbkIkPNW\n' +
  'eix5cDhkjkC+q5SBCOrSSTTlvX3xcOY1gMlA5MgeBfGixFusq4d5VPF2KceZ20/a\n' +
  'ygwGD0Uv0X81OERyPom/dYdJUvfaD9ifPFJ1fKIj/cPFG3yJK/ojpEfndZNdESQL\n' +
  'TkoDekilg2UGOLtY6fb9Ns37ncuIj33gCS/R9m1tgtmqCTcgOQ4hwKhjVF3InmPO\n' +
  '2BbWKvD1RUX+rHC2a2HHDQILOOtDTy8dHvE+qZlK0efrpRgoFEERJAGPi1GDGWiA\n' +
  '7UX1c4MCxIECAwEAAaOBrjCBqzAJBgNVHRMEAjAAMB0GA1UdDgQWBBQbkAcMT7ND\n' +
  'fGp3VPFzYHppZ1zxLTAfBgNVHSMEGDAWgBR0W/koCbvDtFGHUQZLM3j6HKsW2DAd\n' +
  'BgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwCwYDVR0PBAQDAgeAMDIGCCsG\n' +
  'AQUFBwEBBCYwJDAiBggrBgEFBQcwAYYWaHR0cHM6Ly8xMjcuMC4wLjE6OTk5OTAN\n' +
  'BgkqhkiG9w0BAQsFAAOCAQEAF1OTzTmbklFOdZCxrF3zg9owUPJR5RB+PbuBlUfI\n' +
  '8tkGXkMltQ8PN1dv6Cq+d8BluiJdWEzqVoJa/e5SHHJyYQSOhlurRG0GBXllVQ1I\n' +
  'n1PFaI40+9X2X6wrEcdC5nbzogR1jSiksCiTcARMddj0Xrp5FMrFaaGY8M/xqzdW\n' +
  'LTDl4nfbuxtA71cIjnE4kOcaemly9/S2wYWdPktsPxQPY1nPUOeJFI7o0sH3rK0c\n' +
  'JSqtgAG8vnjK+jbx9RpkgqCsXgUbIahL573VTgxrNrsRjCuVal7XVxl/xOKXr6Er\n' +
  'Gpc+OCrXbHNZkUQE5fZH3yL2tXd7EASEb6J3aEWHfF8YBA==\n' +
  '-----END CERTIFICATE-----';

let caPem = '-----BEGIN CERTIFICATE-----\n' +
  'MIIC/zCCAeegAwIBAgIBATANBgkqhkiG9w0BAQsFADASMRAwDgYDVQQDDAdSb290\n' +
  'IENBMB4XDTI0MDMxOTAyMDIyNFoXDTM0MDMxNzAyMDIyNFowEjEQMA4GA1UEAwwH\n' +
  'Um9vdCBDQTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALxI5SDvRfKU\n' +
  '6XaTeyh2LHlUK0rVSeYfXkYf5Mc3Pgucg+ewzQjxkACMx5NYaW1zfGDNPG1i5IZl\n' +
  'cPeWNz1Tm2g6wTd+LyNoNOOmwfLV8pLXSfAukgNrBREf3BzVrbu7hvPd2MmLH23H\n' +
  'OBM9uDPTIqu3n2CDN2EzwULjaSk2g+jvhVKsDLInu5uKPmZBFhs1FWKgcnVnlbi1\n' +
  'AyAx4efheits6EO70oV6UufCEtS1VsBXQHZRAG4ogshWldRBVNxkU6yHAfg0mM/5\n' +
  'EhrZsfh51fWqlrhNWrInjgNV3xIt5ebTIgKZWUlSVHEA/UqDoGfY+CsAJdteZWOW\n' +
  'KjsrC/DK2O0CAwEAAaNgMF4wHQYDVR0OBBYEFHRb+SgJu8O0UYdRBkszePocqxbY\n' +
  'MB8GA1UdIwQYMBaAFHRb+SgJu8O0UYdRBkszePocqxbYMA8GA1UdEwEB/wQFMAMB\n' +
  'Af8wCwYDVR0PBAQDAgEGMA0GCSqGSIb3DQEBCwUAA4IBAQAKOT1ObfQNMN2wdfHq\n' +
  'PQgFDDp6rBMbZe70LswPirSXljo4S/vfbG+gBoWCdu/SfsV+lyP75kg1wX0IQvzW\n' +
  'xYNh864dgqPmGd0v8TIfM0UT0PpnowUyBHQ+E7LNYIOh/kjHbl3oERdEFA2PUyE9\n' +
  'j3GLdg8oe/LqhEQCSAlH+v2RQgBZ9eVN+mSdUxwywm9U3acb0uqVkGiWK/ywumpg\n' +
  'AmIZLMJtMVvg8uDkfy16Z4lChTEdNaJVUqPczUNk2kHXIF4we4be9HoOuTVz/SD/\n' +
  'IsOhXn/BjS3jnhyS9fxo+opJf9zVTWI02Hlh1WVVtH/m3nIZblyAJhcjCHA2wZSz\n' +
  'sSus\n' +
  '-----END CERTIFICATE-----';

let certPemData = stringToUint8Array(certPem);
let caPemData = stringToUint8Array(caPem);

let certPemDataLenData = new Uint8Array(new Uint16Array([certPemData.length]).buffer)
let caPemDataLenData = new Uint8Array(new Uint16Array([caPemData.length]).buffer)

let certChainBuff =
  new Uint8Array(certPemDataLenData.length + certPemData.length + caPemDataLenData.length + caPemData.length)
certChainBuff.set(certPemDataLenData)
certChainBuff.set(certPemData, certPemDataLenData.length)
certChainBuff.set(caPemDataLenData, certPemDataLenData.length + certPemData.length)
certChainBuff.set(caPemData, certPemDataLenData.length + certPemData.length + caPemDataLenData.length)

let certChainData: cert.CertChainData = {
  data: certChainBuff,
  // 证书链包含的证书个数，需业务自行赋值。
  count: 2,
  // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_PEM
};

try {
  let validator = cert.createCertChainValidator('PKIX');
  validator.validate(certChainData).then(result => {
    console.info('validate result: success.');
  }).catch((error: BusinessError) => {
    console.error(`validate failed, errCode: ${error.code}, errMsg: ${error.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`validate failed, errCode: ${e.code}, errMsg: ${e.message}`);
}

```

<a id="validatecert"></a>
## validateCert

```TypeScript
validateCert(cert: X509Cert, params: CertValidationParams): Promise<CertValidationResult>
```

通过构建和验证证书链来验证证书。该接口使用Promise返回结果。

证书链构建过程遵循以下规则：1. 信任锚来源：始终以信任证书列表（trustedCerts）作为信任锚源。仅当trustSystemCa设置为true时，才使用预配置证书作为信任锚源。2. 颁发者搜索顺序：系统首先从信任锚来源中搜索颁发者，若未找到，则继续在非信任证书列表（untrustedCerts）中查找。在线下载的中间CA证书属于非受信任证书。3. 信任锚锁定：一旦在信任锚来源中找到颁发者，后续查找过程将不会再回至非信任证书，即后续证书必须来自信任锚来源。4. 构建完成条件：若partialChain为false（默认值），则仅在找到根证书（自签名证书）时构建完成。若partialChain为true，则在首次在信任锚来源中找到颁发者时构建完成。5. 后续验证：证书链构建完成后，执行其他验证操作，如证书签名验证和证书吊销检查。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidator-validateCert(cert: X509Cert, params: CertValidationParams): Promise<CertValidationResult>--><!--Device-CertChainValidator-validateCert(cert: X509Cert, params: CertValidationParams): Promise<CertValidationResult>-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cert | [X509Cert](arkts-devicecertificate-cert-x509cert-i.md) | 是 | 待验证的证书。 |
| params | [CertValidationParams](arkts-devicecertificate-cert-certvalidationparams-i.md) | 是 | 证书验证参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CertValidationResult&gt; | Promise对象，返回验证结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19020001](../errorcode-cert.md#19020001-内存错误) | 内存错误。 |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | 运行时外部错误。可能的原因：<br>1. 内存拷贝失败；<br>2. 系统内部出现空指针；<br>3. 获取Native对象失败或参数转换失败。 |
| [19020003](../errorcode-cert.md#19020003-参数检查失败) | 参数检查失败。 |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | 调用三方算法库API出错。 |
| [19030002](../errorcode-cert.md#19030002-证书签名验证错误) | 证书签名验证错误。 |
| [19030003](../errorcode-cert.md#19030003-证书尚未生效) | 证书尚未生效。 |
| [19030004](../errorcode-cert.md#19030004-证书过期) | 证书过期。 |
| [19030005](../errorcode-cert.md#19030005-无法获取证书的颁发者) | 无法获取证书的颁发者。 |
| [19030006](../errorcode-cert.md#19030006-证书的密钥用途不含证书签名) | 证书的密钥用途不含证书签名。 |
| [19030007](../errorcode-cert.md#19030007-证书的密钥用途不含数字签名) | 证书的密钥用途不含数字签名。 |
| [19030009](../errorcode-cert.md#19030009-证书不受信任) | 证书不受信任。 |
| [19030010](../errorcode-cert.md#19030010-证书已被吊销) | 证书已被吊销。 |
| [19030011](../errorcode-cert.md#19030011-未知的关键扩展) | 未知的关键扩展。 |
| [19030012](../errorcode-cert.md#19030012-主机名不匹配) | 证书主机名不匹配。 |
| [19030013](../errorcode-cert.md#19030013-邮箱地址不匹配) | 证书邮箱地址不匹配。 |
| [19030014](../errorcode-cert.md#19030014-密钥用途不匹配) | 证书密钥用途不匹配。 |
| [19030015](../errorcode-cert.md#19030015-无法获取证书吊销列表) | 无法获取证书吊销列表。 |
| [19030016](../errorcode-cert.md#19030016-证书吊销列表尚未生效) | 证书吊销列表尚未生效。 |
| [19030017](../errorcode-cert.md#19030017-证书吊销列表已过期) | 证书吊销列表已过期。 |
| [19030018](../errorcode-cert.md#19030018-证书吊销列表签名验证失败) | 证书吊销列表签名验证失败。 |
| [19030019](../errorcode-cert.md#19030019-无法获取证书吊销列表颁发者) | 无法获取证书吊销列表颁发者。 |
| [19030020](../errorcode-cert.md#19030020-无法获取在线证书状态协议ocsp响应) | 无法获取在线证书状态协议（OCSP）响应。 |
| [19030021](../errorcode-cert.md#19030021-无效的ocsp响应) | OCSP响应无效。 |
| [19030022](../errorcode-cert.md#19030022-ocsp签名验证失败) | OCSP签名验证失败。 |
| [19030023](../errorcode-cert.md#19030023-ocsp证书状态未知) | OCSP证书状态未知。 |
| [19030024](../errorcode-cert.md#19030024-网络连接超时) | 网络连接超时。 |

**示例：**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// EC P-256证书链数据
const endEntityCertPem = '-----BEGIN CERTIFICATE-----\n' +
    'MIICwzCCAmmgAwIBAgIUIThWddD/8p7w5QyXOoRY05O61FMwCgYIKoZIzj0EAwIw\n' +
    'gYsxCzAJBgNVBAYTAkNOMRAwDgYDVQQIDAdCZWlqaW5nMRAwDgYDVQQHDAdCZWlq\n' +
    'aW5nMRowGAYDVQQKDBFUZXN0IE9yZ2FuaXphdGlvbjEdMBsGA1UECwwUVGVzdCBJ\n' +
    'bnRlcm1lZGlhdGUgQ0ExHTAbBgNVBAMMFFRlc3QgSW50ZXJtZWRpYXRlIENBMB4X\n' +
    'DTI2MDMzMTA4MjY1OFoXDTI3MDMzMTA4MjY1OFowgYIxCzAJBgNVBAYTAkNOMRAw\n' +
    'DgYDVQQIDAdCZWlqaW5nMRAwDgYDVQQHDAdCZWlqaW5nMRowGAYDVQQKDBFUZXN0\n' +
    'IE9yZ2FuaXphdGlvbjEYMBYGA1UECwwPVGVzdCBEZXBhcnRtZW50MRkwFwYDVQQD\n' +
    'DBB0ZXN0LmV4YW1wbGUuY29tMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEspH8\n' +
    'JVcqNrg7oP4PYHADsW8tc1kIF86JG5SSjh1fz4ja3dF98PMMrsbQtcBZiwp8rD5e\n' +
    'Gp2Nv/C2ymnjJfrig6OBsTCBrjAJBgNVHRMEAjAAMA4GA1UdDwEB/wQEAwIFoDAd\n' +
    'BgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwHQYDVR0OBBYEFH6aJ7ZQayEZ\n' +
    'LeenLt7zowBoafRpMB8GA1UdIwQYMBaAFI2lMRV2YgzF/DBP92jUzOLdzSDdMDIG\n' +
    'A1UdEQQrMCmCEHRlc3QuZXhhbXBsZS5jb22CD3d3dy5leGFtcGxlLmNvbYcEfwAA\n' +
    'ATAKBggqhkjOPQQDAgNIADBFAiEAidnsForpQc9qTBpa68YEYS0TQRUySHaUB/pr\n' +
    'PNfAYqECIGGKM44mqQgSvZyYQHnlnu3jkbHpFJTaQBAvz9B1jFuc\n' +
    '-----END CERTIFICATE-----\n';

const intermediateCaPem = '-----BEGIN CERTIFICATE-----\n' +
    'MIICbzCCAhWgAwIBAgIUI8/xor2S98OupuBX6hWevxhvK+wwCgYIKoZIzj0EAwIw\n' +
    'ezELMAkGA1UEBhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0JlaWpp\n' +
    'bmcxGjAYBgNVBAoMEVRlc3QgT3JnYW5pemF0aW9uMRUwEwYDVQQLDAxUZXN0IFJv\n' +
    'b3QgQ0ExFTATBgNVBAMMDFRlc3QgUm9vdCBDQTAeFw0yNjAzMzEwODI2NThaFw0z\n' +
    'MTAzMzAwODI2NThaMIGLMQswCQYDVQQGEwJDTjEQMA4GA1UECAwHQmVpamluZzEQ\n' +
    'MA4GA1UEBwwHQmVpamluZzEaMBgGA1UECgwRVGVzdCBPcmdhbml6YXRpb24xHTAb\n' +
    'BgNVBAsMFFRlc3QgSW50ZXJtZWRpYXRlIENBMR0wGwYDVQQDDBRUZXN0IEludGVy\n' +
    'bWVkaWF0ZSBDQTBZMBMGByqGSM49AgEGCCqGSM49AwEHA0IABER6WRsCn7Bh3v8c\n' +
    'k6PIkLeM+ot5l0A46XJdfvuJco58ifzBHjtu4kFOkZTA9F0Hb6JefG590CK5ddiD\n' +
    'g5lOHwKjZjBkMBIGA1UdEwEB/wQIMAYBAf8CAQAwDgYDVR0PAQH/BAQDAgEGMB0G\n' +
    'A1UdDgQWBBSNpTEVdmIMxfwwT/do1Mzi3c0g3TAfBgNVHSMEGDAWgBS/nd4dYdW3\n' +
    'zFxQ1pl2U8I/bfUA3zAKBggqhkjOPQQDAgNIADBFAiEA87NkGCv47e5RWc8DsFd/\n' +
    'zL6/2Xn2EoveC+HoUYpxhZMCIAG+ZuTLmUsjalUGbWyR101hxHfvr4ImbEMeYSaA\n' +
    'sVBn\n' +
    '-----END CERTIFICATE-----\n';

const rootCaPem = '-----BEGIN CERTIFICATE-----\n' +
    'MIICWzCCAgGgAwIBAgIUd/I1bFJJw/xQtPEJP6C1E4Fj9jswCgYIKoZIzj0EAwIw\n' +
    'ezELMAkGA1UEBhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0JlaWpp\n' +
    'bmcxGjAYBgNVBAoMEVRlc3QgT3JnYW5pemF0aW9uMRUwEwYDVQQLDAxUZXN0IFJv\n' +
    'b3QgQ0ExFTATBgNVBAMMDFRlc3QgUm9vdCBDQTAeFw0yNjAzMzEwODI2NTdaFw0z\n' +
    'NjAzMjgwODI2NTdaMHsxCzAJBgNVBAYTAkNOMRAwDgYDVQQIDAdCZWlqaW5nMRAw\n' +
    'DgYDVQQHDAdCZWlqaW5nMRowGAYDVQQKDBFUZXN0IE9yZ2FuaXphdGlvbjEVMBMG\n' +
    'A1UECwwMVGVzdCBSb290IENBMRUwEwYDVQQDDAxUZXN0IFJvb3QgQ0EwWTATBgcq\n' +
    'hkjOPQIBBggqhkjOPQMBBwNCAASFeWawqQET+c6EowNooKYiTw1KPzJBgssxQXo7\n' +
    'UEXSQnLHh8sBwVvNN4oFVFImT31DyJVKwxBXpwbrEN1s8J1Io2MwYTAPBgNVHRMB\n' +
    'Af8EBTADAQH/MA4GA1UdDwEB/wQEAwIBBjAdBgNVHQ4EFgQUv53eHWHVt8xcUNaZ\n' +
    'dlPCP231AN8wHwYDVR0jBBgwFoAUv53eHWHVt8xcUNaZdlPCP231AN8wCgYIKoZI\n' +
    'zj0EAwIDSAAwRQIhAIbyIrOZL1GhkRiI2i4IhKmFa4AoXJftTEA5wev99QpkAiA3\n' +
    'khFrJ4rRSpHqbfGN1U14HkFKiCXBalaIe+NISxgC3Q==\n' +
    '-----END CERTIFICATE-----\n';

// string转Uint8Array
function stringToUint8Array(str: string): Uint8Array {
  let arr: Array<number> = [];
  for (let i = 0, j = str.length; i < j; i++) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

async function validateCert(): Promise<void> {
  try {
    // 创建终端实体证书对象
    let certEncodingBlob: cert.EncodingBlob = {
      data: stringToUint8Array(endEntityCertPem),
      encodingFormat: cert.EncodingFormat.FORMAT_PEM
    };
    let x509Cert = await cert.createX509Cert(certEncodingBlob);

    // 创建信任锚证书（根CA）
    let rootCaEncodingBlob: cert.EncodingBlob = {
      data: stringToUint8Array(rootCaPem),
      encodingFormat: cert.EncodingFormat.FORMAT_PEM
    };
    let rootCaCert = await cert.createX509Cert(rootCaEncodingBlob);

    // 创建中间证书
    let intermediateCaEncodingBlob: cert.EncodingBlob = {
      data: stringToUint8Array(intermediateCaPem),
      encodingFormat: cert.EncodingFormat.FORMAT_PEM
    };
    let intermediateCaCert = await cert.createX509Cert(intermediateCaEncodingBlob);

    // 设置验证参数
    let params: cert.CertValidationParams = {
      trustedCerts: [rootCaCert],
      untrustedCerts: [intermediateCaCert],
      validateDate: false
    };

    // 创建验证器并验证证书
    let validator = cert.createCertChainValidator('PKIX');
    let result = await validator.validateCert(x509Cert, params);

    console.info('Certificate validation succeeded!');
    console.info(`Verified chain length: ${result.certChain.length}`);
    for (let i = 0; i < result.certChain.length; i++) {
      let subject = result.certChain[i].getSubjectX500DistinguishedName().getName(cert.EncodingType.ENCODING_UTF8);
      console.info(`Cert ${i}: ${subject}`);
    }
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`validate failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

validateCert();

```

## algorithm

```TypeScript
readonly algorithm: string
```

X509证书链校验器算法名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainValidator-readonly algorithm: string--><!--Device-CertChainValidator-readonly algorithm: string-End-->

**系统能力：** SystemCapability.Security.Cert

