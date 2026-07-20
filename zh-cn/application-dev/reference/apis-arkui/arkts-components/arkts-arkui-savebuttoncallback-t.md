# SaveButtonCallback

```TypeScript
type SaveButtonCallback = (event: ClickEvent, result: SaveButtonOnClickResult, error?: BusinessError<void>) => void
```

点击保存控件触发该回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type SaveButtonCallback = (event: ClickEvent, result: SaveButtonOnClickResult, error?: BusinessError<void>) => void--><!--Device-unnamed-type SaveButtonCallback = (event: ClickEvent, result: SaveButtonOnClickResult, error?: BusinessError<void>) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [ClickEvent](arkts-arkui-clickevent-i.md) | 是 | 点击事件对象，包含点击的位置、时间戳、输入设备等信息。  |
| result | [SaveButtonOnClickResult](arkts-arkui-savebuttononclickresult-e.md) | 是 | 授权结果。 <br>返回SUCCESS表示当前保存动作已获得临时授权，可继续访问媒体库接口；返回TEMPORARY_AUTHORIZATION_FAILED时，不应继续执行后续保存动作。返回CANCELED_BY_USER时，表示用户在授权弹窗中主动取消授权，该结果仅在调用[userCancelEvent](SaveButtonAttribute#userCancelEvent)并设置参数为true时才会返回；若未设置userCancelEvent(true)，用户取消授权时将返回TEMPORARY_AUTHORIZATION_FAILED。  |
| error | [BusinessError](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md)&lt;void&gt; | 否 | 点击按钮时的错误码和错误信息。不传入该参数时为undefined。授权结果需通过result参数判断。 <br> 错误码1表示系统内部错误，可能原因和处理建议如下：<br>1. IPC（Inter-Process Communication，进程间通信）通信失败。请检查系统状态后重试。<br>2. 安全控件弹窗失败。请检查保存控件是否被遮挡或是否满足安全控件样式约束，修正后重试。<br>错误码2表示属性设置错误，具体包括以下情况：<br>1. 字体或图标设置过小。<br>2. 字体或图标与背景颜色相近。<br>3. 字体或图标颜色过于透明。<br>4. padding为负值。<br>5. 按钮被其他组件或窗口遮挡。<br>6. 文本超出控件背景范围。<br>7. 按钮超出窗口或屏幕。<br>8. 按钮整体尺寸过大。<br>9. 按钮文本被截断，显示不全。<br>10. 其他属性设置不当影响安全控件显示。  |

