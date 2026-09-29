# @LocalStorageProp

```TypeScript
declare const LocalStorageProp: (value: string) => PropertyDecorator
```

**\@LocalStorageProp** is used in [state management V1](../../../ui/state-management/arkts-state-management-overview.md) to establish unidirectional data synchronization with the property corresponding to the specified key in [LocalStorage](../arkts-apis/arkts-arkui-localstorage-c.md). After the establishment, changes to the property value in LocalStorage will be synchronized to the variable decorated with **\@LocalStorageProp**, but changes to the variable decorated with **\@LocalStorageProp** will not be synchronized back to LocalStorage. This is applicable to scenarios where LocalStorage needs to be shared among multiple components and only unidirectional data flow is required, avoiding unnecessary data writeback.

For details, see [LocalStorage: Storing Page-Level UI State](../../../ui/state-management/arkts-localstorage.md).

value: Property key name in LocalStorage, which is used to establish unidirectional data synchronization with the property corresponding to the key name. If the property corresponding to the key name already exists in LocalStorage, the local initial value of the variable decorated with **@LocalStorageProp** will be overwritten by the value of the corresponding property in LocalStorage. If the property corresponding to the key name does not exist in LocalStorage, the corresponding property will be created in LocalStorage based on the local initial value of the variable decorated with **@LocalStorageProp**. PropertyDecorator: Property decorator. You do not need to concern yourself with this return value.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare const LocalStorageProp: (value: string) => PropertyDecorator--><!--Device-unnamed-declare const LocalStorageProp: (value: string) => PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
