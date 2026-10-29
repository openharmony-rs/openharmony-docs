# @StorageProp

```TypeScript
declare const StorageProp: (value: string) => PropertyDecorator
```

@StorageProp用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)中，与[AppStorage](../arkts-apis/arkts-arkui-appstorage-c.md)中对应的属性建立单向数据同步。AppStorage中对应属性的变化会同步到@StorageProp装饰的变量，但仅修改@StorageProp装饰的变量不会同步回AppStorage。适用于需要跨页面、跨Ability感知AppStorage全局状态变化且仅保持单向数据流的场景，可避免不必要的数据回写。

开发指南参考：[AppStorage：应用全局的UI状态存储](../../../ui/state-management/arkts-appstorage.md)。

value：AppStorage中的属性键名，用于与该键名对应的属性建立单向数据同步。若AppStorage中已存在该键名对应的属性，则\@StorageProp装饰变量的本地初始值将被AppStorage中对应属性的值覆盖；若AppStorage中不存在该键名对应的属性，则使用\@StorageProp装饰变量的本地初始值在AppStorage中创建该属性。PropertyDecorator：属性装饰器，开发者无需关注该返回值。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-declare const StorageProp: (value: string) => PropertyDecorator--><!--Device-unnamed-declare const StorageProp: (value: string) => PropertyDecorator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
