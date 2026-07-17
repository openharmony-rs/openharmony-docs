# Support

系统公共事件是指由系统服务或系统应用发布的事件，订阅这些公共事件需要特定的权限、使用相应的值。

**起始版本：** 9

<!--Device-commonEventManager-export enum Support--><!--Device-commonEventManager-export enum Support-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BOOT_COMPLETED

```TypeScript
COMMON_EVENT_BOOT_COMPLETED = 'usual.event.BOOT_COMPLETED'
```

表示用户已完成引导并加载系统。

在设备上指定用户已完成引导并加载系统，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.RECEIVER_STARTUP_COMPLETED权限（该权限仅系统应用可申请）

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_BOOT_COMPLETED = 'usual.event.BOOT_COMPLETED'--><!--Device-Support-COMMON_EVENT_BOOT_COMPLETED = 'usual.event.BOOT_COMPLETED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LOCKED_BOOT_COMPLETED

```TypeScript
COMMON_EVENT_LOCKED_BOOT_COMPLETED = 'usual.event.LOCKED_BOOT_COMPLETED'
```

（预留事件，暂未支持）提示用户已完成引导，系统已加载，但屏幕仍锁定。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_LOCKED_BOOT_COMPLETED = 'usual.event.LOCKED_BOOT_COMPLETED'--><!--Device-Support-COMMON_EVENT_LOCKED_BOOT_COMPLETED = 'usual.event.LOCKED_BOOT_COMPLETED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SHUTDOWN

```TypeScript
COMMON_EVENT_SHUTDOWN = 'usual.event.SHUTDOWN'
```

表示设备正在关闭并将继续最终关闭的公共事件的操作。

当设备正在关闭并将继续最终关闭时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_SHUTDOWN = 'usual.event.SHUTDOWN'--><!--Device-Support-COMMON_EVENT_SHUTDOWN = 'usual.event.SHUTDOWN'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BATTERY_CHANGED

```TypeScript
COMMON_EVENT_BATTERY_CHANGED = 'usual.event.BATTERY_CHANGED'
```

表示电池充电状态、电平和其他信息发生变化的公共事件的动作。

当电池电量、电池温度、电池健康状态、设备连接的充电器类型、充电器最大电流、充电器最大电压、电池充电状态、充电次数、电池的总容量、电池剩余容量、电池的技术型号、电池的充电类型变化时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_BATTERY_CHANGED = 'usual.event.BATTERY_CHANGED'--><!--Device-Support-COMMON_EVENT_BATTERY_CHANGED = 'usual.event.BATTERY_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BATTERY_LOW

```TypeScript
COMMON_EVENT_BATTERY_LOW = 'usual.event.BATTERY_LOW'
```

表示电池电量低的普通事件的动作。

当电池电量低于设备设置的低电量百分比值时，将会触发事件通知服务发布该系统公共事件。<!--Del-->设备设置低电量百分比值请参考[电量等级定制开发指导](../../../../../../device-dev/subsystems/subsys-power-battery-level-customization.md)。<!--DelEnd-->

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_BATTERY_LOW = 'usual.event.BATTERY_LOW'--><!--Device-Support-COMMON_EVENT_BATTERY_LOW = 'usual.event.BATTERY_LOW'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BATTERY_OKAY

```TypeScript
COMMON_EVENT_BATTERY_OKAY = 'usual.event.BATTERY_OKAY'
```

表示电池退出低电量状态的公共事件的动作。

当电池电量从低电量等级变化到电池电量高于低电量等级时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_BATTERY_OKAY = 'usual.event.BATTERY_OKAY'--><!--Device-Support-COMMON_EVENT_BATTERY_OKAY = 'usual.event.BATTERY_OKAY'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_POWER_CONNECTED

```TypeScript
COMMON_EVENT_POWER_CONNECTED = 'usual.event.POWER_CONNECTED'
```

设备连接到外部电源的公共事件的动作。

当设备连接到外部可识别的充电器类型充电时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_POWER_CONNECTED = 'usual.event.POWER_CONNECTED'--><!--Device-Support-COMMON_EVENT_POWER_CONNECTED = 'usual.event.POWER_CONNECTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_POWER_DISCONNECTED

```TypeScript
COMMON_EVENT_POWER_DISCONNECTED = 'usual.event.POWER_DISCONNECTED'
```

设备与外部电源断开的公共事件的动作。

当设备与外部电源断开时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_POWER_DISCONNECTED = 'usual.event.POWER_DISCONNECTED'--><!--Device-Support-COMMON_EVENT_POWER_DISCONNECTED = 'usual.event.POWER_DISCONNECTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SCREEN_OFF

```TypeScript
COMMON_EVENT_SCREEN_OFF = 'usual.event.SCREEN_OFF'
```

表示由电源服务发起的设备灭屏完成的普通事件的动作。

当由电源服务发起的设备灭屏完成时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_SCREEN_OFF = 'usual.event.SCREEN_OFF'--><!--Device-Support-COMMON_EVENT_SCREEN_OFF = 'usual.event.SCREEN_OFF'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SCREEN_ON

```TypeScript
COMMON_EVENT_SCREEN_ON = 'usual.event.SCREEN_ON'
```

表示由电源服务发起的设备亮屏完成的普通事件的动作。

当由电源服务发起的设备亮屏完成时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_SCREEN_ON = 'usual.event.SCREEN_ON'--><!--Device-Support-COMMON_EVENT_SCREEN_ON = 'usual.event.SCREEN_ON'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_THERMAL_LEVEL_CHANGED

```TypeScript
COMMON_EVENT_THERMAL_LEVEL_CHANGED = 'usual.event.THERMAL_LEVEL_CHANGED'
```

表示设备热状态的公共事件的动作。

当设备热等级变化时，将会触发事件通知服务发布该系统公共事件。<!--Del-->设备热等级配置请参考[热等级定制开发指导](../../../../../../device-dev/subsystems/subsys-thermal_level.md)。<!--DelEnd-->

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_THERMAL_LEVEL_CHANGED = 'usual.event.THERMAL_LEVEL_CHANGED'--><!--Device-Support-COMMON_EVENT_THERMAL_LEVEL_CHANGED = 'usual.event.THERMAL_LEVEL_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ENTER_FORCE_SLEEP

```TypeScript
COMMON_EVENT_ENTER_FORCE_SLEEP = 'usual.event.ENTER_FORCE_SLEEP'
```

表示设备即将进入强制睡眠模式的公共事件的动作。

当设备即将进入强制睡眠模式时，将会触发事件通知服务发布该系统公共事件。所有订阅者必须在1秒钟内处理该事件。

**起始版本：** 12

<!--Device-Support-COMMON_EVENT_ENTER_FORCE_SLEEP = 'usual.event.ENTER_FORCE_SLEEP'--><!--Device-Support-COMMON_EVENT_ENTER_FORCE_SLEEP = 'usual.event.ENTER_FORCE_SLEEP'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_EXIT_FORCE_SLEEP

```TypeScript
COMMON_EVENT_EXIT_FORCE_SLEEP = 'usual.event.EXIT_FORCE_SLEEP'
```

表示设备退出强制睡眠模式的公共事件的动作。

当设备退出强制睡眠模式时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 12

<!--Device-Support-COMMON_EVENT_EXIT_FORCE_SLEEP = 'usual.event.EXIT_FORCE_SLEEP'--><!--Device-Support-COMMON_EVENT_EXIT_FORCE_SLEEP = 'usual.event.EXIT_FORCE_SLEEP'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ENTER_HIBERNATE

```TypeScript
COMMON_EVENT_ENTER_HIBERNATE = 'usual.event.ENTER_HIBERNATE'
```

表示设备即将进入休眠模式的公共事件的动作。

当设备即将进入休眠模式时，将会触发事件通知服务发布该系统公共事件。所有订阅者必须在1秒钟内处理该事件。

**起始版本：** 15

<!--Device-Support-COMMON_EVENT_ENTER_HIBERNATE = 'usual.event.ENTER_HIBERNATE'--><!--Device-Support-COMMON_EVENT_ENTER_HIBERNATE = 'usual.event.ENTER_HIBERNATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_EXIT_HIBERNATE

```TypeScript
COMMON_EVENT_EXIT_HIBERNATE = 'usual.event.EXIT_HIBERNATE'
```

表示设备退出休眠模式的公共事件的动作。

当设备退出休眠模式时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 15

<!--Device-Support-COMMON_EVENT_EXIT_HIBERNATE = 'usual.event.EXIT_HIBERNATE'--><!--Device-Support-COMMON_EVENT_EXIT_HIBERNATE = 'usual.event.EXIT_HIBERNATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_PRESENT

```TypeScript
COMMON_EVENT_USER_PRESENT = 'usual.event.USER_PRESENT'
```

用户解锁设备的公共事件的动作。

**起始版本：** 9

**废弃版本：** 10

<!--Device-Support-COMMON_EVENT_USER_PRESENT = 'usual.event.USER_PRESENT'--><!--Device-Support-COMMON_EVENT_USER_PRESENT = 'usual.event.USER_PRESENT'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TIME_TICK

```TypeScript
COMMON_EVENT_TIME_TICK = 'usual.event.TIME_TICK'
```

表示系统时间更改的公共事件的动作。

当以整分钟为单位的系统时间更改时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_TIME_TICK = 'usual.event.TIME_TICK'--><!--Device-Support-COMMON_EVENT_TIME_TICK = 'usual.event.TIME_TICK'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TIME_CHANGED

```TypeScript
COMMON_EVENT_TIME_CHANGED = 'usual.event.TIME_CHANGED'
```

设置系统时间的公共事件的动作。

当设置系统时间时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_TIME_CHANGED = 'usual.event.TIME_CHANGED'--><!--Device-Support-COMMON_EVENT_TIME_CHANGED = 'usual.event.TIME_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DATE_CHANGED

```TypeScript
COMMON_EVENT_DATE_CHANGED = 'usual.event.DATE_CHANGED'
```

（预留事件，暂未支持）表示系统日期已更改的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_DATE_CHANGED = 'usual.event.DATE_CHANGED'--><!--Device-Support-COMMON_EVENT_DATE_CHANGED = 'usual.event.DATE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TIMEZONE_CHANGED

```TypeScript
COMMON_EVENT_TIMEZONE_CHANGED = 'usual.event.TIMEZONE_CHANGED'
```

表示系统时区更改的公共事件的动作。

当系统时区更改时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_TIMEZONE_CHANGED = 'usual.event.TIMEZONE_CHANGED'--><!--Device-Support-COMMON_EVENT_TIMEZONE_CHANGED = 'usual.event.TIMEZONE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CLOSE_SYSTEM_DIALOGS

