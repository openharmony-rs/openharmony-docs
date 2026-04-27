# 构建并校验证书链

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API版本26.0.0开始，证书链校验器提供证书链构建和校验能力，支持通过[X509CertValidatorParams](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509certvalidatorparams)参数配置构建和校验行为，包括信任锚设置、证书吊销检查、日期校验等。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。
   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```

2. 基于已有的证书数据，创建待校验[X509Cert](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509cert)证书对象。

3. 调用[cert.createCertChainValidator](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatecertchainvalidator)接口创建证书链校验器对象。

4. 创建[X509CertValidatorParams](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509certvalidatorparams)校验参数对象。

5. 调用[CertChainValidator.validate(cert: X509Cert, params: X509CertValidatorParams)](../../reference/apis-device-certificate-kit/js-apis-cert.md#validate-2)接口构建并校验证书链，返回校验成功的证书链[VerifyCertResult](../../reference/apis-device-certificate-kit/js-apis-cert.md#verifycertresult)。

## 场景一：指定信任证书

当应用有自定义的信任锚证书时，可以通过[trustedCerts](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509certvalidatorparams)参数指定信任的CA证书。

<!-- @[certificate_chain_validation_with_custom_trust_anchor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/ValidateCertChainWithCustomTrustAnchor.ets) -->

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
  let encodingBlob: cert.EncodingBlob = {
    data: stringToUint8Array(certData),
    encodingFormat: cert.EncodingFormat.FORMAT_PEM
  };

  let x509Cert: cert.X509Cert = {} as cert.X509Cert;
  try {
    x509Cert = await cert.createX509Cert(encodingBlob);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createX509Cert failed: errCode: ${e.code}, message: ${e.message}`);
  }
  return x509Cert;
}

async function validateCertChainWithCustomTrustAnchor(): Promise<void> {
  try {
    // 创建证书对象
    let endEntityCert = await createX509Cert(endEntityCertData);
    let intermediateCaCert = await createX509Cert(intermediateCaCertData);
    let rootCaCert = await createX509Cert(rootCaCertData);

    // 构建校验参数
    let params: cert.X509CertValidatorParams = {
      // 不信任的中间证书，用于构建证书链
      untrustedCerts: [intermediateCaCert],
      // 信任锚证书，用于验证证书链
      trustedCerts: [rootCaCert],
      // 不信任系统预置CA证书
      trustSystemCa: false,
      date: '20260422121212Z'
    };
    // 创建证书链校验器实例
    let validator = cert.createCertChainValidator('PKIX');

    // 验证endEntityCert
    let result: cert.VerifyCertResult = await validator.validate(endEntityCert, params);
    console.info('validate success, certChain length: ' + result.certChain.length);
    for (let i = 0; i < result.certChain.length; i++) {
      let subject = result.certChain[i].getSubjectX500DistinguishedName().getName(cert.EncodingType.ENCODING_UTF8);
      console.info(`Cert ${i} subject: ${subject}`);
    }
  } catch (err) {
    // 校验失败
    let error = err as BusinessError;
    console.error('validate failed, errCode: ' + error.code + ', errMsg: ' + error.message);
  }
}
```

## 场景二：信任系统预置CA证书

当应用需要验证互联网公开证书（如HTTPS网站证书）时，可以使用系统预置的CA证书作为信任锚。通过设置[trustSystemCa](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509certvalidatorparams)为`true`，校验器会使用系统预置CA证书库构建并验证证书链。

<!-- @[certificate_chain_validation_with_system_ca](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/ValidateCertChainWithSystemCa.ets) -->

## 场景三：证书吊销校验（CRL）

可以通过[crls](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509certrevokedparams)参数指定CRL，用来检查证书是否被吊销。

<!-- @[certificate_chain_validation_with_crl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/ValidateCertChainWithCrl.ets) -->

## 场景四：国密证书链校验

国密SM2证书链校验，通常需要设置[userId](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509certvalidatorparams)参数。

<!-- @[certificate_chain_validation_for_sm2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/ValidateSm2CertChain.ets) -->
