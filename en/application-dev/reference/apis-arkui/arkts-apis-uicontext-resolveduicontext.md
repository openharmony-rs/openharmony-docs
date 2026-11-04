# Class (ResolvedUIContext)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=1f9dad1f3e6c22cc389887f8092a3a1fbc7dc9a2 translatedAt=2026-10-29T09:11:40.520Z pushedAt=2026-10-30T06:48:56.045Z nl=1 -->

**ResolvedUIContext** represents the UIContext instance obtained through [resolveUIContext](arkts-apis-uicontext-uicontext.md#resolveuicontext22) and its resolution policy. It is applicable to scenarios where the UIContext source policy needs to be obtained and identified.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The sample effect is subject to the actual running on a real device. The current DevEco Studio previewer does not support it.
> - **ResolvedUIContext** inherits from [UIContext](arkts-apis-uicontext-uicontext.md) and adds the **strategy** attribute to record the resolution policy of the UIContext instance.
> - The APIs of this module can be used only in the stage model.

## Attribute

**Atomic service API**: This API can be used in atomic services since API version 22.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                                                     | Read-Only| Optional| Description                               |
| --------- | --------------------------------------------------------- | ---- | ---- | ---------------------------------- |
| strategy      | [ResolveStrategy](arkts-apis-uicontext-e.md#resolvestrategy22) | No   | No   | Resolution policy of the [UIContext](arkts-apis-uicontext-uicontext.md), used to identify the resolution rule adopted when [resolveUIContext](arkts-apis-uicontext-uicontext.md#resolveuicontext22) returns this UIContext instance.             |
