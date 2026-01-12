# Checking a Key (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

Check whether a key exists.

The [Group Key](huks-group-key-overview.md) feature is supported since API version 23.

## How to Develop

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the key property set to specify [the property tags of keys](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag). When a single key is queried, **TAG** can be empty.

3. Use [hasKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukshaskeyitem11) to check whether the key exists.

<!-- @[querying_the_existence_of_a_key_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/OtherOperations/CheckKeyExists/entry/src/main/ets/pages/CheckKeyExists.ets) -->

``` TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

let keyAlias = 'test_key';
let isKeyExist: Boolean;

let generateProperties: huks.HuksParam[] = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_DH
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_AGREE
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_DH_KEY_SIZE_2048
  }
];

let generateHuksOptions: huks.HuksOptions = {
  properties: generateProperties,
  inData: new Uint8Array([])
}

/* 1. Generate a key. */
function generateKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  return new Promise<void>((resolve, reject) => {
    try {
      huks.generateKeyItem(keyAlias, huksOptions, (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data);
        }
      });
    } catch (error) {
      throw (error as Error);
    }
  });
}

async function generateKey(keyAlias: string, huksOptions: huks.HuksOptions): Promise<void> {
  console.info(`enter promise generateKeyItem`);
  await generateKeyItem(keyAlias, huksOptions);
  console.info(`promise: generateKeyItem success`);
}

/* 2. Check whether the key exists. */
let huksOptions: huks.HuksOptions = {
  properties: []
}

function hasKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  return new Promise<boolean>((resolve, reject) => {
    try {
      huks.hasKeyItem(keyAlias, huksOptions, (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data.valueOf());
        }
      });
    } catch (error) {
      throw (error as Error);
    }
  });
}

async function checkKeyExistence(keyAlias: string, huksOptions: huks.HuksOptions): Promise<boolean> {
  console.info(`enter promise hasKeyItem`);
  const exists = await hasKeyItem(keyAlias, huksOptions);
  console.info(`promise: hasKeyItem success, isKeyExist = ${exists}`);
  return exists;
}

async function executeCheckKey(): Promise<string> {
  try {
    /* 1. Generate a key. */
    await generateKey(keyAlias, generateHuksOptions);

    /* 2. Check whether the key exists. */
    isKeyExist = await checkKeyExistence(keyAlias, huksOptions);

    console.info(`Key check completed, isKeyExist = ${isKeyExist}`);
    return 'Success';
  } catch (error) {
    console.error(`Key check failed: ${JSON.stringify(error)}`);
    return 'Failed';
  }
}
```
<!--no_check-->