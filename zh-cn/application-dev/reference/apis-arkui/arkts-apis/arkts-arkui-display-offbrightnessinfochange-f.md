# offBrightnessInfoChange

## offBrightnessInfoChange

```TypeScript
function offBrightnessInfoChange(callback?: BrightnessCallback<long, BrightnessInfo>): void
```

Unregister the callback for brightness info changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-display-function offBrightnessInfoChange(callback?: BrightnessCallback<long, BrightnessInfo>): void--><!--Device-display-function offBrightnessInfoChange(callback?: BrightnessCallback<long, BrightnessInfo>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;long, BrightnessInfo&gt; | 否 | Callback used to return the display corresponding brightness info. If not provided, all callbacks for the given event type will be removed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |
| [1400004](../errorcode-display.md#1400004-参数异常) | Parameter error. Possible cause: 1. Invalid parameter range. |

**示例：**

```TypeScript
let callback: display.BrightnessCallback<long, display.BrightnessInfo> = (id: long, data: display.BrightnessInfo) => {
  console.info(`Listening enabled ${id}. Data: ${JSON.stringify(data)}`);
};
try {
  display.offBrightnessInfoChange(callback);
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`brightnessInfoChange error. Code ${error.code}, message: ${error.message}`);
}
```

