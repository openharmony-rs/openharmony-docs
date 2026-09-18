# @ohos.arkui.advanced.FormMenu(Defines the form menu)

## Modules to Import

```TypeScript
import { AddFormMenuItem, FormMenuItemStyle, AddFormOptions } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [AddFormMenuItem](arkts-arkui-arkui-advanced-formmenu-addformmenuitem-f.md) | Build function of AddFormMenuItem. |

### Interfaces

| Name | Description |
| --- | --- |
| [AddFormOptions](arkts-arkui-arkui-advanced-formmenu-addformoptions-i.md) | Defines the add form options. |
| [FormMenuItemStyle](arkts-arkui-arkui-advanced-formmenu-formmenuitemstyle-i.md) | Defines the form menu item style. |

## Examples

```TypeScript
// index.ets
import { AddFormMenuItem } from '@kit.ArkUI';
import { formBindingData } from '@kit.FormKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const tag = 'AddFormMenuItem';

@Entry
@Component
struct Index {
  @State message: string = 'Long press show menu';
  private compId: string = 'addforms@d46313145';

  @Builder
  MyMenu() {
    Menu() {
      AddFormMenuItem(
        {
          bundleName: 'com.example.myapplication', // Bundle name
          abilityName: 'EntryFormAbility', // Module ability name.
          parameters: {
            'ohos.extra.param.key.form_dimension': 2, // Widget size: 1 for 1 x 2, 2 for 2 x 2, 3 for 2 x 4, 4 for 4 x 4, 7 for 6 x 4.
            'ohos.extra.param.key.form_name': 'widget', // Widget name.
            'ohos.extra.param.key.module_name': 'entry' // Module name of the widget.
          },
        },
        this.compId,
        {
          formBindingData: formBindingData.createFormBindingData({}),
          // formBindingData: formBindingData.createFormBindingData({ data: 'share' }),
          callback: (error, formId) => {
            hilog.info(0x3900, tag, `callback info: formId = ${formId}`);
            if (error?.code === 0) {
              hilog.info(0x3900, tag, "Added to the home screen.")
            } else {
              hilog.error(0x3900, tag, `Failed to add to the home screen. Try another method. Error code: ${error?.code}, error message: ${error?.message}`)
            }
          },
          style: {
            options: {
              startIcon: $r("app.media.icon"), // Menu icon. You can provide your own. The system uses "sys.media.ic_public_add" by default.
              content: "Add to Home Screen",  // Menu content. You can provide your own. "sys.string.ohos_add_form_to_desktop" is used by default.
              endIcon: $r("app.media.icon") // Menu icon. You can provide your own.
            }
          }
        }
      )
    }
  }

  build() {
    Row() {
      Column() {
        Image($r("app.media.startIcon"))   // Custom image.
          .id(this.compId)
          .width(200)
          .height(200)
          .bindContextMenu(this.MyMenu, ResponseType.LongPress, {
            placement: Placement.TopLeft
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

```TypeScript
// WidgetCard.ets
const local = new LocalStorage()

@Entry(local)
@Component
struct WidgetCard {
  @LocalStorageProp('data') data: string = 'defaultdata'; // Define the service widget data to be updated.
  /*
   * The action type.
   */
  readonly ACTION_TYPE: string = 'router';
  /*
   * The ability name.
   */
  readonly ABILITY_NAME: string = 'EntryAbility';
  /*
   * The message.
   */
  readonly MESSAGE: string = 'add detail';
  /*
   * The width percentage setting.
   */
  readonly FULL_WIDTH_PERCENT: string = '100%';
  /*
   * The height percentage setting.
   */
  readonly FULL_HEIGHT_PERCENT: string = '100%';

  build() {
    Row() {
      Column() {
        Text(this.data)
          .fontSize($r('app.float.font_size'))
          .fontWeight(FontWeight.Medium)
          .fontColor($r('app.color.item_title_font'))
      }
      .width(this.FULL_WIDTH_PERCENT)
    }
    .height(this.FULL_HEIGHT_PERCENT)
    .backgroundImage($r('app.media.startIcon'))
    .backgroundImageSize({ width: '100%', height: '100%' })
    .onClick(() => {
      postCardAction(this, {
        action: this.ACTION_TYPE,
        abilityName: this.ABILITY_NAME,
        params: {
          message: this.MESSAGE
        }
      });
    })
  }
}
```
