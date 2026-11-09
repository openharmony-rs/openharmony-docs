# NodeSensitiveInputEventType

```TypeScript
export const enum NodeSensitiveInputEventType
```

定义可通过节点敏感输入监听器上报的输入事件类型。事件对象由[NodeSensitiveInputInfo](arkts-arkui-arkui-uicontext-nodesensitiveinputinfo-i.md)中与该类型匹配的成员字段承载；例如，取值为**TOUCH**时，事件对象由**touchEvent**承载。

**起始版本：** 26.1.0

<!--Device-unnamed-export const enum NodeSensitiveInputEventType--><!--Device-unnamed-export const enum NodeSensitiveInputEventType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## KEY

```TypeScript
KEY = 2
```

上报的事件为按键事件。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-NodeSensitiveInputEventType-KEY = 2--><!--Device-NodeSensitiveInputEventType-KEY = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MOUSE

```TypeScript
MOUSE = 1
```

上报的事件为鼠标事件。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-NodeSensitiveInputEventType-MOUSE = 1--><!--Device-NodeSensitiveInputEventType-MOUSE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOUCH

```TypeScript
TOUCH = 0
```

上报的事件为触摸事件。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-NodeSensitiveInputEventType-TOUCH = 0--><!--Device-NodeSensitiveInputEventType-TOUCH = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
