# UnifiedData

```TypeScript
class UnifiedData
```

Represents the Unified Data Object of UDMF, which provides methods to encapsulate a group of data records.

**Since:** 10

<!--Device-unifiedDataChannel-class UnifiedData--><!--Device-unifiedDataChannel-class UnifiedData-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## addRecord

```TypeScript
addRecord(record: UnifiedRecord): void
```

Adds a data record to the current unified data object. After the call is successful, the specified data record is added to the current unified data object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-UnifiedData-addRecord(record: UnifiedRecord): void--><!--Device-UnifiedData-addRecord(record: UnifiedRecord): void-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| record | [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) | Yes | Data record to add to the unified data object. The record is a UnifiedRecord object or an object of its subclass. |

**Examples**

```TypeScript
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

## constructor

```TypeScript
constructor(record: UnifiedRecord)
```

Creates a unified data object that contains a data record. After the call is successful, a UnifiedData object containing the specified data record is returned.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-UnifiedData-constructor(record: UnifiedRecord)--><!--Device-UnifiedData-constructor(record: UnifiedRecord)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| record | [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) | Yes | Data record to add to the unified data object. The record is a UnifiedRecord object or an object of its subclass. |

**Examples**

```TypeScript
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
let plainText : uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent : 'This is a plain text example',
  abstract : 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);
```

## constructor

```TypeScript
constructor()
```

Creates a unified data object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UnifiedData-constructor()--><!--Device-UnifiedData-constructor()-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Examples**

```TypeScript
let unifiedData = new unifiedDataChannel.UnifiedData();
```

## getRecords

```TypeScript
getRecords(): Array<UnifiedRecord>
```

Obtains all data records in the current unified data object. The data obtained through this API is of the UnifiedRecord type. You need to obtain the data type through [getType](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md#gettype) and then convert it to a subclass before use.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-UnifiedData-getRecords(): Array<UnifiedRecord>--><!--Device-UnifiedData-getRecords(): Array<UnifiedRecord>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)&gt; | Array of all data records contained in the current unified data object. Each record can be converted to a specific subclass after its type is obtained through getType, for reading and processing various types of data in the unified data. |

**Examples**

```TypeScript
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

## getTypes

```TypeScript
getTypes(): Array<string>
```

Obtains the types of all data records in the current unified data object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UnifiedData-getTypes(): Array<string>--><!--Device-UnifiedData-getTypes(): Array<string>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Array of [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md), which represents the set of data types of the current records. The element values include 'general.plain-text','general.hyperlink', 'openharmony.form', and so on. |

**Examples**

```TypeScript
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

## hasType

```TypeScript
hasType(type: string): boolean
```

Checks whether the current unified data object contains the specified data type. The check scope includes the data types added by using [addEntry](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md#addentry) function.

For file types, if the type set of the UnifiedData object contains "general.jpeg", the result is true when hasType is called to check whether the type "general.image" is included (the type "general.jpeg" belongs to the type "general.image").

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UnifiedData-hasType(type: string): boolean--><!--Device-UnifiedData-hasType(type: string): boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Data type to query. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the specified data type exists; returns false otherwise. |

**Examples**

```TypeScript
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

## properties

```TypeScript
get properties(): UnifiedDataProperties
```

Properties of all data records in the current unified data object, including the timestamp, tag, paste scope, and some additional data.

**Type:** [UnifiedDataProperties](arkts-arkdata-unifieddatachannel-unifieddataproperties-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UnifiedData-get properties(): UnifiedDataProperties--><!--Device-UnifiedData-get properties(): UnifiedDataProperties-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set properties(value: UnifiedDataProperties)
```

Properties of all data records in the current unified data object, including the timestamp, tag, paste scope, and some additional data.

**Type:** [UnifiedDataProperties](arkts-arkdata-unifieddatachannel-unifieddataproperties-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UnifiedData-set properties(value: UnifiedDataProperties)--><!--Device-UnifiedData-set properties(value: UnifiedDataProperties)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
