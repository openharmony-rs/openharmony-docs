# DataProxyChangeInfo

```TypeScript
interface DataProxyChangeInfo
```

Defines a struct for notifying subscribers of the shared configuration changes, including data change type, URI, and content.

**Since:** 20

<!--Device-dataShare-interface DataProxyChangeInfo--><!--Device-dataShare-interface DataProxyChangeInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## type

```TypeScript
type: ChangeType
```

Data change type.

**Type:** [ChangeType](arkts-arkdata-datashare-changetype-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyChangeInfo-type: ChangeType--><!--Device-DataProxyChangeInfo-type: ChangeType-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## uri

```TypeScript
uri: string
```

URI to change.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyChangeInfo-uri: string--><!--Device-DataProxyChangeInfo-uri: string-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## value

```TypeScript
value: ValueType
```

Changed data.

**Type:** [ValueType](arkts-arkdata-valuetype-t.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyChangeInfo-value: ValueType--><!--Device-DataProxyChangeInfo-value: ValueType-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## values

```TypeScript
values?: ValueType[]
```

Changed data of the multi-value type. If the changed data is not multi-value type, the **values** is undefined.

**Type:** [ValueType](arkts-arkdata-valuetype-t.md)[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyChangeInfo-values?: ValueType[]--><!--Device-DataProxyChangeInfo-values?: ValueType[]-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer
