# @ohos.runningLock

该模块为RunningLock锁相关操作的接口，RunningLock锁提供使能接近光亮灭屏或者设备熄屏后阻止进入睡眠的能力，包括创建、查询、持锁、释放锁等操作，RunningLock锁的类型详情见
[RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md#RunningLockType)。

**起始版本：** 7

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-basicservices-runninglock-create-f.md#create-1) | 创建RunningLock锁。使用callback异步回调。<br/> |
| [create](arkts-basicservices-runninglock-create-f.md#create-2) | 创建RunningLock锁。使用Promise异步回调。<br/> |
| [createRunningLock](arkts-basicservices-runninglock-createrunninglock-f.md#createRunningLock-1) | 创建RunningLock锁。使用callback异步回调。<br/> |
| [createRunningLock](arkts-basicservices-runninglock-createrunninglock-f.md#createRunningLock-2) | 创建RunningLock锁。使用Promise异步回调。<br/> |
| [isRunningLockTypeSupported](arkts-basicservices-runninglock-isrunninglocktypesupported-f.md#isRunningLockTypeSupported-1) | 查询系统是否支持该类型的锁。使用callback异步回调。<br/> |
| [isRunningLockTypeSupported](arkts-basicservices-runninglock-isrunninglocktypesupported-f.md#isRunningLockTypeSupported-2) | 查询系统是否支持该类型的锁。使用Promise异步回调。<br/> |
| [isSupported](arkts-basicservices-runninglock-issupported-f.md#isSupported-1) | 查询系统是否支持该类型的锁。<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) | 阻止系统睡眠的锁。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | RunningLock锁的类型。<br/> |

