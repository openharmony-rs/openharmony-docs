# off_loopObserver

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## off('loopObserver')

```TypeScript
function off(type: 'loopObserver', observer?: LoopObserver): void
```

注销主线程消息处理监听器。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function off(type: 'loopObserver', observer?: LoopObserver): void--><!--Device-errorManager-function off(type: 'loopObserver', observer?: LoopObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'loopObserver' | 是 | 填写'loopObserver'，表示应用主线程观测器。 |
| observer | LoopObserver | 否 | 应用主线程观测器标志。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：1. 必填参数未填写； 2. 参数类型不正确；3. 参数校验失败。 |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | 请在主线程中调用。 |
| [16300004](../errorcode-ability.md#16300004-指定的observer不存在) | 观测器不存在。 |

**示例**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  errorManager.off('loopObserver');
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```

