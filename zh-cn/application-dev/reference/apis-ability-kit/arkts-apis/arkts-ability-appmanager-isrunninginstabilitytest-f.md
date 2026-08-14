# isRunningInStabilityTest

## isRunningInStabilityTest

```TypeScript
function isRunningInStabilityTest(callback: AsyncCallback<boolean>): void
```

查询当前系统是否处于稳定性测试场景。使用callback异步回调。 > **说明：** > > 稳定性测试场景指为验证应用在复杂、极端或长期运行条件下的可靠性而设计的特定测试环境。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-appManager-function isRunningInStabilityTest(callback: AsyncCallback<boolean>): void--><!--Device-appManager-function isRunningInStabilityTest(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。当接口调用成功，err为undefined，data为当前系统是否处于稳定性测试场景的结果；否则为错误对象。可进行错误处理或其他自定义处理。 &lt;br&gt;返回true表示系统处于稳定性测试场景；返回false表示系统不处于稳定性测试场景。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## 示例

```TypeScript
import { appManager } from '@kit.AbilityKit';

appManager.isRunningInStabilityTest((err, flag) => {
  if (err) {
    console.error(`isRunningInStabilityTest fail, code: ${err.code}, msg:${err.message}`);
  } else {
    console.info(`The result of isRunningInStabilityTest is: ${JSON.stringify(flag)}`);
  }
});
```


## isRunningInStabilityTest

```TypeScript
function isRunningInStabilityTest(): Promise<boolean>
```

查询当前系统是否处于稳定性测试场景。使用Promise异步回调。 > **说明：** > > 稳定性测试场景指为验证应用在复杂、极端或长期运行条件下的可靠性而设计的特定测试环境。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-appManager-function isRunningInStabilityTest(): Promise<boolean>--><!--Device-appManager-function isRunningInStabilityTest(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 以Promise方式返回接口运行结果及当前是否处于稳定性测试场景，可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## 示例

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.isRunningInStabilityTest().then((flag) => {
  console.info(`The result of isRunningInStabilityTest is: ${flag}`);
}).catch((err: Error) => {
  let error=err as BusinessError;
  console.error(`error: code: ${error.code} message: ${error.message}`);
});
```

