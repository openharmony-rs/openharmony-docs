# Checking a Key (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

Check whether a key exists.

## How to Develop

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the key property set to specify [the property tags of keys](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag). When a single key is queried, **TAG** can be empty.

3. Use [hasKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukshaskeyitem11) to check whether the key exists.

```ts
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

/* 1. Set the key alias. */
let keyAlias = 'test_key';
let isKeyExist: boolean;
/* 2. Construct an empty object. */
let huksOptions: huks.HuksOptions = {
  properties: []
}
/* 3. Initialize the key property set. */
let generateProperties: huks.HuksParam[] = [{
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
let generateHuksOptions: huks.HuksOptions = {
  properties: generateProperties,
  inData: new Uint8Array([])
}

/* 4. Generate a key. */
async function publicGenKeyFunc(keyAlias: string, huksOptions: huks.HuksOptions): Promise<boolean> {
  console.info(`enter promise generateKeyItem`);
  let ret: boolean = false;
  try {
    await huks.generateKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: generateKeyItem success`);
        ret = true;
      }).catch((error: BusinessError) => {
        console.error(`promise: generateKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error(`promise: generateKeyItem input arg invalid`);
  }
  return ret;
}

/* 5. Check whether the key exists. */
async function hasKeyItem(keyAlias: string, huksOptions: huks.HuksOptions): Promise<boolean> {
  console.info(`enter promise hasKeyItem`);
  let ret: boolean = false;
  try {
    await huks.hasKeyItem(keyAlias, huksOptions)
      .then((data) => {
        console.info(`promise: hasKeyItem success, data = ${data}`);
        ret = true;
      }).catch((error: BusinessError) => {
        console.error(`promise: hasKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
    return ret;
  } catch (error) {
    console.error(`promise: hasKeyItem input arg invalid, errCode : ${error.code}, errMsg : ${error.message}`);
  }

  return ret;
}

async function testKeyExist() {
  /* 1. Generate a key. */
  let genResult = await publicGenKeyFunc(keyAlias, generateHuksOptions);
  /* 2. Check whether the key exists. */
  if (genResult == true) {
    isKeyExist = await hasKeyItem(keyAlias, huksOptions);
    console.info(`hasKeyItem success, isKeyExist = ${isKeyExist}`);
  } else {
    console.error('Key generation failed, skipping query');
  }
}
```
