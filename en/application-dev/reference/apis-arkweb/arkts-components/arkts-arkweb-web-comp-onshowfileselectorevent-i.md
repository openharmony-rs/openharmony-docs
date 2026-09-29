# OnShowFileSelectorEvent

```TypeScript
declare interface OnShowFileSelectorEvent
```

Defines the callback information for the file selector result, including the result and parameter details.

**Since:** 12

<!--Device-unnamed-declare interface OnShowFileSelectorEvent--><!--Device-unnamed-declare interface OnShowFileSelectorEvent-End-->

**System capability:** SystemCapability.Web.Webview.Core

## fileSelector

```TypeScript
fileSelector: FileSelectorParam
```

Information about the file selector.

**Type:** [FileSelectorParam](arkts-arkweb-web-comp-fileselectorparam-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnShowFileSelectorEvent-fileSelector: FileSelectorParam--><!--Device-OnShowFileSelectorEvent-fileSelector: FileSelectorParam-End-->

**System capability:** SystemCapability.Web.Webview.Core

## result

```TypeScript
result: FileSelectorResult
```

File selection result to be sent to the **Web** component.

**Type:** [FileSelectorResult](arkts-arkweb-web-comp-fileselectorresult-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnShowFileSelectorEvent-result: FileSelectorResult--><!--Device-OnShowFileSelectorEvent-result: FileSelectorResult-End-->

**System capability:** SystemCapability.Web.Webview.Core
