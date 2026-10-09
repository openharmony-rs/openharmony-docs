# DownloadFileButton

<!--Kit: ArkUI--> 
<!--Subsystem: ArkUI--> 
<!--Owner: @yaoyao1798--> 
<!--Designer: @yaoyao1798-->  
<!--Tester: @yangjiayong2686--> 
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c41ee24119717ac6e011a5eb6c87ee4ac4914b0a translatedAt=2026-08-28T01:31:45.678Z pushedAt=2026-08-28T09:09:17.123Z -->

A download file button that provides a unified style of download button in file download scenarios.

> **NOTE**
>
> This component is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { DownloadFileButton } from '@kit.ArkUI';
```

## Child Components

Not supported

## Attributes

The [universal attributes](ts-component-general-attributes.md) are supported.

## DownloadFileButton

DownloadFileButton({ contentOptions: DownloadContentOptions, styleOptions: DownloadStyleOptions })

A download file button that provides a unified style of download button in file download scenarios.

**Decorator**: @Component

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Type                                             | Mandatory| Decorator| Description                            |
| -------------- | ------------------------------------------------- | ---- | ---------- | -------------------------------- |
| contentOptions | [DownloadContentOptions](#downloadcontentoptions) | Yes | @State | Content displayed on the download button. |
| styleOptions   | [DownloadStyleOptions](#downloadstyleoptions)     | Yes  | @State     | Style options for the download button.|

## DownloadContentOptions

Defines the content displayed in the download file button.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                                                        | Read-Only| Optional| Description                                                        |
| ---- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| icon | [DownloadIconStyle](#downloadiconstyle) | No | Yes | Icon style of the download button.<br>Default value: not set. If this parameter is not passed, no icon is displayed. At least one of **icon** and **text** must be set; otherwise, the component cannot be displayed properly. |
| text | [DownloadDescription](#downloaddescription) | No | Yes | Text description of the download button.<br>Default value: not set. If this parameter is not passed, no text description is displayed. At least one of **icon** and **text** must be set; otherwise, the component cannot be displayed properly. |

## DownloadStyleOptions

Defines the style of the icon and text in the download file button.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type                                                        | Read-Only| Optional| Description                                                        |
| --------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| iconSize | [Dimension](ts-types.md#dimension10) | No | Yes | Size of the icon on the download button. The percentage format is not supported. This attribute takes effect only when **contentOptions.icon** is set.<br>Default value: **16vp**<br>Unit: vp |
| layoutDirection | [DownloadLayoutDirection](#downloadlayoutdirection) | No | Yes | Layout direction of the icon and text on the download button. This attribute takes effect only when both **contentOptions.icon** and **contentOptions.text** are set. <br>Default value: **DownloadLayoutDirection.HORIZONTAL** |
| fontSize        | [Dimension](ts-types.md#dimension10) | No   | Yes   | Size of the text on the download button. The percentage format is not supported. This attribute takes effect only when **contentOptions.text** is set.<br>Default value: **16fp**<br>Unit: fp |
| fontStyle | [FontStyle](ts-appendix-enums.md#fontstyle) | No | Yes | Style of the text on the download button. This attribute takes effect only when **contentOptions.text** is set. <br>Default value: **FontStyle.Normal** |
| fontWeight | number\|[FontWeight](ts-appendix-enums.md#fontweight)\|string | No | Yes | Font weight of the text on the download button. This attribute takes effect only when **contentOptions.text** is set. For the number type, the value ranges from 100 to 900 at an interval of 100, and the default value is 400. A larger value indicates a heavier font weight. For the string type, only the string form of the number type value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in **FontWeight**. <br>Default value: **FontWeight.Medium** |
| fontFamily | string\|[Resource](ts-types.md#resource) | No | Yes | Font of the text on the download button. This attribute takes effect only when **contentOptions.text** is set.<br> Default font: **'HarmonyOS Sans'**|
| fontColor | [ResourceColor](ts-types.md#resourcecolor) | No | Yes | Color of the text on the download button. This attribute takes effect only when **contentOptions.text** is set.<br>Default value: **#ffffffff** |
| iconColor | [ResourceColor](ts-types.md#resourcecolor) | No | Yes | Color of the icon on the download button. This attribute takes effect only when **contentOptions.icon** is set. <br>Default value: **#ffffffff** |
| textIconSpace | [Dimension](ts-types.md#dimension10) | No | Yes | Spacing between the icon and text on the download button. This attribute takes effect only when both **contentOptions.icon** and **contentOptions.text** are set.<br> Default value: **4vp**<br>Unit: vp |

## DownloadIconStyle

Defines the icon style of the download file button.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Value  | Description                      |
| ----------- | ---- | -------------------------- |
| FULL_FILLED | 1    | Filled style icon.|
| LINES       | 2    | Line style icon.|

## DownloadDescription

Defines the description on the download button. Different text descriptions apply to different scenarios: **DOWNLOAD** is used for general file download scenarios, **DOWNLOAD_FILE** is used for download scenarios where the file object needs to be emphasized, the **SAVE** series is used for saving scenarios (such as saving images and saving files), **DOWNLOAD_AND_SHARE** is used for scenarios where sharing is required after download, and the **RECEIVE** series is used for file receiving scenarios.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name               | Value  | Description                            |
| ------------------- | ---- | -------------------------------- |
| DOWNLOAD            | 1    | The text on the download file button is **Download**.    |
| DOWNLOAD_FILE       | 2    | The text on the download file button is **Download File**.|
| SAVE                | 3    | The text on the download file button is **Save**.    |
| SAVE_IMAGE          | 4    | The text on the download file button is **Save Image**.|
| SAVE_FILE           | 5    | The text on the download file button is **Save File**.|
| DOWNLOAD_AND_SHARE  | 6    | The text on the download file button is **Download and Share**.|
| RECEIVE             | 7    | The text on the download file button is **Receive**.    |
| CONTINUE_TO_RECEIVE | 8    | The text on the download file button is **Continue**.|

## DownloadLayoutDirection

Defines the direction of the icon and text in the download file button.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Value  | Description                                      |
| ---------- | ---- | ------------------------------------------ |
| HORIZONTAL | 0    | The icon and text on the download file button are arranged horizontally. |
| VERTICAL   | 1    | The icon and text on the download file button are arranged vertically. |

## Events

The [universal events](ts-component-general-events.md) are supported.

##  Example

```ts
// xxx.ets

