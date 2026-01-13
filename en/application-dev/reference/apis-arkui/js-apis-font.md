# @ohos.font (Custom Font Registration)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

The **font** module provides APIs for registering custom fonts.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is ambiguous](../../ui/arkts-global-interface.md#ambiguous-ui-context). For details, see [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - You are advised to use the [loadFontSync](../apis-arkgraphics2d/js-apis-graphics-text.md#loadfontsync) API of the font engine to register custom fonts.

## Modules to Import

```ts
import { font } from '@kit.ArkUI';
```

## font.registerFont<sup>(deprecated)</sup>

registerFont(options: FontOptions): void

Registers a custom font with the font manager.

This API is asynchronous and does not support concurrent calls.

> **NOTE**
>
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use [registerFont](arkts-apis-uicontext-font.md#registerfont) instead. Before calling this API, you need to obtain the [Font](arkts-apis-uicontext-font.md) object using the [getFont](arkts-apis-uicontext-uicontext.md#getfont) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using **registerFont** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context).
>
> - Since API version 10, you can use the [getFont](arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Font](arkts-apis-uicontext-font.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                         | Mandatory  | Description         |
| ------- | --------------------------- | ---- | ----------- |
| options | [FontOptions](#fontoptions) | Yes   | Information about the custom font to register.|

## FontOptions

Information about the custom font to register.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type    | Read-Only| Optional  | Description          |
| ---------- | ------ | ---- | ---- | ------------ |
| familyName | string \| [Resource](arkui-ts/ts-types.md#resource)<sup>10+</sup> | No | No | Name of the custom font to register.  |
| familySrc  | string \| [Resource](arkui-ts/ts-types.md#resource)<sup>10+</sup> | No | No | Path of the custom font file to register.<br>**NOTE**<br>If the font file to specify is a resource located within the system sandbox directory, you are advised to use a string with the **file://** path prefix. Ensure the target file exists in the sandbox path and has read permissions granted.|

> **NOTE**
>
> Directly using **font** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the [Font](arkts-apis-uicontext-font.md) object associated with the current UI context by using the [getFont](./arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](./arkts-apis-uicontext-uicontext.md).

**Example**

```ts
// xxx.ets
@Entry
@Component
struct FontExample {
  @State message: string = 'Hello World';
  // iconFont example, where 0000 is the Unicode character of the specified icon. You need to obtain the Unicode character from the TTF file of the registered iconFont.
  @State unicode: string = '\u0000';
  @State codePoint: string = String.fromCharCode(0x0000);
  private uiContext: UIContext = this.getUIContext();

  aboutToAppear() {
    // Both familyName and familySrc support the Resource type.
    this.uiContext.getFont().registerFont({
      // You are advised to use this.getUIContext().getFont().registerFont().
      // Replace 'app.string.font_name' and 'app.string.font_src' with the actual resource strings.
      familyName: $r('app.string.font_name'),
      familySrc: $r('app.string.font_src')
    })

    // familySrc supports the RawFile type.
    this.uiContext.getFont().registerFont({
      familyName: 'mediumRawFile',
      familySrc: $rawfile('font/medium.ttf')// 'font/medium.ttf' is used only as an example. Replace it with the font resource file you use.
    })

    // Register iconFont.
    this.uiContext.getFont().registerFont({
      familyName: 'iconFont',
      familySrc: '/font/iconFont.ttf'
    })

    // Both familyName and familySrc support the string type.
    this.uiContext.getFont().registerFont({
      familyName: 'medium',
      familySrc: '/font/medium.ttf' // The font folder is at the same level as the pages folder.
    })
  }

  build() {
    Column() {
      Text(this.message)
        .align(Alignment.Center)
        .fontSize(20)
        .fontFamily('medium') // medium: name of the registered custom font. (Registered fonts such as $r('app.string.mediumFamilyName') and 'mediumRawFile' can also be used.)

      // Two methods of using iconFont
      Text(this.unicode)
        .align(Alignment.Center)
        .fontSize(20)
        .fontFamily('iconFont')
      Text(this.codePoint)
        .align(Alignment.Center)
        .fontSize(20)
        .fontFamily('iconFont')
    }.width('100%')
  }
}
```
> **NOTE**
>
> To use custom fonts globally in an application, register the fonts through the [windowStage.loadContent](arkts-apis-window-Window.md#loadcontent9) API in the [onWindowStageCreate](../apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagecreate) lifecycle callback in the **EntryAbility.ets** file.
>
> In HSP projects, avoid using relative paths to register custom fonts. For details, see [Accessing Resources in an HSP Through $r](../../quick-start/in-app-hsp.md).

## font.getSystemFontList<sup>(deprecated)</sup>

getSystemFontList(): Array\<string>

Obtains the system font list.

This API only takes effect on PCs/2-in-1 devices and returns an empty array on other devices.

You are advised to use the [getSystemFontFullNamesByType](../apis-arkgraphics2d/js-apis-graphics-text.md#textgetsystemfontfullnamesbytype14) API to obtain the latest system-supported font list data.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [getSystemFontList](arkts-apis-uicontext-font.md#getsystemfontlist) instead. Before calling this API, you need to obtain the [Font](arkts-apis-uicontext-font.md) object using the [getFont](arkts-apis-uicontext-uicontext.md#getfont) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using **getSystemFontList** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context).
>
> - Since API version 10, you can use the [getFont](arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Font](arkts-apis-uicontext-font.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                | Description              |
| -------------------- | ----------------- |
| Array\<string>       | List of supported fonts. |

> **NOTE**
>
> Directly using **font** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the [Font](arkts-apis-uicontext-font.md) object associated with the current UI context by using the [getFont](arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](arkts-apis-uicontext-uicontext.md).

**Example**

<!--deprecated_code_no_check-->

```ts
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

## font.getFontByName<sup>(deprecated)</sup>

getFontByName(fontName: string): FontInfo

Obtains information about a system font based on the font name.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [getFontByName](arkts-apis-uicontext-font.md#getfontbyname) instead. Before calling this API, you need to obtain the [Font](arkts-apis-uicontext-font.md) object using the [getFont](arkts-apis-uicontext-uicontext.md#getfont) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using **getFontByName** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context).
>
> - Since API version 10, you can use the [getFont](arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Font](arkts-apis-uicontext-font.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type     | Mandatory   | Description         |
| ---------- | --------- | ------- | ------------ |
| fontName   | string    | Yes     | System font name.|

**Return value**

| Type            | Description                         |
| ---------------- | ---------------------------- |
| FontInfo         | Information about the system font.    |

## FontInfo<sup>10+</sup>

Information about the system font.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------------------------- | ------------------------- | ------------------------- |
| path           | string  | No| No| File path of the system font.       |
| postScriptName | string  | No| No| PostScript name of the system font.|
| fullName       | string  | No| No| Name of the system font.          |
| family         | string  | No| No| Family of the system font.      |
| subfamily      | string  | No| No| Subfamily of the system font.     |
| weight         | number  | No| No| Weight of the system font.<br>Value range: [100, 900], with intervals of 100, corresponding to the values in the [FontWeight](../apis-arkgraphics2d/js-apis-graphics-text.md#fontweight) enum<br>Default value: **100**       |
| width          | number  | No| No| Width of the system font.<br>Value range: [1, 9], with intervals of 1, corresponding to the values in the [FontWidth](../apis-arkgraphics2d/js-apis-graphics-text.md#fontwidth) enum   |
| italic         | boolean | No| No| Whether the system font is italic.<br>Default value: **false**<br>**true**: The system font is italic. **false**: The system font is not italic.         |
| monoSpace      | boolean | No| No| Whether the system font is monospaced.<br>Default value: **false**<br>**true**: The system font is monospaced. **false**: The system font is not monospaced.        |
| symbolic       | boolean | No| No| Whether the system font supports symbols.<br>Default value: **false**<br>**true**: The system font supports symbols. **false**: The system font does not support symbols. |

**Example**

> **NOTE**
>
> Directly using **font** can lead to the issue of ambiguous UI context. To avoid this, obtain the [Font](arkts-apis-uicontext-font.md) object associated with the current UI context by using the [getFont](./arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](./arkts-apis-uicontext-uicontext.md).

```ts
// xxx.ets
import { font } from '@kit.ArkUI';

@Entry
@Component
struct FontExample {
  fontList: Array<string> = new Array<string>();
  uiFont = this.getUIContext().getFont();
  fontInfo: font.FontInfo = this.uiFont.getFontByName(''); // You are advised to use the this.getUIContext().getFont().getFontByName() API.

  build() {
    Column() {
      Button("getFontByName")
        .onClick(() => {
          this.fontInfo =
            this.uiFont.getFontByName('HarmonyOS Sans Italic');
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

## font.getUIFontConfig<sup>11+</sup>
getUIFontConfig() : UIFontConfig

Obtains the UI font configuration of the system.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**
| Type            | Description                         |
| ---------------- | ---------------------------- |
| [UIFontConfig](#uifontconfig11)     | UI font configuration of the system.         |

## UIFontConfig<sup>11+</sup>

UI font configuration of the system.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full
| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------------------------- | ------- | ------------------------- |
| fontDir        | Array\<string>  | No| No| Path to the system font file.     |
| generic | Array\<[UIFontGenericInfo](#uifontgenericinfo11)>  | No| No| List of supported generic font families.|
| fallbackGroups       | Array\<[UIFontFallbackGroupInfo](#uifontfallbackgroupinfo11)>  | No| No| List of fallback generic font families.          |

## UIFontGenericInfo<sup>11+</sup>

Defines a list of supported generic font families.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full
| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------------------------- | ------------------------- | ------------------------- |
| family        | string | No| No| Font family name, which is the value of **family** specified in the font file.     |
| alias        | Array\<[UIFontAliasInfo](#uifontaliasinfo11)>  | No| No| Font alias configuration information.|
| adjust       | Array\<[UIFontAdjustInfo](#uifontadjustinfo11)>  | No| No| Weight of the font when displayed, which corresponds to the original weight.|

## UIFontFallbackGroupInfo<sup>11+</sup>

Defines a list of fallback generic font families.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full
| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------------------------- | ------------------------- | ------------------------- |
| fontSetName  | string | No| No| Name of the font family corresponding to the fallback fonts.     |
| fallback        | Array\<[UIFontFallbackInfo](#uifontfallbackinfo11)>  | No| No| Fallback fonts for the font family. If **fontSetName** is **""**, it indicates that the fonts can be used as fallback fonts for all font families.|

## UIFontAliasInfo<sup>11+</sup>

Defines font alias configuration information.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full
| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------- | ------------------------- | ------------------------- |
| name          | string  | No| No| Alias name.     |
| weight        | number  | No| No| Weight of the fonts included in the font family. If the value is greater than 0, the font family contains only the fonts with the specified weight. If the value is 0, the font family contains all fonts.<br>Valid values are **0**, **100**, **400**, **700**, and **900**.|

## UIFontAdjustInfo<sup>11+</sup>

Provides a mapping list between the original weight value of a font and the actual displayed weight value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full
| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------- | ------------------------- | ------------------------- |
| weight        | number  | No| No| Original weight of the font.<br>Valid values are **50**, **80**, **100**, and **200**.     |
| to            | number  | No| No| Weight of the font displayed in the application.<br>Valid values are **100**, **400**, **700**, and **900**.|

## UIFontFallbackInfo<sup>11+</sup>

Provides the fallback font of the font set.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full
| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------- | ------------------------- | ------------------------- |
| language       | string  | No| No| Language supported by the font family. The language format is BCP 47.   |
| family         | string  | No| No| Font family name, which is the value of **family** specified in the font file.|

**Example**

```ts
// xxx.ets
import { font } from '@kit.ArkUI';

@Entry
@Component
struct FontExample {
  build() {
    Column() {
      Button("getUIFontConfig")
        .width('60%')
        .height('6%')
        .margin(50)
        .onClick(() => {
          let fontConfig = font.getUIFontConfig();
          console.info("font-dir -----------" + String(fontConfig.fontDir.length));
          for (let i = 0; i < fontConfig.fontDir.length; i++) {
            console.info(fontConfig.fontDir[i]);
          }
          console.info("generic-------------" + String(fontConfig.generic.length));
          for (let i = 0; i < fontConfig.generic.length; i++) {
            console.info("family:" + fontConfig.generic[i].family);
            for (let j = 0; j < fontConfig.generic[i].alias.length; j++) {
              console.info(fontConfig.generic[i].alias[j].name + " " + fontConfig.generic[i].alias[j].weight);
            }
            for (let j = 0; j < fontConfig.generic[i].adjust.length; j++) {
              console.info(fontConfig.generic[i].adjust[j].weight + " " + fontConfig.generic[i].adjust[j].to);
            }
          }
          console.info("fallback------------" + String(fontConfig.fallbackGroups.length));
          for (let i = 0; i < fontConfig.fallbackGroups.length; i++) {
            console.info("fontSetName:" + fontConfig.fallbackGroups[i].fontSetName);
            for (let j = 0; j < fontConfig.fallbackGroups[i].fallback.length; j++) {
              console.info("language:" + fontConfig.fallbackGroups[i].fallback[j].language + " family:" +
              fontConfig.fallbackGroups[i].fallback[j].family);
            }
          }
        })
    }.width('100%')
  }
}
```
