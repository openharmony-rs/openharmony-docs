# showActionMenu

## 导入模块

```TypeScript
import { prompt } from '@kit.ArkUI';
```

## showActionMenu

```TypeScript
function showActionMenu(options: ActionMenuOptions, callback: AsyncCallback<ActionMenuSuccessResponse>): void
```

创建并显示操作菜单，菜单响应结果异步返回。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** showActionMenu

<!--Device-prompt-function showActionMenu(options: ActionMenuOptions, callback: AsyncCallback<ActionMenuSuccessResponse>): void--><!--Device-prompt-function showActionMenu(options: ActionMenuOptions, callback: AsyncCallback<ActionMenuSuccessResponse>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ActionMenuOptions](arkts-arkui-prompt-actionmenuoptions-i.md) | 是 | 操作菜单选项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ActionMenuSuccessResponse&gt; | 是 | 菜单响应结果回调。 |

**示例：**

```TypeScript
import prompt from '@ohos.prompt'
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
    },
  ]
}, (err, data) => {
  if (err) {
    console.info('showActionMenu err: ' + err);
    return;
  }
  console.info('showActionMenu success callback, click button: ' + data.index);
})

```


## showActionMenu

```TypeScript
function showActionMenu(options: ActionMenuOptions): Promise<ActionMenuSuccessResponse>
```

创建并显示操作菜单，菜单响应后同步返回结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** showActionMenu

<!--Device-prompt-function showActionMenu(options: ActionMenuOptions): Promise<ActionMenuSuccessResponse>--><!--Device-prompt-function showActionMenu(options: ActionMenuOptions): Promise<ActionMenuSuccessResponse>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ActionMenuOptions](arkts-arkui-prompt-actionmenuoptions-i.md) | 是 | 操作菜单选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ActionMenuSuccessResponse&gt; | 菜单响应结果。 |

**示例：**

```TypeScript
import prompt from '@ohos.prompt'
prompt.showActionMenu({
  title: 'showActionMenu Title Info',
  buttons: [
    {
      text: 'item1',
      color: '#666666'
    },
    {
      text: 'item2',
      color: '#000000'
    },
  ]
})
  .then(data => {
    console.info('showActionMenu success, click button: ' + data.index);
  })
  .catch((err:Error) => {
    console.info('showActionMenu error: ' + err);
  })

```

