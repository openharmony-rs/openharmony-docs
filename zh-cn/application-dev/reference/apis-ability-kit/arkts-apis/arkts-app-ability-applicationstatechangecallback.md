# @ohos.app.ability.ApplicationStateChangeCallback

本模块用于监听当前应用进程的状态变化。为了便于表述，下文中将“应用进程”简称为“进程”。
 开发者可调用ApplicationContext.on('applicationStateChange')方法传入自定义ApplicationStateChangeCallback来监听当前进程的前后台状态变化，
 并执行相应操作。例如，统计进程前后台时长、或者当进程退到后台时清理内存缓存。
 > **说明：**
 >
 > 本模块首批接口从API version 10 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
 >
 > 本模块接口仅可在Stage模型下使用。
 ## 约束限制
 该模块仅支持监听当前进程的前后台状态变化。如果需要监听整个应用的前后台状态变化，可使用ApplicationStateObserver.onForegroundApplicationChanged。
 >**说明**
 >
 > 进程的前后台状态不同于应用的前后台状态，两者的差别如下：
 >- 进程的前后台状态：如果进程中存在任何前台状态的UIAbility/UIExtensionAbility或可见窗口，则认为进程状态为前台，反之为后台。
 >- 应用的前后台状态：如果应用下有任何一个进程状态为前台，则认为应用状态为前台，反之为后台。


## 导入模块

```TypeScript
import { ApplicationStateChangeCallback } from '@kit.AbilityKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ApplicationStateChangeCallback](arkts-ability-app-ability-applicationstatechangecallback-applicationstatechangecallback-c.md) | * 本模块用于监听当前应用进程的状态变化。为了便于表述，下文中将“应用进程”简称为“进程”。开发者可调用ApplicationContext.on('applicationStateChange')方法传入自定义ApplicationStateChangeCallback来监听当前进程的前后台状态变化， 并执行相应操作。例如，统计进程前后台时长、或者当进程退到后台时清理内存缓存。 |
