# convertRecordsToEntries

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## convertRecordsToEntries

```TypeScript
function convertRecordsToEntries(data: UnifiedData): void
```

Converts the provided data into a multi-style data structure, which is useful when the original data uses multiple records to represent different styles of the same data.

This API is used only when the following rules are met:

1. The number of records in data is greater than 1.
2. The value of **unifiedData.properties.tag** is **records_to_entries_data_format**.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md) | Yes | Data to convert. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2.Incorrect parameter types; <br>3. Parameter verification failed. |

**Examples**

```TypeScript
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
