# ExtensionAbility组件
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->


ExtensionAbility组件是一种面向特定场景的应用组件。每一个具体场景对应一个不同类型的ExtensionAbility，例如用于卡片场景的FormExtensionAbility，用于输入法场景的InputMethodExtensionAbility，用于延时任务场景的WorkSchedulerExtensionAbility等。开发者通过使用不同类型的ExtensionAbility组件，可以扩展和丰富应用功能，更好地与其他应用或系统开展交互。

不同类型ExtensionAbility组件均由系统定义，且通常由相应的系统服务统一管理（例如InputMethodExtensionAbility组件由输入法管理服务统一管理）。开发者不能直接继承ExtensionAbility组件，只能使用（包括实现或访问）已定义的ExtensionAbilityType。

## ExtensionAbility类型说明

当前系统已定义的ExtensionAbility类型如下表所示。

> **说明：**
> 
> - “是否允许三方应用实现”是指：三方应用能否继承该类型ExtensionAbility实现自己的业务逻辑。
> - “是否有独立Extension沙箱”是指：该类型ExtensionAbility的沙箱是否与主应用沙箱相对独立、不可互相访问。

<!--Table: 20%; 50%; 15%; 15%-->
| ExtensionAbility类型                 | 功能描述 | 是否允许三方应用实现                  | 是否有独立Extension沙箱 |
|--------------------------------------|---------|-------------------------------------------|-----------------------|
| FormExtensionAbility  | 卡片扩展能力，用于提供服务卡片的相关能力。|  是 | 否 |
| WorkSchedulerExtensionAbility | 延时任务扩展能力，用于提供延迟任务的相关能力。      | 是 | 否 |
| InputMethodExtensionAbility | 输入法扩展能力，用于实现输入法应用的开发。      | 是 | 是 |
| <!--Del--><!--DelEnd-->ServiceExtensionAbility<!--Del--><!--DelEnd-->| 后台服务扩展能力，提供后台运行并对外提供相应能力。<br/>三方应用可以连接该ExtensionAbility，并进行通信。 |否| 否 |
| AccessibilityExtensionAbility|无障碍服务扩展能力，支持访问与操作前台界面。| 是| 否 |
| <!--Del--><!--DelEnd-->DataShareExtensionAbility<!--Del--><!--DelEnd-->| 数据共享扩展能力，用于对外提供数据读写服务。| 否| 否 |
|<!--DelRow-->StaticSubscriberExtensionAbility|静态广播扩展能力，用于处理静态事件，比如开机事件。三方应用无法访问。|否| 否 |
|<!--DelRow-->WallpaperExtensionAbility|壁纸扩展能力，用于实现桌面壁纸。三方应用无法访问。|否| 否 |
| BackupExtensionAbility | 数据备份扩展能力，用于提供备份及恢复应用数据的能力。      | 是 | 否 |
|<!--DelRow-->WindowExtensionAbility|界面组合扩展能力，允许系统应用进行跨应用的界面拉起和嵌入。三方应用无法访问。| 否| 否 |
| EnterpriseAdminExtensionAbility|企业设备管理扩展能力，提供企业管理时处理管理事件的能力，<br/>比如设备上应用安装事件、锁屏密码输入错误次数过多事件等。|是| 否 |
| PrintExtensionAbility|文件打印扩展能力，提供应用打印照片、文档等办公场景。|是| 否 |
| ShareExtensionAbility | 分享扩展组件，用于提供分享模板服务扩展的能力。 | 是 | 否 |
| DriverExtensionAbility   | 驱动扩展能力，用于提供驱动相关扩展框架。      | 是 | 否 |
| ActionExtensionAbility| 自定义服务扩展能力，为开发者提供基于UIExtension的自定义操作业务模板。|是| 否 |
| <!--RP3-->AdsServiceExtensionAbility<!--RP3End-->| 广告服务扩展能力，对外提供后台自定义广告业务服务。|是| 否 |
| EmbeddedUIExtensionAbility | 嵌入式UI扩展能力，提供跨进程界面嵌入的能力。 | 是 | 否 |
| FenceExtensionAbility | 地理围栏扩展能力，用于提供<!--RP1-->地理围栏<!--RP1End-->扩展的能力。 | 是 | 否 |
| DistributedExtensionAbility|分布式扩展能力，提供分布式创建、销毁、连接的生命周期回调。|是| 否 |
| AppServiceExtensionAbility | 应用后台服务扩展能力，提供应用后台服务的创建、销毁、连接、断开等生命周期回调。 | 是 | 否 |
| SelectionExtensionAbility | 划词扩展能力，提供系统应用后台服务的连接和断开等生命周期回调。| 是 | 否 |
| FaultLogExtensionAbility | 提供故障延迟通知的能力。| 是 | 否 |
| WebNativeMessagingExtensionAbility | Web插件对接能力。提供插件对接native应用能力。 | 是 | 否 |
| NotificationSubscriberExtensionAbility | 通知订阅拓展能力，用于发送通知数据到三方穿戴设备。 | 是 | 否 |
| PartnerAgentExtensionAbility | 基于蓝牙通信技术，提供设备发现与设备下线的通知功能。 | 是 | 否 |
| PhotoEditorExtensionAbility | 照片编辑扩展能力，提供给应用实现图片编辑的功能。 | 是 | 否 |
|<!--DelRow-->AutoFillExtensionAbility| 自动填充扩展能力，提供自动填充和保存功能。 | 否 | 否 |
| VpnExtensionAbility | VPN扩展能力，提供三方VPN创建、销毁等生命周期回调。 | 是 | 否 |
| FormEditExtensionAbility | 卡片编辑扩展能力，提供卡片页面编辑能力，支持实现用户自定义卡片内容的功能，例如：编辑联系人卡片、修改卡片中展示的联系人、编辑天气卡片等。 | 是 | 否 |
| LiveFormExtensionAbility | 卡片动效扩展能力，提供卡片动效能力，例如卡片破框动效，丰富信息提醒、浅层交互功能，显著提升用户体验。 | 是 | 否 |
|<!--DelRow-->UIServiceExtensionAbility| UI服务扩展能力，在PC/2in1上提供带前台窗口的服务。 | 否 | 否 |
<!--RP2--><!--RP2End-->

