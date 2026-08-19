# Common

Common通用接口

## Common

```TypeScript
Common()
```

构造器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonInterface-(): CommonAttribute--><!--Device-CommonInterface-(): CommonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilityHoverEvent](arkts-arkui-accessibilityhoverevent-i.md) | The accessibility hover action triggers this method invocation. |
| [AlignRuleOption](arkts-arkui-alignruleoption-i.md) | Defines the align rule options of relative container. |
| [AnimatableArithmetic](arkts-arkui-animatablearithmetic-i.md) | 该接口定义非number数据类型的动画运算规则。对非number类型的数据（如数组、结构体、颜色等）做动画，需要实现AnimatableArithmetic\&lt;T\&gt;接口中加法、减法、乘法和判断相等函数，使得该数据能参与动画的插值运算 和识别该数据是否发生改变。即定义它们为实现了AnimatableArithmetic\&lt;T\&gt;接口的类型。 |
| [AnimateParam](arkts-arkui-animateparam-i.md) | 动画效果相关参数。 |
| [AreaChangeOptions](arkts-arkui-areachangeoptions-i.md) | 区域变化相关的参数。 |
| [AttributeModifier](arkts-arkui-attributemodifier-i.md) | Defines the attribute modifier. |
| [AxisEvent](arkts-arkui-axisevent-i.md) | 轴事件的对象说明，继承于[BaseEvent](arkts-arkui-baseevent-i.md)。 |
| [BackgroundBlurStyleOptions](arkts-arkui-backgroundblurstyleoptions-i.md) | 继承自[BlurStyleOptions](arkts-arkui-blurstyleoptions-i.md)。 |
| [BackgroundBrightnessOptions](arkts-arkui-backgroundbrightnessoptions-i.md) | 背景亮度选项。 |
| [BackgroundEffectOptions](arkts-arkui-backgroundeffectoptions-i.md) | 背景效果参数。 |
| [BackgroundImageOptions](arkts-arkui-backgroundimageoptions-i.md) | 定义背景图选项。 |
| [BackgroundOptions](arkts-arkui-backgroundoptions-i.md) | 指定背景选项 |
| [BaseEvent](arkts-arkui-baseevent-i.md) | 基础事件类型。 |
| [BindOptions](arkts-arkui-bindoptions-i.md) | 半模态、全模态的公共配置接口。 |
| [BlurOptions](arkts-arkui-bluroptions-i.md) | 灰阶模糊参数。 |
| [BlurStyleOptions](arkts-arkui-blurstyleoptions-i.md) | 内容模糊选项。 |
| [BorderImageOption](arkts-arkui-borderimageoption-i.md) | Border image option |
| [Callback](arkts-arkui-callback-i.md) | 定义基础的回调函数。 |
| [CaretOffset](arkts-arkui-caretoffset-i.md) | CaretOffset info. |
| [ClickEffect](arkts-arkui-clickeffect-i.md) | 定义点击效果。 |
| [ClickEvent](arkts-arkui-clickevent-i.md) | 继承于[BaseEvent](arkts-arkui-baseevent-i.md)。 |
| [CommonConfiguration](arkts-arkui-commonconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。 |
| [ComponentOptions](arkts-arkui-componentoptions-i.md) | 自定义组件参数，用于配置是否支持组件冻结和全局复用池，适用于需要优化自定义组件性能表现和提升组件复用效率的场景。 |
| [Configuration](arkts-arkui-configuration-i.md) | Defines the data type of the interface restriction. |
| [ContentCoverOptions](arkts-arkui-contentcoveroptions-i.md) | 继承自[BindOptions](arkts-arkui-bindoptions-i.md)。 全屏模态页面内容选项。 |
| [ContentModifier](arkts-arkui-contentmodifier-i.md) | 开发者需要自定义class实现ContentModifier接口。 |
| [ContextMenuAnimationOptions](arkts-arkui-contextmenuanimationoptions-i.md) | 长按预览时显示的样式信息。 |
| [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) | 菜单项的信息。 **表1：同时设置offset与placement时菜单的偏移位置** | placement设置的值 | 菜单的偏移量说明 | | ------------------------------------------------------------ | ------------------------------------------------------------ | | Placement.TopLeft、Placement.Top、Placement.TopRight | offset的x为正数，菜单相对组件向右进行偏移，offset的y为正数，菜单相对组件向上进行偏移。 | | Placement.BottomLeft、Placement.Bottom、Placement.BottomRight | offset的x为正数，菜单相对组件向左进行偏移，offset的y为正数，菜单相对组件向下进行偏移。 | | Placement.RightTop、Placement.Right、Placement.RightBottom | offset的x为正数，菜单相对组件向右进行偏移，offset的y为正数，菜单相对组件向下进行偏移。 | **表2：同时设置arrowOffset与placement时菜单箭头的默认位置** | placement设置的值 | 菜单箭头的位置说明 | | ------------------------------------------- | ------------------------------------------------------------ | | Placement.Top、Placement.Bottom | 箭头显示在水平方向且默认居中，且距离菜单左侧边缘距离为箭头安全距离。 | | Placement.Left、Placement.Right | 箭头显示在垂直方向且默认居中，且距离菜单上侧距离为箭头安全距离。 | | Placement.TopLeft、Placement.BottomLeft | 箭头默认显示在水平方向，且距离菜单左侧边缘距离为箭头安全距离。 | | Placement.TopRight、Placement.BottomRight | 箭头默认显示在水平方向，且距离菜单右侧距离为箭头安全距离。 | | Placement.LeftTop、Placement.RightTop | 箭头默认显示在垂直方向，且距离菜单上侧距离为箭头安全距离。 | | Placement.LeftBottom、Placement.RightBottom | 箭头默认显示在垂直方向，且距离菜单下侧距离为箭头安全距离。 | **表3：enableArrow为true且placement未设置或者值为非法值的菜单默认位置** | 接口 | 菜单默认位置 | |------|-------------| | [bindMenu](arkts-arkui-commonmethod-c.md#bindmenu) | Placement.BottomLeft | | [bindMenu&lt;sup&gt;11+&lt;/sup&gt;](arkts-arkui-commonmethod-c.md#bindmenu) | Placement.BottomLeft | | [bindContextMenu&lt;sup&gt;8+&lt;/sup&gt;](arkts-arkui-commonmethod-c.md#bindcontextmenu) | Placement.Top | | [bindContextMenu&lt;sup&gt;12+&lt;/sup&gt;](arkts-arkui-commonmethod-c.md#bindcontextmenu) | Placement.BottomLeft | | [bindContextMenuWithResponse&lt;sup&gt;23+&lt;/sup&gt;](arkts-arkui-commonmethod-c.md#bindcontextmenuwithresponse) | Placement.Top | |
| [CrownEvent](arkts-arkui-crownevent-i.md) | 组件接收表冠事件的数据结构。内容包括时间戳、旋转角速度、旋转角度、表冠动作和阻止事件冒泡。 |
| [CustomPopupOptions](arkts-arkui-custompopupoptions-i.md) | 弹出自定义气泡的信息。 |
| [DateRange](arkts-arkui-daterange-i.md) | Defines a range of dates. |
| [DepthColorRGB](arkts-arkui-depthcolorrgb-i-sys.md) | 深度空间中的RGB颜色。 |
| [DepthVector3](arkts-arkui-depthvector3-i-sys.md) | 深度空间中的三维向量。 |
| [DepthVector4](arkts-arkui-depthvector4-i-sys.md) | 深度空间中的4D向量。 |
| [DismissContentCoverAction](arkts-arkui-dismisscontentcoveraction-i.md) | Component content cover dismiss |
| [DismissPopupAction](arkts-arkui-dismisspopupaction-i.md) | 气泡关闭的信息。 |
| [DismissSheetAction](arkts-arkui-dismisssheetaction-i.md) | 半模态关闭前的回调。 |
| [DragEvent](arkts-arkui-dragevent-i.md) | 拖拽事件信息。 |
| [DragInteractionOptions](arkts-arkui-draginteractionoptions-i.md) | 设置拖拽过程中预览图浮起的交互模式。 |
| [DragItemInfo](arkts-arkui-dragiteminfo-i.md) | 定义拖拽过程中拖拽项的相关信息。 |
| [DragPreviewOptions](arkts-arkui-dragpreviewoptions-i.md) | 设置拖拽过程中预览图处理模式及数量角标的显示。 |
| [DropOptions](arkts-arkui-dropoptions-i.md) | 设置落入过程的参数。 |
| [EdgeEffectOptions](arkts-arkui-edgeeffectoptions-i.md) | [edgeEffect](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#edgeeffect11)属性参数对象。 |
| [EdgeLightParams](arkts-arkui-edgelightparams-i-sys.md) | 定义边缘流光效果参数。 |
| [EditModeOptions](arkts-arkui-editmodeoptions-i.md) | List/Grid组件编辑模式选项属性参数对象。 |
| [EntryOptions](arkts-arkui-entryoptions-i.md) | 页面入口配置选项，用于在\@Entry装饰页面时配置路由名称、状态存储和共享存储等参数。 |
| [EventTarget](arkts-arkui-eventtarget-i.md) | [BaseEvent](arkts-arkui-baseevent-i.md)中参数target的类型。 触发事件的元素对象的显示区域。 |
| [ExpectedFrameRateRange](arkts-arkui-expectedframeraterange-i.md) | 设置动画期望的帧率。 |
| [FadingEdgeOptions](arkts-arkui-fadingedgeoptions-i.md) | [fadingEdge](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#fadingedge14)属性边缘渐隐参数对象。 |
| [FocusAxisEvent](arkts-arkui-focusaxisevent-i.md) | 焦点轴事件的对象说明，继承于[BaseEvent](arkts-arkui-baseevent-i.md)。 |
| [FocusMovement](arkts-arkui-focusmovement-i.md) | 设置对应的按键对应的走焦目的组件，缺省则遵循默认走焦规则。 |
| [ForegroundBlurStyleOptions](arkts-arkui-foregroundblurstyleoptions-i.md) | 继承自[BlurStyleOptions](arkts-arkui-blurstyleoptions-i.md)，设置内容模糊选项。 |
| [ForegroundEffectOptions](arkts-arkui-foregroundeffectoptions-i.md) | 前景效果参数。 |
| [GeometryInfo](arkts-arkui-geometryinfo-i.md) | 父组件（自定义组件）布局信息，继承自[SizeResult](arkts-arkui-sizeresult-i.md)。 |
| [GeometryTransitionOptions](arkts-arkui-geometrytransitionoptions-i.md) |  |
| [GestureModifier](arkts-arkui-gesturemodifier-i.md) | 开发者需要自定义class实现GestureModifier接口。 |
| [GravityCenterOptions](arkts-arkui-gravitycenteroptions-i-sys.md) | 定义引力中心的参数。 |
| [HistoricalPoint](arkts-arkui-historicalpoint-i.md) | 历史点信息。 |
| [HorizontalAlignParam](arkts-arkui-horizontalalignparam-i.md) | 定义相对容器的水平对齐规则。 |
| [HoverEvent](arkts-arkui-hoverevent-i.md) | 继承于[BaseEvent](arkts-arkui-baseevent-i.md)。 |
| [ICurve](arkts-arkui-icurve-i.md) | 曲线对象。 |
| [IMonitor](arkts-arkui-imonitor-i.md) | 当监听的状态变量变化时，状态管理框架侧将回调开发者注册的函数，并传入变化信息。变化信息的类型为IMonitor。 |
| [IMonitorValue](arkts-arkui-imonitorvalue-i.md) |  |
| [InputCounterOptions](arkts-arkui-inputcounteroptions-i.md) | Define the ratio of characters entered by the the percentage of InputCounterOptions. |
| [InputEventInterceptResult](arkts-arkui-inputeventinterceptresult-i.md) | 输入事件拦截结果接口，用于监听器回调[InputEventListener](arkts-arkui-inputeventlistener-t.md)返回是否拦截的决策。 |
| [InputEventMonitor](arkts-arkui-inputeventmonitor-i.md) | 输入事件监听器标识对象。 此对象由系统创建并返回，作为监听器的唯一标识。 |
| [InvertOptions](arkts-arkui-invertoptions-i.md) | 前景智能取反色。 |
| [ItemDragEventHandler](arkts-arkui-itemdrageventhandler-i.md) | 定义拖拽事件 |
| [ItemDragInfo](arkts-arkui-itemdraginfo-i.md) | 拖拽点信息对象。 |
| [KeyEvent](arkts-arkui-keyevent-i.md) | 按键事件信息。 |
| [KeyframeAnimateParam](arkts-arkui-keyframeanimateparam-i.md) | 动画选项设置。 |
| [KeyframeState](arkts-arkui-keyframestate-i.md) | 设置关键帧选项。 |
| [Layoutable](arkts-arkui-layoutable-i.md) | 子组件布局信息。 |
| [LayoutBorderInfo](arkts-arkui-layoutborderinfo-i.md) | 子组件边框信息 |
| [LayoutChild](arkts-arkui-layoutchild-i.md) | 布局和测量发生时，框架传递给子组件的信息。 |
| [LayoutInfo](arkts-arkui-layoutinfo-i.md) | 子组件布局位置信息 |
| [LightSource](arkts-arkui-lightsource-i-sys.md) | 一个组件支持添加1个光源。 |
| [LinearGradient](arkts-arkui-lineargradient-i.md) | Linear Gradient Interface |
| [LinearGradientBlurOptions](arkts-arkui-lineargradientbluroptions-i.md) |  |
| [LinearGradientOptions](arkts-arkui-lineargradientoptions-i.md) | 线性渐变的参数。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |
| [LocalizedAlignRuleOptions](arkts-arkui-localizedalignruleoptions-i.md) | Defines the Localized align rule options of relative container. |
| [LocalizedHorizontalAlignParam](arkts-arkui-localizedhorizontalalignparam-i.md) | Defines the localized horizontal align param of relative container. |
| [LocalizedVerticalAlignParam](arkts-arkui-localizedverticalalignparam-i.md) | Defines the localized vertical align param of relative container. |
| [Measurable](arkts-arkui-measurable-i.md) | 子组件位置信息。 |
| [MeasureResult](arkts-arkui-measureresult-i.md) | Sub component MeasureResult info. |
| [MenuElement](arkts-arkui-menuelement-i.md) | 菜单项的图标、文本和交互信息。 |
| [MenuGridStyleOptions](arkts-arkui-menugridstyleoptions-i.md) | 菜单栅格样式选项。 |
| [MenuMaskType](arkts-arkui-menumasktype-i.md) | 设置蒙层样式。 |
| [MenuOptions](arkts-arkui-menuoptions-i.md) | 配置弹出菜单的参数，继承自[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)。 |
| [MonitorDecoratorOptions](arkts-arkui-monitordecoratoroptions-i.md) |  |
| [MotionBlurAnchor](arkts-arkui-motionbluranchor-i.md) | Define motion blur anchor coordinates. |
| [MotionBlurOptions](arkts-arkui-motionbluroptions-i.md) | 运动模糊选项。 |
| [MotionPathOptions](arkts-arkui-motionpathoptions-i.md) | 设置组件的运动路径。 |
| [MouseEvent](arkts-arkui-mouseevent-i.md) | 继承于[BaseEvent](arkts-arkui-baseevent-i.md)。 |
| [MouseHistoricalPoint](arkts-arkui-mousehistoricalpoint-i.md) | 鼠标事件历史点信息。 历史点按时间顺序排列，获取到的第一个历史点是最早发生的事件的信息，最后一个是最新发生事件的信息。历史点的数量取决于系统事件队列的配置和硬件性能。历史点主要用于如下场景： 1. 平滑绘制：使用历史点可以实现更平滑的绘制效果，特别是在鼠标快速移动时。 2. 手势识别：通过分析历史点的轨迹，可以识别各种鼠标手势。 3. 性能优化：在一个事件回调中处理多个历史点，减少事件处理频率，提升性能。 4. 轨迹分析：分析鼠标移动轨迹，用于绘图应用或手势控制。 5. 数据分析：历史点中的timestamp可用于计算鼠标移动速度。 |
| [MultiShadowOptions](arkts-arkui-multishadowoptions-i.md) | 投影样式参数。 |
| [NestedScrollOptions](arkts-arkui-nestedscrolloptions-i.md) | [nestedScroll](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#nestedscroll11)属性参数对象。 |
| [OverlayOffset](arkts-arkui-overlayoffset-i.md) | 设置浮层基于自身左上角的偏移量。浮层默认处于组件左上角。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |
| [OverlayOptions](arkts-arkui-overlayoptions-i.md) | 浮层的定位。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 > > align和offset都设置时，效果重叠，浮层相对于组件方位定位后，再基于当前位置的左上角进行偏移。 |
| [PickerDialogButtonStyle](arkts-arkui-pickerdialogbuttonstyle-i.md) | Provide an interface for the button style of picker |
| [PickerTextStyle](arkts-arkui-pickertextstyle-i.md) | Provide an interface for the text style of picker |
| [PixelMapMock](arkts-arkui-pixelmapmock-i-sys.md) | 带有release函数的像素图对象。 |
| [PixelRoundPolicy](arkts-arkui-pixelroundpolicy-i.md) | 指定组件级像素取整的方向。 |
| [PixelStretchEffectOptions](arkts-arkui-pixelstretcheffectoptions-i.md) | 像素扩展属性集合，用于描述像素扩展的信息。 |
| [PointLightStyle](arkts-arkui-pointlightstyle-i-sys.md) | 通过设置光源和被照亮的类型实现点光源照亮周围组件的UI效果。 |
| [PopupBorderLinearGradient](arkts-arkui-popupborderlineargradient-i.md) | 弹出边框线性渐变色。 |
| [PopupCommonOptions](arkts-arkui-popupcommonoptions-i.md) | 配置弹出气泡的参数。使用[UIContext](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md)中的 [getPromptAction()](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取到 [PromptAction](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-promptaction-c.md)对象，再通过该对象调用 [openPopup](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#openpopup)和 [updatePopup](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup)时传入的options参数。 |
| [PopupMaskType](arkts-arkui-popupmasktype-i.md) | 设置遮罩层颜色。 |
| [PopupMessageOptions](arkts-arkui-popupmessageoptions-i.md) | 气泡文本的样式。 |
| [PopupOptions](arkts-arkui-popupoptions-i.md) | 基础气泡的信息。 |
| [PopupStateChangeParam](arkts-arkui-popupstatechangeparam-i.md) | 气泡的显示状态。 |
| [PreviewConfiguration](arkts-arkui-previewconfiguration-i.md) | 配置自定义拖拽过程中的预览图样式。 |
| [PreviewParams](arkts-arkui-previewparams-i.md) | Define Preview property |
| [ProvideOptions](arkts-arkui-provideoptions-i.md) | ProvideOptions是\@Provide的选项。允许在同一组件树上通过allowOverride重写同名的\@Provide，适用于子组件需要覆盖父组件同名\@Provide值的场景，提高了跨层级状态管理的灵活性。具体例子可见 [\@Provide支持allowOverride参数](../../../ui/state-management/arkts-provide-and-consume.md#provide支持allowoverride参数)。 |
| [RadialGradientOptions](arkts-arkui-radialgradientoptions-i.md) | 径向渐变参数。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |
| [Rectangle](arkts-arkui-rectangle-i.md) | 矩形区域类型。 |
| [RectResult](arkts-arkui-rectresult-i.md) | 位置和尺寸类型，用于描述组件的位置和宽高。 |
| [ResponseRegion](arkts-arkui-responseregion-i.md) | 由输入工具类型、触摸位置和大小组成的触摸热区。 |
| [ReusableOptions](arkts-arkui-reusableoptions-i.md) | 可复用自定义组件的参数，用于配置内存优化策略，适用于需要降低可复用自定义组件内存使用量的场景。 |
| [ReuseOptions](arkts-arkui-reuseoptions-i.md) | 复用选项，用于配置复用标识ID，相同复用标识ID的组件会被互相复用，提高复用匹配的精确度。 |
| [RotateAngleOptions](arkts-arkui-rotateangleoptions-i.md) | 指定各轴旋转角的旋转参数选项。 |
| [RotateOptions](arkts-arkui-rotateoptions-i.md) | 组件旋转参数。 |
| [ScaleOptions](arkts-arkui-scaleoptions-i.md) |  |
| [SelectionOptions](arkts-arkui-selectionoptions-i.md) | Defines the selection options. |
| [ShadowOptions](arkts-arkui-shadowoptions-i.md) | 阴影属性集合，用于设置阴影的模糊半径、阴影的颜色、X轴和Y轴的偏移量。 |
| [sharedTransitionOptions](arkts-arkui-sharedtransitionoptions-i.md) | 共享元素转场动画参数。 |
| [SheetDismiss](arkts-arkui-sheetdismiss-i.md) | 控制半模态的关闭。 |
| [SheetOptions](arkts-arkui-sheetoptions-i.md) | 继承自[BindOptions](arkts-arkui-bindoptions-i.md)。 半模态页面内容选项。 |
| [SheetTitleOptions](arkts-arkui-sheettitleoptions-i.md) | 半模态面板的标题。 |
| [SizeResult](arkts-arkui-sizeresult-i.md) | 组件尺寸信息。 |
| [SmartGestureShortcutOptions](arkts-arkui-smartgestureshortcutoptions-i.md) | 智慧手势响应行为配置对象。 |
| [SpatialEffectParams](arkts-arkui-spatialeffectparams-i-sys.md) | 空间效果选项。 |
| [SpatialPosition](arkts-arkui-spatialposition-i-sys.md) | 三维空间中的空间角位置。 |
| [SpringBackAction](arkts-arkui-springbackaction-i.md) | 控制半模态关闭前的回弹。 |
| [StateStyles](arkts-arkui-statestyles-i.md) | 组件不同状态下的样式。 |
| [SweepGradientOptions](arkts-arkui-sweepgradientoptions-i.md) | 角度渐变参数。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |
| [SystemAdaptiveOptions](arkts-arkui-systemadaptiveoptions-i.md) | 系统自适应调节参数，系统会默认开启根据芯片算力进行自适应效果调节的能力。 |
| [TextContentControllerOptions](arkts-arkui-textcontentcontrolleroptions-i.md) | Defines the span options of TextContentController. |
| [TextDecorationOptions](arkts-arkui-textdecorationoptions-i.md) | Defines the options of decoration. |
| [TipsOptions](arkts-arkui-tipsoptions-i.md) | 悬浮气泡自定义参数。 |
| [TouchEvent](arkts-arkui-touchevent-i.md) | 继承于[BaseEvent](arkts-arkui-baseevent-i.md)。在非事件注入场景下，changedTouches是按屏幕刷新率重采样的点，而touches是按器件刷新率上报的点，因此changedTouches与touches的数据可 能不同。 |
| [TouchObject](arkts-arkui-touchobject-i.md) | 触摸事件类型。 |
| [TransitionOptions](arkts-arkui-transitionoptions-i.md) | TransitionOptions通过指定结构体内的参数来指定转场效果。 |
| [TranslateOptions](arkts-arkui-translateoptions-i.md) | Defines the options of translate. |
| [UICommonEvent](arkts-arkui-uicommonevent-i.md) | 用于设置基础事件回调。方法入参为undefined的时候，重置对应的事件回调。 |
| [UIGestureEvent](arkts-arkui-uigestureevent-i.md) | 用于设置组件绑定的手势。 |
| [UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md) | 用于设置滚动事件回调。 |
| [VerticalAlignParam](arkts-arkui-verticalalignparam-i.md) | 定义相对容器的垂直对齐规则。 |
| [VisibleAreaEventOptions](arkts-arkui-visibleareaeventoptions-i.md) | 关于区域变化相关的参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AccessibilityActionInterceptCallback](arkts-arkui-accessibilityactioninterceptcallback-t.md) | 定义在可访问性操作拦截中使用的回调类型。 action的值表示可访问性动作类型。 |
| [AccessibilityCallback](arkts-arkui-accessibilitycallback-t.md) | Defines the callback type used in accessibility hover events. The value of isHover indicates whether the touch is hovering over the component. The value of event contains information about AccessibilityHoverEvent. |
| [AccessibilityFocusCallback](arkts-arkui-accessibilityfocuscallback-t.md) | Defines the callback type used in accessibility focus. The value of isFocus indicates whether the current component is focused |
| [AccessibilityTransparentCallback](arkts-arkui-accessibilitytransparentcallback-t.md) | Defines the callback type used in accessibility hover transparent event. |
| [AnimationRange](arkts-arkui-animationrange-t.md) | 动画开始和结束时相对预览原图缩放比例。 |
| [AreaChangeCallback](arkts-arkui-areachangecallback-t.md) | 组件区域变化事件的回调类型。 |
| [Blender](arkts-arkui-blender-t-sys.md) | Blender |
| [BorderRadiusType](arkts-arkui-borderradiustype-t.md) | 圆角类型。 |
| [BuilderCallback](arkts-arkui-buildercallback-t.md) | `BuilderCallback`是全局`@Builder`函数的类型别名，作为`mutableBuilder`函数的入参类型，用于指定待封装的全局`@Builder`函数。 |
| [CircleShape](arkts-arkui-circleshape-t.md) | 导入CircleShape类型对象。 |
| [ComponentContent](arkts-arkui-componentcontent-t.md) | 组件内容的实体封装。 |
| [Context](arkts-arkui-context-t.md) | Get context. |
| [CustomBuilder](arkts-arkui-custombuilder-t.md) | 定义CustomBuilder类型。 |
| [CustomBuilderT](arkts-arkui-custombuildert-t.md) | 定义带参数的CustomBuilder类型 |
| [DataLoadParams](arkts-arkui-dataloadparams-t.md) | 落入操作时使用的数据加载参数。 |
| [DataSyncOptions](arkts-arkui-datasyncoptions-t.md) | 作为startDataLoading的入参对象。 |
| [DragSpringLoadingConfiguration](arkts-arkui-dragspringloadingconfiguration-t.md) | 定义拖拽的悬停检测配置参数的接口。 |
| [DrawContext](arkts-arkui-drawcontext-t.md) | DrawContext |
| [EllipseShape](arkts-arkui-ellipseshape-t.md) | 导入EllipseShape类型对象。 |
| [EnvDecorator](arkts-arkui-envdecorator-t.md) | 定义EnvDecorator属性装饰器类型。 |
| [Filter](arkts-arkui-filter-t.md) | 导入Filter类型对象。 |
| [FractionStop](arkts-arkui-fractionstop-t.md) | 定义模糊段。 |
| [GestureCollectInterceptCallback](arkts-arkui-gesturecollectinterceptcallback-t.md) | 定义在[onGestureCollectIntercept](arkts-arkui-commonmethod-c.md#ongesturecollectintercept)中使用的回调类型。 |
| [GestureRecognizerJudgeBeginCallback](arkts-arkui-gesturerecognizerjudgebegincallback-t.md) | 自定义手势识别器判定回调类型。 |
| [HoverCallback](arkts-arkui-hovercallback-t.md) | hover事件的回调类型。 |
| [ImageModifier](arkts-arkui-imagemodifier-t.md) | ImageModifier |
| [InputEventListener](arkts-arkui-inputeventlistener-t.md) | 输入事件监听器回调函数类型。 |
| [IntentionCode](arkts-arkui-intentioncode-t.md) | 按键对应的意图。 |
| [Matrix4Transit](arkts-arkui-matrix4transit-t.md) | 为普通方法导入Matrix4Transit类型对象。 |
| [NavDestinationInfo](arkts-arkui-navdestinationinfo-t.md) | NavDestinationInfo实例对象。 |
| [NavigationInfo](arkts-arkui-navigationinfo-t.md) | NavigationInfo实例对象。 |
| [OnDidStopDraggingCallback](arkts-arkui-ondidstopdraggingcallback-t.md) | 滚动组件在结束拖拽时触发的回调。 |
| [OnDragEventCallback](arkts-arkui-ondrageventcallback-t.md) | 拖拽事件的回调函数。 |
| [OnGetPreviewBadgeCallback](arkts-arkui-ongetpreviewbadgecallback-t.md) | 即将启动多选长按聚拢动画时，触发用于获取选中数量的回调。 返回true表示显示选中数量角标，对应Grid或List显示范围内选中item数量；false表示不显示角标。 返回数字时默认显示角标，该数字表示角标中需要显示的数量。取值范围：[0, 2&lt;sup&gt;31&lt;/sup&gt;-1]，超过取值范围时按返回true处理。 返回浮点数时，向下取整。 |
| [OnItemDragStartCallback](arkts-arkui-onitemdragstartcallback-t.md) | 开始拖拽列表或网格元素时触发的回调。 |
| [OnMoveHandler](arkts-arkui-onmovehandler-t.md) | 定义数据源拖拽回调。 |
| [OnNeedSoftkeyboardCallback](arkts-arkui-onneedsoftkeyboardcallback-t.md) | 当绑定该方法的组件判断是否需要键盘时，将触发此回调。前提条件：组件需可获焦，否则本接口不生效。 |
| [OnScrollCallback](arkts-arkui-onscrollcallback-t.md) | 滚动组件滑动时触发的回调。 |
| [OnVisibleIndexesChangeCallback](arkts-arkui-onvisibleindexeschangecallback-t.md) | 懒加载布局容器[LazyColumnLayout](../../../reference/apis-arkui/arkui-ts/ts-container-lazycolumnlayout.md)、 LazyVGridLayout、 [LazyVWaterFlowLayout](../../../reference/apis-arkui/arkui-ts/ts-container-lazyvwaterflowlayout.md)所显示的子组件索引发生变化时的回调 类型。 |
| [OnWillScrollCallback](arkts-arkui-onwillscrollcallback-t.md) | Called before scroll to allow developer to control real offset the Scrollable can scroll. |
| [OnWillStopDraggingCallback](arkts-arkui-onwillstopdraggingcallback-t.md) | 滚动组件划动离手时触发的回调。 |
| [Optional](arkts-arkui-optional-t.md) | 定义可选类型，其值可以是undefined。 |
| [PathShape](arkts-arkui-pathshape-t.md) | 导入PathShape类型对象。 |
| [PixelMap](arkts-arkui-pixelmap-t.md) | Defines the PixelMap type object for ui component. |
| [PointerStyle](arkts-arkui-pointerstyle-t.md) | 光标样式。 |
| [PopupStateChangeCallback](arkts-arkui-popupstatechangecallback-t.md) | 气泡状态变化事件回调。 |
| [PromptActionDialogController](arkts-arkui-promptactiondialogcontroller-t.md) | 从promptAction导入弹出框控制器类型 |
| [RectShape](arkts-arkui-rectshape-t.md) | 导入RectShape类型对象。 |
| [ReuseIdCallback](arkts-arkui-reuseidcallback-t.md) | 获取复用标识ID的回调方法。 |
| [ReusePoolOwnership](arkts-arkui-reusepoolownership-t.md) | 全局复用池的持有类型。 |
| [RouterPageInfo](arkts-arkui-routerpageinfo-t.md) | RouterPageInfo实例对象。 |
| [ShouldBuiltInRecognizerParallelWithCallback](arkts-arkui-shouldbuiltinrecognizerparallelwithcallback-t.md) | 系统内置手势与响应链上其他组件的手势设置并行关系的回调事件类型。 |
| [ShouldRecognizerParallelWithCallback](arkts-arkui-shouldrecognizerparallelwithcallback-t.md) | 手势与响应链上其他组件的手势设置并行关系的回调事件类型。 |
| [SizeChangeCallback](arkts-arkui-sizechangecallback-t.md) | 组件区域变化时的回调类型。 oldValue表示目标元素变化之前的宽高。 newValue表示目标元素变化之后的宽高。 |
| [SpringLoadingContext](arkts-arkui-springloadingcontext-t.md) | 定义回调上下文信息的类，用于在悬停检测回调中传递给应用程序，使其能访问拖拽状态。 |
| [Summary](arkts-arkui-summary-t.md) | 拖拽相关数据的简介。 |
| [SymbolGlyphModifier](arkts-arkui-symbolglyphmodifier-t.md) | SymbolGlyphModifier类型，用于设置自定义图标小符号。 |
| [SystemUiMaterial](arkts-arkui-systemuimaterial-t.md) | 系统材质对象基类。 |
| [Theme](arkts-arkui-theme-t.md) | 主题对象。 |
| [TipsMessageType](arkts-arkui-tipsmessagetype-t.md) | 悬浮气泡弹窗信息。 |
| [TouchTestDoneCallback](arkts-arkui-touchtestdonecallback-t.md) | 动态指定手势识别器是否参与手势处理的回调事件类型，回调内参数的生命周期跟随回调本身，参数内的方法仅支持在回调内同步使用。 |
| [TransitionEffects](arkts-arkui-transitioneffects-t.md) | 定义所有转场效果。 |
| [TransitionFinishCallback](arkts-arkui-transitionfinishcallback-t.md) | 组件转场动画的结束回调类型。 |
| [UIContext](arkts-arkui-uicontext-t.md) | UIContext |
| [UnifiedData](arkts-arkui-unifieddata-t.md) | 拖拽相关的数据。 |
| [UniformDataType](arkts-arkui-uniformdatatype-t.md) | 标准化数据类型。 |
| [VisibleAreaChangeCallback](arkts-arkui-visibleareachangecallback-t.md) | 组件可见区域变化事件的回调类型。 |
| [VisualEffect](arkts-arkui-visualeffect-t.md) | 导入VisualEffect类型对象。 |
| [window](arkts-arkui-window-t.md) |  |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccessibilityAction](arkts-arkui-accessibilityaction-e.md) | 辅助功能操作类型的枚举 |
| [AccessibilityActionInterceptResult](arkts-arkui-accessibilityactioninterceptresult-e.md) | intercept action的枚举 |
| [AccessibilityRoleType](arkts-arkui-accessibilityroletype-e.md) | 定义组件的屏幕朗读功能角色类型。 |
| [AccessibilitySamePageMode](arkts-arkui-accessibilitysamepagemode-e.md) | 当前跨进程嵌入式显示的组件和宿主应用的同page模式。 |
| [AdaptiveColor](arkts-arkui-adaptivecolor-e.md) | 取色模式。 |
| [AnchoredColorMode](arkts-arkui-anchoredcolormode-e.md) | 配置组件主题跟随的颜色模式。 |
| [AvailableLayoutArea](arkts-arkui-availablelayoutarea-e.md) | 预览图宽高设置为百分比时的参考可布局区域大小。 |
| [BlendApplyType](arkts-arkui-blendapplytype-e.md) | 指示如何将指定的混合模式应用于视图的内容。 |
| [BlendMode](arkts-arkui-blendmode-e.md) | 混合模式。 |
| [BlurStyle](arkts-arkui-blurstyle-e.md) | 模糊样式类型。 |
| [BlurStyleActivePolicy](arkts-arkui-blurstyleactivepolicy-e.md) | 定义背景模糊激活策略。 |
| [ChainStyle](arkts-arkui-chainstyle-e.md) | 定义链的风格，支持attributeModifier动态设置属性方法。 |
| [ContentClipMode](arkts-arkui-contentclipmode-e.md) | 表示滚动容器的内容裁剪模式。 |
| [DismissReason](arkts-arkui-dismissreason-e.md) | 关闭原因类型。 |
| [DistortionMode](arkts-arkui-distortionmode-e-sys.md) | 非线性形变动画模式的枚举。 |
| [DragAnimationType](arkts-arkui-draganimationtype-e-sys.md) | 拖拽动画类型。 |
| [DragBehavior](arkts-arkui-dragbehavior-e.md) | 当设置[DragResult](arkts-arkui-dragresult-e.md)为DROP_ENABLED后，可设置DragBehavior为复制（COPY）或剪切（MOVE）。当DragBehavior为复制（COPY）时，拖拽对象的角标会显示加 号；为剪切（MOVE）时，拖拽对象的角标不会显示加号。DragBehavior用来向开发者描述数据的处理方式是复制（COPY）还是剪切（MOVE），但无法最终决定对数据的实际处理方式。DragBehavior会通过onDragEnd带 回给数据拖出方，发起拖拽的一方可通过DragBehavior来区分做出的是复制（COPY）还是剪切（MOVE）数据的不同行为。 |
| [DraggingSizeChangeEffect](arkts-arkui-draggingsizechangeeffect-e.md) | 当一个节点上同时设置长按浮起预览（参考bindContextMenu）与拖拽时，使用该字段设置长按浮起预览图与拖拽预览图过渡动效方式。 |
| [DragPreviewMode](arkts-arkui-dragpreviewmode-e.md) | 设置拖拽预览图的显示模式。 |
| [DragResult](arkts-arkui-dragresult-e.md) | 定义拖拽操作的结果及组件的落入选定状态。 |
| [EdgeLightMode](arkts-arkui-edgelightmode-e-sys.md) | 边缘光效动画模式枚举。 |
| [EffectEdge](arkts-arkui-effectedge-e.md) | 表示当前边缘效果要生效的边缘。 |
| [EffectType](arkts-arkui-effecttype-e.md) | 使用效果模板种类的枚举值。 **效果模板：** | 设备类型 | 模糊半径(单位: px) | 饱和度 | 亮度 | 颜色 | | -------- | ---- | ---------------------- | -------- | -------- | | 移动设备 | 0 | 0 | 0 | '#ffffffff'，显示为白色。 | | 2in1设备：深色模式 | 80 | 1.5 | 1.0 | '#e52e3033'，显示为淡红色的半透明效果。 | | 2in1设备：浅色模式 | 80 | 1.9 | 1.0 | '#e5ffffff'，显示为半透明的深红色。 | | Tablet设备 | 0 | 0 | 0 | '#ffffffff'，显示为白色。 | |
| [FinishCallbackType](arkts-arkui-finishcallbacktype-e.md) | 动画中定义onFinish回调的类型。 |
| [HapticFeedbackMode](arkts-arkui-hapticfeedbackmode-e.md) | 菜单弹出时振动效果。 |
| [HoverModeAreaType](arkts-arkui-hovermodeareatype-e.md) | 悬停态显示区域类型。 |
| [KeyboardAvoidMode](arkts-arkui-keyboardavoidmode-e.md) | 气泡避让键盘时，避让模式的枚举类型。 |
| [LayoutSafeAreaEdge](arkts-arkui-layoutsafeareaedge-e.md) | 扩展安全区域的边缘。 |
| [LayoutSafeAreaType](arkts-arkui-layoutsafeareatype-e.md) | 扩展布局安全区域的枚举类型。 |
| [MenuGridPosition](arkts-arkui-menugridposition-e.md) | 栅格菜单在菜单中的位置枚举值。 |
| [MenuKeyboardAvoidMode](arkts-arkui-menukeyboardavoidmode-e.md) | 菜单避让软键盘的模式。 |
| [MenuPolicy](arkts-arkui-menupolicy-e.md) | Define the menu pop-up policy |
| [MenuPreviewMode](arkts-arkui-menupreviewmode-e.md) | 菜单的预览样式。 |
| [ModalMode](arkts-arkui-modalmode-e.md) | 子窗菜单的模态模式。 |
| [ModalTransition](arkts-arkui-modaltransition-e.md) | 全屏模态转场方式枚举类型，用于设置全屏模态转场类型。 |
| [OutlineStyle](arkts-arkui-outlinestyle-e.md) | 外描边样式。 |
| [PreDragStatus](arkts-arkui-predragstatus-e.md) | 定义拖拽手势触发前的各阶段状态。 |
| [PreviewScaleMode](arkts-arkui-previewscalemode-e.md) | 预览图的缩放方式。 |
| [RepeatMode](arkts-arkui-repeatmode-e.md) | 用于设置被切割的图片在边框上的重复方式。 |
| [ReusableMemOptStrategy](arkts-arkui-reusablememoptstrategy-e.md) | 可复用自定义组件内存优化策略枚举。 |
| [SafeAreaEdge](arkts-arkui-safeareaedge-e.md) | 扩展安全区域的边缘。 |
| [SafeAreaType](arkts-arkui-safeareatype-e.md) | 扩展安全区域的枚举类型。 |
| [ScrollSizeMode](arkts-arkui-scrollsizemode-e.md) | 半模态面板上下滑动时的内容更新方式。 |
| [ShadowStyle](arkts-arkui-shadowstyle-e.md) | 组件阴影效果。 |
| [ShadowType](arkts-arkui-shadowtype-e.md) | 阴影类型。 |
| [SheetKeyboardAvoidMode](arkts-arkui-sheetkeyboardavoidmode-e.md) | 半模态激活输入法时对软键盘的避让方式。 |
| [SheetMode](arkts-arkui-sheetmode-e.md) | 半模态的显示层级模式。 |
| [SheetSize](arkts-arkui-sheetsize-e.md) | 指定半模态的高度。 |
| [SheetType](arkts-arkui-sheettype-e.md) | 半模态弹窗的样式。 |
| [SourceTool](arkts-arkui-sourcetool-e.md) | 定义输入源对应的工具类型。 |
| [SourceType](arkts-arkui-sourcetype-e.md) | 定义输入源对应的设备类型。 |
| [SystemProperties](arkts-arkui-systemproperties-e.md) | 定义系统环境变量枚举值 |
| [ThemeColorMode](arkts-arkui-themecolormode-e.md) | 设置颜色模式。 |
| [TouchTestStrategy](arkts-arkui-touchteststrategy-e.md) | 事件派发策略。 |
| [TransitionEdge](arkts-arkui-transitionedge-e.md) | 转场边缘类型。 |
| [TransitionHierarchyStrategy](arkts-arkui-transitionhierarchystrategy-e-sys.md) | 共享元素动画过程中in/out组件层级位置移动策略枚举。 | 名称 | 值 | 说明 | | ------ | - | ---- | | NONE | 0 | 无层级提拉，in/out组件保持原来的层级位置，受父组件scale、position影响。 | | ADAPTIVE | 1 | 有层级提拉，in/out组件中相对低层级的组件被提拉至组件树上in/out组件相对高层级的位置上。 此模式还会导致被提拉的组件与父组件解绑，不受父组件scale、position影响。 例如in组件层级高于out组件，开启层级提拉后会在动画过程中将out组件从自己的父组件处解耦，并提拉至in组件的层级位置处，in组件层级位置不变。| |

