# OpenHarmony 7.0 Beta1


## 版权和许可声明

本项目贡献依据 **《开发者原创声明》（DCO）** 授权给开放原子开源基金会。本项目是由许多开源软件组件组成的汇编作品，该汇编作品的版权归开放原子开源基金会所有。开放原子开源基金会根据Apache 2.0开源许可协议（以下简称 **Apache 2.0** ）向您提供该汇编作品的授权。

在遵守Apache 2.0，以及本项目包含的开源软件组件适用的对应开源许可协议的前提下，您方可使用本项目。您可以通过以下网址获取Apache 2.0副本：
**[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0#/session/_blank)**

除非适用法律要求或书面约定，依据适用的开源许可协议分发的软件均按“原样”提供，且不附带任何（明示或默示）形式的保证或条件。有关适用的开源许可协议的具体授权和限制，请参见其原文。

## 版本概述

OpenHarmony 7.0 Beta1版本进一步增强应用开发功能，支持对应用更精细化的控制，比如可获取Ability退出原因、AbilityStage启动加载信息、通知自定义铃声和锁屏通知控制等；进一步提升界面交互体验，支持动态布局容器、Tabs嵌套滚动、自定义组件全局复用等；进一步增强窗口管理能力，新增闪控窗、按需销毁窗口页面内容等；进一步增强ArkWeb网页控制能力，内核升级至Chromium 144版本，支持URL白名单控制、网页安全配置等；进一步增强音视频处理能力，支持HDR效果、多屏幕录制、Cinepak编解码等；新增Content Embed内容嵌入服务，支持应用间文档互相嵌入与协同编辑；进一步丰富了图像元数据处理能力、音频编解码能力、MIDI设备支持、相机专业能力、证书管理能力、企业定制能力等。

### 应用程序框架

- Ability上次退出的信息字段新增支持获取退出原因。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#lastexitdetailinfo18)）

- AbilityStage上下文新增launchElement字段，用于在AbilityStage调用onCreate时告知应用正在加载的Ability，从而动态加载资源。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-inner-application-abilityStageContext.md#%E5%B1%9E%E6%80%A7)）

- AbilityStage组件管理器新增AbilityStage即将创建第一个Ability的回调（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onabouttocreateability24)），以及当进程从应用快照启动时的回调（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onlaunchfromhypersnap24)）。

- 新增支持获取指定包名和分身索引的应用名称。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetapplicationlabel)）

- 新增支持用于管理ModularObjectExtensionAbility的C API，提供查询ModularObjectExtensionAbility信息、连接与断开连接等能力。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/capi-modular-object-extension-manager-h.md)）


### ArkUI

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


### 分布式数据管理

- 新增创建或打开已有的关系型数据库的同步方法。同步方法可阻塞线程直到获取到RdbStore。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstoresync24)）


### 媒体

- C API新增隐私保护设置的回调函数，用于响应截屏录屏时捕获的隐私保护事件。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setprivacyprotectcallback)）

- C API新增支持获取多屏幕录制能力信息（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_getmultidisplaycapturecapability)），以及通过DisplayID选择多屏幕进行录制（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_getmultidisplayidsselected)）。


### 音频

- 音频采集和音频渲染新增支持设置独立的音频会话策略和行为参数。（[API参考-音频采集](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/arkts-apis-audio-AudioCapturer.md#setindependentaudiosessionstrategy24)、[API参考-音频渲染](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#setindependentaudiosessionstrategy24)）

- 新增OH_MIDI的C API，支持应用通过USB或蓝牙BLE连接外接MIDI设备（如MIDI键盘、电子琴、MIDI控制器等），实现MIDI消息的收发、设备枚举与热插拔监听，可用于音乐创作、乐器录制与教学、MIDI设备控制等场景。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/media/audio/midi-overview.md)）

- 新增C API，提供声明输入音频格式、输出音频格式底层数据结构和格式转换接口的定义。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/capi-native-audio-converter-h.md)）


### 相机管理

新增支持创建延迟预览输出对象，在配流时替代普通的预览输出对象加入数据流（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createdeferredpreviewoutput24)）。同时支持配置延迟预览的Surface（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#adddeferredsurface24)）。

新增一批拍照/录像模式下的相机专业能力，包括闪光灯、光学防抖、曝光、手动对焦、ISO感光度、物理光圈的调用和设置。

### 音视频编解码

- 新增支持Cinepak媒体格式的编解码能力。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/media/avcodec/avcodec-support-formats.md#%E5%AA%92%E4%BD%93%E7%BC%96%E8%A7%A3%E7%A0%81)）

