# off_globalErrorOccurred

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## off('globalErrorOccurred')

```TypeScript
function off(type: 'globalErrorOccurred', observer?: GlobalObserver): void
```

注销错误观测器，注销之前注册在同一线程的callback全局监听。 如果传入的回调不在通过on方法注册的回调队列中，将抛出16300004错误码，因此建议使用try-catch逻辑进行处理。

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
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：1. 必填参数未填写； 2. 参数类型不正确；3. 参数校验失败。 |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | 调用者无效。 |
| [16300004](../errorcode-ability.md#16300004-指定的observer不存在) | 观测器不存在。 |

**示例**

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
  errorManager.off('globalErrorOccurred', errorFunc)
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```

