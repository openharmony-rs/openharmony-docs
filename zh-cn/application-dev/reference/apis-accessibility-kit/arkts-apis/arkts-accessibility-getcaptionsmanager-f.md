# getCaptionsManager

## getCaptionsManager

```TypeScript
function getCaptionsManager(): CaptionsManager
```

获取无障碍字幕配置管理实例。

**起始版本：** 8

**废弃版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CaptionsManager | 无障碍字幕配置管理。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

let captionsManager = accessibility.getCaptionsManager();

```

