# 证书链校验时从p12文件构造TrustAnchor对象数组

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

证书链校验时从p12文件构造TrustAnchor对象数组。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

2. 基于现有的p12文件数据，调用[cert.createTrustAnchorsWithKeyStore](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatetrustanchorswithkeystore12)创建[X509TrustAnchor](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509trustanchor11)数组对象，并返回结果。

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

