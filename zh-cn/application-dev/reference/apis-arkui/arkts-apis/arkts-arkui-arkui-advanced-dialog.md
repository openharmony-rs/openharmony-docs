# @ohos.arkui.advanced.Dialog(Dialog)

弹出框是一种模态窗口，用于临时展示用户需关注的信息或待处理的操作，同时保持当前上下文环境。用户必须完成交互才能退出该模式。

> **说明：**
 >
 > - 该组件从API version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
 >
 > - 该组件仅可在Stage模型下使用。
 >
 > - 如果Dialog设置[通用属性](../arkts-components/arkts-arkui-common-comp.md#common)和[通用事件](../arkts-components/arkts-arkui-common-comp.md#common)，编译工具链会额外生
 > 成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到Dialog本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议Dialog设置通用属性和通用事件。



## 导入模块

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md) |  |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AlertDialog](arkts-arkui-arkui-advanced-dialog-alertdialog-s.md) | 操作确认类弹出框，用于在触发一个将产生严重后果的不可逆操作（如删除、重置、取消编辑、停止等）时进行确认。 |
| [ConfirmDialog](arkts-arkui-arkui-advanced-dialog-confirmdialog-s.md) | 信息确认类弹出框，用于在操作未正确执行（如网络错误、电池电量过低），或未正确操作时（如指纹录入）反馈错误或提示信息。 |
| [CustomContentDialog](arkts-arkui-arkui-advanced-dialog-customcontentdialog-s.md) | 自定义内容区弹出框，同时支持定义操作区按钮样式。 |
| [LoadingDialog](arkts-arkui-arkui-advanced-dialog-loadingdialog-s.md) | 进度加载类弹出框，用于显示操作执行中的提示信息。 |
| [PopoverDialog](arkts-arkui-arkui-advanced-dialog-popoverdialog-s.md) | 跟手弹出框，基于目标组件位置弹出，上述的TipsDialog、SelectDialog、ConfirmDialog、AlertDialog、LoadingDialog、CustomContentDialog都可作为弹出框内容。 |
| [SelectDialog](arkts-arkui-arkui-advanced-dialog-selectdialog-s.md) | 选择类弹出框，弹框中以列表或网格的形式提供可选的内容。 |
| [TipsDialog](arkts-arkui-arkui-advanced-dialog-tipsdialog-s.md) | 提示弹出框，用于提醒用户关注特定事项或进行确认操作。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PopoverOptions](arkts-arkui-arkui-advanced-dialog-popoveroptions-i.md) | 跟手弹出框参数，用于设置弹出框内容、位置属性等。 |

## 示例

### 示例1（上图下文弹出框）

上图下文弹出框，包含imageRes、content等内容。



