# isFontSupported

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## isFontSupported

```TypeScript
function isFontSupported(fontURL: string | Resource): boolean
```

Checks whether the system supports the specified font file. You can use this API to verify the availability of a font file before loading a custom font, preventing text rendering exceptions caused by unsupported fonts.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fontURL | string &#124; [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | Yes | Path of the font file to be checked. The path must be in the format of "**file://** + Absolute path of the font file" or **$rawfile** (a file path relative to the**resources/rawfile** directory in the project, which includes the font file name). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the system supports the specified font file. **true** means yes; **false** otherwise. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct isFontSupportedTest {
  build() {
    Column({ space: 10 }) {
      Button("is font supported")
        .onClick(() => {
          let filePath = "file:///system/fonts/NotoSansCJK-Regular.ttc"
          let isSupported = text.isFontSupported(filePath)
          console.info("is font supported: " + isSupported)
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```
