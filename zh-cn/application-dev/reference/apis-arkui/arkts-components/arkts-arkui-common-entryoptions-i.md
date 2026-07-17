# EntryOptions

定义Entry类装饰器的选项。

**起始版本：** 23

<!--Device-unnamed-declare interface EntryOptions--><!--Device-unnamed-declare interface EntryOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## routeName

```TypeScript
routeName? : string
```

命名路由名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EntryOptions-routeName? : string--><!--Device-EntryOptions-routeName? : string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## storage

```TypeScript
storage? : LocalStorage
```

要传递的LocalStorage。

**类型：** LocalStorage

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-EntryOptions-storage? : LocalStorage--><!--Device-EntryOptions-storage? : LocalStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## useSharedStorage

```TypeScript
useSharedStorage? : boolean
```

Determines whether to use the LocalStorage instance object returned by the LocalStorage.getShared() interface.

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-EntryOptions-useSharedStorage? : boolean--><!--Device-EntryOptions-useSharedStorage? : boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

