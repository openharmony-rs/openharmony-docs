# @ohos.data.unifiedDataChannel (Unified Data Channel)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=ecdf029dccf124090b32e9e3826719b2cbec1cee translatedAt=2026-09-04T03:57:02.636Z pushedAt=2026-09-09T09:11:03.736Z -->

This module is a part of the Unified Data Management Framework (UDMF). It provides a standardized data channel for various many-to-many cross-application data sharing scenarios, and offers standardized data access and read APIs. It also provides standardized definitions for data types such as text and images, facilitating data exchange between different applications and reducing the workload of data type adaptation.

**Design logic:** UDMF adopts a unified data model, encapsulating different types of data into UnifiedData objects. It identifies different data channel types (such as DATA_HUB and DRAG) through Intention to implement cross-application data sharing. A unique identifier key is generated when data is written, and data is queried by key or intention when read.

When processing data, UDMF does not parse the content of user data, and the storage path has low security. Therefore, it is not recommended to transmit sensitive personal data or private data.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { unifiedDataChannel } from '@kit.ArkData';
```

## ShareOptions<sup>12+</sup>

Enumerates the usage scope types supported by UDMF within a device.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name       | Value | Description                                      |
|------------|-------|--------------------------------------------------|
| IN_APP     | 0     | Indicates that the data can be used within the same application on this device. |
| CROSS_APP  | 1     | Indicates that the data can be used across applications on this device. |

## GetDelayData<sup>12+</sup>

type GetDelayData = (type: string) => UnifiedData

A deferred wrapper for UnifiedData that supports deferred data retrieval. When the data receiver requests a specific type of data, the system triggers this callback, and the data sender can dynamically generate the data in the callback instead of preparing all data in advance. Currently, only the same-device clipboard scenario is supported.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| type | string | Yes | Identifier of the deferred data type, used to distinguish different types of data. For the values, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype). For example, 'general.plain-text' indicates the plain text type. |

**Return value**

| Type                                     | Description                      |
| ---------------------------------------- |-------------------------|
| [UnifiedData](#unifieddata) | UnifiedData object that contains the data of the corresponding type and is returned when the deferred callback is triggered. It can be used for cross-application data sharing and transfer. |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let getDelayData: unifiedDataChannel.GetDelayData = ((type: string) => {
  if (type == uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) {
    let plainTextDetails: Record<string, string> = {
      'attr1': 'value1',
      'attr2': 'value2'
    };
    let plainText: uniformDataStruct.PlainText = {
      uniformDataType: 'general.plain-text',
      textContent: 'This is a plain text example',
      abstract: 'This is abstract',
      details: plainTextDetails
    };
    let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
    let textData = new unifiedDataChannel.UnifiedData(text);
    return textData;
  }
  return new unifiedDataChannel.UnifiedData();
});
```

## ValueType<sup>12+</sup>

type ValueType = number | string | boolean | image.PixelMap | Want | ArrayBuffer | object | null | undefined

Represents the data field types allowed for a unified data record.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Type | Description |
| -------- | -------- |
| number | The number type. |
| string | The string type. |
| boolean | The boolean type. |
| image.PixelMap | The [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) type. |
| Want | The [Want](../apis-ability-kit/js-apis-app-ability-want.md) type. |
| ArrayBuffer | The ArrayBuffer type. |
| object | The object type. |
| null | Null. |
| undefined | Undefined. |

## UriPermission

URI authorization policy in drag-and-drop scenarios.

>**NOTE**
>
>This authorization policy takes effect only in drag-and-drop scenarios and does not take effect in other scenarios.

**Implementation mechanism** During drag-and-drop data transfer, the system grants temporary authorization to the target URI based on the UriPermission configuration. The authorization lifecycle is bound to the drag-and-drop session, and the temporary authorization is automatically cleared after the drag-and-drop is complete. When the receiving application accesses the URI, the system verifies the permission configuration to determine whether access is allowed. The PERSIST permission converts the temporary authorization into persistent authorization.

Four permission policies are supported: no authorization, read, write, and persist. They can be used in combination, and only the following combinations take effect:
- NONE only: no file authorization is granted.
- READ only: only one-time read-only authorization is granted.
- WRITE only: one-time read and write authorization is granted (write authorization includes read authorization).
- READ+WRITE: one-time read and write authorization is granted, with the same effect as using WRITE only.
- READ+PERSIST: persistent read authorization is granted.
- WRITE+PERSIST: grants persistent read and write authorization.
- READ+WRITE+PERSIST: grants persistent read and write authorization.

Rules for applying the drag-and-drop authorization policy (in descending order of priority):
- Single data level: The FileUri and HTML Unified Data Structures (UDS) and the File, Image, Video, Audio, Folder, and HTML Unified Data Content (UDC) structures support configuring authorization policy parameters, which take effect only for a single record at a time and have the highest priority.
- UnifiedData level: The authorization parameters provided in UnifiedDataProperties take effect for a single drag-and-drop operation. If an authorization policy is configured for a piece of data, the configuration of that data takes precedence, with the next highest priority.
- Default level: If no authorization policy is configured for either a single piece of data or UnifiedDataProperties, proxy authorization is performed according to the default drag-and-drop logic. The default logic is as follows:

    - FileUri data (FileUri UDS or the File, Image, Video, Audio, and Folder UDC types): In the drag-and-drop scenario, the default authorization is READ+WRITE+PERSIST (read + write + persistent authorization).
    - HTML data: read authorization is granted only for the URIs under the img tag in the HTML text.

**Since**: 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Value | Description |
| ------------ | --- | ------------------------------------------- |
| NONE | 0 | No permission is granted. |
| READ | 1 | Permission to read or view data. |
| WRITE | 2 | Permission to modify data (including READ). |
| PERSIST | 3 | Permission to persist files. |

## UnifiedDataProperties<sup>12+</sup>

