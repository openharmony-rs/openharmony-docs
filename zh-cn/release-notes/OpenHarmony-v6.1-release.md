# OpenHarmony 6.1 Release

## 版权和许可声明

本项目贡献依据 **《开发者原创声明》（DCO）** 授权给开放原子开源基金会。本项目是由许多开源软件组件组成的汇编作品，该汇编作品的版权归开放原子开源基金会所有。开放原子开源基金会根据Apache 2.0开源许可协议（以下简称 **Apache 2.0** ）向您提供该汇编作品的授权。

在遵守Apache 2.0，以及本项目包含的开源软件组件适用的对应开源许可协议的前提下，您方可使用本项目。您可以通过以下网址获取Apache 2.0副本：
**[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0#/session/_blank)**

除非适用法律要求或书面约定，依据适用的开源许可协议分发的软件均按“原样”提供，且不附带任何（明示或默示）形式的保证或条件。有关适用的开源许可协议的具体授权和限制，请参见其原文。

## 版本概述

OpenHarmony 6.1 Release版本进一步增强应用开发功能，支持对应用更精细化的控制，比如可统计UIAbility启动耗时、可获取通知角标数等；进一步提升动态效果体验，对小语种文字显示进行了优化；进一步增强系统感知能力，ArkWeb可获取网页使用麦克风和摄像头的状态，输入法可感知所在屏幕状态等；进一步丰富了证书管理能力；进一步增强音频控制管理能力、图形处理能力等。

各模块重点新增与增强的特性说明如下：

### 元能力

- LaunchParam中新增UIAbility的启动时间，用于进行启动耗时的统计。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchparam)）
- [module.json5配置文件abilities标签](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/quick-start/module-configuration-file.md#abilities%E6%A0%87%E7%AD%BE)新增allowSelfRedirect配置项，支持应用配置不允许通过AppLinking拉起自己。

### ArkUI

- List/Grid支持多选长按聚拢动效。（[API参考-List组件](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-container-list.md#%E7%A4%BA%E4%BE%8B17%EF%BC%88%E8%AE%BE%E7%BD%AE%E5%A4%9A%E9%80%89%E8%81%9A%E6%8B%A2%E5%8A%A8%E7%94%BB%EF%BC%89)、[API参考-Grid组件](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-container-grid.md#%E7%A4%BA%E4%BE%8B20%EF%BC%88%E8%AE%BE%E7%BD%AE%E5%A4%9A%E9%80%89%E8%81%9A%E6%8B%A2%E5%8A%A8%E7%94%BB%EF%BC%89)）
- 文本类控件小语种显示优化。
- 状态管理支持判断对象类型是否可被观察的能力。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-arkui/js-apis-stateManagement.md#observedresult23)）
- 自定义组件生命周期优化，增加Attach&amp;Detach阶段。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md)）
- Navigation支持设置分栏分割线的颜色，边距和显隐。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#divider23)）

### ArkWeb

- 新增支持设置和获取当前网页麦克风使用状态的能力。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-arkweb/arkts-apis-webview-WebviewController.md#resumemicrophone23)）
- 提供支持查询当前网页的摄像头使用状态的能力。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-arkweb/arkts-basic-components-web-events.md#oncameracapturestatechange23)）
- 新增支持选区文本内容上报能力。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-arkweb/arkts-basic-components-web-events.md#ontextselectionchange23)）
- 新增支持屏蔽密码保险箱和智能填充功能。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-arkweb/arkts-basic-components-web-attributes.md#enableautofill23)）
- 新增上下文菜单事件支持拉起autofill。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-arkweb/arkts-basic-components-web-WebContextMenuResult.md#requestpasswordautofill23)）

### 窗口

- 字体引擎支持应用注册的可变字体实现无极调节。
- 字体引擎优化了小语种的显示效果。

### 包管理

- 打包工具支持增量打包，提升了部分场景的打包速度（需开启so压缩，且与前一次打包相比，文件没有大的变化）。（[指南](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/tools/packing-tool.md)）
- 支持企业设备导入企业签名证书，并使用导入的企业签名证书进行企业应用的安装运行校验，增强企业设备的应用管理能力。

### 事件通知

- 新增查询桌面角标数值的能力，精准更新桌面角标数字。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanagergetbadgenumber22)）
- 新增支持设置是否启用横幅通知和锁屏通知，在不需要提醒用户的场景静默通知，避免打扰用户，影响体验。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-notification-kit/js-apis-inner-notification-notificationFlags.md#notificationflags-1)）
- 新增支持通知重叠图标（overlayIcon），实现针对IM类消息定制通知图标的能力，提升IM类消息的用户体验。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-notification-kit/js-apis-inner-notification-notificationRequest.md#notificationrequest-1)）

