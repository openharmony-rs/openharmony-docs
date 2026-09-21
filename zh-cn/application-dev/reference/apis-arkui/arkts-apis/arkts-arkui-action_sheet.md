# action_sheet(ActionSheet)

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ActionSheet](arkts-arkui-actionsheet-c.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ActionSheetButtonOptions](arkts-arkui-actionsheetbuttonoptions-i.md) | 弹窗中按钮的样式。 |
| [ActionSheetOffset](arkts-arkui-actionsheetoffset-i.md) | 弹窗相对alignment所在位置的偏移量。 |
| [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md) | 列表选择弹窗的样式。 |
| [DismissDialogAction](arkts-arkui-dismissdialogaction-i.md) | 弹窗关闭的信息。 |
| [SheetInfo](arkts-arkui-sheetinfo-i.md) | 弹窗中的选项内容，每一项支持设置文本、图标以及选中的回调。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionSheetOptions](arkts-arkui-actionsheetoptions-i-sys.md) | 列表选择弹窗的样式。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [ImmersiveMode](arkts-arkui-immersivemode-t.md) | 弹窗的蒙层效果。 |
| [LevelMode](arkts-arkui-levelmode-t.md) | 弹窗的显示层级。 |

## 示例

### 示例1（弹出列表选择弹窗）

该示例通过点击按钮弹出列表选择弹窗。



```TypeScript
// xxx.ets
@Entry
@Component
struct ActionSheetExample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('Click to Show ActionSheet')
        .onClick(() => {
          this.getUIContext().showActionSheet({
            title: 'ActionSheet title',
            subtitle: 'ActionSheet subtitle',
            message: 'message',
            autoCancel: true,
            confirm: {
              defaultFocus: true,
              value: 'Confirm button',
              action: () => {
                console.info('Get ActionSheet handled');
              }
            },
            cancel: () => {
              console.info('ActionSheet canceled');
            },
            onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
              console.info(`reason= ${dismissDialogAction.reason}`);
              console.info('ActionSheet onWillDismiss');
              if (dismissDialogAction.reason === DismissReason.PRESS_BACK) {
                dismissDialogAction.dismiss();
              }
              if (dismissDialogAction.reason === DismissReason.TOUCH_OUTSIDE) {
                dismissDialogAction.dismiss();
              }
            },
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -10 },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          })
        })
    }.width('100%')
    .height('100%')
  }
}
```

### 示例2（可在主窗外弹出的弹窗）

在2in1设备上设置showInSubWindow为true时，可以弹出在主窗外显示的弹窗。



```TypeScript
// xxx.ets
@Entry
@Component
struct ActionSheetExample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('Click to Show ActionSheet')
        .onClick(() => {
          this.getUIContext().showActionSheet({
            title: 'ActionSheet title',
            subtitle: 'ActionSheet subtitle',
            message: 'message',
            autoCancel: true,
            showInSubWindow: true,
            isModal: true,
            confirm: {
              defaultFocus: true,
              value: 'Confirm button',
              action: () => {
                console.info('Get ActionSheet handled');
              }
            },
            cancel: () => {
              console.info('ActionSheet canceled');
            },
            onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
              console.info(`reason= ${dismissDialogAction.reason}`);
              console.info('ActionSheet onWillDismiss');
              if (dismissDialogAction.reason === DismissReason.PRESS_BACK) {
                dismissDialogAction.dismiss();
              }
              if (dismissDialogAction.reason === DismissReason.TOUCH_OUTSIDE) {
                dismissDialogAction.dismiss();
              }
            },
            alignment: DialogAlignment.Center,
            offset: { dx: 0, dy: -10 },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          })
        })
    }.width('100%')
    .height('100%')
  }
}
```

### 示例3（设置弹窗的动画）

该示例通过配置transition实现弹窗的显示和消失动画。



