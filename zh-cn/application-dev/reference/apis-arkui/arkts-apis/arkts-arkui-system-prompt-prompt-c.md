# Prompt

创建并显示文本提示框、对话框和操作菜单。 > **说明：** > > - 从API version 8 开始，该接口不再维护，推荐使用新接口[@ohos.promptAction (弹窗)](../../apis-na/arkts-apis/arkts-na-promptaction-n.md#promptAction)。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** -1

<!--Device-unnamed-export default class Prompt--><!--Device-unnamed-export default class Prompt-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showActionMenu

```TypeScript
static showActionMenu(options: ShowActionMenuOptions): void
```

显示操作菜单。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Prompt-static showActionMenu(options: ShowActionMenuOptions): void--><!--Device-Prompt-static showActionMenu(options: ShowActionMenuOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ShowActionMenuOptions](arkts-arkui-system-prompt-showactionmenuoptions-i.md) | 是 | 定义ShowActionMenu的选项。 |

## showDialog

```TypeScript
static showDialog(options: ShowDialogOptions): void
```

显示对话框。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Prompt-static showDialog(options: ShowDialogOptions): void--><!--Device-Prompt-static showDialog(options: ShowDialogOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ShowDialogOptions](arkts-arkui-system-prompt-showdialogoptions-i.md) | 是 | 定义显示对话框的选项。 |

## showToast

```TypeScript
static showToast(options: ShowToastOptions): void
```

显示文本弹窗。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Prompt-static showToast(options: ShowToastOptions): void--><!--Device-Prompt-static showToast(options: ShowToastOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ShowToastOptions](arkts-arkui-system-prompt-showtoastoptions-i.md) | 是 | 定义ShowToast的选项。 |

