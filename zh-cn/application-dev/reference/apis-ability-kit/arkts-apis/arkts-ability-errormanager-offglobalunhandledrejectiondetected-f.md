# off_globalUnhandledRejectionDetected

## off_globalUnhandledRejectionDetected

```TypeScript
function off(type: 'globalUnhandledRejectionDetected', observer?: GlobalObserver): void
```

注销被拒绝promise监听器，注销后无法监听进程中的promise异常。 如果传入的回调不在通过on方法注册的回调队列中，将抛出16300004错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function off(type: 'globalUnhandledRejectionDetected', observer?: GlobalObserver): void--><!--Device-errorManager-function off(type: 'globalUnhandledRejectionDetected', observer?: GlobalObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'globalUnhandledRejectionDetected' | 是 | 填写'globalUnhandledRejectionDetected'，表示注册被拒绝promise监听器。 |
| observer | [GlobalObserver](arkts-ability-errormanager-globalobserver-t.md) | 否 | 由on接口注册的被拒绝promise的callback。建议使用该参数，缺省时默认清除所有通过on注册的相同env的callback，否则删除指定 callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：1. 必填参数未填写； 2. 参数类型不正确；3. 参数校验失败。 |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | 调用者无效。 |
| [16300004](../errorcode-ability.md#16300004-指定的observer不存在) | 观测器不存在。 |

## 示例

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