```TypeScript
// xxx.ets
@Entry
@Component
struct ActionSheetExample {
  build() {
    Column({ space: 5 }) {
      Button('ActionSheet Set Duration')
        .onClick(() => {
          this.getUIContext().showActionSheet({
            title: 'ActionSheet 1',
            message: 'Set Animation Duration open 3 second, close 100 ms',
            autoCancel: true,
            alignment: DialogAlignment.Top,
            transition: TransitionEffect.asymmetric(TransitionEffect.OPACITY
              .animation({ duration: 3000, curve: Curve.Sharp })
              .combine(TransitionEffect.scale({ x: 1.5, y: 1.5 }).animation({ duration: 3000, curve: Curve.Sharp })),
              TransitionEffect.OPACITY.animation({ duration: 100, curve: Curve.Smooth })
                .combine(TransitionEffect.scale({ x: 0.5, y: 0.5 }).animation({ duration: 100, curve: Curve.Smooth }))),
            offset: { dx: 0, dy: -20 },
            confirm: {
              value: 'button',
              action: () => {
                console.info('Button-clicking callback');
              }
            },
            cancel: () => {
              console.info('Closed callbacks');
            },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          })
        }).backgroundColor(0x317aff).height('88px')
    }.width('100%').margin({ top: 5 })
  }
}
```

### 示例4（设置弹窗的样式）

该示例定义了ActionSheet的样式，如宽度、高度、背景色、阴影等。



```TypeScript
// xxx.ets
@Entry
@Component
struct ActionSheetExample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center }) {
      Button('Click to Show ActionSheet')
        .onClick(() => {
          this.getUIContext().showActionSheet({
            title: 'ActionSheet title',
            subtitle: 'ActionSheet subtitle',
            message: 'message',
            autoCancel: true,
            width: 300,
            height: 350,
            cornerRadius: 20,
            borderWidth: 1,
            borderStyle: BorderStyle.Solid, // 设置边框样式
            borderColor: Color.Blue, // 设置边框颜色
            backgroundColor: Color.White,
            shadow: ({
              radius: 20,
              color: Color.Grey,
              offsetX: 50,
              offsetY: 0
            }),
            confirm: {
              defaultFocus: true,
              value: 'Confirm button',
              action: () => {
                console.info('Get ActionSheet handled');
              }
            },
            cancel: () => {
              console.info('ActionSheet canceled');
            },
            onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
              console.info(`reason= ${dismissDialogAction.reason}`);
              console.info('ActionSheet onWillDismiss');
              if (dismissDialogAction.reason === DismissReason.PRESS_BACK) {
                dismissDialogAction.dismiss();
              }
              if (dismissDialogAction.reason === DismissReason.TOUCH_OUTSIDE) {
                dismissDialogAction.dismiss();
              }
            },
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -10 },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          })
        })
    }.width('100%')
  }
}
```

### 示例5（悬停态弹窗）

```TypeScript
// xxx.ets
@Entry
@Component
struct ActionSheetExample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('Click to Show ActionSheet')
        .onClick(() => {
          this.getUIContext().showActionSheet({
            title: 'ActionSheet title',
            subtitle: 'ActionSheet subtitle',
            message: 'message',
            autoCancel: true,
            confirm: {
              defaultFocus: true,
              value: 'Confirm button',
              action: () => {
                console.info('Get ActionSheet handled');
              }
            },
            cancel: () => {
              console.info('ActionSheet canceled');
            },
            onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
              console.info(`reason= ${dismissDialogAction.reason}`);
              console.info('ActionSheet onWillDismiss');
              if (dismissDialogAction.reason === DismissReason.PRESS_BACK) {
                dismissDialogAction.dismiss();
              }
              if (dismissDialogAction.reason === DismissReason.TOUCH_OUTSIDE) {
                dismissDialogAction.dismiss();
              }
            },
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -10 },
            enableHoverMode: true,
            hoverModeArea: HoverModeAreaType.TOP_SCREEN,
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          })
        })
    }.width('100%')
    .height('100%')
  }
}
```

### 示例6（弹窗生命周期）

该示例为弹窗配置生命周期回调。

从API version 19开始，在ActionSheetOptions中新增了onDidAppear、onDidDisappear、onWillAppear和onWillDisappear属性。



```TypeScript
// xxx.ets
@Entry
@Component
struct Example1 {
  @State log: string = 'Log information:';

  build() {
    Column({ space: 5 }) {
      Button('ActionSheet')
        .onClick(() => {
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
                  console.info('ActionSheet apples')
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('ActionSheet bananas')
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('ActionSheet pears')
                }
              }
            ],
            onDidAppear: () => {
              this.log += '# onDidAppear';
              console.info('ActionSheet,is onDidAppear!');
            },
            onDidDisappear: () => {
              this.log += '# onDidDisappear';
              console.info('ActionSheet,is onDidDisappear!');
            },
            onWillAppear: () => {
              this.log = 'Log information:onWillAppear';
              console.info('ActionSheet,is onWillAppear!');
            },
            onWillDisappear: () => {
              this.log += '# onWillDisappear';
              console.info('ActionSheet,is onWillDisappear!');
            }
          })
        })
      Text(this.log).fontSize(30).margin({ top: 200 })
    }.width('100%').margin({ top: 5 })
  }
}
```

### 示例7（自定义背景模糊效果参数）

该示例通过配置backgroundBlurStyleOptions，实现自定义背景模糊效果。

从API version 19开始，在ActionSheetOptions中新增了backgroundBlurStyleOptions属性。



```TypeScript
@Entry
@Component
struct ActionSheetExample {
  build() {
    Stack({ alignContent: Alignment.Top }) {
      Image($r('app.media.bg'))
      Column() {
        Button("ActionSheet")
          .margin(20)
          .onClick(() => {
            this.getUIContext().showActionSheet({
              title: 'ActionSheet Title',
              subtitle: 'ActionSheet Subtitle',
              message: 'ActionSheet Text',
              sheets: [
                {
                  title: 'Apples',
                  action: () => {
                    console.info('apples');
                  }
                },
                {
                  title: 'Bananas',
                  action: () => {
                    console.info('bananas');
                  }
                },
                {
                  title: 'Pears',
                  action: () => {
                    console.info('pears');
                  }
                }
              ],
              alignment: DialogAlignment.Center,
              backgroundColor: undefined,
              backgroundBlurStyle: BlurStyle.Thin,
              backgroundBlurStyleOptions: {
                colorMode: ThemeColorMode.LIGHT,
                adaptiveColor: AdaptiveColor.AVERAGE,
                scale: 1,
                blurOptions: { grayscale: [20, 20] },
              },
            });
          })
      }.width('100%')
    }
  }
}
```

### 示例8（自定义背景效果参数）

该示例通过配置backgroundEffect，实现自定义背景效果。

从API version 19开始，在ActionSheetOptions中新增了backgroundEffect属性。



```TypeScript
@Entry
@Component
struct ActionSheetExample {
  build() {
    Stack({ alignContent: Alignment.Top }) {
      Image($r('app.media.bg'))
      Column() {
        Button("ActionSheet")
          .margin(20)
          .onClick(() => {
            this.getUIContext().showActionSheet({
              title: 'ActionSheet Title',
              subtitle: 'ActionSheet Subtitle',
              message: 'ActionSheet Text',
              sheets: [
                {
                  title: 'Apples',
                  action: () => {
                    console.info('apples');
                  }
                },
                {
                  title: 'Bananas',
                  action: () => {
                    console.info('bananas');
                  }
                },
                {
                  title: 'Pears',
                  action: () => {
                    console.info('pears');
                  }
                }
              ],
              alignment: DialogAlignment.Center,
              backgroundColor: undefined,
              backgroundBlurStyle: BlurStyle.Thin,
              backgroundEffect: {
                radius: 60,
                saturation: 0,
                brightness: 1,
                color: Color.White,
                blurOptions: { grayscale: [20, 20] }
              },
            });
          })
      }.width('100%')
    }
  }
}
```

### 示例9（设置弹窗的沉浸光感效果）

该示例通过ActionSheetOptions中的systemMaterial属性设置组件的系统材质，实现沉浸光感效果。设置系统材质后，ActionSheet弹出过程中会有非线性形变和边缘流光。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在ActionSheetOptions中新增了systemMaterial属性。

```TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct ActionSheetExample {
  build() {
    Stack({ alignContent: Alignment.Top }) {
      Column() {
        Button("ActionSheet")
          .margin(20)
          .onClick(() => {
            this.getUIContext().showActionSheet({
              title: 'ActionSheet Title',
              subtitle: 'ActionSheet Subtitle',
              message: 'ActionSheet Text',
              sheets: [
                {
                  title: 'Apples',
                  action: () => {
                    console.info('apples');
                  }
                },
                {
                  title: 'Bananas',
                  action: () => {
                    console.info('bananas');
                  }
                },
                {
                  title: 'Pears',
                  action: () => {
                    console.info('pears');
                  }
                }
              ],
              alignment: DialogAlignment.Center,
              systemMaterial: new uiMaterial.ImmersiveMaterial({ style: uiMaterial.ImmersiveStyle.ULTRA_THICK })
            });
          })
      }
      .height('100%')
      .width('100%')
      // 请开发者替换为实际资源文件
      .backgroundImage($r("app.media.img"))
      .backgroundImageSize({ width: '100%', height: '100%' })
    }
  }
}
```
