# showDialog

## showDialog

```TypeScript
function showDialog(options: ShowDialogOptions, callback: AsyncCallback<ShowDialogSuccessResponse>): void
```

创建并显示对话框，对话框响应结果使用callback异步回调返回。

> **说明：**
>
> - 从API version 9开始支持，从API version 18开始废弃，建议使用[showDialog](arkts-apis-uicontext-promptaction.md#showdialog)替代。
showDialog需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的
[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，
然后通过该对象进行调用。且直接使用showDialog可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题。
>
> - 从API version 10开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的
[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取当前UI上下文关联的
[PromptAction](arkts-apis-uicontext-promptaction.md)对象。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** showDialog

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ShowDialogOptions | 是 | 页面显示对话框信息描述。 |
| callback | AsyncCallback&lt;ShowDialogSuccessResponse&gt; | 是 | 回调函数。弹出对话框成功，err为undefined，data为获取到的对话框响应结果，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |

**示例：**

```TypeScript
import { promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

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
      console.info('showDialog err: ' + err);
      return;
    }
    console.info('showDialog success callback, click button: ' + data.index);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  let code = (error as BusinessError).code;
  console.error(`showDialog args error code is ${code}, message is ${message}`);
};

```

```TypeScript
import { promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

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
      console.info('showDialog err: ' + err);
      return;
    }
    console.info('showDialog success callback, click button: ' + data.index);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  let code = (error as BusinessError).code;
  console.error(`showDialog args error code is ${code}, message is ${message}`);
};

```

当弹窗的showInSubWindow属性为true时，弹窗可显示在窗口外。

```TypeScript
import { promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  promptAction.showDialog({
    title: 'showDialog Title Info',
    message: 'Message Info',
    isModal: true,
    showInSubWindow: true,
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
      console.info('showDialog err: ' + err);
      return;
    }
    console.info('showDialog success callback, click button: ' + data.index);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  let code = (error as BusinessError).code;
  console.error(`showDialog args error code is ${code}, message is ${message}`);
};

```

当弹窗的showInSubWindow属性为true时，弹窗可显示在窗口外。

```TypeScript
import { promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  promptAction.showDialog({
    title: 'showDialog Title Info',
    message: 'Message Info',
    isModal: true,
    showInSubWindow: true,
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
      console.info('showDialog err: ' + err);
      return;
    }
    console.info('showDialog success callback, click button: ' + data.index);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  let code = (error as BusinessError).code;
  console.error(`showDialog args error code is ${code}, message is ${message}`);
};

```

从API version 19开始，该示例通过调用[ShowDialogOptions](#showdialogoptions)中的onDidAppear、onDidDisappear、onWillAppear和onWillDisappear属性展示了弹窗生命周期的相关接口的使用方法。

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct DialogExample {
  @State log: string = 'Log information:';
  build() {
    Column() {
      Button('showDialog')
        .onClick(() => {
          this.showCustomDialog();
        })
      Text(this.log).fontSize(30).margin({ top: 200 })
    }.width('100%').margin({ top: 5 })
  }

  showCustomDialog() {
    try {
      this.getUIContext().getPromptAction().showDialog({
        title: '操作确认',
        message: '您确定要执行此操作吗？',
        alignment: DialogAlignment.Bottom,
        buttons: [
          {
            text: '取消',
            color: '#999999'
          },
          {
            text: '确定',
            color: '#007DFF'
          }
        ],
        onDidAppear: () => {
          this.log += '# onDidAppear';
          console.info("showDialog,is onDidAppear!");
        },
        onDidDisappear: () => {
          this.log += '# onDidDisappear';
          console.info("showDialog,is onDidDisappear!");
        },
        onWillAppear: () => {
          this.log = 'Log information:#onWillAppear';
          console.info("showDialog,is onWillAppear!");
        },
        onWillDisappear: () => {
          this.log += '# onWillDisappear';
          console.info("showDialog,is onWillDisappear!");
        },
      })
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`捕获到异常: ${err.code}, ${err.message}`);
    }
  }
}

```

从API version 19开始，该示例通过调用[ShowDialogOptions](#showdialogoptions)中的onDidAppear、onDidDisappear、onWillAppear和onWillDisappear属性展示了弹窗生命周期的相关接口的使用方法。

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct DialogExample {
  @State log: string = 'Log information:';
  build() {
    Column() {
      Button('showDialog')
        .onClick(() => {
          this.showCustomDialog();
        })
      Text(this.log).fontSize(30).margin({ top: 200 })
    }.width('100%').margin({ top: 5 })
  }

  showCustomDialog() {
    try {
      this.getUIContext().getPromptAction().showDialog({
        title: '操作确认',
        message: '您确定要执行此操作吗？',
        alignment: DialogAlignment.Bottom,
        buttons: [
          {
            text: '取消',
            color: '#999999'
          },
          {
            text: '确定',
            color: '#007DFF'
          }
        ],
        onDidAppear: () => {
          this.log += '# onDidAppear';
          console.info("showDialog,is onDidAppear!");
        },
        onDidDisappear: () => {
          this.log += '# onDidDisappear';
          console.info("showDialog,is onDidDisappear!");
        },
        onWillAppear: () => {
          this.log = 'Log information:#onWillAppear';
          console.info("showDialog,is onWillAppear!");
        },
        onWillDisappear: () => {
          this.log += '# onWillDisappear';
          console.info("showDialog,is onWillDisappear!");
        },
      })
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`捕获到异常: ${err.code}, ${err.message}`);
    }
  }
}

```


## showDialog

```TypeScript
function showDialog(options: ShowDialogOptions): Promise<ShowDialogSuccessResponse>
```

创建并显示对话框，对话框通过Promise返回结果。

> **说明：**
>
> - 从API version 9开始支持，从API version 18开始废弃，建议使用[showDialog](arkts-apis-uicontext-promptaction.md#showdialog-1)替代。
showDialog需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的
[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，
然后通过该对象进行调用。且直接使用showDialog可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题。
>
> - 从API version 10开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的
[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取当前UI上下文关联的
[PromptAction](arkts-apis-uicontext-promptaction.md)对象。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** showDialog

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ShowDialogOptions | 是 | 对话框选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ShowDialogSuccessResponse&gt; | Promise对象，返回对话框的响应结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |

**示例：**

```TypeScript
import { promptAction } from '@kit.ArkUI';

promptAction.showDialog({
  title: 'Title Info',
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
  ],
})
  .then(data => {
    console.info('showDialog success, click button: ' + data.index);
  })
  .catch((err: Error) => {
    console.info('showDialog error: ' + err);
  })

```

```TypeScript
import { promptAction } from '@kit.ArkUI';

promptAction.showDialog({
  title: 'Title Info',
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
  ],
})
  .then(data => {
    console.info('showDialog success, click button: ' + data.index);
  })
  .catch((err: Error) => {
    console.info('showDialog error: ' + err);
  })

```