### 分布式数据管理

UDMF新增iWork类型UTD，通过扩展名".pages", ".key", ".numbers"可以获取到系统中配置的UTD统一标识符。（[指南](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/database/uniform-data-type-list.md)）

### 音频

- 新增音频编创功能的NDK接口。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-audio-kit/capi-ohaudiosuite.md)）
- 新增接口支持获取音频播放时延，便于在音频数据输出前更精确的预估播放时延，用于音画同步。
- 新增投播的NDK接口，支持应用接入系统投播。
- 提供获取音视频播放来源接口能力，查询音视频应用播放来源信息。
- 新增Menu类型投播接口，支持通话类应用跨平台场景实现设备切换。
- 新增图片类应用投播功能。
- 新增系统级桌面歌词功能，支持音乐类应用创建使用系统桌面歌词。
- 新增公开系统音管理和播放接口。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-audio-kit/js-apis-inner-multimedia-systemSoundPlayer.md)）
- 音频会话新增接口支持混音播放模式下监听静音播放建议通知，提升音频并发播放体验。（[指南](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/media/audio/audio-session-management.md#%E5%90%AF%E7%94%A8%E6%B7%B7%E9%9F%B3%E6%92%AD%E6%94%BE%E4%B8%8B%E9%9D%99%E9%9F%B3%E5%BB%BA%E8%AE%AE%E9%80%9A%E7%9F%A5)）

### 安全基础平台

- 新增支持伴随设备认证的系统能力。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-user-authentication-kit/js-apis-useriam-companiondeviceauth-sys.md)）
- 证书管理新增支持如下特性（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-device-certificate-kit/js-apis-certManager.md)）：
  
  - 支持拉起证书授权对话框接口，在没有可用证书的情况下支持直接返回错误码。
  - 支持获取Ukey硬件证书管理能力。
  - 提供查询证书凭据详情接口。
  - 提供拉起输入ukey pin码对话框的接口。
  - 提供Public API拉起证书凭据安装界面，用户按照向导完成凭据的安装。
  - 用户证书凭据授权界面支持选择Ukey证书和应用私有证书。
- HUKS新增支持如下特性：
  
  - 提供外部硬件密钥使用和查询接口。（[指南](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/security/UniversalKeystoreKit/huks-external-hardware-key-management-overview.md)）
  - 支持基于国密数字信封形式的密钥导入能力。（[指南-ArkTS](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/security/UniversalKeystoreKit/huks-import-envelop-key-arkts.md)、[指南-C/C++](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/security/UniversalKeystoreKit/huks-import-envelop-key-ndk.md)）
