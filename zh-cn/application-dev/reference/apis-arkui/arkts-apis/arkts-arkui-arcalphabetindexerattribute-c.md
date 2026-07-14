# ArcAlphabetIndexerAttribute

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** ArcAlphabetIndexerAttribute extends [CommonMethod<ArcAlphabetIndexerAttribute>](CommonMethod<ArcAlphabetIndexerAttribute>)

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## autoCollapse

```TypeScript
autoCollapse(enable: Optional<boolean>): ArcAlphabetIndexerAttribute
```

设置是否使用自适应折叠模式。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | Optional&lt;boolean&gt; | 是 | 是否使用自适应折叠模式。<br/>默认值：true <br/>true：使用自适应折叠模式。<br/>false：不使用自适应折叠模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## color

```TypeScript
color(color: Optional<ColorMetrics>): ArcAlphabetIndexerAttribute
```

设置普通状态下索引项文字颜色。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ColorMetrics&gt; | 是 | 文字颜色。<br/>默认值：0xFFFFFF，显示为白色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## font

```TypeScript
font(font: Optional<Font>): ArcAlphabetIndexerAttribute
```

设置字母索引条默认字体样式。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | Optional&lt;Font&gt; | 是 | 字母索引条默认字体样式。<br/>默认值：<br/>{<br/>size:'13.0fp',<br/> style:FontStyle.Normal,<br/>weight:500,<br/> family:'HarmonyOS Sans'<br/>} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## itemSize

```TypeScript
itemSize(size: Optional<LengthMetrics>): ArcAlphabetIndexerAttribute
```

设置字母索引条字母区域大小。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | Optional&lt;LengthMetrics&gt; | 是 | 字母索引条字母区域大小，字母区域为圆形，即圆形直径。不支持设置为百分比。<br/>默认值：24.0 <br/>单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## onSelect

```TypeScript
onSelect(handler: Optional<OnSelectCallback>): ArcAlphabetIndexerAttribute
```

索引条选中回调，返回值为当前选中索引。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;OnSelectCallback&gt; | 是 | 回调函数类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## popupBackground

```TypeScript
popupBackground(color: Optional<ColorMetrics>): ArcAlphabetIndexerAttribute
```

设置提示弹窗背景色。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ColorMetrics&gt; | 是 | 提示弹窗背景色。<br/>默认值：0xD8404040，显示为微透明的深灰色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## popupBackgroundBlurStyle

```TypeScript
popupBackgroundBlurStyle(style: Optional<BlurStyle>): ArcAlphabetIndexerAttribute
```

设置提示弹窗的背景模糊材质。未通过该接口设置时，默认为关闭模糊，对应取值为BlurStyle中的NONE。

> **说明：**

> 当通过popupBackgroundBlurStyle设置弹窗气泡的背景模糊材质时，不建议再通过
> [popupBackground](arkts-arkui-arcalphabetindexerattribute-c.md#popupbackground-1)设置背景色。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | Optional&lt;BlurStyle&gt; | 是 | 设置提示弹窗的背景模糊材质。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## popupColor

```TypeScript
popupColor(color: Optional<ColorMetrics>): ArcAlphabetIndexerAttribute
```

设置提示弹窗文字颜色。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ColorMetrics&gt; | 是 | 提示弹窗文字颜色。<br/>默认值：0xFFFFFF，显示为白色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## popupFont

```TypeScript
popupFont(font: Optional<Font>): ArcAlphabetIndexerAttribute
```

设置提示弹窗字体样式。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | Optional&lt;Font&gt; | 是 | 提示弹窗字体样式。<br/>默认值：<br/>{<br/>size:'19.0fp',<br/> style:FontStyle.Normal,<br/>weight:500,<br/> family:'HarmonyOS Sans'<br/>} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## selected

```TypeScript
selected(index: Optional<number>): ArcAlphabetIndexerAttribute
```

设置选中项索引值。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | Optional&lt;number&gt; | 是 | 选中项索引值。 <br/>默认值：0 <br/>该参数支持[!!](../../../../ui/state-management/arkts-new-binding.md)双向绑定变量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(color: Optional<ColorMetrics>): ArcAlphabetIndexerAttribute
```

设置选中项背景颜色。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ColorMetrics&gt; | 是 | 选中项背景颜色。<br/>默认值：0x1F71FF，显示为深蓝色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## selectedColor

```TypeScript
selectedColor(color: Optional<ColorMetrics>): ArcAlphabetIndexerAttribute
```

设置选中项文字颜色。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ColorMetrics&gt; | 是 | 选中项文字颜色。<br/>默认值：0xFFFFFF，显示为白色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## selectedFont

```TypeScript
selectedFont(font: Optional<Font>): ArcAlphabetIndexerAttribute
```

设置选中项文字尺寸、粗细、字体族、倾斜等样式。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | Optional&lt;Font&gt; | 是 | 选中项文字样式。<br/>默认值：{<br/>size:'13.0fp',<br/> style:FontStyle.Normal,<br/> weight:500,<br/> family:'HarmonyOS Sans'<br/>} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## usePopup

```TypeScript
usePopup(enabled: Optional<boolean>): ArcAlphabetIndexerAttribute
```

设置是否使用提示弹窗。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | Optional&lt;boolean&gt; | 是 | 是否使用提示弹窗。<br/>true表示使用提示弹窗；false表示不使用提示弹窗。<br/>默认值：false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

