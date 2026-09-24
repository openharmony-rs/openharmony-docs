# @ohos.arkui.advanced.DialogV2

## Modules to Import

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md) | Declare AdvancedDialogV2Button. |

### Structs

| Name | Description |
| --- | --- |
| [AlertDialogV2](arkts-arkui-arkui-advanced-dialogv2-alertdialogv2-s.md) | Declare CustomDialog AlertDialogV2. |
| [ConfirmDialogV2](arkts-arkui-arkui-advanced-dialogv2-confirmdialogv2-s.md) | Declare CustomDialog ConfirmDialogV2 |
| [CustomContentDialogV2](arkts-arkui-arkui-advanced-dialogv2-customcontentdialogv2-s.md) | Declare custom content dialog |
| [LoadingDialogV2](arkts-arkui-arkui-advanced-dialogv2-loadingdialogv2-s.md) | Declare CustomDialog LoadingDialogV2 |
| [PopoverDialogV2](arkts-arkui-arkui-advanced-dialogv2-popoverdialogv2-s.md) | Declare struct PopoverDialogV2 |
| [SelectDialogV2](arkts-arkui-arkui-advanced-dialogv2-selectdialogv2-s.md) | Declare CustomDialog SelectDialogV2 |
| [TipsDialogV2](arkts-arkui-arkui-advanced-dialogv2-tipsdialogv2-s.md) | Declare CustomDialog TipsDialogV2 |

### Interfaces

| Name | Description |
| --- | --- |
| [AdvancedDialogV2ButtonOptions](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2buttonoptions-i.md) | Declare the options of AdvancedDialogV2Button |
| [PopoverDialogV2Options](arkts-arkui-arkui-advanced-dialogv2-popoverdialogv2options-i.md) | Defines PopoverDialogV2 Options |

### Types

| Name | Description |
| --- | --- |
| [AdvancedDialogV2ButtonAction](arkts-arkui-advanceddialogv2buttonaction-t.md) | Declare the action when the button of dialog is clicked. |
| [AdvancedDialogV2OnCheckedChange](arkts-arkui-advanceddialogv2oncheckedchange-t.md) | Declare the callback when the checkbox of dialog is changed. |
| [PopoverDialogV2OnVisibleChange](arkts-arkui-popoverdialogv2onvisiblechange-t.md) | Declare the callback when the visibility of PopoverDialogV2 is changed. |

## Examples

### Example 1: Dialog Box with an Image Above Text

This example implements a dialog box with an image above the text content, through the use of imageRes, content, and other properties.



```TypeScript
import { TipsDialogV2, AdvancedDialogV2Button, UIContext  } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local checked: boolean = false;

  @Builder
  dialogBuilder(): void {
    TipsDialogV2({
      imageRes: $r('sys.media.ohos_ic_public_voice'),
      content: 'Delete this app?',
      title: 'TipsDialogV2',
      checkTips: 'Do not show again',
      checked: this.checked,
      primaryButton: new AdvancedDialogV2Button({
        content: 'Cancel',
        action: () => {
          console.info('Callback when the first button is clicked');
        },
      }),
      secondaryButton: new AdvancedDialogV2Button({
        content: 'Delete',
        role: ButtonRole.ERROR,
        action: () => {
          console.info('Callback when the second button is clicked');
        }
      }),
      onCheckedChange: (checked: boolean) => {
        console.info('Callback when the checkbox is clicked');
        this.checked = checked;
      }
    })
  }

  build() {
    Row() {
      Stack() {
        Column() {
          Button("TipsDialogV2")
            .width(96)
            .height(40)
            .onClick(() => {
              let uiContext: UIContext = this.getUIContext();
              uiContext.getPromptAction().openCustomDialog({
                builder: () => {
                  this.dialogBuilder();
                },
              });
            })
        }.margin({ bottom: 300 })
      }.align(Alignment.Bottom)
      .width('100%').height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```

### Example 2: List-only Dialog Box

This example presents a dialog box consisting solely of a list defined with selectedIndex and radioContent.



