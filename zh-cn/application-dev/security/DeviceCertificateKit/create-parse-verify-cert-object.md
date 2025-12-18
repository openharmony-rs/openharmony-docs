# 证书对象的创建、解析和校验

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

以校验证书有效性为例，完成证书对象的创建、解析和校验。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。
   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```

2. 基于已有的X509证书数据，调用[cert.createX509Cert](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509cert)创建证书对象。

3. 解析证书的字段信息。
   此处以获取证书版本、证书序列号、证书颁发者名称、证书主体名称、证书对象的字符串类型数据为例，更多字段信息获取接口请查看[API参考文档](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509cert)。

4. 调用[X509Cert.getPublicKey](../../reference/apis-device-certificate-kit/js-apis-cert.md#getpublickey)获取证书中的公钥，并调用[X509Cert.verify](../../reference/apis-device-certificate-kit/js-apis-cert.md#verify)校验签名。示例为自验签场景，因此获取的是本证书中的公钥。应用须结合自身场景获取用于验签的公钥。

5. 调用[X509Cert.checkValidityWithDate](../../reference/apis-device-certificate-kit/js-apis-cert.md#checkvaliditywithdate)校验证书有效期。入参date用于确认此日期是否在X509证书有效期内。

<!-- @[certificate_object_creation_resolution_validation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateParseVerifyCertObject.ets) -->
