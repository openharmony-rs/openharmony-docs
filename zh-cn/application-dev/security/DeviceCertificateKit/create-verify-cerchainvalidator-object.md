# 证书链校验器对象的创建和校验

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

证书链是由一组证书组成的证书集合，以图中样例证书文件为例，即可放在一个证书链中。

样例中可以看到GlobalSign自签名了证书，GlobalSign也签发了GlobalSign RSA OV SSL CA 2018的证书，GlobalSign RSA OV SSL CA 2018又签发了第三级证书。

![zh-cn_image_0000001746997074](figures/zh-cn_image_0000001746997074.png)

开发者可以参考示例将已有的多个证书构建出证书链数据。

## 开发步骤

1. 导入[证书算法库框架模块](../../reference/apis-device-certificate-kit/js-apis-cert.md)。
   ```ts
   import { cert } from '@kit.DeviceCertificateKit';
   ```

2. [cert.createCertChainValidator](../../reference/apis-device-certificate-kit/js-apis-cert.md#certcreatecertchainvalidator)创建证书链校验器对象。

3. 基于已有的证书数据，创建证书链数据对象[CertChainData](../../reference/apis-device-certificate-kit/js-apis-cert.md#certchaindata)。
   
   证书算法库框架提供了证书链校验器对象可用于校验证书链，以验证信任链根源，但待校验的证书链数据对象应符合证书链数据对象的数据结构定义[CertChainData](../../reference/apis-device-certificate-kit/js-apis-cert.md#certchaindata)。

4. 调用[CertChainValidator.validate](../../reference/apis-device-certificate-kit/js-apis-cert.md#validate)校验证书链数据。

<!-- @[certificate_chain_validator_object_creation_and_validation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DeviceCertificateKit/CertificateAlgorithmLibrary/entry/src/main/ets/pages/CreateVerifyCerchainvalidatorObject.ets) -->
