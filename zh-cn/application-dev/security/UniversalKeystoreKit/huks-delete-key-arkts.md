# 密钥删除(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

为保证数据安全性，当不需要使用该密钥时，应该删除密钥。

从API 23开始支持[群组密钥](huks-group-key-overview.md)特性。

## 开发步骤

以删除HKDF256密钥为例。

1. 指定密钥别名，密钥别名命名规范参考[密钥生成介绍及算法规格](huks-key-generation-overview.md)。

2. 初始化密钥属性集。用于删除时指定[密钥的属性TAG](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag)，当删除单个时，TAG字段可传空。

3. 调用接口[deleteKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksdeletekeyitem9)，删除密钥。

<!-- @[key_deletions_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyDeletion/entry/src/main/ets/pages/KeyDeletion.ets) -->

``` TypeScript
/*
 * 以下以HKDF256密钥的Promise操作使用为例
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

/* 1.生成密钥 */
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

/* 2.删除密钥 */
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
    /* 1.生成密钥 */
    console.info('start generateKey...');
    await generateKey(keyAlias, generateHuksOptions);
    console.info('end generateKey...');

    /* 2.删除密钥 */
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