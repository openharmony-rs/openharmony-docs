# FontCollection

```TypeScript
class FontCollection
```

Represents a font collection, which manages the font resources required for text typesetting. FontCollection provides font matching and glyph lookup capabilities for [ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md), and serves as a fundamental component of the text typesetting pipeline. It provides a global instance ([getGlobalInstance](#getglobalinstance)) and local instances ([getLocalInstance](#getlocalinstance)). Fonts loaded by the global instance are shared within the app, making it suitable for common app scenarios. Local instances are independent of each other, and fonts loaded by a local instance take effect only for that instance without affecting others, making them recommended for widget scenarios. Custom fonts can be loaded through [loadFontSync](#loadfontsync) or [loadFont](#loadfont).

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## clearCaches

```TypeScript
clearCaches(): void
```

Clears the font typesetting cache. The font typesetting cache has a memory limit and an automatic clearing mechanism. It occupies limited memory. You are not advised to clear it unless there are special memory requirements.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button().onClick(() => {
        text.FontCollection.getGlobalInstance().clearCaches();
      })
    }
  }
}
```

## getGlobalInstance

```TypeScript
static getGlobalInstance(): FontCollection
```

Obtains a global **FontCollection** instance.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [FontCollection](arkts-arkgraphics2d-text-fontcollection-c.md) | Global FontCollection instance object of the app, which can be used to manage font loading, unloading, typesetting, and other operations. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let fontCollection = text.FontCollection.getGlobalInstance();
}

@Entry
@Component
struct Index {
  fun: Function = textFunc;
  build() {
    Column() {
      Button().onClick(() => {
        this.fun();
      })
    }
  }
}
```

## getLocalInstance

```TypeScript
static getLocalInstance(): FontCollection
```

Obtains the local **FontCollection** instance. This API is recommended for widgets.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [FontCollection](arkts-arkgraphics2d-text-fontcollection-c.md) | Local FontCollection instance object, recommended for widget scenarios. It can be used to manage font loading, unloading, and typesetting operations. @static |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'
let fontCollection = text.FontCollection.getLocalInstance();
```

## loadFont

```TypeScript
loadFont(name: string, path: string | Resource): Promise<void>
```

Loads the custom font. This API uses a promise to return the result. In this API, **name** specifies the alias of the font, and the custom font effect can be displayed only when the value of **name** is set in **fontFamilies** in **[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)**. The supported font file formats are TTF and OTF.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the font. Any string is acceptable. |
| path | string &#124; [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | Yes | Path of the font file to be loaded. The path must be in the format of "**file://** + Absolute path of the font file" or **$rawfile** (a file path relative to the**resources/rawfile** directory in the project, which includes the font file name). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

let fontCollection: text.FontCollection = new text.FontCollection();

@Entry
@Component
struct RenderTest {
  async loadFontPromise() {
    fontCollection.loadFont('testName', 'file:///system/fonts/a.ttf').then((data) => {
      console.info(`Succeeded in doing loadFont ${JSON.stringify(data)} `);
    }).catch((error: Error) => {
      console.error(`Failed to do loadFont, error: ${JSON.stringify(error)} message: ${error.message}`);
    });
  }

  aboutToAppear() {
    this.loadFontPromise();
  }

  build() {
  }
}
```

## loadFontSync

```TypeScript
loadFontSync(name: string, path: string | Resource): void
```

Loads a custom font. This API returns the result synchronously. In this API, **name** specifies the alias of the font, and the custom font effect can be displayed only when the value of **name** is set in **fontFamilies** in **[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)**. The supported font file formats are TTF and OTF.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the font to be called after the font is loaded. |
| path | string &#124; [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | Yes | Path of the font file to be imported. The path must be in the format of "**file://** + Absolute path of the font file" or **$rawfile** (a file path relative to the**resources/rawfile** directory in the project, which includes the font file name). |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

let fontCollection: text.FontCollection = new text.FontCollection();

@Entry
@Component
struct RenderTest {
  LoadFontSyncTest() {
    fontCollection.loadFontSync('Clock_01', 'file:///system/fonts/HarmonyClock_01.ttf')
    let fontFamilies: Array<string> = ["Clock_01"]
    let myTextStyle: text.TextStyle = {
      fontFamilies: fontFamilies
    };
    let myParagraphStyle: text.ParagraphStyle = {
      textStyle: myTextStyle,
    }
    let paragraphBuilder: text.ParagraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);

