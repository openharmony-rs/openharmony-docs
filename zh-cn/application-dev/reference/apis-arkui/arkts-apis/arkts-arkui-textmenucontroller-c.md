# TextMenuController

class TextMenuController

**起始版本：** 16

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disableMenuItems

```TypeScript
static disableMenuItems(items: Array<TextMenuItemId>): void
```

按照id禁用菜单项

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | Array&lt;TextMenuItemId&gt; | 是 |  |

## disableSystemServiceMenuItems

```TypeScript
static disableSystemServiceMenuItems(disable: boolean): void
```

禁用所有的系统菜单

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disable | boolean | 是 |  |

## setMenuOptions

```TypeScript
setMenuOptions(options: TextMenuOptions): void
```

Set text menu options.

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本16开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | TextMenuOptions | 是 | the options of the text menu. |

