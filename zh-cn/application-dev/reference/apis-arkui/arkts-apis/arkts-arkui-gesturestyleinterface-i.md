# GestureStyleInterface

定义事件手势接口。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClick

```TypeScript
onClick?: Callback<ClickEvent>
```

设置点击事件。

**类型：** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[ClickEvent](../arkts-components/arkts-arkui-clickevent-i.md)&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onLongPress

```TypeScript
onLongPress?: Callback<GestureEvent>
```

设置长按事件。

**类型：** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](../arkts-components/arkts-arkui-gestureevent-i.md)&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTouch

```TypeScript
onTouch?: Callback<TouchEvent>
```

设置触摸事件。

**类型：** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[TouchEvent](../arkts-components/arkts-arkui-touchevent-i.md)&gt;

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
