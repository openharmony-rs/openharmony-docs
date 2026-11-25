# @ohos.multimodalInput.intentionCode (Intention Code)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1a59b01eb09cbde916aad8893b634e85d3707880 translatedAt=2026-11-04T04:43:32.786Z pushedAt=2026-11-04T08:04:44.697Z nl=1 -->

The **intentionCode** module maps the original events of the keyboard to intention codes for normalized interaction. For example, if the mapped event of the space bar on the keyboard is **INTENTION_SELECT**, the intent is to select an item.

> **NOTE**
> 
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { IntentionCode } from '@kit.InputKit';
```

## IntentionCode

Enumerates intention codes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name                              | Value  |  Description       |
| -------------------------------- | ------ | --------------------------- |
| INTENTION_UNKNOWN                |  -1 | Unknown intent                 |
| INTENTION_UP                     |  1 | Up                    |
| INTENTION_DOWN                   |  2 | Down                    |
| INTENTION_LEFT                   |  3 | Left                    |
| INTENTION_RIGHT                  |  4 | Right                    |
| INTENTION_SELECT                 |  5 | Select                           |
| INTENTION_ESCAPE                 |  6 | Escape                           |
| INTENTION_BACK                   |  7 | Back                           |
| INTENTION_FORWARD                |  8 | Forward                           |
| INTENTION_MENU                   |  9 | Menu                           |
| INTENTION_PAGE_UP                |  11 | Page up                        |
| INTENTION_PAGE_DOWN              |  12 | Page down                        |
| INTENTION_ZOOM_OUT               |  13 | Zoom out                       |
| INTENTION_ZOOM_IN                |  14 | Zoom in                        |
