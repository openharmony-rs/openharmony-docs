# demoteCurrentFromCandidateMasterProcess

## 导入模块

```TypeScript
import { application } from '@kit.AbilityKit';
```

## demoteCurrentFromCandidateMasterProcess

```TypeScript
export function demoteCurrentFromCandidateMasterProcess(): Promise<void>
```

撤销当前进程的备选主控进程资格。使用Promise异步回调。该接口在PC/2in1、Tablet中可正常调用，在其他设备类型中返回801错误码。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-application-export function demoteCurrentFromCandidateMasterProcess(): Promise<void>--><!--Device-application-export function demoteCurrentFromCandidateMasterProcess(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000116](../errorcode-ability.md#16000116-当前进程已经是主控进程) | The current process is already a master process and does not support cancellation. |
| [16000117](../errorcode-ability.md#16000117-当前进程非备选主控进程) | The current process is not a candidate master process and does not support cancellation. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, application, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      application.demoteCurrentFromCandidateMasterProcess()
        .then(() => {
          console.info('demote succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`demote failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`demoteCurrentFromCandidateMasterProcess failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}

```

