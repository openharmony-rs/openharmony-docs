# SnapshotResult

全量绘制回调结果。

**起始版本：** 12

<!--Device-webview-interface SnapshotResult--><!--Device-webview-interface SnapshotResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## id

```TypeScript
id?: string
```

snapshot的id。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SnapshotResult-id?: string--><!--Device-SnapshotResult-id?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## imagePixelMap

```TypeScript
imagePixelMap?: image.PixelMap
```

全量绘制结果为image.PixelMap格式。

**类型：** image.PixelMap

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SnapshotResult-imagePixelMap?: image.PixelMap--><!--Device-SnapshotResult-imagePixelMap?: image.PixelMap-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## size

```TypeScript
size?: SizeOptions
```

web绘制的尺寸，最多支持16000px * 16000px，长度单位支持px、vp、%，需保持不同参数传入长度单位一致，默认单位vp，超过规格时返回最大规格。（示例：width:'100px'，height:'200px'。或者 width:'20%'，height:'30%'。只写数字时单位为vp。）

**类型：** SizeOptions

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SnapshotResult-size?: SizeOptions--><!--Device-SnapshotResult-size?: SizeOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## status

```TypeScript
status?: boolean
```

snapshot的状态，正常为true，失败为false，获取全量绘制结果失败，返回size的长宽都为0，map为空。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SnapshotResult-status?: boolean--><!--Device-SnapshotResult-status?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

