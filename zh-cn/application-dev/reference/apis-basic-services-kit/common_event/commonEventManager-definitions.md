# 系统定义的公共事件

<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @peixu-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

本文档提供了系统定义的公共事件清单。
公共事件类型定义在[ohos.commonEventManager模块的Support枚举](../js-apis-commonEventManager.md#support)中。



## Ability Kit


### COMMON_EVENT_PACKAGE_RESTARTED

表示用户重启应用包并杀死其所有进程。

在设备上指定用户重启应用包并杀死其所有进程，将会触发事件通知服务发布该系统公共事件。

> **说明：** 
> 
> <!--Del-->系统应用可以监听自身应用和其他应用的重启事件。<!--DelEnd-->
> 
> 三方应用只能监听自身应用的重启事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGE_RESTARTED"



### COMMON_EVENT_PACKAGE_DATA_CLEARED

表示用户清除应用包数据。

在设备上指定用户清除应用包数据，将会触发事件通知服务发布该系统公共事件。

> **说明：** 
> 
> <!--Del-->系统应用可以监听自身应用和其他应用的数据清理事件。<!--DelEnd-->
> 
> 三方应用只能监听自身应用的数据清理事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGE_DATA_CLEARED"


### COMMON_EVENT_QUICK_FIX_APPLY_RESULT

表示快速修复应用。

在设备上指定用户快速修复应用，将会触发事件通知服务发布该系统公共事件。

> **说明：** 
> 
> <!--Del-->系统应用可以监听自身应用和其他应用的快速修复事件。<!--DelEnd-->
> 
> 三方应用只能监听自身应用的安快速修复事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.QUICK_FIX_APPLY_RESULT"



### COMMON_EVENT_QUICK_FIX_REVOKE_RESULT<sup>10+<sup>

表示撤销快速修复。

在设备上撤销快速修复时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.QUICK_FIX_REVOKE_RESULT"



### COMMON_EVENT_PACKAGE_ADDED

表示设备上已安装新应用包的公共事件的动作。

在设备上指定用户下安装了新的应用程序，将会触发事件通知服务发布该系统公共事件。

> **说明：** 
> 
> <!--Del-->系统应用可以监听自身应用和其他应用的安装事件。<!--DelEnd-->
> 
> 三方应用只能监听自身应用的安装事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGE_ADDED"


### COMMON_EVENT_PACKAGE_REMOVED

表示已从设备卸载已安装的应用程序，但应用程序数据保留的公共事件的操作。

在设备指定用户下卸载指定的应用程序包，将会触发事件通知服务发布该系统公共事件。

> **说明：** 
> 
> <!--Del-->系统应用可以监听自身应用和其他应用的卸载事件。<!--DelEnd-->
> 
> 三方应用只能监听自身应用的卸载事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGE_REMOVED"


### COMMON_EVENT_BUNDLE_REMOVED

表示现有的应用程序包从设备中移除的事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.BUNDLE_REMOVED"


### COMMON_EVENT_PACKAGE_FULLY_REMOVED

表示现有的应用程序包从设备上完全删除的事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGE_FULLY_REMOVED"


### COMMON_EVENT_PACKAGE_CHANGED

表示应用包已更改的公共事件的动作（例如，包中的组件已启用或禁用）。

在设备上安装的应用程序包更新或者包的组件被禁用使能，将会触发事件通知服务发布该系统公共事件。

> **说明：** 
> 
> <!--Del-->系统应用可以监听自身应用和其他应用的更改事件。<!--DelEnd-->
> 
> 三方应用只能监听自身应用的更改事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGE_CHANGED"


### COMMON_EVENT_PACKAGE_CACHE_CLEARED

表示用户清除应用包缓存数据的公共事件的动作。

对设备上安装的应用程序包清除缓存时，将会触发事件通知服务发布该系统公共事件。

> **说明：** 
> 
> <!--Del-->系统应用可以监听自身应用和其他应用的缓存清理事件。<!--DelEnd-->
> 
> 三方应用只能监听自身应用的缓存清理事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGE_CACHE_CLEARED"


### COMMON_EVENT_PACKAGES_SUSPENDED

表示包已经被挂起。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGES_SUSPENDED"



### COMMON_EVENT_MY_PACKAGE_SUSPENDED

发送到已被系统挂起的包。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.MY_PACKAGE_SUSPENDED"


### COMMON_EVENT_MY_PACKAGE_UNSUSPENDED

发送到已被系统解除挂起的包。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.MY_PACKAGE_UNSUSPENDED"





### COMMON_EVENT_MANAGE_PACKAGE_STORAGE

通知用户低内存状态并且应该启动包管理。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.MANAGE_PACKAGE_STORAGE"



## Account Kit

### COMMON_EVENT_MINORSMODE_ON<sup>12+<sup>

表示用户开启未成年人模式。

在设备上开启未成年人模式，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**取值：** "usual.event.MINORSMODE_ON"



### COMMON_EVENT_MINORSMODE_OFF<sup>12+<sup>

表示用户关闭未成年人模式。

在设备上关闭未成年人模式，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**取值：** "usual.event.MINORSMODE_OFF"


## ArkData


### COMMON_EVENT_DATA_SHARE_READY<sup>12+</sup>

表示datashare服务可用。

datashare服务启动完成后，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.DATA_SHARE_READY"


## ArkUI

### COMMON_EVENT_SPLIT_SCREEN

表示分屏行为的公共事件。

启动最近任务窗口、创建或销毁分屏条，都会触发通知服务发布这个系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**取值：** "common.event.SPLIT_SCREEN"



## Notification Kit

### COMMON_EVENT_SLOT_CHANGE

  表示通知渠道或通知开关发生变化。

  通知设置里修改应用的渠道参数、渠道开关，或者开启、关闭通知使能开关时，都会触发通知服务发布这个系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.NOTIFICATION_CONTROLLER

**取值：** "usual.event.SLOT_CHANGE"


## Background Tasks Kit


### COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED
表示设备上待机状态变化，触发公共事件发布动作。

如果用户一段时间没有使用设备且屏幕已经关闭情况下，系统延迟后台应用程序CPU和网络访问，将会触发公共事件服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.DEVICE_IDLE_MODE_CHANGED"


## Basic Services Kit

### COMMON_EVENT_USB_STATE

表示USB设备状态发生变化。

当USB断开或者连接时状态发生变化，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.hardware.usb.action.USB_STATE"


### COMMON_EVENT_USB_PORT_CHANGED

提示用户设备的USB端口状态发生改变。

当USB的端口状态发生变化，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.hardware.usb.action.USB_PORT_CHANGED"


### COMMON_EVENT_USB_DEVICE_ATTACHED

当用户设备作为USB主机时，提示USB设备已挂载。

当USB连接时状态发生变化，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.hardware.usb.action.USB_DEVICE_ATTACHED"


### COMMON_EVENT_USB_DEVICE_DETACHED

当用户设备作为USB主机时，提示USB设备被卸载。

当USB断开时状态发生变化，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.hardware.usb.action.USB_DEVICE_DETACHED"


### COMMON_EVENT_TIME_CHANGED

设置系统时间的公共事件的动作。

当设置系统时间时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.TIME_CHANGED"


### COMMON_EVENT_TIME_TICK

表示系统时间更改的公共事件的动作。

当以整分钟为单位的系统时间更改时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.TIME_TICK"


### COMMON_EVENT_TIMEZONE_CHANGED

表示系统时区更改的公共事件的动作。

当系统时区更改时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.TIMEZONE_CHANGED"





### COMMON_EVENT_USER_INFO_UPDATED

表示用户信息已更新。

分布式账号信息变更、系统账号头像信息变更、系统账号名称变更将会触发事件通知服务发布该系统公共事件，事件携带系统账号ID。

与这个公共事件相关的接口：setOsAccountName、setOsAccountProfilePhoto, 这些为系统API，setOsAccountDistributedInfon为公共API，具体参看[系统账号接口文档](../js-apis-osAccount.md)、[分布式账号接口文档](../js-apis-distributed-account.md)。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.USER_INFO_UPDATED"


### COMMON_EVENT_USER_UNLOCKED

表示设备重启后解锁时，当前用户的凭据加密存储已解锁的公共事件的动作。

切换到带有锁屏密码的用户，并且首次解锁会发出触发事件通知服务发布该系统公共事件，事件携带标识该用户的系统账号ID。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.USER_UNLOCKED"


### COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN

表示分布式账号登录成功的动作。

分布式账号登录成功时会触发事件通知服务发布该系统公共事件，事件携带系统账号ID。

与这个公共事件相关的接口：setOsAccountDistributedInfo、updateOsAccountDistributedInfo(已废弃)，这些为公共API，setOsAccountDistributedInfoByLocalId为系统API，具体参看[分布式账号接口文档](../js-apis-distributed-account.md)。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**取值：** "common.event.DISTRIBUTED_ACCOUNT_LOGIN"


### COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT

表示分布式账号登出成功的动作。

分布式账号登出时会触发事件通知服务发布该系统公共事件，事件携带系统账号ID。

与这个公共事件相关的接口：setOsAccountDistributedInfo、updateOsAccountDistributedInfo(已废弃)，这些为公共API，setOsAccountDistributedInfoByLocalId为系统API，具体参看[分布式账号接口文档](../js-apis-distributed-account.md)。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**取值：** "common.event.DISTRIBUTED_ACCOUNT_LOGOUT"


### COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID

表示分布式账号token令牌无效的动作。

分布式账号的token令牌无效时会触发事件通知服务发布该系统公共事件，事件携带系统账号ID。

与这个公共事件相关的接口：setOsAccountDistributedInfo、updateOsAccountDistributedInfo(已废弃)，这些为公共API，setOsAccountDistributedInfoByLocalId为系统API，具体参看[分布式账号接口文档](../js-apis-distributed-account.md)。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**取值：** "common.event.DISTRIBUTED_ACCOUNT_TOKEN_INVALID"



### COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF

表示分布式账号注销的动作。

分布式账号注销成功会时触发事件通知服务发布该系统公共事件，事件携带系统账号ID。

与这个公共事件相关的接口：setOsAccountDistributedInfo、updateOsAccountDistributedInfo(已废弃)，这些为公共API，setOsAccountDistributedInfoByLocalId为系统API，具体参看[分布式账号接口文档](../js-apis-distributed-account.md)。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**取值：** "common.event.DISTRIBUTED_ACCOUNT_LOGOFF"



### COMMON_EVENT_SCREEN_LOCKED

表示屏幕锁定的公共事件。
当锁屏锁定时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**取值：** usual.event.SCREEN_LOCKED



### COMMON_EVENT_SCREEN_UNLOCKED

表示屏幕解锁的公共事件。
当锁屏解锁时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**取值：** usual.event.SCREEN_UNLOCKED


### COMMON_EVENT_USER_PRESENT<sup>(deprecated)</sup>
用户解锁设备的公共事件的动作。

  > 说明：
  >
  > 从API Version 10开始废弃，替代接口为[COMMON_EVENT_SCREEN_UNLOCKED](#common_event_screen_unlocked)。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** usual.event.USER_PRESENT


### COMMON_EVENT_BATTERY_CHANGED

表示电池充电状态、电平和其他信息发生变化的公共事件的动作。

当电池电量、电池电压、电池温度、电池健康状态、设备连接的充电器类型、充电器最大电流、充电器最大电压、电池充电状态、充电次数、电池的总容量、电池剩余容量、电池的技术型号、当前电池的电流、电池的充电类型变化时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.BATTERY_CHANGED"


### COMMON_EVENT_BATTERY_LOW

表示电池电量低的普通事件的动作。

当电池电量低于设备设置的低电量百分比值时，将会触发事件通知服务发布该系统公共事件。<!--Del-->设备设置低电量百分比值请参考[电量等级定制开发指导](../../../../device-dev/subsystems/subsys-power-battery-level-customization.md)。<!--DelEnd-->

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.BATTERY_LOW"


### COMMON_EVENT_BATTERY_OKAY

表示电池退出低电量状态的公共事件的动作。

当电池电量从低电量等级变化到电池电量高于低电量等级时，将会触发事件通知服务发布该系统公共事件。


**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.BATTERY_OKAY"


### COMMON_EVENT_POWER_CONNECTED

设备连接到外部电源的公共事件的动作。

当设备连接到外部可识别的充电器类型充电时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.POWER_CONNECTED"


### COMMON_EVENT_POWER_DISCONNECTED

设备与外部电源断开的公共事件的动作。

当设备与外部电源断开时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.POWER_DISCONNECTED"


### COMMON_EVENT_DISCHARGING

表示系统停止为电池充电的公共事件的动作。

当系统停止为电池充电时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.DISCHARGING"


### COMMON_EVENT_CHARGING

表示系统开始为电池充电的公共事件的动作。

当系统开始为电池充电时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.CHARGING"



### COMMON_EVENT_CHARGE_IDLE_MODE_CHANGED<sup>10+<sup>

表示设备进入充电空闲模式的公共事件的动作。

当设备处于空闲、正在充电并且温升可接受的一种状态时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.CHARGE_IDLE_MODE_CHANGED"


### COMMON_EVENT_SHUTDOWN

表示设备正在关闭并将继续最终关闭的公共事件的操作。

当设备正在关闭并将继续最终关闭时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.SHUTDOWN"


### COMMON_EVENT_SCREEN_OFF

表示由电源服务发起的设备灭屏完成的普通事件的动作。

当由电源服务发起的设备灭屏完成时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.SCREEN_OFF"


### COMMON_EVENT_SCREEN_ON

表示由电源服务发起的设备亮屏完成的普通事件的动作。

当由电源服务发起的设备亮屏完成时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.SCREEN_ON"


### COMMON_EVENT_POWER_SAVE_MODE_CHANGED

表示系统节能模式更改的公共事件的动作。

当系统节能模式更改时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.POWER_SAVE_MODE_CHANGED"


### COMMON_EVENT_THERMAL_LEVEL_CHANGED

表示设备热状态的公共事件的动作。

当设备热等级变化时，将会触发事件通知服务发布该系统公共事件。<!--Del-->设备热等级配置请参考[热等级定制开发指导](../../../../device-dev/subsystems/subsys-thermal_level.md)。<!--DelEnd-->

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.THERMAL_LEVEL_CHANGED"


### COMMON_EVENT_ENTER_FORCE_SLEEP<sup>12+<sup>

表示设备即将进入强制睡眠模式的公共事件的动作。

当设备即将进入强制睡眠模式时，将会触发事件通知服务发布该系统公共事件。所有订阅者必须在1秒钟内处理该事件。


**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.ENTER_FORCE_SLEEP"

### COMMON_EVENT_EXIT_FORCE_SLEEP<sup>12+<sup>

表示设备退出强制睡眠模式的公共事件的动作。

当设备退出强制睡眠模式时，将会触发事件通知服务发布该系统公共事件。


**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.EXIT_FORCE_SLEEP"

### COMMON_EVENT_ENTER_HIBERNATE<sup>15+<sup>

表示设备即将进入休眠模式的公共事件的动作。

当设备即将进入休眠模式时，将会触发事件通知服务发布该系统公共事件。所有订阅者必须在1秒钟内处理该事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.ENTER_HIBERNATE"

### COMMON_EVENT_EXIT_HIBERNATE<sup>15+<sup>

表示设备退出休眠模式的公共事件的动作。

当设备退出休眠模式时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.EXIT_HIBERNATE"






## Connectivity Kit


### COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED

指示设备NFC状态已更改的公共事件的操作。

指示设备NFC状态更改时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.nfc.action.ADAPTER_STATE_CHANGED"


### COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED

检测到NFC场强进入的公共事件。

当检测到NFC场强进入时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.nfc.action.RF_FIELD_ON_DETECTED"


### COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED

检测到NFC场强离开的公共事件。

当检测到NFC场强离开时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.nfc.action.RF_FIELD_OFF_DETECTED"


### COMMON_EVENT_WIFI_POWER_STATE

Wi-Fi状态变化。

当Wi-Fi状态发生变化时（如启用、禁用Wi-Fi），将会触发事件通知服务发布该系统公共事件。

状态值：0：WLAN正在关闭，1：WLAN已关闭，2：WLAN正在打开，3：WLAN已启动。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.wifi.POWER_STATE"


### COMMON_EVENT_WIFI_SCAN_FINISHED

表示Wi-Fi接入点已被扫描并证明可用的动作。

当Wi-Fi接入点已被扫描并证明可用，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.LOCATION

**取值：** "usual.event.wifi.SCAN_FINISHED"


### COMMON_EVENT_WIFI_SCAN_STATE

表示Wi-Fi扫描接入点状态改变。

当Wi-Fi扫描接入点状态发生变化，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.LOCATION

**取值：** "usual.event.wifi.SCAN_STATE"



### COMMON_EVENT_WIFI_RSSI_VALUE

  表示Wi-Fi信号强度（RSSI）改变。

  当Wi-Fi信号强度（RSSI）发生变化，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.GET_WIFI_INFO

**取值：** "usual.event.wifi.RSSI_VALUE"



### COMMON_EVENT_WIFI_CONN_STATE

  Wi-Fi连接状态发生改变。

  当Wi-Fi连接状态发生变化，将会触发事件通知服务发布该系统公共事件。


**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.wifi.CONN_STATE"


### COMMON_EVENT_WIFI_HOTSPOT_STATE

表示Wi-Fi热点状态变化。

当Wi-Fi热点状态发生变化，将会触发事件通知服务发布该系统公共事件。

状态值：2：AP正在打开，3：AP已启动，4：AP正在关闭，5：AP已关闭。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.wifi.HOTSPOT_STATE"


### COMMON_EVENT_WIFI_AP_STA_JOIN

表示客户端加入当前设备Wi-Fi热点。

当客户端加入当前设备Wi-Fi热点，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.GET_WIFI_INFO

**取值：** "usual.event.wifi.WIFI_HS_STA_JOIN"


### COMMON_EVENT_WIFI_AP_STA_LEAVE

表示客户端已断开与当前设备Wi-Fi热点的连接。

当客户端已断开与当前设备Wi-Fi热点的连接，将会触发事件通知服务发布该系统公共事件。


**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.GET_WIFI_INFO

**取值：** "usual.event.wifi.WIFI_HS_STA_LEAVE"


### COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE

表示MPLink（增强Wi-Fi功能）状态已更改。

当MPLink（增强Wi-Fi功能）状态发生变化，将会触发事件通知服务发布该系统公共事件（暂不支持）。


**系统能力：** SystemCapability.Notification.CommonEvent

**订阅方需要的权限：** 无

**取值：** "usual.event.wifi.mplink.STATE_CHANGE"


### COMMON_EVENT_WIFI_P2P_CONN_STATE

表示Wi-Fi P2P连接状态改变。

当Wi-Fi P2P连接状态发生变化，将会触发事件通知服务发布该系统公共事件。


**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.GET_WIFI_INFO和ohos.permission.LOCATION

**取值：** "usual.event.wifi.p2p.CONN_STATE_CHANGE"


### COMMON_EVENT_WIFI_P2P_STATE_CHANGED

表示Wi-Fi P2P状态变化。

当Wi-Fi P2P状态发生变化，将会触发事件通知服务发布该系统公共事件。

状态值：2：P2P正在打开，3：P2P已启动，4：P2P正在关闭，5：P2P已关闭。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.GET_WIFI_INFO

**取值：** "usual.event.wifi.p2p.STATE_CHANGE"


### COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED

表示Wi-Fi P2P对等体状态变化。

当Wi-Fi P2P对等体状态变化，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.GET_WIFI_INFO

**取值：** "usual.event.wifi.p2p.DEVICES_CHANGE"


### COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED

表示Wi-Fi P2P发现状态变化。

当Wi-Fi P2P发现状态变化，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.GET_WIFI_INFO

**取值：** "usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE"


### COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED

表示Wi-Fi P2P当前设备状态变化。

当Wi-Fi P2P当前设备状态变化，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.GET_WIFI_INFO

**取值：** "usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE"


### COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED

表示Wi-Fi P2P群组信息已更改。

当Wi-Fi P2P群组信息发生变化，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.GET_WIFI_INFO

**取值：** "usual.event.wifi.p2p.GROUP_STATE_CHANGED"


## MDM Kit

### COMMON_EVENT_MANAGED_BROWSER_POLICY_CHANGED

表示浏览器托管策略已更改。

当浏览器托管策略发生变化，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.MANAGED_BROWSER_POLICY_CHANGED"


## Localization Kit

### COMMON_EVENT_LOCALE_CHANGED

设置系统语言的公共事件的动作。
当设置系统语言时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** usual.event.LOCALE_CHANGED


## Network Kit

### COMMON_EVENT_CONNECTIVITY_CHANGE<sup>10+<sup>

指示网络连接状态变化。

各类网络（以太网、Wi-Fi、蜂窝等）在发生连接状态状态变化时（断开、断开中、连接中、已连接等），将会触发事件通知服务发布该系统公共事件。
具体枚举值及其对应的连接状态如下表所示：

| 枚举值  |  连接状态  |
| ------ | ---------- |
|    2   |   连接中   |
|    3   |   已连接   |
|    4   |   正在断开 |
|    5   |   已断开   |

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**取值：** usual.event.CONNECTIVITY_CHANGE


### COMMON_EVENT_AIRPLANE_MODE_CHANGED<sup>10+<sup>

指示飞行模式状态变化。

在开启或者关闭系统飞行模式状态后，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** usual.event.AIRPLANE_MODE


### COMMON_EVENT_HTTP_PROXY_CHANGE<sup>10+<sup>

指示网络Http代理配置信息更新。

在系统全局代理或者各类网络（以太网、Wi-Fi、蜂窝等）Http代理配置信息发生变化时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** usual.event.HTTP_PROXY_CHANGE



## Telephony Kit

电话服务子系统面向应用发布如下系统公共事件。

### COMMON_EVENT_SIM_STATE_CHANGED<sup>10+<sup>

提示SIM卡状态更新。

在设备上面的SIM卡状态发生变化时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** usual.event.SIM_STATE_CHANGED



### COMMON_EVENT_CALL_STATE_CHANGED<sup>10+<sup>

提示呼叫状态更新。

在设备呼叫状态更新时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.GET_TELEPHONY_STATE（该权限仅系统应用可申请）

**取值：** usual.event.CALL_STATE_CHANGED



### COMMON_EVENT_NETWORK_STATE_CHANGED<sup>10+<sup>

提示网络状态更新。

在设备网络状态更新时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** usual.event.NETWORK_STATE_CHANGED


### COMMON_EVENT_SIGNAL_INFO_CHANGED<sup>10+<sup>

提示信号信息更新。

在设备信号信息更新时，将会触发事件通知服务发布该系统公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** usual.event.SIGNAL_INFO_CHANGED



## Store Kit
Store Kit面向应用发布如下系统公共事件。

### COMMON_EVENT_PRIVACY_STATE_CHANGED<sup>11+<sup>
表示隐私签署结果的公共事件。
隐私弹框场景下，用户点击同意，会发送此事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PRIVACY_STATE_CHANGED"



## 预留公共事件

以下事件为预留公共事件，暂未支持。


### COMMON_EVENT_PACKAGE_FIRST_LAUNCH

（预留事件，暂未支持）应用程序在安装后首次启动。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGE_FIRST_LAUNCH"


### COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION

（预留事件，暂未支持）当一个包需要被验证时，由系统包验证者发送。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGE_NEEDS_VERIFICATION"


### COMMON_EVENT_PACKAGE_VERIFIED

（预留事件，暂未支持）当一个包被验证时，由系统包验证者发送。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGE_VERIFIED"

### COMMON_EVENT_PACKAGE_REPLACED

（预留事件，暂未支持）表示设备上安装了新版本的应用程序包并替换了旧版本的动作。数据包含包的名称。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGE_REPLACED"


### COMMON_EVENT_MY_PACKAGE_REPLACED

（预留事件，暂未支持）表示设备上安装了新版本的应用程序包并替换了旧版本的应用程序包的动作，不包含额外的数据，只发送给被替换的应用程序。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.MY_PACKAGE_REPLACED"


### COMMON_EVENT_PACKAGES_UNSUSPENDED

（预留事件，暂未支持）表示包已经被解除挂起。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.PACKAGES_UNSUSPENDED"


### COMMON_EVENT_CLOSE_SYSTEM_DIALOGS

（预留事件，暂未支持）表示用户关闭临时系统对话框的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.CLOSE_SYSTEM_DIALOGS"



### COMMON_EVENT_UID_REMOVED

（预留事件，暂未支持）表示用户ID已从系统中删除的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.UID_REMOVED"


### COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE

（预留事件，暂未支持）表示安装在外部存储上的应用程序对系统可用的公共事件的操作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.EXTERNAL_APPLICATIONS_AVAILABLE"


### COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE

（预留事件，暂未支持）表示安装在外部存储上的应用程序对系统不可用的公共事件的操作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE"


### COMMON_EVENT_CONFIGURATION_CHANGED

（预留事件，暂未支持）表示设备状态（例如，方向和区域设置）已更改的公共事件的操作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.CONFIGURATION_CHANGED"



### COMMON_EVENT_DRIVE_MODE
（预留事件，暂未支持）表示系统处于驾驶模式的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.DRIVE_MODE"



### COMMON_EVENT_HOME_MODE
（预留事件，暂未支持）表示系统处于HOME模式的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.HOME_MODE"



### COMMON_EVENT_OFFICE_MODE
（预留事件，暂未支持）表示系统处于办公模式的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.OFFICE_MODE"



### COMMON_EVENT_USER_STARTED

（预留事件，暂未支持）表示用户已启动的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.USER_STARTED"


### COMMON_EVENT_USER_BACKGROUND

（预留事件，暂未支持）表示用户已被带到后台的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.USER_BACKGROUND"


### COMMON_EVENT_USER_STARTING
（预留事件，暂未支持）表示要启动用户的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS（该权限仅系统应用可申请）

**取值：** "usual.event.USER_STARTING"



### COMMON_EVENT_USER_STOPPING
（预留事件，暂未支持）表示要停止用户的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS（该权限仅系统应用可申请）

**取值：** "usual.event.USER_STOPPING"


### COMMON_EVENT_USER_STOPPED
（预留事件，暂未支持）表示用户已停止的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.USER_STOPPED"


### COMMON_EVENT_DISK_REMOVED

（预留事件，暂未支持）外部存储设备状态变更为移除时发送此公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.STORAGE_MANAGER（该权限仅系统应用可申请）

**取值：** "usual.event.data.DISK_BAD_REMOVAL"


### COMMON_EVENT_DISK_UNMOUNTED

（预留事件，暂未支持）部存储设备状态变更为卸载时发送此公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.STORAGE_MANAGER（该权限仅系统应用可申请）

**取值：** "usual.event.data.DISK_UNMOUNTABLE"


### COMMON_EVENT_DISK_MOUNTED

（预留事件，暂未支持）外部存储设备状态变更为挂载时发送此公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.STORAGE_MANAGER（该权限仅系统应用可申请）

**取值：** "usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED"



### COMMON_EVENT_DISK_BAD_REMOVAL

（预留事件，暂未支持）外部存储设备状态变更为挂载状态下移除时发送此公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.STORAGE_MANAGER（该权限仅系统应用可申请）

**取值：** "usual.event.data.DISK_REMOVED"


### COMMON_EVENT_DISK_UNMOUNTABLE

（预留事件，暂未支持）外部存储设备状态变更为插卡情况下无法挂载时发送此公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.STORAGE_MANAGER（该权限仅系统应用可申请）

**取值：** "usual.event.data.DISK_UNMOUNTED"


### COMMON_EVENT_DISK_EJECT

（预留事件，暂未支持）用户已表示希望删除外部存储介质时发送此公共事件。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.STORAGE_MANAGER（该权限仅系统应用可申请）

**取值：** "usual.event.data.DISK_EJECT"


### COMMON_EVENT_DATE_CHANGED

（预留事件，暂未支持）表示系统日期已更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** usual.event.DATE_CHANGED

### COMMON_EVENT_USB_ACCESSORY_ATTACHED

（预留事件，暂未支持）表示已连接USB附件的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED"


### COMMON_EVENT_USB_ACCESSORY_DETACHED

（预留事件，暂未支持）表示USB附件被卸载的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.data.DISK_MOUNTED"

### COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE
（预留事件，暂未支持）蓝牙免提通信连接状态公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE"



### COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE
（预留事件，暂未支持）表示连接到蓝牙免提的设备处于活动状态的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE"


### COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE
（预留事件，暂未支持）表示蓝牙A2DP连接状态已更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE"




### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE
（预留事件，暂未支持）蓝牙A2DP连接状态公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE"




### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE
（预留事件，暂未支持）表示使用蓝牙A2DP连接的设备处于活动状态的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE"



### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE
（预留事件，暂未支持）表示蓝牙A2DP的AVRCP连接状态已更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE"



### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE
（预留事件，暂未支持）蓝牙A2DP播放状态改变的普通事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE"



### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE
（预留事件，暂未支持）表示蓝牙A2DP音频编解码状态更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE"




### COMMON_EVENT_USER_FOREGROUND

（预留事件，暂未支持）表示用户已被带到前台的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.USER_FOREGROUND“




### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED
（预留事件，暂未支持）表示发现远程蓝牙设备的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.LOCATION和ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.remotedevice.DISCOVERED"




### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE
（预留事件，暂未支持）表示远程蓝牙设备的蓝牙类别已更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED
（预留事件，暂未支持）表示已与远程蓝牙设备建立低级别（ACL）连接的公共事件的动作。


**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.bluetooth.remotedevice.ACL_CONNECTED"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED
（预留事件，暂未支持）表示低电平（ACL）连接已从远程蓝牙设备断开的普通事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.remotedevice.ACL_DISCONNECTED"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE

（预留事件，暂未支持）表示远程蓝牙设备的友好名称首次被检索或自上次检索以来被更改的公共事件的操作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.ACCESS_BLUETOOTH

**取值：** "usual.event.bluetooth.remotedevice.NAME_UPDATE"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE
（预留事件，暂未支持）远程蓝牙设备连接状态更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.remotedevice.PAIR_STATE"



### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE
（预留事件，暂未支持）表示远程蓝牙设备的电池电量首次被检索或自上次检索以来被更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT
（预留事件，暂未支持）远程蓝牙设备SDP状态公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.bluetooth.remotedevice.SDP_RESULT"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE
远程蓝牙设备UUID连接状态公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.ACCESS_BLUETOOTH

**取值：** "usual.event.bluetooth.remotedevice.UUID_VALUE"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ
（预留事件，暂未支持）表示远程蓝牙设备配对请求的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.DISCOVER_BLUETOOTH

**取值：** "usual.event.bluetooth.remotedevice.PAIRING_REQ"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL
（预留事件，暂未支持）取消蓝牙配对的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.bluetooth.remotedevice.PAIRING_CANCEL"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ
（预留事件，暂未支持）表示远程蓝牙设备连接请求的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.bluetooth.remotedevice.CONNECT_REQ"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY
（预留事件，暂未支持）表示远程蓝牙设备连接请求响应的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.bluetooth.remotedevice.CONNECT_REPLY"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL
（预留事件，暂未支持）表示取消与远程蓝牙设备的连接的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.bluetooth.remotedevice.CONNECT_CANCEL"


### COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE
（预留事件，暂未支持）表示蓝牙免提连接状态已更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE"


### COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE
（预留事件，暂未支持）表示蓝牙免提音频状态已更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE"


### COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT
（预留事件，暂未支持）表示蓝牙免提音频网关状态已更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT"


### COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE
（预留事件，暂未支持）表示蓝牙免提呼叫状态已更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE"


### COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE
表示蓝牙适配器状态已更改的公共事件的操作，例如蓝牙已打开或关闭。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.bluetooth.host.STATE_UPDATE"


### COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE
（预留事件，暂未支持）表示用户允许扫描蓝牙请求的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.bluetooth.host.REQ_DISCOVERABLE"


### COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE
（预留事件，暂未支持）表示用户打开蓝牙请求的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.host.REQ_ENABLE"



### COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE
（预留事件，暂未支持）表示用户关闭蓝牙请求的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.host.REQ_DISABLE"


### COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE
（预留事件，暂未支持）设备蓝牙扫描模式更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.host.SCAN_MODE_UPDATE"




### COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED
设备上已启动蓝牙扫描的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.ACCESS_BLUETOOTH

**取值：** "usual.event.bluetooth.host.DISCOVERY_STARTED"


### COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED
设备上蓝牙扫描完成的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.ACCESS_BLUETOOTH

**取值：** "usual.event.bluetooth.host.DISCOVERY_FINISHED"


### COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE
指示设备蓝牙适配器名称已更改的公共事件的操作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.ACCESS_BLUETOOTH

**取值：** "usual.event.bluetooth.host.NAME_UPDATE"


### COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE
（预留事件，暂未支持）表示蓝牙A2DP宿连接状态已更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE"



### COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE
（预留事件，暂未支持）蓝牙A2DP宿播放状态改变的普通事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE"


### COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE
（预留事件，暂未支持）表示蓝牙A2DP宿的音频状态已更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.USE_BLUETOOTH

**取值：** "usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE"


### COMMON_EVENT_ABILITY_ADDED
（预留事件，暂未支持）表示已添加能力的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**取值：** "usual.event.ABILITY_ADDED"


### COMMON_EVENT_ABILITY_REMOVED
（预留事件，暂未支持）表示已删除能力的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**取值：** "usual.event.ABILITY_REMOVED"



### COMMON_EVENT_ABILITY_UPDATED
（预留事件，暂未支持）表示能力已更新的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**取值：** "usual.event.ABILITY_UPDATED"


### COMMON_EVENT_LOCATION_MODE_STATE_CHANGED
（预留事件，暂未支持）表示系统定位模式已更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.location.MODE_STATE_CHANGED"


### COMMON_EVENT_IVI_SLEEP
（预留事件，暂未支持）表示表示车辆的车载信息娱乐（IVI）系统正在休眠的常见事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.IVI_SLEEP"


### COMMON_EVENT_IVI_PAUSE
（预留事件，暂未支持）表示IVI已休眠，并通知应用程序停止播放。


**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.IVI_PAUSE"



### COMMON_EVENT_IVI_STANDBY
（预留事件，暂未支持）表示第三方应用暂停当前工作的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.IVI_STANDBY"


### COMMON_EVENT_IVI_LASTMODE_SAVE
（预留事件，暂未支持）表示第三方应用保存其最后一个模式的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.IVI_LASTMODE_SAVE"


### COMMON_EVENT_IVI_VOLTAGE_ABNORMAL
（预留事件，暂未支持）表示车辆电源系统电压异常的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.IVI_VOLTAGE_ABNORMAL"


### COMMON_EVENT_IVI_HIGH_TEMPERATURE

（预留事件，暂未支持）表示IVI温度过高。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.IVI_HIGH_TEMPERATURE"


### COMMON_EVENT_IVI_EXTREME_TEMPERATURE
（预留事件，暂未支持）表示IVI温度极高。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.IVI_EXTREME_TEMPERATURE"



### COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL
（预留事件，暂未支持）表示车载系统具有极端温度的常见事件的动作。


**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.IVI_TEMPERATURE_ABNORMAL"


### COMMON_EVENT_IVI_VOLTAGE_RECOVERY
（预留事件，暂未支持）表示车辆电源系统电压恢复正常的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.IVI_VOLTAGE_RECOVERY"


### COMMON_EVENT_IVI_TEMPERATURE_RECOVERY
（预留事件，暂未支持）表示车载系统温度恢复正常的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.IVI_TEMPERATURE_RECOVERY"


### COMMON_EVENT_IVI_ACTIVE
（预留事件，暂未支持）表示电池服务处于活动状态的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "common.event.IVI_ACTIVE"



### COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED
（预留事件，暂未支持）表示账户可见更改的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.GET_APP_ACCOUNTS（该权限仅系统应用可申请）

**取值：** "usual.event.data.VISIBLE_ACCOUNTS_UPDATED"


### COMMON_EVENT_ACCOUNT_DELETED
（预留事件，暂未支持）删除账户的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS（该权限仅系统应用可申请）

**取值：** "usual.event.data.ACCOUNT_DELETED"



### COMMON_EVENT_FOUNDATION_READY
（预留事件，暂未支持）表示foundation已准备好的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** ohos.permission.RECEIVER_STARTUP_COMPLETED（该权限仅系统应用可申请）

**取值：** "usual.event.data.FOUNDATION_READY"



### COMMON_EVENT_SPN_INFO_CHANGED 
表示spn显示信息已更新的公共事件的动作。

**系统能力：** SystemCapability.Notification.CommonEvent

**订阅者所需权限：** 无

**取值：** "usual.event.SPN_INFO_CHANGED"
<!--no_check-->
