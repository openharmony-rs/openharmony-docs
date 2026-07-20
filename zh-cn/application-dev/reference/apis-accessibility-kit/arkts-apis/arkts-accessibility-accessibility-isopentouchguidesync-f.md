# isOpenTouchGuideSync

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

<a id="isopentouchguidesync"></a>
## isOpenTouchGuideSync

```TypeScript
function isOpenTouchGuideSync(): boolean
```

是否开启了触摸浏览模式。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-accessibility-function isOpenTouchGuideSync(): boolean--><!--Device-accessibility-function isOpenTouchGuideSync(): boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Vision

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否开启了触摸浏览模式。true表示开启了触摸浏览，false表示未开启触摸浏览。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

let status: boolean = accessibility.isOpenTouchGuideSync();

```

