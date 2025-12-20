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

let caChain =
"-----BEGIN CERTIFICATE-----\n" +
  "MIICezCCAiCgAwIBAgIUDczOyWG59LZLx2kP97vi5y0oL+QwCgYIKoZIzj0EAwIw\n" +
  "fjELMAkGA1UEBhMCQ04xEDAOBgNVBAgMB0JlaWppbmcxEDAOBgNVBAcMB0JlaWpp\n" +
  "bmcxHjAcBgNVBAoMFUVDRFNBIEludGVybWVkaWF0ZSBDQTELMAkGA1UECwwCSVQx\n" +
  "HjAcBgNVBAMMFUVDRFNBIEludGVybWVkaWF0ZSBDQTAeFw0yNTEwMTUwNjI3MzVa\n" +
  "Fw0zMDExMDgwNjI3MzVaMHUxCzAJBgNVBAYTAkNOMRAwDgYDVQQIDAdCZWlqaW5n\n" +
  "MRAwDgYDVQQHDAdCZWlqaW5nMRswGQYDVQQKDBJFQ0RTQSBFeGFtcGxlIENvcnAx\n" +
  "CzAJBgNVBAsMAklUMRgwFgYDVQQDDA93d3cuZXhhbXBsZS5jb20wWTATBgcqhkjO\n" +
  "PQIBBggqhkjOPQMBBwNCAASLR4TL7GQxOngZONYxay8vb5QQ2pDdaFobU2YSUC4m\n" +
  "dYxTsTyujMkTgK9sv/Me3Nf1lDXUz8mUCwVLHJ33hx3Jo4GEMIGBMAkGA1UdEwQC\n" +
  "MAAwCwYDVR0PBAQDAgK0MCcGA1UdEQQgMB6CD3d3dy5leGFtcGxlLmNvbYILZXhh\n" +
  "bXBsZS5jb20wHQYDVR0OBBYEFOp+v71yBI53o1mcrxqLOcZi0BrUMB8GA1UdIwQY\n" +
  "MBaAFDhFnzDg8Ap9glv7qyl8ajigm0OsMAoGCCqGSM49BAMCA0kAMEYCIQDIK8lp\n" +
  "z7+PNk6MxW45Lht9pUj/eAZfHW/692ZeJW1dfAIhAI1f3GEzkTihWd6h139gPXcS\n" +
  "y+Sf6/kfJnN0I3v/O2vI\n" +
  "-----END CERTIFICATE-----\n"                                        +
  "-----BEGIN CERTIFICATE-----\n" +
  "MIIEZjCCBAygAwIBAgIMTT/sw52uhI5Hi8tcMAoGCCqGSM49BAMCMFAxCzAJBgNV\n" +
  "BAYTAkJFMRkwFwYDVQQKDBBHbG9iYWxTaWduIG52LXNhMSYwJAYDVQQDDB1HbG9i\n" +
  "YWxTaWduIEVDQyBPViBTU0wgQ0EgMjAxODAeFw0yNTEwMTUwNjIwMzhaFw0yNTEx\n" +
  "MTQwNjIwMzhaMH4xCzAJBgNVBAYTAkNOMRAwDgYDVQQIDAdCZWlqaW5nMRAwDgYD\n" +
  "VQQHDAdCZWlqaW5nMR4wHAYDVQQKDBVFQ0RTQSBJbnRlcm1lZGlhdGUgQ0ExCzAJ\n" +
  "BgNVBAsMAklUMR4wHAYDVQQDDBVFQ0RTQSBJbnRlcm1lZGlhdGUgQ0EwWTATBgcq\n" +
  "hkjOPQIBBggqhkjOPQMBBwNCAARsa530tupy2vzI0ljPlGdO/QRMnXOv0R7cuQ8P\n" +
  "sTnaaqCBXrHZxrwoISe1c3+eq4CnJZBImvZSTSUUW9DfV31Co4ICnDCCApgwDAYD\n" +
  "VR0TBAUwAwEB/zAOBgNVHQ8BAf8EBAMCAe4wNQYDVR0lAQH/BCswKQYIKwYBBQUH\n" +
  "AwIGCCsGAQUFBwMBBggrBgEFBQcDAwYJKoZIhvcNAQkQMD8GA1UdHwQ4MDYwNKAy\n" +
  "oDCGLmh0dHA6Ly9jcmwuZ2xvYmFsc2lnbi5jb20vZ3NlY2NvdnNzbGNhMjAxOC5j\n" +
  "cmwwggGIBggrBgEFBQcBAQSCAXowggF2MIG4BggrBgEFBQcwAoaBq2h0dHBzOi8v\n" +
  "Z2l0Y29kZS5jb20vbTBfNzI2MTA3NzUvY29tcGF0aWJpbGl0eS9ibG9iL21hc3Rl\n" +
  "ci90ZXN0X3N1aXRlL3Jlc291cmNlL21hc3Rlci9zdGFuZGFyZCUyMHN5c3RlbS9h\n" +
  "Y3RzL3Jlc291cmNlL3NlY3VyaXR5L2NlcnRpZmljYXRlX2ZyYW1ld29yay8yMDI1\n" +
  "MDgxODE3ODgzNC9yb290LmNydDCBuAYIKwYBBQUHMAGGgatodHRwczovL2dpdGNv\n" +
  "ZGUuY29tL20wXzcyNjEwNzc1L2NvbXBhdGliaWxpdHkvYmxvYi9tYXN0ZXIvdGVz\n" +
  "dF9zdWl0ZS9yZXNvdXJjZS9tYXN0ZXIvc3RhbmRhcmQlMjBzeXN0ZW0vYWN0cy9y\n" +
  "ZXNvdXJjZS9zZWN1cml0eS9jZXJ0aWZpY2F0ZV9mcmFtZXdvcmsvMjAyNTA4MTgx\n" +
  "Nzg4MzQvcm9vdE9jc3AwNAYDVR0RBC0wK4IJbG9jYWxob3N0hwR/AAABhwTAqAEB\n" +
  "hhJodHRwOi8vMTkyLjE2OC4wLjIwHQYDVR0OBBYEFDhFnzDg8Ap9glv7qyl8ajig\n" +
  "m0OsMB8GA1UdIwQYMBaAFEYc/aft0QonL8U0/qNsvq3lrA9bMAoGCCqGSM49BAMC\n" +
  "A0gAMEUCIFsgnFqsgzPfzRtxLLqsh1tEQeW6xqp875XqpICR6FO7AiEAnJTGezte\n" +
  "A3uK46isQ2HwlmgwmXTNwgSP1JyWr5t6cVA=\n" +
  "-----END CERTIFICATE-----\n"                                        +
  "-----BEGIN CERTIFICATE-----\n" +
  "MIICGTCCAb6gAwIBAgIULcoKoYK2AQviXl1rlu+m7TH/J5UwCgYIKoZIzj0EAwMw\n" +
  "UDELMAkGA1UEBhMCQkUxGTAXBgNVBAoMEEdsb2JhbFNpZ24gbnYtc2ExJjAkBgNV\n" +
  "BAMMHUdsb2JhbFNpZ24gRUNDIE9WIFNTTCBDQSAyMDE4MB4XDTI1MTAxNTAzNTMw\n" +
  "OFoXDTM1MTAxMzAzNTMwOFowUDELMAkGA1UEBhMCQkUxGTAXBgNVBAoMEEdsb2Jh\n" +
  "bFNpZ24gbnYtc2ExJjAkBgNVBAMMHUdsb2JhbFNpZ24gRUNDIE9WIFNTTCBDQSAy\n" +
  "MDE4MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEJgdrEUKaVA8ZPzYD/kLwsn4c\n" +
  "UgkrCkTtMZEtG6l5iGTvpZT4qPTh8h5ILrui9bC+DLPRkEo3YsfHb62EanXqe6N2\n" +
  "MHQwHQYDVR0OBBYEFEYc/aft0QonL8U0/qNsvq3lrA9bMB8GA1UdIwQYMBaAFEYc\n" +
  "/aft0QonL8U0/qNsvq3lrA9bMAsGA1UdDwQEAwIBBjAJBgNVHREEAjAAMAkGA1Ud\n" +
  "EgQCMAAwDwYDVR0TAQH/BAUwAwEB/zAKBggqhkjOPQQDAwNJADBGAiEAz82HL4V2\n" +
  "3zTMVfJVMhHvSf2j+z7mUrRKCc0f21635DkCIQDqxlpMbRjs1bCL4pipCvD+w8v8\n" +
  "i4aEhDebPmxT8WuR7A==\n" +
  "-----END CERTIFICATE-----";
