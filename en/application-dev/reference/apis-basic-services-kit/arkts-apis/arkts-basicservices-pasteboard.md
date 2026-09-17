# @ohos.pasteboard(Pasteboard)

This module provides the capabilities of managing the system pasteboard to support the copy and paste functions. You can use the APIs of this module to operate pasteboard content of the plain text, HTML, URI, Want, PixelMap, and other types.

**Since:** 6

**System capability:** SystemCapability.MiscServices.Pasteboard

## Modules to Import

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createData](arkts-basicservices-pasteboard-createdata-f.md) | Creates a **PasteData** object of the specified type. |
| [createData](arkts-basicservices-pasteboard-createdata-f.md) | Creates a **PasteData** object that contains multiple types of data. |
| [createHtmlData](arkts-basicservices-pasteboard-createhtmldata-f.md) | Creates a **PasteData** object of the HTML type. |
| [createHtmlTextRecord](arkts-basicservices-pasteboard-createhtmltextrecord-f.md) | Creates a **PasteDataRecord** object of the HTML text type. |
| [createPlainTextData](arkts-basicservices-pasteboard-createplaintextdata-f.md) | Creates a **PasteData** object of the plain text type. |
| [createPlainTextRecord](arkts-basicservices-pasteboard-createplaintextrecord-f.md) | Creates a **PasteDataRecord** object of the plain text type. |
| [createRecord](arkts-basicservices-pasteboard-createrecord-f.md) | Creates a **PasteDataRecord** object of the specified type. |
| [createUriData](arkts-basicservices-pasteboard-createuridata-f.md) | Creates a **PasteData** object of the URI type. |
| [createUriRecord](arkts-basicservices-pasteboard-createurirecord-f.md) | Creates a **PasteDataRecord** object of the URI type. |
| [createWantData](arkts-basicservices-pasteboard-createwantdata-f.md) | Creates a **PasteData** object of the Want type. |
| [createWantRecord](arkts-basicservices-pasteboard-createwantrecord-f.md) | Creates a **PasteDataRecord** object of the Want type. |
| [getSystemPasteboard](arkts-basicservices-pasteboard-getsystempasteboard-f.md) | Obtains **SystemPasteboard** object. |

### Classes

| Name | Description |
| --- | --- |
| [ProgressSignal](arkts-basicservices-pasteboard-progresssignal-c.md) | Defines a function for canceling the paste task. This parameter is valid only when [ProgressIndicator](arkts-basicservices-pasteboard-progressindicator-e.md) is set to **NONE**. |

### Interfaces

| Name | Description |
| --- | --- |
| [GetDataParams](arkts-basicservices-pasteboard-getdataparams-i.md) | Defines parameters when an application obtains the Data from the pasteboard, including the destination path, file conflict options, and progress indicator types. |
| [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | Implements a **PasteData** object. PasteData contains one or more data records ([PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md)) and property description objects ([PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md)). Before calling any API in **PasteData**, you must use ** [createData()](arkts-basicservices-pasteboard-createdata-f.md)** or ** [getData()](arkts-basicservices-pasteboard-systempasteboard-i.md#getdata)** to create a **PasteData** object. |
| [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md) | Defines the properties of PasteData in the pasteboard, including the timestamp, data types, pasteable range, and additional data. The defined properties can be applied to the pasteboard only with the [setProperty](arkts-basicservices-pasteboard-pastedata-i.md#setproperty) method. |
| [PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md) | Provides **PasteDataRecord** APIs. A **PasteDataRecord** is an abstract definition of the content in the pasteboard. The pasteboard content consists of one or more plain text, HTML, URI, or Want records. After creating a PasteDataRecord, it is not supported to modify the value of the default data type of the PasteDataRecord. The correct value for the default data type should be specified when creating the PasteDataRecord. If you need to refresh the attribute value of the PasteDataRecord, please use [addEntry](arkts-basicservices-pasteboard-pastedatarecord-i.md#addentry). |
| [ProgressInfo](arkts-basicservices-pasteboard-progressinfo-i.md) | Defines the progress information. This information is reported only when [ProgressIndicator](arkts-basicservices-pasteboard-progressindicator-e.md) is set to **NONE**. |
| [SystemPasteboard](arkts-basicservices-pasteboard-systempasteboard-i.md) | Provides **SystemPasteboard** APIs. Before calling any **SystemPasteboard** API, you must obtain a **SystemPasteboard** object using [getSystemPasteboard](arkts-basicservices-pasteboard-getsystempasteboard-f.md). |

### Enums

| Name | Description |
| --- | --- |
| [FileConflictOptions](arkts-basicservices-pasteboard-fileconflictoptions-e.md) | Enumerates options for file copy conflicts. |
| [Pattern](arkts-basicservices-pasteboard-pattern-e.md) | Describes the patterns supported by the pasteboard. |
| [ProgressIndicator](arkts-basicservices-pasteboard-progressindicator-e.md) | Enumerates options for the progress indicator. You can choose whether to use the default progress indicator. |
| [ShareOption](arkts-basicservices-pasteboard-shareoption-e.md) | Enumerates the pasteable ranges of PasteData. |

### Types

| Name | Description |
| --- | --- |
| [ProgressListener](arkts-basicservices-pasteboard-progresslistener-t.md) | Defines a listener for progress data changes. If the default progress indicator is not used, you can set this API to obtain the paste progress. |
| [UpdateCallback](arkts-basicservices-pasteboard-updatecallback-t.md) | Callback to be invoked when the pasteboard content changes. |
| [ValueType](arkts-basicservices-pasteboard-valuetype-t.md) | Indicates type of value. |

### Constants

| Name | Description |
| --- | --- |
| [MAX_RECORD_NUM](arkts-basicservices-pasteboard-con.md#max_record_num) | Maximum number of records in a **PasteData** object. In versions earlier than API version 10, the value is 512, indicating that no more records can be added once the number of records reaches 512. |
| [MIMETYPE_PIXELMAP](arkts-basicservices-pasteboard-con.md#mimetype_pixelmap) | MIME type of the PixelMap content. |
| [MIMETYPE_TEXT_HTML](arkts-basicservices-pasteboard-con.md#mimetype_text_html) | MIME type of the HTML content. |
| [MIMETYPE_TEXT_PLAIN](arkts-basicservices-pasteboard-con.md#mimetype_text_plain) | MIME type of the plain text content. |
| [MIMETYPE_TEXT_URI](arkts-basicservices-pasteboard-con.md#mimetype_text_uri) | MIME type of the URI content. |
| [MIMETYPE_TEXT_WANT](arkts-basicservices-pasteboard-con.md#mimetype_text_want) | MIME type of the Want content. |
