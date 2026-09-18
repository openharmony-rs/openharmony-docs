# StartupConfig

The module defines the configuration of [AppStartup](../../../application-models/app-startup.md).

**Since:** 12

**System capability:** SystemCapability.Ability.AppStartup

## Modules to Import

```TypeScript
import { StartupConfig } from '@kit.AbilityKit';
```

## startupListener

```TypeScript
startupListener?: StartupListener
```

AppStartup listener, which is called when all the startup tasks are complete.

**Type:** [StartupListener](arkts-ability-app-appstartup-startuplistener-startuplistener-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppStartup

## timeoutMs

```TypeScript
timeoutMs?: number
```

Timeout for executing all startup tasks, measured in ms. The default value is 10000 ms.

**Type:** number

**Default:** 10000

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppStartup
