# isOpenAccessibilitySync

## isOpenAccessibilitySync

```TypeScript
function isOpenAccessibilitySync(): boolean
```

查询当前系统内是否存在已开启的辅助应用。如需获取系统内辅助应用信息，推荐使用 [accessibility.getAccessibilityExtensionListSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

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

// 1、系统内已安装多个辅助应用，若都没有开启，返回false。
// 2、系统内已安装多个辅助应用，若开启任意一个，返回true。
let status: boolean = accessibility.isOpenAccessibilitySync();
```

