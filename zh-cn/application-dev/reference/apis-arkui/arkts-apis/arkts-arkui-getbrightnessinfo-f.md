# getBrightnessInfo

## getBrightnessInfo

```TypeScript
function getBrightnessInfo(displayId: number): BrightnessInfo
```

获取指定displayId对应屏幕的亮度信息。如果屏幕不支持HDR，返回的[BrightnessInfo](arkts-arkui-brightnessinfo-i.md)对象中的currentHeadroom和maxHeadroom
为默认值。虚拟屏的BrightnessInfo对象中sdrNits为默认值。

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 屏幕ID。该参数仅支持整数输入，该参数大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BrightnessInfo | 返回displayId对应屏幕的亮度信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |
| [1400004](../errorcode-display.md#1400004-参数异常) | Parameter error. Possible cause: 1. Invalid parameter range. |

**示例：**

```TypeScript
try {
  let brightnessInfo = display.getBrightnessInfo(0);
  console.info(`brightness info: ${JSON.stringify(brightnessInfo)}`);
} catch (error) {
  console.error(`Failed to getDisplayBrightness. Code: ${error.code}, message: ${error.message}`);
}

```

