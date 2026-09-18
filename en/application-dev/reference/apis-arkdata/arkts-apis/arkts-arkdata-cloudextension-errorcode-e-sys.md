# ErrorCode (System API)

Enumerates the device-cloud sync states. Use the enum name rather than the enum value.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## SUCCESS

```TypeScript
SUCCESS = 0
```

The device-cloud sync is successful.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## UNKNOWN_ERROR

```TypeScript
UNKNOWN_ERROR = 1
```

An unknown error occurs during the device-cloud sync process.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## NETWORK_ERROR

```TypeScript
NETWORK_ERROR = 2
```

A network error occurs during the device-cloud sync process.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## CLOUD_DISABLED

```TypeScript
CLOUD_DISABLED = 3
```

Cloud sync is disabled.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## LOCKED_BY_OTHERS

```TypeScript
LOCKED_BY_OTHERS = 4
```

The device-cloud sync of another device is being performed. The sync of the local device can be performed only when the device-cloud resources are available.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## RECORD_LIMIT_EXCEEDED

```TypeScript
RECORD_LIMIT_EXCEEDED = 5
```

The number of records or size of the data to be synced exceeds the maximum. The maximum value is configured on the cloud.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## NO_SPACE_FOR_ASSET

```TypeScript
NO_SPACE_FOR_ASSET = 6
```

The remaining cloud space is less than the size of the data to be synced.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
