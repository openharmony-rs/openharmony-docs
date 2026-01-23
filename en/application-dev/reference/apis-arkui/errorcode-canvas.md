# Canvas Component Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @ZhangYu-Coder-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 103701 Parameter Error

**Error Message**

Parameter error.

**Description**

This error code is reported when invalid or incorrect parameters are passed to the API.

**Possible Causes**

Refer to the specific documentation of the API that triggers this error.

**Solution**

Provide correct parameters as specified in the API documentation.

## 103702 Drawing Context Is Not Bound to Any Canvas Component

**Error Message**

The drawingContext is not bound to a canvas component.

**Description**

The current drawing context is not bound to any **Canvas** component.

**Possible Causes**

The current drawing context is not bound to any **Canvas** component.

**Solution**

Bind the drawing context to a **Canvas** component and then call the [getContext2DFromDrawingContext](./arkui-ts/ts-canvasrenderingcontext2d.md#getcontext2dfromdrawingcontext23) method.
