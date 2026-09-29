# SelectionMenuOptionsExt

```TypeScript
declare interface SelectionMenuOptionsExt
```

Represents the selection menu option extension.

**Since:** 13

<!--Device-unnamed-declare interface SelectionMenuOptionsExt--><!--Device-unnamed-declare interface SelectionMenuOptionsExt-End-->

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

<!--Device-SelectionMenuOptionsExt-menuType?: MenuType--><!--Device-SelectionMenuOptionsExt-menuType?: MenuType-End-->

**System capability:** SystemCapability.Web.Webview.Core

## onAppear

```TypeScript
onAppear?: Callback<void>
```

Callback invoked when the custom selection menu appears.

**Type:** Callback&lt;void&gt;

**Since:** 13

<!--Device-SelectionMenuOptionsExt-onAppear?: Callback<void>--><!--Device-SelectionMenuOptionsExt-onAppear?: Callback<void>-End-->

**System capability:** SystemCapability.Web.Webview.Core

## onDisappear

```TypeScript
onDisappear?: Callback<void>
```

Callback invoked when the custom selection menu disappears.

**Type:** Callback&lt;void&gt;

**Since:** 13

<!--Device-SelectionMenuOptionsExt-onDisappear?: Callback<void>--><!--Device-SelectionMenuOptionsExt-onDisappear?: Callback<void>-End-->

**System capability:** SystemCapability.Web.Webview.Core

## onMenuHide

```TypeScript
onMenuHide?: Callback<void>
```

Callback invoked when the custom context menu on selection is hidden.

**Type:** Callback&lt;void&gt;

**Since:** 21

<!--Device-SelectionMenuOptionsExt-onMenuHide?: Callback<void>--><!--Device-SelectionMenuOptionsExt-onMenuHide?: Callback<void>-End-->

**System capability:** SystemCapability.Web.Webview.Core

## onMenuShow

```TypeScript
onMenuShow?: Callback<void>
```

Callback invoked when the custom context menu on selection is shown.

**Type:** Callback&lt;void&gt;

**Since:** 21

<!--Device-SelectionMenuOptionsExt-onMenuShow?: Callback<void>--><!--Device-SelectionMenuOptionsExt-onMenuShow?: Callback<void>-End-->

**System capability:** SystemCapability.Web.Webview.Core

## preview

```TypeScript
preview?: CustomBuilder
```

Preview content style of the custom selection menu. If this parameter is not set, there is no preview content.

**Type:** [CustomBuilder](../../apis-arkui/arkts-components/arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 13

<!--Device-SelectionMenuOptionsExt-preview?: CustomBuilder--><!--Device-SelectionMenuOptionsExt-preview?: CustomBuilder-End-->

**System capability:** SystemCapability.Web.Webview.Core

## previewMenuOptions

```TypeScript
previewMenuOptions?: PreviewMenuOptions
```

Custom preview menu options.

**Type:** [PreviewMenuOptions](arkts-arkweb-web-comp-previewmenuoptions-i.md)

**Since:** 20

<!--Device-SelectionMenuOptionsExt-previewMenuOptions?: PreviewMenuOptions--><!--Device-SelectionMenuOptionsExt-previewMenuOptions?: PreviewMenuOptions-End-->

**System capability:** SystemCapability.Web.Webview.Core
