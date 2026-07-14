# WindowDensityInfo

窗口所在显示设备和窗口自定义的显示密度信息，是与像素单位无关的缩放系数，即显示大小缩放系数。

**起始版本：** 15

**系统能力：** SystemCapability.Window.SessionManager

## customDensity

```TypeScript
customDensity: number
```

窗口自定义设置的显示大小缩放系数，该参数取值范围为0.5-4.0。未设置该参数时，将跟随系统显示大小缩放系数变化。该参数仅主窗口生效，在子窗或系统窗口上等于系统显示大小缩放系数(systemDensity)。

**类型：** number

**起始版本：** 15

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## defaultDensity

```TypeScript
defaultDensity: number
```

窗口所在屏幕的系统默认显示大小缩放系数，跟随窗口所在屏幕变化，该参数变化范围为0.5-4.0。

**类型：** number

**起始版本：** 15

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## systemDensity

```TypeScript
systemDensity: number
```

窗口所在屏幕的系统显示大小缩放系数，跟随用户设置变化，该参数变化范围为0.5-4.0。

**类型：** number

**起始版本：** 15

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

