# RdbDataChangeNode (System API)

Represents the RDB data change result. The data returned by the callback is not larger than 10 MB in size.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## data

```TypeScript
data: Array<string>
```

Data of the callback. If an error occurs during callback data processing, the callback will not be triggered.

**Type:** Array&lt;string&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## templateId

```TypeScript
templateId: TemplateId
```

ID of the template that triggers the callback.

**Type:** [TemplateId](arkts-arkdata-datashare-templateid-i-sys.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

## uri

```TypeScript
uri: string
```

URI of the callback.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.
