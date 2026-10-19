# OpenHarmony 7.0 Release

## 版权和许可声明

本项目贡献依据 **《开发者原创声明》（DCO）** 授权给开放原子开源基金会。本项目是由许多开源软件组件组成的汇编作品，该汇编作品的版权归开放原子开源基金会所有。开放原子开源基金会根据Apache 2.0开源许可协议（以下简称 **Apache 2.0** ）向您提供该汇编作品的授权。

在遵守Apache 2.0，以及本项目包含的开源软件组件适用的对应开源许可协议的前提下，您方可使用本项目。您可以通过以下网址获取Apache 2.0副本：
**[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0#/session/_blank)**

除非适用法律要求或书面约定，依据适用的开源许可协议分发的软件均按“原样”提供，且不附带任何（明示或默示）形式的保证或条件。有关适用的开源许可协议的具体授权和限制，请参见其原文。

## 版本概述

OpenHarmony 7.0 Release在6.1 Release版本的基础上进一步增强了系统支持范围和应用开发能力：

- 系统层面，新增支持展锐P7885芯片开发板，并支持轻量系统小型化适配以减少资源占用。

  > **说明：**

  > 系统层面新增能力首次发布于OpenHarmony 6.1 LTS版本。

- 应用框架方面，支持对应用更精细化的控制，比如可获取Ability退出原因、AbilityStage启动加载信息，新增基于ModularObjectExtensionAbility的模块化对象能力及自分发插件管理；ArkUI新增多个V2组件、懒加载布局组件、智慧手势、系统材质、响应式环境变量等能力，进一步提升界面交互体验，支持动态布局容器、Tabs嵌套滚动、自定义组件全局复用等；进一步增强ArkWeb网页控制能力，内核升级至Chromium 144版本，支持URL白名单控制、网页安全配置等；媒体领域新增音频PCM处理与播出、广告插播、离线缓存下载、录屏暂停恢复及音频设备增强管理等功能。此外，还新增压缩解压缩模块、窗口模式设置、多线程检测可配置参数、企业账号与应用管理增强、WebSocket自定义端口、内存导出监听以及统一SDK支持等能力。

具体新增能力如下：

### 系统

标准系统新增支持“展锐P7885芯片开发板”，支持以下能力：
- 支持5G蜂窝通信能力，提供驻网、通话、短信、数据功能。
- 支持统一渲染。
- 支持GNSS卫星状态信息上报，可识别并上报GPS、北斗、GLONASS等卫星数据。
- 适配星闪驱动，支持星闪SLE 1.0，支持星闪配对连接和数据传输。
- 板载适配6类传感器：加速度计、陀螺仪、磁力计、接近传感器、环境光传感器、马达。
- 板载36 PIN标准PCI-E接口，外接板支持USB+千兆以太网接口或者其他标准PCI-E板卡。

轻量系统支持小型化适配，以减少RAM和ROM的使用，详见[轻量系统小型化适配指导](https://gitcode.com/openharmony/docs/blob/master/zh-cn/device-dev/porting/porting-minichip-minimal.md)。

上述能力在OpenHarmony 6.1 LTS版本已经提供支持。

### 元能力

- 新增基于ModularObjectExtensionAbility的模块化对象，支持应用将自身功能以模块化对象的形式开放给其他应用调用。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/application-models/modular-object-extension-overview.md)）
  - 提供基于C API的使用ModularObjectExtensionAbility实现模块化对象的指导。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/application-models/modular-object-extension-development.md)）
  - 支持使用Taihe实现ModularObjectExtensionAbility的IPC通信。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/application-models/modular-object-extension-ability-taihe.md)）
  - 提供声明ModularObject分发器的C API，提供基于类型库元数据的跨进程延迟绑定调用能力。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/capi-modular-object-dispatcher-h.md)）
  - 提供声明ModularObjectExtensionAbility实例的C API，包括注册生命周期回调函数和获取上下文等能力。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/capi-modular-object-extension-ability-h.md)）
  - 提供声明ModularObjectExtensionAbility上下文的C API，包括启动UIAbility、销毁ModularObjectExtensionAbility自身、创建和销毁IPC对象等功能。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/capi-modular-object-extension-context-h.md)）
  - 提供声明用于管理ModularObjectExtensionAbility的C API，包括查询ModularObjectExtensionAbility信息、连接与断开连接等能力。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/capi-modular-object-extension-manager-h.md)）

- 新增提供NativeAbility数据信息的相关C API，用于获取Ability实例ID、Ability名称和napi_env等信息。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/capi-native-ability-wrapper-h.md)）

- 新增声明ExtensionAbility的连接选项的C API，提供包括连接成功、断开连接和连接失败的回调接口。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/capi-connect-options-h.md)）

- 新增自动填充请求信息的定义能力，应用可定义自动填充的信息类型。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-inner-application-autoFillRequest.md)）

- 包管理新增pluginBundleManager模块，提供应用对自分发插件的管理能力，包括安装、卸载本地插件。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-pluginBundleManager.md)）

- Ability上次退出的信息字段新增支持获取退出原因。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#lastexitdetailinfo18)）

- AbilityStage上下文新增launchElement字段，用于在AbilityStage调用onCreate时告知应用正在加载的Ability，从而动态加载资源。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-inner-application-abilityStageContext.md#%E5%B1%9E%E6%80%A7)）

- AbilityStage组件管理器新增AbilityStage即将创建第一个Ability的回调（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onabouttocreateability24)），以及当进程从应用快照启动时的回调（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onlaunchfromhypersnap24)）。

- 新增支持获取指定包名和分身索引的应用名称。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetapplicationlabel)）

- 新增支持用于管理ModularObjectExtensionAbility的C API，提供查询ModularObjectExtensionAbility信息、连接与断开连接等能力。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/capi-modular-object-extension-manager-h.md)）

