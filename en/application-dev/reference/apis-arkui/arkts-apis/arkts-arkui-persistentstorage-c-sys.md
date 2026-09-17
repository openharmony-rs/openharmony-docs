# PersistentStorage

For details about how to use PersistentStorage on the UI, see [PersistentStorage: Persisting Application State](../../../ui/state-management/arkts-persiststorage.md).

> **NOTE:** 

> Since API version 12, PersistentStorage supports **null** and **undefined**.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(appStorage: AppStorage, storage: Storage)
```

Constructor.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appStorage | [AppStorage](arkts-arkui-appstorage-c.md) | Yes | Application-level storage. |
| storage | [Storage](arkts-arkui-storage-c-sys.md) | Yes | Storage. |
