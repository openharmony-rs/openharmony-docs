# 沉浸光感简介
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->


从API版本26.0.0开始，ArkUI新增沉浸光感。

沉浸光感是ArkUI提供的一套从“视觉层”到“感知层”的体验，将光影材质与交互动效表现相结合，帮助应用建立清晰的视觉层次，并在不同设备上保持和谐一致的观感。例如：用户展开菜单时，伴随着形变弹出打破生硬的规整边界，边缘流光勾勒着面板轮廓，将菜单的弹出操作转化为富有沉浸感的体验。

![materialPage](figures/materialPage.gif)

沉浸光感包含[沉浸式系统材质](#沉浸式系统材质)与[沉浸式空间动效](#沉浸式空间动效)两部分能力，前者为组件赋予轻盈通透的质感、在内容之上建立清晰的视觉层次，后者为弹窗和菜单的弹出过程增添灵动自然的动态表现。

沉浸光感会根据设备算力和用户在系统中设置的沉浸光感效果，自适应地调整沉浸式系统材质和沉浸式空间动效的表现程度，其中算力档位由设备定义且固定，可通过获取材质等级接口（[uiMaterial.getGlobalMaterialLevel](../reference/apis-arkui/arkts-apis-uimaterial.md#uimaterialgetglobalmateriallevel)）查询<!--RP1--><!--RP1End-->。沉浸式系统材质还会随系统深浅色模式自动切换效果，确保应用在不同使用环境下都能呈现最佳效果。

## 关键技术

### 沉浸式系统材质

沉浸式系统材质为组件赋予轻盈通透的质感：材质滤镜、折射、高光、阴影等多层效果叠加，让底层内容透过材质层自然渗透，带来远超纯色背景的高端视觉表现。开发者只需[开启沉浸光感](arkts-immersive-light-sense-enable.md)，组件的背景、边框、阴影等视觉效果即由沉浸式系统材质统一接管，随深浅色模式与设备算力自动适配。

沉浸式系统材质提供从超薄到超厚的五种样式<!--RP2--><!--RP2End-->。开启沉浸光感后不同组件的默认样式存在差异，具体请参考[组件适配沉浸光感](./arkts-immersive-light-sense-component-adaptation.md)。

| 样式 | 说明 | 适用场景 |
| --- | --- | --- |
| ULTRA_THIN | 超薄样式，材质层具有很强的透明效果。 | 高度透明的背景，如浮动工具栏。 |
| THIN | 薄样式，材质层具有较强的透明效果。 | 较强透明度的场景，如搜索框。 |
| REGULAR | 常规样式，材质层厚度常规。 | 通用场景。 |
| THICK | 厚样式，模糊效果强。 | 较强模糊背景的场景，如菜单。 |
| ULTRA_THICK | 超厚样式，模糊效果很强。 | 完全模糊背景的场景，如弹窗。 |

此外，沉浸式系统材质还支持自动反色、材质赋色、交互形变与点光源、阴影开关等个性化配置，具体使用方法请参见[沉浸式系统材质视效](arkts-immersive-light-sense-common-capability.md)。

### 沉浸式空间动效
沉浸式空间动效，将光的行为凝练为三种相互呼应的动效类型，具体请参考下表。沉浸式空间动效会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

| 动效类型 | 说明 | 支持的组件 |
| --- | --- | --- |
| 非线性形变 | 实现光影形体的动态蜕变，打破规整边界带来柔和自然的空间过渡。 | AlertDialog，具体示例请参考[示例9（设置弹窗的沉浸光感效果）](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md#示例9设置弹窗的沉浸光感效果)。<br/>CustomDialog，具体示例请参考[示例14（设置弹窗的沉浸光感效果）](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#示例14设置弹窗的沉浸光感效果)。<br/>ActionSheet，具体示例请参考[示例9（设置弹窗的沉浸光感效果）](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md#示例9设置弹窗的沉浸光感效果)。<br/>菜单控制，具体示例请参考[示例24（设置菜单的沉浸光感）](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#示例24设置菜单的沉浸光感)。 |
| 边缘流光 | 流光塑造视觉焦点与层级秩序，依靠光流走向引导用户的视线流转。 | AlertDialog，具体示例请参考[示例9（设置弹窗的沉浸光感效果）](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md#示例9设置弹窗的沉浸光感效果)。<br/>CustomDialog，具体示例请参考[示例14（设置弹窗的沉浸光感效果）](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#示例14设置弹窗的沉浸光感效果)。<br/>ActionSheet，具体示例请参考[示例9（设置弹窗的沉浸光感效果）](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md#示例9设置弹窗的沉浸光感效果)。<br/>菜单控制，具体示例请参考[示例24（设置菜单的沉浸光感）](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#示例24设置菜单的沉浸光感)。 |
| 粒子动画 | 粒子承载信息具象表达，以粒子光点传递信息变化。 | Slider，具体示例请参考[示例10（设置滑动条的沉浸光感效果）](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#示例10设置滑动条的沉浸光感效果)。 |

### 约束与限制
沉浸光感生效范围请参考[开启沉浸光感](arkts-immersive-light-sense-enable.md)。<br/>
沉浸光感开启后，弹窗类组件以及Slider、Toggle在页面内全部区域可生效；其余组件的生效区域为：Navigation/NavDestination标题栏，或横向Tab中barPosition为BarPosition.End的底部TabBar中。<br/>
弹窗类组件和接口包括：[PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md)、[AlertDialog](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md)、[ActionSheet](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md)、[CustomDialog](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md)、[CalendarPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-calendarpicker-dialog.md)、[DatePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md)、[TimePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-timepicker-dialog.md)、[TextPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-textpicker-dialog.md)、[SelectionMenu](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SelectionMenu.md)、[ArkUI_NativeDialog](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativedialog.md)、[@ohos.promptAction (弹窗)](../reference/apis-arkui/js-apis-promptAction.md)、[Popup控制](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md)、[Tips控制](../reference/apis-arkui/arkui-ts/ts-universal-attributes-tips.md)、[菜单控制](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md)、[半模态转场](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md)、[AlphabetIndexer](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md)气泡弹窗、Select下拉菜单的[menuSystemMaterial](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#menusystemmaterial)、[Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md)设置[copyOption](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#copyoption9)后长按或双击触发的文本菜单。

<!--RP3--><!--RP3End-->
