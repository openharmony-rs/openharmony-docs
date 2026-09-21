# @ohos.arkui.advanced.Dialog

## Modules to Import

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md) | Declare ButtonOptions |

### Structs

| Name | Description |
| --- | --- |
| [AlertDialog](arkts-arkui-arkui-advanced-dialog-alertdialog-s.md) | Declare CustomDialog AlertDialog |
| [ConfirmDialog](arkts-arkui-arkui-advanced-dialog-confirmdialog-s.md) | Declare CustomDialog ConfirmDialog |
| [CustomContentDialog](arkts-arkui-arkui-advanced-dialog-customcontentdialog-s.md) | Declare custom content dialog |
| [LoadingDialog](arkts-arkui-arkui-advanced-dialog-loadingdialog-s.md) | Declare CustomDialog LoadingDialog |
| [PopoverDialog](arkts-arkui-arkui-advanced-dialog-popoverdialog-s.md) | Declare struct PopoverDialog |
| [SelectDialog](arkts-arkui-arkui-advanced-dialog-selectdialog-s.md) | Declare CustomDialog SelectDialog |
| [TipsDialog](arkts-arkui-arkui-advanced-dialog-tipsdialog-s.md) | Declare CustomDialog TipsDialog |

### Interfaces

| Name | Description |
| --- | --- |
| [PopoverOptions](arkts-arkui-arkui-advanced-dialog-popoveroptions-i.md) | Defines PopoverDialog Options |

## Examples

### Example 1: Dialog Box with an Image Above Text

This example implements a dialog box with an image above the text content, through the use of imageRes, content, and other properties.



```TypeScript
import { TipsDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  dialogControllerImage: CustomDialogController = new CustomDialogController({
    builder: TipsDialog({
      imageRes: $r('sys.media.ohos_ic_public_voice'),
      content: 'Delete this app?',
      primaryButton: {
        value: 'Cancel',
        action: () => {
          console.info('Callback when the first button is clicked');
        },
      },
      secondaryButton: {
        value: 'Delete',
        role: ButtonRole.ERROR,
        action: () => {
          console.info('Callback when the second button is clicked');
        }
      },
      onCheckedChange: () => {
        console.info('Callback when the checkbox is clicked');
      }
    }),
  })

  build() {
    Row() {
      Stack() {
        Column(){
          Button("Text Below Image")
            .width(96)
            .height(40)
            .onClick(() => {
              this.dialogControllerImage.open();
            })
        }.margin({bottom: 300})
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
import { SelectDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // Set the index of the default selected option.
  radioIndex: number = 0;
  dialogControllerList: CustomDialogController = new CustomDialogController({
    builder: SelectDialog({
      title:'Title',
      selectedIndex: this.radioIndex,
      confirm: {
        value: 'Cancel',
        action: () => {},
      },
      radioContent: [
        {
          title: 'List item',
          action: () => {
            this.radioIndex = 0;
          }
        },
        {
          title: 'List item',
          action: () => {
            this.radioIndex = 1;
          }
        },
        {
          title: 'List item',
          action: () => {
            this.radioIndex = 2;
          }
        },
      ]
    }),
  })

  build() {
    Row() {
      Stack() {
        Column() {
          Button("List Dialog Box")
            .width(96)
            .height(40)
            .onClick(() => {
              this.dialogControllerList.open();
            })
        }.margin({ bottom: 300 })
      }
      .align(Alignment.Bottom)
      .width('100%')
      .height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```

### Example 3: Dialog Box with Text and Check Boxes

This example illustrates a dialog box that combines text content with check boxes defined with content and checkTips.



