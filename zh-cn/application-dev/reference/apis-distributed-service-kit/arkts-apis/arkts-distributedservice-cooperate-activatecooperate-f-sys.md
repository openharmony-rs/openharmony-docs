# activateCooperate（系统接口）

## 导入模块

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

## activateCooperate

```TypeScript
function activateCooperate(targetNetworkId: string, inputDeviceId: int, callback: AsyncCallback<void>): void
```

启动键鼠穿越，使用Callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function activateCooperate(targetNetworkId: string, inputDeviceId: int, callback: AsyncCallback<void>): void--><!--Device-cooperate-function activateCooperate(targetNetworkId: string, inputDeviceId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetNetworkId | string | 是 | 键鼠穿越目标设备描述符。 |
| inputDeviceId | int | 是 | 待穿越输入设备标识符。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，键鼠穿越启动成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [20900001](../../apis-distributedservice-kit/errorcode-devicestatus.md#20900001-操作输入设备失败) | Service exception. Possible causes: <br>1. A system error, such as null pointer, container-related exception, or IPC exception. <br>2. N-API invocation exception or invalid N-API status. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let targetNetworkId = "networkId";
let inputDeviceId = 0;
try {
  cooperate.activateCooperate(targetNetworkId, inputDeviceId, (error: BusinessError) => {
    if (error) {
      console.error(`Start Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
      return;
    }
    console.info(`Start Keyboard mouse crossing success.`);
  });
} catch (error) {
  console.error(`Start Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

ArkTS-Sta示例：

```TypeScript
let targetNetworkId: string = "networkId";
let inputDeviceId: int = 0;
try {
  cooperate.activateCooperate(targetNetworkId, inputDeviceId, (error: BusinessError<void>|null, info: undefined) => {
    if (error) {
      console.error(`Start Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
      return;
    }
    console.info(`Start Keyboard mouse crossing success.`);
  });
} catch (error) {
  console.error(`Start Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```


## activateCooperate

```TypeScript
function activateCooperate(targetNetworkId: string, inputDeviceId: int): Promise<void>
```

启动键鼠穿越，使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function activateCooperate(targetNetworkId: string, inputDeviceId: int): Promise<void>--><!--Device-cooperate-function activateCooperate(targetNetworkId: string, inputDeviceId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetNetworkId | string | 是 | 键鼠穿越目标设备描述符。 |
| inputDeviceId | int | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [20900001](../../apis-distributedservice-kit/errorcode-devicestatus.md#20900001-操作输入设备失败) | Service exception. Possible causes: <br>1. A system error, such as null pointer, container-related exception, or IPC exception. <br>2. N-API invocation exception or invalid N-API status. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let targetNetworkId = "networkId";
let inputDeviceId = 0;
try {
  cooperate.activateCooperate(targetNetworkId, inputDeviceId).then(() => {
    console.info(`Start Keyboard mouse crossing success.`);
  }, (error: BusinessError) => {
    console.error(`Start Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
  });
} catch (error) {
  console.error(`Start Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

ArkTS-Sta示例：

```TypeScript
let targetNetworkId: string = "networkId";
let inputDeviceId: int = 0;
try {
  cooperate.activateCooperate(targetNetworkId, inputDeviceId).then(() => {
    console.info(`Start Keyboard mouse crossing success.`);
  }, (error: Error): void => {
    console.error(`Start Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
  });
} catch (error) {
  console.error(`Start Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

