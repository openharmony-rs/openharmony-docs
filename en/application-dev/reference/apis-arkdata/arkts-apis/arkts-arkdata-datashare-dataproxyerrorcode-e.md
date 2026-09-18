# DataProxyErrorCode

Enumerates the status code returned by the batch operations of shared configuration.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## SUCCESS

```TypeScript
SUCCESS = 0
```

The operation is successful.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## URI_NOT_EXIST

```TypeScript
URI_NOT_EXIST = 1
```

The URI does not exist or the URI is not subscribed to.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## NO_PERMISSION

```TypeScript
NO_PERMISSION = 2
```

No permission to perform this operation on the URI.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## OVER_LIMIT

```TypeScript
OVER_LIMIT = 3
```

The number of configurations published by the current application exceeds the upper limit of 32.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer
