# FocusMovement

设置对应的按键对应的走焦目的组件，缺省则遵循默认走焦规则。

> **说明：**  
>  
> 直接使用focusControl可能导致[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用getUIContext()获取  
> [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md)实例，并使用  
> [getFocusController](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#getfocuscontroller-1)获取绑定实例的focusControl。

**起始版本：** 18

<!--Device-unnamed-declare interface FocusMovement--><!--Device-unnamed-declare interface FocusMovement-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backward

```TypeScript
backward?: string
```

通过shift+tab键走焦到组件的id。

默认值为重置backward为空。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-FocusMovement-backward?: string--><!--Device-FocusMovement-backward?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## down

```TypeScript
down?: string
```

通过方向键下键走焦到组件的id。

默认值为重置down为空。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-FocusMovement-down?: string--><!--Device-FocusMovement-down?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## forward

```TypeScript
forward?: string
```

通过tab键走焦到组件的id。

默认值为重置forward为空。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-FocusMovement-forward?: string--><!--Device-FocusMovement-forward?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## left

```TypeScript
left?: string
```

通过方向键左键走焦到组件的id。

默认值为重置left为空。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-FocusMovement-left?: string--><!--Device-FocusMovement-left?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## right

```TypeScript
right?: string
```

通过方向键右键走焦到组件的id。

默认值为重置right为空。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-FocusMovement-right?: string--><!--Device-FocusMovement-right?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## up

```TypeScript
up?: string
```

通过方向键上键走焦到组件的id。

默认值为重置up为空。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-FocusMovement-up?: string--><!--Device-FocusMovement-up?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