> **说明：**
> 
> 通常情况下，应用中（同一Bundle名称）所有同一类型的ExtensionAbility均运行在同一个独立进程。以下为例外场景：
>
> - ServiceExtensionAbility（仅系统应用涉及）、DataShareExtensionAbility（仅系统应用涉及）与所有UIAbility均运行在同一个独立进程（主进程）。
> - UIExtensionAbility以及继承该类型的ExtensionAbility可以通过module.json5配置文件中的extensionProcessMode字段，配置进程运行模式。
> - AppServiceExtensionAbility可以通过module.json5配置文件中的extensionProcessMode字段，配置进程运行模式。

## 访问指定类型的ExtensionAbility组件

所有类型的ExtensionAbility组件均不能被应用直接启动，而是由相应的系统管理服务拉起，以确保其生命周期受系统管控，使用时拉起，使用完销毁。ExtensionAbility组件的调用方无需关心目标ExtensionAbility组件的生命周期。

  以InputMethodExtensionAbility组件为例进行说明，如下图所示，调用方应用发起对InputMethodExtensionAbility组件的调用，此时将先调用输入法管理服务，由输入法管理服务拉起InputMethodExtensionAbility组件，返回给调用方，同时开始管理其生命周期。

**图1** 使用InputMethodExtensionAbility组件

![ExtensionAbility-start](figures/ExtensionAbility-start.png)


## 实现指定类型的ExtensionAbility组件

以实现卡片FormExtensionAbility为例进行说明。卡片框架提供了FormExtensionAbility基类，开发者通过派生此基类（如MyFormExtensionAbility），实现回调（如创建卡片的onCreate()回调、更新卡片的onUpdateForm()回调等）来实现具体卡片功能，具体开发指导见服务卡片。

卡片FormExtensionAbility实现方不用关心使用方何时去请求添加、删除卡片，FormExtensionAbility实例及其所在的ExtensionAbility进程的整个生命周期，都是由卡片管理系统服务FormManagerService进行调度管理。

![form_extension](figures/form_extension.png)
