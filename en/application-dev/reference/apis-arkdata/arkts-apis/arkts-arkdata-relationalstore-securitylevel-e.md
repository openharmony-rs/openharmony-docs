# SecurityLevel

Enumerates the KV store security levels. Use the enum name rather than the enum value. You cannot change the security level of an RDB store from a higher level to a lower one.

> **NOTE:** 
> 
> To perform data sync operations, the RDB store security level must be lower than or equal to that of the peer
> device. For details, see [Access Control Mechanism in Cross-Device Sync]
> (../../../database/sync-app-data-across-devices-overview.md#access-control-mechanism-in-cross-device-sync).

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## S1

```TypeScript
S1 = 1
```

The RDB store security level is low. If data leakage occurs, minor impact will be caused on the database. An example would be a graph store containing non-sensitive system data such as wallpapers.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## S2

```TypeScript
S2 = 2
```

The RDB store security level is medium. If data leakage occurs, moderate impact will be caused on the database. An example would be a graph store containing audio and video data created by users or call logs.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## S3

```TypeScript
S3 = 3
```

The RDB store security level is high. If data leakage occurs, major impact will be caused on the database. An example would be a graph store containing user fitness, health, and location data.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## S4

```TypeScript
S4 = 4
```

The RDB store security level is critical. If data leakage occurs, severe impact will be caused on the database. An example would be a graph store containing authentication credentials and financial data.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