Defines the properties of all data records in a unified data object, including the timestamp, tag, paste scope, and some additional data.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| extras | Record<string, object> | No | Yes | A dictionary object used to set additional property data. This is an optional field, and the default value is an empty dictionary object.<br/>**Atomic service API:** Since API version 12, this API is supported in atomic services. |
| tag | string | No | Yes | User-defined tag. This is an optional field, and the default value is an empty string.<br/>**Atomic service API:** Since API version 12, this API is supported in atomic services. |
| timestamp | Date | Yes | Yes | Timestamp when the [UnifiedData](#unifieddata) is generated. The default value is January 1, 1970 (UTC).<br/>**Atomic service API:** Since API version 12, this API is supported in atomic services. |
| shareOptions | [ShareOptions](#shareoptions12) | No | Yes | Indicates the usage scope of the [UnifiedData](#unifieddata) within a device. This is an optional field, and the default value is CROSS_APP.<br/>**Atomic service API:** Since API version 12, this API is supported in atomic services. |
| getDelayData | [GetDelayData](#getdelaydata12) | No | Yes | Callback for delayed data retrieval. Currently, this callback is supported only in the same-device clipboard scenario and is triggered when a user reads data from the clipboard. This is an optional field, and the default value is undefined.<br/>**Atomic service API:** Since API version 12, this API is supported in atomic services. |
| uriAuthorizationPolicies | Array<[UriPermission](#uripermission)> | No | Yes | URI authorization policies for the drag-and-drop scenario. The default value is READ+WRITE+PERSIST. This field takes effect only for a single data operation and has a lower priority. For details about the policies, see [UriPermission](#uripermission).<br/>**Since:** 26.0.0<br/>**Atomic service API:** Since API version 26.0.0, this API is supported in atomic services. |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let properties = new unifiedDataChannel.UnifiedDataProperties();
properties.extras = {
  key: {
    title: 'MyTitle',
    content: 'MyContent'
  }
};
properties.tag = "This is a tag of properties";
properties.shareOptions = unifiedDataChannel.ShareOptions.CROSS_APP;
// Support the URI authorization policy since API version 26.0.0.
properties.uriAuthorizationPolicies = [
  unifiedDataChannel.UriPermission.WRITE
];
properties.getDelayData = ((type: string) => {
  if (type == uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) {
    let plainTextDetails: Record<string, string> = {
      'attr1': 'value1',
      'attr2': 'value2'
    };
    let plainText: uniformDataStruct.PlainText = {
      uniformDataType: 'general.plain-text',
      textContent: 'This is a plain text example',
      abstract: 'This is abstract',
      details: plainTextDetails
    };
    let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
    let textData = new unifiedDataChannel.UnifiedData(text);
    return textData;
  }
  return new unifiedDataChannel.UnifiedData();
});
```

## UnifiedData

Represents the Unified Data Object of UDMF, which provides methods to encapsulate a group of data records.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

### Properties

| Name | Type | Read-only | Optional | Description                                                                                              |
| -------- | -------- | -------- | -------- |-------------------------------------------------------------------------------------------------|
| properties<sup>12+</sup> | [UnifiedDataProperties](#unifieddataproperties12) | No | No | Properties of all data records in the current unified data object, including the timestamp, tag, paste scope, and some additional data.<br/>**Atomic service API:** This API is supported in atomic services since API version 12. |

### constructor<sup>12+</sup>

constructor()

Creates a unified data object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Example**

```ts
let unifiedData = new unifiedDataChannel.UnifiedData();
```

### constructor

constructor(record: UnifiedRecord)

Creates a unified data object that contains a data record. After the call is successful, a UnifiedData object containing the specified data record is returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name | Type                            | Mandatory | Description                                      |
| ------ | ------------------------------- | ---- |-----------------------------------------|
| record | [UnifiedRecord](#unifiedrecord) | Yes   | Data record to add to the unified data object. The record is a UnifiedRecord object or an object of its subclass. |

**Error Codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.  |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
let plainText : uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent : 'This is a plain text example',
  abstract : 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);
```

### addRecord

addRecord(record: UnifiedRecord): void

Adds a data record to the current unified data object. After the call is successful, the specified data record is added to the current unified data object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name | Type                            | Mandatory | Description                                          |
| ------ | ------------------------------- | ---- |---------------------------------------------|
| record | [UnifiedRecord](#unifiedrecord) | Yes   | Data record to add to the unified data object. The record is a UnifiedRecord object or an object of its subclass.|

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.  |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  abstract: 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);

let hyperlink: uniformDataStruct.Hyperlink = {
  uniformDataType: 'general.hyperlink',
  url: 'www.XXX.com',
  description: 'This is the description of the hyperlink'
};
let link = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.HYPERLINK, hyperlink);
unifiedData.addRecord(link);
```

### getRecords

getRecords(): Array\<UnifiedRecord\>

Obtains all data records in the current unified data object. The data obtained through this API is of the UnifiedRecord type. You need to obtain the data type through [getType](#gettype) and then convert it to a subclass before use.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Return value**

| Type                                     | Description                      |
| ---------------------------------------- |-------------------------|
| Array\<[UnifiedRecord](#unifiedrecord)\> | Array of all data records contained in the current unified data object. Each record can be converted to a specific subclass after its type is obtained through getType, for reading and processing various types of data in the unified data. |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  abstract: 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);

let hyperlink: uniformDataStruct.Hyperlink = {
  uniformDataType: 'general.hyperlink',
  url: 'www.XXX.com',
  description: 'This is the description of the hyperlink'
};
let link = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.HYPERLINK, hyperlink);
unifiedData.addRecord(link);

let records = unifiedData.getRecords();
for (let i = 0; i < records.length; i++) {
  let record = records[i];
  let types = record.getTypes();
  if (types.includes(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT)) {
    let plainText = record.getEntry(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) as unifiedDataChannel.PlainText;
    console.info(`textContent: ${plainText.textContent}`);
  } else if (types.includes(uniformTypeDescriptor.UniformDataType.HYPERLINK)) {
    let hyperlink = record.getEntry(uniformTypeDescriptor.UniformDataType.HYPERLINK) as unifiedDataChannel.Hyperlink;
    console.info(`linkUrl: ${hyperlink.url}`);
  }
}
```

### hasType<sup>12+</sup>

hasType(type: string): boolean

Checks whether the current unified data object contains the specified data type. The check scope includes the data types added by using [addEntry](#addentry15).

For file types, if the type set of the UnifiedData object contains "general.jpeg", the result is true when hasType is called to check whether the type "general.image" is included (the type "general.jpeg" belongs to the type "general.image").

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name | Type                            | Mandatory | Description                                          |
| ------ | ------------------------------- | ---- |---------------------------------------------|
| type | string | Yes   | Data type to query. For details, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype). |

**Return value**

| Type                                     | Description                      |
| ---------------------------------------- |-------------------------|
| boolean | Returns true if the specified data type exists; returns false otherwise. |

**Error Code**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.  |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  abstract: 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);

let hyperlink: uniformDataStruct.Hyperlink = {
  uniformDataType: 'general.hyperlink',
  url: 'www.XXX.com',
  description: 'This is the description of the hyperlink'
};
let link = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.HYPERLINK, hyperlink);
unifiedData.addRecord(link);

let hasPlainText = unifiedData.hasType(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT);
let hasLink = unifiedData.hasType(uniformTypeDescriptor.UniformDataType.HYPERLINK);
```

### getTypes<sup>12+</sup>

getTypes(): Array\<string\>

Obtains the types of all data records in the current unified data object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Return value**

| Type                                     | Description                      |
| ---------------------------------------- |-------------------------|
| Array\<string\> | Array of [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype), which represents the set of data types of the current records. The element values include 'general.plain-text', 'general.hyperlink', 'openharmony.form', and so on. |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  abstract: 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);

let hyperlink: uniformDataStruct.Hyperlink = {
  uniformDataType: 'general.hyperlink',
  url: 'www.XXX.com',
  description: 'This is the description of the hyperlink'
};
let link = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.HYPERLINK, hyperlink);
unifiedData.addRecord(link);

let types = unifiedData.getTypes();
```

## Summary

Describes the data summary of a unified data object, including the data type and size.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| summary   | Record<string, number> | No | No | A dictionary object whose key indicates the data type (see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype)) and whose value is the total size (in bytes) of the records of that type in the unified data object.<br/>**Atomic service API:** This API can be used in atomic services since API version 11. |
| totalSize | number | No | No | Total size (in bytes) of the records in the unified data object.<br/>**Atomic service API:** This API can be used in atomic services since API version 11. |
| overview<sup>22+</sup>   | Record<string, number> | Yes | No | Mapping between all data types in the unified data object and the sizes of the records of each type, where the data size is in bytes. When the obtained unified data object is empty, the value of this overview attribute is empty.<br/>**Atomic service API:** This API can be used in atomic services since API version 22. |

**Example**

```ts
function parseSummary(summary: unifiedDataChannel.Summary) {
  let summaryRecord = summary.summary as Record<string, number>;
  if (summaryRecord) {
    for (let item of Object.entries(summaryRecord)) {
      if (item && item.length <= 1) {
        continue;
      }
      let summaryStr: string = String(item[1]);
      let info: string[] = summaryStr.split(",");
      if (info.length <= 1) {
        continue;
      }
      let key: string = info[0];
      let value: string = info[1];
    }
  }
  let overviewRecord = summary.overview as Record<string, number>;
  let totalSize = summary.totalSize;
}
```

## UnifiedRecord

An abstract definition of the data content supported by UDMF, called a data record. A unified data object contains one or more data records, for example, a text record, an image record, and an HTML record. Since API version 15, different data formats of the same content can be added to a data record (for example, the same text can be stored in plain text, HTML, or hyperlink formats at the same time). Data consumers can obtain the corresponding format through the getEntry method based on their service requirements.

### constructor<sup>12+</sup>

constructor()

Creates a data record. After the call is successful, an empty UnifiedRecord object is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Example**

```ts
let unifiedRecord = new unifiedDataChannel.UnifiedRecord();
```

### constructor<sup>12+</sup>

constructor(type: string, value: ValueType)

Creates a data record of the specified type and value. After the call is successful, a UnifiedRecord object containing the specified type and value is returned.<br/>When the parameter **value** is of the [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) type, the parameter **type** must correspond to the value of OPENHARMONY_PIXEL_MAP in [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype).<br/>When the parameter **value** is of the [Want](../apis-ability-kit/js-apis-app-ability-want.md) type, the parameter **type** must correspond to the value of OPENHARMONY_WANT in [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name | Type                            | Mandatory | Description                                      |
| ------ | ------------------------------- | ---- |-----------------------------------------|
| type | string | Yes | Type of the data record to create, used to identify the specific type of the data record. For details about the values, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype), for example, 'general.plain-text' and 'general.hyperlink'. |
| value | [ValueType](#valuetype12) | Yes   | Value of the data record to create. |

**Error Codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.  |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

let hyperlink: uniformDataStruct.Hyperlink = {
  uniformDataType: 'general.hyperlink',
  url: 'www.XXX.com',
  description: 'This is the description of the hyperlink'
};
let hyperlinkRecord = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.HYPERLINK, hyperlink);

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  abstract: 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);

let arrayBuffer = new ArrayBuffer(4 * 200 * 200);
let opt: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: { height: 200, width: 200 },
  alphaType: 3
};
let pixelMap: uniformDataStruct.PixelMap = {
  uniformDataType: 'openharmony.pixel-map',
  pixelMap: image.createPixelMapSync(arrayBuffer, opt)
};
let pixelMapRecord =
  new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.OPENHARMONY_PIXEL_MAP, pixelMap);