import { picker } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { DownloadFileButton, DownloadLayoutDirection, DownloadIconStyle, DownloadDescription } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column() {
      DownloadFileButton({
        contentOptions: {
          icon: DownloadIconStyle.FULL_FILLED,
          text: DownloadDescription.DOWNLOAD
        },
        styleOptions: {
          iconSize: '16vp',
          layoutDirection: DownloadLayoutDirection.HORIZONTAL,
          fontSize: '16vp',
          fontStyle: FontStyle.Normal,
          fontWeight: FontWeight.Medium,
          fontFamily: 'HarmonyOS Sans',
          fontColor: '#ffffffff',
          iconColor: '#ffffffff',
          textIconSpace: '4vp'
       }
      })
        .backgroundColor('#007dff')
        .borderStyle(BorderStyle.Dotted)
        .borderWidth(0)
        .borderRadius('24vp')
        .position({ x: 0, y: 0 })
        .markAnchor({ x: 0, y: 0 })
        .offset({ x: 0, y: 0 })
        .constraintSize({})
        .padding({
          top: '12vp',
          bottom: '12vp',
          left: '24vp',
          right: '24vp'
        })
        .onClick(() => {
          this.downloadAction();
        })
    }
  }

  downloadAction() {
    try {
      const document = new picker.DocumentSaveOptions();
      document.pickerMode = picker.DocumentPickerMode.DOWNLOAD;
      new picker.DocumentViewPicker().save(document, (err: BusinessError, result: Array<string>) => {
        if (err) {
          return;
        }
        console.info(`downloadAction result:  ${JSON.stringify(result)}`);
      });
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`downloadAction failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

![en-us_image_0000001643320073](figures/en-us_image_0000001643329999.png)