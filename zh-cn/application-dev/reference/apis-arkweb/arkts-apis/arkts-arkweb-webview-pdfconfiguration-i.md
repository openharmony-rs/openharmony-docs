# PdfConfiguration

[createPdf](arkts-arkweb-webview-webviewcontroller-c.md#createpdf) 函数输入参数。 > **说明：** > > 英寸与像素之间转换公式：像素 = 96 * 英寸。

**起始版本：** 14

<!--Device-webview-interface PdfConfiguration--><!--Device-webview-interface PdfConfiguration-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## height

```TypeScript
height: number
```

页面高度。 取值范围：大于等于0。如果不在取值范围内，则设置为0。 单位：英寸。 推荐值：A4纸页面高度11.69英寸。

**类型：** number

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-PdfConfiguration-height: number--><!--Device-PdfConfiguration-height: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## marginBottom

```TypeScript
marginBottom: number
```

下边距。 取值范围：[0.0, 页面高度的一半)。如果不在取值范围内，则设置为0.0。 单位：英寸。

**类型：** number

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-PdfConfiguration-marginBottom: number--><!--Device-PdfConfiguration-marginBottom: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## marginLeft

```TypeScript
marginLeft: number
```

左边距。 取值范围：[0.0, 页面宽度的一半)。如果不在取值范围内，则设置为0.0。 单位：英寸。

**类型：** number

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-PdfConfiguration-marginLeft: number--><!--Device-PdfConfiguration-marginLeft: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## marginRight

```TypeScript
marginRight: number
```

右边距。 取值范围：[0.0, 页面宽度的一半)。如果不在取值范围内，则设置为0.0。 单位：英寸。

**类型：** number

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-PdfConfiguration-marginRight: number--><!--Device-PdfConfiguration-marginRight: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## marginTop

```TypeScript
marginTop: number
```

上边距。 取值范围：[0.0, 页面高度的一半)。如果不在取值范围内，则设置为0.0。 单位：英寸。

**类型：** number

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-PdfConfiguration-marginTop: number--><!--Device-PdfConfiguration-marginTop: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## scale

```TypeScript
scale?: number
```

放大倍数。 取值范围：[0.0, 2.0]。如果不在取值范围内，小于0.0设置为0.0，大于2.0设置为2.0。 默认值：1.0。

**类型：** number

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-PdfConfiguration-scale?: number--><!--Device-PdfConfiguration-scale?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## shouldPrintBackground

```TypeScript
shouldPrintBackground?: boolean
```

true表示打印背景颜色，false表示不打印背景颜色。 默认值：false。

**类型：** boolean

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-PdfConfiguration-shouldPrintBackground?: boolean--><!--Device-PdfConfiguration-shouldPrintBackground?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## width

```TypeScript
width: number
```

页面宽度。 取值范围：大于等于0。如果不在取值范围内，则设置为0。 单位：英寸。 推荐值：A4纸页面宽度8.27英寸。

**类型：** number

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-PdfConfiguration-width: number--><!--Device-PdfConfiguration-width: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

