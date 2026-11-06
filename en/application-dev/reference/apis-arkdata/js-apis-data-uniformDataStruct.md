# @ohos.data.uniformDataStruct (Uniform Data Structs)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1fae70b72575596c0efec66316113d81f9770910 translatedAt=2026-09-04T03:58:03.284Z pushedAt=2026-09-09T09:11:03.744Z -->

As a part of the Unified Data Management Framework (UDMF), the **uniformDataStruct** module provides data structs corresponding to certain [UniformDataTypes](js-apis-data-uniformTypeDescriptor.md#uniformdatatype) for service scenarios of many-to-many data sharing across applications. It helps simplify data interaction and reduce the data type adaptation workload.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```js
import { uniformDataStruct } from '@kit.ArkData';
```

## PlainText

Plain text typed data, used to describe and manage plain text content. After a **PlainText** object is created, it can be used in data sharing scenarios such as drag-and-drop and copy-paste to implement cross-application plain text data interaction.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

| Name       | Type  | Read-Only| Optional| Description                   |
| ----------- | ------ | ---- | ---- |-----------------------|
| uniformDataType | 'general.plain-text'| Yes   | No   | The unified data type identifier is plain text typed data, fixed to "general.plain-text". For details about the data type description information, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype).                |
| textContent | string | No   | No   | Plain text content. The length limit is 20 MB. |
| abstract    | string | No   | Yes   | Plain text abstract. This is an optional field. Pass this parameter when a brief abstract needs to be provided for the text (for example, for preview, search result display, and other scenarios). If not passed, the default value is an empty string, and no abstract information is provided. |
| details | Record<string, string> | No   | Yes | Dictionary type object. Both the key and value are of the string type, used to describe the detailed attributes of the text content. This is an optional field, and the default value is an empty dictionary object. For example, a data object whose details content is<br/>**{<br/>"title":"title",<br/>"content":"content"<br/>}**<br/>can be generated. Pass this parameter when additional text attribute information needs to be stored. If not passed, the default value is an empty dictionary object, and no additional attributes are provided. |

**Example**

```ts
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

let plainTextDetails: Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2'
};
let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is plainText textContent example',
  abstract: 'this is abstract',
  details: plainTextDetails
};
console.info('plainText.uniformDataType: ' + plainText.uniformDataType);
if (plainText.details != undefined) {
  let plainTextDetailsObj: Record<string, string> = plainText.details;
  for (let kv of Object.entries(plainTextDetailsObj)) {
    console.info('plainText.details.attr: ' + kv[0] + ', value:' + kv[1]);
  }
}
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
```

## Hyperlink

Defines the hyperlink typed data, which is used to describe and manage hyperlink information. After a Hyperlink object is created, it can be used in scenarios such as drag-and-drop and sharing to implement cross-application hyperlink data transfer and redirection.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

| Name       | Type  | Read-Only| Optional| Description          |
| ----------- | ------ | ---- | ---- |--------------|
| uniformDataType | 'general.hyperlink'| Yes  | No  | Uniform data type, which has a fixed value of **general.hyperlink**. For details, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype).|
| url         | string | No   | No   | URL of the link. It supports protocols such as http and https and must conform to the standard URL format. For example, `https://www.example.com` or `file:///path/to/file`.|
| description | string | No   | Yes   | Description of the link content. This is an optional field. Pass this parameter when a text description needs to be provided for the hyperlink (for example, for accessibility, link preview, and other scenarios). If it is not passed, the default value is an empty string, and no description information is provided. |
| details | Record<string, string> | No   | Yes  | Dictionary type object whose keys and values are all of the string type. It is used to describe the detailed attribute content of Hyperlink. This is an optional field, and the default value is an empty dictionary object. For example, a data object whose details content is<br/>**{<br/>"title":"title",<br/>"content":"content"<br/>}**<br/>can be generated. Pass this parameter when additional hyperlink attribute information needs to be stored. If it is not passed, the default value is an empty dictionary object, and no additional attributes are provided. |

**Example**

```ts
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

let hyperlinkDetails: Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2'
};
let hyperlink: uniformDataStruct.Hyperlink = {
  uniformDataType: 'general.hyperlink',
  url: 'www.XXX.com',
  description: 'This is the description of this hyperlink',
  details: hyperlinkDetails
};
console.info('hyperlink.uniformDataType: ' + hyperlink.uniformDataType);
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.HYPERLINK, hyperlink);
```

