# setDefaultErrorHandler

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## setDefaultErrorHandler

```TypeScript
function setDefaultErrorHandler(defaultHandler?: ErrorHandler) : ErrorHandler
```

发生JS_CRASH异常时，支持链式回调，返回上一次注册的处理器，仅限主线程调用。

如果传入非法参数或在子线程调用，将抛出错误码并返回undefined，因此建议使用try-catch逻辑进行处理。

若接口参数为空，后续注册的处理器将无法与前序已注册的处理器建立关联，从而中断链式调用。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-function setDefaultErrorHandler(defaultHandler?: ErrorHandler) : ErrorHandler--><!--Device-errorManager-function setDefaultErrorHandler(defaultHandler?: ErrorHandler) : ErrorHandler-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| defaultHandler | [ErrorHandler](arkts-ability-errormanager-errorhandler-t.md) | 否 | 新注册的错误处理器，缺省时默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ErrorHandler](arkts-ability-errormanager-errorhandler-t.md) | 返回上一次注册的错误处理器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000205](../errorcode-ability.md#16000205-当前接口未在主线程中调用) | API未在主线程中调用。 |

**示例：**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { process } from '@kit.ArkTS';

let oldHandler: errorManager.ErrorHandler;
const errorHandler: errorManager.ErrorHandler = (reason: Error) => {
  // 自定义的errorHandler实现逻辑
  console.info('[Handler] Uncaught exception handler invoked.');
  if (oldHandler) {
      oldHandler(reason);
  } else {
      // 建议增加判空操作，如果为空采用同步退出方式
      const processManager = new process.ProcessManager();
      processManager.exit(0);
  }
};
oldHandler = errorManager.setDefaultErrorHandler(errorHandler);

```

