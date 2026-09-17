# getSystemFontList

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## getSystemFontList

```TypeScript
function getSystemFontList(): Array<string>
```

Obtains this system font list.

This API only takes effect on PCs/2-in-1 devices and returns an empty array on other devices.

You are advised to use the [getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-getsystemfontfullnamesbytype-f.md) API to obtain the latest system-supported font list data.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getFont](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Font](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** getSystemFontList

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of supported fonts. |

**Examples**

```TypeScript
// xxx.ets
import { font } from '@kit.ArkUI';

@Entry
@Component
struct FontExample {
  fontList: Array<string> = new Array<string>();

  build() {
    Column() {
      Button("getSystemFontList")
        .width('60%')
        .height('6%')
        .onClick(() => {
          this.fontList = font.getSystemFontList(); // You are advised to use the this.getUIContext().getFont().getSystemFontList() API.
        })
    }.width('100%')
  }
}
```
