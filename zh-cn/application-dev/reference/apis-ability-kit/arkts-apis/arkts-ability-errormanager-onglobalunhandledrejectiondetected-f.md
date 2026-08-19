# on_globalUnhandledRejectionDetected

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
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
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：1. 必填参数未填写； 2. 参数类型不正确；3. 参数校验失败。 |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | 调用者无效。 |

**示例**

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
// 建议在抛出Promise异常时，使用async抛出异常。
const throwError = async () => {
  throw new Error('uncaught error');
};

let promise1 = new Promise<void>(() => {}).then(() => {
  throwError();
});
```

