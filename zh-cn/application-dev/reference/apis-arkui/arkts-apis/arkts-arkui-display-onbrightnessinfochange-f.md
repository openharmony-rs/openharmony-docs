# onBrightnessInfoChange

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## onBrightnessInfoChange

```TypeScript
function onBrightnessInfoChange(callback: BrightnessCallback<long, BrightnessInfo>): void
```

Register the callback for brightness info changes.

**起始版本：** 23

<!--Device-display-function onBrightnessInfoChange(callback: BrightnessCallback<long, BrightnessInfo>): void--><!--Device-display-function onBrightnessInfoChange(callback: BrightnessCallback<long, BrightnessInfo>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [BrightnessCallback](arkts-arkui-display-brightnesscallback-t.md)&lt;long, [BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md)&gt; | 是 | Callback used to return the display if and corresponding brightness info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1400004](../errorcode-display.md#1400004-参数异常) | Parameter error. Possible cause: 1. Invalid parameter range. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例**

```TypeScript
let callback: display.BrightnessCallback<long, display.BrightnessInfo> = (id: long, data: display.BrightnessInfo) => {
  console.info(`Listening enabled ${id}. Data: ${JSON.stringify(data)}`);
};
try {
  display.onBrightnessInfoChange(callback);
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`brightnessInfoChange error. Code: ${error.code}, message: ${error.message}`);
}
```

