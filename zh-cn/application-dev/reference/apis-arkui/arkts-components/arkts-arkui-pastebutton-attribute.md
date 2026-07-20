# PasteButton属性/事件

不支持通用属性，仅继承[安全控件通用属性](./security_component)。

不支持通用事件，仅支持以下事件。

**继承/实现关系：** PasteButtonAttribute extends [SecurityComponentMethod<PasteButtonAttribute>](SecurityComponentMethod<PasteButtonAttribute>)

**起始版本：** 10

<!--Device-unnamed-declare class PasteButtonAttribute extends SecurityComponentMethod<PasteButtonAttribute>--><!--Device-unnamed-declare class PasteButtonAttribute extends SecurityComponentMethod<PasteButtonAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="onclick"></a>
## onClick

```TypeScript
onClick(event: PasteButtonCallback)
```

点击粘贴控件触发该回调，回调返回授权结果。授权成功后应用可临时获取读取剪贴板权限。

> **说明**  
> - 为避免因控件样式不合法而导致授权失败，请开发者先了解安全控件样式的[约束与限制](docroot://security/AccessToken/security-component-overview.md#约束与限制)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PasteButtonAttribute-onClick(event: PasteButtonCallback): PasteButtonAttribute--><!--Device-PasteButtonAttribute-onClick(event: PasteButtonCallback): PasteButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [PasteButtonCallback](arkts-arkui-pastebuttoncallback-t.md) | 是 | 点击事件的回调函数，用于处理粘贴控件点击后的授权结果。<br>从API version 18开始，统一使用[PasteButtonCallback](arkts-arkui-pastebuttoncallback-t.md)，可额外获取error信息。<br>**起始版本：** 18 |

