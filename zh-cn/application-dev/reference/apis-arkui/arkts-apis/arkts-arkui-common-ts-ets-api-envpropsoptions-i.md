# EnvPropsOptions

用于指定环境变量名称及其默认值的键值对对象，作为[envProps](arkts-arkui-common-ts-ets-api-environment-c.md#envprops-1)参数传入。

**起始版本：** 10

<!--Device-unnamed-declare interface EnvPropsOptions--><!--Device-unnamed-declare interface EnvPropsOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultValue

```TypeScript
defaultValue: number | string | boolean
```

查询不到环境变量key，则使用defaultValue作为默认值存入AppStorage中。

**类型：** number | string | boolean

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EnvPropsOptions-defaultValue: number | string | boolean--><!--Device-EnvPropsOptions-defaultValue: number | string | boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key: string
```

环境变量名称，支持的范围详见[内置环境变量说明](@link Environment)。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EnvPropsOptions-key: string--><!--Device-EnvPropsOptions-key: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

