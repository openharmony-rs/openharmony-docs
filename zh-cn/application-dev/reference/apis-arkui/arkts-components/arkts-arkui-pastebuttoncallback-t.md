# PasteButtonCallback

```TypeScript
type PasteButtonCallback = (event: ClickEvent, result: PasteButtonOnClickResult, error?: BusinessError<void>) => void
```

点击粘贴控件触发该回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type PasteButtonCallback = (event: ClickEvent, result: PasteButtonOnClickResult, error?: BusinessError<void>) => void--><!--Device-unnamed-type PasteButtonCallback = (event: ClickEvent, result: PasteButtonOnClickResult, error?: BusinessError<void>) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [ClickEvent](arkts-arkui-clickevent-i.md) | 是 | 点击事件对象，包含点击位置、时间戳、输入设备等信息。  |
| result | [PasteButtonOnClickResult](arkts-arkui-pastebuttononclickresult-e.md) | 是 | 剪贴板权限的授权结果。 <br>返回SUCCESS表示已获得当前剪贴板内容的临时读取权限，可以继续执行读取操作；返回TEMPORARY_AUTHORIZATION_FAILED表示本次授权未成功，不应继续读取剪贴板内容。  |
| error | [BusinessError](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md)&lt;void&gt; | 否 | 点击按钮时的错误码和错误信息。 <br>默认值:undefined。 <br>授权结果需通过result参数判断。<br/>错误码1表示系统内部错误。请检查系统状态后重试。<br/>错误码2表示属性设置错误，包括但不限于：<br/>1. 字体或图标设置过小。<br/>2. 字体或图标与控件背景颜色相近。<br/>3. 字体或图标颜色过于透明。<br/>4. padding为负值。<br/>5. 按钮被其他组件或窗口遮挡。<br/>6. 文本超出控件背景范围。<br/>7. 按钮超出窗口或屏幕。<br/>8. 按钮整体尺寸过大。<br/>9. 按钮文本被截断，显示不全。<br/>10. 部分安全控件相关属性的设置导致控件无法正常显示。  |