let caTrustCert =
  "-----BEGIN CERTIFICATE-----\n" +
  "MIICGTCCAb6gAwIBAgIULcoKoYK2AQviXl1rlu+m7TH/J5UwCgYIKoZIzj0EAwMw\n" +
  "UDELMAkGA1UEBhMCQkUxGTAXBgNVBAoMEEdsb2JhbFNpZ24gbnYtc2ExJjAkBgNV\n" +
  "BAMMHUdsb2JhbFNpZ24gRUNDIE9WIFNTTCBDQSAyMDE4MB4XDTI1MTAxNTAzNTMw\n" +
  "OFoXDTM1MTAxMzAzNTMwOFowUDELMAkGA1UEBhMCQkUxGTAXBgNVBAoMEEdsb2Jh\n" +
  "bFNpZ24gbnYtc2ExJjAkBgNVBAMMHUdsb2JhbFNpZ24gRUNDIE9WIFNTTCBDQSAy\n" +
  "MDE4MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEJgdrEUKaVA8ZPzYD/kLwsn4c\n" +
  "UgkrCkTtMZEtG6l5iGTvpZT4qPTh8h5ILrui9bC+DLPRkEo3YsfHb62EanXqe6N2\n" +
  "MHQwHQYDVR0OBBYEFEYc/aft0QonL8U0/qNsvq3lrA9bMB8GA1UdIwQYMBaAFEYc\n" +
  "/aft0QonL8U0/qNsvq3lrA9bMAsGA1UdDwQEAwIBBjAJBgNVHREEAjAAMAkGA1Ud\n" +
  "EgQCMAAwDwYDVR0TAQH/BAUwAwEB/zAKBggqhkjOPQQDAwNJADBGAiEAz82HL4V2\n" +
  "3zTMVfJVMhHvSf2j+z7mUrRKCc0f21635DkCIQDqxlpMbRjs1bCL4pipCvD+w8v8\n" +
  "i4aEhDebPmxT8WuR7A==\n" +
  "-----END CERTIFICATE-----";

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
      console.info("validate result is success.");
  } catch (error) {
      console.error("x509CertChain validate failed error code is: " + error.code);
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

```ts
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

// string转Uint8Array。
function stringToUint8Array(str: string): Uint8Array {
  const encoder = new util.TextEncoder();
  return encoder.encodeInto(str);
}

let rootCert = '-----BEGIN CERTIFICATE-----\n' +
  'MIIDjjCCAnagAwIBAgIQAzrx5qcRqaC7KGSxHQn65TANBgkqhkiG9w0BAQsFADBh\n' +
  'MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMRGlnaUNlcnQgSW5jMRkwFwYDVQQLExB3\n' +
  'd3cuZGlnaWNlcnQuY29tMSAwHgYDVQQDExdEaWdpQ2VydCBHbG9iYWwgUm9vdCBH\n' +
  'MjAeFw0xMzA4MDExMjAwMDBaFw0zODAxMTUxMjAwMDBaMGExCzAJBgNVBAYTAlVT\n' +
  'MRUwEwYDVQQKEwxEaWdpQ2VydCBJbmMxGTAXBgNVBAsTEHd3dy5kaWdpY2VydC5j\n' +
  'b20xIDAeBgNVBAMTF0RpZ2lDZXJ0IEdsb2JhbCBSb290IEcyMIIBIjANBgkqhkiG\n' +
  '9w0BAQEFAAOCAQ8AMIIBCgKCAQEAuzfNNNx7a8myaJCtSnX/RrohCgiN9RlUyfuI\n' +
  '2/Ou8jqJkTx65qsGGmvPrC3oXgkkRLpimn7Wo6h+4FR1IAWsULecYxpsMNzaHxmx\n' +
  '1x7e/dfgy5SDN67sH0NO3Xss0r0upS/kqbitOtSZpLYl6ZtrAGCSYP9PIUkY92eQ\n' +
  'q2EGnI/yuum06ZIya7XzV+hdG82MHauVBJVJ8zUtluNJbd134/tJS7SsVQepj5Wz\n' +
  'tCO7TG1F8PapspUwtP1MVYwnSlcUfIKdzXOS0xZKBgyMUNGPHgm+F6HmIcr9g+UQ\n' +
  'vIOlCsRnKPZzFBQ9RnbDhxSJITRNrw9FDKZJobq7nMWxM4MphQIDAQABo0IwQDAP\n' +
  'BgNVHRMBAf8EBTADAQH/MA4GA1UdDwEB/wQEAwIBhjAdBgNVHQ4EFgQUTiJUIBiV\n' +
  '5uNu5g/6+rkS7QYXjzkwDQYJKoZIhvcNAQELBQADggEBAGBnKJRvDkhj6zHd6mcY\n' +
  '1Yl9PMWLSn/pvtsrF9+wX3N3KjITOYFnQoQj8kVnNeyIv/iPsGEMNKSuIEyExtv4\n' +
  'NeF22d+mQrvHRAiGfzZ0JFrabA0UWTW98kndth/Jsw1HKj2ZL7tcu7XUIOGZX1NG\n' +
  'Fdtom/DzMNU+MeKNhJ7jitralj41E6Vf8PlwUHBHQRFXGU7Aj64GxJUTFy8bJZ91\n' +
  '8rGOmaFvE7FBcf6IKshPECBV1/MUReXgRPTqh5Uykw7+U0b6LJ3/iyK5S9kJRaTe\n' +
  'pLiaWN0bfVKfjllDiIGknibVb63dDcY3fe0Dkhvld1927jyNxF1WW6LZZm6zNTfl\n' +
  'MrY=\n' +
  '-----END CERTIFICATE-----';
let intermediateCert = '-----BEGIN CERTIFICATE-----\n' +
  'MIIEszCCA5ugAwIBAgIQCyWUIs7ZgSoVoE6ZUooO+jANBgkqhkiG9w0BAQsFADBh\n' +
  'MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMRGlnaUNlcnQgSW5jMRkwFwYDVQQLExB3\n' +
  'd3cuZGlnaWNlcnQuY29tMSAwHgYDVQQDExdEaWdpQ2VydCBHbG9iYWwgUm9vdCBH\n' +
  'MjAeFw0xNzExMDIxMjI0MzNaFw0yNzExMDIxMjI0MzNaMGAxCzAJBgNVBAYTAlVT\n' +
  'MRUwEwYDVQQKEwxEaWdpQ2VydCBJbmMxGTAXBgNVBAsTEHd3dy5kaWdpY2VydC5j\n' +
  'b20xHzAdBgNVBAMTFlJhcGlkU1NMIFRMUyBSU0EgQ0EgRzEwggEiMA0GCSqGSIb3\n' +
  'DQEBAQUAA4IBDwAwggEKAoIBAQC/uVklRBI1FuJdUEkFCuDL/I3aJQiaZ6aibRHj\n' +
  'ap/ap9zy1aYNrphe7YcaNwMoPsZvXDR+hNJOo9gbgOYVTPq8gXc84I75YKOHiVA4\n' +
  'NrJJQZ6p2sJQyqx60HkEIjzIN+1LQLfXTlpuznToOa1hyTD0yyitFyOYwURM+/CI\n' +
  '8FNFMpBhw22hpeAQkOOLmsqT5QZJYeik7qlvn8gfD+XdDnk3kkuuu0eG+vuyrSGr\n' +
  '5uX5LRhFWlv1zFQDch/EKmd163m6z/ycx/qLa9zyvILc7cQpb+k7TLra9WE17YPS\n' +
  'n9ANjG+ECo9PDW3N9lwhKQCNvw1gGoguyCQu7HE7BnW8eSSFAgMBAAGjggFmMIIB\n' +
  'YjAdBgNVHQ4EFgQUDNtsgkkPSmcKuBTuesRIUojrVjgwHwYDVR0jBBgwFoAUTiJU\n' +
  'IBiV5uNu5g/6+rkS7QYXjzkwDgYDVR0PAQH/BAQDAgGGMB0GA1UdJQQWMBQGCCsG\n' +
  'AQUFBwMBBggrBgEFBQcDAjASBgNVHRMBAf8ECDAGAQH/AgEAMDQGCCsGAQUFBwEB\n' +
  'BCgwJjAkBggrBgEFBQcwAYYYaHR0cDovL29jc3AuZGlnaWNlcnQuY29tMEIGA1Ud\n' +
  'HwQ7MDkwN6A1oDOGMWh0dHA6Ly9jcmwzLmRpZ2ljZXJ0LmNvbS9EaWdpQ2VydEds\n' +
  'b2JhbFJvb3RHMi5jcmwwYwYDVR0gBFwwWjA3BglghkgBhv1sAQEwKjAoBggrBgEF\n' +
  'BQcCARYcaHR0cHM6Ly93d3cuZGlnaWNlcnQuY29tL0NQUzALBglghkgBhv1sAQIw\n' +
  'CAYGZ4EMAQIBMAgGBmeBDAECAjANBgkqhkiG9w0BAQsFAAOCAQEAGUSlOb4K3Wtm\n' +
  'SlbmE50UYBHXM0SKXPqHMzk6XQUpCheF/4qU8aOhajsyRQFDV1ih/uPIg7YHRtFi\n' +
  'CTq4G+zb43X1T77nJgSOI9pq/TqCwtukZ7u9VLL3JAq3Wdy2moKLvvC8tVmRzkAe\n' +
  '0xQCkRKIjbBG80MSyDX/R4uYgj6ZiNT/Zg6GI6RofgqgpDdssLc0XIRQEotxIZcK\n' +
  'zP3pGJ9FCbMHmMLLyuBd+uCWvVcF2ogYAawufChS/PT61D9rqzPRS5I2uqa3tmIT\n' +
  '44JhJgWhBnFMb7AGQkvNq9KNS9dd3GWc17H/dXa1enoxzWjE0hBdFjxPhUb0W3wi\n' +
  '8o34/m8Fxw==\n' +
  '-----END CERTIFICATE-----';
let leafCert = '-----BEGIN CERTIFICATE-----\n' +
  'MIIGIzCCBQugAwIBAgIQD8vHwz7g05mDl1F5X17HGzANBgkqhkiG9w0BAQsFADBg\n' +
  'MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMRGlnaUNlcnQgSW5jMRkwFwYDVQQLExB3\n' +
  'd3cuZGlnaWNlcnQuY29tMR8wHQYDVQQDExZSYXBpZFNTTCBUTFMgUlNBIENBIEcx\n' +
  'MB4XDTI1MDMyNDAwMDAwMFoXDTI2MDMyMzIzNTk1OVowFzEVMBMGA1UEAwwMKi5k\n' +
  'b3ViYW8uY29tMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAw6eEA/GD\n' +
  'ShJ0Rtlet3Lf+uYiYzzFJ6J1iJeT/JyvTwDOTKO2VgMjsFHgUcFJBG6QGZT6PXSv\n' +
  'vhkdzzIqqXzJwDsqqowwTwMk0YN/JUB0yr/9aFlmQakLZClu1W5og7uxp4ME+ep6\n' +
  'aJhoQ9MMCCn3/pvDnLoX1hG9z0pgbUsnIrM+1roLpH+D0FwC4jww7+tDr89/kjb4\n' +
  '/+LMqjAbe1fLtXJRuxH5O+kAQNqLL/0ECvq+4KpC/r/0UxTlRTpGZY2M3MPUEXfp\n' +
  'RKMmkRoRSKwDMJ5u2DK0qanvV6mu7ORPoDsC/fTAiqonjh8rClm/zpj5GN9BQKfu\n' +
  'UoaeWIN/XMZSzQIDAQABo4IDIDCCAxwwHwYDVR0jBBgwFoAUDNtsgkkPSmcKuBTu\n' +
  'esRIUojrVjgwHQYDVR0OBBYEFCseEe+vZQ8BzqzkOju1EhGQwoCYMCMGA1UdEQQc\n' +
  'MBqCDCouZG91YmFvLmNvbYIKZG91YmFvLmNvbTA+BgNVHSAENzA1MDMGBmeBDAEC\n' +
  'ATApMCcGCCsGAQUFBwIBFhtodHRwOi8vd3d3LmRpZ2ljZXJ0LmNvbS9DUFMwDgYD\n' +
  'VR0PAQH/BAQDAgWgMB0GA1UdJQQWMBQGCCsGAQUFBwMBBggrBgEFBQcDAjA/BgNV\n' +
  'HR8EODA2MDSgMqAwhi5odHRwOi8vY2RwLnJhcGlkc3NsLmNvbS9SYXBpZFNTTFRM\n' +
  'U1JTQUNBRzEuY3JsMHYGCCsGAQUFBwEBBGowaDAmBggrBgEFBQcwAYYaaHR0cDov\n' +
  'L3N0YXR1cy5yYXBpZHNzbC5jb20wPgYIKwYBBQUHMAKGMmh0dHA6Ly9jYWNlcnRz\n' +
  'LnJhcGlkc3NsLmNvbS9SYXBpZFNTTFRMU1JTQUNBRzEuY3J0MAwGA1UdEwEB/wQC\n' +
  'MAAwggF9BgorBgEEAdZ5AgQCBIIBbQSCAWkBZwB2AA5XlLzzrqk+MxssmQez95Df\n' +
  'm8I9cTIl3SGpJaxhxU4hAAABlcjhhZsAAAQDAEcwRQIhAKfZw1gNPE4sWKi3WL0U\n' +
  'vO4EGn+MD1hScKPMNHex6Ty+AiBv0yYWRuEURh/8ywDMHC+1f3xFaj9kshfv389b\n' +
  'e09MhAB1AGQRxGykEuyniRyiAi4AvKtPKAfUHjUnq+r+1QPJfc3wAAABlcjhhcUA\n' +
  'AAQDAEYwRAIgClXL9SnQFh+6HEqsT/3aBM6jK9NmzG+hrmJGowOKVFYCIEsGPJda\n' +
  'TtsBnc/PrhZSjOHitpzrzKhW02hHOzkrtlR/AHYASZybad4dfOz8Nt7Nh2SmuFuv\n' +
  'CoeAGdFVUvvp6ynd+MMAAAGVyOGF3gAABAMARzBFAiBExgNNV8q5xfdSU+yL6NAJ\n' +
  'l1ze5IYXTetQf04caLUhKgIhALvTCHHHdvokmFbRKQvrY50ihwDoHd4pKbzRtyQ0\n' +
  'H16bMA0GCSqGSIb3DQEBCwUAA4IBAQAsjyQpYDf1JiYBsO4koUcFPeAdvTp9FbRL\n' +
  'yC0PN34rekPHwcjqsEU7mbuUaZ4EMklHqIqkniStPcKyIDCpSwBu17iezM57fwJA\n' +
  'tb9XfzjxZH1vWEFHImcvMEwR0BLRmwXUnnRt3qOeetTV/UpIwH4HGfHldtRNqSnj\n' +
  'xDiM1c2oRjv+4Qs5CTet70NHsaQBjkUWvioCgigE+vuCPnjwVNXJkfSHjC+DWWzf\n' +
  'Nc+rSFEOvO8Fe4d2rvboT7vXigvTciOeQdig9ySCJQCkWxOvB1AcvZc+kw0YhrpM\n' +
  'xUBhDd+DaUWOgmmVS3n6k3GfOqm2EU7iCp8KyfRu2DAsnlsO/YpH\n' +
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