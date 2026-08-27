# SnapshotResult

全量绘制回调结果。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## id

```TypeScript
id?: string
```

snapshot的id。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## imagePixelMap

```TypeScript
imagePixelMap?: image.PixelMap
```

全量绘制结果为image.PixelMap格式。

**类型：** image.PixelMap

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## size

```TypeScript
size?: SizeOptions
```

Web绘制的真实尺寸，SizeOptions对象包含width和height属性，均为number类型，单位vp。

**类型：** [SizeOptions](../../apis-arkui/arkts-apis/arkts-arkui-sizeoptions-i.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## status

```TypeScript
status?: boolean
```

snapshot的状态，正常为true，失败为false，获取全量绘制结果失败，返回size的长宽都为0，imagePixelMap为空。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
