# BottomTabBarStyle

底部页签和侧边页签样式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class BottomTabBarStyle--><!--Device-unnamed-export declare class BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)
```

BottomTabBarStyle的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BottomTabBarStyle-constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)--><!--Device-BottomTabBarStyle-constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| TabBarSymbol | 是 | 页签内的图片内容。 |
| text | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 页签内的文字内容。 |

## iconStyle

```TypeScript
iconStyle(style: TabBarIconStyle): BottomTabBarStyle
```

设置底部页签的label图标的样式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BottomTabBarStyle-iconStyle(style: TabBarIconStyle): BottomTabBarStyle--><!--Device-BottomTabBarStyle-iconStyle(style: TabBarIconStyle): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TabBarIconStyle](arkts-na-tabcontent-tabbariconstyle-i.md) | 是 | 底部页签的label图标的样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-na-tabcontent-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身。 |

## id

```TypeScript
id(value: string): BottomTabBarStyle
```

设置底部页签的id。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BottomTabBarStyle-id(value: string): BottomTabBarStyle--><!--Device-BottomTabBarStyle-id(value: string): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 设置底部页签的id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-na-tabcontent-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身。 |

## labelStyle

```TypeScript
labelStyle(style: TabBarLabelStyle): BottomTabBarStyle
```

设置底部页签的label文本和字体的样式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BottomTabBarStyle-labelStyle(style: TabBarLabelStyle): BottomTabBarStyle--><!--Device-BottomTabBarStyle-labelStyle(style: TabBarLabelStyle): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TabBarLabelStyle](arkts-na-tabcontent-tabbarlabelstyle-i.md) | 是 | 底部页签的label文本和字体的样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-na-tabcontent-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身。 |

## layoutMode

```TypeScript
layoutMode(value: LayoutMode): BottomTabBarStyle
```

设置底部页签的图片、文字排布的方式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BottomTabBarStyle-layoutMode(value: LayoutMode): BottomTabBarStyle--><!--Device-BottomTabBarStyle-layoutMode(value: LayoutMode): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LayoutMode](arkts-na-tabcontent-layoutmode-e.md) | 是 | 底部页签的图片、文字排布的方式，具体参照LayoutMode枚举。<br/>默认值：LayoutMode.VERTICAL |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-na-tabcontent-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身。 |

## of

```TypeScript
static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle
```

BottomTabBarStyle的静态构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BottomTabBarStyle-static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle--><!--Device-BottomTabBarStyle-static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| TabBarSymbol | 是 | 页签内的图片内容。 |
| text | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 页签内的文字内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-na-tabcontent-bottomtabbarstyle-c.md) | 返回创建的BottomTabBarStyle对象。 |

## padding

```TypeScript
padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle
```

设置底部页签的内边距属性（不支持百分比设置）。使用Dimension时，四个方向内边距同时生效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BottomTabBarStyle-padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle--><!--Device-BottomTabBarStyle-padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Padding](../../apis-arkui/arkts-apis/arkts-arkui-padding-t.md) \| [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md) \| [LocalizedPadding](../../apis-arkui/arkts-apis/arkts-arkui-localizedpadding-i.md) | 是 | 底部页签的内边距。<br/>取值范围：[0, +∞]<br/>默认值：{left:4.0vp,right:4.0 vp,top:0.0vp,bottom:0.0vp}<br/>使用LocalizedPadding时，支持镜像能力。&lt;br /&gt;默认值：{start:LengthMetrics.vp(4),end: LengthMetrics.vp(4),<br/>top:LengthMetrics.vp(0),bottom:LengthMetrics.vp(0)} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-na-tabcontent-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身。 |

## symmetricExtensible

```TypeScript
symmetricExtensible(value: boolean): BottomTabBarStyle
```

设置底部页签的图片、文字是否可以对称借用左右底部页签的空余位置中的最小值，仅fixed水平模式下在底部页签之间有效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BottomTabBarStyle-symmetricExtensible(value: boolean): BottomTabBarStyle--><!--Device-BottomTabBarStyle-symmetricExtensible(value: boolean): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 底部页签的图片、文字是否可以对称借用左右底部页签的空余位置中的最小值。<br/>true：可以对称借用；false：不可以对称借用。<br/>默认值：false，底部页签的图片 、文字不可以对称借用左右底部页签的空余位置中的最小值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-na-tabcontent-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身。 |

## verticalAlign

```TypeScript
verticalAlign(value: VerticalAlign): BottomTabBarStyle
```

设置底部页签的图片、文字在垂直方向上的对齐格式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BottomTabBarStyle-verticalAlign(value: VerticalAlign): BottomTabBarStyle--><!--Device-BottomTabBarStyle-verticalAlign(value: VerticalAlign): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [VerticalAlign](../../apis-arkui/arkts-apis/arkts-arkui-verticalalign-e.md) | 是 | 底部页签的图片、文字在垂直方向上的对齐格式。<br/>默认值：VerticalAlign.Center |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-na-tabcontent-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身。 |

