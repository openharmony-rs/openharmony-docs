# @LocalStorageLink

```TypeScript
declare const LocalStorageLink: (value: string) => PropertyDecorator
```

@LocalStorageLink在[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)中使用，用于与[LocalStorage](../arkts-apis/arkts-arkui-localstorage-c.md)中指定键名对应的属性建立双向数据同步：@LocalStorageLink装饰的变量与LocalStorage中对应属性任一方发生变化时，变更均会同步到另一方。适用于需要在多个组件间共享UI状态并与LocalStorage保持数据实时同步的场景，可避免逐层传递数据，保证跨组件数据一致性。

开发指南参考：[LocalStorage：页面级UI状态存储](../../../ui/state-management/arkts-localstorage.md)。

value：LocalStorage中的属性键名，用于与该键名对应的属性建立双向数据同步。若LocalStorage中已存在该键名对应的属性，则\@LocalStorageLink装饰变量的本地初始值将被LocalStorage中对应属性的值覆盖；若LocalStorage中不存在该键名对应的属性，则使用\@LocalStorageLink装饰变量的本地初始值在LocalStorage中创建该属性。PropertyDecorator：属性装饰器，开发者无需关注该返回值。

**起始版本：** 9

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-declare const LocalStorageLink: (value: string) => PropertyDecorator--><!--Device-unnamed-declare const LocalStorageLink: (value: string) => PropertyDecorator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
