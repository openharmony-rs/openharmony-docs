# ScrollOffset

网页当前的滚动偏移量。

**起始版本：** 13

**系统能力：** SystemCapability.Web.Webview.Core

## x

```TypeScript
x: number
```

网页在水平方向的滚动偏移量。取值为网页左边界x坐标与Web组件左边界x坐标的差值。

当网页向右过滚动时，取值范围为负值。

当网页没有过滚动或者网页向左过滚动时，取值为0或正值。

单位：vp。

**类型：** number

**起始版本：** 13

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## y

```TypeScript
y: number
```

网页在垂直方向的滚动偏移量。取值为网页上边界y坐标与Web组件上边界y坐标的差值。

当网页向下过滚动时，取值范围为负值。

当网页没有过滚动或者网页向上过滚动时，取值为0或正值。

单位：vp。

**类型：** number

**起始版本：** 13

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

