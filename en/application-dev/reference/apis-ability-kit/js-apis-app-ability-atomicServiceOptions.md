# @ohos.app.ability.AtomicServiceOptions (Optional Parameters of openAtomicService)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1; @wendel; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=9b45198dbdb6f53f8bf0896d62425626f2442690 translatedAt=2026-09-03T09:59:28.587Z pushedAt=2026-09-05T10:47:30.235Z -->

AtomicServiceOptions can be used as an input parameter of [openAtomicService()](js-apis-inner-application-uiAbilityContext.md#openatomicservice12) to specify the system startup mode (for example, the install-free capability), pass extra parameters, and receive the result callback for opening an atomic service. It inherits from [StartOptions](js-apis-app-ability-startOptions.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { AtomicServiceOptions } from '@kit.AbilityKit';
```

## AtomicServiceOptions

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| [flags](js-apis-app-ability-wantConstant.md#flags) | number | No|  Yes| Mode in which the system processes the startup.<br>For example, **wantConstant.Flags.FLAG_INSTALL_ON_DEMAND** indicates that the installation-free capability is used.|
| parameters | Record\<string, Object> | No|  Yes| Additional parameters. For details, see the **parameters** field in [Want](js-apis-app-ability-want.md).|
| completionHandlerForAtomicService<sup>20+</sup> | [CompletionHandlerForAtomicService](js-apis-app-ability-CompletionHandlerForAtomicService.md) | No | Yes | Operation class for the result of opening an atomic service, used to receive the result of opening an atomic service.<br/>**Atomic service API**: This API is supported in atomic services since API version 20. |

**Example**

```ts
import { UIAbility, AtomicServiceOptions, common, wantConstant, CompletionHandlerForAtomicService, FailureCode } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let completionHandler: CompletionHandlerForAtomicService = {
      // Callback for handling the successful opening of the atomic service.
      onAtomicServiceRequestSuccess(appId: string) {
        hilog.info(0x0000, 'testTag', `appId:${appId}`);
      },
      // Callback for handling the failure to open the atomic service.
      onAtomicServiceRequestFailure(appId: string, failureCode: FailureCode, failureMessage: string) {
        hilog.info(0x0000, 'testTag', `appId:${appId}, failureCode:${failureCode}, failureMessage:${failureMessage}`);
      }
    };
    // Define the startup options of the atomic service.
    let options: AtomicServiceOptions = {
      // Use the install-free capability to automatically trigger installation when the target atomic service is not installed.
      flags: wantConstant.Flags.FLAG_INSTALL_ON_DEMAND,
      parameters: {
        'demo.result': 123456
      },
      completionHandlerForAtomicService: completionHandler
    };

    try {
      let appId: string = '6918661953712445909'; // Use the actual appId.
      this.context.openAtomicService(appId, options) // Open the atomic service.
        .then((result: common.AbilityResult) => {
          // Business logic processing after the atomic service is opened successfully.
          console.info('openAtomicService succeed');
        })
        .catch((err: BusinessError) => {
          // Handle the business logic for the failure to open the atomic service.
          console.error(`openAtomicService failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`openAtomicService failed, code is ${code}, message is ${message}`);
    }
  }
}
```
