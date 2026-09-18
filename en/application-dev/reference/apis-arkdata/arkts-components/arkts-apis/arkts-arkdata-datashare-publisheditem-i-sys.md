# PublishedItem (System API)

Defines the data to publish.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## data

```TypeScript
data: string | ArrayBuffer
```

Data to publish. If the data to publish exceeds 20 KB, you are advised to use the data in ArrayBuffer format.

**Type:** string &#124; ArrayBuffer

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## key

```TypeScript
key: string
```

Key of the data to publish.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## subscriberId

```TypeScript
subscriberId: string
```

Subscriber ID.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.
