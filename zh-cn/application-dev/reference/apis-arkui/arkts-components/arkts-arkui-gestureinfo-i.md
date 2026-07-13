# GestureInfo

手势信息类型。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isSystemGesture

```TypeScript
isSystemGesture: boolean
```

当前手势是否为组件自带手势。true表示是，false表示否。

默认值：false

**类型：** boolean

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tag

```TypeScript
tag?: string
```

手势标志。

**说明：**

未设置事件标志tag属性时，tag不返回或返回undefined。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: GestureControl.GestureType
```

手势类型。

**说明：**

当手势为未暴露类型的系统内置手势事件时，type的值为-1。

**类型：** GestureControl.GestureType

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

