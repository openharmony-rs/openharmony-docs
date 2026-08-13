# @ohos.thermal

该模块提供热管理相关的接口，包括热档位查询及注册回调等功能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace thermal--><!--Device-unnamed-declare namespace thermal-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getLevel](arkts-basicservices-thermal-getlevel-f.md#getLevel) | 获取当前热档位信息。 |
| [getThermalLevel](arkts-basicservices-thermal-getthermallevel-f.md#getThermalLevel) | 获取当前热档位信息。 |
| [registerThermalLevelCallback](arkts-basicservices-thermal-registerthermallevelcallback-f.md#registerThermalLevelCallback) | 订阅热档位变化时的回调提醒。使用callback异步回调。 |
| [subscribeThermalLevel](arkts-basicservices-thermal-subscribethermallevel-f.md#subscribeThermalLevel) | 订阅热档位变化时的回调提醒。使用callback异步回调。 |
| [unregisterThermalLevelCallback](arkts-basicservices-thermal-unregisterthermallevelcallback-f.md#unregisterThermalLevelCallback) | 取消订阅热档位变化时的回调提醒。使用callback异步回调。 |
| [unsubscribeThermalLevel](arkts-basicservices-thermal-unsubscribethermallevel-f.md#unsubscribeThermalLevel) | 取消订阅热档位变化时的回调提醒。使用callback异步回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md) | 热档位信息。 |

