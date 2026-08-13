# GestureStyleInterface

Defines the Gesture Events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface GestureStyleInterface--><!--Device-unnamed-export declare interface GestureStyleInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClick

```TypeScript
onClick?: Callback<ClickEvent>
```

设置点击事件。

**类型：** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[ClickEvent](../arkts-components/arkts-arkui-clickevent-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureStyleInterface-onClick?: Callback<ClickEvent>--><!--Device-GestureStyleInterface-onClick?: Callback<ClickEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onLongPress

```TypeScript
onLongPress?: Callback<GestureEvent>
```

设置长按事件。

**类型：** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gestureevent-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureStyleInterface-onLongPress?: Callback<GestureEvent>--><!--Device-GestureStyleInterface-onLongPress?: Callback<GestureEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTouch

```TypeScript
onTouch?: Callback<TouchEvent>
```

设置触摸事件。 取值为undefined时，不使用回调函数。

**类型：** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[TouchEvent](../arkts-components/arkts-arkui-touchevent-i.md)&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureStyleInterface-onTouch?: Callback<TouchEvent>--><!--Device-GestureStyleInterface-onTouch?: Callback<TouchEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