```

### getType

getType(): string

Obtains the type of the current data record. Since the data obtained by calling [getRecords](#getrecords) from a unified data object is a UnifiedRecord object, you need to use this API to query the specific type of the record, and then convert the UnifiedRecord object to its subclass and call the subclass APIs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Return value**

| Type   | Description                                                   |
| ------ |------------------------------------------------------|
| string | Specific data type corresponding to the current data record. For details, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype).|

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  abstract: 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);

let records = unifiedData.getRecords();
if (records[0].getType() == uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) {
  let plainText = records[0] as unifiedDataChannel.PlainText;
  console.info(`textContent: ${plainText.textContent}`);
}
```

### getValue<sup>12+</sup>

getValue(): ValueType

Obtains the value of the current data record.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Return value**

| Type   | Description                                                   |
| ------ |------------------------------------------------------|
| [ValueType](#valuetype12) | Value corresponding to the current data record. |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let text =
  new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, 'this is value of text');
let value = text.getValue();

let hyperlinkDetails: Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2'
};
let hyperlink: uniformDataStruct.Hyperlink = {
  uniformDataType: 'general.hyperlink',
  url: 'www.XXX.com',
  description: 'This is the description of the hyperlink',
  details: hyperlinkDetails
};
let hyperlinkRecord = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.HYPERLINK, hyperlink);
let hyperlinkValue = hyperlinkRecord.getValue();
```

### addEntry<sup>15+</sup>

addEntry(type: string, value: ValueType): void

Adds a data entry with the specified data type and content to the current data record. The data type and content added through this method are different representations of the same content. After the call is successful, the specified data type and content are added to the current data record.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name | Type                            | Mandatory | Description                                      |
| ------ | ------------------------------- | ---- |-----------------------------------------|
| type | string | Yes   | Data type to create. For details, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype). |
| value | [ValueType](#valuetype12) | Yes | Value of the data to create. |

**Error Code**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.  |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let fileUriDetails: Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2'
};
let fileUri: uniformDataStruct.FileUri = {
  uniformDataType: 'general.file-uri',
  oriUri: 'file://data/image/1.png',
  fileType: 'general.image',
  details: fileUriDetails
};
let hyperlink: uniformDataStruct.Hyperlink = {
  uniformDataType: 'general.hyperlink',
  url: 'file://data/image/1.png',
  description: 'This is the description of the hyperlink'
};

let unifiedData = new unifiedDataChannel.UnifiedData();
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.HYPERLINK, hyperlink);
record.addEntry(uniformTypeDescriptor.UniformDataType.FILE_URI, fileUri);
unifiedData.addRecord(record);
```

### getEntry<sup>15+</sup>

getEntry(type: string): ValueType

Obtains the data content in a data record by data type.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name | Type                            | Mandatory | Description                                      |
| ------ | ------------------------------- | ---- |-----------------------------------------|
| type | string | Yes | Type of the data to obtain. For details, see [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype). |

**Return value**

| Type   | Description                                                   |
| ------ |------------------------------------------------------|
| [ValueType](#valuetype12) | Value corresponding to the current data record. |

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.  |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let fileUriDetails: Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2'
};
let fileUri: uniformDataStruct.FileUri = {
  uniformDataType: 'general.file-uri',
  oriUri: 'file://data/image/1.png',
  fileType: 'general.image',
  details: fileUriDetails
};
let formDetails: Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2'
};
let form: uniformDataStruct.Form = {
  uniformDataType: 'openharmony.form',
  formId: 1,
  formName: 'form',
  bundleName: 'com.xx.app',
  abilityName: 'ability',
  module: 'module',
  details: formDetails
};

let unifiedData = new unifiedDataChannel.UnifiedData();
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.OPENHARMONY_FORM, form);
record.addEntry(uniformTypeDescriptor.UniformDataType.FILE_URI, fileUri);
unifiedData.addRecord(record);

let records = unifiedData.getRecords();
for (let i = 0; i < records.length; i++) {
  let unifiedDataRecord = records[i] as unifiedDataChannel.UnifiedRecord;
  let fileUriRead: uniformDataStruct.FileUri =
    unifiedDataRecord.getEntry(uniformTypeDescriptor.UniformDataType.FILE_URI) as uniformDataStruct.FileUri;
  if (fileUriRead != undefined) {
    console.info(`oriUri: ${fileUriRead.oriUri}`);
  }
  let formRead =
    unifiedDataRecord.getEntry(uniformTypeDescriptor.UniformDataType.OPENHARMONY_FORM) as uniformDataStruct.Form;
  if (formRead != undefined) {
    console.info(`formName: ${formRead.formName}`);
  }
}
```

### getEntries<sup>15+</sup>

getEntries(): Record<string, ValueType>

Obtains the types and contents of all data in the current data record.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Return value**

| Type   | Description                                                   |
| ------ |------------------------------------------------------|
| Record<string, [ValueType](#valuetype12)> | Types and contents corresponding to the current data record. |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let fileUriDetails : Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2'
};
let fileUri : uniformDataStruct.FileUri = {
  uniformDataType : 'general.file-uri',
  oriUri : 'file://data/image/1.png',
  fileType : 'general.image',
  details : fileUriDetails
};
let formDetails : Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2'
};
let form : uniformDataStruct.Form = {
  uniformDataType : 'openharmony.form',
  formId : 1,
  formName : 'form',
  bundleName : 'com.xx.app',
  abilityName : 'ability',
  module : 'module',
  details : formDetails
};

let unifiedData = new unifiedDataChannel.UnifiedData();
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.OPENHARMONY_FORM, form);
record.addEntry(uniformTypeDescriptor.UniformDataType.FILE_URI, fileUri);
unifiedData.addRecord(record);

let records = unifiedData.getRecords();
for (let i = 0; i < records.length; i++) {
  let unifiedDataRecord = records[i] as unifiedDataChannel.UnifiedRecord;
  let entries : Record<string, unifiedDataChannel.ValueType> = unifiedDataRecord.getEntries();
  let formRead : uniformDataStruct.Form = entries[uniformTypeDescriptor.UniformDataType.OPENHARMONY_FORM] as uniformDataStruct.Form;
  if (formRead != undefined) {
    console.info(`formName: ${formRead.formName}`);
  }
  let fileUriRead : uniformDataStruct.FileUri = entries[uniformTypeDescriptor.UniformDataType.FILE_URI] as uniformDataStruct.FileUri;
  if (fileUriRead != undefined) {
    console.info(`oriUri: ${fileUriRead.oriUri}`);
  }
}
```

### getTypes<sup>15+</sup>

getTypes(): Array\<string\>

Obtains the set of all data types in the data record. This API can be called through a UnifiedRecord data record object to query the set of all data types in the record, including the data types added by using the [addEntry](#addentry15) function.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Return value**

| Type                                     | Description                      |
| ---------------------------------------- |-------------------------|
| Array\<string\> | Array of [UniformDataType](js-apis-data-uniformTypeDescriptor.md#uniformdatatype) objects, indicating the data types corresponding to all data records in the current unified data object. The element values are such as 'general.plain-text', 'general.hyperlink', and 'general.html'. |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let fileUriDetails: Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2'
};
let fileUri: uniformDataStruct.FileUri = {
  uniformDataType: 'general.file-uri',
  oriUri: 'file://data/image/1.png',
  fileType: 'general.image',
  details: fileUriDetails
};
let formDetails: Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2'
};
let form: uniformDataStruct.Form = {
  uniformDataType: 'openharmony.form',
  formId: 1,
  formName: 'form',
  bundleName: 'com.xx.app',
  abilityName: 'ability',
  module: 'module',
  details: formDetails
};

let unifiedData = new unifiedDataChannel.UnifiedData();
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.OPENHARMONY_FORM, form);
record.addEntry(uniformTypeDescriptor.UniformDataType.FILE_URI, fileUri);
unifiedData.addRecord(record);

