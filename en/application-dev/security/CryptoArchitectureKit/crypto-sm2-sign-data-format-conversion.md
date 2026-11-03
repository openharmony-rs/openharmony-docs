# SM2 Signature Data Format Conversion (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=65945a7a0f4fc96eaefe48f50def3bda3f01bc0a translatedAt=2026-10-30T04:03:19.167Z pushedAt=2026-10-30T07:32:11.759Z nl=1 -->

HarmonyOS supports the conversion between the DER and R|S formats.

You can specify SM2 signature data and convert it to DER-format signature data. Conversely, you can also extract the specific SM2 signature data from DER-format signature data.

**Specifying Signature Parameters and Converting to DER Format**
1. Create an [EccSignatureSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#eccsignaturespec20) object to specify SM2 signature parameters.

2. Call [genEccSignature](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#geneccsignature20) and pass in the EccSignatureSpec object to convert it to SM2 signature data in DER format.

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
    console.info('genEccSignature result: success.');
    console.info('data = ' + data);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`ecc failed: errCode: ${e.code}, message: ${e.message}`);
  }
}
```

**Converting DER Ciphertext to the R and S Parameters**
1. Specify the SM2 signature parameters in DER format.

2. Call [genEccSignatureSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#geneccsignaturespec20) and pass in the DER-format data to convert it to SM2 signature data in (r, s) format.

<!-- @[sm2_sign_data_der_to_rs](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/sm2_data_format_convertion/sm2_sign_data_der_to_rs.ets) -->

``` TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

function testSm2SignDataDerToRs() {
  try {
    let data =
      new Uint8Array([48, 69, 2, 33, 0, 216, 15, 76, 238, 158, 165, 108, 76, 72, 63, 115, 52, 255, 51, 149, 54, 224,
        179, 49, 225, 70, 36, 117, 88, 154, 154, 27, 194, 161, 3, 1, 115, 2, 32, 51, 9, 53, 55, 248, 82, 7, 159, 179,
        144, 57, 151, 195, 17, 31, 106, 123, 32, 139, 219, 6, 253, 62, 240, 181, 134, 214, 107, 27, 230, 175, 40]);
    let spec: cryptoFramework.EccSignatureSpec = cryptoFramework.SignatureUtils.genEccSignatureSpec(data);
    console.info('genEccSignatureSpec result: success.');
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`ecc failed: errCode: ${e.code}, message: ${e.message}`);
  }
}
```
