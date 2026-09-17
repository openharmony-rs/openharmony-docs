# Common

Common for ide.

## Common

```TypeScript
Common()
```

Constructor

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Decorators

| Name | Description |
| --- | --- |
| [@AnimatableExtend](arkts-arkui-common-comp-animatableextend-d.md) | The @AnimatableExtend decorator is used to customize animatable property methods. Functions defined within this decorator are called on a frame-by-frame basis during the animation process until the animation ends. |
| [@Builder](arkts-arkui-common-comp-builder-d.md) | Defining Builder MethodDecorator |
| [@BuilderParam](arkts-arkui-common-comp-builderparam-d.md) | Defining BuilderParam PropertyDecorator |
| [@Component](arkts-arkui-common-comp-component-d.md) | Defining Component ClassDecorator Component is a ClassDecorator and it supports ComponentOptions as parameters. |
| [@ComponentV2](arkts-arkui-common-comp-componentv2-d.md) | Defining ComponentV2 ClassDecorator ComponentV2 is a ClassDecorator and it supports ComponentOptions as parameters. |
| [@Computed](arkts-arkui-common-comp-computed-d.md) | Defining Computed MethodDecorator. |
| [@Concurrent](arkts-arkui-common-comp-concurrent-d.md) | Defining Concurrent MethodDecorator |
| [@Consume](arkts-arkui-common-comp-consume-d.md) | Defining Consume PropertyDecorator. |
| [@Consumer](arkts-arkui-common-comp-consumer-d.md) | Defining Consumer PropertyDecorator, aliasName is the only matching key and if aliasName is the default, the default attribute name is regarded as aliasName. And @Consumer will find the nearest @Provider. |
| [@CustomDialog](arkts-arkui-common-comp-customdialog-d.md) | Defining CustomDialog ClassDecorator |
| [@CustomEnv](arkts-arkui-common-comp-customenv-d.md) | Defines the custom environment PropertyDecorator. |
| [@Entry](arkts-arkui-common-comp-entry-d.md) | Defines Entry ClassDecorator. |
| [@Env](arkts-arkui-common-comp-env-d.md) | Defining Env PropertyDecorator. On API 26.0.0 and above, the parameter also supports the SystemEnvKey&lt;T&gt; type. |
| [@Event](arkts-arkui-common-comp-event-d.md) | Defining Event PropertyDecorator. |
| [@Extend](arkts-arkui-common-comp-extend-d.md) | Defining Extend MethodDecorator |
| [@Link](arkts-arkui-common-comp-link-d.md) | Defining Link PropertyDecorator. |
| [@Local](arkts-arkui-common-comp-local-d.md) | Defining Local PropertyDecorator. |
| [@LocalBuilder](arkts-arkui-common-comp-localbuilder-d.md) | Defining LocalBuilder MethodDecorator |
| [@LocalStorageLink](arkts-arkui-common-comp-localstoragelink-d.md) | Defining LocalStorageLink PropertyDecorator. |
| [@LocalStorageProp](arkts-arkui-common-comp-localstorageprop-d.md) | Defining LocalStorageProp PropertyDecorator |
| [@Monitor](arkts-arkui-common-comp-monitor-d.md) | Define Monitor MethodDecorator |
| [@ObjectLink](arkts-arkui-common-comp-objectlink-d.md) | Defining ObjectLink PropertyDecorator. |
| [@Observed](arkts-arkui-common-comp-observed-d.md) | Defining Observed ClassDecorator. |
| [@ObservedV2](arkts-arkui-common-comp-observedv2-d.md) | Defining ObservedV2 ClassDecorator. |
| [@Once](arkts-arkui-common-comp-once-d.md) | Defining Once PropertyDecorator. |
| [@Param](arkts-arkui-common-comp-param-d.md) | Defining Param PropertyDecorator. |
| [@Preview](arkts-arkui-common-comp-preview-d.md) | Defining Preview ClassDecorator. |
| [@Prop](arkts-arkui-common-comp-prop-d.md) | Defining Prop PropertyDecorator. |
| [@Provide](arkts-arkui-common-comp-provide-d.md) | Defining Provide PropertyDecorator. |
| [@Provider](arkts-arkui-common-comp-provider-d.md) | Defining Provider PropertyDecorator, aliasName is the only matching key and if aliasName is the default, the default attribute name is regarded as aliasName. |
| [@Require](arkts-arkui-common-comp-require-d.md) | Defining Require PropertyDecorator. |
| [@Reusable](arkts-arkui-common-comp-reusable-d.md) | Defining Reusable ClassDecorator. |
| [@ReusableV2](arkts-arkui-common-comp-reusablev2-d.md) | Defining ReusableV2 ClassDecorator that is used to decorate @ComponentV2. |
| [@Sendable](arkts-arkui-common-comp-sendable-d.md) | Defining Sendable ClassDecorator The Sendable decorator can be used only for classes. A class with this decorator is marked as sendable, and the class object can be shared globally. Since 12, the Sendable decorator can be used for function and typeAlias also. A function with this decorator is marked as sendable, and the function can be an shareable property of sendable-class object. A typeAlias with this decorator is marked as sendable, and the typeAlias can be used to declare properties, variables, and arguments that need to be assigned with sendable-function. |
| [@State](arkts-arkui-common-comp-state-d.md) | Defining State PropertyDecorator. |
| [@StorageLink](arkts-arkui-common-comp-storagelink-d.md) | Defining StorageLink PropertyDecorator. |
| [@StorageProp](arkts-arkui-common-comp-storageprop-d.md) | Defining StorageProp PropertyDecorator. |
| [@Styles](arkts-arkui-common-comp-styles-d.md) | Defining Styles MethodDecorator |
| [@SyncMonitor](arkts-arkui-common-comp-syncmonitor-d.md) | Define SyncMonitor MethodDecorator. Decorator path parameters are the same as defined for Monitor. The function decorator is functionally equivalent to the UIUtils.addMonitor API with isSynchronous enabled. SyncMonitor must contain at least one path item, with multiple path items separated by commas. Path items are either observed attribute names or array item indices.The path in SyncMonitor supports wildcard at the end of a path item, but path items must never appear at the beginning or in the middle of a path. All other paths using one or more wildcard are invalid. |
| [@Trace](arkts-arkui-common-comp-trace-d.md) | Defining Trace PropertyDecorator. |
| [@Track](arkts-arkui-common-comp-track-d.md) | Defining Track PropertyDecorator. |
| [@Watch](arkts-arkui-common-comp-watch-d.md) | Defining Watch PropertyDecorator. |

### Interfaces

