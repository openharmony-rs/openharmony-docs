# AtomicServiceOptions

**AtomicServiceOptions** is used as an input parameter of [openAtomicService()](arkts-ability-uiabilitycontext-c.md#openatomicservice) to carry arguments. It inherits from [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md).

**Inheritance/Implementation:** AtomicServiceOptions extends [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md)

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { AtomicServiceOptions } from '@kit.AbilityKit';
```

## completionHandlerForAtomicService

```TypeScript
completionHandlerForAtomicService?: CompletionHandlerForAtomicService
```

Operation class for receiving the result of opening an atomic service.

**Type:** [CompletionHandlerForAtomicService](arkts-ability-app-ability-completionhandlerforatomicservice-completionhandlerforatomicservice-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

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

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
