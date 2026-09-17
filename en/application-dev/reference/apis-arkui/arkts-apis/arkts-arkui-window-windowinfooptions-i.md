# WindowInfoOptions

Filter criteria for window information.

**Since:** 26.0.0

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## excludeSystemWindows

```TypeScript
excludeSystemWindows?: boolean
```

Whether the result excludes system windows. If true, the result list does not include system windows; if false, the result list includes system windows.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Window.SessionManager

## foregroundAboveWindow

```TypeScript
foregroundAboveWindow?: number
```

Only include windows with a higher z-order than the specified window ID. When this field is set to the default value 0, this field is not used as a filter criterion.

**Type:** number

**Default:** 0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Window.SessionManager

## foregroundBelowWindow

```TypeScript
foregroundBelowWindow?: number
```

Only include windows with a lower z-order than the specified window ID. When this field is set to the default value 0, this field is not used as a filter criterion.

**Type:** number

**Default:** 0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Window.SessionManager
