# GestureStyleInterface

定义事件手势接口。

**起始版本：** 12

<!--Device-unnamed-declare interface GestureStyleInterface--><!--Device-unnamed-declare interface GestureStyleInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClick

```TypeScript
onClick?: Callback<ClickEvent>
```

设置点击事件。

**类型：** Callback<ClickEvent>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureStyleInterface-onClick?: Callback<ClickEvent>--><!--Device-GestureStyleInterface-onClick?: Callback<ClickEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onLongPress

```TypeScript
onLongPress?: Callback<GestureEvent>
```

设置长按事件。

**类型：** Callback<GestureEvent>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureStyleInterface-onLongPress?: Callback<GestureEvent>--><!--Device-GestureStyleInterface-onLongPress?: Callback<GestureEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTouch

```TypeScript
onTouch?: Callback<TouchEvent>
```

设置触摸事件。

**类型：** Callback<TouchEvent>

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-GestureStyleInterface-onTouch?: Callback<TouchEvent>--><!--Device-GestureStyleInterface-onTouch?: Callback<TouchEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

