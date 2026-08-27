# WorkSchedulerExtensionContext

WorkSchedulerExtensionContext是WorkSchedulerExtensionAbility的上下文环境，继承自 [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。WorkSchedulerExtensionContext可直接作为WorkSchedulerExtension的上下文环境，提供允许访问特定于WorkSchedulerExtensionAbility的资源的能力。

**继承/实现关系：** WorkSchedulerExtensionContext extends ExtensionContext

**起始版本：** 10

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## startServiceExtensionAbility

```TypeScript
startServiceExtensionAbility(want: Want): Promise<void>
```

启动ServiceExtensionAbility，使用Promise异步回调。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Can not start invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例**

```TypeScript
import { WorkSchedulerExtensionAbility, workScheduler } from '@kit.BackgroundTasksKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want : Want = {
  bundleName: 'com.example.workscheduler',
  abilityName: 'ServiceExtAbility'
}

export default class MyWorkSchedulerExtensionAbility extends WorkSchedulerExtensionAbility {
  onWorkStart(workInfo: workScheduler.WorkInfo) {
    console.info(`onWorkStart, workInfo = ${JSON.stringify(workInfo)}`);
      // 拉起对应的service
      this.context.startServiceExtensionAbility(want).then(() => {
        console.info('succeeded in starting ServiceExtensionAbility.');
      }).catch((err: BusinessError) => {
        console.error(`failed to start ServiceExtensionAbility. Code: ${err.code}, message: ${err.message}`);
      });
  }

  onWorkStop(workInfo: workScheduler.WorkInfo) {
    console.info(`onWorkStop, workInfo is ${JSON.stringify(workInfo)}`);
  }
}
```

## stopServiceExtensionAbility

```TypeScript
stopServiceExtensionAbility(want: Want): Promise<void>
```

停止ServiceExtensionAbility，使用Promise异步回调。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 停止Ability的want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Can not start invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例**

```TypeScript
import { WorkSchedulerExtensionAbility, workScheduler } from '@kit.BackgroundTasksKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want : Want = {
  bundleName: 'com.example.workscheduler',
  abilityName: 'ServiceExtAbility'
}

export default class MyWorkSchedulerExtensionAbility extends WorkSchedulerExtensionAbility {
  onWorkStart(workInfo: workScheduler.WorkInfo) {
    console.info(`onWorkStart, workInfo = ${JSON.stringify(workInfo)}`);
  }

  onWorkStop(workInfo: workScheduler.WorkInfo) {
    console.info(`onWorkStop, workInfo is ${JSON.stringify(workInfo)}`);
      // 停止对应的service
      this.context.stopServiceExtensionAbility(want).then(() => {
        console.info('succeeded in stopping ServiceExtensionAbility.');
      }).catch((err: BusinessError) => {
        console.error(`failed to stop ServiceExtensionAbility. Code: ${err.code}, message: ${err.message}`);
      });
  }
}
```
