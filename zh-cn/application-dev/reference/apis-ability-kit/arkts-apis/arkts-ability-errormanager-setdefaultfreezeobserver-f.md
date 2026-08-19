# setDefaultFreezeObserver

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## setDefaultFreezeObserver

```TypeScript
function setDefaultFreezeObserver(defaultObserver?: FreezeObserver) : FreezeObserver
```

发生APP_FREEZE时，支持链式回调，返回上一次注册的处理器，仅限主线程调用。 如果传入非法参数或在子线程调用，将抛出错误码并返回undefined，因此建议使用try-catch逻辑进行处理。 > **说明：** > > 该接口请勿与 > [on('freeze')](arkts-ability-errormanager-onerror-f.md#onerror) > 或 > [off('freeze')](arkts-ability-errormanager-offerror-f.md#offerror) > 接口混用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function setDefaultFreezeObserver(defaultObserver?: FreezeObserver) : FreezeObserver--><!--Device-errorManager-function setDefaultFreezeObserver(defaultObserver?: FreezeObserver) : FreezeObserver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| defaultObserver | [FreezeObserver](arkts-ability-errormanager-freezeobserver-t.md) | 否 | 默认冻屏观测器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FreezeObserver](arkts-ability-errormanager-freezeobserver-t.md) | 返回原来的默认冻屏观测器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000205](../errorcode-ability.md#16000205-当前接口未在主线程中调用) | API未在主线程中调用。 |

**示例**

ArkTS-Dyn示例：

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

export const setFreezeHandler = () => {
  try {
    oldHandler = errorManager.setDefaultFreezeObserver(freezeHandler);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    console.error(`Failed to set freeze handler. Code: ${code}, message: ${message}`);
  }
  console.info('Registered freeze Handler.');
};
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { errorManager } from '@kit.AbilityKit';

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

export const setFreezeHandler = () => {
  try {
    oldHandler = errorManager.setDefaultFreezeObserver(freezeHandler);
    console.info('Registered freeze Handler.');
  } catch (paramError) {
    console.error('setFreezeHandler error: ', paramError);
  }
};
```

