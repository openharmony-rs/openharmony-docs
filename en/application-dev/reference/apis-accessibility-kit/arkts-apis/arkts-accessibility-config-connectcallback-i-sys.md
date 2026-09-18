# ConnectCallback (System API)

Callback provided when enabling an accessibility extension app through the [config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md) API. The callback is invoked when the connection to the accessibility extension app is disconnected.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## onDisconnect

```TypeScript
onDisconnect: OnDisconnectCallback
```

Callback invoked when the connection to the accessibility extension app is disconnected.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.
