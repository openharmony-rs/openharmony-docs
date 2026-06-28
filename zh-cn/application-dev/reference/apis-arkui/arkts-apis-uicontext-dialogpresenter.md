# Class (DialogPresenter)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

提供统一的Dialog API，可创建并显示固定样式对话框、自定义样式对话框，并支持更新与关闭对话框。

> **说明：**
>
> - 本Class首批接口从API version 26.1.0开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 以下API需先使用UIContext中的[getDialogPresenter()](arkts-apis-uicontext-uicontext.md#getdialogpresenter)方法获取到DialogPresenter对象，再通过该对象调用对应方法。

## present

present(options?: dialog.DialogStyleOptions): Promise&lt;DialogResult&gt;

提供一个固定样式的对话框，使用Promise异步回调返回对话结果。

固定样式对话框的标题、副标题、消息、按钮及工作表项等均通过[dialog.DialogStyleOptions](js-apis-dialog.md#dialogstyleoptions)配置，弹窗本身的样式（背景、对齐、蒙层、避让等）继承自[dialog.DialogBaseOptions](js-apis-dialog.md#dialogbaseoptions)。

**原子化服务API：** 从API version 26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明           |
| ------- | ------------------------------------------------------------ | ---- | -------------- |
| options | [dialog.DialogStyleOptions](js-apis-dialog.md#dialogstyleoptions) | 否   | 固定样式对话框选项。 |

**返回值：**

| 类型                                             | 说明                                   |
| ------------------------------------------------ | -------------------------------------- |
| Promise&lt;[DialogResult](js-apis-dialog.md#dialogresult)&gt; | Promise对象，返回对话结果，包含对话框ID。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[弹窗错误码](errorcode-promptAction.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 103306   | The dialog cannot be opened due to node mount failure.       |
| 103308   | The dialog cannot be opened due to subwindow create failure. |

**示例：**

该示例通过调用present接口，展示了弹出固定样式对话框并通过Promise获取对话结果的功能。

```ts
import { DialogPresenter, DialogResult } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private ctx: UIContext = this.getUIContext();
  private dialogPresenter: DialogPresenter = this.ctx.getDialogPresenter();

  build() {
    Column() {
      Button('present固定样式弹窗')
        .onClick(() => {
          this.dialogPresenter.present({
            title: '温馨提示',
            message: { content: '这是一个固定样式弹窗' },
            buttons: [
              {
                value: '取消',
                action: () => {
                  console.info('点击了取消按钮');
                }
              },
              {
                value: '确定',
                action: () => {
                  console.info('点击了确定按钮');
                }
              }
            ]
          })
            .then((result: DialogResult) => {
              console.info('present success, dialogId: ' + result.dialogId);
            })
            .catch((error: BusinessError) => {
              console.error(`present error code is ${error.code}, message is ${error.message}`);
            })
        })
    }.width('100%').height('100%').justifyContent(FlexAlign.Center)
  }
}
```

## present

present(content: CustomBuilder \| CustomBuilderWithId \| ComponentContent&lt;Object&gt;, options?: dialog.DialogCustomOptions): Promise&lt;DialogResult&gt;

提供一个自定义样式的对话框，其中包含所提供的内容，使用Promise异步回调返回对话结果。

content参数通过联合类型接受CustomBuilder或ComponentContent：

- [CustomBuilder](arkui-ts/ts-types.md#custombuilder8)：自定义对话框内容的生成器函数。
- [CustomBuilderWithId](arkts-apis-uicontext-t.md#custombuilderwithid18)：支持在自定义弹窗内容中持有弹窗ID的生成器函数。
- [ComponentContent](./js-apis-arkui-ComponentContent.md)：支持状态驱动更新的组件内容。

自定义对话框的背景、对齐、蒙层、避让等样式通过[dialog.DialogCustomOptions](js-apis-dialog.md#dialogcustomoptions)配置（继承自[dialog.DialogBaseOptions](js-apis-dialog.md#dialogbaseoptions)）。

> **说明：**
>
> [dialog.DialogBaseOptions](js-apis-dialog.md#dialogbaseoptions)中的isModal与showInSubWindow不能同时设置为true，否则只生效showInSubWindow = true，此时为非模态弹出框且不会显示蒙层，并在子窗口中显示。

**原子化服务API：** 从API version 26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明               |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| content | [CustomBuilder](arkui-ts/ts-types.md#custombuilder8) \| [CustomBuilderWithId](arkts-apis-uicontext-t.md#custombuilderwithid18) \| [ComponentContent](./js-apis-arkui-ComponentContent.md)&lt;Object&gt; | 是   | 自定义对话框内容。 |
| options | [dialog.DialogCustomOptions](js-apis-dialog.md#dialogcustomoptions) | 否   | 自定义对话框选项。 |

**返回值：**

| 类型                                             | 说明                                   |
| ------------------------------------------------ | -------------------------------------- |
| Promise&lt;[DialogResult](js-apis-dialog.md#dialogresult)&gt; | Promise对象，返回对话结果，包含对话框ID。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[弹窗错误码](errorcode-promptAction.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 103301   | Dialog content error. The ComponentContent is incorrect.     |
| 103302   | Dialog content already exist. The ComponentContent has already been opened. |
| 103306   | The dialog cannot be opened due to node mount failure.       |
| 103308   | The dialog cannot be opened due to subwindow create failure. |

**示例：**

该示例通过调用present、update和dismiss接口，展示了弹出、更新以及关闭自定义对话框的功能。

```ts
import { ComponentContent, DialogPresenter, DialogResult, DialogBaseAlignment } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = '';
  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column({ space: 20 }) {
    Text(params.text)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
    Button('update更新弹窗')
      .onClick(() => {
        dialogPresenter?.update(contentNode, { alignment: DialogBaseAlignment.BOTTOM })
          .then(() => {
            console.info('update success');
          })
          .catch((error: BusinessError) => {
            console.error(`update error code is ${error.code}, message is ${error.message}`);
          })
      })
    Button('dismiss关闭弹窗')
      .onClick(() => {
        dialogPresenter?.dismiss(dialogId)
          .then(() => {
            console.info('dismiss success');
          })
          .catch((error: BusinessError) => {
            console.error(`dismiss error code is ${error.code}, message is ${error.message}`);
          })
      })
  }.backgroundColor('#FFF0F0F0')
}

let dialogPresenter: DialogPresenter | null = null;
let contentNode: ComponentContent<Object> | null = null;
let dialogId: number = 0;

@Entry
@Component
struct Index {
  @State message: string = '自定义弹窗';

  aboutToAppear(): void {
    dialogPresenter = this.getUIContext().getDialogPresenter();
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params(this.message));
  }

  build() {
    Column({ space: 10 }) {
      Button('present自定义弹窗')
        .onClick(() => {
          dialogPresenter?.present(contentNode, { isModal: true })
            .then((result: DialogResult) => {
              dialogId = result.dialogId;
              console.info('present success, dialogId: ' + result.dialogId);
            })
            .catch((error: BusinessError) => {
              console.error(`present error code is ${error.code}, message is ${error.message}`);
            })
        })
    }.width('100%').height('100%').justifyContent(FlexAlign.Center)
  }
}
```

## update

update(content: ComponentContent&lt;Object&gt;, options?: dialog.DialogBaseOptions): Promise&lt;void&gt;

更新已呈现的自定义对话框，使用Promise异步回调。

content用于标识需要更新的对话框，options为需要更新的选项（背景、对齐、蒙层、避让等，继承自[dialog.DialogBaseOptions](js-apis-dialog.md#dialogbaseoptions)）。

**原子化服务API：** 从API version 26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明                          |
| ------- | ------------------------------------------------------------ | ---- | ----------------------------- |
| content | [ComponentContent](./js-apis-arkui-ComponentContent.md)&lt;Object&gt; | 是   | 用于标识对话框的组件内容。     |
| options | [dialog.DialogBaseOptions](js-apis-dialog.md#dialogbaseoptions) | 否   | 要更新的对话框选项。           |

**返回值：**

| 类型                | 说明                |
| ------------------- | ------------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[弹窗错误码](errorcode-promptAction.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 103301   | Dialog content error. The ComponentContent is incorrect.     |
| 103303   | Dialog content not found. The ComponentContent cannot be found. |

**示例：**

请参考[present](#present)的示例。

## dismiss

dismiss(target: number \| ComponentContent&lt;Object&gt;): Promise&lt;void&gt;

关闭对话框，使用Promise异步回调。

接受对话框ID（由[present](#present)返回的[DialogResult](js-apis-dialog.md#dialogresult)中的dialogId）或[ComponentContent](./js-apis-arkui-ComponentContent.md)引用作为target，关闭对应的对话框。

**原子化服务API：** 从API version 26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明                                   |
| ------ | ------------------------------------------------------------ | ---- | -------------------------------------- |
| target | number \| [ComponentContent](./js-apis-arkui-ComponentContent.md)&lt;Object&gt; | 是   | 要关闭的对话框ID或组件内容。            |

**返回值：**

| 类型                | 说明                |
| ------------------- | ------------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[弹窗错误码](errorcode-promptAction.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 103301   | Dialog content error. The ComponentContent is incorrect.     |
| 103303   | Dialog content not found. The ComponentContent cannot be found. |

**示例：**

该示例通过调用dismiss接口，展示了分别通过对话框ID和组件内容关闭对话框的功能。对话框的弹出可参考[present](#present)的示例。

```ts
import { DialogPresenter, DialogResult } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';


@Entry
@Component
struct Index {
  @State message: string = '自定义弹窗';
  dialogPresenter: DialogPresenter | null = this.getUIContext().getDialogPresenter();
  dialogId: number = 0;

  @Builder
  customDialogComponent() {
    Column() {
      Text('打开了一个弹窗').fontSize(20)
      Row({ space: 10 }) {
        Button('关闭弹窗').onClick(() => {
          try {
            this.getUIContext().getDialogPresenter().dismiss(this.dialogId)
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`dismiss error code is ${code}, message is ${message}`);
          }
        })
      }
    }.height(150).padding(20).justifyContent(FlexAlign.SpaceBetween)
  }

  build() {
    Column({ space: 10 }) {
      Button('present自定义弹窗')
        .onClick(() => {
          this.dialogPresenter?.present(() => {this.customDialogComponent()},
            {
              isModal: true,
              backgroundColor: Color.Pink,
              backgroundBlurStyle: BlurStyle.NONE
            })
            .then((result: DialogResult) => {
              this.dialogId = result.dialogId;
              console.info('present success, dialogId: ' + result.dialogId);
            })
            .catch((error: BusinessError) => {
              console.error(`present error code is ${error.code}, message is ${error.message}`);
            })
        })
    }.width('100%').height('100%').justifyContent(FlexAlign.Center)
  }
}
```
