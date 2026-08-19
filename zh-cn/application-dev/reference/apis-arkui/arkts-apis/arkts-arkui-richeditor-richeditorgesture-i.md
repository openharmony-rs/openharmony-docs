# RichEditorGesture

用户手势事件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RichEditorGesture--><!--Device-unnamed-export declare interface RichEditorGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClick

```TypeScript
onClick?: Callback<ClickEvent>
```

[ClickEvent](../arkts-components/arkts-arkui-clickevent-i.md)为用户点击事件。 点击完成时回调事件。 双击时，第一次点击触发回调事件。

**类型：** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[ClickEvent](../arkts-components/arkts-arkui-clickevent-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorGesture-onClick?: Callback<ClickEvent>--><!--Device-RichEditorGesture-onClick?: Callback<ClickEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onLongPress

```TypeScript
onLongPress?: Callback<GestureEvent>
```

[GestureEvent](../../../reference/apis-arkui/arkui-ts/ts-gesture-common.md#gestureevent对象说明)为用户长按事件。 长按完成时回调事件。

**类型：** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gestureevent-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorGesture-onLongPress?: Callback<GestureEvent>--><!--Device-RichEditorGesture-onLongPress?: Callback<GestureEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

