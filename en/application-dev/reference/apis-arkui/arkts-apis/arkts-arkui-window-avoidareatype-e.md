# AvoidAreaType

```TypeScript
enum AvoidAreaType
```

Enumerates the types of areas to avoid for window content.

When adapting window content for an [immersive layout](../../../windowmanager/window-terminology.md#immersive-layout), you should adjust the content based on the corresponding [AvoidArea](arkts-arkui-window-avoidarea-i.md) specified by **AvoidAreaType**.

**Since:** 7

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## TYPE_SYSTEM

```TypeScript
TYPE_SYSTEM = 0
```

Default area of the system. &lt;!--RP11--&gt;It contains the status bar and three-button navigation bar.&lt;!--RP11End--&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## TYPE_CUTOUT

```TypeScript
TYPE_CUTOUT = 1
```

Cutout area.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## TYPE_SYSTEM_GESTURE

```TypeScript
TYPE_SYSTEM_GESTURE = 2
```

Side return gesture area. Currently, no devices support this type of avoid area.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## TYPE_KEYBOARD

```TypeScript
TYPE_KEYBOARD = 3
```

Fixed soft keyboard area.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## TYPE_NAVIGATION_INDICATOR

```TypeScript
TYPE_NAVIGATION_INDICATOR = 4
```

Bottom navigation bar. &lt;!--RP12--&gt;OpenHarmony devices do not support this capability.&lt;!--RP12End--&gt;

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## TYPE_FLOAT_NAVIGATION

```TypeScript
TYPE_FLOAT_NAVIGATION = 5
```

Area for float navigation

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Window.SessionManager
