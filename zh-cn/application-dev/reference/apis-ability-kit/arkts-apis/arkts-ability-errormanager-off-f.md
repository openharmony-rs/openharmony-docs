# off

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## off('error')

```TypeScript
function off(type: 'error', observerId: number, callback: AsyncCallback<void>): void
```

注销错误观测器。使用callback异步返回。

仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function off(type: 'error', observerId: number, callback: AsyncCallback<void>): void--><!--Device-errorManager-function off(type: 'error', observerId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 填写'error'，表示错误观测器。 |
| observerId | number | 是 | 由on方法返回的观测器的index值。没有具体的单位。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 表示指定的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |
| [16000003](../errorcode-ability.md#16000003-指定的id不存在) | 指定的ID不存在。 |

**示例：**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 100;

const unregisterErrorObserverCallback = (err: BusinessError) => {
  if (err) {
    console.error('------------ unregisterErrorObserverCallback ------------', err);
  }
};

try {
  errorManager.off('error', observerId, unregisterErrorObserverCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}

```


## off('error')

```TypeScript
function off(type: 'error', observerId: number): Promise<void>
```

注销错误观测器。使用Promise异步返回。

仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function off(type: 'error', observerId: number): Promise<void>--><!--Device-errorManager-function off(type: 'error', observerId: number): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 填写'error'，表示错误观测器。 |
| observerId | number | 是 | 由on方法返回的观测器的index值。没有具体的单位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |
| [16000003](../errorcode-ability.md#16000003-指定的id不存在) | 指定的ID不存在。 |

**示例：**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 100;

try {
  errorManager.off('error', observerId)
    .then((data) => {
      console.info('----------- unregisterErrorObserver success ----------', data);
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to unregister error observer. Code: ${err.code}, message: ${err.message}`);
    });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}

```


## off('loopObserver')

```TypeScript
function off(type: 'loopObserver', observer?: LoopObserver): void
```

注销主线程消息处理监听器。

仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function off(type: 'loopObserver', observer?: LoopObserver): void--><!--Device-errorManager-function off(type: 'loopObserver', observer?: LoopObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'loopObserver' | 是 | 填写'loopObserver'，表示应用主线程观测器。 |
| observer | [LoopObserver](arkts-ability-errormanager-loopobserver-t.md) | 否 | 应用主线程观测器标志。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | 请在主线程中调用。 |
| [16300004](../errorcode-ability.md#16300004-指定的observer不存在) | 观测器不存在。 |

**示例：**

```TypeScript
import { errorManager } from '@kit.AbilityKit';

try {
  errorManager.off('loopObserver');
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}

```


## off('unhandledRejection')

```TypeScript
function off(type: 'unhandledRejection', observer?: UnhandledRejectionObserver): void
```

注销被拒绝promise监听器。

仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function off(type: 'unhandledRejection', observer?: UnhandledRejectionObserver): void--><!--Device-errorManager-function off(type: 'unhandledRejection', observer?: UnhandledRejectionObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'unhandledRejection' | 是 | 填写'unhandledRejection'，表示注册被拒绝promise监听器。 |
| observer | [UnhandledRejectionObserver](arkts-ability-errormanager-unhandledrejectionobserver-t.md) | 否 | 注册了被拒绝promise监听器。建议使用该参数，缺省时默认清除所有通过on注册的相同env的observer，否则删除指定observer。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | 请在主线程中调用。 |
| [16300004](../errorcode-ability.md#16300004-指定的observer不存在) | 观测器不存在。 |

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
  throw new Error('uncaught error')
})

errorManager.off('unhandledRejection');

```

或者

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
  throw new Error('uncaught error')
})

errorManager.off('unhandledRejection', observer);

```


## off('globalUnhandledRejectionDetected')

```TypeScript
function off(type: 'globalUnhandledRejectionDetected', observer?: GlobalObserver): void
```

注销被拒绝promise监听器，注销后无法监听进程中的promise异常。

如果传入的回调不在通过on方法注册的回调队列中，将抛出16300004错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function off(type: 'globalUnhandledRejectionDetected', observer?: GlobalObserver): void--><!--Device-errorManager-function off(type: 'globalUnhandledRejectionDetected', observer?: GlobalObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'globalUnhandledRejectionDetected' | 是 | 填写'globalUnhandledRejectionDetected'，表示注册被拒绝promise监听器。 |
| observer | [GlobalObserver](arkts-ability-errormanager-globalobserver-t.md) | 否 | 由on接口注册的被拒绝promise的callback。建议使用该参数，缺省时默认清除所有通过on注册的相同env的callback，否则删除指定callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | 调用者无效。 |
| [16300004](../errorcode-ability.md#16300004-指定的observer不存在) | 观测器不存在。 |

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

const throwError = async () => {
  throw new Error('uncaught error');
};

let promise1 = new Promise<void>(() => {}).then(() => {
  throwError();
});

errorManager.off('globalUnhandledRejectionDetected', promiseFunc);

```


## off('freeze')

```TypeScript
function off(type: 'freeze', observer?: FreezeObserver): void
```

取消之前注册的应用主线程freeze监听。

仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

如果传入的回调与通过on方法注册回调不一致，将抛出16300004错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function off(type: 'freeze', observer?: FreezeObserver): void--><!--Device-errorManager-function off(type: 'freeze', observer?: FreezeObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'freeze' | 是 | 填写'freeze'，表示应用主线程freeze观测器。 |
| observer | [FreezeObserver](arkts-ability-errormanager-freezeobserver-t.md) | 否 | 由on接口注册的freeze监听的callback。建议使用该参数，如果参数不填会直接清空callback，否则删除指定的callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |
| [16300004](../errorcode-ability.md#16300004-指定的observer不存在) | 观测器不存在。 |

**示例：**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const freezeCallback = () => {
  console.info('freezecallback');
};
try {
  errorManager.on('freeze', freezeCallback);
  errorManager.off('freeze', freezeCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}

```


## off('globalErrorOccurred')

```TypeScript
function off(type: 'globalErrorOccurred', observer?: GlobalObserver): void
```

注销错误观测器，注销之前注册在同一线程的callback全局监听。

如果传入的回调不在通过on方法注册的回调队列中，将抛出16300004错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function off(type: 'globalErrorOccurred', observer?: GlobalObserver): void--><!--Device-errorManager-function off(type: 'globalErrorOccurred', observer?: GlobalObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'globalErrorOccurred' | 是 | 填写'globalErrorOccurred'，表示错误观测器。 |
| observer | [GlobalObserver](arkts-ability-errormanager-globalobserver-t.md) | 否 | 由on方法注册的callback。建议使用该参数，缺省时默认清除所有通过on注册的相同env的callback，否则删除指定callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数错误。可能的原因：1. 必填参数未填写；2. 参数类型不正确；3. 参数校验失败。 |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | 调用者无效。 |
| [16300004](../errorcode-ability.md#16300004-指定的observer不存在) | 观测器不存在。 |

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
}

try {
  errorManager.off('globalErrorOccurred', errorFunc)
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}

```