### 分布式数据管理

- 数据共享能力新增支持发布多个值类型的配置用于多应用共享。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkdata/js-apis-data-dataShare.md#publish20)）

- 新增创建或打开已有的关系型数据库的同步方法。同步方法可阻塞线程直到获取到RdbStore。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstoresync24)）

### 图形

- 绘制模块字体绘制能力新增支持获取文字的轮廓路径，同时支持字体回退能力。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Font.md#gettextpathwithfallback)）

- 新增支持为组件内容添加HDR（高动态范围成像）提亮效果。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkgraphics2d/js-apis-uiEffect.md#hdrbrightnessratio24)）

- 新增支持视频的AIHDR格式。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkgraphics2d/js-apis-hdrCapability.md#hdrformat)）

- 绘制模块新增用于处理坐标点的类，支持对坐标点取反和设置偏移量。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-PointUtils.md)）


### 图像

- 新增[WebP图像元数据类](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-WebPMetadata.md)、[GIF图像元数据类](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-GifMetadata.md)、[JFIF图像元数据类](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-JfifMetadata.md)、[TIFF图像元数据类](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-TiffMetadata.md)、[PNG图像元数据类](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-PngMetadata.md)以及[AVIS图像元数据类](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-AvisMetadata.md)，用于存储对应格式图像的元数据。

- 新增[XMP（Extensible Metadata Platform）元数据](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-XMPMetadata.md)。

### ArkUI

- 新增多个基于状态管理（V2）实现的组件，包括[ChipV2](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipV2.md)、[ChipGroupV2](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroupV2.md)、[CounterV2](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-CounterV2.md)、[PopupV2](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-PopupV2.md)、[SwipeRefresherV2](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SwipeRefresherV2.md)、[TreeViewV2](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-TreeViewV2.md)。

- 新增智慧手势的能力（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/ui/arkts-common-events-smartgesture-event.md)）：
  - 新增智慧手势的API，提供智慧手势使能、监听、选中态控制，以及动态决策智慧手势行为的能力。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkts-apis-uicontext-smartgesturecontroller.md)）
  - 交互属性新增对智慧手势的响应。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-smart-gesture-shortcut.md)）

- 滚动与滑动组件新增懒加载瀑布流布局组件[LazyVWaterFlowLayout](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-container-lazyvwaterflowlayout.md)、懒加载垂直线性布局组件[LazyColumnLayout](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-container-lazycolumnlayout.md)、懒加载动态布局容器组件[LazyDynamicLayout](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-container-lazydynamiclayout.md)。

- 响应式环境变量组件新增环境变量容器[WithEnv](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-container-with-env.md)、自定义环境变量[@CustomEnv](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-custom-env-property.md)。

- 新增DatePickerComponent组件，用于选择日期（年月日）和时间（时分秒）。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-DatePickerComponent.md)）

- 新增SelectionContainer组件，用于为多个文本节点提供跨节点文本选中、复制及菜单扩展能力。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-selectioncontainer.md)）

- 新增支持设置调测标签，帮助开发者分辨同类节点，提高开发和分析调试的效率。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-inspector-label.md)）

- ChipGroup组件新增支持通过backgroundSystemMaterial和activatedBackgroundSystemMaterial配置正常状态和激活状态下的系统材质背景。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroup.md#%E7%A4%BA%E4%BE%8B6%E8%AE%BE%E7%BD%AE%E7%B3%BB%E7%BB%9F%E6%9D%90%E8%B4%A8%E6%A0%B7%E5%BC%8F)）

- SelectionMenu组件新增支持通过backgroundSystemMaterial配置菜单的背景板的系统材质。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SelectionMenu.md#%E7%A4%BA%E4%BE%8B3%E8%AE%BE%E7%BD%AE%E8%83%8C%E6%99%AF%E6%9D%BF%E6%9D%90%E8%B4%A8)）

- Navigation组件新增配置项systemMaterial属性，支持系统材质效果。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#示例20设置systemmaterial开启标题栏材质效果)）

- 弹窗类组件DatePickerDialog新增配置项systemMaterial，支持系统材质效果。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions对象说明)）

- C API新增沉浸式材质类型和API声明。（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-native-material-h.md)）

- 组件动态属性新增悬浮状态样式。（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#applyhoveredattribute)、[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-common-attributes-h.md#arkui_uistate)）

- UIContext的OverlayManager新增按层级配置浮层的能力。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkts-apis-uicontext-overlaymanager.md#openorderoverlay)）

- 文本类组件新增支持尾部缩进属性（tailIndents），包括：Text组件（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-text.md#tailindents)、[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_tail_indents)）、属性字符串（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#%E5%B1%9E%E6%80%A7-9)、[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-styled-string-h.md#oh_arkui_paragraphstyle_settailindents)）

- 自定义组件的生命周期新增支持组件由非激活状态转变为激活状态的装饰器[@ComponentActive](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentactive)，以及组件由激活状态转变为非激活状态的装饰器[@ComponentInactive](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentinactive)。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/ui/state-management/arkts-custom-components-new-lifecycle.md#%E8%87%AA%E5%AE%9A%E4%B9%89%E7%BB%84%E4%BB%B6%E7%9A%84%E6%BF%80%E6%B4%BB%E4%B8%8E%E9%9D%9E%E6%BF%80%E6%B4%BB%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F)）

- 自定义组件支持跨Ability迁移。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/ui/state-management/arkts-create-custom-components.md#%E8%87%AA%E5%AE%9A%E4%B9%89%E7%BB%84%E4%BB%B6%E6%94%AF%E6%8C%81%E8%B7%A8ability%E8%BF%81%E7%A7%BB)）

