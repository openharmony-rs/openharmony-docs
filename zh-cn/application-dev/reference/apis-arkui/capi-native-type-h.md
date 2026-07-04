# native_type.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

提供NativeModule公共的类型定义。

**引用文件：** <arkui/native_type.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_Node](capi-arkui-nativemodule-arkui-node-descriptor.md) | ArkUI_Node | 定义ArkUI native组件实例对象。 |
| [ArkUI_ContextCallback](capi-arkui-nativemodule-arkui-contextcallback.md) | ArkUI_ContextCallback | 事件回调类型。 |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) | ArkUI_NumberValue | ArkUI在Native侧的数字类型定义。 |
| [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md) | ArkUI_ColorStop | 定义渐变色结构。 |
| [ArkUI_Rect](capi-arkui-nativemodule-arkui-rect.md) | ArkUI_Rect | 定义遮罩屏蔽区域的范围结构体。 |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md) | ArkUI_IntSize | 尺寸类型，用于描述组件的宽高。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) | ArkUI_IntOffset | 偏移量，用于描述当前组件相对于父组件的偏移量。|
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) | ArkUI_Margin | 外边距属性，用于描述组件的外边距属性。 |
| [ArkUI_NativeDialog](capi-arkui-nativemodule-arkui-nativedialog.md) | ArkUI_NativeDialog | 提供ArkUI在Native侧的自定义弹窗控制器对象定义。 |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md) | ArkUI_LayoutConstraint | 布局约束，组件布局时，进行尺寸范围限制。 |
| [ArkUI_DrawContext](capi-arkui-nativemodule-arkui-drawcontext.md) | ArkUI_DrawContext | 定义组件绘制上下文类型结构。 |
| [ArkUI_Node*](capi-arkui-nativemodule-arkui-node8h.md) | ArkUI_NodeHandle | 定义ArkUI native组件实例对象指针定义。 |
| [ArkUI_NativeDialog*](capi-arkui-nativemodule-arkui-nativedialog8h.md) | ArkUI_NativeDialogHandle | 定义ArkUI在Native侧的自定义弹窗控制器对象指针。 |
| [ArkUI_GestureCollectInterceptInfo](capi-arkui-nativemodule-arkui-gesturecollectinterceptinfo.md) | ArkUI_GestureCollectInterceptInfo | 定义手势收集拦截信息。 |
| [ArkUI_GridItemSize](capi-arkui-nativemodule-arkui-griditemsize.md) | ArkUI_GridItemSize | 定义Grid布局选项onGetIrregularSizeByIndex回调返回值结构体。 |
| [ArkUI_GridItemRect](capi-arkui-nativemodule-arkui-griditemrect.md) | ArkUI_GridItemRect | 定义Grid布局选项onGetRectByIndex回调返回值结构体。 |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md) | ArkUI_GridLayoutOptions | 定义Grid布局选项。 |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) | ArkUI_WaterFlowSectionOption | 定义[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息。 |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md) | ArkUI_ListItemSwipeActionItem | 定义ListItemSwipeActionOption方法内Item的配置信息。 |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md) | ArkUI_ListItemSwipeActionOption | 定义ListItemSwipeActionOption方法的配置信息。 |
| [ArkUI_Context](capi-arkui-nativemodule-arkui-context.md) | ArkUI_Context | 定义ArkUI native UI的上下文实例对象。 |
| [ArkUI_Context*](capi-arkui-nativemodule-arkui-context8h.md) | ArkUI_ContextHandle | 定义ArkUI native UI的上下文实例对象指针定义。 |
| [ArkUI_NodeContent*](capi-arkui-nativemodule-arkui-nodecontent8h.md) | ArkUI_NodeContentHandle | 定义ArkUI NodeContent实例在Native侧的实例对象指针定义。 |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) | ArkUI_ListChildrenMainSize | 定义List的ChildrenMainSize类信息。 |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) | ArkUI_ProgressLinearStyleOption | 定义线性进度条样式。 |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md) | ArkUI_CustomProperty | 定义自定义属性的CustomProperty类信息。 |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md) | ArkUI_HostWindowInfo | 定义窗口属性的HostWindowInfo类信息。 |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md) | ArkUI_ActiveChildrenInfo | 定义ActiveChildrenInfo类信息。 |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md) | ArkUI_CrossLanguageOption | 定义跨语言配置项。 |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md) | ArkUI_AccessibilityState | 定义组件无障碍状态。 |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md) | ArkUI_AccessibilityValue | 定义组件无障碍信息值。 |
| [ArkUI_SystemFontStyleEvent](capi-arkui-nativemodule-arkui-systemfontstyleevent.md) | ArkUI_SystemFontStyleEvent | 系统字体变更事件定义。 |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md) | ArkUI_CustomSpanMeasureInfo | 自定义段落组件的测量信息。 |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md) | ArkUI_CustomSpanMetrics | 自定义段落组件的度量指标。 |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md) | ArkUI_CustomSpanDrawInfo | 自定义段落组件的绘制信息。 |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md) | ArkUI_StyledString_Descriptor | 定义文本组件支持的属性字符串的数据对象。 |
| [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md)| ArkUI_SelectionOptions | 定义选择操作的相关选项。|
|[ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md)|ArkUI_ContentTransitionEffect|内容过渡效果。|
|[ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)|ArkUI_ShowCounterConfig|定义文本输入框的计数器配置。|
|[ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)|ArkUI_TextContentBaseController|定义文本内容基础控制器。|
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md) | ArkUI_TextMenuItem | 定义文本菜单项结构体。 |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md) | ArkUI_TextMenuItemArray | 定义文本菜单项数组结构体。 |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md) | ArkUI_TextEditMenuOptions | 定义文本菜单扩展项结构体。 |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md) | ArkUI_TextSelectionMenuOptions | 定义自定义文本选择菜单结构体。 |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md) | ArkUI_SelectedDragPreviewStyle | 定义选中状态下文本拖拽预览样式。 |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md) | ArkUI_TextMarqueeOptions | 定义文本跑马灯模式配置项。 |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md) | OH_ArkUI_DecorationStyleOptions | 定义装饰线样式。 |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) | OH_ArkUI_TextDataDetectorConfig | 定义文本实体识别的配置。 |
| [OH_ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md) | OH_ArkUI_TextEditorSelectionMenuOptions | 定义文本编辑器的文本选择菜单选项。 |
| [OH_ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md) | OH_ArkUI_TextEditorPlaceholderOptions | 定义文本编辑器无输入时的提示文本选项。 |
| [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md) | OH_ArkUI_TextEditorStyledStringController | 定义文本编辑器的属性字符串控制器。 |
| [OH_ArkUI_TextEditorParagraphStyle](capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md) | OH_ArkUI_TextEditorParagraphStyle | 定义文本编辑器的段落样式。 |
| [OH_ArkUI_TextEditorTextStyle](capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md) | OH_ArkUI_TextEditorTextStyle | 定义文本编辑器的文本样式。 |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md) | OH_ArkUI_FontWeightConfigs | 定义文本的字体粗细配置。可以通过[OH_ArkUI_FontWeightConfigs_Create](#oh_arkui_fontweightconfigs_create) 接口创建对应的文本字体粗细配置对象。可以通过[OH_ArkUI_FontWeightConfigs_Destroy](#oh_arkui_fontweightconfigs_destroy) 接口销毁文本字体粗细配置对象。配置创建后通过[OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight](#oh_arkui_fontweightconfigs_setenablevariablefontweight) 接口设置是否启用可变字体粗细调节。配置创建后通过[OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight](#oh_arkui_fontweightconfigs_getenablevariablefontweight) 接口查看是否启用了可变字体粗细调节。配置创建后通过[OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory](#oh_arkui_fontweightconfigs_setenabledevicefontweightcategory) 接口设置文本字体粗细是否跟随设备的字体粗细级别更新。配置创建后通过[OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory](#oh_arkui_fontweightconfigs_getenabledevicefontweightcategory) 接口查看文本字体粗细是否跟随设备的字体粗细级别更新。 |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md) | OH_ArkUI_FontConfigs | 定义文本的字体配置。可以通过[OH_ArkUI_FontConfigs_Create](#oh_arkui_fontconfigs_create) 接口创建文本字体配置对象。可以通过[OH_ArkUI_FontConfigs_Destroy](#oh_arkui_fontconfigs_destroy) 接口销毁文本字体配置对象。配置创建后通过[OH_ArkUI_FontConfigs_SetFontWeightConfigs](#oh_arkui_fontconfigs_setfontweightconfigs) 接口设置文本的字体粗细配置。配置创建后通过[OH_ArkUI_FontConfigs_GetFontWeightConfigs](#oh_arkui_fontconfigs_getfontweightconfigs) 接口查看文本的字体粗细配置。 |
| [OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md) | OH_ArkUI_TextController | 定义文本组件的控制器。可以通过[OH_ArkUI_TextController_Create](#oh_arkui_textcontroller_create)创建文本组件控制器对象，通过[OH_ArkUI_TextController_Destroy](#oh_arkui_textcontroller_destroy)接口销毁文本组件控制器对象。控制器创建后通过[OH_ArkUI_TextController_SetStyledString](#oh_arkui_textcontroller_setstyledstring) 接口设置文本组件的属性字符串。 |
| [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md) | OH_ArkUI_LinearGradientOptions | 定义线性渐变效果选项。 |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md) | OH_ArkUI_RadialGradientOptions | 定义径向渐变效果选项。 |

### 枚举

| 名称                                                                  | typedef关键字                      | 描述                                |
|---------------------------------------------------------------------|---------------------------------|-----------------------------------|
| [ArkUI_FontStyle](#arkui_fontstyle)                                 | ArkUI_FontStyle                 | 定义字体样式枚举值。                        |
| [ArkUI_FontWeight](#arkui_fontweight)                               | ArkUI_FontWeight                | 定义字体粗细/字重枚举值。                     |
| [ArkUI_TextAlignment](#arkui_textalignment)                         | ArkUI_TextAlignment             | 定义字体水平对齐样式枚举值。                    |
| [ArkUI_TextVerticalAlignment](#arkui_textverticalalignment)         | ArkUI_TextVerticalAlignment     | 定义文本垂直对齐样式枚举值。                    |
| [ArkUI_EnterKeyType](#arkui_enterkeytype)                           | ArkUI_EnterKeyType              | 定义单行文本输入法回车键类型枚举值。                |
| [ArkUI_TextInputType](#arkui_textinputtype)                         | ArkUI_TextInputType             | 定义单行文本输入法类型枚举值。                   |
| [ArkUI_TextAreaType](#arkui_textareatype)                           | ArkUI_TextAreaType              | 定义多行文本输入法类型枚举值。                   |
| [ArkUI_CancelButtonStyle](#arkui_cancelbuttonstyle)                 | ArkUI_CancelButtonStyle         | 定义清除按钮样式枚举值。                      |
| [ArkUI_ProgressType](#arkui_progresstype)                           | ArkUI_ProgressType              | 定义进度条类型枚举值。                       |
| [ArkUI_TextDecorationType](#arkui_textdecorationtype)               | ArkUI_TextDecorationType        | 定义装饰线类型枚举值。                       |
| [ArkUI_TextDecorationStyle](#arkui_textdecorationstyle)             | ArkUI_TextDecorationStyle       | 定义装饰线样式枚举值。                       |
| [ArkUI_TextCase](#arkui_textcase)                                   | ArkUI_TextCase                  | 定义文本大小写枚举值。                       |
| [ArkUI_CopyOptions](#arkui_copyoptions)                             | ArkUI_CopyOptions               | 定义文本复制粘贴模式枚举值。                    |
| [ArkUI_AccessibilityCheckedState](#arkui_accessibilitycheckedstate) | ArkUI_AccessibilityCheckedState | 定义无障碍复选框状态类型枚举值。                  |
| [ArkUI_AccessibilityActionType](#arkui_accessibilityactiontype)     | ArkUI_AccessibilityActionType   | 定义无障碍操作类型。                        |
| [ArkUI_EdgeEffect](#arkui_edgeeffect)                               | ArkUI_EdgeEffect                | 定义边缘滑动效果枚举值。                      |
| [ArkUI_BarState](#arkui_barstate)                               | ArkUI_BarState                | 定义文本控制滚动条状态枚举值。                      |
| [ArkUI_EffectEdge](#arkui_effectedge)                               | ArkUI_EffectEdge                | 定义边缘效果生效边缘的方向枚举值。                 |
| [ArkUI_ScrollDirection](#arkui_scrolldirection)                     | ArkUI_ScrollDirection           | 定义[Scroll](../apis-arkui/arkui-ts/ts-container-scroll.md)组件排列方向枚举值。                |
| [ArkUI_ScrollSnapAlign](#arkui_scrollsnapalign)                     | ArkUI_ScrollSnapAlign           | 定义列表项滚动结束对齐效果枚举值。                 |
| [ArkUI_ScrollBarDisplayMode](#arkui_scrollbardisplaymode)           | ArkUI_ScrollBarDisplayMode      | 定义滚动条状态枚举值。                       |
| [ArkUI_StickyStyle](#arkui_stickystyle)                             | ArkUI_StickyStyle               | 定义列表是否吸顶和吸底枚举值。                   |
| [ArkUI_ContentClipMode](#arkui_contentclipmode)                     | ArkUI_ContentClipMode           | 定义滚动容器的内容层裁剪区域枚举值。                |
| [ArkUI_WaterFlowLayoutMode](#arkui_waterflowlayoutmode)             | ArkUI_WaterFlowLayoutMode       | 定义[WaterFlow](../apis-arkui/arkui-ts/ts-container-waterflow.md)组件布局模式枚举值。             |
| [ArkUI_BorderStyle](#arkui_borderstyle)                             | ArkUI_BorderStyle               | 边框线条样式枚举值。                        |
| [ArkUI_AccessibilityMode](#arkui_accessibilitymode)                 | ArkUI_AccessibilityMode         | 定义无障碍辅助服务模式。                      |
| [ArkUI_TextCopyOptions](#arkui_textcopyoptions)                     | ArkUI_TextCopyOptions           | 定义组件支持设置文本是否可复制粘贴。                |
| [ArkUI_TextHeightAdaptivePolicy](#arkui_textheightadaptivepolicy)   | ArkUI_TextHeightAdaptivePolicy  | 定义文本自适应高度的方式。                     |
| [ArkUI_ScrollNestedMode](#arkui_scrollnestedmode)                   | ArkUI_ScrollNestedMode          | 定义嵌套滚动选项。                         |
| [ArkUI_ScrollEdge](#arkui_scrolledge)                               | ArkUI_ScrollEdge                | 定义滚动到的边缘位置。                       |
| [ArkUI_ScrollAlignment](#arkui_scrollalignment)                     | ArkUI_ScrollAlignment           | 滚动到具体item时的对齐方式。                  |
| [ArkUI_ScrollState](#arkui_scrollstate)                             | ArkUI_ScrollState               | 定义当前滚动状态。                         |
| [ArkUI_SliderBlockStyle](#arkui_sliderblockstyle)                   | ArkUI_SliderBlockStyle          | 定义滑块形状。                           |
| [ArkUI_SliderDirection](#arkui_sliderdirection)                     | ArkUI_SliderDirection           | 定义滑动条滑动方向。                        |
| [ArkUI_SliderStyle](#arkui_sliderstyle)                             | ArkUI_SliderStyle               | 定义滑块与滑轨显示样式。                      |
| [ArkUI_CheckboxShape](#arkui_checkboxshape)                         | ArkUI_CheckboxShape             | 定义CheckBox组件形状。                   |
| [ArkUI_AdaptiveColor](#arkui_adaptivecolor)                         | ArkUI_AdaptiveColor             | 定义取色模式。                           |
| [ArkUI_ColorMode](#arkui_colormode)                                 | ArkUI_ColorMode                 | 定义深浅色模式。                          |
| [ArkUI_SystemColorMode](#arkui_systemcolormode)                     | ArkUI_SystemColorMode           | 定义系统深浅色模式。                        |
| [ArkUI_TextOverflow](#arkui_textoverflow)                           | ArkUI_TextOverflow              | 定义文本超长时的显示方式。                     |
| [ArkUI_ImageSpanAlignment](#arkui_imagespanalignment)               | ArkUI_ImageSpanAlignment        | 定义图片基于文本的对齐方式。                    |
| [ArkUI_WordBreak](#arkui_wordbreak)                                 | ArkUI_WordBreak                 | 定义文本断行规则。                         |
| [ArkUI_EllipsisMode](#arkui_ellipsismode)                           | ArkUI_EllipsisMode              | 定义文本省略位置。                         |
| [ArkUI_ListItemAlignment](#arkui_listitemalignment)                 | ArkUI_ListItemAlignment         | 交叉轴方向的布局方式。                       |
| [ArkUI_LengthMetricUnit](#arkui_lengthmetricunit)                   | ArkUI_LengthMetricUnit          | 定义组件的单位模式。                        |
| [ArkUI_TextInputContentType](#arkui_textinputcontenttype)           | ArkUI_TextInputContentType      | 定义自动填充类型。                         |
| [ArkUI_TextInputStyle](#arkui_textinputstyle)                       | ArkUI_TextInputStyle            | 定义输入框风格。                          |
| [ArkUI_KeyboardAppearance](#arkui_keyboardappearance)               | ArkUI_KeyboardAppearance        | 定义输入框拉起的键盘样式。                     |
| [ArkUI_TextDataDetectorType](#arkui_textdatadetectortype)           | ArkUI_TextDataDetectorType      | 定义文本识别的实体类型。                      |
| [ArkUI_ButtonType](#arkui_buttontype)                               | ArkUI_ButtonType                | 定义按钮样式枚举值。                        |
| [ArkUI_ListItemSwipeActionState](#arkui_listitemswipeactionstate)   | ArkUI_ListItemSwipeActionState  | 定义[Listitem](./arkui-ts/ts-container-listitem.md#listitem10)组件[swipeAction](./arkui-ts/ts-container-listitem.md#swipeaction9)方法的显隐模式。 |
| [ArkUI_ListItemSwipeEdgeEffect](#arkui_listitemswipeedgeeffect)     | ArkUI_ListItemSwipeEdgeEffect   | 定义[Listitem](./arkui-ts/ts-container-listitem.md#listitem10)组件[swipeAction](./arkui-ts/ts-container-listitem.md#swipeaction9)方法的滚动模式。 |
| [ArkUI_ListItemSwipeActionDirection](#arkui_listitemswipeactiondirection) | ArkUI_ListItemSwipeActionDirection | ListItem划出菜单的展开方向。 |
| [ArkUI_ErrorCode](#arkui_errorcode)                                 | ArkUI_ErrorCode                 | 定义错误码枚举值。                         |
| [ArkUI_ScrollSource](#arkui_scrollsource)                           | ArkUI_ScrollSource              | 定义滚动来源枚举值。                        |
| [ArkUI_SafeAreaType](#arkui_safeareatype)                           | ArkUI_SafeAreaType              | 定义扩展安全区域的枚举值。                     |
| [ArkUI_ListItemGroupArea](#arkui_listitemgrouparea)                 | ArkUI_ListItemGroupArea         | 定义ListItemGroup组件区域。            |
| [ArkUI_KeyboardAvoidMode](#arkui_keyboardavoidmode)                 | ArkUI_KeyboardAvoidMode         | 键盘避让模式。                           |
| [ArkUI_HoverModeAreaType](#arkui_hovermodeareatype)                 | ArkUI_HoverModeAreaType         | 悬停态显示区域。                          |
| [ArkUI_ExpandMode](#arkui_expandmode)                               | ArkUI_ExpandMode                | 定义子节点展开模式枚举值。                     |
| [ArkUI_FocusWrapMode](#arkui_focuswrapmode)                         | ArkUI_FocusWrapMode             | 组件走焦换行规则。                         |
| [ArkUI_ItemFillPolicy](#arkui_itemfillpolicy)                         | ArkUI_ItemFillPolicy             | 为不同响应式断点规格指定列数。                         |
| [ArkUI_EdgeDirection](#arkui_edgedirection)                         | ArkUI_EdgeDirection             | 定义矩形边方向。                         |
| [ArkUI_CornerDirection](#arkui_cornerdirection)                     | ArkUI_CornerDirection           | 定义角度方向。                         |
| [ArkUI_GridItemStyle](#arkui_griditemstyle)                         | ArkUI_GridItemStyle             | GridItem样式枚举。                         |
| [ArkUI_MenuPolicy](#arkui_menupolicy)                               | ArkUI_MenuPolicy                | 菜单弹出策略。                             |
| [ArkUI_TextMenuItemId](#arkui_textmenuitemid) | ArkUI_TextMenuItemId | 文本菜单项id枚举。 |
| [ArkUI_TextSpanType](#arkui_textspantype) | ArkUI_TextSpanType | 自定义文本选择菜单的文本识别类型枚举。 |
| [ArkUI_TextResponseType](#arkui_textresponsetype) | ArkUI_TextResponseType | 自定义文本选择菜单的响应类型枚举。 |
| [ArkUI_RenderStrategy](#arkui_renderstrategy)                       | ArkUI_RenderStrategy             | 定义组件绘制圆角的模式。                |
| [ArkUI_MarqueeStartPolicy](#arkui_marqueestartpolicy)| ArkUI_MarqueeStartPolicy| 定义跑马灯启动策略枚举。 |
| [ArkUI_MarqueeUpdatePolicy](#arkui_marqueeupdatepolicy)| ArkUI_MarqueeUpdatePolicy| 定义跑马灯更新策略枚举。 |
| [OH_ArkUI_HapticFeedbackMode](#oh_arkui_hapticfeedbackmode) | OH_ArkUI_HapticFeedbackMode | 震动效果类型枚举。 |
| [OH_ArkUI_TextEditorSpanType](#oh_arkui_texteditorspantype) | OH_ArkUI_TextEditorSpanType | 自定义文本选择菜单span类型枚举。 |
| [OH_ArkUI_TextEditorResponseType](#oh_arkui_texteditorresponsetype) | OH_ArkUI_TextEditorResponseType | 自定义文本选择菜单响应类型枚举。 |
| [OH_ArkUI_TextMenuType](#oh_arkui_textmenutype) | OH_ArkUI_TextMenuType | 文本菜单类型枚举。 |
| [OH_ArkUI_LineBreakStrategy](#oh_arkui_linebreakstrategy) | OH_ArkUI_LineBreakStrategy | 换行策略类型枚举。 |
| [ArkUI_RawInputEventType](#arkui_rawinputeventtype) | ArkUI_RawInputEventType | 原始输入事件类型枚举。 |
| [OH_ArkUI_CrossLanguageOperatingStatus](#oh_arkui_crosslanguageoperatingstatus) | OH_ArkUI_CrossLanguageOperatingStatus | 跨语言配置项的节点树操作状态。 |
| [OH_ArkUI_NodeMountPolicy](#oh_arkui_nodemountpolicy) | OH_ArkUI_NodeMountPolicy | 子节点挂载策略类型枚举。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Create()](#oh_arkui_layoutconstraint_create) | - | 创建布局约束。 |
| [ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Copy(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_copy) | - | 布局约束深拷贝。 |
| [void* OH_ArkUI_LayoutConstraint_Dispose(ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_dispose) | - | 销毁布局约束指针。 |
| [int32_t OH_ArkUI_LayoutConstraint_GetMaxWidth(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getmaxwidth) | - | 通过布局约束获取最大宽度，单位为px。 |
| [int32_t OH_ArkUI_LayoutConstraint_GetMinWidth(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getminwidth) | - | 通过布局约束获取最小宽度，单位为px。 |
| [int32_t OH_ArkUI_LayoutConstraint_GetMaxHeight(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getmaxheight) | - | 通过布局约束获取最大高度，单位为px。 |
| [int32_t OH_ArkUI_LayoutConstraint_GetMinHeight(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getminheight) | - | 通过布局约束获取最小高度，单位为px。 |
| [int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceWidth(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getpercentreferencewidth) | - | 通过布局约束获取宽度百分比基准。 |
| [int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceHeight(const ArkUI_LayoutConstraint* Constraint)](#oh_arkui_layoutconstraint_getpercentreferenceheight) | - | 通过布局约束获取高度百分比基准。 |
| [void OH_ArkUI_LayoutConstraint_SetMaxWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setmaxwidth) | - | 设置最大宽度。 |
| [void OH_ArkUI_LayoutConstraint_SetMinWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setminwidth) | - | 设置最小宽度。 |
| [void OH_ArkUI_LayoutConstraint_SetMaxHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setmaxheight) | - | 设置最大高度。 |
| [void OH_ArkUI_LayoutConstraint_SetMinHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setminheight) | - | 设置最小高度。 |
| [void OH_ArkUI_LayoutConstraint_SetPercentReferenceWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setpercentreferencewidth) | - | 设置宽度百分比基准。 |
| [void OH_ArkUI_LayoutConstraint_SetPercentReferenceHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)](#oh_arkui_layoutconstraint_setpercentreferenceheight) | - | 设置高度百分比基准。 |
| [void* OH_ArkUI_DrawContext_GetCanvas(ArkUI_DrawContext* context)](#oh_arkui_drawcontext_getcanvas) | - | 获取绘制canvas指针，可以转换为图形库的OH_Drawing_Canvas指针进行绘制。 |
| [ArkUI_IntSize OH_ArkUI_DrawContext_GetSize(ArkUI_DrawContext* context)](#oh_arkui_drawcontext_getsize) | - | 获取可绘制区域大小。 |
| [ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create()](#oh_arkui_waterflowsectionoption_create) | - | 创建FlowItem分组配置信息。 |
| [void OH_ArkUI_WaterFlowSectionOption_Dispose(ArkUI_WaterFlowSectionOption* option)](#oh_arkui_waterflowsectionoption_dispose) | - | 销毁FlowItem分组配置信息指针。 |
| [void OH_ArkUI_WaterFlowSectionOption_SetSize(ArkUI_WaterFlowSectionOption* option, int32_t size)](#oh_arkui_waterflowsectionoption_setsize) | - | 设置FlowItem分组配置信息数组长度。 |
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetSize(ArkUI_WaterFlowSectionOption* option)](#oh_arkui_waterflowsectionoption_getsize) | - | 获取FlowItem分组配置信息数组长度。 |
| [void OH_ArkUI_WaterFlowSectionOption_SetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t itemCount)](#oh_arkui_waterflowsectionoption_setitemcount) | - | 设置分组中FlowItem数量。 |
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getitemcount) | - | 通过FlowItem分组配置信息获取对应索引下的FlowItem数量。 |
| [void OH_ArkUI_WaterFlowSectionOption_SetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t crossCount)](#oh_arkui_waterflowsectionoption_setcrosscount) | - | 设置布局栅格，纵向布局时为列数，横向布局时为行数。 |
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getcrosscount) | - | 通过FlowItem分组配置信息获取对应索引下的布局栅格数。 |
| [void OH_ArkUI_WaterFlowSectionOption_SetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float columnGap)](#oh_arkui_waterflowsectionoption_setcolumngap) | - | 设置分组的列间距。 |
| [float OH_ArkUI_WaterFlowSectionOption_GetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getcolumngap) | - | 通过FlowItem分组配置信息获取对应索引下的分组的列间距。 |
| [void OH_ArkUI_WaterFlowSectionOption_SetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float rowGap)](#oh_arkui_waterflowsectionoption_setrowgap) | - | 设置分组的行间距。 |
| [float OH_ArkUI_WaterFlowSectionOption_GetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getrowgap) | - | 通过FlowItem分组配置信息获取对应索引下的分组的行间距。 |
| [void OH_ArkUI_WaterFlowSectionOption_SetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index,float marginTop, float marginRight, float marginBottom, float marginLeft)](#oh_arkui_waterflowsectionoption_setmargin) | - | 设置分组的外边距。 |
| [ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getmargin) | - | 通过FlowItem分组配置信息获取对应索引下的分组的外边距。 |
| [void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex (ArkUI_WaterFlowSectionOption* option, int32_t index, float(\*callback)(int32_t itemIndex))](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex) | - | 通过FlowItem分组配置信息根据itemIndex获取指定FlowItem的主轴大小。如需在回调中使用自定义数据，可使用[OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata)。 |
| [void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData (ArkUI_WaterFlowSectionOption* option, int32_t index, void* userData, float (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata) | - | 通过FlowItem分组配置信息根据itemIndex获取指定Item的主轴大小。与[OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex)的区别在于，该接口支持传入自定义数据userData，并在回调函数中接收该数据。 |
| [void OH_ArkUI_SwiperDigitIndicator_SetFontWeight(ArkUI_SwiperDigitIndicator *indicator, ArkUI_FontWeight fontWeight)](#oh_arkui_swiperdigitindicator_setfontweight) | - | 设置Swiper组件数字导航指示器字体粗细属性。 |
| [ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetFontWeight(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontweight) | - | 获取Swiper组件数字导航指示器字体粗细属性。 |
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontWeight(ArkUI_SwiperDigitIndicator *indicator, ArkUI_FontWeight selectedFontWeight)](#oh_arkui_swiperdigitindicator_setselectedfontweight) | - | 设置被选中Swiper组件数字导航指示器字体粗细属性。 |
| [ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetSelectedFontWeight(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontweight) | - | 获取被选中Swiper组件数字导航指示器字体粗细属性。 |
| [ArkUI_ListItemSwipeActionItem* OH_ArkUI_ListItemSwipeActionItem_Create()](#oh_arkui_listitemswipeactionitem_create) | - | 创建ListItemSwipeActionItem接口设置的配置项。 |
| [void OH_ArkUI_ListItemSwipeActionItem_Dispose(ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionitem_dispose) | - | 销毁ListItemSwipeActionItem实例。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetContent(ArkUI_ListItemSwipeActionItem* item, ArkUI_NodeHandle node)](#oh_arkui_listitemswipeactionitem_setcontent) | - | 设置ListItemSwipeActionItem的布局内容。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item, float distance)](#oh_arkui_listitemswipeactionitem_setactionareadistance) | - | 设置组件长距离滑动删除距离阈值。 |
| [float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionitem_getactionareadistance) | - | 获取组件长距离滑动删除距离阈值。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonenteractionarea) | - | 设置滑动条目进入删除区域时调用的事件。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData (ArkUI_ListItemSwipeActionItem* item,void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonenteractionareawithuserdata) | - | 设置滑动条目进入删除区域时调用的事件，回调事件会传入用户自定义数据。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnAction(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonaction) | - | 设置组件进入长距删除区后删除ListItem时调用的事件。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData(ArkUI_ListItemSwipeActionItem* item,void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonactionwithuserdata) | - | 设置组件进入长距删除区后删除ListItem时调用的事件，回调事件会传入用户自定义数据。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonexitactionarea) | - | 设置滑动条目退出删除区域时调用的事件。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData (ArkUI_ListItemSwipeActionItem* item,void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonexitactionareawithuserdata) | - | 设置滑动条目退出删除区域时调用的事件，回调事件会传入用户自定义数据。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange (ArkUI_ListItemSwipeActionItem* item,void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState))](#oh_arkui_listitemswipeactionitem_setonstatechange) | - | 设置列表项滑动状态变化时候触发的事件。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData (ArkUI_ListItemSwipeActionItem* item,void* userData, void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void* userData))](#oh_arkui_listitemswipeactionitem_setonstatechangewithuserdata) | - | 设置列表项滑动状态变化时候触发的事件，回调事件会传入用户自定义数据。 |
| [ArkUI_ListItemSwipeActionOption* OH_ArkUI_ListItemSwipeActionOption_Create()](#oh_arkui_listitemswipeactionoption_create) | - | 创建ListItemSwipeActionOption接口设置的配置项。 |
| [void OH_ArkUI_ListItemSwipeActionOption_Dispose(ArkUI_ListItemSwipeActionOption* option)](#oh_arkui_listitemswipeactionoption_dispose) | - | 销毁ListItemSwipeActionOption实例。 |
| [void OH_ArkUI_ListItemSwipeActionOption_SetStart(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionoption_setstart) | - | 设置ListItemSwipeActionItem的左侧（垂直布局）或上方（横向布局）布局内容。 |
| [void OH_ArkUI_ListItemSwipeActionOption_SetEnd(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionoption_setend) | - | 设置ListItemSwipeActionItem的右侧（垂直布局）或下方（横向布局）布局内容。 |
| [void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeEdgeEffect edgeEffect)](#oh_arkui_listitemswipeactionoption_setedgeeffect) | - | 设置边缘滑动效果。 |
| [int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect(ArkUI_ListItemSwipeActionOption* option)](#oh_arkui_listitemswipeactionoption_getedgeeffect) | - | 获取边缘滑动效果。 |
| [void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange(ArkUI_ListItemSwipeActionOption* option, void (\*callback)(float offset))](#oh_arkui_listitemswipeactionoption_setonoffsetchange) | - | 滑动操作偏移量更改时调用的事件。 |
| [void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData (ArkUI_ListItemSwipeActionOption* option, void* userData, void (\*callback)(float offset, void* userData))](#oh_arkui_listitemswipeactionoption_setonoffsetchangewithuserdata) | - | 滑动操作偏移量更改时调用的事件，回调事件会传入用户自定义数据。 |
| [int32_t OH_ArkUI_ListItemSwipeAction_Expand(ArkUI_NodeHandle node, ArkUI_ListItemSwipeActionDirection direction)](#oh_arkui_listitemswipeaction_expand) | - |  展开指定ListItem的划出菜单。 |
| [int32_t OH_ArkUI_ListItemSwipeAction_Collapse(ArkUI_NodeHandle node)](#oh_arkui_listitemswipeaction_collapse) | - |  收起指定ListItem的划出菜单。 |
| [ArkUI_AccessibilityState* OH_ArkUI_AccessibilityState_Create(void)](#oh_arkui_accessibilitystate_create) | - | 创建无障碍状态。 |
| [void OH_ArkUI_AccessibilityState_Dispose(ArkUI_AccessibilityState* state)](#oh_arkui_accessibilitystate_dispose) | - | 销毁无障碍状态指针。 |
| [void OH_ArkUI_AccessibilityState_SetDisabled(ArkUI_AccessibilityState* state, int32_t isDisabled)](#oh_arkui_accessibilitystate_setdisabled) | - | 设置无障碍状态是否禁用。 |
| [int32_t OH_ArkUI_AccessibilityState_IsDisabled(ArkUI_AccessibilityState* state)](#oh_arkui_accessibilitystate_isdisabled) | - | 获取无障碍状态是否禁用。 |
| [void OH_ArkUI_AccessibilityState_SetSelected(ArkUI_AccessibilityState* state, int32_t isSelected)](#oh_arkui_accessibilitystate_setselected) | - | 设置无障碍状态是否选中。 |
| [int32_t OH_ArkUI_AccessibilityState_IsSelected(ArkUI_AccessibilityState* state)](#oh_arkui_accessibilitystate_isselected) | - | 获取无障碍状态是否选中。 |
| [void OH_ArkUI_AccessibilityState_SetCheckedState(ArkUI_AccessibilityState* state, int32_t checkedState)](#oh_arkui_accessibilitystate_setcheckedstate) | - | 设置无障碍状态复选框状态。 |
| [int32_t OH_ArkUI_AccessibilityState_GetCheckedState(ArkUI_AccessibilityState* state)](#oh_arkui_accessibilitystate_getcheckedstate) | - | 获取无障碍状态复选框状态。 |
| [ArkUI_AccessibilityValue* OH_ArkUI_AccessibilityValue_Create(void)](#oh_arkui_accessibilityvalue_create) | - | 创建无障碍信息。 |
| [void OH_ArkUI_AccessibilityValue_Dispose(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_dispose) | - | 销毁无障碍信息指针。 |
| [void OH_ArkUI_AccessibilityValue_SetMin(ArkUI_AccessibilityValue* value, int32_t min)](#oh_arkui_accessibilityvalue_setmin) | - | 设置无障碍最小值信息。 |
| [int32_t OH_ArkUI_AccessibilityValue_GetMin(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getmin) | - | 获取无障碍最小值信息。 |
| [void OH_ArkUI_AccessibilityValue_SetMax(ArkUI_AccessibilityValue* value, int32_t max)](#oh_arkui_accessibilityvalue_setmax) | - | 设置无障碍最大值信息。 |
| [int32_t OH_ArkUI_AccessibilityValue_GetMax(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getmax) | - | 获取无障碍最大值信息。 |
| [void OH_ArkUI_AccessibilityValue_SetCurrent(ArkUI_AccessibilityValue* value, int32_t current)](#oh_arkui_accessibilityvalue_setcurrent) | - | 设置无障碍当前值信息。 |
| [int32_t OH_ArkUI_AccessibilityValue_GetCurrent(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getcurrent) | - | 获取无障碍当前值信息。 |
| [void OH_ArkUI_AccessibilityValue_SetRangeMin(ArkUI_AccessibilityValue* value, int32_t rangeMin)](#oh_arkui_accessibilityvalue_setrangemin) | - | 设置范围组件的无障碍最小值信息。 |
| [int32_t OH_ArkUI_AccessibilityValue_GetRangeMin(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getrangemin) | - | 获取范围组件的无障碍最小值信息。 |
| [void OH_ArkUI_AccessibilityValue_SetRangeMax(ArkUI_AccessibilityValue* value, int32_t rangeMax)](#oh_arkui_accessibilityvalue_setrangemax) | - | 设置范围组件的无障碍最大值信息。 |
| [int32_t OH_ArkUI_AccessibilityValue_GetRangeMax(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getrangemax) | - | 获取范围组件的无障碍最大值信息。 |
| [void OH_ArkUI_AccessibilityValue_SetRangeCurrent(ArkUI_AccessibilityValue* value, int32_t rangeCurrent)](#oh_arkui_accessibilityvalue_setrangecurrent) | - | 用于设置范围组件的无障碍当前值信息。 |
| [int32_t OH_ArkUI_AccessibilityValue_GetRangeCurrent(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_getrangecurrent) | - | 用于获取范围组件的无障碍当前值信息。 |
| [void OH_ArkUI_AccessibilityValue_SetText(ArkUI_AccessibilityValue* value, const char* text)](#oh_arkui_accessibilityvalue_settext) | - | 设置无障碍文本描述信息。 |
| [const char* OH_ArkUI_AccessibilityValue_GetText(ArkUI_AccessibilityValue* value)](#oh_arkui_accessibilityvalue_gettext) | - | 获取无障碍文本描述信息。 |
| [ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()](#oh_arkui_listchildrenmainsizeoption_create) | - | 创建ListChildrenMainSize接口设置的配置项。 |
| [void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_dispose) | - | 销毁ListChildrenMainSize实例。 |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)](#oh_arkui_listchildrenmainsizeoption_setdefaultmainsize) | - | 设置List组件列表项在主轴方向的默认尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。 |
| [float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_getdefaultmainsize) | - | 获取List组件的列表项在主轴方向的默认尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。 |
| [void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)](#oh_arkui_listchildrenmainsizeoption_resize) | - | 调整List组件子项主轴尺寸数组的容量大小。 |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)](#oh_arkui_listchildrenmainsizeoption_splice) | - | 对List组件子项主轴尺寸数组进行大小调整。 |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)](#oh_arkui_listchildrenmainsizeoption_updatesize) | - | 更新List组件子项主轴尺寸数组中指定索引位置的尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。 |
| [float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)](#oh_arkui_listchildrenmainsizeoption_getmainsize) | - | 获取List组件子项主轴尺寸数组中指定索引位置的尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。 |
| [ArkUI_CustomSpanMeasureInfo* OH_ArkUI_CustomSpanMeasureInfo_Create(void)](#oh_arkui_customspanmeasureinfo_create) | - | 创建自定义段落组件测量信息。 |
| [void OH_ArkUI_CustomSpanMeasureInfo_Dispose(ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_customspanmeasureinfo_dispose) | - | 销毁自定义段落组件测量信息。 |
| [float OH_ArkUI_CustomSpanMeasureInfo_GetFontSize(ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_customspanmeasureinfo_getfontsize) | - | 获取自定义段落组件的父节点Text的字体大小。 |
| [ArkUI_CustomSpanMetrics* OH_ArkUI_CustomSpanMetrics_Create(void)](#oh_arkui_customspanmetrics_create) | - | 创建自定义段落组件度量信息。 |
| [void OH_ArkUI_CustomSpanMetrics_Dispose(ArkUI_CustomSpanMetrics* metrics)](#oh_arkui_customspanmetrics_dispose) | - | 销毁自定义段落组件度量信息。 |
| [int32_t OH_ArkUI_CustomSpanMetrics_SetWidth(ArkUI_CustomSpanMetrics* metrics, float width)](#oh_arkui_customspanmetrics_setwidth) | - | 设置自定义段落组件的宽度。 |
| [int32_t OH_ArkUI_CustomSpanMetrics_SetHeight(ArkUI_CustomSpanMetrics* metrics, float height)](#oh_arkui_customspanmetrics_setheight) | - | 设置自定义段落组件的高度。 |
| [ArkUI_CustomSpanDrawInfo* OH_ArkUI_CustomSpanDrawInfo_Create(void)](#oh_arkui_customspandrawinfo_create) | - | 创建自定义段落组件绘制信息。 |
| [void OH_ArkUI_CustomSpanDrawInfo_Dispose(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_dispose) | - | 销毁自定义段落组件绘制信息。 |
| [float OH_ArkUI_CustomSpanDrawInfo_GetXOffset(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getxoffset) | - | 获取自定义段落组件相对于挂载组件的x轴偏移值。 |
| [float OH_ArkUI_CustomSpanDrawInfo_GetLineTop(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getlinetop) | - | 获取自定义段落组件相对于挂载组件的上边距。 |
| [float OH_ArkUI_CustomSpanDrawInfo_GetLineBottom(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getlinebottom) | - | 获取自定义段落组件相对于挂载组件的下边距。 |
| [float OH_ArkUI_CustomSpanDrawInfo_GetBaseline(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getbaseline) | - | 获取自定义段落组件相对于挂载组件的基线偏移量。 |
| [void OH_ArkUI_CustomProperty_Destroy(ArkUI_CustomProperty* handle)](#oh_arkui_customproperty_destroy) | - | 销毁CustomProperty实例。 |
| [const char* OH_ArkUI_CustomProperty_GetStringValue(ArkUI_CustomProperty* handle)](#oh_arkui_customproperty_getstringvalue) | - | 获取自定义属性value信息。 |
| [const char* OH_ArkUI_HostWindowInfo_GetName(ArkUI_HostWindowInfo* info)](#oh_arkui_hostwindowinfo_getname) | - | 获取HostWindowInfo对象中的窗口名称。 |
| [void OH_ArkUI_HostWindowInfo_Destroy(ArkUI_HostWindowInfo* info)](#oh_arkui_hostwindowinfo_destroy) | - | 销毁HostWindowInfo对象。 |
| [void OH_ArkUI_ActiveChildrenInfo_Destroy(ArkUI_ActiveChildrenInfo* handle)](#oh_arkui_activechildreninfo_destroy) | - | 销毁ActiveChildrenInfo实例。 |
| [ArkUI_NodeHandle OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex(ArkUI_ActiveChildrenInfo* handle, int32_t index)](#oh_arkui_activechildreninfo_getnodebyindex) | - | 获取ActiveChildrenInfo结构体的下标为index的子节点。 |
| [int32_t OH_ArkUI_ActiveChildrenInfo_GetCount(ArkUI_ActiveChildrenInfo* handle)](#oh_arkui_activechildreninfo_getcount) | - | 获取ActiveChildrenInfo结构体内的节点数量。 |
| [ArkUI_ProgressLinearStyleOption* OH_ArkUI_ProgressLinearStyleOption_Create(void)](#oh_arkui_progresslinearstyleoption_create) | - | 创建线性进度条样式信息。 |
| [void OH_ArkUI_ProgressLinearStyleOption_Destroy(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_destroy) | - | 销毁线性进度条样式信息。 |
| [void OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)](#oh_arkui_progresslinearstyleoption_setsmootheffectenabled) | - | 设置进度平滑动效的开关。 |
| [void OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)](#oh_arkui_progresslinearstyleoption_setscaneffectenabled) | - | 设置扫光效果的开关。 |
| [void OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth(ArkUI_ProgressLinearStyleOption* option, float strokeWidth)](#oh_arkui_progresslinearstyleoption_setstrokewidth) | - | 设置进度条宽度。 |
| [void OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius(ArkUI_ProgressLinearStyleOption* option, float strokeRadius)](#oh_arkui_progresslinearstyleoption_setstrokeradius) | - | 设置进度条圆角半径。 |
| [bool OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getsmootheffectenabled) | - | 获取进度平滑动效的开关信息。 |
| [bool OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getscaneffectenabled) | - | 获取扫光效果的开关信息。 |
| [float OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getstrokewidth) | - | 获取进度条宽度。 |
| [float OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getstrokeradius) | - | 获取进度条圆角半径值。 |
| [ArkUI_CrossLanguageOption* OH_ArkUI_CrossLanguageOption_Create(void)](#oh_arkui_crosslanguageoption_create) | - | 创建跨语言配置项实例。 |
| [void OH_ArkUI_CrossLanguageOption_Destroy(ArkUI_CrossLanguageOption* option)](#oh_arkui_crosslanguageoption_destroy) | - | 销毁跨语言配置项实例。 |
| [void OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus(ArkUI_CrossLanguageOption* option, bool enabled)](#oh_arkui_crosslanguageoption_setattributesettingstatus) | - | 设置配置项中是否允许跨语言修改属性。 |
| [bool OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus(ArkUI_CrossLanguageOption* option)](#oh_arkui_crosslanguageoption_getattributesettingstatus) | - | 获取配置项中是否允许跨语言修改属性。 |
| [void OH_ArkUI_CrossLanguageOption_SetTreeOperatingStatus(ArkUI_CrossLanguageOption* option, OH_ArkUI_CrossLanguageOperatingStatus status)](#oh_arkui_crosslanguageoption_settreeoperatingstatus) | - | 设置跨语言配置项的节点树操作状态。 |
| [OH_ArkUI_CrossLanguageOperatingStatus OH_ArkUI_CrossLanguageOption_GetTreeOperatingStatus(ArkUI_CrossLanguageOption* option)](#oh_arkui_crosslanguageoption_gettreeoperatingstatus) | - | 获取跨语言配置项的节点树操作状态。 |
| [ArkUI_ContentTransitionEffect* OH_ArkUI_ContentTransitionEffect_Create(int32_t type)](#oh_arkui_contenttransitioneffect_create) | - | 创建ContentTransitionEffect属性对象。|
| [ArkUI_GridLayoutOptions* OH_ArkUI_GridLayoutOptions_Create()](#oh_arkui_gridlayoutoptions_create) | - | 创建Grid布局选项。 |
| [void OH_ArkUI_GridLayoutOptions_Dispose(ArkUI_GridLayoutOptions* option)](#oh_arkui_gridlayoutoptions_dispose) | - | 销毁Grid布局选项。 |
| [int32_t OH_ArkUI_GridLayoutOptions_SetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t size)](#oh_arkui_gridlayoutoptions_setirregularindexes) | - | 设置Grid中不规则GridItem的索引数组。 |
| [int32_t OH_ArkUI_GridLayoutOptions_GetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t* size)](#oh_arkui_gridlayoutoptions_getirregularindexes) | - | 获取Grid中不规则GridItem的索引数组。当不设置OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback时，irregularIndexes中GridItem的默认大小为垂直滚动Grid的一整行或水平滚动Grid的一整列。 |
| [void OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemSize(\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_gridlayoutoptions_registergetirregularsizebyindexcallback) | - | Grid布局选项通过GridItem索引获取指定Item占用的行列数。 |
| [void OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemRect (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_gridlayoutoptions_registergetrectbyindexcallback) | - | Grid布局选项通过GridItem索引获取指定Item的起始行列和占用的行列数。 |
| [ArkUI_SelectionOptions OH_ArkUI_SelectionOptions_Create()](#oh_arkui_selectionoptions_create) | - | 创建选择选项。 |
| [void OH_ArkUI_SelectionOptions_Dispose(ArkUI_SelectionOptions* options)](#oh_arkui_selectionoptions_dispose) | - | 释放选择选项对象。 |
| [void OH_ArkUI_SelectionOptions_SetMenuPolicy(ArkUI_SelectionOptions* options, ArkUI_MenuPolicy menuPolicy)](#oh_arkui_selectionoptions_setmenupolicy) | - | 设置选择选项的菜单弹出策略。 |
| [ArkUI_MenuPolicy OH_ArkUI_SelectionOptions_GetMenuPolicy(ArkUI_SelectionOptions* options)](#oh_arkui_selectionoptions_getmenupolicy) | - | 获取选择选项的菜单弹出策略。 |
| [ArkUI_TextContentBaseController* OH_ArkUI_TextContentBaseController_Create()](#oh_arkui_textcontentbasecontroller_create) | - | 创建文本内容基础控制器对象。 |
| [void OH_ArkUI_TextContentBaseController_Dispose(ArkUI_TextContentBaseController* controller)](#oh_arkui_textcontentbasecontroller_dispose) | - | 销毁文本内容基础控制器对象。 |
| [void OH_ArkUI_TextContentBaseController_DeleteBackward(ArkUI_TextContentBaseController* controller)](#oh_arkui_textcontentbasecontroller_deletebackward) | - | 在编辑态时删除光标前字符。其他状态删除输入框组件的最后一个字符。 |
| [void OH_ArkUI_TextContentBaseController_ScrollToVisible(ArkUI_TextContentBaseController* controller, int32_t start, int32_t end)](#oh_arkui_textcontentbasecontroller_scrolltovisible) | - | 将起始索引与结束索引传递给与其绑定的输入框组件，并将此范围内的文字滚动到可视区域。 |
| [ArkUI_TextMenuItem* OH_ArkUI_TextMenuItem_Create()](#oh_arkui_textmenuitem_create) | - | 创建文本菜单项对象。 |
| [void OH_ArkUI_TextMenuItem_Dispose(ArkUI_TextMenuItem* textMenuItem)](#oh_arkui_textmenuitem_dispose) | - | 释放文本菜单项对象。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetContent(ArkUI_TextMenuItem* item, const char* content)](#oh_arkui_textmenuitem_setcontent) | - | 设置文本菜单项标题。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetContent(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textmenuitem_getcontent) | - | 获取文本菜单项标题。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetIcon(ArkUI_TextMenuItem* item, const char* icon)](#oh_arkui_textmenuitem_seticon) | - | 设置文本菜单项图标路径。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetIcon(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textmenuitem_geticon) | - | 获取文本菜单项图标路径。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetLabelInfo(ArkUI_TextMenuItem* item, const char* labelInfo)](#oh_arkui_textmenuitem_setlabelinfo) | - | 设置文本菜单项快捷键提示，例如“复制”菜单项的快捷键提示可以设置为“Ctrl+C”。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetLabelInfo(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textmenuitem_getlabelinfo) | - | 获取文本菜单项快捷键提示，例如“复制”菜单项的快捷键提示一般为“Ctrl+C”。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetId(ArkUI_TextMenuItem* item, int32_t id)](#oh_arkui_textmenuitem_setid) | - | 设置文本菜单项id。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetId(const ArkUI_TextMenuItem* item, int32_t* id)](#oh_arkui_textmenuitem_getid) | - | 获取文本菜单项id。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_GetSize(ArkUI_TextMenuItemArray* items, int32_t* size)](#oh_arkui_textmenuitemarray_getsize) | - | 获取文本菜单项数组大小。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_GetItem(ArkUI_TextMenuItemArray* items, int32_t index, ArkUI_TextMenuItem** item)](#oh_arkui_textmenuitemarray_getitem) | - | 获取文本菜单项数组中指定索引位置的文本菜单项。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Insert(ArkUI_TextMenuItemArray* items, ArkUI_TextMenuItem* item, int32_t index)](#oh_arkui_textmenuitemarray_insert) | - | 在文本菜单项数组中指定索引位置插入一个文本菜单项。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Erase(ArkUI_TextMenuItemArray* items, int32_t index)](#oh_arkui_textmenuitemarray_erase) | - | 删除文本菜单项数组中指定索引位置的文本菜单项。 |
| [ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Clear(ArkUI_TextMenuItemArray* items)](#oh_arkui_textmenuitemarray_clear) | - | 清除文本菜单项数组中所有的文本菜单项。 |
| [ArkUI_TextEditMenuOptions* OH_ArkUI_TextEditMenuOptions_Create()](#oh_arkui_texteditmenuoptions_create) | - | 创建文本菜单扩展项对象。 |
| [void OH_ArkUI_TextEditMenuOptions_Dispose(ArkUI_TextEditMenuOptions* editMenuOptions)](#oh_arkui_texteditmenuoptions_dispose) | - | 释放文本菜单扩展项对象。 |
| [typedef void (\*ArkUI_TextCreateMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)](#arkui_textcreatemenucallback) | ArkUI_TextCreateMenuCallback | 文本菜单创建事件回调函数，在文本菜单创建时会触发此回调函数，开发者可在此函数中设置菜单数据。 |
| [typedef void (\*ArkUI_TextPrepareMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)](#arkui_textpreparemenucallback) | ArkUI_TextPrepareMenuCallback | 文本菜单准备事件回调函数，当文本选择区域变化后显示菜单之前会触发此回调函数，开发者可在此函数中配置菜单数据。 |
| [typedef bool (\*ArkUI_TextMenuItemClickCallback)(const ArkUI_TextMenuItem* item,int32_t start, int32_t end, void* userData)](#arkui_textmenuitemclickcallback) | ArkUI_TextMenuItemClickCallback | 文本菜单项点击事件回调函数，在菜单项被点击时触发此回调函数，开发者可在此函数中对系统默认处理行为进行拦截。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnCreateMenuCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextCreateMenuCallback cb)](#oh_arkui_texteditmenuoptions_registeroncreatemenucallback) | - | 注册文本菜单创建事件回调函数。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnPrepareMenuCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextPrepareMenuCallback cb)](#oh_arkui_texteditmenuoptions_registeronpreparemenucallback) | - | 注册文本菜单准备事件回调函数。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnMenuItemClickCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextMenuItemClickCallback cb)](#oh_arkui_texteditmenuoptions_registeronmenuitemclickcallback) | - | 注册文本菜单项点击事件回调函数。 |
| [ArkUI_TextSelectionMenuOptions* OH_ArkUI_TextSelectionMenuOptions_Create()](#oh_arkui_textselectionmenuoptions_create) | - | 创建自定义文本选择菜单对象。 |
| [void OH_ArkUI_TextSelectionMenuOptions_Dispose(ArkUI_TextSelectionMenuOptions* selectionMenuOptions)](#oh_arkui_textselectionmenuoptions_dispose) | - | 释放自定义文本选择菜单对象。 |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetSpanType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextSpanType textSpanType)](#oh_arkui_textselectionmenuoptions_setspantype) | - | 设置自定义文本选择菜单的文本识别类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetSpanType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextSpanType* spanType)](#oh_arkui_textselectionmenuoptions_getspantype) | - | 获取自定义文本选择菜单的文本识别类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetContentNode(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_NodeHandle node)](#oh_arkui_textselectionmenuoptions_setcontentnode) | - | 设置自定义文本选择菜单的内容节点。 |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetContentNode(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_NodeHandle* node)](#oh_arkui_textselectionmenuoptions_getcontentnode) | - | 获取自定义文本选择菜单的内容节点。 |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetResponseType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextResponseType responseType)](#oh_arkui_textselectionmenuoptions_setresponsetype) | - | 设置自定义文本选择菜单的响应类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetResponseType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextResponseType* responseType)](#oh_arkui_textselectionmenuoptions_getresponsetype) | - | 获取自定义文本选择菜单的响应类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuShowCallback(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, void* userData, void (\*callback)(int32_t start, int32_t end, void* userData))](#oh_arkui_textselectionmenuoptions_registeronmenushowcallback) | - | 注册自定义文本选择菜单显示事件回调。 |
| [ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuHideCallback(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, void* userData, void (\*callback)(int32_t start, int32_t end, void* userData))](#oh_arkui_textselectionmenuoptions_registeronmenuhidecallback) | - | 注册自定义文本选择菜单隐藏事件回调。 |
| [ArkUI_TextMarqueeOptions* OH_ArkUI_TextMarqueeOptions_Create()](#oh_arkui_textmarqueeoptions_create) | - | 创建文本跑马灯模式配置项。 |
| [void OH_ArkUI_TextMarqueeOptions_Dispose(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_dispose) | - | 销毁文本跑马灯模式配置项指针。 |
| [void OH_ArkUI_TextMarqueeOptions_SetStart(ArkUI_TextMarqueeOptions* option, bool start)](#oh_arkui_textmarqueeoptions_setstart) | - | 设置文本跑马灯模式配置项是否播放。|
| [bool OH_ArkUI_TextMarqueeOptions_GetStart(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstart) | - | 获取文本跑马灯模式配置项是否播放。|
| [void OH_ArkUI_TextMarqueeOptions_SetStep(ArkUI_TextMarqueeOptions* option, float step)](#oh_arkui_textmarqueeoptions_setstep) | - | 设置文本跑马灯模式配置项的步长。 |
| [float OH_ArkUI_TextMarqueeOptions_GetStep(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstep) | - | 获取文本跑马灯模式配置项的步长。|
| [void OH_ArkUI_TextMarqueeOptions_SetSpacing(ArkUI_TextMarqueeOptions* option, float spacing)](#oh_arkui_textmarqueeoptions_setspacing) | - | 设置文本跑马灯模式配置项的首尾间距。 |
| [float OH_ArkUI_TextMarqueeOptions_GetSpacing(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getspacing) | - | 获取文本跑马灯模式配置项的首尾间距。 |
| [void OH_ArkUI_TextMarqueeOptions_SetLoop(ArkUI_TextMarqueeOptions* option, int32_t loop)](#oh_arkui_textmarqueeoptions_setloop) | - | 设置文本跑马灯模式配置项的重复滚动的次数，小于等于零时无限循环。 |
| [int32_t OH_ArkUI_TextMarqueeOptions_GetLoop(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getloop) | - | 获取文本跑马灯模式配置项的重复滚动的次数。 |
| [void OH_ArkUI_TextMarqueeOptions_SetFromStart(ArkUI_TextMarqueeOptions* option, bool fromStart)](#oh_arkui_textmarqueeoptions_setfromstart) | - | 设置文本跑马灯模式配置项的运行方向。 |
| [bool OH_ArkUI_TextMarqueeOptions_GetFromStart(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getfromstart) | - | 获取文本跑马灯模式配置项的运行方向。 |
| [void OH_ArkUI_TextMarqueeOptions_SetDelay(ArkUI_TextMarqueeOptions* option, int32_t delay)](#oh_arkui_textmarqueeoptions_setdelay) | - | 设置文本跑马灯模式配置项的每轮滚动延迟时间。|
| [int32_t OH_ArkUI_TextMarqueeOptions_GetDelay(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getdelay) | - | 获取文本跑马灯模式配置项的每轮滚动延迟时间。 |
| [void OH_ArkUI_TextMarqueeOptions_SetFadeout(ArkUI_TextMarqueeOptions* option, bool fadeout)](#oh_arkui_textmarqueeoptions_setfadeout) | - | 设置文本跑马灯模式配置项是否支持文字超长时的渐隐效果。当Text内容超出显示范围时，未完全展现的文字边缘将应用渐隐效果。若两端均有文字未完全显示，则两端同时应用渐隐效果。在渐隐效果开启状态下，[ArkUI_NodeAttributeType](./capi-native-node-h.md#arkui_nodeattributetype)中的NODE_CLIP属性将自动锁定为true，不允许设置为false。 |
| [bool OH_ArkUI_TextMarqueeOptions_GetFadeout(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getfadeout) | - | 获取文本跑马灯模式配置项是否支持文字超长时的渐隐效果。 |
| [void OH_ArkUI_TextMarqueeOptions_SetStartPolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeStartPolicy startPolicy)](#oh_arkui_textmarqueeoptions_setstartpolicy) | - | 设置文本跑马灯模式配置项的启动策略。 |
| [ArkUI_MarqueeStartPolicy OH_ArkUI_TextMarqueeOptions_GetStartPolicy(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstartpolicy) | - | 获取文本跑马灯模式配置项的启动策略。 |
| [void OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeUpdatePolicy updatePolicy)](#oh_arkui_textmarqueeoptions_setupdatepolicy) | - | 设置文本跑马灯模式配置项的更新策略。 |
| [ArkUI_MarqueeUpdatePolicy OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getupdatepolicy) | - | 获取文本跑马灯模式配置项的更新策略。|
| [ArkUI_ErrorCode OH_ArkUI_PickerIndicatorStyle_ConfigureBackground(ArkUI_PickerIndicatorStyle* style, ArkUI_PickerIndicatorBackground* background)](#oh_arkui_pickerindicatorstyle_configurebackground) | - | 设置背景样式参数，此接口仅当选择器选中项样式枚举类型为[ARKUI_PICKER_INDICATOR_BACKGROUND](capi-picker-h.md#arkui_pickerindicatortype)时生效。 |
| [ArkUI_ErrorCode OH_ArkUI_PickerIndicatorStyle_ConfigureDivider(ArkUI_PickerIndicatorStyle* style, ArkUI_PickerIndicatorDivider* divider)](#oh_arkui_pickerindicatorstyle_configuredivider) | - | 设置分割线样式参数，此接口仅当选择器选中项样式枚举类型为[ARKUI_PICKER_INDICATOR_DIVIDER](capi-picker-h.md#arkui_pickerindicatortype)时生效。 |
| [OH_ArkUI_DecorationStyleOptions* OH_ArkUI_DecorationStyleOptions_Create()](#oh_arkui_decorationstyleoptions_create) | - | 创建一个装饰线样式对象。当该对象不再使用时，请调用[OH_ArkUI_DecorationStyleOptions_Destroy](capi-native-type-h.md#oh_arkui_decorationstyleoptions_destroy)销毁。 |
| [void OH_ArkUI_DecorationStyleOptions_Destroy(OH_ArkUI_DecorationStyleOptions* options)](#oh_arkui_decorationstyleoptions_destroy) | - | 销毁装饰线样式对象。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_SetTextDecorationType(OH_ArkUI_DecorationStyleOptions* options, ArkUI_TextDecorationType type)](#oh_arkui_decorationstyleoptions_settextdecorationtype) | - | 设置装饰线样式的装饰类型。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_GetTextDecorationType(OH_ArkUI_DecorationStyleOptions* options, ArkUI_TextDecorationType* type)](#oh_arkui_decorationstyleoptions_gettextdecorationtype) | - | 获取装饰线样式的装饰类型。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_SetColor(OH_ArkUI_DecorationStyleOptions* options, uint32_t color)](#oh_arkui_decorationstyleoptions_setcolor) | - | 设置装饰线的颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_GetColor(OH_ArkUI_DecorationStyleOptions* options, uint32_t* color)](#oh_arkui_decorationstyleoptions_getcolor) | - | 获取装饰线的颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_SetTextDecorationStyle(OH_ArkUI_DecorationStyleOptions* options, ArkUI_TextDecorationStyle style)](#oh_arkui_decorationstyleoptions_settextdecorationstyle) | - | 设置装饰线的样式。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_GetTextDecorationStyle(OH_ArkUI_DecorationStyleOptions* options, ArkUI_TextDecorationStyle* style)](#oh_arkui_decorationstyleoptions_gettextdecorationstyle) | - | 获取装饰线的样式。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_SetThicknessScale(OH_ArkUI_DecorationStyleOptions* options, float thicknessScale)](#oh_arkui_decorationstyleoptions_setthicknessscale) | - | 设置装饰线的粗细缩放比例。 |
| [ArkUI_ErrorCode OH_ArkUI_DecorationStyleOptions_GetThicknessScale(OH_ArkUI_DecorationStyleOptions* options, float* thicknessScale)](#oh_arkui_decorationstyleoptions_getthicknessscale) | - | 获取装饰线的粗细缩放比例。 |
| [OH_ArkUI_TextDataDetectorConfig* OH_ArkUI_TextDataDetectorConfig_Create()](#oh_arkui_textdatadetectorconfig_create) | - | 创建一个文本实体识别配置对象。当该对象不再使用时，请调用[OH_ArkUI_TextDataDetectorConfig_Destroy](capi-native-type-h.md#oh_arkui_textdatadetectorconfig_destroy)销毁。 |
| [void OH_ArkUI_TextDataDetectorConfig_Destroy(OH_ArkUI_TextDataDetectorConfig* config)](#oh_arkui_textdatadetectorconfig_destroy) | - | 销毁文本实体识别配置对象。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_SetTypes(OH_ArkUI_TextDataDetectorConfig* config, const ArkUI_TextDataDetectorType* types, int32_t length)](#oh_arkui_textdatadetectorconfig_settypes) | - | 设置文本实体识别配置的类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_GetTypes(OH_ArkUI_TextDataDetectorConfig* config, ArkUI_TextDataDetectorType* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_textdatadetectorconfig_gettypes) | - | 获取文本实体识别配置的类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_RegisterOnDetectResultUpdateCallback(OH_ArkUI_TextDataDetectorConfig* config, void* userData, void (\*callback)(const char* result, int32_t length, void* userData))](#oh_arkui_textdatadetectorconfig_registerondetectresultupdatecallback) | - | 设置文本实体识别结果更新回调。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_SetColor(OH_ArkUI_TextDataDetectorConfig* config, uint32_t color)](#oh_arkui_textdatadetectorconfig_setcolor) | - | 设置识别内容的颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_GetColor(OH_ArkUI_TextDataDetectorConfig* config, uint32_t* color)](#oh_arkui_textdatadetectorconfig_getcolor) | - | 获取识别内容的颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_SetDecorationStyleOptions(OH_ArkUI_TextDataDetectorConfig* config, OH_ArkUI_DecorationStyleOptions* decoration)](#oh_arkui_textdatadetectorconfig_setdecorationstyleoptions) | - | 设置识别内容的装饰样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_GetDecorationStyleOptions(OH_ArkUI_TextDataDetectorConfig* config, OH_ArkUI_DecorationStyleOptions* decoration)](#oh_arkui_textdatadetectorconfig_getdecorationstyleoptions) | - | 获取识别内容的装饰样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_SetEnablePreviewMenu(OH_ArkUI_TextDataDetectorConfig* config, bool enablePreviewMenu)](#oh_arkui_textdatadetectorconfig_setenablepreviewmenu) | - | 设置长按识别内容时是否显示预览菜单。 |
| [ArkUI_ErrorCode OH_ArkUI_TextDataDetectorConfig_GetEnablePreviewMenu(OH_ArkUI_TextDataDetectorConfig* config, bool* enablePreviewMenu)](#oh_arkui_textdatadetectorconfig_getenablepreviewmenu) | - | 获取长按识别内容时是否显示预览菜单。 |
| [OH_ArkUI_TextEditorPlaceholderOptions* OH_ArkUI_TextEditorPlaceholderOptions_Create()](#oh_arkui_texteditorplaceholderoptions_create) | - | 创建一个无输入时的提示文本的选项对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorPlaceholderOptions_Destroy](capi-native-type-h.md#oh_arkui_texteditorplaceholderoptions_destroy)销毁。 |
| [void OH_ArkUI_TextEditorPlaceholderOptions_Destroy(OH_ArkUI_TextEditorPlaceholderOptions* options)](#oh_arkui_texteditorplaceholderoptions_destroy) | - | 销毁无输入时的提示文本的选项对象。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetValue(OH_ArkUI_TextEditorPlaceholderOptions* options, const char* value)](#oh_arkui_texteditorplaceholderoptions_setvalue) | - | 设置无输入时的提示文本选项的提示文字。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetValue(OH_ArkUI_TextEditorPlaceholderOptions* options, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_texteditorplaceholderoptions_getvalue) | - | 获取无输入时的提示文本选项的提示文字。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontSize(OH_ArkUI_TextEditorPlaceholderOptions* options, float fontSize)](#oh_arkui_texteditorplaceholderoptions_setfontsize) | - | 设置无输入时的提示文本选项的字体大小。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontSize(OH_ArkUI_TextEditorPlaceholderOptions* options, float* fontSize)](#oh_arkui_texteditorplaceholderoptions_getfontsize) | - | 获取无输入时的提示文本选项的字体大小。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontWeight(OH_ArkUI_TextEditorPlaceholderOptions* options, uint32_t fontWeight)](#oh_arkui_texteditorplaceholderoptions_setfontweight) | - | 设置无输入时的提示文本选项的字体粗细。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontWeight(OH_ArkUI_TextEditorPlaceholderOptions* options, uint32_t* fontWeight)](#oh_arkui_texteditorplaceholderoptions_getfontweight) | - | 获取无输入时的提示文本选项的字体粗细。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontFamily(OH_ArkUI_TextEditorPlaceholderOptions* options, const char* fontFamily)](#oh_arkui_texteditorplaceholderoptions_setfontfamily) | - | 设置无输入时的提示文本选项的字体家族。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontFamily(OH_ArkUI_TextEditorPlaceholderOptions* options, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_texteditorplaceholderoptions_getfontfamily) | - | 获取无输入时的提示文本选项的字体家族。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontStyle(OH_ArkUI_TextEditorPlaceholderOptions* options, ArkUI_FontStyle fontStyle)](#oh_arkui_texteditorplaceholderoptions_setfontstyle) | - | 设置无输入时的提示文本选项的字体样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontStyle(OH_ArkUI_TextEditorPlaceholderOptions* options, ArkUI_FontStyle* fontStyle)](#oh_arkui_texteditorplaceholderoptions_getfontstyle) | - | 获取无输入时的提示文本选项的字体样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_SetFontColor(OH_ArkUI_TextEditorPlaceholderOptions* options, uint32_t fontColor)](#oh_arkui_texteditorplaceholderoptions_setfontcolor) | - | 设置无输入时的提示文本选项的字体颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorPlaceholderOptions_GetFontColor(OH_ArkUI_TextEditorPlaceholderOptions* options, uint32_t* fontColor)](#oh_arkui_texteditorplaceholderoptions_getfontcolor) | - | 获取无输入时的提示文本选项的字体颜色。 |
| [OH_ArkUI_TextEditorStyledStringController* OH_ArkUI_TextEditorStyledStringController_Create()](#oh_arkui_texteditorstyledstringcontroller_create) | - | 为文本编辑器创建一个属性字符串控制器对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorStyledStringController_Destroy](capi-native-type-h.md#oh_arkui_texteditorstyledstringcontroller_destroy)销毁。 |
| [void OH_ArkUI_TextEditorStyledStringController_Destroy(OH_ArkUI_TextEditorStyledStringController* controller)](#oh_arkui_texteditorstyledstringcontroller_destroy) | - | 销毁属性字符串控制器。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetCaretOffset(OH_ArkUI_TextEditorStyledStringController* controller, int32_t caretOffset)](#oh_arkui_texteditorstyledstringcontroller_setcaretoffset) | - | 通过属性字符串控制器设置光标偏移量。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetCaretOffset(OH_ArkUI_TextEditorStyledStringController* controller, int32_t* caretOffset)](#oh_arkui_texteditorstyledstringcontroller_getcaretoffset) | - | 通过属性字符串控制器获取光标索引位置。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetSelection(OH_ArkUI_TextEditorStyledStringController* controller, uint32_t start, uint32_t end, ArkUI_MenuPolicy menuPolicy)](#oh_arkui_texteditorstyledstringcontroller_setselection) | - | 通过属性字符串控制器设置选中区域。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_IsEditing(OH_ArkUI_TextEditorStyledStringController* controller, bool* isEditing)](#oh_arkui_texteditorstyledstringcontroller_isediting) | - | 通过属性字符串控制器获取文本编辑器的编辑状态。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_StopEditing(OH_ArkUI_TextEditorStyledStringController* controller)](#oh_arkui_texteditorstyledstringcontroller_stopediting) | - | 通过属性字符串控制器退出文本编辑器的编辑状态。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetPreviewText(OH_ArkUI_TextEditorStyledStringController* controller, uint32_t* offset, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_texteditorstyledstringcontroller_getpreviewtext) | - | 通过属性字符串控制器获取预上屏文本内容。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetCaretRect(OH_ArkUI_TextEditorStyledStringController* controller, ArkUI_Rect* rect)](#oh_arkui_texteditorstyledstringcontroller_getcaretrect) | - | 通过属性字符串控制器获取光标矩形区域。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_DeleteBackward(OH_ArkUI_TextEditorStyledStringController* controller)](#oh_arkui_texteditorstyledstringcontroller_deletebackward) | - | 通过属性字符串控制器删除字符。没有内容被选中时，删除当前光标位置前的1个字符。有内容被选中时，删除选中内容。 |
| [OH_ArkUI_TextEditorParagraphStyle* OH_ArkUI_TextEditorParagraphStyle_Create()](#oh_arkui_texteditorparagraphstyle_create) | - | 为文本编辑器创建一个段落样式对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorParagraphStyle_Destroy](capi-native-type-h.md#oh_arkui_texteditorparagraphstyle_destroy)销毁。 |
| [void OH_ArkUI_TextEditorParagraphStyle_Destroy(OH_ArkUI_TextEditorParagraphStyle* style)](#oh_arkui_texteditorparagraphstyle_destroy) | - | 销毁段落样式对象。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetTextAlign(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextAlignment align)](#oh_arkui_texteditorparagraphstyle_settextalign) | - | 设置段落样式中的文本对齐方式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetTextAlign(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextAlignment* align)](#oh_arkui_texteditorparagraphstyle_gettextalign) | - | 获取段落样式中的文本对齐方式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetLeadingMarginPixelMap(OH_ArkUI_TextEditorParagraphStyle* style, struct OH_PixelmapNative* pixelmap)](#oh_arkui_texteditorparagraphstyle_setleadingmarginpixelmap) | - | 设置段落样式中段落缩进的像素图。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetLeadingMarginPixelMap(OH_ArkUI_TextEditorParagraphStyle* style, struct OH_PixelmapNative** pixelmap)](#oh_arkui_texteditorparagraphstyle_getleadingmarginpixelmap) | - | 获取段落样式中段落缩进的像素图。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetLeadingMarginWidth(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t width)](#oh_arkui_texteditorparagraphstyle_setleadingmarginwidth) | - | 设置段落样式中段落缩进的宽度。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetLeadingMarginWidth(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t* width)](#oh_arkui_texteditorparagraphstyle_getleadingmarginwidth) | - | 获取段落样式中段落缩进的宽度。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetLeadingMarginHeight(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t height)](#oh_arkui_texteditorparagraphstyle_setleadingmarginheight) | - | 设置段落样式中段落缩进的高度。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetLeadingMarginHeight(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t* height)](#oh_arkui_texteditorparagraphstyle_getleadingmarginheight) | - | 获取段落样式中段落缩进的高度。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetWordBreak(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_WordBreak wordBreak)](#oh_arkui_texteditorparagraphstyle_setwordbreak) | - | 设置段落样式的断字方式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetWordBreak(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_WordBreak* wordBreak)](#oh_arkui_texteditorparagraphstyle_getwordbreak) | - | 获取段落样式的断字方式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetLineBreakStrategy(OH_ArkUI_TextEditorParagraphStyle* style, OH_ArkUI_LineBreakStrategy lineBreakStrategy)](#oh_arkui_texteditorparagraphstyle_setlinebreakstrategy) | - | 设置段落样式的换行策略。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetLineBreakStrategy(OH_ArkUI_TextEditorParagraphStyle* style, OH_ArkUI_LineBreakStrategy* lineBreakStrategy)](#oh_arkui_texteditorparagraphstyle_getlinebreakstrategy) | - | 获取段落样式的换行策略。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetParagraphSpacing(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t paragraphSpacing)](#oh_arkui_texteditorparagraphstyle_setparagraphspacing) | - | 设置段落样式的段落间距。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetParagraphSpacing(OH_ArkUI_TextEditorParagraphStyle* style, uint32_t* paragraphSpacing)](#oh_arkui_texteditorparagraphstyle_getparagraphspacing) | - | 获取段落样式的段落间距。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetTextVerticalAlign(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextVerticalAlignment verticalAlignment)](#oh_arkui_texteditorparagraphstyle_settextverticalalign) | - | 设置段落样式的文本垂直对齐方式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetTextVerticalAlign(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextVerticalAlignment* verticalAlignment)](#oh_arkui_texteditorparagraphstyle_gettextverticalalign) | - | 获取段落样式的文本垂直对齐方式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_SetTextDirection(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextDirection textDirection)](#oh_arkui_texteditorparagraphstyle_settextdirection) | - | 设置段落样式的文本方向。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorParagraphStyle_GetTextDirection(OH_ArkUI_TextEditorParagraphStyle* style, ArkUI_TextDirection* textDirection)](#oh_arkui_texteditorparagraphstyle_gettextdirection) | - | 获取段落样式的文本方向。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetTypingParagraphStyle(OH_ArkUI_TextEditorStyledStringController* controller, OH_ArkUI_TextEditorParagraphStyle* style)](#oh_arkui_texteditorstyledstringcontroller_settypingparagraphstyle) | - | 通过属性字符串控制器设置预设段落样式。 |
| [OH_ArkUI_TextEditorTextStyle* OH_ArkUI_TextEditorTextStyle_Create()](#oh_arkui_texteditortextstyle_create) | - | 创建一个文本样式对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorTextStyle_Destroy](capi-native-type-h.md#oh_arkui_texteditortextstyle_destroy)销毁。 |
| [void OH_ArkUI_TextEditorTextStyle_Destroy(OH_ArkUI_TextEditorTextStyle* style)](#oh_arkui_texteditortextstyle_destroy) | - | 销毁文本样式对象。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontColor(OH_ArkUI_TextEditorTextStyle* style, uint32_t color)](#oh_arkui_texteditortextstyle_setfontcolor) | - | 设置文本样式的字体颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontColor(OH_ArkUI_TextEditorTextStyle* style, uint32_t* color)](#oh_arkui_texteditortextstyle_getfontcolor) | - | 获取文本样式的字体颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontSize(OH_ArkUI_TextEditorTextStyle* style, float size)](#oh_arkui_texteditortextstyle_setfontsize) | - | 设置文本样式的字体大小。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontSize(OH_ArkUI_TextEditorTextStyle* style, float* size)](#oh_arkui_texteditortextstyle_getfontsize) | - | 获取文本样式的字体大小。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontStyle(OH_ArkUI_TextEditorTextStyle* style, ArkUI_FontStyle fontStyle)](#oh_arkui_texteditortextstyle_setfontstyle) | - | 设置文本样式的字体样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontStyle(OH_ArkUI_TextEditorTextStyle* style, ArkUI_FontStyle* fontStyle)](#oh_arkui_texteditortextstyle_getfontstyle) | - | 获取文本样式的字体样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontWeight(OH_ArkUI_TextEditorTextStyle* style, uint32_t fontWeight)](#oh_arkui_texteditortextstyle_setfontweight) | - | 设置文本样式的字体粗细。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontWeight(OH_ArkUI_TextEditorTextStyle* style, uint32_t* fontWeight)](#oh_arkui_texteditortextstyle_getfontweight) | - | 获取文本样式的字体粗细。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontFamily(OH_ArkUI_TextEditorTextStyle* style, const char* fontFamily)](#oh_arkui_texteditortextstyle_setfontfamily) | - | 设置文本样式的字体家族。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontFamily(OH_ArkUI_TextEditorTextStyle* style, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_texteditortextstyle_getfontfamily) | - | 获取文本样式的字体家族。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetDecoration(OH_ArkUI_TextEditorTextStyle* style, OH_ArkUI_DecorationStyleOptions* options)](#oh_arkui_texteditortextstyle_setdecoration) | - | 设置文本样式的文本装饰选项。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetDecoration(OH_ArkUI_TextEditorTextStyle* style, OH_ArkUI_DecorationStyleOptions* options)](#oh_arkui_texteditortextstyle_getdecoration) | - | 获取文本样式的文本装饰选项。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetTextShadows(OH_ArkUI_TextEditorTextStyle* style, const OH_ArkUI_ShadowOptions** options, int32_t length)](#oh_arkui_texteditortextstyle_settextshadows) | - | 设置文本样式的文本阴影选项。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetTextShadows(OH_ArkUI_TextEditorTextStyle* style, OH_ArkUI_ShadowOptions** shadowOptions, uint32_t shadowOptionsSize, uint32_t* writeLength)](#oh_arkui_texteditortextstyle_gettextshadows) | - | 获取文本样式的文本阴影选项。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetLineHeight(OH_ArkUI_TextEditorTextStyle* style, int32_t lineHeight)](#oh_arkui_texteditortextstyle_setlineheight) | - | 设置文本样式的文本行高。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetLineHeight(OH_ArkUI_TextEditorTextStyle* style, int32_t* lineHeight)](#oh_arkui_texteditortextstyle_getlineheight) | - | 获取文本样式的文本行高。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetLetterSpacing(OH_ArkUI_TextEditorTextStyle* style, int32_t letterSpacing)](#oh_arkui_texteditortextstyle_setletterspacing) | - | 设置文本样式的字符间距。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetLetterSpacing(OH_ArkUI_TextEditorTextStyle* style, int32_t* letterSpacing)](#oh_arkui_texteditortextstyle_getletterspacing) | - | 获取文本样式的字符间距。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetFontFeature(OH_ArkUI_TextEditorTextStyle* style, const char* fontFeature)](#oh_arkui_texteditortextstyle_setfontfeature) | - | 设置文本样式的文字特性效果，比如数字等宽的特性。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetFontFeature(OH_ArkUI_TextEditorTextStyle* style, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_arkui_texteditortextstyle_getfontfeature) | - | 获取文本样式的文字特性效果，比如数字等宽的特性。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetHalfLeading(OH_ArkUI_TextEditorTextStyle* style, bool halfLeading)](#oh_arkui_texteditortextstyle_sethalfleading) | - | 设置文本样式中文本是否将行间距平分至行的顶部与底部。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetHalfLeading(OH_ArkUI_TextEditorTextStyle* style, bool* halfLeading)](#oh_arkui_texteditortextstyle_gethalfleading) | - | 获取文本样式中文本是否将行间距平分至行的顶部与底部。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetTextBackgroundColor(OH_ArkUI_TextEditorTextStyle* style, uint32_t color)](#oh_arkui_texteditortextstyle_settextbackgroundcolor) | - | 设置文本样式中的文本背景颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetTextBackgroundColor(OH_ArkUI_TextEditorTextStyle* style, uint32_t* color)](#oh_arkui_texteditortextstyle_gettextbackgroundcolor) | - | 获取文本样式中的文本背景颜色。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_SetTextBackgroundRadius(OH_ArkUI_TextEditorTextStyle* style, float topLeft, float topRight, float bottomLeft, float bottomRight)](#oh_arkui_texteditortextstyle_settextbackgroundradius) | - | 设置文本样式中文本背景的圆角半径。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorTextStyle_GetTextBackgroundRadius(OH_ArkUI_TextEditorTextStyle* style, float* topLeft, float* topRight, float* bottomLeft, float* bottomRight)](#oh_arkui_texteditortextstyle_gettextbackgroundradius) | - | 获取文本样式中文本背景的圆角半径。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetTypingStyle(OH_ArkUI_TextEditorStyledStringController* controller, OH_ArkUI_TextEditorTextStyle* style)](#oh_arkui_texteditorstyledstringcontroller_settypingstyle) | - | 通过属性字符串控制器设置预设输入样式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetTypingStyle(OH_ArkUI_TextEditorStyledStringController* controller, OH_ArkUI_TextEditorTextStyle* style)](#oh_arkui_texteditorstyledstringcontroller_gettypingstyle) | - | 通过属性字符串控制器获取预设输入样式。 |
| [OH_ArkUI_TextEditorSelectionMenuOptions* OH_ArkUI_TextEditorSelectionMenuOptions_Create()](#oh_arkui_texteditorselectionmenuoptions_create) | - | 创建一个文本编辑器文本选择菜单选项对象。当该对象不再使用时，请调用[OH_ArkUI_TextEditorSelectionMenuOptions_Destroy](capi-native-type-h.md#oh_arkui_texteditorselectionmenuoptions_destroy)销毁。 |
| [void OH_ArkUI_TextEditorSelectionMenuOptions_Destroy(OH_ArkUI_TextEditorSelectionMenuOptions* options)](#oh_arkui_texteditorselectionmenuoptions_destroy) | - | 销毁文本编辑器文本选择菜单选项对象。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetSpanType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextEditorSpanType textEditorSpanType)](#oh_arkui_texteditorselectionmenuoptions_setspantype) | - | 设置文本编辑器中文本选择菜单的span的类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetSpanType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextEditorSpanType* textEditorSpanType)](#oh_arkui_texteditorselectionmenuoptions_getspantype) | - | 获取文本编辑器中文本选择菜单的span的类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetContentNode(OH_ArkUI_TextEditorSelectionMenuOptions* options, ArkUI_NodeHandle node)](#oh_arkui_texteditorselectionmenuoptions_setcontentnode) | - | 设置文本编辑器中文本选择菜单的内容节点。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetContentNode(OH_ArkUI_TextEditorSelectionMenuOptions* options, ArkUI_NodeHandle* node)](#oh_arkui_texteditorselectionmenuoptions_getcontentnode) | - | 获取文本编辑器中文本选择菜单的内容节点。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetResponseType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextEditorResponseType responseType)](#oh_arkui_texteditorselectionmenuoptions_setresponsetype) | - | 设置文本编辑器中文本选择菜单的响应类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetResponseType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextEditorResponseType* responseType)](#oh_arkui_texteditorselectionmenuoptions_getresponsetype) | - | 获取文本编辑器中文本选择菜单的响应类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetMenuType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextMenuType menuType)](#oh_arkui_texteditorselectionmenuoptions_setmenutype) | - | 设置文本编辑器中文本选择菜单的类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetMenuType(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_TextMenuType* menuType)](#oh_arkui_texteditorselectionmenuoptions_getmenutype) | - | 获取文本编辑器中文本选择菜单的类型。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuShowCallback(OH_ArkUI_TextEditorSelectionMenuOptions* options, void* userData, void (\*callback)(int32_t start, int32_t end, void* callbackUserData))](#oh_arkui_texteditorselectionmenuoptions_registeronmenushowcallback) | - | 设置文本选择菜单显示时触发的事件。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuHideCallback(OH_ArkUI_TextEditorSelectionMenuOptions* options, void* userData, void (\*callback)(int32_t start, int32_t end, void* callbackUserData))](#oh_arkui_texteditorselectionmenuoptions_registeronmenuhidecallback) | - | 设置文本选择菜单隐藏时触发的事件。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuAppearCallback(OH_ArkUI_TextEditorSelectionMenuOptions* options, void* userData, void (\*callback)(int32_t start, int32_t end, void* callbackUserData))](#oh_arkui_texteditorselectionmenuoptions_registeronmenuappearcallback) | - | 设置文本选择菜单出现时触发的事件。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_RegisterOnMenuDisappearCallback(OH_ArkUI_TextEditorSelectionMenuOptions* options, void* userData, void (\*callback)(void* callbackUserData))](#oh_arkui_texteditorselectionmenuoptions_registeronmenudisappearcallback) | - | 设置文本选择菜单消失时触发的事件。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_SetHapticFeedbackMode(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_HapticFeedbackMode mode)](#oh_arkui_texteditorselectionmenuoptions_sethapticfeedbackmode) | - | 设置文本编辑器中文本选择菜单的触觉反馈模式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorSelectionMenuOptions_GetHapticFeedbackMode(OH_ArkUI_TextEditorSelectionMenuOptions* options, OH_ArkUI_HapticFeedbackMode* mode)](#oh_arkui_texteditorselectionmenuoptions_gethapticfeedbackmode) | - | 获取文本编辑器中文本选择菜单的触觉反馈模式。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_CloseSelectionMenu(OH_ArkUI_TextEditorStyledStringController* controller)](#oh_arkui_texteditorstyledstringcontroller_closeselectionmenu) | - | 关闭文本编辑器属性字符串控制器的文本选择菜单。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetSelection(const OH_ArkUI_TextEditorStyledStringController* controller, uint32_t* start, uint32_t* end)](#oh_arkui_texteditorstyledstringcontroller_getselection) | - | 通过属性字符串控制器获取选中区域。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetStyledString(const OH_ArkUI_TextEditorStyledStringController* controller, const ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_texteditorstyledstringcontroller_setstyledstring) | - | 通过属性字符串控制器设置显示的属性字符串。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetStyledString(const OH_ArkUI_TextEditorStyledStringController* controller, ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_texteditorstyledstringcontroller_getstyledstring) | - | 通过属性字符串控制器获取显示的属性字符串。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetStyledPlaceholder(const OH_ArkUI_TextEditorStyledStringController* controller, const ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_texteditorstyledstringcontroller_setstyledplaceholder) | - | 通过属性字符串控制器设置属性字符串样式的提示文本。 |
| [ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_ScrollToVisible(const OH_ArkUI_TextEditorStyledStringController* controller, int32_t start, int32_t end)](#oh_arkui_texteditorstyledstringcontroller_scrolltovisible) | -    | 通过属性字符串控制器使指定起始索引至结束索引范围内的内容滚动至可视区域。 |
| [OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontWeightConfigs_Create()](#oh_arkui_fontweightconfigs_create) | - | 创建文本字体粗细配置对象。 |
| [void OH_ArkUI_FontWeightConfigs_Destroy(OH_ArkUI_FontWeightConfigs* option)](#oh_arkui_fontweightconfigs_destroy) | - | 销毁文本字体粗细配置对象。 |
| [void OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option, bool enable)](#oh_arkui_fontweightconfigs_setenablevariablefontweight) | - | 设置是否启用可变字体粗细调节。 |
| [bool OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option)](#oh_arkui_fontweightconfigs_getenablevariablefontweight) | - | 获取文本字体粗细配置对象是否启用了可变字体粗细调节。 |
| [void OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option, bool enable)](#oh_arkui_fontweightconfigs_setenabledevicefontweightcategory) | - | 设置设备的字体粗细级别改变时文本字体粗细是否自动更新。 |
| [bool OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option)](#oh_arkui_fontweightconfigs_getenabledevicefontweightcategory) | - | 获取文本字体粗细是否跟随设备的字体粗细级别更新。 |
| [OH_ArkUI_FontConfigs* OH_ArkUI_FontConfigs_Create()](#oh_arkui_fontconfigs_create) | - | 创建文本字体配置对象。 |
| [void OH_ArkUI_FontConfigs_Destroy(OH_ArkUI_FontConfigs* option)](#oh_arkui_fontconfigs_destroy) | - | 销毁文本字体配置对象。 |
| [void OH_ArkUI_FontConfigs_SetFontWeightConfigs(OH_ArkUI_FontConfigs* option, OH_ArkUI_FontWeightConfigs* fontWeightConfigs)](#oh_arkui_fontconfigs_setfontweightconfigs) | - | 设置文本字体配置对象的文本字体粗细配置。 |
| [OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontConfigs_GetFontWeightConfigs(OH_ArkUI_FontConfigs* option)](#oh_arkui_fontconfigs_getfontweightconfigs) | - | 获取文本字体配置对象的文本字体粗细配置。 |
| [OH_ArkUI_TextController* OH_ArkUI_TextController_Create()](#oh_arkui_textcontroller_create) | - | 创建文本组件控制器对象。 |
| [void OH_ArkUI_TextController_Destroy(OH_ArkUI_TextController* controller)](#oh_arkui_textcontroller_destroy) | - | 销毁文本组件控制器对象。 |
| [ArkUI_ErrorCode OH_ArkUI_TextController_SetStyledString(OH_ArkUI_TextController* controller, ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_textcontroller_setstyledstring) | - | 设置文本组件的属性字符串。 |
| [OH_ArkUI_LinearGradientOptions* OH_ArkUI_LinearGradientOptions_Create()](#oh_arkui_lineargradientoptions_create) | - | 创建线性渐变效果选项对象。 |
| [void OH_ArkUI_LinearGradientOptions_Destroy(OH_ArkUI_LinearGradientOptions* options)](#oh_arkui_lineargradientoptions_destroy) | - | 销毁线性渐变效果选项对象。 |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetAngle(OH_ArkUI_LinearGradientOptions* options, float angle)](#oh_arkui_lineargradientoptions_setangle) | - | 设置线性渐变效果选项的角度。 |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetAngle(const OH_ArkUI_LinearGradientOptions* options, float* angle)](#oh_arkui_lineargradientoptions_getangle) | - | 获取线性渐变效果选项的角度。 |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetDirection(OH_ArkUI_LinearGradientOptions* options, ArkUI_LinearGradientDirection direction)](#oh_arkui_lineargradientoptions_setdirection) | - | 设置线性渐变选项的方向。 |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetDirection(const OH_ArkUI_LinearGradientOptions* options, ArkUI_LinearGradientDirection* direction)](#oh_arkui_lineargradientoptions_getdirection) | - | 获取线性渐变选项的方向。 |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetRepeating(OH_ArkUI_LinearGradientOptions* options, bool repeating)](#oh_arkui_lineargradientoptions_setrepeating) | - | 设置颜色是否在线性渐变选项中重复。 |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetRepeating(const OH_ArkUI_LinearGradientOptions* options, bool* repeating)](#oh_arkui_lineargradientoptions_getrepeating) | - | 获取线性渐变选项中颜色是否重复。 |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetColorStop(OH_ArkUI_LinearGradientOptions* options, const uint32_t* colors, const float* stops, int32_t colorsAndStopsSize)](#oh_arkui_lineargradientoptions_setcolorstop) | - | 设置线性渐变选项的颜色停止点。 |
| [ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetColorStop(const OH_ArkUI_LinearGradientOptions* options, uint32_t* colors, float* stops, int32_t colorsAndStopsSize, int32_t* writeLength)](#oh_arkui_lineargradientoptions_getcolorstop) | - | 获取线性渐变选项的颜色停止点。 |
| [OH_ArkUI_RadialGradientOptions* OH_ArkUI_RadialGradientOptions_Create()](#oh_arkui_radialgradientoptions_create) | - | 创建一个径向渐变选项对象。 |
| [void OH_ArkUI_RadialGradientOptions_Destroy(OH_ArkUI_RadialGradientOptions* options)](#oh_arkui_radialgradientoptions_destroy) | - | 销毁一个径向渐变选项对象。 |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetCenterX(OH_ArkUI_RadialGradientOptions* options, float centerX)](#oh_arkui_radialgradientoptions_setcenterx) | - | 设置径向渐变选项中心点的X坐标。 |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetCenterX(const OH_ArkUI_RadialGradientOptions* options, float* centerX)](#oh_arkui_radialgradientoptions_getcenterx) | - | 获取径向渐变选项的中心点的X坐标。 |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetCenterY(OH_ArkUI_RadialGradientOptions* options, float centerY)](#oh_arkui_radialgradientoptions_setcentery) | - | 设置径向渐变选项中心点的Y坐标。 |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetCenterY(const OH_ArkUI_RadialGradientOptions* options, float* centerY)](#oh_arkui_radialgradientoptions_getcentery) | - | 获取径向渐变选项的中心点的Y坐标。 |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetRadius(OH_ArkUI_RadialGradientOptions* options, float radius)](#oh_arkui_radialgradientoptions_setradius) | - | 设置径向渐变选项的半径。 |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetRadius(const OH_ArkUI_RadialGradientOptions* options, float* radius)](#oh_arkui_radialgradientoptions_getradius) | - | 获取径向渐变选项的半径。 |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetRepeating(OH_ArkUI_RadialGradientOptions* options, bool repeating)](#oh_arkui_radialgradientoptions_setrepeating) | - | 设置径向渐变选项中颜色是否重复。 |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetRepeating(const OH_ArkUI_RadialGradientOptions* options, bool* repeating)](#oh_arkui_radialgradientoptions_getrepeating) | - | 获取径向渐变选项中颜色是否重复的设置。 |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetColorStop(OH_ArkUI_RadialGradientOptions* options, const uint32_t* colors, const float* stops, int32_t colorsAndStopsSize)](#oh_arkui_radialgradientoptions_setcolorstop) | - | 设置径向渐变选项的颜色停止点。 |
| [ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetColorStop(const OH_ArkUI_RadialGradientOptions* options, uint32_t* colors, float* stops, int32_t colorsAndStopsSize, int32_t* writeLength)](#oh_arkui_radialgradientoptions_getcolorstop) | - | 获取径向渐变选项的颜色停止点。 |

## 枚举类型说明

### ArkUI_FontStyle

```c
enum ArkUI_FontStyle
```

**描述：**


定义字体样式枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_FONT_STYLE_NORMAL = 0 | 标准字体样式。 |
| ARKUI_FONT_STYLE_ITALIC = 1 | 斜体字体样式。 |

### ArkUI_FontWeight

```c
enum ArkUI_FontWeight
```

**描述：**


定义字体粗细/字重枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_FONT_WEIGHT_W100 = 0 | 100 |
| ARKUI_FONT_WEIGHT_W200 = 1 | 200 |
| ARKUI_FONT_WEIGHT_W300 = 2 | 300 |
| ARKUI_FONT_WEIGHT_W400 = 3 | 400 |
| ARKUI_FONT_WEIGHT_W500 = 4 | 500 |
| ARKUI_FONT_WEIGHT_W600 = 5 | 600 |
| ARKUI_FONT_WEIGHT_W700 = 6 | 700 |
| ARKUI_FONT_WEIGHT_W800 = 7 | 800 |
| ARKUI_FONT_WEIGHT_W900 = 8 | 900 |
| ARKUI_FONT_WEIGHT_BOLD = 9 | 字体较粗。 |
| ARKUI_FONT_WEIGHT_NORMAL = 10 | 字体粗细正常。 |
| ARKUI_FONT_WEIGHT_BOLDER = 11 | 字体非常粗。 |
| ARKUI_FONT_WEIGHT_LIGHTER = 12 | 字体较细。 |
| ARKUI_FONT_WEIGHT_MEDIUM = 13 | 字体粗细适中。 |
| ARKUI_FONT_WEIGHT_REGULAR = 14 | 字体粗细正常。 |

### ArkUI_TextAlignment

```c
enum ArkUI_TextAlignment
```

**描述：**


定义字体水平对齐样式枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_ALIGNMENT_START = 0 | 水平对齐首部。 |
| ARKUI_TEXT_ALIGNMENT_CENTER = 1 | 水平居中对齐。 |
| ARKUI_TEXT_ALIGNMENT_END = 2 | 水平对齐尾部。 |
| ARKUI_TEXT_ALIGNMENT_JUSTIFY = 3 | 双端对齐。 |
| ARKUI_TEXT_ALIGNMENT_LEFT_TO_RIGHT = 4 | 从左到右对齐。<br>**起始版本：** 23 |
| ARKUI_TEXT_ALIGNMENT_RIGHT_TO_LEFT = 5 | 从右到左对齐。<br>**起始版本：** 23 |

### ArkUI_TextVerticalAlignment

```c
enum ArkUI_TextVerticalAlignment
```

**描述：**


定义文本垂直对齐样式枚举值。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE = 0 | 基线对齐。 |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_BOTTOM = 1 | 底部对齐。 |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_CENTER = 2 | 居中对齐。 |
| ARKUI_TEXT_VERTICAL_ALIGNMENT_TOP = 3 | 顶部对齐。 |

### ArkUI_TextContentAlign

```c
enum ArkUI_TextContentAlign
```

**描述：**


定义文本内容区垂直对齐样式枚举值。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_CONTENT_ALIGN_TOP = 0 | 顶部对齐。 |
| ARKUI_TEXT_CONTENT_ALIGN_CENTER = 1 | 居中对齐。 |
| ARKUI_TEXT_CONTENT_ALIGN_BOTTOM = 2 | 底部对齐。 |

### ArkUI_TextDirection

``` c
enum ArkUI_TextDirection
```

**描述：**


定义文本排版方向枚举值。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_DIRECTION_LTR = 0 | 文本排版方向从左到右。 |
| ARKUI_TEXT_DIRECTION_RTL = 1 | 文本排版方向从右到左。 |
| ARKUI_TEXT_DIRECTION_DEFAULT = 2 | 文本排版方向遵循组件布局。 |
| ARKUI_TEXT_DIRECTION_AUTO = 3 | 遵循自身实际文本内容的排版方向，如果文本为 RTL（Right-to-Left）类语言（如藏文、维吾尔文），文本排版方向为从右到左。如果为 LTR（Left-to-Right）类语言（如中文、英文），文本排版方向为从左到右。 |

### ArkUI_EnterKeyType

```c
enum ArkUI_EnterKeyType
```

**描述：**


定义单行文本输入法回车键类型枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ENTER_KEY_TYPE_GO = 2 | 显示为开始样式。 |
| ARKUI_ENTER_KEY_TYPE_SEARCH = 3 | 显示为搜索样式。 |
| ARKUI_ENTER_KEY_TYPE_SEND = 4 | 显示为发送样式。 |
| ARKUI_ENTER_KEY_TYPE_NEXT = 5 | 显示为下一个样式。 |
| ARKUI_ENTER_KEY_TYPE_DONE = 6 | 显示为完成样式。 |
| ARKUI_ENTER_KEY_TYPE_PREVIOUS = 7 | 显示为上一个样式。 |
| ARKUI_ENTER_KEY_TYPE_NEW_LINE = 8 | 显示为换行样式。 |

### ArkUI_TextInputType

```c
enum ArkUI_TextInputType
```

**描述：**


定义单行文本输入法类型枚举值。

**起始版本：** 12

| 枚举项 | 描述                       |
| -- |--------------------------|
| ARKUI_TEXTINPUT_TYPE_NORMAL = 0 | 基本输入模式。                  |
| ARKUI_TEXTINPUT_TYPE_NUMBER = 2 | 纯数字模式。                   |
| ARKUI_TEXTINPUT_TYPE_PHONE_NUMBER = 3 | 电话号码输入模式。                |
| ARKUI_TEXTINPUT_TYPE_EMAIL = 5 | 邮箱地址输入模式。                |
| ARKUI_TEXTINPUT_TYPE_PASSWORD = 7 | 密码输入模式。                  |
| ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD = 8 | 纯数字密码输入模式。               |
| ARKUI_TEXTINPUT_TYPE_SCREEN_LOCK_PASSWORD = 9 | 锁屏应用密码输入模式。              |
| ARKUI_TEXTINPUT_TYPE_USER_NAME = 10 | 用户名输入模式。                 |
| ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD = 11 | 新密码输入模式。                 |
| ARKUI_TEXTINPUT_TYPE_NUMBER_DECIMAL = 12 | 带小数点的数字输入模式。             |
| ARKUI_TEXTINPUT_TYPE_ONE_TIME_CODE = 14 | 验证码输入模式。<br>**起始版本：** 20 |

### ArkUI_TextAreaType

```c
enum ArkUI_TextAreaType
```

**描述：**


定义多行文本输入法类型枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXTAREA_TYPE_NORMAL = 0 | 基本输入模式。 |
| ARKUI_TEXTAREA_TYPE_NUMBER = 2 | 纯数字模式。 |
| ARKUI_TEXTAREA_TYPE_PHONE_NUMBER = 3 | 电话号码输入模式。 |
| ARKUI_TEXTAREA_TYPE_EMAIL = 5 | 邮箱地址输入模式。 |
| ARKUI_TEXTAREA_TYPE_ONE_TIME_CODE = 14 | 验证码输入模式。<br>**起始版本：** 20 |

### ArkUI_CancelButtonStyle

```c
enum ArkUI_CancelButtonStyle
```

**描述：**


定义清除按钮样式枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CANCELBUTTON_STYLE_CONSTANT = 0 | 清除按钮常显样式。 |
| ARKUI_CANCELBUTTON_STYLE_INVISIBLE = 1 | 清除按钮常隐样式。 |
| ARKUI_CANCELBUTTON_STYLE_INPUT = 2 | 清除按钮输入样式。 |

### ArkUI_ProgressType

```c
enum ArkUI_ProgressType
```

**描述：**


定义进度条类型枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_PROGRESS_TYPE_LINEAR = 0 | 线性样式。 |
| ARKUI_PROGRESS_TYPE_RING = 1 | 环形无刻度样式。 |
| ARKUI_PROGRESS_TYPE_ECLIPSE = 2 | 圆形样式。 |
| ARKUI_PROGRESS_TYPE_SCALE_RING = 3 | 环形有刻度样式。 |
| ARKUI_PROGRESS_TYPE_CAPSULE = 4 | 胶囊样式。 |

### ArkUI_TextDecorationType

```c
enum ArkUI_TextDecorationType
```

**描述：**


定义装饰线类型枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_DECORATION_TYPE_NONE = 0 | 不使用装饰线。 |
| ARKUI_TEXT_DECORATION_TYPE_UNDERLINE = 1 | 文字下划线修饰。 |
| ARKUI_TEXT_DECORATION_TYPE_OVERLINE = 2 | 文字上划线修饰。 |
| ARKUI_TEXT_DECORATION_TYPE_LINE_THROUGH = 3 | 穿过文本的修饰线。 |

### ArkUI_TextDecorationStyle

```c
enum ArkUI_TextDecorationStyle
```

**描述：**


定义装饰线样式枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_DECORATION_STYLE_SOLID = 0 | 单实线。 |
| ARKUI_TEXT_DECORATION_STYLE_DOUBLE = 1 | 双实线。 |
| ARKUI_TEXT_DECORATION_STYLE_DOTTED = 2 | 点线。 |
| ARKUI_TEXT_DECORATION_STYLE_DASHED = 3 | 虚线。 |
| ARKUI_TEXT_DECORATION_STYLE_WAVY = 4 | 波浪线。 |

### ArkUI_TextCase

```c
enum ArkUI_TextCase
```

**描述：**


定义文本大小写枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_CASE_NORMAL = 0 | 保持原有大小写。 |
| ARKUI_TEXT_CASE_LOWER = 1 | 文本全小写。 |
| ARKUI_TEXT_CASE_UPPER = 2 | 文本全大写。 |

### ArkUI_CopyOptions

```c
enum ArkUI_CopyOptions
```

**描述：**


定义文本复制粘贴模式枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_COPY_OPTIONS_NONE = 0 | 不支持复制。 |
| ARKUI_COPY_OPTIONS_IN_APP = 1 | 支持应用内复制。 |
| ARKUI_COPY_OPTIONS_LOCAL_DEVICE = 2 | 支持设备内复制。 |
| ARKUI_COPY_OPTIONS_CROSS_DEVICE = 3 | 支持跨设备复制。 |

### ArkUI_AccessibilityCheckedState

```c
enum ArkUI_AccessibilityCheckedState
```

**描述：**


定义无障碍复选框状态类型枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ACCESSIBILITY_UNCHECKED = 0 | 复选框未被选中。 |
| ARKUI_ACCESSIBILITY_CHECKED = 1 | 复选框被选中。 |

### ArkUI_AccessibilityActionType

```c
enum ArkUI_AccessibilityActionType
```

**描述：**


定义无障碍操作类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ACCESSIBILITY_ACTION_CLICK = 1 << 0 | 点击操作。 |
| ARKUI_ACCESSIBILITY_ACTION_LONG_CLICK = 1 << 1 | 长按操作。 |
| ARKUI_ACCESSIBILITY_ACTION_CUT = 1 << 2 | 剪切操作。 |
| ARKUI_ACCESSIBILITY_ACTION_COPY = 1 << 3 | 复制操作。 |
| ARKUI_ACCESSIBILITY_ACTION_PASTE = 1 << 4 | 粘贴操作。 |

### ArkUI_EdgeEffect

```c
enum ArkUI_EdgeEffect
```

**描述：**


定义边缘滑动效果枚举值。Grid、Scroll、WaterFlow组件默认值为ARKUI_EDGE_EFFECT_NONE，List组件默认值为ARKUI_EDGE_EFFECT_SPRING。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_EDGE_EFFECT_SPRING = 0 | 弹性物理动效，滑动到边缘后可以根据初始速度或通过触摸事件继续滑动一段距离，松手后回弹。 |
| ARKUI_EDGE_EFFECT_FADE = 1 | 阴影效果，滑动到边缘后会有圆弧状的阴影。 |
| ARKUI_EDGE_EFFECT_NONE = 2 | 滑动到边缘后无效果。 |

### ArkUI_BarState

```c
enum ArkUI_BarState
```

**描述：**


定义文本控制滚动条状态枚举值。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_BAR_STATE_OFF = 0 | 不显示。 |
| ARKUI_BAR_STATE_AUTO = 1 | 按需显示（在触摸时显示滚动条，2秒后自动消失）。 |
| ARKUI_BAR_STATE_ON = 2 | 常驻显示。 |

### ArkUI_EffectEdge

```c
enum ArkUI_EffectEdge
```

**描述：**


定义边缘效果生效边缘的方向枚举值。

**起始版本：** 18

| 枚举项 | 描述                    |
| -- |-----------------------|
| ARKUI_EFFECT_EDGE_START = 1 | 起始边生效。                |
| ARKUI_EFFECT_EDGE_END = 2 | 末尾边生效。                |

### ArkUI_ScrollDirection

```c
enum ArkUI_ScrollDirection
```

**描述：**


定义[Scroll](../apis-arkui/arkui-ts/ts-container-scroll.md)组件排列方向枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_DIRECTION_VERTICAL = 0 | 仅支持竖直方向滚动。 |
| ARKUI_SCROLL_DIRECTION_HORIZONTAL = 1 | 仅支持水平方向滚动。 |
| ARKUI_SCROLL_DIRECTION_NONE = 3 | 禁止滚动。 |
| ARKUI_SCROLL_DIRECTION_FREE = 4 | 自由滚动。<br>**起始版本：** 20 |

### ArkUI_ScrollSnapAlign

```c
enum ArkUI_ScrollSnapAlign
```

**描述：**


定义列表项滚动结束对齐效果枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_SNAP_ALIGN_NONE = 0 | 默认无列表滚动对齐效果。 |
| ARKUI_SCROLL_SNAP_ALIGN_START = 1 | 视图中的第一项将在列表的开头对齐。 |
| ARKUI_SCROLL_SNAP_ALIGN_CENTER = 2 | 视图中的中间项将在列表中心对齐。 |
| ARKUI_SCROLL_SNAP_ALIGN_END = 3 | 视图中的最后一项将在列表末尾对齐。 |

### ArkUI_ScrollBarDisplayMode

```c
enum ArkUI_ScrollBarDisplayMode
```

**描述：**


定义滚动条状态枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF = 0 | 不显示。 |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO = 1 | 按需显示(触摸时显示，2s后消失)。 |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_ON = 2 | 常驻显示。 |

### ArkUI_StickyStyle

```c
enum ArkUI_StickyStyle
```

**描述：**


定义列表是否吸顶和吸底枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_STICKY_STYLE_NONE = 0 | [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md)的[header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)不吸顶，[footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)不吸底。 |
| ARKUI_STICKY_STYLE_HEADER = 1 | [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md)的[header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)吸顶，[footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)不吸底。 |
| ARKUI_STICKY_STYLE_FOOTER = 2 | [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md)的[header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)不吸顶，[footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)吸底。 |
| ARKUI_STICKY_STYLE_BOTH = 3 | [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md)的[header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)吸顶，[footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)吸底。 |

### ArkUI_ContentClipMode

```c
enum ArkUI_ContentClipMode
```

**描述：**


定义滚动容器的内容层裁剪区域枚举值。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY = 0 | 按内容区裁剪。 |
| ARKUI_CONTENT_CLIP_MODE_BOUNDARY = 1 | 按组件区域裁剪。 |
| ARKUI_CONTENT_CLIP_MODE_SAFE_AREA = 2 | 按组件配置的[安全区域](./arkui-ts/ts-universal-attributes-expand-safe-area.md)裁剪。 |

### ArkUI_WaterFlowLayoutMode

```c
enum ArkUI_WaterFlowLayoutMode
```

**描述：**


定义[WaterFlow](../apis-arkui/arkui-ts/ts-container-waterflow.md)组件布局模式枚举值。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_WATER_FLOW_LAYOUT_MODE_ALWAYS_TOP_DOWN = 0 | 从上到下布局。列数切换场景需要从第一个[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)开始布局到当前显示的[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)。 |
| ARKUI_WATER_FLOW_LAYOUT_MODE_SLIDING_WINDOW = 1 | 移动窗口布局。列数切换场景只重新布局当前显示范围到[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)，手指向下滑动再布局从上方进入显示范围的[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)。 |

### ArkUI_BorderStyle

```c
enum ArkUI_BorderStyle
```

**描述：**


边框线条样式枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_BORDER_STYLE_SOLID = 0 | 显示为一条实线，该值为默认值。 |
| ARKUI_BORDER_STYLE_DASHED = 1 | 显示为一系列短的方形虚线。 |
| ARKUI_BORDER_STYLE_DOTTED = 2 | 显示为一系列圆点。 |

### ArkUI_AccessibilityMode

```c
enum ArkUI_AccessibilityMode
```

**描述：**


定义无障碍辅助服务模式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ACCESSIBILITY_MODE_AUTO = 0 | 根据组件不同会转换为“enabled”或者“disabled”。 |
| ARKUI_ACCESSIBILITY_MODE_ENABLED = 1 | 当前组件可被无障碍辅助服务所识别。 |
| ARKUI_ACCESSIBILITY_MODE_DISABLED = 2 | 当前组件不可被无障碍辅助服务所识别。 |
| ARKUI_ACCESSIBILITY_MODE_DISABLED_FOR_DESCENDANTS = 3 | 当前组件及其所有子组件不可被无障碍辅助服务所识别。 |

### ArkUI_TextCopyOptions

```c
enum ArkUI_TextCopyOptions
```

**描述：**


定义组件支持设置文本是否可复制粘贴。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_COPY_OPTIONS_NONE = 0 | 不支持复制。 |
| ARKUI_TEXT_COPY_OPTIONS_IN_APP = 1 | 支持应用内复制。 |
| ARKUI_TEXT_COPY_OPTIONS_LOCAL_DEVICE = 2 | 支持设备内复制。 |
| ARKUI_TEXT_COPY_OPTIONS_CROSS_DEVICE = 3 | 支持跨设备复制。 |

### ArkUI_TextHeightAdaptivePolicy

```c
enum ArkUI_TextHeightAdaptivePolicy
```

**描述：**


定义文本自适应高度的方式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MAX_LINES_FIRST = 0 | 设置文本高度自适应方式为以MaxLines优先。 |
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MIN_FONT_SIZE_FIRST = 1 | 设置文本高度自适应方式为以缩小字体优先。 |
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_LAYOUT_CONSTRAINT_FIRST = 2 | 设置文本高度自适应方式为以布局约束（高度）优先。 |

### ArkUI_ScrollNestedMode

```c
enum ArkUI_ScrollNestedMode
```

**描述：**


定义嵌套滚动选项。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_NESTED_MODE_SELF_ONLY = 0 | 只自身滚动，不与父组件联动。 |
| ARKUI_SCROLL_NESTED_MODE_SELF_FIRST = 1 | 自身先滚动，自身滚动到边缘以后父组件滚动。父组件滚动到边缘以后，如果父组件有边缘效果，则父组件触发边缘效果，否则子组件触发边缘效果。 |
| ARKUI_SCROLL_NESTED_MODE_PARENT_FIRST = 2 | 父组件先滚动，父组件滚动到边缘以后自身滚动。自身滚动到边缘后，如果有边缘效果，会触发自身的边缘效果，否则触发父组件的边缘效果。 |
| ARKUI_SCROLL_NESTED_MODE_PARALLEL = 3 | 自身和父组件同时滚动，自身和父组件都到达边缘以后，如果自身有边缘效果，则自身触发边缘效果，否则父组件触发边缘效果。 |

### ArkUI_ScrollEdge

```c
enum ArkUI_ScrollEdge
```

**描述：**


定义滚动到的边缘位置。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_EDGE_TOP = 0 | 竖直方向上边缘。 |
| ARKUI_SCROLL_EDGE_BOTTOM = 1 | 竖直方向下边缘。 |
| ARKUI_SCROLL_EDGE_START = 2 | 水平方向起始位置。 |
| ARKUI_SCROLL_EDGE_END = 3 | 水平方向末尾位置。 |

### ArkUI_ScrollAlignment

```c
enum ArkUI_ScrollAlignment
```

**描述：**


滚动到具体item时的对齐方式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_ALIGNMENT_START = 0 | 首部对齐。指定item首部与容器首部对齐。 |
| ARKUI_SCROLL_ALIGNMENT_CENTER = 1 | 居中对齐。指定item主轴方向居中对齐于容器。 |
| ARKUI_SCROLL_ALIGNMENT_END = 2 | 尾部对齐。指定item尾部与容器尾部对齐。 |
| ARKUI_SCROLL_ALIGNMENT_AUTO = 3 | 自动对齐。若指定item完全处于显示区，不做调整。否则依照滑动距离最短的原则，将指定item首部对齐或尾部对齐于容器,使指定item完全处于显示区。 |

### ArkUI_ScrollState

```c
enum ArkUI_ScrollState
```

**描述：**


定义当前滚动状态。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_STATE_IDLE = 0 | 空闲状态。使用控制器提供的方法控制滚动时触发，拖动滚动条滚动时触发。 |
| ARKUI_SCROLL_STATE_SCROLL = 1 | 滚动状态。使用手指拖动容器滚动时触发。 |
| ARKUI_SCROLL_STATE_FLING = 2 | 惯性滚动状态。快速划动松手后进行惯性滚动和划动到边缘回弹时触发。 |

### ArkUI_SliderBlockStyle

```c
enum ArkUI_SliderBlockStyle
```

**描述：**


定义滑块形状。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SLIDER_BLOCK_STYLE_DEFAULT = 0 | 使用默认滑块（圆形）。 |
| ARKUI_SLIDER_BLOCK_STYLE_IMAGE = 1 | 使用图片资源作为滑块。 |
| ARKUI_SLIDER_BLOCK_STYLE_SHAPE = 2 | 使用自定义形状作为滑块。 |

### ArkUI_SliderDirection

```c
enum ArkUI_SliderDirection
```

**描述：**


定义滑动条滑动方向。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SLIDER_DIRECTION_VERTICAL = 0 | 方向为纵向。 |
| ARKUI_SLIDER_DIRECTION_HORIZONTAL = 1 | 方向为横向。 |

### ArkUI_SliderStyle

```c
enum ArkUI_SliderStyle
```

**描述：**


定义滑块与滑轨显示样式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SLIDER_STYLE_OUT_SET = 0 | 滑块在滑轨上。 |
| ARKUI_SLIDER_STYLE_IN_SET = 1 | 滑块在滑轨内。 |
| ARKUI_SLIDER_STYLE_NONE = 2 | 无滑块。 |

### ArkUI_CheckboxShape

```c
enum ArkUI_CheckboxShape
```

**描述：**


定义CheckBox组件形状。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ArkUI_CHECKBOX_SHAPE_CIRCLE = 0 | 圆形。 |
| ArkUI_CHECKBOX_SHAPE_ROUNDED_SQUARE = 1 | 圆角方形。 |

### ArkUI_AdaptiveColor

```c
enum ArkUI_AdaptiveColor
```

**描述：**


定义取色模式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ADAPTIVE_COLOR_DEFAULT = 0 | 不使用取色模糊。 |
| ARKUI_ADAPTIVE_COLOR_AVERAGE = 1 | 使用取色模糊。 |

### ArkUI_ColorMode

```c
enum ArkUI_ColorMode
```

**描述：**


定义深浅色模式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_COLOR_MODE_SYSTEM = 0 | 跟随系统深浅色模式。 |
| ARKUI_COLOR_MODE_LIGHT = 1 | 固定使用浅色模式。 |
| ARKUI_COLOR_MODE_DARK = 2 | 固定使用深色模式。 |

### ArkUI_SystemColorMode

```c
enum ArkUI_SystemColorMode
```

**描述：**


定义系统深浅色模式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SYSTEM_COLOR_MODE_LIGHT = 0 | 浅色模式。 |
| ARKUI_SYSTEM_COLOR_MODE_DARK = 1 | 深色模式。 |

### ArkUI_TextOverflow

```c
enum ArkUI_TextOverflow
```

**描述：**


定义文本超长时的显示方式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_OVERFLOW_NONE = 0 | 文本超长时不裁剪显示。 |
| ARKUI_TEXT_OVERFLOW_CLIP = 1 | 文本超长时进行裁剪显示。 |
| ARKUI_TEXT_OVERFLOW_ELLIPSIS = 2 | 文本超长时显示不下的文本用省略号代替。 |
| ARKUI_TEXT_OVERFLOW_MARQUEE = 3 | 文本超长时以跑马灯的方式展示。 |

### ArkUI_ImageSpanAlignment

```c
enum ArkUI_ImageSpanAlignment
```

**描述：**


定义图片基于文本的对齐方式。

**起始版本：** 12

| 枚举项 | 描述                                 |
| -- |------------------------------------|
| ARKUI_IMAGE_SPAN_ALIGNMENT_BASELINE = 0 | 图片下边沿与文本BaseLine对齐。                |
| ARKUI_IMAGE_SPAN_ALIGNMENT_BOTTOM | 图片下边沿与文本下边沿对齐。                     |
| ARKUI_IMAGE_SPAN_ALIGNMENT_CENTER | 图片中间与文本中间对齐。                       |
| ARKUI_IMAGE_SPAN_ALIGNMENT_TOP | 图片上边沿与文本上边沿对齐。                     |
| ARKUI_IMAGE_SPAN_ALIGNMENT_FOLLOW_PARAGRAPH | 图片对齐方式跟随Text组件对齐方式。<br>**起始版本：** 20 |

### ArkUI_WordBreak

```c
enum ArkUI_WordBreak
```

**描述：**


定义文本断行规则。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_WORD_BREAK_NORMAL = 0 | CJK(中文、日文、韩文)文本可以在任意2个字符间断行，而Non-CJK文本（如英文等）只能在空白符处断行。 |
| ARKUI_WORD_BREAK_BREAK_ALL | 对于Non-CJK的文本，可在任意2个字符间断行。CJK(中文、日文、韩文)文本可以在任意2个字符间断行。 |
| ARKUI_WORD_BREAK_BREAK_WORD | 对于Non-CJK的文本可在任意2个字符间断行，一行文本中有断行破发点（如空白符）时，优先按破发点换行。对于CJK的文本，换行效果与NORMAL效果保持一致。 |
| ARKUI_WORD_BREAK_HYPHENATION | 对于Non-CJK的文本，可以按照音节断行。对于CJK的文本，换行效果与NORMAL效果保持一致。<br>**起始版本：** 18 |

### ArkUI_EllipsisMode

```c
enum ArkUI_EllipsisMode
```

**描述：**


定义文本省略位置。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ELLIPSIS_MODE_START = 0 | 省略行首内容。适用单行文本场景。 |
| ARKUI_ELLIPSIS_MODE_CENTER = 1 | 省略行中内容。适用单行文本场景。 |
| ARKUI_ELLIPSIS_MODE_END = 2 | 省略行末内容。适用单行文本和多行文本场景 |
| ARKUI_ELLIPSIS_MODE_MULTILINE_START = 3 | 省略行首内容。适用单行文本和多行文本场景。<br>**起始版本：** 24 |
| ARKUI_ELLIPSIS_MODE_MULTILINE_CENTER = 4 | 省略行中内容。适用单行文本和多行文本场景。<br>**起始版本：** 24 |

### ArkUI_ListItemAlignment

```c
enum ArkUI_ListItemAlignment
```

**描述：**


交叉轴方向的布局方式，默认值为ARKUI_LIST_ITEM_ALIGNMENT_START。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_ALIGNMENT_START = 0 | [ListItem](./arkui-ts/ts-container-listitem.md#listitem10)在List中，交叉轴方向首部对齐。 |
| ARKUI_LIST_ITEM_ALIGNMENT_CENTER = 1 | ListItem在List中，交叉轴方向居中对齐。 |
| ARKUI_LIST_ITEM_ALIGNMENT_END = 2 | ListItem在List中，交叉轴方向尾部对齐。 |

### ArkUI_LengthMetricUnit

```c
enum ArkUI_LengthMetricUnit
```

**描述：**


定义组件的单位模式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LENGTH_METRIC_UNIT_DEFAULT = -1 | 默认，字体类单位为fp，非字体类单位为vp。 |
| ARKUI_LENGTH_METRIC_UNIT_PX = 0 | 单位为px。 |
| ARKUI_LENGTH_METRIC_UNIT_VP = 1 | 单位为vp。 |
| ARKUI_LENGTH_METRIC_UNIT_FP = 2 | 单位为fp。 |

### ArkUI_TextInputContentType

```c
enum ArkUI_TextInputContentType
```

**描述：**


定义自动填充类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXTINPUT_CONTENT_TYPE_USER_NAME = 0 | 【用户名】在已启用密码保险箱的情况下，支持用户名的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSWORD | 【密码】在已启用密码保险箱的情况下，支持密码的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NEW_PASSWORD | 【新密码】在已启用密码保险箱的情况下，支持自动生成新密码。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_STREET_ADDRESS | 【详细地址】在已启用情景化自动填充的情况下，支持详细地址的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_HOUSE_NUMBER | 【门牌号】在已启用情景化自动填充的情况下，支持门牌号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DISTRICT_ADDRESS | 【区/县】在已启用情景化自动填充的情况下，支持区/县的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_CITY_ADDRESS | 【市】在已启用情景化自动填充的情况下，支持市的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PROVINCE_ADDRESS | 【省】在已启用情景化自动填充的情况下，支持省的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_COUNTRY_ADDRESS | 【国家】在已启用情景化自动填充的情况下，支持国家的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FULL_NAME | 【姓名】在已启用情景化自动填充的情况下，支持姓名的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_LAST_NAME | 【姓氏】在已启用情景化自动填充的情况下，支持姓氏的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FIRST_NAME | 【名字】在已启用情景化自动填充的情况下，支持名字的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_NUMBER | 【手机号】在已启用情景化自动填充的情况下，支持手机号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_COUNTRY_CODE | 【国家代码】在已启用情景化自动填充的情况下，支持国家代码的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_PHONE_NUMBER | 【包含国家代码的手机号】在已启用情景化自动填充的情况下，支持包含国家代码的手机号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_EMAIL_ADDRESS | 【邮箱地址】在已启用情景化自动填充的情况下，支持邮箱地址的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_BANK_CARD_NUMBER | 【银行卡号】在已启用情景化自动填充的情况下，支持银行卡号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ID_CARD_NUMBER | 【身份证号】在已启用情景化自动填充的情况下，支持身份证号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NICKNAME | 【昵称】在已启用情景化自动填充的情况下，支持昵称的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DETAIL_INFO_WITHOUT_STREET | 【无街道地址】在已启用情景化自动填充的情况下，支持无街道地址的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FORMAT_ADDRESS | 【标准地址】在已启用情景化自动填充的情况下，支持标准地址的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSPORT_NUMBER | 【护照号】在已启用情景化自动填充的情况下，支持护照号的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_VALIDITY | 【护照有效期】在已启用情景化自动填充的情况下，支持护照有效期的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ISSUE_AT | 【护照签发地】在已启用情景化自动填充的情况下，支持护照签发地的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ORGANIZATION | 【发票抬头名称】在已启用情景化自动填充的情况下，支持发票抬头名称的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_TAX_ID | 【税号】在已启用情景化自动填充的情况下，支持税号的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ADDRESS_CITY_AND_STATE | 【所在地区】在已启用情景化自动填充的情况下，支持所在地区的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FLIGHT_NUMBER | 【航班号】暂不支持自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_NUMBER | 【驾驶证号】暂不支持自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_FILE_NUMBER | 【驾驶证档案编号】暂不支持自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_PLATE | 【车牌号】在已启用情景化自动填充的情况下，支持车牌号的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ENGINE_NUMBER | 【行驶证发动机号】暂不支持自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER | 【车牌识别号】暂不支持自动保存和自动填充。<br>**起始版本：** 18 |

### ArkUI_TextInputStyle

```c
enum ArkUI_TextInputStyle
```

**描述：**


定义输入框风格。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXTINPUT_STYLE_DEFAULT = 0 | 默认风格，光标宽1.5vp，光标高度与文本选中底板高度和字体大小相关。 |
| ARKUI_TEXTINPUT_STYLE_INLINE | 内联输入风格。文本选中底板高度与输入框高度相同。 |

### ArkUI_KeyboardAppearance

```c
enum ArkUI_KeyboardAppearance
```

**描述：**


定义输入框拉起的键盘样式。

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE = 0 | 默认模式，不使用沉浸式样式。 |
| ARKUI_KEYBOARD_APPEARANCE_IMMERSIVE = 1 | 沉浸式模式，由系统决定采用的样式。 |
| ARKUI_KEYBOARD_APPEARANCE_LIGHT_IMMERSIVE = 2 | 浅色沉浸式样式。 |
| ARKUI_KEYBOARD_APPEARANCE_DARK_IMMERSIVE = 3 | 深色沉浸式样式。 |

### ArkUI_TextDataDetectorType

```c
enum ArkUI_TextDataDetectorType
```

**描述：**


定义文本识别的实体类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_PHONE_NUMBER = 0 | 电话号码。 |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_URL | 链接。 |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_EMAIL | 邮箱。 |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_ADDRESS | 地址。 |

### ArkUI_ButtonType

```c
enum ArkUI_ButtonType
```

**描述：**


定义按钮样式枚举值。

**起始版本：** 12

| 枚举项 | 描述                      |
| -- |-------------------------|
| ARKUI_BUTTON_TYPE_NORMAL = 0 | 普通按钮，默认不带圆角。            |
| ARKUI_BUTTON_TYPE_CAPSULE = 1 | 胶囊型按钮，圆角默认为高度的一半。       |
| ARKUI_BUTTON_TYPE_CIRCLE = 2 | 圆形按钮。                   |
| ARKUI_BUTTON_ROUNDED_RECTANGLE = 8 | 圆角矩形按钮。<br>**起始版本：** 19 |

### ArkUI_ListItemSwipeActionState

```c
enum ArkUI_ListItemSwipeActionState
```

**描述：**


定义[Listitem](./arkui-ts/ts-container-listitem.md#listitem10)组件[SwipeAction](./arkui-ts/ts-container-listitem.md#swipeaction9)方法的显隐模式，默认值为ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED = 0 | 收起状态，当ListItem与主轴方向相反滑动时操作项处于隐藏状态。 |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_EXPANDED = 1 | 展开状态，当ListItem与主轴方向相反滑动时操作项处于显示状态。 |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_ACTIONING = 2 | 长距离状态，当ListItem进入长距删除区后删除ListItem的状态。 |

### ArkUI_ListItemSwipeEdgeEffect

```c
enum ArkUI_ListItemSwipeEdgeEffect
```

**描述：**


定义Listitem组件[swipeAction](./arkui-ts/ts-container-listitem.md#swipeaction9)方法的滚动模式，默认值为ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING = 0 | ListItem划动距离超过划出组件大小后可以继续划动。 |
| ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_NONE = 1 | ListItem划动距离不能超过划出组件大小。 |

### ArkUI_ListItemSwipeActionDirection

```c
enum ArkUI_ListItemSwipeActionDirection
```

**描述：**

ListItem划出菜单的展开方向。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_START = 0 | 当列表方向是垂直方向时，LTR模式下表示ListItem的左边，RTL模式下表示ListItem的右边。当列表是水平方向时，表示ListItem的上边。 |
| ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_END = 1 | 当列表方向是垂直方向时，LTR模式下表示ListItem的右边，RTL模式下表示ListItem的左边。当列表是水平方向时，表示ListItem的下边。 |

### ArkUI_ErrorCode

```c
enum ArkUI_ErrorCode
```

**描述：**


定义错误码枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ERROR_CODE_NO_ERROR = 0 | 无错误。 |
| ARKUI_ERROR_CODE_PARAM_INVALID = 401 | 参数错误。 |
| ARKUI_ERROR_CODE_CAPI_INIT_ERROR = 500 |  接口初始化错误。<br>**起始版本：** 18 |
| ARKUI_ERROR_CODE_INTERNAL_ERROR = 100001 |  出现内部错误，例如内部环境错误导致失败，或者由于内部执行失败导致操作失败。<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_PARAM_ERROR = 100023 |  参数错误。错误码的详细介绍请参见[100023 参数错误](../apis-arkui/errorcode-node.md#100023-参数错误)。<br>**起始版本：** 21 |
| ARKUI_ERROR_CODE_XCOMPONENT_STATE_INVALID = 103501 |  当前XComponent状态异常，方法调用失败。错误码的详细介绍请参见[XComponent组件错误码](../apis-arkui/errorcode-xcomponent.md)。<br>**起始版本：** 19 |
| ARKUI_ERROR_CODE_ATTRIBUTE_OR_EVENT_NOT_SUPPORTED = 106102 | 组件不支持特定的属性或者事件。错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。 |
| ARKUI_ERROR_CODE_ARKTS_NODE_NOT_SUPPORTED = 106103 | 不支持对ArkTS创建的节点执行对应的操作。错误码的详细介绍请参见[106103 对应的操作不支持ArkTS创建的节点](../apis-arkui/errorcode-node.md#106103-对应的操作不支持arkts创建的节点)。 |
| ARKUI_ERROR_CODE_ADAPTER_NOT_BOUND = 106104 | 懒加载适配器未绑定到组件上。错误码的详细介绍请参见[106104 适配器未绑定](../apis-arkui/errorcode-nodeadapter.md#106104-适配器未绑定)。 |
| ARKUI_ERROR_CODE_ADAPTER_EXIST = 106105 | 适配器已存在。错误码的详细介绍请参见[106105 适配器已存在](../apis-arkui/errorcode-nodeadapter.md#106105-适配器已存在)。 |
| ARKUI_ERROR_CODE_CHILD_NODE_EXIST = 106106 | 对应节点已存在子节点，无法添加适配器。错误码的详细介绍请参见[106106 子节点已存在](../apis-arkui/errorcode-nodeadapter.md#106106-子节点已存在)。 |
| ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INDEX_OUT_OF_RANGE = 106107 | 组件事件中参数长度超限。错误码的详细介绍请参见[106107 参数下标越界](../apis-arkui/errorcode-nodeadapter.md#106107-参数下标越界)。 |
| ARKUI_ERROR_CODE_NODE_EVENT_PARAM_INVALID = 106108 | 组件事件中不存在该数据。错误码的详细介绍请参见[106108 数据不存在](../apis-arkui/errorcode-nodeadapter.md#106108-数据不存在)。 |
| ARKUI_ERROR_CODE_NODE_EVENT_NO_RETURN = 106109 | 组件事件不支持返回值。错误码的详细介绍请参见[106109 不支持返回值](../apis-arkui/errorcode-nodeadapter.md#106109-不支持返回值)。 |
| ARKUI_ERROR_CODE_NODE_UNSUPPORTED_EVENT_TYPE = 106110 | 暂不支持该事件类型。错误码的详细介绍请参见[106110 暂不支持该事件类型](../apis-arkui/errorcode-nodeadapter.md#106110-暂不支持该事件类型)。<br>**起始版本：** 21 |
| ARKUI_ERROR_CODE_NODE_INDEX_INVALID = 106200 | 传入的索引值非法。<br/>错误码的详细介绍请参见[106200 传入的索引值非法](../apis-arkui/errorcode-router.md#106200-传入的索引值非法)。 |
| ARKUI_ERROR_CODE_GET_INFO_FAILED = 106201 | 查询路由导航信息失败。<br/>错误码的详细介绍请参见[106201 查询路由导航信息失败](../apis-arkui/errorcode-router.md#106201-查询路由导航信息失败)。 |
| ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR = 106202 | 传入的buffer size异常（数据过大）。<br/>错误码的详细介绍请参见[106202 传入的buffer size异常](../apis-arkui/errorcode-router.md#106202-传入的buffer-size异常)。 |
| ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE = 106203 |  传入的节点未挂载到组件树上。错误码的详细介绍请参见[106203 传入的节点未挂载到组件树上](../apis-arkui/errorcode-node.md#106203-传入的节点未挂载到组件树上)。<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD = 106204 |  不支持在非UI线程操作传入的节点。错误码的详细介绍请参见[106204 不支持在非UI线程操作传入的节点](../apis-arkui/errorcode-node.md#106204-不支持在非ui线程操作传入的节点)。<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_FORCE_DARK_CONFIG_INVALID = 106205 |  反色能力入参错误。错误码的详细介绍请参见[106205 反色能力入参错误](../apis-arkui/errorcode-force-dark.md#106205-反色能力入参错误)。<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_NODE_IS_ADOPTED = 106206 |  节点已被接纳为附属节点。错误码的详细介绍请参见[106206 节点已被接纳为附属节点](../apis-arkui/errorcode-adopt.md#106206-节点已被接纳为附属节点)。<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_NODE_HAS_PARENT = 106207 |  被接纳的节点已有父节点。错误码的详细介绍请参见[106207 被接纳的附属节点已有父节点](../apis-arkui/errorcode-adopt.md#106207-被接纳的附属节点已有父节点)。<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_NODE_CAN_NOT_BE_ADOPTED = 106208 |  节点无法被接纳为附属节点。错误码的详细介绍请参见[106208 节点无法被接纳为附属节点](../apis-arkui/errorcode-adopt.md#106208-节点无法被接纳为附属节点)。<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_NODE_CAN_NOT_ADOPT_TO = 106209 |  节点无法接纳其他节点。错误码的详细介绍请参见[106209 节点无法接纳其他节点](../apis-arkui/errorcode-adopt.md#106209-节点无法接纳其他节点)。<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_NODE_IS_NOT_IN_ADOPTED_CHILDREN = 106210 |  节点不是被目标节点接纳的附属节点。错误码的详细介绍请参见[106210 节点不是被目标节点接纳的附属节点](../apis-arkui/errorcode-adopt.md#106210-节点不是被目标节点接纳的附属节点)。<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_NOT_CUSTOM_NODE = 106401 |  当前节点不是自定义节点。错误码的详细介绍请参见[渲染节点错误码](../apis-arkui/errorcode-node-render.md)。<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_CHILD_EXISTED = 106402 |  当前节点已存在子节点。错误码的详细介绍请参见[渲染节点错误码](../apis-arkui/errorcode-node-render.md)。<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_RENDER_PARENT_EXISTED = 106403 |  当前渲染节点存在父组件。错误码的详细介绍请参见[渲染节点错误码](../apis-arkui/errorcode-node-render.md)。<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_RENDER_CHILD_NOT_EXIST = 106404 |  未找到对应的渲染子节点。错误码的详细介绍请参见[渲染节点错误码](../apis-arkui/errorcode-node-render.md)。<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE = 106405 |  参数值超出范围。错误码的详细介绍请参见[渲染节点错误码](../apis-arkui/errorcode-node-render.md)。<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_RENDER_IS_FROM_FRAME_NODE = 106406 |  当前渲染节点从[FrameNode](js-apis-arkui-frameNode.md)中获取。错误码的详细介绍请参见[106406 当前渲染节点从FrameNode中获取](../apis-arkui/errorcode-node-render.md#106406-当前渲染节点从framenode中获取)。<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_RENDER_HAS_INVALID_FRAME_NODE = 106407 |  当前渲染节点从[FrameNode](js-apis-arkui-frameNode.md)中获取且该[FrameNode](js-apis-arkui-frameNode.md)已被取消接纳为附属节点或销毁。错误码的详细介绍请参见[106407 当前渲染节点从FrameNode中获取且该FrameNode已被取消接纳为附属节点或销毁](../apis-arkui/errorcode-node-render.md#106407-当前渲染节点从framenode中获取且该framenode已被取消接纳为附属节点或销毁)。<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_RENDER_NOT_ADOPTED_NODE = 106408 |  当前节点不处于被接纳状态。错误码的详细介绍请参见[106408 当前节点不处于被接纳状态](../apis-arkui/errorcode-node-render.md#106408-当前节点不处于被接纳状态)。<br>**起始版本：** 22 |
| ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE = 150001 |  当前节点无法获得焦点。错误码的详细介绍请参见[150001 节点无法获得焦点](../apis-arkui/errorcode-focus.md#150001-节点无法获得焦点)。<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_FOCUS_NON_FOCUSABLE_ANCESTOR = 150002 |  当前节点对应的祖先节点中存在无法获焦节点。错误码的详细介绍请参见[150002 祖先节点无法获得焦点](../apis-arkui/errorcode-focus.md#150002-祖先节点无法获得焦点)。<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_FOCUS_NON_EXISTENT = 150003 |  当前节点不存在。错误码的详细介绍请参见[150003 节点不存在](../apis-arkui/errorcode-focus.md#150003-节点不存在)。<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_TIMEOUT = 160002 |  截图超时。错误码的详细介绍请参见[截图错误码](../apis-arkui/errorcode-snapshot.md)。<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_MODE_NOT_SUPPORTED = 160003 | 截图选项不支持的色彩空间或动态范围模式。错误码的详细介绍请参见[截图错误码](../apis-arkui/errorcode-snapshot.md)。<br>**起始版本：** 23 |
| ARKUI_ERROR_CODE_COMPONENT_SNAPSHOT_AUTO_NOT_SUPPORTED = 160004 | 离屏节点截图不支持色彩空间或动态范围模式的isAuto参数设置为true。错误码的详细介绍请参见[截图错误码](../apis-arkui/errorcode-snapshot.md)。<br>**起始版本：** 23 |
| ARKUI_ERROR_CODE_NON_SCROLLABLE_CONTAINER = 180001 | 非滚动类容器。错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。 |
| ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH = 180002 | 存储区大小不足。错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。 |
| ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT = 180003 |  该事件不是克隆事件。错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_POST_CLONED_COMPONENT_STATUS_ABNORMAL = 180004 |  组件状态异常。错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。<br>**起始版本：** 15 |
| ARKUI_ERROR_CODE_POST_CLONED_NO_COMPONENT_HIT_TO_RESPOND_TO_THE_EVENT = 180005 |  未命中可响应事件的组件。错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。<br>**起始版本：** 15 |
| ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED = 180006 |  接口不支持此输入事件类型。<br>**起始版本：** 20 |
| ARKUI_ERROR_CODE_INVALID_STYLED_STRING = 180101 |  无效的属性字符串。错误码的详细介绍请参见[属性字符串错误码](../apis-arkui/errorcode-styled-string.md)。<br>**起始版本：** 14 |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID = 190001 |  无效的UIContext对象。错误码的详细介绍请参见[UI上下文错误码](../apis-arkui/errorcode-uicontext.md)。<br>**起始版本：** 18 |
| ARKUI_ERROR_CODE_CALLBACK_INVALID = 190002 |  无效的回调函数。错误码的详细介绍请参见[UI上下文错误码](../apis-arkui/errorcode-uicontext.md)。<br>**起始版本：** 18 |
| ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED = 180102 |  不支持手势识别器类型。错误码的详细介绍请参见[交互事件错误码](../apis-arkui/errorcode-event.md)。<br>**起始版本：** 18 |
| ARKUI_ERROR_CODE_DRAG_DROP_OPERATION_NOT_ALLOWED = 190004 |  当前阶段不允许该操作。错误码的详细介绍请参见[拖拽事件错误码](../apis-arkui/errorcode-drag-event.md)。<br>**起始版本：** 19 |

### ArkUI_ScrollSource

```c
enum ArkUI_ScrollSource
```

**描述：**


定义滚动来源枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_SOURCE_DRAG = 0 | 手指拖动。 |
| ARKUI_SCROLL_SOURCE_FLING = 1 | 手指拖动后的惯性滚动。 |
| ARKUI_SCROLL_SOURCE_EDGE_EFFECT = 2 | 在过界时执行[EdgeEffect.Spring](../apis-arkui/arkui-ts/ts-appendix-enums.md#edgeeffect)边缘特效。 |
| ARKUI_SCROLL_SOURCE_OTHER_USER_INPUT = 3 | 除了拖动以外的其他用户输入，如鼠标滚轮、键盘事件等。 |
| ARKUI_SCROLL_SOURCE_SCROLL_BAR = 4 | 拖动滚动条。 |
| ARKUI_SCROLL_SOURCE_SCROLL_BAR_FLING = 5 | 拖动滚动条后的惯性滚动。 |
| ARKUI_SCROLL_SOURCE_SCROLLER = 6 | 滚动控制器引起的无动画的滚动。 |
| ARKUI_SCROLL_SOURCE_ANIMATION = 7 | 滚动控制器引起的带动画的滚动。 |

### ArkUI_SafeAreaType

```c
enum ArkUI_SafeAreaType
```

**描述：**


定义扩展安全区域的枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SAFE_AREA_TYPE_SYSTEM = 1 | 系统默认非安全区域，包括状态栏、导航栏，该值为默认值。 |
| ARKUI_SAFE_AREA_TYPE_CUTOUT = 1 << 1 | 设备的非安全区域，例如刘海屏或挖孔屏区域。 |
| ARKUI_SAFE_AREA_TYPE_KEYBOARD = 1 << 2 | 软键盘区域。 |

### ArkUI_ListItemGroupArea

```c
enum ArkUI_ListItemGroupArea
```

**描述：**


定义[ListItemGroup](./arkui-ts/ts-container-listitemgroup.md)组件区域，默认值为ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE。

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE = 0 | ListItemGroup区域外。 |
| ARKUI_LIST_ITEM_SWIPE_AREA_NONE = 1 | ListItemGroup没有[header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)、[footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)和[ListItem](./arkui-ts/ts-container-listitem.md#listitem10)时的区域。 |
| ARKUI_LIST_ITEM_SWIPE_AREA_ITEM = 2 | ListItemGroup的ListItem区域。 |
| ARKUI_LIST_ITEM_SWIPE_AREA_HEADER = 3 | ListItemGroup的header区域。 |
| ARKUI_LIST_ITEM_SWIPE_AREA_FOOTER = 4 | ListItemGroup的footer区域。 |

### ArkUI_KeyboardAvoidMode

```c
enum ArkUI_KeyboardAvoidMode
```

**描述：**


键盘避让模式。

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_KEYBOARD_AVOID_MODE_DEFAULT = 0 | 默认避让软键盘并在到达极限高度之后进行高度压缩。 |
| ARKUI_KEYBOARD_AVOID_MODE_NONE = 1 | 不避让键盘。 |

### ArkUI_HoverModeAreaType

```c
enum ArkUI_HoverModeAreaType
```

**描述：**


悬停态显示区域。

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_HOVER_MODE_AREA_TYPE_TOP = 0 | 上半屏。 |
| ARKUI_HOVER_MODE_AREA_TYPE_BOTTOM = 1 | 下半屏。 |

### ArkUI_ExpandMode

```c
enum ArkUI_ExpandMode
```

**描述：**


定义子节点展开模式枚举值。

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_NOT_EXPAND = 0 | 不展开。 |
| ARKUI_EXPAND = 1 | 展开。 |
| ARKUI_LAZY_EXPAND = 2 | 懒展开，按需展开当前节点的子节点，节点展开条件可以参考[LazyForEach：数据懒加载](../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)。 |

### ArkUI_FocusWrapMode

```c
enum ArkUI_FocusWrapMode
```

**描述：**


组件走焦换行规则。Grid、List组件默认值为ARKUI_FOCUS_WRAP_MODE_DEFAULT。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_FOCUS_WRAP_MODE_DEFAULT = 0 | 默认规则，使用方向键走焦不换行。 |
| ARKUI_FOCUS_WRAP_WITH_ARROW = 1 | 使用方向键走焦自动换行。 |

### ArkUI_ItemFillPolicy

```c
enum ArkUI_ItemFillPolicy
```

**描述：**


为不同响应式[断点规格](../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)指定列数。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ITEMFILLPOLICY_NONE = -1 | 没有设置响应式断点规格。 |
| ARKUI_ITEMFILLPOLICY_DEFAULT = 0 | 针对List和Swiper组件：在组件宽度属于sm及更小的断点区间时显示1列，属于md断点区间时显示2列，属于lg及更大的断点区间时显示3列。<br> 针对Grid和WaterFlow组件：在组件宽度属于sm及更小的断点区间时显示2列，属于md断点区间时显示3列，属于lg及更大的断点区间时显示5列。 |
| ARKUI_ITEMFILLPOLICY_SM1MD2LG3 = 1 | 在组件宽度属于sm及更小的断点区间时显示1列，属于md断点区间时显示2列，属于lg及更大的断点区间时显示3列。 |
| ARKUI_ITEMFILLPOLICY_SM2MD3LG5 = 2 | 在组件宽度属于sm及更小的断点区间时显示2列，属于md断点区间时显示3列，属于lg及更大的断点区间时显示5列。 |

### ArkUI_ScrollSnapAnimationSpeed

```c
enum ArkUI_ScrollSnapAnimationSpeed
```

**描述：**


列表限位滚动动画速度。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_SNAP_ANIMATION_NORMAL = 0 | 限位滚动动画速度正常。 |
| ARKUI_SCROLL_SNAP_ANIMATION_SLOW = 1 | 限位滚动动画速度慢。 |

### ArkUI_EdgeDirection

```c
enum ArkUI_EdgeDirection
```

**描述：**


定义矩形边方向。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_EDGE_DIRECTION_ALL = 0 | 设置四个方向的内容。 |
| ARKUI_EDGE_DIRECTION_LEFT = 1 << 0 | 设置左侧方向内容。 |
| ARKUI_EDGE_DIRECTION_RIGHT = 1 << 1 | 设置右侧方向内容。 |
| ARKUI_EDGE_DIRECTION_TOP = 1 << 2 | 设置上侧方向内容。 |
| ARKUI_EDGE_DIRECTION_BOTTOM = 1 << 3 | 设置下侧方向内容。 |

### ArkUI_CornerDirection

```c
enum ArkUI_CornerDirection
```

**描述：**


定义角度方向。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CORNER_DIRECTION_ALL = 0 | 设置四个角度方向的内容。 |
| ARKUI_CORNER_DIRECTION_TOP_LEFT = 1 << 0 | 设置左上侧方向内容。 |
| ARKUI_CORNER_DIRECTION_TOP_RIGHT = 1 << 1 | 设置右上侧方向内容。 |
| ARKUI_CORNER_DIRECTION_BOTTOM_LEFT = 1 << 2 | 设置左下侧方向内容。 |
| ARKUI_CORNER_DIRECTION_BOTTOM_RIGHT = 1 << 3 | 设置右下侧方向容。 |

### ArkUI_GridItemAlignment

```c
enum ArkUI_GridItemAlignment
```
**描述：**

[GridItem](../apis-arkui/arkui-ts/ts-container-griditem.md)对齐方式枚举。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| GRID_ITEM_ALIGNMENT_DEFAULT = 0 | Grid的默认对齐方式。 |
| GRID_ITEM_ALIGNMENT_STRETCH  = 1  | 以一行中的最高的GridItem作为其他GridItem的高度。 |


### ArkUI_GridItemStyle

```c
enum ArkUI_GridItemStyle
```

**描述：**


GridItem样式枚举。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| GRID_ITEM_STYLE_NONE  = 0 | 无样式。 |
| GRID_ITEM_STYLE_PLAIN  = 1  | 显示Hover、Press态样式。 |

### ArkUI_MenuPolicy

```c
enum ArkUI_MenuPolicy
```

**描述：**

菜单弹出策略。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_MENU_POLICY_DEFAULT  = 0 | 根据底层默认逻辑确定是否弹出菜单。 |
| ARKUI_MENU_POLICY_HIDE = 1 | 不弹出菜单。 |
| ARKUI_MENU_POLICY_SHOW = 2 | 弹出菜单。 |

### ArkUI_TextMenuItemId

```c
enum ArkUI_TextMenuItemId
```

**描述**

文本菜单项id枚举。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_MENU_ITEM_ID_CUT = 0 | 裁剪。 |
| ARKUI_TEXT_MENU_ITEM_ID_COPY = 1 | 复制。 |
| ARKUI_TEXT_MENU_ITEM_ID_PASTE = 2 | 粘贴。 |
| ARKUI_TEXT_MENU_ITEM_ID_SELECT_ALL = 3 | 全选。 |
| ARKUI_TEXT_MENU_ITEM_ID_COLLABORATION_SERVICE = 4 | 互通服务。例如跨设备交互，包括跨设备的相机访问等能力。 |
| ARKUI_TEXT_MENU_ITEM_ID_CAMERA_INPUT = 5 | 拍摄输入。 |
| ARKUI_TEXT_MENU_ITEM_ID_AI_WRITER = 6 | AI帮写。该菜单项依赖大模型能力，否则不生效。 |
| ARKUI_TEXT_MENU_ITEM_ID_TRANSLATE = 7 | 翻译。对选中的文本提供翻译服务。 |
| ARKUI_TEXT_MENU_ITEM_ID_SEARCH = 8 | 搜索。对选中的文本提供搜索服务，拉起浏览器搜索选中文本内容。 |
| ARKUI_TEXT_MENU_ITEM_ID_SHARE = 9 | 分享。对选中的文本提供分享服务，拉起分享窗口分享选中文本内容。 |
| ARKUI_TEXT_MENU_ITEM_ID_URL = 10 | 打开链接。对选中的URL提供跳转服务，拉起浏览器搜索或者应用页面。 |
| ARKUI_TEXT_MENU_ITEM_ID_EMAIL = 11 | 新建邮件。对选中的邮箱地址提供跳转服务，拉起邮箱应用。 |
| ARKUI_TEXT_MENU_ITEM_ID_PHONE_NUMBER = 12 | 呼叫。对选中的电话号码跳转服务，拉起电话拨号页面。 |
| ARKUI_TEXT_MENU_ITEM_ID_ADDRESS = 13 | 导航前往。对选中的地址提供跳转服务，拉起地图应用。 |
| ARKUI_TEXT_MENU_ITEM_ID_DATA_TIME = 14 | 新建日程。对选中的日期和时间提供跳转服务，拉起新建日程页面。 |
| ARKUI_TEXT_MENU_ITEM_ID_ASK_AI = 15 | 问问AI。对选中的文本提供AI问询能力。 |
| ARKUI_TEXT_MENU_ITEM_ID_AUTO_FILL = 16 | 自动填充。例如自动填充账号密码。<br>**起始版本：** 24 |
| ARKUI_TEXT_MENU_ITEM_ID_PASSWORD_VAULT = 17 | 密码保险箱。<br>**起始版本：** 24 |
| ARKUI_TEXT_MENU_ITEM_ID_APP_RESERVED_BEGIN = 10000 | 应用自定义菜单项起始id，除了系统内置的菜单项id，应用还可以自定义菜单项id。 |
| ARKUI_TEXT_MENU_ITEM_ID_APP_RESERVED_END = 20000 | 应用自定义菜单项结束id，除了系统内置的菜单项id，应用还可以自定义菜单项id。 |

### ArkUI_TextSpanType

```c
enum ArkUI_TextSpanType
```

**描述**

自定义文本选择菜单的文本识别类型枚举。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_SPAN_TYPE_TEXT = 0 | 选中文本内容为文字类型。 |
| ARKUI_TEXT_SPAN_TYPE_IMAGE = 1 | 选中文本内容为图像类型。 |
| ARKUI_TEXT_SPAN_TYPE_MIXED = 2 | 选中文本内容为图文混合类型。 |
| ARKUI_TEXT_SPAN_TYPE_DEFAULT = 3 | 如果设置为此类型且设置了其他类型时，选中文本后会显示与选中文本内容类型对应的菜单。如果设置为此类型但其他类型未设置时，选中文本后会显示此类型对应的菜单。例如，同时设置了文本识别类型为ARKUI_TEXT_SPAN_TYPE_TEXT、ARKUI_TEXT_SPAN_TYPE_DEFAULT的两个菜单，此时选中文本内容为文字类型会触发ARKUI_TEXT_SPAN_TYPE_TEXT对应的菜单弹出，选中文本内容为图像类型则会触发ARKUI_TEXT_SPAN_TYPE_DEFAULT对应的菜单弹出。 |

### ArkUI_TextResponseType

```c
enum ArkUI_TextResponseType
```

**描述**

自定义文本选择菜单的响应类型枚举。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXT_RESPONSE_TYPE_RIGHT_CLICK = 0 | 通过鼠标右键触发菜单弹出。 |
| ARKUI_TEXT_RESPONSE_TYPE_LONG_PRESS = 1 | 通过长按触发菜单弹出。 |
| ARKUI_TEXT_RESPONSE_TYPE_SELECT = 2 | 通过鼠标选中触发菜单弹出。 |
| ARKUI_TEXT_RESPONSE_TYPE_DEFAULT = 3 | 如果设置为此类型且设置了其他类型时，触发其他类型的操作会显示对应类型的菜单。如果设置为此类型但其他类型未设置时，触发其他类型的操作会显示此类型对应的菜单。例如，同时设置了响应类型为ARKUI_TEXT_RESPONSE_TYPE_RIGHT_CLICK、ARKUI_TEXT_RESPONSE_TYPE_DEFAULT的两个菜单，此时通过鼠标右键会触发ARKUI_TEXT_RESPONSE_TYPE_RIGHT_CLICK对应的菜单弹出，长按则会触发ARKUI_TEXT_RESPONSE_TYPE_DEFAULT对应的菜单弹出。 |

### ArkUI_MarqueeStartPolicy
```c
enum ArkUI_MarqueeStartPolicy
```

**描述：**

定义跑马灯启动策略枚举。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_MARQUEESTARTPOLICY_DEFAULT = 0 | 默认持续滚动。 |
| ARKUI_MARQUEESTARTPOLICY_ONFOCUS = 1 | 获焦以及鼠标悬浮时开始滚动。|

### ArkUI_MarqueeUpdatePolicy
```c
enum ArkUI_MarqueeUpdatePolicy
```

**描述：**

定义跑马灯更新策略枚举。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_MARQUEEUPDATEPOLICY_DEFAULT = 0 | 跑马灯组件属性更新后，从开始位置，运行跑马灯效果。 |
| ARKUI_MARQUEEUPDATEPOLICY_PRESERVEPOSITION = 1 | 跑马灯组件属性更新后，保持当前位置，运行跑马灯效果。|

### ArkUI_RenderStrategy

```c
enum ArkUI_RenderStrategy
```

**描述：**


定义组件绘制圆角的模式。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_RENDERSTRATEGY_FAST  = 0 | 在线绘制模式。 |
| ARKUI_RENDERSTRATEGY_OFFSCREEN = 1 | 离屏绘制模式。 |

### OH_ArkUI_HapticFeedbackMode

```c
enum OH_ArkUI_HapticFeedbackMode
```

**描述**

震动效果类型枚举。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_HAPTIC_FEEDBACK_MODE_DISABLED = 0 | 无震动效果。 |
| OH_ARKUI_HAPTIC_FEEDBACK_MODE_ENABLED = 1 | 有震动效果。 |
| OH_ARKUI_HAPTIC_FEEDBACK_MODE_AUTO = 2 | 跟随系统的震动效果。 |

### OH_ArkUI_TextEditorSpanType

```c
enum OH_ArkUI_TextEditorSpanType
```

**描述**

自定义文本选择菜单span类型枚举。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_TEXT = 0 | 文本span |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_IMAGE = 1 | 图片span。 |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_MIXED = 2 | 混合span。 |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_BUILDER = 3 | 自定义布局span。 |
| OH_ARKUI_TEXT_EDITOR_SPAN_TYPE_DEFAULT = 4 | 默认span。 |

### OH_ArkUI_TextEditorResponseType

```c
enum OH_ArkUI_TextEditorResponseType
```

**描述**

自定义文本选择菜单响应类型枚举。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_RIGHT_CLICK = 0 | 通过鼠标右键触发菜单弹出。 |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_LONG_PRESS = 1 | 通过长按触发菜单弹出。 |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_SELECT = 2 | 通过鼠标选中触发菜单弹出。 |
| OH_ARKUI_TEXT_EDITOR_RESPONSE_TYPE_DEFAULT = 3 | 默认响应类型。 |

### OH_ArkUI_TextMenuType

```c
enum OH_ArkUI_TextMenuType
```

**描述**

文本菜单类型枚举。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_TEXT_EDITOR_SELECTION_MENU = 0 | 文本选择菜单。 |
| OH_ARKUI_TEXT_EDITOR_PREVIEW_MENU = 1 | 预览菜单。 |

### OH_ArkUI_LineBreakStrategy

```c
enum OH_ArkUI_LineBreakStrategy
```

**描述**

换行策略类型枚举。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_LINE_BREAK_STRATEGY_GREEDY = 0 | 贪婪模式。<br>使每一行尽可能显示多的字符，直到这一行不能显示更多字符时进行折行。 |
| OH_ARKUI_LINE_BREAK_STRATEGY_HIGH_QUALITY = 1 | 高质量模式。<br>在平衡模式的基础上，尽可能填满行，同时最后一行的权重较低，可能出现最后一行留白较多的情形。 |
| OH_ARKUI_LINE_BREAK_STRATEGY_BALANCE = 2 | 平衡模式。<br>在不拆词的情况下，尽量使一个段落中每一行的宽度相同。 |

### ArkUI_RawInputEventType

```c
enum ArkUI_RawInputEventType
```

**描述**

原始输入事件类型枚举。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_RAW_INPUT_EVENT_TYPE_TOUCH = 0 | 触摸事件类型。 |
| ARKUI_RAW_INPUT_EVENT_TYPE_MOUSE = 1 | 鼠标事件类型。 |

### OH_ArkUI_CrossLanguageOperatingStatus

```c
enum OH_ArkUI_CrossLanguageOperatingStatus
```

**描述**

跨语言配置项的节点树操作状态。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_TREE_OPERATING_STATUS_UNDEFINED = 0 | 未定义，节点树操作状态的初始值。处于此状态的节点不支持跨语言节点树操作。 |
| OH_ARKUI_TREE_OPERATING_STATUS_ENABLE = 1 | 启用，表示当该配置项应用到节点时，节点的节点树操作状态将被启用。 |
| OH_ARKUI_TREE_OPERATING_STATUS_DISABLE = 2 | 禁用，表示当该配置项应用到节点时，节点的节点树操作状态将被禁用。 |

### OH_ArkUI_NodeMountPolicy

```c
enum OH_ArkUI_NodeMountPolicy
```
**描述**

子节点挂载策略类型枚举。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NODE_MOUNT_POLICY_SINGLE_IF_RENDER_NODE = 0 | 如果需要将[RenderNode](./js-apis-arkui-renderNode.md)作为子节点挂载，此RenderNode必须是唯一子节点。 |
| OH_ARKUI_NODE_MOUNT_POLICY_MIXED = 1 | 允许同时挂载多个[typeNode](./js-apis-arkui-frameNode.md#typenode12)与RenderNode。 |

## 函数说明

### OH_ArkUI_LayoutConstraint_Create()

```c
ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Create()
```

**描述：**


创建布局约束。

**起始版本：** 12

**返回：**

| 类型                          | 说明 |
|-----------------------------| -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* | 创建布局约束的指针。 |

### OH_ArkUI_LayoutConstraint_Copy()

```c
ArkUI_LayoutConstraint* OH_ArkUI_LayoutConstraint_Copy(const ArkUI_LayoutConstraint* Constraint)
```

**描述：**


布局约束深拷贝。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |

**返回：**

| 类型                          | 说明 |
|-----------------------------| -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* | 新的布局约束指针。 |

### OH_ArkUI_LayoutConstraint_Dispose()

```c
void* OH_ArkUI_LayoutConstraint_Dispose(ArkUI_LayoutConstraint* Constraint)
```

**描述：**


销毁布局约束指针。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |

**返回：**

| 类型                          | 说明 |
|-----------------------------| -- |
| void* | 空指针。 |

### OH_ArkUI_LayoutConstraint_GetMaxWidth()

```c
int32_t OH_ArkUI_LayoutConstraint_GetMaxWidth(const ArkUI_LayoutConstraint* Constraint)
```

**描述：**


通过布局约束获取最大宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 最大宽度，单位为px。 |

### OH_ArkUI_LayoutConstraint_GetMinWidth()

```c
int32_t OH_ArkUI_LayoutConstraint_GetMinWidth(const ArkUI_LayoutConstraint* Constraint)
```

**描述：**


通过布局约束获取最小宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 最小宽度，单位为px。 |

### OH_ArkUI_LayoutConstraint_GetMaxHeight()

```c
int32_t OH_ArkUI_LayoutConstraint_GetMaxHeight(const ArkUI_LayoutConstraint* Constraint)
```

**描述：**


通过布局约束获取最大高度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 最大高度，单位为px。 |

### OH_ArkUI_LayoutConstraint_GetMinHeight()

```c
int32_t OH_ArkUI_LayoutConstraint_GetMinHeight(const ArkUI_LayoutConstraint* Constraint)
```

**描述：**


通过布局约束获取最小高度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 最小高度，单位为px。 |

### OH_ArkUI_LayoutConstraint_GetPercentReferenceWidth()

```c
int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceWidth(const ArkUI_LayoutConstraint* Constraint)
```

**描述：**


通过布局约束获取宽度百分比基准。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 宽度百分比基准。 |

### OH_ArkUI_LayoutConstraint_GetPercentReferenceHeight()

```c
int32_t OH_ArkUI_LayoutConstraint_GetPercentReferenceHeight(const ArkUI_LayoutConstraint* Constraint)
```

**描述：**


通过布局约束获取高度百分比基准。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 高度百分比基准。 |

### OH_ArkUI_LayoutConstraint_SetMaxWidth()

```c
void OH_ArkUI_LayoutConstraint_SetMaxWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**描述：**


设置最大宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |
| int32_t value | 最大宽度，单位为px，取值范围：[0, +∞)。 |

### OH_ArkUI_LayoutConstraint_SetMinWidth()

```c
void OH_ArkUI_LayoutConstraint_SetMinWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**描述：**


设置最小宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |
| int32_t value | 最小宽度，单位为px，取值范围：[0, +∞)。 |

### OH_ArkUI_LayoutConstraint_SetMaxHeight()

```c
void OH_ArkUI_LayoutConstraint_SetMaxHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**描述：**


设置最大高度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |
| int32_t value | 最大高度，单位为px，取值范围：[0, +∞)。 |

### OH_ArkUI_LayoutConstraint_SetMinHeight()

```c
void OH_ArkUI_LayoutConstraint_SetMinHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**描述：**


设置最小高度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |
| int32_t value | 最小高度，单位为px，取值范围：[0, +∞)。 |

### OH_ArkUI_LayoutConstraint_SetPercentReferenceWidth()

```c
void OH_ArkUI_LayoutConstraint_SetPercentReferenceWidth(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**描述：**


设置宽度百分比基准。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |
| int32_t value | 宽度百分比基准，取值范围：[0, +∞)。 |

### OH_ArkUI_LayoutConstraint_SetPercentReferenceHeight()

```c
void OH_ArkUI_LayoutConstraint_SetPercentReferenceHeight(ArkUI_LayoutConstraint* Constraint, int32_t value)
```

**描述：**


设置高度百分比基准。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md)* Constraint | 布局约束的指针。 |
| int32_t value | 高度百分比基准，取值范围：[0, +∞)。 |

### OH_ArkUI_DrawContext_GetCanvas()

```c
void* OH_ArkUI_DrawContext_GetCanvas(ArkUI_DrawContext* context)
```

**描述：**


获取绘制canvas指针，可以转换为图形库的[OH_Drawing_Canvas](../apis-arkgraphics2d/capi-drawing-oh-drawing-canvas.md)指针进行绘制。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawContext](capi-arkui-nativemodule-arkui-drawcontext.md)* context | 绘制上下文。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | 用于绘制的canvas指针。 |

### OH_ArkUI_DrawContext_GetSize()

```c
ArkUI_IntSize OH_ArkUI_DrawContext_GetSize(ArkUI_DrawContext* context)
```

**描述：**


获取可绘制区域大小。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawContext](capi-arkui-nativemodule-arkui-drawcontext.md)* context | 绘制上下文。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md) | 可绘制区域大小。 |

### OH_ArkUI_WaterFlowSectionOption_Create()

```c
ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create()
```

**描述：**


创建[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息。

**起始版本：** 12

**返回：**

| 类型                                | 说明 |
|-----------------------------------| -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息。 |

### OH_ArkUI_WaterFlowSectionOption_Dispose()

```c
void OH_ArkUI_WaterFlowSectionOption_Dispose(ArkUI_WaterFlowSectionOption* option)
```

**描述：**


销毁[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息指针。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息。 |

### OH_ArkUI_WaterFlowSectionOption_SetSize()

```c
void OH_ArkUI_WaterFlowSectionOption_SetSize(ArkUI_WaterFlowSectionOption* option,int32_t size)
```

**描述：**


设置FlowItem分组配置信息数组长度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t size | 数组长度。 |

### OH_ArkUI_WaterFlowSectionOption_GetSize()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetSize(ArkUI_WaterFlowSectionOption* option)
```

**描述：**


获取[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息数组长度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 数组长度。如果返回-1，则返回失败。失败的原因可能是option参数异常，如空指针。 |

### OH_ArkUI_WaterFlowSectionOption_SetItemCount()

```c
void OH_ArkUI_WaterFlowSectionOption_SetItemCount(ArkUI_WaterFlowSectionOption* option,int32_t index, int32_t itemCount)
```

**描述：**


设置分组中[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)数量。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |
| int32_t itemCount | 分组中[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)数量。 |

### OH_ArkUI_WaterFlowSectionOption_GetItemCount()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述：**


通过[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息获取对应索引下的[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)数量。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 分组中FlowItem数量。 |

### OH_ArkUI_WaterFlowSectionOption_SetCrossCount()

```c
void OH_ArkUI_WaterFlowSectionOption_SetCrossCount(ArkUI_WaterFlowSectionOption* option,int32_t index, int32_t crossCount)
```

**描述：**


设置布局栅格，纵向布局时为列数，横向布局时为行数。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |
| int32_t crossCount | 布局栅格数量。 |

### OH_ArkUI_WaterFlowSectionOption_GetCrossCount()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述：**


通过[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息获取对应索引下的布局栅格数。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 布局栅格数量。 |

### OH_ArkUI_WaterFlowSectionOption_SetColumnGap()

```c
void OH_ArkUI_WaterFlowSectionOption_SetColumnGap(ArkUI_WaterFlowSectionOption* option,int32_t index, float columnGap)
```

**描述：**


设置分组的列间距。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |
| float columnGap | 列间距。单位：vp。 |

### OH_ArkUI_WaterFlowSectionOption_GetColumnGap()

```c
float OH_ArkUI_WaterFlowSectionOption_GetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述：**


通过FlowItem分组配置信息获取对应索引下的分组的列间距。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 列间距。单位：vp。 |

### OH_ArkUI_WaterFlowSectionOption_SetRowGap()

```c
void OH_ArkUI_WaterFlowSectionOption_SetRowGap(ArkUI_WaterFlowSectionOption* option,int32_t index, float rowGap)
```

**描述：**


设置FlowItem分组的行间距。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | FlowItem分组配置信息数组索引值。 |
| float rowGap | 行间距。单位：vp。 |

### OH_ArkUI_WaterFlowSectionOption_GetRowGap()

```c
float OH_ArkUI_WaterFlowSectionOption_GetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述：**


通过[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息获取对应索引下的分组的行间距。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 行间距。单位：vp。 |

### OH_ArkUI_WaterFlowSectionOption_SetMargin()

```c
void OH_ArkUI_WaterFlowSectionOption_SetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index,float marginTop, float marginRight, float marginBottom, float marginLeft)
```

**描述：**


设置分组的外边距。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |
| float marginTop | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)上外边距。 |
| float marginRight | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)右外边距。 |
| float marginBottom | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)下外边距。 |
| float marginLeft | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)左外边距。 |

### OH_ArkUI_WaterFlowSectionOption_GetMargin()

```c
ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述：**


通过[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息获取对应索引下的分组的外边距。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) | 外边距。单位：vp。 |

### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex()

```c
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex(ArkUI_WaterFlowSectionOption* option,int32_t index, float(*callback)(int32_t itemIndex))
```

**描述：**


通过[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息根据itemIndex获取指定FlowItem的主轴大小。如需在回调中使用自定义数据，可使用[OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata)。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述 |
|------------------------------------------------| -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息。 |
| int32_t index                                  | 分组配置信息数组索引值。 |
| callback                                       | 根据index获取指定Item的主轴大小。itemIndex：[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)索引值。 |

### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData()

```c
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData(ArkUI_WaterFlowSectionOption* option, int32_t index, void* userData,float (*callback)(int32_t itemIndex, void* userData))
```

**描述：**


通过[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息根据itemIndex获取指定Item的主轴大小。与[OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex)的区别在于，该接口支持传入自定义数据userData，并在回调函数中接收该数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |
|  void* userData |用户自定义数据指针，将在回调函数中回传给用户。 |
| callback | 根据index获取指定Item的主轴大小。itemIndex：[FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md)索引值；userData：用户自定义数据。 |


### OH_ArkUI_SwiperDigitIndicator_SetFontWeight()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontWeight(ArkUI_SwiperDigitIndicator *indicator, ArkUI_FontWeight fontWeight)
```

**描述：**


设置Swiper组件数字导航指示器字体粗细属性。

**起始版本：** 19


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) *indicator | 数字导航指示器对象指针。 |
| [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight) fontWeight | 字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)。 |

### OH_ArkUI_SwiperDigitIndicator_GetFontWeight()

```c
ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetFontWeight(ArkUI_SwiperDigitIndicator* indicator)
```

**描述：**


获取Swiper组件数字导航指示器字体粗细属性。

**起始版本：** 19


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight) | 字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)。 |

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontWeight()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontWeight(ArkUI_SwiperDigitIndicator *indicator, ArkUI_FontWeight selectedFontWeight)
```

**描述：**


设置被选中Swiper组件数字导航指示器字体粗细属性。

**起始版本：** 19


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) *indicator | 数字导航指示器对象指针。 |
| [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight) selectedFontWeight | 字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)。 |

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontWeight()

```c
ArkUI_FontWeight OH_ArkUI_SwiperDigitIndicator_GetSelectedFontWeight(ArkUI_SwiperDigitIndicator* indicator)
```

**描述：**


获取被选中Swiper组件数字导航指示器字体粗细属性。

**起始版本：** 19


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight) | 字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)。 |

### OH_ArkUI_ListItemSwipeActionItem_Create()

```c
ArkUI_ListItemSwipeActionItem* OH_ArkUI_ListItemSwipeActionItem_Create()
```

**描述：**


创建ListItemSwipeActionItem接口设置的配置项。

**起始版本：** 12

**返回：**

| 类型                                 | 说明 |
|------------------------------------| -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* | ListItemSwipeActionItem配置项实例。 |

### OH_ArkUI_ListItemSwipeActionItem_Dispose()

```c
void OH_ArkUI_ListItemSwipeActionItem_Dispose(ArkUI_ListItemSwipeActionItem* item)
```

**描述：**


销毁ListItemSwipeActionItem实例。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | 要销毁的ListItemSwipeActionItem实例。 |

### OH_ArkUI_ListItemSwipeActionItem_SetContent()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetContent(ArkUI_ListItemSwipeActionItem* item, ArkUI_NodeHandle node)
```

**描述：**


设置ListItemSwipeActionItem的布局内容。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 布局信息。 |

### OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item, float distance)
```

**描述：**


设置组件长距离滑动删除距离阈值。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |
| float distance | 组件长距离滑动删除距离阈值，单位vp。 |

### OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance()

```c
float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item)
```

**描述：**


获取组件长距离滑动删除距离阈值。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 组件长距离滑动删除距离阈值，单位vp，异常时返回值：0。 |

### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**描述：**


设置滑动条目进入删除区域时调用的事件。

**起始版本：** 12


**参数：**

| 参数项                                     | 描述 |
|-----------------------------------------| -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |
| callback                                | 回调事件。 |

### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item,void* userData, void (*callback)(void* userData))
```

**描述：**


设置滑动条目进入删除区域时调用的事件，回调事件会传入用户自定义数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |
| void* userData | 用户自定义数据。 |
| callback | 回调事件。 |

### OH_ArkUI_ListItemSwipeActionItem_SetOnAction()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnAction(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**描述：**


设置组件进入长距删除区后删除[ListItem](./arkui-ts/ts-container-listitem.md)时调用的事件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |
| callback | 回调事件。 |

### OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData(ArkUI_ListItemSwipeActionItem* item,void* userData, void (*callback)(void* userData))
```

**描述：**


设置组件进入长距删除区后删除ListItem时调用的事件，回调事件会传入用户自定义数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |
| void* userData | 用户自定义数据。 |
| callback | 回调事件。 |

### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**描述：**


设置滑动条目退出删除区域时调用的事件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |
| callback | 回调事件。 |

### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item,void* userData, void (*callback)(void* userData))
```

**描述：**


设置滑动条目退出删除区域时调用的事件，回调事件会传入用户自定义数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |
| void* userData | 用户自定义数据。 |
| callback | 回调事件。 |

### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange(ArkUI_ListItemSwipeActionItem* item,void (*callback)(ArkUI_ListItemSwipeActionState swipeActionState))
```

**描述：**


设置列表项滑动状态变化时候触发的事件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |
| callback | 回调事件。传入参数为swipeActionState，表示列表项滑动状态。 |

### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData(ArkUI_ListItemSwipeActionItem* item,void* userData, void (*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void* userData))
```

**描述：**


设置列表项滑动状态变化时候触发的事件，回调事件会传入用户自定义数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |
|  void* userData | 用户自定义数据。 |
| callback | 回调事件。传入参数为swipeActionState，表示列表项滑动状态。 |

### OH_ArkUI_ListItemSwipeActionOption_Create()

```c
ArkUI_ListItemSwipeActionOption* OH_ArkUI_ListItemSwipeActionOption_Create()
```

**描述：**


创建ListItemSwipeActionOption接口设置的配置项。

**起始版本：** 12

**返回：**

| 类型                                   | 说明 |
|--------------------------------------| -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* | ListItemSwipeActionOption配置项实例。 |

### OH_ArkUI_ListItemSwipeActionOption_Dispose()

```c
void OH_ArkUI_ListItemSwipeActionOption_Dispose(ArkUI_ListItemSwipeActionOption* option)
```

**描述：**


销毁ListItemSwipeActionOption实例。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | 要销毁的ListItemSwipeActionOption实例。 |

### OH_ArkUI_ListItemSwipeActionOption_SetStart()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetStart(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)
```

**描述：**


设置ListItemSwipeActionItem的左侧（垂直布局）或上方（横向布局）布局内容。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | ListItemSwipeActionItem实例。 |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | 布局信息。 |

### OH_ArkUI_ListItemSwipeActionOption_SetEnd()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetEnd(ArkUI_ListItemSwipeActionOption* option,ArkUI_ListItemSwipeActionItem* item)
```

**描述：**


设置ListItemSwipeActionItem的右侧（垂直布局）或下方（横向布局）布局内容。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | ListItemSwipeActionItem实例。 |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | 布局信息。 |

### OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect(ArkUI_ListItemSwipeActionOption* option,ArkUI_ListItemSwipeEdgeEffect edgeEffect)
```

**描述：**


设置边缘滑动效果。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | ListItemSwipeActionItem实例。 |
| [ArkUI_ListItemSwipeEdgeEffect](capi-native-type-h.md#arkui_listitemswipeedgeeffect) edgeEffect | 边缘滑动效果。 |

### OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect()

```c
int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect(ArkUI_ListItemSwipeActionOption* option)
```

**描述：**


获取边缘滑动效果。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | ListItemSwipeActionItem实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 边缘滑动效果。默认返回值：[ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING](#arkui_listitemswipeedgeeffect)。 |

### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange(ArkUI_ListItemSwipeActionOption* option,void (*callback)(float offset))
```

**描述：**


滑动操作偏移量更改时调用的事件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | ListItemSwipeActionItem实例。 |
| callback | 回调事件。offset 滑动偏移量，单位vp。 |

### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData(ArkUI_ListItemSwipeActionOption* option,void* userData, void (*callback)(float offset, void* userData))
```

**描述：**


滑动操作偏移量更改时调用的事件，回调事件会传入用户自定义数据。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | ListItemSwipeActionItem实例。 |
|  void* userData | 用户自定义数据。 |
| callback | 回调事件。offset 滑动偏移量，单位vp。 |

### OH_ArkUI_ListItemSwipeAction_Expand()

```c
int32_t OH_ArkUI_ListItemSwipeAction_Expand(ArkUI_NodeHandle node, ArkUI_ListItemSwipeActionDirection direction)
```

**描述：**

展开指定ListItem的划出菜单。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ListItem节点对象。 |
| [ArkUI_ListItemSwipeActionDirection](#arkui_listitemswipeactiondirection) direction | ListItem划出菜单的展开方向。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>         [ARKUI_ERROR_CODE_PARAM_ERROR](capi-native-type-h.md#arkui_errorcode) 传入的节点对象类型错误。<br>         [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) 传入的节点未挂载到组件树上。 |

> **说明：**
>
> - 如果List组件NODE_LIST_CACHED_COUNT属性设置显示预加载ListItem，List显示区域外已预加载完成的ListItem支持展开，否则List显示区域外节点不支持展开。

### OH_ArkUI_ListItemSwipeAction_Collapse()

```c
int32_t OH_ArkUI_ListItemSwipeAction_Collapse(ArkUI_NodeHandle node)
```

**描述：**

收起指定ListItem的划出菜单。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ListItem节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>         [ARKUI_ERROR_CODE_PARAM_ERROR](capi-native-type-h.md#arkui_errorcode) 传入的节点对象类型错误。<br>         [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-native-type-h.md#arkui_errorcode) 传入的节点未挂载到组件树上。 |

### OH_ArkUI_AccessibilityState_Create()

```c
ArkUI_AccessibilityState* OH_ArkUI_AccessibilityState_Create(void)
```

**描述：**


创建无障碍状态。

**起始版本：** 12

**返回：**

| 类型                            | 说明 |
|-------------------------------| -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* | 无障碍状态对象指针。如果对象返回空指针，表示创建失败，失败的可能原因是应用地址空间满。 |

### OH_ArkUI_AccessibilityState_Dispose()

```c
void OH_ArkUI_AccessibilityState_Dispose(ArkUI_AccessibilityState* state)
```

**描述：**


销毁无障碍状态指针。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | 无障碍状态对象指针。 |

### OH_ArkUI_AccessibilityState_SetDisabled()

```c
void OH_ArkUI_AccessibilityState_SetDisabled(ArkUI_AccessibilityState* state, int32_t isDisabled)
```

**描述：**


设置无障碍状态是否禁用。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | 无障碍状态对象指针。 |
| int32_t isDisabled | 无障碍状态是否禁用， 1表示禁用，0表示不禁用，默认为0。 |

### OH_ArkUI_AccessibilityState_IsDisabled()

```c
int32_t OH_ArkUI_AccessibilityState_IsDisabled(ArkUI_AccessibilityState* state)
```

**描述：**


获取无障碍状态是否禁用。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | 无障碍状态对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 是否禁用， 1表示禁用，0表示未禁用，默认为0;<br>         若state为空，返回默认值。 |

### OH_ArkUI_AccessibilityState_SetSelected()

```c
void OH_ArkUI_AccessibilityState_SetSelected(ArkUI_AccessibilityState* state, int32_t isSelected)
```

**描述：**


设置无障碍状态是否选中。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | 无障碍状态对象指针。 |
| int32_t isSelected | 是否被选中， 1表示选中，0表示未选中，默认为0。 |

### OH_ArkUI_AccessibilityState_IsSelected()

```c
int32_t OH_ArkUI_AccessibilityState_IsSelected(ArkUI_AccessibilityState* state)
```

**描述：**


获取无障碍状态是否选中。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | 无障碍状态对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 是否被选中， 1表示选中，0表示未选中，默认为0;<br>         若state为空，返回默认值。 |

### OH_ArkUI_AccessibilityState_SetCheckedState()

```c
void OH_ArkUI_AccessibilityState_SetCheckedState(ArkUI_AccessibilityState* state, int32_t checkedState)
```

**描述：**


设置无障碍状态复选框状态。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | 无障碍状态对象指针。 |
| int32_t checkedState | 复选框状态，参数类型[ArkUI_AccessibilityCheckedState](capi-native-type-h.md#arkui_accessibilitycheckedstate), 默认值：ARKUI_ACCESSIBILITY_UNCHECKED。 |

### OH_ArkUI_AccessibilityState_GetCheckedState()

```c
int32_t OH_ArkUI_AccessibilityState_GetCheckedState(ArkUI_AccessibilityState* state)
```

**描述：**


获取无障碍状态复选框状态。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)* state | 无障碍状态对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 复选框状态，参数类型[ArkUI_AccessibilityCheckedState](capi-native-type-h.md#arkui_accessibilitycheckedstate), 默认值：ARKUI_ACCESSIBILITY_UNCHECKED;<br>         若函数参数异常，返回默认值。 |

### OH_ArkUI_AccessibilityValue_Create()

```c
ArkUI_AccessibilityValue* OH_ArkUI_AccessibilityValue_Create(void)
```

**描述：**


创建无障碍信息。

**起始版本：** 12

**返回：**

| 类型                            | 说明 |
|-------------------------------| -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* | 无障碍信息对象指针。 |

### OH_ArkUI_AccessibilityValue_Dispose()

```c
void OH_ArkUI_AccessibilityValue_Dispose(ArkUI_AccessibilityValue* value)
```

**描述：**


销毁无障碍信息指针。

**起始版本：** 12


**参数：**

| 参数项                                                                                    | 描述 |
|----------------------------------------------------------------------------------------| -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 无障碍信息对象指针。 |

### OH_ArkUI_AccessibilityValue_SetMin()

```c
void OH_ArkUI_AccessibilityValue_SetMin(ArkUI_AccessibilityValue* value, int32_t min)
```

**描述：**


设置无障碍最小值信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 无障碍信息对象指针。 |
| int32_t min | 基于范围组件的最小值, 默认为-1。 |

### OH_ArkUI_AccessibilityValue_GetMin()

```c
int32_t OH_ArkUI_AccessibilityValue_GetMin(ArkUI_AccessibilityValue* value)
```

**描述：**


获取无障碍最小值信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 无障碍信息对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 基于范围组件的最小值, 默认为-1;<br>         若函数参数异常，返回-1。 |

### OH_ArkUI_AccessibilityValue_SetMax()

```c
void OH_ArkUI_AccessibilityValue_SetMax(ArkUI_AccessibilityValue* value, int32_t max)
```

**描述：**


设置无障碍最大值信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 无障碍信息对象指针。 |
| int32_t max | 基于范围组件的最大值, 默认为-1。 |

### OH_ArkUI_AccessibilityValue_GetMax()

```c
int32_t OH_ArkUI_AccessibilityValue_GetMax(ArkUI_AccessibilityValue* value)
```

**描述：**


获取无障碍最大值信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 无障碍信息对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 基于范围组件的最大值, 默认为-1;<br>         若函数参数异常，返回-1。 |

### OH_ArkUI_AccessibilityValue_SetCurrent()

```c
void OH_ArkUI_AccessibilityValue_SetCurrent(ArkUI_AccessibilityValue* value, int32_t current)
```

**描述：**


设置无障碍当前值信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 无障碍信息对象指针。 |
| int32_t current | 基于范围组件的当前值, 默认为-1。 |

### OH_ArkUI_AccessibilityValue_GetCurrent()

```c
int32_t OH_ArkUI_AccessibilityValue_GetCurrent(ArkUI_AccessibilityValue* value)
```

**描述：**


获取无障碍当前值信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 无障碍信息对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 基于范围组件的当前值, 默认为-1;<br>         若函数参数异常，返回-1。 |

### OH_ArkUI_AccessibilityValue_SetRangeMin()

```c
void OH_ArkUI_AccessibilityValue_SetRangeMin(ArkUI_AccessibilityValue* value, int32_t rangeMin)
```

**描述：**


设置范围组件的无障碍最小值信息。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 需要设置最小值的范围组件无障碍信息对象指针。 |
| int32_t rangeMin | 基于范围组件的最小值, 默认为-1。 |

### OH_ArkUI_AccessibilityValue_GetRangeMin()

```c
int32_t OH_ArkUI_AccessibilityValue_GetRangeMin(ArkUI_AccessibilityValue* value)
```

**描述：**


获取范围组件的无障碍最小值信息。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 需要获取最小值的范围组件无障碍信息对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 基于范围组件的最小值, 默认为-1;<br>         若函数参数异常，返回-1。 |

### OH_ArkUI_AccessibilityValue_SetRangeMax()

```c
void OH_ArkUI_AccessibilityValue_SetRangeMax(ArkUI_AccessibilityValue* value, int32_t rangeMax)
```

**描述：**


设置范围组件的无障碍最大值信息。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 需要设置最大值的范围组件无障碍信息对象指针。 |
| int32_t rangeMax | 基于范围组件的最大值, 默认为-1。 |

### OH_ArkUI_AccessibilityValue_GetRangeMax()

```c
int32_t OH_ArkUI_AccessibilityValue_GetRangeMax(ArkUI_AccessibilityValue* value)
```

**描述：**


获取范围组件的无障碍最大值信息。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 需要获取最小值的范围组件无障碍信息对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 基于范围组件的最大值, 默认为-1;<br>         若函数参数异常，返回-1。 |

### OH_ArkUI_AccessibilityValue_SetRangeCurrent()

```c
void OH_ArkUI_AccessibilityValue_SetRangeCurrent(ArkUI_AccessibilityValue* value, int32_t rangeCurrent)
```

**描述：**


用于设置范围组件的无障碍当前值信息。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 需要设置当前值的范围组件无障碍信息对象指针。 |
| int32_t rangeCurrent | 基于范围组件的当前值, 默认为-1。 |

### OH_ArkUI_AccessibilityValue_GetRangeCurrent()

```c
int32_t OH_ArkUI_AccessibilityValue_GetRangeCurrent(ArkUI_AccessibilityValue* value)
```

**描述：**


用于获取范围组件的无障碍当前值信息。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 需要获取当前值的范围组件无障碍信息对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 基于范围组件的当前值, 默认为-1;<br>         若函数参数异常，返回-1。 |

### OH_ArkUI_AccessibilityValue_SetText()

```c
void OH_ArkUI_AccessibilityValue_SetText(ArkUI_AccessibilityValue* value, const char* text)
```

**描述：**


设置无障碍文本描述信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 无障碍信息对象指针。 |
| const char* text | 组件的文本描述信息, 默认为空字符串。 |

### OH_ArkUI_AccessibilityValue_GetText()

```c
const char* OH_ArkUI_AccessibilityValue_GetText(ArkUI_AccessibilityValue* value)
```

**描述：**


获取无障碍文本描述信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)* value | 无障碍信息对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | 组件的文本描述信息, 默认为空字符串;<br>         若函数参数异常，返回空指针。 |

### OH_ArkUI_ListChildrenMainSizeOption_Create()

```c
ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()
```

**描述：**


创建ListChildrenMainSize接口设置的配置项。

**起始版本：** 12

**返回：**

| 类型                              | 说明 |
|---------------------------------| -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* | ListChildrenMainSize配置项实例。 |

### OH_ArkUI_ListChildrenMainSizeOption_Dispose()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)
```

**描述：**


销毁ListChildrenMainSize实例。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | 要销毁的ListChildrenMainSize实例。 |

### OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)
```

**描述：**


设置[List](./arkui-ts/ts-container-list.md)组件列表项在主轴方向的默认尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |
| float defaultMainSize | 列表项在主轴方向的默认尺寸值，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)
```

**描述：**


获取[List](./arkui-ts/ts-container-list.md)组件的列表项在主轴方向的默认尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 列表项在主轴方向的默认尺寸值，默认为0，单位为[vp](../apis-arkui/arkui-ts/ts-types.md#vp10)，option为空指针时返回-1。 |

### OH_ArkUI_ListChildrenMainSizeOption_Resize()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)
```

**描述：**


调整[List](./arkui-ts/ts-container-list.md)组件子项主轴尺寸数组的容量大小。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |
| int32_t totalSize | 目标数组容量大小。 |

### OH_ArkUI_ListChildrenMainSizeOption_Splice()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)
```

**描述：**


对[List](./arkui-ts/ts-container-list.md)组件子项主轴尺寸数组进行大小调整。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |
| int32_t index | 操作起始索引位置。 |
| int32_t deleteCount | 从起始位置开始删除的元素数量。 |
| int32_t addCount | 从起始位置开始新增的元素数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_ListChildrenMainSizeOption_UpdateSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)
```

**描述：**


更新[List](./arkui-ts/ts-container-list.md)组件子项主轴尺寸数组中指定索引位置的尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |
| int32_t index | 目标元素的数组索引位置。 |
| float mainSize | 要设置的主轴尺寸值，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_ListChildrenMainSizeOption_GetMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)
```

**描述：**


获取[List](./arkui-ts/ts-container-list.md)组件子项主轴尺寸数组中指定索引位置的尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |
| int32_t index | 目标元素的数组索引位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 数组具体位置的值。若函数参数异常，返回-1。 |

### OH_ArkUI_CustomSpanMeasureInfo_Create()

```c
ArkUI_CustomSpanMeasureInfo* OH_ArkUI_CustomSpanMeasureInfo_Create(void)
```

**描述：**


创建自定义段落组件测量信息。

**起始版本：** 12

**返回：**

| 类型                               | 说明 |
|----------------------------------| -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* | CustomSpanMeasureInfo实例。<br> 如果返回空指针，可能是因为内存不足。 |

### OH_ArkUI_CustomSpanMeasureInfo_Dispose()

```c
void OH_ArkUI_CustomSpanMeasureInfo_Dispose(ArkUI_CustomSpanMeasureInfo* info)
```

**描述：**


销毁自定义段落组件测量信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info |  自定义段落组件测量信息指针。 |

### OH_ArkUI_CustomSpanMeasureInfo_GetFontSize()

```c
float OH_ArkUI_CustomSpanMeasureInfo_GetFontSize(ArkUI_CustomSpanMeasureInfo* info)
```

**描述：**


获取自定义段落组件的父节点Text的字体大小。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info |  自定义段落组件测量信息指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 父节点Text的字体大小，单位为fp。若函数参数异常，返回0.0f。<br> 异常返回原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_CustomSpanMetrics_Create()

```c
ArkUI_CustomSpanMetrics* OH_ArkUI_CustomSpanMetrics_Create(void)
```

**描述：**


创建自定义段落组件度量信息。

**起始版本：** 12

**返回：**

| 类型                           | 说明 |
|------------------------------| -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* | CustomSpanMetrics实例。<br> 如果返回空指针，可能是因为内存不足。 |

### OH_ArkUI_CustomSpanMetrics_Dispose()

```c
void OH_ArkUI_CustomSpanMetrics_Dispose(ArkUI_CustomSpanMetrics* metrics)
```

**描述：**


销毁自定义段落组件度量信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | CustomSpanMetrics实例。 |

### OH_ArkUI_CustomSpanMetrics_SetWidth()

```c
int32_t OH_ArkUI_CustomSpanMetrics_SetWidth(ArkUI_CustomSpanMetrics* metrics, float width)
```

**描述：**


设置自定义段落组件的宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | CustomSpanMetrics实例。 |
| float width | 宽度大小，单位为vp。默认值为0.0f，负值与默认值效果一致。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>         异常原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_CustomSpanMetrics_SetHeight()

```c
int32_t OH_ArkUI_CustomSpanMetrics_SetHeight(ArkUI_CustomSpanMetrics* metrics, float height)
```

**描述：**


设置自定义段落组件的高度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | CustomSpanMetrics实例。 |
| float height | 高度大小，单位为vp。默认值为0.0f，负值与默认值效果一致。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>         异常原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_CustomSpanDrawInfo_Create()

```c
ArkUI_CustomSpanDrawInfo* OH_ArkUI_CustomSpanDrawInfo_Create(void)
```

**描述：**


创建自定义段落组件绘制信息。

**起始版本：** 12

**返回：**

| 类型                            | 说明 |
|-------------------------------| -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* | CustomSpanDrawInfo实例。<br> 如果返回空指针，可能是因为内存不足。 |

### OH_ArkUI_CustomSpanDrawInfo_Dispose()

```c
void OH_ArkUI_CustomSpanDrawInfo_Dispose(ArkUI_CustomSpanDrawInfo* info)
```

**描述：**


销毁自定义段落组件绘制信息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  自定义段落组件绘制信息指针。 |

### OH_ArkUI_CustomSpanDrawInfo_GetXOffset()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetXOffset(ArkUI_CustomSpanDrawInfo* info)
```

**描述：**


获取自定义段落组件相对于挂载组件的x轴偏移值。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  自定义段落组件绘制信息指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | x轴偏移值，单位为px。若函数参数异常，返回0.0f。<br> 异常返回原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_CustomSpanDrawInfo_GetLineTop()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetLineTop(ArkUI_CustomSpanDrawInfo* info)
```

**描述：**


获取自定义段落组件相对于挂载组件的上边距。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  自定义段落组件绘制信息指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 上边距值，单位为px。若函数参数异常，返回0.0f。<br> 异常返回原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_CustomSpanDrawInfo_GetLineBottom()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetLineBottom(ArkUI_CustomSpanDrawInfo* info)
```

**描述：**


获取自定义段落组件相对于挂载组件的下边距。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  自定义段落组件绘制信息指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 下边距值，单位为px。若函数参数异常，返回0.0f。<br> 异常返回原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_CustomSpanDrawInfo_GetBaseline()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetBaseline(ArkUI_CustomSpanDrawInfo* info)
```

**描述：**


获取自定义段落组件相对于挂载组件的基线偏移量。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  自定义段落组件绘制信息指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 基线偏移量值，单位为px。若函数参数异常，返回0.0f。<br> 异常返回原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_CustomProperty_Destroy()

```c
void OH_ArkUI_CustomProperty_Destroy(ArkUI_CustomProperty* handle)
```

**描述：**


销毁[ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md)实例。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md)* handle | 要销毁的实例。 |

### OH_ArkUI_CustomProperty_GetStringValue()

```c
const char* OH_ArkUI_CustomProperty_GetStringValue(ArkUI_CustomProperty* handle)
```

**描述：**


获取自定义属性对象的value信息。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CustomProperty](capi-arkui-nativemodule-arkui-customproperty.md)* handle | 自定义属性对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | 自定义属性对象的value信息。 |

### OH_ArkUI_HostWindowInfo_GetName()

```c
const char* OH_ArkUI_HostWindowInfo_GetName(ArkUI_HostWindowInfo* info)
```

**描述：**


获取[ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)对象中的窗口名称。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)* info | HostWindowInfo对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)对象中的窗口名称。 |

### OH_ArkUI_HostWindowInfo_Destroy()

```c
void OH_ArkUI_HostWindowInfo_Destroy(ArkUI_HostWindowInfo* info)
```

**描述：**


销毁[ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)对象。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)* info | 要销毁的[ArkUI_HostWindowInfo](capi-arkui-nativemodule-arkui-hostwindowinfo.md)对象。 |

### OH_ArkUI_ActiveChildrenInfo_Destroy()

```c
void OH_ArkUI_ActiveChildrenInfo_Destroy(ArkUI_ActiveChildrenInfo* handle)
```

**描述：**


销毁[ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)实例。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)* handle | 要销毁的[ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)实例。 |

### OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex()

```c
ArkUI_NodeHandle OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex(ArkUI_ActiveChildrenInfo* handle, int32_t index)
```

**描述：**


获取[ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)结构体的下标为index的子节点。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)* handle | 要获取信息的[ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)实例。 |
| int32_t index | 子节点的下标。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | 下标对应的子节点指针，异常时返回nullptr。 |

### OH_ArkUI_ActiveChildrenInfo_GetCount()

```c
int32_t OH_ArkUI_ActiveChildrenInfo_GetCount(ArkUI_ActiveChildrenInfo* handle)
```

**描述：**


获取[ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)结构体内的节点数量。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)* handle | 要获取信息的[ArkUI_ActiveChildrenInfo](capi-arkui-nativemodule-arkui-activechildreninfo.md)实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 子节点数量，默认值0. |

### OH_ArkUI_ProgressLinearStyleOption_Create()

```c
ArkUI_ProgressLinearStyleOption* OH_ArkUI_ProgressLinearStyleOption_Create(void)
```

**描述：**


创建线性进度条样式信息。

**起始版本：** 15

**返回：**

| 类型                                   | 说明 |
|--------------------------------------| -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* | ProgressLinearStyleOption实例。<br> 如果返回空指针，可能是因为内存不足。 |

### OH_ArkUI_ProgressLinearStyleOption_Destroy()

```c
void OH_ArkUI_ProgressLinearStyleOption_Destroy(ArkUI_ProgressLinearStyleOption* option)
```

**描述：**


销毁线性进度条样式信息。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | 线性进度条样式信息。 |

### OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)
```

**描述：**


设置进度平滑动效的开关。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | 线性进度条样式信息。 |
| bool enabled | 进度平滑动效的开关。开启平滑动效后设置进度，进度会从当前值渐变至设定值，否则进度从当前值突变至设定值。<br/>true：表示开启进度平滑动效。<br/>false：表示关闭进度平滑动效。<br/>默认值：true。 |

### OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)
```

**描述：**


设置扫光效果的开关。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | 线性进度条样式信息。 |
| bool enabled | 扫光效果的开关。<br/>true：表示开启扫光效果。<br/>false：表示关闭扫光效果。<br/>默认值：false。 |

### OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth(ArkUI_ProgressLinearStyleOption* option, float strokeWidth)
```

**描述：**


设置进度条宽度。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | 线性进度条样式信息。 |
| float strokeWidth | 进度条宽度值（不支持百分比设置），单位为vp，默认值：4.0vp。 |

### OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius(ArkUI_ProgressLinearStyleOption* option, float strokeRadius)
```

**描述：**


设置进度条圆角半径。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | 线性进度条样式信息。 |
| float strokeRadius | 进度条圆角半径值，单位为vp，取值范围[0, strokeWidth/2]。默认值：strokeWidth/2。 |

### OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled()

```c
bool OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option)
```

**描述：**


获取进度平滑动效的开关信息。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | 线性进度条样式信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 是否开启平滑动效。<br/>true：表示开启进度平滑动效。<br/>false：表示关闭进度平滑动效。<br/>默认值：true。 |

### OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled()

```c
bool OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option)
```

**描述：**


获取扫光效果的开关信息。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | 线性进度条样式信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 是否开启扫光效果。<br/>true：表示开启扫光效果。<br/>false：表示关闭扫光效果。<br/>默认值：false。 |

### OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth()

```c
float OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth(ArkUI_ProgressLinearStyleOption* option)
```

**描述：**


获取进度条宽度。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | 线性进度条样式信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 进度条宽度值，单位为vp。 |

### OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius()

```c
float OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius(ArkUI_ProgressLinearStyleOption* option)
```

**描述：**


获取进度条圆角半径值。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | 线性进度条样式信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 进度条圆角半径值，单位为vp。 |

### OH_ArkUI_CrossLanguageOption_Create()

```c
ArkUI_CrossLanguageOption* OH_ArkUI_CrossLanguageOption_Create(void)
```

**描述：**


创建跨语言配置项实例。

**起始版本：** 15

**返回：**

| 类型                             | 说明 |
|--------------------------------| -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* | 返回跨语言实例。如果对象返回空指针，则表示创建失败，失败的原因可能是地址空间已满。 |

### OH_ArkUI_CrossLanguageOption_Destroy()

```c
void OH_ArkUI_CrossLanguageOption_Destroy(ArkUI_CrossLanguageOption* option)
```

**描述：**


销毁跨语言配置项实例。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | 要销毁的跨语言配置项实例。 |

### OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus()

```c
void OH_ArkUI_CrossLanguageOption_SetAttributeSettingStatus(ArkUI_CrossLanguageOption* option, bool enabled)
```

**描述：**


设置配置项中是否允许跨语言修改属性。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | 跨语言配置项实例。 |
| bool enabled | 是否允许跨语言修改属性。true表示允许跨语言修改属性，false表示不允许跨语言修改属性，默认值：false。 |

### OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus()

```c
bool OH_ArkUI_CrossLanguageOption_GetAttributeSettingStatus(ArkUI_CrossLanguageOption* option)
```

**描述：**


获取配置项中是否允许跨语言修改属性。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | 跨语言配置项实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 是否允许跨语言修改属性。true表示允许跨语言修改属性，false表示不允许跨语言修改属性。 |

### OH_ArkUI_CrossLanguageOption_SetTreeOperatingStatus()

```c
void OH_ArkUI_CrossLanguageOption_SetTreeOperatingStatus(ArkUI_CrossLanguageOption* option, OH_ArkUI_CrossLanguageOperatingStatus status)
```

**描述：**

设置跨语言配置项的节点树操作状态。

**起始版本：** 26.0.0


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | 跨语言配置项实例。 |
| [OH_ArkUI_CrossLanguageOperatingStatus](#oh_arkui_crosslanguageoperatingstatus) status | 需要设置的节点树操作状态。 默认值：OH_ARKUI_TREE_OPERATING_STATUS_UNDEFINED。 |

### OH_ArkUI_CrossLanguageOption_GetTreeOperatingStatus()

```c
OH_ArkUI_CrossLanguageOperatingStatus OH_ArkUI_CrossLanguageOption_GetTreeOperatingStatus(ArkUI_CrossLanguageOption* option)
```

**描述：**

获取跨语言配置项的节点树操作状态。

**起始版本：** 26.0.0


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_CrossLanguageOption](capi-arkui-nativemodule-arkui-crosslanguageoption.md)* option | 跨语言配置项实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_CrossLanguageOperatingStatus](#oh_arkui_crosslanguageoperatingstatus) | 跨语言配置项的节点树操作状态。 |

### OH_ArkUI_ContentTransitionEffect_Create()

```c
ArkUI_ContentTransitionEffect* OH_ArkUI_ContentTransitionEffect_Create(int32_t type)
```

**描述：**

创建ContentTransitionEffect属性对象。

**起始版本：** 21

**参数：**

| 参数项 | 描述                           |
| -- |------------------------------|
| int32_t type | 指定动效的转场方式。值为0表示无动效转场，值为1时表示淡入淡出动效转场。|

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md)* | 指向ContentTransitionEffect对象的指针。 |

### OH_ArkUI_GridLayoutOptions_Create()

```c
ArkUI_GridLayoutOptions* OH_ArkUI_GridLayoutOptions_Create()
```

**描述：**

创建Grid布局选项。

**起始版本：** 22

**返回：**

| 类型                                | 说明 |
|-----------------------------------| -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* | Grid布局选项。 |

### OH_ArkUI_GridLayoutOptions_Dispose()

```c
void OH_ArkUI_GridLayoutOptions_Dispose(ArkUI_GridLayoutOptions* option)
```

**描述：**

销毁Grid布局选项。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Grid布局选项。 |


### OH_ArkUI_GridLayoutOptions_SetIrregularIndexes()

```c
int32_t OH_ArkUI_GridLayoutOptions_SetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t size)
```

**描述：**

设置Grid中不规则GridItem的索引数组。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Grid布局选项。 |
| uint32_t* irregularIndexes |  GridItem索引数组。 |
| int32_t size | GridItem索引数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)  函数参数异常。<br>         异常原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_GridLayoutOptions_GetIrregularIndexes()

```c
int32_t OH_ArkUI_GridLayoutOptions_GetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t* size)
```

**描述：**

获取Grid中不规则GridItem的索引数组。当不设置OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback时，irregularIndexes中GridItem的默认大小为垂直滚动Grid的一整行或水平滚动Grid的一整列。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Grid布局选项。 |
| uint32_t* irregularIndexes |  GridItem索引数组。 |
| int32_t size | GridItem索引数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>         [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) 数组大小不够。<br>         异常原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback()

```c
void OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemSize (*callback)(int32_t itemIndex, void* userData))
```

**描述：**

Grid布局选项通过GridItem索引获取指定Item占用的行列数。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Grid布局选项。 |
| void* userData | 用户自定义数据。 |
| ArkUI_GridItemSize (\*callback)(int32_t itemIndex, void* userData) | 根据index获取指定Item占用的行列数。<br> itemIndex：GridItem索引值，取值范围来自[OH_ArkUI_GridLayoutOptions_SetIrregularIndexes](capi-native-type-h.md#oh_arkui_gridlayoutoptions_setirregularindexes)。 |

### OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback()

```c
void OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemRect (*callback)(int32_t itemIndex, void* userData))
```

**描述：**

Grid布局选项通过GridItem索引获取指定Item的起始行列和占用的行列数。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Grid布局选项。 |
| void* userData | 用户自定义数据。 |
| ArkUI_GridItemRect (\*callback)(int32_t itemIndex, void* userData) | 根据index获取指定Item的起始行列和占用的行列数。<br>   itemIndex：GridItem索引值。 |
### OH_ArkUI_ShowCounterConfig_Create()

```c
ArkUI_ShowCounterConfig* OH_ArkUI_ShowCounterConfig_Create()
```

**描述：**


创建文本输入框计数器的配置对象。

**起始版本：** 22


**返回：**

| 类型                         | 说明 |
|----------------------------| -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)* | 指向文本输入框计数器的配置对象的指针。 |

### OH_ArkUI_ShowCounterConfig_Dispose()

```c
void OH_ArkUI_ShowCounterConfig_Dispose(ArkUI_ShowCounterConfig* config)
```

**描述：**


销毁文本输入框计数器的配置对象。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)* config | 销毁文本输入框计数器的配置对象。 |

### OH_ArkUI_ShowCounterConfig_SetCounterTextColor()

```c
void OH_ArkUI_ShowCounterConfig_SetCounterTextColor(ArkUI_ShowCounterConfig* config, uint32_t color)
```

**描述：**


设置文本输入框未达到最大字符数时计数器的颜色。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)* config | 指向文本输入框计数器的配置对象指针。 |
| uint32_t color | 文本输入框未达到最大字符数时计数器的颜色，格式为0xARGB。 |

### OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor()

```c
void OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor(ArkUI_ShowCounterConfig* config, uint32_t color)
```

**描述：**


设置文本输入框超出最大字符数时计数器的颜色。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)* config | 指向文本输入框计数器的配置对象指针。 |
| uint32_t color | 文本输入框超出最大字符数时计数器的颜色，格式为0xARGB。 |

### OH_ArkUI_ShowCounterConfig_GetCounterTextColor()

```c
uint32_t OH_ArkUI_ShowCounterConfig_GetCounterTextColor(ArkUI_ShowCounterConfig* config)
```

**描述：**


获取文本输入框未达到最大字符数时计数器的颜色。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)* config | 指向文本输入框计数器的配置对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t  | 返回文本输入框未达到最大字符数时计数器的颜色，格式为0xARGB，如果未通过[OH_ArkUI_ShowCounterConfig_SetCounterTextColor](#oh_arkui_showcounterconfig_setcountertextcolor)接口设置计数器颜色，则返回0。 |


### OH_ArkUI_ShowCounterConfig_GetCounterTextOverflowColor()

```c
uint32_t OH_ArkUI_ShowCounterConfig_GetCounterTextOverflowColor(ArkUI_ShowCounterConfig* config)
```

**描述：**


获取文本输入框超出最大字符数时计数器的颜色。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)* config | 指向文本输入框计数器的配置对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 返回文本输入框超出最大字符数时计数器的颜色，格式为0xARGB，如果未通过[OH_ArkUI_ShowCounterConfig_SetCounterTextOverflowColor](#oh_arkui_showcounterconfig_setcountertextoverflowcolor)接口设置计数器颜色，则返回0。 |

### OH_ArkUI_SelectionOptions_Create()

```c
ArkUI_SelectionOptions OH_ArkUI_SelectionOptions_Create()
```

**描述：**


创建选择选项。

**起始版本：** 23


**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md)* | 指向选择选项对象的指针。 |

### OH_ArkUI_SelectionOptions_Dispose()

```c
void OH_ArkUI_SelectionOptions_Dispose(ArkUI_SelectionOptions* options)
```

**描述：**


释放选择选项对象。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md)* options | 指向待释放的选择选项对象的指针。 |

### OH_ArkUI_SelectionOptions_SetMenuPolicy()

```c
void OH_ArkUI_SelectionOptions_SetMenuPolicy(ArkUI_SelectionOptions* options, ArkUI_MenuPolicy menuPolicy)
```

**描述：**


设置选择选项的菜单弹出策略。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md)* options | 指向选择选项对象的指针。 |
| [ArkUI_MenuPolicy ](#arkui_menupolicy) menuPolicy | 菜单弹出策略。 |

### OH_ArkUI_SelectionOptions_GetMenuPolicy()

```c
ArkUI_MenuPolicy  OH_ArkUI_SelectionOptions_GetMenuPolicy(ArkUI_SelectionOptions* options)
```

**描述：**


获取选择选项的菜单弹出策略。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md)* options | 指向选择选项对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_MenuPolicy ](#arkui_menupolicy) | 菜单弹出策略。 |

### OH_ArkUI_TextContentBaseController_Create()

```c
ArkUI_TextContentBaseController* OH_ArkUI_TextContentBaseController_Create()
```

**描述：**

创建文本内容基础控制器对象。

**起始版本：** 23

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)* | 指向控制器对象的指针。|

### OH_ArkUI_TextContentBaseController_Dispose()

```c
void OH_ArkUI_TextContentBaseController_Dispose(ArkUI_TextContentBaseController* controller)
```

**描述：**

销毁文本内容基础控制器对象。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)* controller | 待销毁的控制器对象指针。 |

### OH_ArkUI_TextContentBaseController_DeleteBackward()

```c
void OH_ArkUI_TextContentBaseController_DeleteBackward(ArkUI_TextContentBaseController* controller)
```

**描述：**

在编辑态时删除光标前字符。其他状态删除输入框组件的最后一个字符。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)* controller | 待修改的配置对象指针。 |

### OH_ArkUI_TextContentBaseController_ScrollToVisible()

```c
void OH_ArkUI_TextContentBaseController_ScrollToVisible(ArkUI_TextContentBaseController* controller, int32_t start, int32_t end)
```

**描述：**

将起始索引与结束索引传递给与其绑定的输入框组件，并将此范围内的文字滚动到可视区域。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)* controller | 待修改的配置对象指针。<br>通过此controller将起始索引与结束索引传递给与其绑定的输入框组件并进行滚动操作。 |
| int32_t start | 起始文字索引值。<br>起始索引应小于等于结束索引，否则接口调用无效。取值范围[0, 输入框文本总长度]，起始索引小于0视为0，大于总长度视为总长度。 |
| int32_t end | 结束文字索引值。<br>结束索引应大于等于起始索引，否则接口调用无效。取值范围[0, 输入框文本总长度]，结束索引小于0视为0，大于总长度视为总长度。 |

### OH_ArkUI_TextMenuItem_Create()

```c
ArkUI_TextMenuItem* OH_ArkUI_TextMenuItem_Create()
```

**描述**

创建文本菜单项对象。

**起始版本：** 22

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* | 指向ArkUI_TextMenuItem对象的指针。 |

### OH_ArkUI_TextMenuItem_Dispose()

```c
void OH_ArkUI_TextMenuItem_Dispose(ArkUI_TextMenuItem* textMenuItem)
```

**描述**

释放文本菜单项对象。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* textMenuItem | 指向ArkUI_TextMenuItem对象的指针。 |

### OH_ArkUI_TextMenuItem_SetContent()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetContent(ArkUI_TextMenuItem* item, const char* content)
```

**描述**

设置文本菜单项标题。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | 指向ArkUI_TextMenuItem对象的指针。 |
| const char* content | 文本菜单项标题，默认为空字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMenuItem_GetContent()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetContent(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取文本菜单项标题。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | 指向ArkUI_TextMenuItem对象的指针。 |
| char* buffer | 缓冲区，由开发者创建分配内存，用于存储文本菜单项标题信息。 |
| int32_t bufferSize | 缓冲区大小。 |
| int32_t* writeLength | 返回值为[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)时表示实际写入缓冲区的长度。<br> 返回值为[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode)时表示字符串完整写入缓冲区所需要的最小长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) 缓冲区大小不足。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMenuItem_SetIcon()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetIcon(ArkUI_TextMenuItem* item, const char* icon)
```

**描述**

设置文本菜单项图标路径。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | 指向ArkUI_TextMenuItem对象的指针。 |
| const char* icon | 文本菜单项图标路径，默认空字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMenuItem_GetIcon()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetIcon(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取文本菜单项图标路径。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | 指向ArkUI_TextMenuItem对象的指针。 |
| char* buffer | 缓冲区，由开发者创建分配内存，用于存储文本菜单项图标路径信息。 |
| int32_t bufferSize | 缓冲区大小。 |
| int32_t* writeLength | 返回值为[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)时表示实际写入缓冲区的长度。<br> 返回值为[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode)时表示字符串完整写入缓冲区所需要的最小长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) 缓冲区大小不足。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMenuItem_SetLabelInfo()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetLabelInfo(ArkUI_TextMenuItem* item, const char* labelInfo)
```

**描述**

设置文本菜单项快捷键提示，例如“复制”菜单项的快捷键提示可以设置为“Ctrl+C”。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | 指向ArkUI_TextMenuItem对象的指针。 |
| const char* labelInfo | 文本菜单项快捷键提示，默认空字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMenuItem_GetLabelInfo()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetLabelInfo(const ArkUI_TextMenuItem* item, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取文本菜单项快捷键提示，例如“复制”菜单项的快捷键提示一般为“Ctrl+C”。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| ------ | --- |
| const [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | 指向ArkUI_TextMenuItem对象的指针。 |
| char* buffer | 缓冲区，由开发者创建分配内存，用于存储文本菜单项快捷键提示信息。 |
| int32_t bufferSize | 缓冲区大小。 |
| int32_t* writeLength | 返回值为[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)时表示实际写入缓冲区的长度。<br> 返回值为[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode)时表示字符串完整写入缓冲区所需要的最小长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) 缓冲区大小不足。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMenuItem_SetId()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_SetId(ArkUI_TextMenuItem* item, int32_t id)
```

**描述**

设置文本菜单项id。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | 指向ArkUI_TextMenuItem对象的指针。 |
| int32_t id | 文本菜单项id。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMenuItem_GetId()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItem_GetId(const ArkUI_TextMenuItem* item, int32_t* id)
```

**描述**

获取文本菜单项id。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | 指向ArkUI_TextMenuItem对象的指针。 |
| int32_t* id | 文本菜单项id。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMenuItemArray_GetSize()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_GetSize(ArkUI_TextMenuItemArray* items, int32_t* size)
```

**描述**

获取文本菜单项数组大小。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | 指向ArkUI_TextMenuItemArray对象的指针。 |
| int32_t* size | 文本菜单项数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMenuItemArray_GetItem()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_GetItem(ArkUI_TextMenuItemArray* items, int32_t index, ArkUI_TextMenuItem** item)
```

**描述**

获取文本菜单项数组中指定索引位置的文本菜单项。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | 指向ArkUI_TextMenuItemArray对象的指针。 |
| int32_t index | 指定索引位置。 |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)** item | 指向ArkUI_TextMenuItem对象的二级指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMenuItemArray_Insert()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Insert(ArkUI_TextMenuItemArray* items, ArkUI_TextMenuItem* item, int32_t index)
```

**描述**

在文本菜单项数组中指定索引位置插入一个文本菜单项。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | 指向ArkUI_TextMenuItemArray对象的指针。 |
| [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | 指向ArkUI_TextMenuItem对象的指针。 |
| int32_t index | 要插入文本菜单项的索引位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMenuItemArray_Erase()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Erase(ArkUI_TextMenuItemArray* items, int32_t index)
```

**描述**

删除文本菜单项数组中指定索引位置的文本菜单项。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | 指向ArkUI_TextMenuItemArray对象的指针。 |
| int32_t index | 要删除的文本菜单项索引位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMenuItemArray_Clear()

```c
ArkUI_ErrorCode OH_ArkUI_TextMenuItemArray_Clear(ArkUI_TextMenuItemArray* items)
```

**描述**

清除文本菜单项数组中所有的文本菜单项。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | 指向ArkUI_TextMenuItemArray对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextEditMenuOptions_Create()

```c
ArkUI_TextEditMenuOptions* OH_ArkUI_TextEditMenuOptions_Create()
```

**描述**

创建文本菜单扩展项对象。

**起始版本：** 22

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | 指向ArkUI_TextEditMenuOptions对象的指针。 |


### OH_ArkUI_TextEditMenuOptions_Dispose()

```c
void OH_ArkUI_TextEditMenuOptions_Dispose(ArkUI_TextEditMenuOptions* editMenuOptions)
```

**描述**

释放文本菜单扩展项对象。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | 指向ArkUI_TextEditMenuOptions对象的指针。 |

### ArkUI_TextCreateMenuCallback()

```c
typedef void (*ArkUI_TextCreateMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)
```

**描述**

文本菜单创建事件回调函数，在文本菜单创建时会触发此回调函数，开发者可在此函数中设置菜单数据。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | 指向ArkUI_TextMenuItemArray对象的指针，该数组对象由系统内部创建并释放，在回调函数中开发者可以调用[OH_ArkUI_TextMenuItemArray_Insert](capi-native-type-h.md#oh_arkui_textmenuitemarray_insert)，[OH_ArkUI_TextMenuItemArray_Erase](capi-native-type-h.md#oh_arkui_textmenuitemarray_erase)进行数组修改。 |
| void\* userData | 用户自定义数据。 |

### ArkUI_TextPrepareMenuCallback()

```c
typedef void (*ArkUI_TextPrepareMenuCallback)(ArkUI_TextMenuItemArray* items, void* userData)
```

**描述**

文本菜单准备事件回调函数，当文本选择区域变化后显示菜单之前会触发此回调函数，开发者可在此函数中配置菜单数据。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMenuItemArray](capi-arkui-nativemodule-arkui-textmenuitemarray.md)* items | 指向ArkUI_TextMenuItemArray对象的指针，该数组对象由系统内部创建并释放，在回调函数中开发者可以调用[OH_ArkUI_TextMenuItemArray_Insert](capi-native-type-h.md#oh_arkui_textmenuitemarray_insert)，[OH_ArkUI_TextMenuItemArray_Erase](capi-native-type-h.md#oh_arkui_textmenuitemarray_erase)进行数组修改。 |
| void\* userData | 用户自定义数据。 |

### ArkUI_TextMenuItemClickCallback()

```c
typedef bool (*ArkUI_TextMenuItemClickCallback)(const ArkUI_TextMenuItem* item,int32_t start, int32_t end, void* userData)
```

**描述**

文本菜单项点击事件回调函数，在菜单项被点击时触发此回调函数，开发者可在此函数中对系统默认处理行为进行拦截。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkUI_TextMenuItem](capi-arkui-nativemodule-arkui-textmenuitem.md)* item | 指向ArkUI_TextMenuItem对象的指针，表示被点击的文本菜单项。 |
| int32_t start | 选中文本起始索引。 |
| int32_t end | 选中文本结束索引。 |
| void\* userData | 用户自定义数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 是否拦截系统默认处理行为。<br> true：拦截系统默认处理行为，如点击“粘贴”、“复制”等文本菜单项时不再执行系统系统默认处理行为，仅执行开发者自定义处理行为。<br> false：不拦截系统默认处理行为，如点击“粘贴”、“复制”等文本菜单项时先执行开发者自定义处理行为，再执行系统默认处理行为。 |

### OH_ArkUI_TextEditMenuOptions_RegisterOnCreateMenuCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnCreateMenuCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextCreateMenuCallback cb)
```

**描述**

注册文本菜单创建事件回调函数。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | 指向ArkUI_TextEditMenuOptions对象的指针。 |
| void* userData | 用户自定义数据。 |
| [ArkUI_TextCreateMenuCallback](capi-native-type-h.md#arkui_textcreatemenucallback) cb | 文本菜单创建事件回调函数。 |

**返回：**

| 类型 | 说明 |
| ---- | --- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextEditMenuOptions_RegisterOnPrepareMenuCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnPrepareMenuCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextPrepareMenuCallback cb)
```

**描述**

注册文本菜单准备事件回调函数。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | 指向ArkUI_TextEditMenuOptions对象的指针。 |
| void* userData | 用户自定义数据。 |
| [ArkUI_TextPrepareMenuCallback](capi-native-type-h.md#arkui_textpreparemenucallback) cb | 文本菜单准备事件回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextEditMenuOptions_RegisterOnMenuItemClickCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditMenuOptions_RegisterOnMenuItemClickCallback(ArkUI_TextEditMenuOptions* editMenuOptions, void* userData, ArkUI_TextMenuItemClickCallback cb)
```

**描述**

注册文本菜单项点击事件回调函数。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)* editMenuOptions | 指向ArkUI_TextEditMenuOptions对象的指针。 |
| void* userData | 用户自定义数据。 |
| [ArkUI_TextMenuItemClickCallback](capi-native-type-h.md#arkui_textmenuitemclickcallback) cb | 文本菜单项点击事件回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextSelectionMenuOptions_Create()

```c
ArkUI_TextSelectionMenuOptions* OH_ArkUI_TextSelectionMenuOptions_Create();
```

**描述**

创建自定义文本选择菜单对象。

**起始版本：** 22

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* | 指向ArkUI_TextSelectionMenuOptions对象的指针。 |


### OH_ArkUI_TextSelectionMenuOptions_Dispose()

```c
void OH_ArkUI_TextSelectionMenuOptions_Dispose(ArkUI_TextSelectionMenuOptions* selectionMenuOptions)
```

**描述**

释放自定义文本选择菜单对象。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | 指向ArkUI_TextSelectionMenuOptions对象的指针。 |

### OH_ArkUI_TextSelectionMenuOptions_SetSpanType()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetSpanType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextSpanType textSpanType)
```

**描述**

设置自定义文本选择菜单的文本识别类型。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | 指向ArkUI_TextSelectionMenuOptions对象的指针。 |
| [ArkUI_TextSpanType](capi-native-type-h.md#arkui_textspantype) textSpanType | 自定义文本选择菜单的文本识别类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextSelectionMenuOptions_GetSpanType()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetSpanType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextSpanType* spanType)
```

**描述**

获取自定义文本选择菜单的文本识别类型。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | 指向ArkUI_TextSelectionMenuOptions对象的指针。 |
| [ArkUI_TextSpanType](capi-native-type-h.md#arkui_textspantype)* spanType | 自定义文本选择菜单的文本识别类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextSelectionMenuOptions_SetContentNode()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetContentNode(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_NodeHandle node)
```

**描述**

设置自定义文本选择菜单的内容节点。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | 指向ArkUI_TextSelectionMenuOptions对象的指针。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 自定义文本选择菜单的内容节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextSelectionMenuOptions_GetContentNode()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetContentNode(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_NodeHandle* node)
```

**描述**

获取自定义文本选择菜单的内容节点。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | 指向ArkUI_TextSelectionMenuOptions对象的指针。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)* node | 自定义文本选择菜单的内容节点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextSelectionMenuOptions_SetResponseType()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_SetResponseType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextResponseType responseType)
```

**描述**

设置自定义文本选择菜单的响应类型。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | 指向ArkUI_TextSelectionMenuOptions对象的指针。 |
| [ArkUI_TextResponseType](capi-native-type-h.md#arkui_textresponsetype) responseType | 自定义文本选择菜单的响应类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextSelectionMenuOptions_GetResponseType()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_GetResponseType(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, ArkUI_TextResponseType* responseType)
```

**描述**

获取自定义文本选择菜单的响应类型。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | 指向ArkUI_TextSelectionMenuOptions对象的指针。 |
| [ArkUI_TextResponseType](capi-native-type-h.md#arkui_textresponsetype)* responseType | 自定义文本选择菜单的响应类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuShowCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuShowCallback(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, void* userData, void (*callback)(int32_t start, int32_t end, void* userData))
```

**描述**

注册自定义文本选择菜单显示事件回调。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | 指向ArkUI_TextSelectionMenuOptions对象的指针。 |
| void* userData | 用户自定义数据，取任意值。设置后，会通过callback回调回传回来。 |
| void (\*callback)(int32_t start, int32_t end, void* userData) | 自定义文本选择菜单显示事件回调。<br> start：选中文本的起始位置。<br> end：选中文本的结束位置。<br> userData：用户自定义数据，对应OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuShowCallback接口的入参userData。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuHideCallback()

```c
ArkUI_ErrorCode OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuHideCallback(ArkUI_TextSelectionMenuOptions* selectionMenuOptions, void* userData, void (*callback)(int32_t start, int32_t end, void* userData))
```

**描述**

注册自定义文本选择菜单隐藏事件回调。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md)* selectionMenuOptions | 指向ArkUI_TextSelectionMenuOptions对象的指针。 |
| void* userData | 用户自定义数据，取任意值。设置后，会通过callback回调回传回来。 |
| void (\*callback)(int32_t start, int32_t end, void* userData) | 自定义文本选择菜单隐藏事件回调。<br> start：选中文本的起始位置。<br> end：选中文本的结束位置。<br> userData：用户自定义数据，对应OH_ArkUI_TextSelectionMenuOptions_RegisterOnMenuHideCallback接口的入参userData。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br> [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_TextMarqueeOptions_Create()
``` c
ArkUI_TextMarqueeOptions* OH_ArkUI_TextMarqueeOptions_Create()
```

**描述：**

创建文本跑马灯模式配置项。

**起始版本：** 23

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)*| 创建文本跑马灯模式配置项的对象指针。|

### OH_ArkUI_TextMarqueeOptions_Dispose()
``` c
void OH_ArkUI_TextMarqueeOptions_Dispose(ArkUI_TextMarqueeOptions* option)
```

**描述：**

销毁文本跑马灯模式配置项指针。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 需要销毁的文本跑马灯模式配置项对象指针。 |


### OH_ArkUI_TextMarqueeOptions_SetStart()
``` c
void OH_ArkUI_TextMarqueeOptions_SetStart(ArkUI_TextMarqueeOptions* option, bool start)
```

**描述：**

设置文本跑马灯模式配置项是否播放。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |
| bool start | 是否播放。true表示播放，false表示不播放。 |

### OH_ArkUI_TextMarqueeOptions_GetStart()
``` c
bool OH_ArkUI_TextMarqueeOptions_GetStart(ArkUI_TextMarqueeOptions* option)
```

**描述：**

获取文本跑马灯模式配置项是否播放。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 是否播放。true表示播放，false表示不播放。|


### OH_ArkUI_TextMarqueeOptions_SetStep()
``` c
void OH_ArkUI_TextMarqueeOptions_SetStep(ArkUI_TextMarqueeOptions* option, float step)
```

**描述：**

设置文本跑马灯模式配置项的步长。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |
| float step | 步长。单位：vp。 |

### OH_ArkUI_TextMarqueeOptions_GetStep()
``` c
float OH_ArkUI_TextMarqueeOptions_GetStep(ArkUI_TextMarqueeOptions* option)
```

**描述：**

获取文本跑马灯模式配置项的步长。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 步长。单位：vp。|


### OH_ArkUI_TextMarqueeOptions_SetSpacing()
``` c
void OH_ArkUI_TextMarqueeOptions_SetSpacing(ArkUI_TextMarqueeOptions* option, float spacing)
```

**描述：**

设置文本跑马灯模式配置项的首尾间距。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |
| float spacing | 首尾间距。单位：vp。|

### OH_ArkUI_TextMarqueeOptions_GetSpacing()
``` c
float OH_ArkUI_TextMarqueeOptions_GetSpacing(ArkUI_TextMarqueeOptions* option)
```

**描述：**

获取文本跑马灯模式配置项的首尾间距。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 首尾间距。单位：vp。|



### OH_ArkUI_TextMarqueeOptions_SetLoop()
``` c
void OH_ArkUI_TextMarqueeOptions_SetLoop(ArkUI_TextMarqueeOptions* option, int32_t loop)
```

**描述：**

设置文本跑马灯模式配置项的重复滚动的次数，小于等于零时无限循环。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |
| int32_t loop | 设置的重复滚动的次数。 |

### OH_ArkUI_TextMarqueeOptions_GetLoop()
``` c
int32_t OH_ArkUI_TextMarqueeOptions_GetLoop(ArkUI_TextMarqueeOptions* option)
```

**描述：**

获取文本跑马灯模式配置项的重复滚动的次数。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 重复滚动的次数。|



### OH_ArkUI_TextMarqueeOptions_SetFromStart()
``` c
void OH_ArkUI_TextMarqueeOptions_SetFromStart(ArkUI_TextMarqueeOptions* option, bool fromStart)
```

**描述：**

设置文本跑马灯模式配置项的运行方向。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |
| bool fromStart | 跑马灯运行方向。true表示从头开始滚动，false表示反向滚动。|

### OH_ArkUI_TextMarqueeOptions_GetFromStart()
``` c
bool OH_ArkUI_TextMarqueeOptions_GetFromStart(ArkUI_TextMarqueeOptions* option)
```

**描述：**

获取文本跑马灯模式配置项的运行方向。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 跑马灯运行方向。true表示从头开始滚动，false表示反向滚动。|


### OH_ArkUI_TextMarqueeOptions_SetDelay()
``` c
void OH_ArkUI_TextMarqueeOptions_SetDelay(ArkUI_TextMarqueeOptions* option, int32_t delay)
```

**描述：**

设置文本跑马灯模式配置项的每轮滚动延迟时间。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |
| int32_t delay| 每轮滚动延迟时间，单位为毫秒。 |

### OH_ArkUI_TextMarqueeOptions_GetDelay()
``` c
int32_t OH_ArkUI_TextMarqueeOptions_GetDelay(ArkUI_TextMarqueeOptions* option)
```

**描述：**

获取文本跑马灯模式配置项的每轮滚动延迟时间。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回每轮滚动延迟时间，单位为毫秒。|

### OH_ArkUI_TextMarqueeOptions_SetFadeout()
``` c
void OH_ArkUI_TextMarqueeOptions_SetFadeout(ArkUI_TextMarqueeOptions* option, bool fadeout)
```

**描述：**

设置文本跑马灯模式配置项是否支持文字超长时的渐隐效果。当Text内容超出显示范围时，未完全展现的文字边缘将应用渐隐效果。<br> 若两端均有文字未完全显示，则两端同时应用渐隐效果。<br> 在渐隐效果开启状态下，[ArkUI_NodeAttributeType](./capi-native-node-h.md#arkui_nodeattributetype)中的NODE_CLIP属性将自动锁定为true，不允许设置为false。


**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |
| bool fadeout| 跑马灯是否支持文字超长时的渐隐效果。<br/>true表示支持渐隐效果，false表示不支持渐隐效果。 |

### OH_ArkUI_TextMarqueeOptions_GetFadeout()
``` c
bool OH_ArkUI_TextMarqueeOptions_GetFadeout(ArkUI_TextMarqueeOptions* option)
```

**描述：**

获取文本跑马灯模式配置项是否支持文字超长时的渐隐效果。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 是否支持文字超长时的渐隐效果。|


### OH_ArkUI_TextMarqueeOptions_SetStartPolicy()
``` c
void OH_ArkUI_TextMarqueeOptions_SetStartPolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeStartPolicy startPolicy)

```

**描述：**

设置文本跑马灯模式配置项的启动策略。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |
| [ArkUI_MarqueeStartPolicy](#arkui_marqueestartpolicy) startPolicy| 启动策略。 |

### OH_ArkUI_TextMarqueeOptions_GetStartPolicy()
``` c
ArkUI_MarqueeStartPolicy OH_ArkUI_TextMarqueeOptions_GetStartPolicy(ArkUI_TextMarqueeOptions* option)
```

**描述：**

获取文本跑马灯模式配置项的启动策略。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkUI_MarqueeStartPolicy | 启动策略。|


### OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy()
``` c
void OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy(ArkUI_TextMarqueeOptions* option,
    ArkUI_MarqueeUpdatePolicy updatePolicy)
```

**描述：**

设置文本跑马灯模式配置项的更新策略。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |
| [ArkUI_MarqueeUpdatePolicy](#arkui_marqueeupdatepolicy) updatePolicy| 更新策略。 |

### OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy()
``` c
ArkUI_MarqueeUpdatePolicy OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy(ArkUI_TextMarqueeOptions* option)
```

**描述：**

获取文本跑马灯模式配置项的更新策略。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_TextMarqueeOptions](./capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | 文本跑马灯模式配置项。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_MarqueeUpdatePolicy](#arkui_marqueeupdatepolicy) | 更新策略。|

### OH_ArkUI_SelectedDragPreviewStyle_Create()

```c
ArkUI_SelectedDragPreviewStyle* OH_ArkUI_SelectedDragPreviewStyle_Create();
```

**描述**

创建选中状态下拖拽文本预览样式对象。

**起始版本：** 23

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md)* | 指向ArkUI_SelectedDragPreviewStyle对象的指针。 |


### OH_ArkUI_SelectedDragPreviewStyle_Dispose()

```c
void OH_ArkUI_SelectedDragPreviewStyle_Dispose(ArkUI_SelectedDragPreviewStyle* config)
```

**描述**

销毁选中状态下拖拽文本预览样式对象。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md)* config | 指向ArkUI_SelectedDragPreviewStyle对象的指针。 |

### OH_ArkUI_SelectedDragPreviewStyle_SetColor()

```c
void  OH_ArkUI_SelectedDragPreviewStyle_SetColor(ArkUI_SelectedDragPreviewStyle* config, uint32_t color);
```

**描述**

设置选中态拖拽文本预览样式的背景色。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md)* config | 指向ArkUI_SelectedDragPreviewStyle对象的指针。 |
| uint32_t color  | 选中态拖拽文本预览样式的的背景，格式为RGBA。|

### OH_ArkUI_SelectedDragPreviewStyle_GetColor()

```c
uint32_t OH_ArkUI_SelectedDragPreviewStyle_GetColor(ArkUI_SelectedDragPreviewStyle* config)
```

**描述**

获取选中态拖拽文本预览样式的背景色。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md)* config | 指向ArkUI_SelectedDragPreviewStyle对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t color | 选中态拖拽文本预览样式的的背景，格式为RGBA。 |

### OH_ArkUI_DecorationStyleOptions_Create()

```c
OH_ArkUI_DecorationStyleOptions* OH_ArkUI_DecorationStyleOptions_Create()
```

**描述**

创建一个装饰线样式对象。当该对象不再使用时，请调用[OH_ArkUI_DecorationStyleOptions_Destroy](capi-native-type-h.md#oh_arkui_decorationstyleoptions_destroy)销毁。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions*](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md) | 指向[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)对象的指针。 |

### OH_ArkUI_DecorationStyleOptions_Destroy()

```c
void OH_ArkUI_DecorationStyleOptions_Destroy(OH_ArkUI_DecorationStyleOptions* options)
```

**描述**

销毁装饰线样式对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)* options | 指向待销毁的选项对象的指针。 |

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
| [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype) type | 装饰类型[ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype)* type | 装饰类型[ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle) style | 装饰线的样式[ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle)* style | 装饰线的样式[ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextDataDetectorConfig_Create()

```c
OH_ArkUI_TextDataDetectorConfig* OH_ArkUI_TextDataDetectorConfig_Create()
```

**描述**

创建一个文本实体识别配置对象。当该对象不再使用时，请调用[OH_ArkUI_TextDataDetectorConfig_Destroy](capi-native-type-h.md#oh_arkui_textdatadetectorconfig_destroy)销毁。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig*](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) | 指向[OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)对象的指针。 |

### OH_ArkUI_TextDataDetectorConfig_Destroy()

```c
void OH_ArkUI_TextDataDetectorConfig_Destroy(OH_ArkUI_TextDataDetectorConfig* config)
```

**描述**

销毁文本实体识别配置对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)* config | 指向[OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)对象的指针。 |

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
| [const ArkUI_TextDataDetectorType](capi-native-type-h.md#arkui_textdatadetectortype)* types | 文本实体识别配置的类型，取值为[ArkUI_TextDataDetectorType](capi-native-type-h.md#arkui_textdatadetectortype)枚举。 |
| int32_t length | 类型的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_TextDataDetectorType](capi-native-type-h.md#arkui_textdatadetectortype)* buffer | 指向类型数组的缓冲区指针。 |
| int32_t bufferSize | 开发者为类型预留的缓冲区最多可以写入的类型的数量。 |
| int32_t* writeLength | 实际写入缓冲区的类型的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。<br>         若bufferSize小于writeLength，返回[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode)。 |

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
| void (\*callback)(const char\* result | 识别结果更新回调。result 识别到的文本实体内容。length 选中文本的结束位置。userData 用户自定义数据，对应OH_ArkUI_TextDataDetectorConfig_RegisterOnDetectResultUpdateCallback接口的入参userData。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若节点、缓冲区或writeLength为空，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。<br>         若bufferSize小于writeLength，返回[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若节点、缓冲区或writeLength为空，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。<br>         若bufferSize小于writeLength，返回[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle) fontStyle | 字体样式。取值为[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)* fontStyle | 字体样式。取值为[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment) align | 文本对齐方式。取值为[ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment)* align | 文本对齐方式。取值为[ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [struct OH_PixelmapNative](../../reference/apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md)* pixelmap | 段落缩进的像素图。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [struct OH_PixelmapNative](../../reference/apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md)** pixelmap | 段落缩进的像素图。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak) wordBreak | 断字方式。取值为[ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak)* wordBreak | 断字方式。取值为[ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [OH_ArkUI_LineBreakStrategy](capi-native-type-h.md#oh_arkui_linebreakstrategy) lineBreakStrategy | 换行策略。取值为[OH_ArkUI_LineBreakStrategy](capi-native-type-h.md#oh_arkui_linebreakstrategy)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [OH_ArkUI_LineBreakStrategy](capi-native-type-h.md#oh_arkui_linebreakstrategy)* lineBreakStrategy | 换行策略。取值为[OH_ArkUI_LineBreakStrategy](capi-native-type-h.md#oh_arkui_linebreakstrategy)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment) verticalAlignment | 文本垂直对齐方式。取值为[ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment)* verticalAlignment | 文本垂直对齐方式。取值为[ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection) textDirection | 文本方向。取值为[ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection)* textDirection | 文本方向。取值为[ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle) fontStyle | 字体样式。取值为[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)* fontStyle | 字体样式。取值为[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)中的枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| bool halfLeading | 文本是否将行间距平分至行的顶部与底部。<br>                    true表示将行间距平分至行的顶部与底部，false表示不将行间距平分至行的顶部与底部。默认值为false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| bool* halfLeading | 文本是否将行间距平分至行的顶部与底部。<br>                    true表示将行间距平分至行的顶部与底部，false表示不将行间距平分至行的顶部与底部。默认值为false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| void (\*callback)(int32_t start | 菜单显示的回调函数。start 选中内容的起始偏移量。end 选中内容的结束偏移量。callbackUserData 用户数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| void (\*callback)(int32_t start | 菜单隐藏的回调函数。start 选中内容的起始偏移量。end 选中内容的结束偏移量。callbackUserData 用户数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| void (\*callback)(int32_t start | 菜单出现的回调函数。start 选中内容的起始偏移量。end 选中内容的结束偏移量。callbackUserData 用户数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| void (\*callback)(void\* callbackUserData) | 菜单消失的回调函数。callbackUserData 用户数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

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
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。<br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |
### OH_ArkUI_TextEditorStyledStringController_GetSelection()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetSelection(const OH_ArkUI_TextEditorStyledStringController* controller, uint32_t* start, uint32_t* end)
```

**描述**

通过属性字符串控制器获取选中区域。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| uint32_t* start | 选中区域的起始位置。 |
| uint32_t* end | 选中区域的结束位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。 <br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。 <br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_SetStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetStyledString(const OH_ArkUI_TextEditorStyledStringController* controller, const ArkUI_StyledString_Descriptor* descriptor)
```

**描述**

通过属性字符串控制器设置显示的属性字符串。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| const [ ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | 指向[ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。 <br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。 <br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_GetStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_GetStyledString(const OH_ArkUI_TextEditorStyledStringController* controller, ArkUI_StyledString_Descriptor* descriptor)
```

**描述**

通过属性字符串控制器获取显示的属性字符串。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | 指向[ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。 <br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。 <br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_SetStyledPlaceholder()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_SetStyledPlaceholder(const OH_ArkUI_TextEditorStyledStringController* controller, const ArkUI_StyledString_Descriptor* descriptor)
```

**描述**

通过属性字符串控制器设置属性字符串样式的提示文本。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| const [ ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | 指向[ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。 <br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。 <br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_TextEditorStyledStringController_ScrollToVisible()

```c
ArkUI_ErrorCode OH_ArkUI_TextEditorStyledStringController_ScrollToVisible(const OH_ArkUI_TextEditorStyledStringController* controller, int32_t start, int32_t end)
```

**描述**

通过属性字符串控制器使指定起始索引至结束索引范围内的内容滚动至可视区域。

**起始版本：** 26.0.0

**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)* controller | 指向[OH_ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)对象的指针。 |
| int32_t start                                                | 起始内容索引值。 <br>     起始索引应小于等于结束索引，否则接口调用无效。取值范围[0, TextEditor组件内容总长度]，起始索引小于0视为0，大于总长度视为总长度。 |
| int32_t end                                                  | 结束内容索引值。 <br>     结束索引应大于等于起始索引，否则接口调用无效。取值范围[0, TextEditor组件内容总长度]，结束索引小于0视为0，大于总长度视为总长度。 |

**返回：**

| 类型                                                     | 说明                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果码。 <br>         若操作成功，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。 <br>         若参数异常，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_PickerIndicatorStyle_ConfigureBackground()

``` c
ArkUI_ErrorCode OH_ArkUI_PickerIndicatorStyle_ConfigureBackground(ArkUI_PickerIndicatorStyle* style, ArkUI_PickerIndicatorBackground* background)
```

**描述**

设置背景样式参数，此接口仅当选择器选中项样式枚举类型为[ARKUI_PICKER_INDICATOR_BACKGROUND](capi-picker-h.md#arkui_pickerindicatortype)时生效。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | 选中项指示器样式[ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)的实例。 |
| [ArkUI_PickerIndicatorBackground](capi-arkui-nativemodule-arkui-pickerindicatorbackground.md)* background | 背景样式参数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_PickerIndicatorStyle_ConfigureDivider()

``` c
ArkUI_ErrorCode OH_ArkUI_PickerIndicatorStyle_ConfigureDivider(ArkUI_PickerIndicatorStyle* style, ArkUI_PickerIndicatorDivider* divider)
```

**描述**

设置分割线样式参数，此接口仅当选择器选中项样式枚举类型为[ARKUI_PICKER_INDICATOR_DIVIDER](capi-picker-h.md#arkui_pickerindicatortype)时生效。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | 选中项指示器样式[ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)的实例。 |
| [ArkUI_PickerIndicatorDivider](capi-arkui-nativemodule-arkui-pickerindicatordivider.md)* divider | 分割线样式参数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_FontWeightConfigs_Create()

```c
OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontWeightConfigs_Create()
```

**描述**

创建文本字体粗细配置对象。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs*](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md) | 返回指向文本字体粗细配置对象的指针。如果创建失败，返回空指针。 |

### OH_ArkUI_FontWeightConfigs_Destroy()

```c
void OH_ArkUI_FontWeightConfigs_Destroy(OH_ArkUI_FontWeightConfigs* option)
```

**描述**

销毁文本字体粗细配置对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | 指向要销毁的文本字体粗细配置对象的指针。 |

### OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight()

```c
void OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option, bool enable)
```

**描述**

设置是否启用可变字重调节。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | 指向待修改的文本字体粗细配置对象的指针。 |
| bool enable | 是否启用可变字重调节。true表示启用可变字重调节。此时如果设置的字重weight取值为[100, 900]范围内任意整数，则字重取值为weight，否则取默认值400。false表示禁用可变字重调节。此时如果设置的字重weight取值为[100, 900]范围内的整百数值，字重取值为weight；weight是非整百数值时，字重取默认值400。默认值为false。 |

### OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight()

```c
bool OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option)
```

**描述**

获取文本字体粗细配置对象是否启用了可变字重调节。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | 指向文本字体粗细配置对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回是否启用可变字重调节。<br>        true表示启用可变字重调节。此时如果设置的字重weight取值为[100, 900]范围内任意整数，则字重取值为weight，否则取默认值400。<br>         false表示禁用可变字重调节。此时如果设置的字重weight取值为[100, 900]范围内的整百数值，字重取值为weight；weight是非整百数值时，字重取默认值400。<br>         默认值为false。字重weight取值为[100, 900]范围外的值，字重取默认值400。 |

### OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory()

```c
void OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option, bool enable)
```

**描述**

设置设备的字体粗细级别改变时文本字体粗细是否自动更新。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | 指向待修改的文本字体粗配置对象的指针。 |
| bool enable | 是否启用文本字体粗细跟随设备的字体粗细级别更新。true表示当设备的字体粗细级别改变时，文本字体粗细将自动更新。false表示当设备的字体粗细级别改变时，文本字体粗不会自动更新。默认值为true。 |

### OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory()

```c
bool OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option)
```

**描述**

获取文本字体粗细是否跟随设备的字体粗细级别更新。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | 指向文本字体粗细配置对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回文本字体粗细是否跟随设备的字体粗细级别更新。<br>         true表示当设备的字体粗细级别改变时，文本字体粗细将自动更新。<br>         false表示当设备的字体粗细级别改变时，文本字体粗细不会自动更新。 |

### OH_ArkUI_FontConfigs_Create()

```c
OH_ArkUI_FontConfigs* OH_ArkUI_FontConfigs_Create()
```

**描述**

创建文本字体配置对象。

**起始版本：** 24

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_FontConfigs*](capi-arkui-nativemodule-oh-arkui-fontconfigs.md) | 返回指向文本字体配置对象的指针。如果创建失败，返回空指针。 |

### OH_ArkUI_FontConfigs_Destroy()

```c
void OH_ArkUI_FontConfigs_Destroy(OH_ArkUI_FontConfigs* option)
```

**描述**

销毁文本字体配置对象。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)* option | 指向要销毁的文本字体配置对象的指针。 |

### OH_ArkUI_FontConfigs_SetFontWeightConfigs()

```c
void OH_ArkUI_FontConfigs_SetFontWeightConfigs(OH_ArkUI_FontConfigs* option, OH_ArkUI_FontWeightConfigs* fontWeightConfigs)
```

**描述**

设置文本字体配置对象的文本字体粗细配置。当该配置不为空指针时，若用户未显式设置，各项配置将使用默认值（可变字重调节默认为禁用，文本字体粗细跟随设备字体粗细级别更新默认为启用）。当该配置为空指针时，不应用上述默认值，文本字体粗细行为与父组件保持一致。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)* option | 指向待修改的文本字体配置对象的指针。 |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* fontWeightConfigs | 文本字体粗细配置。 |

### OH_ArkUI_FontConfigs_GetFontWeightConfigs()

```c
OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontConfigs_GetFontWeightConfigs(OH_ArkUI_FontConfigs* option)
```

**描述**

获取文本字体配置对象的文本字体粗细配置。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)* option | 指向文本字体配置对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs*](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md) | 返回文本字体粗细配置。 |

### OH_ArkUI_TextController_Create()

```c
OH_ArkUI_TextController* OH_ArkUI_TextController_Create()
```

**描述**

创建文本组件控制器对象。

**起始版本：** 26.0.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_TextController*](capi-arkui-nativemodule-oh-arkui-textcontroller.md) | 返回指向文本组件控制器对象的指针。如果创建失败，返回空指针。 |

### OH_ArkUI_TextController_Destroy()

```c
void OH_ArkUI_TextController_Destroy(OH_ArkUI_TextController* controller)
```

**描述**

销毁文本组件控制器对象。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md)* controller | 指向文本组件控制器对象的指针。 |

### OH_ArkUI_TextController_SetStyledString()

```c
ArkUI_ErrorCode OH_ArkUI_TextController_SetStyledString(OH_ArkUI_TextController* controller, ArkUI_StyledString_Descriptor* descriptor)
```

**描述**

设置文本组件的属性字符串。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md)* controller | 指向[OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md)对象的指针。 |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | 指向[ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回结果。<br> [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_LinearGradientOptions_Create()

```c
OH_ArkUI_LinearGradientOptions* OH_ArkUI_LinearGradientOptions_Create()
```

**描述**

创建线性渐变效果选项对象。

**起始版本：** 26.0.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_LinearGradientOptions*](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md) | 指向[OH_ArkUI_LinearGradientOptions*](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)的指针。 |

### OH_ArkUI_LinearGradientOptions_Destroy()

```c
void OH_ArkUI_LinearGradientOptions_Destroy(OH_ArkUI_LinearGradientOptions* options)
```

**描述**

销毁线性渐变效果选项对象。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | 指向[OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)对象的指针。 |

### OH_ArkUI_LinearGradientOptions_SetAngle()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetAngle(OH_ArkUI_LinearGradientOptions* options, float angle)
```

**描述**

设置线性渐变效果选项的角度。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | 指向[OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)对象的指针。 |
| float angle | 线性渐变效果选项的角度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_LinearGradientOptions_GetAngle()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetAngle(const OH_ArkUI_LinearGradientOptions* options, float* angle)
```

**描述**

获取线性渐变效果选项的角度。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | 指向[OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)对象的指针。 |
| float* angle | 线性渐变效果选项的角度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_LinearGradientOptions_SetDirection()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetDirection(OH_ArkUI_LinearGradientOptions* options, ArkUI_LinearGradientDirection direction)
```

**描述**

设置线性渐变选项的方向。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | 指向[OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)对象的指针。 |
| [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection) direction | 线性渐变选项的方向。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_LinearGradientOptions_GetDirection()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetDirection(const OH_ArkUI_LinearGradientOptions* options, ArkUI_LinearGradientDirection* direction)
```

**描述**

获取线性渐变选项的方向。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | 指向[OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)对象的指针。 |
| [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection)* direction | 线性渐变选项的方向。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_LinearGradientOptions_SetRepeating()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetRepeating(OH_ArkUI_LinearGradientOptions* options, bool repeating)
```

**描述**

设置颜色是否在线性渐变选项中重复。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | 指向[OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)对象的指针。 |
| bool repeating | 颜色是否在线性渐变选项中重复，false表示不重复着色，true表示重复着色。默认值：false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_LinearGradientOptions_GetRepeating()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetRepeating(const OH_ArkUI_LinearGradientOptions* options, bool* repeating)
```

**描述**

查询线性渐变选项中颜色是否重复。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | 指向[OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)对象的指针。 |
| bool* repeating | 指向线性渐变选项中颜色是否重复的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_LinearGradientOptions_SetColorStop()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_SetColorStop(OH_ArkUI_LinearGradientOptions* options, const uint32_t* colors, const float* stops, int32_t colorsAndStopsSize)
```

**描述**

设置线性渐变选项的颜色停止点。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | 指向[OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)对象的指针。 |
| const uint32_t* colors | 指向颜色数组的指针。 |
| const float* stops | 指向颜色停止点数组的指针。 |
| int32_t colorsAndStopsSize | 颜色和颜色停止点中的元素数量。颜色和颜色停止点的元素数量必须相同。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_LinearGradientOptions_GetColorStop()

```c
ArkUI_ErrorCode OH_ArkUI_LinearGradientOptions_GetColorStop(const OH_ArkUI_LinearGradientOptions* options, uint32_t* colors, float* stops, int32_t colorsAndStopsSize, int32_t* writeLength)
```

**描述**

获取线性渐变选项的颜色停止点。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)* options | 指向[OH_ArkUI_LinearGradientOptions](capi-arkui-nativemodule-oh-arkui-lineargradientoptions.md)对象的指针。 |
| uint32_t* colors | 指向颜色数组的指针。 |
| float* stops | 指向颜色停止点数组的指针。 |
| int32_t colorsAndStopsSize | 颜色和颜色停止点中的元素数量。颜色和颜色停止点的元素数量必须相同。 |
| int32_t* writeLength | 实际写入的颜色及颜色停止点数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_RadialGradientOptions_Create()

```c
OH_ArkUI_RadialGradientOptions* OH_ArkUI_RadialGradientOptions_Create()
```

**描述**

创建一个径向渐变选项对象。

**起始版本：** 26.0.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions*](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md) | 指向[OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)对象的指针。 |

### OH_ArkUI_RadialGradientOptions_Destroy()

```c
void OH_ArkUI_RadialGradientOptions_Destroy(OH_ArkUI_RadialGradientOptions* options)
```

**描述**

销毁一个径向渐变选项对象。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | 指向[OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)对象的指针。 |

### OH_ArkUI_RadialGradientOptions_SetCenterX()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetCenterX(OH_ArkUI_RadialGradientOptions* options, float centerX)
```

**描述**

设置径向渐变选项中心点的X坐标。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | 指向[OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)对象的指针。 |
| float centerX | 径向渐变选项中心点的X坐标。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_RadialGradientOptions_GetCenterX()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetCenterX(const OH_ArkUI_RadialGradientOptions* options, float* centerX)
```

**描述**

获取径向渐变选项中心点的X坐标。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | 指向[OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)对象的指针。 |
| float* centerX | 指向径向渐变选项中心点的X坐标。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_RadialGradientOptions_SetCenterY()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetCenterY(OH_ArkUI_RadialGradientOptions* options, float centerY)
```

**描述**

设置径向渐变选项中心点的Y坐标。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | 指向[OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)对象的指针。 |
| float centerY | 径向渐变选项中心点的Y坐标。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_RadialGradientOptions_GetCenterY()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetCenterY(const OH_ArkUI_RadialGradientOptions* options, float* centerY)
```

**描述**

获取径向渐变选项中心点的Y坐标。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | 指向[OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)对象的指针。 |
| float* centerY | 指向径向渐变选项中心点的Y坐标。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_RadialGradientOptions_SetRadius()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetRadius(OH_ArkUI_RadialGradientOptions* options, float radius)
```

**描述**

设置径向渐变选项的半径。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | 指向[OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)对象的指针。 |
| float radius | 径向渐变选项的半径。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_RadialGradientOptions_GetRadius()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetRadius(const OH_ArkUI_RadialGradientOptions* options, float* radius)
```

**描述**

获取径向渐变选项的半径。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | 指向[OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)对象的指针。 |
| float* radius | 指向径向渐变选项的半径的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_RadialGradientOptions_SetRepeating()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetRepeating(OH_ArkUI_RadialGradientOptions* options, bool repeating)
```

**描述**

设置径向渐变选项中颜色是否重复。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | 指向[OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)对象的指针。 |
| bool repeating | 径向渐变选项中颜色是否重复，false表示不重复着色，true表示重复着色。默认值：false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_RadialGradientOptions_GetRepeating()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetRepeating(const OH_ArkUI_RadialGradientOptions* options, bool* repeating)
```

**描述**

查询径向渐变选项中颜色是否重复。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | 指向[OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)对象的指针。 |
| bool* repeating | 指向径向渐变选项中颜色是否重复的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_RadialGradientOptions_SetColorStop()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_SetColorStop(OH_ArkUI_RadialGradientOptions* options, const uint32_t* colors, const float* stops, int32_t colorsAndStopsSize)
```

**描述**

设置径向渐变选项的颜色停止点。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | 指向[OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)对象的指针。 |
| const uint32_t* colors | 指向颜色数组的指针。 |
| const float* stops | 指向颜色停止点数组的指针。 |
| int32_t colorsAndStopsSize | 颜色和颜色停止点中的元素数量。颜色和颜色停止点的元素数量必须相同。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |

### OH_ArkUI_RadialGradientOptions_GetColorStop()

```c
ArkUI_ErrorCode OH_ArkUI_RadialGradientOptions_GetColorStop(const OH_ArkUI_RadialGradientOptions* options, uint32_t* colors, float* stops, int32_t colorsAndStopsSize, int32_t* writeLength)
```

**描述**

获取径向渐变选项的颜色停止点。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)* options | 指向[OH_ArkUI_RadialGradientOptions](capi-arkui-nativemodule-oh-arkui-radialgradientoptions.md)对象的指针。 |
| uint32_t* colors | 指向颜色数组的缓冲区指针。 |
| float* stops | 指向颜色停止点数组的指针。 |
| int32_t colorsAndStopsSize | 颜色和颜色停止点中的元素数量。颜色和颜色停止点的元素数量必须相同。 |
| int32_t* writeLength | 实际写入的颜色停止点数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 操作结果码。<br> 操作成功时，返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)。<br> 参数异常时，返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)。 |