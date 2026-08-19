# onFreeze

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## onFreeze

```TypeScript
function onFreeze(observer: FreezeObserver): void
```

注册冻屏事件观测器。 此函数只能在主线程中调用。 请注意，每个进程只支持注册一个观测器。 如果多次注册，后注册的将覆盖之前的。

**起始版本：** 24

<!--Device-errorManager-function onFreeze(observer: FreezeObserver): void--><!--Device-errorManager-function onFreeze(observer: FreezeObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [FreezeObserver](arkts-ability-errormanager-freezeobserver-t.md) | 是 | 应用主线程freeze观测器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：1. 必填参数未填写； 2. 参数类型不正确；3. 参数校验失败。 |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | 调用者无效。 |

**示例**

```TypeScript
import { errorManager } from '@kit.AbilityKit';

export const FreezeRegister = () => {
  try {
    let observer: errorManager.FreezeObserver = () => {
      console.info('onFreezecallback');
    };
    errorManager.onFreeze(observer);
    console.info('Registered onfreeze Handler.');
  } catch (paramError) {
      console.error('onFreeze error: ', paramError);
  }
};
```

