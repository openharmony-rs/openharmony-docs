# PublishedDataChangeNode (System API)

Defines the subscription/unsubscription result of the changes in the published data.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the callback.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## data

```TypeScript
data: Array<PublishedItem>
```

Data of the callback.

**Type:** Array&lt;[PublishedItem](arkts-arkdata-datashare-publisheditem-i-sys.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.
