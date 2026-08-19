# @ohos.power

该模块主要提供查询屏幕状态、查询电源模式、检测待机模式等接口，还提供电源键过滤策略的配置能力。 开发者可以使用该模块的接口获取设备的活动状态、电源模式、亮灭屏状态、待机低功耗状态等，适用于需要根据设备电源状态进行业务逻辑调整的场景， 例如在低功耗模式下限制后台活动、在待机模式下优化续航策略等。

**起始版本：** 23

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
| [getPowerMode](arkts-basicservices-power-getpowermode-f.md) | 获取当前设备的电源模式。不同电源模式对应不同的设备行为策略，开发者可根据返回的模式值调整应用行为以适配当前模式。各模式定义及说明请参见DevicePowerMode。 |
| [isActive](arkts-basicservices-power-isactive-f.md) | 检测当前设备是否处于活动状态。可用于应用根据设备活动状态调整行为，例如在设备非活动状态下暂停后台任务等。 - 有屏的设备亮屏时为活动状态，灭屏时为非活动状态。 - 无屏的设备非休眠时为活动状态，休眠时为非活动状态。 |
| [isScreenOn](arkts-basicservices-power-isscreenon-f.md) | 检测当前设备的亮灭屏状态。使用callback异步回调。 |
| [isScreenOn](arkts-basicservices-power-isscreenon-f.md) | 检测当前设备的亮灭屏状态。使用Promise异步回调。 |
| [isStandby](arkts-basicservices-power-isstandby-f.md) | 检测当前设备是否进入待机低功耗续航模式。待机模式下系统会采取降低功耗的策略，开发者应据此调整应用的后台任务和资源使用策略，避免在待机时执行高耗能操作。 |
| [rebootDevice](arkts-basicservices-power-rebootdevice-f.md) | 重启设备。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getPowerConfig](arkts-basicservices-power-getpowerconfig-f-sys.md) | 按场景名称查询电源配置值。例如，在系统电源管理应用中需要读取特定场景的电源配置参数时使用。 |
| [hibernate](arkts-basicservices-power-hibernate-f-sys.md) | 休眠设备。<br><br>与suspend方法的区别：hibernate为更深的休眠状态（休眠前可选择清理内存），suspend为较浅的低功耗睡眠状态（灭屏后进入睡眠）。 需最大程度节省电量时选择hibernate，需快速恢复设备活动时选择suspend。适用于设备长时间闲置需要深度节能的场景。 |
| [reboot](arkts-basicservices-power-reboot-f-sys.md) | 重启设备。 |
| [refreshActivity](arkts-basicservices-power-refreshactivity-f-sys.md) | 刷新设备活动状态（如：重设屏幕超时灭屏时间等）。<br><br>此接口仅在设备活动状态下生效。 |
| [registerShutdownCallback](arkts-basicservices-power-registershutdowncallback-f-sys.md) | 订阅电源关机或重启的回调提醒。使用callback异步回调。调用此方法订阅回调后，可在不再需要时调用power.unregisterShutdownCallback取消订阅，释放系统资源。 |
| [setPowerConfig](arkts-basicservices-power-setpowerconfig-f-sys.md) | 根据场景名称设置电源配置值。例如，在系统电源管理应用中需要动态调整特定场景的电源配置参数时使用。 |
| [setPowerKeyFilteringStrategy](arkts-basicservices-power-setpowerkeyfilteringstrategy-f-sys.md) | 设置电源键过滤策略，在电源服务订阅电源键事件后，用于配置电源键事件的处理方式。 电源键过滤策略见[power.PowerKeyFilteringStrategy](arkts-basicservices-power-powerkeyfilteringstrategy-e.md)接口。 |
| [setPowerMode](arkts-basicservices-power-setpowermode-f-sys.md) | 设置当前设备的电源模式，不同的电源模式会影响设备的性能与功耗策略。使用callback异步回调。 |
| [setPowerMode](arkts-basicservices-power-setpowermode-f-sys.md) | 设置当前设备的电源模式，不同的电源模式会影响设备的性能与功耗策略。使用Promise异步回调。 |
| [setScreenOffTime](arkts-basicservices-power-setscreenofftime-f-sys.md) | 设置灭屏超时时间。例如，在自助终端或展示设备场景下可设置较长的超时时间以保持屏幕常亮，在低电量场景下可设置较短的超时时间以节省电量。 |
| [shutdown](arkts-basicservices-power-shutdown-f-sys.md) | 系统关机。与reboot方法的区别：shutdown使设备完全关机不再运行，reboot使设备关机后自动重启。 |
| [suspend](arkts-basicservices-power-suspend-f-sys.md) | 使设备进入睡眠状态。<br><br>调用此方法后设备将进入睡眠，如需恢复到活动状态，需调用power.wakeup唤醒设备。<br><br>与hibernate方法的区别：suspend为较浅的低功耗睡眠状态（灭屏后进入睡眠）， hibernate为更深的休眠状态（休眠前可选择清理内存）。需快速恢复设备活动时选择suspend，需最大程度节省电量时选择hibernate。 |
| [unregisterShutdownCallback](arkts-basicservices-power-unregistershutdowncallback-f-sys.md) | 取消订阅电源关机或重启的回调提醒。使用callback同步回调。 此方法与power.registerShutdownCallback配对使用，必须在先调用registerShutdownCallback订阅回调后，再调用此方法取消订阅。 |
| [wakeup](arkts-basicservices-power-wakeup-f-sys.md) | 唤醒设备，将设备从睡眠状态恢复到活动状态。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DevicePowerMode](arkts-basicservices-power-devicepowermode-e.md) | 表示电源模式的枚举值。 |
| [PowerKeyFilteringStrategy](arkts-basicservices-power-powerkeyfilteringstrategy-e.md) | 表示电源键过滤策略。 |

