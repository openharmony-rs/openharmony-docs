# NavDestinationInfo

NavDestination组件信息，由系统返回给开发者。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-uiObserver-export interface NavDestinationInfo--><!--Device-uiObserver-export interface NavDestinationInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

NavDestination在页面栈中的索引。 取值应≥0。

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationInfo-index: number--><!--Device-NavDestinationInfo-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: NavDestinationMode
```

NavDestination类型。 默认值：NavDestinationMode.Standard。

**类型：** [NavDestinationMode](../../apis-na/arkts-apis/arkts-na-navdestination-navdestinationmode-e.md)

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationInfo-mode?: NavDestinationMode--><!--Device-NavDestinationInfo-mode?: NavDestinationMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: ResourceStr
```

NavDestination组件的名称。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationInfo-name: ResourceStr--><!--Device-NavDestinationInfo-name: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestinationId

```TypeScript
navDestinationId: string
```

Auto-generated navDestination id, which is different from common property id of Component.

**类型：** string

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationInfo-navDestinationId: string--><!--Device-NavDestinationInfo-navDestinationId: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navigationId

```TypeScript
navigationId: ResourceStr
```

包含NavDestination组件的Navigation组件的id。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationInfo-navigationId: ResourceStr--><!--Device-NavDestinationInfo-navigationId: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## param

```TypeScript
param?: Object
```

The detailed parameter of NavDestination.

**类型：** Object

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationInfo-param?: Object--><!--Device-NavDestinationInfo-param?: Object-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Size
```

NavDestination组件的大小,单位是vp。

**类型：** Size

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationInfo-size?: Size--><!--Device-NavDestinationInfo-size?: Size-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state: NavDestinationState
```

NavDestination组件的状态。

**类型：** [NavDestinationState](arkts-arkui-uiobserver-navdestinationstate-e.md)

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationInfo-state: NavDestinationState--><!--Device-NavDestinationInfo-state: NavDestinationState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## uniqueId

```TypeScript
uniqueId?: number
```

NavDestination组件的uniqueId。

**类型：** number

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationInfo-uniqueId?: number--><!--Device-NavDestinationInfo-uniqueId?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

