# UI组件适配（表单与弹窗）

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## 表单类组件

### minLabel

ArkTS-Dyn接口声明：[minLabel(value: string)](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#minlabeldeprecated)

替代的ArkTS-Sta接口声明：[min?: number](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#slideroptions对象说明)

### maxLabel

ArkTS-Dyn接口声明：[maxLabel(value: string)](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#maxlabeldeprecated)

替代的ArkTS-Sta接口声明：[max?: number](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#slideroptions对象说明)



ArkTS-Dyn示例：

```ts
Slider({value: 50}).minLabel('0').maxLabel('100')
```

ArkTS-Sta示例：

```ts
Slider({value: 50, min: 0, max: 100})
```

## 弹窗类组件

### placementOnTop

ArkTS-Dyn接口声明：[placementOnTop?: boolean](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#popupoptions类型说明)

替代的ArkTS-Sta接口声明：[placement?: Placement](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#popupoptions类型说明)



ArkTS-Dyn示例：

```ts
@Entry
@Component
struct Example {
  @State handlePopup: boolean = false;

  build() {
    Column() {
      Button('click').onClick((e: ClickEvent) => {
        this.handlePopup = !this.handlePopup;
      }).bindPopup(this.handlePopup, { message: 'test', placementOnTop: true }).position({ x: 0, y: 300 })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Button,
  Placement,
  Position,
  PopupOptions,
  ClickEvent
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct Example {
  @State handlePopup: boolean = false;

  build() {
    Column() {
      Button('click')
        .onClick((e: ClickEvent) => {
          this.handlePopup = !this.handlePopup;
        })
        .bindPopup(this.handlePopup, { message: 'test', placement: Placement.Top } as PopupOptions)
        .position({ x: 0, y: 300 } as Position)
    }
  }
}
```

### maskColor

ArkTS-Dyn接口声明：[maskColor?: Resource | string | number | Color](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#custompopupoptions8类型说明)

替代的ArkTS-Sta接口声明：[mask?: boolean | PopupMaskType](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#custompopupoptions8类型说明)



ArkTS-Dyn示例：

```ts
@Entry
@Component
struct Example {
    @State customPopup: boolean = false;
    
    @Builder popupBuilder() {
        Row() {
            Text('Custom Popup')
        }
    }

    build() {
        Column() {
            Button('click').onClick((e: ClickEvent) => {
                this.customPopup = !this.customPopup;
            }).bindPopup(this.customPopup, {builder: this.popupBuilder, maskColor: Color.Red})
        }
    }
}

```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Button,
  CustomPopupOptions,
  ClickEvent,
  PopupMaskType,
  Builder,
  Row,
  Text,
  Color
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct Example {
  @State customPopup: boolean = false;

  @Builder popupBuilder() {
    Row() {
      Text('Custom Popup')
    }
  }

  build() {
    Column() {
      Button('click').onClick((e: ClickEvent) => {
        this.customPopup = !this.customPopup;
      }).bindPopup(this.customPopup, {builder: this.popupBuilder, mask: { color: Color.Red } as PopupMaskType} as CustomPopupOptions)
    }
  }
}
```

### fontSize

ArkTS-Dyn接口声明：[fontSize(value: Length)](../reference/apis-arkui/arkui-ts/ts-basic-components-menu.md#fontsizedeprecated)

替代的ArkTS-Sta接口声明：[font(value: Font)](../reference/apis-arkui/arkui-ts/ts-basic-components-menu.md#font10)

ArkTS-Dyn示例：

```ts
@Entry
@Component
struct Example {
    // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
    private iconStr: ResourceStr = $r('app.media.icon');

    @Builder
    MyMenu() {
        Menu() {
            MenuItem({startIcon: this.iconStr, content: '菜单选项'})
        }.fontSize(40)
    }

    build() {
        Column() {
            Text('preview-menu').bindContextMenu(this.MyMenu, ResponseType.LongPress, {
                preview: MenuPreviewMode.IMAGE
            })
        }
    }
}
```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Text,
  Builder,
  Menu,
  MenuItem,
  ResourceStr,
  MenuItemOptions,
  MenuPreviewMode,
  ResponseType,
  $r
} from '@ohos.arkui.component';

@Entry
@Component
struct Example {
    // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
    private iconStr: ResourceStr = $r('app.media.icon');

    @Builder
    MyMenu() {
        Menu() {
            MenuItem({startIcon: this.iconStr, content: '菜单选项'} as MenuItemOptions)
        }.font({
            size: 40
        })
    }

    build() {
        Column() {
            Text('preview-menu').bindContextMenu(this.MyMenu, ResponseType.LongPress, {
                preview: MenuPreviewMode.IMAGE
            })
        }
    }
}
```

### ContextMenu.close

ArkTS-Dyn接口声明：[static close()](../reference/apis-arkui/arkui-ts/ts-methods-menu.md#contextmenuclosedeprecated)

替代的ArkTS-Sta接口声明：[引用@ohos.arkui.UIContext的close(): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#contextmenucontroller12)

ArkTS-Dyn示例：

```ts
@Entry
@Component
struct Index {
  @Builder MenuBuilder() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('ContextMenu1')
      Divider().strokeWidth(2).margin(5).color(Color.Black)
      Button('ContextMenu2')
      Divider().strokeWidth(2).margin(5).color(Color.Black)
      Button('ContextMenu3')
    }
    .width(200)
    .height(160)
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Column() {
        Text('ContextMenu')
          .fontSize(20)
          .width('100%')
          .height(500)
          .backgroundColor(0xAFEEEE)
          .textAlign(TextAlign.Center)
      }
      .bindContextMenu(this.MenuBuilder, ResponseType.LongPress)
      .onDragStart(()=>{
        // 拖拽时关闭菜单
        ContextMenu.close() // 建议使用 this.getUIContext().getContextMenuController().close()
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Builder,
  Button,
  Divider,
  Color,
  FlexDirection,
  ItemAlign,
  FlexAlign,
  Flex,
  TextAlign,
  ResponseType,
  Text
} from '@ohos.arkui.component';

@Entry
@Component
struct Index {
  @Builder MenuBuilder() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('ContextMenu1')
      Divider().strokeWidth(2).margin(5).color(Color.Black)
      Button('ContextMenu2')
      Divider().strokeWidth(2).margin(5).color(Color.Black)
      Button('ContextMenu3')
    }
    .width(200)
    .height(160)
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Column() {
        Text('ContextMenu')
          .fontSize(20)
          .width('100%')
          .height(500)
          .backgroundColor(0xAFEEEE)
          .textAlign(TextAlign.Center)
      }
      .bindContextMenu(this.MenuBuilder, ResponseType.LongPress)
      .onDragStart(()=>()=>{
        // 拖拽时关闭菜单
        this.getUIContext().getContextMenuController().close()
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### showToast

ArkTS-Dyn接口声明：

[引用@ohos.prompt的showToast(options: ShowToastOptions): void](../reference/apis-arkui/js-apis-prompt.md#promptshowtoast)

[引用@system.prompt的showToast(options: ShowToastOptions): void](../reference/apis-arkui/js-apis-system-prompt.md#promptshowtoast)

[引用@ohos.promptAction的showToast(options: ShowToastOptions): void](../reference/apis-arkui/js-apis-promptAction.md#promptactionshowtoastdeprecated)

替代的ArkTS-Sta接口声明：

[引用@ohos.arkui.UIContext的showToast(options: promptAction.ShowToastOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showtoast)



ArkTS-Dyn示例：

引用@ohos.prompt的showToast

```ts
import prompt from '@ohos.prompt';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('show toast from ohos.prompt').onClick((e: ClickEvent) => {
        prompt.showToast({
          message: 'test',
          duration: 2000
        })
      })
    }
  }
}
```

引用@system.prompt的showToast

```ts
import prompt from '@system.prompt';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('show toast from system.prompt').onClick((e: ClickEvent) => {
        prompt.showToast({
          message: 'test',
          duration: 2000
        })
      })
    }
  }
}
```

引用@ohos.promptAction的showToast

```ts
import promptAction from '@ohos.promptAction';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('show toast from ohos.promptAction').onClick((e: ClickEvent) => {
        promptAction.showToast({
          message: 'test',
          duration: 2000
        })
      })
    }
  }
}
```


ArkTS-Sta示例：

改用UIContext下的showToast方法

```ts
import {
  Entry,
  Component,
  Column,
  Button,
  ClickEvent,
  Builder
} from '@ohos.arkui.component';
import { UIContext } from '@ohos.arkui.UIContext';

@Entry
@Component
struct Example {
  uiContext: UIContext = this.getUIContext();

  build() {
    Column() {
      Button('show toast from UIContext').onClick((e: ClickEvent) => {
        this.uiContext.getPromptAction().showToast({
          message: 'test',
          duration: 2000
        })
      })
    }
  }
}
```

### ActionSheet.show

ArkTS-Dyn接口声明：[static show(value: ActionSheetOptions)](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md#showdeprecated)

替代的ArkTS-Sta接口声明：[showActionSheet(value: ActionSheetOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showactionsheet)



ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick(() => {
        try {
          ActionSheet.show({
            title: 'ActionSheet',
            message: 'message',
            autoCancel: true,
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -20 },
            confirm: {
              value: 'button',
              action: () => {
                console.info('ActionSheet Button-clicking callback');
              }
            },
            cancel: () => {
              console.info('ActionSheet Closed callbacks');
            },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('ActionSheet apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('ActionSheet bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('ActionSheet pears');
                }
              }
            ],
            onDidAppear: () => {
              console.info("ActionSheet is onDidAppear!");
            },
            onDidDisappear: () => {
              console.info("ActionSheet is onDidDisappear!");
            },
            onWillAppear: () => {
              console.info("ActionSheet is onWillAppear!");
            },
            onWillDisappear: () => {
              console.info("ActionSheet is onWillDisappear!");
            }
          })
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showActionSheet args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Button,
  ClickEvent,
  Builder,
  ActionSheetOptions,
  DialogAlignment
} from '@ohos.arkui.component';
import { BusinessError } from '@ohos.base';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().showActionSheet({
            title: 'ActionSheet',
            message: 'message',
            autoCancel: true,
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -20 },
            confirm: {
              value: 'button',
              action: () => {
                console.info('ActionSheet Button-clicking callback');
              }
            },
            cancel: () => {
              console.info('ActionSheet Closed callbacks');
            },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('ActionSheet apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('ActionSheet bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('ActionSheet pears');
                }
              }
            ],
            onDidAppear: () => {
              console.info("ActionSheet is onDidAppear!");
            },
            onDidDisappear: () => {
              console.info("ActionSheet is onDidDisappear!");
            },
            onWillAppear: () => {
              console.info("ActionSheet is onWillAppear!");
            },
            onWillDisappear: () => {
              console.info("ActionSheet is onWillDisappear!");
            }
          } as ActionSheetOptions)
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showActionSheet args error code is ${code}, message is ${message}`);
        }
        ;
      })
    }
  }
}
```

### AlertDialog.show

ArkTS-Dyn接口声明：[static show(value: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions)](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md#showdeprecated)

替代的ArkTS-Sta接口声明：[showAlertDialog(options: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showalertdialog)



ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('one button dialog').onClick(() => {
        try {
          AlertDialog.show({
            title: 'title',
            message: 'text',
            autoCancel: true,
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -20 },
            gridCount: 3,
            confirm: {
              value: 'button',
              action: () => {
                console.info('Button-clicking callback');
              }
            },
            cancel: () => {
              console.info('Closed callbacks');
            },
            onDidAppear: () => {
              console.info("AlertDialog is onDidAppear!");
            },
            onDidDisappear: () => {
              console.info("AlertDialog is onDidDisappear!");
            },
            onWillAppear: () => {
              console.info("AlertDialog is onWillAppear!");
            },
            onWillDisappear: () => {
              console.info("AlertDialog is onWillDisappear!");
            }
          })
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showAlertDialog args error code is ${code}, message is ${message}`);
        };
      })

      Button('two button dialog').onClick(() => {
        try {
          AlertDialog.show({
            title: 'title',
            message: 'text',
            autoCancel: true,
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -20 },
            gridCount: 3,
            primaryButton: {
              value: 'cancel',
              action: () => {
                console.info('Callback when the first button is clicked');
              }
            },
            secondaryButton: {
              enabled: true,
              defaultFocus: true,
              style: DialogButtonStyle.HIGHLIGHT,
              value: 'ok',
              action: () => {
                console.info('Callback when the second button is clicked');
              }
            },
            cancel: () => {
              console.info('Closed callbacks');
            },
            onDidAppear: () => {
              console.info("AlertDialog is onDidAppear!");
            },
            onDidDisappear: () => {
              console.info("AlertDialog is onDidDisappear!");
            },
            onWillAppear: () => {
              console.info("AlertDialog is onWillAppear!");
            },
            onWillDisappear: () => {
              console.info("AlertDialog is onWillDisappear!");
            }
          })
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showAlertDialog args error code is ${code}, message is ${message}`);
        };
      })

      Button('three button dialog').onClick(() => {
        try {
          AlertDialog.show({
            title: 'title',
            message: 'text',
            autoCancel: true,
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -20 },
            gridCount: 3,
            buttons: [
              {
                value: '按钮',
                action: () => {
                  console.info('Callback when button1 is clicked');
                }
              },
              {
                value: '按钮',
                action: () => {
                  console.info('Callback when button2 is clicked');
                }
              },
              {
                value: '按钮',
                enabled: true,
                defaultFocus: true,
                style: DialogButtonStyle.HIGHLIGHT,
                action: () => {
                  console.info('Callback when button3 is clicked');
                }
              },
            ],
            cancel: () => {
              console.info('Closed callbacks');
            },
            onDidAppear: () => {
              console.info("AlertDialog is onDidAppear!");
            },
            onDidDisappear: () => {
              console.info("AlertDialog is onDidDisappear!");
            },
            onWillAppear: () => {
              console.info("AlertDialog is onWillAppear!");
            },
            onWillDisappear: () => {
              console.info("AlertDialog is onWillDisappear!");
            }
          })
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showAlertDialog args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Button,
  ClickEvent,
  Builder,
  AlertDialogParamWithButtons,
  DialogAlignment,
  AlertDialogParamWithConfirm,
  DialogButtonStyle,
  AlertDialogParamWithOptions
} from '@ohos.arkui.component';
import { BusinessError } from '@ohos.base';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('one button dialog').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().showAlertDialog({
            title: 'title',
            message: 'text',
            autoCancel: true,
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -20 },
            gridCount: 3,
            confirm: {
              value: 'button',
              action: () => {
                console.info('Button-clicking callback')
              }
            },
            cancel: () => {
              console.info('Closed callbacks')
            },
            onDidAppear: () => {
              console.info("AlertDialog is onDidAppear!");
            },
            onDidDisappear: () => {
              console.info("AlertDialog is onDidDisappear!");
            },
            onWillAppear: () => {
              console.info("AlertDialog is onWillAppear!");
            },
            onWillDisappear: () => {
              console.info("AlertDialog is onWillDisappear!");
            }
          } as AlertDialogParamWithConfirm)
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showAlertDialog args error code is ${code}, message is ${message}`);
        };
      })

      Button('two button dialog').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().showAlertDialog({
            title: 'title',
            message: 'text',
            autoCancel: true,
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -20 },
            gridCount: 3,
            primaryButton: {
              value: 'cancel',
              action: () => {
                console.info('Callback when the first button is clicked');
              }
            },
            secondaryButton: {
              enabled: true,
              defaultFocus: true,
              style: DialogButtonStyle.HIGHLIGHT,
              value: 'ok',
              action: () => {
                console.info('Callback when the second button is clicked');
              }
            },
            cancel: () => {
              console.info('Closed callbacks');
            },
            onDidAppear: () => {
              console.info("AlertDialog is onDidAppear!");
            },
            onDidDisappear: () => {
              console.info("AlertDialog is onDidDisappear!");
            },
            onWillAppear: () => {
              console.info("AlertDialog is onWillAppear!");
            },
            onWillDisappear: () => {
              console.info("AlertDialog is onWillDisappear!");
            }
          } as AlertDialogParamWithButtons)
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showAlertDialog args error code is ${code}, message is ${message}`);
        };
      })

      Button('three button dialog').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().showAlertDialog({
            title: 'title',
            message: 'text',
            autoCancel: true,
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -20 },
            gridCount: 3,
            buttons: [
              {
                value: '按钮',
                action: () => {
                  console.info('Callback when button1 is clicked');
                }
              },
              {
                value: '按钮',
                action: () => {
                  console.info('Callback when button2 is clicked');
                }
              },
              {
                value: '按钮',
                enabled: true,
                defaultFocus: true,
                style: DialogButtonStyle.HIGHLIGHT,
                action: () => {
                  console.info('Callback when button3 is clicked');
                }
              },
            ],
            cancel: () => {
              console.info('Closed callbacks');
            },
            onDidAppear: () => {
              console.info("AlertDialog is onDidAppear!");
            },
            onDidDisappear: () => {
              console.info("AlertDialog is onDidDisappear!");
            },
            onWillAppear: () => {
              console.info("AlertDialog is onWillAppear!");
            },
            onWillDisappear: () => {
              console.info("AlertDialog is onWillDisappear!");
            }
          } as AlertDialogParamWithOptions)
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showAlertDialog args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

### showActionMenu

ArkTS-Dyn接口声明：

[showActionMenu(options: promptAction.ActionMenuOptions, callback: promptAction.ActionMenuSuccessResponse): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showactionmenudeprecated)

替代的ArkTS-Sta接口声明：

[showActionMenu(options: promptAction.ActionMenuOptions, callback: AsyncCallback<promptAction.ActionMenuSuccessResponse>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showactionmenu11)



ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick(() => {
        try {
          this.getUIContext().getPromptAction().showActionMenu({
            title: 'Title Info',
            buttons: [
              {
                text: 'item1',
                color: '#666666'
              },
              {
                text: 'item2',
                color: '#000000'
              }
            ]
          }, (err, data) => {
            if (err) {
              console.error('showActionMenu err: ' + err);
              return;
            }
            console.info('showActionMenu success callback, click button: ' + data.index);
          });
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showActionMenu args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Button,
  ClickEvent,
  Builder
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@ohos.base';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().getPromptAction().showActionMenu({
            title: 'Title Info',
            buttons: [
              {
                text: 'item1',
                color: '#666666'
              },
              {
                text: 'item2',
                color: '#000000'
              }
            ] as promptAction.PromptActionDoubleButtons
          }, (err: BusinessError|null, data: promptAction.ActionMenuSuccessResponse|undefined) => {
            if (err) {
              console.error('showActionMenu err: ' + err);
              return;
            }
            if (data) {
              console.info('showActionMenu success callback, click button: ' + data.index);
            }
          });
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showActionMenu args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

### showActionMenu

ArkTS-Dyn接口声明：

引用@ohos.prompt的[showActionMenu(options: ActionMenuOptions, callback: AsyncCallback&lt;ActionMenuSuccessResponse&gt;): void](../reference/apis-arkui/js-apis-prompt.md#promptshowactionmenu)

引用@ohos.promptAction的[showActionMenu(options: ActionMenuOptions, callback: AsyncCallback&lt;ActionMenuSuccessResponse&gt;):void](../reference/apis-arkui/js-apis-promptAction.md#promptactionshowactionmenudeprecated)

替代的ArkTS-Sta接口声明：

引用@ohos.arkui.UIContext的[showActionMenu(options: promptAction.ActionMenuOptions, callback: AsyncCallback<promptAction.ActionMenuSuccessResponse>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showactionmenu11)



ArkTS-Dyn示例：

引用@ohos.prompt的showActionMenu。

```ts
import prompt from '@ohos.prompt';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick(() => {
        try {
          prompt.showActionMenu({
            title: 'Title Info',
            buttons: [
              {
                text: 'item1',
                color: '#666666'
              },
              {
                text: 'item2',
                color: '#000000'
              }
            ]
          }, (err, data) => {
            if (err) {
              console.error('showActionMenu err: ' + err);
              return;
            }
            console.info('showActionMenu success callback, click button: ' + data.index);
          });
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showActionMenu args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

引用@ohos.promptAction的showActionMenu。

```ts
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick(() => {
        try {
          promptAction.showActionMenu({
            title: 'Title Info',
            buttons: [
              {
                text: 'item1',
                color: '#666666'
              },
              {
                text: 'item2',
                color: '#000000'
              }
            ]
          }, (err, data) => {
            if (err) {
              console.error('showActionMenu err: ' + err);
              return;
            }
            console.info('showActionMenu success callback, click button: ' + data.index);
          });
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showActionMenu args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Button,
  ClickEvent,
  Builder
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@ohos.base';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().getPromptAction().showActionMenu({
            title: 'Title Info',
            buttons: [
              {
                text: 'item1',
                color: '#666666'
              },
              {
                text: 'item2',
                color: '#000000'
              }
            ] as promptAction.PromptActionDoubleButtons
          }, (err: BusinessError|null, data: promptAction.ActionMenuSuccessResponse|undefined) => {
            if (err) {
              console.error('showActionMenu err: ' + err);
              return;
            }
            if (data) {
              console.info('showActionMenu success callback, click button: ' + data.index);
            }
          });
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showActionMenu args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

### showActionMenu

ArkTS-Dyn接口声明：

引用@ohos.prompt的[showActionMenu(options: ActionMenuOptions): Promise&lt;ActionMenuSuccessResponse&gt;](../reference/apis-arkui/js-apis-prompt.md#promptshowactionmenu-1)

引用@ohos.promptAction的[showActionMenu(options: ActionMenuOptions): Promise&lt;ActionMenuSuccessResponse&gt;](../reference/apis-arkui/js-apis-promptAction.md#promptactionshowactionmenudeprecated-1)

替代的ArkTS-Sta接口声明：

引用@ohos.arkui.UIContext的[showActionMenu(options: promptAction.ActionMenuOptions): Promise\<promptAction.ActionMenuSuccessResponse>](../reference/apis-arkui/js-apis-arkui-UIContext.md#showactionmenu)



ArkTS-Dyn示例：

引用@ohos.prompt的showActionMenu。

```ts
import prompt from '@ohos.prompt';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick(() => {
        try {
          prompt.showActionMenu({
            title: 'Title Info',
            buttons: [
              {
                text: 'item1',
                color: '#666666'
              },
              {
                text: 'item2',
                color: '#000000'
              }
            ]
          }).then((data) => {
            console.info('showActionMenu success callback, click button: ' + data.index);
          });
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showActionMenu args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

引用@ohos.promptAction的showActionMenu。

```ts
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick(() => {
        try {
          promptAction.showActionMenu({
            title: 'Title Info',
            buttons: [
              {
                text: 'item1',
                color: '#666666'
              },
              {
                text: 'item2',
                color: '#000000'
              }
            ]
          }).then((data) => {
            console.info('showActionMenu success callback, click button: ' + data.index);
          });
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showActionMenu args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Button,
  ClickEvent,
  Builder
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@ohos.base';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().getPromptAction().showActionMenu({
            title: 'Title Info',
            buttons: [
              {
                text: 'item1',
                color: '#666666'
              },
              {
                text: 'item2',
                color: '#000000'
              }
            ] as promptAction.PromptActionDoubleButtons
          }).then((data: promptAction.ActionMenuSuccessResponse) => {
            console.info('showActionMenu success callback, click button: ' + data.index);
          });
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showActionMenu args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

### showDialog

ArkTS-Dyn接口声明：

引用@ohos.prompt的[showDialog(options: ShowDialogOptions, callback: AsyncCallback&lt;ShowDialogSuccessResponse&gt;):void](../reference/apis-arkui/js-apis-prompt.md#promptshowdialog-1)

引用@ohos.promptAction的[showDialog(options: ShowDialogOptions, callback: AsyncCallback&lt;ShowDialogSuccessResponse&gt;):void](../reference/apis-arkui/js-apis-promptAction.md#promptactionshowdialogdeprecated-1)

替代的ArkTS-Sta接口声明：

引用@ohos.arkui.UIContext的[showDialog(options: promptAction.ShowDialogOptions, callback: AsyncCallback\<promptAction.ShowDialogSuccessResponse>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showdialog)



ArkTS-Dyn示例：

引用@ohos.prompt的showDialog。

```ts
import prompt from '@ohos.prompt';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick(() => {
        try {
          prompt.showDialog({
            title: 'showDialog Title Info',
            message: 'Message Info',
            buttons: [
              {
                text: 'button1',
                color: '#000000'
              },
              {
                text: 'button2',
                color: '#000000'
              }
            ]
          }, (err, data) => {
            if (err) {
              console.error('showDialog err: ' + err);
              return;
            }
            console.info('showDialog success callback, click button: ' + data.index);
          });
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showDialog args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

引用@ohos.promptAction的showDialog。

```ts
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick(() => {
        try {
          promptAction.showDialog({
            title: 'showDialog Title Info',
            message: 'Message Info',
            buttons: [
              {
                text: 'button1',
                color: '#000000'
              },
              {
                text: 'button2',
                color: '#000000'
              }
            ]
          }, (err, data) => {
            if (err) {
              console.error('showDialog err: ' + err);
              return;
            }
            console.info('showDialog success callback, click button: ' + data.index);
          });
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showDialog args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Button,
  ClickEvent,
  Builder
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@ohos.base';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().getPromptAction().showDialog({
            title: 'showDialog Title Info',
            message: 'Message Info',
            buttons: [
              {
                text: 'button1',
                color: '#000000'
              },
              {
                text: 'button2',
                color: '#000000'
              }
            ]
          }, (err: BusinessError|null, data: promptAction.ShowDialogSuccessResponse|undefined) => {
            if (err) {
              console.error('showDialog err: ' + err);
              return;
            }
            if (data) {
              console.info('showDialog success callback, click button: ' + data.index);
            }
          });
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showDialog args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

### showDialog

ArkTS-Dyn接口声明：

引用@ohos.prompt的[showDialog(options: ShowDialogOptions): Promise\<ShowDialogSuccessResponse>](../reference/apis-arkui/js-apis-prompt.md#promptshowdialog)

引用@ohos.promptAction的[showDialog(options: ShowDialogOptions): Promise\<ShowDialogSuccessResponse>](../reference/apis-arkui/js-apis-promptAction.md#promptactionshowdialogdeprecated)

替代的ArkTS-Sta接口声明：

引用@ohos.arkui.UIContext的[showDialog(options: promptAction.ShowDialogOptions): Promise\<promptAction.ShowDialogSuccessResponse>](../reference/apis-arkui/js-apis-arkui-UIContext.md#showdialog-1)



ArkTS-Dyn示例：

引用@ohos.prompt的showActionMenu。

```ts
import prompt from '@ohos.prompt';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick(() => {
        try {
          prompt.showDialog({
            title: 'showDialog Title Info',
            message: 'Message Info',
            buttons: [
              {
                text: 'button1',
                color: '#000000'
              },
              {
                text: 'button2',
                color: '#000000'
              }
            ]
          }).then((data) => {
            console.info('showDialog success callback, click button: ' + data.index);
          });
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showDialog args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

引用@ohos.promptAction的showActionMenu。

```ts
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick(() => {
        try {
          promptAction.showDialog({
            title: 'showDialog Title Info',
            message: 'Message Info',
            buttons: [
              {
                text: 'button1',
                color: '#000000'
              },
              {
                text: 'button2',
                color: '#000000'
              }
            ]
          }).then((data) => {
            console.info('showDialog success callback, click button: ' + data.index);
          });
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showDialog args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Button,
  ClickEvent,
  Builder
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@ohos.base';

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('click').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().getPromptAction().showDialog({
            title: 'showDialog Title Info',
            message: 'Message Info',
            buttons: [
              {
                text: 'button1',
                color: '#000000'
              },
              {
                text: 'button2',
                color: '#000000'
              }
            ]
          }).then((data: promptAction.ShowDialogSuccessResponse) => {
            console.info('showDialog success callback, click button: ' + data.index);
          });
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`showDialog args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

### openCustomDialog

ArkTS-Dyn接口声明：

引用@ohos.promptAction的[openCustomDialog(options: CustomDialogOptions): Promise&lt;number&gt;](../reference/apis-arkui/js-apis-promptAction.md#promptactionopencustomdialogdeprecated)

替代的ArkTS-Sta接口声明：

引用@ohos.arkui.UIContext的[openCustomDialog(options: promptAction.CustomDialogOptions): Promise\<number>](../reference/apis-arkui/js-apis-arkui-UIContext.md#opencustomdialog12-1)



ArkTS-Dyn示例：

引用@ohos.promptAction的openCustomDialog。

```ts
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  private customDialogComponentId: number = 0
  @Builder customDialogComponent() {
    Column() {
      Text('Dialog').fontSize(30)
      Button('Close').onClick(() => {
        try {
          this.getUIContext().getPromptAction().closeCustomDialog(this.customDialogComponentId)
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`closeCustomDialog error code is ${code}, message is ${message}`);
        }
      })
    }
  }

  build() {
    Column() {
      Button('click').onClick((e: ClickEvent) => {
        try {
          promptAction.openCustomDialog({
            builder: () => {
              this.customDialogComponent()
            },
          }).then((dialogId: number) => {
            this.customDialogComponentId = dialogId;
          });
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`openCustomDialog args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Button,
  ClickEvent,
  Builder,
  Text
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@ohos.base';

@Entry
@Component
struct Example {
  private customDialogComponentId: number = 0
  @Builder customDialogComponent() {
    Column() {
      Text('Dialog').fontSize(30)
      Button('Close').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().getPromptAction().closeCustomDialog(this.customDialogComponentId)
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`closeCustomDialog error code is ${code}, message is ${message}`);
        }
      })
    }
  }

  build() {
    Column() {
      Button('click').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().getPromptAction().openCustomDialog({
            builder: this.customDialogComponent,
          } as promptAction.CustomDialogOptions
          ).then((dialogId: number) => {
            this.customDialogComponentId = dialogId;
          });
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`openCustomDialog args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

### closeCustomDialog

由@ohos.promptAction提供的closeCustomDialog接口在ArkTS-Dyn中已标记为废弃，并在ArkTS-Sta中不再支持。

ArkTS-Dyn接口声明：

引用@ohos.promptAction的[closeCustomDialog(dialogId: number): void](../reference/apis-arkui/js-apis-promptAction.md#promptactionclosecustomdialogdeprecated)

替代的ArkTS-Sta接口声明：

引用@ohos.arkui.UIContext的[closeCustomDialog(dialogId: number): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#closecustomdialog12-1)



ArkTS-Dyn示例：

引用@ohos.promptAction的closeCustomDialog。

```ts
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Example {
  private customDialogComponentId: number = 0
  @Builder customDialogComponent() {
    Column() {
      Text('Dialog').fontSize(30)
      Button('Close').onClick(() => {
        try {
          this.getUIContext().getPromptAction().closeCustomDialog(this.customDialogComponentId)
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`closeCustomDialog error code is ${code}, message is ${message}`);
        }
      })
    }
  }

  build() {
    Column() {
      Button('click').onClick((e: ClickEvent) => {
        try {
          promptAction.openCustomDialog({
            builder: () => {
              this.customDialogComponent()
            },
          }).then((dialogId: number) => {
            this.customDialogComponentId = dialogId;
          });
        } catch (error) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`openCustomDialog args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import {
  Entry,
  Component,
  Column,
  Button,
  ClickEvent,
  Builder,
  Text
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import promptAction from '@ohos.promptAction';
import { BusinessError } from '@ohos.base';

@Entry
@Component
struct Example {
  private customDialogComponentId: number = 0
  @Builder customDialogComponent() {
    Column() {
      Text('Dialog').fontSize(30)
      Button('Close').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().getPromptAction().closeCustomDialog(this.customDialogComponentId)
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`closeCustomDialog error code is ${code}, message is ${message}`);
        }
      })
    }
  }

  build() {
    Column() {
      Button('click').onClick((e: ClickEvent) => {
        try {
          this.getUIContext().getPromptAction().openCustomDialog({
            builder: this.customDialogComponent,
          } as promptAction.CustomDialogOptions
          ).then((dialogId: number) => {
            this.customDialogComponentId = dialogId;
          });
        } catch (error: BusinessError) {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          console.error(`openCustomDialog args error code is ${code}, message is ${message}`);
        };
      })
    }
  }
}
```