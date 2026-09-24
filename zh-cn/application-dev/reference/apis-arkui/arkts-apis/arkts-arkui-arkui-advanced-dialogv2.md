# @ohos.arkui.advanced.DialogV2

弹出框是一种模态窗口，用于在保持当前上下文环境时，临时展示用户需关注的信息或待处理的操作，用户在弹出框内完成交互。模态弹出框需要用户进行交互才能够退出模态模式。DialogV2提供了提示、选择、确认、警告、加载等多种类型的弹出框，适用于确认删除、显示加载进度、用户选择项、重要提示等场景，帮助开发者简化模态对话框的实现，提供一致的用户交互体验。

该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于
 [状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组
 件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制弹出框的数据和状态，实现更高效的用户界面刷新。

> **说明：**
 >
 > - 该组件仅可在Stage模型下使用。
 >
 > - 如果DialogV2设置[通用属性](../arkts-components/arkts-arkui-common-comp.md#common)和[通用事件](../arkts-components/arkts-arkui-common-comp.md#common)，编译工具链会额
 > 外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到DialogV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议DialogV2设置通用属性和通用事
 > 件。



## 导入模块

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md) | 弹出框操作区按钮。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AlertDialogV2](arkts-arkui-arkui-advanced-dialogv2-alertdialogv2-s.md) | 操作确认类弹出框。当触发一个将产生严重后果的不可逆操作时，如删除、重置、取消编辑、停止等，会触发该类弹出框提示。 |
| [ConfirmDialogV2](arkts-arkui-arkui-advanced-dialogv2-confirmdialogv2-s.md) | 信息确认类弹出框，用于反馈错误或提示信息。当操作未正确执行（如网络错误、电池电量过低）或用户操作不当时（如指纹录入），弹出此类对话框进行提示。 |
| [CustomContentDialogV2](arkts-arkui-arkui-advanced-dialogv2-customcontentdialogv2-s.md) | 自定义内容区弹出框，同时支持定义操作区按钮样式。适用于需要展示复杂或自定义内容的场景，如用户协议确认、表单输入等。 |
| [LoadingDialogV2](arkts-arkui-arkui-advanced-dialogv2-loadingdialogv2-s.md) | 进度加载类弹出框，操作正在执行时的提示信息。适用于耗时操作的场景，如数据加载、文件上传等，用于告知用户当前正在处理中。 |
| [PopoverDialogV2](arkts-arkui-arkui-advanced-dialogv2-popoverdialogv2-s.md) | 跟手弹出框，基于目标组件位置弹出，上述的TipsDialogV2、SelectDialogV2、ConfirmDialogV2、AlertDialogV2、LoadingDialogV2、CustomContentDialogV2都可作为弹出框内容。适用于需要跟随目标组件位置显示的场景，如工具提示、操作引导等。 |
| [SelectDialogV2](arkts-arkui-arkui-advanced-dialogv2-selectdialogv2-s.md) | 选择类弹出框，弹框中以列表或网格的形式提供可选的内容。适用于需要用户从多个选项中选择一个的场景，如选择语言、选择地区等。 |
| [TipsDialogV2](arkts-arkui-arkui-advanced-dialogv2-tipsdialogv2-s.md) | 提示弹出框，即为带图形确认弹出框，必要时可通过图形化方式展现确认弹出框。适用于需要图形化方式展示的重要提示场景，如应用卸载确认等。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AdvancedDialogV2ButtonOptions](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2buttonoptions-i.md) | 用于初始化AdvancedDialogV2Button对象。 |
| [PopoverDialogV2Options](arkts-arkui-arkui-advanced-dialogv2-popoverdialogv2options-i.md) | 跟手弹出框参数，用于设置弹出框内容、位置属性等。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AdvancedDialogV2ButtonAction](arkts-arkui-advanceddialogv2buttonaction-t.md) | 弹出框操作区按钮的点击事件类型。 |
| [AdvancedDialogV2OnCheckedChange](arkts-arkui-advanceddialogv2oncheckedchange-t.md) | 选择框选中状态改变事件。 |
| [PopoverDialogV2OnVisibleChange](arkts-arkui-popoverdialogv2onvisiblechange-t.md) | 跟手弹出框显示状态改变事件。 |

## 示例

### 示例1（上图下文弹出框）

上图下文弹出框，包含imageRes、content等内容。



