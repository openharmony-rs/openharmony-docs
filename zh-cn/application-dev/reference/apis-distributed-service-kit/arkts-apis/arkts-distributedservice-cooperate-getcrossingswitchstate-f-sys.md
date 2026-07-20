# getCrossingSwitchState（系统接口）

## 导入模块

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

<a id="getcrossingswitchstate"></a>
## getCrossingSwitchState

```TypeScript
function getCrossingSwitchState(networkId: string, callback: AsyncCallback<boolean>): void
```

获取目标设备键鼠穿越开关的状态，使用Callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getCooperateSwitchState(networkId:](arkts-distributedservice-cooperate-getcooperateswitchstate-f-sys.md#getcooperateswitchstate-1)

<!--Device-cooperate-function getCrossingSwitchState(networkId: string, callback: AsyncCallback<boolean>): void--><!--Device-cooperate-function getCrossingSwitchState(networkId: string, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 键鼠穿越目标设备描述符。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数，返回true表示目标设备键鼠穿越的开关开启，返回false表示开关未开启。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let deviceDescriptor = "networkId";
try {
  cooperate.getCrossingSwitchState(deviceDescriptor, (error: BusinessError, data: boolean) => {
    if (error) {
      console.error(`Get the status failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
      return;
    }
    console.info(`Get the status success, data: ${JSON.stringify(data)}`);
  });
} catch (error) {
  console.error(`Get the status failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```


<a id="getcrossingswitchstate-1"></a>
## getCrossingSwitchState

```TypeScript
function getCrossingSwitchState(networkId: string): Promise<boolean>
```

获取目标设备键鼠穿越开关的状态，使用Promise异步方式返回结果。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getCooperateSwitchState(networkId:](arkts-distributedservice-cooperate-getcooperateswitchstate-f-sys.md#getcooperateswitchstate-1)

<!--Device-cooperate-function getCrossingSwitchState(networkId: string): Promise<boolean>--><!--Device-cooperate-function getCrossingSwitchState(networkId: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 键鼠穿越目标设备描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回true表示目标设备键鼠穿越的开关开启，返回false表示开关未开启。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let deviceDescriptor = "networkId";
try {
  cooperate.getCrossingSwitchState(deviceDescriptor).then((data: boolean) => {
    console.info(`Get the status success, data: ${JSON.stringify(data)}`);
  }, (error: BusinessError) => {
    console.error(`Get the status failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
  });
} catch (error) {
  console.error(`Get the status failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```

