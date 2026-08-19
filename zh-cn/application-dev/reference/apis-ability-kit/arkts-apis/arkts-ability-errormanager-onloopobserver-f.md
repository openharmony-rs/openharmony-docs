# on_loopObserver

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## on('loopObserver')

```TypeScript
function on(type: 'loopObserver', timeout: number, observer: LoopObserver): void
```

注册主线程消息处理耗时监听器。注册后可以捕获到应用主线程处理消息的具体执行时间。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function on(type: 'loopObserver', timeout: number, observer: LoopObserver): void--><!--Device-errorManager-function on(type: 'loopObserver', timeout: number, observer: LoopObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'loopObserver' | 是 | 填写'loopObserver'，表示注册主线程消息处理耗时监听器。 |
| timeout | number | 是 | 表示事件执行阈值（单位：毫秒）。 阈值必须大于0。 单位为毫秒（ms）。 |
| observer | LoopObserver | 是 | 注册主线程消息处理耗时监听器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：1. 必填参数未填写； 2. 参数类型不正确；3. 参数校验失败。 |

**示例**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.LoopObserver = {
  onLoopTimeOut(timeout: number) {
    console.info('Duration timeout: ' + timeout);
  }
};

try {
  errorManager.on("loopObserver", 1, observer);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```

