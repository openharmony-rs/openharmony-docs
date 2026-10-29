# XComponent Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=5a5f201351bc507eed1f4198e52fee2b1f6735cb translatedAt=2026-10-15T10:49:56.425Z pushedAt=2026-10-16T03:40:16.652Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 103501 Invalid XComponent Status

**Error Message**

Failed to call the method because the **XComponent** is invalid.

**Description**

This error code is reported when the **XComponent** is currently in an invalid state, and the method call fails.

**Possible Causes**

When an **XComponent**-related method is called, the **XComponent** has not finished the initialization, or the surface it holds has been destroyed or released, causing the **XComponent** to be in an invalid state.

**Solution**

1. Ensure that the **XComponent** has been loaded and initialized before calling related methods.
2. Check whether the surface held by the **XComponent** has been destroyed or released. If it is invalid, create an **XComponent** instance again before calling.
