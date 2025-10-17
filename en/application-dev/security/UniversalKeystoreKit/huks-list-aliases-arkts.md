# Querying Key Aliases (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

This topic walks you through on how to query key aliases.

>**NOTE**
> <!--RP1-->The mini-system devices<!--RP1End--> do not support query of key aliases.

## How to Develop

1. Initialize the key property set to query the tags of key aliases. The tags support only [HUKS_TAG_AUTH_STORAGE_LEVEL](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_authstoragelevel).

2. Use [listAliases](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukslistaliases12) to query the key aliases.

```ts
/*
 * The following example uses promise-based APIs to query key aliases.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

/* 1. Initialize the key property set. */
let queryProperties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
    value: huks.HuksAuthStorageLevel.HUKS_AUTH_STORAGE_LEVEL_DE
  }
];
let queryOptions: huks.HuksOptions = {
  properties: queryProperties
};

async function listAliases(options: huks.HuksOptions) {
  console.info(`promise: enter listAliases`);
  try {
    await huks.listAliases(options)
      .then((data) => {
        console.info(`promise: listAliases success`);
        for (let i = 0; i < data.keyAliases.length; ++i) {
          console.info(`promise: aliases ${i} : ${data.keyAliases[i]}`);
        }
      }).catch((error: BusinessError) => {
        console.error(`promise: listAliases failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: listAliases input arg invalid`);
  }
}

async function testListAliases() {
  await listAliases(queryOptions);
}
```
