# Key Generation, Import, and Export

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=f70f62268656d3b182431efa45d33eb33ec094f1 translatedAt=2026-11-10T03:07:54.079Z pushedAt=2026-11-10T06:51:07.590Z nl=1 -->

Starting from API version 26.0.0, HUKS provides key generation, import, and export capabilities. In key management extension scenarios (such as UKey physical devices), applications can use standard HUKS interfaces to generate key pairs, import encrypted and wrapped key pairs, or export public keys in the key management extension service.

Callers include but are not limited to third-party applications, browsers, and internal modules (such as certificate management). The HUKS framework is responsible for forwarding interface calls to the key management extension service to complete the actual operations, and **callers do not need to concern themselves with the specific implementation details**.

## Overview

This section covers the core operations of the key lifecycle:

- In key management extension scenarios, keyAlias is resourceId, meaning that the resource open operation has already been performed, and the providerName, abilityName, and bundleName contained in keyAlias are consistent.

- When calling, [HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) must be specified as [HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22), indicating that the key is managed by the key management extension service implementer. Parameters such as key purpose are handled by the key management extension service implementer according to the business scenario, and **HUKS does not perform additional verification**.

## Generating a Key (ArkTS)

In the key management extension scenario, HUKS supports generating a key pair in the key management extension service. The generated key is stored in the service, the private key never leaves the service provider, and the public key can be obtained through the export API. Parameters such as the key purpose are handled by the key management extension service provider based on the business scenario, and HUKS does not perform additional verification.

