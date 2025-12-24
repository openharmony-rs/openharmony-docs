# 证书链在线校验证书吊销状态

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

## 本地证书链吊销状态校验时仅校验终端实体证书

API 22开始支持本地证书链吊销状态校验时仅校验终端实体证书。

### 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```
2. 调用[cert.createCertChain](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509certchain11)创建证书链对象。

3. 调用[cert.createX509Cert](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509cert)创建X509证书对象。

4. 调用[cert.createX509CRL](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509crl11)创建X509证书吊销列表对象。

5. 构造[cert.CertChainValidationParameters](../../reference/apis-device-certificate-kit/js-apis-cert.md#certchainvalidationparameters11)证书链校验参数对象。

6. 调用[cert.validate](../../reference/apis-device-certificate-kit/js-apis-cert.md#validate11)，传入证书链校验参数，进行证书链校验。

本地仅校验终端实体证书的吊销状态示例：

<!-- @[create-only-check-leaf-cert-revocate-object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateOnlyCheckLeafCertRevocateObject.ets) -->

```ts
import { cert } from '@kit.DeviceCertificateKit';

// string转Uint8Array。
function stringToUint8Array(str: string): Uint8Array {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; i++) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

async function createCertChain(certData: string): Promise<cert.X509CertChain> {
  // 证书二进制数据，需业务自行赋值。
  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(certData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  let X509CertChain: cert.X509CertChain = {} as cert.X509CertChain;
  try {
    X509CertChain = await cert.createX509CertChain(encodingBlob);
  } catch (err) {
    console.error(`createCertChain failed: errCode: ${err.code}, message: ${err.message}`);
  }
  return X509CertChain;
}
async function createCert(certData: string): Promise<cert.X509Cert> {
  // 证书二进制数据，需业务自行赋值。
  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(certData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
  } catch (err) {
    console.error(`createCert failed: errCode: ${err.code}, message: ${err.message}`);
  }
  return x509Cert;
}
export async function createCRL(crmPem: string): Promise<cert.CertCRLCollection> {
  try {
    let crlEncodingBlob: cert.EncodingBlob = {
      data: stringToUint8Array(crmPem),
      encodingFormat: cert.EncodingFormat.FORMAT_PEM
    }
    let crl: cert.X509CRL = await cert.createX509CRL(crlEncodingBlob);
    let collection: cert.CertCRLCollection = cert.createCertCRLCollection([], [crl]);
    return collection;
  } catch (error) {
    throw error as Error;
  }
}

let certChainData =
  "-----BEGIN CERTIFICATE-----\n"                                      +
  "MIIC8TCCAlqgAwIBAgIUIUvzWX3AOgQ/QjNel1SBhBtTPBAwDQYJKoZIhvcNAQEL\n" +
  "BQAwdDELMAkGA1UEBhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0Jl\n" +
  "aWppbmcxGTAXBgNVBAoMEEludGVybWVkaWF0ZTIgQ0ExCzAJBgNVBAsMAklUMRkw\n" +
  "FwYDVQQDDBBJbnRlcm1lZGlhdGUyIENBMB4XDTI1MDkyNDEwMDIzNVoXDTMwMTAx\n" +
  "ODEwMDIzNVowbzELMAkGA1UEBhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNV\n" +
  "BAcMB0JlaWppbmcxFTATBgNVBAoMDEV4YW1wbGUgQ29ycDELMAkGA1UECwwCSVQx\n" +
  "GDAWBgNVBAMMD3d3dy5leGFtcGxlLmNvbTCBnzANBgkqhkiG9w0BAQEFAAOBjQAw\n" +
  "gYkCgYEA4vc1u69q13LMHCvChJDgIpdhXA+ctn9khXD4/lpsaYS5CAnKZzAK74Ip\n" +
  "/i0WcIwYwuVEpggko0DDplioCnYjU/OEtn0Opxt1f4mn17HvUfeNZDN0X3neF43J\n" +
  "F5axTNvIJDuHdiLWoWUMK0JtffSUMQ7Fx3MWyAWahDB9NsltkpMCAwEAAaOBhDCB\n" +
  "gTAJBgNVHRMEAjAAMAsGA1UdDwQEAwIEMDAnBgNVHREEIDAegg93d3cuZXhhbXBs\n" +
  "ZS5jb22CC2V4YW1wbGUuY29tMB0GA1UdDgQWBBSmwesDcCVKq1s+rzKxsCW08As0\n" +
  "rzAfBgNVHSMEGDAWgBRI56SWC90zDEsVlYS5LPemujOebzANBgkqhkiG9w0BAQsF\n" +
  "AAOBgQAhHhPjX5P1PEexyez0eW7DCAo03fxRBhcNjSBBCmiFWeOXvsvZgnDXv/Ky\n" +
  "5tR88MQ0HX2FAl9n0jo3qdvrMfo1EaT+fp1/PKmoE7y0WJD5JkMsKrKvR/5Gaspm\n" +
  "KwlxMhYyu7ET8A022NYLx885eBnWI6OOcnqYXnGeCnWWgNiXug==\n"             +
  "-----END CERTIFICATE-----\n"                                        +
  "-----BEGIN CERTIFICATE-----\n"                                      +
  "MIICvDCCAiWgAwIBAgIUECXHZotH6yK5LTTdPFMkY9kZka0wDQYJKoZIhvcNAQEL\n" +
  "BQAwYjELMAkGA1UEBhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0Jl\n" +
  "aWppbmcxEDAOBgNVBAoMB1Jvb3QgQ0ExCzAJBgNVBAsMAklUMRAwDgYDVQQDDAdS\n" +
  "b290IENBMB4XDTI1MDkyNDEwMDA0NFoXDTMwMDkyMzEwMDA0NFowdDELMAkGA1UE\n" +
  "BhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0JlaWppbmcxGTAXBgNV\n" +
  "BAoMEEludGVybWVkaWF0ZTIgQ0ExCzAJBgNVBAsMAklUMRkwFwYDVQQDDBBJbnRl\n" +
  "cm1lZGlhdGUyIENBMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQC94fbVrcDy\n" +
  "59VyR7/s3D27BPgnod1JzhzDF1QbOQ2N3ZMGBjpxbPtJ7wICK/bRFBNvUwXqJZba\n" +
  "zBER7y1VGZssrDpAW1CcVlAteyVb0ia2kr7sYRmTpUv5sl3nrZIVCy5SqeBVt19L\n" +
  "3UYz/ppHOfFoLLyoXYA/Ix3AlzPJWnCmnwIDAQABo10wWzAMBgNVHRMEBTADAQH/\n" +
  "MAsGA1UdDwQEAwIBBjAdBgNVHQ4EFgQUSOeklgvdMwxLFZWEuSz3proznm8wHwYD\n" +
  "VR0jBBgwFoAUB1FwqNTM5mqxu5ZbsbayDFf57OAwDQYJKoZIhvcNAQELBQADgYEA\n" +
  "dQJjyNHJkf7LlucyWJigmE24BasJDm0Il9pfsvNF7ZzlbUNjrEFnXLXG/ZwRavp/\n" +
  "j5M54cBLOQL02DU0f+YqcPaUmhNqrFq7EVa5VVKZgdQ8f7rOdJVrDhGugfg8zkQo\n" +
  "lbRUUGJ4JVlIR7ntr0WmG0frmZ+/V/t57sxRKNvGq8M=\n"                     +
  "-----END CERTIFICATE-----\n"                                        +
  "-----BEGIN CERTIFICATE-----\n"                                      +
  "MIICwzCCAiygAwIBAgIUFHmiDZ6lR+Z3+u80U1r9f1CViV0wDQYJKoZIhvcNAQEL\n" +
  "BQAwYjELMAkGA1UEBhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0Jl\n" +
  "aWppbmcxEDAOBgNVBAoMB1Jvb3QgQ0ExCzAJBgNVBAsMAklUMRAwDgYDVQQDDAdS\n" +
  "b290IENBMB4XDTI1MDkyNDA5NDgyN1oXDTM1MDkyMjA5NDgyN1owYjELMAkGA1UE\n" +
  "BhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0JlaWppbmcxEDAOBgNV\n" +
  "BAoMB1Jvb3QgQ0ExCzAJBgNVBAsMAklUMRAwDgYDVQQDDAdSb290IENBMIGfMA0G\n" +
  "CSqGSIb3DQEBAQUAA4GNADCBiQKBgQDIKZ7fGE1Z+SqdfywoEl9NqQLOiLiHumzD\n" +
  "JDY1ZWApQpX9098Z2PmvPV6oh84UFEc2nv+yKG1kid2qh9jcm0zNaV2q0AA3t0d8\n" +
  "WTzjbs4HG4kdcUk5FtLhMVEBTUR0/ii38Y4tJXNmaarGyNbyB85GNqXTpxn9mkBp\n" +
  "cAEGa4A7BwIDAQABo3YwdDAdBgNVHQ4EFgQUB1FwqNTM5mqxu5ZbsbayDFf57OAw\n" +
  "HwYDVR0jBBgwFoAUB1FwqNTM5mqxu5ZbsbayDFf57OAwCwYDVR0PBAQDAgEGMAkG\n" +
  "A1UdEQQCMAAwCQYDVR0SBAIwADAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3DQEB\n" +
  "CwUAA4GBAEwSMp+Zo4hMxmPp9VmKuvC5ElJCisdghrJxhb6KWVza9temcnAEkshZ\n" +
  "IRqW4mnstsY5YSuIhPF/oinVCVB7ViRPEb8ZnzxE3Bbka0/ShhE5wjBn75NcCbtD\n" +
  "WZvp+1vl8LlmRwRe2kr5JvcPw5IpGRq1tunznRpg+/3eEpI+KT3E\n"             +
  "-----END CERTIFICATE-----";
let trustRootCertPem =
  "-----BEGIN CERTIFICATE-----\n"                                      +
  "MIICwzCCAiygAwIBAgIUFHmiDZ6lR+Z3+u80U1r9f1CViV0wDQYJKoZIhvcNAQEL\n" +
  "BQAwYjELMAkGA1UEBhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0Jl\n" +
  "aWppbmcxEDAOBgNVBAoMB1Jvb3QgQ0ExCzAJBgNVBAsMAklUMRAwDgYDVQQDDAdS\n" +
  "b290IENBMB4XDTI1MDkyNDA5NDgyN1oXDTM1MDkyMjA5NDgyN1owYjELMAkGA1UE\n" +
  "BhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0JlaWppbmcxEDAOBgNV\n" +
  "BAoMB1Jvb3QgQ0ExCzAJBgNVBAsMAklUMRAwDgYDVQQDDAdSb290IENBMIGfMA0G\n" +
  "CSqGSIb3DQEBAQUAA4GNADCBiQKBgQDIKZ7fGE1Z+SqdfywoEl9NqQLOiLiHumzD\n" +
  "JDY1ZWApQpX9098Z2PmvPV6oh84UFEc2nv+yKG1kid2qh9jcm0zNaV2q0AA3t0d8\n" +
  "WTzjbs4HG4kdcUk5FtLhMVEBTUR0/ii38Y4tJXNmaarGyNbyB85GNqXTpxn9mkBp\n" +
  "cAEGa4A7BwIDAQABo3YwdDAdBgNVHQ4EFgQUB1FwqNTM5mqxu5ZbsbayDFf57OAw\n" +
  "HwYDVR0jBBgwFoAUB1FwqNTM5mqxu5ZbsbayDFf57OAwCwYDVR0PBAQDAgEGMAkG\n" +
  "A1UdEQQCMAAwCQYDVR0SBAIwADAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3DQEB\n" +
  "CwUAA4GBAEwSMp+Zo4hMxmPp9VmKuvC5ElJCisdghrJxhb6KWVza9temcnAEkshZ\n" +
  "IRqW4mnstsY5YSuIhPF/oinVCVB7ViRPEb8ZnzxE3Bbka0/ShhE5wjBn75NcCbtD\n" +
  "WZvp+1vl8LlmRwRe2kr5JvcPw5IpGRq1tunznRpg+/3eEpI+KT3E\n"             +
  "-----END CERTIFICATE-----";
let crl =
  "-----BEGIN X509 CRL-----\n"                                         +
  "MIIBYzCBzQIBATANBgkqhkiG9w0BAQsFADBiMQswCQYDVQQGEwJDTjEQMA4GA1UE\n" +
  "CAwHQmVpamluZzEQMA4GA1UEBwwHQmVpamluZzEQMA4GA1UECgwHUm9vdCBDQTEL\n" +
  "MAkGA1UECwwCSVQxEDAOBgNVBAMMB1Jvb3QgQ0EXDTI1MDkyNDEwMjYxMVoXDTM1\n" +
  "MDkyMjEwMjYxMVowJzAlAhQQJcdmi0frIrktNN08UyRj2RmRrRcNMjUwOTI0MTAy\n" +
  "NTUxWqAOMAwwCgYDVR0UBAMCAQUwDQYJKoZIhvcNAQELBQADgYEAEGLDAa7xHu6U\n" +
  "SEUa7vDI9ZjxeQLJedqo3+j/ihMu1YBSP9yPXTUJ6MZcT8oMLLvYnjjV7Lp4jIq5\n" +
  "yBX3iW9+nrXfJKoHRkP9NMqUdk1jRBVNIG8xT+EYssa+lurN+wDjytI+BEA+kCJQ\n" +
  "4S4wrhhI4mBOBr53GbbsgZfEUhCrMoE=\n"                                 +
  "-----END X509 CRL-----";

async function doTestLeafCertCrlCheck() {
  try {
      let x509CertChain: cert.X509CertChain = await createCertChain(certChainData);
      let x509Cert: cert.X509Cert = await createCert(trustRootCertPem);
      let caCollection: cert.CertCRLCollection = await createCRL(crl);
      const param: cert.CertChainValidationParameters = {
      date: '20250926080000Z',
      trustAnchors: [{
          CACert: x509Cert
      }],
      certCRLs: [caCollection],
      revocationCheckParam: {
          options: [
          cert.RevocationCheckOptions.REVOCATION_CHECK_OPTION_LOCAL_CRL_ONLY_CHECK_END_ENTITY_CERT
          ],
      }
      };
      await x509CertChain.validate(param);
      console.info("validate result is success.");
  } catch (error) {
      console.error("x509CertChain validate failed error code is: " + error.code);
  }
}
```

## 在线校验证书链中的中间CA证书的吊销状态

从API 22开始，支持在线校验证书链中的中间CA证书的吊销状态。

### 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```
2. 调用[cert.createCertChain](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509certchain11)创建证书链对象。

3. 调用[cert.createX509Cert](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509cert)创建X509证书对象。

4. 构造[cert.CertChainValidationParameters](../../reference/apis-device-certificate-kit/js-apis-cert.md#certchainvalidationparameters11)证书链校验参数。

5. 调用[cert.validate](../../reference/apis-device-certificate-kit/js-apis-cert.md#validate11)，传入证书链校验参数，进行证书链校验。

> **说明**
>
> 本开发指导中提供的示例代码需要在配置网络的前提下执行。

在线校验中间证书的吊销状态示例：

<!-- @[create-online-check-intermediate-certificateonly-object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateOnlineCheckIntermediateCertificateonlyObject.ets) -->

``` TypeScript

import { cert } from '@kit.DeviceCertificateKit';

// string转Uint8Array。
function stringToUint8Array(str: string): Uint8Array {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; i++) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

async function createCertChain(certData: string): Promise<cert.X509CertChain> {
  // 证书二进制数据，需业务自行赋值。
  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(certData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  let x509CertChain: cert.X509CertChain = {} as cert.X509CertChain;
  try {
    x509CertChain = await cert.createX509CertChain(encodingBlob);
  } catch (err) {
    console.error(`createCertChain failed: errCode: ${err.code}, message: ${err.message}`);
  }
  return x509CertChain;
}

async function createCert(certData: string): Promise<cert.X509Cert> {
  // 证书二进制数据，需业务自行赋值。
  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(certData),
    // 根据encodingData的格式进行赋值，支持FORMAT_PEM和FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
  } catch (err) {
    console.error(`createCert failed: errCode: ${err.code}, message: ${err.message}`);
  }
  return x509Cert;
}

let caChain =
  '-----BEGIN CERTIFICATE-----\n' +
    'MIICezCCAiCgAwIBAgIUDczOyWG59LZLx2kP97vi5y0oL+QwCgYIKoZIzj0EAwIw\n' +
    'fjELMAkGA1UEBhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0JlaWpp\n' +
    'bmcxHjAcBgNVBAoMFUVDRFNBIEludGVybWVkaWF0ZSBDQTELMAkGA1UECwwCSVQx\n' +
    'HjAcBgNVBAMMFUVDRFNBIEludGVybWVkaWF0ZSBDQTAeFw0yNTEwMTUwNjI3MzVa\n' +
    'Fw0zMDExMDgwNjI3MzVaMHUxCzAJBgNVBAYTAkNOMRAwDgYDVQQIDAdCZWlqaW5n\n' +
    'MRAwDgYDVQQHDAdCZWlqaW5nMRswGQYDVQQKDBJFQ0RTQSBFeGFtcGxlIENvcnAx\n' +
    'CzAJBgNVBAsMAklUMRgwFgYDVQQDDA93d3cuZXhhbXBsZS5jb20wWTATBgcqhkjO\n' +
    'PQIBBggqhkjOPQMBBwNCAASLR4TL7GQxOngZONYxay8vb5QQ2pDdaFobU2YSUC4m\n' +
    'dYxTsTyujMkTgK9sv/Me3Nf1lDXUz8mUCwVLHJ33hx3Jo4GEMIGBMAkGA1UdEwQC\n' +
    'MAAwCwYDVR0PBAQDAgK0MCcGA1UdEQQgMB6CD3d3dy5leGFtcGxlLmNvbYILZXhh\n' +
    'bXBsZS5jb20wHQYDVR0OBBYEFOp+v71yBI53o1mcrxqLOcZi0BrUMB8GA1UdIwQY\n' +
    'MBaAFDhFnzDg8Ap9glv7qyl8ajigm0OsMAoGCCqGSM49BAMCA0kAMEYCIQDIK8lp\n' +
    'z7+PNk6MxW45Lht9pUj/eAZfHW/692ZeJW1dfAIhAI1f3GEzkTihWd6h139gPXcS\n' +
    'y+Sf6/kfJnN0I3v/O2vI\n' +
    '-----END CERTIFICATE-----\n' +
    '-----BEGIN CERTIFICATE-----\n' +
    'MIIEZjCCBAygAwIBAgIMTT/sw52uhI5Hi8tcMAoGCCqGSM49BAMCMFAxCzAJBgNV\n' +
    'BAYTAkJFMRkwFwYDVQQKDBBHbG9iYWxTaWduIG52LXNhMSYwJAYDVQQDDB1HbG9i\n' +
    'YWxTaWduIEVDQyBPViBTU0wgQ0EgMjAxODAeFw0yNTEwMTUwNjIwMzhaFw0yNTEx\n' +
    'MTQwNjIwMzhaMH4xCzAJBgNVBAYTAkNOMRAwDgYDVQQIDAdCZWlqaW5nMRAwDgYD\n' +
    'VQQHDAdCZWlqaW5nMR4wHAYDVQQKDBVFQ0RTQSBJbnRlcm1lZGlhdGUgQ0ExCzAJ\n' +
    'BgNVBAsMAklUMR4wHAYDVQQDDBVFQ0RTQSBJbnRlcm1lZGlhdGUgQ0EwWTATBgcq\n' +
    'hkjOPQIBBggqhkjOPQMBBwNCAARsa530tupy2vzI0ljPlGdO/QRMnXOv0R7cuQ8P\n' +
    'sTnaaqCBXrHZxrwoISe1c3+eq4CnJZBImvZSTSUUW9DfV31Co4ICnDCCApgwDAYD\n' +
    'VR0TBAUwAwEB/zAOBgNVHQ8BAf8EBAMCAe4wNQYDVR0lAQH/BCswKQYIKwYBBQUH\n' +
    'AwIGCCsGAQUFBwMBBggrBgEFBQcDAwYJKoZIhvcNAQkQMD8GA1UdHwQ4MDYwNKAy\n' +
    'oDCGLmh0dHA6Ly9jcmwuZ2xvYmFsc2lnbi5jb20vZ3NlY2NvdnNzbGNhMjAxOC5j\n' +
    'cmwwggGIBggrBgEFBQcBAQSCAXowggF2MIG4BggrBgEFBQcwAoaBq2h0dHBzOi8v\n' +
    'Z2l0Y29kZS5jb20vbTBfNzI2MTA3NzUvY29tcGF0aWJpbGl0eS9ibG9iL21hc3Rl\n' +
    'ci90ZXN0X3N1aXRlL3Jlc291cmNlL21hc3Rlci9zdGFuZGFyZCUyMHN5c3RlbS9h\n' +
    'Y3RzL3Jlc291cmNlL3NlY3VyaXR5L2NlcnRpZmljYXRlX2ZyYW1ld29yay8yMDI1\n' +
    'MDgxODE3ODgzNC9yb290LmNydDCBuAYIKwYBBQUHMAGGgatodHRwczovL2dpdGNv\n' +
    'ZGUuY29tL20wXzcyNjEwNzc1L2NvbXBhdGliaWxpdHkvYmxvYi9tYXN0ZXIvdGVz\n' +
    'dF9zdWl0ZS9yZXNvdXJjZS9tYXN0ZXIvc3RhbmRhcmQlMjBzeXN0ZW0vYWN0cy9y\n' +
    'ZXNvdXJjZS9zZWN1cml0eS9jZXJ0aWZpY2F0ZV9mcmFtZXdvcmsvMjAyNTA4MTgx\n' +
    'Nzg4MzQvcm9vdE9jc3AwNAYDVR0RBC0wK4IJbG9jYWxob3N0hwR/AAABhwTAqAEB\n' +
    'hhJodHRwOi8vMTkyLjE2OC4wLjIwHQYDVR0OBBYEFDhFnzDg8Ap9glv7qyl8ajig\n' +
    'm0OsMB8GA1UdIwQYMBaAFEYc/aft0QonL8U0/qNsvq3lrA9bMAoGCCqGSM49BAMC\n' +
    'A0gAMEUCIFsgnFqsgzPfzRtxLLqsh1tEQeW6xqp875XqpICR6FO7AiEAnJTGezte\n' +
    'A3uK46isQ2HwlmgwmXTNwgSP1JyWr5t6cVA=\n' +
    '-----END CERTIFICATE-----\n' +
    '-----BEGIN CERTIFICATE-----\n' +
    'MIICGTCCAb6gAwIBAgIULcoKoYK2AQviXl1rlu+m7TH/J5UwCgYIKoZIzj0EAwMw\n' +
    'UDELMAkGA1UEBhMCQkUxGTAXBgNVBAoMEEdsb2JhbFNpZ24gbnYtc2ExJjAkBgNV\n' +
    'BAMMHUdsb2JhbFNpZ24gRUNDIE9WIFNTTCBDQSAyMDE4MB4XDTI1MTAxNTAzNTMw\n' +
    'OFoXDTM1MTAxMzAzNTMwOFowUDELMAkGA1UEBhMCQkUxGTAXBgNVBAoMEEdsb2Jh\n' +
    'bFNpZ24gbnYtc2ExJjAkBgNVBAMMHUdsb2JhbFNpZ24gRUNDIE9WIFNTTCBDQSAy\n' +
    'MDE4MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEJgdrEUKaVA8ZPzYD/kLwsn4c\n' +
    'UgkrCkTtMZEtG6l5iGTvpZT4qPTh8h5ILrui9bC+DLPRkEo3YsfHb62EanXqe6N2\n' +
    'MHQwHQYDVR0OBBYEFEYc/aft0QonL8U0/qNsvq3lrA9bMB8GA1UdIwQYMBaAFEYc\n' +
    '/aft0QonL8U0/qNsvq3lrA9bMAsGA1UdDwQEAwIBBjAJBgNVHREEAjAAMAkGA1Ud\n' +
    'EgQCMAAwDwYDVR0TAQH/BAUwAwEB/zAKBggqhkjOPQQDAwNJADBGAiEAz82HL4V2\n' +
    '3zTMVfJVMhHvSf2j+z7mUrRKCc0f21635DkCIQDqxlpMbRjs1bCL4pipCvD+w8v8\n' +
    'i4aEhDebPmxT8WuR7A==\n' +
    '-----END CERTIFICATE-----';
let caTrustCert =
  '-----BEGIN CERTIFICATE-----\n' +
    'MIICGTCCAb6gAwIBAgIULcoKoYK2AQviXl1rlu+m7TH/J5UwCgYIKoZIzj0EAwMw\n' +
    'UDELMAkGA1UEBhMCQkUxGTAXBgNVBAoMEEdsb2JhbFNpZ24gbnYtc2ExJjAkBgNV\n' +
    'BAMMHUdsb2JhbFNpZ24gRUNDIE9WIFNTTCBDQSAyMDE4MB4XDTI1MTAxNTAzNTMw\n' +
    'OFoXDTM1MTAxMzAzNTMwOFowUDELMAkGA1UEBhMCQkUxGTAXBgNVBAoMEEdsb2Jh\n' +
    'bFNpZ24gbnYtc2ExJjAkBgNVBAMMHUdsb2JhbFNpZ24gRUNDIE9WIFNTTCBDQSAy\n' +
    'MDE4MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEJgdrEUKaVA8ZPzYD/kLwsn4c\n' +
    'UgkrCkTtMZEtG6l5iGTvpZT4qPTh8h5ILrui9bC+DLPRkEo3YsfHb62EanXqe6N2\n' +
    'MHQwHQYDVR0OBBYEFEYc/aft0QonL8U0/qNsvq3lrA9bMB8GA1UdIwQYMBaAFEYc\n' +
    '/aft0QonL8U0/qNsvq3lrA9bMAsGA1UdDwQEAwIBBjAJBgNVHREEAjAAMAkGA1Ud\n' +
    'EgQCMAAwDwYDVR0TAQH/BAUwAwEB/zAKBggqhkjOPQQDAwNJADBGAiEAz82HL4V2\n' +
    '3zTMVfJVMhHvSf2j+z7mUrRKCc0f21635DkCIQDqxlpMbRjs1bCL4pipCvD+w8v8\n' +
    'i4aEhDebPmxT8WuR7A==\n' +
    '-----END CERTIFICATE-----';

async function doTestCaCheck() {
  try {
    let x509CertChain: cert.X509CertChain = await createCertChain(caChain);
    let x509Cert: cert.X509Cert = await createCert(caTrustCert);
    const param: cert.CertChainValidationParameters = {
      trustAnchors: [{
        CACert: x509Cert
      }],
      revocationCheckParam: {
        options: [
          cert.RevocationCheckOptions.REVOCATION_CHECK_OPTION_ACCESS_NETWORK,
          cert.RevocationCheckOptions.REVOCATION_CHECK_OPTION_CHECK_INTERMEDIATE_CA_ONLINE
        ],
      }
    };
    await x509CertChain.validate(param);
    console.info(`validate result is success.`);
  } catch (error) {
    console.error(`x509CertChain validate failed error code is: ` + error.code);
  }
}
```


## 证书链校验时忽略在线证书吊销检查的网络不可达异常

从API 23开始，支持证书链校验时忽略网络不可达的在线证书吊销检查异常。

### 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```
2. 调用[cert.createX509CertChain](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509certchain11-2)创建证书链对象。

3. 调用[cert.createX509Cert](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509cert)创建X509证书对象。构造 `cert.CertChainValidationParameters` 证书链校验参数，配置 `revocationCheckParam` 为 `RevocationCheckOptions.REVOCATION_CHECK_OPTION_IGNORE_NETWORK_ERROR`，以忽略网络不可达的情况。

4. 调用[cert.validate](../../reference/apis-device-certificate-kit/js-apis-cert.md#validate11)，传入证书链校验参数，进行证书链校验。

在线CRL检查忽略网络不可达异常示例：

<!-- @[ignore-network-unreachable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/IgnoreNetworkUnreachable.ets) -->

``` TypeScript

import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

// string转Uint8Array。
function stringToUint8Array(str: string): Uint8Array {
  const encoder = new util.TextEncoder();
  return encoder.encodeInto(str);
}
// ...
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
    console.error('createX509Cert failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
  return x509Cert;
}

async function createX509CertChain(): Promise<cert.X509CertChain> {
  const root = await createX509Cert(rootCert);
  const intermediate = await createX509Cert(intermediateCert);
  const leaf = await createX509Cert(leafCert);
  let x509CertChain: cert.X509CertChain = {} as cert.X509CertChain;
  try {
    x509CertChain = cert.createX509CertChain([leaf, intermediate, root]);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error('createX509CertChain failed, errCode: ' + e.code + ', errMsg: ' + e.message);
  }
  return x509CertChain;
}

async function validateCRL() {
  const certChain = await createX509CertChain();
  console.info('createX509CertChain success');
  const root = await createX509Cert(rootCert);
  // 证书链校验数据，需业务自行赋值。
  const param: cert.CertChainValidationParameters = {
    trustAnchors: [{ CACert: root }],
    revocationCheckParam: {
      options: [
        cert.RevocationCheckOptions.REVOCATION_CHECK_OPTION_IGNORE_NETWORK_ERROR,
        cert.RevocationCheckOptions.REVOCATION_CHECK_OPTION_ACCESS_NETWORK
      ],
    }
  }
  try {
    await certChain.validate(param);
    console.info('validateCRL success.');
  } catch (err) {
    console.error(`X509CertChain validate failed: errCode: ${err.code}, message: ${err.message}`);
  }
}
```
