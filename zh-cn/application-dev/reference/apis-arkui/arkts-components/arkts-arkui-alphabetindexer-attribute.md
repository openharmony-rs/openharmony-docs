# AlphabetIndexer属性/事件

[width](arkts-arkui-commonmethod-c.md#width-1)属性设置"auto"时表示自适应宽度，宽度会随索引项最大宽度变化。

[padding](arkts-arkui-commonmethod-c.md#padding-1)属性默认为4vp。

文本最大的字体缩放倍数[maxFontScale](TextAttribute#maxFontScale)和最小的字体缩放倍数[minFontScale](TextAttribute#minFontScale)皆为1，不跟随系统字体大小调节变化。

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** AlphabetIndexerAttribute extends [CommonMethod<AlphabetIndexerAttribute>](CommonMethod<AlphabetIndexerAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class AlphabetIndexerAttribute extends CommonMethod<AlphabetIndexerAttribute>--><!--Device-unnamed-declare class AlphabetIndexerAttribute extends CommonMethod<AlphabetIndexerAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="alignstyle"></a>
## alignStyle

```TypeScript
alignStyle(value: IndexerAlign, offset?: Length)
```

设置索引条提示弹窗的对齐样式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-alignStyle(value: IndexerAlign, offset?: Length): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-alignStyle(value: IndexerAlign, offset?: Length): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [IndexerAlign](arkts-arkui-indexeralign-e.md) | 是 | 索引条提示弹窗的对齐样式，支持弹窗显示在索引条右侧和左侧。<br/>默认值：IndexerAlign.END |
| offset | [Length](../arkts-apis/arkts-arkui-length-t.md) | 否 | 提示弹窗与索引条之间间距，大于等于0为有效值，在不设置或设置为小于0的情况下间距与popupPosition.x相同。与[popupPosition](AlphabetIndexerAttribute#popupPosition)同时设置时，水平方向上offset生效，竖直方向上popupPosition.y生效。<br>**起始版本：** 10 |

<a id="autocollapse"></a>
## autoCollapse

```TypeScript
autoCollapse(value: boolean)
```

设置是否使用自适应折叠模式。

如果索引项第一项为“#”，当除去第一项后剩余索引项数量 <= 9时，选择全显示模式；9 < 剩余索引项数量 <= 13时，根据索引条高度自适应选择全显示模式或者短折叠模式；剩余索引项数量 > 13时，根据索引条高度自适应选择短折叠模式或者长折叠模式。

如果索引项第一项不为“#”，当所有索引项数量 <= 9时，选择全显示模式；9 < 所有索引项数量 <= 13时，根据索引条高度自适应选择全显示模式或者短折叠模式；所有索引项数量 > 13时，根据索引条高度自适应选择短折叠模式或者长折叠模式。

> **说明：**

> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-autoCollapse(value: boolean): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-autoCollapse(value: boolean): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否使用自适应折叠模式。<br/>默认值：<br />API version 12之前：false <br />API version 12及之后：true <br/>true：使用自适应折叠模式。<br/>false：不使用自适应折叠模式。 |

<a id="color"></a>
## color

```TypeScript
color(value: ResourceColor)
```

设置未选中项文本颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-color(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-color(value: ResourceColor): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 未选中项文本颜色。<br/>默认值：0x99182431，显示为略带透明的棕色。 |

<a id="enablehapticfeedback"></a>
## enableHapticFeedback

```TypeScript
enableHapticFeedback(value: boolean)
```

设置是否开启触控反馈。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-enableHapticFeedback(value: boolean): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-enableHapticFeedback(value: boolean): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否支持触控反馈。<br/>true：支持触控反馈。<br/>false：不支持触控反馈。<br/>默认值：true<br/>开启触控反馈时，需要在工程的[module.json5](docroot://quick-start/module-configuration-file.md)中配置requestPermissions字段开启振动权限，配置如下：<br/>"requestPermissions": [{"name": "ohos.permission.VIBRATE"}] |

<a id="font"></a>
## font

```TypeScript
font(value: Font)
```

设置未选中项文本样式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-font(value: Font): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-font(value: Font): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 未选中索引项文本样式。<br/>默认值：<br/>API version 11及以前：<br/>{<br/>size:'12.0fp',<br/> style:FontStyle.Normal,<br/> weight:FontWeight.Regular,<br/> family:'HarmonyOS Sans'<br/>}<br/>API version 12及以后：<br/   >{<br/>size:'10.0vp',<br/> style:FontStyle.Normal,<br/> weight:FontWeight.Medium,<br/> family:'HarmonyOS Sans'<br/>} |

<a id="itemborderradius"></a>
## itemBorderRadius

```TypeScript
itemBorderRadius(value: number)
```

设置索引项背板圆角半径。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-itemBorderRadius(value: number): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-itemBorderRadius(value: number): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置索引项背板圆角半径。<br/>。<br>单位为：vp。 |

<a id="itemsize"></a>
## itemSize

```TypeScript
itemSize(value: string | number)
```

设置索引项区域大小。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-itemSize(value: string | number): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-itemSize(value: string | number): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| number | 是 | 索引项区域大小，索引项区域为正方形，即正方形边长。不支持设置为百分比。<br/>实际取值会受到组件尺寸的约束，索引项宽度最大为组件宽度-左右[padding](arkts-arkui-commonmethod-c.md#padding-1)，索引项高度最大为（组件高度-上下[padding](arkts-arkui-commonmethod-c.md#padding-1)）/索引项个数。传入值小于等于0时，按照默认值处理。<br/>默认值：16.0<br/>单位：vp |

<a id="onpopupselect"></a>
## onPopupSelect

```TypeScript
onPopupSelect(callback: OnAlphabetIndexerPopupSelectCallback)
```

提示弹窗二级索引选中事件，回调参数为当前选中二级索引项索引。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-onPopupSelect(callback: OnAlphabetIndexerPopupSelectCallback): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-onPopupSelect(callback: OnAlphabetIndexerPopupSelectCallback): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAlphabetIndexerPopupSelectCallback](arkts-arkui-onalphabetindexerpopupselectcallback-t.md) | 是 | 提示弹窗二级索引选中事件。<br>**起始版本：** 18 |

<a id="onrequestpopupdata"></a>
## onRequestPopupData

```TypeScript
onRequestPopupData(callback: OnAlphabetIndexerRequestPopupDataCallback)
```

设置提示弹窗二级索引项内容事件，回调参数为当前选中项索引，回调返回值为提示弹窗需显示的二级索引项内容。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-onRequestPopupData(callback: OnAlphabetIndexerRequestPopupDataCallback): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-onRequestPopupData(callback: OnAlphabetIndexerRequestPopupDataCallback): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAlphabetIndexerRequestPopupDataCallback](arkts-arkui-onalphabetindexerrequestpopupdatacallback-t.md) | 是 | 设置提示弹窗二级索引项内容事件。<br>**起始版本：** 18 |

<a id="onselect"></a>
## onSelect

```TypeScript
onSelect(callback: OnAlphabetIndexerSelectCallback)
```

索引项选中事件，回调参数为当前选中项索引。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-onSelect(callback: OnAlphabetIndexerSelectCallback): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-onSelect(callback: OnAlphabetIndexerSelectCallback): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAlphabetIndexerSelectCallback](arkts-arkui-onalphabetindexerselectcallback-t.md) | 是 | 索引项选中事件。<br>**起始版本：** 18 |

<a id="onselected"></a>
## onSelected

```TypeScript
onSelected(callback: (index: number) => void)
```

索引项选中事件，回调参数为当前选中项索引。

> **说明：**

> 从API version 7开始支持，从API version 8开始废弃，建议使用[onSelect](AlphabetIndexerAttribute#onSelect)替代。

**起始版本：** 7

**废弃版本：** 8

**替代接口：** onSelect

<!--Device-AlphabetIndexerAttribute-onSelected(callback: (index: number) => void): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-onSelected(callback: (index: number) => void): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (index: number) =&gt; void | 是 | 当前选中的索引。 |

<a id="popupbackground"></a>
## popupBackground

```TypeScript
popupBackground(value: ResourceColor)
```

设置提示弹窗背景颜色。

该接口未被主动调用或参数value传入undefined时：

API version 11及以前版本，提示弹窗背景颜色默认为0xFFFFFFFF，显示为白色。

对于API version 12至API version 24版本，默认为#66808080，显示为半透明的灰色。

从API版本26.0.0开始，如果和[popupBackgroundBlurStyle](AlphabetIndexerAttribute#popupBackgroundBlurStyle)均未被主动调用或参数value传入undefined，高档、中档算力设备默认显示为沉浸式材质[ImmersiveStyle](docroot://reference/apis-arkui/arkts-apis-uimaterial.md#immersivestyle)的THIN样式，低档算力设备默认显示为白色背景。如果popupBackgroundBlurStyle被主动调用且参数value传入有效值，提示弹窗背景颜色默认为#66808080，显示为半透明的灰色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-popupBackground(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupBackground(value: ResourceColor): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 提示弹窗背景颜色。<br/>弹窗的背景模糊材质效果会对背景色产生影响，可通过设置[popupBackgroundBlurStyle](AlphabetIndexerAttribute#popupBackgroundBlurStyle)属性值为NONE关闭背景模糊材质效果。<br/> |

<a id="popupbackgroundblurstyle"></a>
## popupBackgroundBlurStyle

```TypeScript
popupBackgroundBlurStyle(value: BlurStyle)
```

设置提示弹窗的背景模糊材质。API版本26.0.0之前版本，未通过该接口设置时，默认为组件普通材质模糊，对应取值为BlurStyle中的COMPONENT_REGULAR。从API版本26.0.0开始，[popupBackground](AlphabetIndexerAttribute#popupBackground)和popupBackgroundBlurStyle均未被主动调用或者传入undefined时，在高档、中档算力设备默认显示为沉浸式材质[ImmersiveStyle](docroot://reference/apis-arkui/arkts-apis-uimaterial.md#immersivestyle)的THIN样式，低档算力设备默认显示为白色背景。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-popupBackgroundBlurStyle(value: BlurStyle): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupBackgroundBlurStyle(value: BlurStyle): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BlurStyle](arkts-arkui-blurstyle-e.md) | 是 | 设置提示弹窗的背景模糊材质。<br/>弹窗的背景模糊材质效果会对背景色[popupBackground](AlphabetIndexerAttribute#popupBackground)产生影响，可通过设置属性值为NONE关闭背景模糊材质效果。 |

<a id="popupcolor"></a>
## popupColor

```TypeScript
popupColor(value: ResourceColor)
```

设置提示弹窗一级索引项文本颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-popupColor(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupColor(value: ResourceColor): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 提示弹窗一级索引项文本颜色。<br/>默认值：0xFF007DFF，显示为蓝色。 |

<a id="popupfont"></a>
## popupFont

```TypeScript
popupFont(value: Font)
```

设置提示弹窗一级索引文本样式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-popupFont(value: Font): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupFont(value: Font): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 提示弹窗一级索引文本样式。<br/>默认值：<br/>{<br/>size:'24.0vp',<br/> style:FontStyle.Normal,<br/> weight:FontWeight.Medium,<br/> family:'HarmonyOS Sans'<br/>} |

<a id="popupitembackgroundcolor"></a>
## popupItemBackgroundColor

```TypeScript
popupItemBackgroundColor(value: ResourceColor)
```

设置提示弹窗二级索引项背景颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-popupItemBackgroundColor(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupItemBackgroundColor(value: ResourceColor): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 提示弹窗二级索引项背景颜色。 <br/>默认值：<br />API version 11及以前：#FFFFFFFF，显示为白色。<br />API version12及以后：#00000000，显示为透明色。 |

<a id="popupitemborderradius"></a>
## popupItemBorderRadius

```TypeScript
popupItemBorderRadius(value: number)
```

设置提示弹窗索引项背板圆角半径。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-popupItemBorderRadius(value: number): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupItemBorderRadius(value: number): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置提示弹窗索引项背板圆角半径。默认值：24vp不支持百分比，小于0时按照0设置。提示弹窗背板圆角自适应变化（索引项圆角半径+4vp）。<br>单位为：vp。 |

<a id="popupitemfont"></a>
## popupItemFont

```TypeScript
popupItemFont(value: Font)
```

设置提示弹窗二级索引项文本样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-popupItemFont(value: Font): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupItemFont(value: Font): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 提示弹窗二级索引项文本样式。 <br/>默认值：<br/>{<br/>size:24,<br/>weight:FontWeight.Medium<br/>} |

<a id="popupposition"></a>
## popupPosition

```TypeScript
popupPosition(value: Position)
```

设置弹出窗口相对于索引条上边框中点的位置。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-popupPosition(value: Position): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupPosition(value: Position): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Position](../arkts-apis/arkts-arkui-display-position-i.md) | 是 | 弹出窗口相对于索引条上边框中点的位置。<br/>默认值：{x: 60.0, y: 48.0} |

<a id="popupselectedcolor"></a>
## popupSelectedColor

```TypeScript
popupSelectedColor(value: ResourceColor)
```

设置提示弹窗二级索引选中项文本颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-popupSelectedColor(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupSelectedColor(value: ResourceColor): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 提示弹窗二级索引选中项文本颜色。 <br/>默认值：#FF182431，显示为深暗蓝色。 |

<a id="popuptitlebackground"></a>
## popupTitleBackground

```TypeScript
popupTitleBackground(value: ResourceColor)
```

设置提示弹窗一级索引项背景颜色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-popupTitleBackground(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupTitleBackground(value: ResourceColor): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 设置提示弹窗一级索引项背景颜色。<br/>默认值：<br/>提示弹窗只有一个索引项：#00FFFFFF。<br/>提示弹窗有多个索引项：#0c182431。 |

<a id="popupunselectedcolor"></a>
## popupUnselectedColor

```TypeScript
popupUnselectedColor(value: ResourceColor)
```

设置提示弹窗二级索引未选中项文本颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-popupUnselectedColor(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupUnselectedColor(value: ResourceColor): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 提示弹窗二级索引未选中项文本颜色。 <br/>默认值：#FF182431，显示为深暗蓝色。 |

<a id="selected"></a>
## selected

```TypeScript
selected(index: number)
```

设置选中项索引值。

从API version 10开始，该参数支持[$$](docroot://ui/state-management/arkts-two-way-sync.md)双向绑定变量。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-selected(index: number): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-selected(index: number): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 选中项索引值。<br/>取值范围：[0, [arrayValue](arkts-arkui-alphabetindexeroptions-i.md).length-1]<br/>默认值：0 |

<a id="selectedbackgroundcolor"></a>
## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

设置选中项背景颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-selectedBackgroundColor(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-selectedBackgroundColor(value: ResourceColor): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 选中项背景颜色。<br/>默认值：0x1A007DFF，显示为半透明的蓝绿色。 |

<a id="selectedcolor"></a>
## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

设置选中项文本颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-selectedColor(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-selectedColor(value: ResourceColor): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 选中项文本颜色。<br/>默认值：0xFF007DFF，显示为蓝色。 |

<a id="selectedfont"></a>
## selectedFont

```TypeScript
selectedFont(value: Font)
```

设置选中项文本样式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-selectedFont(value: Font): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-selectedFont(value: Font): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 选中项文本样式。<br/>默认值：<br/>API version 11及以前：<br/>{<br/>size:'12.0fp',<br/> style:FontStyle.Normal,<br/> weight:FontWeight.Regular,<br/> family:'HarmonyOS Sans'<br/>}<br/>API version 12及以后：<br/   >{<br/>size:'10.0vp',<br/> style:FontStyle.Normal,<br/> weight:FontWeight.Medium,<br/> family:'HarmonyOS Sans'<br/>} |

<a id="usingpopup"></a>
## usingPopup

```TypeScript
usingPopup(value: boolean)
```

设置是否显示提示弹窗。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerAttribute-usingPopup(value: boolean): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-usingPopup(value: boolean): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否显示提示弹窗。<br/>默认值：false <br/>true：显示提示弹窗。<br/>false：不显示提示弹窗。 |

