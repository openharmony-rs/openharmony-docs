# getFontPathsByType

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## getFontPathsByType

```TypeScript
function getFontPathsByType(fontType: SystemFontType): Array<string>
```

Obtains the paths of all font files of a specified font type.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fontType | [SystemFontType](arkts-arkgraphics2d-text-systemfonttype-e.md) | Yes | Font type. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of font file paths. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct GetFontPathsByTypeTest {
  build() {
    Column({ space: 10 }) {
      Button("get font path")
        .onClick(() => {
          let fontList = text.getFontPathsByType(text.SystemFontType.ALL)
          console.info("file count: " + fontList.length)
          for (let index = 0; index < fontList.length; index++) {
            console.info("file path: " + fontList[index])
          }
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```
