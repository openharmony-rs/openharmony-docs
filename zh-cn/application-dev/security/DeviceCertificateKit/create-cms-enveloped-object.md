# 证书CMS封装

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API 22开始，支持证书CMS封装。

PKCS#7是用于存储签名或加密数据的标准语法。CMS作为PKCS#7的扩展，支持的数据类型包括数据、签名数据、封装数据、签名和封装数据、摘要数据以及加密数据。该标准常用于保护数据的完整性和机密性。

目前仅支持CMS签名数据和封装数据。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```
2. 调用[cert.createCmsGenerator](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatecmsgenerator18)创建cmsGenerator对象。

3. 调用[cmsGenerator.setRecipientEncryptionAlgorithm](../../reference/apis-device-certificate-kit/js-apis-cert.md#setrecipientencryptionalgorithm22)设置加密算法。

4. 调用[cmsGenerator.addRecipientInfo](../../reference/apis-device-certificate-kit/js-apis-cert.md#addrecipientinfo22)添加接收者信息。

5. 调用[cmsGenerator.doFinal](../../reference/apis-device-certificate-kit/js-apis-cert.md#dofinal18)获取CMS最终封装数据。

6. 调用[cmsGenerator.getEncryptedContentData](../../reference/apis-device-certificate-kit/js-apis-cert.md#getencryptedcontentdata22)获取CMS封装密文数据。

<!-- @[create-cms-enveloped-object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateCmsEnvelopedObject.ets) -->
