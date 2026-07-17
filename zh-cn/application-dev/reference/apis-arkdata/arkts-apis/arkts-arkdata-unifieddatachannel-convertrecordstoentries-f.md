# convertRecordsToEntries

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## convertRecordsToEntries

```TypeScript
function convertRecordsToEntries(data: UnifiedData): void
```

本接口用于将传入的data转换成多样式数据结构。若原data使用多个record去承载同一份数据的不同数据格式，则可以使用此接口将原data转换为多样式数据结构。

当满足以下规则时进行转换，传入的data经转换后变为多样式数据结构：

1. data中的record数量大于1；2. data中的properties中的tag值为"records_to_entries_data_format"。

否则不会产生任何行为。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

<!--Device-unifiedDataChannel-function convertRecordsToEntries(data: UnifiedData): void--><!--Device-unifiedDataChannel-function convertRecordsToEntries(data: UnifiedData): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [UnifiedData](../../apis-arkui/arkts-components/arkts-arkui-unifieddata-t.md) | 是 | 需要转换为多样式数据结构的统一数据对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2.Incorrect parameter types;<br>3. Parameter verification failed. |

**示例：**

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

