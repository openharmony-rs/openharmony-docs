# DrawableDescriptor错误码
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码](../errorcode-universal.md)。

## 111001 资源加载失败

**错误信息**

resource loading failed.

**错误描述**

该错误码在资源加载失败时被触发。

**可能原因**

路径不存在，资源不存在或者文件已损坏。

**处理步骤**

检查资源是否存在或文件是否损坏。

## 111002 资源已释放

**错误信息**

The native memory referenced by the drawableDescriptor has been released.

**错误描述**

该错误码在DrawableDescriptor引用的native内存已被释放时被触发。当调用[release](js-apis-arkui-drawableDescriptor.md#release)方法释放资源后，再调用[getPixelMap](js-apis-arkui-drawableDescriptor.md#getpixelmap)、[getForeground](js-apis-arkui-drawableDescriptor.md#getforeground)、[getBackground](js-apis-arkui-drawableDescriptor.md#getbackground)、[getMask](js-apis-arkui-drawableDescriptor.md#getmask)、[loadSync](js-apis-arkui-drawableDescriptor.md#loadsync21)、[load](js-apis-arkui-drawableDescriptor.md#load21)等接口时会触发此错误。

**可能原因**

在调用[release](js-apis-arkui-drawableDescriptor.md#release)释放DrawableDescriptor资源后，继续调用该对象的其他接口。

**处理步骤**

1. 在调用getPixelMap等接口前，通过[isReleased](js-apis-arkui-drawableDescriptor.md#isreleased)检查对象是否已释放。
2. 避免在[release](js-apis-arkui-drawableDescriptor.md#release)后继续使用该DrawableDescriptor对象。