- 新增支持筛选特定MIME类型的安全解码器，在处理受数字版权管理保护的DRM媒体资源时，可以使用支持安全链路的"安全解码器"。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/media/avcodec/obtain-supported-codecs.md#%E7%AD%9B%E9%80%89%E7%89%B9%E5%AE%9Amime%E7%B1%BB%E5%9E%8B%E7%9A%84%E5%AE%89%E5%85%A8%E8%A7%A3%E7%A0%81%E5%99%A8drm%E6%92%AD%E6%94%BE%E5%9C%BA%E6%99%AF)）

- H265硬件编码器新增支持CBRHQ（高质量恒定码率模式）。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/media/avcodec/video-encoding-configuration-typical-scenarios.md#%E4%BD%8E%E6%97%B6%E5%BB%B6%E5%9C%BA%E6%99%AF)）


### 音视频播控服务

- 新增支持后台播放模式的设置，可由应用告知系统是否支持后台播放，系统根据能力决策实况胶囊的显示。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setbackgroundplaymode24)）

- AVSession的枚举新增定义了在不同场景中使用的额外键的枚举。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-e.md#extrakey)）


### 后台任务管理

提醒的倒计时实例对象新增参数重复周期（repeatInterval）和重复次数（repeatCount）。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-backgroundtasks-kit/js-apis-reminderAgentManager.md#reminderrequesttimer)）


### 基础通信

- 新增支持通过C API获取Wi-Fi连接信息。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-connectivity-kit/capi-oh-wifi-h.md#oh_wifi_getlinkedinfo)）

- 新增A2DP的播放状态广播以及SCO广播事件。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_bluetooth_a2dpsource_play_state_change24)）


### 网络管理

TLS支持证书链的验证，可通过传入数组的方式最多支持到1000个证书。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-network-kit/js-apis-socket.md#tlssecureoptions9)）


### 内容嵌入服务

新增Content Embed内容嵌入服务，提供应用间文档互相嵌入与协同编辑的框架能力，并为开发者封装了客户端与服务端的开发接口，便于快速实现文档跨应用嵌入与协作。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/content-embed/content-embed-kit-overview.md)、[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-content-embed-kit/capi-contentembed.md)）


### 文件管理

- 打开文件或目录时新增参数UNCACHE，支持读写文件不进行页缓存。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-core-file-kit/js-apis-file-fs.md#fileioopen)）

- 新增listFileExt方法支持递归列出和自定义文件名过滤。可通过配置options中recursion参数实现递归列出所有文件的相对路径。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-core-file-kit/js-apis-file-fs.md#fileiolistfileext)）

- 新增支持开发者通过文件mmap能力集（基于文件描述符或文件对象创建文件映射对象），实现文件的高效读写访问。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-core-file-kit/js-apis-file-fs.md#fileiommap)）

- 新增支持应用捐献自身沙箱目录给系统设置为共享，其他应用可以通过文管直接获取到目录里的文件。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/file-management/share-app-file-configuration.md)）


### 卡片

在onUpdateForm回调中新增支持卡片更新原因字段。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-form-kit/js-apis-app-form-formInfo.md#formupdatereason24)）


### 图形

- 新增支持为组件内容添加HDR（高动态范围成像）提亮效果。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkgraphics2d/js-apis-uiEffect.md#hdrbrightnessratio24)）

- 新增支持视频的AIHDR格式。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkgraphics2d/js-apis-hdrCapability.md#hdrformat)）

- 绘制模块新增用于处理坐标点的类，支持对坐标点取反和设置偏移量。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-PointUtils.md)）


### 图像

- 新增[WebP图像元数据类](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-WebPMetadata.md)、[GIF图像元数据类](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-GifMetadata.md)、[JFIF图像元数据类](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-JfifMetadata.md)、[TIFF图像元数据类](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-TiffMetadata.md)、[PNG图像元数据类](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-PngMetadata.md)以及[AVIS图像元数据类](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-AvisMetadata.md)，用于存储对应格式图像的元数据。

- 新增[XMP（Extensible Metadata Platform）元数据](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-image-kit/arkts-apis-image-XMPMetadata.md)。


### 多模输入

- 新增输入事件注入模块，提供键盘和鼠标输入事件模拟能力。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-input-kit/js-apis-inputeventclient.md)）

- C API输入事件增强，提供输入事件的压力、相对窗口左上角的XY相对坐标等事件。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-input-kit/capi-oh-input-manager-h.md#oh_input_settoucheventpressure)）


### 通知

- 新增支持查询本APP通知中wantAgent字段的部分信息。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanagergetnotificationparameters24)）

- 新增支持使用应用沙箱内的文件作为通知的自定义铃声。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/notification/notification-customized-ringtone.md)）

