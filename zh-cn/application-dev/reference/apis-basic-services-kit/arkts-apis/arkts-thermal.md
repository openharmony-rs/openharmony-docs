# @ohos.thermal

该模块提供热管理相关的接口，包括热档位查询及注册回调等功能。系统根据设备温度阈值将热状态划分为多个档位层级（参见[ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md)）， 当设备温度跨越档位阈值时触发回调通知，开发者可根据档位等级执行相应的业务降级策略。

**起始版本：** 23

<!--Device-unnamed-declare namespace thermal--><!--Device-unnamed-declare namespace thermal-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

## 导入模块

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getLevel](arkts-basicservices-thermal-getlevel-f.md) | 获取当前热档位信息。系统根据设备温度实时判定当前所处的热档位层级并返回对应等级，开发者可据此执行相应的业务降级策略。 |
| [getThermalLevel](arkts-basicservices-thermal-getthermallevel-f.md) | 获取当前热档位信息。 |
| [registerThermalLevelCallback](arkts-basicservices-thermal-registerthermallevelcallback-f.md) | 订阅热档位变化时的回调提醒。当设备温度跨越档位阈值导致热档位发生变化时，系统自动触发回调通知， 通过callback返回变化后的热档位等级。使用callback异步回调。此方法与thermal.unregisterThermalLevelCallback配对使用， 用于取消先前注册的热档位回调。 |
| [subscribeThermalLevel](arkts-basicservices-thermal-subscribethermallevel-f.md) | 订阅热档位变化时的回调提醒。使用callback异步回调。此方法需与thermal.unsubscribeThermalLevel配对使用，在不再需要监听时取消订阅。 |
| [unregisterThermalLevelCallback](arkts-basicservices-thermal-unregisterthermallevelcallback-f.md) | 取消订阅热档位变化时的回调提醒。使用callback异步回调。此方法与thermal.registerThermalLevelCallback配对使用，用于取消先前注册的热档位回调。 |
| [unsubscribeThermalLevel](arkts-basicservices-thermal-unsubscribethermallevel-f.md) | 取消订阅热档位变化时的回调提醒。使用callback异步回调。此方法与thermal.subscribeThermalLevel配对使用，用于取消先前订阅的热档位回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md) | 热档位信息。热档位从COOL到ESCAPE逐级递进，各级别对应的设备状态与业务动作建议如下表所示。 |

