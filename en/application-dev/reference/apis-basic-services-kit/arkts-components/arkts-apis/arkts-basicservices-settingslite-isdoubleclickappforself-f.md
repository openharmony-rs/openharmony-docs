# isDoubleClickAppForSelf

## Modules to Import

```TypeScript
import { settingsLite } from '@kit.BasicServicesKit';
```

## isDoubleClickAppForSelf

```TypeScript
function isDoubleClickAppForSelf(callback: ClickCallback): void
```

1. Checks whether the application started by double-pressing the function key is the application itself.
2. This API is triggered to check whether double-pressing the function key starts the application itself.

**Since:** 24

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Applications.Settings.Core.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ClickCallback](arkts-basicservices-settingslite-clickcallback-i.md) | Yes | Callback used to return the execution result. |
