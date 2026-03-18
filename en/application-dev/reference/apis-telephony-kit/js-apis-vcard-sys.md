# @ohos.telephony.vcard (VCard) (System API)
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @Fanyl8-->
<!--Designer: @ghxbob-->
<!--Tester: @weitiantian-->
<!--Adviser: @zhang_yixin13-->

VCard is a file format standard for electronic business cards. It contains information such as names, addresses, phone numbers, URLs, logos, and photos. The VCard module provides the VCard management functions, including importing VCard files to the contact database and exporting contact data to VCard files.

>**NOTE**
>
>The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.<br>
>The APIs provided by this module are system APIs.

## Modules to Import

## VCardBuilderOptions<sup>11+</sup>

Defines the VCard information.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService

| Name        | Type  | Mandatory|    Description   |
| ------------ | ------ | ---- | ---------- |
| cardType     | [VCardType](#vcardtype11) |  No | VCard version. The default value is **VERSION_21**.    |
| charset       | string |  No | VCard encoding type. The default value is **UTF-8**.    |

## VCardType<sup>11+</sup>

Enumerates VCard versions.

**System API**: This is a system API.

**System capability**: SystemCapability.Telephony.CoreService

| Name           | Value  | Description      |
| --------------- | ---- | ---------- |
| VERSION_21 | 0 | VCard 2.1.|
| VERSION_30 | 1 | VCard 3.0.|
| VERSION_40 | 2 | VCard 4.0.|
