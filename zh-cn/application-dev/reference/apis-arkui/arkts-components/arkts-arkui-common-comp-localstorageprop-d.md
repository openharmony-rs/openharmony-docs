# @LocalStorageProp

```TypeScript
declare const LocalStorageProp: (value: string) => PropertyDecorator
```

@LocalStorageProp在状态管理V1中使用，用于与LocalStorage中指定键名对应的属性建立单向数据同步：LocalStorage中对应属性值的变更会同步到@LocalStorageProp装饰的变量，但仅修改@LocalStorageProp装饰的变量不会同步回LocalStorage。适用于需要在多个组件间共享LocalStorage且仅保持单向数据流的场景，可避免不必要的数据回写。

开发指南参考：[LocalStorage：页面级UI状态存储](../../../ui/state-management/arkts-localstorage.md)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
