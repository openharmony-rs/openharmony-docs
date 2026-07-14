# promoteCurrentToCandidateMasterProcess

## promoteCurrentToCandidateMasterProcess

```TypeScript
export function promoteCurrentToCandidateMasterProcess(insertToHead: boolean): Promise<void>
```

开发者可以调用该接口将当前进程放入[备选主控进程](../../../../application-models/ability-terminology.md#candidatemasterprocess备选主控进程)链表。使用
Promise异步回调。
当[主控进程](../../../../application-models/ability-terminology.md#masterprocess主控进程)销毁后，再次启动配置了isolationProcess为true的
UIAbility/UIExtensionAbility组件时，系统会根据是否存在备选主控进程执行相应操作。

- 如果存在备选主控进程，系统会将备选主控进程链表首节点的进程设置为主控进程，触发
[onNewProcessRequest](arkts-ability-abilitystage-c.md#onnewprocessrequest-1)回调。
- 如果不存在备选主控进程，系统会根据组件类型执行相应的操作。
- 对于UIAbility组件，系统将创建新的空进程作为主控进程。
- 对于UIExtensionAbility组件，系统会优先复用已有的UIExtensionAbility进程作为新的主控进程，无可用进程时则创建新的空进程作为主控进程。
该接口在PC/2in1、Tablet中可正常调用，在其他设备类型中返回801错误码。

> **说明：**
>
> 如果当前进程已经是[主控进程](../../../../application-models/ability-terminology.md#masterprocess主控进程)，调用该接口无效并且不会抛出错误码。
>
> 当前进程只有运行了isolationProcess字段设为true的组件，或曾经成为过主控进程，开发者才可将其设置为备选主控进程。
>
>
> 当前仅支持sys/commonUI类型的UIExtensionAbility组件在[module.json5配置文件](../../../../quick-start/module-configuration-file.md)中配
> 置isolationProcess字段为true。

<!--DelEnd-->

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| insertToHead | boolean | 是 | 表示是否将当前进程放入备选主控进程链表的表头。true表示放入表头，false表示放入表尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000115](../errorcode-ability.md#16000115-当前进程不支持设置为备选主控进程) | The current process cannot be set as a candidate master process. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, application, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      application.promoteCurrentToCandidateMasterProcess(true)
        .then(() => {
          console.info('promote succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`promote failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`promoteCurrentToCandidateMasterProcess failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}

```

