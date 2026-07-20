# isScreenReaderOpenSync

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

<a id="isscreenreaderopensync"></a>
## isScreenReaderOpenSync

```TypeScript
function isScreenReaderOpenSync(): boolean
```

是否开启了屏幕朗读模式。

**起始版本：** 18

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-accessibility-function isScreenReaderOpenSync(): boolean--><!--Device-accessibility-function isScreenReaderOpenSync(): boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Vision

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否开启了屏幕朗读。true表示开启了屏幕朗读，false表示未开启屏幕朗读。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

let status: boolean = accessibility.isScreenReaderOpenSync();

```

