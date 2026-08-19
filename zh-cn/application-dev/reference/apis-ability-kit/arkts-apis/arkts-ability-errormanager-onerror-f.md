# on_error

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## on('error')

```TypeScript
function on(type: 'error', observer: ErrorObserver): number
```

注册错误观测器。注册后可以捕获到应用产生的js crash，属于应用崩溃的一种。观测器捕获到该异常时应用不退出，建议在回调函数执行完后，增加同步退出操作。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function on(type: 'error', observer: ErrorObserver): number--><!--Device-errorManager-function on(type: 'error', observer: ErrorObserver): number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 填写'error'，表示错误观测器。 |
| observer | ErrorObserver | 是 | 错误观测器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 观测器的索引值，与观测器一一对应。可用于`errorManager.off`函数中的`observerId`参数。 没有具体的单位。结果返回值是observerId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：1. 必填参数未填写； 2. 参数类型不正确；3. 参数校验失败。 |
| [16000003](../errorcode-ability.md#16000003-指定的id不存在) | 指定的ID不存在。 |

**示例**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errorMsg) {
    console.info('onUnhandledException, errorMsg: ', errorMsg);
  },
  onException(errorObj) {
    console.info('onException, name: ', errorObj.name);
    console.info('onException, message: ', errorObj.message);
    if (typeof(errorObj.stack) === 'string') {
      console.info('onException, stack: ', errorObj.stack);
    }
  }
};
let observerId = -1;

try {
  observerId = errorManager.on('error', observer);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```