let records = unifiedData.getRecords();
for (let i = 0; i < records.length; i++) {
  let unifiedDataRecord = records[i] as unifiedDataChannel.UnifiedRecord;
  let types: Array<string> = unifiedDataRecord.getTypes();
  if (types.includes(uniformTypeDescriptor.UniformDataType.OPENHARMONY_FORM)) {
    console.info(`Types include: ${uniformTypeDescriptor.UniformDataType.OPENHARMONY_FORM}`);
  }
};
```

## Text

Represents text data. It is a subclass of [UnifiedRecord](#unifiedrecord) and the base class of text data, used to describe text data. You are advised to use subclasses of Text, such as [PlainText](#plaintext), [Hyperlink](#hyperlink), and [HTML](#html), to describe data.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| details | Record<string, string> | No | Yes | A dictionary object whose keys and values are both strings, used to describe the text content. For example, you can create a data object whose details are<br/>{<br/>"title":"Title",<br/>"content":"Content"<br/>}<br/>to describe an article. This is an optional field, and the default value is an empty dictionary object. |

**Example**

```ts
let text = new unifiedDataChannel.Text();
text.details = {
  title: 'MyTitle',
  content: 'This is content'
};
let unifiedData = new unifiedDataChannel.UnifiedData(text);
```

## PlainText

A subclass of [Text](#text) that describes plain text data.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| textContent | string | No | No | Plain text content.                |
| abstract    | string | No | Yes | Plain text abstract. This is an optional field, and the default value is an empty string. |

**Example**

```ts
let text = new unifiedDataChannel.PlainText();
text.textContent = 'this is textContent';
text.abstract = 'This is abstract';
```

## Hyperlink

A subclass of [Text](#text) that describes hyperlink data.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| url         | string | No | No | URL of the link.       |
| description | string | No | Yes | Description of the link content. This is an optional field, and the default value is an empty string. |

**Example**

```ts
let link = new unifiedDataChannel.Hyperlink();
link.url = 'www.XXX.com';
link.description = 'This is description';
```

## HTML

The HTML type data, a subclass of [Text](#text), is used to describe HyperText Markup Language data.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| htmlContent  | string | No | No | Content in HTML format.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services.             |
| plainContent | string | No | Yes | Plain text content after HTML tags are removed. This is an optional field, and the default value is an empty string.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| uriAuthorizationPolicies | Array<[UriPermission](#uripermission)> | No | Yes | URI authorization policy used in drag-and-drop scenarios. The default value is READ (read-only authorization), which takes effect only in scenarios such as the img tag. It applies only to a single record and has the highest priority. For details about the policies, see [UriPermission](#uripermission).<br/>**Since:** 26.0.0<br/>**Atomic service API:** Since API version 26.0.0, this API is supported in atomic services. |

**Example**

```ts
let html = new unifiedDataChannel.HTML();
html.htmlContent = '<div><p>Title</p></div>';
html.plainContent = 'This is plainContent';
// Support the URI authorization policy since API version 26.0.0.
html.uriAuthorizationPolicies = [
  unifiedDataChannel.UriPermission.WRITE
];
```

## File

The File type data is a subclass of [UnifiedRecord](#unifiedrecord) and the base class of file type data. It is used to describe file type data. You are advised to use subclasses of File, such as [Image](#image), [Video](#video), and [Folder](#folder), to describe data.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| details | Record<string, string> | No | Yes | A dictionary object whose keys and values are both of the string type. It is used to describe file-related information. For example, you can create a data object with the following details to describe a file:<br/>{<br/>"name":"file name",<br/>"type":"file type"<br/>}. This is an optional field, and the default value is an empty dictionary object.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| uri     | string                    | No | No | URI of a local file or a network file. The URI of a local file can be obtained by calling [getUriFromPath](../apis-core-file-kit/js-apis-file-fileuri.md#fileurigeturifrompath).<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| uriAuthorizationPolicies | Array<[UriPermission](#uripermission)> | No | Yes | URI authorization policy used in drag-and-drop scenarios. The default value is READ+WRITE+PERSIST (read + write + persistent authorization). It applies only to a single record and has the highest priority. For details about the policies, see [UriPermission](#uripermission).<br/>**Since:** 26.0.0<br/>**Atomic service API:** Since API version 26.0.0, this API is supported in atomic services. |

**Example**

```ts
import { unifiedDataChannel } from '@kit.ArkData';
import { fileUri } from '@kit.CoreFileKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let context = this.context;
    let pathDir = context.filesDir;
    let file = new unifiedDataChannel.File();
    file.details = {
      'name': 'test',
      'type': 'txt'
    };
    let filePath = pathDir + '/test.txt';
    file.uri = fileUri.getUriFromPath(filePath);
    // Starting from API version 26.0.0, the URI authorization policy is supported.
    file.uriAuthorizationPolicies = [
      unifiedDataChannel.UriPermission.WRITE
    ];
  }
}
```

## Image

Represents image data. It is a subclass of [File](#file) and is used to describe an image file.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| imageUri | string | No | No | URI of the local image data or network image. The URI of the local image data can be obtained by calling [getUriFromPath](../apis-core-file-kit/js-apis-file-fileuri.md#fileurigeturifrompath). |

**Example**

```ts
import { unifiedDataChannel } from '@kit.ArkData';
import { fileUri } from '@kit.CoreFileKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let context = this.context;
    let pathDir = context.filesDir;
    let image = new unifiedDataChannel.Image();
    let filePath = pathDir + '/test.jpg';
    image.imageUri = fileUri.getUriFromPath(filePath);
  }
}
```

## Video

Video data, a subclass of [File](#file), used to describe a video file.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| videoUri | string | No | No | URI of the local video data or network video. The URI of the local video data can be obtained by calling [getUriFromPath](../apis-core-file-kit/js-apis-file-fileuri.md#fileurigeturifrompath). |

**Example**

```ts
import { unifiedDataChannel } from '@kit.ArkData';
import { fileUri } from '@kit.CoreFileKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let context = this.context;
    let pathDir = context.filesDir;
    let video = new unifiedDataChannel.Video();
    let filePath = pathDir + '/test.mp4';
    video.videoUri = fileUri.getUriFromPath(filePath);
  }
}
```

## Audio

Audio data, a subclass of [File](#file), used to describe an audio file.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| audioUri | string | No | No | URI of the local audio data or network audio data. The URI of the local audio data can be obtained by calling [getUriFromPath](../apis-core-file-kit/js-apis-file-fileuri.md#fileurigeturifrompath). |

**Example**

```ts
import { unifiedDataChannel } from '@kit.ArkData';
import { fileUri } from '@kit.CoreFileKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let context = this.context;
    let pathDir = context.filesDir;
    let audio = new unifiedDataChannel.Audio();
    let filePath = pathDir + '/test.mp3';
    audio.audioUri = fileUri.getUriFromPath(filePath);
  }
}
```

## Folder

Folder type data, a subclass of [File](#file), used to describe a folder.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| folderUri | string | No | No | URI of a local folder or a network folder. The URI of a local folder can be obtained by [getUriFromPath](../apis-core-file-kit/js-apis-file-fileuri.md#fileurigeturifrompath). |

**Example**

```ts
import { unifiedDataChannel } from '@kit.ArkData';
import { fileUri } from '@kit.CoreFileKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let context = this.context;
    let pathDir = context.filesDir;
    let folder = new unifiedDataChannel.Folder();
    let filePath = pathDir + '/folder';
    folder.folderUri = fileUri.getUriFromPath(filePath);
  }
}
```

## SystemDefinedRecord

SystemDefinedRecord is a subclass of [UnifiedRecord](#unifiedrecord) and the base class of OpenHarmony system-specific data types. It is used to describe data types that circulate only within the OpenHarmony system. You are advised to use subclasses of SystemDefinedRecord, such as [SystemDefinedForm](#systemdefinedform), [SystemDefinedAppItem](#systemdefinedappitem), and [SystemDefinedPixelMap](#systemdefinedpixelmap), to describe data.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| details | Record<string, number \| string \| Uint8Array> | No | Yes | A dictionary object whose key is of the string type and whose value can be of the number, string, or Uint8Array (binary byte array) type. This is an optional field, and the default value is an empty dictionary object.|

**Example**

```ts
let sdr = new unifiedDataChannel.SystemDefinedRecord();
let u8Array = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
sdr.details = {
  title: 'recordTitle',
  version: 1,
  content: u8Array
};
let unifiedData = new unifiedDataChannel.UnifiedData(sdr);
```

## SystemDefinedForm

Represents the system-defined widget data, which is a subclass of [SystemDefinedRecord](#systemdefinedrecord).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| formId      | number | No | No | Widget ID.          |
| formName    | string | No | No | Widget name.          |
| bundleName  | string | No | No | Name of the bundle to which the widget belongs.   |
| abilityName | string | No | No | Name of the ability corresponding to the widget. |
| module      | string | No | No | Name of the module to which the widget belongs.   |

**Example**

```ts
let form = new unifiedDataChannel.SystemDefinedForm();
form.formId = 123456;
form.formName = 'MyFormName';
form.bundleName = 'MyBundleName';
form.abilityName = 'MyAbilityName';
form.module = 'MyModule';
let u8Array = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
form.details = {
  formKey1: 123,
  formKey2: 'formValue',
  formKey3: u8Array
};
let unifiedData = new unifiedDataChannel.UnifiedData(form);
```

## SystemDefinedAppItem

System-defined desktop icon data, which is a subclass of [SystemDefinedRecord](#systemdefinedrecord).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| appId       | string | No | No | Application ID corresponding to the icon.      |
| appName     | string | No | No | Application name corresponding to the icon.       |
| appIconId   | string | No | No | Image ID of the icon.<br/>        |
| appLabelId  | string | No | No | Label ID corresponding to the icon name.   |
| bundleName  | string | No | No | Bundle name of the application corresponding to the icon. |
| abilityName | string | No | No | Ability name of the application corresponding to the icon. |

**Example**

```ts
let appItem = new unifiedDataChannel.SystemDefinedAppItem();
appItem.appId = 'MyAppId';
appItem.appName = 'MyAppName';
appItem.appIconId = 'MyAppIconId';
appItem.appLabelId = 'MyAppLabelId';
appItem.bundleName = 'MyBundleName';
appItem.abilityName = 'MyAbilityName';
let u8Array = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
appItem.details = {
  appItemKey1: 123,
  appItemKey2: 'appItemValue',
  appItemKey3: u8Array
};
let unifiedData = new unifiedDataChannel.UnifiedData(appItem);
```

## SystemDefinedPixelMap

An image data type corresponding to the system-defined [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) data type. It is a subclass of [SystemDefinedRecord](#systemdefinedrecord) and stores only the binary data of a PixelMap.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| rawData | Uint8Array | No | No | Binary data of the PixelMap object. |

**Example**

```ts
import { image } from '@kit.ImageKit'; // Module where the PixelMap class is defined.
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

