# AutoStartupCallback (System API)

The module defines the callback to be invoked when auto-startup is set or canceled for an application component.

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## onAutoStartupOff

```TypeScript
onAutoStartupOff(info: AutoStartupInfo): void
```

Called when the auto-startup setting of an application component is canceled.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [AutoStartupInfo](arkts-ability-autostartupinfo-i-sys.md) | Yes | Information about the target application component. |

**Examples**

```TypeScript
import { autoStartupManager, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Define the auto-startup callback object.
let autoStartupCallback: common.AutoStartupCallback = {
  onAutoStartupOn(info: common.AutoStartupInfo) {
    console.info(`autostartupmanager onAutoStartupOn, info: ${JSON.stringify(info)}.`);
  },
  onAutoStartupOff(info: common.AutoStartupInfo) {
    console.info(`autostartupmanager onAutoStartupOff, info: ${JSON.stringify(info)}.`);
  }
};

// Subscribe to the system auto-startup event.
try {
  autoStartupManager.on('systemAutoStartup', autoStartupCallback);
} catch (err) {
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`autoStartupManager.on failed, err code: ${code}, err msg: ${msg}.`);
}
```

## onAutoStartupOn

```TypeScript
onAutoStartupOn(info: AutoStartupInfo): void
```

Called when auto-startup is set for an application component.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [AutoStartupInfo](arkts-ability-autostartupinfo-i-sys.md) | Yes | Information about the target application component. |

**Examples**

```TypeScript
import { autoStartupManager, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Define the auto-startup callback object.
let autoStartupCallback: common.AutoStartupCallback = {
  onAutoStartupOn(info: common.AutoStartupInfo) {
    console.info(`autostartupmanager onAutoStartupOn, info: ${JSON.stringify(info)}.`);
  },
  onAutoStartupOff(info: common.AutoStartupInfo) {
    console.info(`autostartupmanager onAutoStartupOff, info: ${JSON.stringify(info)}.`);
  }
};

// Subscribe to the system auto-startup event.
try {
  autoStartupManager.on('systemAutoStartup', autoStartupCallback);
} catch (err) {
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`autoStartupManager.on failed, err code: ${code}, err msg: ${msg}.`);
}
```
