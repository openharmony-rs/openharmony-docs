# ArcListItemAttribute

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** ArcListItemAttribute extends [CommonMethod<ArcListItemAttribute>](CommonMethod<ArcListItemAttribute>)

**起始版本：** 18

<!--Device-unnamed-export declare class ArcListItemAttribute extends CommonMethod<ArcListItemAttribute>--><!--Device-unnamed-export declare class ArcListItemAttribute extends CommonMethod<ArcListItemAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcListItemAttribute, ArcList, ArcListItem, ArcListAttribute } from '@kit.ArkUI';
```

## autoScale

```TypeScript
autoScale(enable: Optional<boolean>): ArcListItemAttribute
```

用于设置ArcListItem是否支持自动缩放显示。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListItemAttribute-autoScale(enable: Optional<boolean>): ArcListItemAttribute--><!--Device-ArcListItemAttribute-autoScale(enable: Optional<boolean>): ArcListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | ArcListItem是否支持自动缩放显示，true表示支持自动缩放显示，false表示不支持自动缩放显示。<br/>默认值：true，支持自动缩放显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListItemAttribute](arkts-arkui-arkui-arclist-arclistitemattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## swipeAction

```TypeScript
swipeAction(options: Optional<SwipeActionOptions>): ArcListItemAttribute
```

用于设置ArcListItem的划出组件。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListItemAttribute-swipeAction(options: Optional<SwipeActionOptions>): ArcListItemAttribute--><!--Device-ArcListItemAttribute-swipeAction(options: Optional<SwipeActionOptions>): ArcListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;SwipeActionOptions&gt; | 是 | ArcListItem的划出组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListItemAttribute](arkts-arkui-arkui-arclist-arclistitemattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

