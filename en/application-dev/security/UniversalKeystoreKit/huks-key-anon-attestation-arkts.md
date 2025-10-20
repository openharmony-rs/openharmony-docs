# Anonymous Key Attestation (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

Ensure network connection during the operation.

## How to Develop

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initializes a parameter set.

   The **properties** field in [HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions) must contain [HUKS_TAG_ATTESTATION_CHALLENGE](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag). Optional parameters include [HUKS_TAG_ATTESTATION_ID_VERSION_INFO](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) and [HUKS_TAG_ATTESTATION_ID_ALIAS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag).

3. Generate an asymmetric key. For details, see [Key Generation](huks-key-generation-overview.md).

4. Use [anonAttestKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksanonattestkeyitem11) with the key alias and parameter set to perform key attestation.

```ts
/*
 * Perform anonymous key attestation. This example uses promise-based APIs.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

/* 1. Set the key alias. */
let keyAliasString = "key anon attest";
let aliasUint8 = StringToUint8Array(keyAliasString);
let securityLevel = StringToUint8Array('sec_level');
let challenge = StringToUint8Array('challenge_data');
let versionInfo = StringToUint8Array('version_info');
let anonAttestCertChain: Array<string>;

/* Encapsulate the key parameter set. */
let genKeyProperties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PSS
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_GENERATE_TYPE,
    value: huks.HuksKeyGenerateType.HUKS_KEY_GENERATE_TYPE_DEFAULT
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB
  }
]
let genOptions: huks.HuksOptions = {
  properties: genKeyProperties
};

/* 2. Encapsulate the parameter set for key attestation. */
let anonAttestKeyProperties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO,
    value: securityLevel
  }, {
    tag: huks.HuksTag.HUKS_TAG_ATTESTATION_CHALLENGE,
    value: challenge
  }, {
    tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_VERSION_INFO,
    value: versionInfo
  }, {
    tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_ALIAS,
    value: aliasUint8
  }
]
let huksOptions: huks.HuksOptions = {
  properties: anonAttestKeyProperties
};

/* 3. Generate a key. */
async function generateKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter generateKeyItem`);
  try {
    await huks.generateKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: generateKeyItem success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: generateKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: generateKeyItem input arg invalid`);
  }
}

/* 4. Attest the key. */
async function anonAttestKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`enter promise anonAttestKeyItem`);
  try {
    await huks.anonAttestKeyItem(keyAlias, huksOptions)
      .then((data) => {
        if (data !== null && data.certChains !== null) {
          anonAttestCertChain = data.certChains as string[];
        }
        console.info(`promise: anonAttestKeyItem success, anonAttestCertChain = ${anonAttestCertChain}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: anonAttestKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: anonAttestKeyItem input arg invalid`);
  }
}

async function AnonAttestKeyTest() {
  await generateKeyItem(keyAliasString, genOptions);
  await anonAttestKeyItem(keyAliasString, huksOptions);
  console.info('anon attest certChain data: ' + anonAttestCertChain)
}
```
