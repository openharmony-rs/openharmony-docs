# @LocalStorageLink

```TypeScript
declare const LocalStorageLink: (value: string) => PropertyDecorator
```

@LocalStorageLink在状态管理V1中使用，用于与LocalStorage中指定键名对应的属性建立双向数据同步：@LocalStorageLink装饰的变量与LocalStorage中对应属性任一方发生变化时，变更均会同步到另一方。适用于需要在多个组件间共享UI状态并与LocalStorage保持数据实时同步的场景，可避免逐层传递数据，保证跨组件数据一致性。

开发指南参考：[LocalStorage：页面级UI状态存储](../../../ui/state-management/arkts-localstorage.md)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
