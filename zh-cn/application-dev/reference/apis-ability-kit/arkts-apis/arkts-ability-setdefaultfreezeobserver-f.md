# setDefaultFreezeObserver

## setDefaultFreezeObserver

```TypeScript
function setDefaultFreezeObserver(defaultObserver?: FreezeObserver) : FreezeObserver
```

设置默认冻屏观测器。此函数将在通过errorManager.on注册的回调函数执行后立即执行。
可用于替代errorManager.on实现链式调用。
如果为某个模块设置空观测器，将导致调用链中断。

此API必须在主线程中调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| defaultObserver | FreezeObserver | 否 | 默认冻屏观测器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FreezeObserver | - 返回原来的默认冻屏观测器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000205](../errorcode-ability.md#16000205-当前接口未在主线程中调用) | API未在主线程中调用。 |

**示例：**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 用于保存上一次注册的处理器。如果是第一次注册，无前置处理器。
let oldHandler: errorManager.FreezeObserver = () => {};
const freezeHandler: errorManager.FreezeObserver = () => {
  // 自定义的FreezeHandler实现逻辑
  console.info('[freezeHandler] freeze handler invoked.');
  if (oldHandler) {
    oldHandler();
  } else {
    console.info('[freezeHandler] freeze handler end.');
  }
};

export function setFreezeHandler() {
  try {
    oldHandler = errorManager.setDefaultFreezeObserver(freezeHandler);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    console.error(`Failed to set freeze handler. Code: ${code}, message: ${message}`);
  }
  console.info('Registered freeze Handler.');
}

```

