# off_error

## off_error

```TypeScript
function off(type: 'error', observerId: number, callback: AsyncCallback<void>): void
```

注销错误观测器。使用callback异步返回。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function off(type: 'error', observerId: number, callback: AsyncCallback<void>): void--><!--Device-errorManager-function off(type: 'error', observerId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 填写'error'，表示错误观测器。 |
| observerId | number | 是 | 由on方法返回的观测器的index值。没有具体的单位。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 表示指定的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：1. 必填参数未填写； 2. 参数类型不正确；3. 参数校验失败。 |
| [16000003](../errorcode-ability.md#16000003-指定的id不存在) | 指定的ID不存在。 |

## 示例

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


## off_error

```TypeScript
function off(type: 'error', observerId: number): Promise<void>
```

注销错误观测器。使用Promise异步返回。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

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
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：1. 必填参数未填写； 2. 参数类型不正确；3. 参数校验失败。 |
| [16000003](../errorcode-ability.md#16000003-指定的id不存在) | 指定的ID不存在。 |

## 示例

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

