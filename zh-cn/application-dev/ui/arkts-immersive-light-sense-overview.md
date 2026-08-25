# 沉浸光感简介
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->


从API版本26.0.0开始，ArkUI新增沉浸光感。

当用户唤起弹窗时，弹窗边缘泛着柔和的光泽，背后的内容透过沉浸式系统材质若隐若现；当用户展开菜单时，弹出过程伴随细腻的形变与流光；当用户浏览内容时，悬浮其上的工具栏呈现出轻盈通透的质感——沉浸光感正是为这些场景而生。它是ArkUI提供的一套高品质视觉与动效体系，将光影质感与灵动的动态表现相结合，帮助应用建立清晰的视觉层次，并在不同设备上保持和谐一致的观感。沉浸光感包含两部分能力：

- **沉浸式系统材质**：为组件赋予轻盈通透的质感，让内容透过材质层自然渗透，配合折射、高光、阴影等多层效果，使弹窗、菜单、工具栏等浮层元素在内容之上建立清晰的视觉层次。系统提供从超薄到超厚的五种材质样式，覆盖从浮动工具栏到弹窗的不同透光需求。
- **沉浸式空间动效**：为弹窗和菜单的弹出过程增添形变、流光等动态表现，让每一次弹出都灵动自然。

应用默认升级到API 26后，Dialog、文本选择菜单、Toast、AlphabetIndexer四个组件会默认开启沉浸式系统材质。通过[应用级接入](arkts-immersive-light-sense-enable.md#应用级接入)即可开启沉浸光感，Dialog、菜单、Chip等组件默认支持，跟随系统默认样式时无需额外代码改动即可获得高品质的视觉表现。开发者也可以为自定义组件单独设置沉浸式系统材质。

沉浸光感能够根据设备的算力档位和用户在系统设置中配置的沉浸光感效果，自适应地调整沉浸式系统材质和动效的表现程度，不支持跨算力设备设置材质；沉浸式系统材质还会随系统深浅色模式自动切换效果，确保应用在不同使用环境下都能呈现最佳效果。

开发过程中的常见问题请参见[沉浸光感常见问题](arkts-immersive-light-sense-faq.md)。

## 能力范围

沉浸光感提供应用级配置开关和组件级灵活接入两种接入能力，开发者可以按场景选择接入粒度。

**应用级配置开关**

应用在[module.json5](../quick-start/module-configuration-file.md)中配置"ohos.arkui.UIMaterial.state"配置项，统一控制组件的沉浸式系统材质：配置为default（DEFAULT模式）时，[弹窗](arkts-base-dialog-overview.md)、[即时反馈](arkts-create-toast.md)等组件将开启沉浸式系统材质；配置为enable（ENABLE模式）时，[菜单](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md)、[Chip](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-Chip.md)、[Select](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md)、[SegmentButton](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SegmentButton.md)等更多组件默认开启沉浸式系统材质；配置为disable（DISABLE模式）时，全局禁用沉浸式系统材质。若组件已设置背景色、背景模糊、阴影、边框等自定义样式，仍需应用适配处理样式与沉浸式系统材质的冲突。各模式默认开启的完整组件清单与配置方法详见[应用级接入](arkts-immersive-light-sense-enable.md#应用级接入)。

**组件级灵活接入**

除上述默认支持的组件外，开发者还可以为任意组件单独设置沉浸光感效果：

- 通过通用属性[systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial)为组件设置沉浸式系统材质。
- 通过组件options参数中的systemMaterial字段为Toast、Popup、Tips、半模态bindSheet、菜单bindMenu等弹窗类组件设置沉浸式系统材质。
- Select组件的下拉按钮与下拉菜单分别通过[systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial)和[menuSystemMaterial](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#menusystemmaterial)独立控制，可分别开启或关闭。

## 亮点特征

### 沉浸式系统材质

沉浸式系统材质为组件赋予轻盈通透的质感：材质滤镜、折射、高光、阴影等多层效果叠加，让底层内容透过材质层自然渗透，带来远超纯色背景的高端视觉表现。开发者只需设置一处沉浸式系统材质，组件的背景、边框、阴影等视觉效果即由沉浸式系统材质统一接管，随深浅色模式与设备算力自动适配，无需逐项调配。

沉浸式系统材质提供从薄到厚的五种样式：

| 样式 | 说明 | 适用场景 |
| --- | --- | --- |
| ULTRA_THIN | 超薄样式，材质层具有很强的透明效果。 | 需要高度透明的背景，如浮动工具栏。 |
| THIN | 薄样式，材质层具有较强的透明效果。 | 需要较强透明度的场景，如搜索框。 |
| REGULAR | 常规样式，材质层厚度常规。 | 通用场景。 |
| THICK | 厚样式，模糊效果强。 | 需要较强模糊背景的场景，如菜单。 |
| ULTRA_THICK | 超厚样式，模糊效果很强。 | 需要完全模糊背景的场景，如弹窗。 |

此外，沉浸式系统材质还支持赋色、自动反色、阴影开关、交互形变与点光源等个性化配置，具体使用方法请参见[定制沉浸式系统材质效果](arkts-immersive-light-sense-common-capability.md)。


### 沉浸式空间动效

为组件设置了沉浸式系统材质后，在高算力设备上，[Dialog](arkts-base-dialog-overview.md)和[菜单控制](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md)的弹出过程会自动附带形变、流光等沉浸式空间动效，使动画更加灵动流畅。动效无需开发者额外配置，由系统根据设备算力档位和系统沉浸光感强度配置自动决定是否生效：在高算力设备上，沉浸光感强度设置为强或均衡时生效；在中算力设备上，沉浸光感强度设置为强时生效；低算力设备不支持沉浸式空间动效。

## 和相关Kit的关系

<!--RP1--><!--RP1End-->
