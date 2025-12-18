# 证书链校验时下载缺失的中间CA证书

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API 23开始，支持证书链校验时下载缺失的中间CA证书。

以创建X509证书链为例，完成证书链对象的创建，创建过程校验时允许下载缺失的中间证书。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```

2. 基于已有的证书数据，调用[cert.createX509Cert](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatex509cert-1)创建X509证书对象，并返回结果。

3. 调用[cert.buildX509CertChain](../../reference/apis-device-certificate-kit/js-apis-cert.md#certbuildx509certchain12)创建X509证书链对象，将validationParameters的allowDownloadIntermediateCa参数设置为true，开启允许校验过程中从网络下载缺失的中间CA。

> **说明**
>
> 本开发指导中提供的示例代码需要在配置网络的前提下执行。需要申请ohos.permission.INTERNET权限，配置方式请参见[声明权限](../../security/AccessToken/declare-permissions.md)。

<!-- @[allow-download-intermediate-cert](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/AllowDownloadIntermediateCert.ets) -->

