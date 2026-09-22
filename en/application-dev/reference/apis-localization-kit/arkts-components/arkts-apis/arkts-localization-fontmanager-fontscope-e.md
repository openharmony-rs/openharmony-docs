# FontScope

```TypeScript
enum FontScope
```

An enumeration representing the scope of font application.

**Since:** 26.0.1

**System capability:** SystemCapability.Global.FontManager

## APP

```TypeScript
APP = 0
```

Application-level font. The lifecycle of the font follows that of the application. When the application exits or the font service abnormally terminates, the installed font files will be automatically cleaned up or uninstalled. You must first call [onFontObserver](arkts-localization-fontmanager-onfontobserver-f.md) to register a listener before installing the font.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Global.FontManager

## SESSION

```TypeScript
SESSION = 1
```

Session-level font. The lifecycle of a font is not bound to that of the application. When the device is restarted or the current user logs out (in multi-user scenarios), the installed font file will be automatically deleted or uninstalled.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Global.FontManager