- 新增多个组件的C API：[OH_ArkUI_DecorationStyleOptions](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)、[OH_ArkUI_TextDataDetectorConfig](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)、[OH_ArkUI_TextEditorSelectionMenuOptions](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)、[OH_ArkUI_TextEditorPlaceholderOptions](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)、[OH_ArkUI_TextEditorStyledStringController](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)、[OH_ArkUI_TextEditorParagraphStyle](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md)、[OH_ArkUI_ShadowOptions](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-shadowoptions.md)、[OH_ArkUI_TextEditorTextStyle](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md)。

- 新增一批属性字符串的C API。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-styled-string-h.md#oh_arkui_styledstringkey)）

- 支持将含有竞争策略的事件分发到目标UI组件节点。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/js-apis-arkui-builderNode.md#postinputeventwithstrategy24)）

- 新增支持获取UIContext对应页面的根节点。（[ArkTS API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getpagerootnode24)、[C API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-native-node-h.md#oh_arkui_nativemodule_getpagerootnodehandlebycontext)）

- Text组件新增支持根据坐标获取最近的字符的位置信息。（[ArkTS API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-text-common.md#getcharacterpositionatcoordinate24)、[C API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-styled-string-h.md#oh_arkui_textlayoutmanager_getcharacterpositionatcoordinate)）

- 新增拖拽异步通知接口，可以在拖拽的落入行为中指定采取剪切或者复制的处理方式（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-drag-and-drop-h.md#oh_arkui_notifysuggesteddropoperation)），以及指定是否执行拖拽落入行为的动效（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-drag-and-drop-h.md#oh_arkui_notifydisabledefaultdropanimation)）。

- 新增onNeedSoftkeyboard回调，支持开发者配置焦点转移后不关闭拉起的软键盘。（[ArkTS API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-events-onneedsoftkeyboard.md)、[C API参考-NODE_ON_NEED_SOFTKEYBOARD](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)）

- CanvasRenderingContext2D（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-components-canvas-common-property.md#antialias24)）和OffscreenCanvasRenderingContext2D（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-offscreencanvasrenderingcontext2d.md#antialias24)）新增antialias属性，支持关闭文本抗锯齿功能。

- 分段按钮新增enableStateAnimation配置项，用于指定selectedIndexes在绑定的状态变量发生变化时是否执行系统动画。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SegmentButton.md#segmentbutton-1)）

- Tabs组件新增支持嵌套滚动能力。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-container-tabs.md#nestedscroll24)）

- JS组件新增支持旋转表冠事件监听接口。（[API参考-ArkUI.Full](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-js/js-components-common-monitorcrownevents.md)、[API参考-ArkUI.Lite](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-js-lite/js-lite-common-monitorcrownevents.md)）

- 多行文本的缩略模式新增支持设置为省略行首内容（MULTILINE_START）或省略行中内容（MULTILINE_CENTER）。（[ArkTS API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-appendix-enums.md#ellipsismode11)、[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/capi-native-type-h.md#arkui_ellipsismode)）

- 新增动态布局容器组件，支持在运行时动态切换不同的布局算法，不改变子组件的状态。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/ui/arkts-layout-development-dynamiclayout.md)）

- 新增自定义组件全局复用能力，可针对指定\@Reusable/\@ReusableV2复用组件配置复用池，用于提供全局复用的能力。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/ui/state-management/arkts-global-reuse-pool.md)）

### 窗口管理

- 新增支持设置主窗或子窗支持的窗口模式。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkts-apis-window-Window.md#setsupportedwindowmodes)）

- 新增支持按需销毁窗口（WindowStage）的页面内容（UIContent）。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkts-apis-window-WindowStage.md#releaseuicontent24)）

- 新增闪控窗。闪控窗是悬浮在桌面/应用界面上的小型窗口，提供灵活的窗口管理能力，包括判断设备是否支持闪控窗功能、创建闪控窗控制器以启动、更新或停止闪控窗等。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/js-apis-floatView.md)）

### ArkWeb

- ArkWeb基于上游社区的Chromium内核从132升级为144版本。详情请参考[ArkWeb 版本的差异总结](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/ArkWeb_132_144.md)。

- ArkWeb网页请求支持User-Agent Client Hints功能。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkweb/arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24)）

- ArkWeb新增默认右键菜单启用开关，可通过该接口控制默认的右键菜单是否开启。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkweb/arkts-basic-components-web-attributes.md#enabledefaultcontextmenu24)）

- 设置Web页的URL白名单，只有白名单内的URL才能允许加载/跳转，否则将拦截并弹出告警页。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkweb/arkts-apis-webview-WebviewController.md#seturltrustlist24)）

- 在下载任务完成的回调中，新增支持获取下载项的原始URL地址（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkweb/arkts-apis-webview-WebDownloadItem.md#getoriginalurl24)）；新增支持获取引用页的URL地址（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkweb/arkts-apis-webview-WebDownloadItem.md#getreferrerurl24)）。

- 新增安全特性选项配置的类，用于设置网页的安全配置属性。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkweb/arkts-apis-webview-SecurityParams.md)）

### ArkTS语言编译器运行时

- 虚拟机维测能力增强：
  - 新增支持获取所有虚拟机线程的堆内存信息，包括线程ID、线程名称、堆类型和堆对象大小。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkts/js-apis-util.md#getallvmheapmemoryinfo24)）
  - 新增堆内存超过预警阈值的回调函数，在虚拟机主线程完成垃圾回收后如果堆内存仍超过预警阈值则触发回调执行。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkts/js-apis-util.md#onvmheapmemorypressure24)）

- taskpool的execute方法增强，执行任务或任务组可以指定任务超时时长。如果任务或任务组的执行时间超过设置的超时时长，则抛出对应错误信息。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkts/js-apis-taskpool.md#taskpoolexecute24)）

- 新增enableLocalHandleDetection接口，保证EventHandler和libuv机制的任务在scope范围内执行，从而避免内存泄漏。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkts/js-apis-util.md#enablelocalhandledetection24)）

