# BottomTabBarStyle

底部页签和侧边页签样式。

**起始版本：** 9

<!--Device-unnamed-declare class BottomTabBarStyle--><!--Device-unnamed-declare class BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)
```

BottomTabBarStyle的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)--><!--Device-BottomTabBarStyle-constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | ResourceStr \| TabBarSymbol | 是 | 页签内的图片内容。当图标资源加载失败或不存在时，显示灰色图块。如果icon采用svg格式图源，需删除其内置的宽高属性。 否则，icon大小将使用svg图源内置的宽高属性值。<br>**起始版本：** 9 - 11 |
| text | ResourceStr | 是 | 页签内的文字内容。 |

## iconStyle

```TypeScript
iconStyle(style: TabBarIconStyle): BottomTabBarStyle
```

设置底部页签的图标样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-iconStyle(style: TabBarIconStyle): BottomTabBarStyle--><!--Device-BottomTabBarStyle-iconStyle(style: TabBarIconStyle): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TabBarIconStyle](arkts-arkui-tabbariconstyle-i.md) | 是 | 底部页签的label图标的样式，用于设置图标的选中态和未选中态颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身，用于链式调用。 |

## id

```TypeScript
id(value: string): BottomTabBarStyle
```

底部页签的id。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-id(value: string): BottomTabBarStyle--><!--Device-BottomTabBarStyle-id(value: string): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 底部页签的id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身，用于链式调用。 |

## labelStyle

```TypeScript
labelStyle(value: LabelStyle): BottomTabBarStyle
```

设置底部页签的label文本和字体的样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-labelStyle(value: LabelStyle): BottomTabBarStyle--><!--Device-BottomTabBarStyle-labelStyle(value: LabelStyle): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LabelStyle](arkts-arkui-labelstyle-i.md) | 是 | 底部页签的label文本和字体的样式，用于设置文字的颜色、大小、字体、行数等属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身，用于链式调用。 |

## layoutMode

```TypeScript
layoutMode(value: LayoutMode): BottomTabBarStyle
```

设置底部页签的图片、文字排布的方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-layoutMode(value: LayoutMode): BottomTabBarStyle--><!--Device-BottomTabBarStyle-layoutMode(value: LayoutMode): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LayoutMode](arkts-arkui-layoutmode-e.md) | 是 | 底部页签的图片、文字排布的方式，具体参照LayoutMode枚举。<br/>默认值：LayoutMode.VERTICAL |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身，用于链式调用。 |

## of

```TypeScript
static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle
```

BottomTabBarStyle的静态构造函数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle--><!--Device-BottomTabBarStyle-static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | ResourceStr \| TabBarSymbol | 是 | 页签内的图片内容。当图标资源加载失败或不存在时，显示灰色图块。如果icon采用svg格式图源，需删除其内置的宽高属性。 否则，icon大小将使用svg图源内置的宽高属性值。<br>**起始版本：** 10 - 11 |
| text | ResourceStr | 是 | 页签内的文字内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | 返回创建的BottomTabBarStyle对象，用于设置底部页签和侧边页签样式。 |

## padding

```TypeScript
padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle
```

设置底部页签的内边距属性（不支持百分比设置）。使用Dimension时，四个方向内边距同时生效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle--><!--Device-BottomTabBarStyle-padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Padding \| Dimension \| LocalizedPadding | 是 | 底部页签的内边距，用于设置页签内容与边界的距离（不支持百分比设置）。当需要调整页签内部空间分布、 优化视觉效果时传入自定义值。<br/>取值范围：[0, +∞]<br/>默认值：{left:4.0vp,right:4.0vp,top:0.0vp,bottom: 0.0vp}<br/>使用LocalizedPadding时，支持镜像能力。&lt;br /&gt;默认值：{start:LengthMetrics.vp(4),end:LengthMetrics.vp(4),<br/>top: LengthMetrics.vp(0),bottom:LengthMetrics.vp(0)}<br>**起始版本：** 10 - 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身，用于链式调用。 |

## symmetricExtensible

```TypeScript
symmetricExtensible(value: boolean): BottomTabBarStyle
```

设置底部页签的图片、文字是否可以对称借用左右底部页签的空余位置中的最小值，仅fixed水平模式下在底部页签之间有效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-symmetricExtensible(value: boolean): BottomTabBarStyle--><!--Device-BottomTabBarStyle-symmetricExtensible(value: boolean): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 底部页签的图片、文字是否可以对称借用左右底部页签的空余位置中的最小值。 传入true启用对称借用功能（当需要优化页签布局、充分利用空间时选择），传入false禁用对称借用功能（当需要保持页签固定布局、避免页签内容位置变化时选择）。<br/>默认值：false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身。 |

## verticalAlign

```TypeScript
verticalAlign(value: VerticalAlign): BottomTabBarStyle
```

设置底部页签的图片、文字在垂直方向上的对齐格式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-verticalAlign(value: VerticalAlign): BottomTabBarStyle--><!--Device-BottomTabBarStyle-verticalAlign(value: VerticalAlign): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | VerticalAlign | 是 | 底部页签的图片、文字在垂直方向上的对齐格式。<br/>默认值：VerticalAlign.Center |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | 返回BottomTabBarStyle对象本身，用于链式调用。 |

