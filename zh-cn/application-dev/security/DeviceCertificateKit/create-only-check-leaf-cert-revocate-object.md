# 支持本地证书链吊销状态校验时仅校验终端实体证书

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

API 22开始支持本地证书链吊销状态校验时仅校验终端实体证书。

## 开发步骤

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