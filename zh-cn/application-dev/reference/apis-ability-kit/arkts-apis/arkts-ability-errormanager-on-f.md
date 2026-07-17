# on

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## on('error')

```TypeScript
function on(type: 'error', observer: ErrorObserver): number
```

注册错误观测器。注册后可以捕获到应用产生的js crash，属于应用崩溃的一种。观测器捕获到该异常时应用不退出，建议在回调函数执行完后，增加同步退出操作。

仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function on(type: 'error', observer: ErrorObserver): number--><!--Device-errorManager-function on(type: 'error', observer: ErrorObserver): number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 填写'error'，表示错误观测器。 |
| observer | [ErrorObserver](arkts-ability-errormanager-errorobserver-t.md) | 是 | 错误观测器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 观测器的索引值，与观测器一一对应。可用于`errorManager.off`函数中的`observerId`参数。没有具体的单位。结果返回值是observerId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |
| [16000003](../errorcode-ability.md#16000003-指定的id不存在) | 指定的ID不存在。 |

**示例：**

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


## on('loopObserver')

```TypeScript
function on(type: 'loopObserver', timeout: number, observer: LoopObserver): void
```

注册主线程消息处理耗时监听器。注册后可以捕获到应用主线程处理消息的具体执行时间。

仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function on(type: 'loopObserver', timeout: number, observer: LoopObserver): void--><!--Device-errorManager-function on(type: 'loopObserver', timeout: number, observer: LoopObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'loopObserver' | 是 | 填写'loopObserver'，表示注册主线程消息处理耗时监听器。 |
| timeout | number | 是 | 表示事件执行阈值（单位：毫秒）。 阈值必须大于0。 单位为毫秒（ms）。 |
| observer | [LoopObserver](arkts-ability-errormanager-loopobserver-t.md) | 是 | 注册主线程消息处理耗时监听器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |

**示例：**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.LoopObserver = {
  onLoopTimeOut(timeout: number) {
    console.info('Duration timeout: ' + timeout);
  }
};

try {
  errorManager.on('loopObserver', 1, observer);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}

```


## on('unhandledRejection')

```TypeScript
function on(type: 'unhandledRejection', observer: UnhandledRejectionObserver): void
```

注册被拒绝promise监听器。注册后可以捕获到当前线程中未被捕获到的promise rejection。

仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function on(type: 'unhandledRejection', observer: UnhandledRejectionObserver): void--><!--Device-errorManager-function on(type: 'unhandledRejection', observer: UnhandledRejectionObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'unhandledRejection' | 是 | 填写'unhandledRejection'，表示注册被拒绝promise监听器。 |
| observer | [UnhandledRejectionObserver](arkts-ability-errormanager-unhandledrejectionobserver-t.md) | 是 | 注册被拒绝promise监听器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | 请在主线程中调用。 |

**示例：**

```TypeScript
import { errorManager } from '@kit.AbilityKit';

let observer: errorManager.UnhandledRejectionObserver = (reason: Error, promise: Promise<void>) => {
  if (promise === promise1) {
    console.info('promise1 is rejected');
  }
  console.info('reason.name: ', reason.name);
  console.info('reason.message: ', reason.message);
  if (reason.stack) {
    console.info('reason.stack: ', reason.stack);
  }
};

errorManager.on('unhandledRejection', observer);

let promise1 = new Promise<void>(() => {}).then(() => {
  throw new Error('uncaught error');
});

```


## on('globalUnhandledRejectionDetected')

```TypeScript
function on(type: 'globalUnhandledRejectionDetected', observer: GlobalObserver): void
```

在进程中任意线程注册被拒绝promise监听器，注册后可以捕获到当前进程中未被捕获到的promise rejection。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function on(type: 'globalUnhandledRejectionDetected', observer: GlobalObserver): void--><!--Device-errorManager-function on(type: 'globalUnhandledRejectionDetected', observer: GlobalObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'globalUnhandledRejectionDetected' | 是 | 填写'globalUnhandledRejectionDetected'，表示注册被拒绝promise监听器。 |
| observer | [GlobalObserver](arkts-ability-errormanager-globalobserver-t.md) | 是 | 注册被拒绝promise的callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | 调用者无效。 |

**示例：**

```TypeScript
import { errorManager } from '@kit.AbilityKit';

const promiseFunc = (observer: errorManager.GlobalError) => {
  console.info('result name :' + observer.name);
  console.info('result message :' + observer.message);
  console.info('result stack :' + observer.stack);
  console.info('result instanceName :' + observer.instanceName);
  console.info('result instanceType :' + observer.instanceType);
};

errorManager.on('globalUnhandledRejectionDetected', promiseFunc);
// 建议在抛出promise异常时，使用async抛出异常。
const throwError = async () => {
  throw new Error('uncaught error');
};

let promise1 = new Promise<void>(() => {}).then(() => {
  throwError();
});

```


## on('freeze')

```TypeScript
function on(type: 'freeze', observer: FreezeObserver): void
```

注册应用主线程freeze监听。多次注册情况下，取最后一次注册的结果。

仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

> **注意**：  
>  
> 如果该回调函数执行时间超过1s，可能导致[AppRecovery](arkts-app-ability-apprecovery.md)功能不可用。通过解析hilog日志中的begin与Freeze  
> callback execution completed两者的时间差可以计算回调函数执行时长，如果超过1秒，可以尝试采用异步处理、减少阻塞操作、优化数据结构等方法优化回调逻辑，降低执行时长。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function on(type: 'freeze', observer: FreezeObserver): void--><!--Device-errorManager-function on(type: 'freeze', observer: FreezeObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'freeze' | 是 | 填写'freeze'，表示应用主线程freeze观测器。 |
| observer | [FreezeObserver](arkts-ability-errormanager-freezeobserver-t.md) | 是 | 由on接口注册的freeze监听的callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |

**示例：**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const freezeCallback = () => {
  console.info('freezecallback');
};
try {
  errorManager.on('freeze', freezeCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}

```


## on('globalErrorOccurred')

```TypeScript
function on(type: 'globalErrorOccurred', observer: GlobalObserver): void
```

在进程中的任意线程中注册 `errormanager.on` 接口，监听整个进程中任意线程的异常。观测器捕获到该异常时应用不退出，建议在回调函数执行完后，增加同步退出操作。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function on(type: 'globalErrorOccurred', observer: GlobalObserver): void--><!--Device-errorManager-function on(type: 'globalErrorOccurred', observer: GlobalObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'globalErrorOccurred' | 是 | 填写'globalErrorOccurred'，表示错误观测器。 |
| observer | [GlobalObserver](arkts-ability-errormanager-globalobserver-t.md) | 是 | 自定义异常处理回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | 调用者无效。 |

**示例：**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const errorFunc = (observer: errorManager.GlobalError) => {
  console.info('result name :' + observer.name);
  console.info('result message :' + observer.message);
  console.info('result stack :' + observer.stack);
  console.info('result instanceName :' + observer.instanceName);
  console.info('result instanceType :' + observer.instanceType);
};

try {
  errorManager.on('globalErrorOccurred', errorFunc);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}

```

