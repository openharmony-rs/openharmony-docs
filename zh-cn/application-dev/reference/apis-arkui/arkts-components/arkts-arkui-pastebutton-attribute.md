# PasteButton属性/事件

不支持通用属性，仅继承[安全控件通用属性]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 不支持通用事件，仅支持以下事件。

**继承/实现关系：** PasteButtonAttribute extends [SecurityComponentMethod<PasteButtonAttribute>](SecurityComponentMethod<PasteButtonAttribute>)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-unnamed-declare class PasteButtonAttribute extends SecurityComponentMethod<PasteButtonAttribute>--><!--Device-unnamed-declare class PasteButtonAttribute extends SecurityComponentMethod<PasteButtonAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClick

```TypeScript
onClick(event: PasteButtonCallback)
```

点击粘贴控件触发该回调，回调返回授权结果。授权成功后应用可临时获取读取剪贴板权限。 > **说明** > - 为避免因控件样式不合法而导致授权失败，请开发者先了解安全控件样式的\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PasteButtonAttribute-onClick(event: PasteButtonCallback): PasteButtonAttribute--><!--Device-PasteButtonAttribute-onClick(event: PasteButtonCallback): PasteButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 点击事件的回调函数，用于处理粘贴控件点击后的授权结果。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_从API version 18开始，统一使用[PasteButtonCallback]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_，可额外获取error信息。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 18 |

