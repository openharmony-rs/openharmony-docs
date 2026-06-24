# @ohos.power

该模块主要提供重启、关机、查询屏幕状态等接口。开发者可以使用该模块的接口获取设备的活动状态、电源模式、亮灭屏状态等。

**起始版本：** 7

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[getPowerConfig](arkts-basicservices-power-getpowerconfig-f-sys.md#getPowerConfig-1) | 按场景名称查询电源配置值。<br/> |
| [getPowerMode](arkts-basicservices-power-getpowermode-f.md#getPowerMode-1) | 获取当前设备的电源模式。<br/> |
| <!--DelRow-->[hibernate](arkts-basicservices-power-hibernate-f-sys.md#hibernate-1) | 休眠设备。<br/> |
| [isActive](arkts-basicservices-power-isactive-f.md#isActive-1) | 检测当前设备是否处于活动状态。<br/><br/>- 有屏的设备亮屏时为活动状态，熄屏时为非活动状态。<br/>- 无屏的设备非休眠时为活动状态，休眠时为非活动状态。<br/> |
| [isScreenOn](arkts-basicservices-power-isscreenon-f.md#isScreenOn-1) | 检测当前设备的亮灭屏状态。使用callback异步回调。<br/> |
| [isScreenOn](arkts-basicservices-power-isscreenon-f.md#isScreenOn-2) | 检测当前设备的亮灭屏状态。使用Promise异步回调。<br/> |
| [isStandby](arkts-basicservices-power-isstandby-f.md#isStandby-1) | 检测当前设备是否进入待机低功耗续航模式。<br/> |
| <!--DelRow-->[reboot](arkts-basicservices-power-reboot-f-sys.md#reboot-1) | 重启设备。<br/> |
| [rebootDevice](arkts-basicservices-power-rebootdevice-f.md#rebootDevice-1) | 重启系统。<br/> |
| <!--DelRow-->[refreshActivity](arkts-basicservices-power-refreshactivity-f-sys.md#refreshActivity-1) | 刷新设备活动状态（如：重设屏幕超时息屏时间等）。<br/><br/>只有设备在活动状态下生效，设备活动状态见[power.isActive](arkts-basicservices-power-isactive-f.md#isActive-1)接口。<br/> |
| <!--DelRow-->[registerShutdownCallback](arkts-basicservices-power-registershutdowncallback-f-sys.md#registerShutdownCallback-1) | 订阅电源关机或重启的回调提醒。使用callback异步回调。<br/> |
| <!--DelRow-->[setPowerConfig](arkts-basicservices-power-setpowerconfig-f-sys.md#setPowerConfig-1) | 根据场景名称设置电源配置值。<br/> |
| <!--DelRow-->[setPowerKeyFilteringStrategy](arkts-basicservices-power-setpowerkeyfilteringstrategy-f-sys.md#setPowerKeyFilteringStrategy-1) | 设置电源键过滤策略，在电源服务订阅电源键事件后，用于配置电源键事件的处理方式。<br/><br/>电源键过滤策略见[power.PowerKeyFilteringStrategy](arkts-basicservices-power-powerkeyfilteringstrategy-e.md#PowerKeyFilteringStrategy)接口。<br/> |
| <!--DelRow-->[setPowerMode](arkts-basicservices-power-setpowermode-f-sys.md#setPowerMode-1) | 设置当前设备的电源模式。使用callback异步回调。<br/> |
| <!--DelRow-->[setPowerMode](arkts-basicservices-power-setpowermode-f-sys.md#setPowerMode-2) | 设置当前设备的电源模式。使用Promise异步回调。<br/> |
| <!--DelRow-->[setScreenOffTime](arkts-basicservices-power-setscreenofftime-f-sys.md#setScreenOffTime-1) | 设置熄屏超时时间。<br/> |
| <!--DelRow-->[shutdown](arkts-basicservices-power-shutdown-f-sys.md#shutdown-1) | 系统关机。<br/> |
| <!--DelRow-->[suspend](arkts-basicservices-power-suspend-f-sys.md#suspend-1) | 使设备进入睡眠状态。<br/> |
| <!--DelRow-->[unregisterShutdownCallback](arkts-basicservices-power-unregistershutdowncallback-f-sys.md#unregisterShutdownCallback-1) | 取消订阅电源关机或重启的回调提醒。使用callback同步回调。<br/> |
| <!--DelRow-->[wakeup](arkts-basicservices-power-wakeup-f-sys.md#wakeup-1) | 唤醒设备。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DevicePowerMode](arkts-basicservices-power-devicepowermode-e.md) | 表示电源模式的枚举值。<br/> |
| [PowerKeyFilteringStrategy](arkts-basicservices-power-powerkeyfilteringstrategy-e.md) | 表示电源键过滤策略。<br/> |

