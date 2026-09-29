# @StorageProp

```TypeScript
declare const StorageProp: (value: string) => PropertyDecorator
```

**@StorageProp** is used in [state management V1](../../../ui/state-management/arkts-state-management-overview.md) to establish unidirectional data synchronization with the corresponding property in [AppStorage](../arkts-apis/arkts-arkui-appstorage-c.md). The changes of the corresponding property in AppStorage are synchronized to the variable decorated with **@StorageProp**, but the changes of the variable decorated with **@StorageProp** will not be synchronized back to AppStorage. It is applicable to scenarios where the global state changes of AppStorage need to be detected across pages and abilities and only unidirectional data flow is required. This can avoid unnecessary data writeback.

For details, see [AppStorage: Storing Application-wide UI State](../../../ui/state-management/arkts-appstorage.md).

value: Property key name in AppStorage, which is used to establish unidirectional data synchronization with the property corresponding to the key name. If the property corresponding to the key name already exists in AppStorage, the local initial value of the variable decorated with **@StorageProp** will be overwritten by the value of the corresponding property in AppStorage. If the property corresponding to the key name does not exist in AppStorage, the corresponding property will be created in AppStorage based on the local initial value of the variable decorated with **@StorageProp**. PropertyDecorator: Property decorator. You do not need to concern yourself with this return value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-unnamed-declare const StorageProp: (value: string) => PropertyDecorator--><!--Device-unnamed-declare const StorageProp: (value: string) => PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
