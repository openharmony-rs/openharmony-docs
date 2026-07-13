# getAppMemorySize

## getAppMemorySize

```TypeScript
function getAppMemorySize(): Promise<number>
```

获取当前应用程序可以使用的最大内存（RAM）值。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getAppMemorySize

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 当前应用程序可以使用的最大内存（RAM）值，可根据此值进行错误处理或其他自定义处理，单位是M。使用Promise异步回调。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

appManager.getAppMemorySize().then((data) => {
  console.info(`The size of app memory is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});

```


## getAppMemorySize

```TypeScript
function getAppMemorySize(callback: AsyncCallback<number>): void
```

获取当前应用程序可以使用的最大内存（RAM）值。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getAppMemorySize

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;number&gt; | 是 | 获取当前应用程序可以使用的最大内存（RAM）值，可根据此值进行错误处理或其他自定义处理，单位是M。使用callback异步回调。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';

appManager.getAppMemorySize((error, data) => {
  if (error && error.code !== 0) {
    console.error(`getAppMemorySize fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`The size of app memory is: ${JSON.stringify(data)}`);
  }
});

```

