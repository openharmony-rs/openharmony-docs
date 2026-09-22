# ArcAlphabetIndexer属性/事件

```TypeScript
declare class ArcAlphabetIndexerAttribute extends CommonMethod<ArcAlphabetIndexerAttribute>
```

除支持通用属性外，还支持以下属性：

除支持通用事件外，还支持以下事件：

**继承/实现关系：** ArcAlphabetIndexerAttribute extends CommonMethod<ArcAlphabetIndexerAttribute>

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcAlphabetIndexer, ArcAlphabetIndexerAttribute } from '@kit.ArkUI';
```

## autoCollapse

```TypeScript
autoCollapse(enable: Optional<boolean>)
```

设置是否使用自适应折叠模式。当索引项过多时，组件会根据可用显示空间自动调整索引项的显示布局。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | 是 | 是否使用自适应折叠模式。<br>默认值：true <br>true：使用自适应折叠模式。<br>false：不使用自适应折叠模式。 |

## color

```TypeScript
color(color: Optional<ColorMetrics>)
```

设置普通状态下索引项文字颜色。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | 是 | 文字颜色。<br>默认值：0xFFFFFF，显示为白色。 |

## font

```TypeScript
font(font: Optional<Font>)
```

设置弧形字母索引条默认字体样式，即未选中状态下索引项的字体样式。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Font&gt; | 是 | 字母索引条默认字体样式，用于设置索引条上所有字母的显示效果，包括文字大小、粗细、倾斜角度和字体族等。<br>默认值：<br>{<br>size:'13.0fp',<br> style:FontStyle.Normal,<br> weight:500,<br> family:'HarmonyOS Sans'<br>} |

## itemSize

```TypeScript
itemSize(size: Optional<LengthMetrics>)
```

设置弧形索引条索引项区域大小。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | 是 | 弧形索引条索引项区域大小，索引项区域为圆形，即圆形直径。不支持设置为百分比。<br>默认值：24.0 <br>单位：vp |

## onSelect

```TypeScript
onSelect(handler: Optional<OnSelectCallback>)
```

索引条选中回调，返回值为当前选中索引。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnSelectCallback](arkts-arkui-arcalphabetindexer-comp-onselectcallback-t.md)&gt; | 是 | 回调函数，用于处理索引条选中事件。当用户点击或滑动索引条选中某项时触发，回调中返回当前选中项的索引值。 |

## popupBackground

```TypeScript
popupBackground(color: Optional<ColorMetrics>)
```

设置提示弹窗背景色。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | 是 | 提示弹窗背景色。<br>默认值：0xD8404040，显示为微透明的深灰色。 |

## popupBackgroundBlurStyle

```TypeScript
popupBackgroundBlurStyle(style: Optional<BlurStyle>)
```

设置提示弹窗的背景模糊材质。未通过该接口设置时，默认为关闭模糊，对应取值为BlurStyle中的NONE。

> **说明：** 

> 当通过popupBackgroundBlurStyle设置弹窗气泡的背景模糊材质时，不建议再通过
> [popupBackground](#popupbackground)设置背景色。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)&gt; | 是 | 设置提示弹窗的背景模糊材质。<br>默认值：BlurStyle.NONE。<br>设置此属性后不建议再设置[popupBackground](#popupbackground)属性。 |

## popupColor

```TypeScript
popupColor(color: Optional<ColorMetrics>)
```

设置提示弹窗文字颜色。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | 是 | 提示弹窗文字颜色。<br>默认值：0xFFFFFF，显示为白色。 |

## popupFont

```TypeScript
popupFont(font: Optional<Font>)
```

设置提示弹窗字体样式，用于设置提示弹窗中显示的当前选中字母的显示效果，包括文字大小、粗细、倾斜角度和字体族等。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Font&gt; | 是 | 提示弹窗字体样式。<br>默认值：<br>{<br>size:'19.0fp',<br> style:FontStyle.Normal,<br> weight:500,<br> family:'HarmonyOS Sans'<br>} |

## selected

```TypeScript
selected(index: Optional<number>)
```

设置选中项索引值。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | 是 | 选中项索引值。若超出有效索引范围，则取默认值0。<br>默认值：0 <br>该参数支持[!!](../../../ui/state-management/arkts-new-binding.md)双向绑定变量。 |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(color: Optional<ColorMetrics>)
```

设置选中项背景颜色。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | 是 | 选中项背景颜色。<br>默认值：0x1F71FF，显示为深蓝色。 |

## selectedColor

```TypeScript
selectedColor(color: Optional<ColorMetrics>)
```

设置选中项文字颜色。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | 是 | 选中项文字颜色。<br>默认值：0xFFFFFF，显示为白色。 |

## selectedFont

```TypeScript
selectedFont(font: Optional<Font>)
```

设置选中项文字尺寸、粗细、字体族、倾斜等样式。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Font&gt; | 是 | 选中项文字样式。<br>默认值：{<br>size:'13.0fp',<br> style:FontStyle.Normal,<br> weight:500,<br> family:'HarmonyOS Sans'<br>} |

## usePopup

```TypeScript
usePopup(enabled: Optional<boolean>)
```

设置是否使用提示弹窗。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | 是 | 是否使用提示弹窗。<br>true表示使用提示弹窗；false表示不使用提示弹窗。<br>默认值：false |
