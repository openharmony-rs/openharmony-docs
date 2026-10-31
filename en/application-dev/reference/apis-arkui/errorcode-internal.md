# API Call Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3; @huangxiaolinabc; @liyi0309-->
<!--Designer: @hehongyang3; @liyi0309; @fangzhiyuan1-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=bbc6406dab71d9f75b4831661ca1204731bcdd0c translatedAt=2026-08-29T09:21:23.963Z pushedAt=2026-08-31T03:13:46.689Z -->

> **NOTE**
>
> This topic describes only the error codes specific to this module. If an API call exception occurs when you use ArkUI APIs, refer to the error code information in this topic to locate the cause and take the corresponding measures. For universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 100001 Internal Error

**Error Message**

When used for [@ohos.animator](js-apis-animator.md): "The specified page is not found or the object property list is not obtained."

When used for [@ohos.promptAction](js-apis-promptAction.md) or [UIContext](arkts-apis-uicontext-uicontext.md): "Internal error."

When used for [@ohos.router](js-apis-router.md): "Internal error. UI execution context is not found."

When used for the [Navigation](arkui-ts/ts-basic-components-navigation.md) routing framework: "Internal error. Create NavDestination failed, probably caused by wrong UIContext."

When used for [@ohos.arkui.componentSnapshot](js-apis-arkui-componentSnapshot.md): "The builder is not a valid build function."

When used for [@ohos.arkui.componentUtils](js-apis-arkui-componentUtils.md): "UI execution context not found."

**Symptom**

For [@ohos.animator](js-apis-animator.md) or [@ohos.promptAction](js-apis-promptAction.md), this error code is reported when an internal error that you cannot rectify occurs, with specific details included in the error message.

For [@ohos.router](js-apis-router.md), this error code is represented as a string type.

For the [Navigation](arkui-ts/ts-basic-components-navigation.md) routing framework, this error code is represented as a number type.

For [@ohos.arkui.componentSnapshot](js-apis-arkui-componentSnapshot.md), this error code is triggered when the internal state is abnormal.

For [UIContext](./arkts-apis-uicontext-uicontext.md), this error code is reported when an internal error that cannot be rectified by developers occurs.

**Possible Cause**

For [@ohos.animator](js-apis-animator.md), [@ohos.router](js-apis-router.md), or the [Navigation](arkui-ts/ts-basic-components-navigation.md) routing framework: failure to obtain the rendering engine or parse parameters.

For [@ohos.promptAction](js-apis-promptAction.md): failure to obtain the rendering engine or parse parameters, or unclear UI context.

For [@ohos.arkui.componentSnapshot](js-apis-arkui-componentSnapshot.md): failure to obtain a valid UI instance, null pointer exception, UI instance internal state validation exception, failure to query the node because the component is not mounted to the component tree, or the screenshot size exceeding the hardware limit (which varies with the hardware platform).

For [UIContext](./arkts-apis-uicontext-uicontext.md): failure to create a UI instance because <!--Del-->the color picking parameters are not set as required by the API or in invalid types, <!--DelEnd-->the memory is insufficient, or the JS VM is abnormal.

**Solution**

For issues related to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context), use the APIs provided in **UIContext**. For details, see [Using the UI Context API for UI Operations (UIContext)](../../ui/arkts-global-interface.md).

