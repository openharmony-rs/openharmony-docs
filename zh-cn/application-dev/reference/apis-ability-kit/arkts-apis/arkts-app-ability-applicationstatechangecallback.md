# @ohos.app.ability.ApplicationStateChangeCallback

## 导入模块

```TypeScript
import { ApplicationStateChangeCallback } from '@kit.AbilityKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ApplicationStateChangeCallback](arkts-ability-app-ability-applicationstatechangecallback-applicationstatechangecallback-c.md) | 本模块用于监听当前应用进程的状态变化。为了便于表述，下文中将“应用进程”简称为“进程”。开发者可调用[ApplicationContext.on('applicationStateChange')](arkts-ability-applicationcontext-c.md#on-3)方法传入自定义ApplicationStateChangeCallback来监听当前进程的前后台状态变化，从而根据进程前后台状态变化来执行某些操作。例如，统计进程前后台时长、或者当进程退到后台时清理内存缓存。 |

