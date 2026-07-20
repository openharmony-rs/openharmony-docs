# @ohos.runningLock

该模块为RunningLock锁相关操作的接口，提供使能接近光亮灭屏或者设备熄屏后阻止进入睡眠的能力，包括创建、查询、持锁、释放锁等操作，类型详情见[RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md)。

**起始版本：** 7

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
| [create](arkts-basicservices-runninglock-create-f.md#create) | 创建RunningLock锁。使用callback异步回调。 |
| [create](arkts-basicservices-runninglock-create-f.md#create-1) | 创建RunningLock锁。使用Promise异步回调。 |
| [createRunningLock](arkts-basicservices-runninglock-createrunninglock-f.md#createrunninglock) | 创建RunningLock锁。使用callback异步回调。 |
| [createRunningLock](arkts-basicservices-runninglock-createrunninglock-f.md#createrunninglock-1) | 创建RunningLock锁。使用Promise异步回调。 |
| [isRunningLockTypeSupported](arkts-basicservices-runninglock-isrunninglocktypesupported-f.md#isrunninglocktypesupported) | 查询系统是否支持该类型的锁。使用callback异步回调。 |
| [isRunningLockTypeSupported](arkts-basicservices-runninglock-isrunninglocktypesupported-f.md#isrunninglocktypesupported-1) | 查询系统是否支持该类型的锁。使用Promise异步回调。 |
| [isSupported](arkts-basicservices-runninglock-issupported-f.md#issupported) | 查询系统是否支持该类型的锁。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) | 阻止系统睡眠的锁。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | RunningLock锁的类型。 |