const color = new ArrayBuffer(96); // Create a pixelMap object.
let opts: image.InitializationOptions = {
  editable: true, pixelFormat: 3, size: {
    height: 4, width: 6
  }
}
image.createPixelMap(color, opts, (error, pixelMap) => {
  if (error) {
    console.error('Failed to create pixelMap.');
  } else {
    console.info('Succeeded in creating pixelMap.');
    let arrayBuf = new ArrayBuffer(pixelMap.getPixelBytesNumber());
    pixelMap.readPixelsToBuffer(arrayBuf);
    let u8Array = new Uint8Array(arrayBuf);
    let sdPixel = new unifiedDataChannel.SystemDefinedPixelMap();
    sdPixel.rawData = u8Array;
    let unifiedData = new unifiedDataChannel.UnifiedData(sdPixel);

    // Read the record of the pixelMap type from unifiedData.
    let records = unifiedData.getRecords();
    for (let i = 0; i < records.length; i++) {
      if (records[i].getType() === uniformTypeDescriptor.UniformDataType.OPENHARMONY_PIXEL_MAP) {
        let pixelMapRecord = records[i] as unifiedDataChannel.SystemDefinedPixelMap;
        let newArrayBuf = pixelMapRecord.rawData.buffer;
        pixelMap.writeBufferToPixels(newArrayBuf).then(() => {
          console.info('Succeeded in writing data from buffer to a pixelMap');
        }).catch((error: BusinessError) => {
          console.error(`Failed to write data from a buffer to a PixelMap. code is ${error.code}, message is ${error.message}`);
        })
      }
    }
  }
})
```

## ApplicationDefinedRecord

ApplicationDefinedRecord is a subclass of [UnifiedRecord](#unifiedrecord) and the base class of application-defined data types. It describes custom data types that circulate only within the application ecosystem. Applications can extend custom data types based on this class.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| applicationDefinedType | string     | No | No | Identifier of the application-defined type. It must start with 'ApplicationDefined'. |
| rawData                | Uint8Array | No | No | Binary data of the application-defined data type.                      |

**Example**

```ts
let record = new unifiedDataChannel.ApplicationDefinedRecord();
let u8Array = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
record.applicationDefinedType = 'ApplicationDefinedType';
record.rawData = u8Array;
let unifiedData = new unifiedDataChannel.UnifiedData(record);
```

## Intention

Enumerates the data channels supported by UDMF. It is mainly used to identify the different business scenarios targeted by various UDMF data channels.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name       | Value         | Description      |
|----------|-----------|---------|
| DATA_HUB | 'DataHub' | Public data channel.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services.<br/>**Applicable scenario:** Suitable for cross-application data sharing using UDMF in public data sharing scenarios. |
| DRAG<sup>14+</sup> | 'Drag' | Drag-and-drop data channel.<br/>**Applicable scenario:** Suitable for cross-application data sharing using UDMF in drag-and-drop scenarios. |
| SYSTEM_SHARE<sup>20+</sup> | 'SystemShare' | System sharing data channel.<br/>**Applicable scenario:** Suitable for cross-application data sharing using UDMF in system sharing scenarios. |
| PICKER<sup>20+</sup> | 'Picker' | Picker data channel.<br/>**Applicable scenario:** Suitable for cross-application data sharing using UDMF in picker scenarios. |
| MENU<sup>20+</sup> | 'Menu' | Menu data channel.<br/>**Applicable scenario:** Suitable for cross-application data sharing using UDMF in right-click menu scenarios. |

## Visibility<sup>20+</sup>

Enumerates the visibility levels of data.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name          | Value | Description                          |
| ------------- | ---- |------------------------------|
| ALL           | 0    | Visibility level, visible to all applications.    |
| OWN_PROCESS   | 1    | Visibility level, visible only to the data provider.  |

## Options

The data operation APIs provided by UDMF include three optional parameters: intention, key, and visibility. If an API does not require these parameters, they can be left unspecified. For details, see the parameter description of the specific API.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name      | Type                    | Read-only | Optional | Description                                                         |
| --------- | ----------------------- | ---- | ----- | ------------------------------------------------------- |
| intention | [Intention](#intention) | No | Yes | Data channel type related to the data operation. The value is an [Intention](#intention) enum, including DATA_HUB and DRAG. If not specified, the value is empty by default. For details about whether this parameter is mandatory, see the parameter description of the specific API.<br/>**Atomic service API:** This API is supported in atomic services since API version 11.              |
| key | string | No | Yes | Unique identifier of the data object in UDMF. It can be obtained from the return value of [insertData](#unifieddatachannelinsertdata). If not specified, the value is empty by default. For details about whether this parameter is mandatory, see the parameter description of the specific API.<br>It consists of four parts: udmf:/, intention, bundleName, and groupId, which are connected by '/', for example, udmf://DataHub/com.ohos.test/0123456789.<br>Among them, udmf:/ is fixed, DataHub is the value of the corresponding enum, com.ohos.test is the bundle name, and 0123456789 is the randomly generated groupId.<br/>**Atomic service API:** This API is supported in atomic services since API version 11. |
| visibility<sup>20+</sup> | [Visibility](#visibility20) | No | Yes | Visibility level of the data. It is available only for public data channels. The value is a [Visibility](#visibility20) enum. It takes effect only when specified during data writing. If not specified, the default value is Visibility.ALL.<br/>**Atomic service API:** This API is supported in atomic services since API version 20.  |

## FileConflictOptions<sup>15+</sup>

Enumerates the optional policies for file copy conflicts.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name      | Value | Description             |
| --------- | ----- |----------------|
| OVERWRITE | 0    | Overwrites the file when a file with the same name exists in the destination path. |
| SKIP      | 1    | Skips the file when a file with the same name exists in the destination path. |

## ProgressIndicator<sup>15+</sup>

Enumerates the progress indicator options, which determine whether to use the system default progress display.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name    | Value | Description                                 |
| ------- | ----- |------------------------------------|
| NONE    | 0    | Does not use the system default progress display.                       |
| DEFAULT | 1    | Uses the system default progress display. If data is obtained within 500 ms, the default progress bar will not be displayed. |

## ListenerStatus<sup>15+</sup>

Enumerates the status codes returned when obtaining data from UDMF.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name    | Value | Description                                           |
| ------- |-----|----------------------------------------------|
| FINISHED | 0   | Finished.                                       |
| PROCESSING | 1   | Processing.                                     |
| CANCELED | 2   | Canceled.                                  |
| INNER_ERROR  | 200 | An internal error occurred.                                   |
| INVALID_PARAMETERS | 201 | [GetDataParams](#getdataparams15) contains invalid parameters. |
| DATA_NOT_FOUND | 202 | No data is obtained.                                   |
| SYNC_FAILED | 203 | An error occurred during synchronization.                                 |
| COPY_FILE_FAILED | 204 | An error occurred during file copy.                               |

## ProgressInfo<sup>15+</sup>

Defines the data for progress reporting.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

| Name     | Type                                | Read-only | Optional | Description                                                             |
| -------- |-------------------------------------| ---- | ---- |----------------------------------------------------------------|
| progress | number                              | No   | No   | Progress percentage of the drag-and-drop task reported by the system. The value is an integer in the range [-1, 100], where -1 indicates that data acquisition failed this time, and 100 indicates that data acquisition is complete. |
| status | [ListenerStatus](#listenerstatus15) | No   | No   | Status code of the drag-and-drop task reported by the system.                                                  |

## DataProgressListener<sup>15+</sup>

type DataProgressListener = (progressInfo: ProgressInfo, data: UnifiedData | null) => void

Defines the listener callback used to obtain progress information and data.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name      | Type                            | Mandatory    | Description           |
|----------|-------------------------------|-------|--------------|
| progressInfo | [ProgressInfo](#progressinfo15) | Yes | Progress information reported for the drag-and-drop task, including the progress status and progress percentage. It contains two fields: progress (progress percentage, ranging from -1 to 100) and status (task status code). A progress value of -1 indicates a failure to obtain data, and 100 indicates that data obtaining is complete. |
| data        | [UnifiedData](#unifieddata)  \| null  |  Yes    | Data obtained when the progress reaches 100. Returns null when the progress has not reached 100. |

## GetDataParams<sup>15+</sup>

Represents the parameters used to obtain data from UDMF, including the destination path, file conflict options, and progress bar type.

For details about how to use it, see [Example 3 Asynchronously Obtaining Data During Drag](../apis-arkui/arkui-ts/ts-universal-events-drag-drop.md#example-3-asynchronously-obtaining-data-during-drag).

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name                   | Type                                              | Read-only | Optional | Description                                                                                                                                                 |
|----------------------|-------------------------------------------------| ---- | ---- |----------------------------------------------------------------------------------------------------------------------------------------------------|
| progressIndicator    | [ProgressIndicator](#progressindicator15)       | No   | No   | Defines the progress bar indicator options, which determine whether to use the system default progress display.<br>**Atomic service API:** This API is supported in atomic services since API version 15.                                                                                                                         |
| dataProgressListener | [DataProgressListener](#dataprogresslistener15) | No   | No   | Represents the progress and data listener used when obtaining unified data.<br>**Atomic service API:** This API is supported in atomic services since API version 15.                                                                                                                                |
| destUri              | string                                          | No   | Yes   | Destination path for copying files. If file processing is not supported, this parameter does not need to be set and defaults to empty. If file processing is supported, it must be set to an existing directory. If the application involves complex file processing policies or needs to distinguish multi-path storage of files, it is recommended not to set this parameter and let the application complete the file copy processing on its own. When this parameter is not set, the obtained URI is the source path URI; when it is set, the obtained URI is the destination path URI.<br>**Atomic service API:** This API is supported in atomic services since API version 15.|
| fileConflictOptions  | [FileConflictOptions](#fileconflictoptions15)   | No   | Yes   | Defines the options for file copy conflicts. The default value is OVERWRITE.<br>**Atomic service API:** This API is supported in atomic services since API version 15.                                                                                                                         |
| acceptableInfo<sup>20+</sup>  | [DataLoadInfo](#dataloadinfo20)   | No   | Yes   | Defines the receiver's capability to accept data types and the number of data records. In lazy loading scenarios, the sender can generate and return more appropriate data content based on this information. It defaults to empty, indicating that the receiver's data acceptance capability is not provided.<br>**Atomic service API:** This API is supported in atomic services since API version 20.   |

## DataLoadInfo<sup>20+</sup>

Describes the type and quantity of the data to be loaded.

- Used on the **data sender** side to indicate the range of data that can actually be provided. This field must be set.
- Used on the **data receiver** side to indicate the type and quantity of data expected to be loaded. This field can be set as needed.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name                   | Type                                              | Readable | Optional | Description                                                                                                                                                 |
|----------------------|-------------------------------------------------| ---- |-----| -----------------------------------------------------------------------------------------------------------------------------------------------|
| types    | Set\<string\>       | No | Yes | Set of data types. The default value is an empty set.                                                                                                                         |
| recordCount | number | No | Yes | Maximum number of data records expected or that can be provided. The default value is **0**, and the value range is [0, 2<sup>32</sup>-1]. If the value exceeds the range, the default value is used. If the value is a floating-point number, only the integer part is used. When used for drag-and-drop, this value is displayed as the badge count, with a maximum of 2<sup>31</sup>-1. If the value exceeds this maximum, the badge is not displayed. When used as the badge count, its priority is lower than that of the numberBadge method in [DragPreviewOptions](../apis-arkui/arkui-ts/ts-universal-attributes-drag-drop.md#dragpreviewoptions11-1).                            |

## DataLoadHandler<sup>20+</sup>

type DataLoadHandler = (acceptableInfo?: DataLoadInfo) => UnifiedData | null

Defines the handler for delayed data loading. It allows the data sender to dynamically generate data based on the information passed in by the receiver, enabling more flexible and precise data interaction strategies.

This handler is a synchronous function and is suitable for simple business logic. If the business logic is complex or takes a long time to execute (more than 3 seconds), use the asynchronous handler [DelayedDataLoadHandler](#delayeddataloadhandler22) instead.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name      | Type                            | Mandatory    | Description           |
|----------|-------------------------------|-------|--------------|
| acceptableInfo | [DataLoadInfo](#dataloadinfo20) | No     | Data types and quantity that the data receiver can accept. The default value is empty. |

**Return value**

| Type                    | Description                                |
|-----------------------|-----------------------------------|
| [UnifiedData](#unifieddata) \| null | UnifiedData object generated based on the receiver information when the delayed handler is triggered, used for data transfer. If the data cannot be generated or generation fails, null is returned. |

## DelayedDataLoadHandler<sup>22+</sup>

type DelayedDataLoadHandler = (acceptableInfo?: DataLoadInfo) => Promise<UnifiedData | null>

Defines the handler for delayed data loading. It allows the data sender to dynamically generate data based on the information passed in by the receiver, enabling a more flexible and precise data interaction strategy. The result is returned asynchronously through a promise.

This handler is an asynchronous function that does not block the main thread. It can handle complex business logic and execute long-running tasks.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name      | Type                            | Mandatory    | Description           |
|----------|-------------------------------|-------|--------------|
| acceptableInfo | [DataLoadInfo](#dataloadinfo20) | No     | Data types and quantity that the data receiver can accept. The default value is empty. |

**Return value**

| Type                    | Description                                |
|-----------------------|-----------------------------------|
| Promise&lt;[UnifiedData](#unifieddata) \| null&gt; | Promise object. When resolved, it returns the UnifiedData object generated based on the receiver information, or null. When rejected, it returns the error information. |

## DataLoadParams<sup>20+</sup>

Describes the data loading policy of the sender in delayed loading scenarios.

When both loadHandler and delayedDataLoadHandler are passed in, delayedDataLoadHandler takes precedence and loadHandler does not take effect.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name                   | Type                                              | Read-only | Optional | Description                                                                                                                                                 |
|----------------------|-------------------------------------------------| ---- |-----|-----------------------------------------------------------------------------------------------------------------------------------------------|
| loadHandler    | [DataLoadHandler](#dataloadhandler20)       | No | No| Handler used to load data in a delayed manner. This handler is a synchronous function and is suitable for processing simple service logic. If the function involves complex service logic and takes a long time to execute (more than 3s), you are advised to use [DelayedDataLoadHandler](#delayeddataloadhandler22).<br/>**Atomic service API:** This API is supported in atomic services since API version 20.             |
| delayedDataLoadHandler<sup>22+</sup> | [DelayedDataLoadHandler](#delayeddataloadhandler22) | No | Yes| Asynchronous handler used to load data in a delayed manner. The default value is undefined. If this parameter is not set, only loadHandler is used.<br/>**Atomic service API:** This API is supported in atomic services since API version 22.|
| dataLoadInfo | [DataLoadInfo](#dataloadinfo20) | No | No| Describes the data types and quantities that the current sender can generate.<br/>**Atomic service API:** This API is supported in atomic services since API version 20.              |

## unifiedDataChannel.insertData

insertData(options: Options, data: UnifiedData, callback: AsyncCallback&lt;string&gt;): void

Writes data to the public data channel of the UDMF and generates a unique identifier for the data. This API uses an asynchronous callback to return the result.

**Implementation mechanism** After receiving the UnifiedData object, the system verifies data integrity and serializes the data for storage. It routes the data to the corresponding storage space based on the intention value and generates a unique identifier key. The validity period of the data in the public data channel is managed by the system, and the default policy is to automatically clear the data after the application exits.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name      | Type                         | Mandatory | Description                           |
|----------|----------------------------|----|------------------------------|
| options  | [Options](#options)        | Yes  | Configuration parameters. The **intention** field is mandatory and does not support **DRAG**. If it is not specified, error code 401 is returned. Whether other fields are specified does not affect the use of this API.        |
| data | [UnifiedData](#unifieddata) | Yes | Unified data object to write or update, used to store data records and their attribute information. |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback invoked to return the unique identifier key of the data written to the UDMF. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.  |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  abstract: 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);

let options: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
};
try {
  unifiedDataChannel.insertData(options, unifiedData, (err, key) => {
    if (err === undefined) {
      console.info(`Succeeded in inserting data. key = ${key}`);
    } else {
      console.error(`Failed to insert data. code is ${err.code}, message is ${err.message} `);
    }
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Insert data throws an exception. code is ${error.code}, message is ${error.message}`);
}
```

## unifiedDataChannel.insertData

insertData(options: Options, data: UnifiedData): Promise&lt;string&gt;

Writes data to the public data channel of UDMF and generates a unique identifier for the data. This API uses a promise to return the result asynchronously.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name    | Type                         | Mandatory | Description                                                                                                                                                                                                 |
|---------|------------------------------|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| options | [Options](#options)          | Yes       | Configuration options. The **intention** field is mandatory and does not support DRAG. If it is not specified, error code 401 is returned. Whether other fields are specified does not affect the use of this API. |
| data    | [UnifiedData](#unifieddata)  | Yes       | Target data.                                                                                                                                                                                                |

**Return value**

| Type                   | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| Promise&lt;string&gt;  | Promise used to return the unique identifier key of the data written to UDMF. |

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                                                                                                                                                                                 |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 401               | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.                                                                  |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  abstract: 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);

let options: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
};
try {
  unifiedDataChannel.insertData(options, unifiedData).then((key) => {
    console.info(`Succeeded in inserting data. key = ${key}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to insert data. code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Insert data throws an exception. code is ${error.code}, message is ${error.message}`);
}
```

