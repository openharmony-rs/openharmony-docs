# OpenHarmony 6.1 Release

## 版权和许可声明

本项目贡献依据 **《开发者原创声明》（DCO）** 授权给开放原子开源基金会。本项目是由许多开源软件组件组成的汇编作品，该汇编作品的版权归开放原子开源基金会所有。开放原子开源基金会根据Apache 2.0开源许可协议（以下简称 **Apache 2.0** ）向您提供该汇编作品的授权。

在遵守Apache 2.0，以及本项目包含的开源软件组件适用的对应开源许可协议的前提下，您方可使用本项目。您可以通过以下网址获取Apache 2.0副本：
**[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0#/session/_blank)**

除非适用法律要求或书面约定，依据适用的开源许可协议分发的软件均按“原样”提供，且不附带任何（明示或默示）形式的保证或条件。有关适用的开源许可协议的具体授权和限制，请参见其原文。

## 版本概述

OpenHarmony 7.0 Release版本进一步增强应用开发功能，支持对应用更精细化的控制，比如可统计UIAbility启动耗时、可获取通知角标数等；进一步提升动态效果体验，对小语种文字显示进行了优化；进一步增强系统感知能力，ArkWeb可获取网页使用麦克风和摄像头的状态，输入法可感知所在屏幕状态等；进一步丰富了证书管理能力；进一步增强音频控制管理能力、图形处理能力等。

各模块重点新增与增强的特性说明如下：

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

setMultithreadingDetectionEnabled接口新增多线程检测可配置参数，支持开发者配置故障类型、采样频率、故障上报时间间隔（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkts/js-apis-util.md#multithreadingdetectionoptions)）


### 媒体

**媒体管理**

- 新增C API，支持对音频PCM数据处理后再播出的能力（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setpcmprocessorcallback)），同时支持设置音频处理后再播出的回调函数单次可返回的最大数据量（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setpcmprocessormaxlen)）。

- 新增ArkTS API，支持广告插播能力，实现广告资源的播放以及广告事件的监听。（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/arkts-apis-media-AVAdsController.md)）

- 新增ArkTS API，实现应用可以离线缓存下载在线资源。（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/arkts-apis-media-AVDownloaderManager.md)）

- 新增ArkTS API和C PAI，支持录屏过程中暂停录制屏幕与恢复录制屏幕的能力。 （[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/arkts-apis-media-i.md#avscreencapturestrategy20)、[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforpause)）

- 新增C PAI，支持对指定应用的所有窗口进行屏幕录制。（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-base-h.md#oh_capturepickermode)）

**音频**

- 新增音频设备增强管理器功能。（[ArkTS API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md)、[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md)）

- 新增基于C/C++的音频格式转换能力。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/media/audio/audio-suite-format-converter.md)）


**播控框架**

新增支持设置应用支持的播放倍速列表（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setsupportedplayspeeds)）、设置应用支持的循环模式列表（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setsupportedloopmodes)）、设置应用支持的控制类型列表（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setmediacentercontroltype)）。同时通过AVSessionController支持获取应用支持的播放倍速列表（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#getsupportedplayspeeds)）、获取应用支持的循环模式列表（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#getsupportedloopmodes)）、获取应用支持的控制类型列表（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#getmediacentercontroltype)），以及支持注册播放倍速列表变化的监听事件（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#onsupportedplayspeedschange)）、注册循环模式列表变化的监听事件（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#onsupportedloopmodeschange)）、注册控制类型列表变化的监听事件（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#onmediacentercontroltypechanged)）。

**相机**

C API新增元数据对象扩展概念的声明。（[C API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-camera-kit/capi-metadata-object-ext-h.md)）


### 文件管理

新增支持压缩解压缩模块，为应用提供数据压缩和解压缩的能力，可用于文件打包分发、减少存储占用、加速网络传输等场景。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/file-management/archive-overview.md)）

### 企业定制服务

- 企业设备的账号管理新增创建普通系统账号（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-accountManager.md#accountmanagercreatenormalosaccount)）、移除系统账号（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-accountManager.md#accountmanagerremoveosaccount)）以及切换系统账号（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-accountManager.md#accountmanageractivateosaccount)）的接口。

- 企业设备的应用管理新增支持查询指定应用的窗口状态信息列表。可以查询到应用是否在底部Dock栏，以及当前应用窗口是否在前台显示等信息。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-applicationManager.md#applicationmanagergetapplicationwindowstates)）


### 网络管理

建立WebSocket连接的可选参数新增支持supportOriginPort，可用于控制Origin字段是否携带自定义端口号。（[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-network-kit/js-apis-webSocket.md#websocketrequestoptions)）


### DFX

HiDebug新增支持注册内存导出监听器，用于在内存占用较高或通过hidumper命令手动触发时导出应用内存快照。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/dfx/hidebug-guidelines.md#导出内存快照)、[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-performance-analysis-kit/capi-hidebug-h.md#oh_hidebug_registermemdumplistener)）


### 设备管理

串口通信能力新增支持对串口通信的管理，包括获取串口设备列表、打开和关闭串口、读写数据、硬件流控信号管理等。（[指南](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/basic-services/busmanager/serialManager/serial-guidelines.md)、[API参考](https://gitcode.com/OpenHarmony/docs/blob/master/zh-cn/application-dev/reference/apis-basic-services-kit/js-apis-busmanager-serial.md)）