```TypeScript
COMMON_EVENT_CLOSE_SYSTEM_DIALOGS = 'usual.event.CLOSE_SYSTEM_DIALOGS'
```

（预留事件，暂未支持）表示用户关闭临时系统对话框的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_CLOSE_SYSTEM_DIALOGS = 'usual.event.CLOSE_SYSTEM_DIALOGS'--><!--Device-Support-COMMON_EVENT_CLOSE_SYSTEM_DIALOGS = 'usual.event.CLOSE_SYSTEM_DIALOGS'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_ADDED

```TypeScript
COMMON_EVENT_PACKAGE_ADDED = 'usual.event.PACKAGE_ADDED'
```

表示设备上已安装新应用包的公共事件的动作。

在设备上指定用户下安装了新的应用程序，将会触发事件通知服务发布该系统公共事件。

> **说明：**  
>  
> 三方应用只能监听自身应用的安装事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGE_ADDED = 'usual.event.PACKAGE_ADDED'--><!--Device-Support-COMMON_EVENT_PACKAGE_ADDED = 'usual.event.PACKAGE_ADDED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_REPLACED

```TypeScript
COMMON_EVENT_PACKAGE_REPLACED = 'usual.event.PACKAGE_REPLACED'
```

（预留事件，暂未支持）表示设备上安装了新版本的应用程序包并替换了旧版本的动作。数据包含包的名称。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGE_REPLACED = 'usual.event.PACKAGE_REPLACED'--><!--Device-Support-COMMON_EVENT_PACKAGE_REPLACED = 'usual.event.PACKAGE_REPLACED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MY_PACKAGE_REPLACED

```TypeScript
COMMON_EVENT_MY_PACKAGE_REPLACED = 'usual.event.MY_PACKAGE_REPLACED'
```

（预留事件，暂未支持）表示设备上安装了新版本的应用程序包并替换了旧版本的应用程序包的动作，不包含额外的数据，只发送给被替换的应用程序。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_MY_PACKAGE_REPLACED = 'usual.event.MY_PACKAGE_REPLACED'--><!--Device-Support-COMMON_EVENT_MY_PACKAGE_REPLACED = 'usual.event.MY_PACKAGE_REPLACED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_REMOVED

```TypeScript
COMMON_EVENT_PACKAGE_REMOVED = 'usual.event.PACKAGE_REMOVED'
```

表示现有的应用程序包从设备中移除的事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGE_REMOVED = 'usual.event.PACKAGE_REMOVED'--><!--Device-Support-COMMON_EVENT_PACKAGE_REMOVED = 'usual.event.PACKAGE_REMOVED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BUNDLE_REMOVED

```TypeScript
COMMON_EVENT_BUNDLE_REMOVED = 'usual.event.BUNDLE_REMOVED'
```

表示现有的应用程序包从设备中移除的事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_BUNDLE_REMOVED = 'usual.event.BUNDLE_REMOVED'--><!--Device-Support-COMMON_EVENT_BUNDLE_REMOVED = 'usual.event.BUNDLE_REMOVED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_FULLY_REMOVED

```TypeScript
COMMON_EVENT_PACKAGE_FULLY_REMOVED = 'usual.event.PACKAGE_FULLY_REMOVED'
```

表示现有的应用程序包从设备上完全删除的事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGE_FULLY_REMOVED = 'usual.event.PACKAGE_FULLY_REMOVED'--><!--Device-Support-COMMON_EVENT_PACKAGE_FULLY_REMOVED = 'usual.event.PACKAGE_FULLY_REMOVED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_CHANGED

```TypeScript
COMMON_EVENT_PACKAGE_CHANGED = 'usual.event.PACKAGE_CHANGED'
```

表示应用包已更改的公共事件的动作（例如，包中的组件已启用或禁用）。

在设备上安装的应用程序包更新或者包的组件被禁用使能，将会触发事件通知服务发布该系统公共事件。

> **说明：**  
>  
> 三方应用只能监听自身应用的更改事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGE_CHANGED = 'usual.event.PACKAGE_CHANGED'--><!--Device-Support-COMMON_EVENT_PACKAGE_CHANGED = 'usual.event.PACKAGE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_RESTARTED

```TypeScript
COMMON_EVENT_PACKAGE_RESTARTED = 'usual.event.PACKAGE_RESTARTED'
```

表示用户重启应用包并终止其所有进程。

在设备上指定用户重启应用包并终止其所有进程，将会触发事件通知服务发布该系统公共事件。

> **说明：**  
>  
> 三方应用只能监听自身应用的重启事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGE_RESTARTED = 'usual.event.PACKAGE_RESTARTED'--><!--Device-Support-COMMON_EVENT_PACKAGE_RESTARTED = 'usual.event.PACKAGE_RESTARTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_DATA_CLEARED

```TypeScript
COMMON_EVENT_PACKAGE_DATA_CLEARED = 'usual.event.PACKAGE_DATA_CLEARED'
```

表示用户清除应用包数据。

在设备上指定用户清除应用包数据，将会触发事件通知服务发布该系统公共事件。

> **说明：**  
>  
> 三方应用只能监听自身应用的数据清理事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGE_DATA_CLEARED = 'usual.event.PACKAGE_DATA_CLEARED'--><!--Device-Support-COMMON_EVENT_PACKAGE_DATA_CLEARED = 'usual.event.PACKAGE_DATA_CLEARED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_CACHE_CLEARED

```TypeScript
COMMON_EVENT_PACKAGE_CACHE_CLEARED = 'usual.event.PACKAGE_CACHE_CLEARED'
```

表示用户清除应用包缓存数据的公共事件的动作。

对设备上安装的应用程序包清除缓存时，将会触发事件通知服务发布该系统公共事件。

> **说明：**  
>  
> 三方应用只能监听自身应用的缓存清理事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGE_CACHE_CLEARED = 'usual.event.PACKAGE_CACHE_CLEARED'--><!--Device-Support-COMMON_EVENT_PACKAGE_CACHE_CLEARED = 'usual.event.PACKAGE_CACHE_CLEARED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGES_SUSPENDED

```TypeScript
COMMON_EVENT_PACKAGES_SUSPENDED = 'usual.event.PACKAGES_SUSPENDED'
```

表示包已经被挂起。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGES_SUSPENDED = 'usual.event.PACKAGES_SUSPENDED'--><!--Device-Support-COMMON_EVENT_PACKAGES_SUSPENDED = 'usual.event.PACKAGES_SUSPENDED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGES_UNSUSPENDED

```TypeScript
COMMON_EVENT_PACKAGES_UNSUSPENDED = 'usual.event.PACKAGES_UNSUSPENDED'
```

（预留事件，暂未支持）表示包已经被解除挂起。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGES_UNSUSPENDED = 'usual.event.PACKAGES_UNSUSPENDED'--><!--Device-Support-COMMON_EVENT_PACKAGES_UNSUSPENDED = 'usual.event.PACKAGES_UNSUSPENDED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MY_PACKAGE_SUSPENDED

```TypeScript
COMMON_EVENT_MY_PACKAGE_SUSPENDED = 'usual.event.MY_PACKAGE_SUSPENDED'
```

发送到已被系统挂起的包。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_MY_PACKAGE_SUSPENDED = 'usual.event.MY_PACKAGE_SUSPENDED'--><!--Device-Support-COMMON_EVENT_MY_PACKAGE_SUSPENDED = 'usual.event.MY_PACKAGE_SUSPENDED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MY_PACKAGE_UNSUSPENDED

```TypeScript
COMMON_EVENT_MY_PACKAGE_UNSUSPENDED = 'usual.event.MY_PACKAGE_UNSUSPENDED'
```

发送到已被系统解除挂起的包。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_MY_PACKAGE_UNSUSPENDED = 'usual.event.MY_PACKAGE_UNSUSPENDED'--><!--Device-Support-COMMON_EVENT_MY_PACKAGE_UNSUSPENDED = 'usual.event.MY_PACKAGE_UNSUSPENDED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_UID_REMOVED

```TypeScript
COMMON_EVENT_UID_REMOVED = 'usual.event.UID_REMOVED'
```

（预留事件，暂未支持）表示用户ID已从系统中删除的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_UID_REMOVED = 'usual.event.UID_REMOVED'--><!--Device-Support-COMMON_EVENT_UID_REMOVED = 'usual.event.UID_REMOVED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_FIRST_LAUNCH

```TypeScript
COMMON_EVENT_PACKAGE_FIRST_LAUNCH = 'usual.event.PACKAGE_FIRST_LAUNCH'
```

（预留事件，暂未支持）应用程序在安装后首次启动。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGE_FIRST_LAUNCH = 'usual.event.PACKAGE_FIRST_LAUNCH'--><!--Device-Support-COMMON_EVENT_PACKAGE_FIRST_LAUNCH = 'usual.event.PACKAGE_FIRST_LAUNCH'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION

```TypeScript
COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION = 'usual.event.PACKAGE_NEEDS_VERIFICATION'
```

（预留事件，暂未支持）当一个包需要被验证时，由系统包验证者发送。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION = 'usual.event.PACKAGE_NEEDS_VERIFICATION'--><!--Device-Support-COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION = 'usual.event.PACKAGE_NEEDS_VERIFICATION'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_VERIFIED

```TypeScript
COMMON_EVENT_PACKAGE_VERIFIED = 'usual.event.PACKAGE_VERIFIED'
```

（预留事件，暂未支持）当一个包被验证时，由系统包验证者发送。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_PACKAGE_VERIFIED = 'usual.event.PACKAGE_VERIFIED'--><!--Device-Support-COMMON_EVENT_PACKAGE_VERIFIED = 'usual.event.PACKAGE_VERIFIED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE

```TypeScript
COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_AVAILABLE'
```

（预留事件，暂未支持）表示安装在外部存储上的应用程序对系统可用的公共事件的操作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_AVAILABLE'--><!--Device-Support-COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_AVAILABLE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE

```TypeScript
COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE'
```

（预留事件，暂未支持）表示安装在外部存储上的应用程序对系统不可用的公共事件的操作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE'--><!--Device-Support-COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CONFIGURATION_CHANGED

```TypeScript
COMMON_EVENT_CONFIGURATION_CHANGED = 'usual.event.CONFIGURATION_CHANGED'
```

（预留事件，暂未支持）表示设备状态（例如，方向和区域设置）已更改的公共事件的操作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_CONFIGURATION_CHANGED = 'usual.event.CONFIGURATION_CHANGED'--><!--Device-Support-COMMON_EVENT_CONFIGURATION_CHANGED = 'usual.event.CONFIGURATION_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LOCALE_CHANGED

