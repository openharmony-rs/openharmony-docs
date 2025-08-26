# @ohos.app.ability.AtomicServiceOptions (AtomicServiceOptions)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1; @wendel; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

AtomicServiceOptions可以作为[openAtomicService()](js-apis-inner-application-uiAbilityContext.md#openatomicservice12)的入参，用于携带参数。继承于[StartOptions](js-apis-app-ability-startOptions.md)。

> **说明：**
>
> 本模块首批接口从API version 12 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { AtomicServiceOptions } from '@kit.AbilityKit';
```

## AtomicServiceOptions

**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| [flags](js-apis-app-ability-wantConstant.md#flags) | number | 否 |  是 | 系统处理该次启动的方式。<br />例如通过wantConstant.Flags.FLAG_INSTALL_ON_DEMAND表示使用免安装能力。 |
| parameters | Record\<string, Object> | 否 |  是 | 表示额外参数描述。具体描述参考[Want](js-apis-app-ability-want.md)中parameters字段描述。 |
| completionHandlerForAtomicService<sup>20+</sup> | [CompletionHandlerForAtomicService](./js-apis-app-ability-CompletionHandlerForAtomicService.md) | 否 |  是 | 打开原子化服务结果的操作类，用于接收打开原子化服务的结果。<br/>**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。 |

**示例：**

```ts
import { UIAbility, AtomicServiceOptions, common, wantConstant, CompletionHandlerForAtomicService } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { FailureCode } from '@ohos.app.ability.CompletionHandlerForAtomicService';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let completionHandler: CompletionHandlerForAtomicService = {
      onAtomicServiceRequestSuccess(appId: string) {
        hilog.info(0x0000, 'testTag', `appId:${appId}`);
      },
      onAtomicServiceRequestFailure(appId: string, failureCode: FailureCode, failureMessage: string) {
        hilog.info(0x0000, 'testTag', `appId:${appId}, failureCode:${failureCode}, failureMessage:${failureMessage}`);
      }
    };

    let options: AtomicServiceOptions = {
      flags: wantConstant.Flags.FLAG_INSTALL_ON_DEMAND,
      parameters: {
        'demo.result': 123456
      },
      completionHandlerForAtomicService: completionHandler
    };

    try {
      let appId: string = '6918661953712445909'; // 根据实际appId修改此值
      this.context.openAtomicService(appId, options)
        .then((result: common.AbilityResult) => {
          // 执行正常业务
          console.info('openAtomicService succeed');
        })
        .catch((err: BusinessError) => {
          // 处理业务逻辑错误
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
