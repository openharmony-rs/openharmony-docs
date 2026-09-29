# @StorageLink

```TypeScript
declare const StorageLink: (value: string) => PropertyDecorator
```

**@StorageLink** is used in [state management V1](../../../ui/state-management/arkts-state-management-overview.md) to establish bidirectional data synchronization with the property of a specified key in [AppStorage](../arkts-apis/arkts-arkui-appstorage-c.md). When the variable decorated with **@StorageLink** changes, the change is synchronized to the property corresponding to the key in AppStorage. When the property corresponding to the key in AppStorage changes, the change is also synchronized back to the variable decorated with **@StorageLink**. It is applicable to scenarios where the global state of AppStorage needs to be shared across pages and abilities and bidirectional data synchronization with AppStorage is required. It can avoid layer-by-layer state data transfer to ensure data consistency.

For details, see [AppStorage: Storing Application-wide UI State](../../../ui/state-management/arkts-appstorage.md).

value: Property key name in AppStorage, which is used to establish bidirectional data synchronization with the property corresponding to the key name. If the property corresponding to the key name already exists in AppStorage, the local initial value of the variable decorated with **@StorageLink** will be overwritten by the value of the corresponding property in AppStorage. If the property corresponding to the key name does not exist in AppStorage, the corresponding property will be created in AppStorage based on the local initial value of the variable decorated with **@StorageLink**. PropertyDecorator: Property decorator. You do not need to concern yourself with this return value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-unnamed-declare const StorageLink: (value: string) => PropertyDecorator--><!--Device-unnamed-declare const StorageLink: (value: string) => PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
