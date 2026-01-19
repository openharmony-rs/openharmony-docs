# ExtensionAbility组件
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yewei0794-->
<!--Designer: @jsjzju-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->


[ExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md)组件是一种面向特定场景的应用组件。每一个具体场景对应一个不同类型的ExtensionAbility，例如用于卡片场景的[FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md)，用于输入法场景的[InputMethodExtensionAbility](../reference/apis-ime-kit/js-apis-inputmethod-extension-ability.md)，用于延时任务场景的[WorkSchedulerExtensionAbility](../reference/apis-backgroundtasks-kit/js-apis-WorkSchedulerExtensionAbility.md)等。开发者通过使用不同类型的ExtensionAbility组件，可以扩展和丰富应用功能，更好地与其他应用或系统开展交互。

不同类型ExtensionAbility组件均由系统定义，且通常由相应的系统服务统一管理（例如[InputMethodExtensionAbility](../reference/apis-ime-kit/js-apis-inputmethod-extension-ability.md)组件由输入法管理服务统一管理）。开发者不能直接继承ExtensionAbility组件，只能使用（包括实现或访问）已定义的[ExtensionAbility类型](../reference/apis-ability-kit/js-apis-bundleManager.md#extensionabilitytype)。

## ExtensionAbility类型说明

当前系统已定义的ExtensionAbility类型如下表所示。

> **说明：**
> 
> - “是否允许三方应用实现”是指：三方应用能否继承该类型ExtensionAbility实现自己的业务逻辑。
> - “是否有独立Extension沙箱”是指：该类型ExtensionAbility的沙箱是否与主应用沙箱相对独立、不可互相访问。

| ExtensionAbility类型                 | 功能描述 | 是否允许三<br/>方应用实现                  | 是否有独立<br/>Extension沙箱 |
|--------------------------------------|---------|-------------------------------------------|-----------------------|
| [FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md)  | 卡片扩展能力，用于提供[服务卡片](../form/formkit-overview.md)的相关能力。|  是 | 否 |
| [WorkSchedulerExtensionAbility](../reference/apis-backgroundtasks-kit/js-apis-WorkSchedulerExtensionAbility.md) | 延时任务扩展能力，用于提供[延迟任务](../task-management/work-scheduler.md)的相关能力。      | 是 | 否 |
| [InputMethodExtensionAbility](../reference/apis-ime-kit/js-apis-inputmethod-extension-ability.md) | 输入法扩展能力，用于实现[输入法应用](../inputmethod/ime-kit-intro.md)的开发。      | 是 | 是 |
| <!--Del-->[<!--DelEnd-->ServiceExtensionAbility<!--Del-->](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md)<!--DelEnd-->| 后台服务扩展能力，提供后台运行并对外提供相应能力。<br/>三方应用可以连接该ExtensionAbility，并进行通信。 |否| 否 |
| [AccessibilityExtensionAbility](../reference/apis-accessibility-kit/js-apis-application-accessibilityExtensionAbility.md)|无障碍服务扩展能力，支持访问与操作前台界面。| 是| 否 |
| <!--Del-->[<!--DelEnd-->DataShareExtensionAbility<!--Del-->](../reference/apis-arkdata/js-apis-application-dataShareExtensionAbility-sys.md)<!--DelEnd-->| 数据共享扩展能力，用于对外提供数据读写服务。<br/>三方应用可以连接该ExtensionAbility，进行数据读写。| 否| 否 |
|<!--DelRow-->[StaticSubscriberExtensionAbility](../reference/apis-basic-services-kit/js-apis-application-staticSubscriberExtensionAbility-sys.md)|静态广播扩展能力，用于处理静态事件，比如开机事件。三方应用无法访问。|否| 否 |
|<!--DelRow-->[WallpaperExtensionAbility](../reference/apis-basic-services-kit/js-apis-WallpaperExtensionAbility-sys.md)|壁纸扩展能力，用于实现桌面壁纸。三方应用无法访问。|否| 否 |
| [BackupExtensionAbility](../reference/apis-core-file-kit/js-apis-application-backupExtensionAbility.md) | 数据备份扩展能力，用于提供[备份及恢复应用数据](../file-management/app-file-backup-overview.md)的能力。      | 是 | 否 |
|<!--DelRow-->[WindowExtensionAbility](../reference/apis-arkui/js-apis-application-windowExtensionAbility-sys.md)|界面组合扩展能力，允许系统应用进行跨应用的界面拉起和嵌入。三方应用无法访问。| 否| 否 |
| [EnterpriseAdminExtensionAbility](../reference/apis-mdm-kit/js-apis-EnterpriseAdminExtensionAbility.md)|[企业设备管理扩展能力](../mdm/mdm-kit-admin.md)，提供企业管理时处理管理事件的能力，<br/>比如设备上应用安装事件、锁屏密码输入错误次数过多事件等。|是| 否 |
| [PrintExtensionAbility](../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md)|文件打印扩展能力，提供应用打印照片、文档等办公场景。|是| 否 |
| [ShareExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-shareExtensionAbility.md) | 分享扩展组件，用于提供分享模板服务扩展的能力。 | 是 | 否 |
| [DriverExtensionAbility](../reference/apis-driverdevelopment-kit/js-apis-app-ability-driverExtensionAbility.md)   | 驱动扩展能力，用于提供[驱动相关扩展框架](../device/driver/driverextensionability.md)。      | 是 | 否 |
| [ActionExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-actionExtensionAbility.md)| 自定义服务扩展能力，为开发者提供基于UIExtension的自定义操作业务模板。|是| 否 |
| <!--RP3-->[AdsServiceExtensionAbility](../reference/apis-ads-kit/js-apis-adsserviceextensionability.md)<!--RP3End-->| 广告服务扩展能力，对外提供后台自定义广告业务服务。|是| 否 |
| [EmbeddedUIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-embeddedUIExtensionAbility.md) | 嵌入式UI扩展能力，提供[跨进程界面嵌入](embeddeduiextensionability.md)的能力。 | 是 | 否 |
| [FenceExtensionAbility](../reference/apis-location-kit/js-apis-app-ability-FenceExtensionAbility.md) | 地理围栏扩展能力，用于提供<!--RP1-->地理围栏<!--RP1End-->扩展的能力。 | 是 | 否 |
| [DistributedExtensionAbility](../reference/apis-distributedservice-kit/js-apis-distributedExtensionAbility.md)|分布式扩展能力，提供分布式创建、销毁、连接的生命周期回调。|是| 否 |
| [AppServiceExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md) | 应用后台服务扩展能力，提供应用后台服务的创建、销毁、连接、断开等生命周期回调。 | 是 | 否 |
|<!--DelRow-->[SelectionExtensionAbility](../reference/apis-basic-services-kit/js-apis-selectionInput-selectionExtensionAbility-sys.md) | 划词扩展能力，提供系统应用后台服务的连接和断开等生命周期回调。三方应用无法访问。 | 否 | 否 |
| [FaultLogExtensionAbility](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-FaultLogExtensionAbility.md) | 提供故障延迟通知的能力。| 是 | 否 |
| [WebNativeMessagingExtensionAbility](../reference/apis-arkweb/arkts-apis-web-webNativeMessagingExtensionAbility.md) | Web插件对接能力。提供插件对接native应用能力。 | 是 | 否 |
| [NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md) | 通知订阅拓展能力，用于发送通知数据到三方穿戴设备。 | 是 | 否 |
| [PartnerAgentExtensionAbility](../reference/apis-connectivity-kit/js-apis-fusionConnectivity-partnerAgentExtensionAbility.md) | 基于蓝牙通信技术，提供设备发现与设备下线的通知功能。 | 是 | 否 |
| FileAccessExtensionAbility | 为文件管理器和picker提供统一访问入口，让其他App可以访问由App储存和管理的文档和目录 | 否 | 否 | 
| AdsExtensionAbility | 对外提供后台自定义广告业务服务 | 否 | 否 |
| VoIPExtensionAbility | 网络音视频通话 | 是 | 否 |
| RemoteLocationExtensionAbility | 与Push业务结合构建Location定位类场景化消息，支持APP在Extension中上报地理位置，弹出dialog和通知等等 | 是 | 否 |
| RemoteNotificationExtensionAbility | 与Push业务结合构建IM（Extension扩展）场景化消息，支持Push在代理应用弹出通知栏之前拉起应用紫禁城做通知内容替换 | 是 | 否 |
| PushExtensionAbility | 推送能力管理，查找定位、远程设备连接、配置参数更新、声纹更新 | 是 | 否 |
| CallInfoQueryExtensionAbility | 来去电时，页面显示已安装企业应用的联系人信息，方便用户识别来去电人信息，快速回应，增强企业内部沟通效率。 | 是 | 否 |
| InsightIntentUIExtensionAbility | 为开发者提供能被小艺意图调用，以窗口形态呈现内容的扩展能力。 | 是 | 否 |
| StatusBarViewExtensionAbility | 提供三方接入PC状态栏的能力 | 是 | 否 |
| [PhotoEditorExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-photoEditorExtensionAbility.md) | 提供给应用实现图片编辑的垂域服务能力 | 是 | 否 |
| [AutoFillExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-autoFillExtensionAbility-sys.md) | 供用户应用的免密登录功能 | 否 | 否 |
| [VpnExtensionAbility](../reference/apis-network-kit/js-apis-VpnExtensionAbility.md) | 提供三方VPN创建、销毁等生命周期回调。 | 是 | 否 |
| [FormEditExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formEditExtensionAbility.md) | 卡片统一编辑，用于编辑卡片内容，由卡片应用拓展，由桌面拉起 | 是 | 否 |
| [LiveFormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-LiveFormExtensionAbility.md) | 提供3D Live卡的垂类，由应用实现3D卡片效果，由卡片使用方拉起 | 是 | 否 |
| [UIServiceExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-uiServiceExtensionAbility-sys.md) | 在PC上提供带前台窗口的服务 | 否 | 否 |
<!--RP2--><!--RP2End-->

> **说明：**
> 
> 通常情况下，应用中（同一Bundle名称）所有同一类型的ExtensionAbility均运行在同一个独立进程。以下为例外场景：
>
> - ServiceExtensionAbility（仅系统应用涉及）、DataShareExtensionAbility（仅系统应用涉及）与所有UIAbility均运行在同一个独立进程（主进程）。
> - UIExtensionAbility以及继承该类型的ExtensionAbility可以通过module.json5配置文件中的[extensionProcessMode](../quick-start/module-configuration-file.md#extensionabilities标签)字段，配置进程运行模式。

## 访问指定类型的ExtensionAbility组件

所有类型的[ExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md)组件均不能被应用直接启动，而是由相应的系统管理服务拉起，以确保其生命周期受系统管控，使用时拉起，使用完销毁。ExtensionAbility组件的调用方无需关心目标ExtensionAbility组件的生命周期。

  以[InputMethodExtensionAbility](../reference/apis-ime-kit/js-apis-inputmethod-extension-ability.md)组件为例进行说明，如下图所示，调用方应用发起对InputMethodExtensionAbility组件的调用，此时将先调用输入法管理服务，由输入法管理服务拉起InputMethodExtensionAbility组件，返回给调用方，同时开始管理其生命周期。

**图1** 使用InputMethodExtensionAbility组件

![ExtensionAbility-start](figures/ExtensionAbility-start.png)


## 实现指定类型的ExtensionAbility组件

以实现卡片[FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md)为例进行说明。卡片框架提供了FormExtensionAbility基类，开发者通过派生此基类（如MyFormExtensionAbility），实现回调（如创建卡片的onCreate()回调、更新卡片的[onUpdateForm()](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonupdateform)回调等）来实现具体卡片功能，具体开发指导见[服务卡片](../form/formkit-overview.md)。

卡片FormExtensionAbility实现方不用关心使用方何时去请求添加、删除卡片，FormExtensionAbility实例及其所在的[ExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md)进程的整个生命周期，都是由卡片管理系统服务FormManagerService进行调度管理。

![form_extension](figures/form_extension.png)
