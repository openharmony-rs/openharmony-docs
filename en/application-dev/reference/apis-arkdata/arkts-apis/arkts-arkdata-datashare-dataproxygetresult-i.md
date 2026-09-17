# DataProxyGetResult

Defines a struct for obtaining the batch operation result of shared configuration.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## allowList

```TypeScript
allowList: string[] | undefined
```

If the operation is successful, the allowlist is the one set in shared configuration; otherwise, the allowlist is undefined. Only the publisher can obtain the allowlist. Other applications can obtain only the value.

**Type:** string[] &#124; undefined

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

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

## value

```TypeScript
value: ValueType | undefined
```

If the operation is successful, the value is the one set in shared configuration; otherwise, the value is undefined.

**Type:** [ValueType](arkts-arkdata-valuetype-t.md) &#124; undefined

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer
