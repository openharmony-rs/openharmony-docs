# @ohos.arkui.advanced.DownloadFileButton

## Modules to Import

```TypeScript
import { DownloadFileButton, DownloadLayoutDirection, DownloadIconStyle, DownloadDescription, DownloadContentOptions, DownloadStyleOptions } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [DownloadFileButton](arkts-arkui-arkui-advanced-downloadfilebutton-downloadfilebutton-s.md) | Declare Component DownloadFileButton |

### Interfaces

| Name | Description |
| --- | --- |
| [DownloadContentOptions](arkts-arkui-arkui-advanced-downloadfilebutton-downloadcontentoptions-i.md) | Defines the download content options. |
| [DownloadStyleOptions](arkts-arkui-arkui-advanced-downloadfilebutton-downloadstyleoptions-i.md) | Defines the DownloadFileButton style option. |

### Enums

| Name | Description |
| --- | --- |
| [DownloadDescription](arkts-arkui-arkui-advanced-downloadfilebutton-downloaddescription-e.md) | Enum for DownloadDescription |
| [DownloadIconStyle](arkts-arkui-arkui-advanced-downloadfilebutton-downloadiconstyle-e.md) | Enum for DownloadIconStyle |
| [DownloadLayoutDirection](arkts-arkui-arkui-advanced-downloadfilebutton-downloadlayoutdirection-e.md) | Enum for DownloadDescription |

## Examples

```TypeScript
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
