# native_type.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @xiang-shouxing; @yangfan229-->
<!--Designer: @piggyguy; @xiang-shouxing; @yangfan229-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines the common types for the native module.

**File to include**: <arkui/native_type.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_ContextCallback](capi-arkui-nativemodule-arkui-contextcallback.md) | ArkUI_ContextCallback | Defines event callback.|
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) | ArkUI_NumberValue | Provides the number types of ArkUI on the native side.|
| [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md) | ARKUI_TextPickerRangeContent | Defines the struct of the single-column text picker with image resources.|
| [ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md) | ARKUI_TextPickerCascadeRangeContent | Defines the struct of the interconnected multi-column text picker.|
| [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md) | ArkUI_ColorStop | Defines a gradient color stop.|
| [ArkUI_Rect](capi-arkui-nativemodule-arkui-rect.md) | ArkUI_Rect | Defines a mask area.|
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md) | ArkUI_IntSize | Describes the width and height of a component.|
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) | ArkUI_IntOffset | Describes the position of a component.|
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) | ArkUI_Margin | Describes the margins of a component.|
| [ArkUI_TranslationOptions](capi-arkui-nativemodule-arkui-translationoptions.md) | ArkUI_TranslationOptions | Defines the translation options for component transition.|
| [ArkUI_ScaleOptions](capi-arkui-nativemodule-arkui-scaleoptions.md) | ArkUI_ScaleOptions | Defines the scaling options for component transition.|
| [ArkUI_RotationOptions](capi-arkui-nativemodule-arkui-rotationoptions.md) | ArkUI_RotationOptions | Defines the rotation options for component transition.|
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md) | ArkUI_LayoutConstraint | Defines the size constraints of a component during component layout.|
| [ArkUI_DrawContext](capi-arkui-nativemodule-arkui-drawcontext.md) | ArkUI_DrawContext | Defines the component drawing context.|
| [ArkUI_Node*](capi-arkui-nativemodule-arkui-node8h.md) | ArkUI_NodeHandle | Defines the pointer to the ArkUI native component object.|
| [ArkUI_NativeDialog*](capi-arkui-nativemodule-arkui-nativedialog8h.md) | ArkUI_NativeDialogHandle | Defines the handle to the custom dialog box controller of ArkUI on the native side.|
| [ArkUI_GridItemSize](capi-arkui-nativemodule-arkui-griditemsize.md) | ArkUI_GridItemSize | Defines the return value structure for the **onGetIrregularSizeByIndex** callback in **Grid** layout options.|
| [ArkUI_GridItemRect](capi-arkui-nativemodule-arkui-griditemrect.md) | ArkUI_GridItemRect | Defines the return value structure for the **onGetRectByIndex** callback in **Grid** layout options.|
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md) | ArkUI_GridLayoutOptions | Defines the **Grid** layout options.|
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) | ArkUI_WaterFlowSectionOption | Defines the water flow section configuration.|
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md) | ArkUI_ListItemSwipeActionItem | Defines the item configuration for **ListItemSwipeActionOption**.|
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md) | ArkUI_ListItemSwipeActionOption | Defines the configuration for **ListItemSwipeActionOption**.|
| [ArkUI_Context*](capi-arkui-nativemodule-arkui-context8h.md) | ArkUI_ContextHandle | Defines the handle to the ArkUI native UI context.|
| [ArkUI_NodeContent*](capi-arkui-nativemodule-arkui-nodecontent8h.md) | ArkUI_NodeContentHandle | Defines the handle to the ArkUI NodeContent instance on the native side.|
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md) | ArkUI_AlignmentRuleOption | Defines the alignment rule in the relative container.|
| [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md) | ArkUI_GuidelineOption | Defines the ID, direction, and position of a guideline.|
| [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md) | ArkUI_BarrierOption | Defines the ID, direction, and referenced component of a barrier.|
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md) | ArkUI_ImageAnimatorFrameInfo | Defines the image frame information.|
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) | ArkUI_ListChildrenMainSize | Defines the **ChildrenMainSize** information of the **List** component.|
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) | ArkUI_ProgressLinearStyleOption | Defines a struct for the linear progress indicator style.|
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md) | ArkUI_CustomProperty | Defines a struct for the custom property information.|
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md) | ArkUI_HostWindowInfo | Defines a struct for the host window information.|
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md) | ArkUI_ActiveChildrenInfo | Defines a struct for active child node information.|
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md) | ArkUI_CrossLanguageOption | Defines cross-language configuration options.|
| [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md) | AbilityBase_Want | Declares a **Want** object.|
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md) | ArkUI_EmbeddedComponentOption | Defines the **EmbeddedComponentOption** parameter for **EmbeddedComponent**.|
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md) | ArkUI_AccessibilityState | Defines a struct for the component accessibility state.|
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md) | ArkUI_AccessibilityValue | Defines a struct for the component accessibility value.|
| [ArkUI_SystemFontStyleEvent](capi-arkui-nativemodule-arkui-systemfontstyleevent.md) | ArkUI_SystemFontStyleEvent | Defines a struct for the system font style event.|
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md) | ArkUI_CustomSpanMeasureInfo | Defines a struct for the measurement information of a custom span.|
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md) | ArkUI_CustomSpanMetrics | Defines a struct for the measurement metrics of a custom span.|
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md) | ArkUI_CustomSpanDrawInfo | Defines a struct for the drawing information of a custom span.|
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md) | ArkUI_SwiperIndicator | Defines the navigation indicator style of the **Swiper** component.|
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) | ArkUI_SwiperDigitIndicator | Defines the digit-style navigation indicator of the **Swiper** component.|
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) | ArkUI_SwiperArrowStyle | Defines the arrow style for the **Swiper** component.|
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) | ArkUI_StyledString_Descriptor | Defines a struct for the styled string descriptor object supported by the text component.|
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md) | ArkUI_SnapshotOptions | Defines a struct for snapshot options.|
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md) | ArkUI_TextPickerRangeContentArray | Defines the data selection list for the text picker.|
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md) | ArkUI_TextCascadePickerRangeContentArray | Defines the content array for a multi-column cascading data picker.|
| [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md)| ArkUI_SelectionOptions | Defines options of the selection operation.|
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md) | ArkUI_VisibleAreaEventOptions | Returns the created instance of visible area change event parameters.|
|[ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)|ArkUI_PositionEdges|Provides position parameters relative to the boundaries of the container's content area.|
|[ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)|ArkUI_PixelRoundPolicy|Defines a struct for the component pixel rounding policy.|
|[ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md)|ArkUI_ContentTransitionEffect|Defines the content transition effect.|
|[ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)|ArkUI_ShowCounterConfig|Defines the text input character counter configuration.|
|[ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)|ArkUI_TextContentBaseController|Defines the basic controller for text.|
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md) | ArkUI_TextMenuItem | Defines the text menu item structure.|
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md) | ArkUI_TextMenuItemArray | Defines the text menu item array structure.|
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md) | ArkUI_TextEditMenuOptions | Defines the text menu extension structure.|
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md) | ArkUI_TextSelectionMenuOptions | Defines the custom text selection menu structure.|
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md) | ArkUI_SelectedDragPreviewStyle | Defines the drag preview style of the selected text.|
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md) | ArkUI_MotionPathOptions | Defines the motion path option for path animation.|
| [ArkUI_PickerIndicatorBackground](capi-arkui-nativemodule-arkui-pickerindicatorbackground.md)|ArkUI_PickerIndicatorBackground|Defines the style parameter of the background-style indicator.|
| [ArkUI_PickerIndicatorDivider](capi-arkui-nativemodule-arkui-pickerindicatordivider.md)|ArkUI_PickerIndicatorDivider|Defines the style parameter of the divider-style indicator.|
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)|ArkUI_PickerIndicatorStyle|Defines the style of the selected item indicator.|

### Enums

| Name                                                                 | typedef Keyword                     | Description                               |
|---------------------------------------------------------------------|---------------------------------|-----------------------------------|
| [ArkUI_Alignment](#arkui_alignment)                                 | ArkUI_Alignment                 | Enumerates the alignment modes.                       |
| [ArkUI_ImageRepeat](#arkui_imagerepeat)                             | ArkUI_ImageRepeat               | Enumerates the image repeat patterns.                     |
| [ArkUI_FontStyle](#arkui_fontstyle)                                 | ArkUI_FontStyle                 | Enumerates the font styles.                       |
| [ArkUI_FontWeight](#arkui_fontweight)                               | ArkUI_FontWeight                | Enumerates the font weights.                    |
| [ArkUI_TextAlignment](#arkui_textalignment)                         | ArkUI_TextAlignment             | Enumerates text alignment modes.                   |
| [ArkUI_TextVerticalAlignment](#arkui_textverticalalignment)         | ArkUI_TextVerticalAlignment     | Enumerates text vertical alignment styles.                   |
| [ArkUI_EnterKeyType](#arkui_enterkeytype)                           | ArkUI_EnterKeyType              | Enumerates the types of the Enter key for a single-line text box.               |
| [ArkUI_TextInputType](#arkui_textinputtype)                         | ArkUI_TextInputType             | Enumerates the input method type of a single-line text.                  |
| [ArkUI_TextAreaType](#arkui_textareatype)                           | ArkUI_TextAreaType              | Enumerates the input method types of a multi-line text.                  |
| [ArkUI_CancelButtonStyle](#arkui_cancelbuttonstyle)                 | ArkUI_CancelButtonStyle         | Enumerates the styles of the Cancel button.                     |
| [ArkUI_XComponentType](#arkui_xcomponenttype)                       | ArkUI_XComponentType            | Enumerates the types of the **XComponent** component.               |
| [ArkUI_ProgressType](#arkui_progresstype)                           | ArkUI_ProgressType              | Enumerates the styles of the progress indicator.                      |
| [ArkUI_TextDecorationType](#arkui_textdecorationtype)               | ArkUI_TextDecorationType        | Enumerates the text decoration types.                      |
| [ArkUI_TextDecorationStyle](#arkui_textdecorationstyle)             | ArkUI_TextDecorationStyle       | Enumerates the text decoration styles.                      |
| [ArkUI_TextCase](#arkui_textcase)                                   | ArkUI_TextCase                  | Enumerates the text cases.                      |
| [ArkUI_CopyOptions](#arkui_copyoptions)                             | ArkUI_CopyOptions               | Enumerates the text copy and paste modes.                   |
| [ArkUI_ShadowType](#arkui_shadowtype)                               | ArkUI_ShadowType                | Enumerates shadow types.                       |
| [ArkUI_DatePickerMode](#arkui_datepickermode)                       | ArkUI_DatePickerMode            | Enumerates the column display modes of the date picker.                |
| [ArkUI_TextPickerRangeType](#arkui_textpickerrangetype)             | ArkUI_TextPickerRangeType       | Enumerates the types of the text picker.                 |
| [ArkUI_AccessibilityCheckedState](#arkui_accessibilitycheckedstate) | ArkUI_AccessibilityCheckedState | Enumerates the accessibility check box states.                 |
| [ArkUI_AccessibilityActionType](#arkui_accessibilityactiontype)     | ArkUI_AccessibilityActionType   | Enumerates the accessibility action types.                       |
| [ArkUI_EdgeEffect](#arkui_edgeeffect)                               | ArkUI_EdgeEffect                | Enumerates the effects used at the edges of the component when the boundary of the scrollable content is reached.                     |
| [ArkUI_BarState](#arkui_barstate)                               | ArkUI_BarState                | Enumerates the text control scrollbar states.                     |
| [ArkUI_EffectEdge](#arkui_effectedge)                               | ArkUI_EffectEdge                | Enumerates the edges for which the effect takes effect when the boundary of the scrollable content is reached.                |
| [ArkUI_ScrollDirection](#arkui_scrolldirection)                     | ArkUI_ScrollDirection           | Enumerates the scroll directions of scrollable components.               |
| [ArkUI_ScrollSnapAlign](#arkui_scrollsnapalign)                     | ArkUI_ScrollSnapAlign           | Enumerates the alignment modes of list items when scrolling ends.                |
| [ArkUI_ScrollBarDisplayMode](#arkui_scrollbardisplaymode)           | ArkUI_ScrollBarDisplayMode      | Enumerates the scrollbar display modes.                      |
| [ArkUI_Axis](#arkui_axis)                                           | ArkUI_Axis                      | Enumerates the scroll directions.            |
| [ArkUI_StickyStyle](#arkui_stickystyle)                             | ArkUI_StickyStyle               | Enumerates the modes for pinning the header to the top or the footer to the bottom.                  |
| [ArkUI_ContentClipMode](#arkui_contentclipmode)                     | ArkUI_ContentClipMode           | Enumerates the content clipping modes of scrollable components.               |
| [ArkUI_WaterFlowLayoutMode](#arkui_waterflowlayoutmode)             | ArkUI_WaterFlowLayoutMode       | Enumerates the layout modes of the WaterFlow component.            |
| [ArkUI_BorderStyle](#arkui_borderstyle)                             | ArkUI_BorderStyle               | Enumerates the border styles.                       |
| [ArkUI_HitTestMode](#arkui_hittestmode)                             | ArkUI_HitTestMode               | Enumerates the hit test modes.                       |
| [ArkUI_ShadowStyle](#arkui_shadowstyle)                             | ArkUI_ShadowStyle               | Enumerates shadow styles.                         |
| [ArkUI_AnimationCurve](#arkui_animationcurve)                       | ArkUI_AnimationCurve            | Enumerates the animation curves.                         |
| [ArkUI_SwiperArrow](#arkui_swiperarrow)                             | ArkUI_SwiperArrow               | Enumerates arrow styles of the navigation indicator.                  |
| [ArkUI_SwiperNestedScrollMode](#arkui_swipernestedscrollmode)       | ArkUI_SwiperNestedScrollMode    | Enumerates the nested scrolling modes of the **Swiper** component and its parent container.             |
| [ArkUI_PageFlipMode](#arkui_pageflipmode)                           | ArkUI_PageFlipMode              | Enumerates the page flipping modes using the mouse wheel for the <b>Swiper</b> component.                |
| [ArkUI_SwiperAnimationMode](#arkui_swiperanimationmode)             | ArkUI_SwiperAnimationMode       | Enumerates the animation modes for the **Swiper** component when jumping to the page with the specified index.         |
| [ArkUI_AccessibilityMode](#arkui_accessibilitymode)                 | ArkUI_AccessibilityMode         | Enumerates the accessibility modes.                     |
| [ArkUI_TextCopyOptions](#arkui_textcopyoptions)                     | ArkUI_TextCopyOptions           | Enumerates copy options, which define whether copy and paste is allowed for text content.               |
| [ArkUI_TextHeightAdaptivePolicy](#arkui_textheightadaptivepolicy)   | ArkUI_TextHeightAdaptivePolicy  | Defines how the adaptive height is determined for the text.                    |
| [ArkUI_ScrollNestedMode](#arkui_scrollnestedmode)                   | ArkUI_ScrollNestedMode          | Enumerates nested scrolling modes.                        |
| [ArkUI_ScrollEdge](#arkui_scrolledge)                               | ArkUI_ScrollEdge                | Enumerates the edges to which the component scrolls.                      |
| [ArkUI_ScrollAlignment](#arkui_scrollalignment)                     | ArkUI_ScrollAlignment           | Defines how the list item to scroll to is aligned with the container.                 |
| [ArkUI_ScrollState](#arkui_scrollstate)                             | ArkUI_ScrollState               | Enumerates the scrolling states.                        |
| [ArkUI_SliderBlockStyle](#arkui_sliderblockstyle)                   | ArkUI_SliderBlockStyle          | Enumerates the styles of the slider in the block direction.                          |
| [ArkUI_SliderDirection](#arkui_sliderdirection)                     | ArkUI_SliderDirection           | Enumerates the scroll directions of the slider.                       |
| [ArkUI_SliderStyle](#arkui_sliderstyle)                             | ArkUI_SliderStyle               | Enumerates the slider styles.                     |
| [ArkUI_CheckboxShape](#arkui_checkboxshape)                         | ArkUI_CheckboxShape             | Enumerates the shapes of the check box.                  |
| [ArkUI_AnimationPlayMode](#arkui_animationplaymode)                 | ArkUI_AnimationPlayMode         | Enumerates the animation playback modes.                        |
| [ArkUI_ImageSize](#arkui_imagesize)                                 | ArkUI_ImageSize                 | Defines the image size.                        |
| [ArkUI_AdaptiveColor](#arkui_adaptivecolor)                         | ArkUI_AdaptiveColor             | Enumerates the adaptive color modes.                          |
| [ArkUI_ColorMode](#arkui_colormode)                                 | ArkUI_ColorMode                 | Enumerates the color modes.                         |
| [ArkUI_SystemColorMode](#arkui_systemcolormode)                     | ArkUI_SystemColorMode           | Enumerates the system color modes.                       |
| [ArkUI_BlurStyle](#arkui_blurstyle)                                 | ArkUI_BlurStyle                 | Enumerates the blur styles.                        |
| [ArkUI_BlurStyleActivePolicy](#arkui_blurstyleactivepolicy)         | ArkUI_BlurStyleActivePolicy     | Enumerates the activation policies for the background blur effect.                      |
| [ArkUI_VerticalAlignment](#arkui_verticalalignment)                 | ArkUI_VerticalAlignment         | Enumerates the vertical alignment modes.                        |
| [ArkUI_HorizontalAlignment](#arkui_horizontalalignment)             | ArkUI_HorizontalAlignment       | Enumerates the alignment mode in the horizontal direction.                      |
| [ArkUI_TextOverflow](#arkui_textoverflow)                           | ArkUI_TextOverflow              | Enumerates the display modes when the text is too long.                    |
| [ArkUI_ImageSpanAlignment](#arkui_imagespanalignment)               | ArkUI_ImageSpanAlignment        | Enumerates the alignment mode of the image with the text.                   |
| [ArkUI_ObjectFit](#arkui_objectfit)                                 | ArkUI_ObjectFit                 | Enumerates the image filling effects.ImageSpanAlignment    |
| [ArkUI_ImageInterpolation](#arkui_imageinterpolation)               | ArkUI_ImageInterpolation        | Enumerates the image interpolation effects.                        |
| [ArkUI_DynamicRangeMode](#arkui_dynamicrangemode)                   | ArkUI_DynamicRangeMode          | Enumerates the dynamic range modes (for example, SDR/HDR) for images, controlling the display range of image brightness and color gamut.|
| [ArkUI_ImageRotateOrientation](#arkui_imagerotateorientation)       | ArkUI_ImageRotateOrientation    | Enumerates image rotation directions.                        |
| [ArkUI_BlendMode](#arkui_blendmode)                                 | ArkUI_BlendMode                 | Enumerates the blend modes.                         |
| [ArkUI_Direction](#arkui_direction)                                 | ArkUI_Direction                 | Enumerates the modes in which components are laid out along the main axis of the container.              |
| [ArkUI_ItemAlignment](#arkui_itemalignment)                         | ArkUI_ItemAlignment             | Enumerates the modes in which components are laid out along the cross axis of the container.            |
| [ArkUI_ColorStrategy](#arkui_colorstrategy)                         | ArkUI_ColorStrategy             | Enumerates the foreground colors.                          |
| [ArkUI_FlexAlignment](#arkui_flexalignment)                         | ArkUI_FlexAlignment             | Enumerates the vertical alignment modes.                      |
| [ArkUI_FlexDirection](#arkui_flexdirection)                         | ArkUI_FlexDirection             | Enumerates the directions of the main axis in the flex container.                   |
| [ArkUI_FlexWrap](#arkui_flexwrap)                                   | ArkUI_FlexWrap                  | Defines whether the flex container has a single line or multiple lines.                  |
| [ArkUI_Visibility](#arkui_visibility)                               | ArkUI_Visibility                | Enumerates the visibility values.                      |
| [ArkUI_CalendarAlignment](#arkui_calendaralignment)                 | ArkUI_CalendarAlignment         | Enumerates the alignment modes between the calendar picker and the entry component.                  |
| [ArkUI_MaskType](#arkui_masktype)                                   | ArkUI_MaskType                  | Enumerates the mask types.                          |
| [ArkUI_ClipType](#arkui_cliptype)                                   | ArkUI_ClipType                  | Enumerates the clipping region types.                          |
| [ArkUI_ShapeType](#arkui_shapetype)                                 | ArkUI_ShapeType                 | Enumerates custom shape types.                           |
| [ArkUI_LinearGradientDirection](#arkui_lineargradientdirection)     | ArkUI_LinearGradientDirection   | Enumerates the gradient directions.                        |
| [ArkUI_WordBreak](#arkui_wordbreak)                                 | ArkUI_WordBreak                 | Enumerates the word break rules.                        |
| [ArkUI_EllipsisMode](#arkui_ellipsismode)                           | ArkUI_EllipsisMode              | Enumerates the ellipsis positions.                        |
| [ArkUI_ImageRenderMode](#arkui_imagerendermode)                     | ArkUI_ImageRenderMode           | Enumerates the image rendering modes.                        |
| [ArkUI_TransitionEdge](#arkui_transitionedge)                       | ArkUI_TransitionEdge            | Enumerates the slide-in and slide-out positions of the component from the screen edge during transition.                 |
| [ArkUI_FinishCallbackType](#arkui_finishcallbacktype)               | ArkUI_FinishCallbackType        | Enumerates the animation **onFinish** callback types.             |
| [ArkUI_ListItemAlignment](#arkui_listitemalignment)                 | ArkUI_ListItemAlignment         | Enumerates the alignment modes of items along the cross axis.                      |
| [ArkUI_BlendApplyType](#arkui_blendapplytype)                       | ArkUI_BlendApplyType            | Defines how the specified blend mode is applied.               |
| [ArkUI_LengthMetricUnit](#arkui_lengthmetricunit)                   | ArkUI_LengthMetricUnit          | Enumerates the component units.                       |
| [ArkUI_TextInputContentType](#arkui_textinputcontenttype)           | ArkUI_TextInputContentType      | Enumerates the autofill types.                        |
| [ArkUI_BarrierDirection](#arkui_barrierdirection)                   | ArkUI_BarrierDirection          | Enumerates the barrier directions.                        |
| [ArkUI_RelativeLayoutChainStyle](#arkui_relativelayoutchainstyle)   | ArkUI_RelativeLayoutChainStyle  | Enumerates the chain styles.                          |
| [ArkUI_TextInputStyle](#arkui_textinputstyle)                       | ArkUI_TextInputStyle            | Enumerates the text input styles.                         |
| [ArkUI_KeyboardAppearance](#arkui_keyboardappearance)               | ArkUI_KeyboardAppearance        | Enumerates the appearance modes of the keyboard when the text box is focused.                    |
| [ArkUI_TextDataDetectorType](#arkui_textdatadetectortype)           | ArkUI_TextDataDetectorType      | Enumerates the entity types of text recognition.                     |
| [ArkUI_ButtonType](#arkui_buttontype)                               | ArkUI_ButtonType                | Enumerates the button types.                       |
| [ArkUI_RenderFit](#arkui_renderfit)                                 | ArkUI_RenderFit   | Enumerates the sizing and positioning behaviors of animated content in its final state.|
| [ArkUI_SwiperIndicatorType](#arkui_swiperindicatortype)             | ArkUI_SwiperIndicatorType       | Enumerates the navigation indicator types of the **Swiper** component.            |
| [ArkUI_AnimationDirection](#arkui_animationdirection)               | ArkUI_AnimationDirection        | Enumerates the animation playback modes.                          |
| [ArkUI_ListItemSwipeActionState](#arkui_listitemswipeactionstate)   | ArkUI_ListItemSwipeActionState  | Enumerates the swipe action item states of list items.|
| [ArkUI_ListItemSwipeEdgeEffect](#arkui_listitemswipeedgeeffect)     | ArkUI_ListItemSwipeEdgeEffect   | Enumerates the swipe action item edge effects of list items.|
| [ArkUI_ListItemSwipeActionDirection](#arkui_listitemswipeactiondirection) | ArkUI_ListItemSwipeActionDirection | Enumerates the swipe action menu display directions for **ListItem** components.|
| [ArkUI_AnimationStatus](#arkui_animationstatus)                     | ArkUI_AnimationStatus           | Enumerates the playback states of the frame-by-frame animation.                      |
| [ArkUI_AnimationFillMode](#arkui_animationfillmode)                 | ArkUI_AnimationFillMode         | Enumerates the states before and after execution of the frame-by-frame animation.            |
| [ArkUI_ErrorCode](#arkui_errorcode)                                 | ArkUI_ErrorCode                 | Enumerates the error codes.                        |
| [ArkUI_ScrollSource](#arkui_scrollsource)                           | ArkUI_ScrollSource              | Enumerates scroll sources.                       |
| [ArkUI_SafeAreaType](#arkui_safeareatype)                           | ArkUI_SafeAreaType              | Enumerates the types of expanded safe areas.                    |
| [ArkUI_SafeAreaEdge](#arkui_safeareaedge)                           | ArkUI_SafeAreaEdge              | Enumerates the edges for expanding the safe area.                 |
| [ArkUI_FocusMove](#arkui_focusmove)                                 | ArkUI_FocusMove                 | Enumerates the focus movement directions.                    |
| [ArkUI_ListItemGroupArea](#arkui_listitemgrouparea)                 | ArkUI_ListItemGroupArea         | Enumerates areas of the **ListItemGroup** component.           |
| [ArkUI_KeyboardAvoidMode](#arkui_keyboardavoidmode)                 | ArkUI_KeyboardAvoidMode         | Enumerates the soft keyboard avoidance modes.                          |
| [ArkUI_HoverModeAreaType](#arkui_hovermodeareatype)                 | ArkUI_HoverModeAreaType         | Enumerates the types of display areas for the hover mode.                         |
| [ArkUI_ExpandMode](#arkui_expandmode)                               | ArkUI_ExpandMode                | Enumerates the expansion mode of child nodes.                    |
| [ArkUI_NavDestinationState](#arkui_navdestinationstate)             | ArkUI_NavDestinationState       | Enumerates the **NavDestination** component states.           |
| [ArkUI_RouterPageState](#arkui_routerpagestate)                     | ArkUI_RouterPageState           | Enumerates the states of a page during routing.                |
| [ArkUI_UIState](#arkui_uistate)                                     | ArkUI_UIState                   | Enumerates the UI states of a component, used for handling state-specific styles.              |
| [ArkUI_FocusWrapMode](#arkui_focuswrapmode)                         | ArkUI_FocusWrapMode             | Enumerates the focus wrap mode of components.                        |
| [ArkUI_ItemFillPolicy](#arkui_itemfillpolicy)                         | ArkUI_ItemFillPolicy             | Enumerates preset column layouts for different responsive breakpoints.                        |
| [ArkUI_EdgeDirection](#arkui_edgedirection)                         | ArkUI_EdgeDirection             | Enumerates rectangle edge directions.                        |
| [ArkUI_CornerDirection](#arkui_cornerdirection)                     | ArkUI_CornerDirection           | Enumerates corner directions.                        |
| [ArkUI_LayoutPolicy](#arkui_layoutpolicy)                         | ArkUI_LayoutPolicy             | Enumerates layout policies.                        |
| [ArkUI_PixelRoundCalcPolicy](#arkui_pixelroundcalcpolicy) | ArkUI_PixelRoundCalcPolicy | Enumerates pixel rounding calculation policies.|
| [ArkUI_GridItemStyle](#arkui_griditemstyle)                         | ArkUI_GridItemStyle             | Enumerates styles of grid items.                        |
| [ArkUI_MenuPolicy](#arkui_menupolicy)                               | ArkUI_MenuPolicy                | Enumerates menu display policies.                            |
| [ArkUI_ResponseRegionSupportedTool](#arkui_responseregionsupportedtool)                         | ArkUI_ResponseRegionSupportedTool             | Enumerates the input tool types supported for response region configuration.                        |
| [ArkUI_TextMenuItemId](#arkui_textmenuitemid) | ArkUI_TextMenuItemId | Enumerates the IDs of text menu items.|
| [ArkUI_TextSpanType](#arkui_textspantype) | ArkUI_TextSpanType | Enumerates the text recognition types of a custom text selection menu.|
| [ArkUI_TextResponseType](#arkui_textresponsetype) | ArkUI_TextResponseType | Enumerates the response types of a custom text selection menu.|
| [ArkUI_HoverEffect](#arkui_hovereffect) | ArkUI_HoverEffect | Enumerates the hover effects when a component is hovered over.|
| [ArkUI_FocusPriority](#arkui_focuspriority) | ArkUI_FocusPriority | Enumerates the priority levels for focus management within the application. These levels determine the sequence in which UI components receive focus during user interaction.|
| [ArkUI_LayoutSafeAreaType](#arkui_layoutsafeareatype)               | ArkUI_LayoutSafeAreaType         | Enumerates the types of expanded safe areas.                        |
| [ArkUI_LayoutSafeAreaEdge](#arkui_layoutsafeareaedge)               | ArkUI_LayoutSafeAreaEdge         | Enumerates the edges for expanding the safe area.                        |
| [ArkUI_LocalizedAlignment](#arkui_localizedalignment)               | ArkUI_LocalizedAlignment         | Defines the alignment rules of child components in the **Stack** container.                        |
| [ArkUI_RenderStrategy](#arkui_renderstrategy)                       | ArkUI_RenderStrategy             | Defines rendering strategies for drawing rounded corners.               |
| [ArkUI_MarqueeStartPolicy](#arkui_marqueestartpolicy)| ArkUI_MarqueeStartPolicy| Defines the start policy of a marquee.|
| [ArkUI_MarqueeUpdatePolicy](#arkui_marqueeupdatepolicy)| ArkUI_MarqueeUpdatePolicy| Defines the update policy of a marquee.|
| [ArkUI_PickerIndicatorType](#arkui_pickerindicatortype) | ArkUI_PickerIndicatorType | Defines the indicator type of the selected item.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Create()](#oh_arkui_layoutconstraint_create) | - | Creates a size constraint.|
| [ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Copy(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_copy) | - | Performs a deep copy of a size constraint.|
| [void* OH_ArkUI_LayoutConstraint_Dispose(ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_dispose) | - | Disposes of the pointer to a size constraint.|
| [int32_t OH_ArkUI_LayoutConstraint_GetMaxWidth(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getmaxwidth) | - | Obtains the maximum width for a size constraint, in px.|
| [int32_t OH_ArkUI_LayoutConstraint_GetMinWidth(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getminwidth) | - | Obtains the minimum width for a size constraint, in px.|
| [int32_t OH_ArkUI_LayoutConstraint_GetMaxHeight(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getmaxheight) | - | Obtains the maximum height for a size constraint, in px.|
| [int32_t OH_ArkUI_LayoutConstraint_GetMinHeight(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getminheight) | - | Obtains the minimum height for a size constraint, in px.|
| [int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceWidth(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getpercentreferencewidth) | - | Obtains the width percentage reference for a size constraint, in px.|
| [int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceHeight(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getpercentreferenceheight) | - | Obtains the height percentage reference for a size constraint, in px.|
| [void OH_ArkUI_LayoutConstraint_SetMaxWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setmaxwidth) | - | Sets the maximum width.|
| [void OH_ArkUI_LayoutConstraint_SetMinWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setminwidth) | - | Sets the minimum width.|
| [void OH_ArkUI_LayoutConstraint_SetMaxHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setmaxheight) | - | Sets the maximum height.|
| [void OH_ArkUI_LayoutConstraint_SetMinHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setminheight) | - | Sets the minimum height.|
| [void OH_ArkUI_LayoutConstraint_SetPercentReferenceWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setpercentreferencewidth) | - | Sets the width percentage reference.|
| [void OH_ArkUI_LayoutConstraint_SetPercentReferenceHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setpercentreferenceheight) | - | Sets the height percentage reference.|
| [void* OH_ArkUI_DrawContext_GetCanvas(ArkUI_DrawContext* context)](#oh_arkui_drawcontext_getcanvas) | - | Obtains the pointer to a canvas for drawing, which can be converted into the **OH_Drawing_Canvas** in the **Drawing** module.|
| [ArkUI_IntSize OH_ArkUI_DrawContext_GetSize(ArkUI_DrawContext* context)](#oh_arkui_drawcontext_getsize) | - | Obtains the size of a drawing area.|
| [ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create()](#oh_arkui_waterflowsectionoption_create) | - | Creates a water flow section configuration.|
| [void OH_ArkUI_WaterFlowSectionOption_Dispose(ArkUI_WaterFlowSectionOption* option)](#oh_arkui_waterflowsectionoption_dispose) | - | Disposes of the pointer to a water flow section configuration.|
| [void OH_ArkUI_WaterFlowSectionOption_SetSize(ArkUI_WaterFlowSectionOption* option, int32_t size)](#oh_arkui_waterflowsectionoption_setsize) | - | Sets the array length for a water flow section configuration.|
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetSize(ArkUI_WaterFlowSectionOption* option)](#oh_arkui_waterflowsectionoption_getsize) | - | Obtains the array length for a water flow section configuration.|
| [void OH_ArkUI_WaterFlowSectionOption_SetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t itemCount)](#oh_arkui_waterflowsectionoption_setitemcount) | - | Sets the number of items in a water flow section.|
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getitemcount) | - | Obtains the number of items in the water flow section that matches the specified index.|
| [void OH_ArkUI_WaterFlowSectionOption_SetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t crossCount)](#oh_arkui_waterflowsectionoption_setcrosscount) | - | Sets the number of columns (in a vertical layout) or rows (in a horizontal layout) of a water flow.|
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getcrosscount) | - | Obtains the number of columns (in a vertical layout) or rows (in a horizontal layout) of a water flow.|
| [void OH_ArkUI_WaterFlowSectionOption_SetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float columnGap)](#oh_arkui_waterflowsectionoption_setcolumngap) | - | Sets the gap between columns in the specified water flow section.|
| [float OH_ArkUI_WaterFlowSectionOption_GetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getcolumngap) | - | Obtains the gap between columns in the water flow section that matches the specified index.|
| [void OH_ArkUI_WaterFlowSectionOption_SetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float rowGap)](#oh_arkui_waterflowsectionoption_setrowgap) | - | Sets the gap between rows in the specified water flow section.|
| [float OH_ArkUI_WaterFlowSectionOption_GetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getrowgap) | - | Obtains the gap between rows in the water flow section that matches the specified index.|
| [void OH_ArkUI_WaterFlowSectionOption_SetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index,float marginTop, float marginRight, float marginBottom, float marginLeft)](#oh_arkui_waterflowsectionoption_setmargin) | - | Sets the margins for the specified water flow section.|
| [ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getmargin) | - | Obtains the margins of the water flow section that matches the specified index.|
| [void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex (ArkUI_WaterFlowSectionOption* option, int32_t index, float(\*callback)(int32_t itemIndex))](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex) | - | Obtains the main axis size of a specified item based on **flowItemIndex** through a water flow section configuration.|
| [void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData (ArkUI_WaterFlowSectionOption* option, int32_t index, void* userData, float (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata) | - | Obtains the main axis size of a specified item based on **flowItemIndex** through a water flow section configuration.|
| [ArkUI_GuidelineOption* OH_ArkUI_GuidelineOption_Create(int32_t size)](#oh_arkui_guidelineoption_create) | - | Creates a guideline configuration for this **RelativeContainer** component.|
| [void OH_ArkUI_GuidelineOption_Dispose(ArkUI_GuidelineOption* guideline)](#oh_arkui_guidelineoption_dispose) | - | Disposes of a guideline configuration.|
| [void OH_ArkUI_GuidelineOption_SetId(ArkUI_GuidelineOption* guideline, const char* value, int32_t index)](#oh_arkui_guidelineoption_setid) | - | Sets the ID of a guideline.|
| [void OH_ArkUI_GuidelineOption_SetDirection(ArkUI_GuidelineOption* guideline, ArkUI_Axis value, int32_t index)](#oh_arkui_guidelineoption_setdirection) | - | Sets the direction of a guideline.|
| [void OH_ArkUI_GuidelineOption_SetPositionStart(ArkUI_GuidelineOption* guideline, float value, int32_t index)](#oh_arkui_guidelineoption_setpositionstart) | - | Sets the distance between a guideline and the left or top of the container.|
| [void OH_ArkUI_GuidelineOption_SetPositionEnd(ArkUI_GuidelineOption* guideline, float value, int32_t index)](#oh_arkui_guidelineoption_setpositionend) | - | Sets the distance between a guideline and the right or bottom of the container.|
| [const char* OH_ArkUI_GuidelineOption_GetId(ArkUI_GuidelineOption* guideline, int32_t index)](#oh_arkui_guidelineoption_getid) | - | Obtains the ID of a guideline.|
| [ArkUI_Axis OH_ArkUI_GuidelineOption_GetDirection(ArkUI_GuidelineOption* guideline, int32_t index)](#oh_arkui_guidelineoption_getdirection) | - | Obtains the direction of a guideline.|
| [float OH_ArkUI_GuidelineOption_GetPositionStart(ArkUI_GuidelineOption* guideline, int32_t index)](#oh_arkui_guidelineoption_getpositionstart) | - | Obtains the distance between a guideline and the left or top of the container.|
| [float OH_ArkUI_GuidelineOption_GetPositionEnd(ArkUI_GuidelineOption* guideline, int32_t index)](#oh_arkui_guidelineoption_getpositionend) | - | Obtains the distance between a guideline and the right or bottom of the container.|
| [ArkUI_BarrierOption* OH_ArkUI_BarrierOption_Create(int32_t size)](#oh_arkui_barrieroption_create) | - | Creates a barrier configuration for this **RelativeContainer** component.|
| [void OH_ArkUI_BarrierOption_Dispose(ArkUI_BarrierOption* barrierStyle)](#oh_arkui_barrieroption_dispose) | - | Disposes of a barrier configuration.|
| [void OH_ArkUI_BarrierOption_SetId(ArkUI_BarrierOption* barrierStyle, const char* value, int32_t index)](#oh_arkui_barrieroption_setid) | - | Sets the ID of a barrier.|
| [void OH_ArkUI_BarrierOption_SetDirection(ArkUI_BarrierOption* barrierStyle, ArkUI_BarrierDirection value, int32_t index)](#oh_arkui_barrieroption_setdirection) | - | Sets the direction of a barrier.|
| [void OH_ArkUI_BarrierOption_SetReferencedId(ArkUI_BarrierOption* barrierStyle, const char* value, int32_t index)](#oh_arkui_barrieroption_setreferencedid) | - | Sets the referenced components of a barrier.|
| [const char* OH_ArkUI_BarrierOption_GetId(ArkUI_BarrierOption* barrierStyle, int32_t index)](#oh_arkui_barrieroption_getid) | - | Obtains the ID of a barrier.|
| [ArkUI_BarrierDirection OH_ArkUI_BarrierOption_GetDirection(ArkUI_BarrierOption* barrierStyle, int32_t index)](#oh_arkui_barrieroption_getdirection) | - | Obtains the direction of a barrier.|
| [const char* OH_ArkUI_BarrierOption_GetReferencedId(ArkUI_BarrierOption* barrierStyle, int32_t index , int32_t referencedIndex)](#oh_arkui_barrieroption_getreferencedid) | - | Obtains the referenced components of a barrier.|
| [int32_t OH_ArkUI_BarrierOption_GetReferencedIdSize(ArkUI_BarrierOption* barrierStyle, int32_t index)](#oh_arkui_barrieroption_getreferencedidsize) | - | Obtains the number of referenced components of a barrier.|
| [ArkUI_AlignmentRuleOption* OH_ArkUI_AlignmentRuleOption_Create()](#oh_arkui_alignmentruleoption_create) | - | Creates an alignment rule configuration for this **RelativeContainer** component.|
| [void OH_ArkUI_AlignmentRuleOption_Dispose(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_dispose) | - | Disposes of an alignment rule configuration of this **RelativeContainer** component.|
| [void OH_ArkUI_AlignmentRuleOption_SetStart(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)](#oh_arkui_alignmentruleoption_setstart) | - | Sets the left alignment parameters.|
| [void OH_ArkUI_AlignmentRuleOption_SetEnd(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)](#oh_arkui_alignmentruleoption_setend) | - | Sets the right alignment parameters.|
| [void OH_ArkUI_AlignmentRuleOption_SetCenterHorizontal(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)](#oh_arkui_alignmentruleoption_setcenterhorizontal) | - | Sets the horizontal center alignment parameters.|
| [void OH_ArkUI_AlignmentRuleOption_SetTop(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)](#oh_arkui_alignmentruleoption_settop) | - | Sets the top alignment parameters.|
| [void OH_ArkUI_AlignmentRuleOption_SetBottom(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)](#oh_arkui_alignmentruleoption_setbottom) | - | Sets the bottom alignment parameters.|
| [void OH_ArkUI_AlignmentRuleOption_SetCenterVertical(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)](#oh_arkui_alignmentruleoption_setcentervertical) | - | Sets the vertical center alignment parameters.|
| [void OH_ArkUI_AlignmentRuleOption_SetBiasHorizontal(ArkUI_AlignmentRuleOption* option, float horizontal)](#oh_arkui_alignmentruleoption_setbiashorizontal) | - | Sets the bias value of the component in the horizontal direction under the anchor constraints.|
| [void OH_ArkUI_AlignmentRuleOption_SetBiasVertical(ArkUI_AlignmentRuleOption* option, float vertical)](#oh_arkui_alignmentruleoption_setbiasvertical) | - | Sets the bias value of the component in the vertical direction under the anchor constraints.|
| [const char* OH_ArkUI_AlignmentRuleOption_GetStartId(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getstartid) | - | Obtains the ID in the left alignment parameters.|
| [ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetStartAlignment(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getstartalignment) | - | Obtains the alignment mode in left alignment parameters.|
| [const char* OH_ArkUI_AlignmentRuleOption_GetEndId(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getendid) | - | Obtains the alignment mode in the right alignment parameters.|
| [ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetEndAlignment(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getendalignment) | - | Obtains the alignment mode in the right alignment parameters.|
| [const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdHorizontal(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getcenteridhorizontal) | - | Obtains the alignment mode in horizontal center alignment parameters.|
| [ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentHorizontal(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getcenteralignmenthorizontal) | - | Obtains the alignment mode in horizontal center alignment parameters.|
| [const char* OH_ArkUI_AlignmentRuleOption_GetTopId(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_gettopid) | - | Obtains the alignment mode in top alignment parameters.|
| [ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetTopAlignment(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_gettopalignment) | - | Obtains the alignment mode in top alignment parameters.|
| [const char* OH_ArkUI_AlignmentRuleOption_GetBottomId(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getbottomid) | - | Obtains the alignment mode in bottom alignment parameters.|
| [ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetBottomAlignment(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getbottomalignment) | - | Obtains the alignment mode in bottom alignment parameters.|
| [const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdVertical(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getcenteridvertical) | - | Obtains the ID in vertical center alignment parameters.|
| [ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentVertical(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getcenteralignmentvertical) | - | Obtains the ID in vertical center alignment parameters.|
| [float OH_ArkUI_AlignmentRuleOption_GetBiasHorizontal(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getbiashorizontal) | - | Obtains the bias value in the horizontal direction.|
| [float OH_ArkUI_AlignmentRuleOption_GetBiasVertical(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getbiasvertical) | - | Obtains the bias value in the vertical direction.|
| [ArkUI_SwiperIndicator* OH_ArkUI_SwiperIndicator_Create(ArkUI_SwiperIndicatorType type)](#oh_arkui_swiperindicator_create) | - | Creates a navigation indicator for this **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_Dispose(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_dispose) | - | Disposes of the navigation indicator of this **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetStartPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setstartposition) | - | Sets the distance between a navigation indicator and the left edge of the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetStartPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getstartposition) | - | Obtains the distance between a navigation indicator and the left edge of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetTopPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_settopposition) | - | Sets the distance between the navigation indicator and the top edge of the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetTopPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_gettopposition) | - | Obtains the distance between the navigation indicator and the top edge of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetEndPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setendposition) | - | Sets the distance between the navigation indicator and the right edge of the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetEndPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getendposition) | - | Obtains the distance between a navigation indicator and the right edge of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetBottomPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setbottomposition) | - | Sets the distance between the navigation indicator and the bottom edge of the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetBottomPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getbottomposition) | - | Obtains the distance between the navigation indicator and the bottom edge of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator, int32_t ignoreSize)](#oh_arkui_swiperindicator_setignoresizeofbottom) | - | Sets whether the **OH_ArkUI_SwiperIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.|
| [int32_t OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getignoresizeofbottom) | - | Checks whether the **OH_ArkUI_SwiperIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.|
| [void OH_ArkUI_SwiperIndicator_SetItemWidth(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setitemwidth) | - | Sets the width of a dot-style navigation indicator for the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetItemWidth(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getitemwidth) | - | Obtains the width of a dot-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetItemHeight(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setitemheight) | - | Sets the height of a dot-style navigation indicator for the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetItemHeight(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getitemheight) | - | Obtains the height of a dot-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetSelectedItemWidth(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setselecteditemwidth) | - | Sets the width of the selected dot-style navigation indicator for the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetSelectedItemWidth(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselecteditemwidth) | - | Obtains the width of the selected dot-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetSelectedItemHeight(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setselecteditemheight) | - | Sets the height of the selected dot-style navigation indicator for the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetSelectedItemHeight(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselecteditemheight) | - | Obtains the height of the selected dot-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetMask(ArkUI_SwiperIndicator* indicator, int32_t mask)](#oh_arkui_swiperindicator_setmask) | - | Sets whether to enable the mask for a dot-style navigation indicator for the **Swiper** component.|
| [int32_t OH_ArkUI_SwiperIndicator_GetMask(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getmask) | - | Obtains whether the mask is enabled for a dot-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetColor(ArkUI_SwiperIndicator* indicator, uint32_t color)](#oh_arkui_swiperindicator_setcolor) | - | Sets the color of a dot-style navigation indicator for the **Swiper** component.|
| [uint32_t OH_ArkUI_SwiperIndicator_GetColor(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getcolor) | - | Obtains the color of a dot-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetSelectedColor(ArkUI_SwiperIndicator* indicator, uint32_t selectedColor)](#oh_arkui_swiperindicator_setselectedcolor) | - | Sets the color of the selected dot-style navigation indicator for the **Swiper** component.|
| [uint32_t OH_ArkUI_SwiperIndicator_GetSelectedColor(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselectedcolor) | - | Obtains the color of the selected dot-style navigation indicator of the **Swiper** component.|
| [int32_t OH_ArkUI_SwiperIndicator_SetMaxDisplayCount(ArkUI_SwiperIndicator* indicator, int32_t maxDisplayCount)](#oh_arkui_swiperindicator_setmaxdisplaycount) | - | Sets the maximum number of dots for the dot-style navigation indicator.|
| [int32_t OH_ArkUI_SwiperIndicator_GetMaxDisplayCount(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getmaxdisplaycount) | - | Obtains the maximum number of dots for the dot-style navigation indicator.|
| [ArkUI_SwiperDigitIndicator *OH_ArkUI_SwiperDigitIndicator_Create()](#oh_arkui_swiperdigitindicator_create) | - | Creates a digit-style navigation indicator for this **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_Destroy(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_destroy) | - | Disposes of the digit-style navigation indicator of this **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetStartPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setstartposition) | - | Sets the start position of the digit-style navigation indicator for the **Swiper** component. This determines the distance from the left edge of the **Swiper** component. For right-to-left scripts, this determines the distance from the right edge.|
| [float OH_ArkUI_SwiperDigitIndicator_GetStartPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getstartposition) | - | Obtains the start position of the digit-style navigation indicator for the **Swiper** component. This indicates the distance from the left edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the right edge.|
| [void OH_ArkUI_SwiperDigitIndicator_SetTopPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_settopposition) | - | Sets the distance from the digit-style navigation indicator to the top of the **Swiper** component.|
| [float OH_ArkUI_SwiperDigitIndicator_GetTopPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_gettopposition) | - | Obtains the distance from the digit-style navigation indicator to the top of the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetEndPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setendposition) | - | Sets the end position of the digit-style navigation indicator for the **Swiper** component. This determines the distance from the right edge of the **Swiper** component. For right-to-left scripts, this determines the distance from the left edge.|
| [float OH_ArkUI_SwiperDigitIndicator_GetEndPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getendposition) | - | Obtains the end position of the digit-style navigation indicator for the **Swiper** component. This indicates the distance from the right edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the left edge.|
| [void OH_ArkUI_SwiperDigitIndicator_SetBottomPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setbottomposition) | - | Sets the distance from the digit-style navigation indicator to the bottom of the **Swiper** component.|
| [float OH_ArkUI_SwiperDigitIndicator_GetBottomPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getbottomposition) | - | Obtains the distance from the digit-style navigation indicator to the bottom of the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t color)](#oh_arkui_swiperdigitindicator_setfontcolor) | - | Sets the font color of the digit-style navigation indicator for the **Swiper** component.|
| [uint32_t OH_ArkUI_SwiperDigitIndicator_GetFontColor(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontcolor) | - | Obtains the font color of the digit-style navigation indicator for the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t selectedColor)](#oh_arkui_swiperdigitindicator_setselectedfontcolor) | - | Sets the font color of the selected digit-style navigation indicator for the **Swiper** component.|
| [uint32_t OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontcolor) | - | Obtains the font color of the selected digit-style navigation indicator for the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)](#oh_arkui_swiperdigitindicator_setfontsize) | - | Sets the font size of the digit-style navigation indicator for the **Swiper** component.|
| [float OH_ArkUI_SwiperDigitIndicator_GetFontSize(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontsize) | - | Obtains the font size of the digit-style navigation indicator for the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)](#oh_arkui_swiperdigitindicator_setselectedfontsize) | - | Sets the font size of the selected digit-style navigation indicator for the **Swiper** component.|
| [float OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontsize) | - | Obtains the font size of the selected digit-style navigation indicator for the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetFontWeight(ArkUI_SwiperDigitIndicator *indicator, ArkUI_FontWeight fontWeight)](#oh_arkui_swiperdigitindicator_setfontweight) | - | Sets the font weight of the digit-style navigation indicator for the **Swiper** component.|
| [ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetFontWeight(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontweight) | - | Obtains the font weight of the digit-style navigation indicator for the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontWeight(ArkUI_SwiperDigitIndicator *indicator, ArkUI_FontWeight selectedFontWeight)](#oh_arkui_swiperdigitindicator_setselectedfontweight) | - | Sets the font weight of the selected digit-style navigation indicator for the **Swiper** component.|
| [ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetSelectedFontWeight(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontweight) | - | Obtains the font weight of the selected digit-style navigation indicator for the **Swiper** component.|
| [ArkUI_SwiperArrowStyle *OH_ArkUI_SwiperArrowStyle_Create()](#oh_arkui_swiperarrowstyle_create) | - | Creates an arrow style for the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_Destroy(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_destroy) | - | Disposes of the arrow of the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_SetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showBackground)](#oh_arkui_swiperarrowstyle_setshowbackground) | - | Sets whether to display the background of the arrow for the **Swiper** component.|
| [int32_t OH_ArkUI_SwiperArrowStyle_GetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getshowbackground) | - | Checks whether the background of the arrow is displayed for the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showSidebarMiddle)](#oh_arkui_swiperarrowstyle_setshowsidebarmiddle) | - | Sets the position of the arrow for the **Swiper** component.|
| [int32_t OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getshowsidebarmiddle) | - | Obtains the position of the arrow for the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_SetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle, float backgroundSize)](#oh_arkui_swiperarrowstyle_setbackgroundsize) | - | Sets the background size for the arrow of the **Swiper** component.|
| [float OH_ArkUI_SwiperArrowStyle_GetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getbackgroundsize) | - | Obtains the background size of the arrow of the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_SetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t backgroundColor)](#oh_arkui_swiperarrowstyle_setbackgroundcolor) | - | Sets the background color for the arrow of the **Swiper** component.|
| [uint32_t OH_ArkUI_SwiperArrowStyle_GetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getbackgroundcolor) | - | Obtains the background color for the arrow of the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_SetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle, float arrowSize)](#oh_arkui_swiperarrowstyle_setarrowsize) | - | Sets the size for the arrow of the **Swiper** component.|
| [float OH_ArkUI_SwiperArrowStyle_GetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getarrowsize) | - | Obtains the size of the arrow of the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_SetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t arrowColor)](#oh_arkui_swiperarrowstyle_setarrowcolor) | - | Sets the color for the arrow of the **Swiper** component.|
| [uint32_t OH_ArkUI_SwiperArrowStyle_GetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getarrowcolor) | - | Obtains the color of the arrow of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetSpace(ArkUI_SwiperIndicator* indicator, float space)](#oh_arkui_swiperindicator_setspace) | - | Sets the spacing between navigation points.|
| [float OH_ArkUI_SwiperIndicator_GetSpace(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getspace) | - | Obtains the spacing between navigation points.|
| [void OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator, int32_t ignoreSize)](#oh_arkui_swiperdigitindicator_setignoresizeofbottom) | - | Sets whether the **OH_ArkUI_SwiperDigitIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.|
| [int32_t OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getignoresizeofbottom) | - | Checks whether the **OH_ArkUI_SwiperDigitIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.|
| [ArkUI_ListItemSwipeActionItem* OH_ArkUI_ListItemSwipeActionItem_Create()](#oh_arkui_listitemswipeactionitem_create) | - | Creates a **ListItemSwipeActionItem** instance.|
| [void OH_ArkUI_ListItemSwipeActionItem_Dispose(ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionitem_dispose) | - | Disposes of a **ListItemSwipeActionItem** instance.|
| [void OH_ArkUI_ListItemSwipeActionItem_SetContent(ArkUI_ListItemSwipeActionItem* item, ArkUI_NodeHandle node)](#oh_arkui_listitemswipeactionitem_setcontent) | - | Sets the layout content for a **ListItemSwipeActionItem** instance.|
| [void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item, float distance)](#oh_arkui_listitemswipeactionitem_setactionareadistance) | - | Sets the swipe distance threshold for deleting the list item.|
| [float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionitem_getactionareadistance) | - | Obtains the swipe distance threshold for deleting the list item.|
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonenteractionarea) | - | Sets the callback invoked each time the list item enters the delete area.|
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData (ArkUI_ListItemSwipeActionItem* item,void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonenteractionareawithuserdata) | - | Sets the callback invoked each time the list item enters the delete area.|
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnAction(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonaction) | - | Sets the callback invoked when the list item is deleted while in the delete area.|
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData(ArkUI_ListItemSwipeActionItem* item,void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonactionwithuserdata) | - | Sets the callback invoked when the list item is deleted while in the delete area.|
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonexitactionarea) | - | Sets the callback invoked each time the list item exits the delete area.|
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData (ArkUI_ListItemSwipeActionItem* item,void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonexitactionareawithuserdata) | - | Sets the callback invoked each time the list item exits the delete area.|
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange (ArkUI_ListItemSwipeActionItem* item,void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState))](#oh_arkui_listitemswipeactionitem_setonstatechange) | - | Sets the callback invoked when the swipe state of the list item changes.|
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData (ArkUI_ListItemSwipeActionItem* item,void* userData, void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void* userData))](#oh_arkui_listitemswipeactionitem_setonstatechangewithuserdata) | - | Sets the callback invoked when the swipe state of the list item changes.|
| [ArkUI_ListItemSwipeActionOption* OH_ArkUI_ListItemSwipeActionOption_Create()](#oh_arkui_listitemswipeactionoption_create) | - | Creates a **ListItemSwipeActionOption** instance.|
| [void OH_ArkUI_ListItemSwipeActionOption_Dispose(ArkUI_ListItemSwipeActionOption* option)](#oh_arkui_listitemswipeactionoption_dispose) | - | Disposes of a **ListItemSwipeActionOption** instance.|
| [void OH_ArkUI_ListItemSwipeActionOption_SetStart(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionoption_setstart) | - | Sets the layout content for the left edge (for a vertical layout) or top edge (for a horizontal layout) of a **ListItemSwipeActionItem** instance.|
| [void OH_ArkUI_ListItemSwipeActionOption_SetEnd(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionoption_setend) | - | Sets the layout content for the right edge (for a vertical layout) or bottom edge (for a horizontal layout) of a **ListItemSwipeActionItem** instance.|
| [void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeEdgeEffect edgeEffect)](#oh_arkui_listitemswipeactionoption_setedgeeffect) | - | Sets the edge effect used when the boundary of the scrolling area is reached.|
| [int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect(ArkUI_ListItemSwipeActionOption* option)](#oh_arkui_listitemswipeactionoption_getedgeeffect) | - | Obtains the edge effect used when the boundary of the scrolling area is reached.|
| [void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange(ArkUI_ListItemSwipeActionOption* option, void (\*callback)(float offset))](#oh_arkui_listitemswipeactionoption_setonoffsetchange) | - | Sets the callback invoked when the scroll offset changes.|
| [void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData (ArkUI_ListItemSwipeActionOption* option, void* userData, void (\*callback)(float offset, void* userData))](#oh_arkui_listitemswipeactionoption_setonoffsetchangewithuserdata) | - | Sets the callback invoked when the scroll offset changes.|
| [int32_t OH_ArkUI_ListItemSwipeAction_Expand(ArkUI_NodeHandle node, ArkUI_ListItemSwipeActionDirection direction)](#oh_arkui_listitemswipeaction_expand) | - |  Expands the swipe action menu for the specified list item.|
| [int32_t OH_ArkUI_ListItemSwipeAction_Collapse(ArkUI_NodeHandle node)](#oh_arkui_listitemswipeaction_collapse) | - |  Collapses the swipe action menu for the specified list item.|
| [ArkUI_AccessibilityState* OH_ArkUI_AccessibilityState_Create(void)](#oh_arkui_accessibilitystate_create) | - | Creates an accessibility state.|
| [void OH_ArkUI_AccessibilityState_Dispose(ArkUI_AccessibilityState* state)](#oh_arkui_accessibilitystate_dispose) | - | Disposes of the pointer to an accessibility state.|
| [void OH_ArkUI_AccessibilityState_SetDisabled(ArkUI_AccessibilityState* state, int32_t isDisabled)](#oh_arkui_accessibilitystate_setdisabled) | - | Sets whether an accessibility state is disabled.|
| [int32_t OH_ArkUI_AccessibilityState_IsDisabled(ArkUI_AccessibilityState* state)](#oh_arkui_accessibilitystate_isdisabled) | - | Obtains whether an accessibility state is disabled.|
| [void OH_ArkUI_AccessibilityState_SetSelected(ArkUI_AccessibilityState* state, int32_t isSelected)](#oh_arkui_accessibilitystate_setselected) | - | Sets whether an accessibility state is selected.|
| [int32_t OH_ArkUI_AccessibilityState_IsSelected(ArkUI_AccessibilityState* state)](#oh_arkui_accessibilitystate_isselected) | - | Obtains whether an accessibility state is selected.|
| [void OH_ArkUI_AccessibilityState_SetCheckedState(ArkUI_AccessibilityState* state, int32_t checkedState)](#oh_arkui_accessibilitystate_setcheckedstate) | - | Sets the check box state of an accessibility state.|
| [int32_t OH_ArkUI_AccessibilityState_GetCheckedState(ArkUI_AccessibilityState* state)](#oh_arkui_accessibilitystate_getcheckedstate) | - | Obtains the check box state of an accessibility state.|
| [ArkUI_AccessibilityValue* OH_ArkUI_AccessibilityValue_Create(void)](#oh_arkui_accessibilityvalue_create) | - | Creates an **AccessibilityValue** instance.|
| [void OH_ArkUI_AccessibilityValue_Dispose(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_dispose) | - | Disposes of the pointer to an **AccessibilityValue** instance.|
| [void OH_ArkUI_AccessibilityValue_SetMin(ArkUI_AccessibilityValue* value, int32_t min)](#oh_arkui_accessibilityvalue_setmin) | - | Sets the minimum accessibility value.|
| [int32_t OH_ArkUI_AccessibilityValue_GetMin(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getmin) | - | Obtains the minimum accessibility value.|
| [void OH_ArkUI_AccessibilityValue_SetMax(ArkUI_AccessibilityValue* value, int32_t max)](#oh_arkui_accessibilityvalue_setmax) | - | Sets the maximum accessibility value.|
| [int32_t OH_ArkUI_AccessibilityValue_GetMax(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getmax) | - | Obtains the maximum accessibility value.|
| [void OH_ArkUI_AccessibilityValue_SetCurrent(ArkUI_AccessibilityValue* value, int32_t current)](#oh_arkui_accessibilityvalue_setcurrent) | - | Sets the current accessibility value.|
| [int32_t OH_ArkUI_AccessibilityValue_GetCurrent(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getcurrent) | - | Obtains the current accessibility value.|
| [void OH_ArkUI_AccessibilityValue_SetRangeMin(ArkUI_AccessibilityValue* value, int32_t rangeMin)](#oh_arkui_accessibilityvalue_setrangemin) | - | Sets the minimum value for accessibility information of the range-based component.|
| [int32_t OH_ArkUI_AccessibilityValue_GetRangeMin(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getrangemin) | - | Obtains the minimum value for accessibility information of the range-based component.|
| [void OH_ArkUI_AccessibilityValue_SetRangeMax(ArkUI_AccessibilityValue* value, int32_t rangeMax)](#oh_arkui_accessibilityvalue_setrangemax) | - | Sets the maximum value for accessibility information of the range-based component.|
| [int32_t OH_ArkUI_AccessibilityValue_GetRangeMax(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getrangemax) | - | Obtains the maximum value for accessibility information of the range-based component.|
| [void OH_ArkUI_AccessibilityValue_SetRangeCurrent(ArkUI_AccessibilityValue* value, int32_t rangeCurrent)](#oh_arkui_accessibilityvalue_setrangecurrent) | - | Sets the current value for accessibility information of the range-based component.|
| [int32_t OH_ArkUI_AccessibilityValue_GetRangeCurrent(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getrangecurrent) | - | Obtains the current value for accessibility information of the range-based component.|
| [void OH_ArkUI_AccessibilityValue_SetText(ArkUI_AccessibilityValue* value, const char* text)](#oh_arkui_accessibilityvalue_settext) | - | Sets the text description of an **AccessibilityValue** instance.|
| [const char* OH_ArkUI_AccessibilityValue_GetText(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_gettext) | - | Obtains the text description of an **AccessibilityValue** instance.|
| [ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString(char* src)](#oh_arkui_imageanimatorframeinfo_createfromstring) | - | Creates an image frame information object based on an image path, with the image format being SVG, PNG, or JPG.|
| [ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor(ArkUI_DrawableDescriptor* drawable)](#oh_arkui_imageanimatorframeinfo_createfromdrawabledescriptor) | - | Creates an image frame information object based on a **DrawableDescriptor** object, with the image format being Resource or PixelMap.|
| [void OH_ArkUI_ImageAnimatorFrameInfo_Dispose(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_dispose) | - | Disposes of the pointer to an image frame information object.|
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t width)](#oh_arkui_imageanimatorframeinfo_setwidth) | - | Sets the image width.|
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getwidth) | - | Obtains the image width.|
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t height)](#oh_arkui_imageanimatorframeinfo_setheight) | - | Sets the image height.|
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getheight) | - | Obtains the image height.|
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t top)](#oh_arkui_imageanimatorframeinfo_settop) | - | Sets the vertical coordinate of an image relative to the upper left corner of the component.|
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_gettop) | - | Obtains the vertical coordinate of an image relative to the upper left corner of the component.|
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t left)](#oh_arkui_imageanimatorframeinfo_setleft) | - | Sets the horizontal coordinate of an image relative to the upper left corner of the component.|
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getleft) | - | Obtains the horizontal coordinate of an image relative to the upper left corner of the component.|
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t duration)](#oh_arkui_imageanimatorframeinfo_setduration) | - | Sets the playback duration of an image.|
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getduration) | - | Obtains the playback duration of an image.|
| [ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()](#oh_arkui_listchildrenmainsizeoption_create) | - | Creates a **ListChildrenMainSize** instance.|
| [void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_dispose) | - | Disposes of a **ListChildrenMainSize** instance.|
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)](#oh_arkui_listchildrenmainsizeoption_setdefaultmainsize) | - | Sets the default size in a **ListChildrenMainSize** instance.|
| [float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_getdefaultmainsize) | - | Obtains the default size in a **ListChildrenMainSize** instance.|
| [void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)](#oh_arkui_listchildrenmainsizeoption_resize) | - | Resets the array size in a **ListChildrenMainSize** instance.|
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)](#oh_arkui_listchildrenmainsizeoption_splice) | - | Changes the content of a **ChildrenMainSizeOption** array.|
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)](#oh_arkui_listchildrenmainsizeoption_updatesize) | - | Updates the values in a **ChildrenMainSizeOption** array of a **List** component.|
| [float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)](#oh_arkui_listchildrenmainsizeoption_getmainsize) | - | Obtains the value of the **ChildrenMainSizeOption** array of the **List** component.|
| [ArkUI_CustomSpanMeasureInfo* OH_ArkUI_CustomSpanMeasureInfo_Create(void)](#oh_arkui_customspanmeasureinfo_create) | - | Creates measurement information for this custom span.|
| [void OH_ArkUI_CustomSpanMeasureInfo_Dispose(ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_customspanmeasureinfo_dispose) | - | Disposes of measurement information of a custom span.|
| [float OH_ArkUI_CustomSpanMeasureInfo_GetFontSize(ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_customspanmeasureinfo_getfontsize) | - | Obtains the font size of the parent text node of a custom span.|
| [ArkUI_CustomSpanMetrics* OH_ArkUI_CustomSpanMetrics_Create(void)](#oh_arkui_customspanmetrics_create) | - | Creates measurement metrics for this custom span.|
| [void OH_ArkUI_CustomSpanMetrics_Dispose(ArkUI_CustomSpanMetrics* metrics)](#oh_arkui_customspanmetrics_dispose) | - | Disposes of measurement metrics of this custom span.|
| [int32_t OH_ArkUI_CustomSpanMetrics_SetWidth(ArkUI_CustomSpanMetrics* metrics, float width)](#oh_arkui_customspanmetrics_setwidth) | - | Sets the width for a custom span.|
| [int32_t OH_ArkUI_CustomSpanMetrics_SetHeight(ArkUI_CustomSpanMetrics* metrics, float height)](#oh_arkui_customspanmetrics_setheight) | - | Sets the height for a custom span.|
| [ArkUI_CustomSpanDrawInfo* OH_ArkUI_CustomSpanDrawInfo_Create(void)](#oh_arkui_customspandrawinfo_create) | - | Creates drawing information for this custom span.|
| [void OH_ArkUI_CustomSpanDrawInfo_Dispose(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_dispose) | - | Disposes of drawing information for this custom span.|
| [float OH_ArkUI_CustomSpanDrawInfo_GetXOffset(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getxoffset) | - | Obtains the x-axis offset of the custom span relative to the mounted component.|
| [float OH_ArkUI_CustomSpanDrawInfo_GetLineTop(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getlinetop) | - | Obtains the top margin of the custom span relative to the mounted component.|
| [float OH_ArkUI_CustomSpanDrawInfo_GetLineBottom(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getlinebottom) | - | Obtains the bottom margin of the custom span relative to the mounted component.|
| [float OH_ArkUI_CustomSpanDrawInfo_GetBaseline(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getbaseline) | - | Obtains the baseline offset of the custom span relative to the mounted component.|
| [void OH_ArkUI_CustomProperty_Destroy(ArkUI_CustomProperty* handle)](#oh_arkui_customproperty_destroy) | - | Destroys a **CustomProperty** instance.|
| [const char* OH_ArkUI_CustomProperty_GetStringValue(ArkUI_CustomProperty* handle)](#oh_arkui_customproperty_getstringvalue) | - | Obtains the value of a custom property.|
| [const char* OH_ArkUI_HostWindowInfo_GetName(ArkUI_HostWindowInfo* info)](#oh_arkui_hostwindowinfo_getname) | - | Obtains the window name from a **HostWindowInfo** object.|
| [void OH_ArkUI_HostWindowInfo_Destroy(ArkUI_HostWindowInfo* info)](#oh_arkui_hostwindowinfo_destroy) | - | Destroys a **HostWindowInfo** object.|
| [void OH_ArkUI_ActiveChildrenInfo_Destroy(ArkUI_ActiveChildrenInfo* handle)](#oh_arkui_activechildreninfo_destroy) | - | Destroys an **ActiveChildrenInfo** instance.|
| [ArkUI_NodeHandle OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex(ArkUI_ActiveChildrenInfo* handle, int32_t index)](#oh_arkui_activechildreninfo_getnodebyindex) | - | Obtains the child node at the specified index in the specified **ActiveChildrenInfo** instance.|
| [int32_t OH_ArkUI_ActiveChildrenInfo_GetCount(ArkUI_ActiveChildrenInfo* handle)](#oh_arkui_activechildreninfo_getcount) | - | Obtains the number of nodes in the specified **ActiveChildrenInfo** instance.|
| [ArkUI_ProgressLinearStyleOption* OH_ArkUI_ProgressLinearStyleOption_Create(void)](#oh_arkui_progresslinearstyleoption_create) | - | Creates a **ProgressLinearStyleOption** instance.|
| [void OH_ArkUI_ProgressLinearStyleOption_Destroy(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_destroy) | - | Destroys a **ProgressLinearStyleOption** instance.|
| [void OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)](#oh_arkui_progresslinearstyleoption_setsmootheffectenabled) | - | Sets whether to enable the smooth progress effect.|
| [void OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)](#oh_arkui_progresslinearstyleoption_setscaneffectenabled) | - | Sets whether to enable the scan effect.|
| [void OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth(ArkUI_ProgressLinearStyleOption* option, float strokeWidth)](#oh_arkui_progresslinearstyleoption_setstrokewidth) | - | Sets the width of the progress indicator.|
| [void OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius(ArkUI_ProgressLinearStyleOption* option, float strokeRadius)](#oh_arkui_progresslinearstyleoption_setstrokeradius) | - | Sets the corner radius of the progress indicator.|
| [bool OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getsmootheffectenabled) | - | Obtains the enabled status of the smooth progress effect.|
| [bool OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getscaneffectenabled) | - | Obtains the enabled status of the scan effect.|
| [float OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getstrokewidth) | - | Obtains the stroke width of the progress indicator.|
| [float OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getstrokeradius) | - | Obtains the corner radius of the progress indicator.|
| [ArkUI_SnapshotOptions* OH_ArkUI_CreateSnapshotOptions()](#oh_arkui_createsnapshotoptions) | - | Creates a snapshot options object, which must be released using [OH_ArkUI_DestroySnapshotOptions()](#oh_arkui_destroysnapshotoptions) when no longer in use.|
| [void OH_ArkUI_DestroySnapshotOptions(ArkUI_SnapshotOptions* snapshotOptions)](#oh_arkui_destroysnapshotoptions) | - | Destroys a snapshot options object.|
| [int32_t OH_ArkUI_SnapshotOptions_SetScale(ArkUI_SnapshotOptions* snapshotOptions, float scale)](#oh_arkui_snapshotoptions_setscale) | - | Sets the scale property in the snapshot options.|
| [int32_t OH_ArkUI_SnapshotOptions_SetColorMode(ArkUI_SnapshotOptions* snapshotOptions, int32_t colorSpace, bool isAuto)](#oh_arkui_snapshotoptions_setcolormode) | - | Sets the color space in the screenshot option.|
| [int32_t OH_ArkUI_SnapshotOptions_SetDynamicRangeMode(ArkUI_SnapshotOptions* snapshotOptions, int32_t dynamicRangeMode, bool isAuto)](#oh_arkui_snapshotoptions_setdynamicrangemode) | - | Sets the dynamic range mode in the screenshot option.|
| [ArkUI_CrossLanguageOption* OH_ArkUI_CrossLanguageOption_Create(void)](#oh_arkui_crosslanguageoption_create) | - | Creates an instance of the cross-language configuration option.|
| [void OH_ArkUI_CrossLanguageOption_Destroy(ArkUI_CrossLanguageOption* option)](#oh_arkui_crosslanguageoption_destroy) | - | Destroys an instance of the cross-language configuration option.|
| [void OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus(ArkUI_CrossLanguageOption* option, bool enabled)](#oh_arkui_crosslanguageoption_setattributesettingstatus) | - | Sets whether cross-language attribute setting is allowed in the configuration option.|
| [bool OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus(ArkUI_CrossLanguageOption* option)](#oh_arkui_crosslanguageoption_getattributesettingstatus) | - | Checks whether cross-language attribute setting is allowed in the configuration option.|
| [ArkUI_VisibleAreaEventOptions* OH_ArkUI_VisibleAreaEventOptions_Create()](#oh_arkui_visibleareaeventoptions_create) | - | Creates an instance of visible area change event parameters.|
| [void OH_ArkUI_VisibleAreaEventOptions_Dispose(ArkUI_VisibleAreaEventOptions* option)](#oh_arkui_visibleareaeventoptions_dispose) | - | Disposes of an instance of visible area change event parameters.|
| [int32_t OH_ArkUI_VisibleAreaEventOptions_SetRatios(ArkUI_VisibleAreaEventOptions* option, float* value, int32_t size)](#oh_arkui_visibleareaeventoptions_setratios) | - | Sets the threshold ratios for visible area changes.|
| [int32_t OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval(ArkUI_VisibleAreaEventOptions *option, int32_t value)](#oh_arkui_visibleareaeventoptions_setexpectedupdateinterval) | - | Sets the expected update interval for visible area changes.  |
| [int32_t OH_ArkUI_VisibleAreaEventOptions_SetMeasureFromViewport(ArkUI_VisibleAreaEventOptions *option, bool measureFromViewport)](#oh_arkui_visibleareaeventoptions_setmeasurefromviewport) | - | Sets the visible area calculation mode.|
| [int32_t OH_ArkUI_VisibleAreaEventOptions_GetRatios(ArkUI_VisibleAreaEventOptions* option, float* value, int32_t* size)](#oh_arkui_visibleareaeventoptions_getratios) | - | Obtains the threshold ratios for visible area changes.|
| [int32_t OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval(ArkUI_VisibleAreaEventOptions* option)](#oh_arkui_visibleareaeventoptions_getexpectedupdateinterval) | - | Obtains the expected update interval for visible area changes.|
| [bool OH_ArkUI_VisibleAreaEventOptions_GetMeasureFromViewport(ArkUI_VisibleAreaEventOptions* option)](#oh_arkui_visibleareaeventoptions_getmeasurefromviewport) | - | Obtains the visible area calculation mode.|
| [ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)](#oh_arkui_textpickerrangecontentarray_create) | - | Creates a **TextPickerRangeContent** array object.|
| [void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)](#oh_arkui_textpickerrangecontentarray_seticonatindex) | - | Sets the icon data at the specified position in the **TextPickerRangeContent** array.|
| [void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textpickerrangecontentarray_settextatindex) | - | Sets the text data at the specified position in the **TextPickerRangeContent** array.|
| [void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)](#oh_arkui_textpickerrangecontentarray_destroy) | - | Destroys a **TextPickerRangeContent** array object.|
| [ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)](#oh_arkui_textcascadepickerrangecontentarray_create) | - | Creates a **TextCascadePickerRangeContent** array object.|
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex (ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_settextatindex) | - | Sets the text data at the specified position in the **TextCascadePickerRangeContent** array.|
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex (ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_setchildatindex) | - | Sets the child data at the specified position in the **TextCascadePickerRangeContent** array.|
| [void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy (ArkUI_TextCascadePickerRangeContentArray* handle)](#oh_arkui_textcascadepickerrangecontentarray_destroy) | - | Destroys a **TextCascadePickerRangeContent** array object.|
| [ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()](#oh_arkui_embeddedcomponentoption_create) | - | Creates an **EmbeddedComponent** option object.|
| [void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)](#oh_arkui_embeddedcomponentoption_dispose) | - | Disposes of an **EmbeddedComponent** option object.|
| [void OH_ArkUI_EmbeddedComponentOption_SetOnError (ArkUI_EmbeddedComponentOption* option, void (\*callback)(int32_t code, const char* name, const char* message))](#oh_arkui_embeddedcomponentoption_setonerror) | - | Sets the **onError** callback for the **EmbeddedComponent** component. This callback is triggered when an error occurs during the running of the **EmbeddedComponent** component.|
| [void OH_ArkUI_EmbeddedComponentOption_SetOnTerminated (ArkUI_EmbeddedComponentOption* option, void (\*callback)(int32_t code, AbilityBase_Want* want))](#oh_arkui_embeddedcomponentoption_setonterminated) | - | Sets the **onTerminated** callback for the **EmbeddedComponent** component. This callback is triggered when the **EmbeddedComponent** component exits properly.|
| [ArkUI_PositionEdges* OH_ArkUI_PositionEdges_Create()](#oh_arkui_positionedges_create) | - | Creates a **PositionEdges** object.|
| [ArkUI_PositionEdges* OH_ArkUI_PositionEdges_Copy(const ArkUI_PositionEdges* edges)](#oh_arkui_positionedges_copy) | - | Deeply copies a **PositionEdges** attribute object.|
| [void OH_ArkUI_PositionEdges_Dispose(ArkUI_PositionEdges* edges)](#oh_arkui_positionedges_dispose) | - | Disposes of the **PositionEdges** object.|
| [void OH_ArkUI_PositionEdges_SetTop(ArkUI_PositionEdges* edges, float value)](#oh_arkui_positionedges_settop) | - | Sets the value of the **PositionEdges** object in the top direction.|
| [int32_t OH_ArkUI_PositionEdges_GetTop(ArkUI_PositionEdges* edges, float* value)](#oh_arkui_positionedges_gettop) | - | Obtains the value of the **PositionEdges** object in the top direction.|
| [void OH_ArkUI_PositionEdges_SetLeft(ArkUI_PositionEdges* edges, float value)](#oh_arkui_positionedges_setleft) | - | Sets the value of the **PositionEdges** object in the left direction.|
| [int32_t OH_ArkUI_PositionEdges_GetLeft(ArkUI_PositionEdges* edges, float* value)](#oh_arkui_positionedges_getleft) | - | Obtains the value of the **PositionEdges** object in the left direction.|
| [void OH_ArkUI_PositionEdges_SetBottom(ArkUI_PositionEdges* edges, float value)](#oh_arkui_positionedges_setbottom) | - | Obtains the value of the **PositionEdges** object in the bottom direction.|
| [int32_t OH_ArkUI_PositionEdges_GetBottom(ArkUI_PositionEdges* edges, float* value)](#oh_arkui_positionedges_getbottom) | - | Obtains the value of the **PositionEdges** object in the bottom direction.|
| [void OH_ArkUI_PositionEdges_SetRight(ArkUI_PositionEdges* edges, float value)](#oh_arkui_positionedges_setright) | - | Sets the value of the **PositionEdges** object in the right direction.|
| [int32_t OH_ArkUI_PositionEdges_GetRight(ArkUI_PositionEdges* edges, float* value)](#oh_arkui_positionedges_getright) | - | Obtains the value of the **PositionEdges** object in the right direction.|
| [ArkUI_PixelRoundPolicy* OH_ArkUI_PixelRoundPolicy_Create()](#oh_arkui_pixelroundpolicy_create) | - | Creates a **PixelRoundPolicy** attribute object.|
| [void OH_ArkUI_PixelRoundPolicy_Dispose(ArkUI_PixelRoundPolicy* policy)](#oh_arkui_pixelroundpolicy_dispose) | - | Disposes of the **PixelRoundPolicy** object.|
| [void OH_ArkUI_PixelRoundPolicy_SetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)](#oh_arkui_pixelroundpolicy_settop) | - | Sets the top edge pixel rounding policy for the **PixelRoundPolicy** object.|
| [int32_t OH_ArkUI_PixelRoundPolicy_GetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)](#oh_arkui_pixelroundpolicy_gettop) | - | Obtains the top edge pixel rounding policy from the **PixelRoundPolicy** object.|
| [void OH_ArkUI_PixelRoundPolicy_SetStart(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)](#oh_arkui_pixelroundpolicy_setstart) | - | Sets the start edge pixel rounding policy for the **PixelRoundPolicy** object.|
| [int32_t OH_ArkUI_PixelRoundPolicy_GetStart(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)](#oh_arkui_pixelroundpolicy_getstart) | - | Obtains the start edge pixel rounding policy from the **PixelRoundPolicy** object. |
| [void OH_ArkUI_PixelRoundPolicy_SetBottom(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)](#oh_arkui_pixelroundpolicy_setbottom) | - | Sets the bottom edge pixel rounding policy for the **PixelRoundPolicy** object.|
| [int32_t OH_ArkUI_PixelRoundPolicy_GetBottom(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)](#oh_arkui_pixelroundpolicy_getbottom) | - | Obtains the bottom edge pixel rounding policy from the **PixelRoundPolicy** object.|
| [void OH_ArkUI_PixelRoundPolicy_SetEnd(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)](#oh_arkui_pixelroundpolicy_setend) | - | Sets the end edge pixel rounding policy for the **PixelRoundPolicy** object.|
| [int32_t OH_ArkUI_PixelRoundPolicy_GetEnd(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)](#oh_arkui_pixelroundpolicy_getend) | - | Obtains the end edge pixel rounding policy from the **PixelRoundPolicy** object.|
| [ArkUI_ContentTransitionEffect* OH_ArkUI_ContentTransitionEffect_Create(int32_t type)](#oh_arkui_contenttransitioneffect_create) | - | Creates a **ContentTransitionEffect** attribute object.|
| [ArkUI_GridLayoutOptions* OH_ArkUI_GridLayoutOptions_Create()](#oh_arkui_gridlayoutoptions_create) | - | Creates **Grid** layout options.|
| [void OH_ArkUI_GridLayoutOptions_Dispose(ArkUI_GridLayoutOptions* option)](#oh_arkui_gridlayoutoptions_dispose) | - | Disposes **Grid** layout options.|
| [int32_t OH_ArkUI_GridLayoutOptions_SetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t size)](#oh_arkui_gridlayoutoptions_setirregularindexes) | - | Sets the irregular grid item index array for the grid layout.|
| [int32_t OH_ArkUI_GridLayoutOptions_GetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t* size)](#oh_arkui_gridlayoutoptions_getirregularindexes) | - | Obtains the irregular grid item index array for the grid layout. When **OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback** is not set, the grid item specified in this parameter occupies an entire row of the grid that scrolls vertically or an entire column of the grid that scrolls horizontally.|
| [void OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemSize(\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_gridlayoutoptions_registergetirregularsizebyindexcallback) | - | Registers a callback to obtain the row and column span for the grid item at the specified index.|
| [void OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemRect (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_gridlayoutoptions_registergetrectbyindexcallback) | - | Registers a callback to obtain the starting row, starting column, row span, and column span for the grid item at the specified index.|
| [ArkUI_SelectionOptions OH_ArkUI_SelectionOptions_Create()](#oh_arkui_selectionoptions_create) | - | Creates a selection option.|
| [void OH_ArkUI_SelectionOptions_Dispose(ArkUI_SelectionOptions* options)](#oh_arkui_selectionoptions_dispose) | - | Releases the selection option object.|
| [void OH_ArkUI_SelectionOptions_SetMenuPolicy(ArkUI_SelectionOptions* options, ArkUI_MenuPolicy menuPolicy)](#oh_arkui_selectionoptions_setmenupolicy) | - | Sets the menu pop-up policy for selecting options.|
| [ArkUI_MenuPolicy OH_ArkUI_SelectionOptions_GetMenuPolicy(ArkUI_SelectionOptions* options)](#oh_arkui_selectionoptions_getmenupolicy) | - | Obtains the menu pop-up policy for selecting options.|
| [ArkUI_TextContentBaseController* OH_ArkUI_TextContentBaseController_Create()](#oh_arkui_textcontentbasecontroller_create) | - | Creates a basic controller object for text content.|
| [void OH_ArkUI_TextContentBaseController_Dispose(ArkUI_TextContentBaseController* controller)](#oh_arkui_textcontentbasecontroller_dispose) | - | Destroys a basic controller object for text content.|
| [void OH_ArkUI_TextContentBaseController_DeleteBackward(ArkUI_TextContentBaseController* controller)](#oh_arkui_textcontentbasecontroller_deletebackward) | - | Deletes the character before the cursor in editing state; deletes the last character of the text box component in other states.|
| [void OH_ArkUI_TextContentBaseController_ScrollToVisible(ArkUI_TextContentBaseController* controller, int32_t start, int32_t end)](#oh_arkui_textcontentbasecontroller_scrolltovisible) | - | Pass the start and end indexes to the bound text box component, and scroll the text within the range to the visible area.|
| [ArkUI_TextMenuItem* OH_ArkUI_TextMenuItem_Create()](#oh_arkui_textmenuitem_create) | - | Creates a text menu item object.|
| [void OH_ArkUI_TextMenuItem_Dispose(ArkUI_TextMenuItem* textMenuItem)](#oh_arkui_textmenuitem_dispose) | - | Releases a text menu item object.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetContent(ArkUI_TextMenuItem* item, const char* content)](#oh_arkui_textmenuitem_setcontent) | - | Sets the title of a text menu item.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetContent(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textmenuitem_getcontent) | - | Obtains the title of a text menu item.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetIcon(ArkUI_TextMenuItem* item, const char* icon)](#oh_arkui_textmenuitem_seticon) | - | Sets the icon path of a text menu item.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetIcon(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textmenuitem_geticon) | - | Obtains the icon path of a text menu item.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetLabelInfo(ArkUI_TextMenuItem* item, const char* labelInfo)](#oh_arkui_textmenuitem_setlabelinfo) | - | Sets the shortcut hint for a text menu item, for example, the shortcut hint for the **Copy** menu item can be set to **Ctrl+C**.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetLabelInfo(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textmenuitem_getlabelinfo) | - | Obtains the shortcut hint for a text menu item, for example, the shortcut hint for the **Copy** menu item is typically **Ctrl+C**.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetId(ArkUI_TextMenuItem* item, int32_t id)](#oh_arkui_textmenuitem_setid) | - | Sets the ID of a text menu item.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetId(const ArkUI_TextMenuItem* item, int32_t* id)](#oh_arkui_textmenuitem_getid) | - | Obtains the ID of a text menu item.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_GetSize(ArkUI_TextMenuItemArray* items, int32_t* size)](#oh_arkui_textmenuitemarray_getsize) | - | Obtains the size of the text menu item array.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_GetItem(ArkUI_TextMenuItemArray* items, int32_t index, ArkUI_TextMenuItem** item)](#oh_arkui_textmenuitemarray_getitem) | - | Obtains the text menu item at a specified index from the text menu item array.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Insert(ArkUI_TextMenuItemArray* items, ArkUI_TextMenuItem* item, int32_t index)](#oh_arkui_textmenuitemarray_insert) | - | Inserts a text menu item at a specified index into the text menu item array.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Erase(ArkUI_TextMenuItemArray* items, int32_t index)](#oh_arkui_textmenuitemarray_erase) | - | Deletes the text menu item at a specified index from the text menu item array.|
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Clear(ArkUI_TextMenuItemArray* items)](#oh_arkui_textmenuitemarray_clear) | - | Clears all text menu items in the text menu item array.|
| [ArkUI_TextEditMenuOptions* OH_ArkUI_TextEditMenuOptions_Create()](#oh_arkui_texteditmenuoptions_create) | - | Creates a text menu extension object.|
| [void OH_ArkUI_TextEditMenuOptions_Dispose(ArkUI_TextEditMenuOptions* editMenuOptions)](#oh_arkui_texteditmenuoptions_dispose) | - | Releases a text menu extension object.|
| [typedef void (\*ArkUI_TextCreateMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)](#arkui_textcreatemenucallback) | ArkUI_TextCreateMenuCallback | Callback for the text menu creation event. This callback is triggered when a text menu is created, allowing you to set menu data in it.|
| [typedef void (\*ArkUI_TextPrepareMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)](#arkui_textpreparemenucallback) | ArkUI_TextPrepareMenuCallback | Callback for the text menu preparation event. This callback is called when the text selection area changes and before the menu is displayed, allowing you to set menu data in it.|
| [typedef bool (\*ArkUI_TextMenuItemClickCallback)(const ArkUI_TextMenuItem* item,int32_t start, int32_t end, void* userData)](#arkui_textmenuitemclickcallback) | ArkUI_TextMenuItemClickCallback | Callback for the text menu item click event. This callback is called when a menu item is clicked. You can intercept the default processing behavior in this callback.|
| [ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnCreateMenuCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextCreateMenuCallback cb)](#oh_arkui_texteditmenuoptions_registeroncreatemenucallback) | - | Registers the callback for creating text menus.|
| [ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnPrepareMenuCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextPrepareMenuCallback cb)](#oh_arkui_texteditmenuoptions_registeronpreparemenucallback) | - | Registers the callback for preparing text menus.|
| [ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnMenuItemClickCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextMenuItemClickCallback cb)](#oh_arkui_texteditmenuoptions_registeronmenuitemclickcallback) | - | Registers the callback for text menu item clicks.|
| [ArkUI_TextSelectionMenuOptions* OH_ArkUI_TextSelectionMenuOptions_Create()](#oh_arkui_textselectionmenuoptions_create) | - | Creates a custom text selection menu object.|
| [void OH_ArkUI_TextSelectionMenuOptions_Dispose(ArkUI_TextSelectionMenuOptions* selectionMenuOptions)](#oh_arkui_textselectionmenuoptions_dispose) | - | Releases a custom text selection menu object.|
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetSpanType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextSpanType textSpanType)](#oh_arkui_textselectionmenuoptions_setspantype) | - | Sets the text recognition type of a custom text selection menu.|
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetSpanType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextSpanType* spanType)](#oh_arkui_textselectionmenuoptions_getspantype) | - | Obtains the text recognition type of a custom text selection menu.|
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetContentNode(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_NodeHandle node)](#oh_arkui_textselectionmenuoptions_setcontentnode) | - | Sets the content node of a custom text selection menu.|
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetContentNode(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_NodeHandle* node)](#oh_arkui_textselectionmenuoptions_getcontentnode) | - | Obtains the content node of a custom text selection menu.|
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetResponseType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextResponseType responseType)](#oh_arkui_textselectionmenuoptions_setresponsetype) | - | Sets the response type of a custom text selection menu.|
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetResponseType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextResponseType* responseType)](#oh_arkui_textselectionmenuoptions_getresponsetype) | - | Obtains the response type of a custom text selection menu.|
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuShowCallback(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, void* userData, void (\*callback)(int32_t start, int32_t end, void* userData))](#oh_arkui_textselectionmenuoptions_registeronmenushowcallback) | - | Registers the callback for the event of showing a custom text selection menu.|
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuHideCallback(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, void* userData, void (\*callback)(int32_t start, int32_t end, void* userData))](#oh_arkui_textselectionmenuoptions_registeronmenuhidecallback) | - | Registers the callback for the event of hiding a custom text selection menu.|
| [ArkUI_TextMarqueeOptions* OH_ArkUI_TextMarqueeOptions_Create()](#oh_arkui_textmarqueeoptions_create) | - | Creates a text marquee option.|
| [void OH_ArkUI_TextMarqueeOptions_Dispose(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_dispose) | - | Destroys the pointer to a text marquee option.|
| [void OH_ArkUI_TextMarqueeOptions_SetStart(ArkUI_TextMarqueeOptions* option, bool start)](#oh_arkui_textmarqueeoptions_setstart) | - | Sets whether to play text marquee options.|
| [bool OH_ArkUI_TextMarqueeOptions_GetStart(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstart) | - | Obtains whether to play text marquee options.|
| [void OH_ArkUI_TextMarqueeOptions_SetStep(ArkUI_TextMarqueeOptions* option, float step)](#oh_arkui_textmarqueeoptions_setstep) | - | Sets the step of text marquee options.|
| [float OH_ArkUI_TextMarqueeOptions_GetStep(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstep) | - | Obtains the step of text marquee options.|
| [void OH_ArkUI_TextMarqueeOptions_SetSpacing(ArkUI_TextMarqueeOptions* option, float spacing)](#oh_arkui_textmarqueeoptions_setspacing) | - | Sets the distance between the start and end items of the text marquee options.|
| [float OH_ArkUI_TextMarqueeOptions_GetSpacing(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getspacing) | - | Obtains the distance between the start and end items of the text marquee options.|
| [void OH_ArkUI_TextMarqueeOptions_SetLoop(ArkUI_TextMarqueeOptions* option, int32_t loop)](#oh_arkui_textmarqueeoptions_setloop) | - | Sets the number of repetitions for looping text marquee options. The value **0** or negative value indicates infinite looping.|
| [int32_t OH_ArkUI_TextMarqueeOptions_GetLoop(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getloop) | - | Obtains the number of repetitions for looping text marquee options.|
| [void OH_ArkUI_TextMarqueeOptions_SetFromStart(ArkUI_TextMarqueeOptions* option, bool fromStart)](#oh_arkui_textmarqueeoptions_setfromstart) | - | Sets the scrolling direction for looping text marquee options.|
| [bool OH_ArkUI_TextMarqueeOptions_GetFromStart(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getfromstart) | - | Obtains the scrolling direction for looping text marquee options.|
| [void OH_ArkUI_TextMarqueeOptions_SetDelay(ArkUI_TextMarqueeOptions* option, int32_t delay)](#oh_arkui_textmarqueeoptions_setdelay) | - | Sets the delay of each loop for text marquee options.|
| [int32_t OH_ArkUI_TextMarqueeOptions_GetDelay(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getdelay) | - | Obtains the delay of each loop for text marquee options.|
| [void OH_ArkUI_TextMarqueeOptions_SetFadeout(ArkUI_TextMarqueeOptions* option, bool fadeout)](#oh_arkui_textmarqueeoptions_setfadeout) | - | Sets whether text marquee options support a fade-out effect when the text is too long. When supported, if the text content exceeds the display range, the edges of the partially visible text will have a fade-out effect applied. If both ends have partially visible text, both ends will have the fade-out effect applied. When the fade-out effect is enabled, the [NODE_CLIP](./capi-native-node-h.md#arkui_nodeattributetype) attribute is automatically fixed at **true** and cannot be set to **false**.|
| [bool OH_ArkUI_TextMarqueeOptions_GetFadeout(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getfadeout) | - | Obtains whether text marquee options support a fade-out effect when the text is too long.|
| [void OH_ArkUI_TextMarqueeOptions_SetStartPolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeStartPolicy startPolicy)](#oh_arkui_textmarqueeoptions_setstartpolicy) | - | Sets the startup policy of the text marquee options.|
| [ArkUI_MarqueeStartPolicy OH_ArkUI_TextMarqueeOptions_GetStartPolicy(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstartpolicy) | - | Obtains the startup policy of the text marquee options.|
| [void OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeUpdatePolicy updatePolicy)](#oh_arkui_textmarqueeoptions_setupdatepolicy) | - | Sets the update policy of the text marquee options.|
| [ArkUI_MarqueeUpdatePolicy OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getupdatepolicy) | - | Obtains the update policy of the text marquee options.|
| [ArkUI_PickerIndicatorStyle OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)](#oh_arkui_pickerindicatorstyle_create) | ArkUI_PickerIndicatorStyle | Creates a style instance of the selected item indicator.|
| [void  OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)](#oh_arkui_pickerindicatorstyle_dispose) | - | Destroys a style instance of the selected item indicator.|
| [ArkUI_ErrorCode OH_ArkUI_PickerIndicatorStyle_ConfigureBackground(ArkUI_PickerIndicatorStyle* style, ArkUI_PickerIndicatorBackground* background)](#oh_arkui_pickerindicatorstyle_configurebackground) | - | Sets the background style parameters. This API takes effect only when the type of the selected item indicator is [ARKUI_PICKER_INDICATOR_BACKGROUND](capi-native-type-h.md#arkui_pickerindicatortype).|
| [ArkUI_ErrorCode OH_ArkUI_PickerIndicatorStyle_ConfigureDivider(ArkUI_PickerIndicatorStyle* style, ArkUI_PickerIndicatorDivider* divider)](#oh_arkui_pickerindicatorstyle_configuredivider) | - | Sets the divider style parameters. This API takes effect only when the type of the selected item indicator is [ARKUI_PICKER_INDICATOR_DIVIDER](capi-native-type-h.md#arkui_pickerindicatortype).|

## Enum Description

### ArkUI_Alignment

```c
enum ArkUI_Alignment
```

**Description**


Enumerates the alignment modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ALIGNMENT_TOP_START = 0 | Top start.|
| ARKUI_ALIGNMENT_TOP = 1 | Top center.|
| ARKUI_ALIGNMENT_TOP_END = 2 | Top end.|
| ARKUI_ALIGNMENT_START = 3 | Vertically centered start.|
| ARKUI_ALIGNMENT_CENTER = 4 | Horizontally and vertically centered.|
| ARKUI_ALIGNMENT_END = 5 | Vertically centered end.|
| ARKUI_ALIGNMENT_BOTTOM_START = 6 | Bottom start.|
| ARKUI_ALIGNMENT_BOTTOM = 7 | Horizontally centered on the bottom.|
| ARKUI_ALIGNMENT_BOTTOM_END = 8 | Bottom end.|

### ArkUI_ImageRepeat

```c
enum ArkUI_ImageRepeat
```

**Description**


Enumerates the image repeat patterns.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_IMAGE_REPEAT_NONE = 0 | The image is not repeatedly drawn.|
| ARKUI_IMAGE_REPEAT_X | The image is repeatedly drawn only along the x-axis.|
| ARKUI_IMAGE_REPEAT_Y | The image is repeatedly drawn only along the y-axis.|
| ARKUI_IMAGE_REPEAT_XY | The image is repeatedly drawn along both axes.|

### ArkUI_FontStyle

```c
enum ArkUI_FontStyle
```

**Description**


Enumerates the font styles.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_FONT_STYLE_NORMAL = 0 | Standard font style.|
| ARKUI_FONT_STYLE_ITALIC | Italic font style.|

### ArkUI_FontWeight

```c
enum ArkUI_FontWeight
```

**Description**


Enumerates the font weights.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_FONT_WEIGHT_W100 = 0 | 100 |
| ARKUI_FONT_WEIGHT_W200 | 200 |
| ARKUI_FONT_WEIGHT_W300 | 300 |
| ARKUI_FONT_WEIGHT_W400 | 400 |
| ARKUI_FONT_WEIGHT_W500 | 500 |
| ARKUI_FONT_WEIGHT_W600 | 600 |
| ARKUI_FONT_WEIGHT_W700 | 700 |
| ARKUI_FONT_WEIGHT_W800 | 800 |
| ARKUI_FONT_WEIGHT_W900 | 900 |
| ARKUI_FONT_WEIGHT_BOLD | The font weight is bold.|
| ARKUI_FONT_WEIGHT_NORMAL | The font weight is normal.|
| ARKUI_FONT_WEIGHT_BOLDER | The font weight is bolder.|
| ARKUI_FONT_WEIGHT_LIGHTER | The font weight is lighter.|
| ARKUI_FONT_WEIGHT_MEDIUM | The font weight is medium.|
| ARKUI_FONT_WEIGHT_REGULAR | The font weight is normal.|

### ArkUI_TextAlignment

```c
enum ArkUI_TextAlignment
```

**Description**


Enumerates the text alignment mode.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TEXT_ALIGNMENT_START = 0 | Aligned with the start.|
| ARKUI_TEXT_ALIGNMENT_CENTER | Horizontally centered.|
| ARKUI_TEXT_ALIGNMENT_END | Aligned with the end.|
| ARKUI_TEXT_ALIGNMENT_JUSTIFY | Aligned with both margins.|
| ARKUI_TEXT_ALIGNMENT_LEFT_TO_RIGHT = 4 | Aligned from left to right.<br>**Since**: 23|
| ARKUI_TEXT_ALIGNMENT_RIGHT_TO_LEFT = 5 | Aligned from right to left.<br>**Since**: 23|

### ArkUI_TextVerticalAlignment

```c
enum ArkUI_TextVerticalAlignment
```

**Description**


Enumerates text vertical alignment styles.

**Since**: 20

| Value| Description|
| -- | -- |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE = 0 | Aligned to the baseline.|
| ARKUI_TEXT_VERTICAL_ALIGNMENT_BOTTOM | Bottom aligned.|
| ARKUI_TEXT_VERTICAL_ALIGNMENT_CENTER | The list item is centered along|
| ARKUI_TEXT_VERTICAL_ALIGNMENT_TOP | Top aligned.|

### ArkUI_TextContentAlign

```c
enum ArkUI_TextContentAlign
```

**Description**


Enumerates vertical alignment styles in the text content area.

**Since**: 21

| Value| Description|
| -- | -- |
| ARKUI_TEXT_CONTENT_ALIGN_TOP = 0 | Top aligned.|
| ARKUI_TEXT_CONTENT_ALIGN_CENTER = 1 | The list item is centered along|
| ARKUI_TEXT_CONTENT_ALIGN_BOTTOM = 2 | Bottom aligned.|

### ArkUI_TextDirection

``` c
enum ArkUI_TextDirection
```

**Description**


Enumerates the text layout directions.

**Since**: 23

| Value| Description|
| -- | -- |
| ARKUI_TEXT_DIRECTION_LTR = 0 | From left to right.|
| ARKUI_TEXT_DIRECTION_RTL = 1 | From right to left.|
| ARKUI_TEXT_DIRECTION_DEFAULT = 2 | Follow the component layout.|
| ARKUI_TEXT_DIRECTION_AUTO = 3 | Follow the writing direction of the content. For example, for right-to-left (RTL) languages (such as Tibetan and Uyghur), the text is laid out from right to left. For left-to-right (LTR) languages (such as Chinese and English), the text is laid out from left to right.|

### ArkUI_EnterKeyType

```c
enum ArkUI_EnterKeyType
```

**Description**


Enumerates the types of the Enter key for a single-line text box.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ENTER_KEY_TYPE_GO = 2 | The Enter key is labeled "Go."|
| ARKUI_ENTER_KEY_TYPE_SEARCH = 3 | The Enter key is labeled "Search."|
| ARKUI_ENTER_KEY_TYPE_SEND = 4 | The Enter key is labeled "Send."|
| ARKUI_ENTER_KEY_TYPE_NEXT = 5 | The Enter key is labeled "Next."|
| ARKUI_ENTER_KEY_TYPE_DONE = 6 | The Enter key is labeled "Done."|
| ARKUI_ENTER_KEY_TYPE_PREVIOUS = 7 | The Enter key is labeled "Previous."|
| ARKUI_ENTER_KEY_TYPE_NEW_LINE = 8 | The Enter key is labeled "Return."|

### ArkUI_TextInputType

```c
enum ArkUI_TextInputType
```

**Description**


Enumerates the input method type of a single-line text.

**Since**: 12

| Value| Description                      |
| -- |--------------------------|
| ARKUI_TEXTINPUT_TYPE_NORMAL = 0 | Normal input mode.                 |
| ARKUI_TEXTINPUT_TYPE_NUMBER = 2 | Number input mode.                  |
| ARKUI_TEXTINPUT_TYPE_PHONE_NUMBER = 3 | Phone number input mode.               |
| ARKUI_TEXTINPUT_TYPE_EMAIL = 5 | Email address input mode.               |
| ARKUI_TEXTINPUT_TYPE_PASSWORD = 7 | Password input mode.                 |
| ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD = 8 | Numeric password input mode.              |
| ARKUI_TEXTINPUT_TYPE_SCREEN_LOCK_PASSWORD = 9 | Lock screen password input mode.             |
| ARKUI_TEXTINPUT_TYPE_USER_NAME = 10 | Username input mode.                |
| ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD = 11 | New password input mode.                |
| ARKUI_TEXTINPUT_TYPE_NUMBER_DECIMAL = 12 | Number input mode with a decimal point.            |
| ARKUI_TEXTINPUT_TYPE_ONE_TIME_CODE = 14 | Verification code input mode.<br>**Since**: 20|

### ArkUI_TextAreaType

```c
enum ArkUI_TextAreaType
```

**Description**


Enumerates the input method types of a multi-line text.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TEXTAREA_TYPE_NORMAL = 0 | Normal input mode.|
| ARKUI_TEXTAREA_TYPE_NUMBER = 2 | Number input mode.|
| ARKUI_TEXTAREA_TYPE_PHONE_NUMBER = 3 | Phone number input mode.|
| ARKUI_TEXTAREA_TYPE_EMAIL = 5 | Email address input mode.|
| ARKUI_TEXTAREA_TYPE_ONE_TIME_CODE = 14 | Verification code input mode.<br>**Since**: 20|

### ArkUI_CancelButtonStyle

```c
enum ArkUI_CancelButtonStyle
```

**Description**


Enumerates the styles of the Cancel button.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_CANCELBUTTON_STYLE_CONSTANT = 0 | The Cancel button is always displayed.|
| ARKUI_CANCELBUTTON_STYLE_INVISIBLE | The Cancel button is always hidden.|
| ARKUI_CANCELBUTTON_STYLE_INPUT | The Cancel button is displayed when there is text input.|

### ArkUI_XComponentType

```c
enum ArkUI_XComponentType
```

**Description**


Enumerates the types of the **XComponent** component.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_XCOMPONENT_TYPE_SURFACE = 0 | The custom content of EGL/OpenGL ES and media data is displayed individually on the screen.|
| ARKUI_XCOMPONENT_TYPE_TEXTURE = 2 | The custom content of EGL/OpenGL ES and media data is grouped and displayed together with content of the component.|

### ArkUI_ProgressType

```c
enum ArkUI_ProgressType
```

**Description**


Enumerates the styles of the progress indicator.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_PROGRESS_TYPE_LINEAR = 0 | Linear type.|
| ARKUI_PROGRESS_TYPE_RING | Ring style without scale marks.|
| ARKUI_PROGRESS_TYPE_ECLIPSE | Eclipse style.|
| ARKUI_PROGRESS_TYPE_SCALE_RING | Ring style with scale marks.|
| ARKUI_PROGRESS_TYPE_CAPSULE | Capsule style.|

### ArkUI_TextDecorationType

```c
enum ArkUI_TextDecorationType
```

**Description**


Enumerates the text decoration types.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TEXT_DECORATION_TYPE_NONE = 0 | No text decoration.|
| ARKUI_TEXT_DECORATION_TYPE_UNDERLINE | Line under the text.|
| ARKUI_TEXT_DECORATION_TYPE_OVERLINE | Line over the text.|
| ARKUI_TEXT_DECORATION_TYPE_LINE_THROUGH | Line through the text.|

### ArkUI_TextDecorationStyle

```c
enum ArkUI_TextDecorationStyle
```

**Description**


Enumerates the text decoration styles.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TEXT_DECORATION_STYLE_SOLID = 0 | Single solid line.|
| ARKUI_TEXT_DECORATION_STYLE_DOUBLE | Double solid line.|
| ARKUI_TEXT_DECORATION_STYLE_DOTTED | Dotted line.|
| ARKUI_TEXT_DECORATION_STYLE_DASHED | Dashed style.|
| ARKUI_TEXT_DECORATION_STYLE_WAVY | Wavy line.|

### ArkUI_TextCase

```c
enum ArkUI_TextCase
```

**Description**


Enumerates the text cases.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TEXT_CASE_NORMAL = 0 | The original case of the text is retained.|
| ARKUI_TEXT_CASE_LOWER | All letters in the text are in lowercase.|
| ARKUI_TEXT_CASE_UPPER | All letters in the text are in uppercase.|

### ArkUI_CopyOptions

```c
enum ArkUI_CopyOptions
```

**Description**


Enumerates the text copy and paste modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_COPY_OPTIONS_NONE = 0 | Copy is not allowed.|
| ARKUI_COPY_OPTIONS_IN_APP | Intra-application copy is allowed.|
| ARKUI_COPY_OPTIONS_LOCAL_DEVICE | Intra-device copy is allowed.|
| ARKUI_COPY_OPTIONS_CROSS_DEVICE | Cross-device copy is allowed.|

### ArkUI_ShadowType

```c
enum ArkUI_ShadowType
```

**Description**


Enumerates shadow types.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SHADOW_TYPE_COLOR = 0 | Color.|
| ARKUI_SHADOW_TYPE_BLUR = 1 | Blur.|

### ArkUI_DatePickerMode

```c
enum ArkUI_DatePickerMode
```

**Description**


Enumerates the column display modes of the date picker.

**Since**: 18

| Value| Description|
| -- | -- |
| ARKUI_DATEPICKER_MODE_DATE = 0 | Default value. The date displays three columns: year, month, and day.|
| ARKUI_DATEPICKER_YEAR_AND_MONTH = 1 | The date displays two columns: year and month.|
| ARKUI_DATEPICKER_MONTH_AND_DAY = 2 | The date displays two columns: month and day.|

### ArkUI_TextPickerRangeType

```c
enum ArkUI_TextPickerRangeType
```

**Description**


Enumerates the types of the text picker.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TEXTPICKER_RANGETYPE_SINGLE = 0 | Single-column text picker.|
| ARKUI_TEXTPICKER_RANGETYPE_MULTI | Multi-column text picker.|
| ARKUI_TEXTPICKER_RANGETYPE_RANGE_CONTENT | Single-column text picker with image resources.|
| ARKUI_TEXTPICKER_RANGETYPE_CASCADE_RANGE_CONTENT | Interconnected multi-column text picker.|

### ArkUI_AccessibilityCheckedState

```c
enum ArkUI_AccessibilityCheckedState
```

**Description**


Enumerates the accessibility check box states.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ACCESSIBILITY_UNCHECKED = 0 | The check box is not selected.|
| ARKUI_ACCESSIBILITY_CHECKED = 1 | The check box is selected.|

### ArkUI_AccessibilityActionType

```c
enum ArkUI_AccessibilityActionType
```

**Description**


Enumerates the accessibility action types.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ACCESSIBILITY_ACTION_CLICK = 1 << 0 | Tapping|
| ARKUI_ACCESSIBILITY_ACTION_LONG_CLICK = 1 << 1 | Long press|
| ARKUI_ACCESSIBILITY_ACTION_CUT = 1 << 2 | Cut.|
| ARKUI_ACCESSIBILITY_ACTION_COPY = 1 << 3 | Copy.|
| ARKUI_ACCESSIBILITY_ACTION_PASTE = 1 << 4 | Paste.|

### ArkUI_EdgeEffect

```c
enum ArkUI_EdgeEffect
```

**Description**


Enumerates the effects used at the edges of the component when the boundary of the scrollable content is reached.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_EDGE_EFFECT_SPRING = 0 | Spring effect. When at one of the edges, the component can move beyond the bounds based on the initial speed or through touches, and produces a bounce effect when the user releases their finger.|
| ARKUI_EDGE_EFFECT_FADE = 1 | Fade effect. When at one of the edges, the component produces a fade effect.|
| ARKUI_EDGE_EFFECT_NONE = 2 | No effect when the component is at one of the edges.|

### ArkUI_BarState

```c
enum ArkUI_BarState
```

**Description**


Enumerates the text control scrollbar states.

**Since**: 22

| Value| Description|
| -- | -- |
| ARKUI_BAR_STATE_OFF = 0 | Not displayed.|
| ARKUI_BAR_STATE_AUTO = 1 | Displayed when needed.|
| ARKUI_BAR_STATE_ON = 2 | Always displayed.|

### ArkUI_EffectEdge

```c
enum ArkUI_EffectEdge
```

**Description**


Enumerates the edges for which the effect takes effect when the boundary of the scrollable content is reached.

**Since**: 18

| Value| Description                   |
| -- |-----------------------|
| ARKUI_EFFECT_EDGE_START = 1 | Start edge.               |
| ARKUI_EFFECT_EDGE_END = 2 | End edge.               |

### ArkUI_ScrollDirection

```c
enum ArkUI_ScrollDirection
```

**Description**


Enumerates the scroll directions of scrollable components.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_DIRECTION_VERTICAL = 0 | Vertical scrolling only.|
| ARKUI_SCROLL_DIRECTION_HORIZONTAL = 1 | Horizontal scrolling only.|
| ARKUI_SCROLL_DIRECTION_NONE = 3 | Scrolling disabled.|
| ARKUI_SCROLL_DIRECTION_FREE = 4 | Free scrolling in both directions.<br>**Since**: 20|

### ArkUI_ScrollSnapAlign

```c
enum ArkUI_ScrollSnapAlign
```

**Description**


Enumerates the alignment modes of list items when scrolling ends.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_SNAP_ALIGN_NONE = 0 | No alignment. This is the default value.|
| ARKUI_SCROLL_SNAP_ALIGN_START = 1 | The first item in the view is aligned at the start of the list.|
| ARKUI_SCROLL_SNAP_ALIGN_CENTER = 2 | The middle items in the view are aligned in the center of the list.|
| ARKUI_SCROLL_SNAP_ALIGN_END = 3 | The last item in the view is aligned at the end of the list.|

### ArkUI_ScrollBarDisplayMode

```c
enum ArkUI_ScrollBarDisplayMode
```

**Description**


Enumerates the scrollbar display modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF = 0 | Not displayed.|
| ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO = 1 | Displayed when the screen is touched and hidden after 2s.|
| ARKUI_SCROLL_BAR_DISPLAY_MODE_ON = 2 | Always displayed.|

### ArkUI_Axis

```c
enum ArkUI_Axis
```

**Description**


Enumerates scroll directions and [List](./arkui-ts/ts-container-list.md) component arrangement directions.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_AXIS_VERTICAL = 0 | Vertical scrolling only.|
| ARKUI_AXIS_HORIZONTAL = 1 | Horizontal scrolling only.|

### ArkUI_StickyStyle

```c
enum ArkUI_StickyStyle
```

**Description**


Enumerates the modes for pinning the header to the top or the footer to the bottom.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_STICKY_STYLE_NONE = 0 | In the list item group, the header is not pinned to the top, and the footer is not pinned to the bottom.|
| ARKUI_STICKY_STYLE_HEADER = 1 | In the list item group, the header is pinned to the top, and the footer is not pinned to the bottom.|
| ARKUI_STICKY_STYLE_FOOTER = 2 | In the list item group, the footer is pinned to the bottom, and the header is not pinned to the top.|
| ARKUI_STICKY_STYLE_BOTH = 3 | In the list item group, the footer is pinned to the bottom, and the header is pinned to the top.|

### ArkUI_ContentClipMode

```c
enum ArkUI_ContentClipMode
```

**Description**


Enumerates the content clipping modes of scrollable components.

**Since**: 18

| Value| Description|
| -- | -- |
| ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY = 0 | Clip to the content area only.|
| ARKUI_CONTENT_CLIP_MODE_BOUNDARY = 1 | Clip to the component's boundary area.|
| ARKUI_CONTENT_CLIP_MODE_SAFE_AREA = 2 | Clip to the safe area configured for the component.|

### ArkUI_WaterFlowLayoutMode

```c
enum ArkUI_WaterFlowLayoutMode
```

**Description**


Enumerates the layout modes of the WaterFlow component.

**Since**: 18

| Value| Description|
| -- | -- |
| ARKUI_WATER_FLOW_LAYOUT_MODE_ALWAYS_TOP_DOWN = 0 | Layout from top to bottom. In scenarios where column switching occurs, the layout starts from the first water flow item to the currently displayed water flow item.|
| ARKUI_WATER_FLOW_LAYOUT_MODE_SLIDING_WINDOW = 1 | Sliding window layout. In scenarios where column switching occurs, only the range of water flow items currently on display is re-laid out. As the user scrolls down with their finger, water flow items that enter the display range from above are subsequently laid out.|

### ArkUI_BorderStyle

```c
enum ArkUI_BorderStyle
```

**Description**


Enumerates the border styles.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_BORDER_STYLE_SOLID = 0 | Solid border.|
| ARKUI_BORDER_STYLE_DASHED = 1 | Dashed border.|
| ARKUI_BORDER_STYLE_DOTTED = 2 | Dotted border.|

### ArkUI_HitTestMode

```c
enum ArkUI_HitTestMode
```

**Description**


Enumerates the hit test modes.

**Since**: 12

| Value| Description                                                    |
| -- |--------------------------------------------------------|
| ARKUI_HIT_TEST_MODE_DEFAULT = 0 | Both the node and its child node respond to the hit test of a touch event, but its sibling node is blocked from the hit test.                                             |
| ARKUI_HIT_TEST_MODE_BLOCK = 1 | The node responds to the hit test of a touch event, but its child node and sibling node are blocked from the hit test.                                             |
| ARKUI_HIT_TEST_MODE_TRANSPARENT = 2 | Both the node and its child node respond to the hit test of a touch event, and its sibling node is also considered during the hit test.                                        |
| ARKUI_HIT_TEST_MODE_NONE = 3 | The node does not respond to the hit test of a touch event.                                            |
| ARKUI_HIT_TEST_MODE_BLOCK_HIERARCHY = 4 | The node and its child nodes participate in hit tests, while blocking hit tests for all sibling nodes and parent nodes with lower priority.<br>**Since**: 20|
| ARKUI_HIT_TEST_MODE_BLOCK_DESCENDANTS = 5 | The node does not respond to hit tests, and none of its descendants (including children and grandchildren) participate in hit tests either.<br>**Since**: 20                    |

### ArkUI_ShadowStyle

```c
enum ArkUI_ShadowStyle
```

**Description**


Enumerates shadow styles.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_XS = 0 | Mini shadow.|
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_SM = 1 | Small shadow.|
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_MD = 2 | Medium shadow.|
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_LG = 3 | Large shadow.|
| ARKUI_SHADOW_STYLE_OUTER_FLOATING_SM = 4 | Floating small shadow.|
| ARKUI_SHADOW_STYLE_OUTER_FLOATING_MD = 5 | Floating medium shadow.|

### ArkUI_AnimationCurve

```c
enum ArkUI_AnimationCurve
```

**Description**


Enumerates the animation curves.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_CURVE_LINEAR = 0 | The animation speed keeps unchanged.|
| ARKUI_CURVE_EASE = 1 | The animation starts slowly, accelerates, and then slows down towards the end.|
| ARKUI_CURVE_EASE_IN = 2 | The animation starts at a low speed and then picks up speed until the end.|
| ARKUI_CURVE_EASE_OUT = 3 | The animation ends at a low speed.|
| ARKUI_CURVE_EASE_IN_OUT = 4 | The animation starts and ends at a low speed.|
| ARKUI_CURVE_FAST_OUT_SLOW_IN = 5 | The animation uses the standard curve|
| ARKUI_CURVE_LINEAR_OUT_SLOW_IN = 6 | The animation uses the deceleration curve.|
| ARKUI_CURVE_FAST_OUT_LINEAR_IN = 7 | The animation uses the acceleration curve.|
| ARKUI_CURVE_EXTREME_DECELERATION = 8 | The animation uses the extreme deceleration curve.|
| ARKUI_CURVE_SHARP = 9 | The animation uses the sharp curve.|
| ARKUI_CURVE_RHYTHM = 10 | The animation uses the rhythm curve.|
| ARKUI_CURVE_SMOOTH = 11 | The animation uses the smooth curve.|
| ARKUI_CURVE_FRICTION = 12 | The animation uses the friction curve|

### ArkUI_SwiperArrow

```c
enum ArkUI_SwiperArrow
```

**Description**


Enumerates arrow styles of the navigation indicator.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SWIPER_ARROW_HIDE = 0 | The arrow is not displayed for the navigation indicator.|
| ARKUI_SWIPER_ARROW_SHOW = 1 | The arrow is displayed for the navigation indicator.|
| ARKUI_SWIPER_ARROW_SHOW_ON_HOVER = 2 | The arrow is displayed only when the mouse pointer hovers over the navigation indicator.|

### ArkUI_SwiperNestedScrollMode

```c
enum ArkUI_SwiperNestedScrollMode
```

**Description**


Enumerates the nested scrolling mode of the **Swiper** component and its parent container.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY = 0 | The scrolling is contained within the **Swiper** component, and no scroll chaining occurs, that is, the parent container does not scroll when the component scrolling reaches the boundary.|
| ARKUI_SWIPER_NESTED_SRCOLL_SELF_FIRST = 1 | The **Swiper** component scrolls first, and when it hits the boundary, the parent container scrolls. When the parent container hits the boundary, its edge effect is displayed. If no edge effect is specified for the parent container, the edge effect of the child component is displayed instead.|

### ArkUI_PageFlipMode

```c
enum ArkUI_PageFlipMode
```

**Description**


Enumerates the page flipping modes using the mouse wheel for the <b>Swiper</b> component.

**Since**: 15

| Value| Description|
| -- | -- |
| ARKUI_PAGE_FLIP_MODE_CONTINUOUS = 0 | When the mouse wheel is scrolled continuously, multiple pages are flipped, which is determined by the number of times that mouse events are reported.|
| ARKUI_PAGE_FLIP_MODE_SINGLE = 1 | The system does not respond to other mouse wheel events until the page flipping animation ends.|

### ArkUI_SwiperAnimationMode

```c
enum ArkUI_SwiperAnimationMode
```

**Description**


Enumerates the animation modes for the **Swiper** component when jumping to the page with the specified index.

**Since**: 15

| Value| Description|
| -- | -- |
| ARKUI_SWIPER_NO_ANIMATION = 0 | Jumps to the target page without any animation.|
| ARKUI_SWIPER_DEFAULT_ANIMATION = 1 | Animates smoothly to the target page.|
| ARKUI_SWIPER_FAST_ANIMATION = 2 | First jumps to a position near the target page without animation, then animates to the target page.|

### ArkUI_AccessibilityMode

```c
enum ArkUI_AccessibilityMode
```

**Description**


Enumerates the accessibility modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ACCESSIBILITY_MODE_AUTO = 0 | The mode is automatically set to enabled or disabled based on the component.|
| ARKUI_ACCESSIBILITY_MODE_ENABLED = 1 | The component can be identified by the accessibility service.|
| ARKUI_ACCESSIBILITY_MODE_DISABLED = 2 | The component cannot be identified by the accessibility service.|
| ARKUI_ACCESSIBILITY_MODE_DISABLED_FOR_DESCENDANTS = 3 | The component and all its child components cannot be identified by the accessibility service.|

### ArkUI_TextCopyOptions

```c
enum ArkUI_TextCopyOptions
```

**Description**


Enumerates copy options, which define whether copy and paste is allowed for text content.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TEXT_COPY_OPTIONS_NONE = 0 | Copy is not allowed.|
| ARKUI_TEXT_COPY_OPTIONS_IN_APP | Intra-application copy is allowed.|
| ARKUI_TEXT_COPY_OPTIONS_LOCAL_DEVICE | Intra-device copy is allowed.|
| ARKUI_TEXT_COPY_OPTIONS_CROSS_DEVICE | Cross-device copy is allowed.|

### ArkUI_TextHeightAdaptivePolicy

```c
enum ArkUI_TextHeightAdaptivePolicy
```

**Description**


Defines how the adaptive height is determined for the text.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MAX_LINES_FIRST = 0 | Prioritize the **maxLines** settings.|
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MIN_FONT_SIZE_FIRST | Prioritize the **minFontSize** settings.|
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_LAYOUT_CONSTRAINT_FIRST | Prioritize the layout constraint settings in terms of height.|

### ArkUI_ScrollNestedMode

```c
enum ArkUI_ScrollNestedMode
```

**Description**


Enumerates the nested scrolling modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_NESTED_MODE_SELF_ONLY = 0 | The scrolling is contained within the component, and no scroll chaining occurs, that is, the parent component does not scroll when the component scrolling reaches the boundary.|
| ARKUI_SCROLL_NESTED_MODE_SELF_FIRST = 1 | The component scrolls first, and when it hits the boundary, the parent component scrolls. When the parent component hits the boundary, its edge effect is displayed.|
| ARKUI_SCROLL_NESTED_MODE_PARENT_FIRST = 2 | The parent component scrolls first, and when it hits the boundary, the component scrolls.|
| ARKUI_SCROLL_NESTED_MODE_PARALLEL = 3 | The component and its parent component scroll at the same time. When both the component and its parent component hit the boundary, the edge effect of the component is displayed.|

### ArkUI_ScrollEdge

```c
enum ArkUI_ScrollEdge
```

**Description**


Enumerates the edges to which the component scrolls.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_EDGE_TOP = 0 | Top edge in the vertical direction.|
| ARKUI_SCROLL_EDGE_BOTTOM = 1 | Bottom edge in the vertical direction.|
| ARKUI_SCROLL_EDGE_START = 2 | Start position in the horizontal direction.|
| ARKUI_SCROLL_EDGE_END = 3 | End position in the horizontal direction.|

### ArkUI_ScrollAlignment

```c
enum ArkUI_ScrollAlignment
```

**Description**


Defines how the list item to scroll to is aligned with the container.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_ALIGNMENT_START = 0 | The start edge of the list item is flush with the start edge of the container.|
| ARKUI_SCROLL_ALIGNMENT_CENTER = 1 | The list item is centered along the main axis of the container.|
| ARKUI_SCROLL_ALIGNMENT_END = 2 | The end edge of the list item is flush with the end edge of the container.|
| ARKUI_SCROLL_ALIGNMENT_AUTO = 3 | The list item is automatically aligned. If the item is fully contained within the display area, no adjustment is performed. Otherwise, the item is aligned so that its start or end edge is flush with the start or end edge of the container, whichever requires a shorter scrolling distance.|

### ArkUI_ScrollState

```c
enum ArkUI_ScrollState
```

**Description**


Enumerates the scrolling states.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_STATE_IDLE = 0 | Idle. The container enters this state when an API in the controller is used to scroll the container or when the scrollbar is dragged.|
| ARKUI_SCROLL_STATE_SCROLL = 1 | Scrolling. The container enters this state when the user drags the container to scroll.|
| ARKUI_SCROLL_STATE_FLING = 2 | Inertial scrolling. The container enters this state when inertial scrolling occurs or when the container bounces back after being released from a fling.|

### ArkUI_SliderBlockStyle

```c
enum ArkUI_SliderBlockStyle
```

**Description**


Enumerates the styles of the slider in the block direction.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SLIDER_BLOCK_STYLE_DEFAULT = 0 | Round slider.|
| ARKUI_SLIDER_BLOCK_STYLE_IMAGE = 1 | Slider with an image background.|
| ARKUI_SLIDER_BLOCK_STYLE_SHAPE = 2 | Slider in a custom shape.|

### ArkUI_SliderDirection

```c
enum ArkUI_SliderDirection
```

**Description**


Enumerates the scroll directions of the slider.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SLIDER_DIRECTION_VERTICAL = 0 | Vertical direction.|
| ARKUI_SLIDER_DIRECTION_HORIZONTAL = 1 | Horizontal direction.|

### ArkUI_SliderStyle

```c
enum ArkUI_SliderStyle
```

**Description**


Enumerates the slider styles.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SLIDER_STYLE_OUT_SET = 0 | The slider is on the slider rail.|
| ARKUI_SLIDER_STYLE_IN_SET = 1 | The slider is in the slider rail.|
| ARKUI_SLIDER_STYLE_NONE = 2 | There is no thumb.|

### ArkUI_CheckboxShape

```c
enum ArkUI_CheckboxShape
```

**Description**


Enumerates the shapes of the check box.

**Since**: 12

| Value| Description|
| -- | -- |
| ArkUI_CHECKBOX_SHAPE_CIRCLE = 0 | Circle.|
| ArkUI_CHECKBOX_SHAPE_ROUNDED_SQUARE = 1 | Rounded square.|

### ArkUI_AnimationPlayMode

```c
enum ArkUI_AnimationPlayMode
```

**Description**


Enumerates the animation playback modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ANIMATION_PLAY_MODE_NORMAL = 0 | The animation is played forwards.|
| ARKUI_ANIMATION_PLAY_MODE_REVERSE = 1 | The animation is played backwards.|
| ARKUI_ANIMATION_PLAY_MODE_ALTERNATE = 2 | The animation is played forwards for an odd number of times (1, 3, 5...) and backwards for an even number of times (2, 4, 6...).|
| ARKUI_ANIMATION_PLAY_MODE_ALTERNATE_REVERSE = 3 | The animation is played backwards for an odd number of times (1, 3, 5...) and forwards for an even number of times (2, 4, 6...).|

### ArkUI_ImageSize

```c
enum ArkUI_ImageSize
```

**Description**


Defines the image size.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_IMAGE_SIZE_AUTO = 0 | The original image aspect ratio is retained.|
| ARKUI_IMAGE_SIZE_COVER | The image is scaled with its aspect ratio retained for both sides to be greater than or equal to the display boundaries.|
| ARKUI_IMAGE_SIZE_CONTAIN | The image is scaled with its aspect ratio retained for the content to be completely displayed within the display boundaries.|

### ArkUI_AdaptiveColor

```c
enum ArkUI_AdaptiveColor
```

**Description**


Enumerates the adaptive color modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ADAPTIVE_COLOR_DEFAULT = 0 | Adaptive color mode is not used.|
| ARKUI_ADAPTIVE_COLOR_AVERAGE = 1 | Adaptive color mode is used.|

### ArkUI_ColorMode

```c
enum ArkUI_ColorMode
```

**Description**


Enumerates the color modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_COLOR_MODE_SYSTEM = 0 | Following the system color mode.|
| ARKUI_COLOR_MODE_LIGHT = 1 | Light color mode.|
| ARKUI_COLOR_MODE_DARK = 2 | Dark color mode.|

### ArkUI_SystemColorMode

```c
enum ArkUI_SystemColorMode
```

**Description**


Enumerates the system color modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SYSTEM_COLOR_MODE_LIGHT = 0 | Light mode.|
| ARKUI_SYSTEM_COLOR_MODE_DARK = 1 | Dark mode.|

### ArkUI_BlurStyle

```c
enum ArkUI_BlurStyle
```

**Description**


Enumerates the blur styles.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_BLUR_STYLE_THIN = 0 | Thin material.|
| ARKUI_BLUR_STYLE_REGULAR = 1 | Regular material.|
| ARKUI_BLUR_STYLE_THICK = 2 | Thick material.|
| ARKUI_BLUR_STYLE_BACKGROUND_THIN = 3 | Material that creates the minimum depth of field effect.|
| ARKUI_BLUR_STYLE_BACKGROUND_REGULAR = 4 | Material that creates a medium shallow depth of field effect.|
| ARKUI_BLUR_STYLE_BACKGROUND_THICK = 5 | Material that creates a high shallow depth of field effect.|
| ARKUI_BLUR_STYLE_BACKGROUND_ULTRA_THICK = 6 | Material that creates the maximum depth of field effect.|
| ARKUI_BLUR_STYLE_NONE = 7 | No blur.|
| ARKUI_BLUR_STYLE_COMPONENT_ULTRA_THIN = 8 | Component ultra-thin material.|
| ARKUI_BLUR_STYLE_COMPONENT_THIN = 9 | Component thin material.|
| ARKUI_BLUR_STYLE_COMPONENT_REGULAR = 10 | Component regular material.|
| ARKUI_BLUR_STYLE_COMPONENT_THICK = 11 | Component thick material.|
| ARKUI_BLUR_STYLE_COMPONENT_ULTRA_THICK = 12 | Component ultra-thick material.|

### ArkUI_BlurStyleActivePolicy

```c
enum ArkUI_BlurStyleActivePolicy
```

**Description**


Enumerates the activation policies for the background blur effect.

**Since**: 19

| Value| Description|
| -- | -- |
| ARKUI_BLUR_STYLE_ACTIVE_POLICY_FOLLOWS_WINDOW_ACTIVE_STATE = 0 | The blur effect changes according to the window's focus state; it is inactive when the window is not in focus and active when the window is in focus.|
| ARKUI_BLUR_STYLE_ACTIVE_POLICY_ALWAYS_ACTIVE = 1 | The blur effect is always active.|
| ARKUI_BLUR_STYLE_ACTIVE_POLICY_ALWAYS_INACTIVE = 2 | The blur effect is always inactive.|

### ArkUI_VerticalAlignment

```c
enum ArkUI_VerticalAlignment
```

**Description**


Enumerates the vertical alignment modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_VERTICAL_ALIGNMENT_TOP = 0 | Top aligned.|
| ARKUI_VERTICAL_ALIGNMENT_CENTER = 1 | Aligned with the center. This is the default alignment mode.|
| ARKUI_VERTICAL_ALIGNMENT_BOTTOM = 2 | Bottom aligned.|

### ArkUI_HorizontalAlignment

```c
enum ArkUI_HorizontalAlignment
```

**Description**


Enumerates the alignment mode in the horizontal direction.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_HORIZONTAL_ALIGNMENT_START = 0 | Aligned with the start edge in the same direction as the language in use.|
| ARKUI_HORIZONTAL_ALIGNMENT_CENTER = 1 | Aligned with the center. This is the default alignment mode.|
| ARKUI_HORIZONTAL_ALIGNMENT_END = 2 | Aligned with the end edge in the same direction as the language in use.|

### ArkUI_TextOverflow

```c
enum ArkUI_TextOverflow
```

**Description**


Enumerates the display modes when the text is too long.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TEXT_OVERFLOW_NONE = 0 | Extra-long text is not clipped.|
| ARKUI_TEXT_OVERFLOW_CLIP | Extra-long text is clipped.|
| ARKUI_TEXT_OVERFLOW_ELLIPSIS | An ellipsis (...) is used to represent text overflow.|
| ARKUI_TEXT_OVERFLOW_MARQUEE | Text continuously scrolls when text overflow occurs.|

### ArkUI_ImageSpanAlignment

```c
enum ArkUI_ImageSpanAlignment
```

**Description**


Enumerates the alignment mode of the image with the text.

**Since**: 12

| Value| Description                                |
| -- |------------------------------------|
| ARKUI_IMAGE_SPAN_ALIGNMENT_BASELINE = 0 | The image is bottom aligned with the text baseline.               |
| ARKUI_IMAGE_SPAN_ALIGNMENT_BOTTOM | The image is bottom aligned with the text.                    |
| ARKUI_IMAGE_SPAN_ALIGNMENT_CENTER | The image is centered aligned with the text.                      |
| ARKUI_IMAGE_SPAN_ALIGNMENT_TOP | The image is top aligned with the text.                    |
| ARKUI_IMAGE_SPAN_ALIGNMENT_FOLLOW_PARAGRAPH | The image alignment mode follows the text component's alignment mode.<br>**Since**: 20|

### ArkUI_ObjectFit

```c
enum ArkUI_ObjectFit
```

**Description**


Enumerates the image filling effects.ImageSpanAlignment

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_OBJECT_FIT_CONTAIN = 0 | The image is scaled with its aspect ratio retained for the content to be completely displayed within the display boundaries.|
| ARKUI_OBJECT_FIT_COVER | The image is scaled with its aspect ratio retained for both sides to be greater than or equal to the display boundaries.|
| ARKUI_OBJECT_FIT_AUTO | The image is scaled automatically to fit the display area.|
| ARKUI_OBJECT_FIT_FILL | The image is scaled to fill the display area, and its aspect ratio is not retained.|
| ARKUI_OBJECT_FIT_SCALE_DOWN | The image is displayed with its aspect ratio retained, in a size smaller than or equal to the original size.|
| ARKUI_OBJECT_FIT_NONE | The original size is retained.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_START | Not resized, the image is aligned with the start edge of the top of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP | Not resized, the image is horizontally centered at the top of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_TOP_END | Not resized, the image is aligned with the end edge at the top of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_START | Not resized, the image is vertically centered on the start edge of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_CENTER | Not resized, the image is horizontally and vertically centered in the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_END | Not resized, the image is vertically centered on the end edge of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_START | Not resized, the image is aligned with the start edge at the bottom of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM | Not resized, the image is horizontally centered at the bottom of the container.|
| ARKUI_OBJECT_FIT_NONE_AND_ALIGN_BOTTOM_END | Not resized, the image is aligned with the end edge at the bottom of the container.|
| ARKUI_OBJECT_FIT_NONE_MATRIX | The image maintains its original size. Must be used with **NODE_IMAGE_IMAGE_MATRIX**.<br>**Since**: 21|

### ArkUI_ImageInterpolation

```c
enum ArkUI_ImageInterpolation
```

**Description**


Enumerates the image interpolation effects.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_IMAGE_INTERPOLATION_NONE = 0 | No image interpolation.|
| ARKUI_IMAGE_INTERPOLATION_LOW | Low quality interpolation.|
| ARKUI_IMAGE_INTERPOLATION_MEDIUM | Medium quality interpolation.|
| ARKUI_IMAGE_INTERPOLATION_HIGH | High quality interpolation. This mode produces scaled images of the highest possible quality.|

### ArkUI_DynamicRangeMode

```c
enum ArkUI_DynamicRangeMode
```

**Description**


Enumerates the dynamic range modes (for example, SDR/HDR) for images, controlling the display range of image brightness and color gamut.

**Since**: 21

| Value| Description|
| -- | -- |
| ARKUI_DYNAMIC_RANGE_MODE_HIGH = 0 | High dynamic range (HDR), representing the range between minimum and maximum brightness values in an image. A wider range makes image brightness closer to real-world conditions, preventing overexposure (all white) in bright environments and loss of detail (all black) in dark environments.|
| ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT | Constrained high dynamic range, offering richer brightness and color than SDR while maintaining SDR compatibility. Typically used in scenarios requiring SDR backward compatibility.|
| ARKUI_DYNAMIC_RANGE_MODE_STANDARD | Standard dynamic range (SDR), featuring a limited brightness range (typically 0-100 nits) with reduced contrast between bright and dark areas. Dark areas may lose detail to black, while bright areas may become overexposed to white.|

### ArkUI_ImageRotateOrientation

```c
enum ArkUI_ImageRotateOrientation
```

**Description**


Enumerates image rotation directions.

**Since**: 21

| Value| Description|
| -- | -- |
| ARKUI_ORIENTATION_AUTO = 0 | Use EXIF metadata for display orientation, with support for rotation and mirroring.|
| ARKUI_ORIENTATION_UP | Display original pixel data without transformation.|
| ARKUI_ORIENTATION_RIGHT | Display the image after rotating it 90 degrees clockwise.|
| ARKUI_ORIENTATION_DOWN  | Display the image after rotating it 180 degrees clockwise.|
| ARKUI_ORIENTATION_LEFT | Display the image after rotating it 270 degrees clockwise.|
| ARKUI_ORIENTATION_UP_MIRRORED | Display the image after flipping it horizontally.|
| ARKUI_ORIENTATION_RIGHT_MIRRORED  | Display the image after flipping it horizontally and then rotating it 90 degrees clockwise.|
| ARKUI_ORIENTATION_DOWN_MIRRORED | Display the image after flipping it vertically.|
| ARKUI_ORIENTATION_LEFT_MIRRORED | Display the image after flipping it horizontally and then rotating it 270 degrees clockwise.|

### ArkUI_BlendMode

```c
enum ArkUI_BlendMode
```

**Description**


Enumerates the blend modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_BLEND_MODE_NONE = 0 | The top image is superimposed on the bottom image without any blending.|
| ARKUI_BLEND_MODE_CLEAR = 1 | The target pixels covered by the source pixels are erased by being turned to completely transparent.|
| ARKUI_BLEND_MODE_SRC = 2 | r = s: Only the source pixels are displayed.|
| ARKUI_BLEND_MODE_DST = 3 | r = d: Only the target pixels are displayed.|
| ARKUI_BLEND_MODE_SRC_OVER = 4 | r = s + (1 - sa) * d: The source pixels are blended based on opacity and cover the target pixels.|
| ARKUI_BLEND_MODE_DST_OVER = 5 | r = d + (1 - da) * s: The target pixels are blended based on opacity and cover on the source pixels.|
| ARKUI_BLEND_MODE_SRC_IN = 6 | r = s * da: Only the part of the source pixels that overlap with the target pixels is displayed.|
| ARKUI_BLEND_MODE_DST_IN = 7 | r = d * sa: Only the part of the target pixels that overlap with the source pixels is displayed.|
| ARKUI_BLEND_MODE_SRC_OUT = 8 | r = s * (1 - da): Only the part of the source pixels that do not overlap with the target pixels is displayed.|
| ARKUI_BLEND_MODE_DST_OUT = 9 | r = d * (1 - sa): Only the part of the target pixels that do not overlap with the source pixels is displayed.|
| ARKUI_BLEND_MODE_SRC_ATOP = 10 | r = s * da + d * (1 - sa): The part of the source pixels that overlap with the target pixels is displayed and the part of the target pixels that do not overlap with the source pixels are displayed.|
| ARKUI_BLEND_MODE_DST_ATOP = 11 | r = d * sa + s * (1 - da): The part of the target pixels that overlap with the source pixels and the part of the source pixels that do not overlap with the target pixels are displayed.|
| ARKUI_BLEND_MODE_XOR = 12 | r = s * (1 - da) + d * (1 - sa): Only the non-overlapping part between the source pixels and the target pixels is displayed.|
| ARKUI_BLEND_MODE_PLUS = 13 | r = min(s + d, 1): New pixels resulting from adding the source pixels to the target pixels are displayed.|
| ARKUI_BLEND_MODE_MODULATE = 14 | r = s * d: New pixels resulting from multiplying the source pixels with the target pixels are displayed.|
| ARKUI_BLEND_MODE_SCREEN = 15 | r = s + d - s * d: Pixels are blended by adding the source pixels to the target pixels and subtracting the product of their multiplication.|
| ARKUI_BLEND_MODE_OVERLAY = 16 | The MULTIPLY or SCREEN mode is used based on the target pixels.|
| ARKUI_BLEND_MODE_DARKEN = 17 | rc = s + d - max(s * da, d * sa), ra = kSrcOver: When two colors overlap, whichever is darker is used.|
| ARKUI_BLEND_MODE_LIGHTEN = 18 | rc = s + d - min(s * da, d * sa), ra = kSrcOver: The darker of the pixels (source and target) is used.|
| ARKUI_BLEND_MODE_COLOR_DODGE = 19 | The colors of the target pixels are lightened to reflect the source pixels.|
| ARKUI_BLEND_MODE_COLOR_BURN = 20 | The colors of the target pixels are darkened to reflect the source pixels.|
| ARKUI_BLEND_MODE_HARD_LIGHT = 21 | The MULTIPLY or SCREEN mode is used, depending on the source pixels.|
| ARKUI_BLEND_MODE_SOFT_LIGHT = 22 | The LIGHTEN or DARKEN mode is used, depending on the source pixels.|
| ARKUI_BLEND_MODE_DIFFERENCE = 23 | rc = s + d - 2 * (min(s * da, d * sa)), ra = kSrcOver: The final pixel is the result of subtracting the darker of the two pixels (source and target) from the lighter one.|
| ARKUI_BLEND_MODE_EXCLUSION = 24 | rc = s + d - two(s * d), ra = kSrcOver: The final pixel is similar to <b>DIFFERENCE</b>, but with less contrast.|
| ARKUI_BLEND_MODE_MULTIPLY = 25 | r = s * (1 - da) + d * (1 - sa) + s * d: The final pixel is the result of multiplying the source pixel by the target pixel.|
| ARKUI_BLEND_MODE_HUE = 26 | The resultant image is created with the luminance and saturation of the source image and the hue of the target image.|
| ARKUI_BLEND_MODE_SATURATION = 27 | The resultant image is created with the luminance and hue of the target image and the saturation of the source image.|
| ARKUI_BLEND_MODE_COLOR = 28 | The resultant image is created with the saturation and hue of the source image and the luminance of the target image.|
| ARKUI_BLEND_MODE_LUMINOSITY = 29 | The resultant image is created with the saturation and hue of the target image and the luminance of the source image.|

### ArkUI_Direction

```c
enum ArkUI_Direction
```

**Description**


Enumerates the modes in which components are laid out along the main axis of the container.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_DIRECTION_LTR = 0 | Components are arranged from left to right.|
| ARKUI_DIRECTION_RTL = 1 | Components are arranged from right to left.|
| ARKUI_DIRECTION_AUTO = 3 | The default layout direction is used.|

### ArkUI_ItemAlignment

```c
enum ArkUI_ItemAlignment
```

**Description**


Enumerates the modes in which components are laid out along the cross axis of the container.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ITEM_ALIGNMENT_AUTO = 0 | The default configuration of the flex container is used.|
| ARKUI_ITEM_ALIGNMENT_START = 1 | The items in the flex container are aligned with the cross-start edge.|
| ARKUI_ITEM_ALIGNMENT_CENTER = 2 | The items in the flex container are centered along the cross axis.|
| ARKUI_ITEM_ALIGNMENT_END = 3 | The items in the flex container are aligned with the cross-end edge.|
| ARKUI_ITEM_ALIGNMENT_STRETCH = 4 | The items in the flex container are stretched and padded along the cross axis.|
| ARKUI_ITEM_ALIGNMENT_BASELINE = 5 | The items in the flex container are aligned in such a manner that their text baselines are aligned along the cross axis.|

### ArkUI_ColorStrategy

```c
enum ArkUI_ColorStrategy
```

**Description**


Enumerates the foreground colors.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_COLOR_STRATEGY_INVERT = 0 | The foreground colors are the inverse of the component background colors.|
| ARKUI_COLOR_STRATEGY_AVERAGE = 1 | The shadow colors of the component are the average color obtained from the component background shadow area.|
| ARKUI_COLOR_STRATEGY_PRIMARY = 2 | The shadow colors of the component are the primary color obtained from the component background shadow area.|

### ArkUI_FlexAlignment

```c
enum ArkUI_FlexAlignment
```

**Description**


Enumerates the vertical alignment modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_FLEX_ALIGNMENT_START = 1 | The child components are aligned with the start edge of the main axis.|
| ARKUI_FLEX_ALIGNMENT_CENTER = 2 | The child components are aligned in the center of the main axis.|
| ARKUI_FLEX_ALIGNMENT_END = 3 | The child components are aligned with the end edge of the main axis.|
| ARKUI_FLEX_ALIGNMENT_SPACE_BETWEEN = 6 | The child components are evenly distributed along the main axis. The space between any two adjacent components is the same. The first component is aligned with the main-start, and the last component is aligned with the main-end.|
| ARKUI_FLEX_ALIGNMENT_SPACE_AROUND = 7 | The child components are evenly distributed along the main axis. The space between any two adjacent components is the same. The space between the first component and main-start, and that between the last component and cross-main are both half the size of the space between two adjacent components.|
| ARKUI_FLEX_ALIGNMENT_SPACE_EVENLY = 8 | The child components are evenly distributed along the main axis. The space between the first component and main-start, the space between the last component and main-end, and the space between any two adjacent components are the same.|

### ArkUI_FlexDirection

```c
enum ArkUI_FlexDirection
```

**Description**


Enumerates the directions of the main axis in the flex container.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_FLEX_DIRECTION_ROW = 0 | The child components are arranged in the same direction as the main axis runs along the rows.|
| ARKUI_FLEX_DIRECTION_COLUMN = 1 | The child components are arranged in the same direction as the main axis runs down the columns.|
| ARKUI_FLEX_DIRECTION_ROW_REVERSE = 2 | The child components are arranged opposite to the **ROW** direction.|
| ARKUI_FLEX_DIRECTION_COLUMN_REVERSE = 3 | The child components are arranged opposite to the **COLUMN** direction.|

### ArkUI_FlexWrap

```c
enum ArkUI_FlexWrap
```

**Description**


Defines whether the flex container has a single line or multiple lines.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_FLEX_WRAP_NO_WRAP = 0 | The child components in the flex container are arranged in a single line, and they cannot overflow.|
| ARKUI_FLEX_WRAP_WRAP = 1 | The child components in the flex container are arranged in multiple lines, and they may overflow.|
| ARKUI_FLEX_WRAP_WRAP_REVERSE = 2 | The child components in the flex container are reversely arranged in multiple lines, and they may overflow.|

### ArkUI_Visibility

```c
enum ArkUI_Visibility
```

**Description**


Enumerates the visibility values.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_VISIBILITY_VISIBLE = 0 | The component is visible.|
| ARKUI_VISIBILITY_HIDDEN = 1 | The component is hidden, and a placeholder is used for it in the layout.|
| ARKUI_VISIBILITY_NONE = 2 | The component is hidden. It is not involved in the layout, and no placeholder is used for it.|

### ArkUI_CalendarAlignment

```c
enum ArkUI_CalendarAlignment
```

**Description**


Enumerates the alignment modes between the calendar picker and the entry component.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_CALENDAR_ALIGNMENT_START = 0 | Left aligned.|
| ARKUI_CALENDAR_ALIGNMENT_CENTER | Center aligned.|
| ARKUI_CALENDAR_ALIGNMENT_END | Right aligned.|

### ArkUI_MaskType

```c
enum ArkUI_MaskType
```

**Description**


Enumerates the mask types.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_MASK_TYPE_RECTANGLE = 0 | Rectangle.|
| ARKUI_MASK_TYPE_CIRCLE = 1 | Circle.|
| ARKUI_MASK_TYPE_ELLIPSE = 2 | Ellipse.|
| ARKUI_MASK_TYPE_PATH = 3 | Path.|
| ARKUI_MASK_TYPE_PROGRESS = 4 | Progress indicator.|

### ArkUI_ClipType

```c
enum ArkUI_ClipType
```

**Description**


Enumerates the clipping region types.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_CLIP_TYPE_RECTANGLE = 0 | Rectangle.|
| ARKUI_CLIP_TYPE_CIRCLE = 1 | Circle.|
| ARKUI_CLIP_TYPE_ELLIPSE = 2 | Ellipse.|
| ARKUI_CLIP_TYPE_PATH = 3 | Path.|

### ArkUI_ShapeType

```c
enum ArkUI_ShapeType
```

**Description**


Enumerates custom shape types.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SHAPE_TYPE_RECTANGLE = 0 | Rectangle.|
| ARKUI_SHAPE_TYPE_CIRCLE = 1 | Circle.|
| ARKUI_SHAPE_TYPE_ELLIPSE = 2 | Ellipse.|
| ARKUI_SHAPE_TYPE_PATH = 3 | Path.|

### ArkUI_LinearGradientDirection

```c
enum ArkUI_LinearGradientDirection
```

**Description**

Enumerates the gradient directions.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT = 0 | From right to left.|
| ARKUI_LINEAR_GRADIENT_DIRECTION_TOP = 1 | From bottom to top.|
| ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT = 2 | From left to right.|
| ARKUI_LINEAR_GRADIENT_DIRECTION_BOTTOM = 3 | From top to bottom.|
| ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_TOP = 4 | From lower right to upper left.|
| ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM = 5 | From upper right to lower left.|
| ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT_TOP = 6 | From lower left to upper right.|
| ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT_BOTTOM = 7 | From upper left to lower right.|
| ARKUI_LINEAR_GRADIENT_DIRECTION_NONE = 8 | No gradient.|
| ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM = 9 | Custom direction.|

### ArkUI_WordBreak

```c
enum ArkUI_WordBreak
```

**Description**


Enumerates the word break rules.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_WORD_BREAK_NORMAL = 0 | Word breaks can occur between any two characters for Chinese, Japanese, and Korean (CJK) text, but can occur only at a space character for non-CJK text (such as English).|
| ARKUI_WORD_BREAK_BREAK_ALL | Word breaks can occur between any two characters for non-CJK text. CJK text behavior is the same as for **NORMAL**.|
| ARKUI_WORD_BREAK_BREAK_WORD | This option has the same effect as **BREAK_ALL** for non-CJK text, except that if it preferentially wraps lines at appropriate characters (for example, spaces) whenever possible. CJK text behavior is the same as for **NORMAL**.|
| ARKUI_WORD_BREAK_HYPHENATION | Line breaks can occur between any two syllabic units for non-CJK text. CJK text behavior is the same as for **NORMAL**.<br>**Since**: 18|

### ArkUI_EllipsisMode

```c
enum ArkUI_EllipsisMode
```

**Description**


Enumerates the ellipsis positions.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ELLIPSIS_MODE_START = 0 | An ellipsis is used at the start of the line of text.|
| ARKUI_ELLIPSIS_MODE_CENTER | An ellipsis is used at the center of the line of text.|
| ARKUI_ELLIPSIS_MODE_END | An ellipsis is used at the end of the line of text.|

### ArkUI_ImageRenderMode

```c
enum ArkUI_ImageRenderMode
```

**Description**


Enumerates the image rendering modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_IMAGE_RENDER_MODE_ORIGINAL = 0 | Render image pixels as they are in the original source image.|
| ARKUI_IMAGE_RENDER_MODE_TEMPLATE | Render image pixels to create a monochrome template image.|

### ArkUI_TransitionEdge

```c
enum ArkUI_TransitionEdge
```

**Description**


Enumerates the slide-in and slide-out positions of the component from the screen edge during transition.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TRANSITION_EDGE_TOP = 0 | Top edge of the window.|
| ARKUI_TRANSITION_EDGE_BOTTOM = 1 | Bottom edge of the window.|
| ARKUI_TRANSITION_EDGE_START = 2 | Left edge of the window.|
| ARKUI_TRANSITION_EDGE_END = 3 | Right edge of the window.|

### ArkUI_FinishCallbackType

```c
enum ArkUI_FinishCallbackType
```

**Description**


Enumerates the animation **onFinish** callback types.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_FINISH_CALLBACK_REMOVED = 0 | The callback is invoked when the entire animation is removed once it has finished.|
| ARKUI_FINISH_CALLBACK_LOGICALLY = 1 | The callback is invoked when the animation logically enters the falling state, though it may still be in its long tail state.|

### ArkUI_ListItemAlignment

```c
enum ArkUI_ListItemAlignment
```

**Description**


Enumerates the alignment modes of items along the cross axis.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_LIST_ITEM_ALIGNMENT_START = 0 | The list items are packed toward the start edge of the **List** component along the cross axis.|
| ARKUI_LIST_ITEM_ALIGNMENT_CENTER = 1 | The list items are centered in the **List** component along the cross axis.|
| ARKUI_LIST_ITEM_ALIGNMENT_END = 2 | The list items are packed toward the end edge of the **List** component along the cross axis.|

### ArkUI_BlendApplyType

```c
enum ArkUI_BlendApplyType
```

**Description**


Defines how the specified blend mode is applied.

**Since**: 12

| Value| Description|
| -- | -- |
| BLEND_APPLY_TYPE_FAST = 0 | The content of the view is blended in sequence on the target image.|
| BLEND_APPLY_TYPE_OFFSCREEN = 1 | The content of the component and its child components are drawn on the offscreen canvas, and then blended with the existing content on the canvas. |

### ArkUI_LengthMetricUnit

```c
enum ArkUI_LengthMetricUnit
```

**Description**


Enumerates the component units.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_LENGTH_METRIC_UNIT_DEFAULT = -1 | Default, which is fp for fonts and vp for non-fonts.|
| ARKUI_LENGTH_METRIC_UNIT_PX = 0 | px.|
| ARKUI_LENGTH_METRIC_UNIT_VP = 1 | vp.|
| ARKUI_LENGTH_METRIC_UNIT_FP = 2 | fp.|

### ArkUI_TextInputContentType

```c
enum ArkUI_TextInputContentType
```

**Description**


Enumerates the autofill types.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TEXTINPUT_CONTENT_TYPE_USER_NAME = 0 | Username. Password Vault, when enabled, can automatically save and fill in usernames.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSWORD | Password. Password Vault, when enabled, can automatically save and fill in passwords.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_NEW_PASSWORD | New password. Password Vault, when enabled, can automatically generate a new password.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_STREET_ADDRESS | Full street address. The scenario-based autofill feature, when enabled, can automatically save and fill in full street addresses.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_HOUSE_NUMBER | House number. The scenario-based autofill feature, when enabled, can automatically save and fill in house numbers.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_DISTRICT_ADDRESS | District and county. The scenario-based autofill feature, when enabled, can automatically save and fill in districts and counties.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_CITY_ADDRESS | City. The scenario-based autofill feature, when enabled, can automatically save and fill in cities.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PROVINCE_ADDRESS | Province. The scenario-based autofill feature, when enabled, can automatically save and fill in provinces.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_COUNTRY_ADDRESS | Country. The scenario-based autofill feature, when enabled, can automatically save and fill in countries.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FULL_NAME | Full name. The scenario-based autofill feature, when enabled, can automatically save and fill in full names.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_LAST_NAME | Last name. The scenario-based autofill feature, when enabled, can automatically save and fill in last names.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FIRST_NAME | First name. The scenario-based autofill feature, when enabled, can automatically save and fill in first names.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_NUMBER | Phone number. The scenario-based autofill feature, when enabled, can automatically save and fill in phone numbers.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_COUNTRY_CODE | Country code. The scenario-based autofill feature, when enabled, can automatically save and fill in country codes.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_PHONE_NUMBER | Phone number with country code. The scenario-based autofill feature, when enabled, can automatically save and fill in phone numbers with country codes.|
| ARKUI_TEXTINPUT_CONTENT_EMAIL_ADDRESS | Email address. The scenario-based autofill feature, when enabled, can automatically save and fill in email addresses.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_BANK_CARD_NUMBER | Bank card number. The scenario-based autofill feature, when enabled, can automatically save and fill in bank card numbers.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_ID_CARD_NUMBER | ID card number. The scenario-based autofill feature, when enabled, can automatically save and fill in ID card numbers.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_NICKNAME | Nickname. The scenario-based autofill feature, when enabled, can automatically save and fill in nicknames.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_DETAIL_INFO_WITHOUT_STREET | Address information without street address. The scenario-based autofill feature, when enabled, can automatically save and fill in address information without street addresses.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_FORMAT_ADDRESS | Standard address. The scenario-based autofill feature, when enabled, can automatically save and fill in standard addresses.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSPORT_NUMBER | Passport number. The scenario-based autofill feature, when enabled, can automatically save and fill in passport numbers.<br>**Since**: 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_VALIDITY | Passport validity period. The scenario-based autofill feature, when enabled, can automatically save and fill in passport validity periods.<br>**Since**: 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_ISSUE_AT | Passport place of issue. The scenario-based autofill feature, when enabled, can automatically save and fill in the place of issue for passports.<br>**Since**: 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_ORGANIZATION | Invoice title. The scenario-based autofill feature, when enabled, can automatically save and fill in invoice titles.<br>**Since**: 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_TAX_ID | Tax ID. The scenario-based autofill feature, when enabled, can automatically save and fill in tax IDs.<br>**Since**: 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_ADDRESS_CITY_AND_STATE | Location. The scenario-based autofill feature, when enabled, can automatically save and fill in locations.<br>**Since**: 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_FLIGHT_NUMBER | Flight number. Currently not supported for automatic saving and auto-filling.<br>**Since**: 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_NUMBER | Driver's license number. Currently not supported for automatic saving and auto-filling.<br>**Since**: 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_FILE_NUMBER | Driver's license file number. Currently not supported for automatic saving and auto-filling.<br>**Since**: 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_PLATE | License plate number. The scenario-based autofill feature, when enabled, can automatically save and fill in license plate numbers.<br>**Since**: 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_ENGINE_NUMBER | Vehicle registration engine number. Currently not supported for automatic saving and auto-filling.<br>**Since**: 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER | Chassis number. Currently not supported for automatic saving and auto-filling.<br>**Since**: 18|

### ArkUI_BarrierDirection

```c
enum ArkUI_BarrierDirection
```

**Description**


Enumerates the barrier directions.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_BARRIER_DIRECTION_START = 0 | The barrier is on the left side of all the referenced components specified by referencedId.|
| ARKUI_BARRIER_DIRECTION_END = 1 | The barrier is on the right side of all the referenced components specified by referencedId.|
| ARKUI_BARRIER_DIRECTION_TOP = 2 | The barrier is at the top of all the referenced components specified by referencedId.|
| ARKUI_BARRIER_DIRECTION_BOTTOM = 3 | The barrier is at the bottom of all the referenced components specified by referencedId.|

### ArkUI_RelativeLayoutChainStyle

```c
enum ArkUI_RelativeLayoutChainStyle
```

**Description**


Enumerates the chain styles.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_RELATIVE_LAYOUT_CHAIN_STYLE_SPREAD = 0 | Child components are evenly distributed among constraint anchors.|
| ARKUI_RELATIVE_LAYOUT_CHAIN_STYLE_SPREAD_INSIDE = 1 | All child components except the first and last ones are evenly distributed among constraint anchors.|
| ARKUI_RELATIVE_LAYOUT_CHAIN_STYLE_PACKED = 2 | There is no gap between child components in the chain.|

### ArkUI_TextInputStyle

```c
enum ArkUI_TextInputStyle
```

**Description**


Enumerates the text input styles.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TEXTINPUT_STYLE_DEFAULT = 0 | Default style. The caret width is fixed at 1.5 vp, and the caret height is subject to the background height and font size of the selected text.|
| ARKUI_TEXTINPUT_STYLE_INLINE | Inline input style. The background height of the selected text is the same as the height of the text box.|

### ArkUI_KeyboardAppearance

```c
enum ArkUI_KeyboardAppearance
```

**Description**


Enumerates the appearance modes of the keyboard when the text box is focused.

**Since**: 15

| Value| Description|
| -- | -- |
| ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE = 0 | Default appearance mode, not using the immersive style.|
| ARKUI_KEYBOARD_APPEARANCE_IMMERSIVE = 1 | Immersive style, following the system color mode.|
| ARKUI_KEYBOARD_APPEARANCE_LIGHT_IMMERSIVE = 2 | Immersive style in light mode.|
| ARKUI_KEYBOARD_APPEARANCE_DARK_IMMERSIVE = 3 | Immersive style in dark mode.|

### ArkUI_TextDataDetectorType

```c
enum ArkUI_TextDataDetectorType
```

**Description**


Enumerates the entity types of text recognition.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_PHONE_NUMBER = 0 | Phone number.|
| ARKUI_TEXT_DATA_DETECTOR_TYPE_URL | URL.|
| ARKUI_TEXT_DATA_DETECTOR_TYPE_EMAIL | Email address.|
| ARKUI_TEXT_DATA_DETECTOR_TYPE_ADDRESS | Address.|

### ArkUI_ButtonType

```c
enum ArkUI_ButtonType
```

**Description**


Enumerates the button types.

**Since**: 12

| Value| Description                     |
| -- |-------------------------|
| ARKUI_BUTTON_TYPE_NORMAL = 0 | Normal button (without rounded corners by default).           |
| ARKUI_BUTTON_TYPE_CAPSULE = 1 | Capsule-type button (the round corner is half of the height by default).      |
| ARKUI_BUTTON_TYPE_CIRCLE = 2 | Circle button.                  |
| ARKUI_BUTTON_ROUNDED_RECTANGLE = 8 | Rounded rectangle button<br>**Since**: 19|

### ArkUI_RenderFit

```c
enum ArkUI_RenderFit
```

**Description**


Enumerates the sizing and positioning behaviors of animated content in its final state.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_RENDER_FIT_CENTER = 0 | The component's content stays at the final size and always aligned with the center of the component.|
| ARKUI_RENDER_FIT_TOP = 1 | The component's content stays at the final size and always aligned with the top center of the component.|
| ARKUI_RENDER_FIT_BOTTOM = 2 | The component's content stays at the final size and always aligned with the bottom center of the component.|
| ARKUI_RENDER_FIT_LEFT = 3 | The component's content stays at the final size and always aligned with the left of the component.|
| ARKUI_RENDER_FIT_RIGHT = 4 | The component's content stays at the final size and always aligned with the right of the component.|
| ARKUI_RENDER_FIT_TOP_LEFT = 5 | The component's content stays at the final size and always aligned with the upper left corner of the component.|
| ARKUI_RENDER_FIT_TOP_RIGHT = 6 | The component's content stays at the final size and always aligned with the upper right corner of the component.|
| ARKUI_RENDER_FIT_BOTTOM_LEFT = 7 | The component's content stays at the final size and always aligned with the lower left corner of the component.|
| ARKUI_RENDER_FIT_BOTTOM_RIGHT = 8 | The component's content stays at the final size and always aligned with the lower right corner of the component.|
| ARKUI_RENDER_FIT_RESIZE_FILL = 9 | The component's content is always resized to fill the component's content box, without considering its aspect ratio in the final state.|
| ARKUI_RENDER_FIT_RESIZE_CONTAIN = 10 | While maintaining its aspect ratio in the final state, the component's content is scaled to fit within the component's content box. It is always aligned with the center of the component.|
| ARKUI_RENDER_FIT_RESIZE_CONTAIN_TOP_LEFT = 11 | While maintaining its aspect ratio in the final state, the component's content is scaled to fit within the component's content box. When there is remaining space in the width direction of the component, the content is left-aligned with the component. When there is remaining space in the height direction of the component, the content is top-aligned with the component.|
| ARKUI_RENDER_FIT_RESIZE_CONTAIN_BOTTOM_RIGHT = 12 | While maintaining its aspect ratio in the final state, the component's content is scaled to fit within the component's content box. When there is remaining space in the width direction of the component, the content is right-aligned with the component. When there is remaining space in the height direction of the component, the content is bottom-aligned with the component.|
| ARKUI_RENDER_FIT_RESIZE_COVER = 13 | While maintaining its aspect ratio in the final state, the component's content is scaled to cover the component's entire content box. It is always aligned with the center of the component, so that its middle part is displayed.|
| ARKUI_RENDER_FIT_RESIZE_COVER_TOP_LEFT = 14 | While maintaining its aspect ratio in the final state, the component's content is scaled to cover the component's entire content box. When there is remaining space in the width direction, the content is left-aligned with the component, so that its left part is displayed. When there is remaining space in the height direction, the content is top-aligned with the component, so that its top part is displayed.|
| ARKUI_RENDER_FIT_RESIZE_COVER_BOTTOM_RIGHT = 15 | While maintaining its aspect ratio in the final state, the component's content is scaled to cover the component's entire content box. When there is remaining space in the width direction, the content is right-aligned with the component, so that its right part is displayed. When there is remaining space in the height direction, the content is bottom-aligned with the component, so that its bottom part is displayed.|

### ArkUI_SwiperIndicatorType

```c
enum ArkUI_SwiperIndicatorType
```

**Description**


Enumerates the navigation indicator types of the **Swiper** component.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SWIPER_INDICATOR_TYPE_DOT = 0 | Dot type.|
| ARKUI_SWIPER_INDICATOR_TYPE_DIGIT = 1 | Digit type.|

### ArkUI_AnimationDirection

```c
enum ArkUI_AnimationDirection
```

**Description**


Enumerates the animation playback modes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ANIMATION_DIRECTION_NORMAL = 0 | The animation plays in forward loop mode.|
| ARKUI_ANIMATION_DIRECTION_REVERSE = 1 | The animation plays in reverse loop mode.|
| ARKUI_ANIMATION_DIRECTION_ALTERNATE = 2 | The animation plays in alternating loop mode. When the animation is played for an odd number of times, the playback is in forward direction. When the animation is played for an even number of times, the playback is in reverse direction.|
| ARKUI_ANIMATION_DIRECTION_ALTERNATE_REVERSE = 3 | The animation plays in reverse alternating loop mode. When the animation is played for an odd number of times, the playback is in reverse direction. When the animation is played for an even number of times, the playback is in forward direction.|

### ArkUI_ListItemSwipeActionState

```c
enum ArkUI_ListItemSwipeActionState
```

**Description**


Enumerates the swipe action item states of list items.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED = 0 | Collapsed state. When the list item is swiped in the opposite direction of the main axis, the swipe action item is hidden.|
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_EXPANDED = 1 | Expanded state. When the list item is swiped in the opposite direction of the main axis, the swipe action item is shown.|
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_ACTIONING = 2 | In-action state. The list item is in this state when it enters the delete area.|

### ArkUI_ListItemSwipeEdgeEffect

```c
enum ArkUI_ListItemSwipeEdgeEffect
```

**Description**


Enumerates the swipe action item edge effects of list items.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING = 0 | When the list item scrolls to the edge of the list, it can continue to scroll for a distance.|
| ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_NONE = 1 | The list item cannot scroll beyond the edge of the list.|

### ArkUI_ListItemSwipeActionDirection

```c
enum ArkUI_ListItemSwipeActionDirection
```

**Description**

Enumerates the swipe action menu display directions for **ListItem** components.

**Since**: 21

| Value| Description|
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_START = 0 | For vertical lists: left side in LTR mode, right side in RTL mode. For horizontal lists: top side.|
| ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_END = 1 | For vertical lists: right side in LTR mode, left side in RTL mode. For horizontal lists: bottom side.|

### ArkUI_AnimationStatus

```c
enum ArkUI_AnimationStatus
```

**Description**


Enumerates the playback states of the frame-by-frame animation.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ANIMATION_STATUS_INITIAL = 0 | The animation is in the initial state.|
| ARKUI_ANIMATION_STATUS_RUNNING = 1 | The animation is being played.|
| ARKUI_ANIMATION_STATUS_PAUSED = 2 | The animation is paused.|
| ARKUI_ANIMATION_STATUS_STOPPED = 3 | The animation is stopped.|

### ArkUI_AnimationFillMode

```c
enum ArkUI_AnimationFillMode
```

**Description**


Enumerates the states before and after execution of the frame-by-frame animation.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ANIMATION_FILL_MODE_NONE = 0 | Before execution, the animation does not apply any styles to the target component. After execution, the animation restores the target component to its default state.|
| ARKUI_ANIMATION_FILL_MODE_FORWARDS = 1 | The target component retains the state set by the last keyframe encountered during execution of the animation.|
| ARKUI_ANIMATION_FILL_MODE_BACKWARDS = 2 | The animation applies the values defined in the first relevant keyframe once it is applied to the target component, and retains the values during the period set by **delay**.|
| ARKUI_ANIMATION_FILL_MODE_BOTH = 3 | The animation follows the rules for both **Forwards** and **Backwards**, extending the animation attributes in both directions.|

### ArkUI_ErrorCode

```c
enum ArkUI_ErrorCode
```

**Description**


Enumerates the error codes.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ERROR_CODE_NO_ERROR = 0 | No error.|
| ARKUI_ERROR_CODE_PARAM_INVALID = 401 | Parameter error.|
| ARKUI_ERROR_CODE_CAPI_INIT_ERROR = 500 |  API initialization error.<br>**Since**: 18|
| ARKUI_ERROR_CODE_INTERNAL_ERROR = 100001 |  Internal error, such as failure due to internal environment issues or operation failure caused by internal execution errors.<br>**Since**: 15|
| ARKUI_ERROR_CODE_PARAM_ERROR = 100023 |  Parameter error. For details, see [Custom Node Error Codes](../apis-arkui/errorcode-node.md).<br>**Since**: 21|
| ARKUI_ERROR_CODE_XCOMPONENT_STATE_INVALID = 103501 |  The **XComponent** is in an invalid or unsupported state. For details, see [XComponent Error Codes](../apis-arkui/errorcode-xcomponent.md).<br>**Since**: 19|
| ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED = 106102 | The component does not support specific attributes or events. For details, see [Interaction Event Error Codes](../apis-arkui/errorcode-event.md).|
| ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED = 106103 | The specific operation is not allowed on the node created by ArkTS. For details, see [Custom Node Error Codes](../apis-arkui/errorcode-node.md).|
| ARKUI_ERROR_CODE_ADAPTER_NOT_BOUND = 106104 | The adapter for lazy loading is not bound to the component. For details, see [106104 Adapter Not Bound](../apis-arkui/errorcode-nodeadapter.md#106104-adapter-not-bound).|
| ARKUI_ERROR_CODE_ADAPTER_EXIST = 106105 | The adapter already exists. For details, see [106105 Adapter Already Exists](../apis-arkui/errorcode-nodeadapter.md#106105-adapter-already-exists).|
| ARKUI_ERROR_CODE_CHILD_NODE_EXIST = 106106 | Failed to add the adapter because the corresponding node already has a subnode. For details, see [106106 Child Node Exists](../apis-arkui/errorcode-nodeadapter.md#106106-child-node-exists).|
| ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE = 106107 | The parameter length in the parameter event exceeds the limit. For details, see [106107 Index Out of Range](../apis-arkui/errorcode-nodeadapter.md#106107-index-out-of-range).|
| ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID = 106108 | The data does not exist in the component event. For details, see [106108 Data Not Found](../apis-arkui/errorcode-nodeadapter.md#106108-data-not-found).|
| ARKUI_ERROR_CODE_NODE_EVENT_NO_RETURN = 106109 | The component event does not support return values. For details, see [106109 Return Value Not Supported](../apis-arkui/errorcode-nodeadapter.md#106109-return-value-not-supported).|
| ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE = 106110 | This event type is not supported. For details, see [106110 Unsupported Event Type](../apis-arkui/errorcode-nodeadapter.md#106110-unsupported-event-type).<br>**Since**: 21|
| ARKUI_ERROR_CODE_NODE_INDEX_INVALID = 106200 | Invalid index.<br>For details, see [Router Error Codes](../apis-arkui/errorcode-router.md#106200-invalid-index-value).|
| ARKUI_ERROR_CODE_GET_INFO_FAILED = 106201 | Failed to obtain the route navigation information.<br>For details, see [Router Error Codes](../apis-arkui/errorcode-router.md#106201-failed-to-obtain-route-navigation-information).|
| ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR = 106202 | Invalid buffer size.<br>For details, see [Router Error Codes](../apis-arkui/errorcode-router.md#106202-invalid-buffer-size).|
| ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE = 106203 |  The passed node is not mounted to the component tree. For details, see [Custom Node Error Codes](../apis-arkui/errorcode-node.md).<br>**Since**: 15|
| ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD = 106204 |  Operations on the provided node are not supported on non-UI threads. For details, see [Custom Node Error Codes](../apis-arkui/errorcode-node.md#106204-operations-on-the-provided-node-not-supported-on-non-ui-threads).<br>**Since**: 22|
| ARKUI_ERROR_CODE_FORCE_DARK_CONFIG_INVALID = 106205 |  The input parameter for the color inversion capability is incorrect. For details, see [Color Inversion Error Codes](../apis-arkui/errorcode-force-dark.md).<br>**Since**: 20|
| ARKUI_ERROR_CODE_NODE_IS_ADOPTED = 106206 |  The node has been accepted as an auxiliary node. For details, see [Auxiliary Node Error Codes](../apis-arkui/errorcode-adopt.md#106206-the-node-has-been-accepted-as-an-auxiliary-node).<br>**Since**: 22|
| ARKUI_ERROR_CODE_NODE_HAS_PARENT = 106207 |  The accepted node already has a parent node. For details, see [Auxiliary Node Error Codes](../apis-arkui/errorcode-adopt.md#106207-the-auxiliary-node-to-accept-has-a-parent-node).<br>**Since**: 22|
| ARKUI_ERROR_CODE_NODE_CAN_NOT_BE_ADOPTED = 106208 |  The node cannot be accepted as an auxiliary node. For details, see [Auxiliary Node Error Codes](../apis-arkui/errorcode-adopt.md#106208-the-node-cannot-be-accepted-as-an-auxiliary-node).<br>**Since**: 22|
| ARKUI_ERROR_CODE_NODE_CAN_NOT_ADOPT_TO = 106209 |  The node cannot accept other nodes. For details, see [Auxiliary Node Error Codes](../apis-arkui/errorcode-adopt.md#106209-the-node-cannot-accept-other-nodes).<br>**Since**: 22|
| ARKUI_ERROR_CODE_NODE_IS_NOT_IN_ADOPTED_CHILDREN = 106210 |  The node is not an auxiliary node accepted by the target node. For details, see [Auxiliary Node Error Codes](../apis-arkui/errorcode-adopt.md#106210-the-node-is-not-an-affiliated-node-accepted-by-the-target-node).<br>**Since**: 22|
| ARKUI_ERROR_CODE_NOT_CUSTOM_NODE = 106401 |  The current node is not a custom node. For details, see [Render Node Error Codes](../apis-arkui/errorcode-node-render.md).<br>**Since**: 20|
| ARKUI_ERROR_CODE_CHILD_EXISTED = 106402 |  The current node already has child nodes. For details, see [Render Node Error Codes](../apis-arkui/errorcode-node-render.md).<br>**Since**: 20|
| ARKUI_ERROR_CODE_RENDER_PARENT_EXISTED = 106403 |  The current render node has a parent component. For details, see [Render Node Error Codes](../apis-arkui/errorcode-node-render.md).<br>**Since**: 20|
| ARKUI_ERROR_CODE_RENDER_CHILD_NOT_EXIST = 106404 |  Corresponding render child node not found. For details, see [Render Node Error Codes](../apis-arkui/errorcode-node-render.md).<br>**Since**: 20|
| ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE = 106405 |  The parameter value is out of range. For details, see [Render Node Error Codes](../apis-arkui/errorcode-node-render.md).<br>**Since**: 20|
| ARKUI_ERROR_CODE_RENDER_IS_FROM_FRAME_NODE = 106406 |  The current render node is obtained from a FrameNode. For details, see [Render Node Error Codes](../apis-arkui/errorcode-node-render.md#106406-current-render-node-is-obtained-from-framenode).<br>**Since**: 22|
| ARKUI_ERROR_CODE_RENDER_HAS_INVALID_FRAME_NODE = 106407 |  The current render node is obtained from **FrameNode**, and the **FrameNode** has been disposed or no longer adopted. For details, see [Render Node Error Codes](../apis-arkui/errorcode-node-render.md#106407-current-render-node-is-obtained-from-framenode-and-the-framenode-is-disposed-or-no-longer-adopted).<br>**Since**: 22|
| ARKUI_ERROR_CODE_RENDER_NOT_ADOPTED_NODE = 106408 |  The current node is not in the adopted state. For details, see [Render Node Error Codes](../apis-arkui/errorcode-node-render.md#106408-current-node-is-not-in-adopted-state).<br>**Since**: 22|
| ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE = 150001 |  The current node is not focusable. For details, see [Focus Error Codes](../apis-arkui/errorcode-focus.md#150001-component-not-focusable).<br>**Since**: 15|
| ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE_ANCESTOR = 150002 |  An ancestor of the current node is not focusable. For details, see [Focus Error Codes](../apis-arkui/errorcode-focus.md#150002-ancestor-component-not-focusable).<br>**Since**: 15|
| ARKUI_ERROR_CODE_FOCUS_NON_EXISTENT = 150003 |  The current node does not exist. For details, see [Focus Error Codes](../apis-arkui/errorcode-focus.md#150003-component-does-not-exist).<br>**Since**: 15|
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT = 160002 |  Snapshot timed out. For details, see [Snapshot Error Codes](../apis-arkui/errorcode-snapshot.md).<br>**Since**: 15|
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_MODE_NOT_SUPPORTED = 160003 | The provided color space or dynamic range mode is not supported. For details, see [Snapshot Error Codes](../apis-arkui/errorcode-snapshot.md).<br>**Since**: 23|
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_AUTO_NOT_SUPPORTED = 160004 | The **isAuto** setting of the color space or dynamic range mode is not supported for offscreen node snapshots. For details, see [Snapshot Error Codes](../apis-arkui/errorcode-snapshot.md).<br>**Since**: 23|
| ARKUI_ERROR_CODE_NON_SCROLLABLE_CONTAINER = 180001 | The component is not a scrollable container. For details, see [Interaction Event Error Codes](../apis-arkui/errorcode-event.md).|
| ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH = 180002 | The buffer is not large enough. For details, see [Interaction Event Error Codes](../apis-arkui/errorcode-event.md).|
| ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT = 180003 |  The event is not a cloned event. For details, see [Interaction Event Error Codes](../apis-arkui/errorcode-event.md).<br>**Since**: 15|
| ARKUI_ERROR_CODE_POST_CLONED_COMPONENT_STATUS_ABNORMAL = 180004 |  The component status is abnormal. For details, see [Interaction Event Error Codes](../apis-arkui/errorcode-event.md).<br>**Since**: 15|
| ARKUI_ERROR_CODE_POST_CLONED_NO_COMPONENT_HIT_TO_RESPOND_TO_THE_EVENT = 180005 |  No component hit to respond to the event. For details, see [Interaction Event Error Codes](../apis-arkui/errorcode-event.md).<br>**Since**: 15|
| ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED = 180006 |  Input event type not supported.<br>**Since**: 20|
| ARKUI_ERROR_CODE_INVALID_STYLED_STRING = 180101 |  Invalid styled string. For details, see [Styled String Error Codes](../apis-arkui/errorcode-styled-string.md).<br>**Since**: 14|
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID = 190001 |  Invalid UIContext object. For details, see [UI Context Error Codes](../apis-arkui/errorcode-uicontext.md).<br>**Since**: 18|
| ARKUI_ERROR_CODE_CALLBACK_INVALID = 190002 |  Invalid callback function. For details, see [UI Context Error Codes](../apis-arkui/errorcode-uicontext.md).<br>**Since**: 18|
| ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED = 180102 |  The gesture recognizer type is not supported. For details, see [Interaction Event Error Codes](../apis-arkui/errorcode-event.md).<br>**Since**: 18|
| ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED = 190004 |  The operation is not allowed in the current phase. For details, see [Drag Event Error Codes](../apis-arkui/errorcode-drag-event.md).<br>**Since**: 19|

### ArkUI_ScrollSource

```c
enum ArkUI_ScrollSource
```

**Description**


Enumerates scroll sources.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_SOURCE_DRAG = 0 | Finger dragging.|
| ARKUI_SCROLL_SOURCE_FLING = 1 | Inertia scrolling after finger dragging.|
| ARKUI_SCROLL_SOURCE_EDGE_EFFECT = 2 | Cross-boundary bouncing.|
| ARKUI_SCROLL_SOURCE_OTHER_USER_INPUT = 3 | User input other than dragging, such as mouse wheel and keyboard events.|
| ARKUI_SCROLL_SOURCE_SCROLL_BAR = 4 | Scrollbar dragging.|
| ARKUI_SCROLL_SOURCE_SCROLL_BAR_FLING = 5 | Inertial scrolling after scrollbar dragging.|
| ARKUI_SCROLL_SOURCE_SCROLLER = 6 | Scrolling by the scroll controller (without animation).|
| ARKUI_SCROLL_SOURCE_ANIMATION = 7 | Scrolling by the scroll controller (with animation).|

### ArkUI_SafeAreaType

```c
enum ArkUI_SafeAreaType
```

**Description**


Enumerates the types of expanded safe areas.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SAFE_AREA_TYPE_SYSTEM = 1 | Default non-safe area of the system, including the status bar and navigation bar.|
| ARKUI_SAFE_AREA_TYPE_CUTOUT = 1 << 1 | Non-safe area of the device, for example, the notch area.|
| ARKUI_SAFE_AREA_TYPE_KEYBOARD = 1 << 2 | Soft keyboard area.|

### ArkUI_SafeAreaEdge

```c
enum ArkUI_SafeAreaEdge
```

**Description**


Enumerates the edges for expanding the safe area.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_SAFE_AREA_EDGE_TOP = 1 | Top edge.|
| ARKUI_SAFE_AREA_EDGE_BOTTOM = 1 << 1 | Bottom edge.|
| ARKUI_SAFE_AREA_EDGE_START = 1 << 2 | Start edge.|
| ARKUI_SAFE_AREA_EDGE_END = 1 << 3 | End edge.|

### ArkUI_FocusMove

```c
enum ArkUI_FocusMove
```

**Description**


Enumerates the focus movement directions.

**Since**: 18

| Value| Description|
| -- | -- |
| ARKUI_FOCUS_MOVE_FORWARD = 0 | Move focus forward.|
| ARKUI_FOCUS_MOVE_BACKWARD = 1 | Move focus backward.|
| ARKUI_FOCUS_MOVE_UP = 2 | Move focus up.|
| ARKUI_FOCUS_MOVE_DOWN = 3 | Move focus down.|
| ARKUI_FOCUS_MOVE_LEFT = 4 | Move focus left.|
| ARKUI_FOCUS_MOVE_RIGHT = 5 | Move focus right.|

### ArkUI_ListItemGroupArea

```c
enum ArkUI_ListItemGroupArea
```

**Description**


Enumerates areas of the **ListItemGroup** component.

**Since**: 15

| Value| Description|
| -- | -- |
| ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE = 0 | Outside the area of the **ListItemGroup** component.|
| ARKUI_LIST_ITEM_SWIPE_AREA_NONE = 1 | Area when the **ListItemGroup** component does not have the header, footer, or list item.|
| ARKUI_LIST_ITEM_SWIPE_AREA_ITEM = 2 | List item area of the **ListItemGroup** component.|
| ARKUI_LIST_ITEM_SWIPE_AREA_HEADER = 3 | Header area of the **ListItemGroup** component.|
| ARKUI_LIST_ITEM_SWIPE_AREA_FOOTER = 4 | Footer area of the **ListItemGroup** component.|

### ArkUI_KeyboardAvoidMode

```c
enum ArkUI_KeyboardAvoidMode
```

**Description**


Enumerates the soft keyboard avoidance modes.

**Since**: 15

| Value| Description|
| -- | -- |
| ARKUI_KEYBOARD_AVOID_MODE_DEFAULT = 0 | Automatically avoids the soft keyboard and compresses the height when reaching the maximum limit.|
| ARKUI_KEYBOARD_AVOID_MODE_NONE = 1 | The layout is not adjusted to avoid the keyboard.|

### ArkUI_HoverModeAreaType

```c
enum ArkUI_HoverModeAreaType
```

**Description**


Enumerates the types of display areas for the hover mode.

**Since**: 15

| Value| Description|
| -- | -- |
| ARKUI_HOVER_MODE_AREA_TYPE_TOP = 0 | Upper half screen.|
| ARKUI_HOVER_MODE_AREA_TYPE_BOTTOM = 1 | Lower half screen.|

### ArkUI_ExpandMode

```c
enum ArkUI_ExpandMode
```

**Description**


Enumerates the expansion mode of child nodes.

**Since**: 15

| Value| Description|
| -- | -- |
| ARKUI_NOT_EXPAND = 0 | Child nodes are not expanded.|
| ARKUI_EXPAND = 1 | Child nodes are expanded immediately upon rendering.|
| ARKUI_LAZY_EXPAND = 2 | Child nodes are only expanded when needed or requested.|

### ArkUI_NavDestinationState

```c
enum ArkUI_NavDestinationState
```

**Description**


Enumerates the **NavDestination** component states.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_NAV_DESTINATION_STATE_ON_SHOW = 0 | The **NavDestination** component is displayed.|
| ARKUI_NAV_DESTINATION_STATE_ON_HIDE = 1 | The **NavDestination** component is hidden.|
| ARKUI_NAV_DESTINATION_STATE_ON_APPEAR = 2 | The **NavDestination** component is mounted to the component tree.|
| ARKUI_NAV_DESTINATION_STATE_ON_DISAPPEAR = 3 | The **NavDestination** component is unmounted from the component tree.|
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_SHOW = 4 | The **NavDestination** is about to be displayed.|
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_HIDE = 5 | The **NavDestination** is about to be hidden.|
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_APPEAR = 6 | The **NavDestination** is about to be mounted to the component tree.|
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_DISAPPEAR = 7 | The **NavDestination** component is about to be unmounted from the component tree.|
| ARKUI_NAV_DESTINATION_STATE_ON_BACK_PRESS = 100 | The back button is pressed for the **NavDestination** component.|

### ArkUI_RouterPageState

```c
enum ArkUI_RouterPageState
```

**Description**


Enumerates the states of a page during routing.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_APPEAR = 0 | The page is about to be displayed.|
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_DISAPPEAR = 1 | The page is about to be destroyed.|
| ARKUI_ROUTER_PAGE_STATE_ON_SHOW = 2 | The page is displayed.|
| ARKUI_ROUTER_PAGE_STATE_ON_HIDE = 3 | The page is hidden.|
| ARKUI_ROUTER_PAGE_STATE_ON_BACK_PRESS = 4 | The back button is pressed for the page.|

### ArkUI_UIState

```c
enum ArkUI_UIState
```

**Description**


Enumerates the UI states of a component, used for handling state-specific styles.

**Since**: 20

| Value| Description|
| -- | -- |
| UI_STATE_NORMAL = 0 | Normal state.|
| UI_STATE_PRESSED = 1 << 0 | Pressed state.|
| UI_STATE_FOCUSED = 1 << 1 | Focused state.|
| UI_STATE_DISABLED = 1 << 2 | Disabled state.|
| UI_STATE_SELECTED = 1 << 3 | Selected state. This state is supported only by specific component types: **Checkbox**, **Radio**, **Toggle**, **List**, **Grid**, and **MenuItem**.|

### ArkUI_FocusWrapMode

```c
enum ArkUI_FocusWrapMode
```

**Description**


Enumerates the focus wrap mode of components.

**Since**: 20

| Value| Description|
| -- | -- |
| ARKUI_FOCUS_WRAP_MODE_DEFAULT = 0 | Default mode, where focus does not wrap when arrow keys are used.|
| ARKUI_FOCUS_WRAP_WITH_ARROW = 1 | Auto mode, where focus wraps automatically when arrow keys are used.|

### ArkUI_ItemFillPolicy

```c
enum ArkUI_ItemFillPolicy
```

**Description**


Enumerates column count policies for different [responsive breakpoints](../../ui/arkts-layout-development-grid-layout.md#breakpoints).

**Since**: 22

| Value| Description|
| -- | -- |
| ARKUI_ITEMFILLPOLICY_NONE = -1 | No responsive breakpoint policy is set.|
| ARKUI_ITEMFILLPOLICY_DEFAULT = 0 | **List** or **Swiper** component: 1 column (SM or smaller), 2 columns (MD), 3 columns (LG or larger).<br> **Grid** or **WaterFlow** component: 2 columns (SM or smaller), 3 columns (MD), 5 columns (LG or larger).|
| ARKUI_ITEMFILLPOLICY_SM1MD2LG3 = 1 | 1 column (SM or smaller), 2 columns (MD), 3 columns (LG or larger).|
| ARKUI_ITEMFILLPOLICY_SM2MD3LG5 = 2 | 2 columns (SM or smaller), 3 columns (MD), 5 columns (LG or larger).|

### ArkUI_ScrollSnapAnimationSpeed

```c
enum ArkUI_ScrollSnapAnimationSpeed
```

**Description**


Enumerates scroll snap animation speeds for list components.

**Since**: 22

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_SNAP_ANIMATION_NORMAL = 0 | Normal scroll snap animation speed.|
| ARKUI_SCROLL_SNAP_ANIMATION_SLOW = 1 | Slow scroll snap animation speed.|

### ArkUI_EdgeDirection

```c
enum ArkUI_EdgeDirection
```

**Description**


Enumerates rectangle edge directions.

**Since**: 20

| Value| Description|
| -- | -- |
| ARKUI_EDGE_DIRECTION_ALL = 0 | All four edges.|
| ARKUI_EDGE_DIRECTION_LEFT = 1 << 0 | Left edge.|
| ARKUI_EDGE_DIRECTION_RIGHT = 1 << 1 | Right edge.|
| ARKUI_EDGE_DIRECTION_TOP = 1 << 2 | Top edge.|
| ARKUI_EDGE_DIRECTION_BOTTOM = 1 << 3 | Bottom edge.|

### ArkUI_CornerDirection

```c
enum ArkUI_CornerDirection
```

**Description**


Enumerates corner directions.

**Since**: 20

| Value| Description|
| -- | -- |
| ARKUI_CORNER_DIRECTION_ALL = 0 | All four corners.|
| ARKUI_CORNER_DIRECTION_TOP_LEFT = 1 << 0 | Upper left corner.|
| ARKUI_CORNER_DIRECTION_TOP_RIGHT = 1 << 1 | Upper right corner.|
| ARKUI_CORNER_DIRECTION_BOTTOM_LEFT = 1 << 2 | Lower left corner.|
| ARKUI_CORNER_DIRECTION_BOTTOM_RIGHT = 1 << 3 | Lower right corner.|

### ArkUI_LayoutPolicy

```c
enum ArkUI_LayoutPolicy
```

**Description**

Enumerates layout policies.

**Since**: 21

| Value| Description|
| -- | -- |
| ARKUI_LAYOUTPOLICY_MATCHPARENT = 0 | The component size matches parent container dimensions.|
| ARKUI_LAYOUTPOLICY_WRAPCONTENT = 1 | The component size wraps its content, constrained by parent container bounds.|
| ARKUI_LAYOUTPOLICY_FIXATIDEALSIZE = 2 | The component size wraps its content, unconstrained by parent container bounds.|

### ArkUI_PixelRoundCalcPolicy

```c
enum ArkUI_PixelRoundCalcPolicy
```

**Description**

Enumerates pixel rounding calculation policies.

**Since**: 21

| Value| Description|
| -- | -- |
| ARKUI_PIXELROUNDCALCPOLICY_NOFORCEROUND = 0 | No forced rounding calculation.|
| ARKUI_PIXELROUNDCALCPOLICY_FORCECEIL = 1 | Round-up calculation.|
| ARKUI_PIXELROUNDCALCPOLICY_FORCEFLOOR = 2 | Round-down calculation.|

### ArkUI_GridItemAlignment

```c
enum ArkUI_GridItemAlignment
```
**Description**

Enumerates the alignment modes of grid items.

**Since**: 22

| Value| Description|
| -- | -- |
| GRID_ITEM_ALIGNMENT_DEFAULT = 0 | Use the default alignment mode of the grid.|
| GRID_ITEM_ALIGNMENT_STRETCH  = 1  | Use the height of the tallest grid item in a row as the height for all other grid items in that row.|


### ArkUI_GridItemStyle

```c
enum ArkUI_GridItemStyle
```

**Description**


Enumerates styles of grid items.

**Since**: 22

| Value| Description|
| -- | -- |
| GRID_ITEM_STYLE_NONE  = 0 | No style.|
| GRID_ITEM_STYLE_PLAIN  = 1  | Hover or press style.|

### ArkUI_HoverEffect

```c
enum ArkUI_HoverEffect
```

**Description**


Enumerates the hover effects when a component is hovered over.

**Since**: 23

| Value| Description|
| -- | -- |
| ARKUI_HOVER_EFFECT_AUTO = 0 | Default effect.|
| ARKUI_HOVER_EFFECT_SCALE  | Zoom effect.|
| ARKUI_HOVER_EFFECT_HIGHLIGHT  | Highlight effect.|
| ARKUI_HOVER_EFFECT_NONE  | No effect.|

### ArkUI_FocusPriority

```c
enum ArkUI_FocusPriority
```

**Description**


Enumerates the priority levels for focus management within the application. These levels determine the sequence in which UI components receive focus during user interaction.

**Since**: 23

| Value| Description|
| -- | -- |
| ARKUI_FOCUS_PRIORITY_AUTO  = 0 | Default priority.|
| ARKUI_FOCUS_PRIORITY_PRIOR = 2000   | Priority that indicates the component is prioritized in the container.|
| ARKUI_FOCUS_PRIORITY_PREVIOUS = 3000   | Priority of a previously focused node in the container.|

### ArkUI_MenuPolicy

```c
enum ArkUI_MenuPolicy
```

**Description**

Enumerates menu display policies.

**Since**: 23

| Value| Description|
| -- | -- |
| ARKUI_MENU_POLICY_DEFAULT  = 0 | Whether the menu is displayed depends on the underlying default logic.|
| ARKUI_MENU_POLICY_HIDE = 1 | The menu is not popped up.|
| ARKUI_MENU_POLICY_SHOW = 2 | The menu is popped up.|

### ArkUI_ResponseRegionSupportedTool

```c
enum ArkUI_ResponseRegionSupportedTool
```

**Description**


Enumerates the input tool types supported for response region configuration.

**Since**: 23

| Value| Description|
| -- | -- |
| ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL  = 0 | All.|
| ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_FINGER  = 1  | Finger.|
| ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_PEN  = 2  | Stylus.|
| ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_MOUSE  = 3  | Mouse.|

### ArkUI_TextMenuItemId

```c
enum ArkUI_TextMenuItemId
```

**Description**

Enumerates the IDs of text menu items.

**Since**: 22

| Value| Description|
| -- | -- |
| ARKUI_TEXT_MENU_ITEM_ID_CUT = 0 | Clip.|
| ARKUI_TEXT_MENU_ITEM_ID_COPY = 1 | Copy.|
| ARKUI_TEXT_MENU_ITEM_ID_PASTE = 2 | Paste.|
| ARKUI_TEXT_MENU_ITEM_ID_SELECT_ALL = 3 | Select all.|
| ARKUI_TEXT_MENU_ITEM_ID_COLLABORATION_SERVICE = 4 | Collaboration service. For example, cross-device interaction, including cross-device camera access.|
| ARKUI_TEXT_MENU_ITEM_ID_CAMERA_INPUT = 5 | Camera input.|
| ARKUI_TEXT_MENU_ITEM_ID_AI_WRITER = 6 | AI-assisted writing. This menu item requires the large language model. If no large language model is available, this menu item does not take effect.|
| ARKUI_TEXT_MENU_ITEM_ID_TRANSLATE = 7 | Translate. The translation service is provided for the selected text.|
| ARKUI_TEXT_MENU_ITEM_ID_SEARCH = 8 | Search. This menu item launches a browser to search for the selected text.|
| ARKUI_TEXT_MENU_ITEM_ID_SHARE = 9 | Share. This menu item launches a window for sharing the selected text.|
| ARKUI_TEXT_MENU_ITEM_ID_URL = 10 | Open a link. This menu item provides the redirection service for the selected URL, launching a browser search or application page.|
| ARKUI_TEXT_MENU_ITEM_ID_EMAIL = 11 | New Email. This menu item provides the redirection service for the selected email address, launching the email application.|
| ARKUI_TEXT_MENU_ITEM_ID_PHONE_NUMBER = 12 | Call. This menu item provides the redirection service for the selected phone number, launching the phone dialer page.|
| ARKUI_TEXT_MENU_ITEM_ID_ADDRESS = 13 | Navigate. This menu item provides the redirection service for the selected address, launching the map application.|
| ARKUI_TEXT_MENU_ITEM_ID_DATA_TIME = 14 | New event. This menu item provides the redirection service for the selected date and time, launching the page for creating a calendar event.|
| ARKUI_TEXT_MENU_ITEM_ID_ASK_AI = 15 | Ask AI. This menu item provides the AI query capability for the selected text.|
| ARKUI_TEXT_MENU_ITEM_ID_APP_RESERVED_BEGIN = 10000 | Start ID of a custom menu item. In addition to the built-in menu item IDs, you can also customize menu item IDs.|
| ARKUI_TEXT_MENU_ITEM_ID_APP_RESERVED_END = 20000 | End ID of a custom menu item. In addition to the built-in menu item IDs, you can also customize menu item IDs.|

### ArkUI_TextSpanType

```c
enum ArkUI_TextSpanType
```

**Description**

Enumerates the recognition types of a custom text selection menu.

**Since**: 22

| Value| Description|
| -- | -- |
| ARKUI_TEXT_SPAN_TYPE_TEXT = 0 | Text.|
| ARKUI_TEXT_SPAN_TYPE_IMAGE = 1 | Image.|
| ARKUI_TEXT_SPAN_TYPE_MIXED = 2 | Mixed text and image.|
| ARKUI_TEXT_SPAN_TYPE_DEFAULT = 3 | If this type and other types are set, the menu corresponding to the type of the selected text is displayed after the text is selected. If this type is set but other types are not set, the menu corresponding to this type is displayed after the text is selected. For example, if there are two menus whose recognition types are **ARKUI_TEXT_SPAN_TYPE_TEXT** and **ARKUI_TEXT_SPAN_TYPE_DEFAULT** respectively, the menu corresponding to **ARKUI_TEXT_SPAN_TYPE_TEXT** is displayed when the text is selected, and the menu corresponding to **ARKUI_TEXT_SPAN_TYPE_DEFAULT** is displayed when the image is selected.|

### ArkUI_TextResponseType

```c
enum ArkUI_TextResponseType
```

**Description**

Enumerates the response types of a custom text selection menu.

**Since**: 22

| Value| Description|
| -- | -- |
| ARKUI_TEXT_RESPONSE_TYPE_RIGHT_CLICK = 0 | The menu is displayed when the component is right-clicked.|
| ARKUI_TEXT_RESPONSE_TYPE_LONG_PRESS = 1 | The menu is displayed when the component is long-pressed.|
| ARKUI_TEXT_RESPONSE_TYPE_SELECT = 2 | The menu is displayed when the component is selected.|
| ARKUI_TEXT_RESPONSE_TYPE_DEFAULT = 3 | If this type and other types are set, the menu corresponding to the type is displayed when the operation of another type is triggered. If this type is set but other types are not set, the menu corresponding to this type is displayed when an operation of another type is triggered. For example, if there are two menus whose response types are **ARKUI_TEXT_RESPONSE_TYPE_RIGHT_CLICK** and **ARKUI_TEXT_RESPONSE_TYPE_DEFAULT** respectively, the menu corresponding to **ARKUI_TEXT_RESPONSE_TYPE_RIGHT_CLICK** is displayed when you right-click the menu, and the menu corresponding to **ARKUI_TEXT_RESPONSE_TYPE_DEFAULT** is displayed when you hold down the right mouse button.|

### ArkUI_MarqueeStartPolicy
```c
enum ArkUI_MarqueeStartPolicy
```

**Description**

Defines the start policy of a marquee.

**Since**: 23

| Value| Description|
| -- | -- |
| ARKUI_MARQUEESTARTPOLICY_DEFAULT = 0 | The marquee scrolls continuously by default.|
| ARKUI_MARQUEESTARTPOLICY_ONFOCUS = 1 | The marquee scrolls when the focus is obtained or the mouse pointer is hovered over.|

### ArkUI_MarqueeUpdatePolicy
```c
enum ArkUI_MarqueeUpdatePolicy
```

**Description**

Defines the update policy of a marquee.

**Since**: 23

| Value| Description|
| -- | -- |
| ARKUI_MARQUEEUPDATEPOLICY_DEFAULT = 0 | After the marquee attributes are updated, the marquee scrolls from the start position.|
| ARKUI_MARQUEEUPDATEPOLICY_PRESERVEPOSITION = 1 | After the marquee attributes are updated, the marquee scrolls from the current position.|

### ArkUI_LayoutSafeAreaType

```c
enum ArkUI_LayoutSafeAreaType
```

**Description**


Enumerates the types of expanded safe areas.

**Since**: 23

| Value| Description|
| -- | -- |
| ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM = 1 | Default non-safe area of the system, including the status bar and navigation bar.|

### ArkUI_LayoutSafeAreaEdge

```c
enum ArkUI_LayoutSafeAreaEdge
```

**Description**


Enumerates the edges for expanding the safe area.

**Since**: 23

| Value| Description|
| -- | -- |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP = 1 | Top edge.|
| ARKUI_LAYOUT_SAFE_AREA_EDGE_BOTTOM = 1 << 1 | Bottom edge.|
| ARKUI_LAYOUT_SAFE_AREA_EDGE_START = 1 << 2 | Start edge.|
| ARKUI_LAYOUT_SAFE_AREA_EDGE_END = 1 << 3 | End edge.|
| ARKUI_LAYOUT_SAFE_AREA_EDGE_VERTICAL = ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_BOTTOM = 3 | Vertical edge.|
| ARKUI_LAYOUT_SAFE_AREA_EDGE_HORIZONTAL = ARKUI_LAYOUT_SAFE_AREA_EDGE_START \| ARKUI_LAYOUT_SAFE_AREA_EDGE_END = 12 | Horizontal edge.|
| ARKUI_LAYOUT_SAFE_AREA_EDGE_ALL = ARKUI_LAYOUT_SAFE_AREA_EDGE_VERTICAL \| ARKUI_LAYOUT_SAFE_AREA_EDGE_HORIZONTAL = 15 | All edges.|

### ArkUI_LocalizedAlignment

```c
enum ArkUI_LocalizedAlignment
```

**Description**


Defines the alignment rules of child components in a **Stack** container.

**Since**: 23

| Value| Description|
| -- | -- |
| ARKUI_LOCALIZED_ALIGNMENT_TOP_START = 0 | Top start.|
| ARKUI_LOCALIZED_ALIGNMENT_TOP = 1 | Top center.|
| ARKUI_LOCALIZED_ALIGNMENT_TOP_END = 2 | Top end.|
| ARKUI_LOCALIZED_ALIGNMENT_START = 3 | Vertically centered start.|
| ARKUI_LOCALIZED_ALIGNMENT_CENTER = 4 | Horizontally and vertically centered.|
| ARKUI_LOCALIZED_ALIGNMENT_END= = 5 | Vertically centered end.|
| ARKUI_LOCALIZED_ALIGNMENT_BOTTOM_START = 6 | Bottom start.|
| ARKUI_LOCALIZED_ALIGNMENT_BOTTOM = 7 | Horizontally centered on the bottom.|
| ARKUI_LOCALIZED_ALIGNMENT_BOTTOM_END = 8 | Bottom end.|

### ArkUI_RenderStrategy

```c
enum ArkUI_RenderStrategy
```

**Description**


Enumerates strategies for drawing rounded corners.

**Since**: 23

| Value| Description|
| -- | -- |
| ARKUI_RENDERSTRATEGY_FAST  = 0 | Online drawing mode.|
| ARKUI_RENDERSTRATEGY_OFFSCREEN = 1 | Off-screen drawing mode.|

### ArkUI_PickerIndicatorType

``` c
enum ArkUI_PickerIndicatorType
```

**Description**

Defines the indicator type of the selected item.

**Since**: 23

| Value| Description|
| -- | -- |
| ARKUI_PICKER_INDICATOR_BACKGROUND  = 0 | Background.|
| ARKUI_PICKER_INDICATOR_DIVIDER  = 1 | Divider.|

## Function Description

### OH_ArkUI_LayoutConstraint_Create()

```c
ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Create()
```

**Description**


Creates a size constraint.

**Since**: 12

**Returns**

| Type                         | Description|
|-----------------------------| -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* | Pointer to the object of the constraint size.|

### OH_ArkUI_LayoutConstraint_Copy()

```c
ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Copy(const ArkUI_LayoutConstraint* Constraint)
```

**Description**


Performs a deep copy of a size constraint.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|

**Returns**

| Type                         | Description|
|-----------------------------| -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* | Pointer to the new size constraint.|

### OH_ArkUI_LayoutConstraint_Dispose()

```c
void* OH_ArkUI_LayoutConstraint_Dispose(ArkUI_LayoutConstraint* Constraint)
```

**Description**


Disposes of the pointer to a size constraint.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|

**Returns**

| Type                         | Description|
|-----------------------------| -- |
| void* | Null pointer.|

### OH_ArkUI_LayoutConstraint_GetMaxWidth()

```c
int32_t OH_ArkUI_LayoutConstraint_GetMaxWidth(const ArkUI_LayoutConstraint* Constraint)
```

**Description**


Obtains the maximum width for a size constraint, in px.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Maximum width.|

### OH_ArkUI_LayoutConstraint_GetMinWidth()

```c
int32_t OH_ArkUI_LayoutConstraint_GetMinWidth(const ArkUI_LayoutConstraint* Constraint)
```

**Description**


Obtains the minimum width for a size constraint, in px.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Minimum Width|

### OH_ArkUI_LayoutConstraint_GetMaxHeight()

```c
int32_t OH_ArkUI_LayoutConstraint_GetMaxHeight(const ArkUI_LayoutConstraint* Constraint)
```

**Description**


Obtains the maximum height for a size constraint, in px.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Maximum height.|

### OH_ArkUI_LayoutConstraint_GetMinHeight()

```c
int32_t OH_ArkUI_LayoutConstraint_GetMinHeight(const ArkUI_LayoutConstraint* Constraint)
```

**Description**


Obtains the minimum height for a size constraint, in px.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Minimum height.|

### OH_ArkUI_LayoutConstraint_GetPercentReferenceWidth()

```c
int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceWidth(const ArkUI_LayoutConstraint* Constraint)
```

**Description**


Obtains the width percentage reference for a size constraint, in px.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Width percentage reference.|

### OH_ArkUI_LayoutConstraint_GetPercentReferenceHeight()

```c
int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceHeight(const ArkUI_LayoutConstraint* Constraint)
```

**Description**


Obtains the height percentage reference for a size constraint, in px.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Height percentage reference.|

### OH_ArkUI_LayoutConstraint_SetMaxWidth()

```c
void OH_ArkUI_LayoutConstraint_SetMaxWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**Description**


Sets the maximum width.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|
| int32_t value | Maximum width, in pixels.|

### OH_ArkUI_LayoutConstraint_SetMinWidth()

```c
void OH_ArkUI_LayoutConstraint_SetMinWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**Description**


Sets the minimum width.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|
| int32_t value | Minimum width, in px.|

### OH_ArkUI_LayoutConstraint_SetMaxHeight()

```c
void OH_ArkUI_LayoutConstraint_SetMaxHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**Description**


Sets the maximum height.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|
| int32_t value | Maximum height, in px.|

### OH_ArkUI_LayoutConstraint_SetMinHeight()

```c
void OH_ArkUI_LayoutConstraint_SetMinHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**Description**


Sets the minimum height.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|
| int32_t value | Minimum height, in px.|

### OH_ArkUI_LayoutConstraint_SetPercentReferenceWidth()

```c
void OH_ArkUI_LayoutConstraint_SetPercentReferenceWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**Description**


Sets the width percentage reference.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|
| int32_t value | Width percentage reference, in px.|

### OH_ArkUI_LayoutConstraint_SetPercentReferenceHeight()

```c
void OH_ArkUI_LayoutConstraint_SetPercentReferenceHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**Description**


Sets the height percentage reference.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | Size constraint.|
| int32_t value | Height percentage reference, in px.|

### OH_ArkUI_DrawContext_GetCanvas()

```c
void* OH_ArkUI_DrawContext_GetCanvas(ArkUI_DrawContext* context)
```

**Description**


Obtains the pointer to a canvas for drawing, which can be converted into the **OH_Drawing_Canvas** in the **Drawing** module.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawContext](capi-arkui-nativemodule-arkui-drawcontext.md)* context | Drawing context.|

**Returns**

| Type| Description|
| -- | -- |
| void* | Pointer to the canvas for drawing.|

### OH_ArkUI_DrawContext_GetSize()

```c
ArkUI_IntSize OH_ArkUI_DrawContext_GetSize(ArkUI_DrawContext* context)
```

**Description**


Obtains the size of a drawing area.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawContext](capi-arkui-nativemodule-arkui-drawcontext.md)* context | Drawing context.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md) | Size of the drawing area.|

### OH_ArkUI_WaterFlowSectionOption_Create()

```c
ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create()
```

**Description**


Creates a water flow section configuration.

**Since**: 12

**Returns**

| Type                               | Description|
|-----------------------------------| -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* | Pointer to a water flow section configuration.|

### OH_ArkUI_WaterFlowSectionOption_Dispose()

```c
void OH_ArkUI_WaterFlowSectionOption_Dispose(ArkUI_WaterFlowSectionOption* option)
```

**Description**


Disposes of the pointer to a water flow section configuration.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|

### OH_ArkUI_WaterFlowSectionOption_SetSize()

```c
void OH_ArkUI_WaterFlowSectionOption_SetSize(ArkUI_WaterFlowSectionOption* option,int32_t size)
```

**Description**


Sets the array length for a water flow section configuration.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t size | Size of the array.|

### OH_ArkUI_WaterFlowSectionOption_GetSize()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetSize(ArkUI_WaterFlowSectionOption* option)
```

**Description**


Obtains the array length for a water flow section configuration.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Size of the array. If **-1** is returned, an error code indicating failure is returned. The possible cause is that the **option** parameter is abnormal, for example, a null pointer.|

### OH_ArkUI_WaterFlowSectionOption_SetItemCount()

```c
void OH_ArkUI_WaterFlowSectionOption_SetItemCount(ArkUI_WaterFlowSectionOption* option,int32_t index, int32_t itemCount)
```

**Description**


Sets the number of items in a water flow section.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|
| int32_t itemCount | Number of items in the water flow section.|

### OH_ArkUI_WaterFlowSectionOption_GetItemCount()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**


Obtains the number of items in the water flow section that matches the specified index.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Number of items in the water flow section.|

### OH_ArkUI_WaterFlowSectionOption_SetCrossCount()

```c
void OH_ArkUI_WaterFlowSectionOption_SetCrossCount(ArkUI_WaterFlowSectionOption* option,int32_t index, int32_t crossCount)
```

**Description**


Sets the number of columns (in a vertical layout) or rows (in a horizontal layout) of a water flow.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|
| int32_t crossCount | Number of columns or rows, depending on the layout direction.|

### OH_ArkUI_WaterFlowSectionOption_GetCrossCount()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**


Obtains the number of columns (in a vertical layout) or rows (in a horizontal layout) of a water flow.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Number of columns or rows, depending on the layout direction.|

### OH_ArkUI_WaterFlowSectionOption_SetColumnGap()

```c
void OH_ArkUI_WaterFlowSectionOption_SetColumnGap(ArkUI_WaterFlowSectionOption* option,int32_t index, float columnGap)
```

**Description**


Sets the gap between columns in the specified water flow section.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|
| float columnGap | Gap between columns.|

### OH_ArkUI_WaterFlowSectionOption_GetColumnGap()

```c
float OH_ArkUI_WaterFlowSectionOption_GetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**


Obtains the gap between columns in the water flow section that matches the specified index.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|

**Returns**

| Type| Description|
| -- | -- |
| float | Gap between columns.|

### OH_ArkUI_WaterFlowSectionOption_SetRowGap()

```c
void OH_ArkUI_WaterFlowSectionOption_SetRowGap(ArkUI_WaterFlowSectionOption* option,int32_t index, float rowGap)
```

**Description**


Sets the gap between rows in the specified water flow section.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|
| float rowGap | Gap between rows.|

### OH_ArkUI_WaterFlowSectionOption_GetRowGap()

```c
float OH_ArkUI_WaterFlowSectionOption_GetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**


Obtains the gap between rows in the water flow section that matches the specified index.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|

**Returns**

| Type| Description|
| -- | -- |
| float | Gap between rows.|

### OH_ArkUI_WaterFlowSectionOption_SetMargin()

```c
void OH_ArkUI_WaterFlowSectionOption_SetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index,float marginTop, float marginRight, float marginBottom, float marginLeft)
```

**Description**


Sets the margins for the specified water flow section.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|
| float marginTop | Top margin of the water flow section.|
| float marginRight | Right margin of the water flow section.|
| float marginBottom | Bottom margin of the water flow section.|
| float marginLeft | Left margin of the water flow section.|

### OH_ArkUI_WaterFlowSectionOption_GetMargin()

```c
ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**


Obtains the margins of the water flow section that matches the specified index.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) | Margins.|

### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex()

```c
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex(ArkUI_WaterFlowSectionOption* option,int32_t index, float(*callback)(int32_t itemIndex))
```

**Description**


Obtains the main axis size of a specified item based on **flowItemIndex** through a water flow section configuration.

**Since**: 12


**Parameters**

| Name                                           | Description|
|------------------------------------------------| -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index                                  | Index of the target water flow section.|
| callback                                       | Callback used to return the result. **itemIndex**: index of the target water flow section.|

### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData()

```c
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData(ArkUI_WaterFlowSectionOption* option, int32_t index, void* userData,float (*callback)(int32_t itemIndex, void* userData))
```

**Description**


Obtains the main axis size of a specified item based on **flowItemIndex** through a water flow section configuration.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|
|  void* userData | Custom data of the water flow item.|
| callback | Callback used to return the result. **itemIndex**: index of the target water flow section.|

### OH_ArkUI_GuidelineOption_Create()

```c
ArkUI_GuidelineOption* OH_ArkUI_GuidelineOption_Create(int32_t size)
```

**Description**


Creates a guideline configuration for this **RelativeContainer** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| int32_t size | Number of guidelines.|

**Returns**

| Type                        | Description|
|----------------------------| -- |
| [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md)* | Pointer to a guideline configuration.|

### OH_ArkUI_GuidelineOption_Dispose()

```c
void OH_ArkUI_GuidelineOption_Dispose(ArkUI_GuidelineOption* guideline)
```

**Description**


Disposes of a guideline configuration.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md)* guideline | Pointer to a guideline configuration.|

### OH_ArkUI_GuidelineOption_SetId()

```c
void OH_ArkUI_GuidelineOption_SetId(ArkUI_GuidelineOption* guideline, const char* value, int32_t index)
```

**Description**


Sets the ID of a guideline.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md)* guideline | Pointer to a guideline configuration.|
| const char* value | ID, which must be unique and cannot be the same as the name of any component in the container.|
| int32_t index | Index of the guideline.|

### OH_ArkUI_GuidelineOption_SetDirection()

```c
void OH_ArkUI_GuidelineOption_SetDirection(ArkUI_GuidelineOption* guideline, ArkUI_Axis value, int32_t index)
```

**Description**


Sets the direction of a guideline.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md)* guideline | Pointer to a guideline configuration.|
| [ArkUI_Axis](capi-native-type-h.md#arkui_axis) value | Direction. |
| int32_t index | Index of the guideline.|

### OH_ArkUI_GuidelineOption_SetPositionStart()

```c
void OH_ArkUI_GuidelineOption_SetPositionStart(ArkUI_GuidelineOption* guideline, float value, int32_t index)
```

**Description**


Sets the distance between a guideline and the left or top of the container.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md)* guideline | Pointer to a guideline configuration.|
| float value | Distance between the guideline and the left or top of the container.|
| int32_t index | Index of the guideline.|

### OH_ArkUI_GuidelineOption_SetPositionEnd()

```c
void OH_ArkUI_GuidelineOption_SetPositionEnd(ArkUI_GuidelineOption* guideline, float value, int32_t index)
```

**Description**


Sets the distance between a guideline and the right or bottom of the container.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md)* guideline | Pointer to a guideline configuration.|
| float value | Distance between the guideline and the right or bottom of the container.|
| int32_t index | Index of the guideline.|

### OH_ArkUI_GuidelineOption_GetId()

```c
const char* OH_ArkUI_GuidelineOption_GetId(ArkUI_GuidelineOption* guideline, int32_t index)
```

**Description**


Obtains the ID of a guideline.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md)* guideline | Pointer to a guideline configuration.|
| int32_t index | Index of the guideline.|

**Returns**

| Type| Description|
| -- | -- |
| const char* | ID of the guideline.|

### OH_ArkUI_GuidelineOption_GetDirection()

```c
ArkUI_Axis OH_ArkUI_GuidelineOption_GetDirection(ArkUI_GuidelineOption* guideline, int32_t index)
```

**Description**


Obtains the direction of a guideline.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md)* guideline | Pointer to a guideline configuration.|
| int32_t index | Index of the guideline.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_Axis](capi-native-type-h.md#arkui_axis) | Direction. |

### OH_ArkUI_GuidelineOption_GetPositionStart()

```c
float OH_ArkUI_GuidelineOption_GetPositionStart(ArkUI_GuidelineOption* guideline, int32_t index)
```

**Description**


Obtains the distance between the guideline and the left or top of the container.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md)* guideline | Pointer to a guideline configuration.|
| int32_t index | Index of the guideline.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance between the guideline and the left or top of the container. The unit is vp.|

### OH_ArkUI_GuidelineOption_GetPositionEnd()

```c
float OH_ArkUI_GuidelineOption_GetPositionEnd(ArkUI_GuidelineOption* guideline, int32_t index)
```

**Description**


Obtains the distance between the guideline and the right or bottom of the container.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GuidelineOption](capi-arkui-nativemodule-arkui-guidelineoption.md)* guideline | Pointer to a guideline configuration.|
| int32_t index | Index of the guideline.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance between the guideline and the right or bottom of the container. The unit is vp.|

### OH_ArkUI_BarrierOption_Create()

```c
ArkUI_BarrierOption* OH_ArkUI_BarrierOption_Create(int32_t size)
```

**Description**


Creates a barrier configuration for this **RelativeContainer** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| int32_t size | Number of barriers.|

**Returns**

| Type                      | Description|
|--------------------------| -- |
| [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md)* | Returns the barrier configuration.|

### OH_ArkUI_BarrierOption_Dispose()

```c
void OH_ArkUI_BarrierOption_Dispose(ArkUI_BarrierOption* barrierStyle)
```

**Description**


Disposes of a barrier configuration.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md)* barrierStyle | Returns the barrier configuration.|

### OH_ArkUI_BarrierOption_SetId()

```c
void OH_ArkUI_BarrierOption_SetId(ArkUI_BarrierOption* barrierStyle, const char* value, int32_t index)
```

**Description**


Sets the ID of a barrier.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md)* barrierStyle | Returns the barrier configuration.|
| const char* value | ID, which must be unique and cannot be the same as the name of any component in the container.|
| int32_t index | Index of the barrier.|

### OH_ArkUI_BarrierOption_SetDirection()

```c
void OH_ArkUI_BarrierOption_SetDirection(ArkUI_BarrierOption* barrierStyle, ArkUI_BarrierDirection value, int32_t index)
```

**Description**


Sets the direction of a barrier.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md)* barrierStyle | Returns the barrier configuration.|
| [ArkUI_BarrierDirection](capi-native-type-h.md#arkui_barrierdirection) value | Direction. |
| int32_t index | Index of the barrier.|

### OH_ArkUI_BarrierOption_SetReferencedId()

```c
void OH_ArkUI_BarrierOption_SetReferencedId(ArkUI_BarrierOption* barrierStyle, const char* value, int32_t index)
```

**Description**


Sets the referenced components of a barrier.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md)* barrierStyle | Returns the barrier configuration.|
| const char* value | Referenced component IDs.|
| int32_t index | Index of the barrier.|

### OH_ArkUI_BarrierOption_GetId()

```c
const char* OH_ArkUI_BarrierOption_GetId(ArkUI_BarrierOption* barrierStyle, int32_t index)
```

**Description**


Obtains the ID of a barrier.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md)* barrierStyle | Pointer to a guideline configuration.|
| int32_t index | Index of the guideline.|

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns the ID of the barrier.|

### OH_ArkUI_BarrierOption_GetDirection()

```c
ArkUI_BarrierDirection OH_ArkUI_BarrierOption_GetDirection(ArkUI_BarrierOption* barrierStyle, int32_t index)
```

**Description**


Obtains the direction of a barrier.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md)* barrierStyle | Pointer to a guideline configuration.|
| int32_t index | Index of the guideline.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_BarrierDirection](capi-native-type-h.md#arkui_barrierdirection) | Returns the direction of the barrier.|

### OH_ArkUI_BarrierOption_GetReferencedId()

```c
const char* OH_ArkUI_BarrierOption_GetReferencedId(ArkUI_BarrierOption* barrierStyle, int32_t index , int32_t referencedIndex)
```

**Description**


Obtains the referenced components of a barrier.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md)* barrierStyle | Pointer to a guideline configuration.|
| int32_t index | Index of the guideline.|
| int32_t referencedIndex | Index of the referenced component ID.|

**Returns**

| Type| Description|
| -- | -- |
| const char* | Referenced components of the barrier.|

### OH_ArkUI_BarrierOption_GetReferencedIdSize()

```c
int32_t OH_ArkUI_BarrierOption_GetReferencedIdSize(ArkUI_BarrierOption* barrierStyle, int32_t index)
```

**Description**


Obtains the number of referenced components of a barrier.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_BarrierOption](capi-arkui-nativemodule-arkui-barrieroption.md)* barrierStyle | Pointer to a guideline configuration.|
| int32_t index | Index of the guideline.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Number of referenced components of the barrier.|

### OH_ArkUI_AlignmentRuleOption_Create()

```c
ArkUI_AlignmentRuleOption* OH_ArkUI_AlignmentRuleOption_Create()
```

**Description**


Creates an alignment rule configuration for this **RelativeContainer** component.

**Since**: 12

**Returns**

| Type                            | Description|
|--------------------------------| -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* | Alignment rule information.|

### OH_ArkUI_AlignmentRuleOption_Dispose()

```c
void OH_ArkUI_AlignmentRuleOption_Dispose(ArkUI_AlignmentRuleOption* option)
```

**Description**


Disposes of an alignment rule configuration of this **RelativeContainer** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

### OH_ArkUI_AlignmentRuleOption_SetStart()

```c
void OH_ArkUI_AlignmentRuleOption_SetStart(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)
```

**Description**


Sets the left alignment parameters.

**Since**: 12


**Parameters**

| Name                                                                                      | Description|
|-------------------------------------------------------------------------------------------| -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|
| const char* id                                                                            | ID of the component that functions as the anchor point.|
| [ArkUI_HorizontalAlignment](#arkui_horizontalalignment) alignment                         | Alignment mode relative to the anchor component.|

### OH_ArkUI_AlignmentRuleOption_SetEnd()

```c
void OH_ArkUI_AlignmentRuleOption_SetEnd(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)
```

**Description**


Sets the right alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|
| const char* id | ID of the component that functions as the anchor point.|
| [ArkUI_HorizontalAlignment](#arkui_horizontalalignment) alignment | Alignment mode relative to the anchor component.|

### OH_ArkUI_AlignmentRuleOption_SetCenterHorizontal()

```c
void OH_ArkUI_AlignmentRuleOption_SetCenterHorizontal(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)
```

**Description**


Sets the horizontal center alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|
| const char* id | ID of the component that functions as the anchor point.|
| [ArkUI_HorizontalAlignment](#arkui_horizontalalignment) alignment | Alignment mode relative to the anchor component.|

### OH_ArkUI_AlignmentRuleOption_SetTop()

```c
void OH_ArkUI_AlignmentRuleOption_SetTop(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)
```

**Description**


Sets the top alignment parameters.

**Since**: 12


**Parameters**

| Name                                                                                      | Description|
|-------------------------------------------------------------------------------------------| -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|
| const char* id                                                                            | ID of the component that functions as the anchor point.|
| [ArkUI_VerticalAlignment](#arkui_verticalalignment) alignment                             | Alignment mode relative to the anchor component.|

### OH_ArkUI_AlignmentRuleOption_SetBottom()

```c
void OH_ArkUI_AlignmentRuleOption_SetBottom(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)
```

**Description**


Sets the bottom alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|
| const char* id | ID of the component that functions as the anchor point.|
| [ArkUI_VerticalAlignment](#arkui_verticalalignment) alignment | Alignment mode relative to the anchor component.|

### OH_ArkUI_AlignmentRuleOption_SetCenterVertical()

```c
void OH_ArkUI_AlignmentRuleOption_SetCenterVertical(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)
```

**Description**


Sets the vertical center alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|
| const char* id | ID of the component that functions as the anchor point.|
| [ArkUI_VerticalAlignment](#arkui_verticalalignment) alignment | Alignment mode relative to the anchor component.|

### OH_ArkUI_AlignmentRuleOption_SetBiasHorizontal()

```c
void OH_ArkUI_AlignmentRuleOption_SetBiasHorizontal(ArkUI_AlignmentRuleOption* option, float horizontal)
```

**Description**


Sets the bias value of the component in the horizontal direction under the anchor constraints.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|
| float horizontal | Bias value in the horizontal direction.|

### OH_ArkUI_AlignmentRuleOption_SetBiasVertical()

```c
void OH_ArkUI_AlignmentRuleOption_SetBiasVertical(ArkUI_AlignmentRuleOption* option, float vertical)
```

**Description**


Sets the bias value of the component in the vertical direction under the anchor constraints.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|
| float vertical | Returns the bias value in the vertical direction.|

### OH_ArkUI_AlignmentRuleOption_GetStartId()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetStartId(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the ID in the left alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| const char* | ID of the component that functions as the anchor point.|

### OH_ArkUI_AlignmentRuleOption_GetStartAlignment()

```c
ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetStartAlignment(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the alignment mode in left alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment) | Returns the alignment mode in left alignment parameters.|

### OH_ArkUI_AlignmentRuleOption_GetEndId()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetEndId(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the alignment mode in the right alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns the ID in the right alignment parameters.|

### OH_ArkUI_AlignmentRuleOption_GetEndAlignment()

```c
ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetEndAlignment(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the alignment mode in the right alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment) | Returns the alignment mode in the right alignment parameters.|

### OH_ArkUI_AlignmentRuleOption_GetCenterIdHorizontal()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdHorizontal(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the alignment mode in horizontal center alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns the ID in horizontal center alignment parameters.|

### OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentHorizontal()

```c
ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentHorizontal(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the alignment mode in horizontal center alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_HorizontalAlignment](capi-native-type-h.md#arkui_horizontalalignment) | Returns the alignment mode in horizontal center alignment parameters.|

### OH_ArkUI_AlignmentRuleOption_GetTopId()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetTopId(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the alignment mode in top alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns the ID in top alignment parameters.|

### OH_ArkUI_AlignmentRuleOption_GetTopAlignment()

```c
ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetTopAlignment(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the alignment mode in top alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment) | Returns the alignment mode in top alignment parameters.|

### OH_ArkUI_AlignmentRuleOption_GetBottomId()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetBottomId(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the alignment mode in bottom alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns the ID in bottom alignment parameters.|

### OH_ArkUI_AlignmentRuleOption_GetBottomAlignment()

```c
ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetBottomAlignment(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the alignment mode in bottom alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment) | Returns the alignment mode in bottom alignment parameters.|

### OH_ArkUI_AlignmentRuleOption_GetCenterIdVertical()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdVertical(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the ID in vertical center alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns the ID in vertical center alignment parameters.|

### OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentVertical()

```c
ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentVertical(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the ID in vertical center alignment parameters.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_VerticalAlignment](capi-native-type-h.md#arkui_verticalalignment) | Returns the vertical center alignment parameters.|

### OH_ArkUI_AlignmentRuleOption_GetBiasHorizontal()

```c
float OH_ArkUI_AlignmentRuleOption_GetBiasHorizontal(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the bias value in the horizontal direction.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| float | Bias value in the horizontal direction.|

### OH_ArkUI_AlignmentRuleOption_GetBiasVertical()

```c
float OH_ArkUI_AlignmentRuleOption_GetBiasVertical(ArkUI_AlignmentRuleOption* option)
```

**Description**


Obtains the bias value in the vertical direction.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AlignmentRuleOption](capi-arkui-nativemodule-arkui-alignmentruleoption.md)* option | Pointer to an alignment rule configuration.|

**Returns**

| Type| Description|
| -- | -- |
| float | Returns the bias value in the vertical direction.|

### OH_ArkUI_SwiperIndicator_Create()

```c
ArkUI_SwiperIndicator* OH_ArkUI_SwiperIndicator_Create(ArkUI_SwiperIndicatorType type)
```

**Description**


Creates a navigation indicator for the Swiper component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicatorType](capi-native-type-h.md#arkui_swiperindicatortype) type | Type of the navigation indicator.|

**Returns**

| Type                        | Description|
|----------------------------| -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* | Pointer to the navigation indicator.|

### OH_ArkUI_SwiperIndicator_Dispose()

```c
void OH_ArkUI_SwiperIndicator_Dispose(ArkUI_SwiperIndicator* indicator)
```

**Description**


Disposes of the navigation indicator of this **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

### OH_ArkUI_SwiperIndicator_SetStartPosition()

```c
void OH_ArkUI_SwiperIndicator_SetStartPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**


Sets the distance between the navigation indicator and the left edge of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| float value | Distance between the navigation indicator and the left edge of the **Swiper** component. Default value: **0**, in vp.|

### OH_ArkUI_SwiperIndicator_GetStartPosition()

```c
float OH_ArkUI_SwiperIndicator_GetStartPosition(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains the distance between a navigation indicator and the left edge of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance between the navigation indicator and the left edge of the **Swiper** component. Unit: vp.|

### OH_ArkUI_SwiperIndicator_SetTopPosition()

```c
void OH_ArkUI_SwiperIndicator_SetTopPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**


Sets the distance between the navigation indicator and the top edge of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| float value | Distance between a navigation indicator and the top edge of the **Swiper** component. Default value: **0**, in vp.|

### OH_ArkUI_SwiperIndicator_GetTopPosition()

```c
float OH_ArkUI_SwiperIndicator_GetTopPosition(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains the distance between the navigation indicator and the top edge of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance between a navigation indicator and the top edge of the **Swiper** component. Unit: vp.|

### OH_ArkUI_SwiperIndicator_SetEndPosition()

```c
void OH_ArkUI_SwiperIndicator_SetEndPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**


Sets the distance between the navigation indicator and the right edge of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| float value | Distance between the navigation indicator and the right edge of the **Swiper** component. Default value: **0**, in vp.|

### OH_ArkUI_SwiperIndicator_GetEndPosition()

```c
float OH_ArkUI_SwiperIndicator_GetEndPosition(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains the distance between a navigation indicator and the right edge of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance between the navigation indicator and the right edge of the **Swiper** component. Unit: vp.|

### OH_ArkUI_SwiperIndicator_SetBottomPosition()

```c
void OH_ArkUI_SwiperIndicator_SetBottomPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**


Sets the distance between the navigation indicator and the bottom edge of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| float value | Distance between a navigation indicator and the bottom edge of the **Swiper** component. Default value: **0**, in vp.|

### OH_ArkUI_SwiperIndicator_GetBottomPosition()

```c
float OH_ArkUI_SwiperIndicator_GetBottomPosition(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains the distance between the navigation indicator and the bottom edge of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance between a navigation indicator and the bottom edge of the **Swiper** component. Unit: vp.|

### OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom()

```c
void OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator, int32_t ignoreSize)
```

**Description**


Sets whether the **OH_ArkUI_SwiperIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| int32_t ignoreSize | Whether to ignore the indicator size when positioning the indicator. The value **1** means to ignore the indicator size when positioning the indicator, and **0** means the opposite. Default value: **0**.|

### OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom()

```c
int32_t OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator)
```

**Description**


Checks whether the **OH_ArkUI_SwiperIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Whether to ignore the indicator size when positioning the indicator.|

### OH_ArkUI_SwiperIndicator_SetItemWidth()

```c
void OH_ArkUI_SwiperIndicator_SetItemWidth(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**


Sets the width of a dot-style navigation indicator for the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| float value | Width of the dot-style navigation indicator. Default value: **12**, in vp.|

### OH_ArkUI_SwiperIndicator_GetItemWidth()

```c
float OH_ArkUI_SwiperIndicator_GetItemWidth(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains the width of a dot-style navigation indicator of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Width of the dot-style navigation indicator. Unit: vp.|

### OH_ArkUI_SwiperIndicator_SetItemHeight()

```c
void OH_ArkUI_SwiperIndicator_SetItemHeight(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**


Sets the height of a dot-style navigation indicator for the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| float value | Height of the dot-style navigation indicator. Default value: **6**, in vp.|

### OH_ArkUI_SwiperIndicator_GetItemHeight()

```c
float OH_ArkUI_SwiperIndicator_GetItemHeight(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains the height of a dot-style navigation indicator of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Height of the dot-style navigation indicator. Unit: vp.|

### OH_ArkUI_SwiperIndicator_SetSelectedItemWidth()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedItemWidth(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**


Sets the width of the selected dot-style navigation indicator for the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| float value | Width of the dot-style navigation indicator. Default value: **12**, in vp.|

### OH_ArkUI_SwiperIndicator_GetSelectedItemWidth()

```c
float OH_ArkUI_SwiperIndicator_GetSelectedItemWidth(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains the width of the selected dot-style navigation indicator of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Width of the dot-style navigation indicator. Unit: vp.|

### OH_ArkUI_SwiperIndicator_SetSelectedItemHeight()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedItemHeight(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**


Sets the height of the selected dot-style navigation indicator for the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| float value | Height of the dot-style navigation indicator. Default value: **6**, in vp.|

### OH_ArkUI_SwiperIndicator_GetSelectedItemHeight()

```c
float OH_ArkUI_SwiperIndicator_GetSelectedItemHeight(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains the height of the selected dot-style navigation indicator of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Height of the dot-style navigation indicator. Unit: vp.|

### OH_ArkUI_SwiperIndicator_SetMask()

```c
void OH_ArkUI_SwiperIndicator_SetMask(ArkUI_SwiperIndicator* indicator, int32_t mask)
```

**Description**


Sets whether to enable the mask for a dot-style navigation indicator for the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| int32_t mask | Whether to enable the mask. The value **1** means to enable the mask, and **0** means the opposite.|

### OH_ArkUI_SwiperIndicator_GetMask()

```c
int32_t OH_ArkUI_SwiperIndicator_GetMask(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains whether the mask is enabled for a dot-style navigation indicator of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **1** if the mask is enabled; returns **0** otherwise.|

### OH_ArkUI_SwiperIndicator_SetColor()

```c
void OH_ArkUI_SwiperIndicator_SetColor(ArkUI_SwiperIndicator* indicator, uint32_t color)
```

**Description**


Sets the color of a dot-style navigation indicator for the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| uint32_t color | Color, in 0xARGB format. For example, 0xFFFF0000 indicates red.|

### OH_ArkUI_SwiperIndicator_GetColor()

```c
uint32_t OH_ArkUI_SwiperIndicator_GetColor(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains the color of a dot-style navigation indicator of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Color, in 0xARGB format. For example, 0xFFFF0000 indicates red.|

### OH_ArkUI_SwiperIndicator_SetSelectedColor()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedColor(ArkUI_SwiperIndicator* indicator, uint32_t selectedColor)
```

**Description**


Sets the color of the selected dot-style navigation indicator for the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| uint32_t selectedColor | Color, in 0xARGB format. For example, 0xFFFF0000 indicates red.|

### OH_ArkUI_SwiperIndicator_GetSelectedColor()

```c
uint32_t OH_ArkUI_SwiperIndicator_GetSelectedColor(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains the color of the selected dot-style navigation indicator of the **Swiper** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Color, in 0xARGB format. For example, 0xFFFF0000 indicates red.|

### OH_ArkUI_SwiperIndicator_SetMaxDisplayCount()

```c
int32_t OH_ArkUI_SwiperIndicator_SetMaxDisplayCount(ArkUI_SwiperIndicator* indicator, int32_t maxDisplayCount)
```

**Description**


Sets the maximum number of dots for the dot-style navigation indicator.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| int32_t maxDisplayCount | Maximum number of navigation points. Value range: [6, 9].|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if **maxDisplayCount** is set to an invalid value.|

### OH_ArkUI_SwiperIndicator_GetMaxDisplayCount()

```c
int32_t OH_ArkUI_SwiperIndicator_GetMaxDisplayCount(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains the maximum number of dots for the dot-style navigation indicator.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Maximum number of navigation points. Value range: [6, 9].|

### OH_ArkUI_SwiperDigitIndicator_Create()

```c
ArkUI_SwiperDigitIndicator *OH_ArkUI_SwiperDigitIndicator_Create()
```

**Description**


Creates a digit-style navigation indicator for this **Swiper** component.

**Since**: 19

**Returns**

| Type                              | Description|
|----------------------------------| -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) * | Pointer to the digit-style navigation indicator.|

### OH_ArkUI_SwiperDigitIndicator_Destroy()

```c
void OH_ArkUI_SwiperDigitIndicator_Destroy(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**


Disposes of the digit-style navigation indicator of this **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|

### OH_ArkUI_SwiperDigitIndicator_SetStartPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetStartPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**Description**


Sets the start position of the digit-style navigation indicator for the **Swiper** component. This determines the distance from the left edge of the **Swiper** component. For right-to-left scripts, this determines the distance from the right edge.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|
| float value | Distance from the left edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the right edge. Default value: **0**, in vp.|

### OH_ArkUI_SwiperDigitIndicator_GetStartPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetStartPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**


Obtains the start position of the digit-style navigation indicator for the **Swiper** component. This indicates the distance from the left edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the right edge.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance from the left edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the right edge. Unit: vp.|

### OH_ArkUI_SwiperDigitIndicator_SetTopPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetTopPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**Description**


Sets the distance from the digit-style navigation indicator to the top of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|
| float value | Distance from the digit-style navigation indicator to the top of the **Swiper** component. Default value: **0**, in vp.|

### OH_ArkUI_SwiperDigitIndicator_GetTopPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetTopPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**


Obtains the distance from the digit-style navigation indicator to the top of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance from the digit-style navigation indicator to the top of the **Swiper** component. Unit: vp.|

### OH_ArkUI_SwiperDigitIndicator_SetEndPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetEndPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**Description**


Sets the end position of the digit-style navigation indicator for the **Swiper** component. This determines the distance from the right edge of the **Swiper** component. For right-to-left scripts, this determines the distance from the left edge.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|
| float value | Distance from the right edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the left edge. Default value: **0**, in vp.|

### OH_ArkUI_SwiperDigitIndicator_GetEndPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetEndPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**


Obtains the end position of the digit-style navigation indicator for the **Swiper** component. This indicates the distance from the right edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the left edge.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance from the right edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the left edge. Unit: vp.|

### OH_ArkUI_SwiperDigitIndicator_SetBottomPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetBottomPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**Description**


Sets the distance from the digit-style navigation indicator to the bottom of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|
| float value | Distance from the digit-style navigation indicator to the bottom of the **Swiper** component. Default value: **0**, in vp.|

### OH_ArkUI_SwiperDigitIndicator_GetBottomPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetBottomPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**


Obtains the distance from the digit-style navigation indicator to the bottom of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance from the digit-style navigation indicator to the bottom of the **Swiper** component. Unit: vp.|

### OH_ArkUI_SwiperDigitIndicator_SetFontColor()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t color)
```

**Description**


Sets the font color of the digit-style navigation indicator for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|
| uint32_t color | Returns the color, in 0xARGB format. For example, 0xFFFF0000 indicates red. Default value: **0xFF182431**.|

### OH_ArkUI_SwiperDigitIndicator_GetFontColor()

```c
uint32_t OH_ArkUI_SwiperDigitIndicator_GetFontColor(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**


Obtains the font color of the digit-style navigation indicator for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Color, in 0xARGB format. For example, 0xFFFF0000 indicates red.|

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t selectedColor)
```

**Description**


Sets the font color of the selected digit-style navigation indicator for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|
| uint32_t selectedColor | Returns the color, in 0xARGB format. For example, 0xFFFF0000 indicates red. Default value: **0xFF182431**.|

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor()

```c
uint32_t OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**


Obtains the font color of the selected digit-style navigation indicator for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Color, in 0xARGB format. For example, 0xFFFF0000 indicates red.|

### OH_ArkUI_SwiperDigitIndicator_SetFontSize()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)
```

**Description**


Sets the font size of the digit-style navigation indicator for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|
| float size | Font size, in fp.|

### OH_ArkUI_SwiperDigitIndicator_GetFontSize()

```c
float OH_ArkUI_SwiperDigitIndicator_GetFontSize(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**


Obtains the font size of the digit-style navigation indicator for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Font size, in fp.|

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)
```

**Description**


Sets the font size of the selected digit-style navigation indicator for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|
| float size | Font size, in fp.|

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize()

```c
float OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**


Obtains the font size of the selected digit-style navigation indicator for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Font size, in fp.|

### OH_ArkUI_SwiperDigitIndicator_SetFontWeight()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontWeight(ArkUI_SwiperDigitIndicator *indicator, ArkUI_FontWeight fontWeight)
```

**Description**


Sets the font weight of the digit-style navigation indicator for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) *indicator | Pointer to the digit-style navigation indicator.|
| [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight) fontWeight | Font weight, specified using [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).|

### OH_ArkUI_SwiperDigitIndicator_GetFontWeight()

```c
ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetFontWeight(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**


Obtains the font weight of the digit-style navigation indicator for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight) | Font weight, specified using [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).|

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontWeight()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontWeight(ArkUI_SwiperDigitIndicator *indicator, ArkUI_FontWeight selectedFontWeight)
```

**Description**


Sets the font weight of the selected digit-style navigation indicator for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) *indicator | Pointer to the digit-style navigation indicator.|
| [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight) selectedFontWeight | Font weight, specified using [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).|

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontWeight()

```c
ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetSelectedFontWeight(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**


Obtains the font weight of the selected digit-style navigation indicator for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight) | Font weight, specified using [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).|

### OH_ArkUI_SwiperArrowStyle_Create()

```c
ArkUI_SwiperArrowStyle *OH_ArkUI_SwiperArrowStyle_Create()
```

**Description**


Creates an arrow style for the **Swiper** component.

**Since**: 19

**Returns**

| Type                          | Description|
|------------------------------| -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) * | Pointer to the arrow object.|

### OH_ArkUI_SwiperArrowStyle_Destroy()

```c
void OH_ArkUI_SwiperArrowStyle_Destroy(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**


Disposes of the arrow of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|

### OH_ArkUI_SwiperArrowStyle_SetShowBackground()

```c
void OH_ArkUI_SwiperArrowStyle_SetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showBackground)
```

**Description**


Sets whether to display the background of the arrow for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|
| int32_t showBackground | Whether to show the arrow background. The value **1** means to show the background, and **0** means the opposite. The default value is **0**.|

### OH_ArkUI_SwiperArrowStyle_GetShowBackground()

```c
int32_t OH_ArkUI_SwiperArrowStyle_GetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**


Checks whether the background of the arrow is displayed for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns whether the arrow background is displayed. The value **1** means that the background is displayed, and **0** means the opposite.|

### OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle()

```c
void OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showSidebarMiddle)
```

**Description**


Sets the position of the arrow for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|
| int32_t showSidebarMiddle | Position of the arrow. **0**: The arrow is displayed on both sides of the navigation indicator. **1**: The arrow is displayed on both sides of the **Swiper** component. The default value is **0**.|

### OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle()

```c
int32_t OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**


Obtains the position of the arrow for the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns the position of the arrow. **0**: The arrow is displayed on both sides of the navigation indicator. **1**: The arrow is displayed on both sides of the **Swiper** component.|

### OH_ArkUI_SwiperArrowStyle_SetBackgroundSize()

```c
void OH_ArkUI_SwiperArrowStyle_SetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle, float backgroundSize)
```

**Description**


Sets the background size for the arrow of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|
| float backgroundSize | Background size of the arrow, in vp. Default value: 24 vp when displayed on both sides of the navigation indicator and 32 vp when displayed on both sides of the **Swiper** component.|

### OH_ArkUI_SwiperArrowStyle_GetBackgroundSize()

```c
float OH_ArkUI_SwiperArrowStyle_GetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**


Obtains the background size of the arrow of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Background size of the arrow, in vp.|

### OH_ArkUI_SwiperArrowStyle_SetBackgroundColor()

```c
void OH_ArkUI_SwiperArrowStyle_SetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t backgroundColor)
```

**Description**


Sets the background color for the arrow of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|
| uint32_t backgroundColor | Background color of the arrow, in 0xARGB format. For example, 0xFFFF0000 indicates red. Default value: **0x00000000** when displayed on both sides of the navigation indicator and **0x19182431** when displayed on both sides of the **Swiper** component.|

### OH_ArkUI_SwiperArrowStyle_GetBackgroundColor()

```c
uint32_t OH_ArkUI_SwiperArrowStyle_GetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**


Obtains the background color for the arrow of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Background color of the arrow, in 0xARGB format. For example, 0xFFFF0000 indicates red.|

### OH_ArkUI_SwiperArrowStyle_SetArrowSize()

```c
void OH_ArkUI_SwiperArrowStyle_SetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle, float arrowSize)
```

**Description**


Sets the size for the arrow of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|
| float arrowSize | Size of the arrow, in vp. Default value: 18 vp when displayed on both sides of the navigation indicator and 24 vp when displayed on both sides of the **Swiper** component. When the arrow background is displayed, the value of **arrowSize** is fixed at 3/4 of the value of **backgroundSize**.|

### OH_ArkUI_SwiperArrowStyle_GetArrowSize()

```c
float OH_ArkUI_SwiperArrowStyle_GetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**


Obtains the size of the arrow of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Size of the arrow, in vp.|

### OH_ArkUI_SwiperArrowStyle_SetArrowColor()

```c
void OH_ArkUI_SwiperArrowStyle_SetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t arrowColor)
```

**Description**


Sets the color for the arrow of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|
| uint32_t arrowColor | Color of the arrow, in 0xARGB format. For example, 0xFFFF0000 indicates red.|

### OH_ArkUI_SwiperArrowStyle_GetArrowColor()

```c
uint32_t OH_ArkUI_SwiperArrowStyle_GetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**


Obtains the color of the arrow of the **Swiper** component.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the arrow object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Color of the arrow, in 0xARGB format. For example, 0xFFFF0000 indicates red.|

### OH_ArkUI_SwiperIndicator_SetSpace()

```c
void OH_ArkUI_SwiperIndicator_SetSpace(ArkUI_SwiperIndicator* indicator, float space)
```

**Description**


Sets the spacing between navigation points.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|
| float space | Spacing between navigation points. Default value: **8**, in vp.|

### OH_ArkUI_SwiperIndicator_GetSpace()

```c
float OH_ArkUI_SwiperIndicator_GetSpace(ArkUI_SwiperIndicator* indicator)
```

**Description**


Obtains the spacing between navigation points.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| float | Spacing between navigation points. Unit: vp.|

### OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom()

```c
void OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator, int32_t ignoreSize)
```

**Description**


Sets whether the **OH_ArkUI_SwiperDigitIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the navigation indicator.|
| int32_t ignoreSize | Whether to ignore the indicator size when positioning the indicator. The value **1** means to ignore the indicator size when positioning the indicator, and **0** means the opposite. Default value: **0**.|

### OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom()

```c
int32_t OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**


Checks whether the **OH_ArkUI_SwiperDigitIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Whether to ignore the indicator size when positioning the indicator.|

### OH_ArkUI_ListItemSwipeActionItem_Create()

```c
ArkUI_ListItemSwipeActionItem* OH_ArkUI_ListItemSwipeActionItem_Create()
```

**Description**


Creates a **ListItemSwipeActionItem** instance.

**Since**: 12

**Returns**

| Type                                | Description|
|------------------------------------| -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* | Returns the created **ListItemSwipeActionItem** instance.|

### OH_ArkUI_ListItemSwipeActionItem_Dispose()

```c
void OH_ArkUI_ListItemSwipeActionItem_Dispose(ArkUI_ListItemSwipeActionItem* item)
```

**Description**


Disposes of a **ListItemSwipeActionItem** instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | **ListItemSwipeActionItem** instance to dispose of.|

### OH_ArkUI_ListItemSwipeActionItem_SetContent()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetContent(ArkUI_ListItemSwipeActionItem* item, ArkUI_NodeHandle node)
```

**Description**


Sets the layout content for a **ListItemSwipeActionItem** instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Target **ListItemSwipeActionItem** instance.|
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Layout information.|

### OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item, float distance)
```

**Description**


Sets the swipe distance threshold for deleting the list item.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Target **ListItemSwipeActionItem** instance.|
| float distance | Returns the swipe distance threshold for deleting the list item.|

### OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance()

```c
float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item)
```

**Description**


Obtains the swipe distance threshold for deleting the list item.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Target **ListItemSwipeActionItem** instance.|

**Returns**

| Type| Description|
| -- | -- |
| float | Returns the swipe distance threshold for deleting the list item. Return **0** if an error occurs.|

### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**Description**


Sets the callback invoked each time the list item enters the delete area.

**Since**: 12


**Parameters**

| Name                                    | Description|
|-----------------------------------------| -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Target **ListItemSwipeActionItem** instance.|
| callback                                | Callback event.|

### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item,void* userData, void (*callback)(void* userData))
```

**Description**


Sets the callback invoked each time the list item enters the delete area.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Target **ListItemSwipeActionItem** instance.|
| void* userData | User-defined data.|
| callback | Callback event.|

### OH_ArkUI_ListItemSwipeActionItem_SetOnAction()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnAction(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**Description**


Sets the callback invoked when the list item is deleted while in the delete area.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Target **ListItemSwipeActionItem** instance.|
| callback | Callback event.|

### OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData(ArkUI_ListItemSwipeActionItem* item,void* userData, void (*callback)(void* userData))
```

**Description**


Sets the callback invoked when the list item is deleted while in the delete area.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Target **ListItemSwipeActionItem** instance.|
| void* userData | User-defined data.|
| callback | Callback event.|

### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**Description**


Sets the callback invoked each time the list item exits the delete area.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Target **ListItemSwipeActionItem** instance.|
| callback | Callback event.|

### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item,void* userData, void (*callback)(void* userData))
```

**Description**


Sets the callback invoked each time the list item exits the delete area.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Target **ListItemSwipeActionItem** instance.|
| void* userData | User-defined data.|
| callback | Callback event.|

### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange(ArkUI_ListItemSwipeActionItem* item,void (*callback)(ArkUI_ListItemSwipeActionState swipeActionState))
```

**Description**


Sets the callback invoked when the swipe state of the list item changes.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Target **ListItemSwipeActionItem** instance.|
| callback | Callback event. **swipeActionState**: new state after the state change.|

### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData(ArkUI_ListItemSwipeActionItem* item,void* userData, void (*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void* userData))
```

**Description**


Sets the callback invoked when the swipe state of the list item changes.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Target **ListItemSwipeActionItem** instance.|
|  void* userData | User-defined data.|
| callback | Callback event. **swipeActionState**: new state after the state change.|

### OH_ArkUI_ListItemSwipeActionOption_Create()

```c
ArkUI_ListItemSwipeActionOption* OH_ArkUI_ListItemSwipeActionOption_Create()
```

**Description**


Creates a **ListItemSwipeActionOption** instance.

**Since**: 12

**Returns**

| Type                                  | Description|
|--------------------------------------| -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* | Created **ListItemSwipeActionOption** instance.|

### OH_ArkUI_ListItemSwipeActionOption_Dispose()

```c
void OH_ArkUI_ListItemSwipeActionOption_Dispose(ArkUI_ListItemSwipeActionOption* option)
```

**Description**


Disposes of a **ListItemSwipeActionOption** instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | **ListItemSwipeActionOption** instance to dispose of.|

### OH_ArkUI_ListItemSwipeActionOption_SetStart()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetStart(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)
```

**Description**


Sets the layout content for the left edge (for a vertical layout) or top edge (for a horizontal layout) of a **ListItemSwipeActionItem** instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | Target **ListItemSwipeActionItem** instance.|
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Layout information.|

### OH_ArkUI_ListItemSwipeActionOption_SetEnd()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetEnd(ArkUI_ListItemSwipeActionOption* option,ArkUI_ListItemSwipeActionItem* item)
```

**Description**


Sets the layout content for the right edge (for a vertical layout) or bottom edge (for a horizontal layout) of a **ListItemSwipeActionItem** instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | Target **ListItemSwipeActionItem** instance.|
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Layout information.|

### OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect(ArkUI_ListItemSwipeActionOption* option,ArkUI_ListItemSwipeEdgeEffect edgeEffect)
```

**Description**


Sets the edge effect used when the boundary of the scrolling area is reached.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | Target **ListItemSwipeActionItem** instance.|
| [ArkUI_ListItemSwipeEdgeEffect](capi-native-type-h.md#arkui_listitemswipeedgeeffect) edgeEffect | Edge effect.|

### OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect()

```c
int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect(ArkUI_ListItemSwipeActionOption* option)
```

**Description**


Obtains the edge effect used when the boundary of the scrolling area is reached.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | Target **ListItemSwipeActionItem** instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Edge effect. The default return value is **ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING**.|

### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange(ArkUI_ListItemSwipeActionOption* option,void (*callback)(float offset))
```

**Description**


Sets the callback invoked when the scroll offset changes.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | Target **ListItemSwipeActionItem** instance.|
| callback | Callback event. **offset**: scroll offset.|

### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData(ArkUI_ListItemSwipeActionOption* option,void* userData, void (*callback)(float offset, void* userData))
```

**Description**


Sets the callback invoked when the scroll offset changes.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | Target **ListItemSwipeActionItem** instance.|
|  void* userData | User-defined data.|
| callback | Callback event. **offset**: scroll offset.|

### OH_ArkUI_ListItemSwipeAction_Expand()

```c
int32_t OH_ArkUI_ListItemSwipeAction_Expand(ArkUI_NodeHandle node, ArkUI_ListItemSwipeActionDirection direction)
```

**Description**

Expands the swipe action menu for the specified list item.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| node | **ListItem** node object.|
| [ArkUI_ListItemSwipeActionDirection](#arkui_listitemswipeactiondirection) direction | Enumerates the swipe action menu display directions for **ListItem** components.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_ERROR](capi-native-type-h.md#arkui_errorcode) if the node object type is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) if the passed node is not mounted to the component tree when the API is called.|

> **NOTE**
>
> - If the **List** component's **NODE_LIST_CACHED_COUNT** attribute is configured to preload **ListItem** child components, swipe action menus can be expanded for preloaded **ListItem** child components outside the visible area. Otherwise, child components outside the visible area cannot be expanded.

### OH_ArkUI_ListItemSwipeAction_Collapse()

```c
int32_t OH_ArkUI_ListItemSwipeAction_Collapse(ArkUI_NodeHandle node)
```

**Description**

Collapses the swipe action menu for the specified list item.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| node | **ListItem** node object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_ERROR](capi-native-type-h.md#arkui_errorcode) if the node object type is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) if the passed node is not mounted to the component tree when the API is called.|

### OH_ArkUI_AccessibilityState_Create()

```c
ArkUI_AccessibilityState* OH_ArkUI_AccessibilityState_Create(void)
```

**Description**


Creates an accessibility state.

**Since**: 12

**Returns**

| Type                           | Description|
|-------------------------------| -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* | Returns the pointer to the created accessibility state object. If a null pointer is returned, the creation fails. A possible cause is that the application address space is full.|

### OH_ArkUI_AccessibilityState_Dispose()

```c
void OH_ArkUI_AccessibilityState_Dispose(ArkUI_AccessibilityState* state)
```

**Description**


Disposes of the pointer to an accessibility state.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | Pointer to the created accessibility state object.|

### OH_ArkUI_AccessibilityState_SetDisabled()

```c
void OH_ArkUI_AccessibilityState_SetDisabled(ArkUI_AccessibilityState* state, int32_t isDisabled)
```

**Description**


Sets whether an accessibility state is disabled.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | Pointer to the created accessibility state object.|
| int32_t isDisabled | Whether the accessibility state is disabled. The value **1** means that the accessibility state is disabled, and **0** means the opposite. The default value is **0**.|

### OH_ArkUI_AccessibilityState_IsDisabled()

```c
int32_t OH_ArkUI_AccessibilityState_IsDisabled(ArkUI_AccessibilityState* state)
```

**Description**


Obtains whether an accessibility state is disabled.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | Pointer to the created accessibility state object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Whether the accessibility state is disabled. The value **1** means that the accessibility state is disabled, and **0** means the opposite. The default value is **0**.<br>         If the value of **state** is null, the default value is returned.|

### OH_ArkUI_AccessibilityState_SetSelected()

```c
void OH_ArkUI_AccessibilityState_SetSelected(ArkUI_AccessibilityState* state, int32_t isSelected)
```

**Description**


Sets whether an accessibility state is selected.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | Pointer to the created accessibility state object.|
| int32_t isSelected | Whether the accessibility state is selected. The value **1** means that the accessibility state is selected, and **0** means the opposite. The default value is **0**.|

### OH_ArkUI_AccessibilityState_IsSelected()

```c
int32_t OH_ArkUI_AccessibilityState_IsSelected(ArkUI_AccessibilityState* state)
```

**Description**


Obtains whether an accessibility state is selected.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | Pointer to the created accessibility state object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Whether the accessibility state is selected. The value **1** means that the accessibility state is selected, and **0** means the opposite. The default value is **0**.<br>         If the value of **state** is null, the default value is returned.|

### OH_ArkUI_AccessibilityState_SetCheckedState()

```c
void OH_ArkUI_AccessibilityState_SetCheckedState(ArkUI_AccessibilityState* state, int32_t checkedState)
```

**Description**


Sets the check box state of an accessibility state.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | Pointer to the created accessibility state object.|
| int32_t checkedState | Check box status. The parameter type is [ArkUI_AccessibilityCheckedState](capi-native-type-h.md#arkui_accessibilitycheckedstate). The default value is **ARKUI_ACCESSIBILITY_UNCHECKED**.|

### OH_ArkUI_AccessibilityState_GetCheckedState()

```c
int32_t OH_ArkUI_AccessibilityState_GetCheckedState(ArkUI_AccessibilityState* state)
```

**Description**


Obtains the check box state of an accessibility state.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | Pointer to the created accessibility state object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Check box status. The parameter type is [ArkUI_AccessibilityCheckedState](capi-native-type-h.md#arkui_accessibilitycheckedstate). The default value is **ARKUI_ACCESSIBILITY_UNCHECKED**.<br>         If a parameter error occurs, the default value is returned.|

### OH_ArkUI_AccessibilityValue_Create()

```c
ArkUI_AccessibilityValue* OH_ArkUI_AccessibilityValue_Create(void)
```

**Description**


Creates an **AccessibilityValue** instance.

**Since**: 12

**Returns**

| Type                           | Description|
|-------------------------------| -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* | Returns the pointer to the created **AccessibilityValue** instance.|

### OH_ArkUI_AccessibilityValue_Dispose()

```c
void OH_ArkUI_AccessibilityValue_Dispose(ArkUI_AccessibilityValue* value)
```

**Description**


Disposes of the pointer to an **AccessibilityValue** instance.

**Since**: 12


**Parameters**

| Name                                                                                   | Description|
|----------------------------------------------------------------------------------------| -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Returns the pointer to the created **AccessibilityValue** instance.|

### OH_ArkUI_AccessibilityValue_SetMin()

```c
void OH_ArkUI_AccessibilityValue_SetMin(ArkUI_AccessibilityValue* value, int32_t min)
```

**Description**


Sets the minimum accessibility value.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Returns the pointer to the created **AccessibilityValue** instance.|
| int32_t min | Minimum value for the range-based component. The default value is **-1**.|

### OH_ArkUI_AccessibilityValue_GetMin()

```c
int32_t OH_ArkUI_AccessibilityValue_GetMin(ArkUI_AccessibilityValue* value)
```

**Description**


Obtains the minimum accessibility value.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Returns the pointer to the created **AccessibilityValue** instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Minimum value for the range-based component. The default value is **-1**.<br>         If a parameter error occurs, **-1** is returned.|

### OH_ArkUI_AccessibilityValue_SetMax()

```c
void OH_ArkUI_AccessibilityValue_SetMax(ArkUI_AccessibilityValue* value, int32_t max)
```

**Description**


Sets the maximum accessibility value.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Returns the pointer to the created **AccessibilityValue** instance.|
| int32_t max | Maximum value for the range-based component. The default value is **-1**.|

### OH_ArkUI_AccessibilityValue_GetMax()

```c
int32_t OH_ArkUI_AccessibilityValue_GetMax(ArkUI_AccessibilityValue* value)
```

**Description**


Obtains the maximum accessibility value.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Returns the pointer to the created **AccessibilityValue** instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Maximum value for the range-based component. The default value is **-1**.<br>         If a parameter error occurs, **-1** is returned.|

### OH_ArkUI_AccessibilityValue_SetCurrent()

```c
void OH_ArkUI_AccessibilityValue_SetCurrent(ArkUI_AccessibilityValue* value, int32_t current)
```

**Description**


Sets the current accessibility value.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Returns the pointer to the created **AccessibilityValue** instance.|
| int32_t current | Current value for the range-based component. The default value is **-1**.|

### OH_ArkUI_AccessibilityValue_GetCurrent()

```c
int32_t OH_ArkUI_AccessibilityValue_GetCurrent(ArkUI_AccessibilityValue* value)
```

**Description**


Obtains the current accessibility value.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Returns the pointer to the created **AccessibilityValue** instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Current value for the range-based component. The default value is **-1**.<br>         If a parameter error occurs, **-1** is returned.|

### OH_ArkUI_AccessibilityValue_SetRangeMin()

```c
void OH_ArkUI_AccessibilityValue_SetRangeMin(ArkUI_AccessibilityValue* value, int32_t rangeMin)
```

**Description**


Sets the minimum value for accessibility information of the range-based component.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Pointer to the accessibility information object of the range-based component for which you want to set the minimum value.|
| int32_t rangeMin | Minimum value for the range-based component. The default value is **-1**.|

### OH_ArkUI_AccessibilityValue_GetRangeMin()

```c
int32_t OH_ArkUI_AccessibilityValue_GetRangeMin(ArkUI_AccessibilityValue* value)
```

**Description**


Obtains the minimum value for accessibility information of the range-based component.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Pointer to the accessibility information object of the range-based component for which you want to obtain the minimum value.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Minimum value for the range-based component. The default value is **-1**.<br>         If a parameter error occurs, **-1** is returned.|

### OH_ArkUI_AccessibilityValue_SetRangeMax()

```c
void OH_ArkUI_AccessibilityValue_SetRangeMax(ArkUI_AccessibilityValue* value, int32_t rangeMax)
```

**Description**


Sets the maximum value for accessibility information of the range-based component.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Pointer to the accessibility information object of the range-based component for which you want to set the maximum value.|
| int32_t rangeMax | Maximum value for the range-based component. The default value is **-1**.|

### OH_ArkUI_AccessibilityValue_GetRangeMax()

```c
int32_t OH_ArkUI_AccessibilityValue_GetRangeMax(ArkUI_AccessibilityValue* value)
```

**Description**


Obtains the maximum value for accessibility information of the range-based component.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Pointer to the accessibility information object of the range-based component for which you want to obtain the minimum value.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Maximum value for the range-based component. The default value is **-1**.<br>         If a parameter error occurs, **-1** is returned.|

### OH_ArkUI_AccessibilityValue_SetRangeCurrent()

```c
void OH_ArkUI_AccessibilityValue_SetRangeCurrent(ArkUI_AccessibilityValue* value, int32_t rangeCurrent)
```

**Description**


Sets the current value for accessibility information of the range-based component.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Pointer to the accessibility information object of the range-based component for which you want to set the current value.|
| int32_t rangeCurrent | Current value for the range-based component. The default value is **-1**.|

### OH_ArkUI_AccessibilityValue_GetRangeCurrent()

```c
int32_t OH_ArkUI_AccessibilityValue_GetRangeCurrent(ArkUI_AccessibilityValue* value)
```

**Description**


Obtains the current value for accessibility information of the range-based component.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Pointer to the accessibility information object of the range-based component for which you want to obtain the current value.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Current value for the range-based component. The default value is **-1**.<br>         If a parameter error occurs, **-1** is returned.|

### OH_ArkUI_AccessibilityValue_SetText()

```c
void OH_ArkUI_AccessibilityValue_SetText(ArkUI_AccessibilityValue* value, const char* text)
```

**Description**


Sets the text description of an **AccessibilityValue** instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Returns the pointer to the created **AccessibilityValue** instance.|
| const char* text | Text description. The default value is an empty string.|

### OH_ArkUI_AccessibilityValue_GetText()

```c
const char* OH_ArkUI_AccessibilityValue_GetText(ArkUI_AccessibilityValue* value)
```

**Description**


Obtains the text description of an **AccessibilityValue** instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | Returns the pointer to the created **AccessibilityValue** instance.|

**Returns**

| Type| Description|
| -- | -- |
| const char* | Text description. The default value is an empty string.<br>         If a parameter error occurs, a null pointer is returned.|

### OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString()

```c
ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString(char* src)
```

**Description**


Creates an image frame information object based on an image path, with the image format being SVG, PNG, or JPG.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| char* src | Image path.|

**Returns**

| Type                               | Description|
|-----------------------------------| -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* | Pointer to the image frame information object.|

### OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor()

```c
ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor(ArkUI_DrawableDescriptor* drawable)
```

**Description**


Creates an image frame information object based on a **DrawableDescriptor** object, with the image format being Resource or PixelMap.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawable | Pointer to an **ArkUI_DrawableDescriptor** object created using Resource or PixelMap.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* | Pointer to the image frame information object.|

### OH_ArkUI_ImageAnimatorFrameInfo_Dispose()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_Dispose(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**Description**


Disposes of the pointer to an image frame information object.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|

### OH_ArkUI_ImageAnimatorFrameInfo_SetWidth()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t width)
```

**Description**


Sets the image width.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|
| int32_t width | Image width, in px.|

### OH_ArkUI_ImageAnimatorFrameInfo_GetWidth()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**Description**


Obtains the image width.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns the image width, in PX. If **imageInfo** is a null pointer, **0** is returned.|

### OH_ArkUI_ImageAnimatorFrameInfo_SetHeight()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t height)
```

**Description**


Sets the image height.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|
| int32_t height | Image height, in px.|

### OH_ArkUI_ImageAnimatorFrameInfo_GetHeight()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**Description**


Obtains the image height.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns the image height, in PX. If **imageInfo** is a null pointer, **0** is returned.|

### OH_ArkUI_ImageAnimatorFrameInfo_SetTop()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t top)
```

**Description**


Sets the vertical coordinate of an image relative to the upper left corner of the component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|
| int32_t top | Vertical coordinate of the image relative to the upper left corner of the component, in px.|

### OH_ArkUI_ImageAnimatorFrameInfo_GetTop()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**Description**


Obtains the vertical coordinate of an image relative to the upper left corner of the component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns the vertical coordinate of the image relative to the upper left corner of the component, in px. If **imageInfo** is a null pointer, **0** is returned.|

### OH_ArkUI_ImageAnimatorFrameInfo_SetLeft()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t left)
```

**Description**


Sets the horizontal coordinate of an image relative to the upper left corner of the component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|
| int32_t left | Horizontal coordinate of the image relative to the upper left corner of the component, in px.|

### OH_ArkUI_ImageAnimatorFrameInfo_GetLeft()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**Description**


Obtains the horizontal coordinate of an image relative to the upper left corner of the component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns the horizontal coordinate of the image relative to the upper left corner of the component, in px. If **imageInfo** is a null pointer, **0** is returned.|

### OH_ArkUI_ImageAnimatorFrameInfo_SetDuration()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t duration)
```

**Description**


Sets the playback duration of an image.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|
| int32_t duration | Playback duration of an image, in milliseconds.|

### OH_ArkUI_ImageAnimatorFrameInfo_GetDuration()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**Description**


Obtains the playback duration of an image.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | Pointer to the image frame information object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns the playback duration of the image, in milliseconds. If **imageInfo** is a null pointer, **0** is returned.|

### OH_ArkUI_ListChildrenMainSizeOption_Create()

```c
ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()
```

**Description**


Creates a **ListChildrenMainSize** instance.

**Since**: 12

**Returns**

| Type                             | Description|
|---------------------------------| -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* | Created **ListChildrenMainSize** instance.|

### OH_ArkUI_ListChildrenMainSizeOption_Dispose()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)
```

**Description**


Disposes of a **ListChildrenMainSize** instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | **ListChildrenMainSize** instance to dispose of.|

### OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)
```

**Description**


Sets the default size in a **ListChildrenMainSize** instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | **ListChildrenMainSize** instance.|
| float defaultMainSize | Default size to set, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)
```

**Description**


Obtains the default size in a **ListChildrenMainSize** instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | **ListChildrenMainSize** instance.|

**Returns**

| Type| Description|
| -- | -- |
| float | Default size, in vp. The default value is **0**. If **option** is a null pointer, **-1** is returned.|

### OH_ArkUI_ListChildrenMainSizeOption_Resize()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)
```

**Description**


Resets the array size in a **ListChildrenMainSize** instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | **ListChildrenMainSize** instance.|
| int32_t totalSize | Array size.|

### OH_ArkUI_ListChildrenMainSizeOption_Splice()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)
```

**Description**


Changes the content of a **ChildrenMainSizeOption** array.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | **ListChildrenMainSize** instance.|
| int32_t index | Index at which to start changing the values in the array.|
| int32_t deleteCount | Number of elements in the array to remove from the position specified by **index**.|
| int32_t addCount | Number of elements to add to the array from the position specified by **index**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ListChildrenMainSizeOption_UpdateSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)
```

**Description**


Updates the values in a **ChildrenMainSizeOption** array of a **List** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | **ListChildrenMainSize** instance.|
| int32_t index | Index at which to start changing the values in the array.|
| float mainSize | New size value to set at the specified index.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ListChildrenMainSizeOption_GetMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)
```

**Description**


Obtains the value of the **ChildrenMainSizeOption** array of the **List** component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | **ListChildrenMainSize** instance.|
| int32_t index | Index of the value to be obtained.|

**Returns**

| Type| Description|
| -- | -- |
| float | Value at the specified index. If a parameter error occurs, **-1** is returned.|

### OH_ArkUI_CustomSpanMeasureInfo_Create()

```c
ArkUI_CustomSpanMeasureInfo* OH_ArkUI_CustomSpanMeasureInfo_Create(void)
```

**Description**


Creates measurement information for this custom span.

**Since**: 12

**Returns**

| Type                              | Description|
|----------------------------------| -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* | Returns a **CustomSpanMeasureInfo** instance.<br> If a null pointer is returned, the memory may be insufficient.|

### OH_ArkUI_CustomSpanMeasureInfo_Dispose()

```c
void OH_ArkUI_CustomSpanMeasureInfo_Dispose(ArkUI_CustomSpanMeasureInfo* info)
```

**Description**


Disposes of measurement information of a custom span.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info |  Pointer to the measurement information of a custom span.|

### OH_ArkUI_CustomSpanMeasureInfo_GetFontSize()

```c
float OH_ArkUI_CustomSpanMeasureInfo_GetFontSize(ArkUI_CustomSpanMeasureInfo* info)
```

**Description**


Obtains the font size of the parent text node of a custom span.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info |  Pointer to the measurement information of a custom span.|

**Returns**

| Type| Description|
| -- | -- |
| float | Font size of the parent text node. If a parameter error occurs, **0.0f** is returned.<br> A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomSpanMetrics_Create()

```c
ArkUI_CustomSpanMetrics* OH_ArkUI_CustomSpanMetrics_Create(void)
```

**Description**


Creates measurement metrics for this custom span.

**Since**: 12

**Returns**

| Type                          | Description|
|------------------------------| -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* | **CustomSpanMetrics** instance.<br> If a null pointer is returned, the memory may be insufficient.|

### OH_ArkUI_CustomSpanMetrics_Dispose()

```c
void OH_ArkUI_CustomSpanMetrics_Dispose(ArkUI_CustomSpanMetrics* metrics)
```

**Description**


Disposes of measurement metrics of this custom span.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | **CustomSpanMetrics** instance.|

### OH_ArkUI_CustomSpanMetrics_SetWidth()

```c
int32_t OH_ArkUI_CustomSpanMetrics_SetWidth(ArkUI_CustomSpanMetrics* metrics, float width)
```

**Description**


Sets the width for a custom span.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | **CustomSpanMetrics** instance.|
| float width | Width, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomSpanMetrics_SetHeight()

```c
int32_t OH_ArkUI_CustomSpanMetrics_SetHeight(ArkUI_CustomSpanMetrics* metrics, float height)
```

**Description**


Sets the height for a custom span.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | **CustomSpanMetrics** instance.|
| float height | Height, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomSpanDrawInfo_Create()

```c
ArkUI_CustomSpanDrawInfo* OH_ArkUI_CustomSpanDrawInfo_Create(void)
```

**Description**


Creates drawing information for this custom span.

**Since**: 12

**Returns**

| Type                           | Description|
|-------------------------------| -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* | Returns a **CustomSpanDrawInfo** instance.<br> If a null pointer is returned, the memory may be insufficient.|

### OH_ArkUI_CustomSpanDrawInfo_Dispose()

```c
void OH_ArkUI_CustomSpanDrawInfo_Dispose(ArkUI_CustomSpanDrawInfo* info)
```

**Description**


Disposes of drawing information for this custom span.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  Pointer to the drawing information of a custom span.|

### OH_ArkUI_CustomSpanDrawInfo_GetXOffset()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetXOffset(ArkUI_CustomSpanDrawInfo* info)
```

**Description**


Obtains the x-axis offset of the custom span relative to the mounted component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  Pointer to the drawing information of a custom span.|

**Returns**

| Type| Description|
| -- | -- |
| float | Returns the x-axis offset. If a parameter error occurs, **0.0f** is returned.<br> A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomSpanDrawInfo_GetLineTop()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetLineTop(ArkUI_CustomSpanDrawInfo* info)
```

**Description**


Obtains the top margin of the custom span relative to the mounted component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  Pointer to the drawing information of a custom span.|

**Returns**

| Type| Description|
| -- | -- |
| float | Top margin. If a parameter error occurs, **0.0f** is returned.<br> A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomSpanDrawInfo_GetLineBottom()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetLineBottom(ArkUI_CustomSpanDrawInfo* info)
```

**Description**


Obtains the bottom margin of the custom span relative to the mounted component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  Pointer to the drawing information of a custom span.|

**Returns**

| Type| Description|
| -- | -- |
| float | Bottom margin. If a parameter error occurs, **0.0f** is returned.<br> A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomSpanDrawInfo_GetBaseline()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetBaseline(ArkUI_CustomSpanDrawInfo* info)
```

**Description**


Obtains the baseline offset of the custom span relative to the mounted component.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  Pointer to the drawing information of a custom span.|

**Returns**

| Type| Description|
| -- | -- |
| float | Baseline offset. If a parameter error occurs, **0.0f** is returned.<br> A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomProperty_Destroy()

```c
void OH_ArkUI_CustomProperty_Destroy(ArkUI_CustomProperty* handle)
```

**Description**


Destroys a **CustomProperty** instance.

**Since**: 14


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md)* handle | **CustomProperty** instance to destroy.|

### OH_ArkUI_CustomProperty_GetStringValue()

```c
const char* OH_ArkUI_CustomProperty_GetStringValue(ArkUI_CustomProperty* handle)
```

**Description**


Obtains the value of a custom property.

**Since**: 14


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md)* handle | Pointer to the custom property object.|

**Returns**

| Type| Description|
| -- | -- |
| const char* | Value of the custom property.|

### OH_ArkUI_HostWindowInfo_GetName()

```c
const char* OH_ArkUI_HostWindowInfo_GetName(ArkUI_HostWindowInfo* info)
```

**Description**


Obtains the window name from a **HostWindowInfo** object.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)* info | **HostWindowInfo** object.|

**Returns**

| Type| Description|
| -- | -- |
| const char* | Returns the window name obtained from the **HostWindowInfo** object.|

### OH_ArkUI_HostWindowInfo_Destroy()

```c
void OH_ArkUI_HostWindowInfo_Destroy(ArkUI_HostWindowInfo* info)
```

**Description**


Destroys a **HostWindowInfo** object.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)* info | **HostWindowInfo** object to be destroyed.|

### OH_ArkUI_ActiveChildrenInfo_Destroy()

```c
void OH_ArkUI_ActiveChildrenInfo_Destroy(ArkUI_ActiveChildrenInfo* handle)
```

**Description**


Destroys an **ActiveChildrenInfo** instance.

**Since**: 14


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)* handle | **ActiveChildrenInfo** instance to destroy.|

### OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex()

```c
ArkUI_NodeHandle OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex(ArkUI_ActiveChildrenInfo* handle, int32_t index)
```

**Description**


Obtains the child node at the specified index in the specified **ActiveChildrenInfo** instance.

**Since**: 14


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)* handle | **ActiveChildrenInfo** instance from which to obtain the information.|
| int32_t index | Index of the target child node.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Handle to the child node at the specified index, or **nullptr** if an error occurs.|

### OH_ArkUI_ActiveChildrenInfo_GetCount()

```c
int32_t OH_ArkUI_ActiveChildrenInfo_GetCount(ArkUI_ActiveChildrenInfo* handle)
```

**Description**


Obtains the number of nodes in the specified **ActiveChildrenInfo** instance.

**Since**: 14


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)* handle | **ActiveChildrenInfo** instance from which to obtain the information.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Number of child nodes. The default value is **0**.|

### OH_ArkUI_ProgressLinearStyleOption_Create()

```c
ArkUI_ProgressLinearStyleOption* OH_ArkUI_ProgressLinearStyleOption_Create(void)
```

**Description**


Creates a **ProgressLinearStyleOption** instance.

**Since**: 15

**Returns**

| Type                                  | Description|
|--------------------------------------| -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* | Returns the **ProgressLinearStyleOption** instance created.<br> If a null pointer is returned, the memory may be insufficient.|

### OH_ArkUI_ProgressLinearStyleOption_Destroy()

```c
void OH_ArkUI_ProgressLinearStyleOption_Destroy(ArkUI_ProgressLinearStyleOption* option)
```

**Description**


Destroys a **ProgressLinearStyleOption** instance.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to a **ProgressLinearStyleOption** instance.|

### OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)
```

**Description**


Sets whether to enable the smooth progress effect.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to a **ProgressLinearStyleOption** instance.|
| bool enabled | Whether to enable the smooth effect. When this effect is enabled, the progress changes smoothly from the current value to the target value. When this effect is disabled, the progress changes abruptly to the target value. The default value is **true**.|

### OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)
```

**Description**


Sets whether to enable the scan effect.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to a **ProgressLinearStyleOption** instance.|
| bool enabled | Whether to enable the scan effect. The default value is **false**.|

### OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth(ArkUI_ProgressLinearStyleOption* option, float strokeWidth)
```

**Description**


Sets the width of the progress indicator.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to a **ProgressLinearStyleOption** instance.|
| float strokeWidth | Stroke width of the progress indicator, in vp. Percentage values are not supported. The default value is **4.0vp**.|

### OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius(ArkUI_ProgressLinearStyleOption* option, float strokeRadius)
```

**Description**


Sets the corner radius of the progress indicator.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to a **ProgressLinearStyleOption** instance.|
| float strokeRadius | Corner radius of the progress indicator, in vp. The value range is [0, strokeWidth/2]. Default value: **strokeWidth/2**.|

### OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled()

```c
bool OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option)
```

**Description**


Obtains the enabled status of the smooth progress effect.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to a **ProgressLinearStyleOption** instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the enabled status of the smooth progress effect.|

### OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled()

```c
bool OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option)
```

**Description**


Obtains the enabled status of the scan effect.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to a **ProgressLinearStyleOption** instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the enabled status of the scan effect.|

### OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth()

```c
float OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth(ArkUI_ProgressLinearStyleOption* option)
```

**Description**


Obtains the stroke width of the progress indicator.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to a **ProgressLinearStyleOption** instance.|

**Returns**

| Type| Description|
| -- | -- |
| float | Stroke width of the progress indicator, in vp.|

### OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius()

```c
float OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius(ArkUI_ProgressLinearStyleOption* option)
```

**Description**


Obtains the corner radius of the progress indicator.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to a **ProgressLinearStyleOption** instance.|

**Returns**

| Type| Description|
| -- | -- |
| float | Corner radius of the progress indicator, in vp.|

### OH_ArkUI_CreateSnapshotOptions()

```c
ArkUI_SnapshotOptions* OH_ArkUI_CreateSnapshotOptions()
```

**Description**


Creates a snapshot options object, which must be released using [OH_ArkUI_DestroySnapshotOptions()](#oh_arkui_destroysnapshotoptions) when no longer in use.

**Since**: 15

**Returns**

| Type                        | Description|
|----------------------------| -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* | Pointer to the created snapshot options object. If a null pointer is returned, creation failed, possibly due to insufficient memory.|

### OH_ArkUI_DestroySnapshotOptions()

```c
void OH_ArkUI_DestroySnapshotOptions(ArkUI_SnapshotOptions* snapshotOptions)
```

**Description**


Destroys a snapshot options object.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Screenshot options.|

### OH_ArkUI_SnapshotOptions_SetScale()

```c
int32_t OH_ArkUI_SnapshotOptions_SetScale(ArkUI_SnapshotOptions* snapshotOptions, float scale)
```

**Description**


Sets the scale property in the snapshot options.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Screenshot options.|
| float scale | Scale factor.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|
### OH_ArkUI_SnapshotOptions_SetColorMode()

``` C++
int32_t OH_ArkUI_SnapshotOptions_SetColorMode(ArkUI_SnapshotOptions* snapshotOptions, int32_t colorSpace, bool isAuto)
```

**Description**

Sets the color space in the screenshot options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Pointer to the screenshot options.|
| int32_t colorSpace | Color space used for screenshot.<br>If the target component's color space is known, specify it through **colorSpace** and set **isAuto** to **false** to achieve optimal snapshot quality.<br>The supported values are as follows: **3** (RGB color gamut of type Display P3), **4** (RGB color gamut of type sRGB), and **27** ((RGB color gamut of type BT.2020).<br>Default value: **4**<br>This parameter takes effect only when **isAuto** is set to **false**.|
| bool isAuto | Whether the system automatically determines the color space to be used.<br>**true**: The system automatically determines the color space to be used. If the color space used by the component is uncertain, you are advised to set **isAuto** to **true** so that the system can automatically determine the color space to be used.<br>**false**: The color space type set through the **colorSpace** field is used for screenshot.<br>Default value: **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SnapshotOptions_SetDynamicRangeMode()

``` C++
int32_t OH_ArkUI_SnapshotOptions_SetDynamicRangeMode(ArkUI_SnapshotOptions* snapshotOptions, int32_t dynamicRangeMode, bool isAuto)
```

**Description**

Sets the dynamic range mode in the screenshot options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Pointer to the screenshot options.|
| int32_t dynamicRangeMode | Dynamic range mode used for screenshot.<br>If the dynamic range mode used for screenshot is known, you can specify the dynamic range mode using the **dynamicRangeMode** field and set **isAuto** to **false** to achieve the expected snapshot effect.<br>The value can be one of the enumerated values of [ArkUI_DynamicRangeMode](#arkui_dynamicrangemode).<br>Default value: **ARKUI_DYNAMIC_RANGE_MODE_STANDARD**<br>This parameter takes effect only when **isAuto** is set to **false**.|
| bool isAuto | Whether the system automatically determines the dynamic range mode to be used.<br>**true**: whether the system automatically determines the dynamic range mode to be used. If the dynamic range mode used by the component is uncertain, you are advised to set **isAuto** to **true** so that the system can automatically determine the dynamic range mode to be used.<br>**false**: The dynamic range mode set by the **dynamicRangeMode** field is used for screenshot.<br>Default value: **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CrossLanguageOption_Create()

```c
ArkUI_CrossLanguageOption* OH_ArkUI_CrossLanguageOption_Create(void)
```

**Description**


Creates an instance of the cross-language configuration option.

**Since**: 15

**Returns**

| Type                            | Description|
|--------------------------------| -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* | Returns the pointer to the **ArkUI_CrossLanguageOption** instance created. If a null pointer is returned, creation failed, possibly due to insufficient memory.|

### OH_ArkUI_CrossLanguageOption_Destroy()

```c
void OH_ArkUI_CrossLanguageOption_Destroy(ArkUI_CrossLanguageOption* option)
```

**Description**


Destroys an instance of the cross-language configuration option.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | Cross-language configuration option instance to be destroyed.|

### OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus()

```c
void OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus(ArkUI_CrossLanguageOption* option, bool enabled)
```

**Description**


Sets whether cross-language attribute setting is allowed in the configuration option.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | Pointer to the cross-language configuration option instance.|
| bool enabled | Whether cross-language attribute setting is allowed. The default value is **false**.|

### OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus()

```c
bool OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus(ArkUI_CrossLanguageOption* option)
```

**Description**


Checks whether cross-language attribute setting is allowed in the configuration option.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | Pointer to the cross-language configuration option instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether cross-language attribute setting is allowed.|

### OH_ArkUI_VisibleAreaEventOptions_Create()

```c
ArkUI_VisibleAreaEventOptions* OH_ArkUI_VisibleAreaEventOptions_Create()
```

**Description**


Creates an instance of visible area change event parameters.

**Since**: 17

**Returns**

| Type                                | Description|
|------------------------------------| -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* | Returns the created instance of visible area change event parameters.|

### OH_ArkUI_VisibleAreaEventOptions_Dispose()

```c
void OH_ArkUI_VisibleAreaEventOptions_Dispose(ArkUI_VisibleAreaEventOptions* option)
```

**Description**


Disposes of an instance of visible area change event parameters.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Instance of visible area change event parameters to be destroyed.|

### OH_ArkUI_VisibleAreaEventOptions_SetRatios()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_SetRatios(ArkUI_VisibleAreaEventOptions* option, float* value, int32_t size)
```

**Description**


Sets the threshold ratios for visible area changes.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters.|
| float* value | Array of threshold ratios. Each element represents a ratio of the component's visible area (that is, the area of the component that is visible on screen; only the area within the parent component is counted) to the component's total area. The value range of the threshold is [0.0, 1.0]. If the threshold set exceeds this range, the value **0.0** or **1.0** will be used.|
| int32_t size | Size of the array of threshold ratios.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval(ArkUI_VisibleAreaEventOptions *option, int32_t value)
```

**Description**


Sets the expected update interval for visible area changes.  

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md) *option | Pointer to the instance of visible area change event parameters.|
| int32_t value | Expected update interval, in ms.  Default value: **1000**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_VisibleAreaEventOptions_SetMeasureFromViewport()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_SetMeasureFromViewport(ArkUI_VisibleAreaEventOptions* option, bool measureFromViewport)
```

**Description**

Sets the visible area calculation mode.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters.|
| bool measureFromViewport | Visible area calculation mode.<br>**true**: The calculation takes the parent component's **NODE_CLIP** attribute into account. If the parent component's **NODE_CLIP** attribute is **false**: Child components can render beyond the parent component's bounds, and the out-of-bounds area is counted as part of the visible area. If the parent component's **NODE_CLIP** attribute is **true**: Child components are clipped to the parent component's bounds, and the out-of-bounds area is treated as invisible. **false**: The area beyond the parent component's bounds is directly treated as invisible, ignoring the parent component's **NODE_CLIP** attribute.<br>Default value: **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_VisibleAreaEventOptions_GetRatios()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_GetRatios(ArkUI_VisibleAreaEventOptions* option, float* value, int32_t* size)
```

**Description**


Obtains the threshold ratios for visible area changes.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters.|
| float* value | Array of threshold ratios.|
| int32_t* size | Size of the array of threshold ratios.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the provided buffer size is insufficient.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval(ArkUI_VisibleAreaEventOptions* option)
```

**Description**


Obtains the expected update interval for visible area changes.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Expected update interval, in ms.  Default value: **1000**.|


### OH_ArkUI_VisibleAreaEventOptions_GetMeasureFromViewport()

```c
bool OH_ArkUI_VisibleAreaEventOptions_GetMeasureFromViewport(ArkUI_VisibleAreaEventOptions* option)
```

**Description**

Obtains the visible area calculation mode.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Visible area calculation mode.<br>**true**: The calculation takes the parent component's **NODE_CLIP** attribute into account. If the parent component's **NODE_CLIP** attribute is **false**: Child components can render beyond the parent component's bounds, and the out-of-bounds area is counted as part of the visible area. If the parent component's **NODE_CLIP** attribute is **true**: Child components are clipped to the parent component's bounds, and the out-of-bounds area is treated as invisible. **false**: The area beyond the parent component's bounds is directly treated as invisible, ignoring the parent component's **NODE_CLIP** attribute.<br>Default value: **false**.|

### OH_ArkUI_TextPickerRangeContentArray_Create()

```c
ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)
```

**Description**


Creates a **TextPickerRangeContent** array object.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| int32_t length | Length of the **TextPickerRangeContent** array.|

**Returns**

| Type                                    | Description|
|----------------------------------------| -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* | Returns a pointer to an empty **TextPickerRangeContent** array.|

### OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)
```

**Description**


Sets the icon data at the specified position in the **TextPickerRangeContent** array.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **TextPickerRangeContent** array.|
| char* icon | Pointer to the icon image address.|
| int32_t index | Position in the array, starting from 0.|

### OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)
```

**Description**


Sets the text data at the specified position in the **TextPickerRangeContent** array.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **TextPickerRangeContent** array.|
| char* text | Pointer to the text content.|
| int32_t index | Position in the array, starting from 0.|

### OH_ArkUI_TextPickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)
```

**Description**


Destroys a **TextPickerRangeContent** array object.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **TextPickerRangeContent** array.|

### OH_ArkUI_TextCascadePickerRangeContentArray_Create()

```c
ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)
```

**Description**


Creates a **TextCascadePickerRangeContent** array object.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| int32_t length | Length of the **TextPickerRangeContent** array.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* | Returns a pointer to an empty **TextCascadePickerRangeContent** array.|

### OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)
```

**Description**


Sets the text data at the specified position in the **TextCascadePickerRangeContent** array.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the **TextCascadePickerRangeContentHandle** instance.|
| char* text | Pointer to the text content.|
| int32_t index | Position in the array, starting from 0.|

### OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)
```

**Description**


Sets the child data at the specified position in the **TextCascadePickerRangeContent** array.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the **TextCascadePickerRangeContentHandle** instance.|
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* child | Pointer to the child node array.|
| int32_t index | Position in the array, starting from 0.|

### OH_ArkUI_TextCascadePickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy(ArkUI_TextCascadePickerRangeContentArray* handle)
```

**Description**


Destroys a **TextCascadePickerRangeContent** array object.

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the **TextCascadePickerRangeContentHandle** instance.|

### OH_ArkUI_EmbeddedComponentOption_Create()

```c
ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()
```

**Description**


Creates an **EmbeddedComponent** option object.

**Since**: 20

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* | Pointer to the **EmbeddedComponent** option object.|

### OH_ArkUI_EmbeddedComponentOption_Dispose()

```c
void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)
```

**Description**


Disposes of an **EmbeddedComponent** option object.

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* option | Pointer to the target **EmbeddedComponent** option object.|

### OH_ArkUI_EmbeddedComponentOption_SetOnError()

```c
void OH_ArkUI_EmbeddedComponentOption_SetOnError(ArkUI_EmbeddedComponentOption* option, void (*callback)(int32_t code, const char* name, const char* message))
```

**Description**


Sets the **onError** callback for the **EmbeddedComponent** component. This callback is triggered when an error occurs during the running of the **EmbeddedComponent** component.

**Since**: 20


**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* option | Pointer to the **EmbeddedComponent** option object.|
| void (\*callback)(int32_t code, const char* name, const char* message) | User-defined callback function.<br>- **code**: error code returned when the API call fails. For details about error codes, see [UIExtension Error Codes](errorcode-uiextension.md).<br>- **name**: error name returned when the API call fails.<br>- **message**: detailed error message returned when the API call fails.|


### OH_ArkUI_EmbeddedComponentOption_SetOnTerminated()

```c
void OH_ArkUI_EmbeddedComponentOption_SetOnTerminated(ArkUI_EmbeddedComponentOption* option, void (*callback)(int32_t code, AbilityBase_Want* want))
```

**Description**


Sets the **onTerminated** callback for the **EmbeddedComponent** component. This callback is triggered when the **EmbeddedComponent** component exits properly.

**Since**: 20


**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* option | Pointer to the **EmbeddedComponent** option object.|
| void (\*callback)(int32_t code, [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md)* want) | User-defined callback function.<br>- **code**: result code returned when the EmbeddedUIExtensionAbility exits. If the ability exits through **terminateSelfWithResult**, this value matches the code set for the ability. If the ability exits through **terminateSelf**, the default value is **0**.<br>- **want**: data returned when the EmbeddedUIExtensionAbility exits.  |

### OH_ArkUI_PositionEdges_Create()

```c
ArkUI_PositionEdges* OH_ArkUI_PositionEdges_Create()
```

**Description**

Creates a **PositionEdges** object.

**Since**: 21

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* | Pointer to the **PositionEdges** object.|


### OH_ArkUI_PositionEdges_Copy()

```c
ArkUI_PositionEdges* OH_ArkUI_PositionEdges_Copy(const ArkUI_PositionEdges* edges)
```

**Description**

Deep copies the **PositionEdges** object.

**Since**: 21

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the **PositionEdges** object.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* | Pointer to the new **PositionEdges** object.|

### OH_ArkUI_PositionEdges_Dispose()

```c
void OH_ArkUI_PositionEdges_Dispose(ArkUI_PositionEdges* edges)
```

**Description**

Disposes of the **PositionEdges** object.

**Since**: 21

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the **PositionEdges** object.|

### OH_ArkUI_PositionEdges_SetTop()

```c
void OH_ArkUI_PositionEdges_SetTop(ArkUI_PositionEdges* edges, float value)
```

**Description**

Sets the value of the **PositionEdges** object in the top direction.

**Since**: 21

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the **PositionEdges** object.|
|float value|Value of the **PositionEdges** object in the corresponding direction, in vp.|

### OH_ArkUI_PositionEdges_GetTop()

```c
int32_t OH_ArkUI_PositionEdges_GetTop(ArkUI_PositionEdges* edges, float* value)
```

**Description**

Obtains the value of the **PositionEdges** object in the top direction.

**Since**: 21

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the **PositionEdges** object.|
|float* value|Value of the **PositionEdges** object in the corresponding direction, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_PositionEdges_SetLeft()

```c
void OH_ArkUI_PositionEdges_SetLeft(ArkUI_PositionEdges* edges, float value)
```

**Description**

Sets the value of the **PositionEdges** object in the left direction.

**Since**: 21

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the **PositionEdges** object.|
|float value|Value of the **PositionEdges** object in the corresponding direction, in vp.|

### OH_ArkUI_PositionEdges_GetLeft()

```c
int32_t OH_ArkUI_PositionEdges_GetLeft(ArkUI_PositionEdges* edges, float* value)
```

**Description**

Obtains the value of the **PositionEdges** object in the left direction.

**Since**: 21

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the **PositionEdges** object.|
|float* value|Value of the **PositionEdges** object in the corresponding direction, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|


### OH_ArkUI_PositionEdges_SetBottom()

```c
void OH_ArkUI_PositionEdges_SetBottom(ArkUI_PositionEdges* edges, float value)
```

**Description**

Obtains the value of the **PositionEdges** object in the bottom direction.

**Since**: 21

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the **PositionEdges** object.|
|float value|Value of the **PositionEdges** object in the corresponding direction, in vp.|

### OH_ArkUI_PositionEdges_GetBottom()

```c
int32_t OH_ArkUI_PositionEdges_GetBottom(ArkUI_PositionEdges* edges, float* value)
```

**Description**

Obtains the value of the **PositionEdges** object in the bottom direction.

**Since**: 21

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the **PositionEdges** object.|
|float* value|Value of the **PositionEdges** object in the corresponding direction, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_PositionEdges_SetRight()

```c
void OH_ArkUI_PositionEdges_SetRight(ArkUI_PositionEdges* edges, float value)
```

**Description**

Sets the value of the **PositionEdges** object in the right direction.

**Since**: 21

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the **PositionEdges** object.|
|float value|Value of the **PositionEdges** object in the corresponding direction, in vp.|

### OH_ArkUI_PositionEdges_GetRight()

```c
int32_t OH_ArkUI_PositionEdges_GetRight(ArkUI_PositionEdges* edges, float* value)
```

**Description**

Obtains the value of the **PositionEdges** object in the right direction.

**Since**: 21

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the **PositionEdges** object.|
|float* value|Value of the **PositionEdges** object in the corresponding direction, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_PixelRoundPolicy_Create()

```c
ArkUI_PixelRoundPolicy* OH_ArkUI_PixelRoundPolicy_Create()
```

**Description**

Creates a **PixelRoundPolicy** attribute object.

**Since**: 21

**Returns**

| Type                                                        | Description                            |
| ------------------------------------------------------------ | -------------------------------- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* | Pointer to the **PixelRoundPolicy** object.|

### OH_ArkUI_PixelRoundPolicy_Dispose()

```c
void OH_ArkUI_PixelRoundPolicy_Dispose(ArkUI_PixelRoundPolicy* policy)
```

**Description**

Disposes of the **PixelRoundPolicy** object.

**Since**: 21

**Parameters**

| Name                                                      | Description                                    |
| ------------------------------------------------------------ | ---------------------------------------- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the target **PixelRoundPolicy** object.|

### OH_ArkUI_PixelRoundPolicy_SetTop()

```c
void OH_ArkUI_PixelRoundPolicy_SetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)
```

**Description**

Sets the top edge pixel rounding policy for the **PixelRoundPolicy** object.

**Since**: 21

**Parameters**

| Name                                                      | Description                                |
| ------------------------------------------------------------ | ------------------------------------ |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the **PixelRoundPolicy** object.    |
| [ArkUI_PixelRoundCalcPolicy](#arkui_pixelroundcalcpolicy) value | Specific pixel rounding policy.|

### OH_ArkUI_PixelRoundPolicy_GetTop()

```c
int32_t OH_ArkUI_PixelRoundPolicy_GetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)
```

**Description**

Obtains the top edge pixel rounding policy from the **PixelRoundPolicy** object.

**Since**: 21

**Parameters**

| Name                                                      | Description                                |
| ------------------------------------------------------------ | ------------------------------------ |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the **PixelRoundPolicy** object.    |
| [ArkUI_PixelRoundCalcPolicy](#arkui_pixelroundcalcpolicy)* value | Specific pixel rounding policy.|

**Returns**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_PixelRoundPolicy_SetStart()

```c
void OH_ArkUI_PixelRoundPolicy_SetStart(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)
```

**Description**

Sets the start edge pixel rounding policy for the **PixelRoundPolicy** object.

**Since**: 21

**Parameters**

| Name                                                      | Description                                |
| ------------------------------------------------------------ | ------------------------------------ |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the **PixelRoundPolicy** object.    |
| [ArkUI_PixelRoundCalcPolicy](#arkui_pixelroundcalcpolicy) value | Specific pixel rounding policy.|

### OH_ArkUI_PixelRoundPolicy_GetStart()

```c
int32_t OH_ArkUI_PixelRoundPolicy_GetStart(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)
```

**Description**

Obtains the start edge pixel rounding policy from the **PixelRoundPolicy** object. 

**Since**: 21

**Parameters**

| Name                                                      | Description                                |
| ------------------------------------------------------------ | ------------------------------------ |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the **PixelRoundPolicy** object.    |
| [ArkUI_PixelRoundCalcPolicy](#arkui_pixelroundcalcpolicy)* value | Specific pixel rounding policy.|

**Returns**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_PixelRoundPolicy_SetBottom()

```c
void OH_ArkUI_PixelRoundPolicy_SetBottom(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)
```

**Description**

Sets the bottom edge pixel rounding policy for the **PixelRoundPolicy** object.

**Since**: 21

**Parameters**

| Name                                                      | Description                                |
| ------------------------------------------------------------ | ------------------------------------ |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the **PixelRoundPolicy** object.    |
| [ArkUI_PixelRoundCalcPolicy](#arkui_pixelroundcalcpolicy) value | Specific pixel rounding policy.|

### OH_ArkUI_PixelRoundPolicy_GetBottom()

```c
int32_t OH_ArkUI_PixelRoundPolicy_GetBottom(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)
```

**Description**

Obtains the bottom edge pixel rounding policy from the **PixelRoundPolicy** object.

**Since**: 21

**Parameters**

| Name                                                      | Description                                |
| ------------------------------------------------------------ | ------------------------------------ |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the **PixelRoundPolicy** object.    |
| [ArkUI_PixelRoundCalcPolicy](#arkui_pixelroundcalcpolicy)* value | Specific pixel rounding policy.|

**Returns**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_PixelRoundPolicy_SetEnd()

```c
void OH_ArkUI_PixelRoundPolicy_SetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)
```

**Description**

Sets the end edge pixel rounding policy for the **PixelRoundPolicy** object.

**Since**: 21

**Parameters**

| Name                                                      | Description                                |
| ------------------------------------------------------------ | ------------------------------------ |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the **PixelRoundPolicy** object.    |
| [ArkUI_PixelRoundCalcPolicy](#arkui_pixelroundcalcpolicy) value | Specific pixel rounding policy.|

### OH_ArkUI_PixelRoundPolicy_GetEnd()

```c
int32_t OH_ArkUI_PixelRoundPolicy_GetEnd(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)
```

**Description**

Obtains the end edge pixel rounding policy from the **PixelRoundPolicy** object.

**Since**: 21

**Parameters**

| Name                                                      | Description                                |
| ------------------------------------------------------------ | ------------------------------------ |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the **PixelRoundPolicy** object.    |
| [ArkUI_PixelRoundCalcPolicy](#arkui_pixelroundcalcpolicy)* value | Specific pixel rounding policy.|

**Returns**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ContentTransitionEffect_Create()

```c
ArkUI_ContentTransitionEffect* OH_ArkUI_ContentTransitionEffect_Create(int32_t type)
```

**Description**

Creates a **ContentTransitionEffect** attribute object.

**Since**: 21

**Parameters**

| Name| Description                          |
| -- |------------------------------|
| int32_t type | Transition animation type. **0**: No transition animation. **1**: Fade-in and fade-out transition animation.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md)* | Pointer to the **ContentTransitionEffect** object.|

### OH_ArkUI_GridLayoutOptions_Create()

```c
ArkUI_GridLayoutOptions* OH_ArkUI_GridLayoutOptions_Create()
```

**Description**

Creates **Grid** layout options.

**Since**: 22

**Returns**

| Type                               | Description|
|-----------------------------------| -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* | **Grid** layout options.|

### OH_ArkUI_GridLayoutOptions_Dispose()

```c
void OH_ArkUI_GridLayoutOptions_Dispose(ArkUI_GridLayoutOptions* option)
```

**Description**

Disposes **Grid** layout options.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | **Grid** layout options.|


### OH_ArkUI_GridLayoutOptions_SetIrregularIndexes()

```c
int32_t OH_ArkUI_GridLayoutOptions_SetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t size)
```

**Description**

Sets the irregular grid item index array for the grid layout.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | **Grid** layout options.|
| uint32_t* irregularIndexes |  **GridItem** index array.|
| int32_t size | Size of the **GridItem** index array.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_GridLayoutOptions_GetIrregularIndexes()

```c
int32_t OH_ArkUI_GridLayoutOptions_GetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t* size)
```

**Description**

Obtains the irregular grid item index array for the grid layout. When **OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback** is not set, the grid item specified in this parameter occupies an entire row of the grid that scrolls vertically or an entire column of the grid that scrolls horizontally.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | **Grid** layout options.|
| uint32_t* irregularIndexes |  **GridItem** index array.|
| int32_t size | Size of the **GridItem** index array.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the provided buffer size is insufficient.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback()

```c
void OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemSize (*callback)(int32_t itemIndex, void* userData))
```

**Description**

Registers a callback to obtain the row and column span for the grid item at the specified index.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | **Grid** layout options.|
| void* userData | User-defined data.|
| ArkUI_GridItemSize (\*callback)(int32_t itemIndex, void* userData) | Callback that returns the row and column span for the grid item at the specified index.<br> **itemIndex**: grid item index, which must be within the range set by [OH_ArkUI_GridLayoutOptions_SetIrregularIndexes](capi-native-type-h.md#oh_arkui_gridlayoutoptions_setirregularindexes).|

### OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback()

```c
void OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemRect (*callback)(int32_t itemIndex, void* userData))
```

**Description**

Registers a callback to obtain the starting row, starting column, row span, and column span for the grid item at the specified index.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | **Grid** layout options.|
| void* userData | User-defined data.|
| ArkUI_GridItemRect (\*callback)(int32_t itemIndex, void* userData) | Callback that returns the starting row, starting column, row span, and column span for the grid item at the specified index.<br>   **itemIndex**: grid item index.|
### OH_ArkUI_ShowCounterConfig_Create()

```c
ArkUI_ShowCounterConfig* OH_ArkUI_ShowCounterConfig_Create()
```

**Description**


Creates a text input counter configuration object.

**Since**: 22


**Returns**

| Type                        | Description|
|----------------------------| -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-swiperindicator.md)* | Pointer to the text input counter configuration object.|

### OH_ArkUI_ShowCounterConfig_Dispose()

```c
void OH_ArkUI_ShowCounterConfig_Dispose(ArkUI_ShowCounterConfig* config)
```

**Description**


Disposes the text input counter configuration object.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)* config | Pointer to the text input counter configuration object to be disposed.|

### OH_ArkUI_ShowCounterConfig_SetCounterTextColor()

```c
void OH_ArkUI_ShowCounterConfig_SetCounterTextColor(ArkUI_ShowCounterConfig* config, uint32_t color)
```

**Description**


Sets the text color of the counter when the text input has not reached the maximum character limit.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)* config | Pointer to the text input counter configuration object.|
| uint32_t color | Counter text color in 0xARGB format.|

### OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor()

```c
void OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor(ArkUI_ShowCounterConfig* config, uint32_t color)
```

**Description**


Sets the text color of the counter when the text input exceeds the maximum character limit.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)* config | Pointer to the text input counter configuration object.|
| uint32_t color | Counter text color in 0xARGB format.|

### OH_ArkUI_ShowCounterConfig_GetCounterTextColor()

```c
uint32_t OH_ArkUI_ShowCounterConfig_GetCounterTextColor(ArkUI_ShowCounterConfig* config)
```

**Description**


Obtains the text color of the counter when the text input has not reached the maximum character limit.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)* config | Pointer to the text input counter configuration object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t  | Counter text color in 0xARGB format. Returns **0** if no color has been set via [OH_ArkUI_ShowCounterConfig_SetCounterTextColor](#oh_arkui_showcounterconfig_setcountertextcolor).|


### OH_ArkUI_ShowCounterConfig_GetCounterTextOverflowColor()

```c
uint32_t OH_ArkUI_ShowCounterConfig_GetCounterTextOverflowColor(ArkUI_ShowCounterConfig* config)
```

**Description**


Obtains the text color of the counter when the text input exceeds the maximum character limit.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)* config | Pointer to the text input counter configuration object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Counter text color in 0xARGB format. Returns **0** if no color has been set via [OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor](#oh_arkui_showcounterconfig_setcountertextoverflowcolor).|

### OH_ArkUI_SelectionOptions_Create()

```c
ArkUI_SelectionOptions OH_ArkUI_SelectionOptions_Create()
```

**Description**


Creates a selection option.

**Since**: 23


**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md)* | Pointer to the selection option.|

### OH_ArkUI_SelectionOptions_Dispose()

```c
void OH_ArkUI_SelectionOptions_Dispose(ArkUI_SelectionOptions* options)
```

**Description**


Releases a selection option.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md)* options | Pointer to the selection option to be released|

### OH_ArkUI_SelectionOptions_SetMenuPolicy()

```c
void OH_ArkUI_SelectionOptions_SetMenuPolicy(ArkUI_SelectionOptions* options, ArkUI_MenuPolicy menuPolicy)
```

**Description**


Sets the menu pop-up policy for selecting options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md)* options | Pointer to the selection option.|
| [ArkUI_MenuPolicy ](#arkui_menupolicy) menuPolicy | Menu display policy.|

### OH_ArkUI_SelectionOptions_GetMenuPolicy()

```c
ArkUI_MenuPolicy  OH_ArkUI_SelectionOptions_GetMenuPolicy(ArkUI_SelectionOptions* options)
```

**Description**


Obtains the menu display policy of a selection option.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md)* options | Pointer to the selection option.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_MenuPolicy ](#arkui_menupolicy) | Menu display policy.|

### OH_ArkUI_TextContentBaseController_Create()

```c
ArkUI_TextContentBaseController* OH_ArkUI_TextContentBaseController_Create()
```

**Description**

Creates a basic controller object for text content.

**Since**: 23

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)* | Pointer to the controller object.|

### OH_ArkUI_TextContentBaseController_Dispose()

```c
void OH_ArkUI_TextContentBaseController_Dispose(ArkUI_TextContentBaseController* controller)
```

**Description**

Destroys a basic controller object for text content.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)* controller | Pointer to the controller to be destroyed.|

### OH_ArkUI_TextContentBaseController_DeleteBackward()

```c
void OH_ArkUI_TextContentBaseController_DeleteBackward(ArkUI_TextContentBaseController* controller)
```

**Description**

Deletes the character before the cursor in editing state; deletes the last character of the text box component in other states.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)* controller | Pointer to the configuration object to be modified.|

### OH_ArkUI_TextContentBaseController_ScrollToVisible()

```c
void OH_ArkUI_TextContentBaseController_ScrollToVisible(ArkUI_TextContentBaseController* controller, int32_t start, int32_t end)
```

**Description**

Passes the start and end indexes to the bound text box component, and scrolls the text within the range to the visible area.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)* controller | Pointer to the configuration object to be modified.<br>Pass the start and end indexes to the bound text box component and scroll the text within the range.|
| int32_t start | Start text index.<br>The start index must be less than or equal to the end index. Otherwise, the API call is invalid. The value range is [0, Total length of the text in the text box]. If the start index is less than 0, the start index is regarded as 0. If the start index is greater than the total length, the start index is regarded as the total length.|
| int32_t end | End text index.<br>The end index must be greater than or equal to the start index. Otherwise, the API call is invalid. The value range is [0, Total length of the text in the text box]. If the end index is less than 0, the end index is regarded as 0. If the end index is greater than the total length, the end index is regarded as the total length.|

### OH_ArkUI_TextMenuItem_Create()

```c
ArkUI_TextMenuItem* OH_ArkUI_TextMenuItem_Create()
```

**Description**

Creates a text menu item.

**Since**: 22

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* | Pointer to the **ArkUI_TextMenuItem** object.|

### OH_ArkUI_TextMenuItem_Dispose()

```c
void OH_ArkUI_TextMenuItem_Dispose(ArkUI_TextMenuItem* textMenuItem)
```

**Description**

Releases a text menu item.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* textMenuItem | Pointer to the **ArkUI_TextMenuItem** object.|

### OH_ArkUI_TextMenuItem_SetContent()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetContent(ArkUI_TextMenuItem* item, const char* content)
```

**Description**

Sets the title of a text menu item.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | Pointer to the **ArkUI_TextMenuItem** object.|
| const char* content | Title of a text menu item. The default value is an empty string.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMenuItem_GetContent()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetContent(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the title of a text menu item.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | Pointer to the **ArkUI_TextMenuItem** object.|
| char* buffer | Buffer. You can create it and allocate memory to store the title information of the text menu item.|
| int32_t bufferSize | Buffer size.|
| int32_t* writeLength | If the return value is [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode), the length of the data written to the buffer is returned.<br> If the return value is [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode), the minimum length required for writing the string to the buffer is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode): The buffer size is insufficient.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMenuItem_SetIcon()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetIcon(ArkUI_TextMenuItem* item, const char* icon)
```

**Description**

Sets the icon path of a text menu item.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | Pointer to the **ArkUI_TextMenuItem** object.|
| const char* icon | Icon path of the text menu item. The default value is an empty string.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMenuItem_GetIcon()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetIcon(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the icon path of a text menu item.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | Pointer to the **ArkUI_TextMenuItem** object.|
| char* buffer | Buffer. You can create it and allocate memory to store the icon path of the text menu item.|
| int32_t bufferSize | Buffer size.|
| int32_t* writeLength | If the return value is [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode), the length of the data written to the buffer is returned.<br> If the return value is [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode), the minimum length required for writing the string to the buffer is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode): The buffer size is insufficient.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMenuItem_SetLabelInfo()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetLabelInfo(ArkUI_TextMenuItem* item, const char* labelInfo)
```

**Description**

Sets the shortcut hint for a text menu item, for example, the shortcut hint for the **Copy** menu item can be set to **Ctrl+C**.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | Pointer to the **ArkUI_TextMenuItem** object.|
| const char* labelInfo | Shortcut hint of a text menu item. The default value is an empty string.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMenuItem_GetLabelInfo()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetLabelInfo(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the shortcut hint for a text menu item, for example, the shortcut hint for the **Copy** menu item is typically **Ctrl+C**.

**Since**: 22

**Parameters**

| Name| Description|
| ------ | --- |
| const [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | Pointer to the **ArkUI_TextMenuItem** object.|
| char* buffer | Buffer. You can create it and allocate memory to store the shortcut hint of the text menu item.|
| int32_t bufferSize | Buffer size.|
| int32_t* writeLength | If the return value is [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode), the length of the data written to the buffer is returned.<br> If the return value is [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode), the minimum length required for writing the string to the buffer is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode): The buffer size is insufficient.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMenuItem_SetId()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetId(ArkUI_TextMenuItem* item, int32_t id)
```

**Description**

Sets the ID of a text menu item.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | Pointer to the **ArkUI_TextMenuItem** object.|
| int32_t id | ID of a text menu item.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMenuItem_GetId()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetId(const ArkUI_TextMenuItem* item, int32_t* id)
```

**Description**

Obtains the ID of a text menu item.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | Pointer to the **ArkUI_TextMenuItem** object.|
| int32_t* id | ID of a text menu item.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMenuItemArray_GetSize()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_GetSize(ArkUI_TextMenuItemArray* items, int32_t* size)
```

**Description**

Obtains the size of the text menu item array.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | Pointer to the **ArkUI_TextMenuItemArray** object.|
| int32_t* size | Size of the text menu item array.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMenuItemArray_GetItem()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_GetItem(ArkUI_TextMenuItemArray* items, int32_t index, ArkUI_TextMenuItem** item)
```

**Description**

Obtains the text menu item at a specified index from the text menu item array.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | Pointer to the **ArkUI_TextMenuItemArray** object.|
| int32_t index | Index position.|
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)** item | Level-2 pointer to the **ArkUI_TextMenuItem** object.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMenuItemArray_Insert()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Insert(ArkUI_TextMenuItemArray* items, ArkUI_TextMenuItem* item, int32_t index)
```

**Description**

Inserts a text menu item at a specified index into the text menu item array.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | Pointer to the **ArkUI_TextMenuItemArray** object.|
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | Pointer to the **ArkUI_TextMenuItem** object.|
| int32_t index | Index position of the text menu item to be inserted.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMenuItemArray_Erase()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Erase(ArkUI_TextMenuItemArray* items, int32_t index)
```

**Description**

Deletes the text menu item at a specified index from the text menu item array.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | Pointer to the **ArkUI_TextMenuItemArray** object.|
| int32_t index | Index of the text menu item to be deleted.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMenuItemArray_Clear()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Clear(ArkUI_TextMenuItemArray* items)
```

**Description**

Clears all text menu items in the text menu item array.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | Pointer to the **ArkUI_TextMenuItemArray** object.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextEditMenuOptions_Create()

```c
ArkUI_TextEditMenuOptions* OH_ArkUI_TextEditMenuOptions_Create()
```

**Description**

Creates a text menu extension object.

**Since**: 22

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | Pointer to the **ArkUI_TextEditMenuOptions** object.|


### OH_ArkUI_TextEditMenuOptions_Dispose()

```c
void OH_ArkUI_TextEditMenuOptions_Dispose(ArkUI_TextEditMenuOptions* editMenuOptions)
```

**Description**

Releases a text menu extension object.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | Pointer to the **ArkUI_TextEditMenuOptions** object.|

### ArkUI_TextCreateMenuCallback()

```c
typedef void (*ArkUI_TextCreateMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)
```

**Description**

Callback for the text menu creation event. This callback is triggered when a text menu is created, allowing you to set menu data in it.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | Pointer to the **ArkUI_TextMenuItemArray** object, which is created and released by the system. You can call [OH_ArkUI_TextMenuItemArray_Insert](capi-native-type-h.md#oh_arkui_textmenuitemarray_insert) and [OH_ArkUI_TextMenuItemArray_Erase](capi-native-type-h.md#oh_arkui_textmenuitemarray_erase) to modify the array in the callback.|
| void\* userData | User-defined data.|

### ArkUI_TextPrepareMenuCallback()

```c
typedef void (*ArkUI_TextPrepareMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)
```

**Description**

Callback for the text menu preparation event. This callback is called when the text selection area changes and before the menu is displayed, allowing you to set menu data in it.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | Pointer to the **ArkUI_TextMenuItemArray** object, which is created and released by the system. You can call [OH_ArkUI_TextMenuItemArray_Insert](capi-native-type-h.md#oh_arkui_textmenuitemarray_insert) and [OH_ArkUI_TextMenuItemArray_Erase](capi-native-type-h.md#oh_arkui_textmenuitemarray_erase) to modify the array in the callback.|
| void\* userData | User-defined data.|

### ArkUI_TextMenuItemClickCallback()

```c
typedef bool (*ArkUI_TextMenuItemClickCallback)(const ArkUI_TextMenuItem* item,int32_t start, int32_t end, void* userData)
```

**Description**

Callback for the text menu item click event. This callback is called when a menu item is clicked. You can intercept the default processing behavior in this callback.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | Pointer to the **ArkUI_TextMenuItem** object, indicating the clicked text menu item.|
| int32_t start | Start index of the selected text.|
| int32_t end | End index of the selected text.|
| void\* userData | User-defined data.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether to intercept the default processing behavior of the system.<br> **true**: Intercept the system's default processing behavior. For example, clicking text menu items such as **Paste** or **Copy** will only execute the custom processing behavior.<br> **false**: Do not intercept the system's default processing behavior. For example, clicking text menu items such as **Paste** or **Copy** will first execute the custom processing behavior and then the default processing behavior.|

### OH_ArkUI_TextEditMenuOptions_RegisterOnCreateMenuCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnCreateMenuCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextCreateMenuCallback cb)
```

**Description**

Registers the callback for creating text menus.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | Pointer to the **ArkUI_TextEditMenuOptions** object.|
| void* userData | User-defined data.|
| [ArkUI_TextCreateMenuCallback](capi-native-type-h.md#arkui_textcreatemenucallback) cb | Callback for creating text menus.|

**Returns**

| Type| Description|
| ---- | --- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextEditMenuOptions_RegisterOnPrepareMenuCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnPrepareMenuCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextPrepareMenuCallback cb)
```

**Description**

Registers the callback for preparing text menus.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | Pointer to the **ArkUI_TextEditMenuOptions** object.|
| void* userData | User-defined data.|
| [ArkUI_TextPrepareMenuCallback](capi-native-type-h.md#arkui_textpreparemenucallback) cb | Callback for preparing text menus.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextEditMenuOptions_RegisterOnMenuItemClickCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnMenuItemClickCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextMenuItemClickCallback cb)
```

**Description**

Registers the callback for text menu item clicks.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | Pointer to the **ArkUI_TextEditMenuOptions** object.|
| void* userData | User-defined data.|
| [ArkUI_TextMenuItemClickCallback](capi-native-type-h.md#arkui_textmenuitemclickcallback) cb | Callback for text menu item clicks.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextSelectionMenuOptions_Create()

```c
ArkUI_TextSelectionMenuOptions* OH_ArkUI_TextSelectionMenuOptions_Create();
```

**Description**

Creates a custom text selection menu.

**Since**: 22

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* | Pointer to the **ArkUI_TextSelectionMenuOptions** object.|


### OH_ArkUI_TextSelectionMenuOptions_Dispose()

```c
void OH_ArkUI_TextSelectionMenuOptions_Dispose(ArkUI_TextSelectionMenuOptions* selectionMenuOptions)
```

**Description**

Releases a custom text selection menu object.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the **ArkUI_TextSelectionMenuOptions** object.|

### OH_ArkUI_TextSelectionMenuOptions_SetSpanType()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetSpanType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextSpanType textSpanType)
```

**Description**

Sets the recognition type of a custom text selection menu.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the **ArkUI_TextSelectionMenuOptions** object.|
| [ArkUI_TextSpanType](capi-native-type-h.md#arkui_textspantype) textSpanType | Recognition type of a custom text selection menu.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextSelectionMenuOptions_GetSpanType()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetSpanType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextSpanType* spanType)
```

**Description**

Obtains the recognition type of a custom text selection menu.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the **ArkUI_TextSelectionMenuOptions** object.|
| [ArkUI_TextSpanType](capi-native-type-h.md#arkui_textspantype)* spanType | Recognition type of a custom text selection menu.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextSelectionMenuOptions_SetContentNode()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetContentNode(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_NodeHandle node)
```

**Description**

Sets the content node of a custom text selection menu.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the **ArkUI_TextSelectionMenuOptions** object.|
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Content node of the custom text selection menu.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextSelectionMenuOptions_GetContentNode()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetContentNode(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_NodeHandle* node)
```

**Description**

Obtains the content node of a custom text selection menu.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the **ArkUI_TextSelectionMenuOptions** object.|
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* node | Content node of the custom text selection menu.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextSelectionMenuOptions_SetResponseType()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetResponseType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextResponseType responseType)
```

**Description**

Sets the response type of a custom text selection menu.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the **ArkUI_TextSelectionMenuOptions** object.|
| [ArkUI_TextResponseType](capi-native-type-h.md#arkui_textresponsetype) responseType | Response type of the custom text selection menu.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextSelectionMenuOptions_GetResponseType()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetResponseType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextResponseType* responseType)
```

**Description**

Obtains the response type of a custom text selection menu.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the **ArkUI_TextSelectionMenuOptions** object.|
| [ArkUI_TextResponseType](capi-native-type-h.md#arkui_textresponsetype)* responseType | Response type of the custom text selection menu.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuShowCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuShowCallback(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, void* userData, void (*callback)(int32_t start, int32_t end, void* userData))
```

**Description**

Registers the callback for the event of showing a custom text selection menu.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the **ArkUI_TextSelectionMenuOptions** object.|
| void* userData | User-defined data, which can be any value. After the setting, the value is returned through the callback.|
| void (\*callback)(int32_t start, int32_t end, void* userData) | Callback for the event of showing a custom text selection menu.<br> **start**: start position of the selected text.<br> **end**: end position of the selected text.<br> **userData**: user-defined data, which corresponds to the input parameter **userData** of the **OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuShowCallback** API.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuHideCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuHideCallback(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, void* userData, void (*callback)(int32_t start, int32_t end, void* userData))
```

**Description**

Registers the callback for the event of hiding a custom text selection menu.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | Pointer to the **ArkUI_TextSelectionMenuOptions** object.|
| void* userData | User-defined data, which can be any value. After the setting, the value is returned through the callback.|
| void (\*callback)(int32_t start, int32_t end, void* userData) | Callback for the event of hiding a custom text selection menu.<br> **start**: start position of the selected text.<br> **end**: end position of the selected text.<br> **userData**: user-defined data, which corresponds to the input parameter **userData** of the **OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuHideCallback** API.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextMarqueeOptions_Create
``` c
ArkUI_TextMarqueeOptions* OH_ArkUI_TextMarqueeOptions_Create()
```

**Description**

Creates a text marquee option.

**Since**: 23

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)*| Pointer to the text marquee option to be created.|

### OH_ArkUI_TextMarqueeOptions_Dispose
``` c
void OH_ArkUI_TextMarqueeOptions_Dispose(ArkUI_TextMarqueeOptions* option)
```

**Description**

Destroys the pointer to a text marquee option.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Pointer to a text marquee option to be destroyed.|


### OH_ArkUI_TextMarqueeOptions_SetStart
``` c
void OH_ArkUI_TextMarqueeOptions_SetStart(ArkUI_TextMarqueeOptions* option, bool start)
```

**Description**

Sets whether to play text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|
| bool start | Whether to play text marquee options. **true** indicates to play; **false** indicates not to play.|

### OH_ArkUI_TextMarqueeOptions_GetStart
``` c
bool OH_ArkUI_TextMarqueeOptions_GetStart(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains whether to play text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether to play text marquee options. **true** indicates to play; **false** indicates not to play.|


### OH_ArkUI_TextMarqueeOptions_SetStep
``` c
void OH_ArkUI_TextMarqueeOptions_SetStep(ArkUI_TextMarqueeOptions* option, float step)
```

**Description**

Sets the step of text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|
| float step | Step. Unit: vp.|

### OH_ArkUI_TextMarqueeOptions_GetStep
``` c
float OH_ArkUI_TextMarqueeOptions_GetStep(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the step of text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|

**Returns**

| Type| Description|
| -- | -- |
| float | Step. Unit: vp.|


### OH_ArkUI_TextMarqueeOptions_SetSpacing
``` c
void OH_ArkUI_TextMarqueeOptions_SetSpacing(ArkUI_TextMarqueeOptions* option, float spacing)
```

**Description**

Sets the distance between the start and end items of the text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|
| float spacing | Spacing between the start and end items. Unit: vp.|

### OH_ArkUI_TextMarqueeOptions_GetSpacing
``` c
float OH_ArkUI_TextMarqueeOptions_GetSpacing(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the distance between the start and end items of the text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|

**Returns**

| Type| Description|
| -- | -- |
| float | Spacing between the start and end items. Unit: vp.|



### OH_ArkUI_TextMarqueeOptions_SetLoop
``` c
void OH_ArkUI_TextMarqueeOptions_SetLoop(ArkUI_TextMarqueeOptions* option, int32_t loop)
```

**Description**

Sets the number of repetitions for looping text marquee options. The value **0** or negative value indicates infinite looping.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|
| int32_t loop | Number of loops.|

### OH_ArkUI_TextMarqueeOptions_GetLoop
``` c
int32_t OH_ArkUI_TextMarqueeOptions_GetLoop(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the number of repetitions for looping text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Number of loops.|



### OH_ArkUI_TextMarqueeOptions_SetFromStart
``` c
void OH_ArkUI_TextMarqueeOptions_SetFromStart(ArkUI_TextMarqueeOptions* option, bool fromStart)
```

**Description**

Sets the scrolling direction for looping text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|
| bool fromStart | Scrolling direction for looping text marquee options. **true** to scroll from the start; **false** to scroll in reverse.|

### OH_ArkUI_TextMarqueeOptions_GetFromStart
``` c
bool OH_ArkUI_TextMarqueeOptions_GetFromStart(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the scrolling direction for looping text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Scrolling direction for looping text marquee options. **true** to scroll from the start; **false** to scroll in reverse.|


### OH_ArkUI_TextMarqueeOptions_SetDelay
``` c
void OH_ArkUI_TextMarqueeOptions_SetDelay(ArkUI_TextMarqueeOptions* option, int32_t delay)
```

**Description**

Sets the delay of each loop for text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|
| int32_t delay| Delay of each loop, in milliseconds.|

### OH_ArkUI_TextMarqueeOptions_GetDelay
``` c
int32_t OH_ArkUI_TextMarqueeOptions_GetDelay(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the delay of each loop for text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Delay of each loop, in milliseconds.|

### OH_ArkUI_TextMarqueeOptions_SetFadeout
``` c
void OH_ArkUI_TextMarqueeOptions_SetFadeout(ArkUI_TextMarqueeOptions* option, bool fadeout)
```

**Description**

Sets whether text marquee options support a fade-out effect when the text is too long. When supported, if the text content exceeds the display range, the edges of the partially visible text will have a fade-out effect applied.<br> If both ends have partially visible text, both ends will have the fade-out effect applied.<br> When the fade-out effect is enabled, the [NODE_CLIP](./capi-native-node-h.md#arkui_nodeattributetype) attribute is automatically fixed at **true** and cannot be set to **false**.


**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|
| bool fadeout| Whether text marquee options support a fade-out effect when the text is too long.<br>**true** to apply a fade-out effect when the text is too long, **false** otherwise.|

### OH_ArkUI_TextMarqueeOptions_GetFadeout
``` c
bool OH_ArkUI_TextMarqueeOptions_GetFadeout(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains whether text marquee options support a fade-out effect when the text is too long.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether text marquee options support a fade-out effect when the text is too long.|


### OH_ArkUI_TextMarqueeOptions_SetStartPolicy
``` c
void OH_ArkUI_TextMarqueeOptions_SetStartPolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeStartPolicy startPolicy)

```

**Description**

Sets the startup policy of the text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|
| [ArkUI_MarqueeStartPolicy](#arkui_marqueestartpolicy) startPolicy| Startup policy.|

### OH_ArkUI_TextMarqueeOptions_GetStartPolicy
``` c
ArkUI_MarqueeStartPolicy OH_ArkUI_TextMarqueeOptions_GetStartPolicy(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the startup policy of the text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|

**Returns**

| Type| Description|
| -- | -- |
| ArkUI_MarqueeStartPolicy | Startup policy.|


### OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy
``` c
void OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy(ArkUI_TextMarqueeOptions* option,
    ArkUI_MarqueeUpdatePolicy updatePolicy)
```

**Description**

Sets the update policy of the text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|
| [ArkUI_MarqueeUpdatePolicy](#arkui_marqueeupdatepolicy) updatePolicy| Update policy.|

### OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy
``` c
ArkUI_MarqueeUpdatePolicy OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the update policy of the text marquee options.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoption.md)* option | Text marquee option.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_MarqueeUpdatePolicy](#arkui_marqueeupdatepolicy) | Update policy.|

### OH_ArkUI_SelectedDragPreviewStyle_Create()

```c
ArkUI_SelectedDragPreviewStyle* OH_ArkUI_SelectedDragPreviewStyle_Create();
```

**Description**

Creates a preview style shown when dragging selected text.

**Since**: 23

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md)* | Pointer to the **ArkUI_SelectedDragPreviewStyle** object.|


### OH_ArkUI_SelectedDragPreviewStyle_Dispose()

```c
void OH_ArkUI_SelectedDragPreviewStyle_Dispose(ArkUI_SelectedDragPreviewStyle* config)
```

**Description**

Destroys the preview style shown when dragging selected text.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md)* config | Pointer to the **ArkUI_SelectedDragPreviewStyle** object.|

### OH_ArkUI_SelectedDragPreviewStyle_SetColor()

```c
void  OH_ArkUI_SelectedDragPreviewStyle_SetColor(ArkUI_SelectedDragPreviewStyle* config, uint32_t color);
```

**Description**

Sets the background color of the preview style shown when dragging selected text.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md)* config | Pointer to the **ArkUI_SelectedDragPreviewStyle** object.|
| uint32_t color  | Background color of the preview style shown when dragging selected text, in RGBA format.|

### OH_ArkUI_SelectedDragPreviewStyle_GetColor()

```c
uint32_t OH_ArkUI_SelectedDragPreviewStyle_GetColor(ArkUI_SelectedDragPreviewStyle* config)
```

**Description**

Obtains the background color of the preview style shown when dragging selected text.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md)* config | Pointer to the **ArkUI_SelectedDragPreviewStyle** object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t color | Background color of the preview style shown when dragging selected text, in RGBA format.|

### OH_ArkUI_MotionPathOptions_Create()

``` c
ArkUI_MotionPathOptions* OH_ArkUI_MotionPathOptions_Create()
```

**Description**

Create a motion path option for path animation.

**Since**: 23

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).<br>In the newly created [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md) object, **path** (motion path) is an empty string, **from** (start progress) is **0**, **to** (end progress) is **1**, and **rotatable** (whether the component rotates along the path) is **false**.|

### OH_ArkUI_MotionPathOptions_Dispose()

``` c
void OH_ArkUI_MotionPathOptions_Dispose(ArkUI_MotionPathOptions* options)
```

**Description**


Destroys a motion path option of path animation.

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|

### OH_ArkUI_MotionPathOptions_SetPath()

``` c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetPath(ArkUI_MotionPathOptions* options, const char* svgPath)
```

**Description**

Sets the motion path of path animation.

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|
| const char* svgPath | Motion path string of path animation.<br>The path supports "start" and "end" as placeholders for the start and end points, for example, "Mstart.x start.y L50 50 Lend.x end.y Z". For details about the path string format, see [Path Drawing](../../ui/ui-js-components-svg-path.md). Setting this to an empty string is equivalent to not setting a motion path.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_MotionPathOptions_GetPath()

``` c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetPath(const ArkUI_MotionPathOptions* options, char* svgPathBuffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the motion path string stored in the motion path configuration item of the path animation.

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|
| char* svgPathBuffer | Pointer to the buffer for storing the motion path string.|
| const int32_t bufferSize | Size of the buffer that the **svgPathBuffer** parameter points to.|
| int32_t* writeLength | Length of the string written to the buffer when [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) is returned.<br> When [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) is returned due to an input parameter error, **writeLength** is not assigned. If the error is due to a copy exception, **writeLength** indicates the minimum buffer size required to hold the target string.<br> When [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) is returned, it indicates the minimum buffer size required to hold the target string.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the provided buffer size is insufficient.|

### OH_ArkUI_MotionPathOptions_SetFrom()

``` c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetFrom(ArkUI_MotionPathOptions* options, const float from)
```

**Description**

Sets the start progress of the path animation. The progress refers to the ratio of the distance already moved along the path to the total path length.

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|
| const float from | Start progress of the path animation, ranging from 0.0 to 1.0. This value must be less than or equal to the end progress specified by **to**. Otherwise, the error [ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) will be returned.<br>For details about **to**, see [OH_ArkUI_MotionPathOptions_SetTo](#oh_arkui_motionpathoptions_setto).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>Returns [ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) if the value of **from** out of the range of [0.0, 1.0], or is greater than the value of **to**. |

### OH_ArkUI_MotionPathOptions_GetFrom()

``` c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetFrom(const ArkUI_MotionPathOptions* options, float* from)
```

**Description**

Obtains the start progress of the path animation.

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|
| float* from | Pointer to the start progress in [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t |  Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_MotionPathOptions_SetTo()

``` c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetTo(ArkUI_MotionPathOptions* options, const float to)
```

**Description**

Sets the end progress of the path animation. The progress refers to the ratio of the distance already moved along the path to the total path length.

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|
| const float to | End progress of the path animation, ranging from 0.0 to 1.0. This value must be greater than or equal to the start progress specified by **from**. Otherwise, the error [ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) will be returned.<br>For details about the meaning of **from**, see [OH_ArkUI_MotionPathOptions_SetFrom](#oh_arkui_motionpathoptions_setfrom).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t |  Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>Returns [ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](capi-native-type-h.md#arkui_errorcode) if the value of **to** out of the range of [0.0, 1.0], or is less than the value of **from**. |

### OH_ArkUI_MotionPathOptions_GetTo()

``` c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetTo(const ArkUI_MotionPathOptions* options, float* to)
```

**Description**

Obtains the end progress of the path animation.

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|
| float* to | Pointer to the end progress in [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_MotionPathOptions_SetRotatable()

``` c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetRotatable(ArkUI_MotionPathOptions* options, const bool rotatable)
```

**Description**

Sets whether a component rotates along the motion path.

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|
| const bool rotatable | Whether the component rotates along the path. **true**: The component rotates along the path. **false**: The component does not rotate along the path. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_MotionPathOptions_GetRotatable()

``` c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetRotatable(const ArkUI_MotionPathOptions* options, bool* rotatable)
```

**Description**

Obtains whether a component rotates along the motion path.

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).|
| bool* rotatable | Pointer to the **rotatable** parameter value in [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md), indicating whether the component rotates along the path.<br>**true**: The component rotates along the path. **false**: The component does not rotate along the path.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_PickerIndicatorStyle_Create()

``` c
ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)
```

**Description**

Creates a style instance of the selected item indicator.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_PickerIndicatorType](capi-native-type-h.md#arkui_pickerindicatortype) type | Type of the selected item indicator.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* | [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) instance. If a null pointer is returned, the creation fails. The possible cause is that the address space is full or the type is not supported.|

### OH_ArkUI_PickerIndicatorStyle_Dispose()

``` c
void OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)
```

**Description**

Disposes the style instance of the selected item indicator.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) instance to be disposed.|

### OH_ArkUI_PickerIndicatorStyle_ConfigureBackground()

``` c
ArkUI_ErrorCode OH_ArkUI_PickerIndicatorStyle_ConfigureBackground(ArkUI_PickerIndicatorStyle* style, ArkUI_PickerIndicatorBackground* background)
```

**Description**

Sets the background style parameters. This API takes effect only when the type of the selected item indicator is [ARKUI_PICKER_INDICATOR_BACKGROUND](capi-native-type-h.md#arkui_pickerindicatortype).

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) instance.|
| [ArkUI_PickerIndicatorBackground](capi-arkui-nativemodule-arkui-pickerindicatorbackground.md)* background | Background style.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_PickerIndicatorStyle_ConfigureDivider()

``` c
ArkUI_ErrorCode OH_ArkUI_PickerIndicatorStyle_ConfigureDivider(ArkUI_PickerIndicatorStyle* style, ArkUI_PickerIndicatorDivider* divider)
```

**Description**

Sets the divider style parameters. This API takes effect only when the type of the selected item indicator is [ARKUI_PICKER_INDICATOR_DIVIDER](capi-native-type-h.md#arkui_pickerindicatortype).

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) instance.|
| [ArkUI_PickerIndicatorDivider](capi-arkui-nativemodule-arkui-pickerindicatordivider.md)* divider | Divider style.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|
