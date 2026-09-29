# @LocalStorageLink

```TypeScript
declare const LocalStorageLink: (value: string) => PropertyDecorator
```

**\@LocalStorageLink** is used in [state management V1](../../../ui/state-management/arkts-state-management-overview.md) to establish bidirectional data synchronization with the property corresponding to the specified key in [LocalStorage](../arkts-apis/arkts-arkui-localstorage-c.md). When either the variable decorated by **\@LocalStorageLink** or the corresponding property in LocalStorage changes, the change will be synchronized to the other party. This is applicable to scenarios where the UI state needs to be shared among multiple components and data needs to be synchronized with LocalStorage in real time. It can avoid layer-by-layer data transfer and ensure cross-component data consistency.

For details, see [LocalStorage: Storing Page-Level UI State](../../../ui/state-management/arkts-localstorage.md).

value: Property key name in LocalStorage, which is used to establish bidirectional data synchronization with the property corresponding to the key name. If the property corresponding to the key name already exists in LocalStorage, the local initial value of the variable decorated with **@LocalStorageLink** will be overwritten by the value of the corresponding property in LocalStorage. If the property corresponding to the key name does not exist in LocalStorage, the corresponding property will be created in LocalStorage based on the local initial value of the variable decorated with **@LocalStorageLink**. PropertyDecorator: Property decorator. You do not need to concern yourself with this return value.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-unnamed-declare const LocalStorageLink: (value: string) => PropertyDecorator--><!--Device-unnamed-declare const LocalStorageLink: (value: string) => PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
