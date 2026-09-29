# PersistentStorage

```TypeScript
declare class PersistentStorage
```

Provides the persistent storage capability for UI states. It persists selected AppStorage properties to a file and restores these property values from the file and writes them to AppStorage when applications restart. For details about how to use it on the UI, see [PersistentStorage: Persisting Application State](../../../ui/state-management/arkts-persiststorage.md).

> **NOTE:** 

> Since API version 12, PersistentStorage supports **null** and **undefined**.

**Since:** 7

<!--Device-unnamed-declare class PersistentStorage--><!--Device-unnamed-declare class PersistentStorage-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(appStorage: AppStorage, storage: Storage)
```

A constructor.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PersistentStorage-constructor(appStorage: AppStorage, storage: Storage)--><!--Device-PersistentStorage-constructor(appStorage: AppStorage, storage: Storage)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appStorage | [AppStorage](arkts-arkui-appstorage-c.md) | Yes | Application-level storage object. PersistentStorage performs persistent management based on this object. |
| storage | [Storage](arkts-arkui-storage-c-sys.md) | Yes | Persistent storage object, used to actually read and write persistent data. |
