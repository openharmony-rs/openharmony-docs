# EntryOptions

页面入口配置选项，用于在\@Entry装饰页面时配置路由名称、状态存储和共享存储等参数。

**起始版本：** 10

<!--Device-unnamed-declare interface EntryOptions--><!--Device-unnamed-declare interface EntryOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## routeName

```TypeScript
routeName? : string
```

表示作为命名路由页面的名称。当需要通过命名路由方式跳转到此页面时，需设置此参数作为路由名称。不传入时，该页面不会注册为命名路由页面，无法通过命名路由方式跳转访问，仅作为默认入口页面加载。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-EntryOptions-routeName? : string--><!--Device-EntryOptions-routeName? : string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## storage

```TypeScript
storage? : LocalStorage
```

页面级的UI状态存储。当需要在页面外部预先创建并管理UI状态、或需要将已有的LocalStorage实例绑定到此页面以实现状态共享时，传入此参数。当未传入时，框架会创建一个新的LocalStorage实例作为默认值。当 useSharedStorage设置为true且storage已赋值时，useSharedStorage的值优先级更高。

**类型：** LocalStorage

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-EntryOptions-storage? : LocalStorage--><!--Device-EntryOptions-storage? : LocalStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## useSharedStorage

```TypeScript
useSharedStorage? : boolean
```

是否使用 [loadContent](../arkts-apis/arkts-arkui-window-windowstage-i.md#loadcontent) 传入的LocalStorage实例。默认值false。true：使用共享的LocalStorage实例（前提条件：需确保loadContent接口已传入LocalStorage实例；若未传入，则创建新的LocalStorage实例 ）。false：不使用共享的LocalStorage实例。当useSharedStorage设置为true且storage已赋值时，useSharedStorage的值优先级更高。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-EntryOptions-useSharedStorage? : boolean--><!--Device-EntryOptions-useSharedStorage? : boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

