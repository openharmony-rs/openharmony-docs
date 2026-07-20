# NavContentInfo

跳转Destination信息。

**起始版本：** 11

<!--Device-unnamed-declare interface NavContentInfo--><!--Device-unnamed-declare interface NavContentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

NavDestination在NavPathStack中的序号， 如果为根视图(NavBar)，则返回值为 -1。

取值范围：[-1, +∞)。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavContentInfo-index: number--><!--Device-NavContentInfo-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: NavDestinationMode
```

NavDestination的模式，如果是根视图(NavBar)，则返回值为undefined。

**类型：** NavDestinationMode

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavContentInfo-mode?: NavDestinationMode--><!--Device-NavContentInfo-mode?: NavDestinationMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name?: string
```

NavDestination名称，如果为根视图(NavBar)，则返回值为undefined。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavContentInfo-name?: string--><!--Device-NavContentInfo-name?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestinationId

```TypeScript
navDestinationId?: string
```

NavDestination的唯一标识符。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavContentInfo-navDestinationId?: string--><!--Device-NavContentInfo-navDestinationId?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## param

```TypeScript
param?: Object
```

NavDestination页面加载的参数。

**类型：** Object

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavContentInfo-param?: Object--><!--Device-NavContentInfo-param?: Object-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

