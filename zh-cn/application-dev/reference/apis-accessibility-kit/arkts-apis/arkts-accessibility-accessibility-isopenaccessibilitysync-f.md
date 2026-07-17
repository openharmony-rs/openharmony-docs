# isOpenAccessibilitySync

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

## isOpenAccessibilitySync

```TypeScript
function isOpenAccessibilitySync(): boolean
```

查询当前系统内是否存在已开启的辅助应用。如需获取系统内辅助应用信息，推荐使用[accessibility.getAccessibilityExtensionListSync](arkts-accessibility-accessibility-getaccessibilityextensionlistsync-f.md#getaccessibilityextensionlistsync-1)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-accessibility-function isOpenAccessibilitySync(): boolean--><!--Device-accessibility-function isOpenAccessibilitySync(): boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前系统内是否有辅助应用开启。true表示启用了一个或多个辅助应用，false表示未启用任何辅助应用。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 1、系统内已安装多个辅助应用，若都没有开启，返回false。
// 2、系统内已安装多个辅助应用，若开启任意一个，返回true。
let status: boolean = accessibility.isOpenAccessibilitySync();

```

