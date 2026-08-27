# ExpandedMenuItemOptions

自定义菜单扩展项。

**起始版本：** 12

**废弃版本：** 20

**替代接口：** [editMenuOptions](arkts-arkweb-web-attribute.md#editmenuoptions)

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## action

```TypeScript
action: (selectedText: {plainText: string}) => void
```

回调函数，用于接收用户选择菜单扩展项后的操作。回调参数selectedText包含plainText字段，表示用户选中的文本内容。

**起始版本：** 12

**废弃版本：** 20

**替代接口：** [EditMenuOptions](../../apis-arkui/arkts-apis/arkts-arkui-editmenuoptions-i.md)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedText | {plainText: string} | 是 |  |

## content

```TypeScript
content: ResourceStr
```

显示内容。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 12

**废弃版本：** 20

**替代接口：** [EditMenuOptions](../../apis-arkui/arkts-apis/arkts-arkui-editmenuoptions-i.md)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## startIcon

```TypeScript
startIcon?: ResourceStr
```

显示图标。默认值为空，不显示图标。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 12

**废弃版本：** 20

**替代接口：** [EditMenuOptions](../../apis-arkui/arkts-apis/arkts-arkui-editmenuoptions-i.md)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