```TypeScript
import { ConfirmDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  isChecked: boolean = false;
  dialogControllerCheckBox: CustomDialogController = new CustomDialogController({
    builder: ConfirmDialog({
      title:'Title',
      content: 'This is where the content of this dialog box is presented.',
      // Selected state of the check box
      isChecked: this.isChecked,
      // Content of the check box
      checkTips: 'Do not ask me again',
      primaryButton: {
        value: 'Deny',
        action: () => {},
      },
      secondaryButton: {
        value: 'Allow',
        action: () => {
          this.isChecked = false;
          console.info('Callback when the second button is clicked');
        }
      },
      onCheckedChange: () => {
        console.info('Callback when the checkbox is clicked');
      },
    }),
    autoCancel: true,
    alignment: DialogAlignment.Bottom
  })

  build() {
    Row() {
      Stack() {
        Column(){
          Button("Text + Check Box Dialog Box")
            .width(96)
            .height(40)
            .onClick(() => {
              this.dialogControllerCheckBox.open();
            })
        }
        .margin({bottom: 300})
      }
      .align(Alignment.Bottom)
      .width('100%')
      .height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```

### Example 4: Text-only Dialog Box

This example demonstrates a simple text-only dialog box defined with primaryTitle, secondaryTitle, and content.



```TypeScript
import { AlertDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  dialogControllerConfirm: CustomDialogController = new CustomDialogController({
    builder: AlertDialog({
      primaryTitle: 'Primary title',
      secondaryTitle: 'Secondary title',
      content: 'This is where content is displayed.',
      primaryButton: {
        value: 'Cancel',
        action: () => {
        },
      },
      secondaryButton: {
        value: 'OK',
        role: ButtonRole.ERROR,
        action: () => {
          console.info('Callback when the second button is clicked');
        }
      },
    }),
  })

  build() {
    Row() {
      Stack() {
        Column() {
          Button("Text Dialog Box")
            .width(96)
            .height(40)
            .onClick(() => {
              this.dialogControllerConfirm.open();
            })
        }
        .margin({ bottom: 300 })
      }
      .align(Alignment.Bottom)
      .width('100%')
      .height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```

### Example 5: Loading Dialog Box

This example implements a loading dialog box that contains a progress indicator.



```TypeScript
import { LoadingDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  dialogControllerProgress: CustomDialogController = new CustomDialogController({
    builder: LoadingDialog({
      content: 'This is where content is displayed.',
    }),
  })

  build() {
    Row() {
      Stack() {
        Column() {
          Button("Loading Dialog Box")
            .width(96)
            .height(40)
            .onClick(() => {
              this.dialogControllerProgress.open();
            })
        }
        .margin({ bottom: 300 })
      }
      .align(Alignment.Bottom)
      .width('100%')
      .height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```

### Example 6: Dialog Box with a Custom Theme

This example presents a dialog box with a custom theme, through the use of content, theme, and other properties.



```TypeScript
import { CustomColors, CustomTheme, LoadingDialog } from '@kit.ArkUI';

class CustomThemeImpl implements CustomTheme {
  colors?: CustomColors;

  constructor(colors: CustomColors) {
    this.colors = colors;
  }
}

// Custom text content and colors for the dialog box theme
class CustomThemeColors implements CustomColors {
  fontPrimary = '#ffd0a300';
  iconSecondary = '#ffd000cd';
}

@Entry
@Component
struct Index {
  @State customTheme: CustomTheme = new CustomThemeImpl(new CustomThemeColors());
  dialogController: CustomDialogController = new CustomDialogController({
    builder: LoadingDialog({
      content: 'text',
      theme: this.customTheme,
    })
  });

  build() {
    Row() {
      Stack() {
        Column() {
          Button("dialog")
            .width(96)
            .height(40)
            .onClick(() => {
              this.dialogController.open();
            })
        }
        .margin({ bottom: 300 })
      }
      .align(Alignment.Bottom)
      .width('100%')
      .height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```

### Example 7: Dialog Box in Custom Color Mode

This example presents a dialog box in the specified light or dark mode, through the use of content, themeColorMode, and other properties.



