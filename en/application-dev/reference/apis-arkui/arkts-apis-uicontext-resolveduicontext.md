# Class (ResolvedUIContext)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e7bbac8df342a3329dc5f8c5db3d9883d3c9dda2 translatedAt=2026-08-05T03:09:55.963Z pushedAt=2026-08-05T07:17:27.958Z -->

ResolvedUIContext represents the UIContext instance obtained through [resolveUIContext](arkts-apis-uicontext-uicontext.md#resolveuicontext22) and its resolution strategy. It is applicable to scenarios where the UIContext source strategy needs to be obtained and identified.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The sample effect is subject to the actual running on a real device. The current DevEco Studio previewer does not support it.
> - ResolvedUIContext inherits from [UIContext](arkts-apis-uicontext-uicontext.md) and adds the **strategy** property to record the resolution strategy of the UIContext instance.
> - The APIs of this module can be used only in the stage model.

## Attribute

**Atomic service API**: This API can be used in atomic services since API version 22.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                                                     | Read-Only| Optional| Description                               |
| --------- | --------------------------------------------------------- | ---- | ---- | ---------------------------------- |
| strategy      | [ResolveStrategy](arkts-apis-uicontext-e.md#resolvestrategy22) | No   | No   | Resolution strategy of the [UIContext](arkts-apis-uicontext-uicontext.md), used to identify the resolution rule adopted when [resolveUIContext](arkts-apis-uicontext-uicontext.md#resolveuicontext22) returns this UIContext instance.             |