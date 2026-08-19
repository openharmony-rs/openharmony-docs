# @ohos.runningLock

该模块为RunningLock锁相关操作的接口，提供阻止系统睡眠和使能接近光控制亮灭屏的能力，适用于设备灭屏后保持后台任务持续运行、接近光控制亮灭屏、以及阻止系统闲时自动睡眠等场景，保证关键任务的持续执行。 包括创建、查询、持锁、释放锁等操作，类型详情见[RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md)。

**起始版本：** 23

<!--Device-unnamed-declare namespace runningLock--><!--Device-unnamed-declare namespace runningLock-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## 导入模块

```TypeScript
import { runningLock } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-basicservices-runninglock-create-f.md) | 创建RunningLock锁对象。使用callback异步回调。创建锁对象后，需调用hold()方法锁定和持有该锁，才能使锁功能生效。 |
| [create](arkts-basicservices-runninglock-create-f.md) | 创建RunningLock锁对象。使用Promise异步回调。创建锁对象后，需调用hold()方法锁定和持有该锁，才能使锁功能生效。 |
| [createRunningLock](arkts-basicservices-runninglock-createrunninglock-f.md) | 创建RunningLock锁。使用callback异步回调。 |
| [createRunningLock](arkts-basicservices-runninglock-createrunninglock-f.md) | 创建RunningLock锁。使用Promise异步回调。 |
| [isRunningLockTypeSupported](arkts-basicservices-runninglock-isrunninglocktypesupported-f.md) | 查询系统是否支持该类型的锁。使用callback异步回调。 |
| [isRunningLockTypeSupported](arkts-basicservices-runninglock-isrunninglocktypesupported-f.md) | 查询系统是否支持该类型的锁。使用Promise异步回调。 |
| [isSupported](arkts-basicservices-runninglock-issupported-f.md) | 查询系统是否支持该类型的锁。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) | 阻止系统睡眠或使能接近光控制亮灭屏的锁，不同的锁类型具有不同的功能，详见[RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md)。 需结合[create](arkts-basicservices-runninglock-create-f.md)创建锁、[hold](arkts-basicservices-runninglock-runninglock-c.md#hold)持锁、[unhold](arkts-basicservices-runninglock-runninglock-c.md#unhold)释放锁使用。具体使用方法见示例。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | RunningLock锁的类型。 |

