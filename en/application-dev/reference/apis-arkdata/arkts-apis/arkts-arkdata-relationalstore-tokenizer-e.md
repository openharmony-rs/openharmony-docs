# Tokenizer

```TypeScript
enum Tokenizer
```

Enumerates tokenizers that can be used for FTS. Use the enum name rather than the enum value.

The table creation statement varies with the tokenizer in use.

For details about the definition of **this.context** in the sample code, see the application [context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) of the stage model.

The following is an example of the table creation statement when **ICU_TOKENIZER** is used:

The following is an example of the table creation statement when **CUSTOM_TOKENIZER** is used:

The following is an example of the table creation statement when **CUSTOM_TOKENIZER** is used:

**Since:** 17

<!--Device-relationalStore-enum Tokenizer--><!--Device-relationalStore-enum Tokenizer-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## CUSTOM_TOKENIZER

```TypeScript
CUSTOM_TOKENIZER = 2
```

A custom tokenizer is used. Chinese (simplified and traditional), English, and Arabic numerals are supported. Compared with **ICU_TOKENIZER**, **CUSTOM_TOKENIZER** has advantages in tokenization accuracy and resident memory usage. The self-developed tokenizer supports two modes: default tokenization mode and short word tokenization mode (short_words). You can use the cut_mode parameter to specify the mode. If no mode is specified, the default mode is used.

**Since:** 18

<!--Device-Tokenizer-CUSTOM_TOKENIZER = 2--><!--Device-Tokenizer-CUSTOM_TOKENIZER = 2-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## ICU_TOKENIZER

```TypeScript
ICU_TOKENIZER = 1
```

The ICU tokenizer is used, which supports Chinese and multiple languages. If the ICU tokenizer is used, you can set the language to use, for example, **zh_CN** for Chinese and **tr_TR** for Turkish. For details about the supported languages, see [ICU tokenizer](https://gitcode.com/openharmony/third_party_icu/blob/master/icu4c/source/data/lang/en.txt). For details about the language abbreviations, see [locales](https://gitcode.com/openharmony/third_party_icu/tree/master/icu4c/source/data/locales).

**Since:** 17

<!--Device-Tokenizer-ICU_TOKENIZER = 1--><!--Device-Tokenizer-ICU_TOKENIZER = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## NONE_TOKENIZER

```TypeScript
NONE_TOKENIZER = 0
```

NONE_TOKENIZER: not use tokenizer

**Since:** 17

<!--Device-Tokenizer-NONE_TOKENIZER = 0--><!--Device-Tokenizer-NONE_TOKENIZER = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Examples**

For details about the definition of this.context in the sample code, see the application [context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) of the stage model.

The following is an example of the table creation statement when ICU_TOKENIZER is used:

```TypeScript
import { relationalStore } from '@kit.ArkData'; // Import modules.
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

// In this example, Ability is used to obtain an RdbStore instance in the stage model. You can use other implementations as required.
export default class EntryAbility extends UIAbility {
  async onWindowStageCreate(windowStage: window.WindowStage) {
    let store: relationalStore.RdbStore | undefined = undefined;
    const STORE_CONFIG: relationalStore.StoreConfig = {
      name: "MyStore.db",
      securityLevel: relationalStore.SecurityLevel.S3,
      tokenizer: relationalStore.Tokenizer.ICU_TOKENIZER
    };
    store = await relationalStore.getRdbStore(this.context, STORE_CONFIG);

    const SQL_CREATE_TABLE = "CREATE VIRTUAL TABLE example USING fts4(name, content, tokenize='icu zh_CN')";
    if (store != undefined) {
      (store as relationalStore.RdbStore).executeSql(SQL_CREATE_TABLE, (err) => {
        if (err) {
          console.error(`ExecuteSql failed, code is ${err.code},message is ${err.message}`);
          return;
        }
        console.info('create virtual table done.');
      });
    }
  }
}
```

The following is an example of the table creation statement when CUSTOM_TOKENIZER is used:

```TypeScript
import { relationalStore } from '@kit.ArkData'; // Import modules.
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

// In this example, Ability is used to obtain an RdbStore instance in the stage model. You can use other implementations as required.
export default class EntryAbility extends UIAbility {
  async onWindowStageCreate(windowStage: window.WindowStage) {
    let store: relationalStore.RdbStore | undefined = undefined;
    const STORE_CONFIG: relationalStore.StoreConfig = {
      name: "MyStore.db",
      securityLevel: relationalStore.SecurityLevel.S3,
      tokenizer: relationalStore.Tokenizer.CUSTOM_TOKENIZER
    };
    store = await relationalStore.getRdbStore(this.context, STORE_CONFIG);

    const SQL_CREATE_TABLE = "CREATE VIRTUAL TABLE example USING fts5(name, content, tokenize='customtokenizer')";
    if (store != undefined) {
      (store as relationalStore.RdbStore).executeSql(SQL_CREATE_TABLE, (err) => {
        if (err) {
          console.error(`ExecuteSql failed, code is ${err.code},message is ${err.message}`);
          return;
        }
        console.info('create virtual table done.');
      });
    }
  }
}
```

The following is an example of the table creation statement when CUSTOM_TOKENIZER is used:

```TypeScript
import { relationalStore } from '@kit.ArkData'; // Import modules.
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  async onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('custom tokenizer example: window stage create begin.');
    let store: relationalStore.RdbStore | undefined = undefined;
    const storeConfig: relationalStore.StoreConfig = {
      name: "MyStore.db",
      securityLevel: relationalStore.SecurityLevel.S3
    };
    let customType = relationalStore.Tokenizer.CUSTOM_TOKENIZER;
    let customTypeSupported = relationalStore.isTokenizerSupported(customType);
    if (customTypeSupported) {
      storeConfig.tokenizer = customType;
    } else {
      console.info('custom tokenizer example: not support custom tokenizer.');
      return;
    }
    store = await relationalStore.getRdbStore(this.context, storeConfig);

    const SQL_CREATE_TABLE =
      "CREATE VIRTUAL TABLE example USING fts5(name, content, tokenize='customtokenizer cut_mode short_words')";
    if (store != undefined) {
      (store as relationalStore.RdbStore).executeSql(SQL_CREATE_TABLE, (err) => {
        if (err) {
          console.error(`custom tokenizer example: ExecuteSql failed, code is ${err.code},message is ${err.message}`);
          return;
        }
        console.info('custom tokenizer example: create virtual table done.');
      });
    }
  }
}
```