- XML解析新增支持XmlSAXHandler，定义了SAX解析xml文本时的回调方法。开发者需要实现这些回调方法来处理xml文本的不同部分。这些回调方法会在xml解析过程的对应时机触发。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkts/js-apis-xml.md#xmlsaxhandler24)）

- ArkTS运行时提供了多种模块化调试工具，帮助开发者快速定位和解决模块化相关问题。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/arkts-utils/arkts-module-debug.md)）

- setMultithreadingDetectionEnabled接口新增多线程检测可配置参数，支持开发者配置故障类型、采样频率、故障上报时间间隔。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkts/js-apis-util.md#multithreadingdetectionoptions)）

### 媒体

**媒体管理**

- 新增C API，支持对音频PCM数据处理后再播出的能力（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setpcmprocessorcallback)），同时支持设置音频处理后再播出的回调函数单次可返回的最大数据量（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setpcmprocessormaxlen)）。

- 新增ArkTS API，支持广告插播能力，实现广告资源的播放以及广告事件的监听。（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/arkts-apis-media-AVAdsController.md)）

- 新增ArkTS API，实现应用可以离线缓存下载在线资源。（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/arkts-apis-media-AVDownloaderManager.md)）

- 新增ArkTS API和C API，支持录屏过程中暂停录制屏幕与恢复录制屏幕的能力。（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/arkts-apis-media-i.md#avscreencapturestrategy20)、[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforpause)）

- 新增C API，支持对指定应用的所有窗口进行屏幕录制。（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-base-h.md#oh_capturepickermode)）

- C API新增隐私保护设置的回调函数，用于响应截屏录屏时捕获的隐私保护事件。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setprivacyprotectcallback)）

- C API新增支持获取多屏幕录制能力信息（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_getmultidisplaycapturecapability)），以及通过DisplayID选择多屏幕进行录制（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_getmultidisplayidsselected)）。

**音频**

- 新增音频设备增强管理器功能。（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md)、[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md)）

- 新增基于C/C++的音频格式转换能力。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/media/audio/audio-suite-format-converter.md)）

- 音频采集和音频渲染新增支持设置独立的音频会话策略和行为参数。（[API参考-音频采集](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/arkts-apis-audio-AudioCapturer.md#setindependentaudiosessionstrategy24)、[API参考-音频渲染](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#setindependentaudiosessionstrategy24)）

- 新增OH_MIDI的C API，支持应用通过USB或蓝牙BLE连接外接MIDI设备（如MIDI键盘、电子琴、MIDI控制器等），实现MIDI消息的收发、设备枚举与热插拔监听，可用于音乐创作、乐器录制与教学、MIDI设备控制等场景。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/media/audio/midi-overview.md)）

- 新增C API，提供声明输入音频格式、输出音频格式底层数据结构和格式转换接口的定义。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/capi-native-audio-converter-h.md)）

**播控框架**

- 新增支持设置应用支持的播放倍速列表。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setsupportedplayspeeds)）

- 新增支持设置应用支持的循环模式列表。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setsupportedloopmodes)）

- 新增支持设置应用支持的控制类型列表。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setmediacentercontroltype)）

- 通过AVSessionController新增获取应用支持的播放倍速列表。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#getsupportedplayspeeds)）

- 通过AVSessionController新增获取应用支持的循环模式列表。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#getsupportedloopmodes)）

- 通过AVSessionController新增获取应用支持的控制类型列表。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#getmediacentercontroltype)）

- 新增注册播放倍速列表变化的监听事件。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#onsupportedplayspeedschange)）

- 新增注册循环模式列表变化的监听事件。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#onsupportedloopmodeschange)）

- 新增注册控制类型列表变化的监听事件。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#onmediacentercontroltypechanged)）

- 新增支持后台播放模式的设置，可由应用告知系统是否支持后台播放，系统根据能力决策实况胶囊的显示。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setbackgroundplaymode24)）

- AVSession的枚举新增定义了在不同场景中使用的额外键的枚举。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-e.md#extrakey)）

**相机**

- C API新增元数据对象扩展概念的声明。（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-camera-kit/capi-metadata-object-ext-h.md)）

- 新增支持创建延迟预览输出对象，在配流时替代普通的预览输出对象加入数据流（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createdeferredpreviewoutput24)）。同时支持配置延迟预览的Surface（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#adddeferredsurface24)）。

- 新增一批拍照/录像模式下的相机专业能力，包括闪光灯、光学防抖、曝光、手动对焦、ISO感光度、物理光圈的调用和设置。

**音视频编解码**

- 新增支持Cinepak媒体格式的编解码能力。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/media/avcodec/avcodec-support-formats.md#%E5%AA%92%E4%BD%93%E7%BC%96%E8%A7%A3%E7%A0%81)）

- 新增支持筛选特定MIME类型的安全解码器，在处理受数字版权管理保护的DRM媒体资源时，可以使用支持安全链路的"安全解码器"。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/media/avcodec/obtain-supported-codecs.md#%E7%AD%9B%E9%80%89%E7%89%B9%E5%AE%9Amime%E7%B1%BB%E5%9E%8B%E7%9A%84%E5%AE%89%E5%85%A8%E8%A7%A3%E7%A0%81%E5%99%A8drm%E6%92%AD%E6%94%BE%E5%9C%BA%E6%99%AF)）

- H265硬件编码器新增支持CBRHQ（高质量恒定码率模式）。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/media/avcodec/video-encoding-configuration-typical-scenarios.md#%E4%BD%8E%E6%97%B6%E5%BB%B6%E5%9C%BA%E6%99%AF)）

### 文件管理

- 新增支持压缩解压缩模块，为应用提供数据压缩和解压缩的能力，可用于文件打包分发、减少存储占用、加速网络传输等场景。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/file-management/archive-overview.md)）

