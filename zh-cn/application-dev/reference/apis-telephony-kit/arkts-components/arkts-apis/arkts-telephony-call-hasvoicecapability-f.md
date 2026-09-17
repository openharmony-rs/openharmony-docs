# hasVoiceCapability

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## hasVoiceCapability

```TypeScript
function hasVoiceCapability(): boolean
```

检查当前设备是否具备语音通话能力。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示设备具备语音通话能力，返回false表示设备不具备语音通话能力。 |

**示例**

```TypeScript
let result: boolean = call.hasVoiceCapability();
console.info(`hasVoiceCapability: ${JSON.stringify(result)}`);
```
