# @ohos.data.unifiedDataChannel(Unified Data Channel)

This module is a part of the Unified Data Management Framework (UDMF). It provides a standardized data channel for various many-to-many cross-application data sharing scenarios, and offers standardized data access and read APIs. It also provides standardized definitions for data types such as text and images, facilitating data exchange between different applications and reducing the workload of data type adaptation.

**Design logic:** UDMF adopts a unified data model, encapsulating different types of data into UnifiedData objects. It identifies different data channel types (such as DATA_HUB and DRAG) through Intention to implement cross-application data sharing. A unique identifier key is generated when data is written, and data is queried by key or intention when read.

When processing data, UDMF does not parse the content of user data, and the storage path has low security. Therefore, it is not recommended to transmit sensitive personal data or private data.

> **NOTE:** 
> 
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> The APIs of this module can be used only in the stage model.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace unifiedDataChannel--><!--Device-unnamed-declare namespace unifiedDataChannel-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [convertRecordsToEntries](arkts-arkdata-unifieddatachannel-convertrecordstoentries-f.md#convertrecordstoentries-1) | Converts the passed-in data into a multi-style data structure. If the original data uses multiple records to carry different data formats of the same data, you can use this API to convert the original data into a multi-style data structure. The conversion is performed and the passed-in data is converted into a multi-style data structure when the following rules are met: 1. The number of records in the data is greater than 1. 2. The value of the tag in the properties of the data is "records_to_entries_data_format". |
| [deleteData](arkts-arkdata-unifieddatachannel-deletedata-f.md#deletedata-1) | Deletes data from the UDMF public data channel and returns the deleted data set. This API uses an asynchronous callback to return the result. |
| [deleteData](arkts-arkdata-unifieddatachannel-deletedata-f.md#deletedata-2) | Deletes data from the UDMF public data channel and returns the deleted data set. This API uses a promise to return the result asynchronously. |
| [insertData](arkts-arkdata-unifieddatachannel-insertdata-f.md#insertdata-1) | Writes data to the public data channel of the UDMF and generates a unique identifier for the data. This API uses an asynchronous callback to return the result. **Implementation mechanism** After receiving the UnifiedData object, the system verifies data integrity and serializes the data for storage. It routes the data to the corresponding storage space based on the intention value and generates a unique identifier key. The validity period of the data in the public data channel is managed by the system, and the default policy is to automatically clear the data after the application exits. |
| [insertData](arkts-arkdata-unifieddatachannel-insertdata-f.md#insertdata-2) | Writes data to the public data channel of UDMF and generates a unique identifier for the data. This API uses a promise to return the result asynchronously. |
| [queryData](arkts-arkdata-unifieddatachannel-querydata-f.md#querydata-1) | Queries data in the UDMF public data channel. This API uses an asynchronous callback to return the result. |
| [queryData](arkts-arkdata-unifieddatachannel-querydata-f.md#querydata-2) | Queries data in the UDMF public data channel. This API uses a promise to return the result asynchronously. |
| [removeAppShareOptions](arkts-arkdata-unifieddatachannel-removeappshareoptions-f.md#removeappshareoptions-1) | Clears the control information set by [setAppShareOptions](arkts-arkdata-unifieddatachannel-setappshareoptions-f.md). After this API is called successfully, the control information set by setAppShareOptions is cleared, and the in-app drag-and-drop channel data is restored to the default usage scope. |
| [setAppShareOptions](arkts-arkdata-unifieddatachannel-setappshareoptions-f.md#setappshareoptions-1) | Sets the usage scope of the data in the in-app drag-and-drop data channel, as defined by [ShareOptions](arkts-arkdata-unifieddatachannel-shareoptions-e.md). Currently, only the DRAG data channel supports this management setting. After the call succeeds, the usage scope of the data in the in-app drag-and-drop data channel is set to the specified ShareOptions value. |
| [updateData](arkts-arkdata-unifieddatachannel-updatedata-f.md#updatedata-1) | Updates the data in the public data channel that has been written to UDMF. This API uses an asynchronous callback to return the result. |
| [updateData](arkts-arkdata-unifieddatachannel-updatedata-f.md#updatedata-2) | Updates the data in the public data channel that has been written to UDMF. This API uses a promise to return the result. |

### Classes

| Name | Description |
| --- | --- |
| [ApplicationDefinedRecord](arkts-arkdata-unifieddatachannel-applicationdefinedrecord-c.md) | ApplicationDefinedRecord is a subclass of [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) and the base class of application-defined data types. It describes custom data types that circulate only within the application ecosystem. Applications can extend custom data types based on this class. |
| [Audio](arkts-arkdata-unifieddatachannel-audio-c.md) | Audio data, a subclass of [File](arkts-arkdata-unifieddatachannel-file-c.md), used to describe an audio file. |
| [File](arkts-arkdata-unifieddatachannel-file-c.md) | The File type data is a subclass of [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) and the base class of file type data. It is used to describe file type data. You are advised to use subclasses of File, such as [Image](arkts-arkdata-unifieddatachannel-image-c.md), [Video](arkts-arkdata-unifieddatachannel-video-c.md), and [Folder](arkts-arkdata-unifieddatachannel-folder-c.md), to describe data. |
| [Folder](arkts-arkdata-unifieddatachannel-folder-c.md) | Folder type data, a subclass of [File](arkts-arkdata-unifieddatachannel-file-c.md), used to describe a folder. |
| [HTML](arkts-arkdata-unifieddatachannel-html-c.md) | The HTML type data, a subclass of [Text](arkts-arkdata-unifieddatachannel-text-c.md), is used to describe HyperText Markup Language data. |
| [Hyperlink](arkts-arkdata-unifieddatachannel-hyperlink-c.md) | A subclass of [Text](arkts-arkdata-unifieddatachannel-text-c.md) that describes hyperlink data. |
| [Image](arkts-arkdata-unifieddatachannel-image-c.md) | Represents image data. It is a subclass of [File](arkts-arkdata-unifieddatachannel-file-c.md) and is used to describe an image file. |
| [PlainText](arkts-arkdata-unifieddatachannel-plaintext-c.md) | A subclass of [Text](arkts-arkdata-unifieddatachannel-text-c.md) that describes plain text data. |
| [Summary](arkts-arkdata-unifieddatachannel-summary-c.md) | Describes the data summary of a unified data object, including the data type and size. |
| [SystemDefinedAppItem](arkts-arkdata-unifieddatachannel-systemdefinedappitem-c.md) | System-defined desktop icon data, which is a subclass of [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md). |
| [SystemDefinedForm](arkts-arkdata-unifieddatachannel-systemdefinedform-c.md) | Represents the system-defined widget data, which is a subclass of [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md). |
| [SystemDefinedPixelMap](arkts-arkdata-unifieddatachannel-systemdefinedpixelmap-c.md) | An image data type corresponding to the system-defined [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) data type. It is a subclass of [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md) and stores only the binary data of a PixelMap. |
| [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md) | SystemDefinedRecord is a subclass of [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) and the base class of OpenHarmony system-specific data types. It is used to describe data types that circulate only within the OpenHarmony system. You are advised to use subclasses of SystemDefinedRecord, such as [SystemDefinedForm](arkts-arkdata-unifieddatachannel-systemdefinedform-c.md), [SystemDefinedAppItem](arkts-arkdata-unifieddatachannel-systemdefinedappitem-c.md), and [SystemDefinedPixelMap](arkts-arkdata-unifieddatachannel-systemdefinedpixelmap-c.md), to describe data. |
| [Text](arkts-arkdata-unifieddatachannel-text-c.md) | Represents text data. It is a subclass of [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) and the base class of text data, used to describe text data. You are advised to use subclasses of Text, such as [PlainText](arkts-arkdata-unifieddatachannel-plaintext-c.md), [Hyperlink](arkts-arkdata-unifieddatachannel-hyperlink-c.md), and [HTML](arkts-arkdata-unifieddatachannel-html-c.md), to describe data. |
| [UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md) | Represents the Unified Data Object of UDMF, which provides methods to encapsulate a group of data records. |
| [UnifiedDataProperties](arkts-arkdata-unifieddatachannel-unifieddataproperties-c.md) | Defines the properties of the data records in the unified data object, including the timestamp, tag, pasting range, and additional data. |
| [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) | An abstract definition of the data content supported by UDMF, called a data record. A unified data object contains one or more data records, for example, a text record, an image record, and an HTML record. Since API version 15, different data formats of the same content can be added to a data record (for example, the same text can be stored in plain text, HTML, or hyperlink formats at the same time). Data consumers can obtain the corresponding format through the getEntry method based on their service requirements. |
| [Video](arkts-arkdata-unifieddatachannel-video-c.md) | Video data, a subclass of [File](arkts-arkdata-unifieddatachannel-file-c.md), used to describe a video file. |

### Interfaces

| Name | Description |
| --- | --- |
| [DataLoadInfo](arkts-arkdata-unifieddatachannel-dataloadinfo-i.md) | Describes the type and quantity of the data to be loaded. |
| [DataLoadParams](arkts-arkdata-unifieddatachannel-dataloadparams-i.md) | Describes the data loading policy of the sender in delayed loading scenarios. |
| [GetDataParams](arkts-arkdata-unifieddatachannel-getdataparams-i.md) | Represents the parameters used to obtain data from UDMF, including the destination path, file conflict options, and progress bar type. |
| [Options](arkts-arkdata-unifieddatachannel-options-i.md) | The data operation APIs provided by UDMF include three optional parameters: intention, key, and visibility. If an API does not require these parameters, they can be left unspecified. For details, see the parameter description of the specific API. |
| [ProgressInfo](arkts-arkdata-unifieddatachannel-progressinfo-i.md) | Defines the data for progress reporting. |

### Types

| Name | Description |
| --- | --- |
| [DataLoadHandler](arkts-arkdata-unifieddatachannel-dataloadhandler-t.md) | Defines the handler for delayed data loading. It allows the data sender to dynamically generate data based on the information passed in by the receiver, enabling more flexible and precise data interaction strategies. This handler is a synchronous function and is suitable for simple business logic. If the business logic is complex or takes a long time to execute (more than 3 seconds), use the asynchronous handler [DelayedDataLoadHandler](arkts-arkdata-unifieddatachannel-delayeddataloadhandler-t.md). |
| [DataProgressListener](arkts-arkdata-unifieddatachannel-dataprogresslistener-t.md) | Defines the listener callback used to obtain progress information and data. |
| [DelayedDataLoadHandler](arkts-arkdata-unifieddatachannel-delayeddataloadhandler-t.md) | Defines the handler for delayed data loading. It allows the data sender to dynamically generate data based on the information passed in by the receiver, enabling a more flexible and precise data interaction strategy. The result is returned asynchronously through a promise. |
| [GetDelayData](arkts-arkdata-unifieddatachannel-getdelaydata-t.md) | A deferred wrapper for UnifiedData that supports deferred data retrieval. When the data receiver requests a specific type of data, the system triggers this callback, and the data sender can dynamically generate the data in the callback instead of preparing all data in advance. Currently, only the same-device clipboard scenario is supported. |
| [ValueType](arkts-arkdata-unifieddatachannel-valuetype-t.md) | Represents the data field types allowed for a unified data record. |

### Enums

| Name | Description |
| --- | --- |
| [FileConflictOptions](arkts-arkdata-unifieddatachannel-fileconflictoptions-e.md) | Enumerates the optional policies for file copy conflicts. |
| [Intention](arkts-arkdata-unifieddatachannel-intention-e.md) | Enumerates the data channels supported by UDMF. It is mainly used to identify the different business scenarios targeted by various UDMF data channels. |
| [ListenerStatus](arkts-arkdata-unifieddatachannel-listenerstatus-e.md) | Enumerates the status codes returned when obtaining data from UDMF. |
| [ProgressIndicator](arkts-arkdata-unifieddatachannel-progressindicator-e.md) | Enumerates the progress indicator options, which determine whether to use the system default progress display. |
| [ShareOptions](arkts-arkdata-unifieddatachannel-shareoptions-e.md) | Enumerates the usage scope types supported by UDMF within a device. |
| [UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md) | URI authorization policy in drag-and-drop scenarios. |
| [Visibility](arkts-arkdata-unifieddatachannel-visibility-e.md) | Enumerates the visibility levels of data. |
