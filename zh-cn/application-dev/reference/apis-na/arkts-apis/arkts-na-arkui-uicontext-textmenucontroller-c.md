# TextMenuController

class TextMenuController

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class TextMenuController--><!--Device-unnamed-export declare class TextMenuController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disableMenuItems

```TypeScript
static disableMenuItems(items: Array<TextMenuItemId>): void
```

Disable menu action by action id.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextMenuController-static disableMenuItems(items: Array<TextMenuItemId>): void--><!--Device-TextMenuController-static disableMenuItems(items: Array<TextMenuItemId>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | Array&lt;TextMenuItemId&gt; | 是 | menu item id to disable @static |

## disableSystemServiceMenuItems

```TypeScript
static disableSystemServiceMenuItems(disable: boolean): void
```

Disable all system service menus, such as translation and ai writer. True means disable, false means enable.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextMenuController-static disableSystemServiceMenuItems(disable: boolean): void--><!--Device-TextMenuController-static disableSystemServiceMenuItems(disable: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disable | boolean | 是 | flag to disable service menu items @static |

## setMenuOptions

```TypeScript
setMenuOptions(options: TextMenuOptions): void
```

设置文本菜单选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextMenuController-setMenuOptions(options: TextMenuOptions): void--><!--Device-TextMenuController-setMenuOptions(options: TextMenuOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextMenuOptions](../../apis-arkui/arkts-apis/arkts-arkui-textcommon-textmenuoptions-i.md) | 是 | the options of the text menu. |