    let textData = "Test loadFontSync to load the font file HarmonyClock_01.ttf.";
    paragraphBuilder.addText(textData);
    let paragraph: text.Paragraph = paragraphBuilder.build();
    paragraph.layoutSync(600);
  }

  aboutToAppear() {
    this.LoadFontSyncTest();
  }

  build() {
  }
}
```

## loadFontSyncWithCheck

```TypeScript
loadFontSyncWithCheck(name: string, path: string | Resource, index?: number): void
```

Loads a custom font. This API returns the result synchronously. In this API, **name** specifies the alias of the font, and the custom font effect can be displayed only when the value of **name** is set in **fontFamilies** in **[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)**. The supported font file formats are TTF, OTF, and TTC.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the font. Any string is acceptable. |
| path | string &#124; [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | Yes | Path of the font file to load. Two formats are supported: "file:// + absolute path of the font file" or $rawfile('font file path'). |
| index | number | No | Font index to be loaded when the font file format is TTC. The default value is **0**, indicating that the first font of the TTC file is loaded.<br>The index value of a non-TTC file is meaningless. If an index is specified, the value can only be **0**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-abnormal-parameter-value) | Parameter error. |
| [25900002](../errorcode-drawing.md#25900002-file-not-found) | File not found. |
| [25900003](../errorcode-drawing.md#25900003-failed-to-open-the-file) | Failed to open the file. |
| [25900004](../errorcode-drawing.md#25900004-failed-to-locate-the-file) | File seek failed. |
| [25900005](../errorcode-drawing.md#25900005-failed-to-obtain-the-file-size) | Failed to get the file size. |
| [25900006](../errorcode-drawing.md#25900006-failed-to-read-the-file) | Failed to read the file. |
| [25900007](../errorcode-drawing.md#25900007-empty-file) | Empty file. |
| [25900008](../errorcode-drawing.md#25900008-file-damaged) | Corrupted file. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

let fc: text.FontCollection = text.FontCollection.getGlobalInstance();

@Entry
@Component
struct Index {
  message: string = 'Hello World';
  fontFamily: string = 'family';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontFamily(this.fontFamily)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          fc.loadFontSyncWithCheck(this.fontFamily, 'file:///system/fonts/NotoSansCJK-Regular.ttc', 1);
          try {
            fc.loadFontSyncWithCheck(this.fontFamily, '/system/fonts/NotoSansCJK-Regular.ttc', 1);
          } catch (e) {
            console.error(`Failed to do loadFontWithCheck, error: ${JSON.stringify(e)} message: ${e.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## loadFontWithCheck

```TypeScript
loadFontWithCheck(name: string, path: string | Resource, index?: number): Promise<void>
```

Loads a custom font. This API uses a promise to return the result. In this API, **name** specifies the alias of the font, and the custom font effect can be displayed only when the value of **name** is set in **fontFamilies** in **[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)**. The supported font file formats are TTF, OTF, and TTC.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the font. Any string is acceptable. |
| path | string &#124; [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | Yes | Path of the font file to load. Two formats are supported: "file:// + absolute path of the font file" or $rawfile('font file path'). |
| index | number | No | Font index to be loaded when the font file format is TTC. The default value is **0**, indicating that the first font of the TTC file is loaded.<br>The index value of a non-TTC file is meaningless. If an index is specified, the value can only be **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-abnormal-parameter-value) | Parameter error. |
| [25900002](../errorcode-drawing.md#25900002-file-not-found) | File not found. |
| [25900003](../errorcode-drawing.md#25900003-failed-to-open-the-file) | Failed to open the file. |
| [25900004](../errorcode-drawing.md#25900004-failed-to-locate-the-file) | File seek failed. |
| [25900005](../errorcode-drawing.md#25900005-failed-to-obtain-the-file-size) | Failed to get the file size. |
| [25900006](../errorcode-drawing.md#25900006-failed-to-read-the-file) | Failed to read the file. |
| [25900007](../errorcode-drawing.md#25900007-empty-file) | Empty file. |
| [25900008](../errorcode-drawing.md#25900008-file-damaged) | Corrupted file. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

let fc: text.FontCollection = text.FontCollection.getGlobalInstance();

@Entry
@Component
struct Index {
  message: string = 'Hello World';
  fontFamily: string = 'family';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontFamily(this.fontFamily)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          fc.loadFontWithCheck(this.fontFamily, 'file:///system/fonts/NotoSansCJK-Regular.ttc', 1).then((data) => {
            console.info(`Succeeded in doing loadFontWithCheck ${JSON.stringify(data)} `);
          }).catch((error: Error) => {
            console.error(`Failed to do loadFontWithCheck, error: ${JSON.stringify(error)} message: ${error.message}`);
          });
          fc.loadFontWithCheck(this.fontFamily, '/system/fonts/NotoSansCJK-Regular.ttc', 1).then((data) => {
            console.info(`Succeeded in doing loadFontWithCheck ${JSON.stringify(data)} `);
          }).catch((error: Error) => {
            console.error(`Failed to do loadFontWithCheck, error: ${JSON.stringify(error)} message: ${error.message}`);
          });
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## setParagraphCachesEnabled

```TypeScript
setParagraphCachesEnabled(enable: boolean): void
```

Sets whether to enable the typesetting paragraph caching. Typesetting paragraph caching can accelerate the typesetting of repeated text, but it will occupy extra memory. Before this API is called, the system enables typesetting paragraph caching by default.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the typesetting paragraph caching. **true** to enable; **false** otherwise. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('Enable Paragraph Caching').onClick(() => {
        text.FontCollection.getGlobalInstance().setParagraphCachesEnabled(true);
      })
      Button('Disable Paragraph Caching').onClick(() => {
        text.FontCollection.getGlobalInstance().setParagraphCachesEnabled(false);
      })
    }
  }
}
```

## unloadFont

```TypeScript
unloadFont(name: string): Promise<void>
```

Uninstalls a specified custom font. This API uses a promise to return the result.

After this API is called to unload a custom font corresponding to a font alias, the custom font is no longer available.

All layout objects that use the font alias must be destroyed and recreated.

- Unloading a non-existent font alias does not produce any effect and does not throw an error.  
- This operation only affects future font usage.  
- Unloading a font that is currently in use may lead to text rendering exceptions (such as garbled characters or  
missing glyphs).

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Alias of the font to be uninstalled, which is the same as the alias used when the font is loaded. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct UnloadFontTest {
  private fc: text.FontCollection = text.FontCollection.getGlobalInstance();
  @State content: string = "Default font"

  build() {
    Column({ space: 10 }) {
      Text(this.content)
        .fontFamily("custom")
      Button("load font")
        .onClick(async () => {
          await this.fc.loadFont("custom", "file:///system/fonts/NotoSansCJK-Regular.ttc")
          this.content = "Custom font"
        })
      Button("unload font")
        .onClick(async () => {
          await this.fc.unloadFont("custom")
          this.content = "Default font"
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```

## unloadFontSync

```TypeScript
unloadFontSync(name: string): void
```

Uninstalls a specified custom font. This API is synchronous.

After this API is called to unload a custom font corresponding to a font alias, the custom font is no longer available.

All layout objects that use the font alias must be destroyed and recreated.

- Unloading a non-existent font alias does not produce any effect and does not throw an error.  
- This operation only affects future font usage.  
- Unloading a font that is currently in use may lead to text rendering exceptions (such as garbled characters or  
missing glyphs).

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Font alias to be unregistered, which is the same as the alias used for loading the font. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct UnloadFontSyncTest {
  private fc: text.FontCollection = text.FontCollection.getGlobalInstance();
  @State content: string = "Default font"

  build() {
    Column({ space: 10 }) {
      Text(this.content)
        .fontFamily("custom")
      Button("load font")
        .onClick(() => {
          this.fc.loadFontSync("custom", "file:///system/fonts/NotoSansCJK-Regular.ttc")
          this.content = "Custom font"
        })
      Button("unload font")
        .onClick(() => {
          this.fc.unloadFontSync("custom")
          this.content = "Default font"
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```
