# units

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ColorFilter](arkts-na-units-colorfilter-c.md) | 创建具有4*5矩阵的颜色过滤器。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilityActionOptions](arkts-na-units-accessibilityactionoptions-i.md) | 设置组件的无障碍操作的可选参数，用于限制或修改屏幕朗读等辅助应用发起的操作行为。仅Slider组件支持使用。在其他组件使用该接口时，编译环节可 正常通过，但接口功能不生效。 |
| [AccessibilityCustomAction](arkts-na-units-accessibilitycustomaction-i.md) | 自定义无障碍操作接口。 |
| [AccessibilityNextFocusParams](arkts-na-units-accessibilitynextfocusparams-i.md) | 定义无障碍自定义下一个焦点处理过程中可使用的详细参数对象。 |
| [AccessibilityOptions](arkts-na-units-accessibilityoptions-i.md) | Defines the struct of AccessibilityOptions. |
| [Area](arkts-na-units-area-i.md) | 区域类型，用于存储元素所占的区域信息。 |
| [Bias](arkts-na-units-bias-i.md) | 设置组件在锚点约束下的偏移参数。 以水平方向Bias为例，其值为组件到左锚点的距离 D&lt;sub&gt;start&lt;/sub&gt;与组件到水平方向锚点间总距离 D&lt;sub&gt;start&lt;/sub&gt; + D&lt;sub&gt;end&lt;/sub&gt;的比值。镜像语言下，D&lt;sub&gt;start&lt;/ sub&gt;为组件到右锚点的距离。下图中D&lt;sub&gt;width&lt;/sub&gt;表示组件宽度。  竖直方向同理，其值为组件到上锚点的距离D&lt;sub&gt;top&lt;/sub&gt;与组件到竖直方向锚点间总距离D&lt;sub&gt;top&lt;/sub&gt; + D&lt;sub&gt;bottom&lt;/sub&gt;的比值。下图中D&lt;sub&gt;height&lt;/sub&gt;表示组件高度。  |
| [BorderOptions](arkts-na-units-borderoptions-i.md) | 边框属性集合，用于描述边框相关信息。 |
| [BorderRadiuses](arkts-na-units-borderradiuses-i.md) | type BorderRadiuses = { topLeft: Length; topRight: Length; bottomLeft: Length; bottomRight: Length; } 圆角类型，用于描述组件边框圆角半径。 引用该对象时，至少传入一个参数。 |
| [CacheCountInfo](arkts-na-units-cachecountinfo-i.md) | 缓存数量信息。 |
| [ChainWeightOptions](arkts-na-units-chainweightoptions-i.md) | 链中组件的布局权重。 |
| [ConstraintSizeOptions](arkts-na-units-constraintsizeoptions-i.md) | 约束尺寸类型，用于描述组件布局时对尺寸大小的范围限制。 @internal/component/ets/row}、Column、 > RelativeContainer组件中，width、height设置auto表示自适应子组件。在 > TextInput组件中，width设置auto表示自适应文本宽度。 |
| [Coordinate2D](arkts-na-units-coordinate2d-i.md) | 描述一个二维坐标系。 |
| [DirectionalEdgesT](arkts-na-units-directionaledgest-i.md) | 边缘宽度类型，用于描述组件边缘不同方向的宽度。支持全球化。 |
| [DividerStyleOptions](arkts-na-units-dividerstyleoptions-i.md) | 分割线样式属性集合, 用于描述分割线相关信息。 |
| [EdgeColors](arkts-na-units-edgecolors-i.md) | type EdgeColors = { top: ResourceColor; right: ResourceColor; bottom: ResourceColor; left: ResourceColor; } 边框颜色，用于描述组件边框四条边的颜色。 引入该对象时，至少传入一个参数。 |
| [EdgeOutlineStyles](arkts-na-units-edgeoutlinestyles-i.md) | 引入该对象时，至少传入一个参数。 |
| [EdgeOutlineWidths](arkts-na-units-edgeoutlinewidths-i.md) | 引入该对象时，至少传入一个参数。 |
| [EdgeStyles](arkts-na-units-edgestyles-i.md) | type EdgeStyles = { top: BorderStyle; right: BorderStyle; bottom: BorderStyle; left: BorderStyle; } 边框样式，用于描述组件边框四条边的样式。 引入该对象时，至少传入一个参数。 |
| [EdgeWidths](arkts-na-units-edgewidths-i.md) | type EdgeWidths = { top: Length; right: Length; bottom: Length; left: Length; } 边框宽度类型，用于描述组件边框不同方向的宽度。 引入该对象时，至少传入一个参数。 |
| [Edges](arkts-na-units-edges-i.md) | 位置类型，表示相对四边的偏移量。同时设置top和bottom，仅top生效；同时设置left和right，仅left生效。 |
| [Font](arkts-na-units-font-i.md) | 设置文本样式。 |
| [ItemFillPolicy](arkts-na-units-itemfillpolicy-i.md) | 定义一个适用于WaterFlow、Grid、 List、Swiper和 [LazyVWaterFlowLayout](../../../reference/apis-arkui/arkui-ts/ts-container-lazyvwaterflowlayout.md)组件的响应式布局策略。 LazyVWaterFlowLayout组件从API版本26.0.0开始支持。 |
| [LengthConstrain](arkts-na-units-lengthconstrain-i.md) | type LengthConstrain = { minLength: Length; maxLength: Length; } 长度约束，用于对组件最大、最小长度做限制。 |
| [LocalizedBorderRadiuses](arkts-na-units-localizedborderradiuses-i.md) | 圆角类型，用于描述组件边框圆角半径。 引用该对象时，至少传入一个参数。 |
| [LocalizedEdgeColors](arkts-na-units-localizededgecolors-i.md) | 边框颜色，用于描述组件边框四条边的颜色。 引入该对象时，至少传入一个参数。 |
| [LocalizedEdgeWidths](arkts-na-units-localizededgewidths-i.md) | 边框宽度类型，用于描述组件边框不同方向的宽度。 引入该对象时，至少传入一个参数。 |
| [LocalizedEdges](arkts-na-units-localizededges-i.md) | 位置类型，表示相对四边的偏移量。同时设置top和bottom，仅top生效；同时设置start和end，仅start生效。 |
| [LocalizedPadding](arkts-na-units-localizedpadding-i.md) | 内边距类型，用于描述组件不同方向的内边距。 |
| [LocalizedPosition](arkts-na-units-localizedposition-i.md) | 位置类型，用于表示一个坐标点。 |
| [MarkStyle](arkts-na-units-markstyle-i.md) | Define the style of checkbox mark. |
| [Offset](arkts-na-units-offset-i.md) | type Offset = { dx: Length; dy: Length; } 相对布局完成位置坐标偏移量。 |
| [OutlineOptions](arkts-na-units-outlineoptions-i.md) | 外描边选项设置。 |
| [OutlineRadiuses](arkts-na-units-outlineradiuses-i.md) | 引用该对象时，至少传入一个参数。 |
| [Padding](arkts-na-units-padding-i.md) | type Padding = { top: Length; right: Length; bottom: Length; left: Length; } 内边距类型，用于描述组件不同方向的内边距。 引入该对象时，至少传入一个参数。 |
| [Position](arkts-na-units-position-i.md) | 位置类型，用于表示一个坐标点。 |
| [ScrollBarMargin](arkts-na-units-scrollbarmargin-i.md) | 滚动条边距。 |
| [SizeOptions](arkts-na-units-sizeoptions-i.md) | 宽高尺寸类型，用于描述组件布局时的宽高尺寸大小。 |
| [TouchPoint](arkts-na-units-touchpoint-i.md) | 配置跟手点坐标，不配置时，默认居中。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ColorMetrics](arkts-na-colormetrics-t.md) | 定义混合颜色。 |
| [Degree](arkts-na-degree-t.md) | 角度类型，用于描述以deg像素单位为单位的长度。 |
| [Dimension](arkts-na-dimension-t.md) | 长度类型，用于描述尺寸单位。 |
| [DrawingCanvas](arkts-na-drawingcanvas-t.md) | 可用于向DrawingRenderingContext上绘制内容的画布对象。 |
| [EdgeWidth](arkts-na-edgewidth-t.md) | 边框宽度类型，用于描述组件边框不同方向的宽度。 引入该对象时，至少传入一个参数。 |
| [FP](arkts-na-fp-t.md) | 长度类型，用于描述以fp像素单位为单位的长度。 |
| [LPX](arkts-na-lpx-t.md) | 长度类型，用于描述以lpx像素单位为单位的长度。 |
| [Length](arkts-na-length-t.md) | 长度类型，用于描述尺寸单位。 |
| [LengthMetrics](arkts-na-lengthmetrics-t.md) | 定义长度属性。 |
| [LengthMetricsUnit](arkts-na-lengthmetricsunit-t.md) | 定义长度属性单位。 |
| [LocalizedMargin](arkts-na-localizedmargin-t.md) | 外边距类型，用于描述组件不同方向的外边距。 引入该对象时，至少传入一个参数。 |
| [Margin](arkts-na-margin-t.md) | 外边距类型，用于描述组件不同方向的外边距。 引入该对象时，至少传入一个参数。 |
| [PX](arkts-na-px-t.md) | 长度类型，用于描述以px像素单位为单位的长度。 |
| [Percentage](arkts-na-percentage-t.md) | 长度类型，用于描述以百分比单位为单位的长度。 |
| [Resource](arkts-na-resource-t.md) | 资源引用类型，用于设置组件属性的值。各类资源文件，需要放入特定子目录中存储管理，资源目录的示例请参考 [资源分类](../../../quick-start/resource-categories-and-access.md#资源分类)。 可以通过`\\$r`或者`\\$rawfile`创建Resource类型对象，不可以修改Resource中的各属性的值。 - `\\$r('belonging.type.name')` belonging：系统资源或者应用资源，相应的取值为'sys'和'app'； type：资源类型，支持'boolean'、'color'、'float'、'intarray'、'integer'、'pattern'、'plural'、'strarray'、'string'、'media'； name：资源名称，在资源定义时确定。 - `\\$rawfile('filename')` filename：工程中resources/rawfile目录下的文件名称。 |
| [ResourceColor](arkts-na-resourcecolor-t.md) | 颜色类型，用于描述资源颜色类型。 |
| [ResourceStr](arkts-na-resourcestr-t.md) | 字符串类型，用于描述字符串入参可以使用的类型。 |
| [ResponsiveFillType](arkts-na-responsivefilltype-t.md) | 响应式布局填充模式，用于WaterFlow、Grid、List、Swiper和LazyVWaterFlowLayout组件。LazyVWaterFlowLayout组件从API版本26.0.0开始支持。 |
| [VP](arkts-na-vp-t.md) | 长度类型，用于描述以vp像素单位为单位的长度。 |
| [VoidCallback](arkts-na-voidcallback-t.md) | Defines VoidCallback. |

