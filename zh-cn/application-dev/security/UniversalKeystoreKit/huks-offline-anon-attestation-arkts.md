# 离线匿名密钥证明(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API 26.0.0开始支持离线匿名密钥证明，该接口用于在无网络环境下证明密钥的合法性，与在线匿名密钥证明相比，在离线证书有效期内不需要网络连接，推荐优先使用离线密钥证明。离线证书是在该流程中由三级CA颁发的证书，其有效期为1个月。

> **注意：**
>
> - 离线密钥证明依赖网络，需要定期联网使用该接口以更新离线证书。
> - 离线匿名密钥证明需保证本地时间是准确的，否则可能导致对端校验证书超期失败。

## 开发步骤

1. 指定密钥别名，密钥别名命名规范参考[密钥生成介绍及算法规格](huks-key-generation-overview.md)。

2. 初始化参数集。

   [HuksParam[]](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksparam)中的HuksParam字段参数必须包含[HUKS_TAG_ATTESTATION_CHALLENGE](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag)属性,可选参数包含[HUKS_TAG_ATTESTATION_ID_VERSION_INFO](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag)、[HUKS_TAG_ATTESTATION_ID_ALIAS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag)属性。

3. 生成非对称密钥，具体请参考[密钥生成](huks-key-generation-overview.md)。

4. 将密钥别名与参数集作为参数传入[anonAttestKeyItemOffline](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksanonattestkeyitemoffline)方法中，即可进行离线匿名密钥证明。

## 开发案例

``` TypeScript
import { huks } from "@kit.UniversalKeystoreKit";
import { BusinessError } from "@kit.BasicServicesKit";

function StringToUint8Array(str: String) {
  let arr: number[] = new Array();
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

let g_challenge: Uint8Array = StringToUint8Array("hi_challenge_data");
let g_keyAlias: Uint8Array = StringToUint8Array("testKey");

let gCommonParam: Array<huks.HuksParam> = [
  { tag: huks.HuksTag.HUKS_TAG_ATTESTATION_CHALLENGE, value: g_challenge },
  { tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_ALIAS, value: g_keyAlias },
];

let gKeyParam: Array<huks.HuksParam> = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_ECC
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_ECC_KEY_SIZE_256
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE
  },
  {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }
]

let gKeyOption: huks.HuksOptions = { properties: gKeyParam };

async function AnonAttestKeyOfflineTest() {
  let testKeyAlias: string = "testKey";
  await huks.generateKeyItem(testKeyAlias, gKeyOption);

  await huks.anonAttestKeyItemOffline(testKeyAlias, gCommonParam).then((data) => {
    console.info("anonAttestKeyItemOffline success")
  }).catch((error: BusinessError) =>
    console.error(`anonAttestKeyItemOffline error ${JSON.stringify(error)}`))
}
```
