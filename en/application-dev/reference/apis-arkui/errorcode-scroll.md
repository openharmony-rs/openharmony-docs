# Scrollable Component Error Codes

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=5575f73d326abf87cc6dda50f211ca34472d98c2 translatedAt=2026-11-25T10:59:54.473Z pushedAt=2026-11-27T01:18:09.851Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 100004 Controller Not Bound to Component

**Error Message**

Controller not bound to component.

**Description**

This error code is reported when an API is called through a controller but no controller is bound to the component. The error code is a string.

**Possible Causes**

The API called requires a controller, but the component is not bound to one.

**Solution**

Verify that the controller is properly bound to a component and that the component has not been released.