```TypeScript
COMMON_EVENT_LOCALE_CHANGED = 'usual.event.LOCALE_CHANGED'
```

设置系统语言的公共事件的动作。

当设置系统语言时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_LOCALE_CHANGED = 'usual.event.LOCALE_CHANGED'--><!--Device-Support-COMMON_EVENT_LOCALE_CHANGED = 'usual.event.LOCALE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MANAGE_PACKAGE_STORAGE

```TypeScript
COMMON_EVENT_MANAGE_PACKAGE_STORAGE = 'usual.event.MANAGE_PACKAGE_STORAGE'
```

通知用户低内存状态并且应该启动包管理。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_MANAGE_PACKAGE_STORAGE = 'usual.event.MANAGE_PACKAGE_STORAGE'--><!--Device-Support-COMMON_EVENT_MANAGE_PACKAGE_STORAGE = 'usual.event.MANAGE_PACKAGE_STORAGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DRIVE_MODE

```TypeScript
COMMON_EVENT_DRIVE_MODE = 'common.event.DRIVE_MODE'
```

（预留事件，暂未支持）表示系统处于驾驶模式的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_DRIVE_MODE = 'common.event.DRIVE_MODE'--><!--Device-Support-COMMON_EVENT_DRIVE_MODE = 'common.event.DRIVE_MODE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HOME_MODE

```TypeScript
COMMON_EVENT_HOME_MODE = 'common.event.HOME_MODE'
```

（预留事件，暂未支持）表示系统处于HOME模式的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_HOME_MODE = 'common.event.HOME_MODE'--><!--Device-Support-COMMON_EVENT_HOME_MODE = 'common.event.HOME_MODE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_OFFICE_MODE

```TypeScript
COMMON_EVENT_OFFICE_MODE = 'common.event.OFFICE_MODE'
```

（预留事件，暂未支持）表示系统处于办公模式的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_OFFICE_MODE = 'common.event.OFFICE_MODE'--><!--Device-Support-COMMON_EVENT_OFFICE_MODE = 'common.event.OFFICE_MODE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STARTED

```TypeScript
COMMON_EVENT_USER_STARTED = 'usual.event.USER_STARTED'
```

（预留事件，暂未支持）表示用户已启动的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USER_STARTED = 'usual.event.USER_STARTED'--><!--Device-Support-COMMON_EVENT_USER_STARTED = 'usual.event.USER_STARTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_BACKGROUND

```TypeScript
COMMON_EVENT_USER_BACKGROUND = 'usual.event.USER_BACKGROUND'
```

（预留事件，暂未支持）表示用户已被带到后台的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USER_BACKGROUND = 'usual.event.USER_BACKGROUND'--><!--Device-Support-COMMON_EVENT_USER_BACKGROUND = 'usual.event.USER_BACKGROUND'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_FOREGROUND

```TypeScript
COMMON_EVENT_USER_FOREGROUND = 'usual.event.USER_FOREGROUND'
```

（预留事件，暂未支持）表示用户已被带到前台的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USER_FOREGROUND = 'usual.event.USER_FOREGROUND'--><!--Device-Support-COMMON_EVENT_USER_FOREGROUND = 'usual.event.USER_FOREGROUND'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_SWITCHED

```TypeScript
COMMON_EVENT_USER_SWITCHED = 'usual.event.USER_SWITCHED'
```

表示用户切换完成的公共事件的动作。

切换系统账号将会触发事件通知服务发布该系统公共事件，事件携带系统账号ID。

与这个公共事件相关的接口：activateOsAccount, 为系统API，具体参看[@ohos.account.osAccount](../../../../reference/js-apis-osAccount.md)。

要订阅此事件，在API version 21之前，需要申请ohos.permission.MANAGE_LOCAL_ACCOUNTS权限；从API version 21开始，需要申请ohos.permission.MANAGE_LOCAL_ACCOUNTS或ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USER_SWITCHED = 'usual.event.USER_SWITCHED'--><!--Device-Support-COMMON_EVENT_USER_SWITCHED = 'usual.event.USER_SWITCHED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STARTING

```TypeScript
COMMON_EVENT_USER_STARTING = 'usual.event.USER_STARTING'
```

（预留事件，暂未支持）表示要启动用户的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限（该权限仅系统应用可申请）。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USER_STARTING = 'usual.event.USER_STARTING'--><!--Device-Support-COMMON_EVENT_USER_STARTING = 'usual.event.USER_STARTING'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_UNLOCKED

```TypeScript
COMMON_EVENT_USER_UNLOCKED = 'usual.event.USER_UNLOCKED'
```

表示设备重启后解锁时，当前用户的凭据加密存储已解锁的公共事件的动作。

切换到带有锁屏密码的用户，并且首次解锁会发出触发事件通知服务发布该系统公共事件，事件携带标识该用户的系统账号ID。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USER_UNLOCKED = 'usual.event.USER_UNLOCKED'--><!--Device-Support-COMMON_EVENT_USER_UNLOCKED = 'usual.event.USER_UNLOCKED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STOPPING

```TypeScript
COMMON_EVENT_USER_STOPPING = 'usual.event.USER_STOPPING'
```

（预留事件，暂未支持）表示要停止用户的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限（该权限仅系统应用可申请）。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USER_STOPPING = 'usual.event.USER_STOPPING'--><!--Device-Support-COMMON_EVENT_USER_STOPPING = 'usual.event.USER_STOPPING'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STOPPED

```TypeScript
COMMON_EVENT_USER_STOPPED = 'usual.event.USER_STOPPED'
```

（预留事件，暂未支持）表示用户已停止的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USER_STOPPED = 'usual.event.USER_STOPPED'--><!--Device-Support-COMMON_EVENT_USER_STOPPED = 'usual.event.USER_STOPPED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN

```TypeScript
COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN = 'common.event.DISTRIBUTED_ACCOUNT_LOGIN'
```

表示分布式账号登录成功的动作。

分布式账号登录成功时会触发事件通知服务发布该系统公共事件，事件携带系统账号ID和子身份ID。

与这个公共事件相关的接口：setOsAccountDistributedInfo、updateOsAccountDistributedInfo(已废弃)，这些为公共API，setOsAccountDistributedInfoByLocalId为系统API，具体参看[分布式账号接口文档](../../../../reference/js-apis-distributed-account.md)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Support-COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN = 'common.event.DISTRIBUTED_ACCOUNT_LOGIN'--><!--Device-Support-COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN = 'common.event.DISTRIBUTED_ACCOUNT_LOGIN'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT

```TypeScript
COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT = 'common.event.DISTRIBUTED_ACCOUNT_LOGOUT'
```

表示分布式账号登出成功的动作。

分布式账号登出时会触发事件通知服务发布该系统公共事件，事件携带系统账号ID和子身份ID。

与这个公共事件相关的接口：setOsAccountDistributedInfo、updateOsAccountDistributedInfo(已废弃)，这些为公共API，setOsAccountDistributedInfoByLocalId为系统API，具体参看[分布式账号接口文档](../../../../reference/js-apis-distributed-account.md)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Support-COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT = 'common.event.DISTRIBUTED_ACCOUNT_LOGOUT'--><!--Device-Support-COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT = 'common.event.DISTRIBUTED_ACCOUNT_LOGOUT'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID

```TypeScript
COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID = 'common.event.DISTRIBUTED_ACCOUNT_TOKEN_INVALID'
```

表示分布式账号token令牌无效的动作。

分布式账号的token令牌无效时会触发事件通知服务发布该系统公共事件，事件携带系统账号ID和子身份ID。

与这个公共事件相关的接口：setOsAccountDistributedInfo、updateOsAccountDistributedInfo(已废弃)，这些为公共API，setOsAccountDistributedInfoByLocalId为系统API，具体参看[分布式账号接口文档](../../../../reference/js-apis-distributed-account.md)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Support-COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID = 'common.event.DISTRIBUTED_ACCOUNT_TOKEN_INVALID'--><!--Device-Support-COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID = 'common.event.DISTRIBUTED_ACCOUNT_TOKEN_INVALID'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF

```TypeScript
COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF = 'common.event.DISTRIBUTED_ACCOUNT_LOGOFF'
```

表示分布式账号注销的动作。

分布式账号注销成功会时触发事件通知服务发布该系统公共事件，事件携带系统账号ID和子身份ID。

与这个公共事件相关的接口：setOsAccountDistributedInfo、updateOsAccountDistributedInfo(已废弃)，这些为公共API，setOsAccountDistributedInfoByLocalId为系统API，具体参看[分布式账号接口文档](../../../../reference/js-apis-distributed-account.md)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Support-COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF = 'common.event.DISTRIBUTED_ACCOUNT_LOGOFF'--><!--Device-Support-COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF = 'common.event.DISTRIBUTED_ACCOUNT_LOGOFF'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_POWER_STATE

```TypeScript
COMMON_EVENT_WIFI_POWER_STATE = 'usual.event.wifi.POWER_STATE'
```

Wi-Fi状态变化。

当Wi-Fi状态发生变化时（如启用、禁用Wi-Fi），将会触发事件通知服务发布该系统公共事件。

状态值：0：WLAN正在关闭，1：WLAN已关闭，2：WLAN正在打开，3：WLAN已启动。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_POWER_STATE = 'usual.event.wifi.POWER_STATE'--><!--Device-Support-COMMON_EVENT_WIFI_POWER_STATE = 'usual.event.wifi.POWER_STATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_SCAN_FINISHED

```TypeScript
COMMON_EVENT_WIFI_SCAN_FINISHED = 'usual.event.wifi.SCAN_FINISHED'
```

表示Wi-Fi接入点已被扫描并证明可用的动作。

当Wi-Fi接入点已被扫描并证明可用，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.LOCATION权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_SCAN_FINISHED = 'usual.event.wifi.SCAN_FINISHED'--><!--Device-Support-COMMON_EVENT_WIFI_SCAN_FINISHED = 'usual.event.wifi.SCAN_FINISHED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_RSSI_VALUE

```TypeScript
COMMON_EVENT_WIFI_RSSI_VALUE = 'usual.event.wifi.RSSI_VALUE'
```

表示Wi-Fi信号强度（RSSI）改变。

当Wi-Fi信号强度（RSSI）发生变化，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_RSSI_VALUE = 'usual.event.wifi.RSSI_VALUE'--><!--Device-Support-COMMON_EVENT_WIFI_RSSI_VALUE = 'usual.event.wifi.RSSI_VALUE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_CONN_STATE

```TypeScript
COMMON_EVENT_WIFI_CONN_STATE = 'usual.event.wifi.CONN_STATE'
```

Wi-Fi连接状态发生改变。

当Wi-Fi连接状态发生变化，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_CONN_STATE = 'usual.event.wifi.CONN_STATE'--><!--Device-Support-COMMON_EVENT_WIFI_CONN_STATE = 'usual.event.wifi.CONN_STATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_HOTSPOT_STATE

```TypeScript
COMMON_EVENT_WIFI_HOTSPOT_STATE = 'usual.event.wifi.HOTSPOT_STATE'
```

表示Wi-Fi热点状态变化。

当Wi-Fi热点状态发生变化，将会触发事件通知服务发布该系统公共事件。

状态值：2：AP正在打开，3：AP已启动，4：AP正在关闭，5：AP已关闭。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_HOTSPOT_STATE = 'usual.event.wifi.HOTSPOT_STATE'--><!--Device-Support-COMMON_EVENT_WIFI_HOTSPOT_STATE = 'usual.event.wifi.HOTSPOT_STATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_AP_STA_JOIN

```TypeScript
COMMON_EVENT_WIFI_AP_STA_JOIN = 'usual.event.wifi.WIFI_HS_STA_JOIN'
```

表示客户端加入当前设备Wi-Fi热点。

当客户端加入当前设备Wi-Fi热点，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_AP_STA_JOIN = 'usual.event.wifi.WIFI_HS_STA_JOIN'--><!--Device-Support-COMMON_EVENT_WIFI_AP_STA_JOIN = 'usual.event.wifi.WIFI_HS_STA_JOIN'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_AP_STA_LEAVE

```TypeScript
COMMON_EVENT_WIFI_AP_STA_LEAVE = 'usual.event.wifi.WIFI_HS_STA_LEAVE'
```

表示客户端已断开与当前设备Wi-Fi热点的连接。

当客户端已断开与当前设备Wi-Fi热点的连接，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_AP_STA_LEAVE = 'usual.event.wifi.WIFI_HS_STA_LEAVE'--><!--Device-Support-COMMON_EVENT_WIFI_AP_STA_LEAVE = 'usual.event.wifi.WIFI_HS_STA_LEAVE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE

```TypeScript
COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE = 'usual.event.wifi.mplink.STATE_CHANGE'
```

表示MPLink（增强Wi-Fi功能）状态已更改。

当MPLink（增强Wi-Fi功能）状态发生变化，将会触发事件通知服务发布该系统公共事件（暂不支持）。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE = 'usual.event.wifi.mplink.STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE = 'usual.event.wifi.mplink.STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_CONN_STATE

```TypeScript
COMMON_EVENT_WIFI_P2P_CONN_STATE = 'usual.event.wifi.p2p.CONN_STATE_CHANGE'
```

表示Wi-Fi P2P连接状态改变。

当Wi-Fi P2P连接状态发生变化，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO和ohos.permission.LOCATION权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_P2P_CONN_STATE = 'usual.event.wifi.p2p.CONN_STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_WIFI_P2P_CONN_STATE = 'usual.event.wifi.p2p.CONN_STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_STATE_CHANGED = 'usual.event.wifi.p2p.STATE_CHANGE'
```

表示Wi-Fi P2P状态变化。

当Wi-Fi P2P状态发生变化，将会触发事件通知服务发布该系统公共事件。

状态值：2：P2P正在打开，3：P2P已启动，4：P2P正在关闭，5：P2P已关闭。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_P2P_STATE_CHANGED = 'usual.event.wifi.p2p.STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_WIFI_P2P_STATE_CHANGED = 'usual.event.wifi.p2p.STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED = 'usual.event.wifi.p2p.DEVICES_CHANGE'
```

表示Wi-Fi P2P对等体状态变化。

当Wi-Fi P2P对等体状态变化，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED = 'usual.event.wifi.p2p.DEVICES_CHANGE'--><!--Device-Support-COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED = 'usual.event.wifi.p2p.DEVICES_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED = 'usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE'
```

表示Wi-Fi P2P发现状态变化。

当Wi-Fi P2P发现状态变化，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED = 'usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED = 'usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED = 'usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE'
```

表示Wi-Fi P2P当前设备状态变化。

当Wi-Fi P2P当前设备状态变化，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED = 'usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE'--><!--Device-Support-COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED = 'usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED = 'usual.event.wifi.p2p.GROUP_STATE_CHANGED'
```

表示Wi-Fi P2P群组信息已更改。

当Wi-Fi P2P群组信息发生变化，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED = 'usual.event.wifi.p2p.GROUP_STATE_CHANGED'--><!--Device-Support-COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED = 'usual.event.wifi.p2p.GROUP_STATE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE'
```

（预留事件，暂未支持）蓝牙免提通信连接状态公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_CHANGE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_handsfree_ag_connect_state_change)

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE =
        'usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE'
```

（预留事件，暂未支持）表示连接到蓝牙免提的设备处于活动状态的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE =
        'usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE =
        'usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE =
        'usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE'
```

（预留事件，暂未支持）表示蓝牙A2DP连接状态已更改的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE =
        'usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE =
        'usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE'
```

（预留事件，暂未支持）蓝牙A2DP连接状态公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_CHANGE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_a2dpsource_connect_state_change)

<!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE =
        'usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE'
```

（预留事件，暂未支持）表示使用蓝牙A2DP连接的设备处于活动状态的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE =
        'usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE =
        'usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE'
```

（预留事件，暂未支持）蓝牙A2DP播放状态改变的普通事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE'
```

（预留事件，暂未支持）表示蓝牙A2DP的AVRCP连接状态已更改的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_CHANGE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_a2dpsource_avrcp_connect_state_change)

<!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE =
        'usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE'
```

（预留事件，暂未支持）表示蓝牙A2DP音频编解码状态更改的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_CHANGE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_a2dpsource_codec_value_change)

<!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE =
        'usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE =
        'usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED =
        'usual.event.bluetooth.remotedevice.DISCOVERED'
```

（预留事件，暂未支持）表示发现远程蓝牙设备的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.LOCATION和ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED =
        'usual.event.bluetooth.remotedevice.DISCOVERED'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED =
        'usual.event.bluetooth.remotedevice.DISCOVERED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE =
        'usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE'
```

（预留事件，暂未支持）表示远程蓝牙设备的蓝牙类别已更改的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE =
        'usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE =
        'usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED =
        'usual.event.bluetooth.remotedevice.ACL_CONNECTED'
```

（预留事件，暂未支持）表示已与远程蓝牙设备建立低级别（ACL）连接的公共事件的动作。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_acl_state_change)

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED =
        'usual.event.bluetooth.remotedevice.ACL_CONNECTED'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED =
        'usual.event.bluetooth.remotedevice.ACL_CONNECTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED =
        'usual.event.bluetooth.remotedevice.ACL_DISCONNECTED'
```

（预留事件，暂未支持）表示低电平（ACL）连接已从远程蓝牙设备断开的普通事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_acl_state_change)

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED =
        'usual.event.bluetooth.remotedevice.ACL_DISCONNECTED'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED =
        'usual.event.bluetooth.remotedevice.ACL_DISCONNECTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE =
        'usual.event.bluetooth.remotedevice.NAME_UPDATE'
```

（预留事件，暂未支持）表示远程蓝牙设备的友好名称首次被检索或自上次检索以来被更改的公共事件的操作。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE =
        'usual.event.bluetooth.remotedevice.NAME_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE =
        'usual.event.bluetooth.remotedevice.NAME_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE =
        'usual.event.bluetooth.remotedevice.PAIR_STATE'
```

（预留事件，暂未支持）远程蓝牙设备连接状态更改的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE_CHANGE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_pair_state_change)

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE =
        'usual.event.bluetooth.remotedevice.PAIR_STATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE =
        'usual.event.bluetooth.remotedevice.PAIR_STATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE =
        'usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE'
```

（预留事件，暂未支持）表示远程蓝牙设备的电池电量首次被检索或自上次检索以来被更改的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE =
        'usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE =
        'usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT =
        'usual.event.bluetooth.remotedevice.SDP_RESULT'
```

（预留事件，暂未支持）远程蓝牙设备SDP状态公共事件的动作。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT =
        'usual.event.bluetooth.remotedevice.SDP_RESULT'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT =
        'usual.event.bluetooth.remotedevice.SDP_RESULT'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE =
        'usual.event.bluetooth.remotedevice.UUID_VALUE'
```

远程蓝牙设备UUID连接状态公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE =
        'usual.event.bluetooth.remotedevice.UUID_VALUE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE =
        'usual.event.bluetooth.remotedevice.UUID_VALUE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ =
        'usual.event.bluetooth.remotedevice.PAIRING_REQ'
```

（预留事件，暂未支持）表示远程蓝牙设备配对请求的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.DISCOVER_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ =
        'usual.event.bluetooth.remotedevice.PAIRING_REQ'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ =
        'usual.event.bluetooth.remotedevice.PAIRING_REQ'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL =
        'usual.event.bluetooth.remotedevice.PAIRING_CANCEL'
```

（预留事件，暂未支持）取消蓝牙配对的公共事件的动作。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL =
        'usual.event.bluetooth.remotedevice.PAIRING_CANCEL'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL =
        'usual.event.bluetooth.remotedevice.PAIRING_CANCEL'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ =
        'usual.event.bluetooth.remotedevice.CONNECT_REQ'
```

（预留事件，暂未支持）表示远程蓝牙设备连接请求的公共事件的动作。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ =
        'usual.event.bluetooth.remotedevice.CONNECT_REQ'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ =
        'usual.event.bluetooth.remotedevice.CONNECT_REQ'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY =
        'usual.event.bluetooth.remotedevice.CONNECT_REPLY'
```

（预留事件，暂未支持）表示远程蓝牙设备连接请求响应的公共事件的动作。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY =
        'usual.event.bluetooth.remotedevice.CONNECT_REPLY'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY =
        'usual.event.bluetooth.remotedevice.CONNECT_REPLY'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL =
        'usual.event.bluetooth.remotedevice.CONNECT_CANCEL'
```

（预留事件，暂未支持）表示取消与远程蓝牙设备的连接的公共事件的动作。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL =
        'usual.event.bluetooth.remotedevice.CONNECT_CANCEL'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL =
        'usual.event.bluetooth.remotedevice.CONNECT_CANCEL'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE'
```

（预留事件，暂未支持）表示蓝牙免提连接状态已更改的公共事件的动作。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE =
        'usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE'
```

（预留事件，暂未支持）表示蓝牙免提音频状态已更改的公共事件的动作。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE =
        'usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE =
        'usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT =
        'usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT'
```

（预留事件，暂未支持）表示蓝牙免提音频网关状态已更改的公共事件的动作。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT =
        'usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT =
        'usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE =
        'usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE'
```

（预留事件，暂未支持）表示蓝牙免提呼叫状态已更改的公共事件的动作。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE =
        'usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE =
        'usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE =
        'usual.event.bluetooth.host.STATE_UPDATE'
```

表示蓝牙适配器状态已更改的公共事件的操作，例如蓝牙已打开或关闭。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE =
        'usual.event.bluetooth.host.STATE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE =
        'usual.event.bluetooth.host.STATE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE =
        'usual.event.bluetooth.host.REQ_DISCOVERABLE'
```

（预留事件，暂未支持）表示用户允许扫描蓝牙请求的公共事件的动作。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE =
        'usual.event.bluetooth.host.REQ_DISCOVERABLE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE =
        'usual.event.bluetooth.host.REQ_DISCOVERABLE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE = 'usual.event.bluetooth.host.REQ_ENABLE'
```

（预留事件，暂未支持）表示用户打开蓝牙请求的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE = 'usual.event.bluetooth.host.REQ_ENABLE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE = 'usual.event.bluetooth.host.REQ_ENABLE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE =
        'usual.event.bluetooth.host.REQ_DISABLE'
```

（预留事件，暂未支持）表示用户关闭蓝牙请求的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE =
        'usual.event.bluetooth.host.REQ_DISABLE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE =
        'usual.event.bluetooth.host.REQ_DISABLE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE =
        'usual.event.bluetooth.host.SCAN_MODE_UPDATE'
```

（预留事件，暂未支持）设备蓝牙扫描模式更改的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE =
        'usual.event.bluetooth.host.SCAN_MODE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE =
        'usual.event.bluetooth.host.SCAN_MODE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_CHANGE =
        'usual.event.bluetooth.host.SCAN_MODE_CHANGE'
```

表示蓝牙扫描模式变化的公共事件的操作。

当蓝牙扫描模式变化时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 23

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_CHANGE =
        'usual.event.bluetooth.host.SCAN_MODE_CHANGE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_CHANGE =
        'usual.event.bluetooth.host.SCAN_MODE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED =
        'usual.event.bluetooth.host.DISCOVERY_STARTED'
```

设备上已启动蓝牙扫描的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED =
        'usual.event.bluetooth.host.DISCOVERY_STARTED'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED =
        'usual.event.bluetooth.host.DISCOVERY_STARTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED =
        'usual.event.bluetooth.host.DISCOVERY_FINISHED'
```

设备上蓝牙扫描完成的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED =
        'usual.event.bluetooth.host.DISCOVERY_FINISHED'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED =
        'usual.event.bluetooth.host.DISCOVERY_FINISHED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE =
        'usual.event.bluetooth.host.NAME_UPDATE'
```

指示设备蓝牙适配器名称已更改的公共事件的操作。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE =
        'usual.event.bluetooth.host.NAME_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE =
        'usual.event.bluetooth.host.NAME_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE'
```

（预留事件，暂未支持）表示蓝牙A2DP连接状态已更改的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE'
```

（预留事件，暂未支持）蓝牙A2DP播放状态改变的普通事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE'
```

（预留事件，暂未支持）表示蓝牙A2DP宿的音频状态已更改的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 9

**废弃版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED

```TypeScript
COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED = 'usual.event.nfc.action.ADAPTER_STATE_CHANGED'
```

指示设备NFC状态已更改的公共事件的操作。

指示设备NFC状态更改时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED = 'usual.event.nfc.action.ADAPTER_STATE_CHANGED'--><!--Device-Support-COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED = 'usual.event.nfc.action.ADAPTER_STATE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED

```TypeScript
COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED = 'usual.event.nfc.action.RF_FIELD_ON_DETECTED'
```

检测到NFC场强进入的公共事件。

当检测到NFC场强进入时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED = 'usual.event.nfc.action.RF_FIELD_ON_DETECTED'--><!--Device-Support-COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED = 'usual.event.nfc.action.RF_FIELD_ON_DETECTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED

```TypeScript
COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED = 'usual.event.nfc.action.RF_FIELD_OFF_DETECTED'
```

检测到NFC场强离开的公共事件。

当检测到NFC场强离开时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED = 'usual.event.nfc.action.RF_FIELD_OFF_DETECTED'--><!--Device-Support-COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED = 'usual.event.nfc.action.RF_FIELD_OFF_DETECTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISCHARGING

```TypeScript
COMMON_EVENT_DISCHARGING = 'usual.event.DISCHARGING'
```

表示系统停止为电池充电的公共事件的动作。

当系统停止为电池充电时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_DISCHARGING = 'usual.event.DISCHARGING'--><!--Device-Support-COMMON_EVENT_DISCHARGING = 'usual.event.DISCHARGING'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CHARGING

```TypeScript
COMMON_EVENT_CHARGING = 'usual.event.CHARGING'
```

表示系统开始为电池充电的公共事件的动作。

当系统开始为电池充电时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_CHARGING = 'usual.event.CHARGING'--><!--Device-Support-COMMON_EVENT_CHARGING = 'usual.event.CHARGING'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED

```TypeScript
COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED = 'usual.event.DEVICE_IDLE_MODE_CHANGED'
```

表示设备上待机状态变化，触发公共事件发布动作。

如果用户一段时间没有使用设备且屏幕已经关闭情况下，系统延迟后台应用程序CPU和网络访问，将会触发公共事件服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED = 'usual.event.DEVICE_IDLE_MODE_CHANGED'--><!--Device-Support-COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED = 'usual.event.DEVICE_IDLE_MODE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CHARGE_IDLE_MODE_CHANGED

```TypeScript
COMMON_EVENT_CHARGE_IDLE_MODE_CHANGED = 'usual.event.CHARGE_IDLE_MODE_CHANGED'
```

表示设备进入充电空闲模式的公共事件的动作。

当设备处于空闲、正在充电并且温升可接受的一种状态时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_CHARGE_IDLE_MODE_CHANGED = 'usual.event.CHARGE_IDLE_MODE_CHANGED'--><!--Device-Support-COMMON_EVENT_CHARGE_IDLE_MODE_CHANGED = 'usual.event.CHARGE_IDLE_MODE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_POWER_SAVE_MODE_CHANGED

```TypeScript
COMMON_EVENT_POWER_SAVE_MODE_CHANGED = 'usual.event.POWER_SAVE_MODE_CHANGED'
```

表示系统节能模式更改的公共事件的动作。

当系统节能模式更改时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_POWER_SAVE_MODE_CHANGED = 'usual.event.POWER_SAVE_MODE_CHANGED'--><!--Device-Support-COMMON_EVENT_POWER_SAVE_MODE_CHANGED = 'usual.event.POWER_SAVE_MODE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_ADDED

```TypeScript
COMMON_EVENT_USER_ADDED = 'usual.event.USER_ADDED'
```

表示用户已添加到系统中的公共事件的动作。

创建系统账号将会触发事件通知服务发布该系统公共事件，事件携带系统账号ID。

与这个公共事件相关的接口：createOsAccount、createOsAccountForDomain, 这些为系统API，具体参看[@ohos.account.osAccount](../../../../reference/js-apis-osAccount.md)。

要订阅此事件，您的应用必须具备ohos.permission.MANAGE_LOCAL_ACCOUNTS权限（该权限仅系统应用可申请）

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USER_ADDED = 'usual.event.USER_ADDED'--><!--Device-Support-COMMON_EVENT_USER_ADDED = 'usual.event.USER_ADDED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_REMOVED

```TypeScript
COMMON_EVENT_USER_REMOVED = 'usual.event.USER_REMOVED'
```

表示用户已从系统中删除的公共事件的动作。

删除系统账号将会触发事件通知服务发布该系统公共事件，事件携带系统账号ID。

与这个公共事件相关的接口：removeOsAccount, 为系统API，具体参看[@ohos.account.osAccount](../../../../reference/js-apis-osAccount.md)。

要订阅此事件，您的应用必须具备ohos.permission.MANAGE_LOCAL_ACCOUNTS权限（该权限仅系统应用可申请）

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USER_REMOVED = 'usual.event.USER_REMOVED'--><!--Device-Support-COMMON_EVENT_USER_REMOVED = 'usual.event.USER_REMOVED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ABILITY_ADDED

```TypeScript
COMMON_EVENT_ABILITY_ADDED = 'common.event.ABILITY_ADDED'
```

（预留事件，暂未支持）表示已添加能力的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.LISTEN_BUNDLE_CHANGE权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_ABILITY_ADDED = 'common.event.ABILITY_ADDED'--><!--Device-Support-COMMON_EVENT_ABILITY_ADDED = 'common.event.ABILITY_ADDED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ABILITY_REMOVED

```TypeScript
COMMON_EVENT_ABILITY_REMOVED = 'common.event.ABILITY_REMOVED'
```

（预留事件，暂未支持）表示已删除能力的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.LISTEN_BUNDLE_CHANGE权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_ABILITY_REMOVED = 'common.event.ABILITY_REMOVED'--><!--Device-Support-COMMON_EVENT_ABILITY_REMOVED = 'common.event.ABILITY_REMOVED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ABILITY_UPDATED

```TypeScript
COMMON_EVENT_ABILITY_UPDATED = 'common.event.ABILITY_UPDATED'
```

（预留事件，暂未支持）表示能力已更新的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.LISTEN_BUNDLE_CHANGE权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_ABILITY_UPDATED = 'common.event.ABILITY_UPDATED'--><!--Device-Support-COMMON_EVENT_ABILITY_UPDATED = 'common.event.ABILITY_UPDATED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LOCATION_MODE_STATE_CHANGED

```TypeScript
COMMON_EVENT_LOCATION_MODE_STATE_CHANGED = 'usual.event.location.MODE_STATE_CHANGED'
```

（预留事件，暂未支持）表示系统定位模式已更改的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_LOCATION_MODE_STATE_CHANGED = 'usual.event.location.MODE_STATE_CHANGED'--><!--Device-Support-COMMON_EVENT_LOCATION_MODE_STATE_CHANGED = 'usual.event.location.MODE_STATE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_SLEEP

```TypeScript
COMMON_EVENT_IVI_SLEEP = 'common.event.IVI_SLEEP'
```

（预留事件，暂未支持）表示表示车辆的车载信息娱乐（IVI）系统正在休眠的常见事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_IVI_SLEEP = 'common.event.IVI_SLEEP'--><!--Device-Support-COMMON_EVENT_IVI_SLEEP = 'common.event.IVI_SLEEP'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_PAUSE

```TypeScript
COMMON_EVENT_IVI_PAUSE = 'common.event.IVI_PAUSE'
```

（预留事件，暂未支持）表示IVI已休眠，并通知应用程序停止播放。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_IVI_PAUSE = 'common.event.IVI_PAUSE'--><!--Device-Support-COMMON_EVENT_IVI_PAUSE = 'common.event.IVI_PAUSE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_STANDBY

```TypeScript
COMMON_EVENT_IVI_STANDBY = 'common.event.IVI_STANDBY'
```

（预留事件，暂未支持）表示第三方应用暂停当前工作的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_IVI_STANDBY = 'common.event.IVI_STANDBY'--><!--Device-Support-COMMON_EVENT_IVI_STANDBY = 'common.event.IVI_STANDBY'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_LASTMODE_SAVE

```TypeScript
COMMON_EVENT_IVI_LASTMODE_SAVE = 'common.event.IVI_LASTMODE_SAVE'
```

（预留事件，暂未支持）表示第三方应用保存其最后一个模式的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_IVI_LASTMODE_SAVE = 'common.event.IVI_LASTMODE_SAVE'--><!--Device-Support-COMMON_EVENT_IVI_LASTMODE_SAVE = 'common.event.IVI_LASTMODE_SAVE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_VOLTAGE_ABNORMAL

```TypeScript
COMMON_EVENT_IVI_VOLTAGE_ABNORMAL = 'common.event.IVI_VOLTAGE_ABNORMAL'
```

（预留事件，暂未支持）表示车辆电源系统电压异常的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_IVI_VOLTAGE_ABNORMAL = 'common.event.IVI_VOLTAGE_ABNORMAL'--><!--Device-Support-COMMON_EVENT_IVI_VOLTAGE_ABNORMAL = 'common.event.IVI_VOLTAGE_ABNORMAL'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_HIGH_TEMPERATURE

```TypeScript
COMMON_EVENT_IVI_HIGH_TEMPERATURE = 'common.event.IVI_HIGH_TEMPERATURE'
```

（预留事件，暂未支持）表示IVI温度过高。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_IVI_HIGH_TEMPERATURE = 'common.event.IVI_HIGH_TEMPERATURE'--><!--Device-Support-COMMON_EVENT_IVI_HIGH_TEMPERATURE = 'common.event.IVI_HIGH_TEMPERATURE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_EXTREME_TEMPERATURE

```TypeScript
COMMON_EVENT_IVI_EXTREME_TEMPERATURE = 'common.event.IVI_EXTREME_TEMPERATURE'
```

（预留事件，暂未支持）表示IVI温度极高。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_IVI_EXTREME_TEMPERATURE = 'common.event.IVI_EXTREME_TEMPERATURE'--><!--Device-Support-COMMON_EVENT_IVI_EXTREME_TEMPERATURE = 'common.event.IVI_EXTREME_TEMPERATURE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL

```TypeScript
COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL = 'common.event.IVI_TEMPERATURE_ABNORMAL'
```

（预留事件，暂未支持）表示车载系统具有极端温度的常见事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL = 'common.event.IVI_TEMPERATURE_ABNORMAL'--><!--Device-Support-COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL = 'common.event.IVI_TEMPERATURE_ABNORMAL'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_VOLTAGE_RECOVERY

```TypeScript
COMMON_EVENT_IVI_VOLTAGE_RECOVERY = 'common.event.IVI_VOLTAGE_RECOVERY'
```

（预留事件，暂未支持）表示车辆电源系统电压恢复正常的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_IVI_VOLTAGE_RECOVERY = 'common.event.IVI_VOLTAGE_RECOVERY'--><!--Device-Support-COMMON_EVENT_IVI_VOLTAGE_RECOVERY = 'common.event.IVI_VOLTAGE_RECOVERY'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_TEMPERATURE_RECOVERY

```TypeScript
COMMON_EVENT_IVI_TEMPERATURE_RECOVERY = 'common.event.IVI_TEMPERATURE_RECOVERY'
```

（预留事件，暂未支持）表示车载系统温度恢复正常的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_IVI_TEMPERATURE_RECOVERY = 'common.event.IVI_TEMPERATURE_RECOVERY'--><!--Device-Support-COMMON_EVENT_IVI_TEMPERATURE_RECOVERY = 'common.event.IVI_TEMPERATURE_RECOVERY'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_ACTIVE

```TypeScript
COMMON_EVENT_IVI_ACTIVE = 'common.event.IVI_ACTIVE'
```

（预留事件，暂未支持）表示电池服务处于活动状态的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_IVI_ACTIVE = 'common.event.IVI_ACTIVE'--><!--Device-Support-COMMON_EVENT_IVI_ACTIVE = 'common.event.IVI_ACTIVE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_STATE

```TypeScript
COMMON_EVENT_USB_STATE = 'usual.event.hardware.usb.action.USB_STATE'
```

表示USB设备状态发生变化。

当USB断开或者连接时状态发生变化，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USB_STATE = 'usual.event.hardware.usb.action.USB_STATE'--><!--Device-Support-COMMON_EVENT_USB_STATE = 'usual.event.hardware.usb.action.USB_STATE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_PORT_CHANGED

```TypeScript
COMMON_EVENT_USB_PORT_CHANGED = 'usual.event.hardware.usb.action.USB_PORT_CHANGED'
```

提示用户设备的USB端口状态发生改变。

当USB的端口状态发生变化，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USB_PORT_CHANGED = 'usual.event.hardware.usb.action.USB_PORT_CHANGED'--><!--Device-Support-COMMON_EVENT_USB_PORT_CHANGED = 'usual.event.hardware.usb.action.USB_PORT_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_DEVICE_ATTACHED

```TypeScript
COMMON_EVENT_USB_DEVICE_ATTACHED = 'usual.event.hardware.usb.action.USB_DEVICE_ATTACHED'
```

当用户设备作为USB主机时，提示USB设备已挂载。

当USB连接时状态发生变化，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USB_DEVICE_ATTACHED = 'usual.event.hardware.usb.action.USB_DEVICE_ATTACHED'--><!--Device-Support-COMMON_EVENT_USB_DEVICE_ATTACHED = 'usual.event.hardware.usb.action.USB_DEVICE_ATTACHED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_DEVICE_DETACHED

```TypeScript
COMMON_EVENT_USB_DEVICE_DETACHED = 'usual.event.hardware.usb.action.USB_DEVICE_DETACHED'
```

当用户设备作为USB主机时，提示USB设备被卸载。

当USB断开时状态发生变化，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USB_DEVICE_DETACHED = 'usual.event.hardware.usb.action.USB_DEVICE_DETACHED'--><!--Device-Support-COMMON_EVENT_USB_DEVICE_DETACHED = 'usual.event.hardware.usb.action.USB_DEVICE_DETACHED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_ACCESSORY_ATTACHED

```TypeScript
COMMON_EVENT_USB_ACCESSORY_ATTACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED'
```

表示已连接USB配件的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USB_ACCESSORY_ATTACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED'--><!--Device-Support-COMMON_EVENT_USB_ACCESSORY_ATTACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_ACCESSORY_DETACHED

```TypeScript
COMMON_EVENT_USB_ACCESSORY_DETACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED'
```

表示USB配件被卸载的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USB_ACCESSORY_DETACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED'--><!--Device-Support-COMMON_EVENT_USB_ACCESSORY_DETACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_REMOVED

```TypeScript
COMMON_EVENT_DISK_REMOVED = 'usual.event.data.DISK_REMOVED'
```

（预留事件，暂未支持）外部存储设备状态变更为移除时发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_DISK_REMOVED = 'usual.event.data.DISK_REMOVED'--><!--Device-Support-COMMON_EVENT_DISK_REMOVED = 'usual.event.data.DISK_REMOVED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_UNMOUNTED

```TypeScript
COMMON_EVENT_DISK_UNMOUNTED = 'usual.event.data.DISK_UNMOUNTED'
```

（预留事件，暂未支持）外部存储设备状态变更为卸载时发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_DISK_UNMOUNTED = 'usual.event.data.DISK_UNMOUNTED'--><!--Device-Support-COMMON_EVENT_DISK_UNMOUNTED = 'usual.event.data.DISK_UNMOUNTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_MOUNTED

```TypeScript
COMMON_EVENT_DISK_MOUNTED = 'usual.event.data.DISK_MOUNTED'
```

（预留事件，暂未支持）外部存储设备状态变更为挂载时发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_DISK_MOUNTED = 'usual.event.data.DISK_MOUNTED'--><!--Device-Support-COMMON_EVENT_DISK_MOUNTED = 'usual.event.data.DISK_MOUNTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_BAD_REMOVAL

```TypeScript
COMMON_EVENT_DISK_BAD_REMOVAL = 'usual.event.data.DISK_BAD_REMOVAL'
```

（预留事件，暂未支持）外部存储设备状态变更为挂载状态下移除时发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_DISK_BAD_REMOVAL = 'usual.event.data.DISK_BAD_REMOVAL'--><!--Device-Support-COMMON_EVENT_DISK_BAD_REMOVAL = 'usual.event.data.DISK_BAD_REMOVAL'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_UNMOUNTABLE

```TypeScript
COMMON_EVENT_DISK_UNMOUNTABLE = 'usual.event.data.DISK_UNMOUNTABLE'
```

（预留事件，暂未支持）外部存储设备状态变更为插卡情况下无法挂载时发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_DISK_UNMOUNTABLE = 'usual.event.data.DISK_UNMOUNTABLE'--><!--Device-Support-COMMON_EVENT_DISK_UNMOUNTABLE = 'usual.event.data.DISK_UNMOUNTABLE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_EJECT

```TypeScript
COMMON_EVENT_DISK_EJECT = 'usual.event.data.DISK_EJECT'
```

（预留事件，暂未支持）用户已表示希望删除外部存储介质时发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_DISK_EJECT = 'usual.event.data.DISK_EJECT'--><!--Device-Support-COMMON_EVENT_DISK_EJECT = 'usual.event.data.DISK_EJECT'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_REMOVED

```TypeScript
COMMON_EVENT_VOLUME_REMOVED = 'usual.event.data.VOLUME_REMOVED'
```

表示外部存储设备正常移除的公共事件。

当外部存储设备处于卸载状态，移除该设备时，会发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_VOLUME_REMOVED = 'usual.event.data.VOLUME_REMOVED'--><!--Device-Support-COMMON_EVENT_VOLUME_REMOVED = 'usual.event.data.VOLUME_REMOVED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_UNMOUNTED

```TypeScript
COMMON_EVENT_VOLUME_UNMOUNTED = 'usual.event.data.VOLUME_UNMOUNTED'
```

表示外部存储设备状态变更为卸载的公共事件。

当外部存储设备处于挂载状态时，用户选择通过调用unmount接口或者直接移除设备的方法弹出该设备，并且已将外部存储设备卸载成功后，会发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_VOLUME_UNMOUNTED = 'usual.event.data.VOLUME_UNMOUNTED'--><!--Device-Support-COMMON_EVENT_VOLUME_UNMOUNTED = 'usual.event.data.VOLUME_UNMOUNTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_MOUNTED

```TypeScript
COMMON_EVENT_VOLUME_MOUNTED = 'usual.event.data.VOLUME_MOUNTED'
```

表示外部存储设备状态变更为挂载的公共事件。

当用户插入外部存储设备自动挂载成功或者将处于卸载状态的外部存储设备调用mount接口进行挂载成功后，会发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_VOLUME_MOUNTED = 'usual.event.data.VOLUME_MOUNTED'--><!--Device-Support-COMMON_EVENT_VOLUME_MOUNTED = 'usual.event.data.VOLUME_MOUNTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_BAD_REMOVAL

```TypeScript
COMMON_EVENT_VOLUME_BAD_REMOVAL = 'usual.event.data.VOLUME_BAD_REMOVAL'
```

表示外部存储设备异常移除的公共事件。

当外部存储设备处于挂载状态时，用户直接移除该外部存储设备，会发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_VOLUME_BAD_REMOVAL = 'usual.event.data.VOLUME_BAD_REMOVAL'--><!--Device-Support-COMMON_EVENT_VOLUME_BAD_REMOVAL = 'usual.event.data.VOLUME_BAD_REMOVAL'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_EJECT

```TypeScript
COMMON_EVENT_VOLUME_EJECT = 'usual.event.data.VOLUME_EJECT'
```

表示外部存储设备即将被弹出的公共事件。

当外部存储设备处于挂载状态时，用户选择通过调用unmount接口或者直接移除设备的方法弹出该设备时，会发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_VOLUME_EJECT = 'usual.event.data.VOLUME_EJECT'--><!--Device-Support-COMMON_EVENT_VOLUME_EJECT = 'usual.event.data.VOLUME_EJECT'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED

```TypeScript
COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED = 'usual.event.data.VISIBLE_ACCOUNTS_UPDATED'
```

（预留事件，暂未支持）表示账户可见更改的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.GET_APP_ACCOUNTS权限（该权限仅系统应用可申请）。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED = 'usual.event.data.VISIBLE_ACCOUNTS_UPDATED'--><!--Device-Support-COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED = 'usual.event.data.VISIBLE_ACCOUNTS_UPDATED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ACCOUNT_DELETED

```TypeScript
COMMON_EVENT_ACCOUNT_DELETED = 'usual.event.data.ACCOUNT_DELETED'
```

（预留事件，暂未支持）删除账户的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限（该权限仅系统应用可申请）。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_ACCOUNT_DELETED = 'usual.event.data.ACCOUNT_DELETED'--><!--Device-Support-COMMON_EVENT_ACCOUNT_DELETED = 'usual.event.data.ACCOUNT_DELETED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_FOUNDATION_READY

```TypeScript
COMMON_EVENT_FOUNDATION_READY = 'common.event.FOUNDATION_READY'
```

（预留事件，暂未支持）表示foundation已准备好的公共事件的动作。

要订阅此事件，您的应用必须具备ohos.permission.RECEIVER_STARTUP_COMPLETED权限（该权限仅系统应用可申请）。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_FOUNDATION_READY = 'common.event.FOUNDATION_READY'--><!--Device-Support-COMMON_EVENT_FOUNDATION_READY = 'common.event.FOUNDATION_READY'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_AIRPLANE_MODE_CHANGED

```TypeScript
COMMON_EVENT_AIRPLANE_MODE_CHANGED = 'usual.event.AIRPLANE_MODE'
```

指示飞行模式状态变化。

在开启或者关闭系统飞行模式状态后，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_AIRPLANE_MODE_CHANGED = 'usual.event.AIRPLANE_MODE'--><!--Device-Support-COMMON_EVENT_AIRPLANE_MODE_CHANGED = 'usual.event.AIRPLANE_MODE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SPLIT_SCREEN

```TypeScript
COMMON_EVENT_SPLIT_SCREEN = 'common.event.SPLIT_SCREEN'
```

表示分屏行为的公共事件。

启动最近任务窗口、创建或销毁分屏条，都会触发通知服务发布这个系统公共事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Support-COMMON_EVENT_SPLIT_SCREEN = 'common.event.SPLIT_SCREEN'--><!--Device-Support-COMMON_EVENT_SPLIT_SCREEN = 'common.event.SPLIT_SCREEN'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SLOT_CHANGE

```TypeScript
COMMON_EVENT_SLOT_CHANGE = 'usual.event.SLOT_CHANGE'
```

表示通知渠道或通知开关发生变化。

通知设置里修改应用的渠道参数、渠道开关，或者开启、关闭通知使能开关时，都会触发通知服务发布这个系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.NOTIFICATION_CONTROLLER权限。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_SLOT_CHANGE = 'usual.event.SLOT_CHANGE'--><!--Device-Support-COMMON_EVENT_SLOT_CHANGE = 'usual.event.SLOT_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SPN_INFO_CHANGED

```TypeScript
COMMON_EVENT_SPN_INFO_CHANGED = 'usual.event.SPN_INFO_CHANGED'
```

表示spn显示信息已更新的公共事件的动作。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_SPN_INFO_CHANGED = 'usual.event.SPN_INFO_CHANGED'--><!--Device-Support-COMMON_EVENT_SPN_INFO_CHANGED = 'usual.event.SPN_INFO_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_QUICK_FIX_APPLY_RESULT

```TypeScript
COMMON_EVENT_QUICK_FIX_APPLY_RESULT = 'usual.event.QUICK_FIX_APPLY_RESULT'
```

表示快速修复应用。

在设备上指定用户快速修复应用，将会触发事件通知服务发布该系统公共事件。

> **说明：**  
>  
> 三方应用只能监听自身应用的快速修复事件。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_QUICK_FIX_APPLY_RESULT = 'usual.event.QUICK_FIX_APPLY_RESULT'--><!--Device-Support-COMMON_EVENT_QUICK_FIX_APPLY_RESULT = 'usual.event.QUICK_FIX_APPLY_RESULT'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_QUICK_FIX_REVOKE_RESULT

```TypeScript
COMMON_EVENT_QUICK_FIX_REVOKE_RESULT = 'usual.event.QUICK_FIX_REVOKE_RESULT'
```

表示撤销快速修复。

在设备上撤销快速修复时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_QUICK_FIX_REVOKE_RESULT = 'usual.event.QUICK_FIX_REVOKE_RESULT'--><!--Device-Support-COMMON_EVENT_QUICK_FIX_REVOKE_RESULT = 'usual.event.QUICK_FIX_REVOKE_RESULT'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_INFO_UPDATED

```TypeScript
COMMON_EVENT_USER_INFO_UPDATED = 'usual.event.USER_INFO_UPDATED'
```

表示用户信息已更新。

分布式账号信息变更、系统账号头像信息变更、系统账号名称变更将会触发事件通知服务发布该系统公共事件，事件携带系统账号ID。

与这个公共事件相关的接口：setOsAccountName、setOsAccountProfilePhoto, 这些为系统API，setOsAccountDistributedInfo为公共API，具体参看[系统账号接口文档](../../../../reference/js-apis-osAccount.md)、[分布式账号接口文档](../../../../reference/js-apis-distributed-account.md)。

**起始版本：** 9

<!--Device-Support-COMMON_EVENT_USER_INFO_UPDATED = 'usual.event.USER_INFO_UPDATED'--><!--Device-Support-COMMON_EVENT_USER_INFO_UPDATED = 'usual.event.USER_INFO_UPDATED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HTTP_PROXY_CHANGE

```TypeScript
COMMON_EVENT_HTTP_PROXY_CHANGE = 'usual.event.HTTP_PROXY_CHANGE'
```

指示网络Http代理配置信息更新。

在系统全局代理或者各类网络（以太网、Wi-Fi、蜂窝等）Http代理配置信息发生变化时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_HTTP_PROXY_CHANGE = 'usual.event.HTTP_PROXY_CHANGE'--><!--Device-Support-COMMON_EVENT_HTTP_PROXY_CHANGE = 'usual.event.HTTP_PROXY_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SIM_STATE_CHANGED

```TypeScript
COMMON_EVENT_SIM_STATE_CHANGED = 'usual.event.SIM_STATE_CHANGED'
```

提示SIM卡状态更新。

在设备上面的SIM卡状态发生变化时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_SIM_STATE_CHANGED = 'usual.event.SIM_STATE_CHANGED'--><!--Device-Support-COMMON_EVENT_SIM_STATE_CHANGED = 'usual.event.SIM_STATE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CALL_STATE_CHANGED

```TypeScript
COMMON_EVENT_CALL_STATE_CHANGED = 'usual.event.CALL_STATE_CHANGED'
```

提示呼叫状态更新。

在设备呼叫状态更新时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.GET_TELEPHONY_STATE权限（该权限仅系统应用可申请）。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_CALL_STATE_CHANGED = 'usual.event.CALL_STATE_CHANGED'--><!--Device-Support-COMMON_EVENT_CALL_STATE_CHANGED = 'usual.event.CALL_STATE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NETWORK_STATE_CHANGED

```TypeScript
COMMON_EVENT_NETWORK_STATE_CHANGED = 'usual.event.NETWORK_STATE_CHANGED'
```

提示网络状态更新。

在设备网络状态更新时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_NETWORK_STATE_CHANGED = 'usual.event.NETWORK_STATE_CHANGED'--><!--Device-Support-COMMON_EVENT_NETWORK_STATE_CHANGED = 'usual.event.NETWORK_STATE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SIGNAL_INFO_CHANGED

```TypeScript
COMMON_EVENT_SIGNAL_INFO_CHANGED = 'usual.event.SIGNAL_INFO_CHANGED'
```

提示信号信息更新。

在设备信号信息更新时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_SIGNAL_INFO_CHANGED = 'usual.event.SIGNAL_INFO_CHANGED'--><!--Device-Support-COMMON_EVENT_SIGNAL_INFO_CHANGED = 'usual.event.SIGNAL_INFO_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SCREEN_UNLOCKED

```TypeScript
COMMON_EVENT_SCREEN_UNLOCKED = 'usual.event.SCREEN_UNLOCKED'
```

表示屏幕解锁的公共事件。

当锁屏解锁时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Support-COMMON_EVENT_SCREEN_UNLOCKED = 'usual.event.SCREEN_UNLOCKED'--><!--Device-Support-COMMON_EVENT_SCREEN_UNLOCKED = 'usual.event.SCREEN_UNLOCKED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SCREEN_LOCKED

```TypeScript
COMMON_EVENT_SCREEN_LOCKED = 'usual.event.SCREEN_LOCKED'
```

表示屏幕锁定的公共事件。

当锁屏锁定时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Support-COMMON_EVENT_SCREEN_LOCKED = 'usual.event.SCREEN_LOCKED'--><!--Device-Support-COMMON_EVENT_SCREEN_LOCKED = 'usual.event.SCREEN_LOCKED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CONNECTIVITY_CHANGE

```TypeScript
COMMON_EVENT_CONNECTIVITY_CHANGE = 'usual.event.CONNECTIVITY_CHANGE'
```

指示网络连接状态变化。

各类网络（以太网、Wi-Fi、蜂窝等）在发生连接状态状态变化时（断开、断开中、连接中、已连接等），将会触发事件通知服务发布该系统公共事件。

具体枚举值及其对应的连接状态如下表所示：

> **说明**  
> 具体枚举值及其对应的连接状态如下表所示：  
>  
> | 枚举值 | 连接状态 |  
> | ------ | ---------- |  
> | 2 | 连接中 |  
> | 3 | 已连接 |  
> | 4 | 正在断开 |  
> | 5 | 已断开 |。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Support-COMMON_EVENT_CONNECTIVITY_CHANGE = 'usual.event.CONNECTIVITY_CHANGE'--><!--Device-Support-COMMON_EVENT_CONNECTIVITY_CHANGE = 'usual.event.CONNECTIVITY_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_CHANGE =
        'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_CHANGE'
```

表示蓝牙HFP AG连接状态变化的公共事件的操作。

当蓝牙HFP AG连接状态变化时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_CHANGE =
        'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_CHANGE =
        'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MINORSMODE_ON

```TypeScript
COMMON_EVENT_MINORSMODE_ON = 'usual.event.MINORSMODE_ON'
```

表示用户开启未成年人模式。

在设备上开启未成年人模式，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Support-COMMON_EVENT_MINORSMODE_ON = 'usual.event.MINORSMODE_ON'--><!--Device-Support-COMMON_EVENT_MINORSMODE_ON = 'usual.event.MINORSMODE_ON'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MINORSMODE_OFF

```TypeScript
COMMON_EVENT_MINORSMODE_OFF = 'usual.event.MINORSMODE_OFF'
```

表示用户关闭未成年人模式。

在设备上关闭未成年人模式，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Support-COMMON_EVENT_MINORSMODE_OFF = 'usual.event.MINORSMODE_OFF'--><!--Device-Support-COMMON_EVENT_MINORSMODE_OFF = 'usual.event.MINORSMODE_OFF'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DATA_SHARE_READY

```TypeScript
COMMON_EVENT_DATA_SHARE_READY = 'usual.event.DATA_SHARE_READY'
```

表示datashare服务可用。

datashare服务启动完成后，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Support-COMMON_EVENT_DATA_SHARE_READY = 'usual.event.DATA_SHARE_READY'--><!--Device-Support-COMMON_EVENT_DATA_SHARE_READY = 'usual.event.DATA_SHARE_READY'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_CHANGE =
        'usual.event.bluetooth.a2dpsource.CONNECT_STATE_CHANGE'
```

表示蓝牙A2DP Source连接状态变化的公共事件的操作。

当蓝牙A2DP Source连接状态变化时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_CHANGE =
        'usual.event.bluetooth.a2dpsource.CONNECT_STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_CHANGE =
        'usual.event.bluetooth.a2dpsource.CONNECT_STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_CHANGE =
        'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_CHANGE'
```

表示蓝牙AVRCP连接状态变化的公共事件的操作。

当蓝牙AVRCP连接状态变化时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_CHANGE =
        'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_CHANGE =
        'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_CHANGE =
        'usual.event.bluetooth.a2dpsource.CODEC_VALUE_CHANGE'
```

表示蓝牙媒体编解码器变化的公共事件的操作。

当蓝牙媒体编解码器变化时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_CHANGE =
        'usual.event.bluetooth.a2dpsource.CODEC_VALUE_CHANGE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_CHANGE =
        'usual.event.bluetooth.a2dpsource.CODEC_VALUE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAY_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAY_STATE_CHANGE =
        'usual.event.bluetooth.a2dpsource.PLAY_STATE_CHANGE'
```

表示蓝牙媒体A2DP播放状态变化的公共事件的操作。

当蓝牙媒体A2DP播放状态变化时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAY_STATE_CHANGE =
        'usual.event.bluetooth.a2dpsource.PLAY_STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAY_STATE_CHANGE =
        'usual.event.bluetooth.a2dpsource.PLAY_STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_SCO_CONNECT_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_SCO_CONNECT_STATE_CHANGE = 
        'usual.event.bluetooth.SCO_CONNECT_STATE_CHANGE'
```

表示蓝牙SCO状态变化的公共事件的操作。

当蓝牙SCO状态变化时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_BLUETOOTH_SCO_CONNECT_STATE_CHANGE = 
        'usual.event.bluetooth.SCO_CONNECT_STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_SCO_CONNECT_STATE_CHANGE = 
        'usual.event.bluetooth.SCO_CONNECT_STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE = 
        'usual.event.bluetooth.remotedevice.ACL_STATE_CHANGE'
```

表示蓝牙远程设备ACL连接状态变化的公共事件的操作。

当蓝牙远程设备ACL连接状态变化时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE = 
        'usual.event.bluetooth.remotedevice.ACL_STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE = 
        'usual.event.bluetooth.remotedevice.ACL_STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE_CHANGE =
        'usual.event.bluetooth.remotedevice.PAIR_STATE_CHANGE'
```

表示蓝牙配对状态变化的公共事件的操作。

当蓝牙配对状态变化时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE_CHANGE =
        'usual.event.bluetooth.remotedevice.PAIR_STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE_CHANGE =
        'usual.event.bluetooth.remotedevice.PAIR_STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MANAGED_BROWSER_POLICY_CHANGED

```TypeScript
COMMON_EVENT_MANAGED_BROWSER_POLICY_CHANGED = 'usual.event.MANAGED_BROWSER_POLICY_CHANGED'
```

表示浏览器托管策略已更改。

当浏览器托管策略发生变化，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 15

<!--Device-Support-COMMON_EVENT_MANAGED_BROWSER_POLICY_CHANGED = 'usual.event.MANAGED_BROWSER_POLICY_CHANGED'--><!--Device-Support-COMMON_EVENT_MANAGED_BROWSER_POLICY_CHANGED = 'usual.event.MANAGED_BROWSER_POLICY_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_KIOSK_MODE_ON

```TypeScript
COMMON_EVENT_KIOSK_MODE_ON = 'usual.event.KIOSK_MODE_ON'
```

进入Kiosk模式时，事件通知服务将触发并发布系统公共事件。此事件仅由系统发送。

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_KIOSK_MODE_ON = 'usual.event.KIOSK_MODE_ON'--><!--Device-Support-COMMON_EVENT_KIOSK_MODE_ON = 'usual.event.KIOSK_MODE_ON'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_KIOSK_MODE_OFF

```TypeScript
COMMON_EVENT_KIOSK_MODE_OFF = 'usual.event.KIOSK_MODE_OFF'
```

退出Kiosk模式时，事件通知服务将触发并发布系统公共事件。

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_KIOSK_MODE_OFF = 'usual.event.KIOSK_MODE_OFF'--><!--Device-Support-COMMON_EVENT_KIOSK_MODE_OFF = 'usual.event.KIOSK_MODE_OFF'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TABLET_MODE_CHANGED

```TypeScript
COMMON_EVENT_TABLET_MODE_CHANGED = 'usual.event.TABLET_MODE_CHANGED'
```

表示可感知支架开合的设备，例如具有支架的平板电脑，其支架开合状态变化时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 23

<!--Device-Support-COMMON_EVENT_TABLET_MODE_CHANGED = 'usual.event.TABLET_MODE_CHANGED'--><!--Device-Support-COMMON_EVENT_TABLET_MODE_CHANGED = 'usual.event.TABLET_MODE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LID_STATE_CHANGED

```TypeScript
COMMON_EVENT_LID_STATE_CHANGED = 'usual.event.LID_STATE_CHANGED'
```

表示可感知开合盖子的设备，例如具有开合盖子的笔记本电脑，其开合盖状态变化时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 23

<!--Device-Support-COMMON_EVENT_LID_STATE_CHANGED = 'usual.event.LID_STATE_CHANGED'--><!--Device-Support-COMMON_EVENT_LID_STATE_CHANGED = 'usual.event.LID_STATE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_DECRYPTED

```TypeScript
COMMON_EVENT_VOLUME_DECRYPTED = 'usual.event.VOLUME_DECRYPTED'
```

表示设备上的特定卷已被解密。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_VOLUME_DECRYPTED = 'usual.event.VOLUME_DECRYPTED'--><!--Device-Support-COMMON_EVENT_VOLUME_DECRYPTED = 'usual.event.VOLUME_DECRYPTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_ENCRYPTED

```TypeScript
COMMON_EVENT_VOLUME_ENCRYPTED = 'usual.event.VOLUME_ENCRYPTED'
```

表示设备上的特定卷已被加密。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_VOLUME_ENCRYPTED = 'usual.event.VOLUME_ENCRYPTED'--><!--Device-Support-COMMON_EVENT_VOLUME_ENCRYPTED = 'usual.event.VOLUME_ENCRYPTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_ENCRYPTION_POLICY_SET

```TypeScript
COMMON_EVENT_VOLUME_ENCRYPTION_POLICY_SET = 'usual.event.VOLUME_ENCRYPTION_POLICY_SET'
```

表示设备上的特定卷已设置其加密策略。

要订阅此事件，您的应用必须具备ohos.permission.QUERY_VOLUME_ENCRYPTION_STATUS权限.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_VOLUME_ENCRYPTION_POLICY_SET = 'usual.event.VOLUME_ENCRYPTION_POLICY_SET'--><!--Device-Support-COMMON_EVENT_VOLUME_ENCRYPTION_POLICY_SET = 'usual.event.VOLUME_ENCRYPTION_POLICY_SET'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

