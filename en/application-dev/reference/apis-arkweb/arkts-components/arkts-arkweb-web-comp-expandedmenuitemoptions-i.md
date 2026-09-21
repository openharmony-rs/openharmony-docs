# ExpandedMenuItemOptions

```TypeScript
declare interface ExpandedMenuItemOptions
```

Custom menu extension item.

> **NOTE:** 
> 
> This API is supported from API version 12 and deprecated from API version 20. You are advised to use
> [editMenuOptions](arkts-arkweb-web-comp-attribute.md#editmenuoptions) instead.

**Since:** 12

**Deprecated since:** 20

**Substitutes:** [editMenuOptions](arkts-arkweb-web-comp-attribute.md#editmenuoptions)

**System capability:** SystemCapability.Web.Webview.Core

## action

```TypeScript
action: (selectedText: {plainText: string}) => void
```

Callback invoked when the user selects a menu extension item. The callback parameter **selectedText** contains the **plainText** field, which indicates the text content selected by the user.

**Since:** 12

**Deprecated since:** 20

**Substitutes:** [EditMenuOptions](../../apis-arkui/arkts-apis/arkts-arkui-editmenuoptions-i.md)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectedText | {plainText: string} | Yes |  |

## content

```TypeScript
content: ResourceStr
```

Display content.

**Type:** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 12

**Deprecated since:** 20

**Substitutes:** [EditMenuOptions](../../apis-arkui/arkts-apis/arkts-arkui-editmenuoptions-i.md)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## startIcon

```TypeScript
startIcon?: ResourceStr
```

Display icon. The default value is empty, and no icon is displayed.

**Type:** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 12

**Deprecated since:** 20

**Substitutes:** [EditMenuOptions](../../apis-arkui/arkts-apis/arkts-arkui-editmenuoptions-i.md)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
