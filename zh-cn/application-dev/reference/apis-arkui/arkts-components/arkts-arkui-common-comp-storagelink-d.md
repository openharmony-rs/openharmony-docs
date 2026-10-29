# @StorageLink

```TypeScript
declare const StorageLink: (value: string) => PropertyDecorator
```

@StorageLink是[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)的装饰器，用于与[AppStorage](../arkts-apis/arkts-arkui-appstorage-c.md)中指定键名的属性建立双向数据同步：当@StorageLink装饰的变量发生变化时，变更会同步到AppStorage中该键名对应的属性；当AppStorage中该键名对应的属性发生变化时，变更也会同步回@StorageLink装饰的变量。适用于需要跨页面、跨Ability共享AppStorage全局状态并与AppStorage保持双向数据同步的场景，可避免逐层传递状态数据，保证数据一致性。

开发指南参考：[AppStorage：应用全局的UI状态存储](../../../ui/state-management/arkts-appstorage.md)。

value：AppStorage中的属性键名，用于与该键名对应的属性建立双向数据同步。若AppStorage中已存在该键名对应的属性，则\@StorageLink装饰变量的本地初始值将被AppStorage中对应属性的值覆盖；若AppStorage中不存在该键名对应的属性，则以\@StorageLink装饰变量的本地初始值在AppStorage中创建对应属性。PropertyDecorator：属性装饰器，开发者无需关注该返回值。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-declare const StorageLink: (value: string) => PropertyDecorator--><!--Device-unnamed-declare const StorageLink: (value: string) => PropertyDecorator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
