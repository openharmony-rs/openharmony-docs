# PluginErrorCallback（系统接口）

```TypeScript
declare type PluginErrorCallback = (info: PluginErrorData) => void
```

发生错误时触发的回调。AnonyMous Object Rectification

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare type PluginErrorCallback = (info: PluginErrorData) => void--><!--Device-unnamed-declare type PluginErrorCallback = (info: PluginErrorData) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [PluginErrorData](arkts-arkui-pluginerrordata-i-sys.md) | 是 | 插件错误数据  |