- 新增是否开启锁屏通知等字段。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-notification-kit/js-apis-notificationManager.md#notificationsetting20)）

- 新增支持以半模态方式拉起应用的通知设置界面。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanageropennotificationsettingswithresult)）


### 定制

- kiosk模式下，新增支持通过上划停留手势进入最近任务栏（ALLOW_GESTURE_CONTROL）以及通过边缘内划停留手势进入侧边DOCK栏（ALLOW_SIDE_DOCK）。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-applicationManager.md#kioskfeature20)）

- 新增支持安装和卸载企业重签名证书的能力。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanagerinstallenterpriseresignaturecertificate24)）

- 新增支持根据位置索引添加应用到PC/2in1设备的底部快捷栏的能力。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-applicationManager.md#applicationmanageradddockapp24)）

- 设备设置管理支持对当前用户下被隐藏的设置项列表进行添加、删除、查询操作。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-mdm-kit/js-apis-enterprise-deviceSettings.md#devicesettingsaddhiddensettingsmenu24)）



### NDK

JSVM新增支持从外部内存创建ArrayBuffer对象。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/common/capi-jsvm-h.md#oh_jsvm_createarraybufferfromexternalmemory)）


### DFX

- 当应用发生SIGPIPE异常退出时，在Debug版本应用可开启SIGPIPE信号打印调用栈功能辅助定位问题。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/dfx/cppcrash-guidelines.md#%E5%BA%94%E7%94%A8%E5%8F%91%E7%94%9Fsigpipe%E5%BC%82%E5%B8%B8%E9%80%80%E5%87%BA)）

HiProfiler新增文件缓存模式（use_file_cache_mode），通过将缓存数据落盘，提升内存分配信息的采集性能。

- HiDebug新增资源采集功能，支持按需采集应用进程资源分配栈至沙箱，覆盖文件描述符、线程、Native/GPU内存及全局句柄等类别，辅助定位资源泄漏。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/dfx/hidebug-guidelines.md)）

- HiDebug新增支持获取应用程序进程的物理内存使用信息。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-performance-analysis-kit/js-apis-hidebug.md#hidebuggetrssinfo24)）

