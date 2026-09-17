# addWatcher

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## addWatcher

```TypeScript
function addWatcher(watcher: Watcher): AppEventPackageHolder
```

添加事件观察者。可通过事件观察者的回调函数监听事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watcher | [Watcher](arkts-performanceanalysis-hiappevent-watcher-i.md) | 是 | 事件观察者。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AppEventPackageHolder](arkts-performanceanalysis-hiappevent-appeventpackageholder-c.md) | 订阅数据持有者。订阅失败时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
| [11102001](../errorcode-hiappevent.md#11102001-非法的观察者名称) | Invalid watcher name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11102002](../errorcode-hiappevent.md#11102002-非法的过滤事件领域) | Invalid filtering event domain. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11102003](../errorcode-hiappevent.md#11102003-非法的条数值) | Invalid row value. Possibly caused by the row value is less than zero. |
| [11102004](../errorcode-hiappevent.md#11102004-非法的大小值) | Invalid size value. Possibly caused by the size value is less than zero. |
| [11102005](../errorcode-hiappevent.md#11102005-非法的超时值) | Invalid timeout value. Possibly caused by the timeout value is less than zero. |

**示例**

```TypeScript
根据添加的事件观察者类型，目前有如下三种使用方法：

方法一：设置回调条件triggerCondition，实现onTrigger()回调。当满足回调条件时，系统将自动触发回调。
```

```TypeScript
方法二：未设置回调条件参数，使用事件订阅返回的holder对象主动获取监听的事件。

针对异常退出时产生的崩溃事件（hiAppEvent.event.APP_CRASH）和应用冻屏事件（hiAppEvent.event.APP_FREEZE），系统捕获维测日志有一定耗时，典型情况下30s内完成，极端情况下2min左右完成。

在手动处理订阅事件的方法中，由于事件可能未生成或日志信息未抓取完成，建议在进程启动后延时重试调用takeNext()获取此类事件。
```

```TypeScript
方法三：实现onReceive()回调，当监听的事件发生后实时触发回调。
```
