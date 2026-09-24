# FontClientObserver

```TypeScript
interface FontClientObserver
```

Font service status listener.

**Since:** 26.0.1

**System capability:** SystemCapability.Global.FontManager

## Modules to Import

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## onServiceDied

```TypeScript
onServiceDied(): void
```

Callback function called when the font service exits abnormally. Your app can perform operations such as resource cleanup or re-registration in this callback function.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Global.FontManager