- 证书算法库新增支持如下特性：
  
  - 支持证书链校验时忽略在线证书吊销检查的网络不可达异常。（[指南](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/security/DeviceCertificateKit/create-verify-cerchainvalidator-revocation-object.md#%E8%AF%81%E4%B9%A6%E9%93%BE%E6%A0%A1%E9%AA%8C%E6%97%B6%E5%BF%BD%E7%95%A5%E5%9C%A8%E7%BA%BF%E8%AF%81%E4%B9%A6%E5%90%8A%E9%94%80%E6%A3%80%E6%9F%A5%E7%9A%84%E7%BD%91%E7%BB%9C%E4%B8%8D%E5%8F%AF%E8%BE%BE%E5%BC%82%E5%B8%B8)）
  - 支持证书链校验时下载缺失的中间证书。（[指南](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/security/DeviceCertificateKit/allow-download-Intermediate-Cert.md)）

### 图形

- Canvas模块 Drawing NDK新增DrawPixelMapMesh接口能力、Drawing TS新增drawVertics接口能力。
- Path反向状态填充类型的获取和切换功能补齐。
- Rect的偏移、翻转、判空和自更新功能补齐。
- Region区域边界、包围盒、类型判段、平移和包含关系判断功能补齐。
- Matrix的连接、旋转、斜切操作和仿射变换、矩形映射判断功能补齐。
- 提供创建Lattice的ndk接口能力。
- PathIterator/Typeface接口能力补齐。
- NativeWindow 提供lock/unlock接口能力，获取buffer同时对此buffer进行上锁。
- NativeBuffer支持校验格式 尺寸信息。
- NativeBuffer 提供同时获取虚拟地址和OH_NativeBuffer_Config能力。
- NativeBuffer 提供buffer跨进程共享能力，开发者多进程传输buffer更易用。

### 语言运行时与基础库

- 提供external string机制，避免额外拷贝，允许ArkTS侧直接读取C++层中的字符串。（[指南](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/napi/use-napi-about-string.md#napi_create_external_string_utf16)）
- 提供sendable reference特性支持多ArkTS线程并发操作字符串对象。（[指南](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/napi/use-napi-about-sendable-reference.md)）
- 新增接口支持动态开启多线程检测能力。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-arkts/js-apis-util.md#arktsvm23)）

### 定制服务（MDM）

- PC形态设备新增支持DA模式的MDM应用部署，开发者可以根据设备的实际使用场景更灵活得选用部署的模式。
- EnterpriseAdminExtensionAbility中新增EnterpriseAdminExtensionContext对象，提供后台拉起页面的能力。
- 提供禁用指定应用（系统应用和三方应用均支持）的UIAbility组件的能力。
- 提供对系统按键（电源键、音量、BACK键、HOME键、最近任务键）进行拦截的能力。

### 输入法框架

- 新增感知应用进程内键盘绑定失败原因的监听接口，方便根据失败原因作出相应处理。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodonattachmentdidfail23)）
- 新增相关携带屏幕信息接口：
  
  - 多屏多焦点场景下，应用可以获取到自身所在屏幕的键盘信息。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-ime-kit/js-apis-inputmethod-sys.md#ispanelshown23)）
  - 多屏多焦点场景下，应用可以操作自身所在屏幕上的键盘显示和隐藏。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-ime-kit/js-apis-inputmethod-sys.md#inputmethodcontroller)）

### 资源调度

新增运动健康类型长时任务，用户授权后可支持该类型长时任务在后台运行。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#%E5%B1%9E%E6%80%A7)）

### 基础通信

- 新增支持应用在前台读取NFC卡片时，设置卡在位检测间隔的能力，方便应用更自由地处理卡片信息。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-connectivity-kit/js-apis-nfcTag.md#tagon23)）
- 新增蓝牙HID Device类接口，支持使用蓝牙HID Device能力。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-connectivity-kit/js-apis-bluetooth-hid.md#hidcreatehiddeviceprofile23)）
- 新增PartnerAgent接口，支持应用蓝牙设备连接后拉起应用的PartnerAgentExtensionAbility进程。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-connectivity-kit/js-apis-fusionConnectivity-partnerAgent.md)）

### 泛Sensor

Sensor信息中新增字段“isMockSensor”，用于区分是否是模拟器件。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-sensor-service-kit/js-apis-sensor.md)）

### 多模输入

- 提供公共事件，支持感知笔记本上盖开合。
- 提供接口查询当前设备是否具备红外发射器。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-input-kit/js-apis-infraredemitter.md#infraredemitterhasiremitter23)）

### 电源管理

