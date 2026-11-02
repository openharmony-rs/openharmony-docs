# UnifiedRecord

```TypeScript
class UnifiedRecord
```

An abstract definition of the data content supported by UDMF, called a data record. A unified data object contains one or more data records, for example, a text record, an image record, and an HTML record. Since API version 15, different data formats of the same content can be added to a data record (for example, the same text can be stored in plain text, HTML, or hyperlink formats at the same time). Data consumers can obtain the corresponding format through the getEntry method based on their service requirements.

**Since:** 10

<!--Device-unifiedDataChannel-class UnifiedRecord--><!--Device-unifiedDataChannel-class UnifiedRecord-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## addEntry

```TypeScript
addEntry(type: string, value: ValueType): void
```

Adds a data entry with the specified data type and content to the current data record. The data type and content added through this method are different representations of the same content. After the call is successful, the specified data type and content are added to the current data record.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-UnifiedRecord-addEntry(type: string, value: ValueType): void--><!--Device-UnifiedRecord-addEntry(type: string, value: ValueType): void-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Data type to create. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md). |
| value | [ValueType](arkts-arkdata-unifieddatachannel-valuetype-t.md) | Yes | Value of the data to create. |

**Examples**

```TypeScript
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

## constructor

```TypeScript
constructor()
```

Creates a data record. After the call is successful, an empty UnifiedRecord object is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UnifiedRecord-constructor()--><!--Device-UnifiedRecord-constructor()-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Examples**

```TypeScript
let unifiedRecord = new unifiedDataChannel.UnifiedRecord();
```

## constructor

```TypeScript
constructor(type: string, value: ValueType)
```

Creates a data record of the specified type and value. After the call is successful, a UnifiedRecord object containing the specified type and value is returned.<br>When the parameter **value** is of the [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) type, the parameter **type** must correspond to the value of OPENHARMONY_PIXEL_MAP in [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md).

When the parameter **value** is of the [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) type, the parameter **type** must correspond to the value of OPENHARMONY_WANT in [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UnifiedRecord-constructor(type: string, value: ValueType)--><!--Device-UnifiedRecord-constructor(type: string, value: ValueType)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the data record to create, used to identify the specific type of the data record. For details about the values, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md), for example, 'general.plain-text' and 'general.hyperlink'. |
| value | [ValueType](arkts-arkdata-unifieddatachannel-valuetype-t.md) | Yes | Value of the data record to create. |

**Examples**

```TypeScript
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

## getEntries

```TypeScript
getEntries(): Record<string, ValueType>
```

Obtains the types and contents of all data in the current data record.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-UnifiedRecord-getEntries(): Record<string, ValueType>--><!--Device-UnifiedRecord-getEntries(): Record<string, ValueType>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Return value:**

| Type | Description |
| --- | --- |
| Record&lt;string, [ValueType](arkts-arkdata-unifieddatachannel-valuetype-t.md)&gt; | Types and contents corresponding to the current data record. |

**Examples**

```TypeScript
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

## getEntry

```TypeScript
getEntry(type: string): ValueType
```

Obtains the data content in a data record by data type.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-UnifiedRecord-getEntry(type: string): ValueType--><!--Device-UnifiedRecord-getEntry(type: string): ValueType-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the data to obtain. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [ValueType](arkts-arkdata-unifieddatachannel-valuetype-t.md) | Value corresponding to the current data record. |

**Examples**

```TypeScript
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

## getType

```TypeScript
getType(): string
```

Obtains the type of the current data record. Since the data obtained by calling [getRecords](arkts-arkdata-unifieddatachannel-unifieddata-c.md#getrecords) from a unified data object is a UnifiedRecord object, you need to use this API to query the specific type of the record, and then convert the UnifiedRecord object to its subclass and call the subclass APIs.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-UnifiedRecord-getType(): string--><!--Device-UnifiedRecord-getType(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Specific data type corresponding to the current data record. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md). |

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

let records = unifiedData.getRecords();
if (records[0].getType() == uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) {
  let plainText = records[0] as unifiedDataChannel.PlainText;
  console.info(`textContent: ${plainText.textContent}`);
}
```

## getTypes

```TypeScript
getTypes(): Array<string>
```

Obtains the types of all data records in the current unified data object.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-UnifiedRecord-getTypes(): Array<string>--><!--Device-UnifiedRecord-getTypes(): Array<string>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Array of [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md), which represents the set of data types of the current records. The element values include 'general.plain-text','general.hyperlink', 'openharmony.form', and so on. |

**Examples**

```TypeScript
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

## getValue

```TypeScript
getValue(): ValueType
```

Obtains the value of the current data record.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UnifiedRecord-getValue(): ValueType--><!--Device-UnifiedRecord-getValue(): ValueType-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ValueType](arkts-arkdata-unifieddatachannel-valuetype-t.md) | Value corresponding to the current data record. |

**Examples**

```TypeScript
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
