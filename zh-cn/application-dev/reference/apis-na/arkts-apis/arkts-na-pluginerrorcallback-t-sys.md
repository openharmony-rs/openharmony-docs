# PluginErrorCallback（系统接口）

```TypeScript
export type PluginErrorCallback = (info: PluginErrorData) => void
```

发生错误时触发事件回调。 AnonyMous Object Rectification

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type PluginErrorCallback = (info: PluginErrorData) => void--><!--Device-unnamed-export type PluginErrorCallback = (info: PluginErrorData) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [PluginErrorData](arkts-na-plugincomponent-pluginerrordata-i-sys.md) | 是 | 发生错误时提供的数据。 |

