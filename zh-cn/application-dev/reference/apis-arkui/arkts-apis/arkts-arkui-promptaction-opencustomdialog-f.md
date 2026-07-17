# openCustomDialog

## 导入模块

```TypeScript
import { LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## openCustomDialog

```TypeScript
function openCustomDialog(options: CustomDialogOptions): Promise<number>
```

打开自定义弹窗。通过Promise返回结果。

<!--Del-->不支持在ServiceExtension中使用。<!--DelEnd-->

弹窗宽度在设备竖屏时默认为 所在窗口宽度 - 左右margin（16vp，设备为2in1时为40vp），最大默认宽度为400vp。

> **说明：**  
>  
> - 从API version 11开始支持，从API version 18开始废弃，建议使用[openCustomDialog](arkts-apis-uicontext-promptaction.md#opencustomdialog12-1)替代。openCustomDialog需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，然后通过该对象进行调用。且直接使用openCustomDialog可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题。  
>  
> - 从API version 12开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取当前UI上下文关联的[PromptAction](arkts-apis-uicontext-promptaction.md)对象。

**起始版本：** 11

**废弃版本：** 18

**替代接口：** openCustomDialog

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-promptAction-function openCustomDialog(options: CustomDialogOptions): Promise<number>--><!--Device-promptAction-function openCustomDialog(options: CustomDialogOptions): Promise<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CustomDialogOptions](arkts-arkui-promptaction-customdialogoptions-i.md) | 是 | 自定义弹窗的内容。<br>**说明：** 如果BaseDialogOptions中的[isModal](js-apis-promptAction.md#basedialogoptions11)与[showInSubWindow](js-apis-promptAction.md#basedialogoptions11)同时设置为true，则只生效showInSubWindow = true，此时为非模态弹出框且不会显示蒙层，并在子窗口中显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | 返回供closeCustomDialog使用的对话框id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |

**示例：**

```TypeScript
import { promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private customDialogComponentId: number = 0;

  @Builder
  customDialogComponent() {
    Column() {
      Text('弹窗').fontSize(30)
      Row({ space: 50 }) {
        Button("确认").onClick(() => {
          try {
            promptAction.closeCustomDialog(this.customDialogComponentId)
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`closeCustomDialog error code is ${code}, message is ${message}`);
          }
        })
        Button("取消").onClick(() => {
          try {
            promptAction.closeCustomDialog(this.customDialogComponentId)
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`closeCustomDialog error code is ${code}, message is ${message}`);
          }
        })
      }
    }.height(200).padding(5).justifyContent(FlexAlign.SpaceBetween)
  }

  build() {
    Row() {
      Column({ space: 20 }) {
        Text('组件内弹窗')
          .fontSize(30)
          .onClick(() => {
            promptAction.openCustomDialog({
              builder: () => {
                this.customDialogComponent()
              },
              onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
                console.info('reason' + JSON.stringify(dismissDialogAction.reason));
                console.info('dialog onWillDismiss');
                if (dismissDialogAction.reason == DismissReason.PRESS_BACK) {
                  dismissDialogAction.dismiss();
                }
                if (dismissDialogAction.reason == DismissReason.TOUCH_OUTSIDE) {
                  dismissDialogAction.dismiss();
                }
              }
            }).then((dialogId: number) => {
              this.customDialogComponentId = dialogId;
            })
              .catch((error: BusinessError) => {
                console.error(`openCustomDialog error code is ${error.code}, message is ${error.message}`);
              })
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}


```

```TypeScript
import { promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private customDialogComponentId: number = 0;

  @Builder
  customDialogComponent() {
    Column() {
      Text('弹窗').fontSize(30)
      Row({ space: 50 }) {
        Button("确认").onClick(() => {
          try {
            promptAction.closeCustomDialog(this.customDialogComponentId)
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`closeCustomDialog error code is ${code}, message is ${message}`);
          }
        })
        Button("取消").onClick(() => {
          try {
            promptAction.closeCustomDialog(this.customDialogComponentId)
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`closeCustomDialog error code is ${code}, message is ${message}`);
          }
        })
      }
    }.height(200).padding(5).justifyContent(FlexAlign.SpaceBetween)
  }

  build() {
    Row() {
      Column({ space: 20 }) {
        Text('组件内弹窗')
          .fontSize(30)
          .onClick(() => {
            promptAction.openCustomDialog({
              builder: () => {
                this.customDialogComponent()
              },
              onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
                console.info('reason' + JSON.stringify(dismissDialogAction.reason));
                console.info('dialog onWillDismiss');
                if (dismissDialogAction.reason == DismissReason.PRESS_BACK) {
                  dismissDialogAction.dismiss();
                }
                if (dismissDialogAction.reason == DismissReason.TOUCH_OUTSIDE) {
                  dismissDialogAction.dismiss();
                }
              }
            }).then((dialogId: number) => {
              this.customDialogComponentId = dialogId;
            })
              .catch((error: BusinessError) => {
                console.error(`openCustomDialog error code is ${error.code}, message is ${error.message}`);
              })
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}


```

直接使用openCustomDialog可能导致实例不明确的问题，建议使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，再通过此对象调用替代方法[openCustomDialog](arkts-apis-uicontext-promptaction.md#opencustomdialog12-1)。

```TypeScript
import { LevelMode, ImmersiveMode } from '@kit.ArkUI';

let customDialogId: number = 0;

@Builder
function customDialogBuilder(uiContext: UIContext) {
  Column() {
    Text('Custom dialog Message').fontSize(10)
    Row() {
      Button("确认").onClick(() => {
        uiContext.getPromptAction().closeCustomDialog(customDialogId);
      })
      Blank().width(50)
      Button("取消").onClick(() => {
        uiContext.getPromptAction().closeCustomDialog(customDialogId);
      })
    }
  }
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  private uiContext: UIContext = this.getUIContext();

  @Builder
  customDialogComponent() {
    customDialogBuilder(this.uiContext)
  }

  build() {
    Row() {
      Column() {
        Text(this.message).id("test_text")
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            const node: FrameNode | null = this.uiContext.getFrameNodeById("test_text") || null;
            this.uiContext.getPromptAction().openCustomDialog({
              builder: () => {
                this.customDialogComponent()
              },
              keyboardAvoidMode: KeyboardAvoidMode.NONE,
              showInSubWindow: false,
              offset: { dx: 5, dy: 5 },
              backgroundColor: 0xd9ffffff,
              cornerRadius: 20,
              width: '80%',
              height: 200,
              borderWidth: 1,
              borderStyle: BorderStyle.Dashed, // 使用borderStyle属性，需要和borderWidth属性一起使用
              borderColor: Color.Blue, // 使用borderColor属性，需要和borderWidth属性一起使用
              shadow: ({
                radius: 20,
                color: Color.Grey,
                offsetX: 50,
                offsetY: 0
              }),
              levelMode: LevelMode.EMBEDDED,
              levelUniqueId: node?.getUniqueId(),
              immersiveMode: ImmersiveMode.DEFAULT,
            }).then((dialogId: number) => {
              customDialogId = dialogId;
            })
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

直接使用openCustomDialog可能导致实例不明确的问题，建议使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，再通过此对象调用替代方法[openCustomDialog](arkts-apis-uicontext-promptaction.md#opencustomdialog12-1)。

```TypeScript
import { LevelMode, ImmersiveMode } from '@kit.ArkUI';

let customDialogId: number = 0;

@Builder
function customDialogBuilder(uiContext: UIContext) {
  Column() {
    Text('Custom dialog Message').fontSize(10)
    Row() {
      Button("确认").onClick(() => {
        uiContext.getPromptAction().closeCustomDialog(customDialogId);
      })
      Blank().width(50)
      Button("取消").onClick(() => {
        uiContext.getPromptAction().closeCustomDialog(customDialogId);
      })
    }
  }
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  private uiContext: UIContext = this.getUIContext();

  @Builder
  customDialogComponent() {
    customDialogBuilder(this.uiContext)
  }

  build() {
    Row() {
      Column() {
        Text(this.message).id("test_text")
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            const node: FrameNode | null = this.uiContext.getFrameNodeById("test_text") || null;
            this.uiContext.getPromptAction().openCustomDialog({
              builder: () => {
                this.customDialogComponent()
              },
              keyboardAvoidMode: KeyboardAvoidMode.NONE,
              showInSubWindow: false,
              offset: { dx: 5, dy: 5 },
              backgroundColor: 0xd9ffffff,
              cornerRadius: 20,
              width: '80%',
              height: 200,
              borderWidth: 1,
              borderStyle: BorderStyle.Dashed, // 使用borderStyle属性，需要和borderWidth属性一起使用
              borderColor: Color.Blue, // 使用borderColor属性，需要和borderWidth属性一起使用
              shadow: ({
                radius: 20,
                color: Color.Grey,
                offsetX: 50,
                offsetY: 0
              }),
              levelMode: LevelMode.EMBEDDED,
              levelUniqueId: node?.getUniqueId(),
              immersiveMode: ImmersiveMode.DEFAULT,
            }).then((dialogId: number) => {
              customDialogId = dialogId;
            })
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

直接使用openCustomDialog可能导致实例不明确的问题，建议使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，再通过此对象调用替代方法[openCustomDialog](arkts-apis-uicontext-promptaction.md#opencustomdialog12-1)。

```TypeScript
// Index.ets
import { LevelMode, ImmersiveMode } from '@kit.ArkUI';

let customDialogId: number = 0;

@Builder
function customDialogBuilder(uiContext: UIContext) {
  Column() {
    Text('Custom dialog Message').fontSize(10).height(100)
    Row() {
      Button("Next").onClick(() => {
        uiContext.getRouter().pushUrl({ url: 'pages/Next' });
      })
      Blank().width(50)
      Button("Close").onClick(() => {
        uiContext.getPromptAction().closeCustomDialog(customDialogId);
      })
    }
  }.padding(20)
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  private uiContext: UIContext = this.getUIContext();

  @Builder
  customDialogComponent() {
    customDialogBuilder(this.uiContext)
  }

  build() {
    Row() {
      Column() {
        Text(this.message).id("test_text")
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            const node: FrameNode | null = this.uiContext.getFrameNodeById("test_text") || null;
            this.uiContext.getPromptAction().openCustomDialog({
              builder: () => {
                this.customDialogComponent()
              },
              levelMode: LevelMode.EMBEDDED,
              levelUniqueId: node?.getUniqueId(),
              immersiveMode: ImmersiveMode.DEFAULT,
            }).then((dialogId: number) => {
              customDialogId = dialogId;
            })
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

直接使用openCustomDialog可能导致实例不明确的问题，建议使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，再通过此对象调用替代方法[openCustomDialog](arkts-apis-uicontext-promptaction.md#opencustomdialog12-1)。

```TypeScript
// Index.ets
import { LevelMode, ImmersiveMode } from '@kit.ArkUI';

let customDialogId: number = 0;

@Builder
function customDialogBuilder(uiContext: UIContext) {
  Column() {
    Text('Custom dialog Message').fontSize(10).height(100)
    Row() {
      Button("Next").onClick(() => {
        uiContext.getRouter().pushUrl({ url: 'pages/Next' });
      })
      Blank().width(50)
      Button("Close").onClick(() => {
        uiContext.getPromptAction().closeCustomDialog(customDialogId);
      })
    }
  }.padding(20)
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  private uiContext: UIContext = this.getUIContext();

  @Builder
  customDialogComponent() {
    customDialogBuilder(this.uiContext)
  }

  build() {
    Row() {
      Column() {
        Text(this.message).id("test_text")
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            const node: FrameNode | null = this.uiContext.getFrameNodeById("test_text") || null;
            this.uiContext.getPromptAction().openCustomDialog({
              builder: () => {
                this.customDialogComponent()
              },
              levelMode: LevelMode.EMBEDDED,
              levelUniqueId: node?.getUniqueId(),
              immersiveMode: ImmersiveMode.DEFAULT,
            }).then((dialogId: number) => {
              customDialogId = dialogId;
            })
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

```TypeScript
// Next.ets
@Entry
@Component
struct Next {
  @State message: string = 'Back';

  build() {
    Row() {
      Column() {
        Button(this.message)
          .onClick(() => {
            this.getUIContext().getRouter().back();
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

```TypeScript
// Next.ets
@Entry
@Component
struct Next {
  @State message: string = 'Back';

  build() {
    Row() {
      Column() {
        Button(this.message)
          .onClick(() => {
            this.getUIContext().getRouter().back();
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