```TypeScript
import { TipsDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  dialogControllerImage: CustomDialogController = new CustomDialogController({
    builder: TipsDialog({
      imageRes: $r('sys.media.ohos_ic_public_voice'),
      content: '想要卸载这个APP嘛?',
      primaryButton: {
        value: '取消',
        action: () => {
          console.info('Callback when the first button is clicked');
        },
      },
      secondaryButton: {
        value: '删除',
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
          Button("上图下文弹出框")
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

### 示例2（纯列表弹出框）

纯列表弹出框，包含selectedIndex、radioContent等内容。



```TypeScript
import { SelectDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // 设置默认选中radio的index
  radioIndex: number = 0;
  dialogControllerList: CustomDialogController = new CustomDialogController({
    builder: SelectDialog({
      title: '文本标题',
      selectedIndex: this.radioIndex,
      confirm: {
        value: '取消',
        action: () => {},
      },
      radioContent: [
        {
          title: '文本文本文本文本文本',
          action: () => {
            this.radioIndex = 0;
          }
        },
        {
          title: '文本文本文本文本',
          action: () => {
            this.radioIndex = 1;
          }
        },
        {
          title: '文本文本文本文本',
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
          Button("纯列表弹出框")
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

### 示例3（文本与勾选弹出框）

文本与勾选弹出框，包含content、checkTips等内容。



```TypeScript
import { ConfirmDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  isChecked: boolean = false;
  dialogControllerCheckBox: CustomDialogController = new CustomDialogController({
    builder: ConfirmDialog({
      title: '文本标题',
      content: '文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本',
      // 勾选框选中状态
      isChecked: this.isChecked,
      // 勾选框说明文本
      checkTips: '禁止后不再提示',
      primaryButton: {
        value: '禁止',
        action: () => {},
      },
      secondaryButton: {
        value: '允许',
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
          Button("文本+勾选弹出框")
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

### 示例4（纯文本弹出框）

纯文本弹出框，包含primaryTitle、secondaryTitle、content等内容。



```TypeScript
import { AlertDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  dialogControllerConfirm: CustomDialogController = new CustomDialogController({
    builder: AlertDialog({
      primaryTitle: '弹框一级标题',
      secondaryTitle: '弹框二级标题',
      content: '文本文本文本文本文本',
      primaryButton: {
        value: '取消',
        action: () => {
        },
      },
      secondaryButton: {
        value: '确认',
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
          Button("纯文本弹出框")
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

### 示例5（进度加载类弹出框）

进度加载类弹出框，包含content等内容。



```TypeScript
import { LoadingDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  dialogControllerProgress: CustomDialogController = new CustomDialogController({
    builder: LoadingDialog({
      content: '文本文本文本文本文本...',
    }),
  })

  build() {
    Row() {
      Stack() {
        Column() {
          Button("进度加载类弹出框")
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

### 示例6（自定义主题风格弹出框）

自定义主题风格弹出框，包含content、theme等内容。



```TypeScript
import { CustomColors, CustomTheme, LoadingDialog } from '@kit.ArkUI';

class CustomThemeImpl implements CustomTheme {
  colors?: CustomColors;

  constructor(colors: CustomColors) {
    this.colors = colors;
  }
}

// 自定义内容文字及loading组件主题颜色
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

### 示例7（自定义深浅色模式弹出框）

自定义深浅色模式弹出框，包含content、themeColorMode等内容。



```TypeScript
import { LoadingDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  dialogController: CustomDialogController = new CustomDialogController({
    builder: LoadingDialog({
      content: 'Text',
      themeColorMode: ThemeColorMode.DARK, // 设置弹出框深浅色模式为深色模式
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

### 示例8（自定义内容弹出框）

支持自定义内容弹出框，包含contentBuilder、buttons等内容。



```TypeScript
import { CustomContentDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  dialogController: CustomDialogController = new CustomDialogController({
    builder: CustomContentDialog({
      primaryTitle: '标题',
      secondaryTitle: '辅助文本',
      contentBuilder: () => {
        this.buildContent();
      },
      buttons: [
        { 
          value: '按钮1',
          buttonStyle: ButtonStyleMode.TEXTUAL,
          action: () => {
            console.info('Callback when the button is clicked');
          }
        },
        {
          value: '按钮2',
          buttonStyle: ButtonStyleMode.TEXTUAL,
          role: ButtonRole.ERROR
        }
      ],
    }),
  });

  build() {
    Column() {
      Button("支持自定义内容弹出框")
        .onClick(() => {
          this.dialogController.open();
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
  
  // 自定义弹出框的内容区
  @Builder
  buildContent(): void {
    Column() {
      Text('内容区')
    }
    .width('100%')
  }
}
```

### 示例9（跟手弹出框）

从API version 14开始，该示例展示了设置跟手弹出框（警告弹出框为例），包含visible、popover、targetBuilder等内容。



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
  
  // 跟手弹出框内容
  @Builder dialogBuilder() {
    AlertDialog({
      content: '跟手弹出框',
      primaryButton: {
        value: '取消',
        action: () => {
          this.isShow = false;
        },
      },
      secondaryButton: {
        value: '确认',
        action: () => {
          this.isShow = false;
        },
      },
    });
  }

  // 跟手弹出框绑定的builder
  @Builder buttonBuilder() {
    Button('跟手弹出框目标组件')
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

### 示例10（弹出框按钮设置默认获焦）

从API version 18开始，该示例展示了设置默认获焦按钮弹出框（以AlertDialog为例），包含defaultFocus等内容。

```TypeScript
import { AlertDialog } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  dialogController: CustomDialogController = new CustomDialogController({
    builder: AlertDialog({
      primaryTitle: 'AlertDialog',
      secondaryTitle: '副标题',
      content: '第二个按钮设置为默认',
      primaryButton: {
        value: 'DEFAULT',
        action: () => {}
      },
      secondaryButton: {
        value: 'TRUE',
        defaultFocus: true, // 设置该按钮为默认获焦按钮。
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