## unifiedDataChannel.updateData

updateData(options: Options, data: UnifiedData, callback: AsyncCallback&lt;void&gt;): void

Updates the data in the public data channel that has been written to UDMF. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name      | Type                          | Mandatory | Description                                  |
|----------|-----------------------------|----|-------------------------------------|
| options  | [Options](#options)         | Yes  | Configuration parameters. The **key** field is mandatory. If it is not specified, error code 401 is returned. The **intention** parameter supports only DATA_HUB. Whether other fields are specified does not affect the use of this API.                     |
| data     | [UnifiedData](#unifieddata) | Yes  | Target data.                               |
| callback | AsyncCallback&lt;void&gt;   | Yes  | Callback used to return the result. If the data is updated successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Error Codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.  |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  abstract: 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);
let options: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
};
try {
  unifiedDataChannel.insertData(options, unifiedData).then((key) => {
    console.info(`Succeeded in inserting data. key = ${key}`);
    let updateOptions: unifiedDataChannel.Options = {
      intention: unifiedDataChannel.Intention.DATA_HUB,
      key: key
    };
    let plainTextUpdate: uniformDataStruct.PlainText = {
      uniformDataType: 'general.plain-text',
      textContent: 'This is plainText textContent for update',
      abstract: 'This is abstract for update'
    };
    let textUpdate =
      new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainTextUpdate);
    let unifiedDataUpdate = new unifiedDataChannel.UnifiedData(textUpdate);
    try {
      unifiedDataChannel.updateData(updateOptions, unifiedDataUpdate, (err) => {
        if (err === undefined) {
          console.info('Succeeded in updating data.');
        } else {
          console.error(`Failed to update data. code is ${err.code}, message is ${err.message}`);
        }
      });
    } catch (e) {
      let error: BusinessError = e as BusinessError;
      console.error(`Update data throws an exception. code is ${error.code}, message is ${error.message}`);
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to insert data. code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Insert data throws an exception. code is ${error.code}, message is ${error.message}`);
}
```

## unifiedDataChannel.updateData

updateData(options: Options, data: UnifiedData): Promise&lt;void&gt;

Updates the data in the public data channel that has been written to UDMF. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name    | Type                          | Mandatory | Description              |
|---------|-----------------------------|----|-----------------|
| options | [Options](#options)         | Yes  | Configuration options. The **key** field is mandatory. If it is not specified, error code 401 is returned. The **intention** parameter supports only DATA_HUB. Other fields do not affect the use of this API. |
| data    | [UnifiedData](#unifieddata) | Yes  | Target data.           |

**Return value**

| Type                  | Description                         |
|---------------------|----------------------------|
| Promise&lt;void&gt; | Promise that returns no value. |

**Error Codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.  |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  abstract: 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);
let options: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
};

try {
  unifiedDataChannel.insertData(options, unifiedData).then((key) => {
    console.info(`Succeeded in inserting data. key = ${key}`);
    let updateOptions: unifiedDataChannel.Options = {
      intention: unifiedDataChannel.Intention.DATA_HUB,
      key: key
    };
    let plainTextUpdate: uniformDataStruct.PlainText = {
      uniformDataType: 'general.plain-text',
      textContent: 'This is plainText textContent for update',
      abstract: 'This is abstract for update'
    };
    let textUpdate =
      new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainTextUpdate);
    let unifiedDataUpdate = new unifiedDataChannel.UnifiedData(textUpdate);
    try {
      unifiedDataChannel.updateData(updateOptions, unifiedDataUpdate).then(() => {
        console.info('Succeeded in updating data.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to update data. code is ${err.code}, message is ${err.message} `);
      });
    } catch (e) {
      let error: BusinessError = e as BusinessError;
      console.error(`Update data throws an exception. code is ${error.code}, message is ${error.message} `);
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to insert data. code is ${err.code}, message is ${err.message} `);
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Insert data throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## unifiedDataChannel.queryData

queryData(options: Options, callback: AsyncCallback&lt;Array&lt;UnifiedData&gt;&gt;): void

Queries data in the UDMF public data channel. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name      | Type                                                            | Mandatory | Description                                                                                                                                                               |
|----------|---------------------------------------------------------------|----|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| options  | [Options](#options)                                           | Yes  | Configuration options. Both key and intention are optional, and intention does not support DRAG. Corresponding validation is performed based on the passed parameters to return different values.                                                                                                                   |
| callback | AsyncCallback&lt;Array&lt;[UnifiedData](#unifieddata)&gt;&gt; | Yes  | Callback invoked to return all the queried data.<br>If key is specified in options, the data corresponding to the key is returned.<br>If intention is specified in options, all data under the intention is returned.<br>If both intention and key are specified, the intersection of the data queried by the two is returned, which is consistent with the result obtained when only key is specified in options. If there is no intersection, an error is reported. |

**Error Codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.  |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let options: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
};

try {
  unifiedDataChannel.queryData(options, (err, data) => {
    if (err === undefined) {
      console.info(`Succeeded in querying data. size = ${data.length}`);
      for (let i = 0; i < data.length; i++) {
        let records = data[i].getRecords();
        for (let j = 0; j < records.length; j++) {
          if (records[j].getTypes().includes(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT)) {
            let text =
              records[j].getEntry(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) as uniformDataStruct.PlainText;
            console.info(`${i + 1}.${text.textContent}`);
          }
        }
      }
    } else {
      console.error(`Failed to query data. code is ${err.code}, message is ${err.message}`);
    }
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Query data throws an exception. code is ${error.code}, message is ${error.message}`);
}
```

## unifiedDataChannel.queryData

queryData(options: Options): Promise&lt;Array&lt;UnifiedData&gt;&gt;

Queries data in the UDMF public data channel. This API uses a promise to return the result asynchronously.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name    | Type                | Mandatory | Description                                                                                                                                 |
|---------|---------------------|-----------|---------------------------------------------------------------------------------------------------------------------------------------------|
| options | [Options](#options) | Yes       | Configuration parameters. Both key and intention are optional, and the intention parameter does not support DRAG. Corresponding verification is performed based on the passed parameters to return different values. |

**Return value**

| Type                                                      | Description                                                                                                                                                                                                                                                                                                                                 |
|-----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Promise&lt;Array&lt;[UnifiedData](#unifieddata)&gt;&gt; | Promise object used to return all the queried data.<br>If key is specified in options, the data corresponding to the key is returned.<br>If intention is specified in options, all data under the intention is returned.<br>If both intention and key are specified, the intersection of the two query results is returned, which is consistent with the result obtained when only key is specified in options. An error is reported if there is no intersection. |

**Error Code**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                                                                                                                                                                                 |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 401               | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let options: unifiedDataChannel.Options = {
  key: 'udmf://DataHub/com.ohos.test/0123456789'
};

try {
  unifiedDataChannel.queryData(options).then((data) => {
    console.info(`Succeeded in querying data. size = ${data.length}`);
    for (let i = 0; i < data.length; i++) {
      let records = data[i].getRecords();
      for (let j = 0; j < records.length; j++) {
        if (records[j].getTypes().includes(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT)) {
          let text =
            records[j].getEntry(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) as uniformDataStruct.PlainText;
          console.info(`${i + 1}.${text.textContent}`);
        }
      }
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to query data. code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Query data throws an exception. code is ${error.code}, message is ${error.message}`);
}
```

## unifiedDataChannel.deleteData

deleteData(options: Options, callback: AsyncCallback&lt;Array&lt;UnifiedData&gt;&gt;): void

Deletes data from the UDMF public data channel and returns the deleted data set. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name      | Type                                                            | Mandatory | Description                                                                                                                                                                                     |
|----------|---------------------------------------------------------------|----|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| options  | [Options](#options)                                           | Yes  | Configuration parameters. Both key and intention are optional, and intention supports only DATA_HUB. The corresponding verification is performed based on the passed parameters to return different values.                                                                                                                                          |
| callback | AsyncCallback&lt;Array&lt;[UnifiedData](#unifieddata)&gt;&gt; | Yes  | Callback invoked to return all the deleted data.<br>If key is specified in options, the data corresponding to the key is deleted and returned.<br>If intention is specified in options, all data under the intention is deleted and returned.<br>If both intention and key are specified, the intersection of the two is deleted and returned, which is consistent with the result when only key is specified in options; an error is reported if there is no intersection. |

**Error Code**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.  |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let options: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
};

try {
  unifiedDataChannel.deleteData(options, (err, data) => {
    if (err === undefined) {
      console.info(`Succeeded in deleting data. size = ${data.length}`);
      for (let i = 0; i < data.length; i++) {
        let records = data[i].getRecords();
        for (let j = 0; j < records.length; j++) {
          if (records[j].getTypes().includes(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT)) {
            let text =
              records[j].getEntry(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) as uniformDataStruct.PlainText;
            console.info(`${i + 1}.${text.textContent}`);
          }
        }
      }
    } else {
      console.error(`Failed to delete data. code is ${err.code}, message is ${err.message}`);
    }
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Delete data throws an exception. code is ${error.code}, message is ${error.message}`);
}
```

## unifiedDataChannel.deleteData

deleteData(options: Options): Promise&lt;Array&lt;UnifiedData&gt;&gt;

Deletes data from the UDMF public data channel and returns the deleted data set. This API uses a promise to return the result asynchronously.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name    | Type                | Mandatory | Description                                                                                                                                                                                                                             |
|---------|---------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| options | [Options](#options) | Yes       | Configuration parameters. Both key and intention are optional, and intention supports only DATA_HUB. The parameters are verified based on the values passed in to return different results. |

**Return value**

| Type                                                      | Description                                                                                                                                                                                                                                                                                                                                                                                          |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Promise&lt;Array&lt;[UnifiedData](#unifieddata)&gt;&gt; | Promise used to return all deleted data.<br>If key is specified in options, the data corresponding to key is deleted and returned.<br>If intention is specified in options, all data under intention is deleted and returned.<br>If both intention and key are specified, the intersection of the two data sets is deleted and returned, which is the same as the result when only key is specified in options. An error is reported if there is no intersection. |

**Error Message**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                                                                                                                                                                                 |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 401               | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let options: unifiedDataChannel.Options = {
  key: 'udmf://DataHub/com.ohos.test/0123456789'
};

try {
  unifiedDataChannel.deleteData(options).then((data) => {
    console.info(`Succeeded in deleting data. size = ${data.length}`);
    for (let i = 0; i < data.length; i++) {
      let records = data[i].getRecords();
      for (let j = 0; j < records.length; j++) {
        if (records[j].getTypes().includes(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT)) {
          let text =
            records[j].getEntry(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) as uniformDataStruct.PlainText;
          console.info(`${i + 1}.${text.textContent}`);
        }
      }
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to delete data. code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Delete data throws an exception. code is ${error.code}, message is ${error.message}`);
}
```

## unifiedDataChannel.setAppShareOptions<sup>14+</sup>

setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void

Sets the usage scope of the data in the in-app drag-and-drop data channel, as defined by [ShareOptions](#shareoptions12). Currently, only the DRAG data channel supports this management setting. After the call succeeds, the usage scope of the data in the in-app drag-and-drop data channel is set to the specified ShareOptions value.

**Required permissions:** ohos.permission.MANAGE_UDMF_APP_SHARE_OPTION

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name      | Type                         | Mandatory | Description                           |
|----------|----------------------------|----|------------------------------|
| intention | [Intention](#intention) | Yes  | Data channel type related to the data operation. Currently, only the DRAG data channel is supported. |
| shareOptions | [ShareOptions](#shareoptions12) | Yes  | Usage scope of [UnifiedData](#unifieddata) within the device. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Unified Data Management Framework Error Codes](errorcode-udmf.md).

| **Error Code ID** | **Error Message**                                                 |
| ------------ | ------------------------------------------------------------ |
| 201          | Permission denied. Interface caller does not have permission "ohos.permission.MANAGE_UDMF_APP_SHARE_OPTION". |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 20400001     | Settings already exist. To reconfigure, remove the existing sharing options.        |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  unifiedDataChannel.setAppShareOptions(unifiedDataChannel.Intention.DRAG, unifiedDataChannel.ShareOptions.IN_APP);
  console.info(`[UDMF]setAppShareOptions success.`);
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`[UDMF]setAppShareOptions throws an exception. code is ${error.code}, message is ${error.message}`);
}
```