- HiDebug新增支持将转储的堆快照由线程级改为进程级。（[API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-performance-analysis-kit/js-apis-hidebug.md#hidebugsetprocdumpinsharedoom24)）

- HiDebug新增提供包括内核信息在内的Trace采集请求接口。（[ArkTS API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-performance-analysis-kit/js-apis-hidebug.md#hidebugrequesttrace24)、[C API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-performance-analysis-kit/capi-hidebug-h.md#oh_hidebug_requesttrace)）

- HiAppEvent新增应用冻屏告警事件，提供事件的订阅能力。（[指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/dfx/hiappevent-watcher-appfreezewarning-events.md)）

## 配套关系

**表1** 版本软件和工具配套关系

| 软件 | 版本 | 备注 | 
| -------- | -------- | -------- |
| OpenHarmony | 7.0 Beta1 | NA | 
| Public SDK | Ohos_sdk_public 26.0.0.25 (API Version 26.0.0 Beta1) | 面向应用开发者提供，不包含需要使用系统权限的系统接口。通过DevEco Studio默认获取的SDK为Public SDK。 | 
| HUAWEI DevEco Studio（可选） | 26.0.0 Beta1 | OpenHarmony应用开发推荐使用。<br />[请点击这里获取](https://developer.huawei.com/consumer/cn/download/deveco-studio)。 | 
| HUAWEI DevEco Device Tool（可选） | 4.0 Release | OpenHarmony智能设备集成开发环境推荐使用。<br />[请点击这里获取](https://device.harmonyos.com/cn/develop/ide#download)。 | 


## 源码获取

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

通过repo + ssh 下载（需注册gitcode的SSH公钥，请参考[gitcode帮助中心](https://docs.gitcode.com/docs/help/home/user_center/security_management/ssh)）。

- 从版本分支获取源码。可获取该版本分支的最新源码，包括版本发布后在该分支的合入。
   ```
   repo init -u git@gitcode.com:openharmony/manifest.git -b OpenHarmony-7.0-Beta1 --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- 从版本发布Tag节点获取源码。可获取与版本发布时完全一致的源码。
   ```
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v7.0-Beta1 --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

**方式二**

通过repo + https 下载。

- 从版本分支获取源码。可获取该版本分支的最新源码，包括版本发布后在该分支的合入。
   ```
   repo init -u https://gitcode.com/openharmony/manifest -b OpenHarmony-7.0-Beta1 --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- 从版本发布Tag节点获取源码。可获取与版本发布时完全一致的源码。
   ```
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v7.0-Beta1 --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```


### 从镜像站点获取


**表2** 获取源码路径

| 版本源码                                | **版本信息** | **下载站点**                                                 | **SHA256校验码**                                             | **软件包容量** |
| --------------------------------------- | ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------- |
| 全量代码（标准、轻量和小型系统）        | 7.0 Beta1    | *软件包上传中* | *软件包上传中* | - |
| Hi3861解决方案（二进制）        | 7.0 Beta1    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/hispark_pegasus.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/hispark_pegasus.tar.gz.sha256) | 28.9 MB |
| Hi3516解决方案-LiteOS（二进制） | 7.0 Beta1    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/hispark_taurus_LiteOS.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/hispark_taurus_LiteOS.tar.gz.sha256) | 361.3 MB |
| Hi3516解决方案-Linux（二进制）  | 7.0 Beta1    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/hispark_taurus_Linux.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/hispark_taurus_Linux.tar.gz.sha256) | 236.8 MB |
| RK3568标准系统解决方案（二进制）ROM包        | 7.0 Beta1    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/dayu200_standard_arm32_rom.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/dayu200_standard_arm32_rom.tar.gz.sha256) | 	3.7 GB |
| RK3568标准系统解决方案（二进制）XTS包        | 7.0 Beta1    | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/dayu200_standard_arm32_xts.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/dayu200_standard_arm32_xts.tar.gz.sha256) | 	6.6 GB |
| 标准系统Public SDK包（Mac）             | 26.0.0.25 | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/ohos-sdk-mac-public.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/ohos-sdk-mac-public.tar.gz.sha256) | 1.3 GB |
| 标准系统Public SDK包（Mac-M1）             | 26.0.0.25  | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/L2-SDK-MAC-M1-PUBLIC.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/L2-SDK-MAC-M1-PUBLIC.tar.gz.sha256) | 1.2 GB |
| 标准系统Public SDK包（Windows/Linux）   | 26.0.0.25   | [站点](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/ohos-sdk-windows_linux-public.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/7.0-Beta1/ohos-sdk-windows_linux-public.tar.gz.sha256) | 3.0 GB |


## 修复缺陷列表

**表3** 修复缺陷ISSUE列表

| ISSUE单 | 问题描述 | 
| ------- | ------- |
| [73886](https://gitcode.com/openharmony/arkui_ace_engine/issues/73886) | 开机完成时延较长，不满足基线要求。 |
| [856](https://gitcode.com/openharmony/applications_settings/issues/856) | 进程com.ohos.settings小概率出现由于LIFECYCLE_TIMEOUT导致的sysfreeze。 |
| [12339](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12339) | 主进程com.ohos.systemui小概率出现cppcrash，崩溃栈为libark_jsruntime.so。 |


## 遗留缺陷列表

**表4** 遗留缺陷列表

| ISSUE | 问题描述 | 影响 | 计划解决日期 | 
| [633](https://gitcode.com/openharmony/applications_systemui/issues/633) | 进程com.ohos.systemui有较高概率由于THREAD_BLOCK_6S类型的故障导致appfreeze。 | 点击通知-设置跳转较慢，轻微影响使用体验。 | 2026年7月30日 |
| [263](https://gitcode.com/openharmony/device_soc_rockchip/issues/263) | 进程render_service低概率出现由于SERVICE_BLOCK导致的sysfreeze，崩溃栈为libmali-bifrost-g52-g7p0-ohos.so | 设备卡死，重启手机后可恢复。 | 2026年7月30日 |
| [468](https://gitcode.com/openharmony/systemabilitymgr_safwk/issues/468) | 进程foundation在wukong压测下出现内存泄露，5天内存占用增长100M左右。 | 内存占用增长缓慢，用户开发无明显感知。 | 2026年6月30日 |
| [329](https://gitcode.com/openharmony/applications_contacts/issues/329)<br />[192](https://gitcode.com/openharmony/telephony_telephony_data/issues/192) | 联系人列表滑动帧率低于基线要求。| 轻微影响使用体验。 | 2026年7月30日 |
| [193](https://gitcode.com/openharmony/telephony_telephony_data/issues/193) | 首次启动联系人应用的时间超出基线要求。 | 轻微影响使用体验。 | 2026年7月30日 |
| [73886](https://gitcode.com/openharmony/arkui_ace_engine/issues/73886) | 开机完成时延较长，不满足基线要求。 | 轻微影响使用体验。 | 2026年7月30日 |
| [772](https://gitcode.com/openharmony/applications_photos/issues/772) | 首次启动图库应用的时间超出基线要求。 | 轻微影响使用体验。 | 2026年7月30日 |

<!--no_check-->