# 密钥导入(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutitian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API版本26.0.0开始，在外部密钥管理扩展场景下，密钥导入能力支持将加密封装的密钥对导入到扩展设备中。密钥用途等参数传递给Extension后，由Extension实现方根据业务场景自行处理，HUKS不做额外校验。

具体的场景介绍及开发流程，请参考[密钥生成与导入介绍](huks-extension-key-generation-import-overview.md)。

## 开发步骤

1. 获取外部密钥管理扩展的资源ID。具体请参考[获取外部密钥管理扩展资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)。

2. 打开资源，获取资源句柄。

3. 获取或生成用于解封密钥的密钥句柄（wrappedHandle）。

4. 调用[importWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksimportwrappedkeyitem9)导入加密封装的密钥对。

5. 关闭资源。

## 开发案例

```ts
import { huks, huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

async function openResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.openResource(resourceId)
      .then(() => {
        console.info(`promise: openResource success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: openResource failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error(`promise: openResource input arg invalid`);
  }
}

async function importWrappedKeyItem(
  keyAlias: string,
  wrappingKeyAlias: string,
  huksOptions: huks.HuksOptions
): Promise<void> {
  try {
    await huks.importWrappedKeyItem(keyAlias, wrappingKeyAlias, huksOptions)
      .then(() => {
        console.info(`promise: importWrappedKeyItem success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: importWrappedKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error(`promise: importWrappedKeyItem input arg invalid`);
  }
}

async function closeResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.closeResource(resourceId)
      .then(() => {
        console.info(`promise: closeResource success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: closeResource failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error(`promise: closeResource input arg invalid`);
  }
}

async function extensionKeyImport(): Promise<void> {
  /* 1.准备资源ID（keyAlias和wrappingKeyAlias使用resourceId） */
  const resourceId = JSON.stringify({
    providerName: "testProviderName",
    bundleName: "com.example.cryptoapplication",
    abilityName: "CryptoExtension",
    index: {
      key: "testKey"
    } as ESObject
  });
  const keyAlias = resourceId;
  // wrappingKeyAlias可以是相同的resourceId或另一个已打开的资源ID
  const wrappingKeyAlias = resourceId;

  /* 2.构造密钥导入参数 */
  const properties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_RSA
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
    }
  ];
  // 加密封装的密钥数据（由Extension实现方定义格式）
  const wrappedKeyData: Uint8Array = new Uint8Array([/* 封装密钥数据 */]);
  const huksOptions: huks.HuksOptions = {
    properties: properties,
    inData: wrappedKeyData
  };

  try {
    /* 3.打开资源 */
    await openResource(resourceId);
    
    /* 4.导入加密封装的密钥 */
    // 注意：wrappingKeyAlias需要事先存在或通过generateKeyItem生成
    await importWrappedKeyItem(keyAlias, wrappingKeyAlias, huksOptions);
    
    /* 5.关闭资源 */
    await closeResource(resourceId);
    
    console.info(`promise: extensionKeyImport completed successfully`);
  } catch (error) {
    console.error(`promise: extensionKeyImport input arg invalid`);
  }
}
```

## 密钥封装格式说明

> **说明：**
>
> 加密封装的密钥数据（wrappedKeyData）格式由Extension实现方定义。应用需要根据Extension厂商提供的说明准备相应的密钥封装数据。