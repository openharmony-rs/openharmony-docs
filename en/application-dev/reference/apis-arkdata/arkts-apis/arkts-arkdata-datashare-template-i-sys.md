# Template (System API)

```TypeScript
interface Template
```

Defines the struct of the template used in a subscription.

**Since:** 10

<!--Device-dataShare-interface Template--><!--Device-dataShare-interface Template-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## predicates

```TypeScript
predicates: Record<string, string>
```

Predicates to use. When [**on**](arkts-arkdata-datashare-datasharehelper-i-sys.md#onrdbdatachange) is called, the predicates are used to generate data. This parameter applies only to RDB data storage.

**Type:** Record&lt;string, string&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-Template-predicates: Record<string, string>--><!--Device-Template-predicates: Record<string, string>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## scheduler

```TypeScript
scheduler: string
```

Scheduler SQL of the template. Custom functions are embedded for processing, and the preset custom function **remindTimer** is currently used. **remindTimer** triggers a subscription refresh once in the specified scenario. Trigger scenarios: 1. When data is modified and a subscription exists, the corresponding scheduler SQL statement is triggered. 2. When the first subscription of the corresponding database is added, the corresponding scheduler SQL statement is triggered.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-Template-scheduler: string--><!--Device-Template-scheduler: string-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## update

```TypeScript
update?: string
```

Update SQL statement of a specified template. The default value is an empty string. When [on](arkts-arkdata-datashare-datasharehelper-i-sys.md#onrdbdatachange) is called, the **update** parameter is used to update data. This parameter applies only to RDB data storage.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-Template-update?: string--><!--Device-Template-update?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.
