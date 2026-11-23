# Creating a TrustAnchor Object Array from a PKCS #12 File

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=9fca4748e6758305b5cd265dfe627a1972198ec1 translatedAt=2026-11-20T03:38:03.843Z pushedAt=2026-11-20T06:09:36.136Z nl=1 -->

Construct a **TrustAnchor** object array from a PKCS #12 file during certificate chain validation.

## How to Develop

1. Import the [certificate module](../../reference/apis-device-certificate-kit/js-apis-cert.md).

2. Based on the existing PKCS #12 file data, use [cert.createTrustAnchorsWithKeyStore](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatetrustanchorswithkeystore12) to create an [X509TrustAnchor](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509trustanchor11) object array and return the result.

<!-- @[trust_array_constructed_from_p12_file_during_validation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateTrustanchorFromP12.ets) -->

``` TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function test() {
  // ...
  try {
    let data = await cert.createTrustAnchorsWithKeyStore(p12Data, '123456');
    console.info('createTrustAnchorsWithKeyStore result: success, the num of result is :' + data.length);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`createTrustAnchorsWithKeyStore failed, errCode: ${e.code}, message: ${e.message}`);
    // ...
  }
}
```

