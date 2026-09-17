# offFontObserver

## Modules to Import

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## offFontObserver

```TypeScript
function offFontObserver(): void
```

Unregisters the font service death observer.

**Since:** 26.1.0

**Required permissions:** ohos.permission.UPDATE_SCOPE_FONT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Global.FontManager

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [31100110](../errorcode-font-manager.md#31100110-failed-to-call-the-api-due-to-system-errors) | Call failed due to system error. |
| 31100115 | The font observer is not registered. |
