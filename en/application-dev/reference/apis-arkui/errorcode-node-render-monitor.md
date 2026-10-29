# Render State Listening Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangzhiyuan1-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c8d89821f92b220ca7659a1de29fb1e3b0412c5b translatedAt=2026-10-15T10:44:41.443Z pushedAt=2026-10-16T03:06:18.658Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 161001 Number of Nodes Listening for Render State Exceeds the Limit

**Error Message**

The count of nodes monitoring render state is over the limitation.

**Description**

This error code is reported when the number of nodes registered to listen for render state exceeds the system limit.

**Possible Causes**

When the [on('nodeRenderState')](arkts-apis-uicontext-uiobserver.md#onnoderenderstate20) API is called to register a listener for the render state of nodes, the number of nodes registered for listening in a single UI instance exceeds the limit.

**Solution**

Ensure that no more than 64 nodes are registered to listen for the render state in a single UI instance.
