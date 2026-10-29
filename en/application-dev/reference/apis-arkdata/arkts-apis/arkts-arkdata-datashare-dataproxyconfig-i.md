# DataProxyConfig

```TypeScript
interface DataProxyConfig
```

Defines a struct for the data proxy configuration.

**Since:** 20

<!--Device-dataShare-interface DataProxyConfig--><!--Device-dataShare-interface DataProxyConfig-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## maxValueLength

```TypeScript
maxValueLength?: DataProxyMaxValueLength
```

Sets the maximum allowed length of the value of the shared configuration. If not filled, the default value is MAX_LENGTH_4K, that is, the maximum allowed length of the value of the shared configuration is 4096 bytes.

**Type:** [DataProxyMaxValueLength](arkts-arkdata-datashare-dataproxymaxvaluelength-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyConfig-maxValueLength?: DataProxyMaxValueLength--><!--Device-DataProxyConfig-maxValueLength?: DataProxyMaxValueLength-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## type

```TypeScript
type: DataProxyType
```

Type of the data proxy.

**Type:** [DataProxyType](arkts-arkdata-datashare-dataproxytype-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyConfig-type: DataProxyType--><!--Device-DataProxyConfig-type: DataProxyType-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer
