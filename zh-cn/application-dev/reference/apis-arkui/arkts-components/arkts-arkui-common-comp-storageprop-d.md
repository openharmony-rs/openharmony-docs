# @StorageProp

```TypeScript
declare const StorageProp: (value: string) => PropertyDecorator
```

@StorageProp用于状态管理V1中，与AppStorage中对应的属性建立单向数据同步。AppStorage中对应属性的变化会同步到@StorageProp装饰的变量，但仅修改@StorageProp装饰的变量不会同步回AppStorage。适用于需要跨页面、跨Ability感知AppStorage全局状态变化且仅保持单向数据流的场景，可避免不必要的数据回写。

开发指南参考：[AppStorage：应用全局的UI状态存储](../../../ui/state-management/arkts-appstorage.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