- 打开文件或目录时新增参数UNCACHE，支持读写文件不进行页缓存。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-core-file-kit/js-apis-file-fs.md#fileioopen)）

- 新增listFileExt方法支持递归列出和自定义文件名过滤。可通过配置options中recursion参数实现递归列出所有文件的相对路径。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-core-file-kit/js-apis-file-fs.md#fileiolistfileext)）

- 新增支持开发者通过文件mmap能力集（基于文件描述符或文件对象创建文件映射对象），实现文件的高效读写访问。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-core-file-kit/js-apis-file-fs.md#fileiommap)）

- 新增支持应用捐献自身沙箱目录给系统设置为共享，其他应用可以通过文管直接获取到目录里的文件。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/file-management/share-app-file-configuration.md)）

### 企业定制服务

- 企业设备的账号管理新增创建普通系统账号（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-accountManager.md#accountmanagercreatenormalosaccount)）、移除系统账号（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-accountManager.md#accountmanagerremoveosaccount)）以及切换系统账号（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-accountManager.md#accountmanageractivateosaccount)）的接口。

- 企业设备的应用管理新增支持查询指定应用的窗口状态信息列表。可查询应用是否在底部Dock栏、当前应用窗口是否在前台显示等信息。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-applicationManager.md#applicationmanagergetapplicationwindowstates)）

- kiosk模式下，新增支持通过上划停留手势进入最近任务栏（ALLOW_GESTURE_CONTROL）以及通过边缘内划停留手势进入侧边DOCK栏（ALLOW_SIDE_DOCK）。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-applicationManager.md#kioskfeature20)）

- 新增支持安装和卸载企业重签名证书的能力。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanagerinstallenterpriseresignaturecertificate24)）

- 新增支持根据位置索引添加应用到PC/2in1设备的底部快捷栏的能力。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-applicationManager.md#applicationmanageradddockapp24)）

- 设备设置管理支持对当前用户下被隐藏的设置项列表进行添加、删除、查询操作。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-deviceSettings.md#devicesettingsaddhiddensettingsmenu24)）


### 后台任务管理

提醒的倒计时实例对象新增参数重复周期（repeatInterval）和重复次数（repeatCount）。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-backgroundtasks-kit/js-apis-reminderAgentManager.md#reminderrequesttimer)）


### 基础通信

- 新增支持通过C API获取Wi-Fi连接信息。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-connectivity-kit/capi-oh-wifi-h.md#oh_wifi_getlinkedinfo)）

- 新增A2DP的播放状态广播以及SCO广播事件。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_bluetooth_a2dpsource_play_state_change24)）

### 网络管理

- 建立WebSocket连接的可选参数新增支持supportOriginPort，可用于控制Origin字段是否携带自定义端口号。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-network-kit/js-apis-webSocket.md#websocketrequestoptions)）

- TLS支持证书链的验证，可通过传入数组的方式最多支持到1000个证书。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-network-kit/js-apis-socket.md#tlssecureoptions9)）

### 内容嵌入服务

新增Content Embed内容嵌入服务，提供应用间文档互相嵌入与协同编辑的框架能力，并为开发者封装了客户端与服务端的开发接口，便于快速实现文档跨应用嵌入与协作。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/content-embed/content-embed-kit-overview.md)、[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-content-embed-kit/capi-contentembed.md)）

### 卡片

在onUpdateForm回调中新增支持卡片更新原因字段。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-form-kit/js-apis-app-form-formInfo.md#formupdatereason24)）

### DFX

- HiDebug新增支持注册内存导出监听器，用于在内存占用较高或通过hidumper命令手动触发时导出应用内存快照。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/dfx/hidebug-guidelines.md#导出内存快照)、[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-performance-analysis-kit/capi-hidebug-h.md#oh_hidebug_registermemdumplistener)）

- 当应用发生SIGPIPE异常退出时，在Debug版本应用可开启SIGPIPE信号打印调用栈功能辅助定位问题。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/dfx/cppcrash-guidelines.md#%E5%BA%94%E7%94%A8%E5%8F%91%E7%94%9Fsigpipe%E5%BC%82%E5%B8%B8%E9%80%80%E5%87%BA)）

HiProfiler新增文件缓存模式（use_file_cache_mode），通过将缓存数据落盘，提升内存分配信息的采集性能。

- HiDebug新增资源采集功能，支持按需采集应用进程资源分配栈至沙箱，覆盖文件描述符、线程、Native/GPU内存及全局句柄等类别，辅助定位资源泄漏。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/dfx/hidebug-guidelines.md)）

- HiDebug新增支持获取应用程序进程的物理内存使用信息。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-performance-analysis-kit/js-apis-hidebug.md#hidebuggetrssinfo24)）

- HiDebug新增支持将转储的堆快照由线程级改为进程级。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-performance-analysis-kit/js-apis-hidebug.md#hidebugsetprocdumpinsharedoom24)）

- HiDebug新增提供包括内核信息在内的Trace采集请求接口。（[ArkTS API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-performance-analysis-kit/js-apis-hidebug.md#hidebugrequesttrace24)、[C API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-performance-analysis-kit/capi-hidebug-h.md#oh_hidebug_requesttrace)）

- HiAppEvent新增应用冻屏告警事件，提供事件的订阅能力。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/dfx/hiappevent-watcher-appfreezewarning-events.md)）

### 多模输入

- 新增输入事件注入模块，提供键盘和鼠标输入事件模拟能力。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-input-kit/js-apis-inputeventclient.md)）

- C API输入事件增强，提供输入事件的压力、相对窗口左上角的XY相对坐标等事件。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-input-kit/capi-oh-input-manager-h.md#oh_input_settoucheventpressure)）


### 通知

- 新增支持查询本APP通知中wantAgent字段的部分信息。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanagergetnotificationparameters24)）

- 新增支持使用应用沙箱内的文件作为通知的自定义铃声。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/notification/notification-customized-ringtone.md)）

- 新增是否开启锁屏通知等字段。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-notification-kit/js-apis-notificationManager.md#notificationsetting20)）

- 新增支持以半模态方式拉起应用的通知设置界面。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanageropennotificationsettingswithresult)）

### NDK

JSVM新增支持从外部内存创建ArrayBuffer对象。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/common/capi-jsvm-h.md#oh_jsvm_createarraybufferfromexternalmemory)）

### 其他

新增对统一SDK的支持。统一SDK是面向OpenHarmony生态提供的标准化开发工具套件，扩展了OpenHarmony SDK的能力，为开发者提供远场通信、基础语音、分享服务、基础视觉、桌面拓展、文件预览、推送服务、统一扫码服务等多维度开发能力。详见[HarmonyOS SDK for OpenHarmony](https://gitcode.com/harmonyos-sdk-for-openharmony/docs/blob/6.1-release/README.md)。

## 系统应用更新说明

### 新增系统应用  

针对展锐P7885芯片开发板，新增如下系统应用：

#### [文件管理](https://gitcode.com/openharmony/applications_filepicker)

- 支持外置存储浏览。
- 支持文管内访问图库。
- 支持文件Picker（选择、后缀过滤、批量授权）。
- 支持通过路径Picker保存文件。
- 支持文件的打开、分享、重命名、复制、移动、收藏。
- 支持最近删除、文件属性、列表/宫格等视图。
- 支持图片/视频缩略图预览。

#### [时钟](https://gitcode.com/openharmony/applications_clock)

支持世界时钟/计时器。

#### [计算器](https://gitcode.com/openharmony/applications_calculator)

支持标准计算器/科学计算器。

#### [日历](https://gitcode.com/openharmony/applications_calendar)

- 支持日历卡片、查看日历视图。
- 支持查看日程、查看指定日期、查看账户日程、深色模式。
- 支持新建日程、编辑日程&重要日。
- 支持日程搜索、日程管理、日历账户管理。
- 支持普通日程提醒通知、重要日程提醒通知。
- 支持历法设置。

#### [OOBE](https://gitcode.com/openharmony/applications_startup_guide)

- 支持欢迎页。
- 支持选择语言：欢迎及语言设置、地区设置。
- 支持选择地区：欢迎及语言设置、地区设置。
- 支持协议与声明：最终用户许可协议与基础服务声明、数据与隐私声明。
- 支持协议与声明页面。
- 支持选择网络：WLAN 配置。
- 支持增强服务：云应用、增强服务与用户体验改进。

#### [Tips](https://gitcode.com/openharmony/applications_tips)

- 支持快速上手。
- 支持Tips卡片。

#### [录音机](https://gitcode.com/openharmony/applications_sound_recorder)

- 支持录音基本功能，包含前台录音、后台录音。
- 支持录音状态与控制，包含前台暂停/恢复/停止并保存录音、录音波形图、剩余录音时间、后台系统通知、后台锁屏通知、通话与录音并发。
- 支持历史录音播放状态与控制，包含前台/后台播放、列表/播放页面暂停与恢复、进度条拖拽、播放页面波形图及拖拽、后台播控中心大小卡片、系统通知、倍速播放。
- 支持 m4a、wav、amr 播放格式。
- 支持录音标记，包含添加标记、标记跳转、标记随动。
- 支持录音文件管理，包含列表左滑/多选/播放页面删除、列表左滑/长按重命名、录音文件搜索与排序（时间/名称，时间由近到远）。
- 支持普通录音的全部播放、管理、编辑功能。
- 支持录音卡片，大卡片可开始/停止/暂停/恢复录音及编辑，小卡片可开始/停止录音，大小卡片数据同步。
- 支持麦克风权限管控。

#### [SIM卡管理](https://gitcode.com/openharmony/applications_simcardmanagement)

- 支持双卡管理，包含编辑卡1和卡2信息（名称和号码）、启用/停用SIM卡、SIM卡保护功能。
- 支持默认移动数据选择。
- 支持默认拨号卡设置。

### 更新系统应用

针对展锐P7885芯片开发板，如下系统应用在7.0 Release版本的基础上进行了更新：

#### [桌面](https://gitcode.com/openharmony/window_scene_board)

- 支持数字密码/滑动解锁、防暴力破解、锁屏时钟与卡片。
- 支持4×4桌面图标布局、Dock栏、桌面图标角标、应用快捷方式、桌面编辑模式。
- 支持卡片/卡片堆叠/文件夹的完整管理。
- 支持最近任务（锁定、一键清理、滑动删除）。
- 支持状态栏、控制中心、手势/三键导航。
- 支持通知中心（列表、分区、组通知、置顶/静默）。
- 支持实况通知（胶囊/卡片）。
- 支持系统弹框（关机/低电量）、音量面板。
- 支持分屏、悬浮窗（智慧多窗）。
- 支持窗口任务管理（启停、多任务、任务链、持久化恢复）。
- 支持壁纸库、静态壁纸设置、免打扰模式。
- 支持设置内开关、控制中心首页、控制中心二级页。
- 支持时间围栏。
- 支持通知勿扰、应用白名单。
- 支持来电勿扰、通用勿扰策略、指定联系人勿扰、重复来电响铃。
- 支持关联系统深色模式。
- 支持状态栏提醒、实况提醒。
- 支持预置模式，免打扰、睡眠模式、学习模式、工作模式。
- 支持自定义模式、自定义名称、自定义图标、自定义颜色、预置模板创建、自定义创建、模式删除。

#### [设置](https://gitcode.com/openharmony/applications_settings)

- 支持设置内全局搜索。
- 支持WLAN/蓝牙/移动网络。
- 支持壁纸、亮度、深色模式（含定时）、字体与显示大小。
- 支持声音模式、音量面板、来电/信息/通知铃声。
- 支持通知和状态栏管理。
- 支持应用管理、锁屏密码、电池、存储。
- 支持系统导航、语言与输入法、日期时间、重置、开发者选项。
- 支持关于设备完整信息（IMEI、序列号、运行内存等）。
- 支持定时关机。
- 支持设置建议。
- 支持SIM卡管理。
- 支持软件更新。
- 支持系统用户管理、添加账户。
- 支持放大显示、屏幕放大、缩放区域切换。
- 支持颜色反转。
- 支持色彩校正。
- 支持高对比度文字。
- 支持减弱动态效果。
- 支持单声道音频、音量平衡。
- 支持屏幕触控，点击持续时间、忽略重复点击。
- 支持辅助功能快捷键。

#### [相机](https://gitcode.com/openharmony/applications_camera)

- 支持前/后置拍照、前/后置录像。
- 支持相机Picker（仅拍照/仅录像/拍照+录像）。
- 支持相机设置页、百宝箱入口。

#### [图库](https://gitcode.com/openharmony/applications_photos)

- 支持照片浏览/大图浏览/大图手势/大图组件。
- 支持宫格操作/大图菜单操作/卡片操作/相册操作。
- 支持图片编辑/图库设置。
- 支持大图视频播放/照片页浏览。
- 支持图库Picker。


#### [联系人](https://gitcode.com/openharmony/applications_contacts)

- 支持拨号盘搜索及结果快捷操作（详情、黑名单、复制、标记、新建/保存联系人、发短信）。
- 支持通话记录（全部/未接）及长按管理（多选、删除、标记、加入黑名单等）。
- 支持联系人搜索、字母索引、智能/自定义群组。
- 支持联系人新建/编辑/详情（头像、多号码、邮箱、地址、生日等完整字段）。
- 支持收藏联系人及排序、批量管理。
- 支持联系人导入/导出、SIM 卡导入、最近删除、重复联系人合并。
- 支持单人铃声（本地/视频/无铃声）。
- 支持服务卡片（快捷拨打、未接来电、桌面快捷方式）。
- 支持联系人Picker。

#### [短信](https://gitcode.com/openharmony/applications_mms)

- 支持短信发送，长短信、表情。
- 支持群发、转发、失败重发。
- 支持会话列表左滑/长按/滑动多选删除。
- 支持通知栏整合、标记已读、通知回复。
- 支持详情页复制、转发、选择文本等操作。
- 支持列表与详情展示联系人头像。
- 支持信息收藏、送达报告。

#### [通话](https://gitcode.com/openharmony/applications_call)

- 支持语音来去电、接听/挂断/拒接、静音、扬声器、音频设备切换。
- 支持紧急拨号、SOS 连按电源键、紧急位置展示。
- 支持紧急联系人及自动求助。
- 支持来电全屏/横幅、铃声/振动。
- 支持移动数据、APN、数据漫游等设置。
- 支持飞行模式拨号提示、接近光防误触。


## 配套关系

**表1** 版本软件和工具配套关系

| 软件 | 版本 | 备注 | 
| -------- | -------- | -------- |
| OpenHarmony | 7.0 Release | NA | 
| Public SDK | Ohos_sdk_public 26.0.0.38 (API Version 26.0.0 Release) | 面向应用开发者提供，不包含需要使用系统权限的系统接口。通过DevEco Studio默认获取的SDK为Public SDK。 | 
| HUAWEI DevEco Studio（可选） | 26.0.0 Release | OpenHarmony应用开发推荐使用。<br />*软件上传中*。 | 
| HUAWEI DevEco Device Tool（可选） | 4.0 Release | OpenHarmony智能设备集成开发环境推荐使用。<br />[请点击这里获取](https://device.harmonyos.com/cn/develop/ide#download)。 | 
| HarmonyOS SDK for OpenHarmony | 7.0 Release | 面向OpenHarmony生态提供的标准化开发工具套件，扩展了OpenHarmony SDK的能力。<br />详见[HarmonyOS SDK for OpenHarmony](https://gitcode.com/harmonyos-sdk-for-openharmony/docs/blob/master/README.md) | 


### 前提条件

1. 注册gitcode账号。

2. 注册gitcode的SSH公钥，请参考[gitcode帮助中心](https://docs.gitcode.com/docs/help/home/user_center/security_management/ssh)。

3. 安装[git客户端](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)和[git-lfs](https://gitcode.com/gh_mirrors/gi/git-lfs?source_module=search_result_repo)并配置用户信息。
  
   ```shell
   git config --global user.name "yourname"
   git config --global user.email "your-email-address"
   git config --global credential.helper store
   ```

4. 执行如下命令安装gitcode的repo工具。

   下述命令中的安装路径以"~/bin"为例，请用户自行创建所需目录。
  
   ```shell
   mkdir ~/bin
   curl https://raw.gitcode.com/gitcode-dev/repo/raw/main/repo-py3 -o ~/bin/repo
   chmod a+x ~/bin/repo
   pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
   ```

5. 将repo添加到环境变量。

   ```shell
   vim ~/.bashrc               # 编辑环境变量
   export PATH=~/bin:$PATH     # 在环境变量的最后添加一行repo路径信息
   source ~/.bashrc            # 应用环境变量
   ```


### 通过repo获取

**方式一（推荐）**

通过repo + ssh 下载（需注册公钥，请参考[gitcode帮助中心](https://docs.gitcode.com/docs/help/home/user_center/security_management/ssh)）。

- 从版本分支获取源码。可获取该版本分支的最新源码，包括版本发布后在该分支的合入。
   ```shell
   repo init -u git@gitcode.com:openharmony/manifest.git -b OpenHarmony-7.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- 从版本发布Tag节点获取源码。可获取与版本发布时完全一致的源码。
   ```shell
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v7.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

**方式二**

通过repo + https 下载。

- 从版本分支获取源码。可获取该版本分支的最新源码，包括版本发布后在该分支的合入。
   ```shell
   repo init -u https://gitcode.com/openharmony/manifest -b OpenHarmony-7.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- 从版本发布Tag节点获取源码。可获取与版本发布时完全一致的源码。
   ```shell
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v7.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

### 从镜像站点获取

**表2** 获取源码路径

| 版本源码 | **版本信息** | **下载站点** | **SHA256校验码** | **软件包容量** |
|---------------------------------------|------------|------------------------------------------------------------|------------------------------------------------------------|--------|
| 全量代码（标准、轻量和小型系统）        | 7.0 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/code-v7.0-Release.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/code-v7.0-Release.tar.gz.sha256) | 57.3 GB |
| Hi3861解决方案（二进制）        | 7.0 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_20260829.tar.gz.sha256) | 28.9 MB |
| Hi3863解决方案（二进制）        | 7.0 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_3863_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_3863_20260829.tar.gz.sha256) | 6.7 MB |
| Hi3861 64K解决方案（二进制）        | 7.0 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_64k_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_64k_20260829.tar.gz.sha256) | 8.0 MB |
| Hi3863 64K解决方案（二进制）        | 7.0 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_3863_64k_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_3863_64k_20260829.tar.gz.sha256) | 8.0 MB |
| Hi3516解决方案-LiteOS（二进制） | 7.0 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_taurus_LiteOS_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_taurus_LiteOS_20260829.tar.gz.sha256) | 362.4 MB |
| Hi3516解决方案-Linux（二进制）  | 7.0 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_taurus_Linux_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_taurus_Linux_20260829.tar.gz.sha256) | 239.8 MB |
| RK3568标准系统解决方案（二进制）ROM包        | 7.0 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu200_standard_arm32_rom_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu200_standard_arm32_rom_20260829.tar.gz.sha256) | 3.7 GB |
| RK3568标准系统解决方案（二进制）XTS包        | 7.0 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu200_standard_arm32_xts_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu200_standard_arm32_xts_20260829.tar.gz.sha256) | 4.9 GB |
| P7885标准系统解决方案（二进制）ROM包        | 7.0 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu600_standard_arm32_rom_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu600_standard_arm32_rom_20260829.tar.gz.sha256) | 5.2 GB |
| P7885标准系统解决方案（二进制）XTS包        | 7.0 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu600_standard_arm32_xts_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu600_standard_arm32_xts_20260829.tar.gz.sha256) | 5.0 GB |
| 标准系统Public SDK包（Mac）             | 26.0.0.38 | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/ohos-sdk-mac-public_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/ohos-sdk-mac-public_20260829.tar.gz.sha256) | 1.3 GB |
| 标准系统Public SDK包（Mac-M1）             | 26.0.0.38  | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/L2-SDK-MAC-M1-PUBLIC_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/L2-SDK-MAC-M1-PUBLIC_20260829.tar.gz.sha256) | 1.3 GB |
| 标准系统Public SDK包（Windows/Linux/ohos）   | 26.0.0.38   | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Release/ohos-sdk-windows_linux-public_20260829.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Release/ohos-sdk-windows_linux-public_20260829.tar.gz.sha256) | 3.4 GB |

## 修复缺陷列表

**表3** 修复缺陷ISSUE列表

| ISSUE单 | 问题描述 | 
| ------- | ------- |
| [468](https://gitcode.com/openharmony/systemabilitymgr_safwk/issues/468) | 进程foundation在wukong压测下出现内存泄漏，5天内存占用增长100M左右。 |
| [329](https://gitcode.com/openharmony/applications_contacts/issues/329)<br />[192](https://gitcode.com/openharmony/telephony_telephony_data/issues/192) |
| [193](https://gitcode.com/openharmony/telephony_telephony_data/issues/193) | 首次启动联系人应用的时间超出基线要求。 |
| [73886](https://gitcode.com/openharmony/arkui_ace_engine/issues/73886) | 开机完成时延较长，不满足基线要求。 |
| [633](https://gitcode.com/openharmony/applications_systemui/issues/633) | 进程com.ohos.systemui有较高概率由于THREAD_BLOCK_6S类型的故障导致appfreeze。该问题在新版本未复现。 |
| [263](https://gitcode.com/openharmony/device_soc_rockchip/issues/263) | 进程render_service低概率出现由于SERVICE_BLOCK导致的sysfreeze，崩溃栈为libmali-bifrost-g52-g7p0-ohos.so。该问题在新版本未复现。 |
| [772](https://gitcode.com/openharmony/applications_photos/issues/772) | 首次启动图库应用的时间超出基线要求。 |

## 遗留缺陷列表

**表4** 遗留缺陷列表

| ISSUE | 问题描述 | 影响 | 计划解决日期 | 
| ------- | ------- | ------- | ------- |
| [793](https://gitcode.com/openharmony/applications_photos/issues/793) | 进程com.ohos.photos低概率出现cppcrash，崩溃栈为libimage_effect_impl.so | 图库进入编辑模式出现黑屏，退出后重新进入编辑模式可恢复。 | OpenHarmony7.1 |
| [6750](https://gitcode.com/openharmony/web_webview/issues/6750) | 进程com.ohos.note:render低概率出现cppcrash，崩溃栈为libarkweb_engine.so | 记事本应用白屏，重启应用可恢复。 | OpenHarmony7.1 |
| [472](https://gitcode.com/openharmony/communication_bluetooth_service/issues/472) | 进程bluetooth_service低概率出现cppcrash，崩溃栈为libbtstack.z.so | 蓝牙服务会自动重启，用户无明显感知。 | OpenHarmony7.1 |

<!--no_check-->