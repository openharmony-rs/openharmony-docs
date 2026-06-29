# DrawableDescriptor Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 111001 Internal Error

**Error Message**

resource loading failed.

**Description**

This error code is reported when resource loading fails.

**Possible Causes**

The path does not exist, the resource does not exist, or the file is corrupted.

**Solution**

Check whether the resource exists or whether the file is corrupted.

## 111002 Resource Released

**Error Message**

The native memory referenced by the drawableDescriptor has been released.

**Description**

This error code is reported when the native memory referenced by **DrawableDescriptor** has been released. This error occurs when [getPixelMap](js-apis-arkui-drawableDescriptor.md#getpixelmap), [getForeground](js-apis-arkui-drawableDescriptor.md#getforeground), [getBackground](js-apis-arkui-drawableDescriptor.md#getbackground), [getMask](js-apis-arkui-drawableDescriptor.md#getmask), [loadSync](js-apis-arkui-drawableDescriptor.md#loadsync21), or [load](js-apis-arkui-drawableDescriptor.md#load21) is called after [release](js-apis-arkui-drawableDescriptor.md#release) is called to release resources.

**Possible Causes**

After calling [release](js-apis-arkui-drawableDescriptor.md#release) to release the resource of **DrawableDescriptor**, other APIs of the object are called.

**Solution**

1. Before calling APIs such as **getPixelMap**, use [isReleased](js-apis-arkui-drawableDescriptor.md#isreleased) to check whether the object has been released.
2. Do not use the **DrawableDescriptor** object after calling [release](js-apis-arkui-drawableDescriptor.md#release).
