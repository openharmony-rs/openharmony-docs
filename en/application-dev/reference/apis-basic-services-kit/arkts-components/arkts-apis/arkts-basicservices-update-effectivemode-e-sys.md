# EffectiveMode (System API)

```TypeScript
export enum EffectiveMode
```

Enumerates effective modes.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## COLD

```TypeScript
COLD = 1
```

Cold upgrade, which takes effect after the device is restarted. This mode applies to scenarios where a complete system reset or firmware upgrade is required. For details, see [Upgrading Service Terms] (../../../basic-services/update/update-kit-term.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## LIVE

```TypeScript
LIVE = 2
```

Hot upgrade, which takes effect without requiring restarting the device. This mode applies to scenarios where app -layer components need to be upgraded or the device needs to keep running. For details, see [Upgrading Service Terms](../../../basic-services/update/update-kit-term.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## LIVE_AND_COLD

```TypeScript
LIVE_AND_COLD = 3
```

Integrated upgrade, which combines the characteristics of both hot and cold upgrades. This mode applies to scenarios where both hot and cold upgrade components are involved. For details, see [Upgrading Service Terms] (../../../basic-services/update/update-kit-term.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
