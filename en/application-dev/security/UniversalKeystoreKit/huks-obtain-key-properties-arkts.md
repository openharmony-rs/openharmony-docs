# Obtaining Key Properties (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

This topic describes how to obtain properties of a key. Before the operation, ensure that the key exists in HUKS.
>**NOTE**
> <!--RP1-->The mini-system devices<!--RP1End--> do not allow for obtaining key properties.

## How to Develop

1. Set the key alias (**keyAlias**), which cannot exceed 128 bytes.

2. Use [getKeyItemProperties](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksgetkeyitemproperties9) to obtain the properties of the key based on **keyAlias** and **options**. **options** is a reserved parameter and is left empty currently.

3. You can find the key properties in the **properties** field in the [HuksReturnResult](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksreturnresult9) object.

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
/* 2. Set key properties. */
let emptyOptions: huks.HuksOptions = {
  properties: []
};
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

/* 4. Obtain key properties. */
async function getKeyItemProperties(keyAlias: string, emptyOptions: huks.HuksOptions): Promise<boolean> {
  console.info(`enter promise getKeyItemProperties`);
  let ret: boolean = false;
  try {
    await huks.getKeyItemProperties(keyAlias, emptyOptions)
      .then((data) => {
        console.info(`promise: getKeyItemProperties success, data is ` + Uint8ArrayToString(data.outData as Uint8Array));
        ret = true;
      }).catch((error: BusinessError) => {
        console.error(`promise: getKeyItemProperties failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error(`promise: getKeyItemProperties input arg invalid`);
  }
  return ret;
}

async function testGetKeyProperties() {
  /* 1. Generate a key. */
  let genResult = await generateKeyItem(keyAlias, huksOptions);
  /* 2. Obtain key properties. */
  if (genResult == false) {
    console.error('Key generation failed, skipping get properties');
    return;
  }

  let getResult = await getKeyItemProperties(keyAlias, emptyOptions);
  if (getResult == false) {
    console.error('getKeyItemProperties failed');
    return;
  }
  console.info(`testGetKeyProperties success}`);
}
```
