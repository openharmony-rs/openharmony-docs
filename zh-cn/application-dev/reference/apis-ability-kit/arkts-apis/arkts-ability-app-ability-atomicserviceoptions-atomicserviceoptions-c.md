# AtomicServiceOptions

```TypeScript
export default class AtomicServiceOptions extends StartOptions
```

**AtomicServiceOptions**可以作为[openAtomicService()](arkts-ability-uiabilitycontext-c.md#openatomicservice)的入参，用于携带参数。继承自[StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md)。

**继承/实现关系：** AtomicServiceOptions extends [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md)

**起始版本：** 12

<!--Device-unnamed-export default class AtomicServiceOptions extends StartOptions--><!--Device-unnamed-export default class AtomicServiceOptions extends StartOptions-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { AtomicServiceOptions } from '@kit.AbilityKit';
```

## completionHandlerForAtomicService

```TypeScript
completionHandlerForAtomicService?: CompletionHandlerForAtomicService
```

打开原子化服务结果的操作类，用于接收打开原子化服务的结果。

**类型：** [CompletionHandlerForAtomicService](arkts-ability-app-ability-completionhandlerforatomicservice-completionhandlerforatomicservice-c.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-AtomicServiceOptions-completionHandlerForAtomicService?: CompletionHandlerForAtomicService--><!--Device-AtomicServiceOptions-completionHandlerForAtomicService?: CompletionHandlerForAtomicService-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## flags

```TypeScript
flags?: number
```

系统处理该次启动的方式。例如通过wantConstant.Flags.FLAG_INSTALL_ON_DEMAND表示使用免安装能力。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AtomicServiceOptions-flags?: int--><!--Device-AtomicServiceOptions-flags?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters?: Record<string, Object>
```

表示额外参数描述。具体描述参考[Want](arkts-ability-app-ability-want-want-c.md)中parameters字段描述。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AtomicServiceOptions-parameters?: Record<string, Object>--><!--Device-AtomicServiceOptions-parameters?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

```TypeScript
import { UIAbility, AtomicServiceOptions, common, wantConstant, CompletionHandlerForAtomicService, FailureCode } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let completionHandler: CompletionHandlerForAtomicService = {
      // 原子化服务打开成功的回调处理
      onAtomicServiceRequestSuccess(appId: string) {
        hilog.info(0x0000, 'testTag', `appId:${appId}`);
      },
      // 原子化服务打开失败的回调处理
      onAtomicServiceRequestFailure(appId: string, failureCode: FailureCode, failureMessage: string) {
        hilog.info(0x0000, 'testTag', `appId:${appId}, failureCode:${failureCode}, failureMessage:${failureMessage}`);
      }
    };
    // 定义原子化服务启动选项参数
    let options: AtomicServiceOptions = {
      // 使用免安装能力，目标原子化服务未安装时自动触发安装
      flags: wantConstant.Flags.FLAG_INSTALL_ON_DEMAND,
      parameters: {
        'demo.result': 123456
      },
      completionHandlerForAtomicService: completionHandler
    };

    try {
      let appId: string = '6918661953712445909'; // 根据实际appId修改此值
      this.context.openAtomicService(appId, options) // 打开原子化服务
        .then((result: common.AbilityResult) => {
          // 打开成功后的业务逻辑处理
          console.info('openAtomicService succeed');
        })
        .catch((err: BusinessError) => {
          // 处理打开失败的业务逻辑
          console.error(`openAtomicService failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`openAtomicService failed, code is ${code}, message is ${message}`);
    }
  }
}
```
