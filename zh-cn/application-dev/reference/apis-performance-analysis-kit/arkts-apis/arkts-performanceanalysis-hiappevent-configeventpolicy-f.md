# configEventPolicy

## 导入模块

```TypeScript
```

## configEventPolicy

```TypeScript
function configEventPolicy(policy: EventPolicy): Promise<void>
```

系统事件相关的配置策略设置方法，使用Promise方式作为异步回调。在同一生命周期中，可以通过配置策略设置系统事件相关的策略参数。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | [EventPolicy](arkts-performanceanalysis-hiappevent-eventpolicy-i.md) | 是 | 系统事件配置策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**示例**

以下示例用于模拟设置MAIN_THREAD_JANK事件的配置策略：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let policy: hiAppEvent.EventPolicy = {
  mainThreadJankPolicy:{
    logType: 1,
    sampleInterval: 100,
    ignoreStartupTime: 11,
    sampleCount: 21,
    reportTimesPerApp: 3,
    autoStopSampling: true
  }
};
hiAppEvent.configEventPolicy(policy).then(() => {
  hilog.info(0x0000, 'hiAppEvent', `Successfully set main thread jank event policy.`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'hiAppEvent', `Failed to set main thread jank event policy. Code: ${err?.code}, message: ${err?.message}`);
});
```
