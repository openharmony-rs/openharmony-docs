# Scrollable Component Error Codes

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=d20597188c22d75a90cbe878b78662c1b05eda7c translatedAt=2026-11-18T09:27:47.913Z pushedAt=2026-11-20T06:41:48.585Z nl=1 -->

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

## 100031 Placeholder Template Registration Rejected

**Error Message**

Registration rejected: the builder is not marked with @Builder({ isPlaceholder: true }). The ID is not registered.

**Description**

This error code is reported in the following scenario: When the [register](./arkts-apis-placeholderregister.md#register) API of [PlaceholderRegister](./arkts-apis-placeholderregister.md#placeholderregister) is called to register a scroll placeholder template, the builder passed in is not marked with `@Builder({ isPlaceholder: true })` at compile time. The ID will not be registered successfully.

**Possible Causes**

The builder passed in is not a `@Builder({ isPlaceholder: true })` function, or an unmarked builder is passed in dynamically by bypassing the compile-time type check.

**Solution**

Verify that the placeholder template is a global, parameterless, read-only, statically rendered `@Builder({ isPlaceholder: true })` function, and that it is wrapped by **wrapBuilder** before being passed to the **register** API.

