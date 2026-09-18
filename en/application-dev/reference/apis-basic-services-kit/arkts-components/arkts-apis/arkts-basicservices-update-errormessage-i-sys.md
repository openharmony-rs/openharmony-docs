# ErrorMessage (System API)

Represents an error message.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## errorCode

```TypeScript
errorCode: number
```

Error code, which identifies an error type. You can quickly locate the cause of the upgrade failure based on **errorCode** and take corresponding measures. For example, **201** indicates the permission error, **401** indicates the parameter error, and **11500104** indicates the IPC error.

Use scenarios: In the callback of **EVENT_UPGRADE_FAIL**, use **errorCode** to determine the failure cause and handle the error or notify the user. You are advised to analyze and handle the error based on **errorMessage**.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## errorMessage

```TypeScript
errorMessage: string
```

Error message, which provides detailed description of the error. **errorMessage** provides detailed error description, such as 'Permission denied' and 'Parameter verification failed', to help developers understand the cause of the error and perform debugging.

Use scenarios: During error handling, **errorMessage** can be used for log recording, error message display, or error analysis. It is recommended that this parameter be used together with **errorCode**. The **errorCode** parameter defines the error type, and the **errorMessage** parameter provides detailed description.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
