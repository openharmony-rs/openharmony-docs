# LoopObserver

定义异常监听，可以作为 [ErrorManager.on](arkts-ability-errormanager-on-f.md#onloopobserver) 的入参，用于监听应用主线程事件处理超时的情况。通过回调机制实时获取主线程消息实际执行时间，帮助开发者及时发现和定位故障问题。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onLoopTimeOut

```TypeScript
onLoopTimeOut?(timeout: number): void
```

当JS运行时应用主线程处理事件超时时触发的回调函数。 使用场景：用于监控应用主线程处理事件的执行情况，当主线程处理事件超时时触发该回调，开发者可以根据超时情况记录日志、优化代码逻辑等。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 表示应用主线程消息实际执行时间，单位：毫秒，取值范围：大于0的正整数。 |

**示例**

```TypeScript
import { errorManager } from '@kit.AbilityKit';

let observer: errorManager.LoopObserver = {
  onLoopTimeOut(timeout: number) {
    console.info('Duration timeout: ' + timeout);
  }
};

errorManager.on('loopObserver', 1, observer);
```
