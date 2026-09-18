# getUIFontConfig

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## getUIFontConfig

```TypeScript
function getUIFontConfig(): UIFontConfig
```

Obtains the UI font configuration information in the system font configuration file.

This API can only obtain the information in the configuration file. If the UI context is not clear, **undefined** may be returned. If you want to obtain the full font configuration information, you are advised to use the [getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-getsystemfontfullnamesbytype-f.md) API of the font engine.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIFontConfig](arkts-arkui-font-uifontconfig-i.md) | Returns the ui font config |
