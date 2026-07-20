# Toggle属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** ToggleAttribute extends [CommonMethod<ToggleAttribute>](CommonMethod<ToggleAttribute>)

**起始版本：** 8

<!--Device-unnamed-declare class ToggleAttribute extends CommonMethod<ToggleAttribute>--><!--Device-unnamed-declare class ToggleAttribute extends CommonMethod<ToggleAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="contentmodifier"></a>
## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<ToggleConfiguration>)
```

定制Toggle内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ToggleAttribute-contentModifier(modifier: ContentModifier<ToggleConfiguration>): ToggleAttribute--><!--Device-ToggleAttribute-contentModifier(modifier: ContentModifier<ToggleConfiguration>): ToggleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;ToggleConfiguration&gt; | 是 | 在Toggle组件上，定制内容区的方法。<br/>modifier：内容修改器，开发者需要自定义class实现ContentModifier接口。 |

<a id="onchange"></a>
## onChange

```TypeScript
onChange(callback: (isOn: boolean) => void)
```

开关状态切换时触发该事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ToggleAttribute-onChange(callback: (isOn: boolean) => void): ToggleAttribute--><!--Device-ToggleAttribute-onChange(callback: (isOn: boolean) => void): ToggleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (isOn: boolean) =&gt; void | 是 |  |

<a id="selectedcolor"></a>
## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

设置组件在打开状态下的背景颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ToggleAttribute-selectedColor(value: ResourceColor): ToggleAttribute--><!--Device-ToggleAttribute-selectedColor(value: ResourceColor): ToggleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 组件打开状态的背景颜色。<br/>默认值：<br/>当ToggleType为Switch时，默认值为`$r('sys.color.ohos_id_color_emphasize')`。<br/>当ToggleType为Checkbox时，默认值为`$r('sys.color.ohos_id_color_emphasize')`。<br/>当ToggleType为Button时，默认值为`$r('sys.color.ohos_id_color_emphasize')`混合`$r('sys.float.ohos_id_alpha_highlight_bg')`的透明度。 |

<a id="switchpointcolor"></a>
## switchPointColor

```TypeScript
switchPointColor(color: ResourceColor)
```

设置Switch类型的圆形滑块颜色。仅当type为ToggleType.Switch生效。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ToggleAttribute-switchPointColor(color: ResourceColor): ToggleAttribute--><!--Device-ToggleAttribute-switchPointColor(color: ResourceColor): ToggleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | Switch类型的圆形滑块颜色。<br/>默认值：$r('sys.color.ohos_id_color_foreground_contrary')<br/>**说明：**<br/>同时设置了[systemMaterial](arkts-arkui-commonmethod-c.md#systemmaterial-1)新材质时，设置此属性后会出现点光源效果，点光源颜色跟随此属性的设置。 |

<a id="switchstyle"></a>
## switchStyle

```TypeScript
switchStyle(value: SwitchStyle)
```

设置Switch类型的样式。仅当type为ToggleType.Switch生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ToggleAttribute-switchStyle(value: SwitchStyle): ToggleAttribute--><!--Device-ToggleAttribute-switchStyle(value: SwitchStyle): ToggleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SwitchStyle](arkts-arkui-switchstyle-i.md) | 是 | Switch样式风格。 |

