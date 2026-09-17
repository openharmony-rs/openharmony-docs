# DataProxyResult

Defines a struct for the batch operation result of shared configuration.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## result

```TypeScript
result: DataProxyErrorCode
```

Operation result code.

**Type:** [DataProxyErrorCode](arkts-arkdata-datashare-dataproxyerrorcode-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## uri

```TypeScript
uri: string
```

URI to be operated, with a maximum of 256 bytes. The value is fixed at the format of **"datashareproxy://{*bundleName*}/{*path*}"**, in which **bundleName** indicates the bundle name of the publisher application, and **path** can be set to any value but must be unique in the same application.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer
