# @ohos.power

该模块主要提供重启、关机、查询屏幕状态等接口。开发者可以使用该模块的接口获取设备的活动状态、电源模式、亮灭屏状态等。

**起始版本：** 7

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getPowerMode](arkts-basicservices-getpowermode-f.md#getpowermode-1) | 获取当前设备的电源模式。 |
| [isActive](arkts-basicservices-isactive-f.md#isactive-1) | 检测当前设备是否处于活动状态。- 有屏的设备亮屏时为活动状态，熄屏时为非活动状态。- 无屏的设备非休眠时为活动状态，休眠时为非活动状态。 |
| [isScreenOn](arkts-basicservices-isscreenon-f.md#isscreenon-1) | 检测当前设备的亮灭屏状态。使用callback异步回调。 |
| [isScreenOn](arkts-basicservices-isscreenon-f.md#isscreenon-2) | 检测当前设备的亮灭屏状态。使用Promise异步回调。 |
| [isStandby](arkts-basicservices-isstandby-f.md#isstandby-1) | 检测当前设备是否进入待机低功耗续航模式。 |
| [rebootDevice](arkts-basicservices-rebootdevice-f.md#rebootdevice-1) | 重启系统。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getPowerConfig](arkts-basicservices-getpowerconfig-f-sys.md#getpowerconfig-1) | 按场景名称查询电源配置值。 |
| [hibernate](arkts-basicservices-hibernate-f-sys.md#hibernate-1) | 休眠设备。 |
| [reboot](arkts-basicservices-reboot-f-sys.md#reboot-1) | 重启设备。 |
| [refreshActivity](arkts-basicservices-refreshactivity-f-sys.md#refreshactivity-1) | 刷新设备活动状态（如：重设屏幕超时息屏时间等）。只有设备在活动状态下生效，设备活动状态见[power.isActive](arkts-basicservices-isactive-f.md#isactive-1)接口。 |
| [registerShutdownCallback](arkts-basicservices-registershutdowncallback-f-sys.md#registershutdowncallback-1) | 订阅电源关机或重启的回调提醒。使用callback异步回调。 |
| [setPowerConfig](arkts-basicservices-setpowerconfig-f-sys.md#setpowerconfig-1) | 根据场景名称设置电源配置值。 |
| [setPowerKeyFilteringStrategy](arkts-basicservices-setpowerkeyfilteringstrategy-f-sys.md#setpowerkeyfilteringstrategy-1) | 设置电源键过滤策略，在电源服务订阅电源键事件后，用于配置电源键事件的处理方式。电源键过滤策略见[power.PowerKeyFilteringStrategy](arkts-basicservices-powerkeyfilteringstrategy-e.md)接口。 |
| [setPowerMode](arkts-basicservices-setpowermode-f-sys.md#setpowermode-1) | 设置当前设备的电源模式。使用callback异步回调。 |
| [setPowerMode](arkts-basicservices-setpowermode-f-sys.md#setpowermode-2) | 设置当前设备的电源模式。使用Promise异步回调。 |
| [setScreenOffTime](arkts-basicservices-setscreenofftime-f-sys.md#setscreenofftime-1) | 设置熄屏超时时间。 |
| [shutdown](arkts-basicservices-shutdown-f-sys.md#shutdown-1) | 系统关机。 |
| [suspend](arkts-basicservices-suspend-f-sys.md#suspend-1) | 使设备进入睡眠状态。 |
| [unregisterShutdownCallback](arkts-basicservices-unregistershutdowncallback-f-sys.md#unregistershutdowncallback-1) | 取消订阅电源关机或重启的回调提醒。使用callback同步回调。 |
| [wakeup](arkts-basicservices-wakeup-f-sys.md#wakeup-1) | 唤醒设备。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DevicePowerMode](arkts-basicservices-devicepowermode-e.md) | 表示电源模式的枚举值。 |
| [PowerKeyFilteringStrategy](arkts-basicservices-powerkeyfilteringstrategy-e.md) | 表示电源键过滤策略。 |

