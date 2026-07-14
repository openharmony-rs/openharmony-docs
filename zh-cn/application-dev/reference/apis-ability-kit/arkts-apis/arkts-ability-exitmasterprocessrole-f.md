# exitMasterProcessRole

## exitMasterProcessRole

```TypeScript
export function exitMasterProcessRole(): Promise<void>
```

放弃当前进程的[主控进程](../../../../application-models/ability-terminology.md#masterprocess主控进程)身份。使用Promise异步回调。
该接口仅在2in1、Tablet设备中可正常调用，在其他设备中返回801错误码。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000118](../errorcode-ability.md#16000118-当前进程非主控进程) | Not a master process. |
| [16000119](../errorcode-ability.md#16000119-存在未完成的请求) | Cannot exit because there is an unfinished request. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, application, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      application.exitMasterProcessRole()
        .then(() => {
          console.info('exitMasterProcessRole succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`exitMasterProcessRole failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`exitMasterProcessRole failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}

```

