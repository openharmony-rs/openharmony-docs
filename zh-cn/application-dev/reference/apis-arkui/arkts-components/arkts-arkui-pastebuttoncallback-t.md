# PasteButtonCallback

```TypeScript
type PasteButtonCallback = (event: ClickEvent, result: PasteButtonOnClickResult, error?: BusinessError<void>) => void
```

点击粘贴控件触发该回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type PasteButtonCallback = (event: ClickEvent, result: PasteButtonOnClickResult, error?: BusinessError<void>) => void--><!--Device-unnamed-type PasteButtonCallback = (event: ClickEvent, result: PasteButtonOnClickResult, error?: BusinessError<void>) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 点击事件对象，包含点击位置、时间戳、输入设备等信息。  |
| result | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 剪贴板权限的授权结果。 \_\_\_HTML\_TAG\_USD\_0\_\_\_返回SUCCESS表示已获得当前剪贴板内容的临时读取权限，可以继续执行读取操作；返回TEMPORARY\_AUTHORIZATION\_FAILED表示本次授权未成功，不应继续读取剪贴板内容。  |
| error | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 点击按钮时的错误码和错误信息。 \_\_\_HTML\_TAG\_USD\_0\_\_\_默认值:undefined。 \_\_\_HTML\_TAG\_USD\_1\_\_\_授权结果需通过result参数判断。\_\_\_HTML\_TAG\_USD\_2\_\_\_错误码1表示系统内部错误。请检查系统状态后重试。\_\_\_HTML\_TAG\_USD\_3\_\_\_错误码2表示属性设置错误，包括但不限于：\_\_\_HTML\_TAG\_USD\_4\_\_\_1. 字体或图标设置过小。\_\_\_HTML\_TAG\_USD\_5\_\_\_2. 字体或图标与控件背景颜色相近。\_\_\_HTML\_TAG\_USD\_6\_\_\_3. 字体或图标颜色过于透明。\_\_\_HTML\_TAG\_USD\_7\_\_\_4. padding为负值。\_\_\_HTML\_TAG\_USD\_8\_\_\_5. 按钮被其他组件或窗口遮挡。\_\_\_HTML\_TAG\_USD\_9\_\_\_6. 文本超出控件背景范围。\_\_\_HTML\_TAG\_USD\_10\_\_\_7. 按钮超出窗口或屏幕。\_\_\_HTML\_TAG\_USD\_11\_\_\_8. 按钮整体尺寸过大。\_\_\_HTML\_TAG\_USD\_12\_\_\_9. 按钮文本被截断，显示不全。\_\_\_HTML\_TAG\_USD\_13\_\_\_10. 部分安全控件相关属性的设置导致控件无法正常显示。  |

