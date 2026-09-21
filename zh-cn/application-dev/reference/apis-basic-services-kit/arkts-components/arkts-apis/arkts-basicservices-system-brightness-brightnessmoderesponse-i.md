# BrightnessModeResponse

```TypeScript
export interface BrightnessModeResponse
```

包含屏幕亮度模式的对象。

**起始版本：** 3

**废弃版本：** 7

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

## 导入模块

```TypeScript
import { Brightness, BrightnessModeResponse, BrightnessResponse, GetBrightnessModeOptions, GetBrightnessOptions, SetBrightnessModeOptions, SetBrightnessOptions, SetKeepScreenOnOptions } from '@kit.BasicServicesKit';
```

## mode

```TypeScript
mode: number
```

0表示手动调节屏幕亮度模式，1表示自动调节屏幕亮度模式。

**类型：** number

**起始版本：** 3

**废弃版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite
