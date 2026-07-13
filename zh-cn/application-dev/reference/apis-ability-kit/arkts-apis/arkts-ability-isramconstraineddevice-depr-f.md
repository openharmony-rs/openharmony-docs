# isRamConstrainedDevice

## isRamConstrainedDevice

```TypeScript
function isRamConstrainedDevice(): Promise<boolean>
```

查询当前设备是否为RAM受限设备（内存资源严重受限的设备）。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isRamConstrainedDevice

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 以Promise方式返回接口运行结果及当前设备是否为RAM受限设备，可进行错误处理或其他自定义处理。true：当前设备为RAM受限设备，false：当前设备为非RAM受限设备。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

appManager.isRamConstrainedDevice().then((data) => {
  console.info(`The result of isRamConstrainedDevice is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});

```


## isRamConstrainedDevice

```TypeScript
function isRamConstrainedDevice(callback: AsyncCallback<boolean>): void
```

查询当前设备是否为RAM受限设备（内存资源严重受限的设备）。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isRamConstrainedDevice

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 以回调方式返回接口运行结果及当前设备是否为RAM受限设备，可进行错误处理或其他自定义处理。true：当前设备为RAM受限设备，false：当前设备为非RAM受限设备。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';

appManager.isRamConstrainedDevice((error, data) => {
  if (error && error.code !== 0) {
    console.error(`isRamConstrainedDevice fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`The result of isRamConstrainedDevice is: ${JSON.stringify(data)}`);
  }
});

```

