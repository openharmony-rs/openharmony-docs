# common

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
| [$$](arkts-na-common-$$-f.md#) | Convert to a bindable property. |
| [$r](arkts-na-common-$r-f.md) | global \\$r function |
| [$rawfile](arkts-na-common-$rawfile-f.md) | global \\$rawfile function |
| [animateToImmediately](arkts-na-common-animatetoimmediately-f.md) | Define animation functions for immediate distribution. This interface depends on the UI context and cannot be used when the UI context is unclear. It is recommended to use animateToImmediately to explicitly specify the UI context. |
| [applyStyles](arkts-na-common-applystyles-f.md) | Apply style function on this CommonMethod. |
| [makeBindable](arkts-na-common-makebindable-f.md) | Create a bindable property instance. |

### 类

| 名称 | 说明 |
| --- | --- |
| [ChildrenMainSize](arkts-na-common-childrenmainsize-c.md) | Indicates children main size. |
| [ContentTransitionEffect](arkts-na-common-contenttransitioneffect-c.md) | Defines the content transition effect. |
| [DrawModifier](arkts-na-common-drawmodifier-c.md) | Defined the draw modifier of node. Provides draw callbacks for the associated Node. Each DrawModifier instance can be set for only one component. Repeated setting is not allowed. |
| [LayoutPolicy](arkts-na-common-layoutpolicy-c.md) | Defines the policy of Layout |
| [ProgressMask](arkts-na-common-progressmask-c.md) | Implements a ProgressMask object to set the progress, maximum value, and color of the mask. |
| [RawInputEventWrapper](arkts-na-common-rawinputeventwrapper-c.md) | Defines the raw input event wrapper. |
| [ScrollResult](arkts-na-common-scrollresult-c.md) | The actual offset by which the scrollable scrolls. |
| [TextContentControllerBase](arkts-na-common-textcontentcontrollerbase-c.md) | TextContentControllerBase |
| [TouchResult](arkts-na-common-touchresult-c.md) | Defines TouchResult class. |
| [TouchTestInfo](arkts-na-common-touchtestinfo-c.md) | Defines TouchTestInfo class. |
| [TransitionEffect](arkts-na-common-transitioneffect-c.md) | 定义TransitionEffect类指定转场效果。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TextContentControllerBase](arkts-na-common-textcontentcontrollerbase-c-sys.md) | TextContentControllerBase |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilityHoverEvent](arkts-na-common-accessibilityhoverevent-i.md) | The accessibility hover action triggers this method invocation. |
| [AlignRuleOption](arkts-na-common-alignruleoption-i.md) | Defines the align rule options of relative container. |
| [AnimatableArithmetic](arkts-na-common-animatablearithmetic-i.md) | 该接口定义非number数据类型的动画运算规则。对非number类型的数据（如数组、结构体、颜色等）做动画，需要实现AnimatableArithmetic\&lt;T\&gt;接口中加法、减法、乘法和判断相等函数，使得该数据能参与动画的插值运算 和识别该数据是否发生改变。即定义它们为实现了AnimatableArithmetic\&lt;T\&gt;接口的类型。 |
| [AnimateParam](arkts-na-common-animateparam-i.md) | 动画效果相关参数。 |
| [AreaChangeOptions](arkts-na-common-areachangeoptions-i.md) | Defines the options about AreaChangeEvent. |
| [AsymmetricTransitionOption](arkts-na-common-asymmetrictransitionoption-i.md) | Defines the option of asymmetric transition. |
| [AttributeModifier](arkts-na-common-attributemodifier-i.md) | Defines the attribute modifier. |
| [AxisEvent](arkts-na-common-axisevent-i.md) | The axis event triggers this method invocation. |
| [BackgroundBlurStyleOptions](arkts-na-common-backgroundblurstyleoptions-i.md) | 继承自[BlurStyleOptions](arkts-na-common-blurstyleoptions-i.md)。 |
| [BackgroundBrightnessOptions](arkts-na-common-backgroundbrightnessoptions-i.md) | 背景亮度选项。 |
| [BackgroundEffectOptions](arkts-na-common-backgroundeffectoptions-i.md) | 背景效果参数。 |
| [BackgroundImageOptions](arkts-na-common-backgroundimageoptions-i.md) | Define the options for background image. |
| [BackgroundOptions](arkts-na-common-backgroundoptions-i.md) | Defines background options. |
| [BaseEvent](arkts-na-common-baseevent-i.md) | Defines the base event. |
| [BindOptions](arkts-na-common-bindoptions-i.md) | 半模态、全模态的公共配置接口。 |
| [Bindable](arkts-na-common-bindable-i.md) | Defines a bindable property |
| [BlurOptions](arkts-na-common-bluroptions-i.md) | Defines the options of blur |
| [BlurStyleOptions](arkts-na-common-blurstyleoptions-i.md) | Defines the options of blurStyle |
| [BorderImageOption](arkts-na-common-borderimageoption-i.md) | Border image option |
| [CaretOffset](arkts-na-common-caretoffset-i.md) | CaretOffset info. |
| [ClickEffect](arkts-na-common-clickeffect-i.md) | 定义点击效果。 |
| [ClickEvent](arkts-na-common-clickevent-i.md) | The tap action triggers this method invocation. |
| [CommonConfiguration](arkts-na-common-commonconfiguration-i.md) | Defines the common configuration. |
| [CommonMethod](arkts-na-common-commonmethod-i.md) | CommonMethod |
| [Configuration](arkts-na-common-configuration-i.md) | Defines the data type of the interface restriction. |
| [ContentCoverOptions](arkts-na-common-contentcoveroptions-i.md) | 继承自[BindOptions](arkts-na-common-bindoptions-i.md)。 全屏模态页面内容选项。 |
| [ContentModifier](arkts-na-common-contentmodifier-i.md) | Defines the content modifier. |
| [ContextMenuAnimationOptions](arkts-na-common-contextmenuanimationoptions-i.md) | Defines the ContextMenu's preview animator options. |
| [ContextMenuOptions](arkts-na-common-contextmenuoptions-i.md) | Defines the context menu options. |
| [CrownEvent](arkts-na-common-crownevent-i.md) | CrownEvent object description |
| [CustomPopupOptions](arkts-na-common-custompopupoptions-i.md) | Defines the custom popup options. |
| [DateRange](arkts-na-common-daterange-i.md) | Defines a range of dates. |
| [DismissContentCoverAction](arkts-na-common-dismisscontentcoveraction-i.md) | Component content cover dismiss |
| [DismissPopupAction](arkts-na-common-dismisspopupaction-i.md) | Component popup dismiss |
| [DismissSheetAction](arkts-na-common-dismisssheetaction-i.md) | 控制半模态的关闭。 |
| [DividerStyle](arkts-na-common-dividerstyle-i.md) | Provides an interface for the style of an divider including stroke width, color, start margin and end margin |
| [DragEvent](arkts-na-common-dragevent-i.md) | DragEvent object description |
| [DragInteractionOptions](arkts-na-common-draginteractionoptions-i.md) | Defines the drag options. |
| [DragItemInfo](arkts-na-common-dragiteminfo-i.md) | DragItemInfo object description |
| [DragPreviewOptions](arkts-na-common-dragpreviewoptions-i.md) | Defines the preview options. |
| [DropOptions](arkts-na-common-dropoptions-i.md) | Defines the options for the drop handling. |
| [DynamicNode](arkts-na-common-dynamicnode-i.md) | Define DynamicNode. |
| [EdgeEffectOptions](arkts-na-common-edgeeffectoptions-i.md) | Define EdgeEffect Options. |
| [EditModeOptions](arkts-na-common-editmodeoptions-i.md) | Define edit mode options. |
| [EventTarget](arkts-na-common-eventtarget-i.md) | Defines the event target. |
| [ExpectedFrameRateRange](arkts-na-common-expectedframeraterange-i.md) | 设置动画期望的帧率。 |
| [FadingEdgeOptions](arkts-na-common-fadingedgeoptions-i.md) | Defines the fadingEdge options. |
| [FocusAxisEvent](arkts-na-common-focusaxisevent-i.md) | Focus axis event object description. |
| [FocusMovement](arkts-na-common-focusmovement-i.md) | Defines the next focus item. |
| [ForegroundBlurStyleOptions](arkts-na-common-foregroundblurstyleoptions-i.md) | Defines the options of ForegroundBlurStyle |
| [ForegroundEffectOptions](arkts-na-common-foregroundeffectoptions-i.md) | Defines the options of ForegroundEffect |
| [GeometryInfo](arkts-na-common-geometryinfo-i.md) | Sub component layout info. |
| [GeometryTransitionOptions](arkts-na-common-geometrytransitionoptions-i.md) | Defines the options of geometry transition. |
| [GestureModifier](arkts-na-common-gesturemodifier-i.md) | Defines the gesture modifier. |
| [HistoricalPoint](arkts-na-common-historicalpoint-i.md) | TouchObject getHistoricalPoints Function Parameters |
| [HorizontalAlignParam](arkts-na-common-horizontalalignparam-i.md) | Defines the horizontal align rule options of relative container. |
| [HoverEvent](arkts-na-common-hoverevent-i.md) | The hover action triggers this method invocation. |
| [InputCounterOptions](arkts-na-common-inputcounteroptions-i.md) | Define the ratio of characters entered by the the percentage of InputCounterOptions. |
| [InputEventInterceptResult](arkts-na-common-inputeventinterceptresult-i.md) | Defines the input event intercept result. |
| [InputEventMonitor](arkts-na-common-inputeventmonitor-i.md) | Defines the input event monitor identifier. Important Notes: - This object is created and returned by the system as a unique identifier for the listener. - The object is an empty object with no accessible members. - Developers cannot actively construct this object, it can only be obtained through the registration interface. - Used for subsequent unregistration to verify identity. |
| [InvertOptions](arkts-na-common-invertoptions-i.md) | Define the options of invert |
| [ItemDragEventHandler](arkts-na-common-itemdrageventhandler-i.md) | Define item drag event handler. |
| [ItemDragInfo](arkts-na-common-itemdraginfo-i.md) | ItemDragInfo object description |
| [KeyEvent](arkts-na-common-keyevent-i.md) | KeyEvent object description: |
| [KeyframeAnimateParam](arkts-na-common-keyframeanimateparam-i.md) | 动画选项设置。 |
| [KeyframeState](arkts-na-common-keyframestate-i.md) | 设置关键帧选项。 |
| [Layoutable](arkts-na-common-layoutable-i.md) | Provides the child component layout information. |
| [LinearGradientBlurOptions](arkts-na-common-lineargradientbluroptions-i.md) | Linear Gradient Blur Interface |
| [LinearGradientOptions](arkts-na-common-lineargradientoptions-i.md) | Defines the options of linear gradient. |
| [LocalizedAlignRuleOptions](arkts-na-common-localizedalignruleoptions-i.md) | Defines the Localized align rule options of relative container. |
| [LocalizedHorizontalAlignParam](arkts-na-common-localizedhorizontalalignparam-i.md) | Defines the localized horizontal align param of relative container. |
| [LocalizedVerticalAlignParam](arkts-na-common-localizedverticalalignparam-i.md) | Defines the localized vertical align param of relative container. |
| [Measurable](arkts-na-common-measurable-i.md) | Sub component info passed from framework when measure happens. |
| [MeasureResult](arkts-na-common-measureresult-i.md) | Provides the measurement result of the component. |
| [MenuElement](arkts-na-common-menuelement-i.md) | Defines the menu element. |
| [MenuGridStyleOptions](arkts-na-common-menugridstyleoptions-i.md) | Defines grid style of menu. |
| [MenuMaskType](arkts-na-common-menumasktype-i.md) | Menu mask type |
| [MenuOptions](arkts-na-common-menuoptions-i.md) | Defines the menu options. |
| [MotionBlurAnchor](arkts-na-common-motionbluranchor-i.md) | Define motion blur anchor coordinates. |
| [MotionBlurOptions](arkts-na-common-motionbluroptions-i.md) | Define motion blur options. |
| [MotionPathOptions](arkts-na-common-motionpathoptions-i.md) | 设置组件的运动路径。 |
| [MouseEvent](arkts-na-common-mouseevent-i.md) | The mouse click action triggers this method invocation. |
| [MouseHistoricalPoint](arkts-na-common-mousehistoricalpoint-i.md) | Defines the historical point information for mouse event. |
| [MultiShadowOptions](arkts-na-common-multishadowoptions-i.md) | Defines the options of Shadow. |
| [NestedScrollOptions](arkts-na-common-nestedscrolloptions-i.md) | Define nested scroll options |
| [OverlayOffset](arkts-na-common-overlayoffset-i.md) | Defines the OverlayOffset. |
| [OverlayOptions](arkts-na-common-overlayoptions-i.md) | Defines the OverlayOptions interface. &lt;strong&gt;NOTE&lt;/strong&gt;:<br> When both align and offset are set, the effects are combined. The overlay is first aligned relative to the component and then offset from its current upper left corner. |
| [PickerDialogButtonStyle](arkts-na-common-pickerdialogbuttonstyle-i.md) | Provide an interface for the button style of picker |
| [PickerTextStyle](arkts-na-common-pickertextstyle-i.md) | Provide an interface for the text style of picker |
| [PixelRoundPolicy](arkts-na-common-pixelroundpolicy-i.md) | Defines the direction of pixel rounding at the component level. |
| [PixelStretchEffectOptions](arkts-na-common-pixelstretcheffectoptions-i.md) | Set the edge blur effect distance of the corresponding defense line of the component When the component expand out, no re-layout is triggered |
| [PopupBorderLinearGradient](arkts-na-common-popupborderlineargradient-i.md) | Popup border LinearGradient |
| [PopupButton](arkts-na-common-popupbutton-i.md) | Defines the popup button. |
| [PopupCommonOptions](arkts-na-common-popupcommonoptions-i.md) | Popup common options |
| [PopupMaskType](arkts-na-common-popupmasktype-i.md) | Popup mask type |
| [PopupMessageOptions](arkts-na-common-popupmessageoptions-i.md) | Defines the options of popup message. |
| [PopupOptions](arkts-na-common-popupoptions-i.md) | Defines the popup options. |
| [PopupStateChangeParam](arkts-na-common-popupstatechangeparam-i.md) | Popup state change param |
| [PreviewConfiguration](arkts-na-common-previewconfiguration-i.md) | Defines the drag preview configuration. |
| [RadialGradientOptions](arkts-na-common-radialgradientoptions-i.md) | Defines the options of radial gradient. |
| [RectResult](arkts-na-common-rectresult-i.md) | Describe the position, width, and height of a component. |
| [Rectangle](arkts-na-common-rectangle-i.md) | The data type used to describe a rectangular area. |
| [ResponseRegion](arkts-na-common-responseregion-i.md) | Defines the response region interface. |
| [ReuseOptions](arkts-na-common-reuseoptions-i.md) | Defining the reusable configuration parameters. |
| [RotateAngleOptions](arkts-na-common-rotateangleoptions-i.md) | 指定各轴旋转角的旋转参数选项。 |
| [RotateOptions](arkts-na-common-rotateoptions-i.md) | 组件旋转参数。 |
| [ScaleOptions](arkts-na-common-scaleoptions-i.md) |  |
| [SelectionOptions](arkts-na-common-selectionoptions-i.md) | Defines the selection options. |
| [ShadowOptions](arkts-na-common-shadowoptions-i.md) | Define the options of shadow |
| [SheetDismiss](arkts-na-common-sheetdismiss-i.md) | 控制半模态的关闭。 |
| [SheetOptions](arkts-na-common-sheetoptions-i.md) | 继承自[BindOptions](arkts-na-common-bindoptions-i.md)。 半模态页面内容选项。 |
| [SheetTitleOptions](arkts-na-common-sheettitleoptions-i.md) | 半模态面板的标题。 |
| [SizeResult](arkts-na-common-sizeresult-i.md) | Provides the component size information. |
| [SmartGestureShortcutOptions](arkts-na-common-smartgestureshortcutoptions-i.md) | Options for configuring smart gesture shortcuts. |
| [SpringBackAction](arkts-na-common-springbackaction-i.md) | 控制半模态关闭前的回弹。 |
| [StateStyles](arkts-na-common-statestyles-i.md) | Component State Styles. |
| [SweepGradientOptions](arkts-na-common-sweepgradientoptions-i.md) | Defines the options of sweep gradient. |
| [SystemAdaptiveOptions](arkts-na-common-systemadaptiveoptions-i.md) | 系统自适应调节参数，系统会默认开启根据芯片算力进行自适应效果调节的能力。 |
| [TerminationInfo](arkts-na-common-terminationinfo-i.md) | Indicates the information when the provider of the embedded UI is terminated. |
| [TextContentControllerOptions](arkts-na-common-textcontentcontrolleroptions-i.md) | Defines the span options of TextContentController. |
| [TextDecorationOptions](arkts-na-common-textdecorationoptions-i.md) | Defines the options of decoration. |
| [TipsOptions](arkts-na-common-tipsoptions-i.md) | Defines the Tips options. |
| [TouchEvent](arkts-na-common-touchevent-i.md) | Touch Action Function Parameters |
| [TouchObject](arkts-na-common-touchobject-i.md) | Type of the touch event. |
| [TranslateOptions](arkts-na-common-translateoptions-i.md) | Defines the options of translate. |
| [UICommonEvent](arkts-na-common-uicommonevent-i.md) | Defines a UICommonEvent which is used to set different common event to target component. |
| [UIGestureEvent](arkts-na-common-uigestureevent-i.md) | Defines a UIGestureEvent which is used to set different gestures to target component. |
| [UIScrollableCommonEvent](arkts-na-common-uiscrollablecommonevent-i.md) | Defines a UIScrollableCommonEvent which is used to set event to target component. |
| [VerticalAlignParam](arkts-na-common-verticalalignparam-i.md) | Defines the align rule options of relative container. |
| [VisibleAreaEventOptions](arkts-na-common-visibleareaeventoptions-i.md) | Defines the options about VisibleAreaEvent. |
| [sharedTransitionOptions](arkts-na-common-sharedtransitionoptions-i.md) | 共享元素转场动画参数。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ContextMenuOptions](arkts-na-common-contextmenuoptions-i-sys.md) | Defines the context menu options. |
| [DepthColorRGB](arkts-na-common-depthcolorrgb-i-sys.md) | RGB color in depth space. |
| [DepthVector3](arkts-na-common-depthvector3-i-sys.md) | 3D vector in depth space. |
| [DepthVector4](arkts-na-common-depthvector4-i-sys.md) | 4D vector in depth space. |
| [DragEvent](arkts-na-common-dragevent-i-sys.md) | DragEvent object description |
| [EdgeLightParams](arkts-na-common-edgelightparams-i-sys.md) | Defines the parameters of the edge light effect. |
| [GeometryTransitionOptions](arkts-na-common-geometrytransitionoptions-i-sys.md) | Defines the options of geometry transition. |
| [GravityCenterOptions](arkts-na-common-gravitycenteroptions-i-sys.md) | Defines the parameters of the center of gravity. |
| [LightSource](arkts-na-common-lightsource-i-sys.md) | 一个组件支持添加1个光源。 |
| [PixelMapMock](arkts-na-common-pixelmapmock-i-sys.md) | pixelmap object with release function. |
| [PointLightStyle](arkts-na-common-pointlightstyle-i-sys.md) | 通过设置光源和被照亮的类型实现点光源照亮周围组件的UI效果。 |
| [SheetOptions](arkts-na-common-sheetoptions-i-sys.md) | 继承自[BindOptions](arkts-na-common-bindoptions-i.md)。 半模态页面内容选项。 |
| [SpatialEffectParams](arkts-na-common-spatialeffectparams-i-sys.md) | Spatial effect params. |
| [SpatialPosition](arkts-na-common-spatialposition-i-sys.md) | Spatial corner positions in 3D space. |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccessibilityAction](arkts-na-common-accessibilityaction-e.md) | Enum for accessibility action type |
| [AccessibilityActionInterceptResult](arkts-na-common-accessibilityactioninterceptresult-e.md) | Enum for the result of accessibility action intercept function |
| [AccessibilityRoleType](arkts-na-common-accessibilityroletype-e.md) | Enum for accessibility component type |
| [AccessibilitySamePageMode](arkts-na-common-accessibilitysamepagemode-e.md) | Defines the same page mode |
| [AdaptiveColor](arkts-na-common-adaptivecolor-e.md) | Defines adaptive color |
| [AnchoredColorMode](arkts-na-common-anchoredcolormode-e.md) | enum color mode of pointing popup |
| [AvailableLayoutArea](arkts-na-common-availablelayoutarea-e.md) | Defines the available layout area. |
| [BlendApplyType](arkts-na-common-blendapplytype-e.md) | Enum for BlendApplyType. Indicate how to apply specified blend mode to the view's content. |
| [BlendMode](arkts-na-common-blendmode-e.md) | Enum for BlendMode. Blend modes for compositing current component with overlapping content. Use overlapping content as dst, current component as src. |
| [BlurStyle](arkts-na-common-blurstyle-e.md) | 模糊样式类型。 |
| [BlurStyleActivePolicy](arkts-na-common-blurstyleactivepolicy-e.md) | 定义背景模糊激活策略。 |
| [ChainStyle](arkts-na-common-chainstyle-e.md) | Enumerates the chain styles in relative container. |
| [ContentClipMode](arkts-na-common-contentclipmode-e.md) | Enum of scrollable containers' content clip mode. |
| [DismissReason](arkts-na-common-dismissreason-e.md) | 关闭原因类型。 |
| [DragBehavior](arkts-na-common-dragbehavior-e.md) | Enum for Drag Behavior. &lt;strong&gt;NOTE&lt;/strong&gt;:<br> DragBehavior serves to inform you about the intended method of data handling, whether it's a copy or a move, but it does not actually dictate the real processing of the data. |
| [DragPreviewMode](arkts-na-common-dragpreviewmode-e.md) | Defines the drag preview mode. |
| [DragResult](arkts-na-common-dragresult-e.md) | Enum for Drag Result. |
| [DraggingSizeChangeEffect](arkts-na-common-draggingsizechangeeffect-e.md) | Define drag start animation effect from drag preview to the handle drag image |
| [EffectEdge](arkts-na-common-effectedge-e.md) | Enumerates the effective edge of the edge effect. |
| [EffectType](arkts-na-common-effecttype-e.md) | Enum of using the effects template mode. |
| [FinishCallbackType](arkts-na-common-finishcallbacktype-e.md) | 动画中定义onFinish回调的类型。 |
| [HapticFeedbackMode](arkts-na-common-hapticfeedbackmode-e.md) | Defines the menu haptic feedback mode. |
| [HoverModeAreaType](arkts-na-common-hovermodeareatype-e.md) | 悬停态显示区域类型。 |
| [KeyboardAvoidMode](arkts-na-common-keyboardavoidmode-e.md) | enum keyboard avoid mode |
| [LayoutSafeAreaEdge](arkts-na-common-layoutsafeareaedge-e.md) | Define the edges for expanding the safe area in layout. |
| [LayoutSafeAreaType](arkts-na-common-layoutsafeareatype-e.md) | Describe the types for expanding the safe area in layout. |
| [MenuGridPosition](arkts-na-common-menugridposition-e.md) | Defines menu grid position. |
| [MenuKeyboardAvoidMode](arkts-na-common-menukeyboardavoidmode-e.md) | Define the mode of menu how to avoid keyboard. |
| [MenuPolicy](arkts-na-common-menupolicy-e.md) | Define the menu pop-up policy |
| [MenuPreviewMode](arkts-na-common-menupreviewmode-e.md) | Defines the menu preview mode. |
| [ModalMode](arkts-na-common-modalmode-e.md) | Define the modal mode of menu. |
| [ModalTransition](arkts-na-common-modaltransition-e.md) | 全屏模态转场方式枚举类型，用于设置全屏模态转场类型。 |
| [OutlineStyle](arkts-na-common-outlinestyle-e.md) | Outline Style |
| [PreDragStatus](arkts-na-common-predragstatus-e.md) | Defines the drag status before drag action. |
| [PreviewScaleMode](arkts-na-common-previewscalemode-e.md) | Defines the scaling mode for custom preview of contextMenu. |
| [RepeatMode](arkts-na-common-repeatmode-e.md) | Defines the Border Image Repeat Mode. |
| [SafeAreaEdge](arkts-na-common-safeareaedge-e.md) | Enumerates the safe area edges. |
| [SafeAreaType](arkts-na-common-safeareatype-e.md) | The types of expanded safe areas. |
| [ScrollSizeMode](arkts-na-common-scrollsizemode-e.md) | 半模态面板上下滑动时的内容更新方式。 |
| [ShadowStyle](arkts-na-common-shadowstyle-e.md) | enum Shadow style |
| [ShadowType](arkts-na-common-shadowtype-e.md) | Define the type of shadow |
| [SheetKeyboardAvoidMode](arkts-na-common-sheetkeyboardavoidmode-e.md) | 半模态激活输入法时对软键盘的避让方式。 |
| [SheetMode](arkts-na-common-sheetmode-e.md) | 半模态的显示层级模式。 |
| [SheetSize](arkts-na-common-sheetsize-e.md) | 指定半模态的高度。 |
| [SheetType](arkts-na-common-sheettype-e.md) | 半模态弹窗的样式。 |
| [SourceTool](arkts-na-common-sourcetool-e.md) | Defines the event tool type. |
| [SourceType](arkts-na-common-sourcetype-e.md) | Defines the event source type. |
| [ThemeColorMode](arkts-na-common-themecolormode-e.md) | enum color mode |
| [TouchTestStrategy](arkts-na-common-touchteststrategy-e.md) | Defines the touch test strategy object. |
| [TransitionEdge](arkts-na-common-transitionedge-e.md) | 转场边缘类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BlendApplyType](arkts-na-common-blendapplytype-e-sys.md) | Enum for BlendApplyType. Indicate how to apply specified blend mode to the view's content. |
| [DistortionMode](arkts-na-common-distortionmode-e-sys.md) | Enum for distortion animation mode. |
| [DragAnimationType](arkts-na-common-draganimationtype-e-sys.md) | Enum for Drag Animation Type. |
| [EdgeLightMode](arkts-na-common-edgelightmode-e-sys.md) | 边缘光效动画模式枚举。 |
| [TransitionHierarchyStrategy](arkts-na-common-transitionhierarchystrategy-e-sys.md) | 共享元素动画过程中in/out组件层级位置移动策略枚举。 \| 名称 \| 值 \| 说明 \| \| ------ \| - \| ---- \| \| NONE \| 0 \| 无层级提拉，in/out组件保持原来的层级位置，受父组件scale、position影响。 \| \| ADAPTIVE \| 1 \| 有层级提拉，in/out组件中相对低层级的组件被提拉至组件树上in/out组件相对高层级的位置上。 此模式还会导致被提拉的组件与父组件解绑，不受父组件scale、position影响。 例如in组件层级高于out组件，开启层级提拉后会在动画过程中将out组件从自己的父组件处解耦，并提拉至in组件的层级位置处，in组件层级位置不变。\| |
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
| [SystemUiMaterial](arkts-na-systemuimaterial-t-sys.md) | SystemUiMaterial |
<!--DelEnd-->

