# Exporting a Key (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

This topic walks you through on how to export the public key of a persistently stored asymmetric key. Currently, HUKS supports export of the ECC, RSA, Ed25519, X25519, and SM2 public keys.
>**NOTE**<br>
> <!--RP1-->Mini-system devices<!--RP1End--> support export of only the RSA public keys.

## How to Develop

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Use [exportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksexportkeyitem9) to export the key based on the specified **keyAlias** and **options**. **options** is a reserved parameter and is left empty currently.

3. In the [HuksReturnResult](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksreturnresult9) object returned, the public key is in the **outData** field in the DER format defined in X.509. For details about the format, see [Public Key Material Format](huks-concepts.md#public-key-material-format).

```ts
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

function Uint8ArrayToString(fileData: Uint8Array) {
  let dataString = '';
  for (let i = 0; i < fileData.length; i++) {
    dataString += String.fromCharCode(fileData[i]);
  }
  return dataString;
}

/* 1. Set the key alias. */
let keyAlias = 'keyAlias';
/* Leave options empty. */
let emptyOptions: huks.HuksOptions = {
  properties: []
};
/* 2. Set key properties. */
let properties1: huks.HuksParam[] = [{
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
let huksOptions: huks.HuksOptions = {
  properties: properties1,
  inData: new Uint8Array([])
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

/* 4. Export the key. */
async function exportKeyItem(keyAlias: string, emptyOptions: huks.HuksOptions): Promise<boolean> {
  console.info(`enter promise exportKeyItem`);
  let ret: boolean = false;
  try {
    await huks.exportKeyItem(keyAlias, emptyOptions)
      .then((data) => {
        console.info(`promise: exportKeyItem success, data is ` + Uint8ArrayToString(data.outData as Uint8Array));
        ret = true;
      }).catch((error: BusinessError) => {
        console.error(`promise: exportKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error(`promise: exportKeyItem input arg invalid`);
  }
  return ret;
}

async function testExportKeyItem() {
  let retGen = await generateKeyItem(keyAlias, huksOptions);
  if (retGen == false) {
    console.error(`generateKeyItem failed`);
    return;
  }

  let retExp = await exportKeyItem(keyAlias, emptyOptions);
  if (retExp == false) {
    console.error(`exportKeyItem failed`);
    return;
  }
  console.info(`testExportKeyItem success`);
}
```
