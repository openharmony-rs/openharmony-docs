# getFontUnicodeSet

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## getFontUnicodeSet

```TypeScript
function getFontUnicodeSet(path: string | Resource, index: number) : Promise<Array<number>>
```

Obtains an array of font Unicode by font file path. This API uses a promise to return the result.

An empty array is returned if the font file is not found, the font file path is invalid, the font file does not have the required permission, or the file is not in the font format.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string &#124; [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | Yes | Path of the font file to query, which must be "file:// + absolute path of the font file" or $rawfile('file name in the resources/rawfile directory of the project'). |
| index | number | Yes | Index of the font to load when the font file format is ttc/otc. The value ranges from 0 to count-1, where count is the number of fonts contained in the font file. For non-ttc/otc files, the index can only be 0. If this parameter is negative or exceeds the actual index range of the font file, an empty array is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the Unicode array corresponding to the font file. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct GetFontUnicodeSetTest {
  build() {
    Column({ space: 10 }) {
      Button("get fontUnicode")
        .onClick(() => {
          let promise = text.getFontUnicodeSet("file:///system/fonts/HMSymbolVF.ttf", 0)
          promise.then((unicodeSet) => {
            for (let index = 0; index < unicodeSet.length; index++) {
              console.info(unicodeSet[index].toString())
            }
          })
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```