## HTML

Defines the HTML typed data, which is used to describe HyperText Markup Language data. After an HTML object is created, it can be used to transfer rich text content in scenarios such as drag-and-drop and copy-paste, support cross-application HTML format data interaction, and control the URI authorization policy through **uriAuthorizationPolicies**.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

| Name        | Type  | Read-Only| Optional| Description                   |
| ------------ | ------ | ---- | ---- |-----------------------|
| uniformDataType | 'general.html'| Yes  | No  | Uniform data type, which has a fixed value of **general.html**. For details, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype).|
| htmlContent  | string | No   | No   | Content text in HTML format, supporting standard HTML tags. It can be a complete HTML document or an HTML fragment. The length limit is 20 MB. UTF-8 encoding is recommended. For example: \<div>\<p> title <\/p><\/div>. |
| plainContent | string | No   | Yes   | Plain text content after removing HTML tags. This is an optional field. Pass this parameter when a plain text version of the HTML content is required (for example, for text search, display in environments without HTML rendering, and other scenarios). If not passed, the default value is an empty string, and no plain text version is provided. |
| details | Record<string, string> | No   | Yes   | Object of dictionary type, where both the key and value are of string type, used to describe the detailed attribute content of the HTML. This is an optional field, and the default value is an empty dictionary object. For example, a data object can be generated with the details content as<br/>**{<br/>"title":"title",<br/>"content":"content"<br/>}**. |
| uriAuthorizationPolicies | Array<number\> | No | Yes | URI authorization policy for drag-and-drop scenarios. The default value is READ (read-only authorization), which takes effect only in scenarios such as the img tag. It applies only to a single record and has the highest priority. For details about the policy, see [UriPermission](js-apis-data-unifiedDataChannel.md#uripermission).<br/>**Since:** 26.0.0 |

**Example**

```ts
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

let htmlObjDetails: Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2'
};
let htmlObj: uniformDataStruct.HTML = {
  uniformDataType: 'general.html',
  htmlContent: '<div><p>title</p></div>',
  plainContent: 'this is plainContent',
  details: htmlObjDetails,
  // Starting from API version 26.0.0, URI authorization policy is supported.
  uriAuthorizationPolicies: [
    unifiedDataChannel.UriPermission.WRITE
  ]
};
console.info('htmlObj.uniformDataType: ' + htmlObj.uniformDataType);
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.HTML, htmlObj);
```

## OpenHarmonyAppItem

Represents the system-defined desktop icon typed data, which is used to share desktop icon information across applications. Typical usage scenarios include dragging icons on the home screen launcher, sharing application icons in the app store, or creating shortcuts.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

| Name       | Type  | Read-Only| Optional| Description             |
| ----------- | ------ | ---- | ---- |-----------------|
| uniformDataType | 'openharmony.app-item'| Yes  | No  | Uniform data type, which has a fixed value of **openharmony.app-item**. For details, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype).|
| appId       | string | No  | No  | ID of the application, for which the icon is used.     |
| appName     | string | No  | No  | Name of the application, for which the icon is used.      |
| appIconId   | string | No  | No  | Image ID of the icon.       |
| appLabelId  | string | No  | No  | Label ID corresponding to the icon name.   |
| bundleName  | string | No   | No   | Bundle name of the application corresponding to the icon. The format must comply with the application package name specification. |
| abilityName | string | No   | No   | Ability name of the application corresponding to the icon. It is recommended that the name follow the Ability component naming convention: a string no longer than 127 bytes that starts with a letter and can contain letters, digits, underscores (_), or periods (.). Ensure that the name is unique within the entire application. The "package name.Ability name" format is recommended (for example, **"com.example.myapplication.MainAbility"**). |
| details | Record<string, number \| string \| Uint8Array> | No   | Yes   | Dictionary type object. The key is of the string type, and the value can contain data of the number (numeric type), string (string type), or Uint8Array (binary byte array) type. This is an optional field, and the default value is an empty dictionary object.|


**Example**

