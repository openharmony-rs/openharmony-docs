# EventListener

事件监听类用于处理事件。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** ohos.worker.WorkerEventListener

<!--Device-unnamed-export interface EventListener--><!--Device-unnamed-export interface EventListener-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
(evt: Event): void | Promise<void>
```

指定要调用的回调函数。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** ohos.worker.WorkerEventListener.(event:

<!--Device-EventListener-(evt: Event): void | Promise<void>--><!--Device-EventListener-(evt: Event): void | Promise<void>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | evt evt 回调的事件类。 |

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.addEventListener("alert", ()=>{
    console.info("alert listener callback");
})
```

