# WindowSnapshotConfiguration

Describes the configuration of the main window screenshot.

**Since:** 21

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## useCache

```TypeScript
useCache?: boolean
```

Whether the existing screenshot of the main window should be used. The default value is **true**. When it is set to **true**, the system uses the existing screenshot of the main window, or captures the latest screenshot if no existing screenshot is saved. When it is set to **false**, the system captures the latest screenshot of the main window.

**Type:** boolean

**Since:** 21

**System capability:** SystemCapability.Window.SessionManager
