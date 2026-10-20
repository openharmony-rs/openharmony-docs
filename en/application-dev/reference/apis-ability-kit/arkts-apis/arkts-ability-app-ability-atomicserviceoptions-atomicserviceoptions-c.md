# AtomicServiceOptions

```TypeScript
export default class AtomicServiceOptions extends StartOptions
```

**AtomicServiceOptions** is used as an input parameter of [openAtomicService()](arkts-ability-uiabilitycontext-c.md#openatomicservice) to carry arguments. It inherits from [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md).

**Inheritance/Implementation:** AtomicServiceOptions extends [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md)

**Since:** 12

<!--Device-unnamed-export default class AtomicServiceOptions extends StartOptions--><!--Device-unnamed-export default class AtomicServiceOptions extends StartOptions-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { AtomicServiceOptions } from '@kit.AbilityKit';
```

## completionHandlerForAtomicService

```TypeScript
completionHandlerForAtomicService?: CompletionHandlerForAtomicService
```

Operation class for the result of opening an atomic service, used to receive the result of opening an atomic service.

**Type:** [CompletionHandlerForAtomicService](arkts-ability-app-ability-completionhandlerforatomicservice-completionhandlerforatomicservice-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-AtomicServiceOptions-completionHandlerForAtomicService?: CompletionHandlerForAtomicService--><!--Device-AtomicServiceOptions-completionHandlerForAtomicService?: CompletionHandlerForAtomicService-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## flags

```TypeScript
flags?: number
```

Mode in which the system processes the startup. For example, **wantConstant.Flags.FLAG_INSTALL_ON_DEMAND** indicates that the installation-free capability is used.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AtomicServiceOptions-flags?: int--><!--Device-AtomicServiceOptions-flags?: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters?: Record<string, Object>
```

Additional parameters. For details, see the **parameters** field in [Want](arkts-ability-app-ability-want-want-c.md).

**Type:** Record&lt;string, Object&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AtomicServiceOptions-parameters?: Record<string, Object>--><!--Device-AtomicServiceOptions-parameters?: Record<string, Object>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
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
