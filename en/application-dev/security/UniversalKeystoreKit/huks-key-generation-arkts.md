# Generating a Key (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

This topic walks you through on how to randomly generate a key with the DH algorithm. For details about the scenarios and supported algorithms, see [Supported Algorithms](huks-key-generation-overview.md#supported-algorithms).

> **NOTE**
> Key aliases must not contain sensitive information, such as personal data.

## How to Develop

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the key property set.
   - Encapsulate key properties in [HuksParam](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksparam) and use a **HuksParam** array to assign values to the **properties** field of [HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions).
   - The key property set must contain [HuksKeyAlg](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyalg), [HuksKeySize](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeysize), and [HuksKeyPurpose](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeypurpose). That is, the **HUKS_TAG_ALGORITHM**, **HUKS_TAG_PURPOSE**, and **HUKS_TAG_KEY_SIZE** tags are mandatory.
   
   > **NOTE**
   >
   > A key can have only one purpose, and the purpose specified during key generation must match the key purpose during usage. Otherwise, an exception occurs.

3. Use [generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksgeneratekeyitem9) to generate a key based on the key alias and key properties specified.

> **NOTE**
> If the service uses the same key alias to call the HUKS API to generate a key again, HUKS will generate a new key and overwrite the historical key file.

```ts
/* Generate a DH key. */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

/* 1. Set the key alias. */
let keyAlias = 'dh_key';
/* 2. Initialize the key property set. */
let properties1: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_DH
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_AGREE
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_DH_KEY_SIZE_2048
  }
];
let huksOptions: huks.HuksOptions = {
  properties: properties1,
  inData: new Uint8Array(new Array())
}

/* 3. Generate a key. */
async function generateKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`enter promise generateKeyItem`);
  try {
    await huks.generateKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: generateKeyItem success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: generateKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error(`promise: generateKeyItem input arg invalid`);
  }
}

async function TestGenKey() {
  await generateKeyItem(keyAlias, huksOptions);
}
```
