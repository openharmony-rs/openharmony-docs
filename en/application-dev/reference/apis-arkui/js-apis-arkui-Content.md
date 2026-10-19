# Content
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=4da4cab88c5c9e987b28cefe3239aadd52f84dba translatedAt=2026-10-15T10:56:51.649Z pushedAt=2026-10-19T01:58:23.741Z -->

Defines the base class for **ComponentContent** and **NodeContent**, which provides unified content management capabilities for ArkUI content hosting structures and is suitable for scenarios where custom content nodes need to be dynamically created and mounted.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { Content } from '@kit.ArkUI';
```

## Content

A base class for ArkUI content hosting structures. It provides unified content management capabilities for [ComponentContent](./js-apis-arkui-ComponentContent.md) and [NodeContent](./js-apis-arkui-NodeContent.md), which is suitable for scenarios where custom content nodes need to be dynamically created and mounted.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full