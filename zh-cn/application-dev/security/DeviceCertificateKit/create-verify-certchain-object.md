# 证书链对象的创建和校验

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

以校验证书链为例，完成证书链对象的创建，获取证书链中的证书列表以及使用信任锚对证书链进行校验。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```

2. 基于已有的证书数据，调用[cert.createX509CertChain](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509certchain11)创建X509证书链对象，并返回结果。

3. 调用[x509CertChain.getCertList](../../reference/apis-device-certificate-kit/js-apis-cert.md#getcertlist11)获取证书链中的X509证书列表。

4. 调用[x509CertChain.validate](../../reference/apis-device-certificate-kit/js-apis-cert.md#validate11)使用校验参数校验证书链并返回结果。

<!-- @[certificate_chain_object_creation_and_validation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateVerifyCertchainObject.ets) -->

