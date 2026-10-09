# ViewData

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e2e4d688beb0becfa2a64d71411845578aee3b47 translatedAt=2026-09-03T12:20:26.962Z pushedAt=2026-09-05T10:47:30.899Z -->

ViewData represents the view data information for auto-fill, including key data such as the application name, page URL, page node information, and page coordinates, width, and height. It applies to scenarios where page view information needs to be obtained and processed to implement the auto-fill feature.

**Since:** 26.0.0

## Modules to Import

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## ViewData

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name          | Type   | Read-only | Optional | Description       |
| ------------- | ------ | ---- | ---- | --------- |
| bundleName    | string | No   | No   | Bundle name of the application. |
| pageUrl       | string | No   | No   | URL of the page. |
| pageNodeInfos | Array\<[PageNodeInfo](js-apis-inner-application-pageNodeInfo.md)> | No   | No   | Information about the page nodes. |
| pageRect      | [AutoFillRect](js-apis-inner-application-autoFillRect.md)         | No   | No   | Position coordinates and width and height information of the page. On PC/2-in-1 devices, the password vault is displayed as a dialog box. To ensure that the dialog box follows the input box, set **left** and **top** to 0. |
