# ToggleType

Toggle的样式。
> **说明：**  
>  
> Toggle的样式继承对应组件样式的默认值，且不支持设置。例如，如果ToggleType为Button，则该组件样式继承[ButtonType](arkts-arkui-buttontype-e.md)的默认值。由于Button.type从API  
> version 18开始，默认类型从胶囊型变更为圆角矩形，胶囊型按钮不支持设置  
> [borderRadius](arkts-arkui-commonmethod-c.md#borderradius)，此时使用  
> Toggle组件设置borderRadius也不生效。

**起始版本：** 8

<!--Device-unnamed-declare enum ToggleType--><!--Device-unnamed-declare enum ToggleType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Checkbox

```TypeScript
Checkbox
```

提供单选框样式。

**说明：**

API version 11开始，Checkbox默认样式由圆角方形变为圆形。

[通用属性margin](arkts-arkui-commonmethod-c.md#margin)的默认值为：

{

 top: '14px',

 right: '14px',

 bottom: '14px',

 left: '14px'

}。

默认尺寸为：

{width:'20vp', height:'20vp'}。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ToggleType-Checkbox--><!--Device-ToggleType-Checkbox-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Switch

```TypeScript
Switch
```

提供开关样式。

**说明：**

[通用属性margin](arkts-arkui-commonmethod-c.md#margin)默认值为：

{

 top: '6px',

 right: '14px',

 bottom: '6px',

 left: '14px'

}。

默认尺寸为：

{width:'36vp', height:'20vp'}。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ToggleType-Switch--><!--Device-ToggleType-Switch-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Button

```TypeScript
Button
```

提供状态按钮样式。如子组件设置文本，文本内容将显示在按钮内。默认高度为28vp，宽度无默认值。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ToggleType-Button--><!--Device-ToggleType-Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

