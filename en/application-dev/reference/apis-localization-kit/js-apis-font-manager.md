# @ohos.fontManager (Font Management)

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @OningO-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=df198c6db5ca492edb8da7b67cd549e2c4e6273c translatedAt=2026-11-04T04:13:09.254Z pushedAt=2026-11-04T10:13:14.923Z nl=1 -->

This module provides applications with the capabilities of installing, uninstalling, and querying third-party fonts, as well as listening to font service status. Specifically:
- Installs app-level or session-level font files in `.ttf`, `.ttc`, and `.otf` formats.
- Uninstalls installed fonts based on the font path.
- Queries the scope of installed fonts.
- Registers a font service status change listener to notify the application when the font service exits abnormally.

**Since:** 26.0.1

## Modules to Import

```ts
import { fontManager } from '@kit.LocalizationKit';
```

## FontScope

Enumerates the font scopes.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Global.FontManager

| Name | Value | Description |
| -------- | -------- | -------- |
| APP | 0 | App-level font. The lifecycle of the font follows that of the application. When the application exits or the font service exits abnormally, the installed font file is automatically cleared or uninstalled. You must call [fontManager.onFontObserver](#fontmanageronfontobserver) to register a listener before installing the font. |
| SESSION | 1 | Session-level font. The lifecycle of the font does not follow that of the application. When the device restarts or the current user exits (in a multi-user scenario), the installed font file is automatically cleared or uninstalled. |

## FontClientObserver

Listener for font service status changes.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Global.FontManager

### onServiceDied

onServiceDied(): void

Callback invoked when the Font Service exits abnormally. Applications can perform operations such as resource cleanup or re-registration in this callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Global.FontManager

**Example**

```ts
import { fontManager } from '@kit.LocalizationKit';

const observer: fontManager.FontClientObserver = {
  onServiceDied: () => {
    console.info('font service died');
  }
};
```

## fontManager.installScopeFont

installScopeFont(url: string, scope: FontScope): Promise&lt;void&gt;

Installs the font file at the specified path as an app-level or session-level font. This API uses a promise to return the result.

> **NOTE**
>
> - When installing an app-level font, call [fontManager.onFontObserver](#fontmanageronfontobserver) first to register a font service status change listener.
> - After the installation is successful, the application can use the font by its font name. The same font path cannot be installed repeatedly.
> - PC/2-in-1 and tablet devices support installing a maximum of 800 font files, and other devices support installing a maximum of 200 font files.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.UPDATE_SCOPE_FONT

**System capability:** SystemCapability.Global.FontManager

**Parameters**

| Name | Type | Mandatory | Description |
| ----- | ------ | ---- | ----- |
| url | string | Yes | Path of the font file to install. Only font files in `.ttf`, `.ttc`, and `.otf` formats are supported. |
| scope | [FontScope](#fontscope) | Yes | Scope of the font. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Font Management Error Codes](errorcode-font-manager.md).

| ID | Error Message |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 31100101 | The font does not exist. |
| 31100102 | The font is not supported. |
| 31100103 | Failed to copy the font file. |
| 31100104 | The font file is installed. |
| 31100105 | Exceeded the maximum number of installed files. |
| 31100110 | Call failed due to system error. |
| 31100115 | The font observer is not registered. |

**Example**

```ts
import { fontManager } from '@kit.LocalizationKit';

async function installScopeFont() {
  try {
    await fontManager.installScopeFont('fontPath', fontManager.FontScope.APP);
    console.info('installScopeFont suc');
  } catch (error) {
    console.error('installScopeFont err.' + error.code);
  }
}
```

## fontManager.uninstallScopeFont

uninstallScopeFont(url: string): Promise&lt;void&gt;

Uninstalls an installed app-level or session-level font based on the font path. This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.UPDATE_SCOPE_FONT

**System capability:** SystemCapability.Global.FontManager

**Parameters**

| Name | Type | Mandatory | Description |
| ----- | ------ | ---- | ----- |
| url | string | Yes | Path of the font to uninstall. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Font Management Error Codes](errorcode-font-manager.md).

| ID | Error Message |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 31100108 | Failed to delete the font file. |
| 31100110 | Call failed due to system error. |
| 31100112 | The scope font is not found. |

**Example**

```ts
import { fontManager } from '@kit.LocalizationKit';

async function uninstallScopeFont() {
  try {
    await fontManager.uninstallScopeFont('fontPath');
    console.info('uninstallScopeFont suc');
  } catch (error) {
    console.error('uninstallScopeFont err.' + error.code);
  }
}
```

## fontManager.getFontScope

getFontScope(url: string): Promise&lt;FontScope&gt;

Queries the scope of the font at the specified path. This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.UPDATE_SCOPE_FONT

**System capability:** SystemCapability.Global.FontManager

**Parameters**

| Name | Type | Mandatory | Description |
| ----- | ------ | ---- | ----- |
| url | string | Yes | Path of the font to query. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[FontScope](#fontscope)&gt; | Promise object that returns the scope of the font. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Font Management Error Codes](errorcode-font-manager.md).

| ID | Error Message |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 31100110 | Call failed due to system error. |
| 31100112 | The scope font is not found. |

**Example**

```ts
import { fontManager } from '@kit.LocalizationKit';

async function getFontScope() {
  try {
    let scope = await fontManager.getFontScope('fontPath');
    console.info('font scope is ' + scope);
  } catch (error) {
    console.error('getFontScope err.' + error.code);
  }
}
```

## fontManager.onFontObserver

onFontObserver(observer: FontClientObserver): void

Registers a font service status change listener.

> **NOTE**
>
> - Each application can register only one font service status change listener. Repeated registration will report an error.
> - A maximum of five applications can register simultaneously for the same user. Otherwise, an error will be reported.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.UPDATE_SCOPE_FONT

**System capability:** SystemCapability.Global.FontManager

**Parameters**

| Name | Type | Mandatory | Description |
| ----- | ------ | ---- | ----- |
| observer | [FontClientObserver](#fontclientobserver) | Yes | Font service status change listener. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Font Management Error Codes](errorcode-font-manager.md).

| ID | Error Message |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 31100110 | Call failed due to system error. |
| 31100113 | The font observer is already registered. |
| 31100114 | The maximum number of font observers has been reached. |

**Example**

```ts
import { fontManager } from '@kit.LocalizationKit';

const observer: fontManager.FontClientObserver = {
  onServiceDied: () => {
    console.info('font service died, please clean up resources');
  }
};

try {
  fontManager.onFontObserver(observer);
  console.info('onFontObserver suc');
} catch (error) {
  console.error('onFontObserver err.' + error.code);
}
```

## fontManager.offFontObserver

offFontObserver(): void

Unregisters the font service status change listener.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.UPDATE_SCOPE_FONT

**System capability:** SystemCapability.Global.FontManager

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Font Management Error Codes](errorcode-font-manager.md).

| ID | Error Message |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 31100110 | Call failed due to system error. |
| 31100115 | The font observer is not registered. |

**Example**

```ts
import { fontManager } from '@kit.LocalizationKit';

try {
  fontManager.offFontObserver();
  console.info('offFontObserver suc');
} catch (error) {
  console.error('offFontObserver err.' + error.code);
}
```
