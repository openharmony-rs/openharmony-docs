# API Call Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW; @mayaolll; @liyi0309-->
<!--Designer: @CCFFWW; @liyi0309; @jiangdayuan-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 100001 Internal Error

**Error Message**

When used for [@ohos.animator](js-apis-animator.md): "The specified page is not found or the object property list is not obtained."

When used for [@ohos.promptAction](js-apis-promptAction.md) or [UIContext](./arkts-apis-uicontext-uicontext.md): "Internal error."

When used for [@ohos.router](js-apis-router.md): "Internal error. UI execution context is not found."

When used for the [Navigation](arkui-ts/ts-basic-components-navigation.md) routing framework: "Internal error. Create NavDestination failed, probably caused by wrong UIContext."

When used for [@ohos.arkui.componentSnapshot](js-apis-arkui-componentSnapshot.md): "The builder is not a valid build function."

**Symptom**

For [@ohos.animator](js-apis-animator.md) and [@ohos.promptAction](js-apis-promptAction.md), this error code is reported when an internal error that cannot be rectified by developers occurs, with specific details included in the error message.

For [@ohos.router](js-apis-router.md), this error code is represented as a string type.

For the [Navigation](arkui-ts/ts-basic-components-navigation.md) routing framework, this error code is represented as a number type.

For [@ohos.arkui.componentSnapshot](js-apis-arkui-componentSnapshot.md), this error code is triggered when the internal state is abnormal.

For [UIContext](./arkts-apis-uicontext-uicontext.md), this error code is reported when an internal error that cannot be rectified by developers occurs.

**Possible Cause**

For [@ohos.animator](js-apis-animator.md), [@ohos.router](js-apis-router.md), or [Navigation](arkui-ts/ts-basic-components-navigation.md) routing framework: failure to obtain the rendering engine or parse parameters.

For [@ohos.promptAction](js-apis-promptAction.md): failure to obtain the rendering engine or parse parameters, or unclear UI context.

For [@ohos.arkui.componentSnapshot](js-apis-arkui-componentSnapshot.md): failure to obtain a valid UI instance, null pointer exception, failed internal state validation of the UI instance, inability to query the node (because the component is not added to the tree), or snapshot size exceeding hardware limits (which may vary by hardware platform).

For [UIContext](./arkts-apis-uicontext-uicontext.md): insufficient memory or JS VM exceptions leading to failed UI instance creation.

**Solution**

For issues related to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context), use the APIs provided in **UIContext**. For details, see [Using the UI Context API for UI Operations (UIContext)](../../ui/arkts-global-interface.md).
