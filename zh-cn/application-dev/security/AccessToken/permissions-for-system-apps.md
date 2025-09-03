# 可使用ACL申请的系统应用可用权限（系统授权）

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

在申请目标权限前，建议开发者先了解[不同权限的申请路径](determine-application-mode.md)，对权限的工作流程有基本了解后，再结合以下权限字段的具体说明，判断应用能否申请目标权限，提高开发效率。

> **说明：**
>
> - 以下权限仅对APL等级为system_basic及以上的应用开放，不向APL等级为normal的应用开放。
> - 以下权限的授权方式均为system_grant（系统授权）。
> - 以下权限可通过[访问控制列表（ACL）](app-permission-mgmt-overview.md#权限机制中的基本概念)的方式跨级别申请。

申请流程可参考[选择申请权限的方式](determine-application-mode.md)。

## ohos.permission.PRE_START_ATOMIC_SERVICE

允许应用市场跳过loading弹框并为原子化服务提前打开窗口，并在窗口内部显示加载动效。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGE_APP_KEEP_ALIVE

允许对三方应用进程设置保活。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：14

## ohos.permission.ACCESS_BBOX_DIR

允许系统应用读取bbox路径下的日志文件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.CONTROL_LOCATION_SWITCH

允许应用打开和关闭位置信息开关。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.LOCATION_SWITCH_IGNORED

允许系统应用在位置开关关闭的情况下，获取位置信息。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.SUBSCRIBE_SWING_ABILITY

允许应用使用智慧感知订阅能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGER_SWING_MOTION

允许应用使用隔空手势自适配能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MOCK_LOCATION

允许应用使用模拟位置功能。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_LEARN_MORE_DIALOG

允许系统应用拉起“进一步了解”的展示弹窗，获取更多详细信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.WRITE_PROTECTION_ADVICE_POLICY

允许系统应用修改“安全建议”的数据库。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：17

## ohos.permission.READ_PROTECTION_ADVICE_POLICY

允许系统应用读取“安全建议”的数据库。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：17

## ohos.permission.PROXY_MESSAGE_AUTH

允许系统应用调用“信息”应用授权接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**起始版本**：18

## ohos.permission.MANAGE_SETTINGS

允许应用设置SettingsData中设备级配置数据表和用户级配置数据表。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_SCREEN_LOCK

允许应用访问锁屏信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ALLOW_UPGRADE_GUIDE_ACCESS

允许系统应用获取应用的升级引导数据或拉起应用的升级引导组件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_MEDIALIB_THUMB_DB

允许系统应用访问和修改媒体库数据库。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.AGENT_REQUIRE_FORM

允许应用代理请求卡片。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.MANAGE_VPN

允许系统应用启动或停止VPN功能。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

**变更信息**：API 10-11，ACL使能为false；从API 12开始，变更为true。

## ohos.permission.WAKEUP_VISION

允许应用访问语音助手视觉组件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.WAKEUP_VOICE

允许应用访问语音助手唤醒组件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.ATTEST_KEY

允许应用获取用于证明密钥合法性的证书链。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.GET_PHONE_NUMBERS

允许应用读取设备的本机号码。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.ACTIVATE_THEME_PACKAGE

允许系统应用设置主题内容，包括壁纸、图标、皮肤、AOD 和字体等。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.QUERY_ACCESSIBILITY_ELEMENT

允许批量查询无障碍节点。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.SET_UNREMOVABLE_NOTIFICATION

允许应用发布不可被移除通知。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.UNINSTALL_BUNDLE

允许应用卸载应用。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.RECOVER_BUNDLE

允许恢复预置应用。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.UPDATE_SYSTEM

允许调用升级接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.FACTORY_RESET

允许调用恢复出厂接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.ASSIST_DEVICE_UPDATE

允许拉起升级服务对其他设备做辅助、协同升级。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.PLUGIN_UPDATE

允许业务方调用升级相关接口完成插件、AI模型的后下载和更新业务。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.RECEIVE_UPDATE_MESSAGE

允许应用、服务监听系统升级流程中的关键事件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.GET_ALL_PROCESSES

允许系统服务或系统应用查看/proc下全部文件。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGE_LOCAL_ACCOUNTS

允许应用管理系统本地账号。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.ACCESS_SYSTEM_SETTINGS

允许应用接入或拉起系统设置界面。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.SET_ABILITY_CONTROLLER

允许应用拦截Ability组件启动，主要用测试调试，比如：稳定性金刚测试。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

允许应用跨系统本地账号交互。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.CLEAN_APPLICATION_DATA

允许应用清理应用数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.START_ABILITIES_FROM_BACKGROUND

允许应用在后台启动或者访问其他组件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.MANAGE_MISSIONS

允许应用管理系统中的任务。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN

允许应用激活设备管理应用。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.ENTERPRISE_CONFIG

允许应用激活企业设备。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.RECEIVE_ENTERPRISE_POLICY_EVENT

允许系统应用订阅企业设备管理策略事件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：14

## ohos.permission.PUBLISH_SYSTEM_COMMON_EVENT

允许应用发布系统公共事件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.NOTIFICATION_CONTROLLER

允许应用管理通知和订阅通知。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.CLOUDDATA_CONFIG

允许应用获取配置数据库端云信息能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.GET_DEFAULT_APPLICATION

允许应用查询默认应用。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.MANAGE_INTELLIGENT_VOICE

允许应用访问智能语音服务接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.POWER_MANAGER

允许应用调用电源管理子系统的接口休眠或者唤醒设备。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.GET_SCENE_CODE

允许应用获取指定应用当前的场景值。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.MANAGE_ECOLOGICAL_RULE

允许为管控服务设置场景值生成规则和配套的体验。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.INSTALL_ENTERPRISE_BUNDLE

允许应用安装企业InHouse应用。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.INSTALL_BUNDLE

允许应用安装、卸载其他应用（除了企业相关应用，目前有企业InHouse应用，企业MDM应用和企业normal应用）。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.MANAGE_SHORTCUTS

允许应用查询其他应用的快捷方式信息、启动其他应用的快捷方式。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.OBSERVE_FORM_RUNNING

允许应用监听卡片运行状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.WRITE_HIVIEW_SYSTEM

允许应用修改hiview的数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.READ_HIVIEW_SYSTEM

允许应用访问hiview的数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.READ_DFX_SYSEVENT

允许应用访问系统事件打点数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.READ_DFX_XPOWER

允许应用访问xpower的数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.PERMISSION_USED_STATS

允许系统应用访问权限使用记录。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.PERMISSION_RECORD_TOGGLE

允许应用设置权限使用记录开关。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.CAPTURE_SCREEN

允许应用截取屏幕图像。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

允许应用进行用户公共证书凭据的安装、卸载、授权等操作。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

**变更信息**：API 9-11，权限级别为system_basic；从API 12开始，变更为system_core。

## ohos.permission.CLOUDFILE_SYNC

允许应用使用端云同步能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.CHANGE_OVERLAY_ENABLED_STATE

允许系统应用禁用使能overlay特性的应用。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.ACCESS_SCREEN_LOCK_INNER

允许应用使用锁屏服务的锁定屏幕、发送锁屏事件、系统事件回调功能。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.BACKUP

允许应用拥有备份恢复能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.MOUNT_FORMAT_MANAGER

允许应用对外卡进行格式化操作。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.MOUNT_UNMOUNT_MANAGER

允许应用对外卡进行挂载、卸载操作。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.PROXY_AUTHORIZATION_URI

允许应用代理授权URI。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.ACCESS_CAST_ENGINE_MIRROR

允许应用使用镜像投屏能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.ACCESS_CAST_ENGINE_STREAM

允许应用调用系统资源投射能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE

允许在企业设备上安装企业normal应用包。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.UPDATE_MIGRATE

允许升级过程中进行数据迁移。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.MANAGE_SENSOR

允许不直接使用传感器的应用打开和关闭传感器。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.MANAGE_PRINT_JOB

允许应用获取管理打印任务的能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.securityguard.SET_MODEL_STATE

允许应用控制设备风险管理平台模型开关。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.UNLOCK_DEVELOPER_MODE

允许应用解锁开发者模式。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.CAPTURE_VOICE_DOWNLINK_AUDIO

允许应用采集语音下行音频。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.GET_WIFI_INFO_INTERNAL

允许系统进程获取Wi-Fi相关参数。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.ACCESS_BUNDLE_DIR

允许应用访问其他应用安装目录。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.CHANGE_ABILITY_ENABLED_STATE

允许改变应用或者组件的使能状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.CLOUDFILE_SYNC_MANAGER

允许应用获取端云同步管理能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.DUMP

允许导出系统基础信息和SA服务信息。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.DEVICE_STANDBY_EXEMPTION

允许应用在系统待机模式正常使用资源。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.PERCEIVE_SMART_POWER_SCENARIO

允许应用感知智慧功耗场景。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGE_CAMERA_CONFIG

允许应用进行全局相机开关等操作。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.MANAGE_AUDIO_CONFIG

允许应用进行全局麦克风静音等操作。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.MICROPHONE_CONTROL

允许应用进行持久化全局麦克风静音等操作。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.CAPTURE_PLAYBACK

允许系统服务不通过录屏框架，直接进行音频内录。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.MICROPHONE_BACKGROUND

允许系统应用在后台使用麦克风。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.START_DLP_CRED

允许系统应用或者系统服务拉起DLP凭据管理应用。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.START_SHORTCUT

允许应用拉起快捷方式。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.PRELOAD_UI_EXTENSION_ABILITY

预拉起UIExtensionAbility实例。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGE_DISPOSED_APP_STATUS

允许设置和查询应用的处置状态。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.GET_DISPOSED_APP_STATUS

允许查询应用的处置状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.FILE_ACCESS_MANAGER

允许文件管理类应用通过FAF框架访问公共数据文件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.ACCESS_PUSH_SERVICE

允许应用访问推送服务的Ability。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.MANAGE_NET_STRATEGY

允许应用程序获取网络策略相关的信息或修改网络策略相关设置。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.securityguard.REQUEST_SECURITY_EVENT_INFO

允许应用获取风险详细数据。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.securityguard.REPORT_SECURITY_INFO

允许应用上报风险数据至设备风险管理平台。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.GET_SENSITIVE_PERMISSIONS

允许应用读取其他应用的敏感权限的状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**支持设备**：General

**ACL使能**：true

**起始版本**：8

## ohos.permission.ACCESS_SERVICE_DM

允许系统应用获取分布式设备的认证组网能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.UPLOAD_SESSION_MANAGER

允许应用管理上传任务会话。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.ABILITY_BACKGROUND_COMMUNICATION

允许应用将Ability组件在后台启动并与该Ability建立通信连接。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.ACCESS_DLP_FILE

允许对DLP文件进行权限配置和管理。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.ACCESS_IDS

允许应用查询设备的唯一标识符信息。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.ACCESS_MISSIONS

允许应用访问任务栈信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

**废弃版本**：9

## ohos.permission.BUNDLE_ACTIVE_INFO

允许系统应用查询其他应用在前台或后台的运行时间。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.CONNECT_IME_ABILITY

允许绑定输入法Ability（InputMethodAbility）。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.CONNECT_SCREEN_SAVER_ABILITY

允许绑定屏保Ability（ScreenSaverAbility）。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.CONNECTIVITY_INTERNAL

允许应用程序获取网络相关的信息或修改网络相关设置。当前仅支持系统应用申请该权限。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.CONTROL_TASK_SYNC_ANIMATOR

允许应用使用同步任务动画。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.DOWNLOAD_SESSION_MANAGER

允许应用管理下载任务会话。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.GET_DISTRIBUTED_ACCOUNTS

允许应用查询系统分布式账号信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.GET_LOCAL_ACCOUNTS

允许应用查询系统本地账号信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.GET_TELEPHONY_STATE

允许应用读取电话信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.ACCESS_BOOSTER_SERVICE

允许系统服务或系统应用调用网络增强服务中的网络质量感知、网络场景预测、网络加速等功能接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.GET_WALLPAPER

允许应用读取壁纸文件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.GRANT_SENSITIVE_PERMISSIONS

允许应用为其他应用授予敏感权限。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**支持设备**：General

**ACL使能**：true

**起始版本**：8

## ohos.permission.LAUNCH_DATA_PRIVACY_CENTER

允许应用从其隐私声明页面跳转至“数据与隐私”页面。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.LISTEN_BUNDLE_CHANGE

允许应用监听其他应用安装、更新、卸载状态的变化。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.MANAGE_BLUETOOTH

允许应用配对蓝牙设备，并对设备的电话簿或消息进行访问。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS

允许应用管理系统分布式账号信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.MANAGE_MEDIA_RESOURCES

允许应用程序获取当前设备正在播放的媒体资源，并对其进行管理。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.MANAGE_SECURE_SETTINGS

允许应用修改安全类系统设置。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.MANAGE_WIFI_CONNECTION

允许应用管理Wi-Fi的连接。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.MANAGE_WIFI_HOTSPOT

允许应用开启或关闭Wi-Fi热点。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.NOTIFICATION_AGENT_CONTROLLER

允许应用发送代理通知。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.PLACE_CALL

允许应用直接拨打电话。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.POWER_OPTIMIZATION

允许系统应用设置省电模式、获取省电模式的配置信息并接收配置变化的通知。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.PROVISIONING_MESSAGE

允许激活超级设备管理器应用。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.radio.ACCESS_FM_AM

允许应用获取收音机相关服务。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.READ_SCREEN_SAVER

允许应用查询屏保状态信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.REBOOT

允许应用重启设备。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.REBOOT_RECOVERY

允许系统应用重启设备并进入恢复模式。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.REFRESH_USER_ACTION

允许应用在收到用户事件时，重新计算超时时间。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.REMOVE_CACHE_FILES

允许清理指定应用的缓存。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.REQUIRE_FORM

允许应用获取Ability Form。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.START_DESKTOP_UI_COMPONENT

允许应用拉起桌面组件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.REVOKE_SENSITIVE_PERMISSIONS

允许应用撤销给其他应用授予的敏感权限。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**支持设备**：General

**ACL使能**：true

**起始版本**：8

## ohos.permission.RUN_ANY_CODE

允许应用运行未签名的代码。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.sec.ACCESS_UDID

允许系统应用获取UDID。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.securityguard.REQUEST_SECURITY_MODEL_RESULT

允许应用获取设备风险状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.SET_DEFAULT_APPLICATION

允许应用设置、重置默认应用。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.SET_TELEPHONY_STATE

允许应用修改telephony的状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.SET_TIME

允许应用修改系统时间。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.SET_TIME_ZONE

允许应用修改系统时区。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.START_ABILIIES_FROM_BACKGROUND

允许应用在后台启动FA。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

**废弃版本**：9

## ohos.permission.START_INVISIBLE_ABILITY

无论Ability是否可见，都允许应用进行调用。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.STORAGE_MANAGER

允许应用调用storage manager服务中对空间统计以及卷信息的查询接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：9

## ohos.permission.UPDATE_CONFIGURATION

允许更新系统配置。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.WRITE_SCREEN_SAVER

允许应用修改屏保状态信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：7

## ohos.permission.GET_BLUETOOTH_LOCAL_MAC

允许应用获取本机的蓝牙MAC地址。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.GET_BLUETOOTH_PEERS_MAC

允许应用获取外设的蓝牙真实MAC地址。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.USE_USER_IDM

允许应用访问系统身份凭据信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.MANAGE_USER_IDM

允许录入和管理用户身份认证凭据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.ACCESS_PIN_AUTH

允许注册口令认证过程获取口令数据的回调。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.ACCESS_USER_AUTH_INTERNAL

允许调用统一身份认证服务的系统内部接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：8

## ohos.permission.SUPPORT_USER_AUTH

统一用户认证控件资源池访问权限。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.ACCESS_SENSING_WITH_ULTRASOUND

允许应用使用超声波感知。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

## ohos.permission.ACCESS_DISTRIBUTED_HARDWARE

允许系统服务或系统应用访问分布式硬件资源。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.INSTANTSHARE_SWITCH_CONTROL

允许系统服务或系统应用变更近场分享开关状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.ACCESS_INSTANTSHARE_SERVICE

允许系统服务或系统应用访问近场分享服务。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.ACCESS_INSTANTSHARE_PRIVATE_ABILITY

允许系统服务或系统应用使用近场分享私有应用能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.ACCESS_MCP_AUTHORIZATION

允许MCP宿主应用代理其子应用进行用户账号授权登录。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.GET_BUNDLE_RESOURCES

允许查询应用的资源信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.COOPERATE_MANAGER

允许系统应用使能键鼠穿越能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.PERCEIVE_TRAIL

允许系统应用使用MSDP足迹感知功能。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.EXECUTE_INSIGHT_INTENT

允许系统应用执行意图调用。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.VERIFY_ACTIVATION_LOCK

允许应用校验激活锁凭据合法性。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.ACCESS_OUC

允许系统应用拉起软件更新能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.MANAGE_FINGERPRINT_AUTH

允许调用配置和管理指纹认证模块的接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.TRUSTED_RING_HASH_DATA_PERMISSION

允许应用向关键资产信任环发送数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.INPUT_CONTROL_DISPATCHING

允许系统应用屏蔽快捷键分发逻辑。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.MANAGE_TRUSTED_RING

允许使用关键资产信任环服务提供的能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.USE_TRUSTED_RING

允许应用或服务使用关键资产信任环加环能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.RECEIVE_APP_INSTALL_INFO_CHANGE

允许应用监听其他应用的安装进度。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.LAUNCH_SPAMSHIELD_PAGE

允许应用访问骚扰拦截页面。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_SPAMSHIELD_SERVICE

允许应用访问骚扰拦截能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_SECURITY_PRIVACY_CENTER

允许业务接入安全隐私中心。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.GET_SECURITY_PRIVACY_ADVICE

允许系统应用获取安全隐私中心建议相关数据。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.SET_SECURITY_PRIVACY_ADVICE

允许系统应用处理安全隐私中心保护建议。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.USE_SECURITY_PRIVACY_MESSAGER

允许系统服务调用权限管理相关接口。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.GET_PRIVACY_INDICATOR

允许系统应用获取隐私权限事件提醒信息详情。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.SET_PRIVACY_INDICATOR

允许系统应用控制隐私权限事件提醒的呈现状态。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.EXEMPT_PRIVACY_INDICATOR

允许应用在使用权限时不呈现提醒。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.EXEMPT_CAMERA_PRIVACY_INDICATOR

允许应用在使用相机权限时不呈现提醒。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.EXEMPT_MICROPHONE_PRIVACY_INDICATOR

允许应用在使用麦克风权限时不呈现提醒。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.EXEMPT_LOCATION_PRIVACY_INDICATOR

允许应用在使用位置权限时不呈现提醒。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.EXEMPT_PRIVACY_SECURITY_CENTER

允许系统应用在“隐私和安全”中的权限详情页不展示。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.GET_SUPER_PRIVACY

允许获取超级隐私模式的状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.SET_SUPER_PRIVACY

允许设置超级隐私模式的状态。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_PRIVATE_SPACE_MANAGER

允许系统应用或系统服务拉起隐私空间管理。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_PRIVATE_SPACE_PASSWORD_PROTECT

允许系统应用调用隐私空间服务密码保护相关接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_PASSWORDVAULT_ABILITY

允许系统应用或系统服务拉起密码保险箱能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.ACCESS_TEXTAUTOFILL_ABILITY

允许系统应用或系统服务拉起文本智能填充应用管理页面。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_LOWPOWER_MANAGER

允许系统应用或系统服务向lowpowermanager发送消息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.MANAGE_APP_BOOT

允许系统应用设置其他应用开机自启配置。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.ACCESS_ACCOUNT_KIT_SERVICE

允许账号服务查询、修改账号数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.REQUEST_ANONYMOUS_ATTEST

允许系统应用使用设备匿名证明能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.ACCESS_ACCOUNT_KIT_UI

允许系统应用拉起账号用户认证界面。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.START_RECENT_ABILITY

允许应用启动指定的UIAbility，如果该UIAbility有多个实例，将启动最近启动的实例。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.MANAGE_CLOUD_SYNC_CONFIG

允许接入云空间的应用管理应用云同步相关配置。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.ACCESS_FINDDEVICE

允许应用拉起“查找设备”应用。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.MANAGE_FINDSERVICE

允许系统应用获取“查找我的设备”开关状态和打开开关。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.READ_FINDSERVICE

允许系统应用读取“查找我的设备”开关状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGE_USB_CONFIG

允许应用管理USB设备功能和端口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.START_SYSTEM_DIALOG

允许应用拉起模系统弹窗。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.ACCESS_STATUSBAR_ICON

允许应用接入状态栏图标。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

允许应用管理系统音效。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.SECURE_PASTE

允许应用静默读取剪贴板。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.SET_CODE_PROTECT_INFO

允许系统应用设置云侧公钥以及工作秘钥密文，并协商代码保护秘钥信息。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.SET_ADVANCED_SECURITY_MODE

允许应用修改坚盾守护模式配置。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.SET_DEVELOPER_MODE

允许应用修改开发者模式配置。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.DISABLE_PERMISSION_DIALOG

允许系统应用去设置指定应用能否拉起权限弹窗。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.MANAGE_ACTIVATION_LOCK

允许应用管理设备激活锁。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.MANAGE_PRIVATE_PHOTOS

允许应用访问系统预置隐藏相册及相册内文件。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.RECORD_VOICE_CALL

允许应用录制通话内容。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.MANAGE_APP_INSTALL_INFO

允许应用创建、管理应用安装任务。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.MANAGE_APP_UNINSTALL

允许系统应用卸载其它应用。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：19

## ohos.permission.ACCESS_ADVANCED_SECURITY_MODE

允许系统应用打开坚盾守护模式配置界面。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.ACCESS_HIVIEWX

允许系统应用拉起“用户体验改进计划”。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.ACCESS_HIVIEWCARE

允许系统应用拉起智能检测能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.SET_SANDBOX_POLICY

允许系统应用设置动态沙箱策略。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.CHECK_SANDBOX_POLICY

允许系统应用或系统服务查询其他应用的沙箱管控策略。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：15

## ohos.permission.TRIGGER_ACTIVATIONLOCK

允许系统SA调用“查找设备”。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.WRITE_PRIVACY_PUSH_DATA

允许应用往另一个应用中写入隐私Push数据。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：11

## ohos.permission.READ_PRIVACY_PUSH_DATA

允许应用读取另一个应用中的Push隐私数据。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGE_NEARLINK

允许应用配对星闪设备，并对设备的电话簿或消息进行访问。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.GET_NEARLINK_LOCAL_MAC

允许应用获取本机的星闪MAC地址。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.GET_NEARLINK_PEER_MAC

允许应用获取对端设备的星闪MAC地址。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGE_UWB

允许系统应用管理UWB功能。

例如开关UWB、查询芯片类型、查询UWB支持能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.USE_UWB_RANGING

允许系统应用使用UWB测距功能。

例如打开测距会话、启动测距、停止测距、关闭测距会话等。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGE_FINDNETWORK

允许应用管理“查找”网络开关，并可以对物品进行配对、解配对。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.OPERATE_FINDNETWORK

允许应用调用“查找”网络操作类接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.QUERY_FINDNETWORK_LOCATION

允许应用使用“查找”网络查询设备离线位置的功能。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.REGISTER_FINDNETWORK_ACCESSORY

允许应用和系统服务发起查找网络配件注册流程。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.MANAGE_SHUTDOWN_FINDNETWORK

允许应用和系统服务管理设备关机查找功能。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：15

## ohos.permission.MANAGE_RGM

允许系统服务或系统应用管理RGM。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_PROTOCOL_DFX_DATA

允许系统应用读取通讯故障及系统统计信息等数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_PROTOCOL_DFX_STATE

允许系统应用打开或关闭通信协议相关的开关。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_CMAP_SERVICE

允许系统应用访问通信地图服务。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：14

## ohos.permission.MANAGE_USER_ACCOUNT_INFO

允许系统应用及系统SA调用账号服务。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ALLOW_TIPS_ACCESS

允许系统应用拉起其他系统应用的对外暴露组件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_AI_ABILITY

允许应用和系统SA调用语音视觉服务的接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.READ_HEALTH_MOTION

允许系统应用读取步数及运动三环信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.hsdr.REQUEST_HSDR

允许系统应用访问安全检测响应框架安全策略云查功能。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.WRITE_GTOKEN_POLICY

允许系统应用写入应用管控策略。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.READ_GTOKEN_POLICY

允许系统应用读取应用管控策略。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.NOTIFY_DEBUG_ASSERT_RESULT

允许应用设置断言调试结果。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.QUERY_PASSWORD_VAULT_DATA

允许应用获取密码保险箱账号数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.WRITE_ACCOUNT_LOGIN_STATE

允许用户账号往数据管理服务写入自己的登录状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_AS_USER

允许U0用户空间业务调用账号开放能力API。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.SUBSCRIBE_NOTIFICATION_WINDOW_STATE

允许应用订阅通知面板显示或收起时发送的广播。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.CHANGE_DISPLAYMODE

允许系统应用改变屏幕模式。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MIGRATE_DATA

允许应用迁移传入路径下的数据到指定目录。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_DYNAMIC_ICON

允许应用使用动态图标。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.CHANGE_BUNDLE_UNINSTALL_STATE

允许系统应用改变指定应用的可卸载状态。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGE_STYLUS_EVENT

允许系统应用使用手写笔系统能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.USE_CLOUD_DRIVE_SERVICE

允许应用和服务使用云空间服务进行端云数据同步。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.USE_CLOUD_BACKUP_SERVICE

允许应用和服务触发云空间云备份任务执行和通知备份相关事件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.USE_CLOUD_COMMON_SERVICE

允许应用通过云空间公共服务获取云空间相关信息和资源。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.PRELOAD_APPLICATION

允许系统应用或系统服务预加载应用进程。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ENABLE_EXPERIENCE_HBM

允许应用启用屏幕HBM（High Brightness Mode）亮度模式。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.SET_PROCESS_CACHE_STATE

允许应用设置是否支持应用缓存及缓存后快速启动。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_SYSTEM_APP_CERT

允许调用方管理和使用系统业务证书凭据。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_USER_TRUSTED_CERT

允许调用方管理用户CA证书。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_LOCAL_BACKUP

允许应用访问本地备份数据目录。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.CAST_AUDIO_OUTPUT

允许系统投播/协同应用发起音频投播。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.WRITE_RINGTONE

允许铃音库进行写操作。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.GET_ACCOUNT_MINORS_INFO

允许系统应用获取用户账号的未成年使用者信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_LOCAL_THEME

允许系统应用访问下载到本地的主题内容。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_SHADER_CACHE_DIR

允许系统应用访问shader_cache主目录。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.INSTALL_CLONE_BUNDLE

允许应用安装应用分身。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.UNINSTALL_CLONE_BUNDLE

允许应用卸载应用分身。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_SCREEN_LOCK_MEDIA_DATA

允许应用在锁屏后继续访问媒体图片和视频数据。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_SCREEN_LOCK_ALL_DATA

允许应用在锁屏后继续访问媒体图片和视频、通话记录、通话录音、短信内容、邮箱等敏感数据。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_DEVICE_COLLABORATION_PRIVATE_ABILITY

允许系统服务或系统应用访问多屏协同私有应用能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_FILE_CONTENT_SHARE

允许系统服务或系统应用访问共享文件内容。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_RINGTONE_RESOURCE

允许系统应用访问和写入铃音数据公共目录的权限。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_SUBSCRIPTION_CAPSULE_DATA

允许系统应用访问订阅胶囊数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_SEARCH_SERVICE

允许系统应用调用融合搜索服务提供的本地搜索能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.INJECT_INPUT_EVENT

允许系统应用注入输入事件。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.QUERY_SECURITY_EVENT

允许应用获取风险详细数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.REPORT_SECURITY_EVENT

允许应用上报风险数据至设备风险管理平台。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.QUERY_SECURITY_MODEL_RESULT

允许应用查询安全模型执行结果。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGE_SECURITY_GUARD_CONFIG

允许应用管理设备风险管理部件的配置。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.COLLECT_SECURITY_EVENT

允许应用采集安全事件。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.QUERY_SECURITY_POLICY_FROM_CLOUD

允许应用从云侧查询安全策略。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.REPORT_SECURITY_EVENT_TO_CLOUD

允许应用上报安全事件到云侧。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_SCAN_SERVICE

允许系统应用调用扫码直达服务提供的码值分发能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_FACTORY_OTA_DIR

允许系统应用访问无线升级目录。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGE_MOUSE_CURSOR

允许系统应用设置鼠标光标相关状态。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.FILTER_INPUT_EVENT

允许系统应用过滤输入事件。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.INPUT_DEVICE_CONTROLLER

允许应用查询和设置输入设备相关状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACTIVATE_DEVICE_PSI

允许系统应用或系统服务上报设备激活状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.DUMP_AUDIO

允许应用启动音频框架dump能力，将音频数据落盘到本地。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.RECEIVE_FUSION_MESSAGES

允许系统服务或系统应用接收融合服务消息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.RECEIVE_BMS_BROKER_MESSAGES

允许系统服务或系统应用接收包管理代理服务消息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACCESS_FUSION_MANAGER

允许系统服务或系统应用访问融合服务。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.PUBLISH_LOCATION_EVENT

允许应用发布位置管理相关的公共事件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_MULTICORE_HYBRID_ABILITY

允许应用访问智能手表系统服务。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_DEVICE_COLLABORATION_SERVICE

允许应用使用多屏服务的能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.GET_APP_DOMAIN_BUNDLE_INFO

允许应用访问应用和域名的映射关系。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.OPEN_FILE

允许系统应用拉起文件管理应用，并打开文件/文件夹。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.PROCESS_FILE_COPY_PASTE

允许系统应用拉起文件管理应用，并复制、剪切、粘贴文件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.CLEAR_RECYCLEBIN

允许系统应用拉起文件管理应用，并清空回收站。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.GET_FILE_THUMBNAIL

允许系统服务获取文件缩略图。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.NETWORK_DHCP

允许系统应用从DHCP申请IP地址以及分配IP地址。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ALLOW_CONNECT_CAR

允许应用连接车机。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_IDM_WIDGET

允许系统应用拉起用户凭据录入控件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.MANAGE_ACCESSORY

允许应用获取配件（键盘、鼠标等）信息、向配件发送数据及获取配件回复的数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.COLLECT_ACCESSORY_LOG

允许应用获取配件（键盘、鼠标等）日志。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.INSTALL_INTERNALTESTING_BUNDLE

允许应用安装开发者内测构建应用。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.PUBLISH_DISPLAY_ROTATION_EVENT

允许SA向应用或者系统服务发送屏幕旋转状态信息。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.PUBLISH_CAST_PLUGGED_EVENT

允许SA向应用或者系统服务发送投屏线缆插入拔出状态信息。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.GET_ETHERNET_LOCAL_MAC

允许应用查询以太网当前MAC地址。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS

允许模态UIExtension取消对不安全窗口的隐藏。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.ACCESS_DISTRIBUTED_MODEM

允许系统服务访问虚拟Modem。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.GET_TELEPHONY_ESIM_STATE

允许系统应用获取eSIM profile信息及设备芯片开卡相关属性。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：14

## ohos.permission.SET_TELEPHONY_ESIM_STATE

允许系统应用修改eSIM profile文件，及eSIM升级。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：14

## ohos.permission.CAMERA_BACKGROUND

允许系统应用在后台使用相机。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.CALLED_TRANSITION_ON_LOCK_SCREEN

允许应用被位于锁屏界面的其他应用拉起并直接跳转。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.CALLED_BELOW_LOCK_SCREEN

允许应用在处于锁屏状态时进行启动。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.ACCESS_ANALYTICS

允许系统服务访问并读取路径/data/log/faultlog/faultlogger下文件的内容。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.START_RESTORE_NOTIFICATION

允许系统应用订阅备份框架开始恢复的事件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.READ_WEATHER_DATA

允许应用读取天气数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：14

## ohos.permission.ACCESS_MCU_LOG_DIR

允许系统应用访问MCU（microcontroller unit）日志目录。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.GRANT_SHORT_TERM_WRITE_MEDIAVIDEO

允许系统应用或者系统服务为三方应用授予存图片和视频的短时访问权限。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.CHECK_QUICKFIX_RESULT

允许系统服务或应用检查补丁安装结果。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

**变更信息**：API 12-13，开放范围为系统服务；从API 14开始，开放范围变更为系统应用。

## ohos.permission.USER_AUTH_FROM_BACKGROUND

允许应用/服务在后台发起用户身份认证请求。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.MANAGE_RECOVERY_KEY

允许应用创建或删除恢复密钥。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：14

## ohos.permission.UTILIZE_RECOVERY_KEY

允许应用使用恢复密钥重设锁屏密码或恢复用户数据。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：14

## ohos.permission.ACCESS_CONFIDENTIAL_COMPUTING_ZONE

允许应用访问机密计算空间。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.SYNC_ASSET_BETWEEN_TRUSTED_ACCOUNT

允许应用在使用同一受信任账号登录的设备之间同步关键资产。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.GET_RECOVERY_KEY_BRIEF_INFORMATION

允许应用获取恢复密钥的简要信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：14

## ohos.permission.ACCESS_VIRTUAL_KEYBOARD

允许应用/服务更新/查询虚拟键盘状态。

通过该权限，应用可以更新虚拟键盘状态，服务可以查询虚拟键盘状态。当前仅2in1设备场景下可申请此权限。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：14

## ohos.permission.READ_APP_LOCK

允许系统应用读取应用锁状态。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.WRITE_APP_LOCK

允许系统应用修改应用锁状态。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.ACCESS_APP_LOCK

允许应用访问应用锁。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：13

## ohos.permission.ACCESS_APP_SINGLE_PERMISSION_MANAGEMENT

允许应用拉起用于修改其他应用授权的界面。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：15

## ohos.permission.ACCESS_APP_INSTALL_DIR

允许系统应用访问安装文件目录。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：14

## ohos.permission.ACCESS_ACCOUNT_SERVICE_EXTENSION_ABILITY

允许系统应用调用账号ServiceExtensionAbility所提供的服务。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：15

## ohos.permission.ANTI_FRAUD

允许应用接入风控探针以检测端侧风险，检测结果可作为云侧风险决策的输入。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.EXEMPT_CAPTURE_SCREEN_AUTHORIZE

允许应用发起录屏的时候，不弹出隐私授权弹窗。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：15

## ohos.permission.STORAGE_MANAGER_CRYPT

允许系统应用和系统服务调用接口完成加解密操作。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：12

## ohos.permission.WATCH_READ_EMERGENCY_INFO

允许应用读取SOS个人紧急信息数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.WATCH_WRITE_EMERGENCY_INFO

允许应用写入SOS个人紧急信息数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.WATCH_START_SOS_SERVICE

允许应用启用或访问SOS服务。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

**变更信息**：API 12-14，该权限仅向系统服务开放；从API 15开始，开放范围变更为系统应用。

## ohos.permission.ACCESS_DLP_HIDE_INFO

允许系统应用拉起防窥保护设置页。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.GET_ANIM_POLICY

允许系统应用注册动效插件，获取动效使用策略。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.VIRTUAL_KEYBOARD_WINDOW

允许系统应用创建虚拟键盘窗口。

系统应用获取此权限后，才可以成功创建虚拟键盘窗口。当前仅2in1设备系统应用可申请此权限。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：15

## ohos.permission.GET_FAMILY_INFO

允许系统应用获取“家人共享”中的群组信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACCESS_FUSION_AWARENESS_DATA

允许系统应用获取融合感知数据。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACCESS_ACCOUNT_RECOMMENDATION_DATA

允许应用读取“账号建议”的数据，以及拉起账号建议列表UIExtensionAbility。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.GET_PAGE_INFO

允许系统应用获取指定应用页面信息。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

允许扩展外设驱动访问SCSI DDK接口开发SCSI Peripheral扩展外设驱动。

支持以下类型的外设扩展驱动开发：
外设以USB总线接入主机，且满足：

1. 外设InterfaceClass为Mass Storage(0x08)、InterfaceSubClass为SCSI透明命令集(0x06)。
2. 外设能够以对操作系统透明的方式来模拟SCSI设备。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACCESS_DDK_USB_SERIAL

允许扩展外设驱动访问USBSerial DDK接口开发USB Serial扩展外设驱动。

支持以下类型的外设扩展驱动开发：
外设以USB总线接入主机，且满足：

1. 外设InterfaceClass为通信设备控制类 (0x02)、InterfaceSubClass遵循ACMSubClass模型(0x02)。
2. 外设支持通过USB接口模拟传统的串行通信。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACCESS_CUSTOM_RINGTONE

允许应用访问铃音库。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACCESS_STARTUPGUIDE

允许系统应用访问开机向导应用的普通数据、普通公共事件。

仅手机、平板、2in1设备应用可申请此权限。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACCESS_DEVAUTH_CRED_MGR

允许系统应用或系统服务访问设备互信认证SA的凭据管理模块。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACCESS_DEVAUTH_CRED_PRIVILEGE

允许系统应用或系统服务访问设备互信认证SA的凭据管理模块和凭据认证模块并查询和认证其他业务凭据。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACCESS_DEVAUTH_CRED_AUTH

允许系统应用或系统服务访问设备互信认证SA的凭据认证模块。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ANTIFRAUD_DETECT

允许系统应用进行反诈检测。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ANTIFRAUD_PICTURE_DETECT

允许系统应用进行图片换脸检测。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ANTIFRAUD_MODEL_DOWNLOAD

允许系统应用使用模型下载相关接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACCESS_APP_CLONE_DIR

允许系统应用访问从其他设备复制的安装文件路径。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ACCESS_MEDIALIB_RESTORE

允许应用挂载媒体恢复路径。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：17

## ohos.permission.ACCESS_TRUST_LIST_OOBE_MANAGER

允许应用管理在开机向导中可被拉起的应用名单。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.GET_NETWORK_STATS

允许系统应用获取历史流量。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：10

**变更信息**：API 10-11，ACL使能为false；从API 12开始，变更为true。

## ohos.permission.READ_DLP_HIDE_SWITCH

允许系统应用从窥屏提示数据库读取数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.WRITE_DLP_HIDE_SWITCH

允许系统应用向窥屏提示数据库写入数据。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.INSTALL_PLUGIN_BUNDLE

允许应用调用安装插件的接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：19

## ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

允许应用调用企业空间访问DLP文件的接口。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：PC/2in1

**起始版本**：20

## ohos.permission.UNINSTALL_PLUGIN_BUNDLE

允许应用调用卸载插件的接口。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：19

## ohos.permission.GET_EDM_CONFIG

允许系统应用查看行业定制配置文件。

用于保护行业定制配置文件的可见性，例如开机动画、开机logo、桌面布局、壁纸等。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.READ_DHA

允许应用读取设备健康证明信息。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.WRITE_DHA

允许应用写入设备健康证明信息。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.NOTIFY_DHA

允许应用通知设备健康证明事件。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.CHANGE_DEFAULT_APPLICATION

允许应用监听“默认应用”变化事件。

用户可以为系统设置“默认应用”，如设置默认使用某一应用打开指定类型文件。当“默认应用”变化时，将触发“默认应用”变化事件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：19

## ohos.permission.SEND_NOTIFICATION_CROSS_USER

允许应用发送通知给系统中指定用户。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.ALLOW_ACCESS_TIPS

允许系统应用拉起Tips提供的组件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：18

## ohos.permission.UPDATE_FONT

允许应用安装和卸载字体。

**权限级别**：system_basic

**授权方式**：system_grant

**ACL使能**：true

**起始版本**：19

## ohos.permission.READ_PARENT_CONTROL_DATA

允许应用读取家长管控网站的配置。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：Phone | Tablet | 2in1

**起始版本**：19

## ohos.permission.WRITE_PARENT_CONTROL_DATA

允许应用写入家长管控网站的配置。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：Phone | Tablet | 2in1

**起始版本**：19

## ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

允许应用通过无障碍服务接口查询和操作界面上的组件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**支持设备**：General

**ACL使能**：true

**起始版本**：20

## ohos.permission.READ_SOUND_RECORD_IN_FILE_MANAGER

允许应用从文件管理目录读取录音文件。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：Phone | PC/2in1 | Tablet

**起始版本**：20

## ohos.permission.WRITE_SOUND_RECORD_IN_FILE_MANAGER

允许应用向文件管理目录写入录音文件。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：Phone | PC/2in1 | Tablet

**起始版本**：20

## ohos.permission.SANDBOX_ACCESS_MANAGER

允许应用访问其它应用的沙箱目录。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**起始版本**：17

## ohos.permission.REQUEST_DISABLE_NOTIFICATION

允许应用运行的后台上传下载任务不在通知栏显示。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：General

**起始版本**：20

## ohos.permission.RESTORE_APP

允许系统应用拉起恢复弹窗以恢复应用。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：Phone | PC/2in1 | Tablet

**起始版本**：20

## ohos.permission.ALLOW_IOURING

允许系统应用调用io_uring相关系统调用实现异步IO操作。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：General

**起始版本**：20

## ohos.permission.NFC_NOTIFICATION

允许应用发布NFC通知相关的公共事件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：Phone

**起始版本**：20

## ohos.permission.kernel.ALLOW_APP_CODE_DECRYPT

允许系统应用或系统服务调用内核接口进行代码解密。

应用或服务拥有此权限后，可跨进程访问内核接口，针对已加密的代码内容请求解密，可避免非法访问，进一步保护应用代码资产。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：General

**起始版本**：20

## ohos.permission.VIRUS_PROTECTION_SERVICE

允许应用启动病毒查杀任务。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：PC/2in1

**起始版本**：20

## ohos.permission.UPLOAD_SAMPLE_FILE

允许应用上传样本文件到云侧。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：Phone | PC/2in1 | Tablet

**起始版本**：20

## ohos.permission.DOWNLOAD_POLICY_FILE

允许应用从云侧下载策略文件。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：Phone | PC/2in1 | Tablet

**起始版本**：20

## ohos.permission.NOTIFY_VIRUS_PROTECTION

允许应用发送通知给病毒防护。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：PC/2in1

**起始版本**：20

## ohos.permission.ACCESS_VIRUS_PROTECTION

允许应用跳转到病毒防护页面。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：PC/2in1

**起始版本**：20

## ohos.permission.ACCESS_TVCOOPERATION

允许系统应用接入协同服务。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：TV

**起始版本**：20

## ohos.permission.GRANT_URI_PERMISSION_AS_CALLER

允许应用以调用方的身份将URI访问权限授权给目标应用。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：General

**起始版本**：20

## ohos.permission.ACCESS_DFX_LOG_DIR

允许应用访问LOG群组的目录。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：General

**起始版本**：19

## ohos.permission.MANAGE_FILE_ENCRYPTION

允许系统应用修改系统文件的加密状态。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：PC/2in1

**起始版本**：20

## ohos.permission.FILE_TRANSFER_OPERATION

允许系统应用执行文件的传输、取消传输、删除、移除和修改等操作。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：PC/2in1

**起始版本**：20

## ohos.permission.FILE_TRANSFER_INFO_QUERY

允许系统应用查询文件和文件传输的信息。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：PC/2in1

**起始版本**：20

## ohos.permission.MANAGE_LOCAL_WORKSPACES

允许系统应用创建、删除工作空间。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：PC/2in1

**起始版本**：20

## ohos.permission.FILE_ACCESS_FOR_PRIVATE_SPACE

允许隐私空间挂载主空间公共目录到应用沙箱。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：Phone | Tablet

**起始版本**：20

## ohos.permission.MOUNT_HDCDEBUG_PATH

允许应用挂载hdc调试路径。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：PC/2in1

**起始版本**：20

## ohos.permission.ACCESS_CAMERA_SCENARIOS_CARD

允许应用访问遥控拍照场景卡片服务。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：Wearable

**起始版本**：20

## ohos.permission.TRIGGER_LOCAL_WANTAGENT

允许系统应用触发本地WantAgent实例。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：General

**起始版本**：20

## ohos.permission.ACCESS_DISTRIBUTED_KEY_STORE

允许应用使用分布式密钥能力。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：Phone | Tablet | PC/2in1 | Wearable | TV

**起始版本**：20

## ohos.permission.SANDBOX_ACCESS_MANAGER_EXT

允许应用访问其它扩展应用的沙箱目录。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：General

**起始版本**：19

## ohos.permission.kernel.LOAD_INDEPENDENT_LIBRARY

允许HAP加载具有不同ownerid的独立二进制SO。

该SO指具有开发者证书或AdHoc签名的独立二进制SO。

**权限级别**：system_basic

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：PC/2in1

**起始版本**：20

## ohos.permission.GET_DEVICE_INDEPENDENT_BINARY_CERT

允许系统应用查询独立二进制程序的证书信息。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：PC/2in1

**起始版本**：20

## ohos.permission.SET_DEVICE_INDEPENDENT_BINARY_CERT_STATUS

允许系统应用设置独立二进制程序的证书状态。

**权限级别**：system_core

**授权方式**：系统授权（system_grant）

**ACL使能**：true

**支持设备**：PC/2in1

**起始版本**：20
