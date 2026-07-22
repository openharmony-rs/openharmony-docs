# @ohos.power

该模块主要提供重启、关机、查询屏幕状态等接口。开发者可以使用该模块的接口获取设备的活动状态、电源模式、亮灭屏状态等。

**起始版本：** 7

<!--Device-unnamed-declare namespace power--><!--Device-unnamed-declare namespace power-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getPowerMode](arkts-basicservices-power-getpowermode-f.md#getpowermode) | 获取当前设备的电源模式。 |
| [isActive](arkts-basicservices-power-isactive-f.md#isactive) | 检测当前设备是否处于活动状态。  - 有屏的设备亮屏时为活动状态，熄屏时为非活动状态。  - 无屏的设备非休眠时为活动状态，休眠时为非活动状态。 |
| [isScreenOn](arkts-basicservices-power-isscreenon-f.md#isscreenon) | 检测当前设备的亮灭屏状态。使用callback异步回调。 |
| [isScreenOn](arkts-basicservices-power-isscreenon-f.md#isscreenon-1) | 检测当前设备的亮灭屏状态。使用Promise异步回调。 |
| [isStandby](arkts-basicservices-power-isstandby-f.md#isstandby) | 检测当前设备是否进入待机低功耗续航模式。 |
| [rebootDevice](arkts-basicservices-power-rebootdevice-f.md#rebootdevice) | 重启系统。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getPowerConfig](arkts-basicservices-power-getpowerconfig-f-sys.md#getpowerconfig) | 按场景名称查询电源配置值。 |
| [hibernate](arkts-basicservices-power-hibernate-f-sys.md#hibernate) | 休眠设备。 |
| [reboot](arkts-basicservices-power-reboot-f-sys.md#reboot) | 重启设备。 |
| [refreshActivity](arkts-basicservices-power-refreshactivity-f-sys.md#refreshactivity) | 刷新设备活动状态（如：重设屏幕超时息屏时间等）。  只有设备在活动状态下生效，设备活动状态见[power.isActive](arkts-basicservices-power-isactive-f.md#isactive)接口。 |
| [registerShutdownCallback](arkts-basicservices-power-registershutdowncallback-f-sys.md#registershutdowncallback) | 订阅电源关机或重启的回调提醒。使用callback异步回调。 |
| [setPowerConfig](arkts-basicservices-power-setpowerconfig-f-sys.md#setpowerconfig) | 根据场景名称设置电源配置值。 |
| [setPowerKeyFilteringStrategy](arkts-basicservices-power-setpowerkeyfilteringstrategy-f-sys.md#setpowerkeyfilteringstrategy) | 设置电源键过滤策略，在电源服务订阅电源键事件后，用于配置电源键事件的处理方式。  电源键过滤策略见[power.PowerKeyFilteringStrategy](arkts-basicservices-power-powerkeyfilteringstrategy-e.md)接口。 |
| [setPowerMode](arkts-basicservices-power-setpowermode-f-sys.md#setpowermode) | 设置当前设备的电源模式。使用callback异步回调。 |
| [setPowerMode](arkts-basicservices-power-setpowermode-f-sys.md#setpowermode-1) | 设置当前设备的电源模式。使用Promise异步回调。 |
| [setScreenOffTime](arkts-basicservices-power-setscreenofftime-f-sys.md#setscreenofftime) | 设置熄屏超时时间。 |
| [shutdown](arkts-basicservices-power-shutdown-f-sys.md#shutdown) | 系统关机。 |
| [suspend](arkts-basicservices-power-suspend-f-sys.md#suspend) | 使设备进入睡眠状态。 |
| [unregisterShutdownCallback](arkts-basicservices-power-unregistershutdowncallback-f-sys.md#unregistershutdowncallback) | 取消订阅电源关机或重启的回调提醒。使用callback同步回调。 |
| [wakeup](arkts-basicservices-power-wakeup-f-sys.md#wakeup) | 唤醒设备。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DevicePowerMode](arkts-basicservices-power-devicepowermode-e.md) | 表示电源模式的枚举值。 |
| [PowerKeyFilteringStrategy](arkts-basicservices-power-powerkeyfilteringstrategy-e.md) | 表示电源键过滤策略。 |

