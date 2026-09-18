# GlobalError

Describes the object related to the exception event name, message, error stack information, exception thread name, and exception thread type.

**Inheritance/Implementation:** GlobalError extends Error

**Since:** 18

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## instanceName

```TypeScript
instanceName: string
```

Name of a VM instance.

**NOTE:** 

Rules for the **instanceName** field in exceptions in the TaskPool thread:

- **globalErrorOccurred** events: identified as "TaskPool Thread + method name".  
- **globalUnhandledRejectionDetected** events: identified as "TaskPool Thread + task name".  
- If identified as "TaskPool Thread" only, the exception occurs within an asynchronous callback.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## instanceType

```TypeScript
instanceType: InstanceType
```

Type of the VM instance.

**Type:** InstanceType

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
