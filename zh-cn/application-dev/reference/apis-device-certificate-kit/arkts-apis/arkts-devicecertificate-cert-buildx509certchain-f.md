# buildX509CertChain

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { certificateManager } from '@kit.DeviceCertificateKit';
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## buildX509CertChain

```TypeScript
function buildX509CertChain(param: CertChainBuildParameters): Promise<CertChainBuildResult>
```

表示使用CertChainBuildParameters对象方式创建X.509证书链对象。使用Promise方式返回结果。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-cert-function buildX509CertChain(param: CertChainBuildParameters): Promise<CertChainBuildResult>--><!--Device-cert-function buildX509CertChain(param: CertChainBuildParameters): Promise<CertChainBuildResult>-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [CertChainBuildParameters](arkts-devicecertificate-cert-certchainbuildparameters-i.md) | 是 | 构建证书链的参数对象。 <br> [CertChainBuildParameters](arkts-devicecertificate-cert-certchainbuildparameters-i.md)中的maxLength要小于证书集合中证书数量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CertChainBuildResult](arkts-devicecertificate-cert-certchainbuildresult-i.md)&gt; | Promise对象，返回创建的CertChainBuildResult实例。 |

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

async function createX509Cert(certData: string): Promise<cert.X509Cert> {
  // 证书二进制数据，需业务自行赋值。
  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(certData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX509Cert failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
  return x509Cert;
}

async function buildX509CertChain() {
  try {
    const caCert = await createX509Cert(caPem);
    const x509Cert = await createX509Cert(certPem);
    let certCrlCollection = cert.createCertCRLCollection([x509Cert]);
    let param: cert.CertChainBuildParameters = {
      certMatchParameters: { validDate: '20240812080000Z' },
      maxLength: 3,
      validationParameters: {
        date: '20240812080000Z',
        certCRLs: [certCrlCollection],
        trustAnchors: [{ CACert: caCert }, { CACert: caCert }]
      }
    };
    let certChainBuildResult = await cert.buildX509CertChain(param);
    console.info('cert issuer name: ' + certChainBuildResult.validationResult.entityCert.getIssuerName().data);
    console.info('ca subject name: ' + certChainBuildResult.validationResult.trustAnchor.CACert?.getSubjectName().data);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX509CertChain failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

buildX509CertChain();
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

async function createX509Cert(certData: string): Promise<cert.X509Cert | undefined> {
  // 证书二进制数据，需业务自行赋值。
  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(certData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  let x509Cert: cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX509Cert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
    return undefined;
  }
  return x509Cert;
}

async function buildX509CertChain() {
  try {
    const caCert = await createX509Cert(caPem);
    const x509Cert = await createX509Cert(certPem);
    if (caCert != undefined && x509Cert != undefined) {
      let certCrlCollection = cert.createCertCRLCollection([x509Cert]);
      let param: cert.CertChainBuildParameters = {
        certMatchParameters: {validDate:'20240812080000Z'},
        maxLength: 3,
        validationParameters: {
          date: '20240812080000Z',
          certCRLs: [certCrlCollection],
          trustAnchors: [{CACert:caCert}, {CACert:caCert}],
        }
      };
      let certChainBuildResult = await cert.buildX509CertChain(param);
      console.info("cert issuer name: " + certChainBuildResult.validationResult.entityCert.getIssuerName().data);
      console.info("ca subject name: " +
      certChainBuildResult.validationResult.trustAnchor.CACert?.getSubjectName().data);
    }
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX509CertChain failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
}
```

