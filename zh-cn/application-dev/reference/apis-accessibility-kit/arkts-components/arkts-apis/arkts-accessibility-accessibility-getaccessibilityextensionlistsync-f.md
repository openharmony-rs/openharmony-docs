# getAccessibilityExtensionListSync

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## getAccessibilityExtensionListSync

```TypeScript
function getAccessibilityExtensionListSync(
    abilityType: AbilityType,
    stateType: AbilityState
  ): Array<AccessibilityAbilityInfo>
```

查询当前系统内辅助应用列表，支持按条件查询。

本接口为同步版本，与[accessibility.getAccessibilityExtensionList](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md)（异步版本）功能相同，如需立即获取结果可使用本接口，如需在非阻塞场景下查询建议使用异步版本。

**起始版本：** 12

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityType | [AbilityType](arkts-accessibility-accessibility-abilitytype-t.md) | 是 | 辅助应用的类型。 |
| stateType | [AbilityState](arkts-accessibility-accessibility-abilitystate-t.md) | 是 | 辅助应用的状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[AccessibilityAbilityInfo](arkts-accessibility-accessibility-accessibilityabilityinfo-i.md)&gt; | 返回辅助应用信息列表。 |

**示例**

```TypeScript
查询所有已安装的辅助应用。
```

```TypeScript
查询所有已启用的具有语音反馈的辅助应用。
```
