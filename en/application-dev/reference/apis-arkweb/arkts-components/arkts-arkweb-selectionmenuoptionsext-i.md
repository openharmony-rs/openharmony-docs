# SelectionMenuOptionsExt

Represents the selection menu option extension.

**Since:** 13

**System capability:** SystemCapability.Web.Webview.Core

## menuType

```TypeScript
menuType?: MenuType
```

Type of the custom selection menu.

Default value: **MenuType.SELECTION_MENU**

Since API version 20, **MenuType.PREVIEW_MENU** supports hyperlink preview.

**Type:** [MenuType](../../apis-arkui/arkts-apis/arkts-arkui-menutype-e.md)

**Since:** 13

**System capability:** SystemCapability.Web.Webview.Core

## onAppear

```TypeScript
onAppear?: Callback<void>
```

Callback invoked when the custom selection menu appears.

**Type:** Callback&lt;void&gt;

**Since:** 13

**System capability:** SystemCapability.Web.Webview.Core

## onDisappear

```TypeScript
onDisappear?: Callback<void>
```

Callback invoked when the custom selection menu disappears.

**Type:** Callback&lt;void&gt;

**Since:** 13

**System capability:** SystemCapability.Web.Webview.Core

## onMenuHide

```TypeScript
onMenuHide?: Callback<void>
```

Callback invoked when the custom context menu on selection is hidden.

**Type:** Callback&lt;void&gt;

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## onMenuShow

```TypeScript
onMenuShow?: Callback<void>
```

Callback invoked when the custom context menu on selection is shown.

**Type:** Callback&lt;void&gt;

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## preview

```TypeScript
preview?: CustomBuilder
```

Preview content style of the custom selection menu. If this parameter is not set, there is no preview content.

**Type:** [CustomBuilder](../../apis-arkui/arkts-components/arkts-arkui-custombuilder-t.md)

**Since:** 13

**System capability:** SystemCapability.Web.Webview.Core

## previewMenuOptions

```TypeScript
previewMenuOptions?: PreviewMenuOptions
```

Custom preview menu options.

**Type:** [PreviewMenuOptions](arkts-arkweb-previewmenuoptions-i.md)

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core
