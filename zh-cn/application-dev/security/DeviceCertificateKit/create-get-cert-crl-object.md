# 证书集合及证书吊销列表集合对象的创建和获取

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从输入的证书集合和证书吊销列表集合中选择满足条件的证书或者证书吊销列表。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```

2. 基于已有的证书数据，调用[cert.createX509Cert](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509cert-1)创建X509证书的对象。

3. 基于已有的CRL数据，调用[cert.createX509CRL](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509crl11-1)创建X509证书吊销列表的对象。

4. 调用[cert.createCertCRLCollection](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatecertcrlcollection11)创建[CertCRLCollection](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcrlcollection11)的对象，并返回相应的结果。

5. 调用[CertCRLCollection.selectCerts](../../reference/apis-device-certificate-kit/js-apis-cert.md#selectcerts11)查找所有与[X509CertMatchParameters](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509certmatchparameters11)匹配的证书对象数组，并返回结果。

6. 调用[CertCRLCollection.selectCRLs](../../reference/apis-device-certificate-kit/js-apis-cert.md#selectcrls11)查找所有与[X509CRLMatchParameters](../../reference/apis-device-certificate-kit/js-apis-cert.md#x509crlmatchparameters11)匹配的证书吊销列表数组，并返回结果。

<!-- @[certificate_collection_and_certificate_revocation_list_collection_object_creation_and_acquisition](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateGetCertCrlObject.ets) -->
