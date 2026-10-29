# @LocalStorageProp

```TypeScript
declare const LocalStorageProp: (value: string) => PropertyDecorator
```

@LocalStorageProp在[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)中使用，用于与[LocalStorage](../arkts-apis/arkts-arkui-localstorage-c.md)中指定键名对应的属性建立单向数据同步：LocalStorage中对应属性值的变更会同步到@LocalStorageProp装饰的变量，但仅修改@LocalStorageProp装饰的变量不会同步回LocalStorage。适用于需要在多个组件间共享LocalStorage且仅保持单向数据流的场景，可避免不必要的数据回写。

开发指南参考：[LocalStorage：页面级UI状态存储](../../../ui/state-management/arkts-localstorage.md)。

value：LocalStorage中的属性键名，用于与该键名对应的属性建立单向数据同步。若LocalStorage中已存在该键名对应的属性，则\@LocalStorageProp装饰变量的本地初始值将被LocalStorage中对应属性的值覆盖；若LocalStorage中不存在该键名对应的属性，则使用\@LocalStorageProp装饰变量的本地初始值在LocalStorage中创建该属性。PropertyDecorator：属性装饰器，开发者无需关注该返回值。

**起始版本：** 9

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare const LocalStorageProp: (value: string) => PropertyDecorator--><!--Device-unnamed-declare const LocalStorageProp: (value: string) => PropertyDecorator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
