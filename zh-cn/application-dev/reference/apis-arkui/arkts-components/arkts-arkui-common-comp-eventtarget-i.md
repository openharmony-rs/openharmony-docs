# EventTarget

```TypeScript
declare interface EventTarget
```

[BaseEvent](arkts-arkui-common-comp-baseevent-i.md)中参数target的类型。

触发事件的元素对象的显示区域。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## area

```TypeScript
area: Area
```

目标元素的区域信息。

**类型：** [Area](../arkts-apis/arkts-arkui-area-i.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

开发者设置的节点[id](arkts-arkui-common-comp-commonmethod-c.md#id)。默认值：undefined

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
