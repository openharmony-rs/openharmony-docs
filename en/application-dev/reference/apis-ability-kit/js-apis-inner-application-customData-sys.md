# CustomData (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=9b45198dbdb6f53f8bf0896d62425626f2442690 translatedAt=2026-09-03T11:55:59.052Z pushedAt=2026-09-05T10:47:30.784Z -->

When a modal page is pulled up, developers can pass custom data to the autofill service through the [reloadInModal](js-apis-inner-application-autoFillExtensionContext-sys.md#reloadinmodal13) API, and obtain the data through the [onFillRequest](js-apis-app-ability-autoFillExtensionAbility-sys.md#onfillrequest) API of the autofill service. This is applicable to scenarios where context information needs to be passed during the autofill process.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 13. Newly added APIs will be marked with a superscript to indicate their earliest API version. 
> The APIs of this module can be used only in the stage model. 
> The APIs provided by this module are system APIs.

## CustomData

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

| Name| Type                  | Read-Only| Optional| Description                                                |
| ---- | ---------------------- | ---- | ---- | ---------------------------------------------------- |
| data | Record<string, Object> | No  | No  | Custom data transferred for starting the modal page. The data is of the Record type.|
