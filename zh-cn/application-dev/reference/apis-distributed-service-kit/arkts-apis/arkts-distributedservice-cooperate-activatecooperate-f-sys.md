# activateCooperate（系统接口）

## 导入模块

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

## activateCooperate

```TypeScript
function activateCooperate(targetNetworkId: string, inputDeviceId: number, callback: AsyncCallback<void>): void
```

启动键鼠穿越，使用Callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.COOPERATE_MANAGER

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetNetworkId | string | 是 | 键鼠穿越目标设备描述符。 |
| inputDeviceId | number | 是 | 待穿越输入设备标识符。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，键鼠穿越启动成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified.  2. Incorrect parameter types.  3. Parameter verification failed. |
| [20900001](../errorcode-devicestatus.md#20900001-操作输入设备失败) | Service exception. Possible causes:  1. A system error, such as null pointer, container-related exception, or IPC exception.  2. N-API invocation exception or invalid N-API status. |

**示例**

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


## activateCooperate

```TypeScript
function activateCooperate(targetNetworkId: string, inputDeviceId: number): Promise<void>
```

启动键鼠穿越，使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.COOPERATE_MANAGER

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetNetworkId | string | 是 | 键鼠穿越目标设备描述符。 |
| inputDeviceId | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified.  2. Incorrect parameter types.  3. Parameter verification failed. |
| [20900001](../errorcode-devicestatus.md#20900001-操作输入设备失败) | Service exception. Possible causes:  1. A system error, such as null pointer, container-related exception, or IPC exception.  2. N-API invocation exception or invalid N-API status. |

**示例**

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