```ts
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

let u8Array = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
let appItemDetails: Record<string, number | string | Uint8Array> = {
  'appItemKey1': 123,
  'appItemKey2': 'appItemValue',
  'appItemKey3': u8Array
};
let appItem: uniformDataStruct.OpenHarmonyAppItem = {
  uniformDataType: 'openharmony.app-item',
  appId: 'MyAppId',
  appName: 'MyAppName',
  appIconId: 'MyAppIconId',
  appLabelId: 'MyAppLabelId',
  bundleName: 'MyBundleName',
  abilityName: 'MyAbilityName',
  details: appItemDetails
};
console.info('appItem.uniformDataType: ' + appItem.uniformDataType);
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.OPENHARMONY_APP_ITEM, appItem);
```

## ContentForm<sup>14+</sup>

Defines the content card typed data, which is used to share content card information across applications. Typical usage scenarios include sharing article cards in news applications, sharing product cards in e-commerce applications, and sharing content previews in social applications.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

| Name        | Type  | Read-Only| Optional| Description                                                                                                                            |
|------------| ------ | ---- |----|--------------------------------------------------------------------------------------------------------------------------------|
| uniformDataType | 'general.content-form'| Yes  | No | Uniform data type, which has a fixed value of **general.content-form**.|
| title      | string | No  | No | Title of the content widget.|
| thumbData  | Uint8Array | No   | Yes  | Image data corresponding to the content card. The default value is empty.|
| description| string | No   | Yes  | Description information in the content card. The default value is an empty string.|
| appIcon    | Uint8Array | No   | Yes  | Application icon data in the content card. The default value is empty.|
| appName    | string | No   | Yes  | Application name in the content card. The default value is an empty string.|
| linkUri    | string | No   | Yes  | Redirect hyperlink corresponding to the content card, which must comply with the URI format specification. The default value is an empty string.|


**Example**

```ts
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

let thumbDataU8Array = new Uint8Array([1, 2, 3, 4, 5]);
let appIconU8Array = new Uint8Array([6, 7, 8, 9, 10]);
let contentForm: uniformDataStruct.ContentForm = {
  uniformDataType: 'general.content-form',
  title: 'MyTitle',
  thumbData: thumbDataU8Array,
  description: 'MyDescription',
  appName: 'MyAppName',
  linkUri: 'MyLinkUri',
  appIcon: appIconU8Array
};
console.info('contentForm.uniformDataType: ' + contentForm.uniformDataType);
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.CONTENT_FORM, contentForm);
```

## Form<sup>15+</sup>

Represents the system-defined card typed data, which is used to share card information across applications. Typical usage scenarios include card drag-and-drop sharing, cross-application transfer of card content, and data sharing of home screen widgets.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

| Name        | Type  | Read-Only| Optional| Description                                                                                                                            |
|------------| ------ | ---- |----|--------------------------------------------------------------------------------------------------------------------------------|
| uniformDataType | 'openharmony.form'| Yes  | No | Uniform data type, which has a fixed value of **openharmony.form**. For details, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype).|
| formId     | number | No  | No | Widget ID.|
| formName   | string | No  | No | Widget name.|
| bundleName | string | No | No | Bundle name of the card. The format must comply with the application package name specification. |
| abilityName | string | No | No | Ability name corresponding to the card. It is recommended that the name follow the Ability component naming convention: a string no longer than 127 bytes, starting with a letter and containing letters, digits, underscores (_), or periods (.). Ensure that the name is unique within the entire application. The "package name.Ability name" format is recommended (for example, "com.example.myapplication.MainAbility"). |
| module     | string | No  | No | Module to which the widget belongs.|
| details | Record<string, number \| string \| Uint8Array> | No | Yes | Dictionary type object. The key is of the string type, and the value can contain data of the number (numeric type), string (string type), or Uint8Array (binary byte array) type. This is an optional field, and the default value is an empty dictionary object. |


**Example**

```ts
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

let u8Array = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
let formDetails: Record<string, number | string | Uint8Array> = {
  'formKey1': 123,
  'formKey2': 'formValue',
  'formKey3': u8Array
};
let form: uniformDataStruct.Form = {
  uniformDataType: 'openharmony.form',
  formId: 1,
  formName: 'formName',
  bundleName: 'com.xx.app',
  abilityName: 'abilityName',
  module: 'module',
  details: formDetails
};
console.info('form.uniformDataType: ' + form.uniformDataType);
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.OPENHARMONY_FORM, form);
```

## FileUri<sup>15+</sup>

