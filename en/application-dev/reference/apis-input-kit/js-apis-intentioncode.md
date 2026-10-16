# @ohos.multimodalInput.intentionCode (Intention Code)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=6ff193a1258b05452b4935e34a160adf6db64d7a translatedAt=2026-09-11T01:11:57.062Z pushedAt=2026-09-11T02:42:28.842Z -->

The **intentionCode** module maps the original events of the keyboard to intention codes for normalized interaction. For instance, the spacebar on the keyboard is mapped to the INTENTION_SELECT event, representing a selection intention.

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
