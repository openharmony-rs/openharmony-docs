# DataProxyConfig

Defines a struct for the data proxy configuration.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## maxValueLength

```TypeScript
maxValueLength?: DataProxyMaxValueLength
```

Sets the maximum length of the data proxy value. The default value is MAX_LENGTH_4K, indicating that the maximum value length is 4096 bytes. If the length of the value that is actually transferred or obtained exceeds the maximum value length specified by this parameter, the publish or get operation will fail. Default value: MAX_LENGTH_4K.

**Type:** [DataProxyMaxValueLength](arkts-arkdata-datashare-dataproxymaxvaluelength-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## type

```TypeScript
type: DataProxyType
```

Type of the data proxy.

**Type:** [DataProxyType](arkts-arkdata-datashare-dataproxytype-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer
