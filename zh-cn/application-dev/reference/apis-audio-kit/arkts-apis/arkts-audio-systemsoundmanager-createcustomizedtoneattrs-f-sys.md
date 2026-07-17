# createCustomizedToneAttrs（系统接口）

## 导入模块

```TypeScript
import { systemSoundManager } from '@kit.AudioKit';
```

## createCustomizedToneAttrs

```TypeScript
function createCustomizedToneAttrs(): ToneAttrs
```

创建自定义铃声属性。

**起始版本：** 12

<!--Device-systemSoundManager-function createCustomizedToneAttrs(): ToneAttrs--><!--Device-systemSoundManager-function createCustomizedToneAttrs(): ToneAttrs-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ToneAttrs](arkts-audio-systemsoundmanager-toneattrs-i-sys.md) | 铃声属性类。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
let toneAttrs: systemSoundManager.ToneAttrs = systemSoundManager.createCustomizedToneAttrs();

```

