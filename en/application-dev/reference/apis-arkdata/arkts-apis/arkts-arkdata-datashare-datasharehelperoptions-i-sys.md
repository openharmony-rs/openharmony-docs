# DataShareHelperOptions (System API)

```TypeScript
interface DataShareHelperOptions
```

Specifies the optional parameters of [DataShareHelper](arkts-arkdata-datashare-datasharehelper-i-sys.md), including whether it is in proxy mode and the startup waiting time for non-silent access.

**Since:** 10

<!--Device-dataShare-interface DataShareHelperOptions--><!--Device-dataShare-interface DataShareHelperOptions-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## isProxy

```TypeScript
isProxy?: boolean
```

Default value: **false**. If set to **true**, the [DataShareHelper](arkts-arkdata-datashare-datasharehelper-i-sys.md) to be created is in proxy mode, and all operations do not open the data provider application unless the database does not exist. When the database does not exist, [createDataShareHelper](arkts-arkdata-datashare-createdatasharehelper-f-sys.md) starts the data provider to create the database.

**Type:** boolean

**Default:** false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataShareHelperOptions-isProxy?: boolean--><!--Device-DataShareHelperOptions-isProxy?: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## waitTime

```TypeScript
waitTime?: number
```

Waiting time for starting the data provider process, in seconds. The default value is **2**. The value must be greater than 0.

**Type:** number

**Default:** 2

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataShareHelperOptions-waitTime?: int--><!--Device-DataShareHelperOptions-waitTime?: int-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.
