# matchFontDescriptors

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## matchFontDescriptors

```TypeScript
function matchFontDescriptors(desc: FontDescriptor): Promise<Array<FontDescriptor>>
```

Obtains all system font descriptors that match the provided font descriptor. This API uses a promise to return the result.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| desc | [FontDescriptor](arkts-arkgraphics2d-text-fontdescriptor-i.md) | Yes | Font descriptor to match against. If this parameter is left unspecified, all system font descriptors are returned. If a specific value is provided, the matching is performed based on the value provided. If the matching fails, an empty array is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[FontDescriptor](arkts-arkgraphics2d-text-fontdescriptor-i.md)&gt;&gt; | Promise used to return all matched system font descriptors. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'
import { BusinessError } from '@kit.BasicServicesKit'

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button("font descriptor")
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .width(300)
          .height(80)
          .onClick(() => {
            console.info(`Get font descriptor start`)
            let promise = text.matchFontDescriptors({
              weight: text.FontWeight.W400,
            })
            promise.then((data) => {
              console.info(`Font descriptor array size: ${data.length}`);
              console.info(`Font descriptor result: ${JSON.stringify(data)}`)
            }).catch((error: BusinessError) => {
              console.error(`Failed to match the font descriptor, error: ${JSON.stringify(error)}`);
            });
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
