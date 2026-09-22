# units

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ColorFilter](arkts-arkui-colorfilter-c.md) | 创建具有4*5矩阵的颜色过滤器。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilityActionOptions](arkts-arkui-accessibilityactionoptions-i.md) | 设置组件的无障碍操作的可选参数，用于限制或修改屏幕朗读等辅助应用发起的操作行为。仅[Slider](../arkts-components/arkts-arkui-slider-comp.md#slider)组件支持使用。在其他组件使用该接口时，编译环节可正常通过，但接口功能不生效。 |
| [AccessibilityCustomAction](arkts-arkui-accessibilitycustomaction-i.md) | 自定义无障碍操作接口。 |
| [AccessibilityNextFocusParams](arkts-arkui-accessibilitynextfocusparams-i.md) | 定义无障碍自定义下一个焦点处理过程中可使用的详细参数对象。 |
| [AccessibilityOptions](arkts-arkui-accessibilityoptions-i.md) | 定义AccessibilityOptions的结构体。 |
| [Area](arkts-arkui-area-i.md) | 区域类型，用于存储元素所占的区域信息。 |
| [Bias](arkts-arkui-bias-i.md) | 设置组件在锚点约束下的偏移参数。 |
| [BorderOptions](arkts-arkui-borderoptions-i.md) | 边框属性集合，用于描述边框相关信息。 |
| [CacheCountInfo](arkts-arkui-cachecountinfo-i.md) | 缓存数量信息。 |
| [ChainWeightOptions](arkts-arkui-chainweightoptions-i.md) | 链中组件的布局权重。 |
| [ConstraintSizeOptions](arkts-arkui-constraintsizeoptions-i.md) | 约束尺寸类型，用于描述组件布局时对尺寸大小的范围限制。 |
| [Coordinate2D](arkts-arkui-coordinate2d-i.md) | 描述一个二维坐标。 |
| [DirectionalEdgesT](arkts-arkui-directionaledgest-i.md) | 边缘宽度类型，用于描述组件边缘不同方向的宽度。支持全球化。 |
| [DividerStyleOptions](arkts-arkui-dividerstyleoptions-i.md) | 分割线样式属性集合，用于描述分割线相关信息。 |
| [Edges](arkts-arkui-edges-i.md) | 位置类型，表示相对四边的偏移量。同时设置top和bottom，仅top生效；同时设置left和right，仅left生效。 |
| [Font](arkts-arkui-font-i.md) | 设置文本样式。 |
| [ItemFillPolicy](arkts-arkui-itemfillpolicy-i.md) | 定义一个适用于WaterFlow、Grid、List、Swiper和LazyVWaterFlowLayout组件的响应式布局策略。LazyVWaterFlowLayout组件从API版本26.0.0开始支持。 |
| [LocalizedBorderRadiuses](arkts-arkui-localizedborderradiuses-i.md) | 圆角类型，用于描述组件边框圆角半径。 |
| [LocalizedEdgeColors](arkts-arkui-localizededgecolors-i.md) | 边框颜色，用于描述组件边框四条边的颜色。 |
| [LocalizedEdges](arkts-arkui-localizededges-i.md) | 位置类型，表示相对四边的偏移量。同时设置top和bottom，仅top生效；同时设置start和end，仅start生效。 |
| [LocalizedEdgeWidths](arkts-arkui-localizededgewidths-i.md) | 边框宽度类型，用于描述组件边框不同方向的宽度。 |
| [LocalizedPadding](arkts-arkui-localizedpadding-i.md) | 内边距类型，用于描述组件不同方向的内边距。 |
| [LocalizedPosition](arkts-arkui-localizedposition-i.md) | 位置类型，用于表示一个坐标点。 |
| [MarkStyle](arkts-arkui-markstyle-i.md) | 定义checkbox标记的样式。 |
| [OutlineOptions](arkts-arkui-outlineoptions-i.md) | 外描边选项设置。 |
| [Position](arkts-arkui-position-i.md) | 位置类型，用于表示一个坐标点。 |
| [ScrollBarMargin](arkts-arkui-scrollbarmargin-i.md) | 滚动条边距。 |
| [SizeOptions](arkts-arkui-sizeoptions-i.md) | 宽高尺寸类型，用于描述组件布局时的宽高尺寸大小。 |
| [TouchPoint](arkts-arkui-touchpoint-i.md) | 配置跟手点坐标，不配置时，默认居中。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-arkui-colormetrics-t.md) | 定义混合颜色。 |
| [Degree](arkts-arkui-degree-t.md) | 角度类型，用于描述以deg为单位的角度。 |
| [Dimension](arkts-arkui-dimension-t.md) | 长度类型，用于描述尺寸单位。 |
| [EdgeWidth](arkts-arkui-edgewidth-t.md) | 边框宽度类型，用于描述组件边框不同方向的宽度。 |
| [FP](arkts-arkui-fp-t.md) | 长度类型，用于描述以fp像素单位为单位的长度。 |
| [Length](arkts-arkui-length-t.md) | 长度类型，用于描述尺寸单位。 |
| [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | 定义长度属性。 |
| [LengthMetricsUnit](arkts-arkui-lengthmetricsunit-t.md) | 定义长度属性单位。 |
| [LocalizedMargin](arkts-arkui-localizedmargin-t.md) | 外边距类型，用于描述组件不同方向的外边距。 |
| [LPX](arkts-arkui-lpx-t.md) | 长度类型，用于描述以lpx像素单位为单位的长度。 |
| [Margin](arkts-arkui-margin-t.md) | 外边距类型，用于描述组件不同方向的外边距。 |
| [Percentage](arkts-arkui-percentage-t.md) | 长度类型，用于描述以百分比单位为单位的长度。 |
| [PX](arkts-arkui-px-t.md) | 长度类型，用于描述以px像素单位为单位的长度。 |
| [Resource](arkts-arkui-resource-t.md) | 资源引用类型，用于设置组件属性的值。各类资源文件，需要放入特定子目录中存储管理，资源目录的示例请参考[资源分类](../../../quick-start/resource-categories-and-access.md#资源分类)。 |
| [ResourceColor](arkts-arkui-resourcecolor-t.md) | 颜色类型，用于描述资源颜色类型。 |
| [ResourceStr](arkts-arkui-resourcestr-t.md) | 字符串类型，用于描述字符串入参可以使用的类型。 |
| [ResponsiveFillType](arkts-arkui-responsivefilltype-t.md) | 响应式布局填充模式，用于WaterFlow、Grid、List、Swiper和LazyVWaterFlowLayout组件。LazyVWaterFlowLayout组件从API版本26.0.0开始支持。 |
| [VoidCallback](arkts-arkui-voidcallback-t.md) | 无参数、无返回值的函数回调类型，用于定义不需要传递数据且不返回结果的回调场景。 |
| [VP](arkts-arkui-vp-t.md) | 长度类型，用于描述以vp为单位的长度。 |
