# 证书CMS签名

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API 18开始，支持证书CMS签名。

从API 22开始，支持证书CMS封装。

PKCS#7是用于存储签名或加密数据的标准语法。CMS作为PKCS#7的扩展，支持的数据类型包括数据、签名数据、封装数据、签名和封装数据、摘要数据以及加密数据。该标准常用于保护数据的完整性和机密性。
目前仅支持CMS签名数据和封装数据。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```
2. 调用[cert.createCmsGenerator](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatecmsgenerator18)创建cmsGenerator对象。

3. 调用[cmsGenerator.addSigner](../../reference/apis-device-certificate-kit/js-apis-cert.md#addsigner18)添加签名者信息。

4. 调用[cmsGenerator.addCert](../../reference/apis-device-certificate-kit/js-apis-cert.md#addcert18)添加证书。

5. 调用[cmsGenerator.doFinal](../../reference/apis-device-certificate-kit/js-apis-cert.md#dofinal18)获取Cms最终签名数据。

- 异步方法示例：

<!-- @[create-cms-sign-object-async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateCmsSignObjectAsync.ets) -->

- 同步方法示例：

<!-- @[create-cms-sign-object-sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateCmsSignObjectSync.ets) -->
