# LoadingProgress属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性。

支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

**继承/实现关系：** LoadingProgressAttribute extends [CommonMethod<LoadingProgressAttribute>](CommonMethod<LoadingProgressAttribute>)

**起始版本：** 8

<!--Device-unnamed-declare class LoadingProgressAttribute extends CommonMethod<LoadingProgressAttribute>--><!--Device-unnamed-declare class LoadingProgressAttribute extends CommonMethod<LoadingProgressAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: ResourceColor)
```

设置加载进度条前景色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LoadingProgressAttribute-color(value: ResourceColor): LoadingProgressAttribute--><!--Device-LoadingProgressAttribute-color(value: ResourceColor): LoadingProgressAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 加载进度条的前景色。<br/>默认值：<br/>API version 10及以下：'#99666666'<br/>API version 11及以上：'#ff666666' |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<LoadingProgressConfiguration>)
```

定制LoadingProgress内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LoadingProgressAttribute-contentModifier(modifier: ContentModifier<LoadingProgressConfiguration>): LoadingProgressAttribute--><!--Device-LoadingProgressAttribute-contentModifier(modifier: ContentModifier<LoadingProgressConfiguration>): LoadingProgressAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;LoadingProgressConfiguration&gt; | 是 | 在LoadingProgress组件上，定制内容区的方法。<br/>modifier： 内容修改器，开发者需要自定义class实现ContentModifier接口。 |

## enableLoading

```TypeScript
enableLoading(value: boolean)
```

设置LoadingProgress动画是否显示。LoadingProgress动画不显示时，该组件依旧占位。通用属性[Visibility](../arkts-apis/arkts-arkui-visibility-e.md).Hidden隐藏的是包括[border](arkts-arkui-commonmethod-c.md#border)、[padding](arkts-arkui-commonmethod-c.md#padding)等整个组件范围，而enableLoading=false只隐藏LoadingProgress本身动画内容，不包括border等。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LoadingProgressAttribute-enableLoading(value: boolean): LoadingProgressAttribute--><!--Device-LoadingProgressAttribute-enableLoading(value: boolean): LoadingProgressAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | LoadingProgress动画是否显示。<br/>默认值：true，true表示显示LoadingProgress动画，false表示不显示LoadingProgress动画。 |

