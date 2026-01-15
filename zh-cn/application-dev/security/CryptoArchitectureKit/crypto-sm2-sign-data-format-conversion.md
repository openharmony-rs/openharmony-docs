# SM2签名数据格式转换(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

当前支持DER格式与（r、s）格式互转的能力。

开发者可指定SM2签名数据，将其转换成DER格式密文。反之，也可以从DER格式密文中取出具体的SM2签名数据。

**指定密文参数，转换为DER格式**
1. 构造[EccSignatureSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#eccsignaturespec20)对象，用于指定SM2密文参数。

2. 调用[genEccSignature](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#geneccsignature20)，将EccSignatureSpec对象传入，转换为DER格式的SM2密文。

<!-- @[sm2_sign_data_rs_to_der](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/sm2_data_format_convertion/sm2_sign_data_rs_to_der.ets) -->

``` TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

function testSm2SignDataRsToDer() {
  try {
    let spec: cryptoFramework.EccSignatureSpec = {
      r: BigInt('97726608965854271693043443511967021777934035174185659091642456228829830775155'),
      s: BigInt('23084224202834231287427338597254751764391338275617140205467537273296855150376'),
    };

    let data = cryptoFramework.SignatureUtils.genEccSignature(spec);
    console.info('genEccSignature success');
    console.info('data is ' + data);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`ecc error, ${e.code}, ${e.message}`);
  }
}
```

**指定DER格式，转换为（r、s）格式**
1. 指定DER格式的SM2密文参数。

2. 调用[genEccSignatureSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#geneccsignaturespec20)，将DER格式数据传入，转换为(r、s)格式的SM2密文。

<!-- @[sm2_sign_data_der_to_rs](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/sm2_data_format_convertion/sm2_sign_data_der_to_rs.ets) -->