```TypeScript
import { SelectDialogV2, AdvancedDialogV2Button ,UIContext  } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local radioIndex: number = 0;
  @Builder
  dialogBuilder(): void {
    SelectDialogV2({
      title:'Title',
      selectedIndex: this.radioIndex,
      confirm: new AdvancedDialogV2Button({
        content: 'Cancel',
        action: () => {},
      }),
      radioContent: [
        {
          title: 'List item',
          action: () => {
            this.radioIndex = 0
          }
        },
        {
          title: 'List item',
          action: () => {
            this.radioIndex = 1
          }
        },
        {
          title: 'List item',
          action: () => {
            this.radioIndex = 2
          }
        },
      ]
    })
  }
  build() {
    Row() {
      Stack() {
        Column() {
          Button("List Dialog Box")
            .width(96)
            .height(40)
            .onClick(() => {
              let uiContext: UIContext = this.getUIContext();
              uiContext.getPromptAction().openCustomDialog({
                builder: () => {
                  this.dialogBuilder();
                }
              })
            })
        }.margin({ bottom: 300 })
      }.align(Alignment.Bottom)
      .width('100%').height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```

### Example 3: Dialog Box with Text and Check Boxes

This example illustrates a dialog box that combines text content with check boxes defined with content and checkTips.



```TypeScript
import { ConfirmDialogV2, AdvancedDialogV2Button, UIContext  } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local checked: boolean = false;

  @Builder
  dialogBuilder(): void {
    ConfirmDialogV2({
      title:'Title',
      content: 'This is where the content of this dialog box is presented.',
      checked: this.checked,
      checkTips: 'Do not ask me again',
      primaryButton: new AdvancedDialogV2Button({
        content: 'Deny',
        action: () => {
          console.info('Callback when the primary button is clicked');
        },
      }),
      secondaryButton: new AdvancedDialogV2Button({
        content: 'Allow',
        action: () => {
          this.checked = false
          console.info('Callback when the second button is clicked');
        }
      }),
      onCheckedChange: (checked: boolean) => {
        console.info('Callback when the checkbox is clicked');
        this.checked = checked;
      },
    })
  }

  build() {
    Row() {
      Stack() {
        Column() {
          Button("Open ConfirmDialogV2")
            .width(96)
            .height(40)
            .onClick(() => {
              let uiContext: UIContext = this.getUIContext();
              uiContext.getPromptAction().openCustomDialog({
                builder: () => {
                  this.dialogBuilder();
                },
                alignment: DialogAlignment.Bottom
              });
            })
        }.margin({ bottom: 300 })
      }.align(Alignment.Bottom)
      .width('100%').height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```

### Example 4: Text-only Dialog Box

This example demonstrates a simple text-only dialog box defined with primaryTitle, secondaryTitle, and content.



```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, UIContext  } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Builder
  dialogBuilder(): void {
    AlertDialogV2({
      primaryTitle: 'Primary title',
      secondaryTitle: 'Secondary title',
      content: 'This is where content is displayed.',
      primaryButton: new AdvancedDialogV2Button({
        content: 'Cancel',
        action: () => {
          console.info('Callback when the primary button is clicked');
        },
      }),
      secondaryButton: new AdvancedDialogV2Button({
        content: 'OK',
        role: ButtonRole.ERROR,
        action: () => {
          console.info('Callback when the second button is clicked');
        }
      }),
    })
  }

  build() {
    Row() {
      Stack() {
        Column() {
          Button("Open AlertDialogV2")
            .width(96)
            .height(40)
            .onClick(() => {
              let uiContext: UIContext = this.getUIContext();
              uiContext.getPromptAction().openCustomDialog({
                builder: () => {
                  this.dialogBuilder();
                }
              });
            })
        }.margin({ bottom: 300 })
      }.align(Alignment.Bottom)
      .width('100%').height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```

### Example 5: Loading Dialog Box

This example implements a loading dialog box that contains a progress indicator.



