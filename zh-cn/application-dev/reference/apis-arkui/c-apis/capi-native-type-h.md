# native_type.h

## 概述

Defines the common types for the native module.

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_GridItemSize](capi-arkui-nativemodule-arkui-griditemsize.md) | ArkUI_GridItemSize | Defines the return value structure for the <b>onGetIrregularSizeByIndex</b> callbackin <b>Grid</b> layout options. |
| [ArkUI_GridItemRect](capi-arkui-nativemodule-arkui-griditemrect.md) | ArkUI_GridItemRect | Defines the return value structure for the <b>onGetRectByIndex</b> callback in <b>Grid</b> layout options. |
| [ArkUI_PickerIndicatorBackground](capi-arkui-nativemodule-arkui-pickerindicatorbackground.md) | ArkUI_PickerIndicatorBackground | Style parameters of background indicator. |
| [ArkUI_PickerIndicatorDivider](capi-arkui-nativemodule-arkui-pickerindicatordivider.md) | ArkUI_PickerIndicatorDivider | Style parameters of divider indicator. |
| [ArkUI_ContextCallback](capi-arkui-nativemodule-arkui-contextcallback.md) | ArkUI_ContextCallback | Defines the event callback type. |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) | ArkUI_NumberValue | Provides the number types of ArkUI in the native code. |
| [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md) | ARKUI_TextPickerRangeContent | Defines the input structure of the single-column text picker with image resources. |
| [ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md) | ARKUI_TextPickerCascadeRangeContent | Defines the input structure of the interconnected multi-column text picker. |
| [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md) | ArkUI_ColorStop | Defines the gradient color stop structure. |
| [ArkUI_Rect](capi-arkui-nativemodule-arkui-rect.md) | ArkUI_Rect | Defines a mask area. |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md) | ArkUI_IntSize | Describes the width and height of a component. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) | ArkUI_IntOffset | Describes the position of a component. |
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) | ArkUI_Margin | Describes the margins of a component. |
| [ArkUI_TranslationOptions](capi-arkui-nativemodule-arkui-translationoptions.md) | ArkUI_TranslationOptions | Defines the translation options for component transition. |
| [ArkUI_ScaleOptions](capi-arkui-nativemodule-arkui-scaleoptions.md) | ArkUI_ScaleOptions | Defines the scaling options for component transition. |
| [ArkUI_RotationOptions](capi-arkui-nativemodule-arkui-rotationoptions.md) | ArkUI_RotationOptions | Defines the rotation options for component transition. |
| [ArkUI_Node](capi-arkui-nativemodule-arkui-node.md) | - | Defines the ArkUI native component object. |
| [ArkUI_NodeContent*](capi-arkui-nativemodule-arkui-nodecontent8h.md) | ArkUI_NodeContentHandle | Defines the pointer type of the ArkUI node content |
| [ArkUI_NativeDialog](capi-arkui-nativemodule-arkui-nativedialog.md) | - | Defines the custom dialog box controller of ArkUI on the native side. |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md) | ArkUI_LayoutConstraint | Sets the size constraints of a component during component layout. |
| [ArkUI_DrawContext](capi-arkui-nativemodule-arkui-drawcontext.md) | ArkUI_DrawContext | Defines the structure of the component drawing context. |
| [ArkUI_Node*](capi-arkui-nativemodule-arkui-node8h.md) | ArkUI_NodeHandle | Defines the pointer to the ArkUI native component object. |
| [ArkUI_NativeDialog*](capi-arkui-nativemodule-arkui-nativedialog8h.md) | ArkUI_NativeDialogHandle | Defines the pointer to the custom dialog box controller of ArkUI on the native side. |
| [ArkUI_GestureCollectInterceptInfo](capi-arkui-nativemodule-arkui-gesturecollectinterceptinfo.md) | ArkUI_GestureCollectInterceptInfo | Defines information about gesture collection interception. |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) | ArkUI_PickerIndicatorStyle | Definition of indicator style. |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md) | ArkUI_GridLayoutOptions | Defines the <b>Grid</b> layout options. |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) | ArkUI_WaterFlowSectionOption | Defines the water flow section configuration. |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md) | ArkUI_ListItemSwipeActionItem | Define the configuration information of the Item within the ListitemSwipeActionOption method. |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md) | ArkUI_ListItemSwipeActionOption | Define the configuration information for the ListitemSwipeActionOption method. |
| [ArkUI_Context](capi-arkui-nativemodule-arkui-context.md) | - | Defines the ArkUI native context object. |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md) | ArkUI_SwiperIndicator | Defines the navigation indicator style for the swiper. |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) | ArkUI_SwiperDigitIndicator | Defines the digital indicator style for the swiper. |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) | ArkUI_SwiperArrowStyle | Defines the arrow style for the swiper. |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) | ArkUI_ListChildrenMainSize | Define the ChildrenMainSize class information for a List. |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md) | ArkUI_ImageAnimatorFrameInfo | Defines the image frame. |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md) | ArkUI_AccessibilityState | Defines the accessibility state for the component. |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md) | ArkUI_AccessibilityValue | Defines the accessibility value for the component. |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md) | ArkUI_CustomProperty | Define the information of the Custom Property class for custom properties. |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md) | ArkUI_HostWindowInfo | Define the information of the HostWindowInfo class for window properties. |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md) | ArkUI_ActiveChildrenInfo | Define ActiveChildenInfo class information. |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md) | ArkUI_CrossLanguageOption | The cross-language option. |
| [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md) | AbilityBase_Want | Declares the Ability base want. |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md) | ArkUI_EmbeddedComponentOption | Define the EmbeddedComponentOption for the EmbeddedComponent. |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md) | ArkUI_PositionEdges | Define the Edges describing the position of a component by distances to the container's four edges. |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md) | ArkUI_PixelRoundPolicy | Defines the PixelRound policy of a component's four edges. |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md) | ArkUI_Matrix4 | Defines the matrix4 object. |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md) | ArkUI_SelectedDragPreviewStyle | Defines the selected drag preview style configuration. |
| [ArkUI_SystemFontStyleEvent](capi-arkui-nativemodule-arkui-systemfontstyleevent.md) | ArkUI_SystemFontStyleEvent | Defines parameter used by the system font style callback event. |
| [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md) | ArkUI_ContentTransitionEffect | Set the types and parameters related to content transition effects. |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md) | OH_ArkUI_TextEditorSelectionMenuOptions | 定义文本编辑器的文本选择菜单选项。 |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md) | OH_ArkUI_TextEditorPlaceholderOptions | 定义文本编辑器无输入时的提示文本选项。 |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md) | OH_ArkUI_TextEditorStyledStringController | 定义文本编辑器的属性字符串控制器。 |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md) | OH_ArkUI_TextEditorParagraphStyle | 定义文本编辑器的段落样式。 |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) | OH_ArkUI_ShadowOptions | 定义阴影选项。 |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md) | OH_ArkUI_TextEditorTextStyle | 定义文本编辑器的文本样式。 |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md) | ArkUI_MotionPathOptions | Defines the motion path options for path animation. |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md) | ArkUI_Matrix4ScaleOptions | Defines the scale options for matrix scaling. |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md) | ArkUI_Matrix4RotationOptions | Defines the rotation options for matrix rotating. |
| [ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md) | ArkUI_Matrix4TranslationOptions | Defines the translation options for matrix translating. |
| [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md) | OH_ArkUI_LinearGradientOptions | Defines linear gradient options. |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md) | OH_ArkUI_RadialGradientOptions | Defines radial gradient options. |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_PickerIndicatorType](#arkui_pickerindicatortype) | ArkUI_PickerIndicatorType | Enumerates the selected indicator type of picker. |
| [ArkUI_Alignment](#arkui_alignment) | ArkUI_Alignment | Enumerates the alignment modes. |
| [ArkUI_ImageRepeat](#arkui_imagerepeat) | ArkUI_ImageRepeat | Enumerates the image repeat patterns. |
| [ArkUI_XComponentType](#arkui_xcomponenttype) | ArkUI_XComponentType | Enumerates the types of the <b><XComponent></b> component. |
| [ArkUI_CopyOptions](#arkui_copyoptions) | ArkUI_CopyOptions | Enumerates the text copy and paste modes. |
| [ArkUI_ShadowType](#arkui_shadowtype) | ArkUI_ShadowType | Enumerates the shadow types. |
| [ArkUI_DatePickerMode](#arkui_datepickermode) | ArkUI_DatePickerMode | Enumerates the modes of the date picker. |
| [ArkUI_TextPickerRangeType](#arkui_textpickerrangetype) | ArkUI_TextPickerRangeType | Enumerates the types of the text picker. |
| [ArkUI_EdgeEffect](#arkui_edgeeffect) | ArkUI_EdgeEffect | Enumerates the effects used at the edges of the component when the boundary of the scrollable content isreached. |
| [ArkUI_BarState](#arkui_barstate) | ArkUI_BarState | Enumerates the status of the scroll bar. |
| [ArkUI_EffectEdge](#arkui_effectedge) | ArkUI_EffectEdge | Enumerates the edges for which the effect takes effect when the boundary of the scrollable content is reached. |
| [ArkUI_FocusWrapMode](#arkui_focuswrapmode) | ArkUI_FocusWrapMode | Enumerates the focus wrap mode of components. |
| [ArkUI_ItemFillPolicy](#arkui_itemfillpolicy) | ArkUI_ItemFillPolicy | Specifies the number of columns for different responsive breakpoint specifications. |
| [ArkUI_GridItemAlignment](#arkui_griditemalignment) | ArkUI_GridItemAlignment | Enumerates the grid item alignment modes. |
| [ArkUI_GridItemStyle](#arkui_griditemstyle) | ArkUI_GridItemStyle | Enumerates styles of grid items. |
| [ArkUI_ScrollDirection](#arkui_scrolldirection) | ArkUI_ScrollDirection | Enumerates the scroll directions for the <b><Scroll></b> component. |
| [ArkUI_ScrollSnapAlign](#arkui_scrollsnapalign) | ArkUI_ScrollSnapAlign | Enumerates the alignment modes of list items when scrolling ends. |
| [ArkUI_ScrollSnapAnimationSpeed](#arkui_scrollsnapanimationspeed) | ArkUI_ScrollSnapAnimationSpeed | Enumerates the scroll snap animation speeds for lists. |
| [ArkUI_ScrollBarDisplayMode](#arkui_scrollbardisplaymode) | ArkUI_ScrollBarDisplayMode | Enumerates the scrollbar display modes. |
| [ArkUI_Axis](#arkui_axis) | ArkUI_Axis | Enumerates the scroll directions for the <b><List></b> component. |
| [ArkUI_StickyStyle](#arkui_stickystyle) | ArkUI_StickyStyle | Enumerates the modes for pinning the header to the top or the footer to the bottom. |
| [ArkUI_ContentClipMode](#arkui_contentclipmode) | ArkUI_ContentClipMode | Enumerates the content clipping modes of scrollable components. |
| [ArkUI_WaterFlowLayoutMode](#arkui_waterflowlayoutmode) | ArkUI_WaterFlowLayoutMode | Enumerates the layout modes of the WaterFlow component. |
| [ArkUI_BorderStyle](#arkui_borderstyle) | ArkUI_BorderStyle | Enumerates the border styles. |
| [ArkUI_ShadowStyle](#arkui_shadowstyle) | ArkUI_ShadowStyle | Enumerates the shadow styles. |
| [ArkUI_AnimationCurve](#arkui_animationcurve) | ArkUI_AnimationCurve | Enumerates the animation curves. |
| [ArkUI_SwiperArrow](#arkui_swiperarrow) | ArkUI_SwiperArrow | Enumerates arrow styles of the navigation point indicator. |
| [ArkUI_SwiperNestedScrollMode](#arkui_swipernestedscrollmode) | ArkUI_SwiperNestedScrollMode | Nested scrolling mode for Swiper components and parent components. |
| [ArkUI_PageFlipMode](#arkui_pageflipmode) | ArkUI_PageFlipMode | Enumerates the page flipping modes using the mouse wheel for the <b>Swiper</b> component. |
| [ArkUI_SwiperAnimationMode](#arkui_swiperanimationmode) | ArkUI_SwiperAnimationMode | Enumerates the animation modes for {@link NODE_SWIPER_INDEX}. |
| [ArkUI_AccessibilityMode](#arkui_accessibilitymode) | ArkUI_AccessibilityMode | Enumerates the accessibility modes. |
| [ArkUI_ScrollNestedMode](#arkui_scrollnestedmode) | ArkUI_ScrollNestedMode | Defines nested scrolling options. |
| [ArkUI_ScrollEdge](#arkui_scrolledge) | ArkUI_ScrollEdge | Defines the edge to which the component scrolls. |
| [ArkUI_ScrollAlignment](#arkui_scrollalignment) | ArkUI_ScrollAlignment | Alignment when scrolling to specific items. |
| [ArkUI_ScrollState](#arkui_scrollstate) | ArkUI_ScrollState | Define the current scrolling state. |
| [ArkUI_AnimationPlayMode](#arkui_animationplaymode) | ArkUI_AnimationPlayMode | Enumerates the animation playback modes. |
| [ArkUI_ImageSize](#arkui_imagesize) | ArkUI_ImageSize | Defines the image size. |
| [ArkUI_AdaptiveColor](#arkui_adaptivecolor) | ArkUI_AdaptiveColor | Enumerates the adaptive color modes. |
| [ArkUI_ColorMode](#arkui_colormode) | ArkUI_ColorMode | Enumerates the color modes. |
| [ArkUI_SystemColorMode](#arkui_systemcolormode) | ArkUI_SystemColorMode | Enumerates the system color modes. |
| [ArkUI_BlurStyle](#arkui_blurstyle) | ArkUI_BlurStyle | Enumerates the blur styles. |
| [ArkUI_BlurStyleActivePolicy](#arkui_blurstyleactivepolicy) | ArkUI_BlurStyleActivePolicy | Enumerates the activation policies for the background blur effect. |
| [ArkUI_VerticalAlignment](#arkui_verticalalignment) | ArkUI_VerticalAlignment | Enumerates the vertical alignment modes. |
| [ArkUI_HorizontalAlignment](#arkui_horizontalalignment) | ArkUI_HorizontalAlignment | Enumerates the alignment mode in the horizontal direction. |
| [ArkUI_ObjectFit](#arkui_objectfit) | ArkUI_ObjectFit | Defines how the image is resized to fit its container.ImageSpanAlignment |
| [ArkUI_ImageInterpolation](#arkui_imageinterpolation) | ArkUI_ImageInterpolation | Enumerates the image interpolation effect. |
| [ArkUI_DynamicRangeMode](#arkui_dynamicrangemode) | ArkUI_DynamicRangeMode | Enumerates the image dynamic range mode. |
| [ArkUI_ImageRotateOrientation](#arkui_imagerotateorientation) | ArkUI_ImageRotateOrientation | Enumerates the image rotate orientation. |
| [ArkUI_BlendMode](#arkui_blendmode) | ArkUI_BlendMode | Enumerates the blend modes. |
| [ArkUI_Direction](#arkui_direction) | ArkUI_Direction | Enumerates the modes in which components are laid out along the main axis of the container. |
| [ArkUI_ItemAlignment](#arkui_itemalignment) | ArkUI_ItemAlignment | Enumerates the modes in which components are laid out along the cross axis of the container. |
| [ArkUI_ColorStrategy](#arkui_colorstrategy) | ArkUI_ColorStrategy | Enumerates the foreground colors. |
| [ArkUI_FlexAlignment](#arkui_flexalignment) | ArkUI_FlexAlignment | Enumerates the vertical alignment modes. |
| [ArkUI_FlexDirection](#arkui_flexdirection) | ArkUI_FlexDirection | Enumerates the directions of the main axis in the flex container. |
| [ArkUI_FlexWrap](#arkui_flexwrap) | ArkUI_FlexWrap | Defines whether the flex container has a single line or multiple lines. |
| [ArkUI_CalendarAlignment](#arkui_calendaralignment) | ArkUI_CalendarAlignment | Enumerates the alignment modes between the calendar picker and the entry component. |
| [ArkUI_MaskType](#arkui_masktype) | ArkUI_MaskType | Enumerates the mask types. |
| [ArkUI_ClipType](#arkui_cliptype) | ArkUI_ClipType | Enumerates the clipping region types. |
| [ArkUI_ShapeType](#arkui_shapetype) | ArkUI_ShapeType | Enumerates the custom shapes. |
| [ArkUI_LinearGradientDirection](#arkui_lineargradientdirection) | ArkUI_LinearGradientDirection | Enumerates the gradient directions. |
| [ArkUI_ImageRenderMode](#arkui_imagerendermode) | ArkUI_ImageRenderMode | Enumerates the image rendering modes. |
| [ArkUI_TransitionEdge](#arkui_transitionedge) | ArkUI_TransitionEdge | Enumerates the slide-in and slide-out positions of the component from the screen edge during transition. |
| [ArkUI_BlendApplyType](#arkui_blendapplytype) | ArkUI_BlendApplyType | Defines how the specified blend mode is applied. |
| [ArkUI_FinishCallbackType](#arkui_finishcallbacktype) | ArkUI_FinishCallbackType | Enumerates the animation onFinish callback types. |
| [ArkUI_ListItemAlignment](#arkui_listitemalignment) | ArkUI_ListItemAlignment | Enumerates the alignment modes of items along the cross axis. |
| [ArkUI_LengthMetricUnit](#arkui_lengthmetricunit) | ArkUI_LengthMetricUnit | Enumerates the component units. |
| [ArkUI_RenderFit](#arkui_renderfit) | ArkUI_RenderFit | Enumerates the render fit. |
| [ArkUI_SwiperIndicatorType](#arkui_swiperindicatortype) | ArkUI_SwiperIndicatorType | Define the navigation indicator type of the swiper. |
| [ArkUI_ListItemSwipeActionState](#arkui_listitemswipeactionstate) | ArkUI_ListItemSwipeActionState | Define the pattern of element arrangement in the main axis direction of the Swiper component. |
| [ArkUI_ListItemSwipeEdgeEffect](#arkui_listitemswipeedgeeffect) | ArkUI_ListItemSwipeEdgeEffect | Define the explicit and implicit mode of the SwipeAction method for the Listitem component. |
| [ArkUI_ErrorCode](#arkui_errorcode) | ArkUI_ErrorCode | Define error code enumeration values. |
| [ArkUI_AnimationStatus](#arkui_animationstatus) | ArkUI_AnimationStatus | Defines the playback status for the image animator. |
| [ArkUI_AnimationFillMode](#arkui_animationfillmode) | ArkUI_AnimationFillMode | Defines the status before and after execution of the animation in the current playback direction. |
| [ArkUI_AccessibilityCheckedState](#arkui_accessibilitycheckedstate) | ArkUI_AccessibilityCheckedState | Defines the state type for the accessibility checkbox. |
| [ArkUI_AnimationDirection](#arkui_animationdirection) | ArkUI_AnimationDirection | Enumerates the animation playback modes. |
| [ArkUI_ScrollSource](#arkui_scrollsource) | ArkUI_ScrollSource | Define the rolling source enumeration value. |
| [ArkUI_AccessibilityActionType](#arkui_accessibilityactiontype) | ArkUI_AccessibilityActionType | Define accessible action types. |
| [ArkUI_NavDestinationState](#arkui_navdestinationstate) | ArkUI_NavDestinationState | Defines the state of the NavDestination component. |
| [ArkUI_RouterPageState](#arkui_routerpagestate) | ArkUI_RouterPageState | Define the state of Router Page. |
| [ArkUI_SafeAreaType](#arkui_safeareatype) | ArkUI_SafeAreaType | defines the enumerated value of the extended security zone. |
| [ArkUI_ListItemGroupArea](#arkui_listitemgrouparea) | ArkUI_ListItemGroupArea | Define an enum for the areas of the <b>ListItemGroup</b> component. |
| [ArkUI_SafeAreaEdge](#arkui_safeareaedge) | ArkUI_SafeAreaEdge | defines the enumerated value of the direction of the extended security zone. |
| [ArkUI_KeyboardAvoidMode](#arkui_keyboardavoidmode) | ArkUI_KeyboardAvoidMode | defines the enumerated value of the customDialog's keyboard avoid mode. |
| [ArkUI_HoverModeAreaType](#arkui_hovermodeareatype) | ArkUI_HoverModeAreaType | defines the enumerated value of area in hover mode. |
| [ArkUI_ExpandMode](#arkui_expandmode) | ArkUI_ExpandMode | Enumerates the expand modes. |
| [ArkUI_EdgeDirection](#arkui_edgedirection) | ArkUI_EdgeDirection | Enumerates the edge direction. |
| [ArkUI_CornerDirection](#arkui_cornerdirection) | ArkUI_CornerDirection | Enumerates the corner direction. |
| [ArkUI_PixelRoundCalcPolicy](#arkui_pixelroundcalcpolicy) | ArkUI_PixelRoundCalcPolicy | Enumerates the PixelRoundPolicy. |
| [ArkUI_MenuPolicy](#arkui_menupolicy) | ArkUI_MenuPolicy | Menu pop-up strategy. |
| [ArkUI_ListItemSwipeActionDirection](#arkui_listitemswipeactiondirection) | ArkUI_ListItemSwipeActionDirection | Define the direction to expand the swipe action. |
| [ArkUI_LayoutSafeAreaType](#arkui_layoutsafeareatype) | ArkUI_LayoutSafeAreaType | Define the types for expanding the safe area in layout. |
| [ArkUI_LayoutSafeAreaEdge](#arkui_layoutsafeareaedge) | ArkUI_LayoutSafeAreaEdge | Define the edges for expanding the safe area in layout. |
| [ArkUI_LocalizedAlignment](#arkui_localizedalignment) | ArkUI_LocalizedAlignment | Enumerates the localizedAlignment modes. |
| [ArkUI_RenderStrategy](#arkui_renderstrategy) | ArkUI_RenderStrategy | Enumerates the graphics rendering strategy. |
| [ArkUI_LayoutPolicy](#arkui_layoutpolicy) | ArkUI_LayoutPolicy | Enumerates the LayoutPolicy. |
| [OH_ArkUI_HapticFeedbackMode](#oh_arkui_hapticfeedbackmode) | OH_ArkUI_HapticFeedbackMode | 震动效果类型枚举。 |
| [OH_ArkUI_TextEditorSpanType](#oh_arkui_texteditorspantype) | OH_ArkUI_TextEditorSpanType | 自定义文本选择菜单span类型枚举。 |
| [OH_ArkUI_TextEditorResponseType](#oh_arkui_texteditorresponsetype) | OH_ArkUI_TextEditorResponseType | 自定义文本选择菜单响应类型枚举。 |
| [OH_ArkUI_TextMenuType](#oh_arkui_textmenutype) | OH_ArkUI_TextMenuType | 文本菜单类型枚举。 |
| [OH_ArkUI_CrossLanguageOperatingStatus](#oh_arkui_crosslanguageoperatingstatus) | OH_ArkUI_CrossLanguageOperatingStatus | Enumerates the tree operating status for the cross-language option. |
| [OH_ArkUI_NodeMountPolicy](#oh_arkui_nodemountpolicy) | OH_ArkUI_NodeMountPolicy | Enumeration of the policy for mounting child node to the target node. |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Create()](#oh_arkui_layoutconstraint_create) | Creates a size constraint. |
| [ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Copy(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_copy) | Creates a deep copy of a size constraint. |
| [void* OH_ArkUI_LayoutConstraint_Dispose(ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_dispose) | Destroys the pointer to a size constraint. |
| [int32_t OH_ArkUI_LayoutConstraint_GetMaxWidth(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getmaxwidth) | Obtains the maximum width for a size constraint, in px. |
| [int32_t OH_ArkUI_LayoutConstraint_GetMinWidth(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getminwidth) | Obtains the minimum width for a size constraint, in px. |
| [int32_t OH_ArkUI_LayoutConstraint_GetMaxHeight(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getmaxheight) | Obtains the maximum height for a size constraint, in px. |
| [int32_t OH_ArkUI_LayoutConstraint_GetMinHeight(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getminheight) | Obtains the minimum height for a size constraint, in px. |
| [int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceWidth(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getpercentreferencewidth) | Obtains the width percentage reference for a size constraint, in px. |
| [int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceHeight(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getpercentreferenceheight) | Obtains the height percentage reference for a size constraint, in px. |
| [void OH_ArkUI_LayoutConstraint_SetMaxWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setmaxwidth) | Sets the maximum width. |
| [void OH_ArkUI_LayoutConstraint_SetMinWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setminwidth) | Sets the minimum width. |
| [void OH_ArkUI_LayoutConstraint_SetMaxHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setmaxheight) | Sets the maximum height. |
| [void OH_ArkUI_LayoutConstraint_SetMinHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setminheight) | Sets the minimum height. |
| [void OH_ArkUI_LayoutConstraint_SetPercentReferenceWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setpercentreferencewidth) | Sets the width percentage reference. |
| [void OH_ArkUI_LayoutConstraint_SetPercentReferenceHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setpercentreferenceheight) | Sets the height percentage reference. |
| [void* OH_ArkUI_DrawContext_GetCanvas(ArkUI_DrawContext* context)](#oh_arkui_drawcontext_getcanvas) | Obtains the pointer to a canvas for drawing, which can be converted into the <b>OH_Drawing_Canvas</b> pointerin the <b>Drawing</b> module. |
| [ArkUI_IntSize OH_ArkUI_DrawContext_GetSize(ArkUI_DrawContext* context)](#oh_arkui_drawcontext_getsize) | Obtains the size of a drawing area. |
| [ArkUI_GridLayoutOptions* OH_ArkUI_GridLayoutOptions_Create()](#oh_arkui_gridlayoutoptions_create) | Creates <b>Grid</b> layout options. |
| [void OH_ArkUI_GridLayoutOptions_Dispose(ArkUI_GridLayoutOptions* option)](#oh_arkui_gridlayoutoptions_dispose) | Disposes of <b>Grid</b> layout options. |
| [int32_t OH_ArkUI_GridLayoutOptions_SetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t size)](#oh_arkui_gridlayoutoptions_setirregularindexes) | Sets the irregular grid item index array for the grid layout. |
| [int32_t OH_ArkUI_GridLayoutOptions_GetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t* size)](#oh_arkui_gridlayoutoptions_getirregularindexes) | Obtains the irregular grid item index array for the grid layout.When <b>OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback</b> is not set,the grid item specified in <b>irregularIndexes</b> occupies an entire row of the grid that scrolls vertically oran entire column of the grid that scrolls horizontally. |
| [void OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemSize (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_gridlayoutoptions_registergetirregularsizebyindexcallback) | Registers a callback to obtain the row and column span for the grid item at the specified index. |
| [void OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemRect (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_gridlayoutoptions_registergetrectbyindexcallback) | Registers a callback to obtain the starting row, starting column, row span,and column span for the grid item at the specified index. |
| [ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create()](#oh_arkui_waterflowsectionoption_create) | Creates water flow section configuration. |
| [void OH_ArkUI_WaterFlowSectionOption_Dispose(ArkUI_WaterFlowSectionOption* option)](#oh_arkui_waterflowsectionoption_dispose) | Destroys the pointer to a water flow section configuration. |
| [void OH_ArkUI_WaterFlowSectionOption_SetSize(ArkUI_WaterFlowSectionOption* option, int32_t size)](#oh_arkui_waterflowsectionoption_setsize) | Sets the FlowItem block configuration information array length. |
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetSize(ArkUI_WaterFlowSectionOption* option)](#oh_arkui_waterflowsectionoption_getsize) | Gets the FlowItem grouping configuration information array length. |
| [void OH_ArkUI_WaterFlowSectionOption_SetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t itemCount)](#oh_arkui_waterflowsectionoption_setitemcount) | Sets the number of items in a water flow section. |
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getitemcount) | Obtains the number of items in the water flow section that matches the specified index. |
| [void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex(ArkUI_WaterFlowSectionOption* option, int32_t index, float(\*callback)(int32_t itemIndex))](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex) | The FlowItem grouping configuration information getsthe spindle size ofthe specified Item based on flowItemIndex. |
| [void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData(ArkUI_WaterFlowSectionOption* option, int32_t index, void* userData, float (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata) | The FlowItem grouping configuration information getsthe spindle size ofthe specified Item based on flowItemIndex. |
| [void OH_ArkUI_WaterFlowSectionOption_SetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t crossCount)](#oh_arkui_waterflowsectionoption_setcrosscount) | Sets the number of columns (in a vertical layout) or rows (in a horizontal layout) of a water flow. |
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getcrosscount) | Obtains the number of columns (in a vertical layout) or rows (in a horizontal layout) in the water flow sectionthat matches the specified index. |
| [void OH_ArkUI_WaterFlowSectionOption_SetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float columnGap)](#oh_arkui_waterflowsectionoption_setcolumngap) | Sets the gap between columns in the specified water flow section. |
| [float OH_ArkUI_WaterFlowSectionOption_GetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getcolumngap) | Obtains the gap between columns in the water flow section that matches the specified index. |
| [void OH_ArkUI_WaterFlowSectionOption_SetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float rowGap)](#oh_arkui_waterflowsectionoption_setrowgap) | Sets the gap between rows in the specified water flow section. |
| [float OH_ArkUI_WaterFlowSectionOption_GetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getrowgap) | Obtains the gap between rows in the water flow section that matches the specified index. |
| [void OH_ArkUI_WaterFlowSectionOption_SetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index, float marginTop, float marginRight, float marginBottom, float marginLeft)](#oh_arkui_waterflowsectionoption_setmargin) | Sets the margins for the specified water flow section. |
| [ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getmargin) | Obtains the margins of the water flow section that matches the specified index. |
| [ArkUI_SwiperIndicator* OH_ArkUI_SwiperIndicator_Create(ArkUI_SwiperIndicatorType type)](#oh_arkui_swiperindicator_create) | Creates a navigation indicator. |
| [void OH_ArkUI_SwiperIndicator_Dispose(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_dispose) | Destroys the pointer to the indicator. |
| [void OH_ArkUI_SwiperIndicator_SetStartPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setstartposition) | Sets the distance between the navigation point and the start of the swiper. |
| [float OH_ArkUI_SwiperIndicator_GetStartPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getstartposition) | Obtains the distance between the navigation point and the start of the swiper. |
| [void OH_ArkUI_SwiperIndicator_SetTopPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_settopposition) | Sets the distance between the navigation point and the top of the swiper. |
| [float OH_ArkUI_SwiperIndicator_GetTopPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_gettopposition) | Obtains the distance between the navigation point and the top of the swiper. |
| [void OH_ArkUI_SwiperIndicator_SetEndPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setendposition) | Sets the distance between the navigation point and the right of the swiper. |
| [float OH_ArkUI_SwiperIndicator_GetEndPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getendposition) | Obtains the distance between the navigation point and the end of the swiper. |
| [void OH_ArkUI_SwiperIndicator_SetBottomPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setbottomposition) | Sets the distance between the navigation point and the bottom of the swiper. |
| [float OH_ArkUI_SwiperIndicator_GetBottomPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getbottomposition) | Obtains the distance between the navigation point and the bottom of the swiper. |
| [void OH_ArkUI_SwiperIndicator_SetItemWidth(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setitemwidth) | Sets the width of the dot for the dot indicator. |
| [float OH_ArkUI_SwiperIndicator_GetItemWidth(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getitemwidth) | Obtains the width of the dot for the dot indicator. |
| [void OH_ArkUI_SwiperIndicator_SetItemHeight(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setitemheight) | Sets the height of the dot for the dot indicator. |
| [float OH_ArkUI_SwiperIndicator_GetItemHeight(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getitemheight) | Obtains the height of the dot for the dot indicator. |
| [void OH_ArkUI_SwiperIndicator_SetSelectedItemWidth(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setselecteditemwidth) | Sets the width of the selected dot for the dot indicator. |
| [float OH_ArkUI_SwiperIndicator_GetSelectedItemWidth(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselecteditemwidth) | Obtains the width of the selected dot for the dot indicator. |
| [void OH_ArkUI_SwiperIndicator_SetSelectedItemHeight(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setselecteditemheight) | Sets the height of the selected dot for the dot indicator. |
| [float OH_ArkUI_SwiperIndicator_GetSelectedItemHeight(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselecteditemheight) | Obtains the height of the selected dot for the dot indicator. |
| [void OH_ArkUI_SwiperIndicator_SetMask(ArkUI_SwiperIndicator* indicator, int32_t mask)](#oh_arkui_swiperindicator_setmask) | Sets whether to display the mask style of the dot navigation indicator. |
| [int32_t OH_ArkUI_SwiperIndicator_GetMask(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getmask) | Obtains whether to display the mask style of the dot navigation indicator. |
| [void OH_ArkUI_SwiperIndicator_SetColor(ArkUI_SwiperIndicator* indicator, uint32_t color)](#oh_arkui_swiperindicator_setcolor) | Sets the color of the dot navigation indicator. |
| [uint32_t OH_ArkUI_SwiperIndicator_GetColor(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getcolor) | Obtains the color of the dot navigation indicator. |
| [void OH_ArkUI_SwiperIndicator_SetSelectedColor(ArkUI_SwiperIndicator* indicator, uint32_t selectedColor)](#oh_arkui_swiperindicator_setselectedcolor) | Sets the color of the selected dot for the navigation indicator. |
| [uint32_t OH_ArkUI_SwiperIndicator_GetSelectedColor(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselectedcolor) | Obtains the color of the selected dot for the dot navigation indicator. |
| [int32_t OH_ArkUI_SwiperIndicator_SetMaxDisplayCount(ArkUI_SwiperIndicator* indicator, int32_t maxDisplayCount)](#oh_arkui_swiperindicator_setmaxdisplaycount) | Sets the number of maxDisplayCount for the dot navigation indicator. |
| [int32_t OH_ArkUI_SwiperIndicator_GetMaxDisplayCount(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getmaxdisplaycount) | Obtains the number of maxDisplayCount for the dot navigation indicator. |
| [void OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator, int32_t ignoreSize)](#oh_arkui_swiperindicator_setignoresizeofbottom) | Sets whether to ignore the size of the indicator for [OH_ArkUI_SwiperIndicator_SetBottomPosition](capi-native-type-h.md#oh_arkui_swiperindicator_setbottomposition). |
| [int32_t OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getignoresizeofbottom) | Obtains whether to ignore the size of the indicator for [OH_ArkUI_SwiperIndicator_SetBottomPosition](capi-native-type-h.md#oh_arkui_swiperindicator_setbottomposition). |
| [void OH_ArkUI_SwiperIndicator_SetSpace(ArkUI_SwiperIndicator* indicator, float space)](#oh_arkui_swiperindicator_setspace) | Sets the space between the dots of the navigation indicator. |
| [float OH_ArkUI_SwiperIndicator_GetSpace(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getspace) | Obtains the space between the dots of the navigation indicator. |
| [ArkUI_SwiperDigitIndicator *OH_ArkUI_SwiperDigitIndicator_Create()](#oh_arkui_swiperdigitindicator_create) | Creates a digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_SetStartPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setstartposition) | Sets the distance between the digital indicator and the start of the swiper. |
| [float OH_ArkUI_SwiperDigitIndicator_GetStartPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getstartposition) | Gets the distance between the digital indicator and the start of the swiper. |
| [void OH_ArkUI_SwiperDigitIndicator_SetTopPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_settopposition) | Sets the distance between the digital indicator and the top of the swiper. |
| [float OH_ArkUI_SwiperDigitIndicator_GetTopPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_gettopposition) | Gets the distance between the digital indicator and the top of the swiper. |
| [void OH_ArkUI_SwiperDigitIndicator_SetEndPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setendposition) | Sets the distance between the digital indicator and the end of the swiper. |
| [float OH_ArkUI_SwiperDigitIndicator_GetEndPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getendposition) | Gets the distance between the digital indicator and the end of the swiper. |
| [void OH_ArkUI_SwiperDigitIndicator_SetBottomPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setbottomposition) | Sets the distance between the digital indicator and the bottom of the swiper. |
| [float OH_ArkUI_SwiperDigitIndicator_GetBottomPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getbottomposition) | Gets the distance between the digital indicator and the bottom of the swiper. |
| [void OH_ArkUI_SwiperDigitIndicator_SetFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t color)](#oh_arkui_swiperdigitindicator_setfontcolor) | Sets the font color of total count in the digital indicator. |
| [uint32_t OH_ArkUI_SwiperDigitIndicator_GetFontColor(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontcolor) | Gets the font color of total count in the digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t selectedColor)](#oh_arkui_swiperdigitindicator_setselectedfontcolor) | Sets the font color of selected index in the digital indicator. |
| [uint32_t OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontcolor) | Gets the font color of selected index in the digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_SetFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)](#oh_arkui_swiperdigitindicator_setfontsize) | Sets the font size of total count in the digital indicator. |
| [float OH_ArkUI_SwiperDigitIndicator_GetFontSize(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontsize) | Gets the font size of total count in the digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)](#oh_arkui_swiperdigitindicator_setselectedfontsize) | Sets the font size of selected index in the digital indicator. |
| [float OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontsize) | Gets the font size of selected index in the digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_SetFontWeight(ArkUI_SwiperDigitIndicator *indicator, ArkUI_FontWeight fontWeight)](#oh_arkui_swiperdigitindicator_setfontweight) | Sets the font weight of total count in the digital indicator. |
| [ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetFontWeight(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontweight) | Gets the font weight of total count in the digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontWeight(ArkUI_SwiperDigitIndicator *indicator, ArkUI_FontWeight selectedFontWeight)](#oh_arkui_swiperdigitindicator_setselectedfontweight) | Sets the font weight of selected index in the digital indicator. |
| [ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetSelectedFontWeight(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontweight) | Gets the font weight of selected index in the digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_Destroy(ArkUI_SwiperDigitIndicator *indicator)](#oh_arkui_swiperdigitindicator_destroy) | Destroys the digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator, int32_t ignoreSize)](#oh_arkui_swiperdigitindicator_setignoresizeofbottom) | Sets whether to ignore the size of the indicator for [OH_ArkUI_SwiperDigitIndicator_SetBottomPosition](capi-native-type-h.md#oh_arkui_swiperdigitindicator_setbottomposition). |
| [int32_t OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getignoresizeofbottom) | Obtains whether to ignore the size of the indicator for [OH_ArkUI_SwiperDigitIndicator_SetBottomPosition](capi-native-type-h.md#oh_arkui_swiperdigitindicator_setbottomposition). |
| [ArkUI_SwiperArrowStyle *OH_ArkUI_SwiperArrowStyle_Create()](#oh_arkui_swiperarrowstyle_create) | Creates a arrow style for swiper. |
| [void OH_ArkUI_SwiperArrowStyle_SetShowBackground(ArkUI_SwiperArrowStyle *arrowStyle, int32_t showBackground)](#oh_arkui_swiperarrowstyle_setshowbackground) | Sets whether to show the background for the arrow. |
| [int32_t OH_ArkUI_SwiperArrowStyle_GetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getshowbackground) | Gets whether to show the background for the arrow. |
| [void OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showSidebarMiddle)](#oh_arkui_swiperarrowstyle_setshowsidebarmiddle) | Sets the display position of the arrow. |
| [int32_t OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getshowsidebarmiddle) | Gets the display position of the arrow. |
| [void OH_ArkUI_SwiperArrowStyle_SetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle, float backgroundSize)](#oh_arkui_swiperarrowstyle_setbackgroundsize) | Sets the background size of the arrow. |
| [float OH_ArkUI_SwiperArrowStyle_GetBackgroundSize(ArkUI_SwiperArrowStyle *arrowStyle)](#oh_arkui_swiperarrowstyle_getbackgroundsize) | Gets the background size of the arrow. |
| [void OH_ArkUI_SwiperArrowStyle_Destroy(ArkUI_SwiperArrowStyle *arrowStyle)](#oh_arkui_swiperarrowstyle_destroy) | Destroys the arrow style. |
| [void OH_ArkUI_SwiperArrowStyle_SetBackgroundColor(ArkUI_SwiperArrowStyle *arrowStyle, uint32_t backgroundColor)](#oh_arkui_swiperarrowstyle_setbackgroundcolor) | Sets the background color of the arrow. |
| [uint32_t OH_ArkUI_SwiperArrowStyle_GetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getbackgroundcolor) | Gets the background color of the arrow. |
| [void OH_ArkUI_SwiperArrowStyle_SetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle, float arrowSize)](#oh_arkui_swiperarrowstyle_setarrowsize) | Sets the size of the arrow. |
| [float OH_ArkUI_SwiperArrowStyle_GetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getarrowsize) | Gets the size of the arrow. |
| [void OH_ArkUI_SwiperArrowStyle_SetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t arrowColor)](#oh_arkui_swiperarrowstyle_setarrowcolor) | Sets the color of the arrow. |
| [uint32_t OH_ArkUI_SwiperArrowStyle_GetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getarrowcolor) | Gets the color of the arrow. |
| [ArkUI_GuidelineOption* OH_ArkUI_GuidelineOption_Create(int32_t size)](#oh_arkui_guidelineoption_create) | Create auxiliary line information in the RelativeContaine container. |
| [void OH_ArkUI_GuidelineOption_Dispose(ArkUI_GuidelineOption* guideline)](#oh_arkui_guidelineoption_dispose) | Destroy auxiliary line information. |
| [void OH_ArkUI_GuidelineOption_SetId(ArkUI_GuidelineOption* guideline, const char* value, int32_t index)](#oh_arkui_guidelineoption_setid) | Set the Id of the auxiliary line. |
| [void OH_ArkUI_GuidelineOption_SetDirection(ArkUI_GuidelineOption* guideline, ArkUI_Axis value, int32_t index)](#oh_arkui_guidelineoption_setdirection) | Set the direction of the auxiliary line. |
| [void OH_ArkUI_GuidelineOption_SetPositionStart(ArkUI_GuidelineOption* guideline, float value, int32_t index)](#oh_arkui_guidelineoption_setpositionstart) | Set the distance from the left or top of the container. |
| [void OH_ArkUI_GuidelineOption_SetPositionEnd(ArkUI_GuidelineOption* guideline, float value, int32_t index)](#oh_arkui_guidelineoption_setpositionend) | Set the distance from the right or bottom of the container. |
| [const char* OH_ArkUI_GuidelineOption_GetId(ArkUI_GuidelineOption* guideline, int32_t index)](#oh_arkui_guidelineoption_getid) | Get the Id of the auxiliary line. |
| [ArkUI_Axis OH_ArkUI_GuidelineOption_GetDirection(ArkUI_GuidelineOption* guideline, int32_t index)](#oh_arkui_guidelineoption_getdirection) | Get the direction of the auxiliary line. |
| [float OH_ArkUI_GuidelineOption_GetPositionStart(ArkUI_GuidelineOption* guideline, int32_t index)](#oh_arkui_guidelineoption_getpositionstart) | Get the distance from the left or top of the container. |
| [float OH_ArkUI_GuidelineOption_GetPositionEnd(ArkUI_GuidelineOption* guideline, int32_t index)](#oh_arkui_guidelineoption_getpositionend) | Get the distance from the right side or bottom of the container. |
| [ArkUI_BarrierOption* OH_ArkUI_BarrierOption_Create(int32_t size)](#oh_arkui_barrieroption_create) | creates barrier information within the RelativeContaine container. |
| [void OH_ArkUI_BarrierOption_Dispose(ArkUI_BarrierOption* barrierStyle)](#oh_arkui_barrieroption_dispose) | Destroy barrier information. |
| [void OH_ArkUI_BarrierOption_SetId(ArkUI_BarrierOption* barrierStyle, const char* value, int32_t index)](#oh_arkui_barrieroption_setid) | Set the Id of the barrier. |
| [void OH_ArkUI_BarrierOption_SetDirection(ArkUI_BarrierOption* barrierStyle, ArkUI_BarrierDirection value, int32_t index)](#oh_arkui_barrieroption_setdirection) | Set the direction of the barrier. |
| [void OH_ArkUI_BarrierOption_SetReferencedId(ArkUI_BarrierOption* barrierStyle, const char* value, int32_t index)](#oh_arkui_barrieroption_setreferencedid) | Sets the dependent component of the barrier. |
| [const char* OH_ArkUI_BarrierOption_GetId(ArkUI_BarrierOption* barrierStyle, int32_t index)](#oh_arkui_barrieroption_getid) | Get the Id of the barrier. |
| [ArkUI_BarrierDirection OH_ArkUI_BarrierOption_GetDirection(ArkUI_BarrierOption* barrierStyle, int32_t index)](#oh_arkui_barrieroption_getdirection) | Gets the direction of the barrier. |
| [const char* OH_ArkUI_BarrierOption_GetReferencedId(ArkUI_BarrierOption* barrierStyle, int32_t index, int32_t referencedIndex)](#oh_arkui_barrieroption_getreferencedid) | Get the dependent components of the barrier. |
| [int32_t OH_ArkUI_BarrierOption_GetReferencedIdSize(ArkUI_BarrierOption* barrierStyle, int32_t index)](#oh_arkui_barrieroption_getreferencedidsize) | Gets the number of dependent components of the barrier. |
| [ArkUI_ContentTransitionEffect* OH_ArkUI_ContentTransitionEffect_Create(int32_t type)](#oh_arkui_contenttransitioneffect_create) | creates content switching animation effects. |
| [ArkUI_AlignmentRuleOption* OH_ArkUI_AlignmentRuleOption_Create()](#oh_arkui_alignmentruleoption_create) | creates alignment rule information for subcomponents in relative containers. |
| [void OH_ArkUI_AlignmentRuleOption_Dispose(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_dispose) | Destroys the alignment rule information of subcomponents in relative containers. |
| [void OH_ArkUI_AlignmentRuleOption_SetStart(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)](#oh_arkui_alignmentruleoption_setstart) | Set the start alignment parameter. |
| [void OH_ArkUI_AlignmentRuleOption_SetEnd(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)](#oh_arkui_alignmentruleoption_setend) | Set the end alignment parameter. |
| [void OH_ArkUI_AlignmentRuleOption_SetCenterHorizontal(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)](#oh_arkui_alignmentruleoption_setcenterhorizontal) | Set the parameters for horizontal center alignment. |
| [void OH_ArkUI_AlignmentRuleOption_SetTop(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)](#oh_arkui_alignmentruleoption_settop) | Set the parameters for top alignment. |
| [void OH_ArkUI_AlignmentRuleOption_SetBottom(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)](#oh_arkui_alignmentruleoption_setbottom) | Set the bottom alignment parameters. |
| [void OH_ArkUI_AlignmentRuleOption_SetCenterVertical(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)](#oh_arkui_alignmentruleoption_setcentervertical) | Set the parameters for vertical center alignment. |
| [void OH_ArkUI_AlignmentRuleOption_SetBiasHorizontal(ArkUI_AlignmentRuleOption* option, float horizontal)](#oh_arkui_alignmentruleoption_setbiashorizontal) | Sets the horizontal offset parameter of the component under the anchor point constraint. |
| [void OH_ArkUI_AlignmentRuleOption_SetBiasVertical(ArkUI_AlignmentRuleOption* option, float vertical)](#oh_arkui_alignmentruleoption_setbiasvertical) | Set the vertical offset parameter of the component under the anchor point constraint. |
| [const char* OH_ArkUI_AlignmentRuleOption_GetStartId(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getstartid) | Get the Id of the start-aligned parameter. |
| [ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetStartAlignment(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getstartalignment) | Gets the alignment of the start-aligned parameter. |
| [const char* OH_ArkUI_AlignmentRuleOption_GetEndId(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getendid) | Get the end alignment parameter. |
| [ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetEndAlignment(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getendalignment) | Get the end alignment parameter. |
| [const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdHorizontal(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getcenteridhorizontal) | Gets the parameters of horizontal center alignment. |
| [ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentHorizontal(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getcenteralignmenthorizontal) | Gets the parameters of horizontal center alignment. |
| [const char* OH_ArkUI_AlignmentRuleOption_GetTopId(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_gettopid) | Get the top-aligned parameters. |
| [ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetTopAlignment(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_gettopalignment) | Get the top-aligned parameters. |
| [const char* OH_ArkUI_AlignmentRuleOption_GetBottomId(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getbottomid) | Get the bottom alignment parameters. |
| [ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetBottomAlignment(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getbottomalignment) | Get the bottom alignment parameters. |
| [const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdVertical(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getcenteridvertical) | Gets the parameters of vertical center alignment. |
| [ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentVertical(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getcenteralignmentvertical) | Gets the parameters of vertical center alignment. |
| [float OH_ArkUI_AlignmentRuleOption_GetBiasHorizontal(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getbiashorizontal) | Get the bias value in the horizontal direction. |
| [float OH_ArkUI_AlignmentRuleOption_GetBiasVertical(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getbiasvertical) | Get the bias value in the vertical direction. |
| [ArkUI_ListItemSwipeActionItem* OH_ArkUI_ListItemSwipeActionItem_Create()](#oh_arkui_listitemswipeactionitem_create) | Create a configuration item for the ListitemSwipeActionItem interface settings. |
| [void OH_ArkUI_ListItemSwipeActionItem_Dispose(ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionitem_dispose) | Destroy the ListitemSwipeActionItem instance. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetContent(ArkUI_ListItemSwipeActionItem* item, ArkUI_NodeHandle node)](#oh_arkui_listitemswipeactionitem_setcontent) | Set the layout content of ListItem SwipeActionItem. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item, float distance)](#oh_arkui_listitemswipeactionitem_setactionareadistance) | Set the threshold for long-distance sliding deletion distance of components. |
| [float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionitem_getactionareadistance) | Obtain the threshold for long-distance sliding deletion distance of components. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonenteractionarea) | Set the event to be called when a sliding entry enters the deletion area. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonenteractionareawithuserdata) | Set the event triggered when a sliding entry enters the deletion area. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnAction(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonaction) | Set the event to be called when a component enters the long-range deletion area and deletes a ListItem. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonactionwithuserdata) | Set the event triggered when a component enters the long-range deletion area and deletes a ListItem. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonexitactionarea) | Set the event to be called when a sliding entry exits the deletion area. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonexitactionareawithuserdata) | Set the event triggered when a sliding entry exits the deletion area. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange(ArkUI_ListItemSwipeActionItem* item, void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState))](#oh_arkui_listitemswipeactionitem_setonstatechange) | Set the event triggered when the sliding state of a list item changes. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void* userData))](#oh_arkui_listitemswipeactionitem_setonstatechangewithuserdata) | Set the event triggered when the sliding state of a list item changes. |
| [ArkUI_ListItemSwipeActionOption* OH_ArkUI_ListItemSwipeActionOption_Create()](#oh_arkui_listitemswipeactionoption_create) | Create a configuration item for the ListitemSwipeActionOption interface settings. |
| [void OH_ArkUI_ListItemSwipeActionOption_Dispose(ArkUI_ListItemSwipeActionOption* option)](#oh_arkui_listitemswipeactionoption_dispose) | Destroy the ListitemSwipeActionOption instance. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetStart(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionoption_setstart) | Set the layout content on the left (vertical layout) or top (horizontal layout)of the ListItem SwipeActionItem. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetEnd(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionoption_setend) | Set the layout content on the right (vertical layout) or bottom (horizontal layout)of the ListItem SwipeActionItem. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeEdgeEffect edgeEffect)](#oh_arkui_listitemswipeactionoption_setedgeeffect) | Set the sliding effect. |
| [int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect(ArkUI_ListItemSwipeActionOption* option)](#oh_arkui_listitemswipeactionoption_getedgeeffect) | Get the sliding effect. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange(ArkUI_ListItemSwipeActionOption* option, void (\*callback)(float offset))](#oh_arkui_listitemswipeactionoption_setonoffsetchange) | The event called when the sliding operation offset changes. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData(ArkUI_ListItemSwipeActionOption* option, void* userData, void (\*callback)(float offset, void* userData))](#oh_arkui_listitemswipeactionoption_setonoffsetchangewithuserdata) | Set the event triggered when the sliding operation offset changes. |
| [ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()](#oh_arkui_listchildrenmainsizeoption_create) | Create configuration items for the ListChildrenMainSize interface settings. |
| [void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_dispose) | Destroy the ListChildrenMainSize instance. |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)](#oh_arkui_listchildrenmainsizeoption_setdefaultmainsize) | Set the default size of ChildrenMainSizeOption for the List component. |
| [float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_getdefaultmainsize) | Get the default size of ChildrenMainSizeOption for the List component. |
| [void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)](#oh_arkui_listchildrenmainsizeoption_resize) | Reset the array size of ChildrenMainSizeOption for the List component. |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)](#oh_arkui_listchildrenmainsizeoption_splice) | Resize the ChildrenMainSizeOption array operation on the List component. |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)](#oh_arkui_listchildrenmainsizeoption_updatesize) | Update the value of the ChildrenMainSizeOption array in the List component. |
| [float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)](#oh_arkui_listchildrenmainsizeoption_getmainsize) | Get the value of the ChildrenMainSizeOption array for the List component. |
| [ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString(char* src)](#oh_arkui_imageanimatorframeinfo_createfromstring) | Create a image frame from the image path. |
| [ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor(ArkUI_DrawableDescriptor* drawable)](#oh_arkui_imageanimatorframeinfo_createfromdrawabledescriptor) | Create a image frame from the drawable descriptor. |
| [void OH_ArkUI_ImageAnimatorFrameInfo_Dispose(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_dispose) | Destroy the pointer to the image frame. |
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t width)](#oh_arkui_imageanimatorframeinfo_setwidth) | Set the width of the image frame. |
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getwidth) | Get the width of the image frame. |
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t height)](#oh_arkui_imageanimatorframeinfo_setheight) | Set the height of the image frame. |
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getheight) | Get the height of the image frame. |
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t top)](#oh_arkui_imageanimatorframeinfo_settop) | Set the vertical coordinate of the image relative to the upper left corner of the widget. |
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_gettop) | Get the vertical coordinate of the image relative to the upper left corner of the widget. |
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t left)](#oh_arkui_imageanimatorframeinfo_setleft) | Set the horizontal coordinate of the image relative to the upper left corner of the widget. |
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getleft) | Get the horizontal coordinate of the image relative to the upper left corner of the widget. |
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t duration)](#oh_arkui_imageanimatorframeinfo_setduration) | Set the playback duration of the image frame. |
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getduration) | Get the playback duration of the image frame. |
| [ArkUI_AccessibilityState* OH_ArkUI_AccessibilityState_Create(void)](#oh_arkui_accessibilitystate_create) | Create accessibility state. |
| [void OH_ArkUI_AccessibilityState_Dispose(ArkUI_AccessibilityState* state)](#oh_arkui_accessibilitystate_dispose) | Dispose accessibility state. |
| [void OH_ArkUI_AccessibilityState_SetDisabled(ArkUI_AccessibilityState* state, int32_t isDisabled)](#oh_arkui_accessibilitystate_setdisabled) | Set accessibility state disabled. |
| [int32_t OH_ArkUI_AccessibilityState_IsDisabled(ArkUI_AccessibilityState* state)](#oh_arkui_accessibilitystate_isdisabled) | Get accessibility state disabled. |
| [void OH_ArkUI_AccessibilityState_SetSelected(ArkUI_AccessibilityState* state, int32_t isSelected)](#oh_arkui_accessibilitystate_setselected) | Set accessibility state selected. |
| [int32_t OH_ArkUI_AccessibilityState_IsSelected(ArkUI_AccessibilityState* state)](#oh_arkui_accessibilitystate_isselected) | Get accessibility state selected. |
| [void OH_ArkUI_AccessibilityState_SetCheckedState(ArkUI_AccessibilityState* state, int32_t checkedState)](#oh_arkui_accessibilitystate_setcheckedstate) | Set accessibility checked state. |
| [int32_t OH_ArkUI_AccessibilityState_GetCheckedState(ArkUI_AccessibilityState* state)](#oh_arkui_accessibilitystate_getcheckedstate) | Get accessibility checked state. |
| [ArkUI_AccessibilityValue* OH_ArkUI_AccessibilityValue_Create(void)](#oh_arkui_accessibilityvalue_create) | Create accessibility value. |
| [void OH_ArkUI_AccessibilityValue_Dispose(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_dispose) | Dispose accessibility value. |
| [void OH_ArkUI_AccessibilityValue_SetMin(ArkUI_AccessibilityValue* value, int32_t min)](#oh_arkui_accessibilityvalue_setmin) | Set accessibility minimum value. |
| [int32_t OH_ArkUI_AccessibilityValue_GetMin(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getmin) | Get accessibility minimum value. |
| [void OH_ArkUI_AccessibilityValue_SetMax(ArkUI_AccessibilityValue* value, int32_t max)](#oh_arkui_accessibilityvalue_setmax) | Set accessibility minimum value. |
| [int32_t OH_ArkUI_AccessibilityValue_GetMax(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getmax) | Get accessibility minimum value. |
| [void OH_ArkUI_AccessibilityValue_SetCurrent(ArkUI_AccessibilityValue* value, int32_t current)](#oh_arkui_accessibilityvalue_setcurrent) | Set accessibility current value. |
| [int32_t OH_ArkUI_AccessibilityValue_GetCurrent(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getcurrent) | Get accessibility current value. |
| [void OH_ArkUI_AccessibilityValue_SetRangeMin(ArkUI_AccessibilityValue* value, int32_t rangeMin)](#oh_arkui_accessibilityvalue_setrangemin) | Set accessibility minimum value. |
| [int32_t OH_ArkUI_AccessibilityValue_GetRangeMin(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getrangemin) | Get accessibility minimum value. |
| [void OH_ArkUI_AccessibilityValue_SetRangeMax(ArkUI_AccessibilityValue* value, int32_t rangeMax)](#oh_arkui_accessibilityvalue_setrangemax) | Set accessibility maximum value. |
| [int32_t OH_ArkUI_AccessibilityValue_GetRangeMax(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getrangemax) | Get accessibility maximum value. |
| [void OH_ArkUI_AccessibilityValue_SetRangeCurrent(ArkUI_AccessibilityValue* value, int32_t rangeCurrent)](#oh_arkui_accessibilityvalue_setrangecurrent) | Set accessibility current value. |
| [int32_t OH_ArkUI_AccessibilityValue_GetRangeCurrent(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getrangecurrent) | Get accessibility current value. |
| [void OH_ArkUI_AccessibilityValue_SetText(ArkUI_AccessibilityValue* value, const char* text)](#oh_arkui_accessibilityvalue_settext) | Set accessibility text value. |
| [const char* OH_ArkUI_AccessibilityValue_GetText(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_gettext) | Get accessibility text value. |
| [void OH_ArkUI_CustomProperty_Destroy(ArkUI_CustomProperty* handle)](#oh_arkui_customproperty_destroy) | Destroy the instance of Customs Property. |
| [const char* OH_ArkUI_CustomProperty_GetStringValue(ArkUI_CustomProperty* handle)](#oh_arkui_customproperty_getstringvalue) | Get custom attribute value information. |
| [const char* OH_ArkUI_HostWindowInfo_GetName(ArkUI_HostWindowInfo* info)](#oh_arkui_hostwindowinfo_getname) | Get window name from HostWindowInfo. |
| [void OH_ArkUI_HostWindowInfo_Destroy(ArkUI_HostWindowInfo* info)](#oh_arkui_hostwindowinfo_destroy) | Destroy the instance of HostWindowInfo. |
| [void OH_ArkUI_ActiveChildrenInfo_Destroy(ArkUI_ActiveChildrenInfo* handle)](#oh_arkui_activechildreninfo_destroy) | Destroy ActiveChildenInfo instance. |
| [ArkUI_NodeHandle OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex(ArkUI_ActiveChildrenInfo* handle, int32_t index)](#oh_arkui_activechildreninfo_getnodebyindex) | Retrieve the child nodes of ActiveChildenInfo with the structure index. |
| [int32_t OH_ArkUI_ActiveChildrenInfo_GetCount(ArkUI_ActiveChildrenInfo* handle)](#oh_arkui_activechildreninfo_getcount) | Retrieve the number of nodes within the structure of ActiveChildenInfo. |
| [ArkUI_CrossLanguageOption* OH_ArkUI_CrossLanguageOption_Create(void)](#oh_arkui_crosslanguageoption_create) | Create a cross-language option instance. |
| [void OH_ArkUI_CrossLanguageOption_Destroy(ArkUI_CrossLanguageOption* option)](#oh_arkui_crosslanguageoption_destroy) | Destroy the cross-language option instance. |
| [void OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus(ArkUI_CrossLanguageOption* option, bool enabled)](#oh_arkui_crosslanguageoption_setattributesettingstatus) | Enable the attribute setting in the cross-language option. |
| [bool OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus(ArkUI_CrossLanguageOption* option)](#oh_arkui_crosslanguageoption_getattributesettingstatus) | Get the attribute setting enable of the cross-language option. |
| [ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)](#oh_arkui_textpickerrangecontentarray_create) | Creates a TextPickerRangeContent instance. |
| [void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)](#oh_arkui_textpickerrangecontentarray_seticonatindex) | Sets the icon resource path or URI for one item in an {@link ArkUI_TextPickerRangeContentArray}. |
| [void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textpickerrangecontentarray_settextatindex) | Sets the display text for one item in an {@link ArkUI_TextPickerRangeContentArray}. |
| [void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)](#oh_arkui_textpickerrangecontentarray_destroy) | Releases an {@link ArkUI_TextPickerRangeContentArray} created by[OH_ArkUI_TextPickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textpickerrangecontentarray_create). |
| [ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)](#oh_arkui_textcascadepickerrangecontentarray_create) | Allocates one column level of an interconnected (cascade) TextPicker range. Use with range type[ARKUI_TEXTPICKER_RANGETYPE_CASCADE_RANGE_CONTENT](capi-native-type-h.md#arkui_textpickerrangetype). The returned pointer addresses a contiguous arrayof sibling nodes; each node may carry display text and an optional next-level range from[OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex](capi-native-type-h.md#oh_arkui_textcascadepickerrangecontentarray_setchildatindex). |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_settextatindex) | Sets the display text for one sibling node on a cascade TextPicker level. |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_setchildatindex) | Sets the childs info of items in a multi text picker ranges. |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy(ArkUI_TextCascadePickerRangeContentArray* handle)](#oh_arkui_textcascadepickerrangecontentarray_destroy) | Releases a cascade range level allocated with [OH_ArkUI_TextCascadePickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textcascadepickerrangecontentarray_create). |
| [ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()](#oh_arkui_embeddedcomponentoption_create) | Create an object for the EmbeddedComponent option. |
| [void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)](#oh_arkui_embeddedcomponentoption_dispose) | Destroy the object by EmbeddedComponent option. |
| [void OH_ArkUI_EmbeddedComponentOption_SetOnError(ArkUI_EmbeddedComponentOption* option, void (\*callback)(int32_t code, const char* name, const char* message))](#oh_arkui_embeddedcomponentoption_setonerror) | Set the onError of EmbeddedComponent. |
| [void OH_ArkUI_EmbeddedComponentOption_SetOnTerminated(ArkUI_EmbeddedComponentOption* option, void (\*callback)(int32_t code, AbilityBase_Want* want))](#oh_arkui_embeddedcomponentoption_setonterminated) | Set the onTerminated of EmbeddedComponent. |
| [int32_t OH_ArkUI_ListItemSwipeAction_Expand(ArkUI_NodeHandle node, ArkUI_ListItemSwipeActionDirection direction)](#oh_arkui_listitemswipeaction_expand) | Expand the swipe action. |
| [int32_t OH_ArkUI_ListItemSwipeAction_Collapse(ArkUI_NodeHandle node)](#oh_arkui_listitemswipeaction_collapse) | Collapse the swipe action. |
| [ArkUI_PositionEdges* OH_ArkUI_PositionEdges_Create()](#oh_arkui_positionedges_create) | Create an edge object for position attribute. |
| [ArkUI_PositionEdges* OH_ArkUI_PositionEdges_Copy(const ArkUI_PositionEdges* edges)](#oh_arkui_positionedges_copy) | Creates a deep copy of an edge object for position attribute. |
| [void OH_ArkUI_PositionEdges_Dispose(ArkUI_PositionEdges* edges)](#oh_arkui_positionedges_dispose) | Dispose an edge object for position attribute. |
| [void OH_ArkUI_PositionEdges_SetTop(ArkUI_PositionEdges* edges, float value)](#oh_arkui_positionedges_settop) | Sets the top edge of an edge object for position attribute. |
| [int32_t OH_ArkUI_PositionEdges_GetTop(ArkUI_PositionEdges* edges, float* value)](#oh_arkui_positionedges_gettop) | Gets the top edge of an edge object for position attribute. |
| [void OH_ArkUI_PositionEdges_SetLeft(ArkUI_PositionEdges* edges, float value)](#oh_arkui_positionedges_setleft) | Sets the left edge of an edge object for position attribute. |
| [int32_t OH_ArkUI_PositionEdges_GetLeft(ArkUI_PositionEdges* edges, float* value)](#oh_arkui_positionedges_getleft) | Gets the left edge of an edge object for position attribute. |
| [void OH_ArkUI_PositionEdges_SetBottom(ArkUI_PositionEdges* edges, float value)](#oh_arkui_positionedges_setbottom) | Sets the bottom edge of an edge object for position attribute. |
| [int32_t OH_ArkUI_PositionEdges_GetBottom(ArkUI_PositionEdges* edges, float* value)](#oh_arkui_positionedges_getbottom) | Gets the bottom edge of an edge object for position attribute. |
| [void OH_ArkUI_PositionEdges_SetRight(ArkUI_PositionEdges* edges, float value)](#oh_arkui_positionedges_setright) | Sets the right edge of an edge object for position attribute. |
| [int32_t OH_ArkUI_PositionEdges_GetRight(ArkUI_PositionEdges* edges, float* value)](#oh_arkui_positionedges_getright) | Gets the right edge of an edge object for position attribute. |
| [ArkUI_PixelRoundPolicy* OH_ArkUI_PixelRoundPolicy_Create()](#oh_arkui_pixelroundpolicy_create) | Create a policy object for PixelRound attribute. |
| [void OH_ArkUI_PixelRoundPolicy_Dispose(ArkUI_PixelRoundPolicy* policy)](#oh_arkui_pixelroundpolicy_dispose) | Dispose a policy object for PixelRound attribute. |
| [void OH_ArkUI_PixelRoundPolicy_SetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)](#oh_arkui_pixelroundpolicy_settop) | Sets the top edge of a policy object for PixelRound attribute. |
| [int32_t OH_ArkUI_PixelRoundPolicy_GetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)](#oh_arkui_pixelroundpolicy_gettop) | Gets the top edge of a policy object for PixelRound attribute. |
| [void OH_ArkUI_PixelRoundPolicy_SetStart(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)](#oh_arkui_pixelroundpolicy_setstart) | Sets the start edge of a policy object for PixelRound attribute. |
| [int32_t OH_ArkUI_PixelRoundPolicy_GetStart(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)](#oh_arkui_pixelroundpolicy_getstart) | Gets the start edge of a policy object for PixelRound attribute. |
| [void OH_ArkUI_PixelRoundPolicy_SetBottom(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)](#oh_arkui_pixelroundpolicy_setbottom) | Sets the bottom edge of a policy object for PixelRound attribute. |
| [int32_t OH_ArkUI_PixelRoundPolicy_GetBottom(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)](#oh_arkui_pixelroundpolicy_getbottom) | Gets the bottom edge of a policy object for PixelRound attribute. |
| [void OH_ArkUI_PixelRoundPolicy_SetEnd(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)](#oh_arkui_pixelroundpolicy_setend) | Sets the end edge of a policy object for PixelRound attribute. |
| [int32_t OH_ArkUI_PixelRoundPolicy_GetEnd(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)](#oh_arkui_pixelroundpolicy_getend) | Gets the end edge of a policy object for PixelRound attribute. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetContent(ArkUI_TextMenuItem* item, const char* content)](#oh_arkui_textmenuitem_setcontent) | Set text menu item title. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetContent(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textmenuitem_getcontent) | Get text menu item title. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetIcon(ArkUI_TextMenuItem* item, const char* icon)](#oh_arkui_textmenuitem_seticon) | Set text menu item icon. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetIcon(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textmenuitem_geticon) | Get text menu item icon. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetLabelInfo(ArkUI_TextMenuItem* item, const char* labelInfo)](#oh_arkui_textmenuitem_setlabelinfo) | Set text menu item label info for keyboard shortcut. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetLabelInfo(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textmenuitem_getlabelinfo) | Get text menu item label info for keyboard shortcut.. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetId(ArkUI_TextMenuItem* item, int32_t id)](#oh_arkui_textmenuitem_setid) | Set text menu item id. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetId(const ArkUI_TextMenuItem* item, int32_t* id)](#oh_arkui_textmenuitem_getid) | Get text menu item id. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_GetSize(ArkUI_TextMenuItemArray* items, int32_t* size)](#oh_arkui_textmenuitemarray_getsize) | Get the size of text menu items. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_GetItem(ArkUI_TextMenuItemArray* items, int32_t index, ArkUI_TextMenuItem** item)](#oh_arkui_textmenuitemarray_getitem) | Get text menu item at index. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Insert(ArkUI_TextMenuItemArray* items, ArkUI_TextMenuItem* item, int32_t index)](#oh_arkui_textmenuitemarray_insert) | Insert text menu item at index. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Erase(ArkUI_TextMenuItemArray* items, int32_t index)](#oh_arkui_textmenuitemarray_erase) | Erase text menu item at index. |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Clear(ArkUI_TextMenuItemArray* items)](#oh_arkui_textmenuitemarray_clear) | Clear all the items. |
| [ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnCreateMenuCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextCreateMenuCallback cb)](#oh_arkui_texteditmenuoptions_registeroncreatemenucallback) | Set the event to be called when text menu create. |
| [ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnPrepareMenuCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextPrepareMenuCallback cb)](#oh_arkui_texteditmenuoptions_registeronpreparemenucallback) | Set the event to be called when menu prepare. |
| [ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnMenuItemClickCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextMenuItemClickCallback cb)](#oh_arkui_texteditmenuoptions_registeronmenuitemclickcallback) | Set the event to be called when menu item click. |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetSpanType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextSpanType textSpanType)](#oh_arkui_textselectionmenuoptions_setspantype) | Sets the recognition types of a configuration object for selected text recognition. |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetSpanType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextSpanType* spanType)](#oh_arkui_textselectionmenuoptions_getspantype) | Gets the span type select menu options. |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetContentNode(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_NodeHandle node)](#oh_arkui_textselectionmenuoptions_setcontentnode) | Set custom text menu node of text. |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetContentNode(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_NodeHandle* node)](#oh_arkui_textselectionmenuoptions_getcontentnode) | Get custom text menu node of text. |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetResponseType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextResponseType responseType)](#oh_arkui_textselectionmenuoptions_setresponsetype) | Sets the recognition types of a configuration object for selected text recognition. |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetResponseType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextResponseType* responseType)](#oh_arkui_textselectionmenuoptions_getresponsetype) | Gets the response type select menu options. |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuShowCallback(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, void* userData, void (\*callback)(int32_t start, int32_t end, void* userData))](#oh_arkui_textselectionmenuoptions_registeronmenushowcallback) | Set the event to be called when selection menu show. |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuHideCallback(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, void* userData, void (\*callback)(int32_t start, int32_t end, void* userData))](#oh_arkui_textselectionmenuoptions_registeronmenuhidecallback) | Set the event to be called when selection menu hide. |
| [ArkUI_SelectionOptions* OH_ArkUI_SelectionOptions_Create()](#oh_arkui_selectionoptions_create) | Create selection options. |
| [void OH_ArkUI_SelectionOptions_Dispose(ArkUI_SelectionOptions* options)](#oh_arkui_selectionoptions_dispose) | Dispose selection options object. |
| [void OH_ArkUI_SelectionOptions_SetMenuPolicy(ArkUI_SelectionOptions* options, ArkUI_MenuPolicy menuPolicy)](#oh_arkui_selectionoptions_setmenupolicy) | Sets the menu policy for selection options. |
| [ArkUI_MenuPolicy OH_ArkUI_SelectionOptions_GetMenuPolicy(ArkUI_SelectionOptions* options)](#oh_arkui_selectionoptions_getmenupolicy) | Gets the menu policy of selection options. |
| [ArkUI_MotionPathOptions* OH_ArkUI_MotionPathOptions_Create()](#oh_arkui_motionpathoptions_create) | Create an object of the motion path options for path animation.In the newly created ArkUI_MotionPathOptions, the "path" value is an empty string, the "from" value is 0,the "to" value is 1, and the "rotatable" value is false. |
| [void OH_ArkUI_MotionPathOptions_Dispose(ArkUI_MotionPathOptions* options)](#oh_arkui_motionpathoptions_dispose) | Dispose the ArkUI_MotionPathOptions object. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetPath(ArkUI_MotionPathOptions* options, const char* svgPath)](#oh_arkui_motionpathoptions_setpath) | Sets the the motion path for the animation using an SVG path string. The path supports using "start" and"end" as placeholders for the starting and ending points, for example:"Mstart.x start.y L50 50 Lend.x end.y Z". Refer to the SVG path format for the path string.When set to an empty string, it is equivalent to not setting a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetPath(const ArkUI_MotionPathOptions* options, char* svgPathBuffer, const int32_t bufferSize, int32_t* writeLength)](#oh_arkui_motionpathoptions_getpath) | Gets the motion path string in the ArkUI_MotionPathOptions object. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetFrom(ArkUI_MotionPathOptions* options, const float from)](#oh_arkui_motionpathoptions_setfrom) | Sets the starting progress in the ArkUI_MotionPathOptions. Progress refers to the ratio of the length of thepath that has been traveled to the total length of the entire path. The value range is [0.0, 1.0], and the"from" value should be less than or equal to the "to" value; otherwise, an ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGEerror code will be returned. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetFrom(const ArkUI_MotionPathOptions* options, float* from)](#oh_arkui_motionpathoptions_getfrom) | Gets the starting progress in the ArkUI_MotionPathOptions object. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetTo(ArkUI_MotionPathOptions* options, const float to)](#oh_arkui_motionpathoptions_setto) | Sets the endpoint progress in the ArkUI_MotionPathOptions. Progress refers to the ratio of the length of thepath that has been traveled to the total length of the entire path. The value range is [0.0, 1.0], and the"from" value should be less than or equal to the "to" value; otherwise, an ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGEerror code will be returned. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetTo(const ArkUI_MotionPathOptions* options, float* to)](#oh_arkui_motionpathoptions_getto) | Gets the endpoint progress in the ArkUI_MotionPathOptions object. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetRotatable(ArkUI_MotionPathOptions* options, const bool rotatable)](#oh_arkui_motionpathoptions_setrotatable) | Sets the rotatable parameter in the ArkUI_MotionPathOptions. It indicates whether to rotate along the path.True means rotating along the path, while false means not rotating along the path. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetRotatable(const ArkUI_MotionPathOptions* options, bool* rotatable)](#oh_arkui_motionpathoptions_getrotatable) | Gets the rotatable parameter in the ArkUI_MotionPathOptions. |
| [ArkUI_SelectedDragPreviewStyle* OH_ArkUI_SelectedDragPreviewStyle_Create()](#oh_arkui_selecteddragpreviewstyle_create) | Create a configuration object for selected drag preview style. |
| [void OH_ArkUI_SelectedDragPreviewStyle_Dispose(ArkUI_SelectedDragPreviewStyle* config)](#oh_arkui_selecteddragpreviewstyle_dispose) | Dispose a configuration object for selected drag preview style. |
| [void OH_ArkUI_SelectedDragPreviewStyle_SetColor(ArkUI_SelectedDragPreviewStyle* config, uint32_t color)](#oh_arkui_selecteddragpreviewstyle_setcolor) | Sets the color of background for selected drag preview style. |
| [uint32_t OH_ArkUI_SelectedDragPreviewStyle_GetColor(ArkUI_SelectedDragPreviewStyle* config)](#oh_arkui_selecteddragpreviewstyle_getcolor) | Gets the color of background for selected drag preview style. |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_SetTextDecorationType(OH_ArkUI_DecorationStyleOptions* options, ArkUI_TextDecorationType type)](#oh_arkui_decorationstyleoptions_settextdecorationtype) | 设置装饰线样式的装饰类型。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_GetTextDecorationType(OH_ArkUI_DecorationStyleOptions* options, ArkUI_TextDecorationType* type)](#oh_arkui_decorationstyleoptions_gettextdecorationtype) | 获取装饰线样式的装饰类型。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_SetColor(OH_ArkUI_DecorationStyleOptions* options, uint32_t color)](#oh_arkui_decorationstyleoptions_setcolor) | 设置装饰线的颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_GetColor(OH_ArkUI_DecorationStyleOptions* options, uint32_t* color)](#oh_arkui_decorationstyleoptions_getcolor) | 获取装饰线的颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_SetTextDecorationStyle(OH_ArkUI_DecorationStyleOptions* options, ArkUI_TextDecorationStyle style)](#oh_arkui_decorationstyleoptions_settextdecorationstyle) | 设置装饰线的样式。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_GetTextDecorationStyle(OH_ArkUI_DecorationStyleOptions* options, ArkUI_TextDecorationStyle* style)](#oh_arkui_decorationstyleoptions_gettextdecorationstyle) | 获取装饰线的样式。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_SetThicknessScale(OH_ArkUI_DecorationStyleOptions* options, float thicknessScale)](#oh_arkui_decorationstyleoptions_setthicknessscale) | 设置装饰线的粗细缩放比例。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_GetThicknessScale(OH_ArkUI_DecorationStyleOptions* options, float* thicknessScale)](#oh_arkui_decorationstyleoptions_getthicknessscale) | 获取装饰线的粗细缩放比例。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_SetTypes(OH_ArkUI_TextDataDetectorConfig* config, const ArkUI_TextDataDetectorType* types, int32_t length)](#oh_arkui_textdatadetectorconfig_settypes) | 设置文本实体识别配置的类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_GetTypes(OH_ArkUI_TextDataDetectorConfig* config, ArkUI_TextDataDetectorType* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textdatadetectorconfig_gettypes) | 获取文本实体识别配置的类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_RegisterOnDetectResultUpdateCallback(OH_ArkUI_TextDataDetectorConfig* config, void* userData, void (\*callback)(const char* result, int32_t length, void* userData))](#oh_arkui_textdatadetectorconfig_registerondetectresultupdatecallback) | 设置文本实体识别结果更新回调。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_SetColor(OH_ArkUI_TextDataDetectorConfig* config, uint32_t color)](#oh_arkui_textdatadetectorconfig_setcolor) | 设置识别内容的颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_GetColor(OH_ArkUI_TextDataDetectorConfig* config, uint32_t* color)](#oh_arkui_textdatadetectorconfig_getcolor) | 获取识别内容的颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_SetDecorationStyleOptions(OH_ArkUI_TextDataDetectorConfig* config, OH_ArkUI_DecorationStyleOptions* decoration)](#oh_arkui_textdatadetectorconfig_setdecorationstyleoptions) | 设置识别内容的装饰样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_GetDecorationStyleOptions(OH_ArkUI_TextDataDetectorConfig* config, OH_ArkUI_DecorationStyleOptions* decoration)](#oh_arkui_textdatadetectorconfig_getdecorationstyleoptions) | 获取识别内容的装饰样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_SetEnablePreviewMenu(OH_ArkUI_TextDataDetectorConfig* config, bool enablePreviewMenu)](#oh_arkui_textdatadetectorconfig_setenablepreviewmenu) | 设置长按识别内容时是否显示预览菜单。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_GetEnablePreviewMenu(OH_ArkUI_TextDataDetectorConfig* config, bool* enablePreviewMenu)](#oh_arkui_textdatadetectorconfig_getenablepreviewmenu) | 获取长按识别内容时是否显示预览菜单。 |
| [ArkUI_ErrorCode OH_ArkUI_TextController_SetStyledString(OH_ArkUI_TextController* controller, ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_textcontroller_setstyledstring) | Set the StyledString of the text. |
| [OH_ArkUI_TextEditorPlaceholderOptions* OH_ArkUI_TextEditorPlaceholderOptions_Create()](#oh_arkui_texteditorplaceholderoptions_create) | 创建一个无输入时的提示文本的选项对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorPlaceholderOptions_Destroy](capi-native-type-h.md#oh_arkui_texteditorplaceholderoptions_destroy)销毁。 |
| [void OH_ArkUI_TextEditorPlaceholderOptions_Destroy(OH_ArkUI_TextEditorPlaceholderOptions* options)](#oh_arkui_texteditorplaceholderoptions_destroy) | 销毁无输入时的提示文本的选项对象。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetValue(OH_ArkUI_TextEditorPlaceholderOptions* options, const char* value)](#oh_arkui_texteditorplaceholderoptions_setvalue) | 设置无输入时的提示文本选项的提示文字。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetValue(OH_ArkUI_TextEditorPlaceholderOptions* options, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_texteditorplaceholderoptions_getvalue) | 获取无输入时的提示文本选项的提示文字。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontSize(OH_ArkUI_TextEditorPlaceholderOptions* options, float fontSize)](#oh_arkui_texteditorplaceholderoptions_setfontsize) | 设置无输入时的提示文本选项的字体大小。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontSize(OH_ArkUI_TextEditorPlaceholderOptions* options, float* fontSize)](#oh_arkui_texteditorplaceholderoptions_getfontsize) | 获取无输入时的提示文本选项的字体大小。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontWeight(OH_ArkUI_TextEditorPlaceholderOptions* options, uint32_t fontWeight)](#oh_arkui_texteditorplaceholderoptions_setfontweight) | 设置无输入时的提示文本选项的字体粗细。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontWeight(OH_ArkUI_TextEditorPlaceholderOptions* options, uint32_t* fontWeight)](#oh_arkui_texteditorplaceholderoptions_getfontweight) | 获取无输入时的提示文本选项的字体粗细。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontFamily(OH_ArkUI_TextEditorPlaceholderOptions* options, const char* fontFamily)](#oh_arkui_texteditorplaceholderoptions_setfontfamily) | 设置无输入时的提示文本选项的字体家族。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontFamily(OH_ArkUI_TextEditorPlaceholderOptions* options, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_texteditorplaceholderoptions_getfontfamily) | 获取无输入时的提示文本选项的字体家族。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontStyle(OH_ArkUI_TextEditorPlaceholderOptions* options, ArkUI_FontStyle fontStyle)](#oh_arkui_texteditorplaceholderoptions_setfontstyle) | 设置无输入时的提示文本选项的字体样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontStyle(OH_ArkUI_TextEditorPlaceholderOptions* options, ArkUI_FontStyle* fontStyle)](#oh_arkui_texteditorplaceholderoptions_getfontstyle) | 获取无输入时的提示文本选项的字体样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontColor(OH_ArkUI_TextEditorPlaceholderOptions* options, uint32_t fontColor)](#oh_arkui_texteditorplaceholderoptions_setfontcolor) | 设置无输入时的提示文本选项的字体颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontColor(OH_ArkUI_TextEditorPlaceholderOptions* options, uint32_t* fontColor)](#oh_arkui_texteditorplaceholderoptions_getfontcolor) | 获取无输入时的提示文本选项的字体颜色。 |
| [OH_ArkUI_TextEditorStyledStringController* OH_ArkUI_TextEditorStyledStringController_Create()](#oh_arkui_texteditorstyledstringcontroller_create) | 为文本编辑器创建一个属性字符串控制器对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorStyledStringController_Destroy](capi-native-type-h.md#oh_arkui_texteditorstyledstringcontroller_destroy)销毁。 |
| [void OH_ArkUI_TextEditorStyledStringController_Destroy(OH_ArkUI_TextEditorStyledStringController* controller)](#oh_arkui_texteditorstyledstringcontroller_destroy) | 销毁属性字符串控制器。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetCaretOffset(OH_ArkUI_TextEditorStyledStringController* controller, int32_t caretOffset)](#oh_arkui_texteditorstyledstringcontroller_setcaretoffset) | 通过属性字符串控制器设置光标偏移量。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetCaretOffset(OH_ArkUI_TextEditorStyledStringController* controller, int32_t* caretOffset)](#oh_arkui_texteditorstyledstringcontroller_getcaretoffset) | 通过属性字符串控制器获取光标索引位置。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetSelection(OH_ArkUI_TextEditorStyledStringController* controller, uint32_t start, uint32_t end, ArkUI_MenuPolicy menuPolicy)](#oh_arkui_texteditorstyledstringcontroller_setselection) | 通过属性字符串控制器设置选中区域。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_IsEditing(OH_ArkUI_TextEditorStyledStringController* controller, bool* isEditing)](#oh_arkui_texteditorstyledstringcontroller_isediting) | 通过属性字符串控制器获取文本编辑器的编辑状态。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_StopEditing(OH_ArkUI_TextEditorStyledStringController* controller)](#oh_arkui_texteditorstyledstringcontroller_stopediting) | 通过属性字符串控制器退出文本编辑器的编辑状态。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetPreviewText(OH_ArkUI_TextEditorStyledStringController* controller, uint32_t* offset, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_texteditorstyledstringcontroller_getpreviewtext) | 通过属性字符串控制器获取预上屏文本内容。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetCaretRect(OH_ArkUI_TextEditorStyledStringController* controller, ArkUI_Rect* rect)](#oh_arkui_texteditorstyledstringcontroller_getcaretrect) | 通过属性字符串控制器获取光标矩形区域。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_DeleteBackward(OH_ArkUI_TextEditorStyledStringController* controller)](#oh_arkui_texteditorstyledstringcontroller_deletebackward) | 通过属性字符串控制器删除字符。没有内容被选中时，删除当前光标位置前的1个字符。有内容被选中时，删除选中内容。 |
| [OH_ArkUI_TextEditorParagraphStyle* OH_ArkUI_TextEditorParagraphStyle_Create()](#oh_arkui_texteditorparagraphstyle_create) | 为文本编辑器创建一个段落样式对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorParagraphStyle_Destroy](capi-native-type-h.md#oh_arkui_texteditorparagraphstyle_destroy)销毁。 |
| [void OH_ArkUI_TextEditorParagraphStyle_Destroy(OH_ArkUI_TextEditorParagraphStyle* style)](#oh_arkui_texteditorparagraphstyle_destroy) | 销毁段落样式对象。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetTextAlign(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextAlignment align)](#oh_arkui_texteditorparagraphstyle_settextalign) | 设置段落样式中的文本对齐方式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetTextAlign(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextAlignment* align)](#oh_arkui_texteditorparagraphstyle_gettextalign) | 获取段落样式中的文本对齐方式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetLeadingMarginPixelMap(OH_ArkUI_TextEditorParagraphStyle* style, struct OH_PixelmapNative* pixelmap)](#oh_arkui_texteditorparagraphstyle_setleadingmarginpixelmap) | 设置段落样式中段落缩进的像素图。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetLeadingMarginPixelMap(OH_ArkUI_TextEditorParagraphStyle* style, struct OH_PixelmapNative** pixelmap)](#oh_arkui_texteditorparagraphstyle_getleadingmarginpixelmap) | 获取段落样式中段落缩进的像素图。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetLeadingMarginWidth(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t width)](#oh_arkui_texteditorparagraphstyle_setleadingmarginwidth) | 设置段落样式中段落缩进的宽度。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetLeadingMarginWidth(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t* width)](#oh_arkui_texteditorparagraphstyle_getleadingmarginwidth) | 获取段落样式中段落缩进的宽度。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetLeadingMarginHeight(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t height)](#oh_arkui_texteditorparagraphstyle_setleadingmarginheight) | 设置段落样式中段落缩进的高度。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetLeadingMarginHeight(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t* height)](#oh_arkui_texteditorparagraphstyle_getleadingmarginheight) | 获取段落样式中段落缩进的高度。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetWordBreak(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_WordBreak wordBreak)](#oh_arkui_texteditorparagraphstyle_setwordbreak) | 设置段落样式的断字方式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetWordBreak(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_WordBreak* wordBreak)](#oh_arkui_texteditorparagraphstyle_getwordbreak) | 获取段落样式的断字方式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetLineBreakStrategy(OH_ArkUI_TextEditorParagraphStyle* style, OH_ArkUI_LineBreakStrategy lineBreakStrategy)](#oh_arkui_texteditorparagraphstyle_setlinebreakstrategy) | 设置段落样式的换行策略。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetLineBreakStrategy(OH_ArkUI_TextEditorParagraphStyle* style, OH_ArkUI_LineBreakStrategy* lineBreakStrategy)](#oh_arkui_texteditorparagraphstyle_getlinebreakstrategy) | 获取段落样式的换行策略。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetParagraphSpacing(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t paragraphSpacing)](#oh_arkui_texteditorparagraphstyle_setparagraphspacing) | 设置段落样式的段落间距。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetParagraphSpacing(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t* paragraphSpacing)](#oh_arkui_texteditorparagraphstyle_getparagraphspacing) | 获取段落样式的段落间距。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetTextVerticalAlign(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextVerticalAlignment verticalAlignment)](#oh_arkui_texteditorparagraphstyle_settextverticalalign) | 设置段落样式的文本垂直对齐方式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetTextVerticalAlign(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextVerticalAlignment* verticalAlignment)](#oh_arkui_texteditorparagraphstyle_gettextverticalalign) | 获取段落样式的文本垂直对齐方式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetTextDirection(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextDirection textDirection)](#oh_arkui_texteditorparagraphstyle_settextdirection) | 设置段落样式的文本方向。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetTextDirection(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextDirection* textDirection)](#oh_arkui_texteditorparagraphstyle_gettextdirection) | 获取段落样式的文本方向。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetTypingParagraphStyle(OH_ArkUI_TextEditorStyledStringController* controller, OH_ArkUI_TextEditorParagraphStyle* style)](#oh_arkui_texteditorstyledstringcontroller_settypingparagraphstyle) | 通过属性字符串控制器设置预设段落样式。 |
| [OH_ArkUI_ShadowOptions* OH_ArkUI_ShadowOptions_Create()](#oh_arkui_shadowoptions_create) | 创建一个阴影选项对象。当该对象不再使用时，请调用[OH_ArkUI_ShadowOptions_Destroy](capi-native-type-h.md#oh_arkui_shadowoptions_destroy)销毁。 |
| [void OH_ArkUI_ShadowOptions_Destroy(OH_ArkUI_ShadowOptions* options)](#oh_arkui_shadowoptions_destroy) | 销毁阴影选项对象。 |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetRadius(OH_ArkUI_ShadowOptions* options, float radius)](#oh_arkui_shadowoptions_setradius) | 设置阴影选项的模糊半径。 |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetRadius(OH_ArkUI_ShadowOptions* options, float* radius)](#oh_arkui_shadowoptions_getradius) | 获取阴影选项的模糊半径。 |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetType(OH_ArkUI_ShadowOptions* options, ArkUI_ShadowType type)](#oh_arkui_shadowoptions_settype) | 设置阴影选项的阴影类型。 |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetType(OH_ArkUI_ShadowOptions* options, ArkUI_ShadowType* type)](#oh_arkui_shadowoptions_gettype) | 获取阴影选项的阴影类型。 |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetColor(OH_ArkUI_ShadowOptions* options, uint32_t color)](#oh_arkui_shadowoptions_setcolor) | 设置阴影选项的阴影颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetColor(OH_ArkUI_ShadowOptions* options, uint32_t* color)](#oh_arkui_shadowoptions_getcolor) | 获取阴影选项的阴影颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetOffsetX(OH_ArkUI_ShadowOptions* options, float offsetX)](#oh_arkui_shadowoptions_setoffsetx) | 设置阴影在x轴上的偏移量。 |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetOffsetX(OH_ArkUI_ShadowOptions* options, float* offsetX)](#oh_arkui_shadowoptions_getoffsetx) | 获取阴影在x轴上的偏移量。 |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetOffsetY(OH_ArkUI_ShadowOptions* options, float offsetY)](#oh_arkui_shadowoptions_setoffsety) | 设置阴影在y轴上的偏移量。 |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetOffsetY(OH_ArkUI_ShadowOptions* options, float* offsetY)](#oh_arkui_shadowoptions_getoffsety) | 获取阴影在y轴上的偏移量。 |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetFill(OH_ArkUI_ShadowOptions* options, bool isFill)](#oh_arkui_shadowoptions_setfill) | 设置是否用阴影填充组件内部。 |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetFill(OH_ArkUI_ShadowOptions* options, bool* isFill)](#oh_arkui_shadowoptions_getfill) | 获取是否用阴影填充组件内部。 |
| [OH_ArkUI_TextEditorTextStyle* OH_ArkUI_TextEditorTextStyle_Create()](#oh_arkui_texteditortextstyle_create) | 创建一个文本样式对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorTextStyle_Destroy](capi-native-type-h.md#oh_arkui_texteditortextstyle_destroy)销毁。 |
| [void OH_ArkUI_TextEditorTextStyle_Destroy(OH_ArkUI_TextEditorTextStyle* style)](#oh_arkui_texteditortextstyle_destroy) | 销毁文本样式对象。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontColor(OH_ArkUI_TextEditorTextStyle* style, uint32_t color)](#oh_arkui_texteditortextstyle_setfontcolor) | 设置文本样式的字体颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontColor(OH_ArkUI_TextEditorTextStyle* style, uint32_t* color)](#oh_arkui_texteditortextstyle_getfontcolor) | 获取文本样式的字体颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontSize(OH_ArkUI_TextEditorTextStyle* style, float size)](#oh_arkui_texteditortextstyle_setfontsize) | 设置文本样式的字体大小。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontSize(OH_ArkUI_TextEditorTextStyle* style, float* size)](#oh_arkui_texteditortextstyle_getfontsize) | 获取文本样式的字体大小。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontStyle(OH_ArkUI_TextEditorTextStyle* style, ArkUI_FontStyle fontStyle)](#oh_arkui_texteditortextstyle_setfontstyle) | 设置文本样式的字体样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontStyle(OH_ArkUI_TextEditorTextStyle* style, ArkUI_FontStyle* fontStyle)](#oh_arkui_texteditortextstyle_getfontstyle) | 获取文本样式的字体样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontWeight(OH_ArkUI_TextEditorTextStyle* style, uint32_t fontWeight)](#oh_arkui_texteditortextstyle_setfontweight) | 设置文本样式的字体粗细。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontWeight(OH_ArkUI_TextEditorTextStyle* style, uint32_t* fontWeight)](#oh_arkui_texteditortextstyle_getfontweight) | 获取文本样式的字体粗细。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontFamily(OH_ArkUI_TextEditorTextStyle* style, const char* fontFamily)](#oh_arkui_texteditortextstyle_setfontfamily) | 设置文本样式的字体家族。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontFamily(OH_ArkUI_TextEditorTextStyle* style, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_texteditortextstyle_getfontfamily) | 获取文本样式的字体家族。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetDecoration(OH_ArkUI_TextEditorTextStyle* style, OH_ArkUI_DecorationStyleOptions* options)](#oh_arkui_texteditortextstyle_setdecoration) | 设置文本样式的文本装饰选项。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetDecoration(OH_ArkUI_TextEditorTextStyle* style, OH_ArkUI_DecorationStyleOptions* options)](#oh_arkui_texteditortextstyle_getdecoration) | 获取文本样式的文本装饰选项。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetTextShadows(OH_ArkUI_TextEditorTextStyle* style, const OH_ArkUI_ShadowOptions** options, int32_t length)](#oh_arkui_texteditortextstyle_settextshadows) | 设置文本样式的文本阴影选项。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetTextShadows(OH_ArkUI_TextEditorTextStyle* style, OH_ArkUI_ShadowOptions** shadowOptions, uint32_t shadowOptionsSize, uint32_t* writeLength)](#oh_arkui_texteditortextstyle_gettextshadows) | 获取文本样式的文本阴影选项。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetLineHeight(OH_ArkUI_TextEditorTextStyle* style, int32_t lineHeight)](#oh_arkui_texteditortextstyle_setlineheight) | 设置文本样式的文本行高。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetLineHeight(OH_ArkUI_TextEditorTextStyle* style, int32_t* lineHeight)](#oh_arkui_texteditortextstyle_getlineheight) | 获取文本样式的文本行高。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetLetterSpacing(OH_ArkUI_TextEditorTextStyle* style, int32_t letterSpacing)](#oh_arkui_texteditortextstyle_setletterspacing) | 设置文本样式的字符间距。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetLetterSpacing(OH_ArkUI_TextEditorTextStyle* style, int32_t* letterSpacing)](#oh_arkui_texteditortextstyle_getletterspacing) | 获取文本样式的字符间距。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontFeature(OH_ArkUI_TextEditorTextStyle* style, const char* fontFeature)](#oh_arkui_texteditortextstyle_setfontfeature) | 设置文本样式的文字特性效果，比如数字等宽的特性。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontFeature(OH_ArkUI_TextEditorTextStyle* style, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_texteditortextstyle_getfontfeature) | 获取文本样式的文字特性效果，比如数字等宽的特性。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetHalfLeading(OH_ArkUI_TextEditorTextStyle* style, bool halfLeading)](#oh_arkui_texteditortextstyle_sethalfleading) | 设置文本样式中文本是否将行间距平分至行的顶部与底部。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetHalfLeading(OH_ArkUI_TextEditorTextStyle* style, bool* halfLeading)](#oh_arkui_texteditortextstyle_gethalfleading) | 获取文本样式中文本是否将行间距平分至行的顶部与底部。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetTextBackgroundColor(OH_ArkUI_TextEditorTextStyle* style, uint32_t color)](#oh_arkui_texteditortextstyle_settextbackgroundcolor) | 设置文本样式中的文本背景颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetTextBackgroundColor(OH_ArkUI_TextEditorTextStyle* style, uint32_t* color)](#oh_arkui_texteditortextstyle_gettextbackgroundcolor) | 获取文本样式中的文本背景颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetTextBackgroundRadius(OH_ArkUI_TextEditorTextStyle* style, float topLeft, float topRight, float bottomLeft, float bottomRight)](#oh_arkui_texteditortextstyle_settextbackgroundradius) | 设置文本样式中文本背景的圆角半径。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetTextBackgroundRadius(OH_ArkUI_TextEditorTextStyle* style, float* topLeft, float* topRight, float* bottomLeft, float* bottomRight)](#oh_arkui_texteditortextstyle_gettextbackgroundradius) | 获取文本样式中文本背景的圆角半径。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetTypingStyle(OH_ArkUI_TextEditorStyledStringController* controller, OH_ArkUI_TextEditorTextStyle* style)](#oh_arkui_texteditorstyledstringcontroller_settypingstyle) | 通过属性字符串控制器设置预设输入样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetTypingStyle(OH_ArkUI_TextEditorStyledStringController* controller, OH_ArkUI_TextEditorTextStyle* style)](#oh_arkui_texteditorstyledstringcontroller_gettypingstyle) | 通过属性字符串控制器获取预设输入样式。 |
| [OH_ArkUI_TextEditorSelectionMenuOptions* OH_ArkUI_TextEditorSelectionMenuOptions_Create()](#oh_arkui_texteditorselectionmenuoptions_create) | 创建一个文本编辑器文本选择菜单选项对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorSelectionMenuOptions_Destroy](capi-native-type-h.md#oh_arkui_texteditorselectionmenuoptions_destroy)销毁。 |
| [void OH_ArkUI_TextEditorSelectionMenuOptions_Destroy(OH_ArkUI_TextEditorSelectionMenuOptions* options)](#oh_arkui_texteditorselectionmenuoptions_destroy) | 销毁文本编辑器文本选择菜单选项对象。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetSpanType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextEditorSpanType textEditorSpanType)](#oh_arkui_texteditorselectionmenuoptions_setspantype) | 设置文本编辑器中文本选择菜单的span的类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetSpanType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextEditorSpanType* textEditorSpanType)](#oh_arkui_texteditorselectionmenuoptions_getspantype) | 获取文本编辑器中文本选择菜单的span的类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetContentNode(OH_ArkUI_TextEditorSelectionMenuOptions* options, ArkUI_NodeHandle node)](#oh_arkui_texteditorselectionmenuoptions_setcontentnode) | 设置文本编辑器中文本选择菜单的内容节点。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetContentNode(OH_ArkUI_TextEditorSelectionMenuOptions* options, ArkUI_NodeHandle* node)](#oh_arkui_texteditorselectionmenuoptions_getcontentnode) | 获取文本编辑器中文本选择菜单的内容节点。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetResponseType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextEditorResponseType responseType)](#oh_arkui_texteditorselectionmenuoptions_setresponsetype) | 设置文本编辑器中文本选择菜单的响应类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetResponseType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextEditorResponseType* responseType)](#oh_arkui_texteditorselectionmenuoptions_getresponsetype) | 获取文本编辑器中文本选择菜单的响应类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetMenuType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextMenuType menuType)](#oh_arkui_texteditorselectionmenuoptions_setmenutype) | 设置文本编辑器中文本选择菜单的类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetMenuType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextMenuType* menuType)](#oh_arkui_texteditorselectionmenuoptions_getmenutype) | 获取文本编辑器中文本选择菜单的类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuShowCallback(OH_ArkUI_TextEditorSelectionMenuOptions* options, void* userData, void (\*callback)(int32_t start, int32_t end, void* callbackUserData))](#oh_arkui_texteditorselectionmenuoptions_registeronmenushowcallback) | 设置文本选择菜单显示时触发的事件。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuHideCallback(OH_ArkUI_TextEditorSelectionMenuOptions* options, void* userData, void (\*callback)(int32_t start, int32_t end, void* callbackUserData))](#oh_arkui_texteditorselectionmenuoptions_registeronmenuhidecallback) | 设置文本选择菜单隐藏时触发的事件。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuAppearCallback(OH_ArkUI_TextEditorSelectionMenuOptions* options, void* userData, void (\*callback)(int32_t start, int32_t end, void* callbackUserData))](#oh_arkui_texteditorselectionmenuoptions_registeronmenuappearcallback) | 设置文本选择菜单出现时触发的事件。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuDisappearCallback(OH_ArkUI_TextEditorSelectionMenuOptions* options, void* userData, void (\*callback)(void* callbackUserData))](#oh_arkui_texteditorselectionmenuoptions_registeronmenudisappearcallback) | 设置文本选择菜单消失时触发的事件。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetHapticFeedbackMode(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_HapticFeedbackMode mode)](#oh_arkui_texteditorselectionmenuoptions_sethapticfeedbackmode) | 设置文本编辑器中文本选择菜单的触觉反馈模式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetHapticFeedbackMode(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_HapticFeedbackMode* mode)](#oh_arkui_texteditorselectionmenuoptions_gethapticfeedbackmode) | 获取文本编辑器中文本选择菜单的触觉反馈模式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_CloseSelectionMenu(OH_ArkUI_TextEditorStyledStringController* controller)](#oh_arkui_texteditorstyledstringcontroller_closeselectionmenu) | 关闭文本编辑器属性字符串控制器的文本选择菜单。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetSelection(const OH_ArkUI_TextEditorStyledStringController* controller, uint32_t* start, uint32_t* end)](#oh_arkui_texteditorstyledstringcontroller_getselection) | 通过属性字符串控制器获取选中区域。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetStyledString(const OH_ArkUI_TextEditorStyledStringController* controller, const ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_texteditorstyledstringcontroller_setstyledstring) | 通过属性字符串控制器设置显示的属性字符串。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetStyledString(const OH_ArkUI_TextEditorStyledStringController* controller, ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_texteditorstyledstringcontroller_getstyledstring) | 通过属性字符串控制器获取显示的属性字符串。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetStyledPlaceholder(const OH_ArkUI_TextEditorStyledStringController* controller, const ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_texteditorstyledstringcontroller_setstyledplaceholder) | 通过属性字符串控制器设置属性字符串样式的提示文本。 |
| [ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)](#oh_arkui_pickerindicatorstyle_create) | Create the ArkUI_PickerIndicatorStyle instance. |
| [void OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)](#oh_arkui_pickerindicatorstyle_dispose) | Destroy the ArkUI_PickerIndicatorStyle instance. |
| [ArkUI_ErrorCode OH_ArkUI_PickerIndicatorStyle_ConfigureBackground(ArkUI_PickerIndicatorStyle* style, ArkUI_PickerIndicatorBackground* background)](#oh_arkui_pickerindicatorstyle_configurebackground) | Set the parameters of background style. |
| [ArkUI_ErrorCode OH_ArkUI_PickerIndicatorStyle_ConfigureDivider(ArkUI_PickerIndicatorStyle* style, ArkUI_PickerIndicatorDivider* divider)](#oh_arkui_pickerindicatorstyle_configuredivider) | Set the parameters of divider style. |
| [ArkUI_Matrix4ScaleOptions* OH_ArkUI_Matrix4ScaleOptions_Create()](#oh_arkui_matrix4scaleoptions_create) | Create an object of ArkUI_Matrix4ScaleOptions.In the newly created options, the default values for the scaling coefficients in the x, y and z directionsare 1, and the default values for centerX, centerY are 0. |
| [void OH_ArkUI_Matrix4ScaleOptions_Dispose(ArkUI_Matrix4ScaleOptions* options)](#oh_arkui_matrix4scaleoptions_dispose) | Disposes the ArkUI_Matrix4ScaleOptions object. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetX(ArkUI_Matrix4ScaleOptions* options, const float scaleX)](#oh_arkui_matrix4scaleoptions_setx) | Set the scaling factor in the x direction in ArkUI_Matrix4ScaleOptions. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetX(const ArkUI_Matrix4ScaleOptions* options, float* scaleX)](#oh_arkui_matrix4scaleoptions_getx) | Get the scaling factor in the x direction in ArkUI_Matrix4ScaleOptions.If the value of x is never set, its default value is 1. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetY(ArkUI_Matrix4ScaleOptions* options, const float scaleY)](#oh_arkui_matrix4scaleoptions_sety) | Set the scaling factor in the y direction in ArkUI_Matrix4ScaleOptions. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetY(const ArkUI_Matrix4ScaleOptions* options, float* scaleY)](#oh_arkui_matrix4scaleoptions_gety) | Get the scaling factor in the y direction in ArkUI_Matrix4ScaleOptions.If the value of y is never set, its default value is 1. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetZ(ArkUI_Matrix4ScaleOptions* options, const float scaleZ)](#oh_arkui_matrix4scaleoptions_setz) | Set the scaling factor in the z direction in ArkUI_Matrix4ScaleOptions. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetZ(const ArkUI_Matrix4ScaleOptions* options, float* scaleZ)](#oh_arkui_matrix4scaleoptions_getz) | Get the scaling factor in the z direction in ArkUI_Matrix4ScaleOptions.If the value of z is never set, its default value is 1. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetCenterX(ArkUI_Matrix4ScaleOptions* options, const float centerX)](#oh_arkui_matrix4scaleoptions_setcenterx) | Set x offset relative to the transformation center. 0 means no additional x-direction offset from thetransformation center. The unit is px. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetCenterX(const ArkUI_Matrix4ScaleOptions* options, float* centerX)](#oh_arkui_matrix4scaleoptions_getcenterx) | Get the value of centerX from the options, which represents the x-direction offset relative to thetransformation center. The unit is px. If the value of centerX is never set, its default value is 0. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetCenterY(ArkUI_Matrix4ScaleOptions* options, const float centerY)](#oh_arkui_matrix4scaleoptions_setcentery) | Set y offset relative to the transformation center. 0 means no additional y-direction offset from thetransformation center. The unit is px. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetCenterY(const ArkUI_Matrix4ScaleOptions* options, float* centerY)](#oh_arkui_matrix4scaleoptions_getcentery) | Get the value of centerY from the options, which represents the y-direction offset relative to thetransformation center. The unit is px. If the value of centerY is never set, its default value is 0. |
| [ArkUI_Matrix4RotationOptions* OH_ArkUI_Matrix4RotationOptions_Create()](#oh_arkui_matrix4rotationoptions_create) | Create an object of ArkUI_Matrix4RotationOptions.In the newly created options, the x, y, and z values in the direction vector specifying the rotation axisare undetermined; The default values for centerX, centerY are 0; The default value for angle is 0.If none of x, y, z are specified, it is equivalent to x=0, y=0, z=1, which means rotation around the z-axis.Once any one of x, y, z is specified, the remaining unspecified values are equivalent to 0. |
| [void OH_ArkUI_Matrix4RotationOptions_Dispose(ArkUI_Matrix4RotationOptions* options)](#oh_arkui_matrix4rotationoptions_dispose) | Disposes the ArkUI_Matrix4RotationOptions object. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetX(ArkUI_Matrix4RotationOptions* options, const float x)](#oh_arkui_matrix4rotationoptions_setx) | Set the value of the direction vector for the x-axis direction in ArkUI_Matrix4RotationOptions. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetX(const ArkUI_Matrix4RotationOptions* options, float* x)](#oh_arkui_matrix4rotationoptions_getx) | Get the value of the direction vector for the x-axis direction in ArkUI_Matrix4RotationOptions.If the value of x is never set, its value will be undefined, so the function will returnARKUI_ERROR_CODE_PARAM_INVALID. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetY(ArkUI_Matrix4RotationOptions* options, const float y)](#oh_arkui_matrix4rotationoptions_sety) | Set the value of the direction vector for the y-axis direction in ArkUI_Matrix4RotationOptions. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetY(const ArkUI_Matrix4RotationOptions* options, float* y)](#oh_arkui_matrix4rotationoptions_gety) | Get the value of the direction vector for the y-axis direction in ArkUI_Matrix4RotationOptions.If the value of y is never set, its value will be undefined, so the function will returnARKUI_ERROR_CODE_PARAM_INVALID. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetZ(ArkUI_Matrix4RotationOptions* options, const float z)](#oh_arkui_matrix4rotationoptions_setz) | Set the value of the direction vector for the z-axis direction in ArkUI_Matrix4RotationOptions. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetZ(const ArkUI_Matrix4RotationOptions* options, float* z)](#oh_arkui_matrix4rotationoptions_getz) | Get the value of the direction vector for the z-axis direction in ArkUI_Matrix4RotationOptions.If the value of z is never set, its value will be undefined, so the function will returnARKUI_ERROR_CODE_PARAM_INVALID. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetAngle(ArkUI_Matrix4RotationOptions* options, const float angle)](#oh_arkui_matrix4rotationoptions_setangle) | Set the value of the rotation angle in ArkUI_Matrix4RotationOptions. The unit is degree. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetAngle(const ArkUI_Matrix4RotationOptions* options, float* angle)](#oh_arkui_matrix4rotationoptions_getangle) | Get the value of the rotation angle in ArkUI_Matrix4RotationOptions. The unit is degree.If the value of angle is never set, its default value is 0. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetCenterX(ArkUI_Matrix4RotationOptions* options, const float centerX)](#oh_arkui_matrix4rotationoptions_setcenterx) | Set x offset relative to the transformation center. 0 means no additional x-direction offset from thetransformation center. The unit is px. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetCenterX(const ArkUI_Matrix4RotationOptions* options, float* centerX)](#oh_arkui_matrix4rotationoptions_getcenterx) | Get the value of centerX from the options, which represents the x-direction offset relative to thetransformation center. The unit is px. If the value of centerX is never set, its default value is 0. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetCenterY(ArkUI_Matrix4RotationOptions* options, const float centerY)](#oh_arkui_matrix4rotationoptions_setcentery) | Set y offset relative to the transformation center. 0 means no additional y-direction offset from thetransformation center. The unit is px. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetCenterY(const ArkUI_Matrix4RotationOptions* options, float* centerY)](#oh_arkui_matrix4rotationoptions_getcentery) | Get the value of centerY from the options, which represents the y-direction offset relative to thetransformation center. The unit is px. If the value of centerY is never set, its default value is 0. |
| [ArkUI_Matrix4TranslationOptions* OH_ArkUI_Matrix4TranslationOptions_Create()](#oh_arkui_matrix4translationoptions_create) | Create an object of ArkUI_Matrix4TranslationOptions.In the newly created options, the default values for x, y and z are 0. |
| [void OH_ArkUI_Matrix4TranslationOptions_Dispose(ArkUI_Matrix4TranslationOptions* options)](#oh_arkui_matrix4translationoptions_dispose) | Disposes the ArkUI_Matrix4TranslationOptions object. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_SetX(ArkUI_Matrix4TranslationOptions* options, const float x)](#oh_arkui_matrix4translationoptions_setx) | Set the translation value in the x-axis direction. The unit is px.If the value of x is never set, its default value is 0. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_GetX(const ArkUI_Matrix4TranslationOptions* options, float* x)](#oh_arkui_matrix4translationoptions_getx) | Get the translation value in the x-axis direction from ArkUI_Matrix4TranslationOptions. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_SetY(ArkUI_Matrix4TranslationOptions* options, const float y)](#oh_arkui_matrix4translationoptions_sety) | Set the translation value in the y-axis direction. The unit is px.If the value of y is never set, its default value is 0. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_GetY(const ArkUI_Matrix4TranslationOptions* options, float* y)](#oh_arkui_matrix4translationoptions_gety) | Get the translation value in the y-axis direction from ArkUI_Matrix4TranslationOptions. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_SetZ(ArkUI_Matrix4TranslationOptions* options, const float z)](#oh_arkui_matrix4translationoptions_setz) | Set the translation value in the z-axis direction. The unit is px.If the value of z is never set, its default value is 0. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_GetZ(const ArkUI_Matrix4TranslationOptions* options, float* z)](#oh_arkui_matrix4translationoptions_getz) | Get the translation value in the z-axis direction from ArkUI_Matrix4TranslationOptions. |
| [ArkUI_Matrix4* OH_ArkUI_Matrix4_CreateIdentity()](#oh_arkui_matrix4_createidentity) | Create an identity matrix4 object. |
| [ArkUI_Matrix4* OH_ArkUI_Matrix4_CreateByElements(const float* elements)](#oh_arkui_matrix4_createbyelements) | Specify each element of the matrix to create a matrix4 object. |
| [void OH_ArkUI_Matrix4_Dispose(ArkUI_Matrix4* matrix)](#oh_arkui_matrix4_dispose) | Disposes a matrix4 object. |
| [ArkUI_Matrix4* OH_ArkUI_Matrix4_Copy(const ArkUI_Matrix4* matrix)](#oh_arkui_matrix4_copy) | Create a copy of the matrix4 object. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_Invert(ArkUI_Matrix4* matrix)](#oh_arkui_matrix4_invert) | Perform an inverse matrix transformation on the input matrix.If the matrix is invertible, this function will modify the input matrix; otherwise, the matrix will remainunchanged and an error code will be returned. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_Combine(ArkUI_Matrix4* oriMatrix, const ArkUI_Matrix4* anotherMatrix)](#oh_arkui_matrix4_combine) | Combine another matrix with the original matrix, and storing the resulting matrix in oriMatrix.The resulting matrix is equivalent to first applying the transformation of oriMatrix and then applyingthe transformation of anotherMatrix. This function will alter the oriMatrix object. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_Translate(ArkUI_Matrix4* matrix, const ArkUI_Matrix4TranslationOptions* translate)](#oh_arkui_matrix4_translate) | Apply a tranlation transformation to the original matrix to obtain the translated matrix. Each translationtransformation is applied cumulatively. This function will alter the input matrix object. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_Scale(ArkUI_Matrix4* matrix, const ArkUI_Matrix4ScaleOptions* scale)](#oh_arkui_matrix4_scale) | Apply a scale transformation to the original matrix to obtain the scaled matrix. Each scaletransformation is applied cumulatively. This function will alter the input matrix object. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_Rotate(ArkUI_Matrix4* matrix, const ArkUI_Matrix4RotationOptions* rotate)](#oh_arkui_matrix4_rotate) | Apply a rotation transformation to the original matrix to obtain the rotated matrix. Each rotationtransformation is applied cumulatively. This function will alter the input matrix object. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_Skew(ArkUI_Matrix4* matrix, const float skewX, const float skewY)](#oh_arkui_matrix4_skew) | Apply a skew transformation to the original matrix to obtain the skewed matrix. Each skewtransformation is applied cumulatively. This function will alter the input matrix object. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_TransformPoint(const ArkUI_Matrix4* matrix, const ArkUI_PointF* oriPoint, ArkUI_PointF* result)](#oh_arkui_matrix4_transformpoint) | Calculate the new coordinate position of a point after it has been transformed by a matrix.The calculated transformed coordinate point will be filled into the ArkUI_PointF structurepointed to by result. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_SetPolyToPoly(ArkUI_Matrix4* matrix, const ArkUI_PointF* src, const ArkUI_PointF* dst, const uint32_t pointCount)](#oh_arkui_matrix4_setpolytopoly) | Map the vertex coordinates of one polygon to the vertex coordinates of another polygon, and calculate the requiredmatrix. The resulting matrix will be filled into the object pointed to by matrix. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_GetElements(const ArkUI_Matrix4* matrix, float* result)](#oh_arkui_matrix4_getelements) | Obtain the 16 elements of the matrix and fill them into the array pointed to by result.The array pointed to by result must have space for 16 float elements. |
| [void OH_ArkUI_CrossLanguageOption_SetTreeOperatingStatus(ArkUI_CrossLanguageOption* option, OH_ArkUI_CrossLanguageOperatingStatus status)](#oh_arkui_crosslanguageoption_settreeoperatingstatus) | Sets the tree operating status for the cross-language option. |
| [OH_ArkUI_CrossLanguageOperatingStatus OH_ArkUI_CrossLanguageOption_GetTreeOperatingStatus(ArkUI_CrossLanguageOption* option)](#oh_arkui_crosslanguageoption_gettreeoperatingstatus) | Gets the tree operating status of the cross-language option. |
| [OH_ArkUI_LinearGradientOptions* OH_ArkUI_LinearGradientOptions_Create()](#oh_arkui_lineargradientoptions_create) | Creates a linear gradient options object.The returned object must be released by calling <b>OH_ArkUI_LinearGradientOptions_Destroy</b>. |
| [void OH_ArkUI_LinearGradientOptions_Destroy(OH_ArkUI_LinearGradientOptions* options)](#oh_arkui_lineargradientoptions_destroy) | Destroys a linear gradient options object. |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetAngle(OH_ArkUI_LinearGradientOptions* options, float angle)](#oh_arkui_lineargradientoptions_setangle) | Sets angle of linear gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetAngle(const OH_ArkUI_LinearGradientOptions* options, float* angle)](#oh_arkui_lineargradientoptions_getangle) | Gets angle of linear gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetDirection(OH_ArkUI_LinearGradientOptions* options, ArkUI_LinearGradientDirection direction)](#oh_arkui_lineargradientoptions_setdirection) | Sets direction of linear gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetDirection(const OH_ArkUI_LinearGradientOptions* options, ArkUI_LinearGradientDirection* direction)](#oh_arkui_lineargradientoptions_getdirection) | Gets direction of linear gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetRepeating(OH_ArkUI_LinearGradientOptions* options, bool repeating)](#oh_arkui_lineargradientoptions_setrepeating) | Sets whether colors are repeated in linear gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetRepeating(const OH_ArkUI_LinearGradientOptions* options, bool* repeating)](#oh_arkui_lineargradientoptions_getrepeating) | Gets whether colors are repeated in linear gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetColorStop(OH_ArkUI_LinearGradientOptions* options, const uint32_t* colors, const float* stops, int32_t colorsAndStopsSize)](#oh_arkui_lineargradientoptions_setcolorstop) | Sets color stops of linear gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetColorStop(const OH_ArkUI_LinearGradientOptions* options, uint32_t* colors, float* stops, int32_t colorsAndStopsSize, int32_t* writeLength)](#oh_arkui_lineargradientoptions_getcolorstop) | Gets color stops of linear gradient options. |
| [OH_ArkUI_RadialGradientOptions* OH_ArkUI_RadialGradientOptions_Create()](#oh_arkui_radialgradientoptions_create) | Creates a radial gradient options object.The returned object must be released by calling <b>OH_ArkUI_RadialGradientOptions_Destroy</b>. |
| [void OH_ArkUI_RadialGradientOptions_Destroy(OH_ArkUI_RadialGradientOptions* options)](#oh_arkui_radialgradientoptions_destroy) | Destroys a radial gradient options object. |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetCenterX(OH_ArkUI_RadialGradientOptions* options, float centerX)](#oh_arkui_radialgradientoptions_setcenterx) | Sets centerX of radial gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetCenterX(const OH_ArkUI_RadialGradientOptions* options, float* centerX)](#oh_arkui_radialgradientoptions_getcenterx) | Gets centerX of radial gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetCenterY(OH_ArkUI_RadialGradientOptions* options, float centerY)](#oh_arkui_radialgradientoptions_setcentery) | Sets centerY of radial gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetCenterY(const OH_ArkUI_RadialGradientOptions* options, float* centerY)](#oh_arkui_radialgradientoptions_getcentery) | Gets centerY of radial gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetRadius(OH_ArkUI_RadialGradientOptions* options, float radius)](#oh_arkui_radialgradientoptions_setradius) | Sets radius of radial gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetRadius(const OH_ArkUI_RadialGradientOptions* options, float* radius)](#oh_arkui_radialgradientoptions_getradius) | Gets radius of radial gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetRepeating(OH_ArkUI_RadialGradientOptions* options, bool repeating)](#oh_arkui_radialgradientoptions_setrepeating) | Sets whether colors are repeated in radial gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetRepeating(const OH_ArkUI_RadialGradientOptions* options, bool* repeating)](#oh_arkui_radialgradientoptions_getrepeating) | Gets whether colors are repeated in radial gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetColorStop(OH_ArkUI_RadialGradientOptions* options, const uint32_t* colors, const float* stops, int32_t colorsAndStopsSize)](#oh_arkui_radialgradientoptions_setcolorstop) | Sets color stops of radial gradient options. |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetColorStop(const OH_ArkUI_RadialGradientOptions* options, uint32_t* colors, float* stops, int32_t colorsAndStopsSize, int32_t* writeLength)](#oh_arkui_radialgradientoptions_getcolorstop) | Gets color stops of radial gradient options. |

## 枚举类型说明

### ArkUI_PickerIndicatorType

```c
enum ArkUI_PickerIndicatorType
```

**描述**

Enumerates the selected indicator type of picker.

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_PICKER_INDICATOR_BACKGROUND = 0 | background. |
| ARKUI_PICKER_INDICATOR_DIVIDER = 1 | divider. |

### ArkUI_Alignment

```c
enum ArkUI_Alignment
```

**描述**

Enumerates the alignment modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ALIGNMENT_TOP_START = 0 | Top start. |
| ARKUI_ALIGNMENT_TOP | Top center. |
| ARKUI_ALIGNMENT_TOP_END | Top end. |
| ARKUI_ALIGNMENT_START | Vertically centered start. |
| ARKUI_ALIGNMENT_CENTER | Horizontally and vertically centered. |
| ARKUI_ALIGNMENT_END | Vertically centered end. |
| ARKUI_ALIGNMENT_BOTTOM_START | Bottom start. |
| ARKUI_ALIGNMENT_BOTTOM | Horizontally centered on the bottom. |
| ARKUI_ALIGNMENT_BOTTOM_END | Bottom end. |

### ArkUI_ImageRepeat

```c
enum ArkUI_ImageRepeat
```

**描述**

Enumerates the image repeat patterns.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_REPEAT_NONE = 0 | The image is not repeatedly drawn. |
| ARKUI_IMAGE_REPEAT_X | The image is repeatedly drawn only along the x-axis. |
| ARKUI_IMAGE_REPEAT_Y | The image is repeatedly drawn only along the y-axis. |
| ARKUI_IMAGE_REPEAT_XY | The image is repeatedly drawn along both axes. |

### ArkUI_XComponentType

```c
enum ArkUI_XComponentType
```

**描述**

Enumerates the types of the <b><XComponent></b> component.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_XCOMPONENT_TYPE_SURFACE = 0 | The custom content of EGL/OpenGL ES and media data is displayed individually on the screen. |
| ARKUI_XCOMPONENT_TYPE_TEXTURE = 2 | The custom content of EGL/OpenGL ES and media data is grouped and displayed together with contentof the component. |

### ArkUI_CopyOptions

```c
enum ArkUI_CopyOptions
```

**描述**

Enumerates the text copy and paste modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_COPY_OPTIONS_NONE = 0 | Copy is not allowed. |
| ARKUI_COPY_OPTIONS_IN_APP | Intra-application copy is allowed. |
| ARKUI_COPY_OPTIONS_LOCAL_DEVICE | Intra-device copy is allowed. |
| ARKUI_COPY_OPTIONS_CROSS_DEVICE | Cross-device copy is allowed. |

### ArkUI_ShadowType

```c
enum ArkUI_ShadowType
```

**描述**

Enumerates the shadow types.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SHADOW_TYPE_COLOR = 0 | Color. |
| ARKUI_SHADOW_TYPE_BLUR | Blur. |

### ArkUI_DatePickerMode

```c
enum ArkUI_DatePickerMode
```

**描述**

Enumerates the modes of the date picker.

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_DATEPICKER_MODE_DATE = 0 | A mode that displays the date in months, days of month, and years. |
| ARKUI_DATEPICKER_YEAR_AND_MONTH = 1 | A mode that displays the date in months and years. |
| ARKUI_DATEPICKER_MONTH_AND_DAY = 2 | A mode that displays the date in months and days of the month. |

### ArkUI_TextPickerRangeType

```c
enum ArkUI_TextPickerRangeType
```

**描述**

Enumerates the types of the text picker.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXTPICKER_RANGETYPE_SINGLE = 0 | Single-column text picker. |
| ARKUI_TEXTPICKER_RANGETYPE_MULTI | Multi-column text picker. |
| ARKUI_TEXTPICKER_RANGETYPE_RANGE_CONTENT | Single-column text picker with image resources. |
| ARKUI_TEXTPICKER_RANGETYPE_CASCADE_RANGE_CONTENT | Interconnected multi-column text picker. |

### ArkUI_EdgeEffect

```c
enum ArkUI_EdgeEffect
```

**描述**

Enumerates the effects used at the edges of the component when the boundary of the scrollable content isreached.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_EDGE_EFFECT_SPRING = 0 | Spring effect. When at one of the edges, the component can move beyond the bounds based on the initial |
| ARKUI_EDGE_EFFECT_FADE | Fade effect. When at one of the edges, the component produces a fade effect. |
| ARKUI_EDGE_EFFECT_NONE | No effect after the scrollbar is moved to the edge. |

### ArkUI_BarState

```c
enum ArkUI_BarState
```

**描述**

Enumerates the status of the scroll bar.

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_BAR_STATE_OFF = 0 | Not displayed. |
| ARKUI_BAR_STATE_AUTO = 1 | On-demand display. |
| ARKUI_BAR_STATE_ON = 2 | Resident display. |

### ArkUI_EffectEdge

```c
enum ArkUI_EffectEdge
```

**描述**

Enumerates the edges for which the effect takes effect when the boundary of the scrollable content is reached.

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_EFFECT_EDGE_START = 1 | Start edge. |
| ARKUI_EFFECT_EDGE_END = 2 | End edge. |

### ArkUI_FocusWrapMode

```c
enum ArkUI_FocusWrapMode
```

**描述**

Enumerates the focus wrap mode of components.

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_FOCUS_WRAP_MODE_DEFAULT = 0 | Default mode, where focus does not wrap when arrow keys are used. |
| ARKUI_FOCUS_WRAP_WITH_ARROW = 1 | Focus wraps automatically when arrow keys are used. |

### ArkUI_ItemFillPolicy

```c
enum ArkUI_ItemFillPolicy
```

**描述**

Specifies the number of columns for different responsive breakpoint specifications.

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ITEMFILLPOLICY_NONE = -1 | No responsive breakpoint configuration. |
| ARKUI_ITEMFILLPOLICY_DEFAULT = 0 | Default responsive layout:<b>List</b> or <b>Swiper</b> component: 1 column (SM or smaller), 2 columns (MD), 3 columns (LG or larger).<b>Grid</b> or <b>WaterFlow</b> component: 2 columns (SM or smaller), 3 columns (MD), 5 columns (LG or larger). |
| ARKUI_ITEMFILLPOLICY_SM1MD2LG3 = 1 | 1 column (SM or smaller), 2 columns (MD), 3 columns (LG or larger). |
| ARKUI_ITEMFILLPOLICY_SM2MD3LG5 = 2 | 2 columns (SM or smaller), 3 columns (MD), 5 columns (LG or larger). |

### ArkUI_GridItemAlignment

```c
enum ArkUI_GridItemAlignment
```

**描述**

Enumerates the grid item alignment modes.

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| GRID_ITEM_ALIGNMENT_DEFAULT = 0 | Use the default alignment mode of the grid. |
| GRID_ITEM_ALIGNMENT_STRETCH = 1 | Set the height of all grid items in a row to match the height of the tallest item in that row. |

### ArkUI_GridItemStyle

```c
enum ArkUI_GridItemStyle
```

**描述**

Enumerates styles of grid items.

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| GRID_ITEM_STYLE_NONE = 0 | No style. |
| GRID_ITEM_STYLE_PLAIN = 1 | Hover or press style. |

### ArkUI_ScrollDirection

```c
enum ArkUI_ScrollDirection
```

**描述**

Enumerates the scroll directions for the <b><Scroll></b> component.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_DIRECTION_VERTICAL = 0 | Only vertical scrolling is supported. |
| ARKUI_SCROLL_DIRECTION_HORIZONTAL | Only horizontal scrolling is supported. |
| ARKUI_SCROLL_DIRECTION_NONE = 3 | Scrolling is not allowed. |
| ARKUI_SCROLL_DIRECTION_FREE = 4 |  |

### ArkUI_ScrollSnapAlign

```c
enum ArkUI_ScrollSnapAlign
```

**描述**

Enumerates the alignment modes of list items when scrolling ends.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_SNAP_ALIGN_NONE = 0 | No alignment. This is the default value. |
| ARKUI_SCROLL_SNAP_ALIGN_START | The first item in the view is aligned at the start of the list. |
| ARKUI_SCROLL_SNAP_ALIGN_CENTER | The middle items in the view are aligned in the center of the list. |
| ARKUI_SCROLL_SNAP_ALIGN_END | The last item in the view is aligned at the end of the list. |

### ArkUI_ScrollSnapAnimationSpeed

```c
enum ArkUI_ScrollSnapAnimationSpeed
```

**描述**

Enumerates the scroll snap animation speeds for lists.

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_SNAP_ANIMATION_NORMAL = 0 | Normal scroll snap animation speed. |
| ARKUI_SCROLL_SNAP_ANIMATION_SLOW = 1 | Slow scroll snap animation speed. |

### ArkUI_ScrollBarDisplayMode

```c
enum ArkUI_ScrollBarDisplayMode
```

**描述**

Enumerates the scrollbar display modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF = 0 | Hide. |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO | Display on demand (displays when the screen is touched and disappears after 2s). |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_ON | Always display. |

### ArkUI_Axis

```c
enum ArkUI_Axis
```

**描述**

Enumerates the scroll directions for the <b><List></b> component.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_AXIS_VERTICAL = 0 | Only vertical scrolling is supported. |
| ARKUI_AXIS_HORIZONTAL | Only horizontal scrolling is supported. |

### ArkUI_StickyStyle

```c
enum ArkUI_StickyStyle
```

**描述**

Enumerates the modes for pinning the header to the top or the footer to the bottom.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_STICKY_STYLE_NONE = 0 | In the list item group, the header is not pinned to the top, and the footer is not pinned to the bottom. |
| ARKUI_STICKY_STYLE_HEADER = 1 | In the list item group, the header is pinned to the top, and the footer is not pinned to the bottom. |
| ARKUI_STICKY_STYLE_FOOTER = 2 | In the list item group, the footer is pinned to the bottom, and the header is not pinned to the top. |
| ARKUI_STICKY_STYLE_BOTH = 3 | In the list item group, the footer is pinned to the bottom, and the header is pinned to the top. |

### ArkUI_ContentClipMode

```c
enum ArkUI_ContentClipMode
```

**描述**

Enumerates the content clipping modes of scrollable components.

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY = 0 | clip by content |
| ARKUI_CONTENT_CLIP_MODE_BOUNDARY | clip by boundary |
| ARKUI_CONTENT_CLIP_MODE_SAFE_AREA | clip by safe area padding |

### ArkUI_WaterFlowLayoutMode

```c
enum ArkUI_WaterFlowLayoutMode
```

**描述**

Enumerates the layout modes of the WaterFlow component.

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_WATER_FLOW_LAYOUT_MODE_ALWAYS_TOP_DOWN = 0 | Layout items from top to viewport. |
| ARKUI_WATER_FLOW_LAYOUT_MODE_SLIDING_WINDOW | Layout items in viewport. |

### ArkUI_BorderStyle

```c
enum ArkUI_BorderStyle
```

**描述**

Enumerates the border styles.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_BORDER_STYLE_SOLID = 0 | Solid border. |
| ARKUI_BORDER_STYLE_DASHED | Dashed border. |
| ARKUI_BORDER_STYLE_DOTTED | Dotted border. |

### ArkUI_ShadowStyle

```c
enum ArkUI_ShadowStyle
```

**描述**

Enumerates the shadow styles.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_XS = 0 | Mini shadow. |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_SM | Little shadow. |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_MD | Medium shadow. |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_LG | Large shadow. |
| ARKUI_SHADOW_STYLE_OUTER_FLOATING_SM | Floating small shadow. |
| ARKUI_SHADOW_STYLE_OUTER_FLOATING_MD | Floating medium shadow. |

### ArkUI_AnimationCurve

```c
enum ArkUI_AnimationCurve
```

**描述**

Enumerates the animation curves.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CURVE_LINEAR = 0 | The animation speed keeps unchanged. |
| ARKUI_CURVE_EASE | The animation starts slowly, accelerates, and then slows down towards the end. |
| ARKUI_CURVE_EASE_IN | The animation starts at a low speed and then picks up speed until the end. |
| ARKUI_CURVE_EASE_OUT | The animation ends at a low speed. |
| ARKUI_CURVE_EASE_IN_OUT | The animation starts and ends at a low speed. |
| ARKUI_CURVE_FAST_OUT_SLOW_IN | The animation uses the standard curve |
| ARKUI_CURVE_LINEAR_OUT_SLOW_IN | The animation uses the deceleration curve. |
| ARKUI_CURVE_FAST_OUT_LINEAR_IN | The animation uses the acceleration curve. |
| ARKUI_CURVE_EXTREME_DECELERATION | The animation uses the extreme deceleration curve. |
| ARKUI_CURVE_SHARP | The animation uses the sharp curve. |
| ARKUI_CURVE_RHYTHM | The animation uses the rhythm curve. |
| ARKUI_CURVE_SMOOTH | The animation uses the smooth curve. |
| ARKUI_CURVE_FRICTION | The animation uses the friction curve |

### ArkUI_SwiperArrow

```c
enum ArkUI_SwiperArrow
```

**描述**

Enumerates arrow styles of the navigation point indicator.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SWIPER_ARROW_HIDE = 0 | The arrow is not displayed for the navigation point indicator. |
| ARKUI_SWIPER_ARROW_SHOW | The arrow is displayed for the navigation point indicator. |
| ARKUI_SWIPER_ARROW_SHOW_ON_HOVER | The arrow is displayed only when the mouse pointer hovers over the navigation point indicator. |

### ArkUI_SwiperNestedScrollMode

```c
enum ArkUI_SwiperNestedScrollMode
```

**描述**

Nested scrolling mode for Swiper components and parent components.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY = 0 | Swiper only scrolls on its own and is not linked to its parent component. |
| ARKUI_SWIPER_NESTED_SRCOLL_SELF_FIRST | The Swiper itself scrolls first, and the parent component scrolls after it reaches the edge. After the parentcomponent scrolls to the edge, if the parent component has an edge effect, the parent component triggers the edge |

### ArkUI_PageFlipMode

```c
enum ArkUI_PageFlipMode
```

**描述**

Enumerates the page flipping modes using the mouse wheel for the <b>Swiper</b> component.

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_PAGE_FLIP_MODE_CONTINUOUS = 0 | When the mouse wheel is scrolled continuously, multiple pages are flipped, which is determined by the number of |
| ARKUI_PAGE_FLIP_MODE_SINGLE | The system does not respond to other mouse wheel events until the page flipping animation ends. |

### ArkUI_SwiperAnimationMode

```c
enum ArkUI_SwiperAnimationMode
```

**描述**

Enumerates the animation modes for {@link NODE_SWIPER_INDEX}.

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SWIPER_NO_ANIMATION = 0 | Jump to target index without animation. |
| ARKUI_SWIPER_DEFAULT_ANIMATION = 1 | Scroll to target index with animation. |
| ARKUI_SWIPER_FAST_ANIMATION = 2 | Jump to some index near the target index without animation, then scroll to target index with animation. |

### ArkUI_AccessibilityMode

```c
enum ArkUI_AccessibilityMode
```

**描述**

Enumerates the accessibility modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ACCESSIBILITY_MODE_AUTO = 0 | Whether the component can be identified by the accessibility service is dependent on the component. |
| ARKUI_ACCESSIBILITY_MODE_ENABLED | The component can be identified by the accessibility service. |
| ARKUI_ACCESSIBILITY_MODE_DISABLED | The component cannot be identified by the accessibility service. |
| ARKUI_ACCESSIBILITY_MODE_DISABLED_FOR_DESCENDANTS | The component and all its child components cannot be identified by the accessibility service. |

### ArkUI_ScrollNestedMode

```c
enum ArkUI_ScrollNestedMode
```

**描述**

Defines nested scrolling options.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_NESTED_MODE_SELF_ONLY = 0 | The scrolling is contained within the component, and no scroll chaining occurs, that is, the parent component |
| ARKUI_SCROLL_NESTED_MODE_SELF_FIRST | The component scrolls first, and when it hits the boundary, the parent component scrolls.When the parent component hits the boundary, its edge effect is displayed. If no edge |
| ARKUI_SCROLL_NESTED_MODE_PARENT_FIRST | The parent component scrolls first, and when it hits the boundary, the component scrolls.When the component hits the boundary, its edge effect is displayed. If no edge effect is specified for the |
| ARKUI_SCROLL_NESTED_MODE_PARALLEL | The component and its parent component scroll at the same time. When both the component and its parent componenthit the boundary, the edge effect of the component is displayed. If no edge effect is specified for the |

### ArkUI_ScrollEdge

```c
enum ArkUI_ScrollEdge
```

**描述**

Defines the edge to which the component scrolls.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_EDGE_TOP = 0 | Top edge in the vertical direction. |
| ARKUI_SCROLL_EDGE_BOTTOM | Bottom edge in the vertical direction. |
| ARKUI_SCROLL_EDGE_START | Start position in the horizontal direction. |
| ARKUI_SCROLL_EDGE_END | End position in the horizontal direction. |

### ArkUI_ScrollAlignment

```c
enum ArkUI_ScrollAlignment
```

**描述**

Alignment when scrolling to specific items.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_ALIGNMENT_START = 0 | Align the head. Align the head of the specified item with the head of the container. |
| ARKUI_SCROLL_ALIGNMENT_CENTER | Center alignment. Align the axis direction of the specified item to the center of the container. |
| ARKUI_SCROLL_ALIGNMENT_END | Tail alignment. Align the tail of the specified item with the tail of the container. |
| ARKUI_SCROLL_ALIGNMENT_AUTO | Automatic alignment. If the specified item is completely in the display area, no adjustments will be made.Otherwise, according to the principle of the shortest sliding distance, align the head or tail of the specified |

### ArkUI_ScrollState

```c
enum ArkUI_ScrollState
```

**描述**

Define the current scrolling state.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_STATE_IDLE = 0 | Idle state. Trigger when using the method provided by the controller to control scrolling, and trigger when |
| ARKUI_SCROLL_STATE_SCROLL | Scroll state. Triggered when dragging the container with fingers to scroll. |
| ARKUI_SCROLL_STATE_FLING | Inertial rolling state. Triggered when inertia rolling and bouncing back to the edge are performed after |

### ArkUI_AnimationPlayMode

```c
enum ArkUI_AnimationPlayMode
```

**描述**

Enumerates the animation playback modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ANIMATION_PLAY_MODE_NORMAL = 0 | The animation is played forwards. |
| ARKUI_ANIMATION_PLAY_MODE_REVERSE | The animation is played reversely. |
| ARKUI_ANIMATION_PLAY_MODE_ALTERNATE | The animation is played normally for an odd number of times (1, 3, 5...) and reversely for an even number |
| ARKUI_ANIMATION_PLAY_MODE_ALTERNATE_REVERSE | The animation is played reversely for an odd number of times (1, 3, 5...) and normally for an even number |

### ArkUI_ImageSize

```c
enum ArkUI_ImageSize
```

**描述**

Defines the image size.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_SIZE_AUTO = 0 | The original image aspect ratio is retained. |
| ARKUI_IMAGE_SIZE_COVER | The image is scaled with its aspect ratio retained for both sides to be greater than or equal |
| ARKUI_IMAGE_SIZE_CONTAIN | The image is scaled with its aspect ratio retained for the content to be completely displayed within the display |

### ArkUI_AdaptiveColor

```c
enum ArkUI_AdaptiveColor
```

**描述**

Enumerates the adaptive color modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ADAPTIVE_COLOR_DEFAULT = 0 | Adaptive color mode is not used. |
| ARKUI_ADAPTIVE_COLOR_AVERAGE | Adaptive color mode is used. |

### ArkUI_ColorMode

```c
enum ArkUI_ColorMode
```

**描述**

Enumerates the color modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_COLOR_MODE_SYSTEM = 0 | Following the system color mode. |
| ARKUI_COLOR_MODE_LIGHT | Light color mode. |
| ARKUI_COLOR_MODE_DARK | Dark color mode. |

### ArkUI_SystemColorMode

```c
enum ArkUI_SystemColorMode
```

**描述**

Enumerates the system color modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SYSTEM_COLOR_MODE_LIGHT = 0 | Light color mode. |
| ARKUI_SYSTEM_COLOR_MODE_DARK | Dark color mode. |

### ArkUI_BlurStyle

```c
enum ArkUI_BlurStyle
```

**描述**

Enumerates the blur styles.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_BLUR_STYLE_THIN = 0 | Thin material. |
| ARKUI_BLUR_STYLE_REGULAR | Regular material. |
| ARKUI_BLUR_STYLE_THICK | Thick material. |
| ARKUI_BLUR_STYLE_BACKGROUND_THIN | Material that creates the minimum depth of field effect. |
| ARKUI_BLUR_STYLE_BACKGROUND_REGULAR | Material that creates a medium shallow depth of field effect. |
| ARKUI_BLUR_STYLE_BACKGROUND_THICK | Material that creates a high shallow depth of field effect. |
| ARKUI_BLUR_STYLE_BACKGROUND_ULTRA_THICK | Material that creates the maximum depth of field effect. |
| ARKUI_BLUR_STYLE_NONE | No blur. |
| ARKUI_BLUR_STYLE_COMPONENT_ULTRA_THIN | Component ultra-thin material. |
| ARKUI_BLUR_STYLE_COMPONENT_THIN | Component thin material. |
| ARKUI_BLUR_STYLE_COMPONENT_REGULAR | Component regular material. |
| ARKUI_BLUR_STYLE_COMPONENT_THICK | Component thick material. |
| ARKUI_BLUR_STYLE_COMPONENT_ULTRA_THICK | Component ultra-thick material. |

### ArkUI_BlurStyleActivePolicy

```c
enum ArkUI_BlurStyleActivePolicy
```

**描述**

Enumerates the activation policies for the background blur effect.

**起始版本：** 19

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_BLUR_STYLE_ACTIVE_POLICY_FOLLOWS_WINDOW_ACTIVE_STATE = 0 | The blur effect changes according to the window's focus state; |
| ARKUI_BLUR_STYLE_ACTIVE_POLICY_ALWAYS_ACTIVE | The blur effect is always active. |
| ARKUI_BLUR_STYLE_ACTIVE_POLICY_ALWAYS_INACTIVE | The blur effect is always inactive. |

### ArkUI_VerticalAlignment

```c
enum ArkUI_VerticalAlignment
```

**描述**

Enumerates the vertical alignment modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_VERTICAL_ALIGNMENT_TOP = 0 | Top aligned. |
| ARKUI_VERTICAL_ALIGNMENT_CENTER | Center aligned. This is the default alignment mode. |
| ARKUI_VERTICAL_ALIGNMENT_BOTTOM | Bottom aligned. |

### ArkUI_HorizontalAlignment

```c
enum ArkUI_HorizontalAlignment
```

**描述**

Enumerates the alignment mode in the horizontal direction.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_HORIZONTAL_ALIGNMENT_START = 0 | Aligned with the start edge in the same direction as the language in use. |
| ARKUI_HORIZONTAL_ALIGNMENT_CENTER | Center aligned. This is the default alignment mode. |
| ARKUI_HORIZONTAL_ALIGNMENT_END | Aligned with the end edge in the same direction as the language in use. |

### ArkUI_ObjectFit

```c
enum ArkUI_ObjectFit
```

**描述**

Defines how the image is resized to fit its container.ImageSpanAlignment

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_OBJECT_FIT_CONTAIN = 0 | The image is scaled with its aspect ratio retained for the content to be completely displayed within the |
| ARKUI_OBJECT_FIT_COVER | The image is scaled with its aspect ratio retained for both sides to be greater than or equal to the |
| ARKUI_OBJECT_FIT_AUTO | The image is scaled automatically to fit the display area. |
| ARKUI_OBJECT_FIT_FILL | The image is scaled to fill the display area, and its aspect ratio is not retained. |
| ARKUI_OBJECT_FIT_SCALE_DOWN | The image content is displayed with its aspect ratio retained. The size is smaller than or equal to the |
| ARKUI_OBJECT_FIT_NONE | The original size is retained. |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_START | Not resized, the image is aligned with the start edge of the top of the container. |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP | Not resized, the image is horizontally centered at the top of the container. |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_END | Not resized, the image is aligned with the end edge at the top of the container. |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_START | Not resized, the image is vertically centered on the start edge of the container. |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_CENTER | Not resized, the image is horizontally and vertically centered in the container. |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_END | Not resized, the image is vertically centered on the end edge of the container. |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_START | Not resized, the image is aligned with the start edge at the bottom of the container. |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM | Not resized, the image is horizontally centered at the bottom of the container. |
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_END | Not resized, the image is aligned with the end edge at the bottom of the container. |
| ARKUI_OBJECT_FIT_NONE_MATRIX |  |

### ArkUI_ImageInterpolation

```c
enum ArkUI_ImageInterpolation
```

**描述**

Enumerates the image interpolation effect.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_INTERPOLATION_NONE = 0 | No image interpolation. |
| ARKUI_IMAGE_INTERPOLATION_LOW | Low quality interpolation. |
| ARKUI_IMAGE_INTERPOLATION_MEDIUM | Medium quality interpolation. |
| ARKUI_IMAGE_INTERPOLATION_HIGH | High quality interpolation. This mode produces scaled images of the highest possible quality. |

### ArkUI_DynamicRangeMode

```c
enum ArkUI_DynamicRangeMode
```

**描述**

Enumerates the image dynamic range mode.

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_DYNAMIC_RANGE_MODE_HIGH = 0 | high dynamic range mode. |
| ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT | constraint dynamic range mode. |
| ARKUI_DYNAMIC_RANGE_MODE_STANDARD | standard dynamic range mode. |

### ArkUI_ImageRotateOrientation

```c
enum ArkUI_ImageRotateOrientation
```

**描述**

Enumerates the image rotate orientation.

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ORIENTATION_AUTO = 0 | Use EXIF metadata for display orientation, with support for rotation and mirroring. |
| ARKUI_ORIENTATION_UP | Display original pixel data without transformation. |
| ARKUI_ORIENTATION_RIGHT | Display the image after rotating it 90 degrees clockwise. |
| ARKUI_ORIENTATION_DOWN | Display the image after rotating it 180 degrees clockwise. |
| ARKUI_ORIENTATION_LEFT | Display the image after rotating it 270 degrees clockwise. |
| ARKUI_ORIENTATION_UP_MIRRORED | Display the image after flipping it horizontally. |
| ARKUI_ORIENTATION_RIGHT_MIRRORED | Display the image after flipping it horizontally and then rotating it 90 degrees clockwise. |
| ARKUI_ORIENTATION_DOWN_MIRRORED | Display the image after flipping it vertically. |
| ARKUI_ORIENTATION_LEFT_MIRRORED | Display the image after flipping it horizontally and then rotating it 270 degrees clockwise. |

### ArkUI_BlendMode

```c
enum ArkUI_BlendMode
```

**描述**

Enumerates the blend modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_BLEND_MODE_NONE = 0 | The top image is superimposed on the bottom image without any blending. |
| ARKUI_BLEND_MODE_CLEAR | The target pixels covered by the source pixels are erased by being turned to completely transparent. |
| ARKUI_BLEND_MODE_SRC | r = s: Only the source pixels are displayed. |
| ARKUI_BLEND_MODE_DST | r = d: Only the target pixels are displayed. |
| ARKUI_BLEND_MODE_SRC_OVER | r = s + (1 - sa) * d: The source pixels are blended based on opacity and cover the target pixels. |
| ARKUI_BLEND_MODE_DST_OVER | r = d + (1 - da) * s: The target pixels are blended based on opacity and cover on the source pixels. |
| ARKUI_BLEND_MODE_SRC_IN | r = s * da: Only the part of the source pixels that overlap with the target pixels is displayed. |
| ARKUI_BLEND_MODE_DST_IN | r = d * sa: Only the part of the target pixels that overlap with the source pixels is displayed. |
| ARKUI_BLEND_MODE_SRC_OUT | r = s * (1 - da): Only the part of the source pixels that do not overlap with the target pixels is displayed. |
| ARKUI_BLEND_MODE_DST_OUT | r = d * (1 - sa): Only the part of the target pixels that do not overlap with the source pixels is displayed. |
| ARKUI_BLEND_MODE_SRC_ATOP | r = s * da + d * (1 - sa): The part of the source pixels that overlap with the target pixels is displayed andthe part of the target pixels that do not overlap with the source pixels are displayed. |
| ARKUI_BLEND_MODE_DST_ATOP | r = d * sa + s * (1 - da): The part of the target pixels that overlap with the source pixels and the part ofthe source pixels that do not overlap with the target pixels are displayed. |
| ARKUI_BLEND_MODE_XOR | r = s * (1 - da) + d * (1 - sa): Only the non-overlapping part between the source pixels and the target pixels |
| ARKUI_BLEND_MODE_PLUS | r = min(s + d, 1): New pixels resulting from adding the source pixels to the target pixels are displayed. |
| ARKUI_BLEND_MODE_MODULATE | r = s * d: New pixels resulting from multiplying the source pixels with the target pixels are displayed. |
| ARKUI_BLEND_MODE_SCREEN | r = s + d - s * d: Pixels are blended by adding the source pixels to the target pixels and subtracting the |
| ARKUI_BLEND_MODE_OVERLAY | The MULTIPLY or SCREEN mode is used based on the target pixels. |
| ARKUI_BLEND_MODE_DARKEN | rc = s + d - max(s * da, d * sa), ra = kSrcOver: When two colors overlap, whichever is darker is used. |
| ARKUI_BLEND_MODE_LIGHTEN | rc = s + d - min(s * da, d * sa), ra = |
| ARKUI_BLEND_MODE_COLOR_DODGE | The colors of the target pixels are lightened to reflect the source pixels. |
| ARKUI_BLEND_MODE_COLOR_BURN | The colors of the target pixels are darkened to reflect the source pixels. |
| ARKUI_BLEND_MODE_HARD_LIGHT | The MULTIPLY or SCREEN mode is used, depending on the source pixels. |
| ARKUI_BLEND_MODE_SOFT_LIGHT | The LIGHTEN or DARKEN mode is used, depending on the source pixels. |
| ARKUI_BLEND_MODE_DIFFERENCE | rc = s + d - 2 * (min(s * da, d * sa)), ra =       kSrcOver: The final pixel is the result of subtracting the darker of the two pixels (source and target) from |
| ARKUI_BLEND_MODE_EXCLUSION | rc = s + d - two(s * d), ra = kSrcOver: The final pixel is similar to <b>DIFFERENCE</b>, but with less contrast. |
| ARKUI_BLEND_MODE_MULTIPLY | r = s * (1 - da) + d * (1 - sa) + s * d: The final pixel is the result of multiplying the source pixel |
| ARKUI_BLEND_MODE_HUE | The resultant image is created with the luminance and saturation of the source image and the hue of the target |
| ARKUI_BLEND_MODE_SATURATION | The resultant image is created with the luminance and hue of the target image and the saturation of the source |
| ARKUI_BLEND_MODE_COLOR | The resultant image is created with the saturation and hue of the source image and the luminance of the target |
| ARKUI_BLEND_MODE_LUMINOSITY | The resultant image is created with the saturation and hue of the target image and the luminance of the source |

### ArkUI_Direction

```c
enum ArkUI_Direction
```

**描述**

Enumerates the modes in which components are laid out along the main axis of the container.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_DIRECTION_LTR = 0 | Components are arranged from left to right. |
| ARKUI_DIRECTION_RTL | Components are arranged from right to left. |
| ARKUI_DIRECTION_AUTO = 3 | The default layout direction is used. |

### ArkUI_ItemAlignment

```c
enum ArkUI_ItemAlignment
```

**描述**

Enumerates the modes in which components are laid out along the cross axis of the container.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ITEM_ALIGNMENT_AUTO = 0 | The default configuration in the container is used. |
| ARKUI_ITEM_ALIGNMENT_START | The items in the container are aligned with the cross-start edge. |
| ARKUI_ITEM_ALIGNMENT_CENTER | The items in the container are centered along the cross axis. |
| ARKUI_ITEM_ALIGNMENT_END | The items in the container are aligned with the cross-end edge. |
| ARKUI_ITEM_ALIGNMENT_STRETCH | The items in the container are stretched and padded along the cross axis. |
| ARKUI_ITEM_ALIGNMENT_BASELINE | The items in the container are aligned in such a manner that their text baselines are aligned along the |

### ArkUI_ColorStrategy

```c
enum ArkUI_ColorStrategy
```

**描述**

Enumerates the foreground colors.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_COLOR_STRATEGY_INVERT = 0 | The foreground colors are the inverse of the component background colors. |
| ARKUI_COLOR_STRATEGY_AVERAGE | The shadow colors of the component are the average color obtained from the component background shadow area. |
| ARKUI_COLOR_STRATEGY_PRIMARY | The shadow colors of the component are the primary color obtained from the component background shadow area. |

### ArkUI_FlexAlignment

```c
enum ArkUI_FlexAlignment
```

**描述**

Enumerates the vertical alignment modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_FLEX_ALIGNMENT_START = 1 | The child components are aligned with the start edge of the main axis. |
| ARKUI_FLEX_ALIGNMENT_CENTER = 2 | The child components are aligned in the center of the main axis. |
| ARKUI_FLEX_ALIGNMENT_END = 3 | The child components are aligned with the end edge of the main axis. |
| ARKUI_FLEX_ALIGNMENT_SPACE_BETWEEN = 6 | The child components are evenly distributed along the main axis. The space between any two adjacent componentsis the same. The first component is aligned with the main-start, and the last component is aligned with |
| ARKUI_FLEX_ALIGNMENT_SPACE_AROUND = 7 | The child components are evenly distributed along the main axis. The space between any two adjacent componentsis the same. The space between the first component and main-start, and that between the last component and |
| ARKUI_FLEX_ALIGNMENT_SPACE_EVENLY = 8 | The child components are evenly distributed along the main axis. The space between the first componentand main-start, the space between the last component and main-end, and the space between any two adjacent |

### ArkUI_FlexDirection

```c
enum ArkUI_FlexDirection
```

**描述**

Enumerates the directions of the main axis in the flex container.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_FLEX_DIRECTION_ROW = 0 | The child components are arranged in the same direction as the main axis runs along the rows. |
| ARKUI_FLEX_DIRECTION_COLUMN | The child components are arranged in the same direction as the main axis runs down the columns. |
| ARKUI_FLEX_DIRECTION_ROW_REVERSE | The child components are arranged opposite to the <b>ROW</b> direction. |
| ARKUI_FLEX_DIRECTION_COLUMN_REVERSE | The child components are arranged opposite to the <b>COLUMN</b> direction. |

### ArkUI_FlexWrap

```c
enum ArkUI_FlexWrap
```

**描述**

Defines whether the flex container has a single line or multiple lines.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_FLEX_WRAP_NO_WRAP = 0 | The child components in the flex container are arranged in a single line, and they cannot overflow. |
| ARKUI_FLEX_WRAP_WRAP | The child components in the flex container are arranged in multiple lines, and they may overflow. |
| ARKUI_FLEX_WRAP_WRAP_REVERSE | The child components in the flex container are reversely arranged in multiple lines, and they may overflow. |

### ArkUI_CalendarAlignment

```c
enum ArkUI_CalendarAlignment
```

**描述**

Enumerates the alignment modes between the calendar picker and the entry component.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CALENDAR_ALIGNMENT_START = 0 | Left aligned. |
| ARKUI_CALENDAR_ALIGNMENT_CENTER | Center aligned. |
| ARKUI_CALENDAR_ALIGNMENT_END | Right aligned. |

### ArkUI_MaskType

```c
enum ArkUI_MaskType
```

**描述**

Enumerates the mask types.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_MASK_TYPE_RECTANGLE = 0 | Rectangle. |
| ARKUI_MASK_TYPE_CIRCLE | Circle. |
| ARKUI_MASK_TYPE_ELLIPSE | Ellipse. |
| ARKUI_MASK_TYPE_PATH | Path. |
| ARKUI_MASK_TYPE_PROGRESS | Progress indicator. |

### ArkUI_ClipType

```c
enum ArkUI_ClipType
```

**描述**

Enumerates the clipping region types.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CLIP_TYPE_RECTANGLE = 0 | Rectangle. |
| ARKUI_CLIP_TYPE_CIRCLE | Circle. |
| ARKUI_CLIP_TYPE_ELLIPSE | Ellipse. |
| ARKUI_CLIP_TYPE_PATH | Path. |

### ArkUI_ShapeType

```c
enum ArkUI_ShapeType
```

**描述**

Enumerates the custom shapes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SHAPE_TYPE_RECTANGLE = 0 | Rectangle. |
| ARKUI_SHAPE_TYPE_CIRCLE | Circle. |
| ARKUI_SHAPE_TYPE_ELLIPSE | Ellipse. |
| ARKUI_SHAPE_TYPE_PATH | Path. |

### ArkUI_LinearGradientDirection

```c
enum ArkUI_LinearGradientDirection
```

**描述**

Enumerates the gradient directions.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT = 0 | From right to left. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_TOP | From bottom to top. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT | From left to right. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_BOTTOM | From top to bottom. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_TOP | From lower right to upper left. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM | From upper right to lower left. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT_TOP | From lower left to upper right. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT_BOTTOM | From upper left to lower right. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_NONE | No gradient. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM | Custom direction. |

### ArkUI_ImageRenderMode

```c
enum ArkUI_ImageRenderMode
```

**描述**

Enumerates the image rendering modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_IMAGE_RENDER_MODE_ORIGINAL = 0 | Render image pixels as they are in the original source image. |
| ARKUI_IMAGE_RENDER_MODE_TEMPLATE | Render image pixels to create a monochrome template image. |

### ArkUI_TransitionEdge

```c
enum ArkUI_TransitionEdge
```

**描述**

Enumerates the slide-in and slide-out positions of the component from the screen edge during transition.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TRANSITION_EDGE_TOP = 0 | Top edge of the window. |
| ARKUI_TRANSITION_EDGE_BOTTOM | Bottom edge of the window. |
| ARKUI_TRANSITION_EDGE_START | Left edge of the window. |
| ARKUI_TRANSITION_EDGE_END | Right edge of the window. |

### ArkUI_BlendApplyType

```c
enum ArkUI_BlendApplyType
```

**描述**

Defines how the specified blend mode is applied.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| BLEND_APPLY_TYPE_FAST = 0 | The content of the view is blended in sequence on the target image. |
| BLEND_APPLY_TYPE_OFFSCREEN | The content of the component and its child components are drawn on the offscreen canvas, and then blended with |

### ArkUI_FinishCallbackType

```c
enum ArkUI_FinishCallbackType
```

**描述**

Enumerates the animation onFinish callback types.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_FINISH_CALLBACK_REMOVED = 0 | The callback is invoked when the entire animation is removed once it has finished. |
| ARKUI_FINISH_CALLBACK_LOGICALLY | The callback is invoked when the animation logically enters the falling state, though it may still be in its |

### ArkUI_ListItemAlignment

```c
enum ArkUI_ListItemAlignment
```

**描述**

Enumerates the alignment modes of items along the cross axis.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_ALIGNMENT_START = 0 | The list items are packed toward the start edge of the list container along the cross axis. |
| ARKUI_LIST_ITEM_ALIGNMENT_CENTER | The list items are centered in the list container along the cross axis. |
| ARKUI_LIST_ITEM_ALIGNMENT_END | The list items are packed toward the end edge of the list container along the cross axis. |

### ArkUI_LengthMetricUnit

```c
enum ArkUI_LengthMetricUnit
```

**描述**

Enumerates the component units.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LENGTH_METRIC_UNIT_DEFAULT = -1 | Default, which is fp for fonts and vp for non-fonts. |
| ARKUI_LENGTH_METRIC_UNIT_PX = 0 | px. |
| ARKUI_LENGTH_METRIC_UNIT_VP | vp. |
| ARKUI_LENGTH_METRIC_UNIT_FP | fp. |

### ArkUI_RenderFit

```c
enum ArkUI_RenderFit
```

**描述**

Enumerates the render fit.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_RENDER_FIT_CENTER = 0 | Maintains the content size of the animation's final state, |
| ARKUI_RENDER_FIT_TOP | Maintains the content size of the animation's final state, |
| ARKUI_RENDER_FIT_BOTTOM | Maintains the content size of the animation's final state, |
| ARKUI_RENDER_FIT_LEFT | Maintains the content size of the animation's final state, |
| ARKUI_RENDER_FIT_RIGHT | Maintains the content size of the animation's final state, |
| ARKUI_RENDER_FIT_TOP_LEFT | Maintains the content size of the animation's final state, |
| ARKUI_RENDER_FIT_TOP_RIGHT | Keep the content size of the animation final state, |
| ARKUI_RENDER_FIT_BOTTOM_LEFT | Keep the content size of the animation final state, |
| ARKUI_RENDER_FIT_BOTTOM_RIGHT | Keep the content size of the animation final state, |
| ARKUI_RENDER_FIT_RESIZE_FILL | The aspect ratio of the animation's final state content is not considered, |
| ARKUI_RENDER_FIT_RESIZE_CONTAIN | Reduce or enlarge the aspect ratio of the animation final state content,so that the content is fully displayed in the component, |
| ARKUI_RENDER_FIT_RESIZE_CONTAIN_TOP_LEFT | Keep the aspect ratio of the animation final state content to reduce or enlarge,so that the content is fully displayed in the component.When there is left over in the broad direction of the component,the content is aligned to the left of the component,and when there is left over in the high direction of the component, |
| ARKUI_RENDER_FIT_RESIZE_CONTAIN_BOTTOM_RIGHT | Keep the aspect ratio of the animation final state content to reduce or enlarge,so that the content is fully displayed in the component.When there is left in the wide direction of the component,the content is aligned with the component on the right.When there is left in the high direction of the component, |
| ARKUI_RENDER_FIT_RESIZE_COVER | Keep the aspect ratio of the animation final state content reduced or enlarged,so that both sides of the content are greater than or equal to both sides of the component, |
| ARKUI_RENDER_FIT_RESIZE_COVER_TOP_LEFT | Keep the aspect ratio of the final content of the animation reduced or enlargedso that both sides of the content are exactly greater than or equal to both sides of the component.When the content width is left, the content is aligned to the left of the component,and the left portion of the content is displayed. When the content is left in the high direction, |
| ARKUI_RENDER_FIT_RESIZE_COVER_BOTTOM_RIGHT | Keep the aspect ratio of the final content of the animation reduced or enlarged sothat both sides of the content are exactly greater than or equal to both sides of the component.When the content width is left, the content and the component remain right aligned,and the right part of the content is displayed. When the content is left in the high direction,the content and the component remain aligned at the bottom, |

### ArkUI_SwiperIndicatorType

```c
enum ArkUI_SwiperIndicatorType
```

**描述**

Define the navigation indicator type of the swiper.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SWIPER_INDICATOR_TYPE_DOT | dot type. |
| ARKUI_SWIPER_INDICATOR_TYPE_DIGIT | digit type. |

### ArkUI_ListItemSwipeActionState

```c
enum ArkUI_ListItemSwipeActionState
```

**描述**

Define the pattern of element arrangement in the main axis direction of the Swiper component.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED = 0 | In the folded state, when the ListItem slides in the opposite direction to the main axis, |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_EXPANDED | In the folded state, when the ListItem slides in the opposite direction to the spindle, |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_ACTIONING | Long distance state, the state of deleting a ListItem after it enters the long distance deletion area. |

### ArkUI_ListItemSwipeEdgeEffect

```c
enum ArkUI_ListItemSwipeEdgeEffect
```

**描述**

Define the explicit and implicit mode of the SwipeAction method for the Listitem component.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING = 0 | The ListItem can continue to be scratched after the distance exceeds the size of the scratched component. |
| ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_NONE | The sliding distance of the ListItem cannot exceed the size of the scratched component. |

### ArkUI_ErrorCode

```c
enum ArkUI_ErrorCode
```

**描述**

Define error code enumeration values.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ERROR_CODE_NO_ERROR = 0 | @error No errors. |
| ARKUI_ERROR_CODE_PARAM_INVALID = 401 | @error Parameter error. |
| ARKUI_ERROR_CODE_CAPI_INIT_ERROR = 500 |  CAPI init error.<br>**起始版本：** 18 |
| ARKUI_ERROR_CODE_INTERNAL_ERROR = 100001 |  Internal error occurs, such as failure occurs because of the internal environment error,or operation failed because of the internal execution failed.<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_XCOMPONENT_STATE_INVALID = 103501 |  The XComponent is in invalid state.<br>**起始版本：** 19 |
| ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED = 106102 | @error The component does not support specific properties or events. |
| ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED = 106103 | @error The corresponding operation does not support nodes created by ArkTS. |
| ARKUI_ERROR_CODE_ADAPTER_NOT_BOUND = 106104 | @error The lazy loading adapter is not bound to the component. |
| ARKUI_ERROR_CODE_ADAPTER_EXIST = 106105 | @error The adapter already exists. |
| ARKUI_ERROR_CODE_CHILD_NODE_EXIST = 106106 | @error The corresponding node already has a child node and cannot add an adapter. |
| ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE = 106107 | The parameter length in the parameter event exceeds the limit. |
| ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID = 106108 | The data does not exist in the component event. |
| ARKUI_ERROR_CODE_NODE_EVENT_NO_RETURN = 106109 | The component event does not support return values. |
| ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE = 106110 |  The event type is not supported by the node.<br>**起始版本：** 21 |
| ARKUI_ERROR_CODE_NODE_INDEX_INVALID = 106200 | The index value is invalid. |
| ARKUI_ERROR_CODE_GET_INFO_FAILED = 106201 | Failed to query route navigation information. |
| ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR = 106202 | The buffer size is not large enough. |
| ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE = 106203 |  The node is not on main tree.<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD = 106204 |  The node is running on invalid thread.<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_FORCE_DARK_CONFIG_INVALID = 106205 |  Force dark config is invalid.<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_NODE_IS_ADOPTED = 106206 |  The node has already been adopted.<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_NODE_HAS_PARENT = 106207 |  This node already has a parent node.<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_NODE_CAN_NOT_BE_ADOPTED = 106208 |  The node cannot be adopted.<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_NODE_CAN_NOT_ADOPT_TO = 106209 |  The node cannot adopt children.<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_NODE_IS_NOT_IN_ADOPTED_CHILDREN = 106210 |  This child node is not adopted by the parent node.<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_NOT_CUSTOM_NODE = 106401 |  The node type is not custom node.<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_CHILD_EXISTED = 106402 |  Node already has children.<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_RENDER_PARENT_EXISTED = 106403 |  RenderNode parent is existed.<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_RENDER_CHILD_NOT_EXIST = 106404 |  RenderNode child is not exist.<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE = 106405 |  Param is out of range.<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_RENDER_IS_FROM_FRAME_NODE = 106406 |  The RenderNode is obtained from a FrameNode.<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_RENDER_HAS_INVALID_FRAME_NODE = 106407 |  The RenderNode is obtained from a FrameNode,and its corresponding FrameNode is no longer in the adopted state.<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_RENDER_NOT_ADOPTED_NODE = 106408 |  The node is not adopted.<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE = 150001 |  The node requesting focus is not focusable.<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE_ANCESTOR = 150002 |  The node requesting focus has unfocusable ancestor.<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_FOCUS_NON_EXISTENT = 150003 |  The node requesting focus does not exists.<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT = 160002 |  The snapshot taking is timeout.<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_MODE_NOT_SUPPORTED = 160003 |  The provided color space or dynamic range mode is not supported. For details about the error codes,see [Snapshot Error Codes](../apis-arkui/errorcode-snapshot.md).<br>**起始版本：** 23 |
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_AUTO_NOT_SUPPORTED = 160004 |  The isAuto parameter of the color space or dynamic range mode is set to true for offscreen node snapshot.For details about the error codes, see [Snapshot Error Codes](../apis-arkui/errorcode-snapshot.md).<br>**起始版本：** 23 |
| ARKUI_ERROR_CODE_NON_SCROLLABLE_CONTAINER = 180001 | The component is not a scroll container. |
| ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH = 180002 | The buffer is not large enough. |
| ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT = 180003 |  The event is not a clone event.<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_POST_CLONED_COMPONENT_STATUS_ABNORMAL = 180004 |  The component status is abnormal.<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_POST_CLONED_NO_COMPONENT_HIT_TO_RESPOND_TO_THE_EVENT = 180005 |  No component hit to respond to the event.<br>**起始版本：** 15 |
| ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED = 180006 |  Input event type not supported.<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_INVALID_STYLED_STRING = 180101 |  invalid styled string.<br>**起始版本：** 14 |
| ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED = 180102 |  The gesture recognizer type is not supported.<br>**起始版本：** 18 |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID = 190001 |  The uiContext is invalid.<br>**起始版本：** 18 |
| ARKUI_ERROR_CODE_CALLBACK_INVALID = 190002 |  The callback function is invalid.<br>**起始版本：** 18 |
| ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED = 190004 |  operation is not allowed for current drag drop pharse.<br>**起始版本：** 19 |
| ARKUI_ERROR_CODE_PARAM_ERROR = 100023 |  Parameter error.<br>**起始版本：** 21 |

### ArkUI_AnimationStatus

```c
enum ArkUI_AnimationStatus
```

**描述**

Defines the playback status for the image animator.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ANIMATION_STATUS_INITIAL | The animation is in the initial state. |
| ARKUI_ANIMATION_STATUS_RUNNING | The animation is being played. |
| ARKUI_ANIMATION_STATUS_PAUSED | The animation is paused. |
| ARKUI_ANIMATION_STATUS_STOPPED | The animation is stopped. |

### ArkUI_AnimationFillMode

```c
enum ArkUI_AnimationFillMode
```

**描述**

Defines the status before and after execution of the animation in the current playback direction.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ANIMATION_FILL_MODE_NONE | Before execution, the animation does not apply any styles to the target component. |
| ARKUI_ANIMATION_FILL_MODE_FORWARDS | The target component retains the state set by the last keyframe encountered |
| ARKUI_ANIMATION_FILL_MODE_BACKWARDS | The animation applies the values defined in the first relevant keyframe once it is applied to |
| ARKUI_ANIMATION_FILL_MODE_BOTH | The animation follows the rules for both Forwards and Backwards, |

### ArkUI_AccessibilityCheckedState

```c
enum ArkUI_AccessibilityCheckedState
```

**描述**

Defines the state type for the accessibility checkbox.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ACCESSIBILITY_UNCHECKED = 0 | The Checkbox unchecked. |
| ARKUI_ACCESSIBILITY_CHECKED | The Checkbox checked. |

### ArkUI_AnimationDirection

```c
enum ArkUI_AnimationDirection
```

**描述**

Enumerates the animation playback modes.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ANIMATION_DIRECTION_NORMAL = 0 | The animation plays in forward loop mode. |
| ARKUI_ANIMATION_DIRECTION_REVERSE | The animation plays in reverse loop mode. |
| ARKUI_ANIMATION_DIRECTION_ALTERNATE | The animation plays in alternating loop mode. When the animation is played for an odd number of times, theplayback is in forward direction. When the animation is played for an even number of times, the playback is in |
| ARKUI_ANIMATION_DIRECTION_ALTERNATE_REVERSE | The animation plays in reverse alternating loop mode. When the animation is played for an odd number of times,the playback is in reverse direction. When the animation is played for an even number of times, the playback is |

### ArkUI_ScrollSource

```c
enum ArkUI_ScrollSource
```

**描述**

Define the rolling source enumeration value.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_SOURCE_DRAG = 0 | Finger drag. |
| ARKUI_SCROLL_SOURCE_FLING | Inertial roll after finger drag. |
| ARKUI_SCROLL_SOURCE_EDGE_EFFECT | Execute the EdgeEffect.Spring edge effect when crossing the boundary. |
| ARKUI_SCROLL_SOURCE_OTHER_USER_INPUT | Other user input other than dragging, such as mouse wheel, keyboard events, etc. |
| ARKUI_SCROLL_SOURCE_SCROLL_BAR | Drag the scroll bar. |
| ARKUI_SCROLL_SOURCE_SCROLL_BAR_FLING | Inertia scrolling after dragging the scroll bar. |
| ARKUI_SCROLL_SOURCE_SCROLLER | The scroll controller causes unanimated scrolling. |
| ARKUI_SCROLL_SOURCE_ANIMATION | The scroll controller causes the scroll to drive the painting. |

### ArkUI_AccessibilityActionType

```c
enum ArkUI_AccessibilityActionType
```

**描述**

Define accessible action types.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ACCESSIBILITY_ACTION_CLICK = 1 << 0 | click action. |
| ARKUI_ACCESSIBILITY_ACTION_LONG_CLICK = 1 << 1 | long click action. |
| ARKUI_ACCESSIBILITY_ACTION_CUT = 1 << 2 | cut action. |
| ARKUI_ACCESSIBILITY_ACTION_COPY = 1 << 3 | copy action. |
| ARKUI_ACCESSIBILITY_ACTION_PASTE = 1 << 4 | paste action. |

### ArkUI_NavDestinationState

```c
enum ArkUI_NavDestinationState
```

**描述**

Defines the state of the NavDestination component.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_NAV_DESTINATION_STATE_ON_SHOW = 0 | The NavDestination show. |
| ARKUI_NAV_DESTINATION_STATE_ON_HIDE = 1 | The NavDestination hide. |
| ARKUI_NAV_DESTINATION_STATE_ON_APPEAR = 2 | The NavDestination is mounted to the component tree. |
| ARKUI_NAV_DESTINATION_STATE_ON_DISAPPEAR = 3 | The NavDestination removed from the component tree. |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_SHOW = 4 | Before the NavDestination show. |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_HIDE = 5 | Before the NavDestination hide. |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_APPEAR = 6 | Before the NavDestination mount to the component tree. |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_DISAPPEAR = 7 | Before the NavDestination removed from the component tree. |
| ARKUI_NAV_DESTINATION_STATE_ON_BACK_PRESS = 100 | The NavDestination returns from the component. |

### ArkUI_RouterPageState

```c
enum ArkUI_RouterPageState
```

**描述**

Define the state of Router Page.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_APPEAR = 0 | The Router Page is about to be created. |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_DISAPPEAR = 1 | The Router Page is about to be destroyed. |
| ARKUI_ROUTER_PAGE_STATE_ON_SHOW = 2 | The Router Page show. |
| ARKUI_ROUTER_PAGE_STATE_ON_HIDE = 3 | The Router Page hide. |
| ARKUI_ROUTER_PAGE_STATE_ON_BACK_PRESS = 4 | The Router Page returns. |

### ArkUI_SafeAreaType

```c
enum ArkUI_SafeAreaType
```

**描述**

defines the enumerated value of the extended security zone.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SAFE_AREA_TYPE_SYSTEM = 1 | The default security zone includes the status bar and navigation bar. |
| ARKUI_SAFE_AREA_TYPE_CUTOUT = 1 << 1 | Non-secure areas of the device, such as bangs or hole holes. |
| ARKUI_SAFE_AREA_TYPE_KEYBOARD = 1 << 2 | Soft keyboard area. |

### ArkUI_ListItemGroupArea

```c
enum ArkUI_ListItemGroupArea
```

**描述**

Define an enum for the areas of the <b>ListItemGroup</b> component.

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE = 0 | Outside the area of the <b>ListItemGroup</b> component. |
| ARKUI_LIST_ITEM_SWIPE_AREA_NONE | Area when the <b>ListItemGroup</b> component does not have the header, footer, or list item. |
| ARKUI_LIST_ITEM_SWIPE_AREA_ITEM | List item area of the <b>ListItemGroup</b> component. |
| ARKUI_LIST_ITEM_SWIPE_AREA_HEADER | Header area of the <b>ListItemGroup</b> component. |
| ARKUI_LIST_ITEM_SWIPE_AREA_FOOTER | Footer area of the <b>ListItemGroup</b> component. |

### ArkUI_SafeAreaEdge

```c
enum ArkUI_SafeAreaEdge
```

**描述**

defines the enumerated value of the direction of the extended security zone.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SAFE_AREA_EDGE_TOP = 1 | Upper area. |
| ARKUI_SAFE_AREA_EDGE_BOTTOM = 1 << 1 | Lower area. |
| ARKUI_SAFE_AREA_EDGE_START = 1 << 2 | Front area. |
| ARKUI_SAFE_AREA_EDGE_END = 1 << 3 | Tail area. |

### ArkUI_KeyboardAvoidMode

```c
enum ArkUI_KeyboardAvoidMode
```

**描述**

defines the enumerated value of the customDialog's keyboard avoid mode.

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_KEYBOARD_AVOID_MODE_DEFAULT = 0 | Defines avoid keyboard when keyboard shows. |
| ARKUI_KEYBOARD_AVOID_MODE_NONE | Defines not avoid keyboard when keyboard shows. |

### ArkUI_HoverModeAreaType

```c
enum ArkUI_HoverModeAreaType
```

**描述**

defines the enumerated value of area in hover mode.

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_HOVER_MODE_AREA_TYPE_TOP = 0 | Layout top half screen when the phone in hover mode. |
| ARKUI_HOVER_MODE_AREA_TYPE_BOTTOM | Layout bottom half screen when the phone in hover mode. |

### ArkUI_ExpandMode

```c
enum ArkUI_ExpandMode
```

**描述**

Enumerates the expand modes.

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_NOT_EXPAND = 0 | Not expand. |
| ARKUI_EXPAND = 1 | Expand. |
| ARKUI_LAZY_EXPAND = 2 | Lazy expand. Expand the children of node if needed. |

### ArkUI_EdgeDirection

```c
enum ArkUI_EdgeDirection
```

**描述**

Enumerates the edge direction.

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_EDGE_DIRECTION_ALL = 0 | Set all edge direction. |
| ARKUI_EDGE_DIRECTION_LEFT | Set left edge direction. |
| ARKUI_EDGE_DIRECTION_RIGHT | Set right edge direction. |
| ARKUI_EDGE_DIRECTION_TOP | Set top edge direction. |
| ARKUI_EDGE_DIRECTION_BOTTOM | Set bottom edge direction. |

### ArkUI_CornerDirection

```c
enum ArkUI_CornerDirection
```

**描述**

Enumerates the corner direction.

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CORNER_DIRECTION_ALL = 0 | Set all corner direction. |
| ARKUI_CORNER_DIRECTION_TOP_LEFT | Set top left corner direction. |
| ARKUI_CORNER_DIRECTION_TOP_RIGHT | Set top right corner direction. |
| ARKUI_CORNER_DIRECTION_BOTTOM_LEFT | Set bottom left corner direction. |
| ARKUI_CORNER_DIRECTION_BOTTOM_RIGHT | Set bottom right corner direction. |

### ArkUI_PixelRoundCalcPolicy

```c
enum ArkUI_PixelRoundCalcPolicy
```

**描述**

Enumerates the PixelRoundPolicy.

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_PIXELROUNDCALCPOLICY_NOFORCEROUND = 0 | No Force round the component boundary coordinates to integer pixel. |
| ARKUI_PIXELROUNDCALCPOLICY_FORCECEIL | Force ceil the component boundary coordinates to integer pixel. |
| ARKUI_PIXELROUNDCALCPOLICY_FORCEFLOOR | Force floor the component boundary coordinates to integer pixel. |

### ArkUI_MenuPolicy

```c
enum ArkUI_MenuPolicy
```

**描述**

Menu pop-up strategy.

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_MENU_POLICY_DEFAULT = 0 | Determine whether to pop up the menu according to the underlying default logic. |
| ARKUI_MENU_POLICY_HIDE = 1 | Never pop up the menu. |
| ARKUI_MENU_POLICY_SHOW = 2 | Always pop up the menu. |

### ArkUI_ListItemSwipeActionDirection

```c
enum ArkUI_ListItemSwipeActionDirection
```

**描述**

Define the direction to expand the swipe action.

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_START = 0 | When the List direction is vertical, it indicates the left in LTR mode and right in RTL mode.When the List direction is horizontal, it indicates the top. |
| ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_END = 1 | When the List direction is vertical, it indicates the right in LTR mode and left in RTL mode.When the List direction is horizontal, it indicates the bottom. |

### ArkUI_LayoutSafeAreaType

```c
enum ArkUI_LayoutSafeAreaType
```

**描述**

Define the types for expanding the safe area in layout.

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM = 1 | Default non-safe area of the system, including the status bar and navigation bar. |

### ArkUI_LayoutSafeAreaEdge

```c
enum ArkUI_LayoutSafeAreaEdge
```

**描述**

Define the edges for expanding the safe area in layout.

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP = 1 | Top edge of the safe area. |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_BOTTOM = 1 << 1 | Bottom edge of the safe area. |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_START = 1 << 2 | Start edge of the safe area. |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_END = 1 << 3 | End edge of the safe area. |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_VERTICAL = ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_BOTTOM | Vertical edge of the safe area. |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_HORIZONTAL = ARKUI_LAYOUT_SAFE_AREA_EDGE_START \| ARKUI_LAYOUT_SAFE_AREA_EDGE_END | Horizontal edge of the safe area. |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_ALL = ARKUI_LAYOUT_SAFE_AREA_EDGE_VERTICAL \| ARKUI_LAYOUT_SAFE_AREA_EDGE_HORIZONTAL | All edges of the safe area. |

### ArkUI_LocalizedAlignment

```c
enum ArkUI_LocalizedAlignment
```

**描述**

Enumerates the localizedAlignment modes.

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LOCALIZED_ALIGNMENT_TOP_START = 0 | Top start. |
| ARKUI_LOCALIZED_ALIGNMENT_TOP | Top center. |
| ARKUI_LOCALIZED_ALIGNMENT_TOP_END | Top end. |
| ARKUI_LOCALIZED_ALIGNMENT_START | Vertically centered start. |
| ARKUI_LOCALIZED_ALIGNMENT_CENTER | Horizontally and vertically centered. |
| ARKUI_LOCALIZED_ALIGNMENT_END | Vertically centered end. |
| ARKUI_LOCALIZED_ALIGNMENT_BOTTOM_START | Bottom start. |
| ARKUI_LOCALIZED_ALIGNMENT_BOTTOM | Horizontally centered on the bottom. |
| ARKUI_LOCALIZED_ALIGNMENT_BOTTOM_END | Bottom end. |

### ArkUI_RenderStrategy

```c
enum ArkUI_RenderStrategy
```

**描述**

Enumerates the graphics rendering strategy.

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_RENDERSTRATEGY_FAST = 0 | The current component and its child components will be drawn directly onto the screen canvas. |
| ARKUI_RENDERSTRATEGY_OFFSCREEN | The current component and its child components will first be drawn onto an off-screen canvas,then undergo some graphic rendering operations, and finally be drawn onto the main canvas. |

### ArkUI_LayoutPolicy

```c
enum ArkUI_LayoutPolicy
```

**描述**

Enumerates the LayoutPolicy.

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LAYOUTPOLICY_MATCHPARENT = 0 | The component fills its parent, which means its size is as large as its parent |
| ARKUI_LAYOUTPOLICY_WRAPCONTENT | The component fills its content, which means its size is as large as its children but it is constrainedby its parent. |
| ARKUI_LAYOUTPOLICY_FIXATIDEALSIZE | The component fills its content which means its size is as large as its children. |

### OH_ArkUI_HapticFeedbackMode

```c
enum OH_ArkUI_HapticFeedbackMode
```

**描述**

震动效果类型枚举。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_HAPTIC_FEEDBACK_MODE_DISABLED = 0 |  |
| OH_ARKUI_HAPTIC_FEEDBACK_MODE_ENABLED = 1 |  |
| OH_ARKUI_HAPTIC_FEEDBACK_MODE_AUTO = 2 |  |

### OH_ArkUI_TextEditorSpanType

```c
enum OH_ArkUI_TextEditorSpanType
```

**描述**

自定义文本选择菜单span类型枚举。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_TEXT = 0 |  |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_IMAGE = 1 |  |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_MIXED = 2 |  |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_BUILDER = 3 |  |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_DEFAULT = 4 |  |

### OH_ArkUI_TextEditorResponseType

```c
enum OH_ArkUI_TextEditorResponseType
```

**描述**

自定义文本选择菜单响应类型枚举。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_RIGHT_CLICK = 0 |  |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_LONG_PRESS = 1 |  |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_SELECT = 2 |  |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_DEFAULT = 3 |  |

### OH_ArkUI_TextMenuType

```c
enum OH_ArkUI_TextMenuType
```

**描述**

文本菜单类型枚举。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_SELECTION_MENU = 0 |  |
| OH_ARKUI_TEXT_EDITOR_PREVIEW_MENU = 1 |  |

### OH_ArkUI_CrossLanguageOperatingStatus

```c
enum OH_ArkUI_CrossLanguageOperatingStatus
```

**描述**

Enumerates the tree operating status for the cross-language option.

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_TREE_OPERATING_STATUS_UNDEFINED = 0 |  |
| OH_ARKUI_TREE_OPERATING_STATUS_ENABLE = 1 |  |
| OH_ARKUI_TREE_OPERATING_STATUS_DISABLE = 2 |  |

### OH_ArkUI_NodeMountPolicy

```c
enum OH_ArkUI_NodeMountPolicy
```

**描述**

Enumeration of the policy for mounting child node to the target node.

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NODE_MOUNT_POLICY_SINGLE_IF_RENDER_NODE = 0 |  |
| OH_ARKUI_NODE_MOUNT_POLICY_MIXED = 1 |  |


## 函数说明

### OH_ArkUI_LayoutConstraint_Create()

```c
ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Create()
```

**描述**

Creates a size constraint.

**起始版本：** 12

### OH_ArkUI_LayoutConstraint_Copy()

```c
ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Copy(const ArkUI_LayoutConstraint* Constraint)
```

**描述**

Creates a deep copy of a size constraint.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_LayoutConstraint*](capi-arkui-nativemodule-arkui-layoutconstraint.md) | Returns the pointer to the new size constraint. |

### OH_ArkUI_LayoutConstraint_Dispose()

```c
void* OH_ArkUI_LayoutConstraint_Dispose(ArkUI_LayoutConstraint* Constraint)
```

**描述**

Destroys the pointer to a size constraint.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |

### OH_ArkUI_LayoutConstraint_GetMaxWidth()

```c
int32_t OH_ArkUI_LayoutConstraint_GetMaxWidth(const ArkUI_LayoutConstraint* Constraint)
```

**描述**

Obtains the maximum width for a size constraint, in px.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the maximum width. |

### OH_ArkUI_LayoutConstraint_GetMinWidth()

```c
int32_t OH_ArkUI_LayoutConstraint_GetMinWidth(const ArkUI_LayoutConstraint* Constraint)
```

**描述**

Obtains the minimum width for a size constraint, in px.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the minimum width. |

### OH_ArkUI_LayoutConstraint_GetMaxHeight()

```c
int32_t OH_ArkUI_LayoutConstraint_GetMaxHeight(const ArkUI_LayoutConstraint* Constraint)
```

**描述**

Obtains the maximum height for a size constraint, in px.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the maximum height. |

### OH_ArkUI_LayoutConstraint_GetMinHeight()

```c
int32_t OH_ArkUI_LayoutConstraint_GetMinHeight(const ArkUI_LayoutConstraint* Constraint)
```

**描述**

Obtains the minimum height for a size constraint, in px.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the minimum height. |

### OH_ArkUI_LayoutConstraint_GetPercentReferenceWidth()

```c
int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceWidth(const ArkUI_LayoutConstraint* Constraint)
```

**描述**

Obtains the width percentage reference for a size constraint, in px.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the width percentage reference. |

### OH_ArkUI_LayoutConstraint_GetPercentReferenceHeight()

```c
int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceHeight(const ArkUI_LayoutConstraint* Constraint)
```

**描述**

Obtains the height percentage reference for a size constraint, in px.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the height percentage reference. |

### OH_ArkUI_LayoutConstraint_SetMaxWidth()

```c
void OH_ArkUI_LayoutConstraint_SetMaxWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**描述**

Sets the maximum width.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |
| int32_t value | Indicates the maximum width, in px. |

### OH_ArkUI_LayoutConstraint_SetMinWidth()

```c
void OH_ArkUI_LayoutConstraint_SetMinWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**描述**

Sets the minimum width.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |
| int32_t value | Indicates the minimum width, in px. |

### OH_ArkUI_LayoutConstraint_SetMaxHeight()

```c
void OH_ArkUI_LayoutConstraint_SetMaxHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**描述**

Sets the maximum height.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |
| int32_t value | Indicates the maximum height, in px. |

### OH_ArkUI_LayoutConstraint_SetMinHeight()

```c
void OH_ArkUI_LayoutConstraint_SetMinHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**描述**

Sets the minimum height.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |
| int32_t value | Indicates the minimum height, in px. |

### OH_ArkUI_LayoutConstraint_SetPercentReferenceWidth()

```c
void OH_ArkUI_LayoutConstraint_SetPercentReferenceWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**描述**

Sets the width percentage reference.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |
| int32_t value | Indicates the width percentage reference, in px. |

### OH_ArkUI_LayoutConstraint_SetPercentReferenceHeight()

```c
void OH_ArkUI_LayoutConstraint_SetPercentReferenceHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**描述**

Sets the height percentage reference.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Indicates the pointer to the size constraint. |
| int32_t value | Indicates the height percentage reference, in px. |

### OH_ArkUI_DrawContext_GetCanvas()

```c
void* OH_ArkUI_DrawContext_GetCanvas(ArkUI_DrawContext* context)
```

**描述**

Obtains the pointer to a canvas for drawing, which can be converted into the <b>OH_Drawing_Canvas</b> pointerin the <b>Drawing</b> module.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawContext](capi-arkui-nativemodule-arkui-drawcontext.md)* context | Indicates the pointer to the drawing context. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | Returns the pointer to the canvas for drawing. |

### OH_ArkUI_DrawContext_GetSize()

```c
ArkUI_IntSize OH_ArkUI_DrawContext_GetSize(ArkUI_DrawContext* context)
```

**描述**

Obtains the size of a drawing area.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawContext](capi-arkui-nativemodule-arkui-drawcontext.md)* context | Indicates the pointer to the drawing context. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md) | Returns the size of the drawing area. |

### OH_ArkUI_GridLayoutOptions_Create()

```c
ArkUI_GridLayoutOptions* OH_ArkUI_GridLayoutOptions_Create()
```

**描述**

Creates <b>Grid</b> layout options.

**起始版本：** 22

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_GridLayoutOptions*](capi-arkui-nativemodule-arkui-gridlayoutoptions.md) | <b>Grid</b> layout options created. |

### OH_ArkUI_GridLayoutOptions_Dispose()

```c
void OH_ArkUI_GridLayoutOptions_Dispose(ArkUI_GridLayoutOptions* option)
```

**描述**

Disposes of <b>Grid</b> layout options.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | <b>Grid</b> layout options. |

### OH_ArkUI_GridLayoutOptions_SetIrregularIndexes()

```c
int32_t OH_ArkUI_GridLayoutOptions_SetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t size)
```

**描述**

Sets the irregular grid item index array for the grid layout.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | <b>Grid</b> layout options. |
| uint32_t* irregularIndexes | Array of irregular grid item indexes. |
| int32_t size | Size of the index array. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         If an error code is returned, it may be due to a failure in parameter validation;<br>         the parameter must not be null. |

### OH_ArkUI_GridLayoutOptions_GetIrregularIndexes()

```c
int32_t OH_ArkUI_GridLayoutOptions_GetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t* size)
```

**描述**

Obtains the irregular grid item index array for the grid layout.When <b>OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback</b> is not set,the grid item specified in <b>irregularIndexes</b> occupies an entire row of the grid that scrolls vertically oran entire column of the grid that scrolls horizontally.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | <b>Grid</b> layout options. |
| uint32_t* irregularIndexes | Array of irregular grid item indexes. |
| int32_t* size | Size of the index array. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the provided buffer size is insufficient.<br>         If an error code is returned, it may be due to a failure in parameter validation;<br>         the parameter must not be null. |

### OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback()

```c
void OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemSize (*callback)(int32_t itemIndex, void* userData))
```

**描述**

Registers a callback to obtain the row and column span for the grid item at the specified index.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)\* option | <b>Grid</b> layout options. |
| void\* userData | Indicates the custom data. |
| ArkUI_GridItemSize (\*callback)(int32_t itemIndex | Callback that returns the row and column span for the grid item at the specified index.itemIndex: grid item index, which must be within the range set by[OH_ArkUI_GridLayoutOptions_SetIrregularIndexes](capi-native-type-h.md#oh_arkui_gridlayoutoptions_setirregularindexes). |

### OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback()

```c
void OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemRect (*callback)(int32_t itemIndex, void* userData))
```

**描述**

Registers a callback to obtain the starting row, starting column, row span,and column span for the grid item at the specified index.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)\* option | <b>Grid</b> layout options. |
| void\* userData | Indicates the custom data. |
| ArkUI_GridItemRect (\*callback)(int32_t itemIndex | Callback that returns the starting row, starting column, row span,and column span for the grid item at the specified index.itemIndex: grid item index. |

### OH_ArkUI_WaterFlowSectionOption_Create()

```c
ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create()
```

**描述**

Creates water flow section configuration.

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption*](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) | Returns the water flow section configuration. |

### OH_ArkUI_WaterFlowSectionOption_Dispose()

```c
void OH_ArkUI_WaterFlowSectionOption_Dispose(ArkUI_WaterFlowSectionOption* option)
```

**描述**

Destroys the pointer to a water flow section configuration.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Indicates the pointer to a water flow section configuration. |

### OH_ArkUI_WaterFlowSectionOption_SetSize()

```c
void OH_ArkUI_WaterFlowSectionOption_SetSize(ArkUI_WaterFlowSectionOption* option, int32_t size)
```

**描述**

Sets the FlowItem block configuration information array length.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem Indicates the packet configuration. |
| int32_t size | Array Length. |

### OH_ArkUI_WaterFlowSectionOption_GetSize()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetSize(ArkUI_WaterFlowSectionOption* option)
```

**描述**

Gets the FlowItem grouping configuration information array length.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem Indicates the packet configuration. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Array size. If -1 is returned, the return fails.<br>        The possible cause of the failure is that the option parameter is abnormal, such as a null pointer. |

### OH_ArkUI_WaterFlowSectionOption_SetItemCount()

```c
void OH_ArkUI_WaterFlowSectionOption_SetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t itemCount)
```

**描述**

Sets the number of items in a water flow section.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Indicates the pointer to a water flow section configuration. |
| int32_t index | Indicates the index of the target water flow section. |
| int32_t itemCount | Indicates the number of items in the water flow section. |

### OH_ArkUI_WaterFlowSectionOption_GetItemCount()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述**

Obtains the number of items in the water flow section that matches the specified index.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Indicates the pointer to a water flow section configuration. |
| int32_t index | Indicates the index of the target water flow section. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the number of items in the water flow section. |

### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex()

```c
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex(ArkUI_WaterFlowSectionOption* option, int32_t index, float(*callback)(int32_t itemIndex))
```

**描述**

The FlowItem grouping configuration information getsthe spindle size ofthe specified Item based on flowItemIndex.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)\* option | Indicates the pointer to a water flow section configuration. |
| int32_t index | Indicates the index of the target water flow section. |
| float(\*callback)(int32_t itemIndex) | Gets the spindle size of the specified Item based on index. |

### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData()

```c
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData(ArkUI_WaterFlowSectionOption* option, int32_t index, void* userData, float (*callback)(int32_t itemIndex, void* userData))
```

**描述**

The FlowItem grouping configuration information getsthe spindle size ofthe specified Item based on flowItemIndex.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)\* option | Indicates the pointer to a water flow section configuration. |
| int32_t index | Indicates the index of the target water flow section. |
| void\* userData | FlowItem Custom data. |
| float (\*callback)(int32_t itemIndex | Gets the spindle size of the specified Item based on index. |

### OH_ArkUI_WaterFlowSectionOption_SetCrossCount()

```c
void OH_ArkUI_WaterFlowSectionOption_SetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t crossCount)
```

**描述**

Sets the number of columns (in a vertical layout) or rows (in a horizontal layout) of a water flow.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Indicates the pointer to a water flow section configuration. |
| int32_t index | Indicates the index of the target water flow section. |
| int32_t crossCount | Indicates the number of columns or rows, depending on the layout direction. |

### OH_ArkUI_WaterFlowSectionOption_GetCrossCount()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述**

Obtains the number of columns (in a vertical layout) or rows (in a horizontal layout) in the water flow sectionthat matches the specified index.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Indicates the pointer to a water flow section configuration. |
| int32_t index | Indicates the index of the target water flow section. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the number of columns or rows. |

### OH_ArkUI_WaterFlowSectionOption_SetColumnGap()

```c
void OH_ArkUI_WaterFlowSectionOption_SetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float columnGap)
```

**描述**

Sets the gap between columns in the specified water flow section.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Indicates the pointer to a water flow section configuration. |
| int32_t index | Indicates the index of the target water flow section. |
| float columnGap | Indicates the gap between columns to set. |

### OH_ArkUI_WaterFlowSectionOption_GetColumnGap()

```c
float OH_ArkUI_WaterFlowSectionOption_GetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述**

Obtains the gap between columns in the water flow section that matches the specified index.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Indicates the pointer to a water flow section configuration. |
| int32_t index | Indicates the index of the target water flow section. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the gap between columns. |

### OH_ArkUI_WaterFlowSectionOption_SetRowGap()

```c
void OH_ArkUI_WaterFlowSectionOption_SetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float rowGap)
```

**描述**

Sets the gap between rows in the specified water flow section.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Indicates the pointer to a water flow section configuration. |
| int32_t index | Indicates the index of the target water flow section. |
| float rowGap | Indicates the gap between rows to set. |

### OH_ArkUI_WaterFlowSectionOption_GetRowGap()

```c
float OH_ArkUI_WaterFlowSectionOption_GetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述**

Obtains the gap between rows in the water flow section that matches the specified index.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Indicates the pointer to a water flow section configuration. |
| int32_t index | Indicates the index of the target water flow section. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the gap between rows. |

### OH_ArkUI_WaterFlowSectionOption_SetMargin()

```c
void OH_ArkUI_WaterFlowSectionOption_SetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index, float marginTop, float marginRight, float marginBottom, float marginLeft)
```

**描述**

Sets the margins for the specified water flow section.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Indicates the pointer to a water flow section configuration. |
| int32_t index | Indicates the index of the target water flow section. |
| float marginTop | Indicates the top margin of the water flow section. |
| float marginRight | Indicates the right margin of the water flow section. |
| float marginBottom | Indicates the bottom margin of the water flow section. |
| float marginLeft | Indicates the left margin of the water flow section. |

### OH_ArkUI_WaterFlowSectionOption_GetMargin()

```c
ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述**

Obtains the margins of the water flow section that matches the specified index.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Indicates the pointer to a water flow section configuration. |
| int32_t index | Indicates the index of the target water flow section. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) | Returns the margins. |

### OH_ArkUI_SwiperIndicator_Create()

```c
ArkUI_SwiperIndicator* OH_ArkUI_SwiperIndicator_Create(ArkUI_SwiperIndicatorType type)
```

**描述**

Creates a navigation indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicatorType](capi-native-type-h.md#arkui_swiperindicatortype) type | Indicates the type of the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_SwiperIndicator*](capi-arkui-nativemodule-arkui-swiperindicator.md) | Returns the pointer to the new indicator. |

### OH_ArkUI_SwiperIndicator_Dispose()

```c
void OH_ArkUI_SwiperIndicator_Dispose(ArkUI_SwiperIndicator* indicator)
```

**描述**

Destroys the pointer to the indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

### OH_ArkUI_SwiperIndicator_SetStartPosition()

```c
void OH_ArkUI_SwiperIndicator_SetStartPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

Sets the distance between the navigation point and the start of the swiper.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the distance between the navigation point and the start of the swiper. |

### OH_ArkUI_SwiperIndicator_GetStartPosition()

```c
float OH_ArkUI_SwiperIndicator_GetStartPosition(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains the distance between the navigation point and the start of the swiper.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the distance between the navigation point and the start of the swiper. |

### OH_ArkUI_SwiperIndicator_SetTopPosition()

```c
void OH_ArkUI_SwiperIndicator_SetTopPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

Sets the distance between the navigation point and the top of the swiper.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the distance between the navigation point and the top of the swiper. |

### OH_ArkUI_SwiperIndicator_GetTopPosition()

```c
float OH_ArkUI_SwiperIndicator_GetTopPosition(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains the distance between the navigation point and the top of the swiper.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the distance between the navigation point and the top of the swiper. |

### OH_ArkUI_SwiperIndicator_SetEndPosition()

```c
void OH_ArkUI_SwiperIndicator_SetEndPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

Sets the distance between the navigation point and the right of the swiper.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the distance between the navigation point and the right of the swiper. |

### OH_ArkUI_SwiperIndicator_GetEndPosition()

```c
float OH_ArkUI_SwiperIndicator_GetEndPosition(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains the distance between the navigation point and the end of the swiper.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the distance between the navigation point and the end of the swiper. |

### OH_ArkUI_SwiperIndicator_SetBottomPosition()

```c
void OH_ArkUI_SwiperIndicator_SetBottomPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

Sets the distance between the navigation point and the bottom of the swiper.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the distance between the navigation point and the bottom of the swiper. |

### OH_ArkUI_SwiperIndicator_GetBottomPosition()

```c
float OH_ArkUI_SwiperIndicator_GetBottomPosition(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains the distance between the navigation point and the bottom of the swiper.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the distance between the navigation point and the bottom of the swiper. |

### OH_ArkUI_SwiperIndicator_SetItemWidth()

```c
void OH_ArkUI_SwiperIndicator_SetItemWidth(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

Sets the width of the dot for the dot indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the width of the dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_GetItemWidth()

```c
float OH_ArkUI_SwiperIndicator_GetItemWidth(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains the width of the dot for the dot indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the width of the dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_SetItemHeight()

```c
void OH_ArkUI_SwiperIndicator_SetItemHeight(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

Sets the height of the dot for the dot indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the height of the dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_GetItemHeight()

```c
float OH_ArkUI_SwiperIndicator_GetItemHeight(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains the height of the dot for the dot indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the height of the dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_SetSelectedItemWidth()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedItemWidth(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

Sets the width of the selected dot for the dot indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the width of the selected dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_GetSelectedItemWidth()

```c
float OH_ArkUI_SwiperIndicator_GetSelectedItemWidth(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains the width of the selected dot for the dot indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the width of the selected dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_SetSelectedItemHeight()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedItemHeight(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

Sets the height of the selected dot for the dot indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the height of the selected dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_GetSelectedItemHeight()

```c
float OH_ArkUI_SwiperIndicator_GetSelectedItemHeight(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains the height of the selected dot for the dot indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the height of the selected dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_SetMask()

```c
void OH_ArkUI_SwiperIndicator_SetMask(ArkUI_SwiperIndicator* indicator, int32_t mask)
```

**描述**

Sets whether to display the mask style of the dot navigation indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| int32_t mask | Whether to display the mask style. True means to display. |

### OH_ArkUI_SwiperIndicator_GetMask()

```c
int32_t OH_ArkUI_SwiperIndicator_GetMask(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains whether to display the mask style of the dot navigation indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns whether to display the mask style. True means to display. |

### OH_ArkUI_SwiperIndicator_SetColor()

```c
void OH_ArkUI_SwiperIndicator_SetColor(ArkUI_SwiperIndicator* indicator, uint32_t color)
```

**描述**

Sets the color of the dot navigation indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| uint32_t color | the color of the dot navigation indicator, in 0xARGB format. |

### OH_ArkUI_SwiperIndicator_GetColor()

```c
uint32_t OH_ArkUI_SwiperIndicator_GetColor(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains the color of the dot navigation indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | Returns the color of the dot navigation indicator, in 0xARGB format. |

### OH_ArkUI_SwiperIndicator_SetSelectedColor()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedColor(ArkUI_SwiperIndicator* indicator, uint32_t selectedColor)
```

**描述**

Sets the color of the selected dot for the navigation indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| uint32_t selectedColor | the color of the selected dot, in 0xARGB format. |

### OH_ArkUI_SwiperIndicator_GetSelectedColor()

```c
uint32_t OH_ArkUI_SwiperIndicator_GetSelectedColor(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains the color of the selected dot for the dot navigation indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | Returns the color of the selected dot, in 0xARGB format. |

### OH_ArkUI_SwiperIndicator_SetMaxDisplayCount()

```c
int32_t OH_ArkUI_SwiperIndicator_SetMaxDisplayCount(ArkUI_SwiperIndicator* indicator, int32_t maxDisplayCount)
```

**描述**

Sets the number of maxDisplayCount for the dot navigation indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| int32_t maxDisplayCount | the maxDisplayCount of the navigation dot, span is 6-9. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) Success.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) indicator is null or maxDisplayCount less then 6 or<br>         maxDisplayCount more then 9 |

### OH_ArkUI_SwiperIndicator_GetMaxDisplayCount()

```c
int32_t OH_ArkUI_SwiperIndicator_GetMaxDisplayCount(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains the number of maxDisplayCount for the dot navigation indicator.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the number of the maxDisplayCount, span is 6-9.<br>         0 - indicator is null |

### OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom()

```c
void OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator, int32_t ignoreSize)
```

**描述**

Sets whether to ignore the size of the indicator for [OH_ArkUI_SwiperIndicator_SetBottomPosition](capi-native-type-h.md#oh_arkui_swiperindicator_setbottomposition).

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| int32_t ignoreSize | Whether to ignore the size of the indicator. The value 1 means to ignore, and 0 means the opposite.The default value is 0. |

### OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom()

```c
int32_t OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains whether to ignore the size of the indicator for [OH_ArkUI_SwiperIndicator_SetBottomPosition](capi-native-type-h.md#oh_arkui_swiperindicator_setbottomposition).

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns whether to ignore the size of the indicator. |

### OH_ArkUI_SwiperIndicator_SetSpace()

```c
void OH_ArkUI_SwiperIndicator_SetSpace(ArkUI_SwiperIndicator* indicator, float space)
```

**描述**

Sets the space between the dots of the navigation indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float space | the space between the dots of the navigation indicator, the default value is 8vp. |

### OH_ArkUI_SwiperIndicator_GetSpace()

```c
float OH_ArkUI_SwiperIndicator_GetSpace(ArkUI_SwiperIndicator* indicator)
```

**描述**

Obtains the space between the dots of the navigation indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | the space between the dots of the navigation indicator |

### OH_ArkUI_SwiperDigitIndicator_Create()

```c
ArkUI_SwiperDigitIndicator *OH_ArkUI_SwiperDigitIndicator_Create()
```

**描述**

Creates a digital indicator.

**起始版本：** 19

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator *](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) | Returns the pointer to the new indicator. |

### OH_ArkUI_SwiperDigitIndicator_SetStartPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetStartPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**描述**

Sets the distance between the digital indicator and the start of the swiper.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| float value | Indicates the distance between the digital indicator and the start of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_GetStartPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetStartPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

Gets the distance between the digital indicator and the start of the swiper.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the distance between the digital indicator and the start of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_SetTopPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetTopPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**描述**

Sets the distance between the digital indicator and the top of the swiper.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| float value | Indicates the distance between the digital indicator and the top of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_GetTopPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetTopPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

Gets the distance between the digital indicator and the top of the swiper.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the distance between the digital indicator and the top of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_SetEndPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetEndPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**描述**

Sets the distance between the digital indicator and the end of the swiper.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| float value | Indicates the distance between the digital indicator and the end of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_GetEndPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetEndPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

Gets the distance between the digital indicator and the end of the swiper.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the distance between the digital indicator and the end of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_SetBottomPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetBottomPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**描述**

Sets the distance between the digital indicator and the bottom of the swiper.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| float value | Returns the distance between the digital indicator and the bottom of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_GetBottomPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetBottomPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

Gets the distance between the digital indicator and the bottom of the swiper.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the distance between the digital indicator and the bottom of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_SetFontColor()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t color)
```

**描述**

Sets the font color of total count in the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| uint32_t color | font color, in 0xARGB format. Default value: 0xFF182431. |

### OH_ArkUI_SwiperDigitIndicator_GetFontColor()

```c
uint32_t OH_ArkUI_SwiperDigitIndicator_GetFontColor(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

Gets the font color of total count in the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | font color, in 0xARGB format. |

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t selectedColor)
```

**描述**

Sets the font color of selected index in the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| uint32_t selectedColor | font color, in 0xARGB format. Default value: 0xFF182431. |

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor()

```c
uint32_t OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

Gets the font color of selected index in the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | font color, in 0xARGB format. |

### OH_ArkUI_SwiperDigitIndicator_SetFontSize()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)
```

**描述**

Sets the font size of total count in the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| float size | font size, in fp. |

### OH_ArkUI_SwiperDigitIndicator_GetFontSize()

```c
float OH_ArkUI_SwiperDigitIndicator_GetFontSize(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

Gets the font size of total count in the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | font size, in fp. |

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)
```

**描述**

Sets the font size of selected index in the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| float size | font size, in fp. |

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize()

```c
float OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

Gets the font size of selected index in the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | font size, in fp. |

### OH_ArkUI_SwiperDigitIndicator_SetFontWeight()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontWeight(ArkUI_SwiperDigitIndicator *indicator, ArkUI_FontWeight fontWeight)
```

**描述**

Sets the font weight of total count in the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) *indicator | The pointer to the digital indicator. |
| [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight) fontWeight | font weight [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>. |

### OH_ArkUI_SwiperDigitIndicator_GetFontWeight()

```c
ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetFontWeight(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

Gets the font weight of total count in the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight) | font weight [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). |

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontWeight()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontWeight(ArkUI_SwiperDigitIndicator *indicator, ArkUI_FontWeight selectedFontWeight)
```

**描述**

Sets the font weight of selected index in the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) *indicator | The pointer to the digital indicator. |
| [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight) selectedFontWeight | font weight [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>. |

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontWeight()

```c
ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetSelectedFontWeight(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

Gets the font weight of selected index in the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight) | font weight [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). |

### OH_ArkUI_SwiperDigitIndicator_Destroy()

```c
void OH_ArkUI_SwiperDigitIndicator_Destroy(ArkUI_SwiperDigitIndicator *indicator)
```

**描述**

Destroys the digital indicator.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) *indicator | The pointer to the digital indicator. |

### OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom()

```c
void OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator, int32_t ignoreSize)
```

**描述**

Sets whether to ignore the size of the indicator for [OH_ArkUI_SwiperDigitIndicator_SetBottomPosition](capi-native-type-h.md#oh_arkui_swiperdigitindicator_setbottomposition).

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| int32_t ignoreSize | Whether to ignore the size of the indicator. The value 1 means to ignore, and 0 means the opposite.The default value is 0. |

### OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom()

```c
int32_t OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

Obtains whether to ignore the size of the indicator for [OH_ArkUI_SwiperDigitIndicator_SetBottomPosition](capi-native-type-h.md#oh_arkui_swiperdigitindicator_setbottomposition).

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns whether to ignore the size of the indicator. |

### OH_ArkUI_SwiperArrowStyle_Create()

```c
ArkUI_SwiperArrowStyle *OH_ArkUI_SwiperArrowStyle_Create()
```

**描述**

Creates a arrow style for swiper.

**起始版本：** 19

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_SwiperArrowStyle *](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) | Returns the pointer to the new arrow style. |

### OH_ArkUI_SwiperArrowStyle_SetShowBackground()

```c
void OH_ArkUI_SwiperArrowStyle_SetShowBackground(ArkUI_SwiperArrowStyle *arrowStyle, int32_t showBackground)
```

**描述**

Sets whether to show the background for the arrow.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) *arrowStyle | The pointer to the arrow style. |
| int32_t showBackground | whether to show the background for the arrow.The value <b>1</b> means to show the background, and <b>0</b> means the opposite.The default value is <b>0</b>. |

### OH_ArkUI_SwiperArrowStyle_GetShowBackground()

```c
int32_t OH_ArkUI_SwiperArrowStyle_GetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle)
```

**描述**

Gets whether to show the background for the arrow.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | whether to show the background for the arrow.<br>         The value <b>1</b> means to show the background, and <b>0</b> means the opposite. |

### OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle()

```c
void OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showSidebarMiddle)
```

**描述**

Sets the display position of the arrow.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |
| int32_t showSidebarMiddle | the display position of the arrow.The value <b>1</b> means to display on boths sides of the swiper,and <b>0</b> means display on boths sides of the swiper indicator.The default value is <b>0</b>. |

### OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle()

```c
int32_t OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle)
```

**描述**

Gets the display position of the arrow.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | the display position of the arrow. The value <b>1</b> means to display on boths sides of the swiper,<br>         and <b>0</b> means display on boths sides of the swiper indicator. |

### OH_ArkUI_SwiperArrowStyle_SetBackgroundSize()

```c
void OH_ArkUI_SwiperArrowStyle_SetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle, float backgroundSize)
```

**描述**

Sets the background size of the arrow.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |
| float backgroundSize | the background size of the arrow. The unit is vp.The default value is <b>24</b> when the arrow displays on both sides of the swiper indicator.The default value is <b>32</b> when the arrow displays on both sides of the swiper. |

### OH_ArkUI_SwiperArrowStyle_GetBackgroundSize()

```c
float OH_ArkUI_SwiperArrowStyle_GetBackgroundSize(ArkUI_SwiperArrowStyle *arrowStyle)
```

**描述**

Gets the background size of the arrow.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) *arrowStyle | The pointer to the arrow style. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Returns the background size of the arrow. The unit is vp. |

### OH_ArkUI_SwiperArrowStyle_Destroy()

```c
void OH_ArkUI_SwiperArrowStyle_Destroy(ArkUI_SwiperArrowStyle *arrowStyle)
```

**描述**

Destroys the arrow style.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) *arrowStyle | The pointer to the arrow style. |

### OH_ArkUI_SwiperArrowStyle_SetBackgroundColor()

```c
void OH_ArkUI_SwiperArrowStyle_SetBackgroundColor(ArkUI_SwiperArrowStyle *arrowStyle, uint32_t backgroundColor)
```

**描述**

Sets the background color of the arrow.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) *arrowStyle | The pointer to the arrow style. |
| uint32_t backgroundColor | the background color of the arrow, in 0xARGB format.The default value is <b>0x00000000</b> when the arrow displays on both sides of the swiper indicator.The default value is <b>0x19182431</b> when the arrow displays on both sides of the swiper. |

### OH_ArkUI_SwiperArrowStyle_GetBackgroundColor()

```c
uint32_t OH_ArkUI_SwiperArrowStyle_GetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle)
```

**描述**

Gets the background color of the arrow.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | Returns the background color of the arrow, in 0xARGB format. |

### OH_ArkUI_SwiperArrowStyle_SetArrowSize()

```c
void OH_ArkUI_SwiperArrowStyle_SetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle, float arrowSize)
```

**描述**

Sets the size of the arrow.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |
| float arrowSize | the size of the arrow. The unit is vp.The default value is <b>18</b> when the arrow displays on both sides of the swiper indicator.The default value is <b>24</b> when the arrow displays on both sides of the swiper.The arrow size is fixed to 3/4 of the background size when the background is shown. |

### OH_ArkUI_SwiperArrowStyle_GetArrowSize()

```c
float OH_ArkUI_SwiperArrowStyle_GetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle)
```

**描述**

Gets the size of the arrow.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | the size of the arrow. The unit is vp. |

### OH_ArkUI_SwiperArrowStyle_SetArrowColor()

```c
void OH_ArkUI_SwiperArrowStyle_SetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t arrowColor)
```

**描述**

Sets the color of the arrow.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |
| uint32_t arrowColor | the color of the arrow, in 0xARGB format. The default value is <b>0x00182431</b>. |

### OH_ArkUI_SwiperArrowStyle_GetArrowColor()

```c
uint32_t OH_ArkUI_SwiperArrowStyle_GetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle)
```

**描述**

Gets the color of the arrow.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | Returns the color of the arrow, in 0xARGB format. |

### OH_ArkUI_GuidelineOption_Create()

```c
ArkUI_GuidelineOption* OH_ArkUI_GuidelineOption_Create(int32_t size)
```

**描述**

Create auxiliary line information in the RelativeContaine container.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t size | The number of auxiliary lines. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_GuidelineOption* | auxiliary line information. |

### OH_ArkUI_GuidelineOption_Dispose()

```c
void OH_ArkUI_GuidelineOption_Dispose(ArkUI_GuidelineOption* guideline)
```

**描述**

Destroy auxiliary line information.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |

### OH_ArkUI_GuidelineOption_SetId()

```c
void OH_ArkUI_GuidelineOption_SetId(ArkUI_GuidelineOption* guideline, const char* value, int32_t index)
```

**描述**

Set the Id of the auxiliary line.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| const char* value | id, must be unique and cannot have the same name as the component in the container. |
| int32_t index | auxiliary line index value. |

### OH_ArkUI_GuidelineOption_SetDirection()

```c
void OH_ArkUI_GuidelineOption_SetDirection(ArkUI_GuidelineOption* guideline, ArkUI_Axis value, int32_t index)
```

**描述**

Set the direction of the auxiliary line.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| [ArkUI_Axis](capi-native-type-h.md#arkui_axis) value | direction. |
| int32_t index | auxiliary line index value. |

### OH_ArkUI_GuidelineOption_SetPositionStart()

```c
void OH_ArkUI_GuidelineOption_SetPositionStart(ArkUI_GuidelineOption* guideline, float value, int32_t index)
```

**描述**

Set the distance from the left or top of the container.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| float value | The distance from the left or top of the container. |
| int32_t index | auxiliary line index value. |

### OH_ArkUI_GuidelineOption_SetPositionEnd()

```c
void OH_ArkUI_GuidelineOption_SetPositionEnd(ArkUI_GuidelineOption* guideline, float value, int32_t index)
```

**描述**

Set the distance from the right or bottom of the container.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| float value | The distance from the right side or bottom of the container. |
| int32_t index | auxiliary line index value. |

### OH_ArkUI_GuidelineOption_GetId()

```c
const char* OH_ArkUI_GuidelineOption_GetId(ArkUI_GuidelineOption* guideline, int32_t index)
```

**描述**

Get the Id of the auxiliary line.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | Id. |

### OH_ArkUI_GuidelineOption_GetDirection()

```c
ArkUI_Axis OH_ArkUI_GuidelineOption_GetDirection(ArkUI_GuidelineOption* guideline, int32_t index)
```

**描述**

Get the direction of the auxiliary line.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_Axis](capi-native-type-h.md#arkui_axis) | direction. |

### OH_ArkUI_GuidelineOption_GetPositionStart()

```c
float OH_ArkUI_GuidelineOption_GetPositionStart(ArkUI_GuidelineOption* guideline, int32_t index)
```

**描述**

Get the distance from the left or top of the container.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | The distance from the left or top of the container. |

### OH_ArkUI_GuidelineOption_GetPositionEnd()

```c
float OH_ArkUI_GuidelineOption_GetPositionEnd(ArkUI_GuidelineOption* guideline, int32_t index)
```

**描述**

Get the distance from the right side or bottom of the container.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | The distance from the right side or bottom of the container. |

### OH_ArkUI_BarrierOption_Create()

```c
ArkUI_BarrierOption* OH_ArkUI_BarrierOption_Create(int32_t size)
```

**描述**

creates barrier information within the RelativeContaine container.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t size | Number of barriers. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_BarrierOption* | barrier information. |

### OH_ArkUI_BarrierOption_Dispose()

```c
void OH_ArkUI_BarrierOption_Dispose(ArkUI_BarrierOption* barrierStyle)
```

**描述**

Destroy barrier information.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | barrier information. |

### OH_ArkUI_BarrierOption_SetId()

```c
void OH_ArkUI_BarrierOption_SetId(ArkUI_BarrierOption* barrierStyle, const char* value, int32_t index)
```

**描述**

Set the Id of the barrier.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | barrier information. |
| const char* value | id, must be unique and cannot have the same name as the component in the container. |
| int32_t index | Barrier index value. |

### OH_ArkUI_BarrierOption_SetDirection()

```c
void OH_ArkUI_BarrierOption_SetDirection(ArkUI_BarrierOption* barrierStyle, ArkUI_BarrierDirection value, int32_t index)
```

**描述**

Set the direction of the barrier.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | barrier information. |
| ArkUI_BarrierDirection value | direction. |
| int32_t index | Barrier index value. |

### OH_ArkUI_BarrierOption_SetReferencedId()

```c
void OH_ArkUI_BarrierOption_SetReferencedId(ArkUI_BarrierOption* barrierStyle, const char* value, int32_t index)
```

**描述**

Sets the dependent component of the barrier.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | barrier information. |
| const char* value | The ID of the dependent component. |
| int32_t index | Barrier index value. |

### OH_ArkUI_BarrierOption_GetId()

```c
const char* OH_ArkUI_BarrierOption_GetId(ArkUI_BarrierOption* barrierStyle, int32_t index)
```

**描述**

Get the Id of the barrier.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | The Id of the barrier. |

### OH_ArkUI_BarrierOption_GetDirection()

```c
ArkUI_BarrierDirection OH_ArkUI_BarrierOption_GetDirection(ArkUI_BarrierOption* barrierStyle, int32_t index)
```

**描述**

Gets the direction of the barrier.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_BarrierDirection | The direction of the barrier. |

### OH_ArkUI_BarrierOption_GetReferencedId()

```c
const char* OH_ArkUI_BarrierOption_GetReferencedId(ArkUI_BarrierOption* barrierStyle, int32_t index, int32_t referencedIndex)
```

**描述**

Get the dependent components of the barrier.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | auxiliary line information. |
| int32_t index | auxiliary line index value. |
| int32_t referencedIndex | dependent component Id index value. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | The barrier's dependent components. |

### OH_ArkUI_BarrierOption_GetReferencedIdSize()

```c
int32_t OH_ArkUI_BarrierOption_GetReferencedIdSize(ArkUI_BarrierOption* barrierStyle, int32_t index)
```

**描述**

Gets the number of dependent components of the barrier.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | The number of dependent components of the barrier. |

### OH_ArkUI_ContentTransitionEffect_Create()

```c
ArkUI_ContentTransitionEffect* OH_ArkUI_ContentTransitionEffect_Create(int32_t type)
```

**描述**

creates content switching animation effects.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t type | content transition type: 0-identity, 1-opacity. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ContentTransitionEffect*](capi-arkui-nativemodule-arkui-contenttransitioneffect.md) | content transition effect. |

### OH_ArkUI_AlignmentRuleOption_Create()

```c
ArkUI_AlignmentRuleOption* OH_ArkUI_AlignmentRuleOption_Create()
```

**描述**

creates alignment rule information for subcomponents in relative containers.

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_AlignmentRuleOption* | Alignment rule information. |

### OH_ArkUI_AlignmentRuleOption_Dispose()

```c
void OH_ArkUI_AlignmentRuleOption_Dispose(ArkUI_AlignmentRuleOption* option)
```

**描述**

Destroys the alignment rule information of subcomponents in relative containers.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

### OH_ArkUI_AlignmentRuleOption_SetStart()

```c
void OH_ArkUI_AlignmentRuleOption_SetStart(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)
```

**描述**

Set the start alignment parameter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| const char* id | The id value of the anchor component. |
| [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment) alignment | Alignment relative to the anchor component. |

### OH_ArkUI_AlignmentRuleOption_SetEnd()

```c
void OH_ArkUI_AlignmentRuleOption_SetEnd(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)
```

**描述**

Set the end alignment parameter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| const char* id | The id value of the anchor component. |
| [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment) alignment | Alignment relative to the anchor component. |

### OH_ArkUI_AlignmentRuleOption_SetCenterHorizontal()

```c
void OH_ArkUI_AlignmentRuleOption_SetCenterHorizontal(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)
```

**描述**

Set the parameters for horizontal center alignment.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| const char* id | The id value of the anchor component. |
| [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment) alignment | Alignment relative to anchor component |

### OH_ArkUI_AlignmentRuleOption_SetTop()

```c
void OH_ArkUI_AlignmentRuleOption_SetTop(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)
```

**描述**

Set the parameters for top alignment.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| const char* id | The id value of the anchor component. |
| [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment) alignment | Alignment relative to anchor component |

### OH_ArkUI_AlignmentRuleOption_SetBottom()

```c
void OH_ArkUI_AlignmentRuleOption_SetBottom(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)
```

**描述**

Set the bottom alignment parameters.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| const char* id | The id value of the anchor component. |
| [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment) alignment | Alignment relative to anchor component |

### OH_ArkUI_AlignmentRuleOption_SetCenterVertical()

```c
void OH_ArkUI_AlignmentRuleOption_SetCenterVertical(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)
```

**描述**

Set the parameters for vertical center alignment.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| const char* id | The id value of the anchor component. |
| [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment) alignment | Alignment relative to the anchor component. |

### OH_ArkUI_AlignmentRuleOption_SetBiasHorizontal()

```c
void OH_ArkUI_AlignmentRuleOption_SetBiasHorizontal(ArkUI_AlignmentRuleOption* option, float horizontal)
```

**描述**

Sets the horizontal offset parameter of the component under the anchor point constraint.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| float horizontal | bias value in the horizontal direction. |

### OH_ArkUI_AlignmentRuleOption_SetBiasVertical()

```c
void OH_ArkUI_AlignmentRuleOption_SetBiasVertical(ArkUI_AlignmentRuleOption* option, float vertical)
```

**描述**

Set the vertical offset parameter of the component under the anchor point constraint.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| float vertical | bias value in the vertical direction. |

### OH_ArkUI_AlignmentRuleOption_GetStartId()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetStartId(ArkUI_AlignmentRuleOption* option)
```

**描述**

Get the Id of the start-aligned parameter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | The id value of the anchor component. |

### OH_ArkUI_AlignmentRuleOption_GetStartAlignment()

```c
ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetStartAlignment(ArkUI_AlignmentRuleOption* option)
```

**描述**

Gets the alignment of the start-aligned parameter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment) | The alignment of the parameters. |

### OH_ArkUI_AlignmentRuleOption_GetEndId()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetEndId(ArkUI_AlignmentRuleOption* option)
```

**描述**

Get the end alignment parameter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | End-aligned parameter id. |

### OH_ArkUI_AlignmentRuleOption_GetEndAlignment()

```c
ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetEndAlignment(ArkUI_AlignmentRuleOption* option)
```

**描述**

Get the end alignment parameter.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment) | The alignment of the end-aligned parameter. |

### OH_ArkUI_AlignmentRuleOption_GetCenterIdHorizontal()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdHorizontal(ArkUI_AlignmentRuleOption* option)
```

**描述**

Gets the parameters of horizontal center alignment.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | The id of the parameter of horizontal center alignment. |

### OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentHorizontal()

```c
ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentHorizontal(ArkUI_AlignmentRuleOption* option)
```

**描述**

Gets the parameters of horizontal center alignment.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment) | The alignment of the horizontally centered alignment parameter. |

### OH_ArkUI_AlignmentRuleOption_GetTopId()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetTopId(ArkUI_AlignmentRuleOption* option)
```

**描述**

Get the top-aligned parameters.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | Top aligned parameter id. |

### OH_ArkUI_AlignmentRuleOption_GetTopAlignment()

```c
ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetTopAlignment(ArkUI_AlignmentRuleOption* option)
```

**描述**

Get the top-aligned parameters.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment) | The alignment of the top-aligned parameter. |

### OH_ArkUI_AlignmentRuleOption_GetBottomId()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetBottomId(ArkUI_AlignmentRuleOption* option)
```

**描述**

Get the bottom alignment parameters.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | The id of the bottom-aligned parameter. |

### OH_ArkUI_AlignmentRuleOption_GetBottomAlignment()

```c
ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetBottomAlignment(ArkUI_AlignmentRuleOption* option)
```

**描述**

Get the bottom alignment parameters.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment) | The alignment of the bottom-aligned parameter. |

### OH_ArkUI_AlignmentRuleOption_GetCenterIdVertical()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdVertical(ArkUI_AlignmentRuleOption* option)
```

**描述**

Gets the parameters of vertical center alignment.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | The id of the vertical center alignment parameter. |

### OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentVertical()

```c
ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentVertical(ArkUI_AlignmentRuleOption* option)
```

**描述**

Gets the parameters of vertical center alignment.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment) | The alignment of the vertical center alignment parameter. |

### OH_ArkUI_AlignmentRuleOption_GetBiasHorizontal()

```c
float OH_ArkUI_AlignmentRuleOption_GetBiasHorizontal(ArkUI_AlignmentRuleOption* option)
```

**描述**

Get the bias value in the horizontal direction.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | The bias value in the horizontal direction. |

### OH_ArkUI_AlignmentRuleOption_GetBiasVertical()

```c
float OH_ArkUI_AlignmentRuleOption_GetBiasVertical(ArkUI_AlignmentRuleOption* option)
```

**描述**

Get the bias value in the vertical direction.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | bias value in vertical direction. |

### OH_ArkUI_ListItemSwipeActionItem_Create()

```c
ArkUI_ListItemSwipeActionItem* OH_ArkUI_ListItemSwipeActionItem_Create()
```

**描述**

Create a configuration item for the ListitemSwipeActionItem interface settings.

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem*](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md) | List Item SwipeActionItem configuration item instance. If the object returns a null pointer,<br>         it indicates creation failure, and the reason for the failure may be that the address space is full. |

### OH_ArkUI_ListItemSwipeActionItem_Dispose()

```c
void OH_ArkUI_ListItemSwipeActionItem_Dispose(ArkUI_ListItemSwipeActionItem* item)
```

**描述**

Destroy the ListitemSwipeActionItem instance.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | List Item SwipeActionItem instance to be destroyed. |

### OH_ArkUI_ListItemSwipeActionItem_SetContent()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetContent(ArkUI_ListItemSwipeActionItem* item, ArkUI_NodeHandle node)
```

**描述**

Set the layout content of ListItem SwipeActionItem.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | List Item SwipeActionItem instance. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Layout information. |

### OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item, float distance)
```

**描述**

Set the threshold for long-distance sliding deletion distance of components.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | List Item SwipeActionItem instance. |
| float distance | Component long-distance sliding deletion distance threshold. |

### OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance()

```c
float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item)
```

**描述**

Obtain the threshold for long-distance sliding deletion distance of components.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | List Item SwipeActionItem instance. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | Component long-distance sliding deletion distance threshold. If -1.0f is returned, the return fails.<br>        The possible cause of the failure is that the item parameter is abnormal, such as a null pointer. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**描述**

Set the event to be called when a sliding entry enters the deletion area.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | List Item SwipeActionItem instance. |
| void (\*callback)() | Callback Events. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(void* userData))
```

**描述**

Set the event triggered when a sliding entry enters the deletion area.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | List Item SwipeActionItem instance. |
| void\* userData | User defined data. |
| void (\*callback)(void\* userData) | Callback Events. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnAction()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnAction(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**描述**

Set the event to be called when a component enters the long-range deletion area and deletes a ListItem.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | List Item SwipeActionItem instance. |
| void (\*callback)() | Callback Events. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(void* userData))
```

**描述**

Set the event triggered when a component enters the long-range deletion area and deletes a ListItem.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | List Item SwipeActionItem instance. |
| void\* userData | User defined data. |
| void (\*callback)(void\* userData) | Callback Events. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**描述**

Set the event to be called when a sliding entry exits the deletion area.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | List Item SwipeActionItem instance. |
| void (\*callback)() | Callback Events. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(void* userData))
```

**描述**

Set the event triggered when a sliding entry exits the deletion area.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | List Item SwipeActionItem instance. |
| void\* userData | User defined data. |
| void (\*callback)(void\* userData) | Callback Events. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange(ArkUI_ListItemSwipeActionItem* item, void (*callback)(ArkUI_ListItemSwipeActionState swipeActionState))
```

**描述**

Set the event triggered when the sliding state of a list item changes.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | List Item SwipeActionItem instance. |
| void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState) | Callback Events.swipeActionState The changed state. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void* userData))
```

**描述**

Set the event triggered when the sliding state of a list item changes.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | List Item SwipeActionItem instance. |
| void\* userData | User defined data. |
| void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState | Callback Events.swipeActionState The changed state. |

### OH_ArkUI_ListItemSwipeActionOption_Create()

```c
ArkUI_ListItemSwipeActionOption* OH_ArkUI_ListItemSwipeActionOption_Create()
```

**描述**

Create a configuration item for the ListitemSwipeActionOption interface settings.

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption*](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md) | List Item SwipeActionOption configuration item instance.If the object returns a null pointer,<br>         it indicates a creation failure, and the reason for the failure may be that the address space is full. |

### OH_ArkUI_ListItemSwipeActionOption_Dispose()

```c
void OH_ArkUI_ListItemSwipeActionOption_Dispose(ArkUI_ListItemSwipeActionOption* option)
```

**描述**

Destroy the ListitemSwipeActionOption instance.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | List Item SwipeActionOption instance to be destroyed. |

### OH_ArkUI_ListItemSwipeActionOption_SetStart()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetStart(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)
```

**描述**

Set the layout content on the left (vertical layout) or top (horizontal layout)of the ListItem SwipeActionItem.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | List Item SwipeActionItem instance. |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Layout information. |

### OH_ArkUI_ListItemSwipeActionOption_SetEnd()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetEnd(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)
```

**描述**

Set the layout content on the right (vertical layout) or bottom (horizontal layout)of the ListItem SwipeActionItem.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | List Item SwipeActionItem instance. |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Layout information. |

### OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeEdgeEffect edgeEffect)
```

**描述**

Set the sliding effect.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | List Item SwipeActionItem instance. |
| [ArkUI_ListItemSwipeEdgeEffect](capi-native-type-h.md#arkui_listitemswipeedgeeffect) edgeEffect | Sliding effect. |

### OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect()

```c
int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect(ArkUI_ListItemSwipeActionOption* option)
```

**描述**

Get the sliding effect.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | List Item SwipeActionItem instance. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Sliding effect. The default return value is 0. If -1 is returned, the return fails.<br>        The possible cause of the failure is that the option parameter is abnormal, such as a null pointer. |

### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange(ArkUI_ListItemSwipeActionOption* option, void (*callback)(float offset))
```

**描述**

The event called when the sliding operation offset changes.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)\* option | List Item SwipeActionItem instance. |
| void (\*callback)(float offset) | Callback Events.offset Slide offset. |

### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData(ArkUI_ListItemSwipeActionOption* option, void* userData, void (*callback)(float offset, void* userData))
```

**描述**

Set the event triggered when the sliding operation offset changes.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)\* option | List Item SwipeActionItem instance. |
| void\* userData | User defined data. |
| void (\*callback)(float offset | Callback Events.offset Slide offset. |

### OH_ArkUI_ListChildrenMainSizeOption_Create()

```c
ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()
```

**描述**

Create configuration items for the ListChildrenMainSize interface settings.

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ListChildrenMainSize*](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) | ListChildrenMainSize configuration item instance.If the object returns a null pointer,<br>         it indicates a creation failure, and the reason for the failure may be that the address space is full. |

### OH_ArkUI_ListChildrenMainSizeOption_Dispose()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)
```

**描述**

Destroy the ListChildrenMainSize instance.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | The ListChildrenMainSize instance to be destroyed. |

### OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)
```

**描述**

Set the default size of ChildrenMainSizeOption for the List component.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize instance. |
| float defaultMainSize | The default size of the ListItem under the List, measured in vp. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 0 represents success. If defaultMainSize is less than 0 or option is a null pointer, return 401. |

### OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)
```

**描述**

Get the default size of ChildrenMainSizeOption for the List component.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize instance. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | The default size of the ListItem under the List is 0, measured in vp.<br>         When the option is a null pointer, it returns -1. |

### OH_ArkUI_ListChildrenMainSizeOption_Resize()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)
```

**描述**

Reset the array size of ChildrenMainSizeOption for the List component.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize instance. |
| int32_t totalSize | Array size. |

### OH_ArkUI_ListChildrenMainSizeOption_Splice()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)
```

**描述**

Resize the ChildrenMainSizeOption array operation on the List component.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize instance. |
| int32_t index | To modify the starting position of the MainSize array. |
| int32_t deleteCount | The number of MainSize arrays to be deleted starting from index. |
| int32_t addCount | The number of MainSize arrays to be added starting from index. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 0 represents success. If the function parameter is abnormal, return 401. |

### OH_ArkUI_ListChildrenMainSizeOption_UpdateSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)
```

**描述**

Update the value of the ChildrenMainSizeOption array in the List component.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize instance. |
| int32_t index | To modify the starting position of the MainSize array. |
| float mainSize | The actual modified value. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 0 represents success. If the function parameter is abnormal, return 401. |

### OH_ArkUI_ListChildrenMainSizeOption_GetMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)
```

**描述**

Get the value of the ChildrenMainSizeOption array for the List component.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize instance. |
| int32_t index | The index position of the value to be obtained. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | The value of the specific position of the array. If the function parameter is abnormal, return -1. |

### OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString()

```c
ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString(char* src)
```

**描述**

Create a image frame from the image path.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char* src | Indicates the image path. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo*](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md) | Returns the pointer to the image frame object.<br> If a null pointer is returned, the object fails to be created. The possible cause is that<br> the src parameter is abnormal, for example, the pointer is null. |

### OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor()

```c
ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor(ArkUI_DrawableDescriptor* drawable)
```

**描述**

Create a image frame from the drawable descriptor.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_DrawableDescriptor* drawable | Indicates the pointer to the drawable descriptor. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo*](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md) | Returns the pointer to the image frame object.<br> If a null pointer is returned, the object fails to be created. The possible cause is that<br> the drawable parameter is abnormal, for example, the pointer is null. |

### OH_ArkUI_ImageAnimatorFrameInfo_Dispose()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_Dispose(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**描述**

Destroy the pointer to the image frame.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Indicates the pointer to the image frame. |

### OH_ArkUI_ImageAnimatorFrameInfo_SetWidth()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t width)
```

**描述**

Set the width of the image frame.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Indicates the pointer to the image frame. |
| int32_t width | Indicates the width of the image frame, and the unit is PX. |

### OH_ArkUI_ImageAnimatorFrameInfo_GetWidth()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**描述**

Get the width of the image frame.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Indicates the pointer to the image frame. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Return the width of the image frame, and the unit is PX. Return 0 when the imageInfo is null. |

### OH_ArkUI_ImageAnimatorFrameInfo_SetHeight()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t height)
```

**描述**

Set the height of the image frame.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Indicates the pointer to the image frame. |
| int32_t height | Indicates the height of the image frame, and the unit is PX. |

### OH_ArkUI_ImageAnimatorFrameInfo_GetHeight()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**描述**

Get the height of the image frame.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Indicates the pointer to the image frame. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Return the height of the image frame, and the unit is PX. Return 0 when the imageInfo is null. |

### OH_ArkUI_ImageAnimatorFrameInfo_SetTop()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t top)
```

**描述**

Set the vertical coordinate of the image relative to the upper left corner of the widget.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Indicates the pointer to the image frame. |
| int32_t top | Indicates the vertical coordinate of the image relative to the upper left corner of the widget,and the unit is PX. |

### OH_ArkUI_ImageAnimatorFrameInfo_GetTop()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**描述**

Get the vertical coordinate of the image relative to the upper left corner of the widget.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Indicates the pointer to the image frame. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the vertical coordinate of the image relative to the upper left corner of the widget,<br> and the unit is PX. Return 0 when the imageInfo is null. |

### OH_ArkUI_ImageAnimatorFrameInfo_SetLeft()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t left)
```

**描述**

Set the horizontal coordinate of the image relative to the upper left corner of the widget.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Indicates the pointer to the image frame. |
| int32_t left | Indicates the horizontal coordinate of the image relative to the upper left corner of the widget,and the unit is PX. |

### OH_ArkUI_ImageAnimatorFrameInfo_GetLeft()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**描述**

Get the horizontal coordinate of the image relative to the upper left corner of the widget.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Indicates the pointer to the image frame. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the horizontal coordinate of the image relative to the upper left corner of the widget,<br> and the unit is PX. Return 0 when the imageInfo is null. |

### OH_ArkUI_ImageAnimatorFrameInfo_SetDuration()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t duration)
```

**描述**

Set the playback duration of the image frame.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Indicates the pointer to the image frame. |
| int32_t duration | Indicates the playback duration of each image frame, and the unit is milliseconds. |

### OH_ArkUI_ImageAnimatorFrameInfo_GetDuration()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**描述**

Get the playback duration of the image frame.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Indicates the pointer to the image frame. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the playback duration of the image frame, and the unit is milliseconds.<br> Return 0 when the imageInfo is null. |

### OH_ArkUI_AccessibilityState_Create()

```c
ArkUI_AccessibilityState* OH_ArkUI_AccessibilityState_Create(void)
```

**描述**

Create accessibility state.

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_AccessibilityState*](capi-arkui-nativemodule-arkui-accessibilitystate.md) | Returns the pointer to the accessibility state object.<br> If a null pointer is returned, the object fails to be created. The possible cause is that the address space is full. |

### OH_ArkUI_AccessibilityState_Dispose()

```c
void OH_ArkUI_AccessibilityState_Dispose(ArkUI_AccessibilityState* state)
```

**描述**

Dispose accessibility state.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | accessibility state object. |

### OH_ArkUI_AccessibilityState_SetDisabled()

```c
void OH_ArkUI_AccessibilityState_SetDisabled(ArkUI_AccessibilityState* state, int32_t isDisabled)
```

**描述**

Set accessibility state disabled.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | accessibility state object. |
| int32_t isDisabled | accessibility state disabled, Value 1 indicates disabled and 0 indicates enbled. |

### OH_ArkUI_AccessibilityState_IsDisabled()

```c
int32_t OH_ArkUI_AccessibilityState_IsDisabled(ArkUI_AccessibilityState* state)
```

**描述**

Get accessibility state disabled.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | accessibility state object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | accessibility state disabled, Value 1 indicates disabled and 0 indicates enbled. The default value is 0.<br>         If the function parameter is abnormal, return the default value. |

### OH_ArkUI_AccessibilityState_SetSelected()

```c
void OH_ArkUI_AccessibilityState_SetSelected(ArkUI_AccessibilityState* state, int32_t isSelected)
```

**描述**

Set accessibility state selected.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | accessibility state object. |
| int32_t isSelected | accessibility state selected, Value 1 indicates selected, and 0 indicates not selected.The default value is 0. |

### OH_ArkUI_AccessibilityState_IsSelected()

```c
int32_t OH_ArkUI_AccessibilityState_IsSelected(ArkUI_AccessibilityState* state)
```

**描述**

Get accessibility state selected.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | accessibility state object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | accessibility state selected, Value 1 indicates selected, and 0 indicates not selected.<br>         The default value is 0.<br>         If the function parameter is abnormal, return the default value. |

### OH_ArkUI_AccessibilityState_SetCheckedState()

```c
void OH_ArkUI_AccessibilityState_SetCheckedState(ArkUI_AccessibilityState* state, int32_t checkedState)
```

**描述**

Set accessibility checked state.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | accessibility state object. |
| int32_t checkedState | checked state, and uses the [ArkUI_AccessibilityCheckedState](capi-native-type-h.md#arkui_accessibilitycheckedstate) enumeration value,The default value is ARKUI_ACCESSIBILITY_UNCHECKED. |

### OH_ArkUI_AccessibilityState_GetCheckedState()

```c
int32_t OH_ArkUI_AccessibilityState_GetCheckedState(ArkUI_AccessibilityState* state)
```

**描述**

Get accessibility checked state.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | accessibility state object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | checked state, and uses the [ArkUI_AccessibilityCheckedState](capi-native-type-h.md#arkui_accessibilitycheckedstate) enumeration value,<br>         The default value is ARKUI_ACCESSIBILITY_UNCHECKED.<br>         If the function parameter is abnormal, return the default value. |

### OH_ArkUI_AccessibilityValue_Create()

```c
ArkUI_AccessibilityValue* OH_ArkUI_AccessibilityValue_Create(void)
```

**描述**

Create accessibility value.

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_AccessibilityValue*](capi-arkui-nativemodule-arkui-accessibilityvalue.md) | Returns the pointer to the accessibility state object.<br> If a null pointer is returned, the object fails to be created. The possible cause is that the address space is full. |

### OH_ArkUI_AccessibilityValue_Dispose()

```c
void OH_ArkUI_AccessibilityValue_Dispose(ArkUI_AccessibilityValue* value)
```

**描述**

Dispose accessibility value.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |

### OH_ArkUI_AccessibilityValue_SetMin()

```c
void OH_ArkUI_AccessibilityValue_SetMin(ArkUI_AccessibilityValue* value, int32_t min)
```

**描述**

Set accessibility minimum value.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |
| int32_t min | minimum value based on range components, The default value is -1. |

### OH_ArkUI_AccessibilityValue_GetMin()

```c
int32_t OH_ArkUI_AccessibilityValue_GetMin(ArkUI_AccessibilityValue* value)
```

**描述**

Get accessibility minimum value.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | minimum value based on range components, The default value is -1.<br>         If the function parameter is abnormal, return -1. |

### OH_ArkUI_AccessibilityValue_SetMax()

```c
void OH_ArkUI_AccessibilityValue_SetMax(ArkUI_AccessibilityValue* value, int32_t max)
```

**描述**

Set accessibility minimum value.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |
| int32_t max | maximum value based on range components, The default value is -1. |

### OH_ArkUI_AccessibilityValue_GetMax()

```c
int32_t OH_ArkUI_AccessibilityValue_GetMax(ArkUI_AccessibilityValue* value)
```

**描述**

Get accessibility minimum value.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | maximum value based on range components, The default value is -1.<br>         If the function parameter is abnormal, return -1. |

### OH_ArkUI_AccessibilityValue_SetCurrent()

```c
void OH_ArkUI_AccessibilityValue_SetCurrent(ArkUI_AccessibilityValue* value, int32_t current)
```

**描述**

Set accessibility current value.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |
| int32_t current | value based on range components, The default value is -1. |

### OH_ArkUI_AccessibilityValue_GetCurrent()

```c
int32_t OH_ArkUI_AccessibilityValue_GetCurrent(ArkUI_AccessibilityValue* value)
```

**描述**

Get accessibility current value.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | current value based on range components, The default value is -1.<br>         If the function parameter is abnormal, return -1. |

### OH_ArkUI_AccessibilityValue_SetRangeMin()

```c
void OH_ArkUI_AccessibilityValue_SetRangeMin(ArkUI_AccessibilityValue* value, int32_t rangeMin)
```

**描述**

Set accessibility minimum value.

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |
| int32_t rangeMin | minimum value based on range components, The default value is -1. |

### OH_ArkUI_AccessibilityValue_GetRangeMin()

```c
int32_t OH_ArkUI_AccessibilityValue_GetRangeMin(ArkUI_AccessibilityValue* value)
```

**描述**

Get accessibility minimum value.

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | minimum value based on range components, The default value is -1.<br>         If the function parameter is abnormal, return -1. |

### OH_ArkUI_AccessibilityValue_SetRangeMax()

```c
void OH_ArkUI_AccessibilityValue_SetRangeMax(ArkUI_AccessibilityValue* value, int32_t rangeMax)
```

**描述**

Set accessibility maximum value.

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |
| int32_t rangeMax | maximum value based on range components, The default value is -1. |

### OH_ArkUI_AccessibilityValue_GetRangeMax()

```c
int32_t OH_ArkUI_AccessibilityValue_GetRangeMax(ArkUI_AccessibilityValue* value)
```

**描述**

Get accessibility maximum value.

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | maximum value based on range components, The default value is -1.<br>         If the function parameter is abnormal, return -1. |

### OH_ArkUI_AccessibilityValue_SetRangeCurrent()

```c
void OH_ArkUI_AccessibilityValue_SetRangeCurrent(ArkUI_AccessibilityValue* value, int32_t rangeCurrent)
```

**描述**

Set accessibility current value.

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |
| int32_t rangeCurrent | value based on range components, The default value is -1. |

### OH_ArkUI_AccessibilityValue_GetRangeCurrent()

```c
int32_t OH_ArkUI_AccessibilityValue_GetRangeCurrent(ArkUI_AccessibilityValue* value)
```

**描述**

Get accessibility current value.

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | current value based on range components, The default value is -1.<br>         If the function parameter is abnormal, return -1. |

### OH_ArkUI_AccessibilityValue_SetText()

```c
void OH_ArkUI_AccessibilityValue_SetText(ArkUI_AccessibilityValue* value, const char* text)
```

**描述**

Set accessibility text value.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |
| const char* text | The textual description information of the component, which defaults to an empty string. |

### OH_ArkUI_AccessibilityValue_GetText()

```c
const char* OH_ArkUI_AccessibilityValue_GetText(ArkUI_AccessibilityValue* value)
```

**描述**

Get accessibility text value.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | accessibility value object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | The textual description information of the component, which defaults to an empty string;<br>         If the function parameter is abnormal, return null. |

### OH_ArkUI_CustomProperty_Destroy()

```c
void OH_ArkUI_CustomProperty_Destroy(ArkUI_CustomProperty* handle)
```

**描述**

Destroy the instance of Customs Property.

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md)* handle | The instance of Customs Property to be destroyed. |

### OH_ArkUI_CustomProperty_GetStringValue()

```c
const char* OH_ArkUI_CustomProperty_GetStringValue(ArkUI_CustomProperty* handle)
```

**描述**

Get custom attribute value information.

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md)* handle | Custom attribute object pointer. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | Customize the value information within the attribute structure. |

### OH_ArkUI_HostWindowInfo_GetName()

```c
const char* OH_ArkUI_HostWindowInfo_GetName(ArkUI_HostWindowInfo* info)
```

**描述**

Get window name from HostWindowInfo.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)* info | HostWindowInfo object pointer. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | Window name in HostWindowInfo. |

### OH_ArkUI_HostWindowInfo_Destroy()

```c
void OH_ArkUI_HostWindowInfo_Destroy(ArkUI_HostWindowInfo* info)
```

**描述**

Destroy the instance of HostWindowInfo.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)* info | Instance of HostWindowInfo to be destroyed. |

### OH_ArkUI_ActiveChildrenInfo_Destroy()

```c
void OH_ArkUI_ActiveChildrenInfo_Destroy(ArkUI_ActiveChildrenInfo* handle)
```

**描述**

Destroy ActiveChildenInfo instance.

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)* handle | ActiveChild instance to be destroyed. |

### OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex()

```c
ArkUI_NodeHandle OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex(ArkUI_ActiveChildrenInfo* handle, int32_t index)
```

**描述**

Retrieve the child nodes of ActiveChildenInfo with the structure index.

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)* handle | The ActiveChildenInfo instance for obtaining information. |
| int32_t index | The index of child nodes. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | The child node pointer corresponding to the index. Return nullptr in case of exception. |

### OH_ArkUI_ActiveChildrenInfo_GetCount()

```c
int32_t OH_ArkUI_ActiveChildrenInfo_GetCount(ArkUI_ActiveChildrenInfo* handle)
```

**描述**

Retrieve the number of nodes within the structure of ActiveChildenInfo.

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)* handle | The ActiveChildenInfo instance for obtaining information. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Number of child nodes. Default value: 0. |

### OH_ArkUI_CrossLanguageOption_Create()

```c
ArkUI_CrossLanguageOption* OH_ArkUI_CrossLanguageOption_Create(void)
```

**描述**

Create a cross-language option instance.

**起始版本：** 15

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_CrossLanguageOption*](capi-arkui-nativemodule-arkui-crosslanguageoption.md) | Returns a cross-language option instance. If the result is a null pointer, it may be out of memory. |

### OH_ArkUI_CrossLanguageOption_Destroy()

```c
void OH_ArkUI_CrossLanguageOption_Destroy(ArkUI_CrossLanguageOption* option)
```

**描述**

Destroy the cross-language option instance.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | The cross-language option instance. |

### OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus()

```c
void OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus(ArkUI_CrossLanguageOption* option, bool enabled)
```

**描述**

Enable the attribute setting in the cross-language option.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | The cross-language option. |
| bool enabled | The attribute setting in the cross-language option.Default value: false. |

### OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus()

```c
bool OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus(ArkUI_CrossLanguageOption* option)
```

**描述**

Get the attribute setting enable of the cross-language option.

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | The cross-language option. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | The attribute setting enable of the cross-language option. |

### OH_ArkUI_TextPickerRangeContentArray_Create()

```c
ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)
```

**描述**

Creates a TextPickerRangeContent instance.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t length | The length of the picker array. Value range: [1, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_TextPickerRangeContentArray* | Returns a pointer to the created instance on success. Initialize each item of the array<br>         as a null pointer;call [OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex](capi-native-type-h.md#oh_arkui_textpickerrangecontentarray_seticonatindex) and/or<br>         [OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex](capi-native-type-h.md#oh_arkui_textpickerrangecontentarray_settextatindex) for each index as needed.<br>         Returns <b>nullptr</b> if <b>length</b> is not in <b>[1, +∞)</b>.<br>         When the object is no longer used, release it with [OH_ArkUI_TextPickerRangeContentArray_Destroy](capi-native-type-h.md#oh_arkui_textpickerrangecontentarray_destroy). |

### OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)
```

**描述**

Sets the icon resource path or URI for one item in an {@link ArkUI_TextPickerRangeContentArray}.

>**说明：** 
>If an icon was already set at <b>index</b>, the previous buffer is released before assigning the new value.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_TextPickerRangeContentArray* handle | Pointer returned by [OH_ArkUI_TextPickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textpickerrangecontentarray_create). If <b>nullptr</b>, thisfunction has no effect. |
| char* icon | Null-terminated C string for the icon (path or URI). The content is copied into the array; the callerkeeps ownership of <b>icon</b>. If <b>nullptr</b>, this function has no effect. |
| int32_t index | Index of the item to set. Valid values are greater than or equal to <b>0</b> and less than the<b>length</b> argument passed to [OH_ArkUI_TextPickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textpickerrangecontentarray_create). Otherwise this functiondoes nothing. |

### OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)
```

**描述**

Sets the display text for one item in an {@link ArkUI_TextPickerRangeContentArray}.

>**说明：** 
>If text was already set at <b>index</b>, the previous buffer is released before assigning the new value.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_TextPickerRangeContentArray* handle | Pointer returned by [OH_ArkUI_TextPickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textpickerrangecontentarray_create). If <b>nullptr</b>, thisfunction has no effect. |
| char* text | Null-terminated C string shown for the item. The content is copied into the array; the caller keepsownership of <b>text</b>. If <b>nullptr</b>, this function has no effect. |
| int32_t index | Index of the item to set. Valid values are greater than or equal to <b>0</b> and less than the<b>length</b> argument passed to [OH_ArkUI_TextPickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textpickerrangecontentarray_create). Otherwise this functiondoes nothing. |

### OH_ArkUI_TextPickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)
```

**描述**

Releases an {@link ArkUI_TextPickerRangeContentArray} created by[OH_ArkUI_TextPickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textpickerrangecontentarray_create).

>**说明：** 
>After this call, <b>handle</b> must not be used. Do not pass pointers that were not returned by
 *       [OH_ArkUI_TextPickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textpickerrangecontentarray_create).

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_TextPickerRangeContentArray* handle | Instance to destroy. If <b>nullptr</b>, this function has no effect. |

### OH_ArkUI_TextCascadePickerRangeContentArray_Create()

```c
ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)
```

**描述**

Allocates one column level of an interconnected (cascade) TextPicker range. Use with range type[ARKUI_TEXTPICKER_RANGETYPE_CASCADE_RANGE_CONTENT](capi-native-type-h.md#arkui_textpickerrangetype). The returned pointer addresses a contiguous arrayof sibling nodes; each node may carry display text and an optional next-level range from[OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex](capi-native-type-h.md#oh_arkui_textcascadepickerrangecontentarray_setchildatindex).

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t length | Number of sibling entries on this column. Value range: <b>[1, +∞)</b>. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_TextCascadePickerRangeContentArray* | Returns a pointer to the first sibling node when <b>length</b> is in <b>[1, +∞)</b>; returns <b>nullptr</b><br>         otherwise. The sibling count used for bounds checks equals <b>length</b>. |

### OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)
```

**描述**

Sets the display text for one sibling node on a cascade TextPicker level.

>**说明：** 
>If text was already set at <b>index</b>, the previous buffer is released before assigning the new value.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_TextCascadePickerRangeContentArray* handle | Pointer returned by [OH_ArkUI_TextCascadePickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textcascadepickerrangecontentarray_create). If <b>nullptr</b>,this function has no effect. |
| char* text | Null-terminated C string. The content is copied; the caller keeps ownership of <b>text</b>. If<b>nullptr</b>, this function has no effect. |
| int32_t index | Index of the sibling to set. Valid values are greater than or equal to <b>0</b> and less than the<b>length</b> argument passed to [OH_ArkUI_TextCascadePickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textcascadepickerrangecontentarray_create). Otherwise thisfunction does nothing. |

### OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)
```

**描述**

Sets the childs info of items in a multi text picker ranges.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_TextCascadePickerRangeContentArray* handle | Pointer returned by [OH_ArkUI_TextCascadePickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textcascadepickerrangecontentarray_create). If <b>nullptr</b>,this function has no effect. |
| ArkUI_TextCascadePickerRangeContentArray* child | Pointer returned by [OH_ArkUI_TextCascadePickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textcascadepickerrangecontentarray_create) for the child column.If <b>nullptr</b>, this function has no effect. If a subtree already exists at <b>index</b>, it is destroyedwith [OH_ArkUI_TextCascadePickerRangeContentArray_Destroy](capi-native-type-h.md#oh_arkui_textcascadepickerrangecontentarray_destroy) before the new <b>child</b> is stored.While <b>child</b> stays attached under the parent, the caller must not call[OH_ArkUI_TextCascadePickerRangeContentArray_Destroy](capi-native-type-h.md#oh_arkui_textcascadepickerrangecontentarray_destroy) on <b>child</b>. |
| int32_t index | Index of the sibling that owns the subtree. Valid values are greater than or equal to <b>0</b> and lessthan the <b>length</b> argument passed to [OH_ArkUI_TextCascadePickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textcascadepickerrangecontentarray_create).Otherwise this function does nothing. |

### OH_ArkUI_TextCascadePickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy(ArkUI_TextCascadePickerRangeContentArray* handle)
```

**描述**

Releases a cascade range level allocated with [OH_ArkUI_TextCascadePickerRangeContentArray_Create](capi-native-type-h.md#oh_arkui_textcascadepickerrangecontentarray_create).

>**说明：** 
>Do not call [OH_ArkUI_TextCascadePickerRangeContentArray_Destroy](capi-native-type-h.md#oh_arkui_textcascadepickerrangecontentarray_destroy) on a <b>child</b> while
 *       it is still stored in a parent's {@code children}.

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| ArkUI_TextCascadePickerRangeContentArray* handle | Instance to destroy. If <b>nullptr</b>, this function has no effect. |

### OH_ArkUI_EmbeddedComponentOption_Create()

```c
ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()
```

**描述**

Create an object for the EmbeddedComponent option.

**起始版本：** 20

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_EmbeddedComponentOption*](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md) | A pointer to the object of the EmbeddedComponent option. |

### OH_ArkUI_EmbeddedComponentOption_Dispose()

```c
void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)
```

**描述**

Destroy the object by EmbeddedComponent option.

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* option | Pointer to the object by the EmbeddeComponent to be destroyed. |

### OH_ArkUI_EmbeddedComponentOption_SetOnError()

```c
void OH_ArkUI_EmbeddedComponentOption_SetOnError(ArkUI_EmbeddedComponentOption* option, void (*callback)(int32_t code, const char* name, const char* message))
```

**描述**

Set the onError of EmbeddedComponent.

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)\* option | Pointer to the object option by the EmbeddedComponent. |
| void (\*callback)(int32_t code | Common error information about the API invoking failure. |
| const char\* name | Common error name information about the API invoking failure. |
| const char\* message) | Common error message information about the API invoking failure. |

### OH_ArkUI_EmbeddedComponentOption_SetOnTerminated()

```c
void OH_ArkUI_EmbeddedComponentOption_SetOnTerminated(ArkUI_EmbeddedComponentOption* option, void (*callback)(int32_t code, AbilityBase_Want* want))
```

**描述**

Set the onTerminated of EmbeddedComponent.

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)\* option | Pointer to the object option by the EmbeddedComponent. |
| void (\*callback)(int32_t code | Result code returned when the EmbeddedUIExtensionAbility exits. |
| [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md)\* want) | Data returned when the EmbeddedUIExtensionAbility exits. |

### OH_ArkUI_ListItemSwipeAction_Expand()

```c
int32_t OH_ArkUI_ListItemSwipeAction_Expand(ArkUI_NodeHandle node, ArkUI_ListItemSwipeActionDirection direction)
```

**描述**

Expand the swipe action.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | List Item node. |
| [ArkUI_ListItemSwipeActionDirection](capi-native-type-h.md#arkui_listitemswipeactiondirection) direction | expand direction of swipeAction. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_ERROR](capi-native-type-h.md#arkui_errorcode) The component type of the node is incorrect.<br>         [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) The node not mounted to component tree. |

### OH_ArkUI_ListItemSwipeAction_Collapse()

```c
int32_t OH_ArkUI_ListItemSwipeAction_Collapse(ArkUI_NodeHandle node)
```

**描述**

Collapse the swipe action.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | List Item node. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) success.<br>         [ARKUI_ERROR_CODE_PARAM_ERROR](capi-native-type-h.md#arkui_errorcode) The component type of the node is incorrect.<br>         [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) The node not mounted to component tree. |

### OH_ArkUI_PositionEdges_Create()

```c
ArkUI_PositionEdges* OH_ArkUI_PositionEdges_Create()
```

**描述**

Create an edge object for position attribute.

**起始版本：** 21

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_PositionEdges*](capi-arkui-nativemodule-arkui-positionedges.md) | A pointer to the edge object. |

### OH_ArkUI_PositionEdges_Copy()

```c
ArkUI_PositionEdges* OH_ArkUI_PositionEdges_Copy(const ArkUI_PositionEdges* edges)
```

**描述**

Creates a deep copy of an edge object for position attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | A pointer to an edge object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_PositionEdges*](capi-arkui-nativemodule-arkui-positionedges.md) | A pointer to the new edge object. |

### OH_ArkUI_PositionEdges_Dispose()

```c
void OH_ArkUI_PositionEdges_Dispose(ArkUI_PositionEdges* edges)
```

**描述**

Dispose an edge object for position attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object to be disposed. |

### OH_ArkUI_PositionEdges_SetTop()

```c
void OH_ArkUI_PositionEdges_SetTop(ArkUI_PositionEdges* edges, float value)
```

**描述**

Sets the top edge of an edge object for position attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float value | The distance of top edge to the corresponding edge of parent container, in vp. |

### OH_ArkUI_PositionEdges_GetTop()

```c
int32_t OH_ArkUI_PositionEdges_GetTop(ArkUI_PositionEdges* edges, float* value)
```

**描述**

Gets the top edge of an edge object for position attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float* value | The distance of top edge to the corresponding edge of parent container, in vp. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>      Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the parameter is invalid. |

### OH_ArkUI_PositionEdges_SetLeft()

```c
void OH_ArkUI_PositionEdges_SetLeft(ArkUI_PositionEdges* edges, float value)
```

**描述**

Sets the left edge of an edge object for position attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float value | The distance of left edge to the corresponding edge of parent container, in vp. |

### OH_ArkUI_PositionEdges_GetLeft()

```c
int32_t OH_ArkUI_PositionEdges_GetLeft(ArkUI_PositionEdges* edges, float* value)
```

**描述**

Gets the left edge of an edge object for position attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float* value | The distance of left edge to the corresponding edge of parent container, in vp. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>      Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the parameter is invalid. |

### OH_ArkUI_PositionEdges_SetBottom()

```c
void OH_ArkUI_PositionEdges_SetBottom(ArkUI_PositionEdges* edges, float value)
```

**描述**

Sets the bottom edge of an edge object for position attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float value | The distance of bottom edge to the corresponding edge of parent container, in vp. |

### OH_ArkUI_PositionEdges_GetBottom()

```c
int32_t OH_ArkUI_PositionEdges_GetBottom(ArkUI_PositionEdges* edges, float* value)
```

**描述**

Gets the bottom edge of an edge object for position attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float* value | The distance of bottom edge to the corresponding edge of parent container, in vp. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>      Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the parameter is invalid. |

### OH_ArkUI_PositionEdges_SetRight()

```c
void OH_ArkUI_PositionEdges_SetRight(ArkUI_PositionEdges* edges, float value)
```

**描述**

Sets the right edge of an edge object for position attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float value | The distance of right edge to the corresponding edge of parent container, in vp. |

### OH_ArkUI_PositionEdges_GetRight()

```c
int32_t OH_ArkUI_PositionEdges_GetRight(ArkUI_PositionEdges* edges, float* value)
```

**描述**

Gets the right edge of an edge object for position attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float* value | The distance of right edge to the corresponding edge of parent container, in vp. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>      Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the parameter is invalid. |

### OH_ArkUI_PixelRoundPolicy_Create()

```c
ArkUI_PixelRoundPolicy* OH_ArkUI_PixelRoundPolicy_Create()
```

**描述**

Create a policy object for PixelRound attribute.

**起始版本：** 21

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_PixelRoundPolicy*](capi-arkui-nativemodule-arkui-pixelroundpolicy.md) | A pointer to the policy object. |

### OH_ArkUI_PixelRoundPolicy_Dispose()

```c
void OH_ArkUI_PixelRoundPolicy_Dispose(ArkUI_PixelRoundPolicy* policy)
```

**描述**

Dispose a policy object for PixelRound attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object to be disposed. |

### OH_ArkUI_PixelRoundPolicy_SetTop()

```c
void OH_ArkUI_PixelRoundPolicy_SetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)
```

**描述**

Sets the top edge of a policy object for PixelRound attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-native-type-h.md#arkui_pixelroundcalcpolicy) value | The CalcPolicy of top edge. |

### OH_ArkUI_PixelRoundPolicy_GetTop()

```c
int32_t OH_ArkUI_PixelRoundPolicy_GetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)
```

**描述**

Gets the top edge of a policy object for PixelRound attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-native-type-h.md#arkui_pixelroundcalcpolicy)* value | The CalcPolicy of top edge. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>      Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the parameter is invalid. |

### OH_ArkUI_PixelRoundPolicy_SetStart()

```c
void OH_ArkUI_PixelRoundPolicy_SetStart(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)
```

**描述**

Sets the start edge of a policy object for PixelRound attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-native-type-h.md#arkui_pixelroundcalcpolicy) value | The CalcPolicy of start edge. |

### OH_ArkUI_PixelRoundPolicy_GetStart()

```c
int32_t OH_ArkUI_PixelRoundPolicy_GetStart(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)
```

**描述**

Gets the start edge of a policy object for PixelRound attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-native-type-h.md#arkui_pixelroundcalcpolicy)* value | The CalcPolicy of start edge. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>      Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the parameter is invalid. |

### OH_ArkUI_PixelRoundPolicy_SetBottom()

```c
void OH_ArkUI_PixelRoundPolicy_SetBottom(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)
```

**描述**

Sets the bottom edge of a policy object for PixelRound attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-native-type-h.md#arkui_pixelroundcalcpolicy) value | The CalcPolicy of bottom edge. |

### OH_ArkUI_PixelRoundPolicy_GetBottom()

```c
int32_t OH_ArkUI_PixelRoundPolicy_GetBottom(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)
```

**描述**

Gets the bottom edge of a policy object for PixelRound attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-native-type-h.md#arkui_pixelroundcalcpolicy)* value | The CalcPolicy of bottom edge. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>      Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the parameter is invalid. |

### OH_ArkUI_PixelRoundPolicy_SetEnd()

```c
void OH_ArkUI_PixelRoundPolicy_SetEnd(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)
```

**描述**

Sets the end edge of a policy object for PixelRound attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-native-type-h.md#arkui_pixelroundcalcpolicy) value | The CalcPolicy of end edge. |

### OH_ArkUI_PixelRoundPolicy_GetEnd()

```c
int32_t OH_ArkUI_PixelRoundPolicy_GetEnd(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)
```

**描述**

Gets the end edge of a policy object for PixelRound attribute.

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-native-type-h.md#arkui_pixelroundcalcpolicy)* value | The CalcPolicy of end edge. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | Returns the result code.<br>      Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>      Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the parameter is invalid. |

### OH_ArkUI_TextMenuItem_SetContent()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetContent(ArkUI_TextMenuItem* item, const char* content)
```

**描述**

Set text menu item title.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | The text menu item. |
| const char* content | The name of the text menu item, which defaults to an empty string. The string will copy to framework. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextMenuItem_GetContent()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetContent(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

Get text menu item title.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | The text menu item object. |
| char* buffer | The buffer of the text menu content, memory space needs to be allocated by the developer. |
| int32_t bufferSize | The name of the text menu item, which defaults to an empty string; |
| int32_t* writeLength | Indicates the string length actually written to the bufferwhen returning [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode).Indicates the minimum buffer size that can accommodate the targetwhen [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) is returned. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | The error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the node, buffer or writeLength is null.<br>         [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_TextMenuItem_SetIcon()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetIcon(ArkUI_TextMenuItem* item, const char* icon)
```

**描述**

Set text menu item icon.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | The text menu item. |
| const char* icon | The text menu item icon resource, which defaults to an empty string. The string will copy to framework. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextMenuItem_GetIcon()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetIcon(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

Get text menu item icon.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | The text menu item object |
| char* buffer | The buffer of the text menu content, memory space needs to be allocated by the developer. |
| int32_t bufferSize | The icon of the text menu item, which defaults to an empty string; |
| int32_t* writeLength | Indicates the string length actually written to the bufferwhen returning [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode).Indicates the minimum buffer size that can accommodate the targetwhen [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) is returned. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | The error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the node, buffer or writeLength is null.<br>         [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_TextMenuItem_SetLabelInfo()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetLabelInfo(ArkUI_TextMenuItem* item, const char* labelInfo)
```

**描述**

Set text menu item label info for keyboard shortcut.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | The text menu item. |
| const char* labelInfo | The text menu item shortcut displays, which defaults to an empty string.The string will copy to framework. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextMenuItem_GetLabelInfo()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetLabelInfo(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

Get text menu item label info for keyboard shortcut..

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | The text menu item object |
| char* buffer | The buffer of the text menu content, memory space needs to be allocated by the developer. |
| int32_t bufferSize | The shortcuts of the text menu item, which defaults to an empty string; |
| int32_t* writeLength | Indicates the string length actually written to the bufferwhen returning [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode).Indicates the minimum buffer size that can accommodate the targetwhen [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) is returned. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | The error code.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the node, buffer or writeLength is null.<br>         [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) If the buffer size is less than the minimum buffer size. |

### OH_ArkUI_TextMenuItem_SetId()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetId(ArkUI_TextMenuItem* item, int32_t id)
```

**描述**

Set text menu item id.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | The text menu item. |
| int32_t id | The text menu id. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextMenuItem_GetId()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetId(const ArkUI_TextMenuItem* item, int32_t* id)
```

**描述**

Get text menu item id.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | The text menu item object |
| int32_t* id | The text menu item id; |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextMenuItemArray_GetSize()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_GetSize(ArkUI_TextMenuItemArray* items, int32_t* size)
```

**描述**

Get the size of text menu items.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | The text menu items. |
| int32_t* size | The size of text menu items. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextMenuItemArray_GetItem()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_GetItem(ArkUI_TextMenuItemArray* items, int32_t index, ArkUI_TextMenuItem** item)
```

**描述**

Get text menu item at index.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | The text menu items. |
| int32_t index | The index of text menu items. |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)** item | The text menu item at index of array. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextMenuItemArray_Insert()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Insert(ArkUI_TextMenuItemArray* items, ArkUI_TextMenuItem* item, int32_t index)
```

**描述**

Insert text menu item at index.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | The text menu items. |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | The text menu item at index of array. The item will copy by framework. |
| int32_t index | The index of text menu items. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextMenuItemArray_Erase()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Erase(ArkUI_TextMenuItemArray* items, int32_t index)
```

**描述**

Erase text menu item at index.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | The text menu items. |
| int32_t index | The index of text menu items. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextMenuItemArray_Clear()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Clear(ArkUI_TextMenuItemArray* items)
```

**描述**

Clear all the items.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | The text menu items. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextEditMenuOptions_RegisterOnCreateMenuCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnCreateMenuCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextCreateMenuCallback cb)
```

**描述**

Set the event to be called when text menu create.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | Pointer to the ArkUI_TextEditMenuOptions object. |
| void* userData | The user data. |
| [ArkUI_TextCreateMenuCallback](capi-text-common-h.md#arkui_textcreatemenucallback) cb | The create callback function. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextEditMenuOptions_RegisterOnPrepareMenuCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnPrepareMenuCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextPrepareMenuCallback cb)
```

**描述**

Set the event to be called when menu prepare.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | Pointer to the ArkUI_TextEditMenuOptions object. |
| void* userData | The user data. |
| [ArkUI_TextPrepareMenuCallback](capi-text-common-h.md#arkui_textpreparemenucallback) cb | The prepare callback function. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextEditMenuOptions_RegisterOnMenuItemClickCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnMenuItemClickCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextMenuItemClickCallback cb)
```

**描述**

Set the event to be called when menu item click.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | Pointer to the ArkUI_TextEditMenuOptions object. |
| void* userData | The user data. |
| [ArkUI_TextMenuItemClickCallback](capi-text-common-h.md#arkui_textmenuitemclickcallback) cb | The menu item click callback function. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextSelectionMenuOptions_SetSpanType()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetSpanType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextSpanType textSpanType)
```

**描述**

Sets the recognition types of a configuration object for selected text recognition.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the ArkUI_TextSelectionMenuOptions object. |
| [ArkUI_TextSpanType](capi-text-common-h.md#arkui_textspantype) textSpanType | The span type of [ArkUI_TextSpanType](capi-text-common-h.md#arkui_textspantype). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextSelectionMenuOptions_GetSpanType()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetSpanType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextSpanType* spanType)
```

**描述**

Gets the span type select menu options.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the ArkUI_TextSelectionMenuOptions object. |
| [ArkUI_TextSpanType](capi-text-common-h.md#arkui_textspantype)* spanType | the text span type [ArkUI_TextSpanType](capi-text-common-h.md#arkui_textspantype). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextSelectionMenuOptions_SetContentNode()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetContentNode(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_NodeHandle node)
```

**描述**

Set custom text menu node of text.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the ArkUI_TextSelectionMenuOptions object. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | The custom menu node. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextSelectionMenuOptions_GetContentNode()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetContentNode(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_NodeHandle* node)
```

**描述**

Get custom text menu node of text.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the ArkUI_TextSelectionMenuOptions object. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* node | The custom menu node. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextSelectionMenuOptions_SetResponseType()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetResponseType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextResponseType responseType)
```

**描述**

Sets the recognition types of a configuration object for selected text recognition.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the ArkUI_TextSelectionMenuOptions object. |
| [ArkUI_TextResponseType](capi-text-common-h.md#arkui_textresponsetype) responseType | The response type of [ArkUI_TextResponseType](capi-text-common-h.md#arkui_textresponsetype). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextSelectionMenuOptions_GetResponseType()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetResponseType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextResponseType* responseType)
```

**描述**

Gets the response type select menu options.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the ArkUI_TextSelectionMenuOptions object. |
| [ArkUI_TextResponseType](capi-text-common-h.md#arkui_textresponsetype)* responseType | The text response type [ArkUI_TextResponseType](capi-text-common-h.md#arkui_textresponsetype). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuShowCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuShowCallback(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, void* userData, void (*callback)(int32_t start, int32_t end, void* userData))
```

**描述**

Set the event to be called when selection menu show.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)\* selectionMenuOptions | Pointer to the ArkUI_TextSelectionMenuOptions object. |
| void\* userData | The user data. |
| void (\*callback)(int32_t start | The callback function of menu show.start The start offset of the selected content.end The end offset of the selected content.userData The user data. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuHideCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuHideCallback(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, void* userData, void (*callback)(int32_t start, int32_t end, void* userData))
```

**描述**

Set the event to be called when selection menu hide.

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)\* selectionMenuOptions | Pointer to the ArkUI_TextSelectionMenuOptions object. |
| void\* userData | The user data. |
| void (\*callback)(int32_t start | The callback function of menu hide.start The start offset of the selected content.end The end offset of the selected content.userData The user data. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SelectionOptions_Create()

```c
ArkUI_SelectionOptions* OH_ArkUI_SelectionOptions_Create()
```

**描述**

Create selection options.

**起始版本：** 23

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_SelectionOptions* | A pointer to the selection options object. |

### OH_ArkUI_SelectionOptions_Dispose()

```c
void OH_ArkUI_SelectionOptions_Dispose(ArkUI_SelectionOptions* options)
```

**描述**

Dispose selection options object.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| {ArkUI_SelectionOptions*} | options Pointer to the selection options object. to be disposed. |

### OH_ArkUI_SelectionOptions_SetMenuPolicy()

```c
void OH_ArkUI_SelectionOptions_SetMenuPolicy(ArkUI_SelectionOptions* options, ArkUI_MenuPolicy menuPolicy)
```

**描述**

Sets the menu policy for selection options.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| {ArkUI_SelectionOptions*} | options Pointer to the selection options. |
| {ArkUI_MenuPolicy} | menuPolicy The menu policy. |

### OH_ArkUI_SelectionOptions_GetMenuPolicy()

```c
ArkUI_MenuPolicy OH_ArkUI_SelectionOptions_GetMenuPolicy(ArkUI_SelectionOptions* options)
```

**描述**

Gets the menu policy of selection options.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| {ArkUI_SelectionOptions*} | options Pointer to the selection options object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_MenuPolicy](capi-native-type-h.md#arkui_menupolicy) | Returns the menu policy. |

### OH_ArkUI_MotionPathOptions_Create()

```c
ArkUI_MotionPathOptions* OH_ArkUI_MotionPathOptions_Create()
```

**描述**

Create an object of the motion path options for path animation.In the newly created ArkUI_MotionPathOptions, the "path" value is an empty string, the "from" value is 0,the "to" value is 1, and the "rotatable" value is false.

**起始版本：** 23

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_MotionPathOptions*](capi-arkui-nativemodule-arkui-motionpathoptions.md) | A pointer to the ArkUI_MotionPathOptions. |

### OH_ArkUI_MotionPathOptions_Dispose()

```c
void OH_ArkUI_MotionPathOptions_Dispose(ArkUI_MotionPathOptions* options)
```

**描述**

Dispose the ArkUI_MotionPathOptions object.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to the ArkUI_MotionPathOptions object to be disposed. |

### OH_ArkUI_MotionPathOptions_SetPath()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetPath(ArkUI_MotionPathOptions* options, const char* svgPath)
```

**描述**

Sets the the motion path for the animation using an SVG path string. The path supports using "start" and"end" as placeholders for the starting and ending points, for example:"Mstart.x start.y L50 50 Lend.x end.y Z". Refer to the SVG path format for the path string.When set to an empty string, it is equivalent to not setting a path animation.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to the ArkUI_MotionPathOptions object. |
| const char* svgPath | The motion path for the path animation. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_MotionPathOptions_GetPath()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetPath(const ArkUI_MotionPathOptions* options, char* svgPathBuffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

Gets the motion path string in the ArkUI_MotionPathOptions object.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to the ArkUI_MotionPathOptions object. |
| char* svgPathBuffer | Buffer pointer to the motion path string. |
| const int32_t bufferSize | The buffer size of the svgPathBuffer parameter. |
| int32_t* writeLength | Indicates the string length actually written to the bufferwhen returning [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode).Indicates the minimum buffer size that can accommodate the targetwhen [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) is returned. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the buffer size is less than the minimum buffer size. |

### OH_ArkUI_MotionPathOptions_SetFrom()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetFrom(ArkUI_MotionPathOptions* options, const float from)
```

**描述**

Sets the starting progress in the ArkUI_MotionPathOptions. Progress refers to the ratio of the length of thepath that has been traveled to the total length of the entire path. The value range is [0.0, 1.0], and the"from" value should be less than or equal to the "to" value; otherwise, an ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGEerror code will be returned.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to the ArkUI_MotionPathOptions object. |
| const float from | The starting progress in the ArkUI_MotionPathOptions. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs.<br>         Returns [ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) if the "from" value is out of range or the "from" value<br>                 is greater than the "to" value. |

### OH_ArkUI_MotionPathOptions_GetFrom()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetFrom(const ArkUI_MotionPathOptions* options, float* from)
```

**描述**

Gets the starting progress in the ArkUI_MotionPathOptions object.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to the ArkUI_MotionPathOptions object. |
| float* from | The starting progress in the ArkUI_MotionPathOptions. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_MotionPathOptions_SetTo()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetTo(ArkUI_MotionPathOptions* options, const float to)
```

**描述**

Sets the endpoint progress in the ArkUI_MotionPathOptions. Progress refers to the ratio of the length of thepath that has been traveled to the total length of the entire path. The value range is [0.0, 1.0], and the"from" value should be less than or equal to the "to" value; otherwise, an ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGEerror code will be returned.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to the ArkUI_MotionPathOptions object. |
| const float to | The endpoint progress in the ArkUI_MotionPathOptions. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs.<br>         Returns [ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) if the "to" value is out of range or the "to" value<br>                 is less than the "from" value. |

### OH_ArkUI_MotionPathOptions_GetTo()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetTo(const ArkUI_MotionPathOptions* options, float* to)
```

**描述**

Gets the endpoint progress in the ArkUI_MotionPathOptions object.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to the ArkUI_MotionPathOptions object. |
| float* to | The endpoint progress in the ArkUI_MotionPathOptions. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_MotionPathOptions_SetRotatable()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetRotatable(ArkUI_MotionPathOptions* options, const bool rotatable)
```

**描述**

Sets the rotatable parameter in the ArkUI_MotionPathOptions. It indicates whether to rotate along the path.True means rotating along the path, while false means not rotating along the path.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to the ArkUI_MotionPathOptions object. |
| const bool rotatable | The rotatable parameter in the ArkUI_MotionPathOptions. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_MotionPathOptions_GetRotatable()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetRotatable(const ArkUI_MotionPathOptions* options, bool* rotatable)
```

**描述**

Gets the rotatable parameter in the ArkUI_MotionPathOptions.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to the ArkUI_MotionPathOptions object. |
| bool* rotatable | The rotatable parameter in the ArkUI_MotionPathOptions. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_SelectedDragPreviewStyle_Create()

```c
ArkUI_SelectedDragPreviewStyle* OH_ArkUI_SelectedDragPreviewStyle_Create()
```

**描述**

Create a configuration object for selected drag preview style.

**起始版本：** 23

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_SelectedDragPreviewStyle*](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md) | A pointer to the configuration object. |

### OH_ArkUI_SelectedDragPreviewStyle_Dispose()

```c
void OH_ArkUI_SelectedDragPreviewStyle_Dispose(ArkUI_SelectedDragPreviewStyle* config)
```

**描述**

Dispose a configuration object for selected drag preview style.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)* config | Pointer to the configuration object to be disposed. |

### OH_ArkUI_SelectedDragPreviewStyle_SetColor()

```c
void OH_ArkUI_SelectedDragPreviewStyle_SetColor(ArkUI_SelectedDragPreviewStyle* config, uint32_t color)
```

**描述**

Sets the color of background for selected drag preview style.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)* config | Pointer to the configuration object to be modified. |
| uint32_t color | Background color. |

### OH_ArkUI_SelectedDragPreviewStyle_GetColor()

```c
uint32_t OH_ArkUI_SelectedDragPreviewStyle_GetColor(ArkUI_SelectedDragPreviewStyle* config)
```

**描述**

Gets the color of background for selected drag preview style.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)* config | Pointer to the configuration object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | Returns the background color. |

### OH_ArkUI_DecorationStyleOptions_SetTextDecorationType()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_SetTextDecorationType(OH_ArkUI_DecorationStyleOptions* options, ArkUI_TextDecorationType type)
```

**描述**

设置装饰线样式的装饰类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | 指向[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)对象的指针。 |
| [ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype) type | 装饰类型[ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_DecorationStyleOptions_GetTextDecorationType()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_GetTextDecorationType(OH_ArkUI_DecorationStyleOptions* options, ArkUI_TextDecorationType* type)
```

**描述**

获取装饰线样式的装饰类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | 指向[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)对象的指针。 |
| [ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype)* type | 装饰类型[ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_DecorationStyleOptions_SetColor()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_SetColor(OH_ArkUI_DecorationStyleOptions* options, uint32_t color)
```

**描述**

设置装饰线的颜色。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | 指向[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)对象的指针。 |
| uint32_t color | 装饰线的颜色，0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_DecorationStyleOptions_GetColor()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_GetColor(OH_ArkUI_DecorationStyleOptions* options, uint32_t* color)
```

**描述**

获取装饰线的颜色。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | 指向[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)对象的指针。 |
| uint32_t* color | 装饰线的颜色，0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_DecorationStyleOptions_SetTextDecorationStyle()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_SetTextDecorationStyle(OH_ArkUI_DecorationStyleOptions* options, ArkUI_TextDecorationStyle style)
```

**描述**

设置装饰线的样式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | 指向[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)对象的指针。 |
| [ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle) style | 装饰线的样式[ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_DecorationStyleOptions_GetTextDecorationStyle()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_GetTextDecorationStyle(OH_ArkUI_DecorationStyleOptions* options, ArkUI_TextDecorationStyle* style)
```

**描述**

获取装饰线的样式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | 指向[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)对象的指针。 |
| [ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle)* style | 装饰线的样式[ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_DecorationStyleOptions_SetThicknessScale()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_SetThicknessScale(OH_ArkUI_DecorationStyleOptions* options, float thicknessScale)
```

**描述**

设置装饰线的粗细缩放比例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | 指向[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)对象的指针。 |
| float thicknessScale | 装饰线的粗细缩放比例。取值范围为[0, +∞)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_DecorationStyleOptions_GetThicknessScale()

```c
ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_GetThicknessScale(OH_ArkUI_DecorationStyleOptions* options, float* thicknessScale)
```

**描述**

获取装饰线的粗细缩放比例。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | 指向[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)对象的指针。 |
| float* thicknessScale | 装饰线的粗细缩放比例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextDataDetectorConfig_SetTypes()

```c
ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_SetTypes(OH_ArkUI_TextDataDetectorConfig* config, const ArkUI_TextDataDetectorType* types, int32_t length)
```

**描述**

设置文本实体识别配置的类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)* config | 指向[OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)对象的指针。 |
| [const ArkUI_TextDataDetectorType](capi-text-h.md#arkui_textdatadetectortype)* types | 文本实体识别配置的类型，取值为[ArkUI_TextDataDetectorType](capi-text-h.md#arkui_textdatadetectortype)枚举。 |
| int32_t length | 类型的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextDataDetectorConfig_GetTypes()

```c
ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_GetTypes(OH_ArkUI_TextDataDetectorConfig* config, ArkUI_TextDataDetectorType* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取文本实体识别配置的类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)* config | 指向[OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)对象的指针。 |
| [ArkUI_TextDataDetectorType](capi-text-h.md#arkui_textdatadetectortype)* buffer | 指向类型数组的缓冲区指针。 |
| int32_t bufferSize | 开发者为类型预留的缓冲区最多可以写入的类型的数量。 |
| int32_t* writeLength | 实际写入缓冲区的类型的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若bufferSize小于writeLength，返回[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextDataDetectorConfig_RegisterOnDetectResultUpdateCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_RegisterOnDetectResultUpdateCallback(OH_ArkUI_TextDataDetectorConfig* config, void* userData, void (*callback)(const char* result, int32_t length, void* userData))
```

**描述**

设置文本实体识别结果更新回调。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)\* config | 指向[OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)对象的指针。 |
| void\* userData | 用户数据。 |
| void (\*callback)(const char\* result | detect result update callback. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextDataDetectorConfig_SetColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_SetColor(OH_ArkUI_TextDataDetectorConfig* config, uint32_t color)
```

**描述**

设置识别内容的颜色。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)* config | 指向[OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)对象的指针。 |
| uint32_t color | 识别内容的颜色，0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextDataDetectorConfig_GetColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_GetColor(OH_ArkUI_TextDataDetectorConfig* config, uint32_t* color)
```

**描述**

获取识别内容的颜色。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)* config | 指向[OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)对象的指针。 |
| uint32_t* color | 识别内容的颜色，0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextDataDetectorConfig_SetDecorationStyleOptions()

```c
ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_SetDecorationStyleOptions(OH_ArkUI_TextDataDetectorConfig* config, OH_ArkUI_DecorationStyleOptions* decoration)
```

**描述**

设置识别内容的装饰样式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)* config | 指向[OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)对象的指针。 |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* decoration | 识别内容的装饰样式，取值为[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextDataDetectorConfig_GetDecorationStyleOptions()

```c
ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_GetDecorationStyleOptions(OH_ArkUI_TextDataDetectorConfig* config, OH_ArkUI_DecorationStyleOptions* decoration)
```

**描述**

获取识别内容的装饰样式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)* config | 指向[OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)对象的指针。 |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* decoration | 识别内容的装饰样式，取值为[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextDataDetectorConfig_SetEnablePreviewMenu()

```c
ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_SetEnablePreviewMenu(OH_ArkUI_TextDataDetectorConfig* config, bool enablePreviewMenu)
```

**描述**

设置长按识别内容时是否显示预览菜单。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)* config | 指向[OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)对象的指针。 |
| bool enablePreviewMenu | 长按识别内容时是否显示预览菜单。true表示启用预览菜单，false表示不启用预览菜单。默认值为false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextDataDetectorConfig_GetEnablePreviewMenu()

```c
ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_GetEnablePreviewMenu(OH_ArkUI_TextDataDetectorConfig* config, bool* enablePreviewMenu)
```

**描述**

获取长按识别内容时是否显示预览菜单。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)* config | 指向[OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)对象的指针。 |
| bool* enablePreviewMenu | 长按识别内容时是否显示预览菜单。true表示显示预览菜单，false表示不显示预览菜单。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextController_SetStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_TextController_SetStyledString(OH_ArkUI_TextController* controller, ArkUI_StyledString_Descriptor* descriptor)
```

**描述**

Set the StyledString of the text.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md)* controller | the controller of the text. |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to an <b>ArkUI_StyledString_Descriptor</b> object, which will be set to Text. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_TextEditorPlaceholderOptions_Create()

```c
OH_ArkUI_TextEditorPlaceholderOptions* OH_ArkUI_TextEditorPlaceholderOptions_Create()
```

**描述**

创建一个无输入时的提示文本的选项对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorPlaceholderOptions_Destroy](capi-native-type-h.md#oh_arkui_texteditorplaceholderoptions_destroy)销毁。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions*](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md) | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |

### OH_ArkUI_TextEditorPlaceholderOptions_Destroy()

```c
void OH_ArkUI_TextEditorPlaceholderOptions_Destroy(OH_ArkUI_TextEditorPlaceholderOptions* options)
```

**描述**

销毁无输入时的提示文本的选项对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |

### OH_ArkUI_TextEditorPlaceholderOptions_SetValue()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetValue(OH_ArkUI_TextEditorPlaceholderOptions* options, const char* value)
```

**描述**

设置无输入时的提示文本选项的提示文字。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |
| const char* value | 提示文字。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorPlaceholderOptions_GetValue()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetValue(OH_ArkUI_TextEditorPlaceholderOptions* options, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取无输入时的提示文本选项的提示文字。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |
| char* buffer | 提示文字写入内存的缓冲区，内存空间需由开发者分配。 |
| int32_t bufferSize | 缓冲区最多可写入的字符的数量。 |
| int32_t* writeLength | 实际表示写入缓冲区的字符的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若节点、缓冲区或writeLength为空，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若bufferSize小于writeLength，返回[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorPlaceholderOptions_SetFontSize()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontSize(OH_ArkUI_TextEditorPlaceholderOptions* options, float fontSize)
```

**描述**

设置无输入时的提示文本选项的字体大小。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |
| float fontSize | 字体大小，单位为fp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorPlaceholderOptions_GetFontSize()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontSize(OH_ArkUI_TextEditorPlaceholderOptions* options, float* fontSize)
```

**描述**

获取无输入时的提示文本选项的字体大小。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |
| float* fontSize | 字体大小，单位为fp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorPlaceholderOptions_SetFontWeight()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontWeight(OH_ArkUI_TextEditorPlaceholderOptions* options, uint32_t fontWeight)
```

**描述**

设置无输入时的提示文本选项的字体粗细。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |
| uint32_t fontWeight | 字体粗细。取值范围为[100, 900]中的整百数值，例如100、900。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorPlaceholderOptions_GetFontWeight()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontWeight(OH_ArkUI_TextEditorPlaceholderOptions* options, uint32_t* fontWeight)
```

**描述**

获取无输入时的提示文本选项的字体粗细。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |
| uint32_t* fontWeight | 字体粗细。取值范围为[100, 900]中的整百数值，例如100、900。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorPlaceholderOptions_SetFontFamily()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontFamily(OH_ArkUI_TextEditorPlaceholderOptions* options, const char* fontFamily)
```

**描述**

设置无输入时的提示文本选项的字体家族。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |
| const char* fontFamily | 字体家族。存放待设置的字体名称，不同字体名称通过逗号拼接。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorPlaceholderOptions_GetFontFamily()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontFamily(OH_ArkUI_TextEditorPlaceholderOptions* options, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取无输入时的提示文本选项的字体家族。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |
| char* buffer | 字体家族写入内存的缓冲区，内存空间需由开发者分配。 |
| int32_t bufferSize | 缓冲区最多可写入的字符的数量。 |
| int32_t* writeLength | 实际写入缓冲区的字符的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若节点、缓冲区或writeLength为空，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若bufferSize小于writeLength，返回[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorPlaceholderOptions_SetFontStyle()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontStyle(OH_ArkUI_TextEditorPlaceholderOptions* options, ArkUI_FontStyle fontStyle)
```

**描述**

设置无输入时的提示文本选项的字体样式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |
| [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle) fontStyle | 字体样式。取值为[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorPlaceholderOptions_GetFontStyle()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontStyle(OH_ArkUI_TextEditorPlaceholderOptions* options, ArkUI_FontStyle* fontStyle)
```

**描述**

获取无输入时的提示文本选项的字体样式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |
| [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)* fontStyle | 字体样式。取值为[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorPlaceholderOptions_SetFontColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontColor(OH_ArkUI_TextEditorPlaceholderOptions* options, uint32_t fontColor)
```

**描述**

设置无输入时的提示文本选项的字体颜色。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |
| uint32_t fontColor | 字体颜色，0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorPlaceholderOptions_GetFontColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontColor(OH_ArkUI_TextEditorPlaceholderOptions* options, uint32_t* fontColor)
```

**描述**

获取无输入时的提示文本选项的字体颜色。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)* options | 指向[OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)对象的指针。 |
| uint32_t* fontColor | 字体颜色，0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_Create()

```c
OH_ArkUI_TextEditorStyledStringController* OH_ArkUI_TextEditorStyledStringController_Create()
```

**描述**

为文本编辑器创建一个属性字符串控制器对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorStyledStringController_Destroy](capi-native-type-h.md#oh_arkui_texteditorstyledstringcontroller_destroy)销毁。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController*](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md) | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |

### OH_ArkUI_TextEditorStyledStringController_Destroy()

```c
void OH_ArkUI_TextEditorStyledStringController_Destroy(OH_ArkUI_TextEditorStyledStringController* controller)
```

**描述**

销毁属性字符串控制器。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |

### OH_ArkUI_TextEditorStyledStringController_SetCaretOffset()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetCaretOffset(OH_ArkUI_TextEditorStyledStringController* controller, int32_t caretOffset)
```

**描述**

通过属性字符串控制器设置光标偏移量。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| int32_t caretOffset | 索引位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_GetCaretOffset()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetCaretOffset(OH_ArkUI_TextEditorStyledStringController* controller, int32_t* caretOffset)
```

**描述**

通过属性字符串控制器获取光标索引位置。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| int32_t* caretOffset | 索引位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_SetSelection()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetSelection(OH_ArkUI_TextEditorStyledStringController* controller, uint32_t start, uint32_t end, ArkUI_MenuPolicy menuPolicy)
```

**描述**

通过属性字符串控制器设置选中区域。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| uint32_t start | 选中区域的起始位置。 |
| uint32_t end | 选中区域的结束位置。 |
| [ArkUI_MenuPolicy](capi-native-type-h.md#arkui_menupolicy) menuPolicy | 选区内菜单弹出的策略。取值为[ArkUI_MenuPolicy](capi-native-type-h.md#arkui_menupolicy)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_IsEditing()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_IsEditing(OH_ArkUI_TextEditorStyledStringController* controller, bool* isEditing)
```

**描述**

通过属性字符串控制器获取文本编辑器的编辑状态。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| bool* isEditing | 编辑状态。true表示是编辑态，false表示不是编辑态。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_StopEditing()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_StopEditing(OH_ArkUI_TextEditorStyledStringController* controller)
```

**描述**

通过属性字符串控制器退出文本编辑器的编辑状态。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_GetPreviewText()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetPreviewText(OH_ArkUI_TextEditorStyledStringController* controller, uint32_t* offset, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

通过属性字符串控制器获取预上屏文本内容。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| uint32_t* offset | 预上屏文本位置。 |
| char* buffer | 预上屏文本内容写入内存的缓冲区，内存空间需由开发者分配。 |
| int32_t bufferSize | 缓冲区最多可写入的字符的数量。 |
| int32_t* writeLength | 实际写入缓冲区的字符的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_GetCaretRect()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetCaretRect(OH_ArkUI_TextEditorStyledStringController* controller, ArkUI_Rect* rect)
```

**描述**

通过属性字符串控制器获取光标矩形区域。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| [ArkUI_Rect](capi-arkui-nativemodule-arkui-rect.md)* rect | 光标区域信息。取值为[ArkUI_Rect](capi-arkui-nativemodule-arkui-rect.md)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_DeleteBackward()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_DeleteBackward(OH_ArkUI_TextEditorStyledStringController* controller)
```

**描述**

通过属性字符串控制器删除字符。没有内容被选中时，删除当前光标位置前的1个字符。有内容被选中时，删除选中内容。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_Create()

```c
OH_ArkUI_TextEditorParagraphStyle* OH_ArkUI_TextEditorParagraphStyle_Create()
```

**描述**

为文本编辑器创建一个段落样式对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorParagraphStyle_Destroy](capi-native-type-h.md#oh_arkui_texteditorparagraphstyle_destroy)销毁。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle*](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md) | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |

### OH_ArkUI_TextEditorParagraphStyle_Destroy()

```c
void OH_ArkUI_TextEditorParagraphStyle_Destroy(OH_ArkUI_TextEditorParagraphStyle* style)
```

**描述**

销毁段落样式对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |

### OH_ArkUI_TextEditorParagraphStyle_SetTextAlign()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetTextAlign(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextAlignment align)
```

**描述**

设置段落样式中的文本对齐方式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| [ArkUI_TextAlignment](capi-text-common-h.md#arkui_textalignment) align | 文本对齐方式。取值为[ArkUI_TextAlignment](capi-text-common-h.md#arkui_textalignment)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_GetTextAlign()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetTextAlign(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextAlignment* align)
```

**描述**

获取段落样式中的文本对齐方式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| [ArkUI_TextAlignment](capi-text-common-h.md#arkui_textalignment)* align | 文本对齐方式。取值为[ArkUI_TextAlignment](capi-text-common-h.md#arkui_textalignment)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_SetLeadingMarginPixelMap()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetLeadingMarginPixelMap(OH_ArkUI_TextEditorParagraphStyle* style, struct OH_PixelmapNative* pixelmap)
```

**描述**

设置段落样式中段落缩进的像素图。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| struct OH_PixelmapNative* pixelmap | 段落缩进的像素图。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_GetLeadingMarginPixelMap()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetLeadingMarginPixelMap(OH_ArkUI_TextEditorParagraphStyle* style, struct OH_PixelmapNative** pixelmap)
```

**描述**

获取段落样式中段落缩进的像素图。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| struct OH_PixelmapNative** pixelmap | 段落缩进的像素图。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_SetLeadingMarginWidth()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetLeadingMarginWidth(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t width)
```

**描述**

设置段落样式中段落缩进的宽度。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| uint32_t width | 段落缩进的宽度，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_GetLeadingMarginWidth()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetLeadingMarginWidth(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t* width)
```

**描述**

获取段落样式中段落缩进的宽度。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| uint32_t* width | 段落缩进的宽度，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_SetLeadingMarginHeight()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetLeadingMarginHeight(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t height)
```

**描述**

设置段落样式中段落缩进的高度。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| uint32_t height | 段落缩进的高度，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_GetLeadingMarginHeight()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetLeadingMarginHeight(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t* height)
```

**描述**

获取段落样式中段落缩进的高度。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| uint32_t* height | 段落缩进的高度，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_SetWordBreak()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetWordBreak(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_WordBreak wordBreak)
```

**描述**

设置段落样式的断字方式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak) wordBreak | 断字方式。取值为[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_GetWordBreak()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetWordBreak(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_WordBreak* wordBreak)
```

**描述**

获取段落样式的断字方式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)* wordBreak | 断字方式。取值为[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_SetLineBreakStrategy()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetLineBreakStrategy(OH_ArkUI_TextEditorParagraphStyle* style, OH_ArkUI_LineBreakStrategy lineBreakStrategy)
```

**描述**

设置段落样式的换行策略。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| [OH_ArkUI_LineBreakStrategy](capi-text-common-h.md#oh_arkui_linebreakstrategy) lineBreakStrategy | 换行策略。取值为[OH_ArkUI_LineBreakStrategy](capi-text-common-h.md#oh_arkui_linebreakstrategy)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_GetLineBreakStrategy()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetLineBreakStrategy(OH_ArkUI_TextEditorParagraphStyle* style, OH_ArkUI_LineBreakStrategy* lineBreakStrategy)
```

**描述**

获取段落样式的换行策略。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| [OH_ArkUI_LineBreakStrategy](capi-text-common-h.md#oh_arkui_linebreakstrategy)* lineBreakStrategy | 换行策略。取值为[OH_ArkUI_LineBreakStrategy](capi-text-common-h.md#oh_arkui_linebreakstrategy)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_SetParagraphSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetParagraphSpacing(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t paragraphSpacing)
```

**描述**

设置段落样式的段落间距。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| uint32_t paragraphSpacing | 段落间距，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_GetParagraphSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetParagraphSpacing(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t* paragraphSpacing)
```

**描述**

获取段落样式的段落间距。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| uint32_t* paragraphSpacing | 段落间距，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_SetTextVerticalAlign()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetTextVerticalAlign(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextVerticalAlignment verticalAlignment)
```

**描述**

设置段落样式的文本垂直对齐方式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| [ArkUI_TextVerticalAlignment](capi-text-common-h.md#arkui_textverticalalignment) verticalAlignment | 文本垂直对齐方式。取值为[ArkUI_TextVerticalAlignment](capi-text-common-h.md#arkui_textverticalalignment)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_GetTextVerticalAlign()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetTextVerticalAlign(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextVerticalAlignment* verticalAlignment)
```

**描述**

获取段落样式的文本垂直对齐方式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| [ArkUI_TextVerticalAlignment](capi-text-common-h.md#arkui_textverticalalignment)* verticalAlignment | 文本垂直对齐方式。取值为[ArkUI_TextVerticalAlignment](capi-text-common-h.md#arkui_textverticalalignment)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_SetTextDirection()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetTextDirection(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextDirection textDirection)
```

**描述**

设置段落样式的文本方向。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection) textDirection | 文本方向。取值为[ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorParagraphStyle_GetTextDirection()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetTextDirection(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextDirection* textDirection)
```

**描述**

获取段落样式的文本方向。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 指向[OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)对象的指针。 |
| [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection)* textDirection | 文本方向。取值为[ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_SetTypingParagraphStyle()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetTypingParagraphStyle(OH_ArkUI_TextEditorStyledStringController* controller, OH_ArkUI_TextEditorParagraphStyle* style)
```

**描述**

通过属性字符串控制器设置预设段落样式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)* style | 预设段落样式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_ShadowOptions_Create()

```c
OH_ArkUI_ShadowOptions* OH_ArkUI_ShadowOptions_Create()
```

**描述**

创建一个阴影选项对象。当该对象不再使用时，请调用[OH_ArkUI_ShadowOptions_Destroy](capi-native-type-h.md#oh_arkui_shadowoptions_destroy)销毁。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_ShadowOptions*](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |

### OH_ArkUI_ShadowOptions_Destroy()

```c
void OH_ArkUI_ShadowOptions_Destroy(OH_ArkUI_ShadowOptions* options)
```

**描述**

销毁阴影选项对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |

### OH_ArkUI_ShadowOptions_SetRadius()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetRadius(OH_ArkUI_ShadowOptions* options, float radius)
```

**描述**

设置阴影选项的模糊半径。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |
| float radius | 阴影的模糊半径，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_ShadowOptions_GetRadius()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetRadius(OH_ArkUI_ShadowOptions* options, float* radius)
```

**描述**

获取阴影选项的模糊半径。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |
| float* radius | 阴影的模糊半径，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_ShadowOptions_SetType()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetType(OH_ArkUI_ShadowOptions* options, ArkUI_ShadowType type)
```

**描述**

设置阴影选项的阴影类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |
| [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype) type | 阴影类型[ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_ShadowOptions_GetType()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetType(OH_ArkUI_ShadowOptions* options, ArkUI_ShadowType* type)
```

**描述**

获取阴影选项的阴影类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |
| [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype)* type | 阴影类型[ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_ShadowOptions_SetColor()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetColor(OH_ArkUI_ShadowOptions* options, uint32_t color)
```

**描述**

设置阴影选项的阴影颜色。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |
| uint32_t color | 阴影颜色，0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_ShadowOptions_GetColor()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetColor(OH_ArkUI_ShadowOptions* options, uint32_t* color)
```

**描述**

获取阴影选项的阴影颜色。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |
| uint32_t* color | 阴影颜色，0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_ShadowOptions_SetOffsetX()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetOffsetX(OH_ArkUI_ShadowOptions* options, float offsetX)
```

**描述**

设置阴影在x轴上的偏移量。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |
| float offsetX | 阴影在x轴上的偏移量，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_ShadowOptions_GetOffsetX()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetOffsetX(OH_ArkUI_ShadowOptions* options, float* offsetX)
```

**描述**

获取阴影在x轴上的偏移量。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |
| float* offsetX | 阴影在x轴上的偏移量，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_ShadowOptions_SetOffsetY()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetOffsetY(OH_ArkUI_ShadowOptions* options, float offsetY)
```

**描述**

设置阴影在y轴上的偏移量。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |
| float offsetY | 阴影在y轴上的偏移量，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_ShadowOptions_GetOffsetY()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetOffsetY(OH_ArkUI_ShadowOptions* options, float* offsetY)
```

**描述**

获取阴影在y轴上的偏移量。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |
| float* offsetY | 阴影在y轴上的偏移量，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_ShadowOptions_SetFill()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetFill(OH_ArkUI_ShadowOptions* options, bool isFill)
```

**描述**

设置是否用阴影填充组件内部。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |
| bool isFill | 是否用阴影填充组件内部。true表示用阴影填充组件内部，false表示不用阴影填充组件内部。默认值为false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_ShadowOptions_GetFill()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetFill(OH_ArkUI_ShadowOptions* options, bool* isFill)
```

**描述**

获取是否用阴影填充组件内部。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | 指向[OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)对象的指针。 |
| bool* isFill | 是否用阴影填充组件内部。true表示用阴影填充组件内部，false表示不用阴影填充组件内部。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_Create()

```c
OH_ArkUI_TextEditorTextStyle* OH_ArkUI_TextEditorTextStyle_Create()
```

**描述**

创建一个文本样式对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorTextStyle_Destroy](capi-native-type-h.md#oh_arkui_texteditortextstyle_destroy)销毁。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle*](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md) | 指向[OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)对象的指针。 |

### OH_ArkUI_TextEditorTextStyle_Destroy()

```c
void OH_ArkUI_TextEditorTextStyle_Destroy(OH_ArkUI_TextEditorTextStyle* style)
```

**描述**

销毁文本样式对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | 指向[OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)对象的指针。 |

### OH_ArkUI_TextEditorTextStyle_SetFontColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontColor(OH_ArkUI_TextEditorTextStyle* style, uint32_t color)
```

**描述**

设置文本样式的字体颜色。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| uint32_t color | 字体颜色，0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetFontColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontColor(OH_ArkUI_TextEditorTextStyle* style, uint32_t* color)
```

**描述**

获取文本样式的字体颜色。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| uint32_t* color | 字体颜色，0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_SetFontSize()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontSize(OH_ArkUI_TextEditorTextStyle* style, float size)
```

**描述**

设置文本样式的字体大小。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| float size | 字体大小，单位为fp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetFontSize()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontSize(OH_ArkUI_TextEditorTextStyle* style, float* size)
```

**描述**

获取文本样式的字体大小。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| float* size | 字体大小，单位为fp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_SetFontStyle()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontStyle(OH_ArkUI_TextEditorTextStyle* style, ArkUI_FontStyle fontStyle)
```

**描述**

设置文本样式的字体样式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle) fontStyle | 字体样式。取值为[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetFontStyle()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontStyle(OH_ArkUI_TextEditorTextStyle* style, ArkUI_FontStyle* fontStyle)
```

**描述**

获取文本样式的字体样式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)* fontStyle | 字体样式。取值为[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_SetFontWeight()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontWeight(OH_ArkUI_TextEditorTextStyle* style, uint32_t fontWeight)
```

**描述**

设置文本样式的字体粗细。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| uint32_t fontWeight | 字体粗细。取值范围为[100, 900]中的整百数值，例如100、900。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetFontWeight()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontWeight(OH_ArkUI_TextEditorTextStyle* style, uint32_t* fontWeight)
```

**描述**

获取文本样式的字体粗细。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| uint32_t* fontWeight | 字体粗细。取值范围为[100, 900]中的整百数值，例如100、900。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_SetFontFamily()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontFamily(OH_ArkUI_TextEditorTextStyle* style, const char* fontFamily)
```

**描述**

设置文本样式的字体家族。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| const char* fontFamily | 字体家族。存放待设置的字体名称，不同字体名称通过逗号拼接。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetFontFamily()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontFamily(OH_ArkUI_TextEditorTextStyle* style, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取文本样式的字体家族。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| char* buffer | 字体家族内容写入内存的缓冲区，内存空间需由开发者分配。 |
| int32_t bufferSize | 缓冲区最多可写入的字符的数量。 |
| int32_t* writeLength | 实际写入缓冲区的字符的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_SetDecoration()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetDecoration(OH_ArkUI_TextEditorTextStyle* style, OH_ArkUI_DecorationStyleOptions* options)
```

**描述**

设置文本样式的文本装饰选项。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | 指向[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetDecoration()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetDecoration(OH_ArkUI_TextEditorTextStyle* style, OH_ArkUI_DecorationStyleOptions* options)
```

**描述**

获取文本样式的文本装饰选项。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | 指向[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_SetTextShadows()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetTextShadows(OH_ArkUI_TextEditorTextStyle* style, const OH_ArkUI_ShadowOptions** options, int32_t length)
```

**描述**

设置文本样式的文本阴影选项。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| [const OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)** options | 文本阴影选项。 |
| int32_t length | 文本阴影选项的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetTextShadows()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetTextShadows(OH_ArkUI_TextEditorTextStyle* style, OH_ArkUI_ShadowOptions** shadowOptions, uint32_t shadowOptionsSize, uint32_t* writeLength)
```

**描述**

获取文本样式的文本阴影选项。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)** shadowOptions | 文本阴影选项。 |
| uint32_t shadowOptionsSize | 阴影选项的缓冲区大小。 |
| uint32_t* writeLength | 文本样式中实际的文本阴影选项数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_SetLineHeight()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetLineHeight(OH_ArkUI_TextEditorTextStyle* style, int32_t lineHeight)
```

**描述**

设置文本样式的文本行高。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| int32_t lineHeight | 文本行高。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetLineHeight()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetLineHeight(OH_ArkUI_TextEditorTextStyle* style, int32_t* lineHeight)
```

**描述**

获取文本样式的文本行高。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| int32_t* lineHeight | 文本行高。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_SetLetterSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetLetterSpacing(OH_ArkUI_TextEditorTextStyle* style, int32_t letterSpacing)
```

**描述**

设置文本样式的字符间距。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| int32_t letterSpacing | 字符间距。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetLetterSpacing()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetLetterSpacing(OH_ArkUI_TextEditorTextStyle* style, int32_t* letterSpacing)
```

**描述**

获取文本样式的字符间距。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| int32_t* letterSpacing | 字符间距。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_SetFontFeature()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontFeature(OH_ArkUI_TextEditorTextStyle* style, const char* fontFeature)
```

**描述**

设置文本样式的文字特性效果，比如数字等宽的特性。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| const char* fontFeature | 字体特性。存放待设置的字体特性，多个特性通过逗号拼接。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetFontFeature()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontFeature(OH_ArkUI_TextEditorTextStyle* style, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取文本样式的文字特性效果，比如数字等宽的特性。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| char* buffer | 字体特性内容写入内存的缓冲区，内存空间需由开发者分配。 |
| int32_t bufferSize | 缓冲区最多可写入的字符的数量。 |
| int32_t* writeLength | 实际表示写入缓冲区的字符的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_SetHalfLeading()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetHalfLeading(OH_ArkUI_TextEditorTextStyle* style, bool halfLeading)
```

**描述**

设置文本样式中文本是否将行间距平分至行的顶部与底部。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| bool halfLeading | 文本是否将行间距平分至行的顶部与底部。<br>true表示将行间距平分至行的顶部与底部，false表示不将行间距平分至行的顶部与底部。默认值为false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetHalfLeading()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetHalfLeading(OH_ArkUI_TextEditorTextStyle* style, bool* halfLeading)
```

**描述**

获取文本样式中文本是否将行间距平分至行的顶部与底部。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| bool* halfLeading | 文本是否将行间距平分至行的顶部与底部。<br>true表示将行间距平分至行的顶部与底部，false表示不将行间距平分至行的顶部与底部。默认值为false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_SetTextBackgroundColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetTextBackgroundColor(OH_ArkUI_TextEditorTextStyle* style, uint32_t color)
```

**描述**

设置文本样式中的文本背景颜色。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| uint32_t color | 文本背景颜色，0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetTextBackgroundColor()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetTextBackgroundColor(OH_ArkUI_TextEditorTextStyle* style, uint32_t* color)
```

**描述**

获取文本样式中的文本背景颜色。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| uint32_t* color | 文本背景颜色，0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_SetTextBackgroundRadius()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetTextBackgroundRadius(OH_ArkUI_TextEditorTextStyle* style, float topLeft, float topRight, float bottomLeft, float bottomRight)
```

**描述**

设置文本样式中文本背景的圆角半径。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| float topLeft | 文本背景左上角的圆角半径。单位为vp。 |
| float topRight | 文本背景右上角的圆角半径。单位为vp。 |
| float bottomLeft | 文本背景左下角的圆角半径。单位为vp。 |
| float bottomRight | 文本背景右下角的圆角半径。单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorTextStyle_GetTextBackgroundRadius()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetTextBackgroundRadius(OH_ArkUI_TextEditorTextStyle* style, float* topLeft, float* topRight, float* bottomLeft, float* bottomRight)
```

**描述**

获取文本样式中文本背景的圆角半径。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | TextEditor组件文本样式。 |
| float* topLeft | 文本背景左上角的圆角半径。单位为vp。 |
| float* topRight | 文本背景右上角的圆角半径。单位为vp。 |
| float* bottomLeft | 文本背景左下角的圆角半径。单位为vp。 |
| float* bottomRight | 文本背景右下角的圆角半径。单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_SetTypingStyle()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetTypingStyle(OH_ArkUI_TextEditorStyledStringController* controller, OH_ArkUI_TextEditorTextStyle* style)
```

**描述**

通过属性字符串控制器设置预设输入样式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | 预设输入样式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_GetTypingStyle()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetTypingStyle(OH_ArkUI_TextEditorStyledStringController* controller, OH_ArkUI_TextEditorTextStyle* style)
```

**描述**

通过属性字符串控制器获取预设输入样式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)* style | 预设输入样式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_Create()

```c
OH_ArkUI_TextEditorSelectionMenuOptions* OH_ArkUI_TextEditorSelectionMenuOptions_Create()
```

**描述**

创建一个文本编辑器文本选择菜单选项对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorSelectionMenuOptions_Destroy](capi-native-type-h.md#oh_arkui_texteditorselectionmenuoptions_destroy)销毁。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions*](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md) | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_Destroy()

```c
void OH_ArkUI_TextEditorSelectionMenuOptions_Destroy(OH_ArkUI_TextEditorSelectionMenuOptions* options)
```

**描述**

销毁文本编辑器文本选择菜单选项对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_SetSpanType()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetSpanType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextEditorSpanType textEditorSpanType)
```

**描述**

设置文本编辑器中文本选择菜单的span的类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| [OH_ArkUI_TextEditorSpanType](capi-native-type-h.md#oh_arkui_texteditorspantype) textEditorSpanType | span的类型。取值为[OH_ArkUI_TextEditorSpanType](capi-native-type-h.md#oh_arkui_texteditorspantype)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_GetSpanType()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetSpanType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextEditorSpanType* textEditorSpanType)
```

**描述**

获取文本编辑器中文本选择菜单的span的类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| [OH_ArkUI_TextEditorSpanType](capi-native-type-h.md#oh_arkui_texteditorspantype)* textEditorSpanType | span的类型。取值为[OH_ArkUI_TextEditorSpanType](capi-native-type-h.md#oh_arkui_texteditorspantype)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_SetContentNode()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetContentNode(OH_ArkUI_TextEditorSelectionMenuOptions* options, ArkUI_NodeHandle node)
```

**描述**

设置文本编辑器中文本选择菜单的内容节点。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 内容节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_GetContentNode()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetContentNode(OH_ArkUI_TextEditorSelectionMenuOptions* options, ArkUI_NodeHandle* node)
```

**描述**

获取文本编辑器中文本选择菜单的内容节点。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* node | 内容节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_SetResponseType()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetResponseType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextEditorResponseType responseType)
```

**描述**

设置文本编辑器中文本选择菜单的响应类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| [OH_ArkUI_TextEditorResponseType](capi-native-type-h.md#oh_arkui_texteditorresponsetype) responseType | 响应类型。取值为[OH_ArkUI_TextEditorResponseType](capi-native-type-h.md#oh_arkui_texteditorresponsetype)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_GetResponseType()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetResponseType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextEditorResponseType* responseType)
```

**描述**

获取文本编辑器中文本选择菜单的响应类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| [OH_ArkUI_TextEditorResponseType](capi-native-type-h.md#oh_arkui_texteditorresponsetype)* responseType | 响应类型。取值为[OH_ArkUI_TextEditorResponseType](capi-native-type-h.md#oh_arkui_texteditorresponsetype)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_SetMenuType()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetMenuType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextMenuType menuType)
```

**描述**

设置文本编辑器中文本选择菜单的类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| [OH_ArkUI_TextMenuType](capi-native-type-h.md#oh_arkui_textmenutype) menuType | 菜单类型。取值为[OH_ArkUI_TextMenuType](capi-native-type-h.md#oh_arkui_textmenutype)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_GetMenuType()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetMenuType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextMenuType* menuType)
```

**描述**

获取文本编辑器中文本选择菜单的类型。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| [OH_ArkUI_TextMenuType](capi-native-type-h.md#oh_arkui_textmenutype)* menuType | 菜单类型。取值为[OH_ArkUI_TextMenuType](capi-native-type-h.md#oh_arkui_textmenutype)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuShowCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuShowCallback(OH_ArkUI_TextEditorSelectionMenuOptions* options, void* userData, void (*callback)(int32_t start, int32_t end, void* callbackUserData))
```

**描述**

设置文本选择菜单显示时触发的事件。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)\* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| void\* userData | 用户数据。 |
| void (\*callback)(int32_t start | 菜单显示时的回调函数。start 选中内容的起始偏移量。end 选中内容的结束偏移量。callbackUserData 用户数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuHideCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuHideCallback(OH_ArkUI_TextEditorSelectionMenuOptions* options, void* userData, void (*callback)(int32_t start, int32_t end, void* callbackUserData))
```

**描述**

设置文本选择菜单隐藏时触发的事件。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)\* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| void\* userData | 用户数据。 |
| void (\*callback)(int32_t start | 菜单隐藏时的回调函数。start 选中内容的起始偏移量。end 选中内容的结束偏移量。userData 用户数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuAppearCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuAppearCallback(OH_ArkUI_TextEditorSelectionMenuOptions* options, void* userData, void (*callback)(int32_t start, int32_t end, void* callbackUserData))
```

**描述**

设置文本选择菜单出现时触发的事件。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)\* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| void\* userData | 用户数据。 |
| void (\*callback)(int32_t start | 菜单出现时的回调函数。start 选中内容的起始偏移量。end 选中内容的结束偏移量。userData 用户数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuDisappearCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuDisappearCallback(OH_ArkUI_TextEditorSelectionMenuOptions* options, void* userData, void (*callback)(void* callbackUserData))
```

**描述**

设置文本选择菜单消失时触发的事件。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)\* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| void\* userData | 用户数据。 |
| void (\*callback)(void\* callbackUserData) | 菜单消失时的回调函数。userData 用户数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_SetHapticFeedbackMode()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetHapticFeedbackMode(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_HapticFeedbackMode mode)
```

**描述**

设置文本编辑器中文本选择菜单的触觉反馈模式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| [OH_ArkUI_HapticFeedbackMode](capi-native-type-h.md#oh_arkui_hapticfeedbackmode) mode | 触觉反馈模式。取值为[OH_ArkUI_HapticFeedbackMode](capi-native-type-h.md#oh_arkui_hapticfeedbackmode)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorSelectionMenuOptions_GetHapticFeedbackMode()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetHapticFeedbackMode(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_HapticFeedbackMode* mode)
```

**描述**

获取文本编辑器中文本选择菜单的触觉反馈模式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)* options | 指向[OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)对象的指针。 |
| [OH_ArkUI_HapticFeedbackMode](capi-native-type-h.md#oh_arkui_hapticfeedbackmode)* mode | 触觉反馈模式。取值为[OH_ArkUI_HapticFeedbackMode](capi-native-type-h.md#oh_arkui_hapticfeedbackmode)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_CloseSelectionMenu()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_CloseSelectionMenu(OH_ArkUI_TextEditorStyledStringController* controller)
```

**描述**

关闭文本编辑器属性字符串控制器的文本选择菜单。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_GetSelection()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetSelection(const OH_ArkUI_TextEditorStyledStringController* controller, uint32_t* start, uint32_t* end)
```

**描述**

通过属性字符串控制器获取选中区域。

>**说明：** 
>所有输入指针参数必须由调用者分配、管理和释放。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| uint32_t* start | 选中区域的起始位置。 |
| uint32_t* end | 选中区域的结束位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_SetStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetStyledString(const OH_ArkUI_TextEditorStyledStringController* controller, const ArkUI_StyledString_Descriptor* descriptor)
```

**描述**

通过属性字符串控制器设置显示的属性字符串。

>**说明：** 
>所有输入指针参数必须由调用者分配、管理和释放。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| [const ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | 指向[ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_GetStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetStyledString(const OH_ArkUI_TextEditorStyledStringController* controller, ArkUI_StyledString_Descriptor* descriptor)
```

**描述**

通过属性字符串控制器获取显示的属性字符串。

>**说明：** 
>所有输入指针参数必须由调用者分配、管理和释放。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | 指向[ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_SetStyledPlaceholder()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetStyledPlaceholder(const OH_ArkUI_TextEditorStyledStringController* controller, const ArkUI_StyledString_Descriptor* descriptor)
```

**描述**

通过属性字符串控制器设置属性字符串样式的提示文本。

>**说明：** 
>所有输入指针参数必须由调用者分配、管理和释放。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| [const ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | 指向[ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>     <br>若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>     <br>若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_PickerIndicatorStyle_Create()

```c
ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)
```

**描述**

Create the ArkUI_PickerIndicatorStyle instance.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PickerIndicatorType](capi-native-type-h.md#arkui_pickerindicatortype) type | The picker selection indicator enumeration type. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_PickerIndicatorStyle*](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) | ArkUI_PickerIndicatorStyle instance. If the instance returns a null pointer,<br>         it indicates creation failure, and the reason for the failure may be that the address space is full or<br>         the type not supported. |

### OH_ArkUI_PickerIndicatorStyle_Dispose()

```c
void OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)
```

**描述**

Destroy the ArkUI_PickerIndicatorStyle instance.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | The ArkUI_PickerIndicatorStyle instance to be destroyed. |

### OH_ArkUI_PickerIndicatorStyle_ConfigureBackground()

```c
ArkUI_ErrorCode OH_ArkUI_PickerIndicatorStyle_ConfigureBackground(ArkUI_PickerIndicatorStyle* style, ArkUI_PickerIndicatorBackground* background)
```

**描述**

Set the parameters of background style.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | The ArkUI_PickerIndicatorStyle instance. |
| [ArkUI_PickerIndicatorBackground](capi-arkui-nativemodule-arkui-pickerindicatorbackground.md)* background | The parameters of background style. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if success.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) The parameters set need to be consistent with<br>        the type of the created instance. If they are not consistent, this error code will be returned.<br>        This interface only takes effect when the type is "background". |

### OH_ArkUI_PickerIndicatorStyle_ConfigureDivider()

```c
ArkUI_ErrorCode OH_ArkUI_PickerIndicatorStyle_ConfigureDivider(ArkUI_PickerIndicatorStyle* style, ArkUI_PickerIndicatorDivider* divider)
```

**描述**

Set the parameters of divider style.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | The ArkUI_PickerIndicatorStyle instance. |
| [ArkUI_PickerIndicatorDivider](capi-arkui-nativemodule-arkui-pickerindicatordivider.md)* divider | The parameters of divider style. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if success.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) The parameters set need to be consistent with<br>        the type of the created instance. If they are not consistent, this error code will be returned.<br>        This interface only takes effect when the type is "divider". |

### OH_ArkUI_Matrix4ScaleOptions_Create()

```c
ArkUI_Matrix4ScaleOptions* OH_ArkUI_Matrix4ScaleOptions_Create()
```

**描述**

Create an object of ArkUI_Matrix4ScaleOptions.In the newly created options, the default values for the scaling coefficients in the x, y and z directionsare 1, and the default values for centerX, centerY are 0.

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions*](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md) | Returns a pointer to the newly created ArkUI_Matrix4ScaleOptions. |

### OH_ArkUI_Matrix4ScaleOptions_Dispose()

```c
void OH_ArkUI_Matrix4ScaleOptions_Dispose(ArkUI_Matrix4ScaleOptions* options)
```

**描述**

Disposes the ArkUI_Matrix4ScaleOptions object.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the ArkUI_Matrix4ScaleOptions instance to be destroyed. |

### OH_ArkUI_Matrix4ScaleOptions_SetX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetX(ArkUI_Matrix4ScaleOptions* options, const float scaleX)
```

**描述**

Set the scaling factor in the x direction in ArkUI_Matrix4ScaleOptions.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the ArkUI_Matrix4ScaleOptions object. |
| const float scaleX | The scaling factor in the x direction. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful. <br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4ScaleOptions_GetX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetX(const ArkUI_Matrix4ScaleOptions* options, float* scaleX)
```

**描述**

Get the scaling factor in the x direction in ArkUI_Matrix4ScaleOptions.If the value of x is never set, its default value is 1.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the ArkUI_Matrix4ScaleOptions object. |
| float* scaleX | The scaling factor in the x direction. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4ScaleOptions_SetY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetY(ArkUI_Matrix4ScaleOptions* options, const float scaleY)
```

**描述**

Set the scaling factor in the y direction in ArkUI_Matrix4ScaleOptions.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the ArkUI_Matrix4ScaleOptions object. |
| const float scaleY | The scaling factor in the y direction. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4ScaleOptions_GetY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetY(const ArkUI_Matrix4ScaleOptions* options, float* scaleY)
```

**描述**

Get the scaling factor in the y direction in ArkUI_Matrix4ScaleOptions.If the value of y is never set, its default value is 1.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the ArkUI_Matrix4ScaleOptions object. |
| float* scaleY | The scaling factor in the y direction. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4ScaleOptions_SetZ()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetZ(ArkUI_Matrix4ScaleOptions* options, const float scaleZ)
```

**描述**

Set the scaling factor in the z direction in ArkUI_Matrix4ScaleOptions.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the ArkUI_Matrix4ScaleOptions object. |
| const float scaleZ | The scaling factor in the z direction. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4ScaleOptions_GetZ()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetZ(const ArkUI_Matrix4ScaleOptions* options, float* scaleZ)
```

**描述**

Get the scaling factor in the z direction in ArkUI_Matrix4ScaleOptions.If the value of z is never set, its default value is 1.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the ArkUI_Matrix4ScaleOptions object. |
| float* scaleZ | The scaling factor in the z direction. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4ScaleOptions_SetCenterX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetCenterX(ArkUI_Matrix4ScaleOptions* options, const float centerX)
```

**描述**

Set x offset relative to the transformation center. 0 means no additional x-direction offset from thetransformation center. The unit is px.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the ArkUI_Matrix4ScaleOptions object. |
| const float centerX | The x offset relative to the transformation center. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4ScaleOptions_GetCenterX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetCenterX(const ArkUI_Matrix4ScaleOptions* options, float* centerX)
```

**描述**

Get the value of centerX from the options, which represents the x-direction offset relative to thetransformation center. The unit is px. If the value of centerX is never set, its default value is 0.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the ArkUI_Matrix4ScaleOptions object. |
| float* centerX | The x-direction offset relative to the transformation center. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4ScaleOptions_SetCenterY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetCenterY(ArkUI_Matrix4ScaleOptions* options, const float centerY)
```

**描述**

Set y offset relative to the transformation center. 0 means no additional y-direction offset from thetransformation center. The unit is px.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the ArkUI_Matrix4ScaleOptions object. |
| const float centerY | The y offset relative to the transformation center. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4ScaleOptions_GetCenterY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetCenterY(const ArkUI_Matrix4ScaleOptions* options, float* centerY)
```

**描述**

Get the value of centerY from the options, which represents the y-direction offset relative to thetransformation center. The unit is px. If the value of centerY is never set, its default value is 0.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the ArkUI_Matrix4ScaleOptions object. |
| float* centerY | The y-direction offset relative to the transformation center. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4RotationOptions_Create()

```c
ArkUI_Matrix4RotationOptions* OH_ArkUI_Matrix4RotationOptions_Create()
```

**描述**

Create an object of ArkUI_Matrix4RotationOptions.In the newly created options, the x, y, and z values in the direction vector specifying the rotation axisare undetermined; The default values for centerX, centerY are 0; The default value for angle is 0.If none of x, y, z are specified, it is equivalent to x=0, y=0, z=1, which means rotation around the z-axis.Once any one of x, y, z is specified, the remaining unspecified values are equivalent to 0.

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_Matrix4RotationOptions*](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md) | Returns a pointer to the newly created ArkUI_Matrix4RotationOptions. |

### OH_ArkUI_Matrix4RotationOptions_Dispose()

```c
void OH_ArkUI_Matrix4RotationOptions_Dispose(ArkUI_Matrix4RotationOptions* options)
```

**描述**

Disposes the ArkUI_Matrix4RotationOptions object.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions instance to be destroyed. |

### OH_ArkUI_Matrix4RotationOptions_SetX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetX(ArkUI_Matrix4RotationOptions* options, const float x)
```

**描述**

Set the value of the direction vector for the x-axis direction in ArkUI_Matrix4RotationOptions.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions object. |
| const float x | The value of the direction vector for the x-axis direction. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4RotationOptions_GetX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetX(const ArkUI_Matrix4RotationOptions* options, float* x)
```

**描述**

Get the value of the direction vector for the x-axis direction in ArkUI_Matrix4RotationOptions.If the value of x is never set, its value will be undefined, so the function will returnARKUI_ERROR_CODE_PARAM_INVALID.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions object. |
| float* x | The value of the direction vector for the x-axis direction. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4RotationOptions_SetY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetY(ArkUI_Matrix4RotationOptions* options, const float y)
```

**描述**

Set the value of the direction vector for the y-axis direction in ArkUI_Matrix4RotationOptions.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions object. |
| const float y | The value of the direction vector for the y-axis direction. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4RotationOptions_GetY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetY(const ArkUI_Matrix4RotationOptions* options, float* y)
```

**描述**

Get the value of the direction vector for the y-axis direction in ArkUI_Matrix4RotationOptions.If the value of y is never set, its value will be undefined, so the function will returnARKUI_ERROR_CODE_PARAM_INVALID.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions object. |
| float* y | The value of the direction vector for the y-axis direction. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4RotationOptions_SetZ()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetZ(ArkUI_Matrix4RotationOptions* options, const float z)
```

**描述**

Set the value of the direction vector for the z-axis direction in ArkUI_Matrix4RotationOptions.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions object. |
| const float z | The value of the direction vector for the z-axis direction. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4RotationOptions_GetZ()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetZ(const ArkUI_Matrix4RotationOptions* options, float* z)
```

**描述**

Get the value of the direction vector for the z-axis direction in ArkUI_Matrix4RotationOptions.If the value of z is never set, its value will be undefined, so the function will returnARKUI_ERROR_CODE_PARAM_INVALID.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions object. |
| float* z | The value of the direction vector for the z-axis direction. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4RotationOptions_SetAngle()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetAngle(ArkUI_Matrix4RotationOptions* options, const float angle)
```

**描述**

Set the value of the rotation angle in ArkUI_Matrix4RotationOptions. The unit is degree.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions object. |
| const float angle | The value of the rotation angle in ArkUI_Matrix4RotationOptions. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4RotationOptions_GetAngle()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetAngle(const ArkUI_Matrix4RotationOptions* options, float* angle)
```

**描述**

Get the value of the rotation angle in ArkUI_Matrix4RotationOptions. The unit is degree.If the value of angle is never set, its default value is 0.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions object. |
| float* angle | The value of the rotation angle in ArkUI_Matrix4RotationOptions. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4RotationOptions_SetCenterX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetCenterX(ArkUI_Matrix4RotationOptions* options, const float centerX)
```

**描述**

Set x offset relative to the transformation center. 0 means no additional x-direction offset from thetransformation center. The unit is px.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions object. |
| const float centerX | The x offset relative to the transformation center. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4RotationOptions_GetCenterX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetCenterX(const ArkUI_Matrix4RotationOptions* options, float* centerX)
```

**描述**

Get the value of centerX from the options, which represents the x-direction offset relative to thetransformation center. The unit is px. If the value of centerX is never set, its default value is 0.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions object. |
| float* centerX | The x-direction offset relative to the transformation center. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4RotationOptions_SetCenterY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetCenterY(ArkUI_Matrix4RotationOptions* options, const float centerY)
```

**描述**

Set y offset relative to the transformation center. 0 means no additional y-direction offset from thetransformation center. The unit is px.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions object. |
| const float centerY | The y offset relative to the transformation center. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4RotationOptions_GetCenterY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetCenterY(const ArkUI_Matrix4RotationOptions* options, float* centerY)
```

**描述**

Get the value of centerY from the options, which represents the y-direction offset relative to thetransformation center. The unit is px. If the value of centerY is never set, its default value is 0.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the ArkUI_Matrix4RotationOptions object. |
| float* centerY | The y-direction offset relative to the transformation center. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4TranslationOptions_Create()

```c
ArkUI_Matrix4TranslationOptions* OH_ArkUI_Matrix4TranslationOptions_Create()
```

**描述**

Create an object of ArkUI_Matrix4TranslationOptions.In the newly created options, the default values for x, y and z are 0.

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_Matrix4TranslationOptions*](capi-arkui-nativemodule-arkui-matrix4translationoptions.md) | Returns a pointer to the newly created ArkUI_Matrix4TranslationOptions. |

### OH_ArkUI_Matrix4TranslationOptions_Dispose()

```c
void OH_ArkUI_Matrix4TranslationOptions_Dispose(ArkUI_Matrix4TranslationOptions* options)
```

**描述**

Disposes the ArkUI_Matrix4TranslationOptions object.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the ArkUI_Matrix4TranslationOptions instance to be destroyed. |

### OH_ArkUI_Matrix4TranslationOptions_SetX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_SetX(ArkUI_Matrix4TranslationOptions* options, const float x)
```

**描述**

Set the translation value in the x-axis direction. The unit is px.If the value of x is never set, its default value is 0.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the ArkUI_Matrix4TranslationOptions object. |
| const float x | The translation value in the x-axis direction. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4TranslationOptions_GetX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_GetX(const ArkUI_Matrix4TranslationOptions* options, float* x)
```

**描述**

Get the translation value in the x-axis direction from ArkUI_Matrix4TranslationOptions.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the ArkUI_Matrix4TranslationOptions object. |
| float* x | The translation value in the x-axis direction. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4TranslationOptions_SetY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_SetY(ArkUI_Matrix4TranslationOptions* options, const float y)
```

**描述**

Set the translation value in the y-axis direction. The unit is px.If the value of y is never set, its default value is 0.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the ArkUI_Matrix4TranslationOptions object. |
| const float y | The translation value in the y-axis direction. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4TranslationOptions_GetY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_GetY(const ArkUI_Matrix4TranslationOptions* options, float* y)
```

**描述**

Get the translation value in the y-axis direction from ArkUI_Matrix4TranslationOptions.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the ArkUI_Matrix4TranslationOptions object. |
| float* y | The translation value in the y-axis direction. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4TranslationOptions_SetZ()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_SetZ(ArkUI_Matrix4TranslationOptions* options, const float z)
```

**描述**

Set the translation value in the z-axis direction. The unit is px.If the value of z is never set, its default value is 0.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the ArkUI_Matrix4TranslationOptions object. |
| const float z | The translation value in the z-axis direction. Value range: (-∞, +∞). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4TranslationOptions_GetZ()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_GetZ(const ArkUI_Matrix4TranslationOptions* options, float* z)
```

**描述**

Get the translation value in the z-axis direction from ArkUI_Matrix4TranslationOptions.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the ArkUI_Matrix4TranslationOptions object. |
| float* z | The translation value in the z-axis direction. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4_CreateIdentity()

```c
ArkUI_Matrix4* OH_ArkUI_Matrix4_CreateIdentity()
```

**描述**

Create an identity matrix4 object.

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_Matrix4*](capi-arkui-nativemodule-arkui-matrix4.md) | Returns the created identity matrix4 object. |

### OH_ArkUI_Matrix4_CreateByElements()

```c
ArkUI_Matrix4* OH_ArkUI_Matrix4_CreateByElements(const float* elements)
```

**描述**

Specify each element of the matrix to create a matrix4 object.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const float* elements | Pointer to the array of expected matrix element data. The length of array should be greater thanor equal to 16. The parameter must not be null. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_Matrix4*](capi-arkui-nativemodule-arkui-matrix4.md) | Returns the newly created matrix4 object.<br>         If the pointer of elements is null, the function will return null. |

### OH_ArkUI_Matrix4_Dispose()

```c
void OH_ArkUI_Matrix4_Dispose(ArkUI_Matrix4* matrix)
```

**描述**

Disposes a matrix4 object.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the matrix4 object to be disposed. |

### OH_ArkUI_Matrix4_Copy()

```c
ArkUI_Matrix4* OH_ArkUI_Matrix4_Copy(const ArkUI_Matrix4* matrix)
```

**描述**

Create a copy of the matrix4 object.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the original matrix4 object. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_Matrix4*](capi-arkui-nativemodule-arkui-matrix4.md) | Returns the newly created matrix4 object. |

### OH_ArkUI_Matrix4_Invert()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_Invert(ArkUI_Matrix4* matrix)
```

**描述**

Perform an inverse matrix transformation on the input matrix.If the matrix is invertible, this function will modify the input matrix; otherwise, the matrix will remainunchanged and an error code will be returned.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the matrix4 object to be inverted. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if the matrix is not invertible. |

### OH_ArkUI_Matrix4_Combine()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_Combine(ArkUI_Matrix4* oriMatrix, const ArkUI_Matrix4* anotherMatrix)
```

**描述**

Combine another matrix with the original matrix, and storing the resulting matrix in oriMatrix.The resulting matrix is equivalent to first applying the transformation of oriMatrix and then applyingthe transformation of anotherMatrix. This function will alter the oriMatrix object.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* oriMatrix | Pointer to the original matrix4 object. |
| [const ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* anotherMatrix | Pointer to another matrix object to be combined. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4_Translate()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_Translate(ArkUI_Matrix4* matrix, const ArkUI_Matrix4TranslationOptions* translate)
```

**描述**

Apply a tranlation transformation to the original matrix to obtain the translated matrix. Each translationtransformation is applied cumulatively. This function will alter the input matrix object.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the matrix4 object to be translated. |
| [const ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* translate | Pointer to the translation options. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4_Scale()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_Scale(ArkUI_Matrix4* matrix, const ArkUI_Matrix4ScaleOptions* scale)
```

**描述**

Apply a scale transformation to the original matrix to obtain the scaled matrix. Each scaletransformation is applied cumulatively. This function will alter the input matrix object.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the matrix4 object to be scaled. |
| [const ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* scale | Pointer to the scale options. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4_Rotate()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_Rotate(ArkUI_Matrix4* matrix, const ArkUI_Matrix4RotationOptions* rotate)
```

**描述**

Apply a rotation transformation to the original matrix to obtain the rotated matrix. Each rotationtransformation is applied cumulatively. This function will alter the input matrix object.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the matrix4 object to be rotated. |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* rotate | Pointer to the rotation options. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4_Skew()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_Skew(ArkUI_Matrix4* matrix, const float skewX, const float skewY)
```

**描述**

Apply a skew transformation to the original matrix to obtain the skewed matrix. Each skewtransformation is applied cumulatively. This function will alter the input matrix object.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the matrix4 object to be skewed. It must not be null. |
| const float skewX | Skew coefficient in the x direction. |
| const float skewY | Skew coefficient in the y direction. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4_TransformPoint()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_TransformPoint(const ArkUI_Matrix4* matrix, const ArkUI_PointF* oriPoint, ArkUI_PointF* result)
```

**描述**

Calculate the new coordinate position of a point after it has been transformed by a matrix.The calculated transformed coordinate point will be filled into the ArkUI_PointF structurepointed to by result.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the matrix4 object. |
| const ArkUI_PointF* oriPoint | Pointer to the original coordinate point. |
| ArkUI_PointF* result | Pointer to the result point. It must not be null. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4_SetPolyToPoly()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_SetPolyToPoly(ArkUI_Matrix4* matrix, const ArkUI_PointF* src, const ArkUI_PointF* dst, const uint32_t pointCount)
```

**描述**

Map the vertex coordinates of one polygon to the vertex coordinates of another polygon, and calculate the requiredmatrix. The resulting matrix will be filled into the object pointed to by matrix.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the original matrix4 object. The result matrix will be filled into the object pointed to by it.It must not be null. |
| const ArkUI_PointF* src | Pointer to the array of original polygon coordinate points. The array should be at least as long as pointCount. |
| const ArkUI_PointF* dst | Pointer to the array of polygon coordinate points after mapping. The array should be at least as long as pointCount. |
| const uint32_t pointCount | The number of polygon points, which must be one of the values 0, 1, 2, 3, or 4. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_Matrix4_GetElements()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_GetElements(const ArkUI_Matrix4* matrix, float* result)
```

**描述**

Obtain the 16 elements of the matrix and fill them into the array pointed to by result.The array pointed to by result must have space for 16 float elements.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the original matrix4 object. |
| float* result | Pointer to an array that can hold 16 floating-point numbers. It must not be null. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_CrossLanguageOption_SetTreeOperatingStatus()

```c
void OH_ArkUI_CrossLanguageOption_SetTreeOperatingStatus(ArkUI_CrossLanguageOption* option, OH_ArkUI_CrossLanguageOperatingStatus status)
```

**描述**

Sets the tree operating status for the cross-language option.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | The cross-language option. |
| [OH_ArkUI_CrossLanguageOperatingStatus](capi-native-type-h.md#oh_arkui_crosslanguageoperatingstatus) status | The tree operating status to be set for the cross-language option.Default value: OH_ARKUI_TREE_OPERATING_STATUS_UNDEFINED. |

### OH_ArkUI_CrossLanguageOption_GetTreeOperatingStatus()

```c
OH_ArkUI_CrossLanguageOperatingStatus OH_ArkUI_CrossLanguageOption_GetTreeOperatingStatus(ArkUI_CrossLanguageOption* option)
```

**描述**

Gets the tree operating status of the cross-language option.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | The cross-language option. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_CrossLanguageOperatingStatus](capi-native-type-h.md#oh_arkui_crosslanguageoperatingstatus) | Return the tree operating status of the cross-language option. |

### OH_ArkUI_LinearGradientOptions_Create()

```c
OH_ArkUI_LinearGradientOptions* OH_ArkUI_LinearGradientOptions_Create()
```

**描述**

Creates a linear gradient options object.The returned object must be released by calling <b>OH_ArkUI_LinearGradientOptions_Destroy</b>.

**起始版本：** 26.0.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_LinearGradientOptions*](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md) | Pointer to the <b>OH_ArkUI_LinearGradientOptions</b> object. |

### OH_ArkUI_LinearGradientOptions_Destroy()

```c
void OH_ArkUI_LinearGradientOptions_Destroy(OH_ArkUI_LinearGradientOptions* options)
```

**描述**

Destroys a linear gradient options object.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | Pointer to the <b>OH_ArkUI_LinearGradientOptions</b> object. |

### OH_ArkUI_LinearGradientOptions_SetAngle()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetAngle(OH_ArkUI_LinearGradientOptions* options, float angle)
```

**描述**

Sets angle of linear gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | Pointer to the <b>OH_ArkUI_LinearGradientOptions</b> object. |
| float angle | Start angle of linear gradient. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_LinearGradientOptions_GetAngle()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetAngle(const OH_ArkUI_LinearGradientOptions* options, float* angle)
```

**描述**

Gets angle of linear gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | Pointer to the <b>OH_ArkUI_LinearGradientOptions</b> object. |
| float* angle | Pointer to the start angle of linear gradient. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_LinearGradientOptions_SetDirection()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetDirection(OH_ArkUI_LinearGradientOptions* options, ArkUI_LinearGradientDirection direction)
```

**描述**

Sets direction of linear gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | Pointer to the <b>OH_ArkUI_LinearGradientOptions</b> object. |
| [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection) direction | Direction of linear gradient.The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_LinearGradientOptions_GetDirection()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetDirection(const OH_ArkUI_LinearGradientOptions* options, ArkUI_LinearGradientDirection* direction)
```

**描述**

Gets direction of linear gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | Pointer to the <b>OH_ArkUI_LinearGradientOptions</b> object. |
| [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)* direction | Pointer to the direction of linear gradient.The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_LinearGradientOptions_SetRepeating()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetRepeating(OH_ArkUI_LinearGradientOptions* options, bool repeating)
```

**描述**

Sets whether colors are repeated in linear gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | Pointer to the <b>OH_ArkUI_LinearGradientOptions</b> object. |
| bool repeating | Whether colors are repeated. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_LinearGradientOptions_GetRepeating()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetRepeating(const OH_ArkUI_LinearGradientOptions* options, bool* repeating)
```

**描述**

Gets whether colors are repeated in linear gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | Pointer to the <b>OH_ArkUI_LinearGradientOptions</b> object. |
| bool* repeating | Pointer to whether colors are repeated. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_LinearGradientOptions_SetColorStop()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetColorStop(OH_ArkUI_LinearGradientOptions* options, const uint32_t* colors, const float* stops, int32_t colorsAndStopsSize)
```

**描述**

Sets color stops of linear gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | Pointer to the <b>OH_ArkUI_LinearGradientOptions</b> object. |
| const uint32_t* colors | Pointer to the color array. |
| const float* stops | Pointer to the stop array. |
| int32_t colorsAndStopsSize | Number of elements in colors and stops.The number of elements in colors and stops must be the same. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_LinearGradientOptions_GetColorStop()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetColorStop(const OH_ArkUI_LinearGradientOptions* options, uint32_t* colors, float* stops, int32_t colorsAndStopsSize, int32_t* writeLength)
```

**描述**

Gets color stops of linear gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | Pointer to the <b>OH_ArkUI_LinearGradientOptions</b> object. |
| uint32_t* colors | Buffer pointer to the color array. |
| float* stops | Buffer pointer to the stop array. |
| int32_t colorsAndStopsSize | Buffer size reserved for color stops by developer.The number of elements in colors and stops must be the same.It should be larger than writeLength,otherwise the operation will return ARKUI_ERROR_CODE_PARAM_INVALID. |
| int32_t* writeLength | Number of color stops actually written. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |

### OH_ArkUI_RadialGradientOptions_Create()

```c
OH_ArkUI_RadialGradientOptions* OH_ArkUI_RadialGradientOptions_Create()
```

**描述**

Creates a radial gradient options object.The returned object must be released by calling <b>OH_ArkUI_RadialGradientOptions_Destroy</b>.

**起始版本：** 26.0.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions*](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md) | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |

### OH_ArkUI_RadialGradientOptions_Destroy()

```c
void OH_ArkUI_RadialGradientOptions_Destroy(OH_ArkUI_RadialGradientOptions* options)
```

**描述**

Destroys a radial gradient options object.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |

### OH_ArkUI_RadialGradientOptions_SetCenterX()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetCenterX(OH_ArkUI_RadialGradientOptions* options, float centerX)
```

**描述**

Sets centerX of radial gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |
| float centerX | X-coordinate of center point. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_RadialGradientOptions_GetCenterX()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetCenterX(const OH_ArkUI_RadialGradientOptions* options, float* centerX)
```

**描述**

Gets centerX of radial gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |
| float* centerX | Pointer to the X-coordinate of center point. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_RadialGradientOptions_SetCenterY()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetCenterY(OH_ArkUI_RadialGradientOptions* options, float centerY)
```

**描述**

Sets centerY of radial gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |
| float centerY | Y-coordinate of center point. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_RadialGradientOptions_GetCenterY()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetCenterY(const OH_ArkUI_RadialGradientOptions* options, float* centerY)
```

**描述**

Gets centerY of radial gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |
| float* centerY | Pointer to the Y-coordinate of center point. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_RadialGradientOptions_SetRadius()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetRadius(OH_ArkUI_RadialGradientOptions* options, float radius)
```

**描述**

Sets radius of radial gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |
| float radius | Radius of radial gradient. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_RadialGradientOptions_GetRadius()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetRadius(const OH_ArkUI_RadialGradientOptions* options, float* radius)
```

**描述**

Gets radius of radial gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |
| float* radius | Pointer to the radius of radial gradient. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_RadialGradientOptions_SetRepeating()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetRepeating(OH_ArkUI_RadialGradientOptions* options, bool repeating)
```

**描述**

Sets whether colors are repeated in radial gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |
| bool repeating | Whether colors are repeated. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_RadialGradientOptions_GetRepeating()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetRepeating(const OH_ArkUI_RadialGradientOptions* options, bool* repeating)
```

**描述**

Gets whether colors are repeated in radial gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |
| bool* repeating | Pointer to whether colors are repeated. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_RadialGradientOptions_SetColorStop()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetColorStop(OH_ArkUI_RadialGradientOptions* options, const uint32_t* colors, const float* stops, int32_t colorsAndStopsSize)
```

**描述**

Sets color stops of radial gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |
| const uint32_t* colors | Pointer to the color array. |
| const float* stops | Pointer to the stop array. |
| int32_t colorsAndStopsSize | Number of elements in colors and stops.The number of elements in colors and stops must be the same. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code. |

### OH_ArkUI_RadialGradientOptions_GetColorStop()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetColorStop(const OH_ArkUI_RadialGradientOptions* options, uint32_t* colors, float* stops, int32_t colorsAndStopsSize, int32_t* writeLength)
```

**描述**

Gets color stops of radial gradient options.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | Pointer to the <b>OH_ArkUI_RadialGradientOptions</b> object. |
| uint32_t* colors | Buffer pointer to the color array. |
| float* stops | Buffer pointer to the stop array. |
| int32_t colorsAndStopsSize | Buffer size reserved for color stops by developer.The number of elements in colors and stops must be the same.It should be larger than writeLength,otherwise the operation will return ARKUI_ERROR_CODE_PARAM_INVALID. |
| int32_t* writeLength | Number of color stops actually written. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Returns the result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter exception occurs. |