Defines the file URI typed data, which is used to describe the URI address information of a file. After a FileUri object is created, it can be used in scenarios such as file drag-and-drop and file sharing, support controlling file access permissions through uriAuthorizationPolicies, and implement cross-application file data transfer and permission management.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

| Name        | Type  | Read-Only| Optional| Description                                                                                                                            |
|------------| ------ | ---- |----|--------------------------------------------------------------------------------------------------------------------------------|
| uniformDataType | 'general.file-uri'| Yes  | No | Uniform data type, which has a fixed value of **general.file-uri**. For details, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype).|
| oriUri     | string | No   | No  | Original URI path of the file. Supports local file absolute paths, the file:// protocol, and http/https network URL formats. The length limit is 4096 bytes. For example: `/data/local/tmp/test.txt`, `file:///data/local/tmp/test.txt`, or `http://example.com/file.txt`.|
| fileType   | string | No   | No  | The file type must be a standardized data type (that is, the UTD-ID corresponding to each type in the [UTD preset list](../../database/uniform-data-type-list.md) or a custom UTD-ID). The maximum length limit of fileType is 1024 bytes. An exception is thrown when the limit is exceeded.|
| details | Record<string, number \| string \| Uint8Array> | No   | Yes   | Dictionary type object. The key is of the string type, and the value can contain data of the number (numeric type), string (string type), or Uint8Array (binary byte array) type. This is an optional field, and the default value is an empty dictionary object.|
| uriAuthorizationPolicies | Array<number\> | No | Yes | URI authorization policy used in drag-and-drop scenarios. The default value is **READ+WRITE+PERSIST** (read + write + persistent authorization). It applies only to a single record and has the highest priority. For details about the policies, see [UriPermission](js-apis-data-unifiedDataChannel.md#uripermission).<br/>**Since:** 26.0.0|


**Example**

```ts
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

let u8Array = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
let fileUriDetails: Record<string, number | string | Uint8Array> = {
  'fileUriKey1': 123,
  'fileUriKey2': 'fileUriValue',
  'fileUriKey3': u8Array
};
let fileUri: uniformDataStruct.FileUri = {
  uniformDataType: 'general.file-uri',
  oriUri: 'www.xx.com',
  fileType: 'general.image',
  details: fileUriDetails,
  // Starting from API version 26.0.0, the URI authorization policy is supported.
  uriAuthorizationPolicies: [
    unifiedDataChannel.UriPermission.WRITE
  ]
};
console.info('fileUri.uniformDataType: ' + fileUri.uniformDataType);
// You are advised to set type to uniformTypeDescriptor.UniformDataType.FILE_URI to use the uniform data struct of FileUri type to construct records.
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.FILE_URI, fileUri);
```

## PixelMap<sup>15+</sup>

Represents the system-defined pixel map typed data, used to describe image pixel data. After a PixelMap object is created, it can be used in scenarios such as image drag-and-drop and image sharing to implement cross-application image data transfer.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

| Name        | Type  | Read-Only| Optional| Description                                                                                                                            |
|------------| ------ | ---- |----|--------------------------------------------------------------------------------------------------------------------------------|
| uniformDataType | 'openharmony.pixel-map'| Yes   | No  | Unified data type identifier of the pixel map typed data, fixed to "openharmony.pixel-map". For details about the data type description information, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype). |
| pixelMap     | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No   | No  | Pixel map object. |
| details | Record<string, number \| string \| Uint8Array> | No   | Yes   | Dictionary type object. The key is of the string type, and the value can contain data of the number (numeric type), string (string type), or Uint8Array (binary byte array) type. This is an optional field, and the default value is an empty dictionary object.|


**Example**

```ts
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

let u8Array = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
let arrayBuffer = new ArrayBuffer(4 * 200 * 200);
let opt: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: { height: 200, width: 200 },
  alphaType: 3
};
let pixelMapDetails: Record<string, number | string | Uint8Array> = {
  'pixelMapKey1': 123,
  'pixelMapKey2': 'pixelMapValue',
  'pixelMapKey3': u8Array
};
let pixelMap: uniformDataStruct.PixelMap = {
  uniformDataType: 'openharmony.pixel-map',
  pixelMap: image.createPixelMapSync(arrayBuffer, opt),
  details: pixelMapDetails
};
console.info('pixelMap.uniformDataType: ' + pixelMap.uniformDataType);
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.OPENHARMONY_PIXEL_MAP, pixelMap);
```