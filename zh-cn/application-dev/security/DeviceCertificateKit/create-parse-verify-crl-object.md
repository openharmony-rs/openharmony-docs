# 证书吊销列表对象的创建、解析和校验

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

以校验证书是否已吊销为例，完成证书吊销列表对象的创建、解析和校验。若证书已被吊销，将打印被吊销日期。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)和[加解密算法库模块](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md)。
   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   import { cryptoFramework } from '@kit.CryptoArchitectureKit';
   ```

2. 基于已有的CRL数据，调用[cert.createX509CRL](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509crl11)创建X509证书吊销列表的对象。

3. 解析证书吊销列表信息。

   此处以获取证书吊销列表版本、证书吊销列表类型、证书吊销列表颁发者名称、证书吊销列表对象的字符串类型数据为例，更多字段信息获取接口请查看[API参考文档](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509crl11)。

4. 基于已有公钥信息，创建PublicKey公钥对象。

   具体可参考[加解密算法库框架-指定二进制数据生成非对称密钥对](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-3)。

5. 调用[X509CRL.verify](../../reference/apis-device-certificate-kit/js-apis-cert.md#verify11)校验签名合法性。

6. 基于已有的X509证书数据，调用[cert.createX509Cert](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509cert)创建证书对象。

7. 调用[X509CRL.isRevoked](../../reference/apis-device-certificate-kit/js-apis-cert.md#isrevoked11)判断X509证书是否已被吊销。

8. 调用[X509CRL.getRevokedCert](../../reference/apis-device-certificate-kit/js-apis-cert.md#getrevokedcert11)获取被吊销证书对象。

9.  调用[X509CRLEntry.getRevocationDate](../../reference/apis-device-certificate-kit/js-apis-cert.md#getrevocationdate11)获取被吊销日期。

<!-- @[create_parse_verify_certificate_revocation_list_objects](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateParseVerifyCrlObject.ets) -->
