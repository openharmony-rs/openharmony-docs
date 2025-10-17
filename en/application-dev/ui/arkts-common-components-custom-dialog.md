# Basic Custom Dialog Box (CustomDialog) (Not Recommended)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @HelloCrease-->
A custom dialog box is a dialog box you customize by using APIs of the **CustomDialogController** class. It can be used for user interactions, showing ads, award announcements, alerts, software update notifications, and more. For details, see [Custom Dialog Box](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md).

> **NOTE**
> 
> In ArkUI, dialog boxes do not close automatically when you switch pages unless you manually call **close**. To enable a dialog box to be dismissed during page navigation, consider using the [navigation page displayed in dialog mode](arkts-navigation-navigation.md#page-display-mode) or [page-level dialog box](arkts-embedded-dialog.md).

By default, the dialog box is modal and has a mask. You cannot interact with the controls under the mask (click and gesture transparent transmission are not supported). You can specify the modality of a dialog box by setting the isModal attribute in [CustomDialogControllerOptions](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontrolleroptions). For details, see [Types of Popup Windows](arkts-dialog-overview.md#types-of-popup-windows).

When isModal is set to true, the dialog box is a modal dialog box, and the mask area around the dialog box does not support transparent transmission. When isModal is set to false, the dialog box is a non-modal dialog box, and the mask area around the dialog box supports transparent transmission. Therefore, if you need to allow the interaction of the dialog box and the page outside the dialog box at the same time, you need to set the dialog box to non-modal.

## Lifecycle

From API version 19, the CustomDialog provides lifecycle functions to notify users of the lifecycle of the dialog box. The order in which these lifecycle events are triggered is as follows: **onWillAppear**, **onDidAppear**, **onWillDisappear**, **onDidDisappear**.

| Name           |Type| Description                      |
| ----------------- | ------ | ---------------------------- |
| onWillAppear    | Callback&lt;void&gt; | Triggered before the dialog box display animation.|
| onDidAppear    | Callback&lt;void&gt;  | Triggered after the dialog box appears.   |
| onWillDisappear | Callback&lt;void&gt; | Triggered before the dialog box exit animation.|
| onDidDisappear | Callback&lt;void&gt;  | Triggered after the dialog box disappears.   |

## Creating a Custom Dialog Box

1. Use the \@CustomDialog decorator to create a custom dialog box. You can define the content of the dialog box within the decorator. Note that **CustomDialogController** must be defined in @Component.
   
   ```ts
   @CustomDialog
   struct CustomDialogExample {
     controller: CustomDialogController
   
     build() {
       Column() {
         Text('I am content')
           .fontSize(20)
       }.height(60).justifyContent(FlexAlign.Center)
     }
   }
   ```
2. Create a builder that is bound to the decorator.
   
   ```ts
    @Entry
    @Component
    struct CustomDialogUser {
      dialogController: CustomDialogController = new CustomDialogController({
        builder: CustomDialogExample(),
      })
    }
   ```
3. Click the component bound to the **onClick** event to display the dialog box.
   
   ```ts
   @Entry
   @Component
   struct CustomDialogUser {
     dialogController: CustomDialogController = new CustomDialogController({
       builder: CustomDialogExample(),
     })
   
     build() {
       Column() {
         Button('click me')
           .onClick(() => {
             this.dialogController.open();
           })
       }.width('100%').margin({ top: 5 })
     }
   }
   ```
   
   ![en-us_image_0000001562700493](figures/en-us_image_0000001562700493.png)

## Implementing Interaction with the Custom Dialog Box

Custom dialog boxes can be used for data interactions to complete a series of operations.

1. Add buttons and data functions to the \@CustomDialog decorator.
   
   ```ts
   @CustomDialog
   struct CustomDialogExample {
     cancel: () => void = () => {
     }
     confirm: () => void = () => {
     }
     controller: CustomDialogController;
   
     build() {
       Column() {
         Text('I am content').fontSize(20).margin({ top: 10, bottom: 10 })
         Flex({ justifyContent: FlexAlign.SpaceAround }) {
           Button('Cancel')
             .onClick(() => {
               this.controller.close();
               if (this.cancel) {
                 this.cancel();
               }
             }).backgroundColor(0xffffff).fontColor(Color.Black)
           Button('Obtain')
             .onClick(() => {
               this.controller.close();
               if (this.confirm) {
                 this.confirm();
               }
             }).backgroundColor(0xffffff).fontColor(Color.Red)
         }.margin({ bottom: 10 })
       }
     }
   }
   ```
2. Receive the page in the builder and create corresponding function operations.
   
   ```ts
   @Entry
   @Component
   struct CustomDialogUser {
     dialogController: CustomDialogController = new CustomDialogController({
       builder: CustomDialogExample({
         cancel: ()=> { this.onCancel() },
         confirm: ()=> { this.onAccept() },
       }),
     });
   
     onCancel() {
       console.info('Callback when the first button is clicked');
     }
   
     onAccept() {
       console.info('Callback when the second button is clicked');
     }
   
     build() {
       Column() {
         Button('click me')
           .onClick(() => {
             this.dialogController.open();
           })
       }.width('100%').margin({ top: 5 })
     }
   }
   ```
   
   ![en-us_image_0000001511421320](figures/en-us_image_0000001511421320.png)
   
   3. Use the button in the dialog box to implement route redirection and obtain the parameters passed in from the redirection target page.
   
   ```ts
   // Index.ets
   @CustomDialog
   struct CustomDialogExample {
     @Link textValue: string;
     controller?: CustomDialogController;
     cancel: () => void = () => {
     }
     confirm: () => void = () => {
     }
   
     build() {
       Column({ space: 20 }) {
         if (this.textValue != '') {
           Text(`Content of the second page: ${this.textValue}`)
             .fontSize(20)
         } else {
           Text('Obtain the content of the second page?')
             .fontSize(20)
         }
         Flex({ justifyContent: FlexAlign.SpaceAround }) {
           Button('Cancel')
             .onClick(() => {
               if (this.controller != undefined) {
                 this.controller.close();
                 this.cancel();
               }
             }).backgroundColor(0xffffff).fontColor(Color.Black)
           Button('Obtain')
             .onClick(() => {
               if (this.controller != undefined && this.textValue != '') {
                 this.controller.close();
               } else if (this.controller != undefined) {
                 this.getUIContext().getRouter().pushUrl({
                   url: 'pages/Index2'
                 });
                 this.controller.close();
               }
             }).backgroundColor(0xffffff).fontColor(Color.Red)
         }.margin({ bottom: 10 })
       }.borderRadius(10).padding({ top: 20 })
     }
   }
   
   @Entry
   @Component
   struct CustomDialogUser {
     @State textValue: string = '';
     dialogController: CustomDialogController | null = new CustomDialogController({
       builder: CustomDialogExample({
         cancel: () => {
           this.onCancel()
         },
         confirm: () => {
           this.onAccept()
         },
         textValue: this.textValue
       })
     });
   
     // Set dialogController to null when the custom component is about to be destroyed.
     aboutToDisappear() {
       this.dialogController = null; // Set dialogController to null.
     }
   
     onPageShow() {
       const params = this.getUIContext().getRouter().getParams() as Record<string, string>; // Obtain the passed parameter object.
       if (params) {
         this.dialogController?.open();
         this.textValue = params.info as string; // Obtain the value of the id attribute.
       }
     }
   
     onCancel() {
       console.info('Callback when the first button is clicked');
     }
   
     onAccept() {
       console.info('Callback when the second button is clicked');
     }
   
     exitApp() {
       console.info('Click the callback in the blank area');
     }
   
     build() {
       Column() {
         Button('Click Me')
           .onClick(() => {
             if (this.dialogController != null) {
               this.dialogController.open();
             }
           }).backgroundColor(0x317aff)
       }.width('100%').margin({ top: 5 })
     }
   }
   ```
   
   ```ts
   // Index2.ets
   @Entry
   @Component
   struct Index2 {
     @State message: string =' Back';

     build() {
       Column() {
         Button(this.message)
           .type(ButtonType.Capsule)
           .onClick(() => {
              this.getUIContext().getRouter().back({
                url: 'pages/Index',
                params: {
                info: 'Hello World'
              }
           });
         })
       }.width('100%').height('100%').margin({ top: 20 })
     }
   }
   ```
   
   ![DialogRouter](figures/DialogRouter.gif)

## Defining the Custom Dialog Box Animation

You can define the custom dialog box animation, including its duration and speed, through **openAnimation**.

```ts
@CustomDialog
struct CustomDialogExample {
  controller?: CustomDialogController;

  build() {
    Column() {
      Text('Whether to change a text?').fontSize(16).margin({ bottom: 10 })
    }
  }
}

@Entry
@Component
struct CustomDialogUser {
  @State textValue: string = '';
  @State inputValue: string = 'click me';
  dialogController: CustomDialogController | null = new CustomDialogController({
    builder: CustomDialogExample(),
    openAnimation: {
      duration: 1200,
      curve: Curve.Friction,
      delay: 500,
      playMode: PlayMode.Alternate,
      onFinish: () => {
        console.info('play end')
      }
    },
    autoCancel: true,
    alignment: DialogAlignment.Bottom,
    offset: { dx: 0, dy: -20 },
    gridCount: 4,
    customStyle: false,
    backgroundColor: 0xd9ffffff,
    cornerRadius: 10,
  });

  // Set dialogController to null when the custom component is about to be destroyed.
  aboutToDisappear() {
    this.dialogController = null; // Set dialogController to null.
  }

  build() {
    Column() {
      Button(this.inputValue)
        .onClick(() => {
          if (this.dialogController != null) {
            this.dialogController.open();
          }
        }).backgroundColor(0x317aff)
    }.width('100%').margin({ top: 5 })
  }
}
```

![openAnimator](figures/openAnimator.gif)

## Defining the Custom Dialog Box Style

You can define the width, height, background color, and shadow of the dialog to control its style.

```ts
@CustomDialog
struct CustomDialogExample {
  controller?: CustomDialogController;

  build() {
    Column() {
      Text('I am content').fontSize(16).margin({ bottom: 10 })
    }
  }
}

@Entry
@Component
struct CustomDialogUser {
  @State textValue: string = '';
  @State inputValue: string = 'click me';
  dialogController: CustomDialogController | null = new CustomDialogController({
    builder: CustomDialogExample(),
    autoCancel: true,
    alignment: DialogAlignment.Center,
    offset: { dx: 0, dy: -20 },
    gridCount: 4,
    customStyle: false,
    backgroundColor: 0xd9ffffff,
    cornerRadius: 20,
    width: '80%',
    height: '100px',
    borderWidth: 1,
    borderStyle: BorderStyle.Dashed,// borderStyle must be used with borderWidth in pairs.
    borderColor: Color.Blue,// borderColor must be used with borderWidth in pairs.
    shadow: ({ radius: 20, color: Color.Grey, offsetX: 50, offsetY: 0}),
  });

  // Set dialogController to null when the custom component is about to be destroyed.
  aboutToDisappear() {
    this.dialogController = null; // Set dialogController to null.
  }

  build() {
    Column() {
      Button(this.inputValue)
        .onClick(() => {
          if (this.dialogController != null) {
            this.dialogController.open();
          }
        }).backgroundColor(0x317aff)
    }.width('100%').margin({ top: 5 })
  }
}
```

![custom_style](figures/custom_style.gif)

## Nesting a Custom Dialog Box

To nest a dialog box (dialog 2) inside another dialog box (dialog 1), it is recommended that you define dialog 2 within the parent component of dialog 1 so that you can then open dialog 2 through the callback sent from the parent component to dialog 1.

```ts
@CustomDialog
struct CustomDialogExampleTwo {
  controllerTwo?: CustomDialogController;
  @State message: string = "I'm the second dialog box.";
  @State showIf: boolean = false;

  build() {
    Column() {
      if (this.showIf) {
        Text("Text")
          .fontSize(30)
          .height(100)
      }
      Text(this.message)
        .fontSize(30)
        .height(100)
      Button("Create Text")
        .onClick(() => {
          this.showIf = true;
        })
      Button('Close Second Dialog Box')
        .onClick(() => {
          if (this.controllerTwo != undefined) {
            this.controllerTwo.close();
          }
        })
        .margin(20)
    }
  }
}

@CustomDialog
struct CustomDialogExample {
  openSecondBox?: () => void
  controller?: CustomDialogController

  build() {
    Column() {
      Button('Open Second Dialog Box and close this box')
        .onClick(() => {
          this.controller!.close();
          this.openSecondBox!();
        })
        .margin(20)
    }.borderRadius(10)
  }
}

@Entry
@Component
struct CustomDialogUser {
  @State inputValue: string = 'Click Me';
  dialogController: CustomDialogController | null = new CustomDialogController({
    builder: CustomDialogExample({
      openSecondBox: () => {
        if (this.dialogControllerTwo != null) {
          this.dialogControllerTwo.open()
        }
      }
    }),
    cancel: this.exitApp,
    autoCancel: true,
    alignment: DialogAlignment.Bottom,
    offset: { dx: 0, dy: -20 },
    gridCount: 4,
    customStyle: false
  });
  dialogControllerTwo: CustomDialogController | null = new CustomDialogController({
    builder: CustomDialogExampleTwo(),
    alignment: DialogAlignment.Bottom,
    offset: { dx: 0, dy: -25 }
  });

  aboutToDisappear() {
    this.dialogController = null;
    this.dialogControllerTwo = null;
  }

  onCancel() {
    console.info('Callback when the first button is clicked');
  }

  onAccept() {
    console.info('Callback when the second button is clicked');
  }

  exitApp() {
    console.info('Click the callback in the blank area');
  }

  build() {
    Column() {
      Button(this.inputValue)
        .onClick(() => {
          if (this.dialogController != null) {
            this.dialogController.open();
          }
        }).backgroundColor(0x317aff)
    }.width('100%').margin({ top: 5 })
  }
}
```

![nested_dialog](figures/nested_dialog.gif)

If you define dialog 2 within dialog 1 instead, because of the parent-child relationship that exists between custom dialog boxes in terms of state management, you will not be able to create any component in dialog 2 once dialog 1 is destroyed (closed).

## Implementing Physical Return Interception of Dialog Boxes

If the onWillDismiss callback function in [CustomDialogControllerOptions](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontrolleroptions) is registered, the dialog box will not be closed immediately when you perform interaction operations such as closing the dialog box by clicking the mask layer, sliding from left to right, pressing the Back button, or pressing the ESC key on the keyboard. In the callback function, you can obtain the operation type of blocking the dialog box closure through the reason attribute in [DismissDialogAction](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#dismissdialogaction12) and determine whether to close the dialog box based on the reason.

```ts
@CustomDialog
struct CustomDialogExample {
  cancel: () => void = () => {
  }
  confirm: () => void = () => {
  }
  controller?: CustomDialogController;

  build() {
    Column() {
      Text('Are you sure?')
        .fontSize(20)
        .margin({
          top: 10,
          bottom: 10
        })
      Row() {
        Button('Cancel')
          .onClick(() => {
            if (this.controller != undefined) {
              this.controller.close();
            }
          })
          .backgroundColor(0xffffff)
          .fontColor(Color.Black)
        Button('Obtain')
          .onClick(() => {
            if (this.controller != undefined) {
              this.controller.close();
            }
          })
          .backgroundColor(0xffffff)
          .fontColor(Color.Red)
      }
      .width('100%')
      .justifyContent(FlexAlign.SpaceAround)
      .margin({ bottom: 10 })
    }
  }
}

@Entry
@Component
struct InterceptCustomDialog {
  dialogController: CustomDialogController = new CustomDialogController({
    builder: CustomDialogExample({
      cancel: () => {
        this.onCancel();
      },
      confirm: () => {
        this.onAccept();
      }
    }),
    onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
      console.info('dialog onWillDismiss reason: ' + dismissDialogAction.reason);
      // 1. Press the back button, swipe left or right, or press ESC.
      // 2. Touch the overlay layer.
      // 3. Touch the close button.
      if (dismissDialogAction.reason === DismissReason.PRESS_BACK) {
        // Close the dialog box by calling dismiss.
        // dismissDialogAction.dismiss();
      }
      if (dismissDialogAction.reason === DismissReason.TOUCH_OUTSIDE) {
        // dismissDialogAction.dismiss();
      }
    },
    alignment: DialogAlignment.Bottom,
    offset: { dx: 0, dy: -20 }
  })

  onCancel() {
    console.info('Callback when the first button is clicked');
  }

  onAccept() {
    console.info('Callback when the second button is clicked');
  }

  build() {
    Column() {
      Button('click me')
        .onClick(() => {
          this.dialogController.open();
        })
    }
    .width('100%')
  }
}
```

![onWillDismiss_dialog](figures/onWillDismiss_dialog.gif)

## Setting the Distance Between the Dialog Box and the Soft Keyboard

To ensure the independence of the dialog box, the dialog box is kept away from the surrounding elements, such as the status bar, navigation bar, and keyboard. When the soft keyboard is displayed, the dialog box automatically avoids the soft keyboard and keeps a distance of 16 vp from the soft keyboard by default. From API version 15, you can use keyboardAvoidMode and keyboardAvoidDistance in [CustomDialogControllerOptions](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontrolleroptions) to set the behavior of the dialog box when the soft keyboard is displayed, including whether to avoid the soft keyboard and the distance between the dialog box and the soft keyboard.
Note that the value of **keyboardAvoidMode** should be set to **KeyboardAvoidMode.DEFAULT**.

```ts
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI'

@CustomDialog
struct CustomDialogExample {
  controller?: CustomDialogController;
  build() {
    Column() {
      Column() {
        Text('keyboardAvoidDistance: 0vp')
          .fontSize(20)
          .margin({ bottom: 36 })
        TextInput({ placeholder: '' })
      }.backgroundColor('#FFF0F0F0')
    }
  }
}

@Entry
@Component
struct Index {
  dialogController: CustomDialogController | null = new CustomDialogController({
    builder: CustomDialogExample({
    }),
    autoCancel: true,
    gridCount: 4,
    showInSubWindow: true,
    isModal: true,
    customStyle: false,
    cornerRadius: 30,
    alignment:DialogAlignment.Bottom,
    keyboardAvoidMode: KeyboardAvoidMode.DEFAULT, // The dialog box automatically avoids the soft keyboard.
    keyboardAvoidDistance: LengthMetrics.vp(0) // The distance between the soft keyboard and the pop-up box is 0 vp.
  })

  build() {
    Row() {
      Row({ space: 20 }) {
        Text('Open the pop-up box')
          .fontSize(30)
          .onClick(() => {
            if (this.dialogController != null) {
              this.dialogController.open();
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```



## Obtaining the Status of a Pop-up Box

In the service module, multiple pop-up boxes may appear on the page at the same time. To avoid opening the same pop-up box repeatedly, you are advised to check the status of the pop-up box through the controller before displaying the pop-up box. If the pop-up box is already displayed, do not open it again.
The getState API is added since API version 20 to obtain the current status of a pop-up box. For details about the pop-up box status, see the description of the [CommonState](../reference/apis-arkui/js-apis-promptAction.md#commonstate20) enumeration.

The following example uses the [getDialogController](../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getdialogcontroller18) and [CustomDialogController](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontroller) methods to obtain the current status of a pop-up box.

```ts
// xxx.ets
@CustomDialog
struct CustomDialogExample {
  controller?: CustomDialogController

  build() {
    Column() {
      Button('Click me to query the pop-up window status: using the controller of the custom component')
        .onClick(() => {
          if (this.getDialogController() != undefined) {
            console.info('state:' + this.getDialogController().getState())
          } else {
            console.info('state: no exist')
          }
        }).margin(20)
      Button('Click me to query the pop-up window status: using CustomDialogController')
        .onClick(() => {
          console.info('state:' + this.controller?.getState())
        }).margin(20)
      Button('Close Dialog Box')
        .onClick(() => {
          if (this.getDialogController() != undefined) {
            this.getDialogController().close()
          }
        }).margin(20)
      
    }
  }
}

@Entry
@Component
struct CustomDialogUser {
  dialogController: CustomDialogController | null = new CustomDialogController({
    builder: CustomDialogExample({
    }),
    autoCancel: false
  })

  build() {
    Column() {
      Button('click me')
        .onClick(() => {
          if (this.dialogController != null) {
            this.dialogController.open()
          }
        })
    }.width('100%').margin({ top: 5 })
  }
}
```


