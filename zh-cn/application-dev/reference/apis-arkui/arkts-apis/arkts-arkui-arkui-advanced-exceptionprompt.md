# @ohos.arkui.advanced.ExceptionPrompt

异常提示，适用于有异常需要提示异常内容的情况。

> **说明：**
 >
 > - 该组件仅可在Stage模型下使用。
 >
 > - 如果ExceptionPrompt设置[通用属性](../arkts-components/arkts-arkui-common-comp.md#common)和[通用事件](../arkts-components/arkts-arkui-common-comp.md#common)，
 > 编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到ExceptionPrompt本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议
 > ExceptionPrompt设置通用属性和通用事件。

## 子组件

无

## ExceptionPromptAttribute

不支持通用事件。

## 导入模块

```TypeScript
import { MarginType, PromptOptions, ExceptionPrompt } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ExceptionPrompt](arkts-arkui-arkui-advanced-exceptionprompt-exceptionprompt-s.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PromptOptions](arkts-arkui-arkui-advanced-exceptionprompt-promptoptions-i.md) | PromptOptions定义options的类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [MarginType](arkts-arkui-arkui-advanced-exceptionprompt-margintype-e.md) | MarginType定义marginType的类型。 |

## 示例

### 示例1（设置异常提示）

该示例展示了如何设置异常提示的异常图标、异常提示的文字、边距样式和右侧图标按钮的文字内容。



```TypeScript
import { ExceptionPrompt, PromptOptions, MarginType } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State options: PromptOptions = {
    icon: $r('sys.media.ohos_ic_public_fail'),
    tip: '异常提示',
    marginType: MarginType.DEFAULT_MARGIN,
    actionText: '设置网络',
    marginTop: 80,
    isShown: true,
  }

  build() {
    Column() {
      ExceptionPrompt({
        options: this.options,
        onTipClick: () => {
          // 单击左侧的文本切换到连接状态
        },
        onActionTextClick: () => {
          // 点击“设置网络”按钮，打开设置网络弹窗界面
        },
      })
    }
  }
}
```

### 示例2（设置弹窗类型的异常提示）

该示例使用自定义弹窗设置弹窗类型的异常提示。



```TypeScript
import { ExceptionPrompt, PromptOptions, MarginType } from '@kit.ArkUI';

@CustomDialog
struct CustomDialogExample {
  @Link textValue: string;
  @Link inputValue: string;
  @State options: PromptOptions = {
    icon: $r('sys.media.ohos_ic_public_fail'),
    tip: '异常提示！',
    marginType: MarginType.DEFAULT_MARGIN,
    actionText: '设置',
    marginTop: 5,
    isShown: true,
  };
  cancel: () => void = () => {
  };
  confirm: () => void = () => {
  };
  controller?: CustomDialogController;

  // 若尝试在CustomDialog中传入多个其他的Controller，以实现在CustomDialog中打开另一个或另一些CustomDialog，
  // 那么此处需要将指向自己的controller放在最后
  build() {
    Column() {
      ExceptionPrompt({
        options: this.options,
      })
      TextInput({ placeholder: '', text: this.textValue }).margin({ top: 70 }).height(60).width('90%')
        .onChange((value: string) => {
          this.textValue = value;
        })
      Text('Whether to change a text?').fontSize(16).margin({ bottom: 10 })
      Flex({ justifyContent: FlexAlign.SpaceAround }) {
        Button('cancel')
          .onClick(() => {
            this.controller?.close();
            this.cancel();
          }).backgroundColor(0xffffff).fontColor(Color.Black)
        Button('confirm')
          .onClick(() => {
            this.inputValue = this.textValue;
            this.controller?.close();
            this.confirm();
          }).backgroundColor(0xffffff).fontColor(Color.Red)
      }.margin({ bottom: 10 })
    }
  }
}

@Entry
@Component
struct Index1 {
  @State options: PromptOptions = {
    icon: $r('sys.media.ohos_ic_public_fail'),
    tip: '',
    marginType: MarginType.DEFAULT_MARGIN,
    actionText: '',
    marginTop: 80,
    isShown: true,
  }
  @State textValue: string = '';
  @State inputValue: string = 'click me';
  dialogController: CustomDialogController | undefined = new CustomDialogController({
    builder: CustomDialogExample({
      cancel: this.onCancel,
      confirm: this.onAccept,
      textValue: $textValue,
      inputValue: $inputValue,
    }),
    cancel: this.existApp,
    autoCancel: true,
    alignment: DialogAlignment.Bottom,
    offset: { dx: 0, dy: -20 },
    gridCount: 4,
    customStyle: false,
  })

  aboutToDisappear() {
    this.dialogController = undefined; // 将dialogController置空
  }

  onCancel() {
    console.info('Callback when the first button is clicked');
  }

  onAccept() {
    console.info('Callback when the second button is clicked');
  }

  existApp() {
    console.info('Click the callback in the blank area');
  }

  build() {
    Column() {
      Button('Click Me')
        .width('30%')
        .margin({ top: 420 })
        .zIndex(999)
        .onClick(() => {
          if (this.dialogController != undefined) {
            this.dialogController.open();
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例3（设置Symbol类型图标）

从API version 18开始，该示例通过设置PromptOptions的属性symbolStyle，展示了自定义Symbol类型图标。

```TypeScript
import { ExceptionPrompt, MarginType, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column() {
      ExceptionPrompt({
        options: {
          icon: $r('sys.symbol.house'),
          tip: '异常提示',
          marginType: MarginType.DEFAULT_MARGIN,
          actionText: '设置网络',
          marginTop: 80,
          isShown: true,
        },
      })
      ExceptionPrompt({
        options: {
          icon: $r('sys.symbol.house'),
          symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Red]),
          tip: '异常提示',
          marginType: MarginType.DEFAULT_MARGIN,
          actionText: '设置网络',
          marginTop: 200,
          isShown: true,
        },
      })
    }
  }
}
```