```TypeScript
import { LoadingDialogV2, UIContext  } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Builder
  dialogBuilder(): void {
    LoadingDialogV2({
      content: 'This is where content is displayed.',
    })
  }

  build() {
    Row() {
      Stack() {
        Column() {
          Button("Open LoadingDialogV2")
            .width(96)
            .height(40)
            .onClick(() => {
              let uiContext: UIContext = this.getUIContext();
              uiContext.getPromptAction().openCustomDialog({
                builder: () => {
                  this.dialogBuilder();
                }
              });
            })
        }.margin({ bottom: 300 })
      }.align(Alignment.Bottom)
      .width('100%').height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```

### Example 6: Dialog Box with a Custom Theme

This example presents a dialog box with a custom theme, through the use of content, theme, and other properties.



```TypeScript
import { CustomColors, CustomTheme, LoadingDialogV2, UIContext  } from '@kit.ArkUI';

class CustomThemeImpl implements CustomTheme {
  colors?: CustomColors;

  constructor(colors: CustomColors) {
    this.colors = colors;
  }
}

class CustomThemeColors implements CustomColors {
  fontPrimary = '#ffd0a300';
  iconSecondary = '#ffd000cd';
}

@Entry
@ComponentV2
struct Index {
  @Builder
  dialogBuilder(): void {
    WithTheme({ theme: new CustomThemeImpl(new CustomThemeColors()) }) {
      LoadingDialogV2({
        content: 'This is where content is displayed.',
      })
    }
  }

  build() {
    Row() {
      Stack() {
        Column() {
          Button("Open LoadingDialogV2")
            .width(96)
            .height(40)
            .onClick(() => {
              let uiContext: UIContext = this.getUIContext();
              uiContext.getPromptAction().openCustomDialog({
                builder: () => {
                  this.dialogBuilder();
                }
              });
            })
        }.margin({ bottom: 300 })
      }.align(Alignment.Bottom)
      .width('100%').height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```

### Example 7: Dialog Box with Custom Content

This example implements a dialog box with custom content defined with contentBuilder and buttons.



```TypeScript
import { CustomContentDialogV2, AdvancedDialogV2Button, UIContext  } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Builder
  dialogBuilder(): void {
    CustomContentDialogV2({
      primaryTitle: 'Primary title',
      secondaryTitle: 'Secondary title',
      contentBuilder: () => {
        this.buildContent();
      },
      buttons: [
        new AdvancedDialogV2Button({
          content: 'Button 1', buttonStyle: ButtonStyleMode.TEXTUAL,
          action: () => {
            console.info('Callback when the button is clicked');
          }
        }),
        new AdvancedDialogV2Button({
          content: 'Button 2', buttonStyle: ButtonStyleMode.TEXTUAL, role: ButtonRole.ERROR,
        })
      ],
    })
  }

  build() {
    Column() {
      Button("Open CustomContentDialogV2")
        .onClick(() => {
            let uiContext: UIContext = this.getUIContext();
            uiContext.getPromptAction().openCustomDialog({
            builder: () => {
              this.dialogBuilder();
            }
          })
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }

  @Builder
  buildContent(): void {
    Column() {
      Text('Content area')
    }
  }
}
```

### Example 8: Popover Dialog Box

This example demonstrates a popover dialog box for alert purposes, through the use of visible, popover, targetBuilder, and other properties.

```TypeScript
import { AlertDialogV2, PopoverDialogV2, PopoverDialogV2Options, AdvancedDialogV2Button} from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local isShow: boolean = false;
  @Local popoverOptions: PopoverDialogV2Options = {
    builder: () => {
      this.dialogBuilder();
    }
  }

  @Builder dialogBuilder() {
    AlertDialogV2({
      content: 'Popover dialog box',
      primaryButton: new AdvancedDialogV2Button({
        content: 'Cancel',
        action: () => {
          this.isShow = false;
        },
      }),
      secondaryButton: new AdvancedDialogV2Button({
        content: 'OK',
        action: () => {
          this.isShow = false;
        },
      }),
    });
  }

  @Builder buttonBuilder() {
    Button('Target Component').onClick(() => {
      this.isShow = true;
    });
  }

  build() {
    Column() {
      PopoverDialogV2({
        visible: this.isShow!!,
        popover: this.popoverOptions,
        targetBuilder: () => {
          this.buttonBuilder();
        },
      })
    }
  }
}
```