```TypeScript
import { TipsDialogV2, AdvancedDialogV2Button, UIContext } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local checked: boolean = false;

  @Builder
  dialogBuilder(): void {
    // 构建提示弹出框，配置图片、内容、勾选状态和操作按钮
    TipsDialogV2({
      imageRes: $r('sys.media.ohos_ic_public_voice'),
      content: '想要卸载这个APP吗?',
      title: 'TipsDialogV2',
      checkTips: '不再提示',
      checked: this.checked,
      primaryButton: new AdvancedDialogV2Button({
        content: '取消',
        action: () => {
          console.info('Callback when the first button is clicked');
        },
      }),
      secondaryButton: new AdvancedDialogV2Button({
        content: '删除',
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
          Button("打开TipsDialogV2弹出框")
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

### 示例2（纯列表弹出框）

纯列表弹出框，包含selectedIndex、radioContent等内容。



```TypeScript
import { SelectDialogV2, AdvancedDialogV2Button ,UIContext  } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local radioIndex: number = 0;
  @Builder
  dialogBuilder(): void {
    // 构建选择弹出框，配置标题、选中项、底部按钮和选项列表
    SelectDialogV2({
      title: '文本标题',
      selectedIndex: this.radioIndex,
      confirm: new AdvancedDialogV2Button({
        content: '取消',
        action: () => {},
      }),
      radioContent: [
        {
          title: '文本文本文本文本文本',
          action: () => {
            this.radioIndex = 0
          }
        },
        {
          title: '文本文本文本文本',
          action: () => {
            this.radioIndex = 1
          }
        },
        {
          title: '文本文本文本文本',
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
          Button("纯列表弹出框")
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

### 示例3（文本与勾选弹出框）

文本与勾选弹出框，包含content、checkTips等内容。



```TypeScript
import { ConfirmDialogV2, AdvancedDialogV2Button, UIContext  } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local checked: boolean = false;

  @Builder
  dialogBuilder(): void {
    // 构建信息确认弹出框，配置标题、内容、勾选状态和操作按钮
    ConfirmDialogV2({
      title: '文本标题',
      content: '文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本',
      checked: this.checked,
      checkTips: '禁止后不再提示',
      primaryButton: new AdvancedDialogV2Button({
        content: '禁止',
        action: () => {
          console.info('Callback when the primary button is clicked');
        },
      }),
      secondaryButton: new AdvancedDialogV2Button({
        content: '允许',
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
          Button("打开ConfirmDialogV2弹出框")
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

### 示例4（纯文本弹出框）

纯文本弹出框，包含primaryTitle、secondaryTitle、content等内容。



```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, UIContext } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Builder
  dialogBuilder(): void {
    // 构建操作确认弹出框，配置标题、内容和操作按钮
    AlertDialogV2({
      primaryTitle: '弹框一级标题',
      secondaryTitle: '弹框二级标题',
      content: '文本文本文本文本文本',
      primaryButton: new AdvancedDialogV2Button({
        content: '取消',
        action: () => {
          console.info('Callback when the primary button is clicked');
        },
      }),
      secondaryButton: new AdvancedDialogV2Button({
        content: '确认',
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
          Button("打开AlertDialogV2弹出框")
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

### 示例5（进度加载类弹出框）

进度加载类弹出框，包含content等内容。



```TypeScript
import { LoadingDialogV2, UIContext  } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Builder
  dialogBuilder(): void {
    // 构建进度加载弹出框，配置提示内容
    LoadingDialogV2({
      content: '文本文本文本文本文本...',
    })
  }

  build() {
    Row() {
      Stack() {
        Column() {
          Button("打开LoadingDialogV2弹出框")
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

### 示例6（使用WithTheme自定义主题的弹出框）

使用WithTheme自定义主题的弹出框，通过WithTheme包装LoadingDialogV2实现主题风格定制。



```TypeScript
import { CustomColors, CustomTheme, LoadingDialogV2, UIContext } from '@kit.ArkUI';

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
        content: '文本文本文本文本文本...',
      })
    }
  }

  build() {
    Row() {
      Stack() {
        Column() {
          Button("打开LoadingDialogV2弹出框")
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

### 示例7（自定义内容弹出框）

支持自定义内容弹出框，包含contentBuilder、buttons等内容。



```TypeScript
import { CustomContentDialogV2, AdvancedDialogV2Button, UIContext } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Builder
  dialogBuilder(): void {
    // 构建自定义内容弹出框，配置标题、内容构建器和操作区按钮
    CustomContentDialogV2({
      primaryTitle: '标题',
      secondaryTitle: '辅助文本',
      contentBuilder: () => {
        this.buildContent();
      },
      buttons: [
        new AdvancedDialogV2Button({
          content: '按钮1', buttonStyle: ButtonStyleMode.TEXTUAL,
          action: () => {
            console.info('Callback when the button is clicked');
          }
        }),
        new AdvancedDialogV2Button({
          content: '按钮2', buttonStyle: ButtonStyleMode.TEXTUAL, role: ButtonRole.ERROR,
        })
      ],
    })
  }

  build() {
    Column() {
      Button("打开CustomContentDialogV2弹出框")
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
      Text('内容区')
    }
  }
}
```

### 示例8（跟手弹出框）

跟手弹出框（警告弹出框为例），包含visible、popover、targetBuilder等内容。

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
      content: '跟手弹出框',
      primaryButton: new AdvancedDialogV2Button({
        content: '取消',
        action: () => {
          this.isShow = false;
        },
      }),
      secondaryButton: new AdvancedDialogV2Button({
        content: '确认',
        action: () => {
          this.isShow = false;
        },
      }),
    });
  }

  @Builder buttonBuilder() {
    Button('跟手弹出框目标组件').onClick(() => {
      this.isShow = true;
    });
  }

  build() {
    Column() {
      // 构建跟手弹出框，配置显示状态、弹出选项和目标组件
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
