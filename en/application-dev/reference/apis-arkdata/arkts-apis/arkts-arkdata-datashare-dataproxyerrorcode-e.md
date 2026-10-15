# DataProxyErrorCode

```TypeScript
enum DataProxyErrorCode
```

Enumerates the status code returned by the batch operations of shared configuration.

**Since:** 20

<!--Device-dataShare-enum DataProxyErrorCode--><!--Device-dataShare-enum DataProxyErrorCode-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## NO_PERMISSION

```TypeScript
NO_PERMISSION = 2
```

No permission to perform this operation on the URI.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyErrorCode-NO_PERMISSION = 2--><!--Device-DataProxyErrorCode-NO_PERMISSION = 2-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## OVER_LIMIT

```TypeScript
OVER_LIMIT = 3
```

The number of configurations published by the current application exceeds the upper limit of 32.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyErrorCode-OVER_LIMIT = 3--><!--Device-DataProxyErrorCode-OVER_LIMIT = 3-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## SUCCESS

```TypeScript
SUCCESS = 0
```

The operation is successful.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyErrorCode-SUCCESS = 0--><!--Device-DataProxyErrorCode-SUCCESS = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## URI_NOT_EXIST

```TypeScript
URI_NOT_EXIST = 1
```

The URI does not exist or the URI is not subscribed to.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataProxyErrorCode-URI_NOT_EXIST = 1--><!--Device-DataProxyErrorCode-URI_NOT_EXIST = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer
