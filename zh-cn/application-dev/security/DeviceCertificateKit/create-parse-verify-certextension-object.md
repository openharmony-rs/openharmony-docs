# 证书扩展信息对象的创建、解析和校验

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

以获取证书指定OID域段，并判断是否为CA证书为例，完成证书扩展信息对象的创建、解析和校验。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。
   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```

2. 解析证书扩展域段数据，调用[cert.createCertExtension](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatecertextension10)创建证书扩展域段对象。

3. 调用[CertExtension.getEntry](../../reference/apis-device-certificate-kit/js-apis-cert.md#getentry10)获取指定OID证书扩展域段信息。比如，证书扩展域段对象标识符列表，根据对象标识符获取具体数据等。

4. 调用[CertExtension.checkCA](../../reference/apis-device-certificate-kit/js-apis-cert.md#checkca10)判断证书是否为CA证书。

<!-- @[create_parse_validate_certificate_extension_info_objects](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateParseVerifyCertextensionObject.ets) -->
