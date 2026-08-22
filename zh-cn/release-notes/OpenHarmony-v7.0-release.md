# OpenHarmony 7.0 Release

## 版权和许可声明

本项目贡献依据 **《开发者原创声明》（DCO）** 授权给开放原子开源基金会。本项目是由许多开源软件组件组成的汇编作品，该汇编作品的版权归开放原子开源基金会所有。开放原子开源基金会根据Apache 2.0开源许可协议（以下简称 **Apache 2.0** ）向您提供该汇编作品的授权。

在遵守Apache 2.0，以及本项目包含的开源软件组件适用的对应开源许可协议的前提下，您方可使用本项目。您可以通过以下网址获取Apache 2.0副本：
**[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0#/session/_blank)**

除非适用法律要求或书面约定，依据适用的开源许可协议分发的软件均按“原样”提供，且不附带任何（明示或默示）形式的保证或条件。有关适用的开源许可协议的具体授权和限制，请参见其原文。

## 版本概述

OpenHarmony 7.0 Release在Beta1版本的基础上进一步增强了应用开发能力。系统层面，新增支持展锐P7885芯片开发板，并支持轻量系统小型化适配以减少资源占用。应用框架方面，新增基于ModularObjectExtensionAbility的模块化对象能力及自分发插件管理，ArkUI新增多个V2组件、懒加载布局组件、智慧手势、系统材质、响应式环境变量等能力。媒体领域新增音频PCM处理与播出、广告插播、离线缓存下载、录屏暂停恢复及音频设备增强管理等功能。此外，还新增压缩解压缩模块、窗口模式设置、多线程检测可配置参数、企业账号与应用管理增强、WebSocket自定义端口、内存导出监听以及统一SDK支持等能力。

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

### 分布式数据管理

数据共享能力新增支持发布多个值类型的配置用于多应用共享。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkdata/js-apis-data-dataShare.md#publish20)）

### 图形

绘制模块字体绘制能力新增支持获取文字的轮廓路径，同时支持字体回退能力。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Font.md#gettextpathwithfallback)）

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

### 窗口管理

新增支持设置主窗或子窗支持的窗口模式。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkui/arkts-apis-window-Window.md#setsupportedwindowmodes)）

### 语言编译器与运行时

setMultithreadingDetectionEnabled接口新增多线程检测可配置参数，支持开发者配置故障类型、采样频率、故障上报时间间隔。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkts/js-apis-util.md#multithreadingdetectionoptions)）

### 媒体

**媒体管理**

- 新增C API，支持对音频PCM数据处理后再播出的能力（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setpcmprocessorcallback)），同时支持设置音频处理后再播出的回调函数单次可返回的最大数据量（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setpcmprocessormaxlen)）。

- 新增ArkTS API，支持广告插播能力，实现广告资源的播放以及广告事件的监听。（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/arkts-apis-media-AVAdsController.md)）

- 新增ArkTS API，实现应用可以离线缓存下载在线资源。（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/arkts-apis-media-AVDownloaderManager.md)）

- 新增ArkTS API和C API，支持录屏过程中暂停录制屏幕与恢复录制屏幕的能力。（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/arkts-apis-media-i.md#avscreencapturestrategy20)、[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforpause)）

- 新增C API，支持对指定应用的所有窗口进行屏幕录制。（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-base-h.md#oh_capturepickermode)）

**音频**

- 新增音频设备增强管理器功能。（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md)、[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md)）

- 新增基于C/C++的音频格式转换能力。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/media/audio/audio-suite-format-converter.md)）

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

**相机**

C API新增元数据对象扩展概念的声明。（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-camera-kit/capi-metadata-object-ext-h.md)）

### 文件管理

新增支持压缩解压缩模块，为应用提供数据压缩和解压缩的能力，可用于文件打包分发、减少存储占用、加速网络传输等场景。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/file-management/archive-overview.md)）

### 企业定制服务

- 企业设备的账号管理新增创建普通系统账号（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-accountManager.md#accountmanagercreatenormalosaccount)）、移除系统账号（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-accountManager.md#accountmanagerremoveosaccount)）以及切换系统账号（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-accountManager.md#accountmanageractivateosaccount)）的接口。

- 企业设备的应用管理新增支持查询指定应用的窗口状态信息列表。可查询应用是否在底部Dock栏、当前应用窗口是否在前台显示等信息。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-applicationManager.md#applicationmanagergetapplicationwindowstates)）

### 网络管理

建立WebSocket连接的可选参数新增支持supportOriginPort，可用于控制Origin字段是否携带自定义端口号。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-network-kit/js-apis-webSocket.md#websocketrequestoptions)）

### DFX

HiDebug新增支持注册内存导出监听器，用于在内存占用较高或通过hidumper命令手动触发时导出应用内存快照。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/dfx/hidebug-guidelines.md#导出内存快照)、[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-performance-analysis-kit/capi-hidebug-h.md#oh_hidebug_registermemdumplistener)）

### 其他

新增对统一SDK的支持。统一SDK是面向OpenHarmony生态提供的标准化开发工具套件，扩展了OpenHarmony SDK的能力，为开发者提供远场通信、基础语音、分享服务、基础视觉、桌面拓展、文件预览、推送服务、统一扫码服务等多维度开发能力。详见[HarmonyOS SDK for OpenHarmony](https://gitcode.com/harmonyos-sdk-for-openharmony/docs/blob/6.1-release/README.md)。

## 预置应用更新说明

### 新增预置应用

针对展锐P7885芯片开发板，新增如下预置应用：

#### [文件管理](https://gitcode.com/openharmony/applications_filepicker)

- 支持外置存储浏览。
- 支持文管内访问图库。
- 支持文件Picker（选择、后缀过滤、批量授权）。
- 支持通过路径Picker保存文件。
- 支持文件的打开、分享、重命名、复制、移动、收藏。
- 支持最近删除、文件属性、列表/宫格等视图。

#### [时钟](https://gitcode.com/openharmony/applications_clock)

- 支持世界时钟/计时器。

#### [计算器](https://gitcode.com/openharmony/applications_calculator)

- 支持标准计算器/科学计算器。

### 更新预置应用

针对展锐P7885芯片开发板，如下预置应用在6.1 Release版本的基础上进行了更新：

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

#### [设置](https://gitcode.com/openharmony/applications_settings)

- 支持设置内全局搜索。
- 支持WLAN/蓝牙/移动网络。
- 支持壁纸、亮度、深色模式（含定时）、字体与显示大小。
- 支持声音模式、音量面板、来电/信息/通知铃声。
- 支持通知和状态栏管理。
- 支持应用管理、锁屏密码、电池、存储。
- 支持系统导航、语言与输入法、日期时间、重置、开发者选项。
- 支持关于设备完整信息（IMEI、序列号、运行内存等）。

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
- 支持联系人导入/导出、SIM卡导入、最近删除、重复联系人合并。
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
- 支持紧急拨号、SOS连按电源键、紧急位置展示。
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
| 全量代码（标准、轻量和小型系统）        | 7.0 Release    | *软件上传中* | *软件上传中* | NA |
| Hi3861解决方案（二进制）        | 7.0 Release    | *软件上传中* | *软件上传中* | NA |
| Hi3863解决方案（二进制）        | 7.0 Release    | *软件上传中* | *软件上传中* | NA |
| Hi3861 64K解决方案（二进制）        | 7.0 Release    | *软件上传中* | *软件上传中* | NA |
| Hi3863 64K解决方案（二进制）        | 7.0 Release    | *软件上传中* | *软件上传中* | NA |
| Hi3516解决方案-LiteOS（二进制） | 7.0 Release    | *软件上传中* | *软件上传中* | NA |
| Hi3516解决方案-Linux（二进制）  | 7.0 Release    | *软件上传中* | *软件上传中* | NA |
| RK3568标准系统解决方案（二进制）ROM包        | 7.0 Release    | *软件上传中* | *软件上传中* | NA |
| RK3568标准系统解决方案（二进制）XTS包        | 7.0 Release    | *软件上传中* | *软件上传中* | NA |
| P7885标准系统解决方案（二进制）ROM包        | 7.0 Release    | *软件上传中* | *软件上传中* | NA |
| P7885标准系统解决方案（二进制）XTS包        | 7.0 Release    | *软件上传中* | *软件上传中* | NA |
| 标准系统Public SDK包（Mac）             | 26.0.0.38 | *软件上传中* | *软件上传中* | NA |
| 标准系统Public SDK包（Mac-M1）             | 26.0.0.38  | *软件上传中* | *软件上传中* | NA |
| 标准系统Public SDK包（Windows/Linux）   | 26.0.0.38   | *软件上传中* | *软件上传中* | NA |

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
| [793](https://gitcode.com/openharmony/applications_photos/issues/793) | 进程com.ohos.photos低概率出现cppcrash，崩溃栈为libimage_effect_impl.so | 图库进入编辑模式出现黑屏，退出后重新进入编辑模式可恢复。 | OpenHarmony7.1 |
| [6750](https://gitcode.com/openharmony/web_webview/issues/6750) | 进程com.ohos.note:render低概率出现cppcrash，崩溃栈为libarkweb_engine.so | 记事本应用白屏，重启应用可恢复。 | OpenHarmony7.1 |
| [472](https://gitcode.com/openharmony/communication_bluetooth_service/issues/472) | 进程bluetooth_service低概率出现cppcrash，崩溃栈为libbtstack.z.so | 蓝牙服务会自动重启，用户无明显感知。 | OpenHarmony7.1 |

<!--no_check-->