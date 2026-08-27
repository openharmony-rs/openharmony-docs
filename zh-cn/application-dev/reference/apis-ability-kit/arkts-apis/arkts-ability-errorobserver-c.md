# ErrorObserver

定义异常监听，可以作为 [errorManager.on('error')](arkts-ability-errormanager-on-f.md#onerror) 的入参监听当前应用发生的异常。通过异常监听，开发者可以及时捕获和处理应用运行时的未捕获异常及JS层上报的异常，提升应用的稳定性和用户体验。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onException

```TypeScript
onException?(errObject: Error): void
```

应用产生异常，上报js层时的回调。此回调为可选方法，若未实现，将使用系统默认异常处理逻辑。 可与[ErrorObserver.onUnhandledException](#onunhandledexception)的配合使用，通过errorManager.on('error')注册ErrorObserver对象来实现异常监听。 建议同时实现两个回调方法，用于获取完整的异常信息。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errObject | Error | 是 | 有关异常事件名字、消息和错误堆栈信息的对象。 |

**示例**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errObject) {
    console.error('onUnhandledException, errObject: ', errObject);
  },
  onException(errorObj) {
    console.error('onException, name: ', errorObj.name);
    console.error('onException, message: ', errorObj.message);
    if (typeof (errorObj.stack) === 'string') {
      console.error('onException, stack: ', errorObj.stack);
    }
  }
};

try {
  errorManager.on('error', observer);
} catch (error) {
  console.error(`registerErrorObserver failed, error.code: ${(error as BusinessError).code}, error.message: ${(error as BusinessError).message}`);
}
```

## onUnhandledException

```TypeScript
onUnhandledException(errMsg: string): void
```

应用产生未捕获的异常时的回调。当应用代码发生未捕获的异常时，系统会自动调用此方法，将异常信息传递给开发者进行处理。 与[ErrorObserver.onException](#onexception)的差异在于： onUnhandledException仅捕获未处理的异常，参数仅包含错误消息字符串；而onException会捕获所有上报到JS层的异常，参数为完整的Error对象，包含name、message、stack等更多信息。 建议在需要完整错误信息时使用onException，仅需简单错误消息时使用onUnhandledException。二者可组合使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errMsg | string | 是 | 有关异常的消息和错误堆栈跟踪。 |

**示例**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errMsg) {
    console.error('onUnhandledException, errMsg: ', errMsg);
  }
};

try {
  errorManager.on('error', observer);
} catch (error) {
  console.error(`registerErrorObserver failed, error.code: ${(error as BusinessError).code}, error.message: ${(error as BusinessError).message}`);
}
```
