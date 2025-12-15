# Deleting a Key (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

To ensure data security, delete the key that is no longer required.

## How to Develop

For example, delete a 256-bit HKDF key.

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the key property set to specify [the property tags of keys](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag). When a single key is to be deleted, **TAG** can be empty.

3. Use [deleteKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksdeletekeyitem9) to delete the key.

```ts
/*
 * Delete a 256-bit HKDF key. This example uses promise-based APIs.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

/* 1. Set the key alias. */
let keyAlias = 'test_Key';
/* 2. Initialize the key property set. */
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
let deleteHuksOptions: huks.HuksOptions = {
  properties: []
}

/* 3. Generate a key. */
async function generateKeyItem(keyAlias: string, huksOptions: huks.HuksOptions): Promise<boolean> {
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

/*4. Delete a key.*/
async function deleteKeyItem(keyAlias: string, huksOptions: huks.HuksOptions): Promise<boolean> {
  console.info(`enter promise deleteKeyItem`);
  let ret: boolean = false;
  try {
    await huks.deleteKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: deleteKeyItem success`);
        ret = true;
      }).catch((error: BusinessError) => {
        console.error(`promise: deleteKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: deleteKeyItem input arg invalid`);
  }
  return ret;
}

async function testDelete() {
  let retGen = await generateKeyItem(keyAlias, generateHuksOptions);
  if (retGen == false) {
    console.error(`generateKeyItem failed`);
    return;
  }

  let retDel = await deleteKeyItem(keyAlias, deleteHuksOptions);
  if (retDel == false) {
    console.error(`deleteKeyItem failed`);
    return;
  }

  console.info(`deleteKeyItem test success`);
}
```
