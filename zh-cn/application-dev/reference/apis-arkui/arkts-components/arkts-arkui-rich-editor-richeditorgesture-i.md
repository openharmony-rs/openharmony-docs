# RichEditorGesture

用户手势事件。

**起始版本：** 11

<!--Device-unnamed-declare interface RichEditorGesture--><!--Device-unnamed-declare interface RichEditorGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClick

```TypeScript
onClick?: Callback<ClickEvent>
```

[ClickEvent](arkts-arkui-common-clickevent-i.md)为用户点击事件。

点击完成时回调事件。

双击时，第一次点击触发回调事件。

**类型：** Callback<ClickEvent>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorGesture-onClick?: Callback<ClickEvent>--><!--Device-RichEditorGesture-onClick?: Callback<ClickEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onLongPress

```TypeScript
onLongPress?: Callback<GestureEvent>
```

[GestureEvent](../../../../reference/apis-arkui/arkui-ts/ts-gesture-common.md#gestureevent对象说明)为用户长按事件。

长按完成时回调事件。

**类型：** Callback<GestureEvent>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorGesture-onLongPress?: Callback<GestureEvent>--><!--Device-RichEditorGesture-onLongPress?: Callback<GestureEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

