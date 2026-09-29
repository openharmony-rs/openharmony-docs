# GetDataParams

```TypeScript
interface GetDataParams
```

Represents the parameters for obtaining data from UDMF, including the destination directory, option for resolving file conflicts, and progress indicator type.

For details, see [Obtaining Data Asynchronously Through Drag-and-Drop].

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

Indicates progress and data listener when getting unified data.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-GetDataParams-dataProgressListener: DataProgressListener--><!--Device-GetDataParams-dataProgressListener: DataProgressListener-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## acceptableInfo

```TypeScript
acceptableInfo?: DataLoadInfo
```

Indicates the supported data information.

**Type:** [DataLoadInfo](arkts-arkdata-unifieddatachannel-dataloadinfo-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-GetDataParams-acceptableInfo?: DataLoadInfo--><!--Device-GetDataParams-acceptableInfo?: DataLoadInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## destUri

```TypeScript
destUri?: string
```

Indicates the dest path uri where copy file will be copied to sandbox of application.

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-GetDataParams-destUri?: string--><!--Device-GetDataParams-destUri?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## fileConflictOptions

```TypeScript
fileConflictOptions?: FileConflictOptions
```

Indicates file conflict options when dest path has file with same name.

**Type:** [FileConflictOptions](arkts-arkdata-unifieddatachannel-fileconflictoptions-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-GetDataParams-fileConflictOptions?: FileConflictOptions--><!--Device-GetDataParams-fileConflictOptions?: FileConflictOptions-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## progressIndicator

```TypeScript
progressIndicator: ProgressIndicator
```

Indicates whether to use default system progress indicator.

**Type:** [ProgressIndicator](arkts-arkdata-unifieddatachannel-progressindicator-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-GetDataParams-progressIndicator: ProgressIndicator--><!--Device-GetDataParams-progressIndicator: ProgressIndicator-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
