# Content

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=d89c4be0c26be57dcac6e3a0bb8b7f968642aa19 translatedAt=2026-07-29T09:31:36.748Z pushedAt=2026-07-30T08:25:37.385Z -->

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