## unifiedDataChannel.removeAppShareOptions<sup>14+</sup>

removeAppShareOptions(intention: Intention): void

Clears the control information set by [setAppShareOptions](#unifieddatachannelsetappshareoptions14). After this API is called successfully, the control information set by setAppShareOptions is cleared, and the in-app drag-and-drop channel data is restored to the default usage scope.

**Required permissions:** ohos.permission.MANAGE_UDMF_APP_SHARE_OPTION

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name      | Type                    | Mandatory | Description                                                         |
| --------- | ----------------------- | --------- | ------------------------------------------------------------ |
| intention | [Intention](#intention) | Yes       | Data channel type related to the data operation. Currently, only the DRAG data channel is supported. |

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                                 |
| ------------ | ------------------------------------------------------------ |
| 201          | Permission denied. Interface caller does not have permission "ohos.permission.MANAGE_UDMF_APP_SHARE_OPTION". |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  unifiedDataChannel.removeAppShareOptions(unifiedDataChannel.Intention.DRAG);
  console.info(`[UDMF]removeAppShareOptions success.`);
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`[UDMF]removeAppShareOptions throws an exception. code is ${error.code}, message is ${error.message}`);
}
```

## unifiedDataChannel.convertRecordsToEntries<sup>17+</sup>

convertRecordsToEntries(data: UnifiedData): void

Converts the passed-in data into a multi-style data structure. If the original data uses multiple records to carry different data formats of the same data, you can use this API to convert the original data into a multi-style data structure.

The conversion is performed and the passed-in data is converted into a multi-style data structure when the following rules are met:
1. The number of records in the data is greater than 1.
2. The value of the tag in the properties of the data is "records_to_entries_data_format".

Otherwise, no action is taken.

**Atomic service API**: This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters**

| Name    | Type                    | Mandatory | Description                                                         |
| --------- | ----------------------- | ---- | ------------------------------------------------------------ |
| data    | [UnifiedData](#unifieddata) | Yes  | Unified data object to be converted into a multi-style data structure.           |

**Error code:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **Error Code ID** | **Error Message**                                                 |
| ----------------- | ------------------------------------------------------------ |
| 401               | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { unifiedDataChannel } from '@kit.ArkData';
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let details: Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2'
};
let plainTextObj: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'The weather is very good today',
  abstract: 'The weather is very good today',
  details: details
};
let htmlObj: uniformDataStruct.HTML = {
  uniformDataType: 'general.html',
  htmlContent: '<div><p>The weather is very good today</p></div>',
  plainContent: 'The weather is very good today',
  details: details
};
let plainText = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainTextObj);
let html = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.HTML, htmlObj);
let unifiedData = new unifiedDataChannel.UnifiedData(plainText);
unifiedData.addRecord(html);
unifiedData.properties.tag = 'records_to_entries_data_format';

try {
  unifiedDataChannel.convertRecordsToEntries(unifiedData);
  let records: Array<unifiedDataChannel.UnifiedRecord> = unifiedData.getRecords();
  console.info(`Records size is ${records.length}`); // After conversion, its length must be less than 1
  if (records.length == 1) {
    let plainTextObjRead: uniformDataStruct.PlainText =
      records[0].getEntry(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) as uniformDataStruct.PlainText;
    console.info(`TextContent is ${plainTextObjRead.textContent}`);
    let htmlObjRead: uniformDataStruct.HTML =
      records[0].getEntry(uniformTypeDescriptor.UniformDataType.HTML) as uniformDataStruct.HTML;
    console.info(`HtmlContent is ${htmlObjRead.htmlContent}`);
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Convert data throws an exception. code is ${error.code}, message is ${error.message}`);
}
```