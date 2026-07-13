# SnapshotInfo

获取全量绘制结果入参。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## id

```TypeScript
id?: string
```

snapshot的id。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## size

```TypeScript
size?: SizeOptions
```

web绘制的尺寸，最多支持16000px * 16000px，长度单位支持px、vp、%，需保持不同参数传入长度单位一致，默认单位vp，超过规格时返回最大规格。（示例：width:'100px'，height:'200px'。
或者 width:'20%'，height:'30%'。只写数字时单位为vp。）

**类型：** SizeOptions

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

