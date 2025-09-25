# Querying Key Aliases (ArkTS)

This topic walks you through on how to query key aliases.

>**NOTE**
> The mini-system devices do not support query of key aliases.

## How to Develop

1. Initialize the key property set to query the tags of key aliases. **TAG** supports only [HUKS_TAG_AUTH_STORAGE_LEVEL](../../reference/apis-universal-keystore-kit/_huks_type_api.md#oh_huks_authstoragelevel).

2. Use [listAliases](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukslistaliases12) to query the key aliases.

```ts
/*
 * The following example uses promise-based APIs to query key aliases.
 */
import { huks } from '@kit.UniversalKeystoreKit';

async function testListAliases() {
  /* 1. Initialize the key property set. */
  let queryProperties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: huks.HuksAuthStorageLevel.HUKS_AUTH_STORAGE_LEVEL_DE
    }
  ];
  let queryOptions: huks.HuksOptions = {
    properties: queryProperties
  };

  try {
    /* 2. Query key aliases. */
    let result: huks.HuksListAliasesReturnResult = await huks.listAliases(queryOptions);
    console.info(`promise: listAliases success`);
  } catch (error) {
    console.error(`promise: listAliases fail`);
  }
}
```
