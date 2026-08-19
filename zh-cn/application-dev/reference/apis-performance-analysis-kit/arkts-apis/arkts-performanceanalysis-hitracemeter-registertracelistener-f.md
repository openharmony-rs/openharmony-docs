# registerTraceListener

## 导入模块

```TypeScript
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## registerTraceListener

```TypeScript
function registerTraceListener(callback: TraceEventListener): int
```

注册应用trace捕获开关通知回调，使用callback异步回调。 注册成功后，立即执行一次回调函数，后续回调函数由应用trace捕获开关状态变化触发执行。 回调函数保存在应用进程内，一个进程最多可以注册10个回调函数。若注册的回调包含耗时操作，当回调被执行时，注册或注销行为会被阻塞 （等待回调执行完成）。因此，建议不要在应用主线程中注册或注销包含耗时操作的回调，避免发生应用冻屏。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-hiTraceMeter-function registerTraceListener(callback: TraceEventListener): int--><!--Device-hiTraceMeter-function registerTraceListener(callback: TraceEventListener): int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TraceEventListener](arkts-performanceanalysis-hitracemeter-traceeventlistener-t.md) | 是 | 注册的回调函数，用于监听应用trace捕获开关状态变化。当trace捕获开关状态发生变化时 （从开启变为关闭或从关闭变为开启），会触发此回调并传入当前的trace状态。注册成功后会立即执行一次回调，后续每次trace捕获开关状态变化 都会触发回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 回调注册状态。 >= 0：注册成功，返回用于注销的回调索引，索引范围[0, 9]； -1：已达到最大回调函数注册数量； -2：无效参数，参数非TraceEventListener类型。 |

**示例**

```TypeScript
// 注册的回调函数定义
let callback: hiTraceMeter.TraceEventListener = (traceStatus: boolean) => {
  if (traceStatus) {
    // 当前应用trace捕获开启
    // ...
  } else {
    // 当前应用trace捕获关闭
    // ...
  }
};

// 注册应用trace捕获开关通知回调
let index = hiTraceMeter.registerTraceListener(callback);
if (index < 0) {
  // 异常处理......
}
```

