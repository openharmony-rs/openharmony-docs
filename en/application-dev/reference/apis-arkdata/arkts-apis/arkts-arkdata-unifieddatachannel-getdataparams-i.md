# GetDataParams

```TypeScript
interface GetDataParams
```

Represents the parameters used to obtain data from UDMF, including the destination path, file conflict options, and progress bar type.

For details about how to use it, see [Obtaining Data Asynchronously Through Drag-and-Drop].

**Since:** 15

<!--Device-unifiedDataChannel-interface GetDataParams--><!--Device-unifiedDataChannel-interface GetDataParams-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## dataProgressListener

```TypeScript
dataProgressListener: DataProgressListener
```

Represents the progress and data listener used when obtaining unified data.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-GetDataParams-dataProgressListener: DataProgressListener--><!--Device-GetDataParams-dataProgressListener: DataProgressListener-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## acceptableInfo

```TypeScript
acceptableInfo?: DataLoadInfo
```

efines the receiver's capability to accept data types and the number of data records. In lazy loading scenarios, the sender can generate and return more appropriate data content based on this information. It defaults to empty, indicating that the receiver's data acceptance capability is not provided.

**Type:** [DataLoadInfo](arkts-arkdata-unifieddatachannel-dataloadinfo-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-GetDataParams-acceptableInfo?: DataLoadInfo--><!--Device-GetDataParams-acceptableInfo?: DataLoadInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## destUri

```TypeScript
destUri?: string
```

Destination path for copying files. If file processing is not supported, this parameter does not need to be set and defaults to empty. If file processing is supported, it must be set to an existing directory. If the application involves complex file processing policies or needs to distinguish multi-path storage of files, it is recommended not to set this parameter and let the application complete the file copy processing on its own. When this parameter is not set, the obtained URI is the source path URI; when it is set, the obtained URI is the destination path URI.

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-GetDataParams-destUri?: string--><!--Device-GetDataParams-destUri?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## fileConflictOptions

```TypeScript
fileConflictOptions?: FileConflictOptions
```

Defines the options for file copy conflicts. The default value is OVERWRITE.

**Type:** [FileConflictOptions](arkts-arkdata-unifieddatachannel-fileconflictoptions-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-GetDataParams-fileConflictOptions?: FileConflictOptions--><!--Device-GetDataParams-fileConflictOptions?: FileConflictOptions-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## progressIndicator

```TypeScript
progressIndicator: ProgressIndicator
```

Defines the progress bar indicator options, which determine whether to use the system default progress display.

**Type:** [ProgressIndicator](arkts-arkdata-unifieddatachannel-progressindicator-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-GetDataParams-progressIndicator: ProgressIndicator--><!--Device-GetDataParams-progressIndicator: ProgressIndicator-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
