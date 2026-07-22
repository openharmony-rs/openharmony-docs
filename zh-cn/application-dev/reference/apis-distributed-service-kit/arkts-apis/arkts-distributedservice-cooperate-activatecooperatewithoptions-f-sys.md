# activateCooperateWithOptions（系统接口）

## 导入模块

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

## activateCooperateWithOptions

```TypeScript
function activateCooperateWithOptions(targetNetworkId: string, inputDeviceId: number,
    cooperateOptions?: CooperateOptions
  ): Promise<void>
```

启动键鼠穿越，使用选项开始屏幕跳转。

**起始版本：** 20

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function activateCooperateWithOptions(targetNetworkId: string, inputDeviceId: int,    cooperateOptions?: CooperateOptions  ): Promise<void>--><!--Device-cooperate-function activateCooperateWithOptions(targetNetworkId: string, inputDeviceId: int,    cooperateOptions?: CooperateOptions  ): Promise<void>-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetNetworkId | string | 是 | 键鼠穿越目标设备描述符。 |
| inputDeviceId | number | 是 | 发起穿越操作的输入设备ID。 |
| cooperateOptions | [CooperateOptions](arkts-distributedservice-cooperate-cooperateoptions-i-sys.md) | 否 | 穿越可选控制参数，用于控制穿出点具体位置等。不设置此参数时，本接口能力与[cooperate.activateCooperate](arkts-distributedservice-cooperate-activatecooperate-f-sys.md#activatecooperate)相同。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [20900001](../../apis-input-kit/errorcode-cooperator.md#20900001-服务异常) | Service exception. Possible causes:<br>1. A system error, such as null pointer, container-related exception, or IPC exception.<br>2. N-API invocation exception or invalid N-API status. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let targetNetworkId = "networkId";
let inputDeviceId = 0;
try {
  cooperate.activateCooperateWithOptions(targetNetworkId, inputDeviceId).then(() => {
    console.info(`activateCooperateWithOptions success.`);
  }, (error: BusinessError) => {
    console.error(`activateCooperateWithOptions, error: ${JSON.stringify(error, [`code`, `message`])}`);
  });
} catch (error) {
  console.error(`activateCooperateWithOptions, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```

