# Class (Font)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=89682c631d1be2b78acdb9477c9eda01133e0baf translatedAt=2026-08-05T03:07:56.644Z pushedAt=2026-08-05T06:42:12.048Z -->

The Font class manages custom font and system font information, supporting functions such as registering custom fonts, obtaining the system font list, and querying detailed font information. It is applicable to scenarios where custom fonts need to be used in an app or system font resources need to be queried.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 10.
>
> - For the following APIs, you must first use [getFont()](./arkts-apis-uicontext-uicontext.md#getfont) in **UIContext** to obtain a **Font** object, and then call the APIs using the obtained object.
>
> - You are advised to use the [loadFontSync](../apis-arkgraphics2d/js-apis-graphics-text.md#loadfontsync) API of the font engine to register custom fonts.

## registerFont

registerFont(options: font.FontOptions): void

Registers a custom font with the font manager.

You are advised to use the [loadFontSync](../apis-arkgraphics2d/js-apis-graphics-text.md#loadfontsync) API of the font engine to register the custom font.

This API is asynchronous. Font registration is an asynchronous process and does not support concurrent calls. Since registration is completed asynchronously, it is recommended to call this API in advance during the page initialization phase (such as aboutToAppear) to ensure that the font is registered before use.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description         |
| ------- | ---------------------------------------- | ---- | ----------- |
| options | [font.FontOptions](js-apis-font.md#fontoptions) | Yes    | Custom font information to register.<br>**Note**<br>The path for the font file to register needs to be set. When reading resources within the system sandbox directory, it is recommended to use a string with the **file://** path prefix. Ensure that the file exists under the sandbox directory path and has read permissions. |

**Example**

<!--code_no_check-->

```ts
// xxx.ets
import { Font } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  private uiContext: UIContext = this.getUIContext();
  private font: Font = this.uiContext.getFont();

  aboutToAppear() {
    this.font.registerFont({
      familyName: 'medium',
      familySrc: '/font/medium.ttf' // The font folder is at the same level as the pages folder.
    });
  }

  build() {
    Column() {
      Text(this.message)
        .align(Alignment.Center)
        .fontSize(20)
        .fontFamily('medium') // Name of the registered custom font. Call registerFont to register the font before using this font name.
    }.width('100%')
  }
}
```

## getSystemFontList

getSystemFontList(): Array\<string> 

Obtains the list of supported fonts.

This API only takes effect on PCs/2-in-1 devices and returns an empty array on other devices.

You are advised to use the [getSystemFontFullNamesByType](../apis-arkgraphics2d/js-apis-graphics-text.md#textgetsystemfontfullnamesbytype14) API to obtain the latest system-supported font list data.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type            | Description       |
| -------------- | --------- |
| Array\<string> | List of system-supported font names. The returned names can be used with the **getFontByName** method to query detailed information about the corresponding fonts. |

**Example**

<!--code_no_check-->

```ts
// xxx.ets
import { Font } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private uiContext: UIContext = this.getUIContext();
  private font: Font = this.uiContext.getFont();
  fontList: Array<string> = new Array<string>();

  build() {
    Column() {
      Button("getSystemFontList")
        .width('60%')
        .height('6%')
        .onClick(() => {
          this.fontList = this.font.getSystemFontList();
          console.info('getSystemFontList', JSON.stringify(this.fontList));
        })
    }.width('100%')
  }
}
```

## getFontByName

getFontByName(fontName: string): font.FontInfo

Obtains information about a system font based on the font name.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description     |
| -------- | ------ | ---- | ------- |
| fontName | string | Yes | System font name, which can be obtained through the [getSystemFontList()](#getsystemfontlist) method. |

**Return value**

| Type                                     | Description          |
| ----------------------------------------- | -------------- |
| [font.FontInfo](js-apis-font.md#fontinfo10) | Detailed information about the font.<br>If the font cannot be found, **undefined** is returned. |

**Example**

<!--code_no_check-->

```ts
// xxx.ets
import { Font, font } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private uiContext: UIContext = this.getUIContext();
  private font: Font = this.uiContext.getFont();
  fontInfo: font.FontInfo = this.font.getFontByName('');

  build() {
    Column() {
      Button("getFontByName")
        .width('60%')
        .height('6%')
        .onClick(() => {
          this.fontInfo = this.font.getFontByName('HarmonyOS Sans Italic');
          console.info("getFontByName(): path = " + this.fontInfo.path);
          console.info("getFontByName(): postScriptName = " + this.fontInfo.postScriptName);
          console.info("getFontByName(): fullName = " + this.fontInfo.fullName);
          console.info("getFontByName(): family = " + this.fontInfo.family);
          console.info("getFontByName(): subfamily = " + this.fontInfo.subfamily);
          console.info("getFontByName(): weight = " + this.fontInfo.weight);
          console.info("getFontByName(): width = " + this.fontInfo.width);
          console.info("getFontByName(): italic = " + this.fontInfo.italic);
          console.info("getFontByName(): monoSpace = " + this.fontInfo.monoSpace);
          console.info("getFontByName(): symbolic = " + this.fontInfo.symbolic);
        })
    }.width('100%')
  }
}
```