# 使用系统预置CA证书校验证书链

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API 20开始，支持使用系统预置CA证书校验证书链。

以校验证书链为例，完成证书链对象的创建，使用系统预置CA证书对证书链进行校验。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```

2. 基于已有的证书数据，调用[cert.createX509CertChain](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509certchain11)创建X509证书链对象，并返回结果。

3. 调用[x509CertChain.validate](../../reference/apis-device-certificate-kit/js-apis-cert.md#validate11)设置校验参数trustSystemCa为true，使用系统预置CA证书校验证书链并返回结果。

<!-- @[verify-certchain-by-systemca](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/VerifyCertchainBySystemca.ets) -->
