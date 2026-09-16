# @StorageLink

```TypeScript
declare const StorageLink: (value: string) => PropertyDecorator
```

@StorageLink是状态管理V1的装饰器，用于与AppStorage中指定键名的属性建立双向数据同步：当@StorageLink装饰的变量发生变化时，变更会同步到AppStorage中该键名对应的属性；当AppStorage中该键名对应的属性发生变化时，变更也会同步回@StorageLink装饰的变量。适用于需要跨页面、跨Ability共享AppStorage全局状态并与AppStorage保持双向数据同步的场景，可避免逐层传递状态数据，保证数据一致性。

开发指南参考：[AppStorage：应用全局的UI状态存储](../../../ui/state-management/arkts-appstorage.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
