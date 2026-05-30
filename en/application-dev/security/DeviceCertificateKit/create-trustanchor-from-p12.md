# Creating a TrustAnchor Object Array from a .p12 File

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

This topic walks you through on how to create a **TrustAnchor** object array from a .p12 file during certificate chain verification.

## How to Develop

1. Import the [cert](../../reference/apis-device-certificate-kit/js-apis-cert.md) module.

2. Use [cert.createTrustAnchorsWithKeyStore](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatetrustanchorswithkeystore12) to create an [X509TrustAnchor](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509trustanchor11) array object based on the .p12 file.

<!-- @[trust_array_constructed_from_p12_file_during_validation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateTrustanchorFromP12.ets) -->

``` TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

function test() {
  // ...
  try {
    cert.createTrustAnchorsWithKeyStore(p12Data, '123456').then((data) => {
      console.info('createTrustAnchorsWithKeyStore result: success, the num of result is :' + data.length);
    }).catch((err: BusinessError) => {
      console.error(`createTrustAnchorsWithKeyStore failed, errCode: ${err.code}, message: ${err.message}`);
    })
  } catch (error) {
    console.error(`createTrustAnchorsWithKeyStore failed, errCode: ${error.code}, message: ${error.message}`);
  }
}
```
