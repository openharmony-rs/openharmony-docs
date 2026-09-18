# Template (System API)

Defines the struct of the template used in a subscription.

**Since:** 10

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

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## scheduler

```TypeScript
scheduler: string
```

Template scheduler SQL, which is embedded with a custom function. Currently, the **remindTimer** function is embedded. The **remindTimer** triggers a subscription-based update in specified scenarios.

The scheduler SQL statement is triggered when:

1. The subscribed data is modified.
2. The first subscription is added to the corresponding database.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

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

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.
