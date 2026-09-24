# UnifiedDataProperties

```TypeScript
class UnifiedDataProperties
```

Defines the properties of the data records in the unified data object, including the timestamp, tag, pasting range, and additional data.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## getDelayData

```TypeScript
getDelayData?: GetDelayData
```

Callback for obtaining the deferred data. Currently, it can be used only in the pasteboard application of the same device. The default value is **undefined**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## extras

```TypeScript
extras?: Record<string, object>
```

Object of the dictionary type used to set other properties. The default value is an empty dictionary object.

**Type:** Record&lt;string, object&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## shareOptions

```TypeScript
shareOptions?: ShareOptions
```

Range, in which [UnifiedData](arkts-arkdata-unifieddatachannel-unifieddataproperties-c.md) can be used. The default value is **CROSS_APP**.

**Type:** [ShareOptions](arkts-arkdata-unifieddatachannel-shareoptions-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## tag

```TypeScript
tag?: string
```

Customized tag. The default value is an empty string.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## timestamp

```TypeScript
readonly timestamp?: Date
```

Timestamp when [UnifiedData](arkts-arkdata-unifieddatachannel-unifieddataproperties-c.md) is generated. The default value is January 1, 1970 (UTC).

**Type:** Date

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uriAuthorizationPolicies

```TypeScript
uriAuthorizationPolicies?: Array<UriPermission>
```

URI authorization policies for the drag-and-drop scenario. The default value is READ+WRITE+PERSIST. This field takes effect only for a single data operation and has a lower priority. For details about the policies, see [UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md).

**Type:** Array&lt;[UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
