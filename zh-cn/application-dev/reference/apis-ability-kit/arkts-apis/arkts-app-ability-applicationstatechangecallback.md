# @ohos.app.ability.ApplicationStateChangeCallback

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ApplicationStateChangeCallback](arkts-ability-app-ability-applicationstatechangecallback-applicationstatechangecallback-i.md) | 本模块用于监听当前应用进程的状态变化。为了便于表述，下文中将“应用进程”简称为“进程”。 开发者可调用 [ApplicationContext.on('applicationStateChange')]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 方法传入自定义ApplicationStateChangeCallback来监听当前进程的前后台状态变化，从而根据进程前后台状态变化来执行某些操作。例如，统计进程前后台时长、或者当进程退到后台时清理内存缓存。 |

