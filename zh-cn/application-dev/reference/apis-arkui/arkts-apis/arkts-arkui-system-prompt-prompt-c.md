# Prompt

创建并显示文本提示框、对话框和操作菜单。

> **说明：**
> 
> - 从API version 8 开始，该接口不再维护，推荐使用新接口[@ohos.promptAction (弹窗)](arkts-arkui-promptaction-n.md)。

**起始版本：** 3

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Prompt, Button, ShowActionMenuOptions, ShowDialogOptions, ShowDialogSuccessResponse, ShowToastOptions } from '@kit.ArkUI';
```

## showActionMenu

```TypeScript
static showActionMenu(options: ShowActionMenuOptions): void
```

显示操作菜单。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ShowActionMenuOptions](arkts-arkui-system-prompt-showactionmenuoptions-i.md) | 是 | 定义ShowActionMenu的选项。 |

**示例**

```TypeScript
import prompt from '@system.prompt';
class C{
  showActionMenu() {
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
      ],
      success: (tapIndex)=> {
        console.info('dialog success callback，click button : ' + tapIndex);
      },
      fail: (errMsg)=> {
        console.info('dialog fail callback' + errMsg);
      },
    });
  }
}
export default new C()
```

## showDialog

```TypeScript
static showDialog(options: ShowDialogOptions): void
```

显示对话框。

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ShowDialogOptions](arkts-arkui-system-prompt-showdialogoptions-i.md) | 是 | 定义显示对话框的选项。 |

**示例**

```TypeScript
import prompt from '@system.prompt';
class B{
  showDialog() {
    prompt.showDialog({
      title: 'Title Info',
      message: 'Message Info',
      buttons: [
        {
          text: 'button',
          color: '#666666'
        },
      ],
      success: (data)=> {
        console.info('dialog success callback，click button : ' + data.index);
      },
      cancel: ()=> {
        console.info('dialog cancel callback');
      },
    });
  }
}
export default new B()
```

## showToast

```TypeScript
static showToast(options: ShowToastOptions): void
```

显示文本弹窗。

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ShowToastOptions](arkts-arkui-system-prompt-showtoastoptions-i.md) | 是 | 定义ShowToast的选项。 |

**示例**

```TypeScript
import prompt from '@system.prompt';
class A{
  showToast() {
    prompt.showToast({
      message: 'Message Info',
      duration: 2000
    });
  }
}
export default new A()
```
