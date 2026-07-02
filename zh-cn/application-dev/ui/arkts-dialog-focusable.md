# 弹出框焦点策略
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
ArkUI的弹出框焦点策略可以设定是否中断用户当前操作，并聚焦到新弹出的弹出框。若设定弹出框不获取焦点，则新弹出时不会中断用户当前操作，例如，当用户正在文本框中输入内容时，新弹出的弹出框不会关闭软键盘，焦点仍保留在文本框中。

从API version 19开始，可以通过设置[focusable](../reference/apis-arkui/js-apis-promptAction.md#basedialogoptions11)参数来管理弹出框是否获取焦点。

## 使用约束

[openCustomDialog](arkts-uicontext-custom-dialog.md)和[CustomDialog](arkts-common-components-custom-dialog.md)支持通过focusable参数来管理弹出框是否获取焦点。

> **说明：**
> 
> 只有弹出覆盖在当前窗口之上的弹出框才可以获取焦点。

## 创建不获取焦点的弹出框

> **说明：**
> 
> 详细变量定义请参考[完整示例](#完整示例)。

1. 初始化一个弹出框内容区域，内含一个Text组件。

    <!-- @[dialog_focus_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/customdialog/dialogboxfocuspolicy/DialogFocusStrategy.ets) -->
    
    ``` TypeScript
    @State dialogIdIndex: number = 0;
    // 请在resources\base\element\string.json文件中配置name为'dialog_message'，value为非空字符串的资源
    private message: string =
      this.getUIContext().getHostContext()?.resourceManager.getStringByNameSync('dialog_message') as string;
    // 存储所有弹窗延时关闭定时器ID数组，页面销毁统一清除
    private timerIdList: number[] = [];
    // 标记页面是否已销毁，销毁后不再执行弹窗关闭逻辑
    private isPageDestroy: boolean = false;
    
    @Builder
    customDialogComponent() {
      Column({ space: 5 }) {
        Text(this.message + this.dialogIdIndex)
          .fontSize(30)
      }
      .height(200)
      .padding(5)
      .justifyContent(FlexAlign.SpaceBetween)
    }
    ```




2. 创建一个TextInput组件，在onChange事件函数中通过调用[UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)中的[getPromptAction](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取[PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md)对象，再通过该对象调用[openCustomDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12)接口，并设置[focusable](../reference/apis-arkui/js-apis-promptAction.md#basedialogoptions11)参数为false，以创建弹出框。

    <!-- @[dialog_focus_text_input](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/customdialog/dialogboxfocuspolicy/DialogFocusStrategy.ets) -->
    
    ``` TypeScript
    TextInput()
      .onChange(() => {
        this.dialogIdIndex++;
        this.getUIContext().getPromptAction().openCustomDialog({
          builder: () => {
            this.customDialogComponent();
          },
          focusable: false
        }).then((dialogId: number) => {
          // 创建延时关闭定时器
          const timerId = setTimeout(() => {
            // 页面已销毁则直接跳过关闭逻辑
            if (this.isPageDestroy) {
              return;
            }
            this.getUIContext().getPromptAction().closeCustomDialog(dialogId);
            // 关闭弹窗后移除已完成定时器记录
            const idx = this.timerIdList.findIndex(item => item === timerId);
            if (idx > -1) {
              this.timerIdList.splice(idx, 1);
            }
          }, 3000);
          // 保存定时器ID，页面销毁时统一清理
          this.timerIdList.push(timerId);
        }).catch((err: BusinessError) => {
          console.error(`Failed to open dialog. Error code: ${err.code}`);
        });
      })
    ```

## 完整示例

当用户正在文本框中输入内容时，新弹出的弹出框不会关闭软键盘，焦点仍保留在文本框中。
<!-- @[dialog_focus](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/customdialog/dialogboxfocuspolicy/DialogFocusStrategy.ets) -->

``` TypeScript
@Entry
@Component
export struct Index {
  @State dialogIdIndex: number = 0;
  // 请在resources\base\element\string.json文件中配置name为'dialog_message'，value为非空字符串的资源
  private message: string =
    this.getUIContext().getHostContext()?.resourceManager.getStringByNameSync('dialog_message') as string;
  // 存储所有弹窗延时关闭定时器ID数组，页面销毁统一清除
  private timerIdList: number[] = [];
  // 标记页面是否已销毁，销毁后不再执行弹窗关闭逻辑
  private isPageDestroy: boolean = false;

  @Builder
  customDialogComponent() {
    Column({ space: 5 }) {
      Text(this.message + this.dialogIdIndex)
        .fontSize(30)
    }
    .height(200)
    .padding(5)
    .justifyContent(FlexAlign.SpaceBetween)
  }


  /**
   * 页面销毁生命周期：清除所有定时器，防止延时关闭弹窗触发异常、内存泄漏
   */
  aboutToDisappear(): void {
    this.isPageDestroy = true;
    // 遍历清除全部未执行的定时器
    this.timerIdList.forEach(timerId => {
      clearTimeout(timerId);
    });
    this.timerIdList = [];
  }

  build() {
    NavDestination() {
      Column({ space: 5 }) {
        TextInput()
          .onChange(() => {
            this.dialogIdIndex++;
            this.getUIContext().getPromptAction().openCustomDialog({
              builder: () => {
                this.customDialogComponent();
              },
              focusable: false
            }).then((dialogId: number) => {
              // 创建延时关闭定时器
              const timerId = setTimeout(() => {
                // 页面已销毁则直接跳过关闭逻辑
                if (this.isPageDestroy) {
                  return;
                }
                this.getUIContext().getPromptAction().closeCustomDialog(dialogId);
                // 关闭弹窗后移除已完成定时器记录
                const idx = this.timerIdList.findIndex(item => item === timerId);
                if (idx > -1) {
                  this.timerIdList.splice(idx, 1);
                }
              }, 3000);
              // 保存定时器ID，页面销毁时统一清理
              this.timerIdList.push(timerId);
            }).catch((err: BusinessError) => {
              console.error(`Failed to open dialog. Error code: ${err.code}`);
            });
          })
      }.width('100%')
    }
  }
}
```

![dialog-focusable-demo1](figures/dialog-focusable-demo1.gif)
