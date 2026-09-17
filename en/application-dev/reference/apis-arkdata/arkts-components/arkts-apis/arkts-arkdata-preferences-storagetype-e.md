# StorageType

Enumerates the storage types of preferences.

> **NOTE:** 
> 
> - Before using this mode, you are advised to call **isStorageTypeSupported** to check whether this storage type is supported.
> 
> - Once the storage type is selected and data instances are obtained via **getPreferences()**, the storage type cannot be changed.
> 
> - Data cannot be directly migrated between the **Preferences** instances that use different storage types. To migrate data between them, you need to read the data to be migrated and then write the data.
> 
> - If you need to change the storage directory of preferences, you cannot move or overwrite files. Instead, you need to read the data and then write the data.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

## XML

```TypeScript
XML = 0
```

[XML](../../../database/data-persistence-by-preferences.md#xml) format, which is the default storage type of **Preferences**.

In this mode, data is stored in XML format. Data operations are performed in the memory. To persist data, call **flush()**.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

## GSKV

```TypeScript
GSKV
```

[GSKV](../../../database/data-persistence-by-preferences.md#gskv) format.

Data is stored in GSKV mode. Data operations are flushed on a real-time basis without calling **flush()**.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core