An app initiates a key generation request by calling the HUKS [generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksgeneratekeyitem9) API, and the request is forwarded to the [onGenerateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#ongeneratekeyitem) API of **CryptoExtensionAbility** to complete key generation.

### How to Develop

1. Obtain the resourceId through the [obtaining a resource ID](huks-extension-ability-general-operation.md#obtaining-a-resource-id) operation, and pass the resourceId to open the resource. For details, see [Opening and Closing Resources](huks-extension-ability-general-operation.md#opening-and-closing-resources).

2. Call [generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksgeneratekeyitem9) to generate a key pair. It is recommended that parameters such as the algorithm type, key length, and key purpose be passed in. In the key parameters, [HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) must be set to [HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22), indicating that the key is managed by the key management extension service.

3. After the operation is complete, close the resource. For details, see [Opening and Closing Resources](huks-extension-ability-general-operation.md#opening-and-closing-resources).

### Development Examples

<!-- @[extension_key_generation_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/ExtensionKeyGeneration.ets) -->

``` TypeScript
import { huks, huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function openResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.openResource(resourceId)
      .then(() => {
        console.info('promise: openResource success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: openResource failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: openResource input arg invalid.');
  }
}

async function generateKeyItem(keyAlias: string, huksOptions: huks.HuksOptions): Promise<void> {
  try {
    await huks.generateKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info('promise: generateKeyItem success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: generateKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: generateKeyItem input arg invalid.');
  }
}

async function closeResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.closeResource(resourceId)
      .then(() => {
        console.info('promise: closeResource success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: closeResource failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: closeResource input arg invalid.');
  }
}

async function extensionKeyGeneration(): Promise<void> {
  /* 1. Prepare the resource ID (keyAlias uses resourceId). */
  const resourceId = JSON.stringify({
    providerName: 'testProviderName',
    bundleName: 'com.example.cryptoapplication',
    abilityName: 'CryptoExtension',
    index: {
      key: 'testKey'
    } as ESObject
  });
  const keyAlias = resourceId;

  const properties: huks.HuksParam[] = [
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_CLASS,
      value: huks.HuksKeyClassType.HUKS_KEY_CLASS_EXTENSION
    },
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
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN
    }
  ];
  const huksOptions: huks.HuksOptions = {
    properties: properties,
    inData: new Uint8Array([])
  };

  try {
    /* 2. Open the resource. */
    await openResource(resourceId);

    /* 3. Generate the key. */
    await generateKeyItem(keyAlias, huksOptions);

    /* 4. Close the resource. */
    await closeResource(resourceId);

    console.info('promise: extensionKeyGeneration completed successfully.');
  } catch (error) {
    console.error('promise: extensionKeyGeneration input arg invalid.');
  }
}
```

## Importing a Key (ArkTS)

In the key management extension scenario, HUKS supports importing an encrypted wrapped key pair into the key management extension service. The wrapped key pair is usually encrypted by a secure negotiation key to ensure that the key is not disclosed during transmission. Parameters such as the key purpose are handled by the external key management service provider based on the business scenario, and HUKS does not perform additional verification.

- The keyAlias and wrappingKeyAlias involved in the interface input parameters are resourceIds. Both parameters must have been successfully opened in the key management extension service through the resource opening interface. If either resourceId is not opened or has been closed, the interface returns an error indicating that the resource does not exist.

- When the passed keyAlias and wrappingKeyAlias are inconsistent, the certificate is imported into the resource identified by keyAlias by default.

An app initiates a key security import request by calling the [importWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksimportwrappedkeyitem9) API of HUKS. The request is then forwarded to the [onImportWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onimportwrappedkeyitem) API of **CryptoExtensionAbility** to complete the key security import.

### How to Develop

1. Obtain the resourceId through the [obtaining a resource ID](huks-extension-ability-general-operation.md#obtaining-a-resource-id) operation, and pass the resourceId to open the resource. For details, see [Opening and Closing Resources](huks-extension-ability-general-operation.md#opening-and-closing-resources).

2. Call [importWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksimportwrappedkeyitem9) to import the encrypted wrapped key pair. In the key parameters, set [HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) to [HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22), indicating that the key is managed by the key management extension service.

3. After the operation is complete, close the resource. For details, see [Opening and Closing Resources](huks-extension-ability-general-operation.md#opening-and-closing-resources).

### Development Examples

<!-- @[extension_key_import_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/ExtensionKeyImport.ets) -->

``` TypeScript
import { huks, huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function openResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.openResource(resourceId)
      .then(() => {
        console.info('promise: openResource success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: openResource failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: openResource input arg invalid.');
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
        console.info('promise: importWrappedKeyItem success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: importWrappedKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: importWrappedKeyItem input arg invalid.');
  }
}

async function closeResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.closeResource(resourceId)
      .then(() => {
        console.info('promise: closeResource success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: closeResource failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: closeResource input arg invalid.');
  }
}

async function extensionKeyImport(): Promise<void> {
  /* 1. Prepare the resource ID (keyAlias and wrappingKeyAlias use resourceId). */
  const resourceId = JSON.stringify({
    providerName: 'testProviderName',
    bundleName: 'com.example.cryptoapplication',
    abilityName: 'CryptoExtension',
    index: {
      key: 'testKey'
    } as ESObject
  });
  const keyAlias = resourceId;
  const wrappingKeyAlias = resourceId;

  const properties: huks.HuksParam[] = [
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_CLASS,
      value: huks.HuksKeyClassType.HUKS_KEY_CLASS_EXTENSION
    },
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
  // Encrypted wrapped key data (the format is defined by the Extension implementer).
  const wrappedKeyData: Uint8Array = new Uint8Array([/* wrapped key data */]);
  const huksOptions: huks.HuksOptions = {
    properties: properties,
    inData: wrappedKeyData
  };

  try {
    /* 2. Open the resource. */
    await openResource(resourceId);

    /* 3. Import the encrypted wrapped key. */
    await importWrappedKeyItem(keyAlias, wrappingKeyAlias, huksOptions);

    /* 4. Close the resource. */
    await closeResource(resourceId);

    console.info('promise: extensionKeyImport completed successfully.');
  } catch (error) {
    console.error('promise: extensionKeyImport input arg invalid.');
  }
}
```

## Exporting a Key (ArkTS)

In the key management extension scenario, HUKS supports exporting the public key of a specified key from the key management extension service. The exported public key can be used in scenarios such as certificate application, key agreement, and PIN encryption.

An app initiates a public key export request by calling the HUKS [exportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksexportkeyitem9) API, and the request is forwarded to the [onExportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onexportkeyitem) API of **CryptoExtensionAbility** to complete the public key export.

### How to Develop

1. Obtain the resourceId through the [obtaining a resource ID](huks-extension-ability-general-operation.md#obtaining-a-resource-id) operation, and pass the resourceId to open the resource. For details, see [Opening and Closing Resources](huks-extension-ability-general-operation.md#opening-and-closing-resources).

2. Call [exportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksexportkeyitem9) to export the public key. In the key parameters, specify [HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) as [HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22), indicating that the key is managed by external key management extension.

3. After the operation is complete, close the resource. For details, see [Opening and Closing Resources](huks-extension-ability-general-operation.md#opening-and-closing-resources).

### Development Examples

<!-- @[extension_key_export_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/ExtensionKeyExport.ets) -->

``` TypeScript
import { huks, huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function openResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.openResource(resourceId)
      .then(() => {
        console.info('promise: openResource success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: openResource failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: openResource input arg invalid.');
  }
}

async function exportPublicKey(keyAlias: string): Promise<Uint8Array> {
  let publicKey: Uint8Array = new Uint8Array([]);
  try {
    const exportProperties: huks.HuksParam[] = [
      {
        tag: huks.HuksTag.HUKS_TAG_KEY_CLASS,
        value: huks.HuksKeyClassType.HUKS_KEY_CLASS_EXTENSION
      }
    ];
    const exportOptions: huks.HuksOptions = {
      properties: exportProperties
    };
    await huks.exportKeyItem(keyAlias, exportOptions)
      .then((data) => {
        publicKey = data.outData as Uint8Array;
        console.info('promise: exportKeyItem success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: exportKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: exportKeyItem input arg invalid.');
  }
  return publicKey;
}

async function closeResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.closeResource(resourceId)
      .then(() => {
        console.info('promise: closeResource success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: closeResource failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: closeResource input arg invalid.');
  }
}

async function extensionKeyExport(): Promise<Uint8Array> {
  /* 1. Prepare the resource ID. */
  const resourceId = 'your_resource_id';

  let publicKey: Uint8Array = new Uint8Array([]);
  try {
    /* 2. Open the resource. */
    await openResource(resourceId);

    /* 3. Export the public key. */
    publicKey = await exportPublicKey(resourceId);
    console.info(`promise: public key length: ${publicKey.length}`);

    /* 4. Close the resource. */
    await closeResource(resourceId);

    console.info('promise: extensionKeyExport completed successfully.');
  } catch (error) {
    console.error('promise: extensionKeyExport input arg invalid.');
  }
  return publicKey;
}
```

## Specification Differences

The preceding APIs reuse the original HUKS API definitions. In the key management extension scenario, the parameters in `params` are optional, and the supported range is defined by the implementer of the key management extension service. If the corresponding parameters are not passed in, the key management extension service uses the configured default behavior.

- **Key generation (generateKeyItem)**: It is recommended to pass in parameters such as the algorithm type (`HUKS_TAG_ALGORITHM`), key length (`HUKS_TAG_KEY_SIZE`), and key purpose (`HUKS_TAG_PURPOSE`). If not passed in, the key management extension service uses the default values. `keyAlias` must be a valid `resourceId`.
- **Secure key import (importWrappedKeyItem)**: It is recommended to pass in parameters such as the algorithm type, key length, and key purpose. `keyAlias` and `wrappingKeyAlias` must be valid `resourceId` values. `wrappedKey` is the wrapped key data, and its format is defined by the implementer of the key management extension service.
- **Public key export (exportKeyItem)**: It is recommended to pass in the key purpose (`HUKS_TAG_PURPOSE`) parameter to export the public key for a specific purpose. If not passed in, the key management extension service uses the default value (signing purpose by default). `keyAlias` must be a valid `resourceId`.