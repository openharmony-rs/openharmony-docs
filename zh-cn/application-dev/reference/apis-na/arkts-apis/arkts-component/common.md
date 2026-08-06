# component/common

Defines the namespace of focus controller.

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [cursorControl](arkts-na-cursorcontrol-n.md) | CursorControl |
| [focusControl](arkts-na-focuscontrol-n.md) | Defines the namespace of focus controller. |

### 函数

| 名称 | 说明 |
| --- | --- |
| [$$](common-$$-f.md#$$) | Convert to a bindable property. |
| [$r](common-$r-f.md#$r) | global \_\_\_ESCAPED\_DOLLAR\_\_\_r function |
| [$rawfile](common-$rawfile-f.md#$rawfile) | global \_\_\_ESCAPED\_DOLLAR\_\_\_rawfile function |
| [animateToImmediately](common-animatetoimmediately-f.md#animatetoimmediately) | Define animation functions for immediate distribution. This interface depends on the UI context and cannot be used when the UI context is unclear. It is recommended to use \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ to explicitly specify the UI context. |
| [applyStyles](common-applystyles-f.md#applystyles) | Apply style function on this CommonMethod. |
| [makeBindable](common-makebindable-f.md#makebindable) | Create a bindable property instance. |

### 类

| 名称 | 说明 |
| --- | --- |
| [ChildrenMainSize](common-childrenmainsize-c.md) | Indicates children main size. |
| [ContentTransitionEffect](common-contenttransitioneffect-c.md) | Defines the content transition effect. |
| [DrawModifier](common-drawmodifier-c.md) | Defined the draw modifier of node. Provides draw callbacks for the associated Node. Each DrawModifier instance can be set for only one component. Repeated setting is not allowed. |
| [LayoutPolicy](common-layoutpolicy-c.md) | Defines the policy of Layout |
| [ProgressMask](common-progressmask-c.md) | Implements a ProgressMask object to set the progress, maximum value, and color of the mask. |
| [RawInputEventWrapper](common-rawinputeventwrapper-c.md) | Defines the raw input event wrapper. |
| [ScrollResult](common-scrollresult-c.md) | The actual offset by which the scrollable scrolls. |
| [TextContentControllerBase](common-textcontentcontrollerbase-c.md) | TextContentControllerBase |
| [TouchResult](common-touchresult-c.md) | Defines TouchResult class. |
| [TouchTestInfo](common-touchtestinfo-c.md) | Defines TouchTestInfo class. |
| [TransitionEffect](common-transitioneffect-c.md) | 定义TransitionEffect类指定转场效果。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TextContentControllerBase](common-textcontentcontrollerbase-c-sys.md) | TextContentControllerBase |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilityHoverEvent](common-accessibilityhoverevent-i.md) | The accessibility hover action triggers this method invocation. |
| [AlignRuleOption](common-alignruleoption-i.md) | Defines the align rule options of relative container. |
| [AnimatableArithmetic](common-animatablearithmetic-i.md) | 该接口定义非number数据类型的动画运算规则。对非number类型的数据（如数组、结构体、颜色等）做动画，需要实现AnimatableArithmetic\&lt;T\&gt;接口中加法、减法、乘法和判断相等函数，使得该数据能参与动画的插值运算 和识别该数据是否发生改变。即定义它们为实现了AnimatableArithmetic\&lt;T\&gt;接口的类型。 |
| [AnimateParam](common-animateparam-i.md) | 动画效果相关参数。 |
| [AreaChangeOptions](common-areachangeoptions-i.md) | Defines the options about AreaChangeEvent. |
| [AsymmetricTransitionOption](common-asymmetrictransitionoption-i.md) | Defines the option of asymmetric transition. |
| [AttributeModifier](common-attributemodifier-i.md) | Defines the attribute modifier. |
| [AxisEvent](common-axisevent-i.md) | The axis event triggers this method invocation. |
| [BackgroundBlurStyleOptions](common-backgroundblurstyleoptions-i.md) | 继承自[BlurStyleOptions]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [BackgroundBrightnessOptions](common-backgroundbrightnessoptions-i.md) | 背景亮度选项。 |
| [BackgroundEffectOptions](common-backgroundeffectoptions-i.md) | 背景效果参数。 |
| [BackgroundImageOptions](common-backgroundimageoptions-i.md) | Define the options for background image. |
| [BackgroundOptions](common-backgroundoptions-i.md) | Defines background options. |
| [BaseEvent](common-baseevent-i.md) | Defines the base event. |
| [BindOptions](common-bindoptions-i.md) | 半模态、全模态的公共配置接口。 |
| [Bindable](common-bindable-i.md) | Defines a bindable property |
| [BlurOptions](common-bluroptions-i.md) | Defines the options of blur |
| [BlurStyleOptions](common-blurstyleoptions-i.md) | Defines the options of blurStyle |
| [BorderImageOption](common-borderimageoption-i.md) | Border image option |
| [CaretOffset](common-caretoffset-i.md) | CaretOffset info. |
| [ClickEffect](common-clickeffect-i.md) | 定义点击效果。 |
| [ClickEvent](common-clickevent-i.md) | The tap action triggers this method invocation. |
| [CommonConfiguration](common-commonconfiguration-i.md) | Defines the common configuration. |
| [CommonMethod](common-commonmethod-i.md) | CommonMethod |
| [Configuration](common-configuration-i.md) | Defines the data type of the interface restriction. |
| [ContentCoverOptions](common-contentcoveroptions-i.md) | 继承自[BindOptions]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 全屏模态页面内容选项。 |
| [ContentModifier](common-contentmodifier-i.md) | Defines the content modifier. |
| [ContextMenuAnimationOptions](common-contextmenuanimationoptions-i.md) | Defines the ContextMenu's preview animator options. |
| [ContextMenuOptions](common-contextmenuoptions-i.md) | Defines the context menu options. |
| [CrownEvent](common-crownevent-i.md) | CrownEvent object description |
| [CustomPopupOptions](common-custompopupoptions-i.md) | Defines the custom popup options. |
| [DateRange](common-daterange-i.md) | Defines a range of dates. |
| [DismissContentCoverAction](common-dismisscontentcoveraction-i.md) | Component content cover dismiss |
| [DismissPopupAction](common-dismisspopupaction-i.md) | Component popup dismiss |
| [DismissSheetAction](common-dismisssheetaction-i.md) | 控制半模态的关闭。 |
| [DividerStyle](common-dividerstyle-i.md) | Provides an interface for the style of an divider including stroke width, color, start margin and end margin |
| [DragEvent](common-dragevent-i.md) | DragEvent object description |
| [DragInteractionOptions](common-draginteractionoptions-i.md) | Defines the drag options. |
| [DragItemInfo](common-dragiteminfo-i.md) | DragItemInfo object description |
| [DragPreviewOptions](common-dragpreviewoptions-i.md) | Defines the preview options. |
| [DropOptions](common-dropoptions-i.md) | Defines the options for the drop handling. |
| [DynamicNode](common-dynamicnode-i.md) | Define DynamicNode. |
| [EdgeEffectOptions](common-edgeeffectoptions-i.md) | Define EdgeEffect Options. |
| [EditModeOptions](common-editmodeoptions-i.md) | Define edit mode options. |
| [EventTarget](common-eventtarget-i.md) | Defines the event target. |
| [ExpectedFrameRateRange](common-expectedframeraterange-i.md) | 设置动画期望的帧率。 |
| [FadingEdgeOptions](common-fadingedgeoptions-i.md) | Defines the fadingEdge options. |
| [FocusAxisEvent](common-focusaxisevent-i.md) | Focus axis event object description. |
| [FocusMovement](common-focusmovement-i.md) | Defines the next focus item. |
| [ForegroundBlurStyleOptions](common-foregroundblurstyleoptions-i.md) | Defines the options of ForegroundBlurStyle |
| [ForegroundEffectOptions](common-foregroundeffectoptions-i.md) | Defines the options of ForegroundEffect |
| [GeometryInfo](common-geometryinfo-i.md) | Sub component layout info. |
| [GeometryTransitionOptions](common-geometrytransitionoptions-i.md) | Defines the options of geometry transition. |
| [GestureModifier](common-gesturemodifier-i.md) | Defines the gesture modifier. |
| [HistoricalPoint](common-historicalpoint-i.md) | TouchObject getHistoricalPoints Function Parameters |
| [HorizontalAlignParam](common-horizontalalignparam-i.md) | Defines the horizontal align rule options of relative container. |
| [HoverEvent](common-hoverevent-i.md) | The hover action triggers this method invocation. |
| [InputCounterOptions](common-inputcounteroptions-i.md) | Define the ratio of characters entered by the the percentage of InputCounterOptions. |
| [InputEventInterceptResult](common-inputeventinterceptresult-i.md) | Defines the input event intercept result. |
| [InputEventMonitor](common-inputeventmonitor-i.md) | Defines the input event monitor identifier. Important Notes: - This object is created and returned by the system as a unique identifier for the listener. - The object is an empty object with no accessible members. - Developers cannot actively construct this object, it can only be obtained through the registration interface. - Used for subsequent unregistration to verify identity. |
| [InvertOptions](common-invertoptions-i.md) | Define the options of invert |
| [ItemDragEventHandler](common-itemdrageventhandler-i.md) | Define item drag event handler. |
| [ItemDragInfo](common-itemdraginfo-i.md) | ItemDragInfo object description |
| [KeyEvent](common-keyevent-i.md) | KeyEvent object description: |
| [KeyframeAnimateParam](common-keyframeanimateparam-i.md) | 动画选项设置。 |
| [KeyframeState](common-keyframestate-i.md) | 设置关键帧选项。 |
| [Layoutable](common-layoutable-i.md) | Provides the child component layout information. |
| [LinearGradientBlurOptions](common-lineargradientbluroptions-i.md) | Linear Gradient Blur Interface |
| [LinearGradientOptions](common-lineargradientoptions-i.md) | Defines the options of linear gradient. |
| [LocalizedAlignRuleOptions](common-localizedalignruleoptions-i.md) | Defines the Localized align rule options of relative container. |
| [LocalizedHorizontalAlignParam](common-localizedhorizontalalignparam-i.md) | Defines the localized horizontal align param of relative container. |
| [LocalizedVerticalAlignParam](common-localizedverticalalignparam-i.md) | Defines the localized vertical align param of relative container. |
| [Measurable](common-measurable-i.md) | Sub component info passed from framework when measure happens. |
| [MeasureResult](common-measureresult-i.md) | Provides the measurement result of the component. |
| [MenuElement](common-menuelement-i.md) | Defines the menu element. |
| [MenuGridStyleOptions](common-menugridstyleoptions-i.md) | Defines grid style of menu. |
| [MenuMaskType](common-menumasktype-i.md) | Menu mask type |
| [MenuOptions](common-menuoptions-i.md) | Defines the menu options. |
| [MotionBlurAnchor](common-motionbluranchor-i.md) | Define motion blur anchor coordinates. |
| [MotionBlurOptions](common-motionbluroptions-i.md) | Define motion blur options. |
| [MotionPathOptions](common-motionpathoptions-i.md) | 设置组件的运动路径。 |
| [MouseEvent](common-mouseevent-i.md) | The mouse click action triggers this method invocation. |
| [MouseHistoricalPoint](common-mousehistoricalpoint-i.md) | Defines the historical point information for mouse event. |
| [MultiShadowOptions](common-multishadowoptions-i.md) | Defines the options of Shadow. |
| [NestedScrollOptions](common-nestedscrolloptions-i.md) | Define nested scroll options |
| [OverlayOffset](common-overlayoffset-i.md) | Defines the OverlayOffset. |
| [OverlayOptions](common-overlayoptions-i.md) | Defines the OverlayOptions interface. \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_NOTE\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ When both align and offset are set, the effects are combined. The overlay is first aligned relative to the component and then offset from its current upper left corner. |
| [PickerDialogButtonStyle](common-pickerdialogbuttonstyle-i.md) | Provide an interface for the button style of picker |
| [PickerTextStyle](common-pickertextstyle-i.md) | Provide an interface for the text style of picker |
| [PixelRoundPolicy](common-pixelroundpolicy-i.md) | Defines the direction of pixel rounding at the component level. |
| [PixelStretchEffectOptions](common-pixelstretcheffectoptions-i.md) | Set the edge blur effect distance of the corresponding defense line of the component When the component expand out, no re-layout is triggered |
| [PopupBorderLinearGradient](common-popupborderlineargradient-i.md) | Popup border LinearGradient |
| [PopupButton](common-popupbutton-i.md) | Defines the popup button. |
| [PopupCommonOptions](common-popupcommonoptions-i.md) | Popup common options |
| [PopupMaskType](common-popupmasktype-i.md) | Popup mask type |
| [PopupMessageOptions](common-popupmessageoptions-i.md) | Defines the options of popup message. |
| [PopupOptions](common-popupoptions-i.md) | Defines the popup options. |
| [PopupStateChangeParam](common-popupstatechangeparam-i.md) | Popup state change param |
| [PreviewConfiguration](common-previewconfiguration-i.md) | Defines the drag preview configuration. |
| [RadialGradientOptions](common-radialgradientoptions-i.md) | Defines the options of radial gradient. |
| [RectResult](common-rectresult-i.md) | Describe the position, width, and height of a component. |
| [Rectangle](common-rectangle-i.md) | The data type used to describe a rectangular area. |
| [ResponseRegion](common-responseregion-i.md) | Defines the response region interface. |
| [ReuseOptions](common-reuseoptions-i.md) | Defining the reusable configuration parameters. |
| [RotateAngleOptions](common-rotateangleoptions-i.md) | 指定各轴旋转角的旋转参数选项。 |
| [RotateOptions](common-rotateoptions-i.md) | 组件旋转参数。 |
| [ScaleOptions](common-scaleoptions-i.md) |  |
| [SelectionOptions](common-selectionoptions-i.md) | Defines the selection options. |
| [ShadowOptions](common-shadowoptions-i.md) | Define the options of shadow |
| [SheetDismiss](common-sheetdismiss-i.md) | 控制半模态的关闭。 |
| [SheetOptions](common-sheetoptions-i.md) | 继承自[BindOptions]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 半模态页面内容选项。 |
| [SheetTitleOptions](common-sheettitleoptions-i.md) | 半模态面板的标题。 |
| [SizeResult](common-sizeresult-i.md) | Provides the component size information. |
| [SmartGestureShortcutOptions](common-smartgestureshortcutoptions-i.md) | Options for configuring smart gesture shortcuts. |
| [SpringBackAction](common-springbackaction-i.md) | 控制半模态关闭前的回弹。 |
| [StateStyles](common-statestyles-i.md) | Component State Styles. |
| [SweepGradientOptions](common-sweepgradientoptions-i.md) | Defines the options of sweep gradient. |
| [SystemAdaptiveOptions](common-systemadaptiveoptions-i.md) | 系统自适应调节参数，系统会默认开启根据芯片算力进行自适应效果调节的能力。 |
| [TerminationInfo](common-terminationinfo-i.md) | Indicates the information when the provider of the embedded UI is terminated. |
| [TextContentControllerOptions](common-textcontentcontrolleroptions-i.md) | Defines the span options of TextContentController. |
| [TextDecorationOptions](common-textdecorationoptions-i.md) | Defines the options of decoration. |
| [TipsOptions](common-tipsoptions-i.md) | Defines the Tips options. |
| [TouchEvent](common-touchevent-i.md) | Touch Action Function Parameters |
| [TouchObject](common-touchobject-i.md) | Type of the touch event. |
| [TranslateOptions](common-translateoptions-i.md) | Defines the options of translate. |
| [UICommonEvent](common-uicommonevent-i.md) | Defines a UICommonEvent which is used to set different common event to target component. |
| [UIGestureEvent](common-uigestureevent-i.md) | Defines a UIGestureEvent which is used to set different gestures to target component. |
| [UIScrollableCommonEvent](common-uiscrollablecommonevent-i.md) | Defines a UIScrollableCommonEvent which is used to set event to target component. |
| [VerticalAlignParam](common-verticalalignparam-i.md) | Defines the align rule options of relative container. |
| [VisibleAreaEventOptions](common-visibleareaeventoptions-i.md) | Defines the options about VisibleAreaEvent. |
| [sharedTransitionOptions](common-sharedtransitionoptions-i.md) | 共享元素转场动画参数。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CommonMethod](common-commonmethod-i-sys.md) | CommonMethod |
| [ContextMenuOptions](common-contextmenuoptions-i-sys.md) | Defines the context menu options. |
| [DepthColorRGB](common-depthcolorrgb-i-sys.md) | RGB color in depth space. |
| [DepthVector3](common-depthvector3-i-sys.md) | 3D vector in depth space. |
| [DepthVector4](common-depthvector4-i-sys.md) | 4D vector in depth space. |
| [DragEvent](common-dragevent-i-sys.md) | DragEvent object description |
| [EdgeLightParams](common-edgelightparams-i-sys.md) | Defines the parameters of the edge light effect. |
| [GeometryTransitionOptions](common-geometrytransitionoptions-i-sys.md) | Defines the options of geometry transition. |
| [GravityCenterOptions](common-gravitycenteroptions-i-sys.md) | Defines the parameters of the center of gravity. |
| [LightSource](common-lightsource-i-sys.md) | 一个组件支持添加1个光源。 |
| [PixelMapMock](common-pixelmapmock-i-sys.md) | pixelmap object with release function. |
| [PointLightStyle](common-pointlightstyle-i-sys.md) | 通过设置光源和被照亮的类型实现点光源照亮周围组件的UI效果。 |
| [SheetOptions](common-sheetoptions-i-sys.md) | 继承自[BindOptions]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 半模态页面内容选项。 |
| [SpatialEffectParams](common-spatialeffectparams-i-sys.md) | Spatial effect params. |
| [SpatialPosition](common-spatialposition-i-sys.md) | Spatial corner positions in 3D space. |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccessibilityAction](common-accessibilityaction-e.md) | Enum for accessibility action type |
| [AccessibilityActionInterceptResult](common-accessibilityactioninterceptresult-e.md) | Enum for the result of accessibility action intercept function |
| [AccessibilityRoleType](common-accessibilityroletype-e.md) | Enum for accessibility component type |
| [AccessibilitySamePageMode](common-accessibilitysamepagemode-e.md) | Defines the same page mode |
| [AdaptiveColor](common-adaptivecolor-e.md) | Defines adaptive color |
| [AnchoredColorMode](common-anchoredcolormode-e.md) | enum color mode of pointing popup |
| [AvailableLayoutArea](common-availablelayoutarea-e.md) | Defines the available layout area. |
| [BlendApplyType](common-blendapplytype-e.md) | Enum for BlendApplyType. Indicate how to apply specified blend mode to the view's content. |
| [BlendMode](common-blendmode-e.md) | Enum for BlendMode. Blend modes for compositing current component with overlapping content. Use overlapping content as dst, current component as src. |
| [BlurStyle](common-blurstyle-e.md) | 模糊样式类型。 |
| [BlurStyleActivePolicy](common-blurstyleactivepolicy-e.md) | 定义背景模糊激活策略。 |
| [ChainStyle](common-chainstyle-e.md) | Enumerates the chain styles in relative container. |
| [ContentClipMode](common-contentclipmode-e.md) | Enum of scrollable containers' content clip mode. |
| [DismissReason](common-dismissreason-e.md) | 关闭原因类型。 |
| [DragBehavior](common-dragbehavior-e.md) | Enum for Drag Behavior. \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_NOTE\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ DragBehavior serves to inform you about the intended method of data handling, whether it's a copy or a move, but it does not actually dictate the real processing of the data. |
| [DragPreviewMode](common-dragpreviewmode-e.md) | Defines the drag preview mode. |
| [DragResult](common-dragresult-e.md) | Enum for Drag Result. |
| [DraggingSizeChangeEffect](common-draggingsizechangeeffect-e.md) | Define drag start animation effect from drag preview to the handle drag image |
| [EffectEdge](common-effectedge-e.md) | Enumerates the effective edge of the edge effect. |
| [EffectType](common-effecttype-e.md) | Enum of using the effects template mode. |
| [FinishCallbackType](common-finishcallbacktype-e.md) | 动画中定义onFinish回调的类型。 |
| [HapticFeedbackMode](common-hapticfeedbackmode-e.md) | Defines the menu haptic feedback mode. |
| [HoverModeAreaType](common-hovermodeareatype-e.md) | 悬停态显示区域类型。 |
| [KeyboardAvoidMode](common-keyboardavoidmode-e.md) | enum keyboard avoid mode |
| [LayoutSafeAreaEdge](common-layoutsafeareaedge-e.md) | Define the edges for expanding the safe area in layout. |
| [LayoutSafeAreaType](common-layoutsafeareatype-e.md) | Describe the types for expanding the safe area in layout. |
| [MenuGridPosition](common-menugridposition-e.md) | Defines menu grid position. |
| [MenuKeyboardAvoidMode](common-menukeyboardavoidmode-e.md) | Define the mode of menu how to avoid keyboard. |
| [MenuPolicy](common-menupolicy-e.md) | Define the menu pop-up policy |
| [MenuPreviewMode](common-menupreviewmode-e.md) | Defines the menu preview mode. |
| [ModalMode](common-modalmode-e.md) | Define the modal mode of menu. |
| [ModalTransition](common-modaltransition-e.md) | 全屏模态转场方式枚举类型，用于设置全屏模态转场类型。 |
| [OutlineStyle](common-outlinestyle-e.md) | Outline Style |
| [PreDragStatus](common-predragstatus-e.md) | Defines the drag status before drag action. |
| [PreviewScaleMode](common-previewscalemode-e.md) | Defines the scaling mode for custom preview of contextMenu. |
| [RepeatMode](common-repeatmode-e.md) | Defines the Border Image Repeat Mode. |
| [SafeAreaEdge](common-safeareaedge-e.md) | Enumerates the safe area edges. |
| [SafeAreaType](common-safeareatype-e.md) | The types of expanded safe areas. |
| [ScrollSizeMode](common-scrollsizemode-e.md) | 半模态面板上下滑动时的内容更新方式。 |
| [ShadowStyle](common-shadowstyle-e.md) | enum Shadow style |
| [ShadowType](common-shadowtype-e.md) | Define the type of shadow |
| [SheetKeyboardAvoidMode](common-sheetkeyboardavoidmode-e.md) | 半模态激活输入法时对软键盘的避让方式。 |
| [SheetMode](common-sheetmode-e.md) | 半模态的显示层级模式。 |
| [SheetSize](common-sheetsize-e.md) | 指定半模态的高度。 |
| [SheetType](common-sheettype-e.md) | 半模态弹窗的样式。 |
| [SourceTool](common-sourcetool-e.md) | Defines the event tool type. |
| [SourceType](common-sourcetype-e.md) | Defines the event source type. |
| [ThemeColorMode](common-themecolormode-e.md) | enum color mode |
| [TouchTestStrategy](common-touchteststrategy-e.md) | Defines the touch test strategy object. |
| [TransitionEdge](common-transitionedge-e.md) | 转场边缘类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BlendApplyType](common-blendapplytype-e-sys.md) | Enum for BlendApplyType. Indicate how to apply specified blend mode to the view's content. |
| [DistortionMode](common-distortionmode-e-sys.md) | Enum for distortion animation mode. |
| [DragAnimationType](common-draganimationtype-e-sys.md) | Enum for Drag Animation Type. |
| [EdgeLightMode](common-edgelightmode-e-sys.md) | 边缘光效动画模式枚举。 |
| [TransitionHierarchyStrategy](common-transitionhierarchystrategy-e-sys.md) | 共享元素动画过程中in/out组件层级位置移动策略枚举。 \| 名称 \| 值 \| 说明 \| \| ------ \| - \| ---- \| \| NONE \| 0 \| 无层级提拉，in/out组件保持原来的层级位置，受父组件scale、position影响。 \| \| ADAPTIVE \| 1 \| 有层级提拉，in/out组件中相对低层级的组件被提拉至组件树上in/out组件相对高层级的位置上。 此模式还会导致被提拉的组件与父组件解绑，不受父组件scale、position影响。 例如in组件层级高于out组件，开启层级提拉后会在动画过程中将out组件从自己的父组件处解耦，并提拉至in组件的层级位置处，in组件层级位置不变。\| |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AccessibilityActionInterceptCallback](arkts-na-accessibilityactioninterceptcallback-t.md) | Defines the callback type used in accessibility action intercept. The value of action indicates the accessibility action type. |
| [AccessibilityCallback](arkts-na-accessibilitycallback-t.md) | Defines the callback type used in accessibility hover events. The value of isHover indicates whether the touch is hovering over the component. The value of event contains information about AccessibilityHoverEvent. |
| [AccessibilityFocusCallback](arkts-na-accessibilityfocuscallback-t.md) | Defines the callback type used in accessibility focus. The value of isFocus indicates whether the current component is focused |
| [AccessibilityTransparentCallback](arkts-na-accessibilitytransparentcallback-t.md) | Defines the callback type used in accessibility hover transparent event. |
| [AnimationNumberRange](arkts-na-animationnumberrange-t.md) | Defines the animator range of start and end property. |
| [AreaChangeCallback](arkts-na-areachangecallback-t.md) | Defines the options for the AreaChangeEvent. |
| [BindableResourceStr](arkts-na-bindableresourcestr-t.md) | Defines the Two-way binding type of ResourceStr. |
| [BindableResourceStrArray](arkts-na-bindableresourcestrarray-t.md) | Defines the Two-way binding type of ResourceStr[]. |
| [BorderRadiusType](arkts-na-borderradiustype-t.md) | Defines the type of border radius. |
| [Callback](arkts-na-callback-t.md) | Defines the callback |
| [CommonAttribute](arkts-na-commonattribute-t.md) | CommonAttribute for ide. |
| [Context](arkts-na-context-t.md) | Export Context. |
| [CustomProperty](arkts-na-customproperty-t.md) | Defines the value of the custom property.. |
| [CustomStyles](arkts-na-customstyles-t.md) | The custom styles function block. |
| [DataLoadParams](arkts-na-dataloadparams-t.md) | Import the DataLoadParams type object for ui component. |
| [DataSyncOptions](arkts-na-datasyncoptions-t.md) | Import the GetDataParams type object for ui component. |
| [DateTimeOptions](arkts-na-datetimeoptions-t.md) | Defines the format for displaying dates and times. |
| [DoubleLengthDetents](arkts-na-doublelengthdetents-t.md) | 定义了两个高度的挡位。 |
| [DragSpringLoadingConfiguration](arkts-na-dragspringloadingconfiguration-t.md) | The type for DragSpringLoadingConfiguration, see the detailed description in dragController. |
| [DrawContext](arkts-na-drawcontext-t.md) | DrawContext. |
| [Filter](arkts-na-filter-t.md) | 导入Filter类型对象。 |
| [FractionStop](arkts-na-fractionstop-t.md) | Defines the segment of blur. The first element in the tuple means fraction. The range of this value is [0,1]. A value of 1 means opaque and 0 means completely transparent. The second element means the stop position. The range of this value is [0,1]. A value of 1 means region ending position and 0 means region starting position. |
| [GestureCollectInterceptCallback](arkts-na-gesturecollectinterceptcallback-t.md) | Defines the callback type used in onGestureCollectIntercept. |
| [GestureRecognizerJudgeBeginCallback](arkts-na-gesturerecognizerjudgebegincallback-t.md) | Defines the callback type used in onGestureRecognizerJudgeBegin. |
| [HoverCallback](arkts-na-hovercallback-t.md) | Defines the callback type used in hover events. The value of isHover indicates whether the mouse is hovering over the component. The value of event contains information about HoverEvent. |
| [ICurve](arkts-na-icurve-t.md) | 曲线对象。 |
| [InputEventListener](arkts-na-inputeventlistener-t.md) | Defines the input event listener callback function type. Performance Warning: Do not perform time-consuming operations in the callback, otherwise it may cause the application to freeze. The listener executes synchronously in the UI thread and will directly block the event processing flow. It is recommended to only perform simple judgments and calculations, avoiding: - Synchronous I/O operations - Complex data processing - Network requests - Massive log output |
| [Matrix4Transit](arkts-na-matrix4transit-t.md) | 矩阵对象接口。 |
| [ModifierKeyStateGetter](arkts-na-modifierkeystategetter-t.md) | The modifier key state query function block. |
| [NavDestinationInfo](arkts-na-navdestinationinfo-t.md) | The navigation destination information. |
| [NavigationInfo](arkts-na-navigationinfo-t.md) | The navigation information. |
| [OnDidStopDraggingCallback](arkts-na-ondidstopdraggingcallback-t.md) | On scroll callback using in scrollable onDidStopDragging. |
| [OnDragEventCallback](arkts-na-ondrageventcallback-t.md) | The event callback function for drag and drop common interfaces. |
| [OnGetPreviewBadgeCallback](arkts-na-ongetpreviewbadgecallback-t.md) | Defines the callback type used in onGetPreviewBadge of EditModeOptions. |
| [OnItemDragStartCallback](arkts-na-onitemdragstartcallback-t.md) | Defines the callback type used in onItemDragStart. |
| [OnMoveHandler](arkts-na-onmovehandler-t.md) | Defines the onMove callback. |
| [OnNeedSoftkeyboardCallback](arkts-na-onneedsoftkeyboardcallback-t.md) | Defines the callback type used in onNeedSoftkeyboard. Called when component is focused, the return value indicates whether keyboard is needed. |
| [OnScrollCallback](arkts-na-onscrollcallback-t.md) | On scroll callback using in scrollable onDidScroll. |
| [OnVisibleIndexesChangeCallback](arkts-na-onvisibleindexeschangecallback-t.md) | Defines the callback type used in OnVisibleIndexesChange. |
| [OnWillScrollCallback](arkts-na-onwillscrollcallback-t.md) | Called before scroll to allow developer to control real offset the Scrollable can scroll. |
| [OnWillStopDraggingCallback](arkts-na-onwillstopdraggingcallback-t.md) | On scroll callback using in scrollable onWillStopDragging. |
| [Optional](arkts-na-optional-t.md) | Defines the type that can be undefined. |
| [PixelMap](arkts-na-pixelmap-t.md) | Defines the PixelMap type object for ui component. |
| [PointerStyle](arkts-na-pointerstyle-t.md) | Import the PointerStyle type object for setCursor. |
| [PopupStateChangeCallback](arkts-na-popupstatechangecallback-t.md) | Popup state change callback |
| [PromptActionDialogController](arkts-na-promptactiondialogcontroller-t.md) | Import the DialogController type from promptAction. |
| [ReuseIdCallback](arkts-na-reuseidcallback-t.md) | ReuseId callback type. It is used to compute reuseId. |
| [RouterPageInfo](arkts-na-routerpageinfo-t.md) | The router page information. |
| [ShouldBuiltInRecognizerParallelWithCallback](arkts-na-shouldbuiltinrecognizerparallelwithcallback-t.md) | Defines the callback type used in shouldBuiltInRecognizerParallelWith. |
| [ShouldRecognizerParallelWithCallback](arkts-na-shouldrecognizerparallelwithcallback-t.md) | Defines the callback type used in shouldRecognizerParallelWith. |
| [SingleLengthDetent](arkts-na-singlelengthdetent-t.md) | 定义了单个高度的挡位。 |
| [SizeChangeCallback](arkts-na-sizechangecallback-t.md) | Defines the callback type used in onSizeChange. |
| [SpringLoadingContext](arkts-na-springloadingcontext-t.md) | The type for SpringLoadingContext, see the detailed description in dragController. |
| [Summary](arkts-na-summary-t.md) | Import the Summary type object for ui component. |
| [SystemUiMaterial](arkts-na-systemuimaterial-t.md) | SystemUiMaterial |
| [TipsMessageType](arkts-na-tipsmessagetype-t.md) | Defines the TipsMessageType property with ResourceStr and StyledString. |
| [TouchTestDoneCallback](arkts-na-touchtestdonecallback-t.md) | Defines the callback type used in onTouchTestDone. When the user touch down, the system performs hit test process to collect all gesture recognizers based on the press location, when the collection is completed, and before gesture begin to be recognizing, the callback is triggered, you can get all recognizer's information from this callback. |
| [TransitionFinishCallback](arkts-na-transitionfinishcallback-t.md) | 组件转场动画的结束回调类型。 |
| [TripleLengthDetents](arkts-na-triplelengthdetents-t.md) | 定义了三个高度的挡位。 |
| [UIContext](arkts-na-uicontext-t.md) | UIContext. |
| [UnifiedData](arkts-na-unifieddata-t.md) | Import the UnifiedData type object for ui component. |
| [UniformDataType](arkts-na-uniformdatatype-t.md) | Import the UniformDataType type object for ui component. |
| [VisibleAreaChangeCallback](arkts-na-visibleareachangecallback-t.md) | Defines the callback type used in VisibleAreaChange events. |
| [VisualEffect](arkts-na-visualeffect-t.md) | 导入VisualEffect类型对象。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Blender](arkts-na-blender-t-sys.md) | Blender |
<!--DelEnd-->

