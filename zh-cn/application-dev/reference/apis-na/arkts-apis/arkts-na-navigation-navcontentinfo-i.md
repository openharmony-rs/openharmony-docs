# NavContentInfo

跳转Destination信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface NavContentInfo--><!--Device-unnamed-export declare interface NavContentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: int
```

NavDestination在NavPathStack中的序号， 如果为根视图(NavBar)，则返回值为 -1。 取值应为≥-1的整数。 取值范围为全体整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavContentInfo-index: int--><!--Device-NavContentInfo-index: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: NavDestinationMode
```

NavDestination的模式，如果是根视图(NavBar)，则返回值为undefined。 默认值： NavDestinationMode.STANDARD。

**类型：** [NavDestinationMode](arkts-na-navdestination-navdestinationmode-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavContentInfo-mode?: NavDestinationMode--><!--Device-NavContentInfo-mode?: NavDestinationMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name?: string
```

NavDestination名称，如果为根视图(NavBar)，则返回值为undefined。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavContentInfo-name?: string--><!--Device-NavContentInfo-name?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestinationId

```TypeScript
navDestinationId?: string
```

NavDestination的唯一标识符。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavContentInfo-navDestinationId?: string--><!--Device-NavContentInfo-navDestinationId?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## param

```TypeScript
param?: Object
```

NavDestination页面加载的参数。

**类型：** Object

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavContentInfo-param?: Object--><!--Device-NavContentInfo-param?: Object-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

