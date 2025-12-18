# 证书PKCS12的创建和解析

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API 18开始，支持解析PKCS12证书。

从API 21开始，支持创建PKCS12证书。

PKCS12是一种用于存储和传输用户私钥、证书及其相关证书链的标准格式。该格式通过密码保护，将多个密码学对象打包为一个加密的容器文件，支持存储私钥、公钥证书、证书颁发机构证书以及其他相关的密码学数据。PKCS12广泛应用于数字证书的安全存储、跨平台传输和证书备份场景，是实现证书管理和PKI应用的重要标准之一。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。

   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```
2. 调用[cert.createPkcs12](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatepkcs1221)创建PKCS12文件。

3. 调用[cert.parsePkcs12](../../reference/apis-device-certificate-kit/js-apis-cert.md#certparsepkcs1218)解析PKCS12文件。

- 异步方法示例：

<!-- @[create-parse-pkcs12-async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateParsePkcs12Async.ets) -->

- 同步方法示例：

<!-- @[create-parse-pkcs12-sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateParsePkcs12Sync.ets) -->
