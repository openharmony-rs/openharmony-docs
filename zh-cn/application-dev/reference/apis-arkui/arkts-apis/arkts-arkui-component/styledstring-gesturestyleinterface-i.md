# GestureStyleInterface

Defines the Gesture Events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface GestureStyleInterface--><!--Device-unnamed-export declare interface GestureStyleInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClick

```TypeScript
onClick?: Callback<ClickEvent>
```

设置点击事件。

**类型：** Callback&lt;ClickEvent&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureStyleInterface-onClick?: Callback<ClickEvent>--><!--Device-GestureStyleInterface-onClick?: Callback<ClickEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onLongPress

```TypeScript
onLongPress?: Callback<GestureEvent>
```

设置长按事件。

**类型：** Callback&lt;GestureEvent&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureStyleInterface-onLongPress?: Callback<GestureEvent>--><!--Device-GestureStyleInterface-onLongPress?: Callback<GestureEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTouch

```TypeScript
onTouch?: Callback<TouchEvent>
```

设置触摸事件。 取值为undefined时，不使用回调函数。

**类型：** Callback&lt;TouchEvent&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureStyleInterface-onTouch?: Callback<TouchEvent>--><!--Device-GestureStyleInterface-onTouch?: Callback<TouchEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

