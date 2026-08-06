# SaveButtonCallback

```TypeScript
type SaveButtonCallback = (event: ClickEvent, result: SaveButtonOnClickResult, error?: BusinessError<void>) => void
```

点击保存控件触发该回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type SaveButtonCallback = (event: ClickEvent, result: SaveButtonOnClickResult, error?: BusinessError<void>) => void--><!--Device-unnamed-type SaveButtonCallback = (event: ClickEvent, result: SaveButtonOnClickResult, error?: BusinessError<void>) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 点击事件对象，包含点击的位置、时间戳、输入设备等信息。  |
| result | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 授权结果。 \_\_\_HTML\_TAG\_USD\_1\_\_\_返回SUCCESS表示当前保存动作已获得临时授权，可继续访问媒体库接口；返回TEMPORARY\_AUTHORIZATION\_FAILED时，不应继续执行后续保存动作。返回CANCELED\_BY\_USER时，表示用户在授权弹窗中主动取消授权，该结果仅在调用[userCancelEvent]\_\_\_JSDOC\_LINK\_USD\_0\_\_\_并设置参数为true时才会返回；若未设置userCancelEvent(true)，用户取消授权时将返回TEMPORARY\_AUTHORIZATION\_FAILED。  |
| error | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 点击按钮时的错误码和错误信息。不传入该参数时为undefined。授权结果需通过result参数判断。 \_\_\_HTML\_TAG\_USD\_0\_\_\_ 错误码1表示系统内部错误，可能原因和处理建议如下：\_\_\_HTML\_TAG\_USD\_1\_\_\_1. IPC（Inter-Process Communication，进程间通信）通信失败。请检查系统状态后重试。\_\_\_HTML\_TAG\_USD\_2\_\_\_2. 安全控件弹窗失败。请检查保存控件是否被遮挡或是否满足安全控件样式约束，修正后重试。\_\_\_HTML\_TAG\_USD\_3\_\_\_错误码2表示属性设置错误，具体包括以下情况：\_\_\_HTML\_TAG\_USD\_4\_\_\_1. 字体或图标设置过小。\_\_\_HTML\_TAG\_USD\_5\_\_\_2. 字体或图标与背景颜色相近。\_\_\_HTML\_TAG\_USD\_6\_\_\_3. 字体或图标颜色过于透明。\_\_\_HTML\_TAG\_USD\_7\_\_\_4. padding为负值。\_\_\_HTML\_TAG\_USD\_8\_\_\_5. 按钮被其他组件或窗口遮挡。\_\_\_HTML\_TAG\_USD\_9\_\_\_6. 文本超出控件背景范围。\_\_\_HTML\_TAG\_USD\_10\_\_\_7. 按钮超出窗口或屏幕。\_\_\_HTML\_TAG\_USD\_11\_\_\_8. 按钮整体尺寸过大。\_\_\_HTML\_TAG\_USD\_12\_\_\_9. 按钮文本被截断，显示不全。\_\_\_HTML\_TAG\_USD\_13\_\_\_10. 其他属性设置不当影响安全控件显示。  |