| Name | Description |
| --- | --- |
| [AccessibilityHoverEvent](arkts-arkui-accessibilityhoverevent-i.md) | The accessibility hover action triggers this method invocation. |
| [AlignRuleOption](arkts-arkui-alignruleoption-i.md) | Defines the align rule options of relative container. |
| [AnimatableArithmetic](arkts-arkui-animatablearithmetic-i.md) | The **AnimatableArithmetic** API defines animation calculation rules for non-number data types. To animate non-number data (such as arrays, structs, and colors), you need to implement the addition, subtraction, multiplication, and equality checking functions in the **AnimatableArithmetic\&lt;T\&gt;** API. This enables the data to participate in animation interpolation calculations and to detect whether the data has changed. In other words, the non-number data is defined as types that implement the **AnimatableArithmetic\&lt;T\&gt;** API. |
| [AnimateParam](arkts-arkui-animateparam-i.md) | Defines parameters related to animation effects. |
| [AreaChangeOptions](arkts-arkui-areachangeoptions-i.md) | Defines the options for the AreaChangeEvent. |
| [AttributeModifier](arkts-arkui-attributemodifier-i.md) | Defines the attribute modifier. |
| [AxisEvent](arkts-arkui-axisevent-i.md) | Describes the axis event object. Inherits from [BaseEvent](arkts-arkui-baseevent-i.md). |
| [BackgroundBlurStyleOptions](arkts-arkui-backgroundblurstyleoptions-i.md) | Defines the options of backgroundBlurStyle |
| [BackgroundBrightnessOptions](arkts-arkui-backgroundbrightnessoptions-i.md) | Provides background brightness options. |
| [BackgroundEffectOptions](arkts-arkui-backgroundeffectoptions-i.md) | Defines the options of BackgroundEffect |
| [BackgroundImageOptions](arkts-arkui-backgroundimageoptions-i.md) | Define the options for background image. |
| [BackgroundOptions](arkts-arkui-backgroundoptions-i.md) | Defines background options. |
| [BaseEvent](arkts-arkui-baseevent-i.md) | Basic event type. |
| [BindOptions](arkts-arkui-bindoptions-i.md) | Overlay module options |
| [BlurOptions](arkts-arkui-bluroptions-i.md) | Grayscale blur parameters. |
| [BlurSnapshotOptions](arkts-arkui-blursnapshotoptions-i-sys.md) | Defines the options for blur snapshot optimization. Setting this object enables blur optimization. |
| [BlurStyleOptions](arkts-arkui-blurstyleoptions-i.md) | Defines the options of blurStyle |
| [BorderImageOption](arkts-arkui-borderimageoption-i.md) | Border image option |
| [Callback](arkts-arkui-callback-i.md) | Defines the basic callback. |
| [CaretOffset](arkts-arkui-caretoffset-i.md) | Describes the position of the caret relative to the text box. |
| [ClickEffect](arkts-arkui-clickeffect-i.md) | Defines the click effect. |
| [ClickEvent](arkts-arkui-clickevent-i.md) | Inherits from [BaseEvent](arkts-arkui-baseevent-i.md). |
| [CommonConfiguration](arkts-arkui-commonconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. |
| [ComponentOptions](arkts-arkui-componentoptions-i.md) | Defines the options of Component ClassDecorator. |
| [Configuration](arkts-arkui-configuration-i.md) | Defines the data type of the interface restriction. |
| [ContentCoverOptions](arkts-arkui-contentcoveroptions-i.md) | Inherited from [BindOptions](arkts-arkui-bindoptions-i.md). |
| [ContentModifier](arkts-arkui-contentmodifier-i.md) | Defines the content modifier. |
| [ContextMenuAnimationOptions](arkts-arkui-contextmenuanimationoptions-i.md) | Defines the style for displaying a long-press preview. |
| [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) | Configures menu item information. |
| [CrownEvent](arkts-arkui-crownevent-i.md) | Defines a data structure for the crown event received by a component. It includes the timestamp, angular velocity, rotation angle, crown action, and event propagation disabling. |
| [CustomPopupOptions](arkts-arkui-custompopupoptions-i.md) | Provides information for displaying a custom popup. |
| [DateRange](arkts-arkui-daterange-i.md) | Defines a range of dates. |
| [DepthColorRGB](arkts-arkui-depthcolorrgb-i-sys.md) | RGB color in depth space. |
| [DepthVector3](arkts-arkui-depthvector3-i-sys.md) | 3D vector in depth space. |
| [DepthVector4](arkts-arkui-depthvector4-i-sys.md) | 4D vector in depth space. |
| [DismissContentCoverAction](arkts-arkui-dismisscontentcoveraction-i.md) | Component content cover dismiss |
| [DismissPopupAction](arkts-arkui-dismisspopupaction-i.md) | Provides information about the dismissal of the popup. |
| [DismissSheetAction](arkts-arkui-dismisssheetaction-i.md) | Component sheet dismiss |
| [DragEvent](arkts-arkui-dragevent-i.md) | Provides information about the drag event. |
| [DragInteractionOptions](arkts-arkui-draginteractionoptions-i.md) | Interaction behavior for the floating preview image |
| [DragItemInfo](arkts-arkui-dragiteminfo-i.md) | Defines the information about the dragged item during drag. |
| [DragPreviewOptions](arkts-arkui-dragpreviewoptions-i.md) | Preview image processing mode and badge count during dragging. |
| [DropOptions](arkts-arkui-dropoptions-i.md) | Sets parameters for the drop process. |
| [EdgeEffectOptions](arkts-arkui-edgeeffectoptions-i.md) | Define EdgeEffect Options. |
| [EdgeLightParams](arkts-arkui-edgelightparams-i-sys.md) | Defines the parameters of the edge light effect. |
| [EditModeOptions](arkts-arkui-editmodeoptions-i.md) | Define edit mode options. |
| [EntryOptions](arkts-arkui-entryoptions-i.md) | Defines the options of Entry ClassDecorator. |
| [EventTarget](arkts-arkui-eventtarget-i.md) | Defines the type of the **target** parameter in [BaseEvent](arkts-arkui-baseevent-i.md). |
| [ExpectedFrameRateRange](arkts-arkui-expectedframeraterange-i.md) | Sets the expected frame rate range for an animation. |
| [FadingEdgeOptions](arkts-arkui-fadingedgeoptions-i.md) | Defines the fadingEdge options. |
| [FocusAxisEvent](arkts-arkui-focusaxisevent-i.md) | Describes the focus axis event object. Inherits from [BaseEvent](arkts-arkui-baseevent-i.md). |
| [FocusMovement](arkts-arkui-focusmovement-i.md) | Sets the target component for focus movement based on key presses. If it is not specified, the default focus movement logic applies. |
| [ForegroundBlurStyleOptions](arkts-arkui-foregroundblurstyleoptions-i.md) | Inherits from [BlurStyleOptions](arkts-arkui-blurstyleoptions-i.md) to define the foreground blur options. |
| [ForegroundEffectOptions](arkts-arkui-foregroundeffectoptions-i.md) | Describes the foreground effect. |
| [GeometryInfo](arkts-arkui-geometryinfo-i.md) | Provides layout geometry information of the parent component (a custom component). Inherits from [SizeResult](arkts-arkui-sizeresult-i.md). |
| [GeometryTransitionOptions](arkts-arkui-geometrytransitionoptions-i.md) | Defines the options of geometry transition. |
| [GestureModifier](arkts-arkui-gesturemodifier-i.md) | You need a custom class to implement the **GestureModifier** API. |
| [GravityCenterOptions](arkts-arkui-gravitycenteroptions-i-sys.md) | Defines the parameters of the center of gravity. |
| [HistoricalPoint](arkts-arkui-historicalpoint-i.md) | Provides historical touch point information. |
| [HorizontalAlignParam](arkts-arkui-horizontalalignparam-i.md) | Defines the horizontal align rule of relative container. |
| [HoverEvent](arkts-arkui-hoverevent-i.md) | Inherits from [BaseEvent](arkts-arkui-baseevent-i.md). |
| [ICurve](arkts-arkui-icurve-i.md) | Interface for curve object. |
| [IMonitor](arkts-arkui-imonitor-i.md) | Define IMonitor interface |
| [IMonitorValue](arkts-arkui-imonitorvalue-i.md) | Define IMonitorValue interface |
| [InputCounterOptions](arkts-arkui-inputcounteroptions-i.md) | Provides configuration options for the character counter. |
| [InputEventInterceptResult](arkts-arkui-inputeventinterceptresult-i.md) | Input event interception result interface, used by the listener callback [InputEventListener](arkts-arkui-inputeventlistener-t.md) to return the interception decision. |
| [InputEventMonitor](arkts-arkui-inputeventmonitor-i.md) | Input event monitor identity object. |
| [InvertOptions](arkts-arkui-invertoptions-i.md) | Describes the options for inverting the foreground color. |
| [ItemDragEventHandler](arkts-arkui-itemdrageventhandler-i.md) | Define item drag event handler. |
| [ItemDragInfo](arkts-arkui-itemdraginfo-i.md) | ItemDragInfo object description |
| [KeyEvent](arkts-arkui-keyevent-i.md) | KeyEvent object description. |
| [KeyframeAnimateParam](arkts-arkui-keyframeanimateparam-i.md) | Provides animation configuration options. |
| [KeyframeState](arkts-arkui-keyframestate-i.md) | Provides keyframe configuration options. |
| [Layoutable](arkts-arkui-layoutable-i.md) | Provides the child component layout information. |
| [LayoutBorderInfo](arkts-arkui-layoutborderinfo-i.md) | Provides the border information of the child component. |
| [LayoutChild](arkts-arkui-layoutchild-i.md) | Sub component info passed from framework when layout and measure happens. |
| [LayoutInfo](arkts-arkui-layoutinfo-i.md) | Provides the child component layout information. |
| [LightSource](arkts-arkui-lightsource-i-sys.md) | Each component allows for one light source. |
| [LinearGradient](arkts-arkui-lineargradient-i.md) | Linear Gradient Interface |
| [LinearGradientBlurOptions](arkts-arkui-lineargradientbluroptions-i.md) | Linear Gradient Blur Interface |
| [LinearGradientOptions](arkts-arkui-lineargradientoptions-i.md) | Defines the linear gradient parameters. |
| [LocalizedAlignRuleOptions](arkts-arkui-localizedalignruleoptions-i.md) | Defines the Localized align rule options of relative container. |
| [LocalizedHorizontalAlignParam](arkts-arkui-localizedhorizontalalignparam-i.md) | Defines the localized horizontal align param of relative container. |
| [LocalizedVerticalAlignParam](arkts-arkui-localizedverticalalignparam-i.md) | Defines the localized vertical align param of relative container. |
| [Measurable](arkts-arkui-measurable-i.md) | Provides the child component position information. |
| [MeasureResult](arkts-arkui-measureresult-i.md) | Provides the measurement result of the component. This API inherits from [SizeResult](arkts-arkui-sizeresult-i.md). |
| [MenuElement](arkts-arkui-menuelement-i.md) | Configures icon, text, and interaction information of a menu item. |
| [MenuGridStyleOptions](arkts-arkui-menugridstyleoptions-i.md) | Defines the grid style of menu. |
| [MenuMaskType](arkts-arkui-menumasktype-i.md) | Sets the mask type. |
| [MenuOptions](arkts-arkui-menuoptions-i.md) | Configues menu item information, which is inherited from [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md). |
| [MonitorDecoratorOptions](arkts-arkui-monitordecoratoroptions-i.md) | Defines MonitorDecoratorOptions interface |
| [MotionBlurAnchor](arkts-arkui-motionbluranchor-i.md) | Describes the coordinates of the motion blur anchor. |
| [MotionBlurOptions](arkts-arkui-motionbluroptions-i.md) | Defines motion blur options. |
| [MotionPathOptions](arkts-arkui-motionpathoptions-i.md) | Defines motion path configuration options of the component. |
| [MouseEvent](arkts-arkui-mouseevent-i.md) | Inherits from [BaseEvent](arkts-arkui-baseevent-i.md). |
| [MouseHistoricalPoint](arkts-arkui-mousehistoricalpoint-i.md) | Mouse event historical point information. |
| [MultiShadowOptions](arkts-arkui-multishadowoptions-i.md) | Defines shadow style properties. |
| [NestedScrollOptions](arkts-arkui-nestedscrolloptions-i.md) | Define nested scroll options |
| [OverlayOffset](arkts-arkui-overlayoffset-i.md) | Offset of the overlay from the upper left corner. By default, the overlay is in the upper left corner of the component. |
| [OverlayOptions](arkts-arkui-overlayoptions-i.md) |  |
| [PickerDialogButtonStyle](arkts-arkui-pickerdialogbuttonstyle-i.md) | Provide an interface for the button style of picker |
| [PickerTextStyle](arkts-arkui-pickertextstyle-i.md) | Provide an interface for the text style of picker |
| [PixelMapMock](arkts-arkui-pixelmapmock-i-sys.md) | pixelmap object with release function. |
| [PixelRoundPolicy](arkts-arkui-pixelroundpolicy-i.md) | Enumerates the directions of pixel rounding at the component level. |
| [PixelStretchEffectOptions](arkts-arkui-pixelstretcheffectoptions-i.md) | Describes the pixel stretch effect options. |
| [PointLightStyle](arkts-arkui-pointlightstyle-i-sys.md) | You apply a point light style by setting the light source that emits illumination and the components to be illuminated. |
| [PopupBorderLinearGradient](arkts-arkui-popupborderlineargradient-i.md) | Sets the color and direction of the linear gradient for the outlines. |
| [PopupCommonOptions](arkts-arkui-popupcommonoptions-i.md) | Configures the parameters of a popup. You can use the [getPromptAction()](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getpromptaction) method in [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [PromptAction](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) object, and then call the attributes of **options** when [openPopup](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#openpopup18) or [updatePopup](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18) is called. |
| [PopupMaskType](arkts-arkui-popupmasktype-i.md) | Sets the color of the mask. |
| [PopupMessageOptions](arkts-arkui-popupmessageoptions-i.md) | Describes the popup message text style. |
| [PopupOptions](arkts-arkui-popupoptions-i.md) | Provides the configuration options for the popup. |
| [PopupStateChangeParam](arkts-arkui-popupstatechangeparam-i.md) | Display state of the popup. |
| [PreviewConfiguration](arkts-arkui-previewconfiguration-i.md) | Configures the style of the preview image during custom drag operations. |
| [PreviewParams](arkts-arkui-previewparams-i.md) | Define Preview property |
| [ProvideOptions](arkts-arkui-provideoptions-i.md) | Defines the options of Provide PropertyDecorator. |
| [RadialGradientOptions](arkts-arkui-radialgradientoptions-i.md) | Defines the radial gradient parameters. |
| [Rectangle](arkts-arkui-rectangle-i.md) | The data type used to describe a rectangular area. |
| [RectResult](arkts-arkui-rectresult-i.md) | Describes the position, width, and height of a component. |
| [ResponseRegion](arkts-arkui-responseregion-i.md) | Defines a touch target consisting of an input tool type, touch position, and size. |
| [ReusableOptions](arkts-arkui-reusableoptions-i.md) | Defines the options for Reusable ClassDecorator. |
| [ReuseOptions](arkts-arkui-reuseoptions-i.md) | Defining the reusable configuration parameters. |
| [RotateAngleOptions](arkts-arkui-rotateangleoptions-i.md) | Rotation parameter option of the rotation angle on each axis. |
| [RotateOptions](arkts-arkui-rotateoptions-i.md) | Defines component rotation parameters. |
| [ScaleOptions](arkts-arkui-scaleoptions-i.md) | Defines the options of scale. |
| [SelectionOptions](arkts-arkui-selectionoptions-i.md) | Defines the selection options. |
| [ShadowOptions](arkts-arkui-shadowoptions-i.md) | Provides the shadow attributes, including the blur radius, color, and offset along the x-axis and y-axis. |
| [sharedTransitionOptions](arkts-arkui-sharedtransitionoptions-i.md) | Parameters of the shared element transition animation. |
| [SheetDismiss](arkts-arkui-sheetdismiss-i.md) | Component sheet dismiss |
| [SheetOptions](arkts-arkui-sheetoptions-i.md) | Optional attributes of the sheet. Inherits from [BindOptions](arkts-arkui-bindoptions-i.md). |
| [SheetTitleBarBackgroundBlurOptions](arkts-arkui-sheettitlebarbackgroundbluroptions-i-sys.md) | Custom options for title bar background blur. All sub-properties are optional; unset properties use system default values. |
| [SheetTitleOptions](arkts-arkui-sheettitleoptions-i.md) | Component sheet title options |
| [SizeResult](arkts-arkui-sizeresult-i.md) |  |
| [SmartGestureShortcutOptions](arkts-arkui-smartgestureshortcutoptions-i.md) | Smart gesture response behavior configuration object. |
| [SpatialEffectParams](arkts-arkui-spatialeffectparams-i-sys.md) | Spatial effect params. |
| [SpatialPosition](arkts-arkui-spatialposition-i-sys.md) | Spatial corner positions in 3D space. |
| [SpringBackAction](arkts-arkui-springbackaction-i.md) | Defines sheet spring back action |
| [StateStyles](arkts-arkui-statestyles-i.md) | State-specific styles for the component. |
| [SweepGradientOptions](arkts-arkui-sweepgradientoptions-i.md) | Defines the sweep gradient parameters. |
| [SystemAdaptiveOptions](arkts-arkui-systemadaptiveoptions-i.md) | Provides parameters for system adaptive adjustments. By default, the system performs adaptive adjustments based on chip performance. |
| [TextContentControllerOptions](arkts-arkui-textcontentcontrolleroptions-i.md) | Provides configuration options for text insertion operations in text input components. |
| [TextDecorationOptions](arkts-arkui-textdecorationoptions-i.md) | Provides text decoration options. |
| [TipsOptions](arkts-arkui-tipsoptions-i.md) | Defines the parameters of the tooltip. |
| [TouchEvent](arkts-arkui-touchevent-i.md) | Inherits from [BaseEvent](arkts-arkui-baseevent-i.md). In non-event injection scenarios, **changedTouches** contains points resampled at the screen refresh rate, while **touches** contains points reported at the device's refresh rate. As such, **changedTouches** data may differ from **touches**. |
| [TouchObject](arkts-arkui-touchobject-i.md) | Type of the touch event. |
| [TransitionOptions](arkts-arkui-transitionoptions-i.md) | Defines the transition effect by setting parameters in the struct. |
| [TranslateOptions](arkts-arkui-translateoptions-i.md) | Defines the options of translate. |
| [UICommonEvent](arkts-arkui-uicommonevent-i.md) | Implements a common event callback. Passing **undefined** as the input parameter resets the corresponding event callback. |
| [UIGestureEvent](arkts-arkui-uigestureevent-i.md) | Provides APIs for configuring gestures bound to a component. |
| [UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md) | Defines a UIScrollableCommonEvent which is used to set event to target component. |
| [VerticalAlignParam](arkts-arkui-verticalalignparam-i.md) | Defines the vertical align rule of relative container. |
| [VisibleAreaEventOptions](arkts-arkui-visibleareaeventoptions-i.md) | Describes visible area change configuration options. |

### Types

| Name | Description |
| --- | --- |
| [AccessibilityActionInterceptCallback](arkts-arkui-accessibilityactioninterceptcallback-t.md) | Defines the callback type used in accessibility action intercept. The value of action indicates the accessibility action type. |
| [AccessibilityCallback](arkts-arkui-accessibilitycallback-t.md) | Defines the callback type used in accessibility hover events. The value of isHover indicates whether the touch is hovering over the component. The value of event contains information about AccessibilityHoverEvent. |
| [AccessibilityFocusCallback](arkts-arkui-accessibilityfocuscallback-t.md) | Defines the callback type used in accessibility focus. The value of isFocus indicates whether the current component is focused |
| [AccessibilityTransparentCallback](arkts-arkui-accessibilitytransparentcallback-t.md) | Defines the callback type used in accessibility hover transparent event. |
| [AnimationRange](arkts-arkui-animationrange-t.md) | Sets the relative scale ratio at the start and end of the animation compared to the original preview image. |
| [AreaChangeCallback](arkts-arkui-areachangecallback-t.md) | Callback type for the component area change event. |
| [Blender](arkts-arkui-blender-t-sys.md) | [Blender](arkts-arkui-blender-t-sys.md) |
| [BorderRadiusType](arkts-arkui-borderradiustype-t.md) | Enumerates the border corner radius types. |
| [BuilderCallback](arkts-arkui-buildercallback-t.md) | Defines the callback type used in mutableBuilder. |
| [CircleShape](arkts-arkui-circleshape-t.md) | Defines the CircleShape type. |
| [ComponentContent](arkts-arkui-componentcontent-t.md) | Represents a constructor used to create a **ComponentContent** object. |
| [Context](arkts-arkui-context-t.md) | Get context. |
| [CustomBuilder](arkts-arkui-custombuilder-t.md) | Defines the CustomBuilder Type. |
| [CustomBuilderT](arkts-arkui-custombuildert-t.md) | Defines the CustomBuilder type with parameter. |
| [DataLoadParams](arkts-arkui-dataloadparams-t.md) | Defines the data loading parameters used during a drop operation. |
| [DataSyncOptions](arkts-arkui-datasyncoptions-t.md) | Defines the input parameter object for **startDataLoading**. |
| [DragSpringLoadingConfiguration](arkts-arkui-dragspringloadingconfiguration-t.md) | Defines the configuration parameters for drag hover detection. |
| [DrawContext](arkts-arkui-drawcontext-t.md) | [DrawContext](arkts-arkui-drawcontext-t.md) |
| [EllipseShape](arkts-arkui-ellipseshape-t.md) | Defines the EllipseShape type. |
| [EnvDecorator](arkts-arkui-envdecorator-t.md) | Define Env Decorator type |
| [Filter](arkts-arkui-filter-t.md) | Represents a filter object. |
| [FractionStop](arkts-arkui-fractionstop-t.md) | Defines a gradient blur stop. |
| [GestureCollectInterceptCallback](arkts-arkui-gesturecollectinterceptcallback-t.md) | Defines the callback type used in [onGestureCollectIntercept](arkts-arkui-commonmethod-c.md#ongesturecollectintercept). |
| [GestureRecognizerJudgeBeginCallback](arkts-arkui-gesturerecognizerjudgebegincallback-t.md) | Represents a custom gesture recognizer judgment callback type. |
| [HoverCallback](arkts-arkui-hovercallback-t.md) | Defines the callback type for hover events. |
| [ImageModifier](arkts-arkui-imagemodifier-t.md) | [ImageModifier](arkts-arkui-imagemodifier-t.md) |
| [InputEventListener](arkts-arkui-inputeventlistener-t.md) | Input event listener callback type. |
| [IntentionCode](arkts-arkui-intentioncode-t.md) | Intention corresponding to the key. |
| [Matrix4Transit](arkts-arkui-matrix4transit-t.md) | Import the Matrix4Transit type object for common method. |
| [MonitorDecorator](arkts-arkui-monitordecorator-t.md) | Defines Monitor Decorator type |
| [NavDestinationInfo](arkts-arkui-navdestinationinfo-t.md) | The navigation destination information. |
| [NavigationInfo](arkts-arkui-navigationinfo-t.md) | The navigation information. |
| [OnDidStopDraggingCallback](arkts-arkui-ondidstopdraggingcallback-t.md) | On scroll callback using in scrollable onDidStopDragging. |
| [OnDragEventCallback](arkts-arkui-ondrageventcallback-t.md) | Defines a callback for drag events. |
| [OnGetPreviewBadgeCallback](arkts-arkui-ongetpreviewbadgecallback-t.md) | Defines the callback type used in onGetPreviewBadge of EditModeOptions. |
| [OnItemDragStartCallback](arkts-arkui-onitemdragstartcallback-t.md) | Defines the callback type used in onItemDragStart. |
| [OnMoveHandler](arkts-arkui-onmovehandler-t.md) | Defines the onMove callback. |
| [OnNeedSoftkeyboardCallback](arkts-arkui-onneedsoftkeyboardcallback-t.md) | Defines the callback type used in onNeedSoftkeyboard. Called when component is focused, the return value indicates whether keyboard is needed. |
| [OnScrollCallback](arkts-arkui-onscrollcallback-t.md) | On scroll callback using in scrollable onDidScroll. |
| [OnVisibleIndexesChangeCallback](arkts-arkui-onvisibleindexeschangecallback-t.md) | Defines the callback type used in OnVisibleIndexesChange. |
| [OnWillScrollCallback](arkts-arkui-onwillscrollcallback-t.md) | Called before scroll to allow developer to control real offset the Scrollable can scroll. |
| [OnWillStopDraggingCallback](arkts-arkui-onwillstopdraggingcallback-t.md) | On scroll callback using in scrollable onWillStopDragging. |
| [Optional](arkts-arkui-optional-t.md) | Defines the Optional type. The value can be **undefined**. |
| [PathShape](arkts-arkui-pathshape-t.md) | Defines the PathShape type. |
| [PixelMap](arkts-arkui-pixelmap-t.md) | Defines the PixelMap type object for ui component. |
| [PointerStyle](arkts-arkui-pointerstyle-t.md) | Defines the pointer style. |
| [PopupStateChangeCallback](arkts-arkui-popupstatechangecallback-t.md) | Represents the callback invoked when the popup state changes. |
| [PromptActionDialogController](arkts-arkui-promptactiondialogcontroller-t.md) | Import the DialogController type from promptAction. |
| [RectShape](arkts-arkui-rectshape-t.md) | Defines the RectShape type. |
| [ReuseIdCallback](arkts-arkui-reuseidcallback-t.md) | ReuseId callback type. It is used to compute reuseId. |
| [ReusePoolOwnership](arkts-arkui-reusepoolownership-t.md) | Defining the reuse type of a custom component. |
| [RouterPageInfo](arkts-arkui-routerpageinfo-t.md) | The router page information. |
| [ShouldBuiltInRecognizerParallelWithCallback](arkts-arkui-shouldbuiltinrecognizerparallelwithcallback-t.md) | Represents the callback used to set the parallel relationship between built-in gestures and gestures of other components in the response chain. |
| [ShouldRecognizerParallelWithCallback](arkts-arkui-shouldrecognizerparallelwithcallback-t.md) | Represents the callback used to set the parallel relationship between gestures of the current component and gestures of other components in the response chain. |
| [SizeChangeCallback](arkts-arkui-sizechangecallback-t.md) | Defines the callback type used in onSizeChange. The value of oldValue is last size of the component. The value of newValue is new size of the component. |
| [SpringLoadingContext](arkts-arkui-springloadingcontext-t.md) | Defines callback context information, which is passed to the application in the hover detection callback to allow the application to access the drag status. |
| [Summary](arkts-arkui-summary-t.md) | Provides a summary of drag-related data. |
| [SymbolGlyphModifier](arkts-arkui-symbolglyphmodifier-t.md) | Defines custom icon symbol configurations. |
| [SystemUiMaterial](arkts-arkui-systemuimaterial-t.md) | Base class for system material objects. |
| [Theme](arkts-arkui-theme-t.md) | Theme. |
| [TipsMessageType](arkts-arkui-tipsmessagetype-t.md) | Provides information about the tooltip. |
| [TouchTestDoneCallback](arkts-arkui-touchtestdonecallback-t.md) | Represents the callback type for dynamically specifying gesture recognizer participation in gesture processing. |
| [TransitionEffects](arkts-arkui-transitioneffects-t.md) | Defines all transition effects. |
| [TransitionFinishCallback](arkts-arkui-transitionfinishcallback-t.md) | Represents the type of callback for the end of a component's transition animation. |
| [UIContext](arkts-arkui-uicontext-t.md) | [UIContext](arkts-arkui-uicontext-t.md) |
| [UnifiedData](arkts-arkui-unifieddata-t.md) | Defines drag-related data. |
| [UniformDataType](arkts-arkui-uniformdatatype-t.md) | Import the UniformDataType type object for ui component. |
| [VisibleAreaChangeCallback](arkts-arkui-visibleareachangecallback-t.md) | Represents a callback for visible area changes of the component. |
| [VisualEffect](arkts-arkui-visualeffect-t.md) | Represents a visual effect configuration object. |
| [window](arkts-arkui-window-t.md) | The type for window. |

### Enums

| Name | Description |
| --- | --- |
| [AccessibilityAction](arkts-arkui-accessibilityaction-e.md) | Enum for accessibility action type |
| [AccessibilityActionInterceptResult](arkts-arkui-accessibilityactioninterceptresult-e.md) | Enum for the result of accessibility action intercept function |
| [AccessibilityRoleType](arkts-arkui-accessibilityroletype-e.md) | Enumerates the component role types used by screen readers. @enum { number } |
| [AccessibilitySamePageMode](arkts-arkui-accessibilitysamepagemode-e.md) | Enumerates the same-page modes for cross-process embedded components and their host applications. @enum { number } |
| [AdaptiveColor](arkts-arkui-adaptivecolor-e.md) | Enumerates the adaptive color modes used for the background blur effect. |
| [AnchoredColorMode](arkts-arkui-anchoredcolormode-e.md) | @enum { number } |
| [AvailableLayoutArea](arkts-arkui-availablelayoutarea-e.md) | Enumerates the reference sizes of the available layout area when the preview image width and height are set to percentages. |
| [BlendApplyType](arkts-arkui-blendapplytype-e.md) | Defines how to apply the specified blend mode to the content of a view. |
| [BlendMode](arkts-arkui-blendmode-e.md) | Blend mode. |
| [BlurStyle](arkts-arkui-blurstyle-e.md) | Enumerates blur styles. |
| [BlurStyleActivePolicy](arkts-arkui-blurstyleactivepolicy-e.md) | Enumerates the policies for activating the blur style. |
| [ChainStyle](arkts-arkui-chainstyle-e.md) | Enumerates the chain styles in relative container. |
| [ContentClipMode](arkts-arkui-contentclipmode-e.md) | Enum of scrollable containers' content clip mode. |
| [DismissReason](arkts-arkui-dismissreason-e.md) | Enumerates the reasons for popup dismissal. |
| [DistortionMode](arkts-arkui-distortionmode-e-sys.md) | Enum for distortion animation mode. |
| [DragAnimationType](arkts-arkui-draganimationtype-e-sys.md) | Enumerates drag animation types. |
| [DragBehavior](arkts-arkui-dragbehavior-e.md) | Describes the drag behavior. When [DragResult](arkts-arkui-dragresult-e.md) is set to **DROP_ENABLED**, you can define **DragBehavior** as either **COPY** or **MOVE**. When **DragBehavior** is set to **COPY**, a plus sign will be displayed in the badge of the dragged object. When **DragBehavior** is set to **MOVE**, the plus sign will not be displayed. **DragBehavior** is used to indicate the intended way of handling data (either copy or move) without governing the actual data processing. This behavior is reported back to the drag source through **onDragEnd**, enabling the drag initiator to distinguish whether the operation results in a copy or a move of the data. |
| [DraggingSizeChangeEffect](arkts-arkui-draggingsizechangeeffect-e.md) | Enumerates the transition effects for switching between the floating image (set through [bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu)) and the drag preview when both are configured on a component. |
| [DragPreviewMode](arkts-arkui-dragpreviewmode-e.md) | Sets the display mode of the drag preview. |
| [DragResult](arkts-arkui-dragresult-e.md) | Defines the result of a drag operation and the drop-selection state of a component. |
| [EdgeLightMode](arkts-arkui-edgelightmode-e-sys.md) | Edge light animation mode enumeration. |
| [EffectEdge](arkts-arkui-effectedge-e.md) | Enumerates the effective edge of the edge effect. |
| [EffectType](arkts-arkui-effecttype-e.md) | Enum of using the effects template mode. |
| [FinishCallbackType](arkts-arkui-finishcallbacktype-e.md) | Defines the type of the **onFinish** callback. |
| [HapticFeedbackMode](arkts-arkui-hapticfeedbackmode-e.md) | Enumerates the haptic feedback modes used when the menu is displayed. |
| [HoverModeAreaType](arkts-arkui-hovermodeareatype-e.md) | Enumerates the type of area in hover mode. |
| [KeyboardAvoidMode](arkts-arkui-keyboardavoidmode-e.md) | Enumerates modes in which a popup responds when the keyboard is displayed. |
| [LayoutSafeAreaEdge](arkts-arkui-layoutsafeareaedge-e.md) | Define the edges for expanding the safe area in layout. |
| [LayoutSafeAreaType](arkts-arkui-layoutsafeareatype-e.md) | Enumerates the types for expanding layout safe areas. |
| [MenuGridPosition](arkts-arkui-menugridposition-e.md) | The position of grid in menu. |
| [MenuKeyboardAvoidMode](arkts-arkui-menukeyboardavoidmode-e.md) | Enumerates the modes in which the menu avoids the soft keyboard. |
| [MenuPolicy](arkts-arkui-menupolicy-e.md) | Enumerates menu display policies. |
| [MenuPreviewMode](arkts-arkui-menupreviewmode-e.md) | Defines the preview style of a menu. |
| [ModalMode](arkts-arkui-modalmode-e.md) | Enumerates modal modes of the sub-window menu. |
| [ModalTransition](arkts-arkui-modaltransition-e.md) | Defines modal transition type. |
| [OutlineStyle](arkts-arkui-outlinestyle-e.md) | Enumerates outline styles. |
| [PreDragStatus](arkts-arkui-predragstatus-e.md) | Defines the states before the drag gesture is triggered. |
| [PreviewScaleMode](arkts-arkui-previewscalemode-e.md) | Enumerates the scale modes of the preview image. |
| [RepeatMode](arkts-arkui-repeatmode-e.md) | Defines the Border Image Repeat Mode. |
| [ReusableMemOptStrategy](arkts-arkui-reusablememoptstrategy-e.md) | Defines a type for memory optimization strategy. |
| [SafeAreaEdge](arkts-arkui-safeareaedge-e.md) | Enumerates the edges for expanding the safe area. |
| [SafeAreaType](arkts-arkui-safeareatype-e.md) | Enumerates the types for expanding layout safe areas. |
| [ScrollSizeMode](arkts-arkui-scrollsizemode-e.md) | Define the scroll size mode of the sheet. |
| [ShadowStyle](arkts-arkui-shadowstyle-e.md) | enum Shadow style |
| [ShadowType](arkts-arkui-shadowtype-e.md) | Define the type of shadow |
| [SheetKeyboardAvoidMode](arkts-arkui-sheetkeyboardavoidmode-e.md) | Define the mode of sheet how to avoid keyboard. |
| [SheetMode](arkts-arkui-sheetmode-e.md) | Define the display mode of the sheet. |
| [SheetSize](arkts-arkui-sheetsize-e.md) | Defines sheet size type. |
| [SheetTitleBarBackgroundBlur](arkts-arkui-sheettitlebarbackgroundblur-e.md) | Enum of title bar background blur styles. |
| [SheetTitleBarHoverMode](arkts-arkui-sheettitlebarhovermode-e.md) | Enum of title bar hover modes. |
| [SheetType](arkts-arkui-sheettype-e.md) | Defines the sheet type. |
| [SourceTool](arkts-arkui-sourcetool-e.md) | Enumerates the input source tool types. |
| [SourceType](arkts-arkui-sourcetype-e.md) | Enumerates the input source device types. |
| [SpatialPositionMode](arkts-arkui-spatialpositionmode-e-sys.md) | Spatial position mode. Indicates the coordinate system used by the corner positions. |
| [SystemProperties](arkts-arkui-systemproperties-e.md) | Defining Environment variable enumeration value. |
| [ThemeColorMode](arkts-arkui-themecolormode-e.md) | Enumerates the color modes. |
| [TouchTestStrategy](arkts-arkui-touchteststrategy-e.md) | Event dispatch strategy. |
| [TransitionEdge](arkts-arkui-transitionedge-e.md) | Enumerates the transition edge types. |
| [TransitionHierarchyStrategy](arkts-arkui-transitionhierarchystrategy-e-sys.md) | Enumerates the strategies for the hierarchical position movement of **in** / **out** components in the component tree during the shared element transition process. |

## Examples

```TypeScript
This example demonstrates how to modify the HitTestMode attribute of a component using onTouchIntercept.
```

```TypeScript
### Example 1: Implementing a Frame-by-Frame Layout Effect

The following example implements the frame-by-frame layout effects by changing the width of the Text component.


```

```TypeScript
### Example 2: Implementing a Polyline Animation Effect

The following example implements a polyline animation effect.
```

```TypeScript
### Example 1: Setting the Edge Light Effect Animation for a Sheet

The following example enables the Edge Light Effect animation by setting the edgeLightMode attribute, and uses the systemMaterial API in [SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions) to implement a semi-transparent material effect.

Since API version 26.0.0, the edgeLightMode attribute is added to [SheetOptions](arkts-arkui-sheetoptions-i.md).


```

```TypeScript
### Example 2 (Set Blur Optimization for Sheet)

The following example enables blur optimization by setting the blurSnapshot attribute. When the systemMaterial API in [SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions) is used to set a material effect, or the blurStyle API in [SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions) is used to set blur, and a significant increase in power consumption is observed, you can try enabling blur optimization.

Since API version 26.0.0, [SheetOptions](arkts-arkui-sheetoptions-i.md) adds the blurSnapshot attribute.
```

```TypeScript
### Example 1: Setting onAccessibilityActionIntercept to Intercept Click Events

This example demonstrates how to use the onAccessibilityActionIntercept event to intercept the click event of a Toggle component before it is triggered in accessibility mode, and the developer decides whether to allow the click event.
```

```TypeScript
### Example 2: Setting the onAccessibilityFocus Callback

Since API version 18, the callback is triggered when the focus acquisition or blur state changes. This example demonstrates the basic usage of [onAccessibilityFocus](arkts-arkui-commonmethod-c.md#onaccessibilityfocus). When the focus moves to "onAccessibilityFocus takes effect", "[testingTag] isFocus current is true" is printed. When the focus moves to a position other than "onAccessibilityFocus takes effect", "[testingTag] isFocus current is false" is printed.
```

```TypeScript
This example demonstrates how to set the hover effect for components using hoverEffect.
```

```TypeScript
// After the allowForceDark(false) attribute is added to a component, the color inversion is not used for the current component and all its child components.
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Column() {
        Text("Hello World")
          .fontSize(20)
          .fontColor(Color.Blue)
          .onClick(() => {
            console.info(`Text is clicked`);
          })
      }
      .allowForceDark(false) // Column and its child component Text do not use the color inversion, and are not affected by the color inversion used by the parent component Column.

      Row() {
        Button('BUTTON')
          .backgroundColor(Color.Grey)
          .allowForceDark(true)
          .onClick(() => {
            console.info(`Button is clicked`);
          })
      }
      .allowForceDark(false) // Row and its child component Button do not use the color inversion, and are not affected by the color inversion used by the parent component Column.
    }
    .allowForceDark(true)
    .width('100%')
    .height('100%')
  }
}
```

```TypeScript
### Example 1: Setting a Gradient Border

This example demonstrates how to set a gradient border for a component using the [borderImage](arkts-arkui-commonmethod-c.md#borderimage) API.


```

```TypeScript
### Example 2: Dynamically Adjusting Property Values

Dynamically adjusts the property values in the [borderImage](arkts-arkui-commonmethod-c.md#borderimage) API via the [Slider](../../apis-arkui/arkui-js/js-components-basic-slider.md) API.


```

```TypeScript
### Example 3: Using LocalizedEdgeWidths Type Values

This example demonstrates how to use the [LocalizedEdgeWidths](ts-types.md#localizededgewidths12) type for the slice, width, and outset properties in the [borderImage](arkts-arkui-commonmethod-c.md#borderimage) API.
```

```TypeScript
// xxx.ets
@Entry
@Component
struct TouchableExample {
  @State text1: string = '';
  @State text2: string = '';

  build() {
    Stack() {
      Rect()
        .fill(Color.Gray).width(150).height(150)
        .onClick(() => {
          console.info(this.text1 = 'Rect Clicked');
        })
        .overlay(this.text1, { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
      Ellipse()
        .fill(Color.Pink).width(150).height(80)
        .touchable(false) // When the Ellipse area is touched, the message "Ellipse Clicked" is not displayed.
        .onClick(() => {
          console.info(this.text2 = 'Ellipse Clicked');
        })
        .overlay(this.text2, { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
    }.margin(100);
  }
}
```

```TypeScript
### Example 1: Binding a Tooltip

This example shows how to bind a tooltip to a button using bindTips.


```

```TypeScript
### Example 2: Displaying and Hiding Multiple Tooltips

This example demonstrates how to configure multiple tooltips to appear and disappear in sequence using bindTips.


```

```TypeScript
### Example 3: Setting the Immersive Light-Sensing Visual Effect of a Floating Bubble

This example sets the system material of a component through the systemMaterial attribute in [TipsOptions](arkts-arkui-tipsoptions-i.md), implementing the immersive light-sensing visual effect of bindTips.

The immersive light-sensing effect of a component is adaptively adjusted based on the device computing power and the immersive light-sensing effect set by the user in the system, requiring no additional adaptation by developers.

Since API version 26.0.0, the systemMaterial attribute is added to TipsOptions.
```

```TypeScript
This example shows how to set the opacity of a component using [opacity](#opacity).
```

```TypeScript
This example demonstrates property animations using the animation API.
```

```TypeScript
@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      ReusableV2Component()
        .reuse({reuseId: () => 'reuseComponent'}) // Use 'reuseComponent' as reuseId.
      ReusableV2Component()
        .reuse({reuseId: () => ''}) // If an empty string is used, the component name 'ReusableV2Component' is used as reuseId.
      ReusableV2Component() // If reuseId is not specified, the component name 'ReusableV2Component' is used as reuseId.
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  build() {
    Text('content')
  }
}
```

```TypeScript
### Example 1: Setting a Touch Target via the responseRegion API

This example demonstrates how to set a touch target for a button using responseRegion to respond to click events.


```

```TypeScript
### Example 2: Setting a Touch Target via the responseRegionList API

This example demonstrates how to set a touch target for a button using [responseRegionList](arkts-arkui-commonmethod-c.md#responseregionlist) to respond to click events.

The responseRegionList API is supported since API version 22.


```

```TypeScript
### Example 3: Setting the Mouse Touch Target to Respond to Click Events

This example uses [mouseResponseRegion](arkts-arkui-commonmethod-c.md#mouseresponseregion) to set the mouse touch target to respond to click events.
```

```TypeScript
This example demonstrates how to apply content blur to an image using foregroundBlurStyle.
```

```TypeScript
### Example 1: Setting Custom Properties for a System Component

This example shows how to set custom properties on the [Column](ts-container-column.md) component and obtain the set custom properties from its corresponding FrameNode.
```

```TypeScript
### Example 2: Setting Custom Properties for a Custom Component

Since API version 26.0.0, custom properties can be set for custom components via the [customProperty](#customproperty) API. This example demonstrates a [custom component layout](../../../ui/state-management/arkts-page-custom-components-layout.md) scenario: custom properties are set for a custom component, and their values are obtained from the [onMeasureSize](ts-custom-component-layout.md#onmeasuresize10) callback.
```

```TypeScript
### Example 1: Displaying a Basic Menu

This example demonstrates how to display a basic menu by configuring [MenuElement](#menuelement) for bindMenu.


```

```TypeScript
### Example 2: Displaying a Custom Menu

This example shows how to use bindMenu with a custom builder to create a custom menu. In addition, starting from API version 18, the hapticFeedbackMode property in [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) can be configured to implement the haptic feedback effect when the menu is displayed.


```

```TypeScript
### Example 3: Displaying a Menu on Long Press

This example demonstrates how to display a menu by setting [responseType](ts-appendix-enums.md#responsetype8).LongPress for bindContextMenu.


```

```TypeScript
### Example 4: Displaying a Menu with an Arrow on Right-Clicking

This example demonstrates how to display a menu with an arrow by setting the enableArrow property in [responseType](ts-appendix-enums.md#responsetype8).RightClick and [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) for bindContextMenu. In addition, starting from API version 18, the hapticFeedbackMode property in [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) can be configured to implement the haptic feedback effect when the menu is displayed.


```

```TypeScript
### Example 5: Displaying a Menu with a Screenshot Preview on Long Press

This example demonstrates how to display a menu with a screenshot preview by setting [MenuPreviewMode](arkts-arkui-menupreviewmode-e.md) of the preview property in [responseType](ts-appendix-enums.md#responsetype8).LongPress and [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) for bindContextMenu.


```

```TypeScript
### Example 6: Displaying a Menu with a Custom Preview on Long Press

This example demonstrates how to display a menu with a custom preview by setting [CustomBuilder](ts-types.md#custombuilder8) of the preview property in [responseType](ts-appendix-enums.md#responsetype8).LongPress and [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) for bindContextMenu.


```

```TypeScript
### Example 7: Using a State Variable for Menu Visibility

This example demonstrates how to use [bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu) with isShown to control the visibility of the menu.


```

```TypeScript
### Example 8: Using Custom Menu and Preview Animations

This example demonstrates how implement custom entrance and exit animations for the menu and preview by setting the transition property in [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) of bindContextMenu.


```

```TypeScript
### Example 9: Setting the Symbol Icon

This example shows how to display a menu with symbol icons by setting symbolIcon in [MenuElement](#menuelement) of bindMenu.


```

```TypeScript
### Example 10: Using Shared Element Transition

This example demonstrates how to implement a shared element transition effect from the component screenshot to the custom preview by setting hoverScale of the previewAnimationOptions property in [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) for bindContextMenu.


```

```TypeScript
### Example 11: Customizing the Background Blur Effect

This example demonstrates how to customize the blur background effect of a menu by setting the backgroundBlurStyleOptions property in [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) for bindMenu.

The backgroundBlurStyleOptions property is added to ContextMenuOptions since API version 18.


```

```TypeScript
### Example 12: Customizing the Background Effect

This example demonstrates how to customize the background effect of a menu by setting the backgroundEffect property in [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) for bindMenu.

The backgroundEffect property is added to ContextMenuOptions since API version 18.


```

```TypeScript
### Example 13: Configuring Lift-Finger Interruption for a Shared Element Transition

This example demonstrates how to implement a shared element transition by setting the previewAnimationOptions property in [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) for bindContextMenu and how to control whether lifting the finger after a long press can cancel the menu pop-up by setting hoverScaleInterruption.

From API version 20, the hoverScaleInterruption property is added to the [ContextMenuAnimationOptions](arkts-arkui-contextmenuanimationoptions-i.md) type of previewAnimationOptions.


```

```TypeScript
### Example 14: Setting the Radius of the Rounded Corners of the Preview Image Border

This example demonstrates how to implement the function using bindContextMenu with [responseType](ts-appendix-enums.md#responsetype8).LongPress set. In addition, the [MenuPreviewMode](arkts-arkui-menupreviewmode-e.md) type of the preview property in [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) is set to determine the menu preview mode. previewBorderRadius is set to implement the radius of the rounded corners of the preview image.

In API version 19, the previewBorderRadius property is added to [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md).


```

```TypeScript
### Example 15: Configuring Lifecycle Callbacks for bindMenu

This sample shows how to configure lifecycle callbacks for bindMenu11+.

From API version 20, the onWillAppear, onDidAppear, onWillDisappear, and onDidDisappear properties are added to [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md).
```

```TypeScript
### Example 16: Setting the Menu Mask

This example demonstrates how to implement the menu mask using bindMenu with the mask property.

In API version 20, the mask property is added to [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md).


```

```TypeScript
### Example 17: Setting the Outline Style of a Drop-Down Menu Using bindMenu

This example demonstrates how to set the outline style of the drop-down menu by setting the outlineWidth and outlineColor properties of bindMenu.

In API version 20, the outlineWidth and outlineColor properties are added to [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md).


```

```TypeScript
### Example 18: Passing a CustomBuilder with Parameters to bindMenu

This example demonstrates how to configure the properties of a menu by passing a CustomBuilder with parameters to bindMenu.


```

```TypeScript
### Example 19: Displaying Different Menus Based on the Trigger Mode

This example demonstrates how to bind a menu to the target component by passing CustomBuilderT<ResponseType> to [bindContextMenuWithResponse](arkts-arkui-commonmethod-c.md#bindcontextmenuwithresponse). The component returns the mode of triggering menu display in the UI function. You can implement differentiated display based on the returned trigger mode.

The bindContextMenuWithResponse API is added since API version 23.


```

```TypeScript
### Example 20: Setting the Menu to Avoid the Soft Keyboard

This example demonstrates how to configure the menu to avoid the soft keyboard by setting keyboardAvoidMode in bindMenu and set the minimum distance for avoiding the soft keyboard by setting minKeyboardAvoidDistance.

Starting from API version 23, the** keyboardAvoidMode** and minKeyboardAvoidDistance properties are added to [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md).
```

```TypeScript
### Example 21: Setting the Position of the Menu to Display Relative to the Upper Left Corner of the Bound Component

This example shows how to set the anchorPosition property in [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) to display the menu relative to the upper left corner of the bound component.

The anchorPosition property is added to ContextMenuOptions since API version 20.


```

```TypeScript
### Example 22: Setting the Maximum Height of a Menu

This sample shows how to use the maxHeight attribute in [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) to set the maximum height of a menu.

If the maxHeight attribute is not set, the maximum height of the menu is 80% of the available height by default, and all list items can be displayed. If the maxHeight attribute is set to 50% of the available height, only eight list items can be displayed.

The maxHeight attribute is added to ContextMenuOptions as of API version 26.0.0.


```

```TypeScript
### Example 23: Setting the Spacing Between the Menu and Target Component

This example describes how to increase the spacing between the menu and the target component by setting the targetSpace attribute in [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md).

The targetSpace attribute is added to ContextMenuOptions as of API version 26.0.0.
```

```TypeScript
### Example 24: Setting the System Material of a Menu

This example uses the systemMaterial attribute in [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) to set the system material of the component, thereby achieving the immersive light effect for the menu.

The immersive light effect of the component will be automatically adjusted based on the device computing power and the immersive light effect set by the user in the system. You do not need to perform additional adaptation.

The systemMaterial attribute is added to ContextMenuOptions as of API version 26.0.0.

Menu without system material

Menu with system material
```

```TypeScript
### Example 25: Setting a Grid Menu Using gridStyle

This example shows how to use gridStyle to set the grid menu style in [bindContextMenuByIsShow](arkts-arkui-commonmethod-c.md#bindcontextmenubyisshow). You can customize the grid layout of the menu by setting the count, horizontalSize, and position attributes.

In API version 26.0.0 and later, the [bindContextMenuByIsShow](arkts-arkui-commonmethod-c.md#bindcontextmenubyisshow) API is added, and the gridStyle attribute is added to [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md).
```

```TypeScript
### Example 1: Displaying Different Types of Popups

This example shows how to configure the keyboardAvoidMode attribute in [PopupOptions](#popupoptions) or [CustomPopupOptions](arkts-arkui-custompopupoptions-i.md) to determine whether the popup avoids the soft keyboard.

The keyboardAvoidMode attribute is added to PopupOptions and CustomPopupOptions since API version 15.


```

```TypeScript
### Example 2: Setting the Popup Text Style

In this example, the messageOptions attribute in [PopupOptions](#popupoptions) is configured to display a popup with a custom text style.


```

```TypeScript
### Example 3: Setting the Popup Style

This example sets the arrowHeight, arrowWidth, radius, shadow, and popupColor attributes in [PopupOptions](#popupoptions) to implement the style of the popup arrow and the popup itself.


```

```TypeScript
### Example 4: Setting the Popup Animation

This example shows how to configure the transition attribute in [PopupOptions](#popupoptions) or [CustomPopupOptions](arkts-arkui-custompopupoptions-i.md) to implement the entrance and exit animations on the popup.


```

```TypeScript
### Example 5: Adding an Event to a Popup

This example shows how to use the onWillDismiss attribute in [PopupOptions](#popupoptions) to intercept popup dismissal events and execute callback functions.


```

```TypeScript
### Example 6: Intercepting the Popup Dismissal Event

In this example, the onWillDismiss attribute in [PopupOptions](#popupoptions) is set to false, so that the popup does not respond to the exit event. In addition, you can set the followTransformOfTarget attribute of [PopupOptions](#popupoptions) to determine whether the popup follows the changes of the host component.


```

```TypeScript
### Example 7: Setting the Linear Gradient for the Inner and Outer Outlines of a Popup

This example configures the outlineWidth, borderWidth, outlineLinearGradient, and borderLinearGradient attributes in [PopupOptions](#popupoptions) to set the color and direction of the linear gradient of the inner and outer outlines of the popup.

The outlineWidth, borderWidth, outlineLinearGradient, and borderLinearGradient attributes are added to PopupOptions since API version 20.


```

```TypeScript
### Example 8: Setting the Mode for the Popup to Avoid the Bound Component

This example configures the avoidTarget attribute of [PopupOptions](#popupoptions) to enable the popup to avoid the bound component.

The avoidTarget attribute is added to PopupOptions since API version 20.


```

```TypeScript
### Example 9: Setting the System Material Effect of a Popup

This example implements the immersive light-sensing visual effect of a popup by using the systemMaterial attribute in [PopupOptions](#popupoptions) to set the system material of the component.

The immersive light-sensing effect of the component is automatically adjusted based on the device computing power and the immersive light-sensing effect set by the user in the system, so developers do not need to perform additional adaptation.

The systemMaterial attribute is added to PopupOptions as of API version 26.0.0.

Menu without system material



Menu with system material


```

```TypeScript
### Example 10: Customizing the Background Effect of a Popup

This example customizes the popup background effect by setting the backgroundBlurStyleOptions and backgroundEffect attributes of [PopupOptions](#popupoptions).

In API version 26.0.0 and later, the backgroundBlurStyleOptions and backgroundEffect attributes are added to PopupOptions.
```

```TypeScript
### Example 11: Setting the Display Level Mode of a Popup

This example configures the levelMode attribute of [PopupOptions](#popupoptions) to display a popup on the page. After the button is clicked, the page-level popup will not be displayed on the next route page.

From API version 26.0.0, the levelMode attribute is added to PopupOptions.
```

```TypeScript
PageTwo:
```

```TypeScript
### Example 1: Obtaining Touch Event Parameters

This example shows how to configure a touch event for a button. When the button is touched, it obtains relevant parameters of the event.


```

```TypeScript
### Example 2: Obtaining the Real-Time Position of a Component

This example uses the [getCurrentLocalPosition](#getcurrentlocalposition) method to obtain the coordinates of the touch position relative to the upper left corner of the current component's real-time position.

The getCurrentLocalPosition API is supported since API version 26.0.0.
```

```TypeScript
### Example 1: Setting Sheets with Different Heights

This example demonstrates how to set different heights for sheets using the height attribute.


```

```TypeScript
### Example 2: Setting Three Different Height Detents

This example demonstrates how to use the detents attribute of bindSheet to set three different height detents for a sheet.

The drag bar is effective only when there are multiple height detents.

Unlike the height attribute, which can set different heights at different times, the detents attribute provides a gesture to switch between detent heights and is more suitable for fixed height intervals.

If the height range is uncertain or there may be more than three different heights, avoid using the detents attribute.


```

```TypeScript
### Example 3: Setting the Border Width and Color

This example demonstrates how to use the borderWidth and borderColor attributes with LocalizedEdgeWidths and LocalizedEdgeColors types in bindSheet.

The following shows how the example is represented with left-to-right scripts.



The following shows how the example is represented with right-to-left scripts.


```

```TypeScript
### Example 4: Using Dismiss Callbacks

This example shows how to register onWillDismiss and onWillSpringBackWhenDismiss with bindSheet.


```

```TypeScript
### Example 5: Setting the Content Update Mode

ScrollSizeMode.CONTINUOUS continuously updates the content and is suitable for scenarios where detents switch between multiple heights.

Whenever possible, minimize UI loading time within the builder, as real-time content refreshing during scrolling has higher performance requirements.

When the sheet is dragged to switch between detents, the content height is refreshed only after the sheet is released.



When the sheet is dragged to switch between detents, the content height is refreshed in real time during the drag.


```

```TypeScript
### Example 6: Configuring the Sheet to Resize to Avoid the Keyboard

This example demonstrates how to adjust the scrollable content within a sheet when the keyboard height changes by setting SheetKeyboardAvoidMode to RESIZE_ONLY.


```

```TypeScript
### Example 7: Setting the Corner Radius in a Mirrored Layout

This example demonstrates how to set different corner radii for a sheet in a mirrored layout. Typically, to avoid a poor visual experience, do not set different values.

Since API version 15, the radius attribute supports the LocalizedBorderRadiuses type.

The following shows how the example is represented with left-to-right scripts.



The following shows how the example is represented with right-to-left scripts.


```

```TypeScript
### Example 8: Implementing a Side Sheet

This example demonstrates how to implement a side sheet. This feature is supported since API version 20.
```

```TypeScript
### Example 9: Implementing a Full-Screen Content Cover Sheet

This example demonstrates how to implement a full-screen sheet. This feature is supported since API version 20.


```

```TypeScript
### Example 10: Setting the System Material for a Half-Modal

This example sets the system material through the systemMaterial attribute of the half-modal.

Since API version 26.0.0, the [SheetOptions](arkts-arkui-sheetoptions-i.md) adds the systemMaterial attribute.
```

```TypeScript
### Example 1: Implementing Modal Transition Using bindContentCover

This example demonstrates how to implement a modal transition using the bindContentCover API.


```

```TypeScript
### Example 2: Implementing a Custom Transition Animation

This example applies a custom animation to two modals whose transition type is none.


```

```TypeScript
### Example 3: Implementing a Slide-up and Slide-down Transition Animation

This example shows two modals whose transition type is slide-up and slide-down animation.


```

```TypeScript
### Example 4: Implementing an Opacity Transition Animation

This example shows two modals whose transition type is opacity animation.


```

```TypeScript
### Example 5: Implementing Custom Transitions with Different Effects

This example mainly demonstrates custom transitions for full-screen modals, including rotation and translation effects.


```

```TypeScript
### Example 6: Setting a Full-Screen Modal to Adapt to the Safe Area

Starting from API version 20, this example mainly demonstrates the content effect when enableSafeArea is set to true to adapt the full-screen modal to the safe area. The background color of the full-screen modal container is light blue, the content color is gray, and the content is laid out within the safe area.
```

```TypeScript
### Example 1: Using the Same TransitionEffect Configuration for Image Appearance and Disappearance

This example primarily demonstrates how to use the same [TransitionEffect](arkts-arkui-transitioneffect-c.md) to achieve both the appearance and disappearance of an image, where the appearance and disappearance are inverse processes of each other.

Schematic diagram:
```

```TypeScript
### Example 2: Using Different TransitionEffect Configurations for Image Appearance and Disappearance

This example demonstrates how to use different [TransitionEffect](arkts-arkui-transitioneffect-c.md) configurations to implement the appearance and disappearance of an image.

Schematic diagram:
```

```TypeScript
### Example 3: Setting transition on Parent and Child Components

This example demonstrates how to configure [transition](#transition) on both parent and child components to implement the appearance and disappearance of images.

Schematic diagram:
```

```TypeScript
### Example 4: Dual-animation Composite Effect During Visibility Switching

This example demonstrates the dual-animation composite effect produced when [transition](#transition) animation is superimposed on layout animation as [visibility](ts-universal-attributes-visibility.md#visibility) switches between Visibility.Visible and Visibility.None.
```

```TypeScript
This example demonstrates how to set the motion path for the translation animation of a component. This method only configures the motion path parameters. To produce an actual translation animation effect, it must be used together with animation trigger methods such as animateTo and changes in component attribute states. Setting motionPath alone does not trigger an animation.
```

```TypeScript
This example demonstrates the click feedback effects on different types of components.
```

```TypeScript
### Example 1: Using Foreground Color Settings

This example demonstrates how to set the foreground color using foregroundColor.


```

```TypeScript
### Example 2: Setting the Foreground Color to Background Inverse

This example demonstrates how to set the foreground color to the inverse of the background color using [ColoringStrategy](ts-appendix-enums.md#coloringstrategy10).INVERT.


```

```TypeScript
### Example 3: Implementing a Foreground Color Not Inherited from the Parent Component

This example compares the effects of setting both foreground and background colors on a component versus setting only the background color.
```

```TypeScript
### Example 1: Setting Accessibility Text and Description

This example demonstrates how to use accessibilityText and accessibilityDescription to customize the content announced by screen readers.
```

```TypeScript
### Example 2: Setting the Accessibility Group

This example shows how to prioritize reading the accessibility text of child components.
```

```TypeScript
### Example 3: Setting the Initial Focus and the Next Focus of a Component

This example demonstrates the use of accessibilityDefaultFocus to set the default initial focus for the screen reader on the current page and accessibilityNextFocusId to set the next focus for components during focus traversal.
```

```TypeScript
### Example 4: Setting the Accessibility Component Type and Text Hint

This example demonstrates the use of accessibilityRole to set the accessibility component type and accessibilityTextHint to provide text hints for components that can be queried by assistive technologies.
```

```TypeScript
### Example 5: Configuring Screen Reader Scrolling, Focus Highlight Frame, and Cross-Process Focus

This example demonstrates how to use accessibilityScrollTriggerable to set whether the accessibility node supports Screen Reader scrolling, accessibilityFocusDrawLevel to set the drawing level of the accessibility focus green frame, and accessibilityUseSamePage to set the same-page mode for components displayed across processes in embedded mode (such as [EmbeddedComponent](ts-container-embedded-component.md)).


```

```TypeScript
### Example 6: Configuring Child Component State and Action Handlers in Accessibility Aggregation Mode

This example demonstrates how to use the optional parameters stateControllerRoleType or stateControllerId in accessibilityGroup to delegate accessibility state information to specific child components, and actionControllerRoleType or actionControllerId to delegate accessibility control operations to specific child components.
```

```TypeScript
### Example 7: Setting the State Announcement for the Accessibility Component

This example uses the [accessibilityStateDescription](#accessibilitystatedescription23) API to modify the Status Announcement of a component. After the accessibility feature is enabled, when the component is focused or clicked, the Screen Reader announces the state information of the component.

The accessibilityStateDescription API is available since API version 23.
```

```TypeScript
### Example 8: Setting the Accessibility Action Options to Modify the Component Scrolling Step

This example demonstrates how to customize the scrolling step of a component by using the scrollStep parameter in [accessibilityActionOptions](ts-types.md#accessibilityactionoptions23). The following uses a sliding distance change of the Slider component in screen reading scenarios.

AccessibilityActionOptions is available since API version 23.
```

```TypeScript
### Example 9 (Set Custom Accessibility Actions)

This example demonstrates how to use [accessibilityCustomActions](arkts-arkui-commonmethod-c.md#accessibilitycustomactions) to set custom accessibility actions for a component. Developers can bind callbacks for custom actions by action name.

Since API version 26.0.0, accessibilityCustomActions is added.
```

```TypeScript
This example demonstrates how to use the id APIs to obtain attributes of a component with the specified by ID and trigger events on that component.
```

```TypeScript
This example demonstrates how to use reuseId to identify the reuse group of a custom component.
```

```TypeScript
This example demonstrates how to obscure the content of Text and Image components using the obscured API.
```

```TypeScript
This example shows how to set up a flex layout through the flexBasis, flexGrow, flexShrink, and alignSelf attributes.
```

```TypeScript
### Example 1: Obtaining Click Event Parameters

This example configures a click event [ClickEvent](arkts-arkui-clickevent-i.md) for a button. When the button is clicked, the relevant parameters of the click event can be obtained.


```

```TypeScript
### Example 2: Obtaining the Real-Time Position of a Component

This example uses the [getCurrentLocalPosition](#getcurrentlocalposition) method to obtain the coordinates of the upper-left corner of the current component based on its real-time position.

The getCurrentLocalPosition API is supported since API version 26.0.0.
```

```TypeScript
### Example 1: Using OnMove for Drag Sorting in List

This example demonstrates how to use onMove for drag and drop with ForEach in a List component.
```

```TypeScript
### Example 2: Using OnMove for Drag Sorting in List and Setting Drag Event Callback

This example demonstrates how to use onMove with additional drag event callbacks in a List component containing ForEach, available since API version 20.
```

```TypeScript
### Example 3: Using ForEach onMove for Drag Sorting in a Grid with Regular Layout and Setting the Drag Event Callback

Supported since API version 26.0.0, the following example shows the callback event triggered after the Grid component sets the drag effect for ForEach. All GridItems in the Grid are regular.


```

```TypeScript
### Example 4: Using ForEach onMove for Drag Sorting in Grid Irregular Layout and Setting the Drag Event Callback

Since API version 26.0.0, the following example shows the callback event triggered after the Grid component sets the drag effect for ForEach, where the Grid contains irregular GridItems. The application can use [irregularIndexes](ts-container-grid.md#gridlayoutoptions10) to set which indexes are irregular nodes, and adjust the number of rows and columns occupied by the GridItem by modifying the rectSize of the corresponding index.


```

```TypeScript
### Example 5: Using LazyForEach onMove for Drag Sorting in Grid Irregular Layout and Setting the Drag Event Callback

Starting from API version 26.0.0, the following example demonstrates the callback event triggered after the drag effect is set for the Grid component using LazyForEach, where the Grid contains irregular GridItems. The application can use irregularIndexes to set which indexes are irregular nodes, and adjust the number of rows and columns occupied by the GridItem by modifying the rectSize of the corresponding index.
```

```TypeScript

```

```TypeScript
### Example 6: Using Repeat's onMove for Drag Sorting in Grid Irregular Layout and Setting the Drag Event Callback

Supported since API version 26.0.0, the example below shows the callback event triggered after Repeat sets the drag effect in the Grid component, where the Grid contains irregular GridItems. The application can use irregularIndexes to set which indexes are irregular nodes, and adjust the number of rows and columns occupied by the GridItem by modifying the rectSize of the corresponding index.
```

```TypeScript
This example demonstrates the merging of drawing for background blur and other effects.
```

```TypeScript
This example sets the component size change event on the Text component. When the Text size changes, the onSizeChange event is triggered to obtain the oldValue and newValue parameters.
```

```TypeScript
This example demonstrates how to use [animateToImmediately](#animatetoimmediately) to implement the immediate delivery of explicit animations.
```

```TypeScript
This example demonstrates how to create a custom check box using ContentModifier. This check box comes in the custom pentagon style instead of the original check box style. When selected, the check box shows a red triangle pattern inside, and the title displays the word "selected"; when deselected, the check box hides the red triangle pattern inside, and the title displays the word "unselected."
```

```TypeScript
### Example 1: Setting the Brightness Effect

This example demonstrates how to add a brightness effect to a component using advancedBlendMode.

Below is how the component looks with the brightness effect applied:


```

```TypeScript
### Example 2: Setting the Render Group Exclusion Attribute

This example demonstrates how to use the [excludeFromRenderGroup](arkts-arkui-commonmethod-c-sys.md#excludefromrendergroup) to avoid repeated invalidations of the render group cache in scenarios involving attribute animations on the component.

The [excludeFromRenderGroup](arkts-arkui-commonmethod-c-sys.md#excludefromrendergroup) attribute is supported since API version 22.


```

```TypeScript
### Example 3: Setting the Brightening and Fade-Out Effects

Since API version 23, this example demonstrates how to use advancedBlendMode to add both the brightening and fade-out effects to a component.


```

```TypeScript
### Example 4: Setting Component Edge Light Effect

This example demonstrates how to add an edge glow effect to a component through [edgeLight](#edgelight).

Since API version 26.0.0, the edgeLight method is added.
```

```TypeScript
This example demonstrates how to set a keyframe animation through keyframeAnimateTo, including the delay, the onFinish completion callback, and the curve configuration of each keyframe.
```

```TypeScript
This example demonstrates how to use the visibility configuration to achieve different visibility control effects.
```

```TypeScript
### Example 1: Implementing Custom Gesture Judgment

In this example, the [onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin) event is configured to implement customized judgment of the press and hold, fast swipe, swipe, pinch, and drag gestures. From API version 21, the [BaseEvent](ts-universal-events-click.md#baseevent8) axisPinch attribute can be used to obtain the two-finger zoom ratio.


```

```TypeScript
### Example 2: Implementing Custom Area Gesture Judgment

This example uses onGestureJudgeBegin to determine whether to respond to the press and hold gesture and drag gesture based on the area where the gesture is triggered.


```

```TypeScript
### Example 3: Implementing Real-time Monitoring of Active Touch Points in Gestures

This example configures the onGestureJudgeBegin callback to read fingerInfos to detect the number of valid touch points, ID of each touch point, and coordinates of each touch point in real time.
```

```TypeScript
### Example 1: Setting the Event Dispatch Strategy to FORWARD_COMPETITION

In this example, click the blank area below the List and drag to make the List scroll. When the Button is pressed, the Button responds to the onClick event.


```

```TypeScript
### Example 2: Setting the Event Dispatch Strategy to FORWARD

In this example, clicking and dragging in the blank area below the List component causes the List component to scroll. The Button component does not respond to onClick events.


```

```TypeScript
### Example 3: Setting the Event Dispatch Strategy to DEFAULT

In this example, clicking and dragging in the blank area below the List component does not cause the List component to scroll. The Button component still responds to onClick events.
```

```TypeScript
### Example 1: Switching the Background Color with a Modifier

This example demonstrates how to switch the background color of a Button component by binding it to a modifier.


```

```TypeScript
### Example 2: Implementing the Pressed State Effect with a Modifier

This example implements the pressed state effect by binding a modifier to a Button. For details about using it with state management V2, see [Modifier and makeObserved](../../../ui/state-management/arkts-v1-v2-migration-inner-object.md#modifier).


```

```TypeScript
### Example 3: Understanding Custom Modifiers Do Not Support State Data Changes

This example shows how to set the width of a custom modifier using state data. Custom modifiers do not support observing changes in data decorated with the @State decorator. Therefore, the width does not change when the button is clicked.


```

```TypeScript
### Example 4: Combining Modifier and Custom Modifier Attributes

This example sets width, height, and margin through a custom modifier. When the button is clicked, [borderStyle](ts-appendix-enums.md#borderstyle) and [borderWidth](ts-universal-attributes-border.md#borderwidth) are set. After the click, all five attributes take effect.


```

```TypeScript
### Example 5: Setting the Focused State Style with a Modifier

This example demonstrates how to implement a focused state style for a Button component by binding it to a modifier. After Button2 is clicked, the Button component displays the focused style when it has focus.


```

```TypeScript
### Example 6: Setting the Disabled State Style with a Modifier

This example demonstrates how to implement a disabled state style for a Button component by binding it to a modifier. After Button2 is clicked, the Button component displays the disabled style when it is disabled.


```

```TypeScript
### Example 7: Setting the Selected State Style with a Modifier

This example implements the style effect when a component is selected by binding a modifier to a Radio.


```

```TypeScript
### Example 8: Implementing the Pressed State Effect for a Custom Component with a Modifier

This example demonstrates how to implement a pressed state effect for a custom component (Common) by binding it to a modifier.


```

```TypeScript
### Example 9: Implementing the Mouse Hover Effect with a Modifier

This example implements the mouse hover effect by binding a modifier to aButton. When the mouse moves over the Button, the background color of the Button changes to red, which is the hover effect; when the mouse leaves the Button, the background color changes to black, which is the normal state effect. The hover style is set through the [applyHoveredAttribute](arkts-arkui-attributemodifier-i.md#applyhoveredattribute) API.

Since API version 26.0.0, the [applyHoveredAttribute](arkts-arkui-attributemodifier-i.md#applyhoveredattribute) API is added.
```

```TypeScript
### Example 1: Setting the Follow-Hand Morph Drag Animation

This example sets [dragAnimationType](#attributes) to FOLLOW_HAND_MORPH to implement the follow-hand morph drag animation effect, and executes a custom drop animation through [executeFollowHandMorphDropAnimation](arkts-arkui-dragevent-i-sys.md#executefollowhandmorphdropanimation) when the drag ends.

Since API version 26.0.0, the [dragAnimationType](#attributes) attribute, the [executeFollowHandMorphDropAnimation](arkts-arkui-dragevent-i-sys.md#executefollowhandmorphdropanimation) method, and the [interruptFollowHandMorphDropAnimation](../arkts-apis/arkts-arkui-arkui-uicontext-dragcontroller-c-sys.md#interruptfollowhandmorphdropanimation) method are added.
```

```TypeScript
### Example 1: Setting Focus and Focus Traversal Effects for Components

This example shows how to use [defaultFocus](#defaultfocus9), [groupDefaultFocus](arkts-arkui-commonmethod-c.md#groupdefaultfocus), and [focusOnTouch](arkts-arkui-commonmethod-c.md#focusontouch). defaultFocus sets the bound component as the initial focus after the [hierarchical page](../../../ui/arkts-common-events-focus-event.md#basic-concepts) is created. groupDefaultFocus sets the bound component as the initial focus after the container with the specified tabIndex is created. focusOnTouch sets the bound component to obtain focus upon being clicked.

Diagrams:

On first-time access, the focus is on the TextInput component bound to defaultFocus.



When the Tab key is pressed for the first time, the focus switches to the container with tabIndex(1), and automatically navigates to the first focusable component inside it:



When the Tab key is pressed for the second time, the focus switches to the container with tabIndex(2), and automatically navigates to the component bound to groupDefaultFocus inside it:



When the Tab key is pressed for the third time, the focus switches to the container with tabIndex(3), and automatically navigates to the component configured with defaultFocus inside it:



Tap the component bound to focusOnTouch, the component itself gains focus, the focus box is cleared, and after pressing the Tab key again, the focus box is displayed:


```

```TypeScript
### Example 2: Setting Focus on a Specific Component

This example demonstrates how to set focus on a specific component using [focusControl.requestFocus](#requestfocus9).

Diagrams:

Press the Tab key to activate the focus state display.

Below shows how the UI behaves when you request focus for a component that does not exist.



Below shows how the UI behaves when you request focus for a component that is not focusable.



Below shows how the UI behaves when you request focus for a focusable component.


```

```TypeScript
### Example 3: Customizing the Focus Box Style

This example shows how to change the focus box style of a component by configuring [focusBox](#focusbox12).


```

```TypeScript
### Example 4: Setting Focus Group Traversal

This example demonstrates how to set a component as the initial focus when its container gains focus by configuring [focusScopePriority](arkts-arkui-commonmethod-c.md#focusscopepriority). Configuring [focusScopeId](arkts-arkui-commonmethod-c.md#focusscopeid) allows the bound container component to become a focus group.

Diagrams:

When the Tab key is pressed for the first time, the focus transfers to the component bound to focusScopePriority in container 1.



Continue pressing the Tab key, and the focus transfers to the next component in container 1.



Press the Tab key again, and the focus transfers to the next component in container 1.



Continue pressing the Tab key, and the focus transfers to the component configured with focusScopePriority in container 2.



Continue pressing the Tab key, and the focus transfers to the component named Group1 in container 1.


```

```TypeScript
### Example 5: Setting Tab Focus Stay

This example implements Tab key focus stay on a component by configuring [tabStop](arkts-arkui-commonmethod-c.md#tabstop).

Diagrams:

Press the Tab key twice consecutively, and the focus transfers to button2.



Then press the Tab key, and the focus transfers to the component configured with tabStop.



Pressing Enter moves the focus to button3.



Pressing ESC again moves the focus to the component configured with tabStop.



Press the Tab key again, and the focus cycles back to button1.


```

```TypeScript
### Example 6: Setting Custom Focus Movement

This example demonstrates how to implement custom focus movement logic using the [nextFocus](arkts-arkui-commonmethod-c.md#nextfocus) API, available since API version 18.

If [nextFocus](arkts-arkui-commonmethod-c.md#nextfocus) is not configured, the default focus navigation order when pressing the Tab key is: M->A->B->C->D->E->F. After [nextFocus](arkts-arkui-commonmethod-c.md#nextfocus) is configured, the focus navigation order changes to: M->D->F->B->C.
```

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State isShow: boolean = false;

  build() {
    Stack({ alignContent: Alignment.Center }) {
      if (this.isShow) {
        // Customize the image resource path as needed.
        Image($r('app.media.pic'))
          .autoResize(false)
          .clip(true)
          .width(300)
          .height(400)
          .offset({ y: 100 })
          .geometryTransition('picture', { follow: false })
          .transition(TransitionEffect.OPACITY)
      } else {
        // geometryTransition is bound to a container. Therefore, a relative layout must be configured for the child components of the container.
        // The multiple levels of containers here are used to demonstrate passing of relative layout constraints.
        Column() {
          Column() {
            // Customize the image resource path as needed.
            Image($r('app.media.icon'))
              .width('100%').height('100%')
          }.width('100%').height('100%')
        }
        .width(80)
        .height(80)
        // geometryTransition synchronizes corner radius settings, but only for the bound component, which is the container in this example.
        // In other words, corner radius settings of the container are synchronized, and those of the child components are not.
        .borderRadius(20)
        .clip(true)
        .geometryTransition('picture')
        // transition ensures that the component is not destructed immediately when it exits. You can customize the transition effect.
        .transition(TransitionEffect.OPACITY)
      }
    }
    .onClick(() => {
      this.getUIContext().animateTo({ duration: 1000 }, () => {
        this.isShow = !this.isShow;
      });
    })
  }
}
```

```TypeScript
### Example 1: Adding Graphical Transformation Effects

This example applies rotation, translation, scaling, and transformation matrix effects to the component using [rotate](#rotate), [translate](#translate), [scale](#scale), and [transform](#transform).


```

```TypeScript
### Example 2: Setting the Rotation Perspective

This example demonstrates how to set the rotation perspective for a component by using [perspective](#rotateoptions).


```

```TypeScript
### Example 3: Implementing Rotation Around a Center Point

This example shows how to achieve the same rotation effect by setting different parameters for [rotate](#rotate) and [transform](#transform).


```

```TypeScript
### Example 4: Implementing Graphical Transformation Through transform3D

This example demonstrates how to implement image transformation by setting [transform3D](arkts-arkui-commonmethod-c.md#transform3d). This functionality is supported since API version 20.


```

```TypeScript
### Example 5: Rotating an Image Based on Angles of Each Axis

This example demonstrates how to implement rotation by setting the [RotateAngleOptions](arkts-arkui-rotateangleoptions-i.md) parameter of rotate. This functionality is supported since API version 20.
```

```TypeScript
### Example 1: Creating an Appearance Animation for a Component

> NOTE
> 
> Directly using animateTo can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the [UIContext](../arkts-apis-uicontext-uicontext.md) object using the getUIContext() API and then call animateTo bound to the instance using the [animateTo](../arkts-apis-uicontext-uicontext.md#animateto) API.

This example demonstrates how to create an appearance animation for a component using the onAppear method.


```

```TypeScript
### Example 2: Enabling Component Disappearance After Animation Completion

This example demonstrates how to make a component disappear after the animation ends.
```

```TypeScript
### Example 1: Setting Basic Styles

This example shows how to set the border width, color, border radius, and styles such as dotted or dashed lines.


```

```TypeScript
### Example 2: Border Width, Corner Radius, and Color Types

The width, radius, and color attribute values of the border attribute use the LocalizedEdgeWidths, LocalizedBorderRadiuses, and LocalizedEdgeColors types, respectively.

Example image for left-to-right (LTR) display languages



Example image for right-to-left (RTL) display languages


```

```TypeScript
### Example 3: Configuring Offscreen Rounded Corners

This example demonstrates how to set the rendering strategy for drawing rounded corners on components, supported since API version 22.

The fast rendering mode (RenderStrategy.FAST) performs real-time rendering through GPU hardware acceleration and is suitable for common corner radius scenarios. The offscreen rendering mode (RenderStrategy.OFFSCREEN) first draws the component to an offscreen buffer and then composites it, which is suitable for corner radius scenarios involving complex content such as blur and scrolling, and can avoid corner radius clipping anomalies. The following illustration compares the online rendering mode (top) with the offscreen rendering mode (bottom):


```

```TypeScript
### Example 4: Setting Irregular Corner Radii

This example uses [borderRadius](#borderradius) to set four different corner radius values. When one of the corner radius values exceeds half of the smaller value of the height or width, the irregular corner radius is drawn by value ratio.
```

```TypeScript
### Example 1: Setting the Alignment Mode and Main Axis Layout

Sets the alignment mode of the content within the element and the layout of child elements along the main axis of the parent component.


```

```TypeScript
### Example 2: Setting the Position Offset

This example demonstrates position offsets based on the parent component, relative positioning, and anchors.


```

```TypeScript
### Example 3: Setting the Absolute Positioning and Relative Offset

This example demonstrates how to use position to set absolute positioning, which determines the position of child components relative to the parent component. It also shows how to use offset to set relative offsets for moving components from their original layout positions.


```

```TypeScript
### Example 4: Implementing a Mirror Effect

Common layout attributes support the [mirroring capability](./../../../ui/arkts-internationalization.md#using-the-mirroring-capability). This example demonstrates how to implement a mirroring effect using the [position](#position), [offset](#offset), and [markAnchor](#markanchor) attributes. The light blue blocks indicate the original effect, and the dark blue blocks indicate the mirroring effect.

Before mirroring:



After mirroring (For details about the conditions for mirroring to take effect, see [Using the Mirroring Capability](./../../../ui/arkts-internationalization.md#using-the-mirroring-capability)):


```

```TypeScript
### Example 5: Using the align Property with Mirroring Adaptation

Sets the alignment mode of the content within the element and the layout of child elements along the main axis of the parent component.


```

```TypeScript
### Example 6: Using layoutGravity to Individually Set the Alignment Rule of a Child Component in the Stack Component

This example shows how to adjust the text position within the Stack container.
```

```TypeScript
The sample code implements the custom transition animation of a shared element image when a click on the image area triggers page redirection.
```

```TypeScript
// PageB.ets
@Entry
@Component
struct PageBExample {
  build() {
    Stack() {
      // Replace $r('app.media.ic_health_heart') with the image resource file you use.
      Image($r('app.media.ic_health_heart')).width(150).height(150)
        .sharedTransition('sharedImage', { duration: 800, curve: Curve.Linear, delay: 100 })
    }.width('100%').height('100%')
  }

  pageTransition() {
    PageTransitionEnter({ type: RouteType.None, duration: 0 })
    PageTransitionExit({ type: RouteType.None, duration: 0 })
  }
}
```

```TypeScript
### Example 1: Setting Basic Background Styles

This example shows how to configure basic background styles by setting backgroundColor, backgroundImage, backgroundImageSize, and backgroundImagePosition.


```

```TypeScript
### Example 2: Setting the Background Blur Style

This example sets the background blur style using backgroundBlurStyle.


```

```TypeScript
### Example 3: Setting the Component Background

This example shows how to set the component background using background.


```

```TypeScript
### Example 4: Setting Component Background Brightness

This example sets the component background brightness using backgroundBrightness.

The following figures show how the component looks with the background brightness set.

When rate and lightUpDegree are both set to 0.5



When rate is set to 0.5 and lightUpDegree -0.1



The following figure shows how the component looks without the background brightness set.


```

```TypeScript
### Example 5: Setting Blur Effects

This example shows how to use blur to apply a foreground blur effect and backdropBlur to apply a background blur effect.


```

```TypeScript
### Example 6: Setting Text Blur Effects

This example uses [blendMode](ts-universal-attributes-image-effect.md#blendmode11) and backgroundEffect to implement an irregular text blur effect.If line leakage occurs, developers should first ensure that the components where the two blendMode attributes are set have exactly the same size. If the sizes are confirmed to be the same, the component boundary may fall on floating-point coordinates. In this case, try setting the [pixelRound](ts-universal-attributes-pixelRoundForComponent.md#pixelround) universal attribute to align the component boundaries on both sides of the generated white or dark lines to integer pixel coordinates.
```

```TypeScript
### Example 7: Comparing Blur Effects

This example compares three different blur effects: [backgroundEffect11+](#backgroundeffect11), [backdropBlur](arkts-arkui-commonmethod-c.md#backdropblur), and [backgroundBlurStyle9+](#backgroundblurstyle9).


```

```TypeScript
### Example 8: Applying a P3 Color Gamut Background Effect

This example demonstrates how to apply a P3 color gamut background effect using [backgroundColor](#backgroundcolor20), available since API version 20.


```

```TypeScript
### Example 9: Setting Component Background Extension

This example shows how to use [background](#background10) to extend the component's background to the parent component's safe area, supported since API version 20.
```

```TypeScript
### Example 1: Implementing Custom Drawing Through DrawModifier

This example demonstrates how to implement custom drawing for the [Text](ts-basic-components-text.md) component through DrawModifier.


```

```TypeScript
### Example 2: Implementing Custom Foreground Drawing for a Container Through DrawModifier

This example demonstrates how to implement custom foreground drawing for a [Column](ts-container-column.md) container using DrawModifier.
```

```TypeScript
This example uses enabled to set whether a button is interactive.
```

```TypeScript
This example demonstrates how to apply a motion blur effect.
```

```TypeScript
This example registers a crown event for a component and reports the received crown event data.
```

```TypeScript
// xxx.ets
@Entry
@Component
struct Example {
  build() {
    Column() {
      Flex({ wrap: FlexWrap.Wrap }) {
        Column() {
          Text('width(220)')
            .width(220)
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("width('220px')")
            .width('220px')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
        }.margin(5)

        Column() {
          Text("width('220vp')")
            .width('220vp')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("width('220lpx') designWidth:720")
            .width('220lpx')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("width(getUIContext().vp2px(220) + 'px')")
            .width(this.getUIContext().vp2px(220) + 'px')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("fontSize('12fp')")
            .width(220)
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12fp')
        }.margin(5)

        Column() {
          Text('width(px2vp(220))')
            .width(this.getUIContext().px2vp(220))
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12fp')
        }.margin(5)
      }.width('100%')
    }
  }
}
```

```TypeScript
This example shows how to use pixelRound to guide layout adjustments when there is a 1 px gap in the parent component.
```

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State lightIntensity: number = 0;
  @State bloomValue: number = 0;

  build() {
    Row({ space: 20 }) {
      Flex()
        .pointLight({ illuminated: IlluminatedType.BORDER })
        .backgroundColor(0x307af7)
        .size({ width: 50, height: 50 })
        .borderRadius(25)

      Flex()
        .pointLight({
          lightSource: {
            intensity: this.lightIntensity,
            positionX: '50%',
            positionY: '50%',
            positionZ: 80
          },
          bloom: this.bloomValue
        })
        .animation({ duration: 333 })
        .backgroundColor(0x307af7)
        .size({ width: 50, height: 50 })
        .borderRadius(25)
        .onTouch((event: TouchEvent) => {
          // Enhance the light source intensity and luminous intensity when pressed, and restore the default effect when released or canceled.
          if (event.type === TouchType.Down) {
            this.lightIntensity = 1;
            this.bloomValue = 1;
          } else if (event.type === TouchType.Up || event.type === TouchType.Cancel) {
            this.lightIntensity = 0;
            this.bloomValue = 0;
          }
        })

      Flex()
        .pointLight({ illuminated: IlluminatedType.BORDER_CONTENT })
        .backgroundColor(0x307af7)
        .size({ width: 50, height: 50 })
        .borderRadius(25)
    }
    .justifyContent(FlexAlign.Center)
    .backgroundColor(Color.Black)
    .size({ width: '100%', height: '100%' })
  }
}
```

```TypeScript
### Example 1: Implementing Nested Scrolling

This example demonstrates how to implement nested scrolling using shouldBuiltInRecognizerParallelWith and onGestureRecognizerJudgeBegin. The inner component takes precedence in responding to swipe gestures. When the inner component reaches the top or bottom, the outer component can then take over the scrolling.


```

```TypeScript
### Example 2: Blocking Inner Container Gestures in Nested Scrolling

This example demonstrates how to set the exposeInnerGesture parameter to true to enable a first-level Tabs container to intercept the swipe gestures of a nested second-level Tabs container, thereby triggering the swipe gestures of the built-in Swiper component of the first-level Tabs container.

You can define variables to record the index of the inner Tabs container and use this index to determine whether the swipe has reached the boundary of the inner Tabs container. When the boundary is reached, the callback is triggered to return a rejection result, blocking the swipe gesture of the inner Tabs container so that the outer Tabs container generates the swipe gesture.


```

```TypeScript
### Example 3: Blocking Gestures to Obtain Properties

This example configures onGestureRecognizerJudgeBegin to recognize gestures and obtain property parameters such as the gesture distance, number of fingers, whether to limit the number of fingers, repeated trigger state, duration, number of taps, rotation angle, swipe direction, and speed threshold.


```

```TypeScript
### Example 4: Canceling Child Component Touch Events on Successful Gesture Trigger

This example demonstrates how to use onGestureRecognizerJudgeBegin to implement gesture recognition. When the parent container's gesture is successfully triggered, it calls cancelTouch() to forcibly cancel touch events on child components, enabling precise switching between parent and child gesture control.


```

```TypeScript
### Example 5: Customizing Gesture Recognizer Participation in Gesture Processing

This example demonstrates how to use [onTouchTestDone](arkts-arkui-commonmethod-c.md#ontouchtestdone) to exclude a gesture recognizer from subsequent gesture processing, available from API version 20. When the callback is triggered, [preventBegin](./ts-gesture-common.md#preventbegin20) is called to prevent the recognizer from participating in further processing. Tapping the overlapping area of Tap2 and Tap1, if preventBegin is not called, triggers the gesture corresponding to Tap2. If preventBegin is called to block Tap2, the gesture corresponding to Tap1 is triggered.


```

```TypeScript
### Example 6: Customizing the Collection Results of Events and Gestures

This example configures [onGestureCollectIntercept](arkts-arkui-commonmethod-c.md#ongesturecollectintercept) to specify whether a gesture recognizer or touch recognizer is passed through to other nodes. When button2 is tapped, the touch event is not passed through to Column. When button1 is tapped, the touch event is passed through to Column, and Column changes color.

The onGestureCollectIntercept API is added since API version 26.0.0.
```

```TypeScript


The component tree corresponding to the example is shown in the following figure.
```

```TypeScript
### Example 7: Nested Scrolling with Non-Built-in Gestures

This example implements nested scrolling using [shouldRecognizerParallelWith](arkts-arkui-commonmethod-c.md#shouldrecognizerparallelwith) and [onGestureRecognizerJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturerecognizerjudgebegin). The inner component takes precedence in responding to the swipe gesture. When the inner component scrolls to the top or bottom, the outer component can take over the scrolling.

The shouldRecognizerParallelWith API is added since API version 26.0.0.
```

```TypeScript
### Example 1: Enabling the Keyboard Continuation

In this example, the [onNeedSoftkeyboard](arkts-arkui-commonmethod-c.md#onneedsoftkeyboard) API is used to enable the keyboard continuation for a button. After the keyboard is started by the text box, switch the focus to the button upon a tap. In this case, the keyboard will not collapse. Tap the text box again to continue entering text.

The [onNeedSoftkeyboard](arkts-arkui-commonmethod-c.md#onneedsoftkeyboard) API is available since API version 24.
```

```TypeScript
### Example 1: Using the Automatic Memory Optimization Strategy

In the following example, the reusable custom component ReusableComponent uses the automatic memory optimization strategy through the memoryOptimizationStrategy attribute of [ReusableOptions](arkts-arkui-reusableoptions-i.md). Click the Recycle button to trigger the recycling of the ReusableComponent component. Then, when the app goes to the background, the reuse pool cache is released.

The ReusableOptions API is added since API version 26.0.0.
```

```TypeScript
### Example 1: Allowing Drag and Drop

This example demonstrates how to use [allowDrop](arkts-arkui-commonmethod-c.md#allowdrop) to configure component drop targets and [draggable](#draggable) to enable component dragging.


```

```TypeScript
### Example 2: Setting the Drag Preview

This example demonstrates how to configure the preview displayed during the drag process using [dragPreview](#dragpreview11).


```

```TypeScript
### Example 3: Setting the Drag Preview Style

This example demonstrates how to configure the drag preview style using [dragPreviewOptions](#dragpreviewoptions11). Set ENABLE_DEFAULT_SHADOW and ENABLE_DEFAULT_RADIUS for default shadow and unified rounded corner effects. Starting from API version 18, set [dragPreviewOptions](#dragpreviewoptions11) to ENABLE_DRAG_ITEM_GRAY_EFFECT to enable grayscale effects on the original drag item.


```

```TypeScript
### Example 4: Enabling the Multi-select Drag Functionality

This example demonstrates how to configure [isMultiSelectionEnabled](arkts-arkui-draginteractionoptions-i.md) to enable the multi-select drag functionality in the Grid component.


```

```TypeScript
### Example 5: Enabling the Default Pressed State Animation

This example demonstrates configuring [defaultAnimationBeforeLifting](arkts-arkui-draginteractionoptions-i.md) to enable the default press animation effect in the Grid component.


```

```TypeScript
### Example 6: Customizing the Preview Style

This example demonstrates customizing the Image component background by configuring [ImageModifier](arkts-arkui-imagemodifier-t.md).


```

```TypeScript
### Example 7: Configuring Image Dragging Settings

This example demonstrates drag configuration for different image types (online resources, local resources, and PixelMap).

The ohos.permission.INTERNET permission is required for using online images. For details about how to apply for a permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).


```

```TypeScript
### Example 8: Enabling Haptic Feedback for Dragging

This example demonstrates enabling haptic feedback during image drag operations by configuring [enableHapticFeedback](arkts-arkui-draginteractionoptions-i.md), supported since API version 18.
```

```TypeScript
### Example 9: Customizing the Drag Preview

Starting from API version 15, this example configures [onlyForLifting](./ts-universal-events-drag-drop.md#previewconfiguration15) to create a custom preview image exclusively for the lift animation effect, and [isLiftingDisabled](arkts-arkui-draginteractionoptions-i.md) to disable the lift animation effect.

Custom preview for the lifting effect only



Custom preview with the lifting effect disabled


```

```TypeScript
### Example 10: Implementing Touch Point Calculation Based on Initial Drag Preview Size

Since API version 19, Example 10 implements the calculation of the follow-finger point position during the drag process based on the original size of the final drag preview image by configuring [DragPreviewMode](arkts-arkui-draginteractionoptions-i.md) to ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW. When [DragPreviewMode](arkts-arkui-dragpreviewmode-e.md) is set to ENABLE_MULTI_TILE_EFFECT, this attribute does not take effect.


```

```TypeScript
### Example 11: Implementing Transition Effects Between Floating Images and Drag Previews

This example demonstrates how to implement different transition effects between floating images and drag previews by configuring [DraggingSizeChangeEffect](arkts-arkui-draggingsizechangeeffect-e.md), supported since API version 19.


```

```TypeScript
### Example 12: Setting Dropping of a Custom Component

In API version 23 and later, this example demonstrates how to implement the drag-and-drop function for a custom component by passing a type through the component's [onDragStart](ts-universal-events-drag-drop.md#ondragstart) API and setting the target component's [allowDrop](arkts-arkui-commonmethod-c.md#allowdrop) attribute to allow dropping of that type.


```

```TypeScript
### Example 13: Setting the Material Effect of the Drag Backdrop Image

This example sets the material effect of the drag backdrop by configuring the [systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial) attribute in [allowDrop](arkts-arkui-commonmethod-c.md#allowdrop).

Since API version 26.0.0, the modifier parameter in the [DragPreviewOptions](arkts-arkui-imagemodifier-t.md) interface additionally supports the [systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial) attribute.
```

```TypeScript
### Example 1: Implementing a Custom Layout

This example demonstrates how to implement a custom layout.


```

```TypeScript
### Example 2: Determining Whether to Participate in Layout Calculation

This example shows how to determine whether a component participates in layout calculation based on its position.


```

```TypeScript
### Example 3: Obtaining the Child Component FrameNode and Setting Related Attributes

This example shows how to obtain the FrameNode of a child component using uniqueId and change its size and background color using the FrameNode API.


```

```TypeScript
### Example 4: Allowing the Child Component to Ignore Parent Component Size Constraints

This example demonstrates how to use the fixAtIdealSize property of the [LayoutPolicy](./ts-universal-attributes-size.md#layoutpolicy15) object to allow the child component to ignore parent component size constraints.
```

```TypeScript
### Example 1: Triggering the onKeyEvent Callback

This example sets a key event for a button. When the button obtains focus, pressing a key triggers the onKeyEvent callback. For details about the process and specific timing of the key event triggering, see [Key Event Data Flow](../../../ui/arkts-interaction-development-guide-keyboard.md#key-event-data-flow).


```

```TypeScript
### Example 2: Obtaining the Unicode Code Point

This example demonstrates how to obtain the Unicode code point of the pressed key using the key event.


```

```TypeScript
### Example 3: Triggering the onKeyPreIme Callback

This example demonstrates how to use the onKeyPreIme callback to intercept and disable the left arrow key in a text box.
```

```TypeScript
### Example 4: Preventing Event Bubbling

This example demonstrates event bubbling prevention using stopPropagation. Adding event.stopPropagation() to the Button component's onKeyEvent callback ensures only the Button component responds to keyboard events, while the parent Column remains unresponsive.

> NOTE
> 
> The onKeyEvent event bubbles by default.
> 
> Event bubbling: In a tree structure, after a child node finishes processing an event, the event is passed to its parent node for processing.
> 
> In [onKeyEvent15+](#onkeyevent15), you can return true to consume the key event and prevent bubbling, which is equivalent to calling stopPropagation.
```

```TypeScript
### Example 1: Obtaining Parameters Related to a Mouse Event

This example demonstrates how to set a mouse event on a button. When the button is clicked using a mouse device, the [onMouse](#onmouse) event is triggered to obtain relevant mouse event parameters. Starting from API version 15, the [MouseEvent](#mouseevent) object provides access to the targetDisplayId, rawDeltaX, rawDeltaY, and pressedButtons parameters.

For mouse wheel event examples, see [Axis Event](ts-universal-events-axis.md#example).

The figure below shows how the button looks when clicked.


```

```TypeScript
### Example 2: Obtaining Historical Points of the Current Frame

This example calls the [getHistoricalPoints](#gethistoricalpoints) API to obtain the historical points of the current frame, which can be used to implement smoother drawing.

The getHistoricalPoints API is added as of API version 26.0.0.
```

```TypeScript
### Example 3: Obtaining the Real-Time Position of a Component

This example uses the [getCurrentLocalPosition](#getcurrentlocalposition) method to obtain the coordinates of the mouse position relative to the upper left corner of the real-time position of the current component.

The getCurrentLocalPosition API is supported since API version 26.0.0.
```

```TypeScript
### Example 1: Setting the Component Stacking Order

This example demonstrates how to set the stacking order of components using zIndex.

When no zIndex is set for child components in a Stack container, they are displayed in the order in which they are declared by default, with later-declared components overlapping earlier-declared ones.



Display of child components in the Stack container when zIndex is set


```

```TypeScript
### Example 2: Dynamically Modifying the zIndex Attribute

This example demonstrates dynamically modifying the zIndex attribute on a Button component.

Effect without clicking the Button component to change zIndex



Effect after clicking the Button component to dynamically change zIndex so that Text1 and Text2 have the same zIndex value



Effect after the Button component is clicked to dynamically change zIndex so that Text2 has a higher zIndex value than Text1


```

```TypeScript
### Example 3: Setting zIndex for Components in Different Containers

This example sets the zIndex attribute for components in different containers. Text1 and Text2 are in the same Stack container, while Text3 is in another Stack container. Although Text3 has the smallest zIndex value, Text1 and Text2 still cannot be displayed above Text3 based on their zIndex values.
```

```TypeScript
### Example 1: Using onVisibleAreaChange to Listen for Visible Area Changes

This example demonstrates how to set an [onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange) event for a component, which triggers the callback when the component is fully displayed or completely hidden.
```

```TypeScript
### Example 2: Using onVisibleAreaApproximateChange to Listen for Visible Area Changes

This example demonstrates how to set an [onVisibleAreaApproximateChange](arkts-arkui-commonmethod-c.md#onvisibleareaapproximatechange) event for a component, which triggers the callback when the component is fully displayed or completely hidden. This feature is supported from API version 17.


```

```TypeScript
### Example 3: Setting measureFromViewport to Calculate the Visible Area When a Child Component Extends Beyond Its Parent

Starting from API version 22, this example demonstrates the effect comparison after setting the measureFromViewport parameter for the onVisibleAreaChange event. The main difference is reflected in the component visibility ratio (currentRatio) returned by the callback. When measureFromViewport is set to true, the returned component visibility ratio (currentRatio) better matches the actual effect. Because different devices have different screen pixel densities, the calculation of the visible area change event involves decimal rounding, and currentRatio may have slight differences.
```

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State isShow: boolean = false

  build() {
    Stack({ alignContent: Alignment.Center }) {
      if (this.isShow) {
        Image($r('app.media.pic'))
          .autoResize(false)
          .clip(true)
          .width(300)
          .height(400)
          .offset({ y: 100 })
          .geometryTransition("picture", { hierarchyStrategy: TransitionHierarchyStrategy.ADAPTIVE })
          .transition(TransitionEffect.OPACITY)
      } else {
        // geometryTransition is bound to a container. Therefore, a relative layout must be configured for the child components of the container.
        // The multiple levels of containers here are used to demonstrate passing of relative layout constraints.
        Column() {
          Column() {
            Image($r('app.media.icon'))
              .width('100%').height('100%')
          }.width('100%').height('100%')
        }
        .width(80)
        .height(80)
        // geometryTransition synchronizes rounded corner settings, but only for the bound component, which is the container in this example.
        // In other words, rounded corner settings of the container are synchronized, and those of the child components are not.
        .borderRadius(20)
        .clip(true)
        .geometryTransition("picture", { hierarchyStrategy: TransitionHierarchyStrategy.ADAPTIVE })
        // transition ensures that the component is not destructed immediately when it exits. You can customize the transition effect.
        .transition(TransitionEffect.OPACITY)
      }
    }
    .onClick(() => {
      this.getUIContext()?.animateTo({ duration: 1000 }, () => {
        this.isShow = !this.isShow;
      })
    })
  }
}
```

```TypeScript
This example sets the mouse cursor style using setCursor.
```

```TypeScript
### Example 1: Using onAreaChange to Listen for Area Changes

This example demonstrates how to set an area change event for a Text component. When the layout of the Text component changes, the onAreaChange event is triggered, allowing you to obtain relevant parameters.


```

```TypeScript
### Example 2: Using onAreaChange to Listen for Area Changes at a Custom Interval

In this example, by setting [expectedUpdateInterval](arkts-arkui-areachangeoptions-i.md), the [onAreaChange](#onareachange-1) event can be triggered when the Text layout changes, achieving the effect of interval callbacks.

Since API version 26.0.0, [onAreaChange](#onareachange-1), [AreaChangeCallback](arkts-arkui-areachangecallback-t.md), and [AreaChangeOptions](arkts-arkui-areachangeoptions-i.md) are added.
```

```TypeScript
This example demonstrates how to use restoreId to set the ID of the List component for device matching during hopping.
```

```TypeScript
### Example 1: Setting Polymorphic Styles for the Text Component

This example shows the style changes of the Text component when the state is set to hovered, pressed, and disabled using [stateStyles](#statestyles).

The hovered attribute is added to [stateStyles](#statestyles) as of API version 26.0.0.


```

```TypeScript
### Example 2: Setting Polymorphic Styles for the Radio Component

This example demonstrates the style changes of the Radio component when its state is selected.


```

```TypeScript
### Example 3: Setting Polymorphic Styles for the Builder Component

This example shows the style change of the custom component in @Builder when the state is pressed.
```

```TypeScript
### Example 1: Setting Different Image Attributes

Sets image effects, including shadow, grayscale, highlight, saturation, contrast, image inversion, color blending, hue rotation, and so on.


```

```TypeScript
### Example 2: Applying a Linear Gradient Blur Effect

This example demonstrates how to apply a linear gradient blur effect on a component using [linearGradientBlur](arkts-arkui-commonmethod-c.md#lineargradientblur).


```

```TypeScript
### Example 3: Setting Offscreen Rendering Effect

This example demonstrates how to use [renderGroup](arkts-arkui-commonmethod-c.md#rendergroup) to set whether the component is rendered entirely offscreen and then composited with its parent component.


```

```TypeScript
### Example 4: Blending the Current Component Content with Canvas Content

This example demonstrates how to blend the current component content with the canvas content below using [blendMode](#blendmode11).


```

```TypeScript
### Example 5: Inverting the Foreground Color

This example demonstrates how to achieve intelligent foreground color inversion using [InvertOptions](arkts-arkui-invertoptions-i.md).


```

```TypeScript
### Example 6: Setting Non-Overlapping Same-Layer Shadows

This example demonstrates how to implement non-overlapping shadow effect within the same layer using [useShadowBatching](arkts-arkui-commonmethod-c.md#useshadowbatching) in combination with [shadow](#shadow).


```

```TypeScript
### Example 7: Applying a Spherical Effect to a Component

This example demonstrates how to apply a spherical effect to a component using [sphericalEffect](arkts-arkui-commonmethod-c.md#sphericaleffect).

Below is how the component looks with the spherical effect applied.



Below is how the component looks without the spherical effect applied.


```

```TypeScript
### Example 8: Applying a Light Up Effect to a Component

This example demonstrates how to apply a light up effect to a component using [lightUpEffect](arkts-arkui-commonmethod-c.md#lightupeffect).

Below is how the component looks with the light up effect applied.



Below is how the component looks with lightUpEffect set to 0.2:



Below is how the component looks without the light up effect applied.


```

```TypeScript
### Example 9: Applying a Pixel Stretch Effect to a Component

This example demonstrates how to apply a pixel stretch effect to a component using [pixelStretchEffect](arkts-arkui-commonmethod-c.md#pixelstretcheffect).

Below is how the component looks with the pixel stretch effect applied.



Below is how the component looks without the pixel stretch effect applied.


```

```TypeScript
### Example 10: Applying a System Bar Effect to a Component

This example demonstrates how to apply a system bar effect to a component using [systemBarEffect](arkts-arkui-commonmethod-c.md#systembareffect).

Below is how the component looks with the system bar effect applied.


```

```TypeScript
### Example 11: Setting Whether the Component Is Double-Sided

This example demonstrates how to use [doubleSided](arkts-arkui-commonmethod-c.md#doublesided) to set whether the component is double-sided.

The doubleSided method is added since API version 26.0.0.
```

```TypeScript
### Example 1: Implementing Gesture-based Scrolling

This example sets the [enableScrollInteraction](#enablescrollinteraction11) attribute to scroll a vertical list with gestures and call back the index when the currently displayed interface changes.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](./ts-container-list.md#example-1-adding-a-scroll-event).


```

```TypeScript
### Example 2: Setting Edge Fading

This example sets the [fadingEdge](#fadingedge14) attribute to enable the edge fading effect for the [List](ts-container-list.md) component and set the edge fading length.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](./ts-container-list.md#example-1-adding-a-scroll-event).


```

```TypeScript
### Example 3: Setting the Clipping Region

This example sets the [clipContent](arkts-arkui-scrollablecommonmethod-c.md#clipcontent) attribute to change the clipping area of the component's content layer.


```

```TypeScript
### Example 4: Setting the Scrollbar Margin

This example demonstrates how to use the [scrollBarMargin](#scrollbarmargin20) attribute to adjust the scrollbar margins of a scrollable component, available since API version 20.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](./ts-container-list.md#example-1-adding-a-scroll-event).
```

```TypeScript
### Example 1: Using the onAccessibilityHover Event

This example demonstrates how to use the onAccessibilityHover event to configure a button in accessibility mode.
```

```TypeScript
### Example 2: Capturing a Touch Event on a Non-Focusable Component

This example shows how to capture touch events from a component that cannot receive focus in accessibility mode using the onAccessibilityHoverTransparent API and display event details in the text area below.

Starting from API version 20, the [onAccessibilityHoverTransparent](arkts-arkui-commonmethod-c.md#onaccessibilityhovertransparent) API with the input parameter type AccessibilityTransparentCallback has been added.
```

```TypeScript
### Example 1 (Setting Component Drag and Drop)

Example 1 shows how to set the drag and drop area for some components (such as Image and Text).


```

```TypeScript
### Example 2 (Custom Drop Animation)

Since API version 18, Example 2 demonstrates how to implement a custom drop animation through the [executeDropAnimation](arkts-arkui-dragevent-i.md#executedropanimation) API.


```

```TypeScript
### Example 3 (Asynchronously Obtaining Data During Drag)

Since API version 15, Example 3 demonstrates asynchronously obtaining data during drag through [startDataLoading](arkts-arkui-dragevent-i.md#startdataloading).
```

```TypeScript
### Example 4 (Get the screen ID of the current drag)

Since API version 20, Example 4 shows how to obtain the drag event through the onDragXXX (onDragEnd not supported) API and call the [getDisplayId](#getdisplayid20) API of the drag event to obtain the screen ID.


```

```TypeScript
### Example 5 (Obtaining the Package Name and Checking Whether It Is a Cross-Device Drag)

Starting from API version 20, Example 5 shows how to obtain a drag event through the onDragXXX API, call the [getDragSource](arkts-arkui-dragevent-i.md#getdragsource) API of the drag event to obtain the package name, and call the isRemote API to determine whether it is a cross-device drag.


```

```TypeScript
### Example 6 (Drag Supporting Hover Detection)

Since API version 20, Example 6 demonstrates registering a callback through the [onDragSpringLoading](arkts-arkui-commonmethod-c.md#ondragspringloading) API and obtaining context information (current state and notification sequence) through [SpringLoadingContext](#springloadingcontext20) in the callback.


```

```TypeScript
### Example 7 (Delayed Data Provision by the Drag Initiator)

Starting from API version 20, Example 7 demonstrates calling [setDataLoadParams](arkts-arkui-dragevent-i.md#setdataloadparams) in [onDragStart](#ondragstart) to delay data provision, and calling [startDataLoading](arkts-arkui-dragevent-i.md#startdataloading) in [onDrop](#ondrop) to obtain data asynchronously.


```

```TypeScript
### Example 8: Automatically Hiding a Specified Component During Drag

This example uses the [autoHideComponentUniqueIds](#attributes) attribute of DragEvent to automatically hide a specified component after a drag is successfully initiated.

Since API version 26.0.0, DragEvent adds the autoHideComponentUniqueIds attribute.
```

```TypeScript
Set the grid configuration for different device types. gridSpan and gridOffset are used to set the default occupied column count and offset column count, and they take effect only when the corresponding size is not configured in useSizeType. In the example, useSizeType configures the value for the sm size (span: 2, offset: 1). To achieve the same grid effect for other unconfigured sizes, set the default values through gridSpan and gridOffset.

> NOTE
> 
> This example demonstrates the usage of deprecated APIs. It is recommended to use the new components [GridCol](ts-container-gridcol.md) and [GridRow](ts-container-gridrow.md) to implement the grid layout.
```

```TypeScript
### Example 1: Using onHover

This example demonstrates how to set the [onHover](#onhover) event on a button. When the mouse or stylus hovers over the button, the event is triggered to dynamically change the text content and background color of the button.

Diagrams:

The figure below shows how the button looks in the non-hovered state.



The figure below shows how the button looks when a stylus hovers on it.


```

```TypeScript
### Example 2: Using onHoverMove

Since API version 15, this example sets the [onHoverMove](arkts-arkui-commonmethod-c.md#onhovermove) event of the button. When a stylus hovers over the button, the UI displays the current hover position of the stylus.
```

```TypeScript
### Example 1: Creating Outlines

This example demonstrates how to create component outlines using [outline](arkts-arkui-commonmethod-c.md#outline).


```

```TypeScript
### Example 2: Using the LocalizedEdgeColors Type

This example demonstrates how to set the color attribute of the [outline](arkts-arkui-commonmethod-c.md#outline) attribute to the [LocalizedEdgeColors](ts-types.md#localizededgecolors12) type.
```

```TypeScript
This example demonstrates how to apply blur effects using foregroundFilter, backgroundFilter, and compositingFilter.
```

```TypeScript
### Example 1: Parent Component Prioritizes Gesture Recognition and Parent and Child Components Trigger Gestures Simultaneously

This example uses priorityGesture and parallelGesture to implement parent component priority gesture recognition and simultaneous gesture triggering by parent and child components, respectively.


```

```TypeScript
### Example 2: Monitoring the Number of Valid Touch Points in a Swipe Gesture in Real Time

This example reads fingerInfos to monitor the number of valid touch points involved in a swipe gesture in real time.
```

```TypeScript
This example demonstrates how to set whether a component monopolizes events by configuring monopolizeEvents.
```

```TypeScript
### Example 1: Setting Component Keyboard Shortcuts

This example demonstrates how to set up keyboard shortcuts for components. This allows users to press the modifier key and accompanying key at the same time to trigger the component to respond to the shortcut and trigger the onClick event or a custom event.


```

```TypeScript
### Example 2: Binding and Unbinding Keyboard Shortcuts

This example demonstrates how to bind and unbind keyboard shortcuts.
```

```TypeScript
### Example 1: Understanding the Hit Test Effect When the Hit Test Mode Is Block and Transparent

This example demonstrates the hit test effects of Block and Transparent hit test modes by setting different [HitTestMode](./ts-appendix-enums.md#hittestmode9) values.
```

```TypeScript
### Example 2: Understanding the Hit Test Effect When the Hit Test Type is BLOCK_HIERARCHY

Starting from API version 20, this example demonstrates the hit test effect when the hit test mode is set to BLOCK_HIERARCHY.
```

```TypeScript
### Example 3: Understanding the Hit Test Effect When the Hit Test Type is BLOCK_DESCENDANTS

Starting from API version 20, this example demonstrates the hit test effect when the hit test mode is set to BLOCK_DESCENDANTS.
```

```TypeScript
### Example 4: Understanding the Hit Test Effect When Multiple Nodes Overlap in the Stack Component

This example demonstrates the hit testing effect when multiple nodes have overlapping touch areas within a Stack component. If [HitTestMode](./ts-appendix-enums.md#hittestmode9) is set to None, the overlapping background area cannot respond to hit testing. The background area responds to hit testing only when the attribute is set to Transparent.
```

```TypeScript
### Example 1: Setting the Component Width, Height, Margin, and Padding

This example demonstrates how to set the width, height, padding, and margin of a component.


```

```TypeScript
### Example 2: Using LocalizedPadding and LocalizedMargin Types

This example demonstrates how to use LocalizedPadding and LocalizedMargin types to define the padding and margin attributes.

The following shows how the example is represented with left-to-right scripts.



The following shows how the example is represented with right-to-left scripts.


```

```TypeScript
### Example 3: Setting a Component-Level Safe Area

This example demonstrates how to set a component-level safe area for a container.


```

```TypeScript
### Example 4: Using attributeModifier to Dynamically Set a Safe Area

This example demonstrates how to use attributeModifier to dynamically set a component-level safe area for a container.


```

```TypeScript
### Example 5: Setting the Layout Policy

This example demonstrates how to set the layout policy for a container's size.


```

```TypeScript
### Example 6: Setting matchParent on a Single Direction of a Child Component

This example demonstrates the layout effect when the Column component adapts to child components and a child component sets matchParent on only a single direction. Since API version 26.0.0, the height of the Column component adapts to the first and second child components, and the width adapts to the first and third child components.
```

```TypeScript
This example demonstrates how components gain and lose focus. The colors of the buttons change when they gain or lose focus.
```

```TypeScript
### Example 1: Obtaining Axis Event Parameters

This example shows how to set up an axis event on a button. When the user scrolls the mouse wheel, the axis event parameters are captured. Starting from API version 21, this example uses the  attribute of [BaseEvent](./ts-universal-events-click.md#baseevent8) and [getPinchAxisScaleValue](arkts-arkui-axisevent-i.md#getpinchaxisscalevalue) to obtain the pinch scale value. Starting from API version 22, this example uses [hasAxis](arkts-arkui-axisevent-i.md#hasaxis) to check whether the axis event contains the specified axis type.

The figure below shows the event parameters captured when the user scrolls the mouse wheel.


```

```TypeScript
### Example 2: Obtaining the Real-Time Position of a Component

This example uses the [getCurrentLocalPosition](#getcurrentlocalposition) method to obtain the coordinates of the mouse cursor position relative to the upper-left corner of the current component's real-time position.

The getCurrentLocalPosition API is supported since API version 26.0.0.
```

```TypeScript
### Example 1: Using Different Clipping Attributes

This example demonstrates how to clip and mask an image using [clipShape](arkts-arkui-commonmethod-c.md#clipshape), [clip](#clip12), and [maskShape](arkts-arkui-commonmethod-c.md#maskshape).


```

```TypeScript
### Example 2: Implementing Component Masking

This example demonstrates how to mask an image using [mask](#mask12).
```

```TypeScript
### Example 1: Disabling Default Click Sound Effect

This example disables the default click sound effect by setting the enableClickSoundEffect attribute. You can call audio-related APIs in the onClick callback to customize the sound effect. For details, see [Using SoundPool to Play Short Sounds](../../../media/media/using-soundpool-for-playback.md).

The [enableClickSoundEffect](arkts-arkui-commonmethod-c.md#enableclicksoundeffect) attribute is added since API version 24.
```

```TypeScript
### Example 1: Dynamically Binding a Gesture

This example demonstrates how to dynamically set the gestures bound to a component using gestureModifier.


```

```TypeScript
### Example 2: Dynamically Binding a Gesture Group

This example demonstrates how to dynamically set the gesture group bound to a component using gestureModifier.
```

```TypeScript
This example demonstrates how to set different content fill modes for a component during width and height animations through the renderFit attribute.
```

```TypeScript
In this example, the toolbar universal attribute is bound to the [Button](ts-basic-components-button.md) component under [Navigation](ts-basic-components-navigation.md) to add a toolbar item containing two [Button](ts-basic-components-button.md) components at the beginning of the NavBar column of the title bar. The toolbar universal attribute is bound to the [Text](ts-basic-components-text.md) component under [NavDestination](ts-basic-components-navdestination.md) to add a toolbar item containing a slider component and a search bar component at the end of the NavDestination column of the title bar.
```

```TypeScript
### Example 1: Color Linear Gradient

This example demonstrates how to create a linear color gradient using [linearGradient](#lineargradient).


```

```TypeScript
### Example 2: Creating a Sweep Gradient

This example demonstrates how to create a sweep color gradient using [sweepGradient](arkts-arkui-commonmethod-c.md#sweepgradient).


```

```TypeScript
### Example 3: Creating a Radial Gradient

This example demonstrates how to create a radial color gradient using [radialGradient](arkts-arkui-commonmethod-c.md#radialgradient).
```

```TypeScript
### Example 1: Setting the Component Aspect Ratio

This example illustrates how to use the aspectRatio attribute to set different aspect ratios for a component.

Figure 1 Portrait display

Figure 2 Landscape display
```

```TypeScript
### Example 2: Setting the Component Display Priority

This example shows how to use displayPriority to set the display priority for child components.
```

```TypeScript
This example demonstrates how to set the foreground attributes through the foregroundEffect API.
```

```TypeScript
### Example 1: Implementing an Immersive Effect

This example demonstrates how to use the expandSafeArea attribute to expand the safe area to the top and bottom to achieve an immersive effect.


```

```TypeScript
### Example 2: Setting a Fixed Width or Height with expandSafeArea

This example demonstrates the effect of setting both a fixed width or height and the expandSafeArea attribute.

As shown in the figure below, the Column component expands to the top status bar ([SafeAreaEdge.TOP]) but does not expand to the bottom navigation bar ([SafeAreaEdge.BOTTOM]). The height of the component after expansion remains consistent with the set value.


```

```TypeScript
### Example 3: Fixing the Background Image Position During Keyboard Avoidance

This example shows how to set the expandSafeArea attribute for the background image to keep it fixed when the keyboard is displayed and the layout is adjusted.


```

```TypeScript
### Example 4: Setting the Keyboard Avoidance Mode to Resize

This example demonstrates how to use setKeyboardAvoidMode to set the keyboard avoidance mode to RESIZE, which resizes the page when the keyboard is displayed.
```

```TypeScript

```

```TypeScript
### Example 5: Setting Keyboard Avoidance Mode to Offset

This example demonstrates how to use setKeyboardAvoidMode to set the keyboard avoidance mode to OFFSET, which lifts the page when the keyboard is displayed. However, if the input cursor is positioned more than the keyboard's height from the bottom of the screen, the page will not be lifted, as demonstrated in this example.
```

```TypeScript

```

```TypeScript
### Example 6: Switching Avoidance Modes

This example demonstrates how to switch between OFFSET, RESIZE, and NONE modes using setKeyboardAvoidMode to achieve three different keyboard avoidance effects.


```

```TypeScript
### Example 7: Expanding the Safe Area in Scrollable Containers

This example demonstrates how to use the expandSafeArea attribute in a scrollable container to implement an immersive effect. The Swiper component in the Scroll container can extend into the status bar.


```

```TypeScript
### Example 8: Extending the Component Layout Area with ignoreLayoutSafeArea

This example shows how to use [ignoreLayoutSafeArea](#ignorelayoutsafearea20) to adjust the component position. The comparison with the default behavior (without this attribute) is as follows: After ignoreLayoutSafeArea is applied, the Row component is positioned in the upper left corner of the combined range consisting of the Stack content area, the Stack component-level safe area, and the system status bar. The component occupies the upper left portion of this expanded layout boundary.
```

```TypeScript
### Example 9: Extending the Component Layout Area with ignoreLayoutSafeArea and LayoutPolicy.matchParent

This example demonstrates how to use both [ignoreLayoutSafeArea](#ignorelayoutsafearea20) and [LayoutPolicy.matchParent](ts-universal-attributes-size.md#layoutpolicy15) to adjust the component's size and position simultaneously. After ignoreLayoutSafeArea is applied, the Row component takes the lower right portion of the combined range consisting of the Stack content area and the Stack component-level safe area, and expands to fill the available space.


```

```TypeScript
### Example 10: Understanding the Difference Between expandSafeArea and ignoreLayoutSafeArea

This example demonstrates the layout effects of a container with expandSafeArea and ignoreLayoutSafeArea set, respectively, and their impact on the layout of child components. In both cases, the container visibly extends. However, the child components of the container with expandSafeArea are not affected by the container's extension, while the child components of the container with ignoreLayoutSafeArea have their positions adjusted due to the container's extension.
```

```TypeScript
This example demonstrates how to control the mounting and unmounting of a component using a button, triggering onAttach and onDetach events.
```

```TypeScript
### Example 1: Setting an Overlay Using a String

This example demonstrates how to set an overlay using a string.


```

```TypeScript
### Example 2: Setting an Overlay Using a Custom Builder

This example demonstrates how to set an overlay using a custom builder.


```

```TypeScript
### Example 3: Setting an Overlay Using ComponentContent

This example uses overlay to pass in ComponentContent, and updates the ComponentContent parameters through the update method, so that backgroundColor keeps changing.
```
