# SubTabBarStyle

子页签样式。打开后在切换页签时会播放跳转动画。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class SubTabBarStyle--><!--Device-unnamed-export declare class SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## board

```TypeScript
board(value: BoardStyle): SubTabBarStyle
```

设置选中子页签的背板风格。子页签的背板风格仅在水平模式下有效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubTabBarStyle-board(value: BoardStyle): SubTabBarStyle--><!--Device-SubTabBarStyle-board(value: BoardStyle): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BoardStyle](arkts-na-tabcontent-boardstyle-i.md) | 是 | 选中子页签的背板风格对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-na-tabcontent-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身。 |

## constructor

```TypeScript
constructor(content: ResourceStr | ComponentContentBase)
```

SubTabBarStyle的构造函数。支持ComponentContent设置自定义内容。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubTabBarStyle-constructor(content: ResourceStr | ComponentContentBase)--><!--Device-SubTabBarStyle-constructor(content: ResourceStr | ComponentContentBase)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [ComponentContentBase](arkts-na-componentcontent-componentcontentbase-c.md) | 是 | 页签内的内容。&lt;br /&gt;**说明：**&lt;br /&gt;1.自定义内容不支持labelStyle属性。&lt;br /&gt;2.自定 义内容超出页签范围，则不显示超出部分。&lt;br /&gt;3.自定义内容小于页签范围，则会居中对齐。&lt;br /&gt;4.自定义内容异常或无可用显示组件，则显示空白。 |

## id

```TypeScript
id(value: string): SubTabBarStyle
```

设置子页签的id。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubTabBarStyle-id(value: string): SubTabBarStyle--><!--Device-SubTabBarStyle-id(value: string): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 子页签的id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-na-tabcontent-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身。 |

## indicator

```TypeScript
indicator(style: SubTabBarIndicatorStyle): SubTabBarStyle
```

设置选中子页签的下划线风格。子页签的下划线风格仅在水平模式下有效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubTabBarStyle-indicator(style: SubTabBarIndicatorStyle): SubTabBarStyle--><!--Device-SubTabBarStyle-indicator(style: SubTabBarIndicatorStyle): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [SubTabBarIndicatorStyle](arkts-na-tabcontent-subtabbarindicatorstyle-i.md) | 是 | 选中子页签的下划线风格对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-na-tabcontent-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身。 |

## indicator

```TypeScript
indicator(value: SubTabBarIndicatorStyle | DrawableTabBarIndicator): SubTabBarStyle
```

设置选中子页签的下划线风格。子页签的下划线风格仅在水平模式下有效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubTabBarStyle-indicator(value: SubTabBarIndicatorStyle | DrawableTabBarIndicator): SubTabBarStyle--><!--Device-SubTabBarStyle-indicator(value: SubTabBarIndicatorStyle | DrawableTabBarIndicator): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SubTabBarIndicatorStyle](arkts-na-tabcontent-subtabbarindicatorstyle-i.md) \| [DrawableTabBarIndicator](arkts-na-tabcontent-drawabletabbarindicator-i.md) | 是 | 选中子页签的下划线风格对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-na-tabcontent-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身。 |

## labelStyle

```TypeScript
labelStyle(style: TabBarLabelStyle): SubTabBarStyle
```

设置子页签的label文本和字体的样式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubTabBarStyle-labelStyle(style: TabBarLabelStyle): SubTabBarStyle--><!--Device-SubTabBarStyle-labelStyle(style: TabBarLabelStyle): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TabBarLabelStyle](arkts-na-tabcontent-tabbarlabelstyle-i.md) | 是 | 子页签的label文本和字体的样式对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-na-tabcontent-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身。 |

## of

```TypeScript
static of(content: ResourceStr | ComponentContentBase): SubTabBarStyle
```

SubTabBarStyle的静态构造函数。支持ComponentContent设置自定义内容。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubTabBarStyle-static of(content: ResourceStr | ComponentContentBase): SubTabBarStyle--><!--Device-SubTabBarStyle-static of(content: ResourceStr | ComponentContentBase): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [ComponentContentBase](arkts-na-componentcontent-componentcontentbase-c.md) | 是 | 页签内的内容。支持ComponentContentBase设置自定义内容。&lt;br /&gt;**说明：**&lt;br /&gt;1.自 定义内容不支持labelStyle属性。&lt;br /&gt;2.自定义内容超出页签范围，则不显示超出部分。&lt;br /&gt;3.自定义内容小于页签范围，则会居中对齐。&lt;br /&gt;4.自定义内容异常或无可用显示组件，则显示空白。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-na-tabcontent-subtabbarstyle-c.md) | 返回创建的SubTabBarStyle对象。 |

## padding

```TypeScript
padding(value: Padding | Dimension): SubTabBarStyle
```

设置子页签的内边距属性（不支持百分比设置）。使用Dimension时，四个方向内边距同时生效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubTabBarStyle-padding(value: Padding | Dimension): SubTabBarStyle--><!--Device-SubTabBarStyle-padding(value: Padding | Dimension): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Padding](../../apis-arkui/arkts-apis/arkts-arkui-padding-t.md) \| [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md) | 是 | 子页签的内边距属性。<br/>取值范围：[0, +∞]<br/>异常值时取默认值。&lt;br /&gt;默认值：{left:8.0vp,right:8.0vp, top:17.0vp,bottom:18.0vp} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-na-tabcontent-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身。 |

## padding

```TypeScript
padding(padding: LocalizedPadding): SubTabBarStyle
```

设置子页签的内边距属性，支持镜像能力（不支持百分比设置）。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubTabBarStyle-padding(padding: LocalizedPadding): SubTabBarStyle--><!--Device-SubTabBarStyle-padding(padding: LocalizedPadding): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| padding | [LocalizedPadding](../../apis-arkui/arkts-apis/arkts-arkui-localizedpadding-i.md) | 是 | 子页签的内边距属性。<br/>异常值时取默认值。<br/>取值范围：[0, +∞]<br/>异常值时取默认值。&lt;br /&gt;默认值：{start: LengthMetrics.vp(8),end:LengthMetrics.vp(8),<br/>top:LengthMetrics.vp(17),bottom:LengthMetrics.vp(18)} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-na-tabcontent-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身。 |

## selectedMode

```TypeScript
selectedMode(value: SelectedMode): SubTabBarStyle
```

设置选中子页签的显示方式。子页签的显示方式仅在水平模式下有效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubTabBarStyle-selectedMode(value: SelectedMode): SubTabBarStyle--><!--Device-SubTabBarStyle-selectedMode(value: SelectedMode): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SelectedMode](arkts-na-tabcontent-selectedmode-e.md) | 是 | 选中子页签的显示方式。&lt;br /&gt;默认值：SelectedMode.INDICATOR |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-na-tabcontent-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身。 |

