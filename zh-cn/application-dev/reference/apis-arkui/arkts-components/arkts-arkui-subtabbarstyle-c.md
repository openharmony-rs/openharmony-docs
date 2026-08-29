# SubTabBarStyle

子页签样式。打开后在切换页签时会播放跳转动画。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## board

```TypeScript
board(value: BoardStyle): SubTabBarStyle
```

设置选中子页签的背板风格。子页签的背板风格仅在水平模式下有效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BoardStyle](arkts-arkui-boardstyle-i.md) | 是 | 选中子页签的背板风格对象，用于设置背板的圆角半径等样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身，用于链式调用。 |

## constructor

```TypeScript
constructor(content: ResourceStr)
```

SubTabBarStyle的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 页签内的文字内容。 |

## constructor

```TypeScript
constructor(content: ResourceStr | ComponentContent)
```

SubTabBarStyle的构造函数。支持ComponentContent设置自定义内容。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| ComponentContent | 是 | 页签内的内容。   **说明：** 1.自定义内容不支持labelStyle属性。 2.自定义内容超 出页签范围，则不显示超出部分。 3.自定义内容小于页签范围，则会居中对齐。 4.自定义内容异常或无可用显示组件，则显示空白。 |

## id

```TypeScript
id(value: string): SubTabBarStyle
```

设置子页签的id。可用于通过TabsController查找或控制指定页签，以及在状态管理和事件处理中标识不同的页签。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 子页签的id，用于标识和区分不同的页签。当需要通过代码控制特定页签的显示、隐藏或进行其他操作时，可设置此参数。id值需在同一Tabs组件内保持唯一。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身，用于链式调用。 |

## indicator

```TypeScript
indicator(value: IndicatorStyle): SubTabBarStyle
```

设置选中子页签的下划线风格。子页签的下划线风格仅在水平模式下有效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [IndicatorStyle](arkts-arkui-indicatorstyle-i.md) | 是 | 选中子页签的下划线风格对象，用于设置下划线的颜色、高度、宽度、圆角半径等样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身。 |

## indicator

```TypeScript
indicator(value: IndicatorStyle | DrawableTabBarIndicator): SubTabBarStyle
```

设置选中子页签的下划线风格。与[indicator](#indicator)相比，新增了图片格式的下划线风格，图片的显示效果参照 [ImageFit.Cover](../arkts-apis/arkts-arkui-imagefit-e.md)。子页签的下划线风格仅在水平模式下有效。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [IndicatorStyle](arkts-arkui-indicatorstyle-i.md) \| [DrawableTabBarIndicator](arkts-arkui-drawabletabbarindicator-i.md) | 是 | 选中子页签的下划线风格对象。IndicatorStyle：一般形式的下划线样式。DrawableTabBarIndicator：图片形式的下划线样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身，用于链式调用。 |

## labelStyle

```TypeScript
labelStyle(value: LabelStyle): SubTabBarStyle
```

设置子页签的label文本和字体的样式。子页签的label文本和字体的样式仅在水平模式下有效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LabelStyle](arkts-arkui-labelstyle-i.md) | 是 | 子页签的label文本和字体的样式对象，用于设置文字的颜色、大小、字体、行数等属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身，用于链式调用。 |

## of

```TypeScript
static of(content: ResourceStr): SubTabBarStyle
```

SubTabBarStyle的静态构造函数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 页签内的文字内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md) | 返回创建的SubTabBarStyle对象，用于设置子页签样式。 |

## of

```TypeScript
static of(content: ResourceStr | ComponentContent): SubTabBarStyle
```

SubTabBarStyle的静态构造函数。支持ComponentContent设置自定义内容。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| ComponentContent | 是 | 页签内的内容。支持ComponentContent设置自定义内容。   **说明：** 1.自定义内容不支持 labelStyle属性。 2.自定义内容超出页签范围，则不显示超出部分。 3.自定义内容小于页签范围，则会居中对齐。 4.自定义内容异常或无可用显示组件，则显示空白。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md) | 返回创建的SubTabBarStyle对象，用于设置子页签样式。 |

## padding

```TypeScript
padding(value: Padding | Dimension): SubTabBarStyle
```

设置子页签的内边距属性（不支持百分比设置）。使用Dimension时，四个方向内边距同时生效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Padding \| [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 子页签的内边距属性（不支持百分比设置），用于调整页签内容与边界的距离。取值范围：[0, +∞]异常值时取默认值。默认值： {left:8.0vp,right:8.0vp,top:17.0vp,bottom:18.0vp}   **说明：**从API version 12开始， 参数支持LocalizedPadding类型，支持镜像能力。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身，用于链式调用。 |

## padding

```TypeScript
padding(padding: LocalizedPadding): SubTabBarStyle
```

设置子页签的内边距属性，支持镜像能力（不支持百分比设置）。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| padding | [LocalizedPadding](../arkts-apis/arkts-arkui-localizedpadding-i.md) | 是 | 子页签的内边距属性（不支持百分比设置），用于调整页签内容与边界的距离，支持镜像能力。 取值范围：[0, +∞]异常值时取默认值。默认值： {start:LengthMetrics.vp(8),end:LengthMetrics.vp(8),top:LengthMetrics.vp(17),bottom:LengthMetrics.vp(18)} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身，用于链式调用。 |

## selectedMode

```TypeScript
selectedMode(value: SelectedMode): SubTabBarStyle
```

设置选中子页签的显示方式。子页签的显示方式仅在水平模式下有效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SelectedMode](arkts-arkui-selectedmode-e.md) | 是 | 选中子页签的显示方式，用于控制子页签的选中效果样式。可选值：SelectedMode.INDICATOR（使用下划线模式，适用于需要明确指示选中状态的场景）、 SelectedMode.BOARD（使用背板模式，适用于需要突出选中页签的场景）。默认值：SelectedMode.INDICATOR |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md) | 返回SubTabBarStyle对象本身，用于链式调用。 |