- 新增阻止睡眠的运行锁类型BACKGROUND_USER_IDLE。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-basic-services-kit/js-apis-runninglock.md#runninglocktype)）
- 新增注册/去注册关机回调的接口，应用可以按需感知关机即将进行，以便及时执行某些重要处理动作。（[API参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/zh-cn/application-dev/reference/apis-basic-services-kit/js-apis-power-sys.md#powerregistershutdowncallback23)）

### 测试与认证平台

- SP Host新增Fd泄露分析能力，支持抓取和分析Fd资源申请释放调用事件和调用栈。
- SP Host新增支持展示ION内存，ASHMem内存，so引用申请释放动态泳道图和调用栈火焰图。
- SP Host新增支持支持ArkTS对象，ArkWeb JS对象申请释放动态泳道图和调用栈火焰图。

## 版本演进

计划于6月30日前发布OpenHarmony 6.1 LTS版本作为OpenHarmony新的长期维护和长期维护和兼容性测评主推版本。

## 配套关系

**表1** 版本软件和工具配套关系

| 软件 | 版本 | 备注 | 
| -------- | -------- | -------- |
| OpenHarmony | 6.1 Release | NA | 
| Public SDK | Ohos_sdk_public 6.1.0.31 (API Version 23 Release) | 面向应用开发者提供，不包含需要使用系统权限的系统接口。通过DevEco Studio默认获取的SDK为Public SDK。 | 
| HUAWEI DevEco Studio（可选） | 6.1.0 Release | OpenHarmony应用开发推荐使用。<br />*待发布后提供*。 | 
| HUAWEI DevEco Device Tool（可选） | 4.0 Release | OpenHarmony智能设备集成开发环境推荐使用。<br />[请点击这里获取](https://device.harmonyos.com/cn/develop/ide#download)。 | 


## 源码获取


### 前提条件

1. 注册GitCode帐号。

2. 注册码云SSH公钥，请参考[码云帮助中心](https://gitcode.com/help/articles/4191)。

3. 安装[git客户端](https://gitcode.com/link?target=https%3A%2F%2Fgit-scm.com%2Fbook%2Fzh%2Fv2%2F%25E8%25B5%25B7%25E6%25AD%25A5-%25E5%25AE%2589%25E8%25A3%2585-Git)和[git-lfs](https://gitcode.com/vcs-all-in-one/git-lfs?_from=gitee_search#downloading)并配置用户信息。
   ```
   git config --global user.name "yourname"
   git config --global user.email "your-email-address"
   git config --global credential.helper store
   ```

4. 安装码云repo工具，可以执行如下命令。
   ```
   curl -s https://gitcode.com/oschina/repo/raw/fork_flow/repo-py3 > /usr/local/bin/repo  #如果没有权限，可下载至其他目录，并将其配置到环境变量中chmod a+x /usr/local/bin/repo
   pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
   ```


### 通过repo获取

**方式一（推荐）**

通过repo + ssh 下载（需注册公钥，请参考[码云帮助中心](https://gitcode.com/help/articles/4191)）。

- 从版本分支获取源码。可获取该版本分支的最新源码，包括版本发布后在该分支的合入。
   ```
   repo init -u git@gitcode.com:openharmony/manifest.git -b OpenHarmony-6.1-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- 从版本发布Tag节点获取源码。可获取与版本发布时完全一致的源码。
   ```
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v6.1-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

**方式二**

通过repo + https 下载。

- 从版本分支获取源码。可获取该版本分支的最新源码，包括版本发布后在该分支的合入。
   ```
   repo init -u https://gitcode.com/openharmony/manifest -b OpenHarmony-6.1-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- 从版本发布Tag节点获取源码。可获取与版本发布时完全一致的源码。
   ```
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v6.1-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```


### 从镜像站点获取


**表2** 获取源码路径

| 版本源码 | **版本信息** | **下载站点** | **SHA256校验码** | **软件包容量** |
|---------------------------------------|------------|------------------------------------------------------------|------------------------------------------------------------|--------|
| 全量代码（标准、轻量和小型系统）        | 6.1 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-Release/code-v6.1-Release.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-Release/code-v6.1-Release.tar.gz.sha256) | 64.2 GB |
| Hi3861解决方案（二进制）        | 6.1 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-Release/hispark_pegasus.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-Release/hispark_pegasus.tar.gz.sha256) | 28.8 MB |
| Hi3516解决方案-LiteOS（二进制） | 6.1 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-Release/hispark_taurus_LiteOS.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-Release/hispark_taurus_LiteOS.tar.gz.sha256) | 359.6 MB |
| Hi3516解决方案-Linux（二进制）  | 6.1 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-Release/hispark_taurus_Linux.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-Release/hispark_taurus_Linux.tar.gz.sha256) | 237.7 MB |
| RK3568标准系统解决方案（二进制）ROM包        | 6.1 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-Release/dayu200_standard_arm32_rom.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-Release/dayu200_standard_arm32_rom.tar.gz.sha256) | 	718.0 GB |
| RK3568标准系统解决方案（二进制）XTS包        | 6.1 Release    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-Release/dayu200_standard_arm32_xts.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-Release/dayu200_standard_arm32_xts.tar.gz.sha256) | 	4.4 GB |
| 标准系统Public SDK包（Mac）             | 6.1.0.31 | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-Release/ohos-sdk-mac-public.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-Release/ohos-sdk-mac-public.tar.gz.sha256) | 1.3 GB |
| 标准系统Public SDK包（Mac-M1）             | 6.1.0.31  | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-Release/L2-SDK-MAC-M1-PUBLIC.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-Release/L2-SDK-MAC-M1-PUBLIC.tar.gz.sha256) | 1.2 GB |
| 标准系统Public SDK包（Windows/Linux）   | 6.1.0.31   | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-Release/ohos-sdk-windows_linux-public.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-Release/ohos-sdk-windows_linux-public.tar.gz.sha256) | 	2.3 GB |


## 修复缺陷列表

**表3** 修复缺陷ISSUE列表

| ISSUE单 | 问题描述 | 
| ------- | ------- |
| [19592](https://gitcode.com/openharmony/graphic_graphic_2d/issues/19592) | 仿抖音滑动评论区帧率43 FPS，不满足基线要求。 |
| [588](https://gitcode.com/openharmony/applications_systemui/issues/588) | 进程com.ohos.systemui在wukong压测下出现内存泄露。 |
| [296](https://gitcode.com/openharmony/applications_mms/issues/296)<br />[295](https://gitcode.com/openharmony/applications_mms/issues/295) | 进程com.ohos.mms小概率出现因anonymous或deleteAction导致的jscrash。 |
| [527](https://gitcode.com/openharmony/hiviewdfx_hilog/issues/527) | 进程/system/bin/hilogd下的hilogd.server线程小概率出现cppcrash。 |
| [63972](https://gitcode.com/openharmony/arkui_ace_engine/issues/63972) | 进程com.ohos.contacts下的m.ohos.contacts线程小概率出现因libace_compatible.z.so导致的cppcrash。 |

## 遗留缺陷列表

**表4** 遗留缺陷列表

| ISSUE | 问题描述 | 影响 | 计划解决日期 | 
| -------- | -------- | -------- | -------- |
| [19617](https://gitcode.com/openharmony/graphic_graphic_2d/issues/19617) | 开机完成时延较前一版本稍有劣化。 | 轻微影响使用体验。 | 2026年5月30日 |
| [329](https://gitcode.com/openharmony/applications_contacts/issues/329)<br />[192](https://gitcode.com/openharmony/telephony_telephony_data/issues/192) | 联系人列表滑动帧率低于基线要求。| 轻微影响使用体验。 | 2026年5月30日 |
| [193](https://gitcode.com/openharmony/telephony_telephony_data/issues/193) | 首次启动联系人应用的时间超出基线要求。 | 轻微影响使用体验。 | 2026年5月30日 |
| [73886](https://gitcode.com/openharmony/arkui_ace_engine/issues/73886) | 开机完成时延较长，不满足基线要求。 | 轻微影响使用体验。 | 2026年4月30日 |
| [772](https://gitcode.com/openharmony/applications_photos/issues/772) | 首次启动图库应用的时间超出基线要求。 | 轻微影响使用体验。 | 2026年5月30日 |
| [245](https://gitcode.com/openharmony/device_soc_rockchip/issues/245) | 进程render_service小概率出现因SERVICE_BLOCK导致的sysfreeze，阻塞原因为libmali-bifrost-g52-g7p0-ohos.so故障 | 键鼠卡顿1-2秒，短暂无法操作，1-2秒后自动恢复。 | 2026年6月30日 |
| [246](https://gitcode.com/openharmony/device_soc_rockchip/issues/246) | RK3568在wukong压测下出现重启问题（Kernel panic - not syncing: watchdog pretimeout event） | 重启后恢复正常。 | 2026年6月30日 |
| [248](https://gitcode.com/openharmony/device_soc_rockchip/issues/248) | 进程codec_host下的omx_msg_hdl线程小概率出现cppcrash，崩溃栈为libomxvpu_dec.z.so。 | 键鼠卡顿1-2秒，短暂无法操作，1-2秒后自动恢复。 | 2026年6月30日 |
| [856](https://gitcode.com/openharmony/applications_settings/issues/856) | 进程com.ohos.settings小概率出现由于LIFECYCLE_TIMEOUT导致的sysfreeze。 | 正常业务使用时未复现该问题，对用户影响较小。 | 2026年5月30日 |
| [630](https://gitcode.com/openharmony/applications_systemui/issues/630) | 进程com.ohos.systemui小概率出现jscrash，崩溃栈为subscriberCallBack。 | 设备黑屏后几秒后恢复。 | 2026年3月31日 |
| [12339](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12339) | 主进程com.ohos.systemui小概率出现cppcrash，崩溃栈为libark_jsruntime.so。 | 设备黑屏后几秒后恢复。 | 2026年3月31日 |

<!--no_check-->