# 证书CMS解封装

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API 22开始，支持证书CMS解封装。

PKCS#7是用于存储签名或加密数据的标准语法。CMS作为PKCS#7的扩展，支持的数据类型包括数据、签名数据、封装数据、签名和封装数据、摘要数据以及加密数据。该标准常用于保护数据的完整性和机密性。

目前仅支持CMS签名数据和封装数据。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```
2. 调用[cms封装](../../security/DeviceCertificateKit/create-cms-sign-object.md)进行CMS数据封装。

3. 调用[cert.createCmsParser](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatecmsparser22)创建CmsParser对象。

4. 调用[cmsParser.setRawData](../../reference/apis-device-certificate-kit/js-apis-cert.md#setrawdata22)设置CMS数据。

5. 调用[cmsParser.decryptEnvelopedData](../../reference/apis-device-certificate-kit/js-apis-cert.md#decryptenvelopeddata22)解密封装数据。

解封装示例：

<!-- @[create-cms-decapsulation-object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateCmsDecapsulationObject.ets) -->

