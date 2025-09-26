# @ohos.nfc.tag (Standard NFC Tags)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @amunra03-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->
<!--Adviser: @zhang_yixin13-->

The **tag** module provides APIs for operating and managing NFC tags. The following tag read modes are available:
<br>Background mode: The device reads the tag by using NFC without starting any application, and then searches for applications based on the tag type. If only one application is matched, the card reading page of that application will be started. If multiple applications are matched, an application selector will be started, asking the user to select an application.
<br>Foreground mode: A foreground application has priority to read the NFC tag discovered.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Declaring the NFC Tag Background Mode

To enable NFC tags to be read without starting an application, declare NFC-related attributes in the **module.json5** file.
```json
{
    "module": {
        // Other declared attributes

        "abilities": [
            {
                "skills": [
                    {
                        "actions": [
                            // Other declared actions

                            // Add the action of the NFC tag.
                            "ohos.nfc.tag.action.TAG_FOUND"
                        ],
                        "uris": [
                            {
                                "type":"tag-tech/NfcA"
                            },
                            {
                                "type":"tag-tech/IsoDep"
                            }
                            // Add other technologies if necessary.
                            // Example: NfcB, NfcF, NfcV, Ndef, MifareClassic, MifareUL, and NdefFormatable
                        ]
                    }
                ]
            }
        ],
        "requestPermissions": [
            {
                "name": "ohos.permission.NFC_TAG",
                "reason": "$string:app_name"
            }
        ]
    }
}
```
> **NOTE**<br>
>
>1. The **actions** field must contain **ohos.nfc.tag.action.TAG_FOUND** and cannot be changed.
>2. The **type** field under **uris** must start with **tag-tech/**, followed by NfcA, NfcB, NfcF, NfcV, IsoDep, Ndef, MifareClassic, MifareUL, or NdefFormatable. If there are multiple types, enter them in different lines. Incorrect settings of this field will cause a parsing failure.
>3. The **name** field under **requestPermissions** is mandatory. It must be **ohos.permission.NFC_TAG** and cannot be changed.
>4. When calling the APIs and constants of this module, use **canIUse("SystemCapability.Communication.NFC.Tag")** to check whether the device supports NFC. If the device does not support NFC, the application stability may be affected. For details, see [NFC Tag Read/Write Development](../../connectivity/nfc/nfc-tag-access-guide.md).
>5. If an error is reported while importing the tag module editor, the capabilities of a specific device model may exceed the capability set defined for the default device. To use these capabilities, configure a custom SysCap by following instructions in [SystemCapability Development](https://developer.huawei.com/consumer/en/doc/harmonyos-references/syscap).

## **Modules to Import**

```js
import { tag } from '@kit.ConnectivityKit';
```

## **tag.TagInfo**

Before a card with tags is read or written, **[TagInfo](#taginfo)** must be obtained to determine the tag technologies supported by the card. In this way, the application can invoke the correct API to communicate with the card.
```js
import { tag } from '@kit.ConnectivityKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
    onCreate(want : Want, launchParam: AbilityConstant.LaunchParam) {
        // Add other function code.

        // Initialize the want that contains the found tag by using the NFC service.
        let tagInfo : tag.TagInfo | null = null;
        try {
            tagInfo = tag.getTagInfo(want);
        } catch (error) {
            console.error("tag.getTagInfo catch error: " + error);
        }
        if (tagInfo == null) {
            console.error("no TagInfo to be created, ignore it.");
            return;
        }

        // Obtain the list of technologies that can be used for discovering tags.
        let isNfcATag =  false;
        let isIsoDepTag =  false;
        for (let i = 0; i < tagInfo.technology.length; i++) {
            if (tagInfo.technology[i] == tag.NFC_A) {
                isNfcATag = true;
            }
            if (tagInfo.technology[i] == tag.ISO_DEP) {
                isIsoDepTag = true;
            }
        // Check for other technologies, for example, NFC_B, NFC_F, NFC_V, NDEF, MIFARE_CLASSIC, MIFARE_ULTRALIGHT, and NDEF_FORMATABLE.
        }

        // Use NFC-A APIs to access the discovered tags.
        if (isNfcATag) {
            let nfcA : tag.NfcATag | null = null;
            try {
                nfcA = tag.getNfcA(tagInfo);
            } catch (error) {
                console.error("tag.getNfcA catch error: " + error);
            }
            // Code for reading or writing the discovered tag.
        }

        // Use IsoDep APIs to access the discovered tags.
        if (isIsoDepTag) {
            let isoDep : tag.IsoDepTag | null = null;
            try {
                isoDep = tag.getIsoDep(tagInfo);
            } catch (error) {
                console.error("tag.getIsoDep catch error: " + error);
            }
            // Code for reading or writing the discovered tag.
        }
        // Use the same code to process other NFC tags, including NfcA, NfcB, NfcF, NfcV, Ndef, MifareClassic, MifareUL, and NdefFormatable.
    }
}
```

## tag.getNfcATag<sup>(deprecated)</sup>

getNfcATag(tagInfo: [TagInfo](#taginfo)): [NfcATag](js-apis-nfctech.md#nfcatag)

Obtains an **NfcATag** object, which allows access to the tags that use the NFC-A technology.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [tag.getNfcA](#taggetnfca9) instead.

**System capability**: SystemCapability.Communication.NFC.Tag

**Parameters**

| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                             | **Description**          |
| ------------------------------------- | ------------------ |
| [NfcATag](js-apis-nfctech.md#nfcatag) | **NfcATag** object obtained.|

## tag.getNfcA<sup>9+</sup>

getNfcA(tagInfo: [TagInfo](#taginfo)): [NfcATag](js-apis-nfctech.md#nfcatag)

Obtains an **NfcATag** object, which allows access to the tags that use the NFC-A technology.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                             | **Description**          |
| ------------------------------------- | ------------------ |
| [NfcATag](js-apis-nfctech.md#nfcatag) | **NfcATag** object obtained.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201  | The tag running state is abnormal in the service. |

## tag.getNfcBTag<sup>(deprecated)</sup>

getNfcBTag(tagInfo: [TagInfo](#taginfo)): [NfcBTag](js-apis-nfctech.md#nfcbtag)

Obtains an **NfcBTag** object, which allows access to the tags that use the NFC-B technology.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [tag.getNfcB](#taggetnfcb9) instead.

**System capability**: SystemCapability.Communication.NFC.Tag

**Parameters**

| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                             | **Description**          |
| ------------------------------------- | ------------------ |
| [NfcBTag](js-apis-nfctech.md#nfcbtag) | **NfcBTag** object obtained.|

## tag.getNfcB<sup>9+</sup>

getNfcB(tagInfo: [TagInfo](#taginfo)): [NfcBTag](js-apis-nfctech.md#nfcbtag)

Obtains an **NfcBTag** object, which allows access to the tags that use the NFC-B technology.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                             | **Description**          |
| ------------------------------------- | ------------------ |
| [NfcBTag](js-apis-nfctech.md#nfcbtag) | **NfcBTag** object obtained.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201  | The tag running state is abnormal in the service. |

## tag.getNfcFTag<sup>(deprecated)</sup>

getNfcFTag(tagInfo: [TagInfo](#taginfo)): [NfcFTag](js-apis-nfctech.md#nfcftag)

Obtains an **NfcFTag** object, which allows access to the tags that use the NFC-F technology.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [tag.getNfcF](#taggetnfcf9) instead.

**System capability**: SystemCapability.Communication.NFC.Tag

**Parameters**

| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                             | **Description**          |
| ------------------------------------- | ------------------ |
| [NfcFTag](js-apis-nfctech.md#nfcftag) | **NfcFTag** object obtained.|

## tag.getNfcF<sup>9+</sup>

getNfcF(tagInfo: [TagInfo](#taginfo)): [NfcFTag](js-apis-nfctech.md#nfcftag)

Obtains an **NfcFTag** object, which allows access to the tags that use the NFC-F technology.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                             | **Description**          |
| ------------------------------------- | ------------------ |
| [NfcFTag](js-apis-nfctech.md#nfcftag) | **NfcFTag** object obtained.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201  | The tag running state is abnormal in the service. |

## tag.getNfcVTag<sup>(deprecated)</sup>

getNfcVTag(tagInfo: [TagInfo](#taginfo)): [NfcVTag](js-apis-nfctech.md#nfcvtag)

Obtains an **NfcVTag** object, which allows access to the tags that use the NFC-V technology.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [tag.getNfcV](#taggetnfcv9) instead.

**System capability**: SystemCapability.Communication.NFC.Tag

**Parameters**

| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                             | **Description**          |
| ------------------------------------- | ------------------ |
| [NfcVTag](js-apis-nfctech.md#nfcvtag) | **NfcVTag** object obtained.|

## tag.getNfcV<sup>9+</sup>

getNfcV(tagInfo: [TagInfo](#taginfo)): [NfcVTag](js-apis-nfctech.md#nfcvtag)

Obtains an **NfcVTag** object, which allows access to the tags that use the NFC-V technology.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                             | **Description**          |
| ------------------------------------- | ------------------ |
| [NfcVTag](js-apis-nfctech.md#nfcvtag) | **NfcVTag** object obtained.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201  | The tag running state is abnormal in the service. |

## tag.getIsoDep<sup>9+</sup>

getIsoDep(tagInfo: [TagInfo](#taginfo)): [IsoDepTag](js-apis-nfctech.md#isodeptag9 )

Obtains an **IsoDepTag** object, which allows access to the tags that use the IsoDep technology.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                                  | **Description**                                               |
| ------------------------------------------ | ------------------------------------------------------- |
| [IsoDepTag](js-apis-nfctech.md#isodeptag9) | **IsoDepTag** object obtained.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201  | The tag running state is abnormal in the service. |

## tag.getNdef<sup>9+</sup>

getNdef(tagInfo: [TagInfo](#taginfo)): [NdefTag](js-apis-nfctech.md#ndeftag9)

Obtains an **NdefTag** object, which allows access to NFC Data Exchange Format (NDEF) tags.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                              | **Description**                                           |
| -------------------------------------- | --------------------------------------------------- |
| [NdefTag](js-apis-nfctech.md#ndeftag9) | **NdefTag** object obtained.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201  | The tag running state is abnormal in the service. |

## tag.getMifareClassic<sup>9+</sup>

getMifareClassic(tagInfo: [TagInfo](#taginfo)): [MifareClassicTag](js-apis-nfctech.md#mifareclassictag9)

Obtains a **MifareClassicTag** object, which allows access to the tags that use MIFARE Classic.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                                                 | **Description**                                                               |
| --------------------------------------------------------- | ----------------------------------------------------------------------- |
| [MifareClassicTag](js-apis-nfctech.md#mifareclassictag9) | **MifareClassicTag** object obtained.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201  | The tag running state is abnormal in the service. |

## tag.getMifareUltralight<sup>9+</sup>

getMifareUltralight(tagInfo: [TagInfo](#taginfo)): [MifareUltralightTag](js-apis-nfctech.md#mifareultralighttag9)

Obtains a **MifareUltralightTag** object, which allows access to the tags that use MIFARE Ultralight.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**
| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                                                      | **Description**                                                                     |
| -------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| [MifareUltralightTag](js-apis-nfctech.md#mifareultralighttag9) | **MifareUltralightTag** object obtained.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201  | The tag running state is abnormal in the service. |

## tag.getNdefFormatable<sup>9+</sup>

getNdefFormatable(tagInfo: [TagInfo](#taginfo)): [NdefFormatableTag](js-apis-nfctech.md#ndefformatabletag9)

Obtains an **NdefFormatableTag** object, which allows access to the tags that are NDEF formattable.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**
| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| **Type**                                                 | **Description**                                                                 |
| --------------------------------------------------------- | ------------------------------------------------------------------------- |
| [NdefFormatableTag](js-apis-nfctech.md#ndefformatabletag9) | **NdefFormatableTag** object obtained.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201  | The tag running state is abnormal in the service. |

## tag.getBarcodeTag<sup>18+</sup>

getBarcodeTag(tagInfo: [TagInfo](#taginfo)): [BarcodeTag](js-apis-nfctech.md#barcodetag18)

Obtains a **BarcodeTag** object, which allows access to the tags in the BarcodeTag format.


**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 18.

**Parameters**
| Name | Type               | Mandatory| Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------- |
| tagInfo | [TagInfo](#taginfo) | Yes  | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](#taggettaginfo9).|

**Return value**

| Type                       | Description                |
| ------------------------- | ------------------ |
| [BarcodeTag](js-apis-nfctech.md#barcodetag18) | **BarcodeTag** object obtained.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message|
| ------- | -------|
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201 | The tag running state is abnormal in the service. |


## tag.getTagInfo<sup>9+</sup>

getTagInfo(want: [Want](../apis-ability-kit/js-apis-app-ability-want.md#want)): [TagInfo](#taginfo)

Obtains **TagInfo** from **Want**, which is initialized by the NFC service and contains the attributes required by **TagInfo**.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name| Type                                    | Mandatory| Description                                               |
| ------ | ---------------------------------------- | ---- | --------------------------------------------------- |
| want   | [Want](../apis-ability-kit/js-apis-app-ability-want.md#want) | Yes  | Data obtained from the parameters of the **onCreate** entry function when an ability is dispatched.|

**Return value**

| **Type**           | **Description**                                    |
| ------------------- | -------------------------------------------- |
| [TagInfo](#taginfo) | **TagInfo** object obtained.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |

## tag.registerForegroundDispatch<sup>10+</sup>

registerForegroundDispatch(elementName: [ElementName](../apis-ability-kit/js-apis-bundleManager-elementName.md), discTech: number[], callback: AsyncCallback&lt;[TagInfo](#taginfo)&gt;): void

Registers a listener for the NFC tag read event so that the tag can be preferentially dispatched to a foreground application. You can set the supported NFC tag technologies in **discTech**. The callback returns [TagInfo](#taginfo) read. This API can be called only by an application running in the foreground. It must be used with [tag.unregisterForegroundDispatch](#tagunregisterforegrounddispatch10) in pairs. The registered callback must be unregistered before the tag reading page exits the foreground or is destroyed.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name      | Type    | Mandatory| Description                                                   |
| ------------ | -------- | ---- | ------------------------------------------------------- |
| elementName   |  [ElementName](../apis-ability-kit/js-apis-bundleManager-elementName.md)   | Yes  | Information about the tag reading page of the application. It cannot be empty and must contain at least **bundleName** and **abilityName**.         |
| discTech         |  number[]   | Yes  | NFC tag technologies supported by the foreground application. It cannot be empty. At least one NFC tag technology must be specified. Each number indicates the constant value of an NFC tag technology. The tag technologies are polled based on the specified value, which contains one or more of [NFC_A](#constants), [NFC_B](#constants), [NFC_F](#constants), and [NFC_V](#constants) only.|
| callback | AsyncCallback&lt;[TagInfo](#taginfo)&gt; | Yes  | Callback used to return the tag information read. It cannot be empty.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 201  | Permission denied. |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201 | The tag running state is abnormal in the service. |
| 3100202  | The element state is invalid. |

**Example**

See the example of [tag.unregisterForegroundDispatch](#tagunregisterforegrounddispatch10).

## tag.unregisterForegroundDispatch<sup>10+</sup>

unregisterForegroundDispatch(elementName: [ElementName](../apis-ability-kit/js-apis-bundleManager-elementName.md)): void

Unregisters the listener for the NFC tag read event. If the listener is unregistered, the NFC tag discovered will not be dispatched to foreground applications. The registered callback must be unregistered before the tag reading page exits the foreground or is destroyed.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name      | Type    | Mandatory| Description                                                   |
| ------------ | -------- | ---- | ------------------------------------------------------- |
| elementName   |  [ElementName](../apis-ability-kit/js-apis-bundleManager-elementName.md)   | Yes  | Information about the tag reading page of the application. It cannot be empty and must contain at least **bundleName** and **abilityName**.          |

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 201  | Permission denied. |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201 | The tag running state is abnormal in the service. |

**Example**

```js

import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want, bundleManager } from '@kit.AbilityKit';

let discTech: number[] = [tag.NFC_A, tag.NFC_B]; // Specify the technology required for foreground ability.
let elementName : bundleManager.ElementName;
function foregroundCb(err : BusinessError, tagInfo : tag.TagInfo) {
    if (!err) {
        console.log("foreground callback: tag found tagInfo = ", JSON.stringify(tagInfo));
    } else {
        console.error("foreground callback err: " + err.message);
        return;
    }
  // Other operations on taginfo
}

export default class MainAbility extends UIAbility {
    OnCreate(want : Want, launchParam : AbilityConstant.LaunchParam) {
        console.log("OnCreate");
        elementName = {
            bundleName: want.bundleName as string,
            abilityName: want.abilityName as string,
            moduleName: want.moduleName as string
        }
    }

    onForeground() {
        console.log("onForeground");
        try {
            tag.registerForegroundDispatch(elementName, discTech, foregroundCb);
        } catch (e) {
            console.error("registerForegroundDispatch error: " + (e as BusinessError).message);
        }
    }

    onBackground() {
        console.log("onBackground");
        try {
            tag.unregisterForegroundDispatch(elementName);
        } catch (e) {
            console.error("unregisterForegroundDispatch error: " + (e as BusinessError).message);
        }
    }

    onWindowStageDestroy() {
        console.log("onWindowStageDestroy");
        try {
            tag.unregisterForegroundDispatch(elementName);
        } catch (e) {
            console.error("unregisterForegroundDispatch error: " + (e as BusinessError).message);
        }
    }

  // Other functions in the ability lifecycle
}
```

## tag.on<sup>11+</sup>

on(type: 'readerMode', elementName: [ElementName](../apis-ability-kit/js-apis-bundleManager-elementName.md), discTech: number[], callback: AsyncCallback&lt;[TagInfo](#taginfo)&gt;): void

Subscribes to the NFC tag read event to implement dispatch of the tag to a foreground application preferentially. The device enters the reader mode and disables card simulation. You can set the supported NFC tag technologies in **discTech**. The callback returns [TagInfo](#taginfo) read. This API must be used with [tag.off](#tagoff11) in pairs. If the NFC reader mode is enabled by [tag.on](#tagon11), **tag.off** must be called when the application page exits the foreground or is destroyed.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name      | Type    | Mandatory| Description                                                   |
| ------------ | -------- | ---- | ------------------------------------------------------- |
| type    | string  | Yes  | Event type, which has a fixed value of **readerMode**.|
| elementName   |  [ElementName](../apis-ability-kit/js-apis-bundleManager-elementName.md)   | Yes  | Information about the tag reading page of the application. It cannot be empty and must contain at least **bundleName** and **abilityName**.         |
| discTech         |  number[]   | Yes  | NFC tag technologies supported by the foreground application. It cannot be empty. At least one NFC tag technology must be specified. Each number indicates the constant value of an NFC tag technology. The tag technologies are polled based on the specified value, which contains one or more of [NFC_A](#constants), [NFC_B](#constants), [NFC_F](#constants), and [NFC_V](#constants) only.|
| callback | AsyncCallback&lt;[TagInfo](#taginfo)&gt; | Yes  | Callback used to return the tag information read. It cannot be empty.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 201  | Permission denied. |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201 | The tag running state is abnormal in the service. |
| 3100202  | The element state is invalid. |

**Example**

See the example of [tag.off](#tagoff11).

## tag.off<sup>11+</sup>

off(type: 'readerMode', elementName: [ElementName](../apis-ability-kit/js-apis-bundleManager-elementName.md), callback?: AsyncCallback&lt;[TagInfo](#taginfo)&gt;): void

Unsubscribes from the NFC tag card read event. The device exits the reader mode and resumes card simulation. If the NFC reader mode is enabled by [tag.on](#tagon11), this API must be used when the application page exits the foreground or is destroyed.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name      | Type    | Mandatory| Description                                                   |
| ------------ | -------- | ---- | ------------------------------------------------------- |
| type    | string  | Yes  | Event type, which has a fixed value of **readerMode**.|
| elementName   |  [ElementName](../apis-ability-kit/js-apis-bundleManager-elementName.md)   | Yes  | Information about the tag reading page of the application. It cannot be empty and must contain at least **bundleName** and **abilityName**.         |
| callback | AsyncCallback&lt;[TagInfo](#taginfo)&gt; | No  | Callback to unregister.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 201  | Permission denied. |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
| 801  | Capability not supported. |
| 3100201 | The tag running state is abnormal in the service. |
| 3100203  | The off() API can be called only when the on() has been called. |

**Example**

```js
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want, bundleManager } from '@kit.AbilityKit';

let discTech: number[] = [tag.NFC_A, tag.NFC_B]; // Specify the technology required for foreground ability.
let elementName : bundleManager.ElementName;

function readerModeCb(err : BusinessError, tagInfo : tag.TagInfo) {
    if (!err) {
        console.log("offCallback: tag found tagInfo = ", JSON.stringify(tagInfo));
    } else {
        console.error("offCallback err: " + err.message);
        return;
    }
  // Other operations on taginfo
}

export default class MainAbility extends UIAbility {
    OnCreate(want : Want, launchParam : AbilityConstant.LaunchParam) {
        console.log("OnCreate");
        elementName = {
            bundleName: want.bundleName as string,
            abilityName: want.abilityName as string,
            moduleName: want.moduleName as string
        }
    }

    onForeground() {
        console.log("on start");
        try {
            tag.on('readerMode', elementName, discTech, readerModeCb);
        } catch (e) {
            console.error("tag.on error: " + (e as BusinessError).message);
        }
    }

    onBackground() {
        console.log("onBackground");
        try {
            tag.off('readerMode', elementName, readerModeCb);
        } catch (e) {
            console.error("tag.off error: " + (e as BusinessError).message);
        }
    }

    onWindowStageDestroy() {
        console.log("onWindowStageDestroy");
        try {
            tag.off('readerMode', elementName, readerModeCb);
        } catch (e) {
            console.error("tag.off error: " + (e as BusinessError).message);
        }
    }

  // Other functions in the ability lifecycle
}
```

## tag.ndef.makeUriRecord<sup>9+</sup>

makeUriRecord(uri: string): NdefRecord

Creates an NDEF record based on the specified URI.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name| Type  | Mandatory| Description                             |
| ------ | ------ | ---- | --------------------------------- |
| uri    | string | Yes  | Data to write to the NDEF record.|

**Return value**

| **Type**                  | **Description**                                                    |
| -------------------------- | ------------------------------------------------------------ |
| [NdefRecord](#ndefrecord9) | NDEF record created. For details, see *NFCForum-TS-NDEF_1.0*.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |

**Example**

```js
import { tag } from '@kit.ConnectivityKit';

try {
    let uri = "https://www.example.com"; // Set the correct URI.
    let ndefRecord : tag.NdefRecord = tag.ndef.makeUriRecord(uri);
    if (ndefRecord != undefined) {
        console.log("ndefMessage makeUriRecord rtdType: " + ndefRecord.rtdType);
        console.log("ndefMessage makeUriRecord payload: " + ndefRecord.payload);
    } else {
        console.log("ndefMessage makeUriRecord ndefRecord: " + ndefRecord);
    }
} catch (businessError) {
    console.error("ndefMessage makeUriRecord catch businessError: " + businessError);
}
```

## tag.ndef.makeTextRecord<sup>9+</sup>

makeTextRecord(text: string, locale: string): NdefRecord

Creates an NDEF record based on the specified text data and encoding type.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name| Type  | Mandatory| Description                                 |
| ------ | ------ | ---- | ------------------------------------- |
| text   | string | Yes  | Text to write to the NDEF record.|
| locale | string | Yes  | Encoding mode of the text.             |

**Return value**

| **Type**                  | **Description**                                                    |
| -------------------------- | ------------------------------------------------------------ |
| [NdefRecord](#ndefrecord9) | NDEF record created. For details, see *NFCForum-TS-NDEF_1.0*.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |

**Example**

```js
import { tag } from '@kit.ConnectivityKit';

try {
    let text = "Hello World"; // Set the text as demanded.
    let locale = "en"; // Set the expected encoding format.
    let ndefRecord : tag.NdefRecord = tag.ndef.makeTextRecord(text, locale);
    if (ndefRecord != undefined) {
        console.log("ndefMessage makeTextRecord rtdType: " + ndefRecord.rtdType);
        console.log("ndefMessage makeTextRecord payload: " + ndefRecord.payload);
    } else {
        console.log("ndefMessage makeTextRecord ndefRecord: " + ndefRecord);
    }
} catch (businessError) {
    console.error("ndefMessage makeTextRecord catch businessError: " + businessError);
}
```

## tag.ndef.makeApplicationRecord<sup>18+</sup>

makeApplicationRecord(bundleName: string): NdefRecord

Creates an NDEF record based on the specified application bundle name.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 18.

**Parameters**

| Name| Type  | Mandatory| Description                                 |
| ------ | ------ | ---- | ------------------------------------- |
| bundleName   | string | Yes  | Application bundle name.|

**Return value**

| **Type**                  | **Description**                                                    |
| -------------------------- | ------------------------------------------------------------ |
| [NdefRecord](#ndefrecord9) | NDEF record created. For details, see *NFCForum-TS-NDEF_1.0*.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |

**Example**

```js
import { tag } from '@kit.ConnectivityKit';

try {
    let bundleName: string = 'com.demo.test';
    let ndefRecord : tag.NdefRecord = tag.ndef.makeApplicationRecord(bundleName);
    if (ndefRecord != undefined) {
        console.log("ndefMessage makeApplicationRecord rtdType: " + ndefRecord.rtdType);
        console.log("ndefMessage makeApplicationRecord payload: " + ndefRecord.payload);
    } else {
        console.log("ndefMessage makeApplicationRecord ndefRecord: " + ndefRecord);
    }
} catch (businessError) {
    console.error("ndefMessage makeApplicationRecord catch businessError: " + businessError);
}
```

## tag.ndef.makeMimeRecord<sup>9+</sup>

makeMimeRecord(mimeType: string, mimeData: number[]): NdefRecord

Creates an NDEF record based on the specified MIME data and type.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name  | Type    | Mandatory| Description                                                   |
| -------- | -------- | ---- | ------------------------------------------------------- |
| mimeType | string   | Yes  | MIME type that complies with RFC rules, for example, **text/plain** or **image/jpeg**.|
| mimeData | number[] | Yes  | MIME data, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**.|

**Return value**

| **Type**                  | **Description**                                                    |
| -------------------------- | ------------------------------------------------------------ |
| [NdefRecord](#ndefrecord9) | NDEF record created. For details, see *NFCForum-TS-NDEF_1.0*.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |

**Example**

```js
import { tag } from '@kit.ConnectivityKit';

try {
    let mimeType = "text/plain"; // Set a correct MIME type.
    let mimeData = [0x01, 0x02, 0x03, 0x04]; // Set the correct MIME data.
    let ndefRecord : tag.NdefRecord = tag.ndef.makeMimeRecord(mimeType, mimeData);
    if (ndefRecord != undefined) {
        console.log("ndefMessage makeMimeRecord rtdType: " + ndefRecord.rtdType);
        console.log("ndefMessage makeMimeRecord payload: " + ndefRecord.payload);
    } else {
        console.log("ndefMessage makeMimeRecord ndefRecord: " + ndefRecord);
    }
} catch (businessError) {
    console.error("ndefMessage makeMimeRecord catch businessError: " + businessError);
}
```
## tag.ndef.makeExternalRecord<sup>9+</sup>

makeExternalRecord(domainName: string, type: string, externalData: number[]): NdefRecord

Creates an NDEF record based on application-specific data.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name      | Type    | Mandatory| Description                                                   |
| ------------ | -------- | ---- | ------------------------------------------------------- |
| domainName   | string   | Yes  | Bundle name of the application or domain name of the organization that releases the applications.         |
| type         | string   | Yes  | Type of the application data.                                   |
| externalData | number[] | Yes  | Application data, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**.|

**Return value**

| **Type**                  | **Description**                                                    |
| -------------------------- | ------------------------------------------------------------ |
| [NdefRecord](#ndefrecord9) | NDEF record created. For details, see *NFCForum-TS-NDEF_1.0*.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |

**Example**

```js
import { tag } from '@kit.ConnectivityKit';

try {
    let domainName = "ohos.nfc.application"; // Set a correct bundle name.
    let type = "test"; // Set a correct data type.
    let externalData = [0x01, 0x02, 0x03, 0x04]; // Set the correct external data.
    let ndefRecord : tag.NdefRecord = tag.ndef.makeExternalRecord(domainName, type, externalData);
    if (ndefRecord != undefined) {
        console.log("ndefMessage makeExternalRecord rtdType: " + ndefRecord.rtdType);
        console.log("ndefMessage makeExternalRecord payload: " + ndefRecord.payload);
    } else {
        console.log("ndefMessage makeExternalRecord ndefRecord: " + ndefRecord);
    }
} catch (businessError) {
    console.error("ndefMessage makeExternalRecord catch businessError: " + businessError);
}
```

## tag.ndef.messageToBytes<sup>9+</sup>

messageToBytes(ndefMessage: [NdefMessage](js-apis-nfctech.md#ndefmessage9)): number[]

Converts an NDEF message to bytes.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name     | Type                                          | Mandatory| Description              |
| ----------- | ---------------------------------------------- | ---- | ------------------ |
| ndefMessage | [NdefMessage](js-apis-nfctech.md#ndefmessage9) | Yes  | NDEF message to convert.|

**Return value**

| **Type**| **Description**                                                                             |
| -------- | ------------------------------------------------------------------------------------- |
| number[] | NDEF message in bytes, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |

**Example**

```js
import { tag } from '@kit.ConnectivityKit';

let rawData = [0xD1, 0x01, 0x03, 0x54, 0x4E, 0x46, 0x43]; // Set the correct raw data, which is in the NDEF format.
try {
    let ndefMessage : tag.NdefMessage = tag.ndef.createNdefMessage(rawData);
    console.log("ndef createNdefMessage, ndefMessage: " + ndefMessage);
    let rawData2 : number[] = tag.ndef.messageToBytes(ndefMessage);
    console.log("ndefMessage messageToBytes rawData2: " + rawData2);
} catch (businessError) {
    console.error("ndef createNdefMessage businessError: " + businessError);
}
```
## tag.ndef.createNdefMessage<sup>9+</sup>

createNdefMessage(data: number[]): [NdefMessage](js-apis-nfctech.md#ndefmessage9)

Creates an NDEF message from raw byte data. The data must comply with the NDEF record format. Otherwise, the NDE record list contained in the **NdefMessage** object will be empty.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**                                                                          |
| ---------- | -------- | -------- | ---------------------------------------------------------------------------------- |
| data       | number[] | Yes      | Raw byte data, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**. The data must comply with the NDEF record format.|

**Return value**

| **Type**                                      | **Description**                                                     |
| ---------------------------------------------- | ------------------------------------------------------------- |
| [NdefMessage](js-apis-nfctech.md#ndefmessage9) | NDEF message created. For details, see *NFCForum-TS-NDEF_1.0*.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |

**Example**
```js
import { tag } from '@kit.ConnectivityKit';

let rawData = [0xD1, 0x01, 0x03, 0x54, 0x4E, 0x46, 0x43]; // The NDEF data must be resolvable.
try {
    let ndefMessage : tag.NdefMessage = tag.ndef.createNdefMessage(rawData);
    console.log("ndef createNdefMessage, ndefMessage: " + ndefMessage);
} catch (businessError) {
    console.error("ndef createNdefMessage businessError: " + businessError);
}
```

## tag.ndef.createNdefMessage<sup>9+</sup>

createNdefMessage(ndefRecords: NdefRecord[]): [NdefMessage](js-apis-nfctech.md#ndefmessage9)

Creates an NDEF message from the NDEF records list.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| **Name** | **Type**                                     | **Mandatory**| **Description**                                                        |
| ----------- | --------------------------------------------- | -------- | ---------------------------------------------------------------- |
| ndefRecords | [NdefRecord](js-apis-nfcTag.md#ndefrecord9)[] | Yes      | NDEF record list used to create the NDEF message. For details, see *NFCForum-TS-NDEF_1.0*.|

**Return value**

| **Type**                                      | **Description**                                                     |
| ---------------------------------------------- | ------------------------------------------------------------- |
| [NdefMessage](js-apis-nfctech.md#ndefmessage9) | NDEF message created. For details, see *NFCForum-TS-NDEF_1.0*.|

**Error codes**

For details about the error codes, see [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 401  | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |

**Example**

```js
import { tag } from '@kit.ConnectivityKit';

let uriRecord : tag.NdefRecord = tag.ndef.makeUriRecord("https://www.example.com");
let textRecord : tag.NdefRecord = tag.ndef.makeTextRecord("Hello World", "en");
let ndefRecords : tag.NdefRecord[] = [uriRecord, textRecord];
try {
    let ndefMessage : tag.NdefMessage = tag.ndef.createNdefMessage(ndefRecords);
    console.log("ndef createNdefMessage ndefMessage: " + ndefMessage);
} catch (businessError) {
    console.error("ndef createNdefMessage businessError: " + businessError);
}
```

## TagInfo

Defines the **TagInfo** object, which provides information about the tag technologies supported by a card.

**System capability**: SystemCapability.Communication.NFC.Tag

**Required permissions**: ohos.permission.NFC_TAG

| **Name**                     | **Type**                                                     | **Read-Only**| **Optional**| **Description**                                                                                    |
| ----------------------------- | ------------------------------------------------------------- | -------- | -------- | -------------------------------------------------------------------------------------------- |
| uid<sup>9+</sup>              | number[]                                                      | Yes      | No      | Tag unique identifier (UID), which consists of hexadecimal numbers ranging from **0x00** to **0xFF**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                    |
| technology<sup>9+</sup>       | number[]                                                      | Yes      | No      | Supported tag technologies. Each number is a constant indicating the supported technology.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                    |
| supportedProfiles             | number[]                                                      | Yes      | No      | Supported profiles. This parameter is not supported since API version 9. Use [tag.TagInfo#technology](#taginfo) instead.           |

## NdefRecord<sup>9+</sup>
Defines an NDEF record. For details, see *NFCForum-TS-NDEF_1.0*.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| **Name**| **Type**| **Read-Only**| **Optional**| **Description**                                                                                 |
| -------- | -------- | -------- | -------- | ----------------------------------------------------------------------------------------- |
| tnf      | number   | Yes      | No      | Type name field (TNF) of the NDEF record.                                                      |
| rtdType  | number[] | Yes      | No      | Record type definition (RTD) of the NDEF record. It consists of hexadecimal numbers ranging from **0x00** to **0xFF**.|
| id       | number[] | Yes      | No      | NDEF record ID, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**.                               |
| payload  | number[] | Yes      | No      | NDEF payload, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**.                          |

## Constants
Enumerates the tag technology types.

**System capability**: SystemCapability.Communication.NFC.Tag

| **Name**                    |**Type**| **Value**| **Description**                   |
| ---------------------------- | ------ | ------ | --------------------------- |
| NFC_A<sup>7+</sup>                        |  number | 1      | NFC-A (ISO 14443-3A).<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| NFC_B<sup>7+</sup>                        |  number | 2      | NFC-B (ISO 14443-3B).<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| ISO_DEP<sup>7+</sup>                      |  number | 3      | ISO-DEP (ISO 14443-4).<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| NFC_F<sup>7+</sup>                        |  number | 4      | NFC-F (JIS 6319-4).<br>**Atomic service API**: This API can be used in atomic services since API version 12.   |
| NFC_V<sup>7+</sup>                        |  number | 5      | NFC-V (ISO 15693).<br>**Atomic service API**: This API can be used in atomic services since API version 12.    |
| NDEF<sup>7+</sup>                         |  number | 6      | NDEF.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                 |
| NDEF_FORMATABLE<sup>9+</sup> |  number | 7      | NDEF formattable.<br>**Atomic service API**: This API can be used in atomic services since API version 12.      |
| MIFARE_CLASSIC<sup>7+</sup>               |  number | 8      | MIFARE Classic.<br>**Atomic service API**: This API can be used in atomic services since API version 12.       |
| MIFARE_ULTRALIGHT<sup>7+</sup>            |  number | 9      | MIFARE Ultralight.<br>**Atomic service API**: This API can be used in atomic services since API version 12.     |
| NFC_BARCODE<sup>18+</sup>    |  number | 10     | BARCODE technology.<br>**Atomic service API**: This API can be used in atomic services since API version 18.              |

## TnfType<sup>9+</sup>
Enumerates the TNF types. For details, see *NFCForum-TS-NDEF_1.0*.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| **Name**        | **Value**| **Description**                                        |
| ---------------- | ------ | ------------------------------------------------ |
| TNF_EMPTY        | 0x0    | Empty.                                         |
| TNF_WELL_KNOWN   | 0x1    | NFC Forum Well Known Type [NFC RTD].           |
| TNF_MEDIA        | 0x2    | Media-type as defined in RFC 2046 [RFC 2046].  |
| TNF_ABSOLUTE_URI | 0x3    | Absolute URI as defined in RFC 3986 [RFC 3986].|
| TNF_EXT_APP      | 0x4    | NFC Forum external type [NFC RTD].             |
| TNF_UNKNOWN      | 0x5    | Unknown.                                       |
| TNF_UNCHANGED    | 0x6    | Unchanged (see section 2.3.3 in *NFCForum-TS-NDEF_1.0*).                 |

## NDEF Record RTD
Enumerates the NDEF record types. For details about the RTD, see *NFCForum-TS-NDEF_1.0*.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| **Name**             |**Type**| **Value**| **Description**               |
| --------------------- | ------ | ------ | ----------------------- |
| RTD_TEXT<sup>9+</sup> |number[]| [0x54] | NDEF record of the text type.|
| RTD_URI<sup>9+</sup>  |number[]| [0x55] | NDEF record of the URI type. |

## NfcForumType<sup>9+</sup>
Enumerates the NFC Forum tag types.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| **Name**        | **Value**| **Description**            |
| ---------------- | ------ | -------------------- |
| NFC_FORUM_TYPE_1 | 1      | NFC Forum tag type 1.      |
| NFC_FORUM_TYPE_2 | 2      | NFC Forum tag type 2.      |
| NFC_FORUM_TYPE_3 | 3      | NFC Forum tag type 3.      |
| NFC_FORUM_TYPE_4 | 4      | NFC Forum tag type 4.      |
| MIFARE_CLASSIC   | 101    | MIFARE Classic.|

## MifareClassicType<sup>9+</sup>
Enumerates the MIFARE Classic tag types.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| **Name**    | **Value**| **Description**            |
| ------------ | ------ | -------------------- |
| TYPE_UNKNOWN | 0      | Unknown type.  |
| TYPE_CLASSIC | 1      | MIFARE Classic.|
| TYPE_PLUS    | 2      | MIFARE Plus.   |
| TYPE_PRO     | 3      | MIFARE Pro.    |

## MifareClassicSize<sup>9+</sup>
Enumerates the sizes of a MIFARE Classic tag.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| **Name**    | **Value**| **Description**                         |
| ------------ | ------ | --------------------------------- |
| MC_SIZE_MINI | 320    | Each tag has 5 sectors, and each sector has 4 blocks. |
| MC_SIZE_1K   | 1024   | Each tag has 16 sectors, and each sector has 4 blocks.|
| MC_SIZE_2K   | 2048   | Each tag has 32 sectors, and each sector has 4 blocks.|
| MC_SIZE_4K   | 4096   | Each tag has 40 sectors, and each sector has 4 blocks.|

## MifareUltralightType<sup>9+</sup>
Enumerates the MIFARE Ultralight tag types.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| **Name**         | **Value**| **Description**                 |
| ----------------- | ------ | ------------------------- |
| TYPE_UNKNOWN      | 0      | Unknown type.     |
| TYPE_ULTRALIGHT   | 1      | MIFARE Ultralight.  |
| TYPE_ULTRALIGHT_C | 2      | MIFARE Ultralight C.|

## NfcATag<sup>7+</sup>

type NfcATag = _NfcATag

Defines an **NfcATag** object.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_NfcATag](./js-apis-nfctech.md#nfcatag) | Object that implements access to NFC-A (ISO 15693) properties and I/O operations on a tag. |

## NfcBTag<sup>7+</sup>

type NfcBTag = _NfcBTag

Obtains an **NfcBTag** object.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_NfcBTag](./js-apis-nfctech.md#nfcbtag) | Object that implements access to NFC-B (ISO 14443-3B) properties and I/O operations on a tag. |

## NfcFTag<sup>7+</sup>

type NfcFTag = _NfcFTag

Obtains an **NfcFTag** object.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_NfcFTag](./js-apis-nfctech.md#nfcftag) | Object that implements access to NFC-F (ISO 6319-4) properties and I/O operations on a tag. |

## NfcVTag<sup>7+</sup>

type NfcVTag = _NfcVTag

Obtains an **NfcVTag** object.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_NfcVTag](./js-apis-nfctech.md#nfcvtag) | Object that implements access to NFC-V (ISO 15693) properties and I/O operations on a tag. |

## IsoDepTag<sup>9+</sup>

type IsoDepTag = _IsoDepTag

Obtains an **IsoDepTag** object.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_IsoDepTag](js-apis-nfctech.md#isodeptag9) | Object that implements access to ISO-DEP (ISO 14443-4) properties and I/O operations on a tag. |

## NdefTag<sup>9+</sup>

type NdefTag = _NdefTag

Obtains an **NdefTag** object.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_NdefTag](./js-apis-nfctech.md#ndeftag9) | Object that implements access to NDEF tags. |

## MifareClassicTag<sup>9+</sup>

type MifareClassicTag = _MifareClassicTag

Obtains a **MifareClassicTag** object.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_MifareClassicTag](./js-apis-nfctech.md#mifareclassictag9) | Object that implements access to MIFARE Classic properties and I/O operations on a tag.|

## MifareUltralightTag<sup>9+</sup>

type MifareUltralightTag = _MifareUltralightTag;

Obtains a **MifareUltralightTag** object.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_MifareUltralightTag](./js-apis-nfctech.md#mifareultralighttag9) | Object that implements access to MIFARE Ultralight properties and I/O operations on a tag.|

## NdefFormatableTag<sup>9+</sup>

type NdefFormatableTag = _NdefFormatableTag

Obtains a **NdefFormatableTag** object.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_NdefFormatableTag](js-apis-nfctech.md#ndefformatabletag9) | Object that implements formatting of NDEF formattable tags. |

## BarcodeTag<sup>18+</sup>

type BarcodeTag = _BarcodeTag

Obtains a **BarcodeTag** object.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 18.

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_BarcodeTag](./js-apis-nfctech.md#barcodetag18) | Object that implements access to the barcode tag properties and I/O operations on a tag.|

## NdefMessage<sup>9+</sup>

type NdefMessage = _NdefMessage

Obtains an **NdefMessage** object.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_NdefMessage](./js-apis-nfctech.md#ndefmessage9) | Obtains all NDEF records.|

## TagSession<sup>7+</sup>

type TagSession = _TagSession

Obtains a **TagSession** object.

**System capability**: SystemCapability.Communication.NFC.Tag

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| [_TagSession](./js-apis-tagSession.md#tagsession) | Base class of all [NFC tag technologies](js-apis-nfctech.md). It provides common APIs for establishing connections and transferring data.|
<!--no_check-->