```TypeScript
import { LoadingDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  dialogController: CustomDialogController = new CustomDialogController({
    builder: LoadingDialog({
      content: 'Text',
      themeColorMode: ThemeColorMode.DARK, // Set the color mode to dark mode.
    })
  });

  build() {
    Row() {
      Stack() {
        Column() {
          Button("Dialog")
            .width(96)
            .height(40)
            .onClick(() => {
              this.dialogController.open();
            })
        }
        .margin({ bottom: 300 })
      }
      .align(Alignment.Bottom)
      .width('100%')
      .height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```

### Example 8: Dialog Box with Custom Content

This example implements a dialog box with custom content defined with contentBuilder and buttons.



```TypeScript
import { CustomContentDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  dialogController: CustomDialogController = new CustomDialogController({
    builder: CustomContentDialog({
      primaryTitle: 'Primary title',
      secondaryTitle: 'Secondary title',
      contentBuilder: () => {
        this.buildContent();
      },
      buttons: [
        { 
          value: 'Button 1',
          buttonStyle: ButtonStyleMode.TEXTUAL, 
          action: () => {
            console.info('Callback when the button is clicked');
          }
        },
        {
          value: 'Button 2',
          buttonStyle: ButtonStyleMode.TEXTUAL,
          role: ButtonRole.ERROR
        }
      ],
    }),
  });

  build() {
    Column() {
      Button("Dialog Box with Custom Content")
        .onClick(() => {
          this.dialogController.open();
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
  
  // Custom content area of the dialog box
  @Builder
  buildContent(): void {
    Column() {
      Text('Content area')
    }
    .width('100%')
  }
}
```

### Example 9: Popover Dialog Box

This example demonstrates a popover dialog box for alert purposes, through the use of visible, popover, targetBuilder, and other properties. This functionality is supported since API version 14.



```TypeScript
import { AlertDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State isShow: boolean = false;
  @State popoverOptions: PopoverOptions = {
    builder: () => {
      this.dialogBuilder();
    },
    width: 320,
  }
  
  // Popover dialog box content
  @Builder dialogBuilder() {
    AlertDialog({
      content: 'Popover dialog box',
      primaryButton: {
        value: 'Cancel',
        action: () => {
          this.isShow = false;
        },
      },
      secondaryButton: {
        value: 'OK',
        action: () => {
          this.isShow = false;
        },
      },
    });
  }
  
  // Builder for the button that triggers the popover dialog box
  @Builder buttonBuilder() {
    Button('Target Component')
    .onClick(() => {
      this.isShow = true;
    });
  }

  build() {
    Column() {
      PopoverDialog({
        visible: this.isShow,
        popover: this.popoverOptions,
        targetBuilder: () => {
          this.buttonBuilder();
        },
      })
    }
  }
}
```

### Example 10: Setting the Default Focus Button for a Dialog Box

This example demonstrates how to set the button that receives focus by default in a dialog box using AlertDialog, including the defaultFocus property. This functionality is supported since API version 18.

```TypeScript
import { AlertDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  dialogController: CustomDialogController = new CustomDialogController({
    builder: AlertDialog({
      primaryTitle: 'AlertDialog',
      secondaryTitle: 'Subtitle',
      content: 'The second button gains focus by default.',
      primaryButton: {
        value: 'DEFAULT',
        action: () => {}
      },
      secondaryButton: {
        value: 'TRUE',
        defaultFocus: true, // Set the button as the default focus button.
        action: () => {}
      },
    })
  });

  build() {
    Row() {
      Stack() {
        Column() {
          Button("AlertDialog")
            .width(96)
            .height(40)
            .onClick(() => {
              this.dialogController.open();
            })
        }
        .margin({ bottom: 300 })
      }
      .align(Alignment.Bottom)
      .width('100%')
      .height('100%')
    }
    .backgroundImageSize({ width: '100%', height: '100%' })
    .height('100%')
  }
}
```
