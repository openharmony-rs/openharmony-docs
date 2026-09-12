# @ohos.font (Custom Font Registration)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8a65b118b29a0c9d1936c3b96f0e90c33fab49ab translatedAt=2026-09-01T03:16:21.087Z pushedAt=2026-09-01T10:49:23.841Z -->

This module provides capabilities such as registering custom fonts and obtaining the system font list, font details, and system font configuration. It is applicable to scenarios where applications need to use custom font styles (such as brand and icon fonts) or obtain system font information. By using this module, you can unify brand fonts, improve the aesthetics and consistency of the user interface, and meet diverse design requirements.

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
| familyName | string \| [Resource](arkui-ts/ts-types.md#resource)<sup>10+</sup> | No  | No  | Name of the font to register. It is recommended to use letters, digits, and underscores.   |
| familySrc  | string \| [Resource](arkui-ts/ts-types.md#resource)<sup>10+</sup> | No  | No  | File path of the font to register. This parameter supports **Resource** references, **$rawfile** paths, relative paths, and absolute paths.<br>**Note:**<br>When reading resources in the system sandbox path, you are advised to use a string with the **file://** path prefix. Ensure that the file exists in the sandbox directory and has read permission. |

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
    });

    // familySrc supports the RawFile type.
    this.uiContext.getFont().registerFont({
      familyName: 'mediumRawFile',
      familySrc: $rawfile('font/medium.ttf') // Replace 'font/medium.ttf' with the actual resource font file.
    });

    // Register iconFont.
    this.uiContext.getFont().registerFont({
      familyName: 'iconFont',
      familySrc: '/font/iconFont.ttf'
    });

    // Both familyName and familySrc support the string type.
    this.uiContext.getFont().registerFont({
      familyName: 'medium',
      familySrc: '/font/medium.ttf' // The font folder is at the same level as the pages folder.
    });
  }

  build() {
    Column() {
      Text(this.message)
        .align(Alignment.Center)
        .fontSize(20)
        .fontFamily('medium') // medium: name of the registered custom font. (Registered fonts such as $r('app.string.font_name') and 'mediumRawFile' can also be used.)

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

Obtains this system font list.

This API only takes effect on PCs/2-in-1 devices and returns an empty array on other devices.

You are advised to use the [getSystemFontFullNamesByType](../apis-arkgraphics2d/js-apis-graphics-text.md#textgetsystemfontfullnamesbytype14) API to obtain the latest system-supported font list data.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [getSystemFontList](arkts-apis-uicontext-font.md#getsystemfontlist) instead. Before calling this API, you need to obtain the [Font](arkts-apis-uicontext-font.md) object using the [getFont](arkts-apis-uicontext-uicontext.md#getfont) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using **getSystemFontList** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context).
>
> - Since API version 10, you can use the [getFont](arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [Font](arkts-apis-uicontext-font.md) object associated with the current UI context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                | Description              |
| -------------------- | ----------------- |
| Array\<string>       | List of supported fonts. |

> **NOTE**
>
> Directly using **font** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the [Font](arkts-apis-uicontext-font.md) object associated with the current UI context by using the [getFont](arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](./arkts-apis-uicontext-uicontext.md).

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

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type     | Mandatory   | Description         |
| ---------- | --------- | ------- | ------------ |
| fontName   | string    | Yes     | System font name.|

**Return value**

| Type            | Description                         |
| ---------------- | ---------------------------- |
| FontInfo         | Font details, including attributes such as the path, name, font weight, width, and whether it is italic. |

## FontInfo<sup>10+</sup>

Information about the system font.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------------------------- | ------------------------- | ------------------------- |
| path           | string  | No| No| File path of the system font.       |
| postScriptName | string  | No| No| PostScript name of the system font.|
| fullName       | string  | No| No| Name of the system font.          |
| family         | string  | No| No| Family of the system font.      |
| subfamily      | string  | No| No| Subfamily of the system font.     |
| weight         | number  | No | No | Weight of the system font.<br>Value range: [100, 900], with an interval of 100, corresponding to the values in [FontWeight](../apis-arkgraphics2d/js-apis-graphics-text.md#fontweight). |
| width          | number  | No | No | Width of the system font.<br>Value range: [1, 9], with an interval of 1, corresponding to the values in [FontWidth](../apis-arkgraphics2d/js-apis-graphics-text.md#fontwidth).    |
| italic         | boolean | No | No | Whether the system font is italic.<br>Default value: **false**<br>The value **true** indicates an italic font, and **false** indicates a non-italic font.          |
| monoSpace      | boolean | No | No | Whether the system font is monospaced.<br>Default value: **false**<br>The value **true** indicates a monospaced font, and **false** indicates a non-monospaced font.         |
| symbolic       | boolean | No | No | Whether the system font supports symbolic fonts.<br>Default value: **false**<br>The value **true** indicates that symbolic fonts are supported, and **false** indicates that symbolic fonts are not supported.  |

**Example**

> **NOTE**
>
> Directly using **font** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the [Font](arkts-apis-uicontext-font.md) object associated with the current UI context by using the [getFont](./arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](./arkts-apis-uicontext-uicontext.md).

```ts
// xxx.ets
@Entry
@Component
struct FontExample {
  private fontInfo = this.getUIContext().getFont().getFontByName('');

  build() {
    Column() {
      Button('getFontByName')
        .onClick(() => {
          this.fontInfo =
            this.getUIContext().getFont().getFontByName('HarmonyOS Sans Italic');
          console.info('getFontByName(): path = ' + this.fontInfo.path);
          console.info('getFontByName(): postScriptName = ' + this.fontInfo.postScriptName);
          console.info('getFontByName(): fullName = ' + this.fontInfo.fullName);
          console.info('getFontByName(): family = ' + this.fontInfo.family);
          console.info('getFontByName(): subfamily = ' + this.fontInfo.subfamily);
          console.info('getFontByName(): weight = ' + this.fontInfo.weight);
          console.info('getFontByName(): width = ' + this.fontInfo.width);
          console.info('getFontByName(): italic = ' + this.fontInfo.italic);
          console.info('getFontByName(): monoSpace = ' + this.fontInfo.monoSpace);
          console.info('getFontByName(): symbolic = ' + this.fontInfo.symbolic);
        })
    }.width('100%')
  }
}
```

## font.getUIFontConfig<sup>11+</sup>

getUIFontConfig() : UIFontConfig

Obtains the UI font configuration in the system font configuration file. This API is commonly used in scenarios where the system font configuration needs to be analyzed or viewed, such as font management tools, font debugging and diagnosis, and font configuration information display.

This API only supports obtaining the information in the configuration file, and **undefined** may be returned when the UI context is not clear. To obtain the full font configuration information, it is recommended to use the [getSystemFontFullNamesByType](../apis-arkgraphics2d/js-apis-graphics-text.md#textgetsystemfontfullnamesbytype14) API of the font engine to obtain the latest font list data supported by the system.

> **NOTE**
>
> You need to first obtain the [Font](arkts-apis-uicontext-font.md) object through the [getFont](arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](arkts-apis-uicontext-uicontext.md), and then call the related API through the object. Directly using **getUIFontConfig** may cause the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context).

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type            | Description                         |
| ---------------- | ---------------------------- |
| [UIFontConfig](#uifontconfig11)     | UI font configuration of the system, including the font directory, generic font group, and fallback font group.          |

## UIFontConfig<sup>11+</sup>

UI font configuration of the system.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------------------------- | ------- | ------------------------- |
| fontDir        | Array\<string>  | No | No | List of paths where the system font files are located. Each array element is an absolute system path.      |
| generic | Array\<[UIFontGenericInfo](#uifontgenericinfo11)>  | No| No| List of generic font families supported by the system.|
| fallbackGroups       | Array\<[UIFontFallbackGroupInfo](#uifontfallbackgroupinfo11)>  | No | No | List of system fallback font groups, used to specify the fallback fonts to use when the primary font does not support certain characters.           |

## UIFontGenericInfo<sup>11+</sup>

Defines a list of supported generic font families.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------------------------- | ------------------------- | ------------------------- |
| family        | string | No| No| Font family name, which is the value of **family** specified in the font file.     |
| alias        | Array\<[UIFontAliasInfo](#uifontaliasinfo11)>  | No | No | Alias list of the font family, used to provide alternative names for the fonts. |
| adjust       | Array\<[UIFontAdjustInfo](#uifontadjustinfo11)>  | No | No | Font weight value mapping list, which maps the original weight values of the fonts to the actually displayed weight values. |

## UIFontFallbackGroupInfo<sup>11+</sup>

Defines a list of fallback generic font families.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------------------------- | ------------------------- | ------------------------- |
| fontSetName  | string | No | No | Name of the font family corresponding to the fallback font group. If **fontSetName** is set to **""**, the fallback font group can be used for all font families.      |
| fallback        | Array\<[UIFontFallbackInfo](#uifontfallbackinfo11)>  | No| No| Fallback fonts for the font family. If **fontSetName** is set to **""**, it indicates that the fonts can be used as fallback fonts for all font families.|

## UIFontAliasInfo<sup>11+</sup>

Defines font alias configuration information.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------- | ------------------------- | ------------------------- |
| name          | string  | No| No| Alias name.     |
| weight        | number  | No | No | When the value of **weight** is greater than 0, this font family contains only fonts of the specified weight. When the value of **weight** is 0, this font family contains all fonts.<br>The value options can be **0**, **100**, **400**, **700**, and **900**. |

## UIFontAdjustInfo<sup>11+</sup>

Provides a mapping list between the original weight value of a font and the actual displayed weight value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------- | ------------------------- | ------------------------- |
| weight        | number  | No  | No  | Original weight value of the font.<br>The value options can be **50**, **80**, **100**, and **200**.      |
| to            | number  | No  | No  | Weight value of the font displayed in the application.<br>The value options can be **100**, **400**, **700**, and **900**. |

## UIFontFallbackInfo<sup>11+</sup>

Provides the fallback font of the font set.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type   | Read-Only| Optional | Description                      |
| -------------- | ------- | ------- | ------------------------- | ------------------------- |
| language       | string  | No | No | Language type supported by the font family. The language format is a BCP47 tag (for example, **"zh-Hans"** indicates Simplified Chinese, and **"en"** indicates English).    |
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
      Button('getUIFontConfig')
        .width('60%')
        .height('6%')
        .margin(50)
        .onClick(() => {
          let fontConfig = font.getUIFontConfig();
          console.info('font-dir -----------' + String(fontConfig.fontDir.length));
          for (let i = 0; i < fontConfig.fontDir.length; i++) {
            console.info(fontConfig.fontDir[i]);
          }
          console.info('generic-------------' + String(fontConfig.generic.length));
          for (let i = 0; i < fontConfig.generic.length; i++) {
            console.info('family:' + fontConfig.generic[i].family);
            for (let j = 0; j < fontConfig.generic[i].alias.length; j++) {
              console.info(fontConfig.generic[i].alias[j].name + ' ' + fontConfig.generic[i].alias[j].weight);
            }
            for (let j = 0; j < fontConfig.generic[i].adjust.length; j++) {
              console.info(fontConfig.generic[i].adjust[j].weight + ' ' + fontConfig.generic[i].adjust[j].to);
            }
          }
          console.info('fallbackGroups------------' + String(fontConfig.fallbackGroups.length));
          for (let i = 0; i < fontConfig.fallbackGroups.length; i++) {
            console.info('fontSetName:' + fontConfig.fallbackGroups[i].fontSetName);
            for (let j = 0; j < fontConfig.fallbackGroups[i].fallback.length; j++) {
              console.info('language:' + fontConfig.fallbackGroups[i].fallback[j].language + ' family:' +
              fontConfig.fallbackGroups[i].fallback[j].family);
            }
          }
        })
    }.width('100%')
  }
}
```