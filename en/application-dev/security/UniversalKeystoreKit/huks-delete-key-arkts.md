# Deleting a Key (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

To ensure data security, delete the key that is no longer required.

The [Group Key](huks-group-key-overview.md) feature is supported since API version 23.

## How to Develop

For example, delete a 256-bit HKDF key.

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the key property set to specify [the property tags of keys](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag). When a single key is to be deleted, **TAG** can be empty.

3. Use [deleteKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksdeletekeyitem9) to delete the key.

<!-- @[key_deletions_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyDeletion/entry/src/main/ets/pages/KeyDeletion.ets) -->

``` TypeScript
/*
 * Delete a 256-bit HKDF key. This example uses promise-based APIs.
 */
import { huks } from '@kit.UniversalKeystoreKit';

let keyAlias = 'test_Key';

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
  try {
    await generateKeyItem(keyAlias, huksOptions);
    console.info(`promise: generateKeyItem success`);
  } catch (error) {
    console.error(`promise: generateKeyItem failed, ${JSON.stringify(error)}`);
  }
}

/* 2. Delete the key. */
let deleteHuksOptions: huks.HuksOptions = {
  properties: []
}

function deleteKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  return new Promise<void>((resolve, reject) => {
    try {
      huks.deleteKeyItem(keyAlias, huksOptions, (error, data) => {
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

async function deleteKey(keyAlias: string, huksOptions: huks.HuksOptions): Promise<void> {
  console.info(`enter promise deleteKeyItem`);
  try {
    await deleteKeyItem(keyAlias, huksOptions);
    console.info(`promise: deleteKeyItem success`);
  } catch (error) {
    console.error(`promise: deleteKeyItem failed, ${JSON.stringify(error)}`);
  }
}

async function executeKeyLifecycle(): Promise<string> {
  try {
    /* 1. Generate a key. */
    console.info('start generateKey...');
    await generateKey(keyAlias, generateHuksOptions);
    console.info('end generateKey...');

    /* 2. Delete the key. */
    console.info('start deleteKey...');
    await deleteKey(keyAlias, deleteHuksOptions);
    console.info('end deleteKey...');

    console.info('Key lifecycle completed successfully');
    return 'Success';
  } catch (error) {
    console.error(`Key lifecycle failed: ${JSON.stringify(error)}`);
    return 'Failed';
  }
}
```
