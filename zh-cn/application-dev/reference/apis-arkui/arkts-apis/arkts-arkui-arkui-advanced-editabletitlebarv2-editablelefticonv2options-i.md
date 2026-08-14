# EditableLeftIconV2Options

左侧图标配置选项接口。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare interface EditableLeftIconV2Options--><!--Device-unnamed-export declare interface EditableLeftIconV2Options-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

是否默认获取焦点。 true：获焦。 false：不获焦。 默认值：false。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditableLeftIconV2Options-defaultFocus?: boolean--><!--Device-EditableLeftIconV2Options-defaultFocus?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconType

```TypeScript
iconType?: EditableLeftIconTypeV2
```

图标类型。

**类型：** [EditableLeftIconTypeV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticontypev2-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditableLeftIconV2Options-iconType?: EditableLeftIconTypeV2--><!--Device-EditableLeftIconV2Options-iconType?: EditableLeftIconTypeV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAction

```TypeScript
onAction?: OnActionCallback
```

点击左侧图标的回调函数。未设置时，Back类型默认执行路由返回，Cancel类型无操作。

**类型：** [OnActionCallback](arkts-arkui-onactioncallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditableLeftIconV2Options-onAction?: OnActionCallback--><!--Device-EditableLeftIconV2Options-onAction?: OnActionCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

