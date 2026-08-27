# ArcListItemAttribute

除支持通用属性外，还支持以下属性：

**继承/实现关系：** ArcListItemAttribute extends CommonMethod<ArcListItemAttribute>

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## autoScale

```TypeScript
autoScale(enable: Optional<boolean>): ArcListItemAttribute
```

用于设置ArcListItem是否自动缩放。开启后，ArcListItem会根据其在弧形列表中的位置自动调整显示尺寸。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | ArcListItem是否支持自动缩放显示，true表示支持，false表示不支持。 默认值：true，支持自动缩放显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListItemAttribute](arkts-arkui-arkui-arclist-arclistitemattribute-c.md) |  |

## swipeAction

```TypeScript
swipeAction(options: Optional<SwipeActionOptions>): ArcListItemAttribute
```

用于设置ArcListItem的划出操作。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[SwipeActionOptions](../arkts-components/arkts-arkui-swipeactionoptions-i.md)&gt; | 是 | ArcListItem划出操作的配置选项，具体配置请参考SwipeActionOptions。未设置时，不配置划出操作。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListItemAttribute](arkts-arkui-arkui-arclist-arclistitemattribute-c.md) |  |
