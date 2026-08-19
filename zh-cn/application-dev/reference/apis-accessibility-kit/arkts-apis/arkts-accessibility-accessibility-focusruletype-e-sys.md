# FocusRuleType（系统接口）

表示聚焦规则类型的枚举。

**起始版本：** 26.0.0

<!--Device-unnamed-export enum FocusRuleType--><!--Device-unnamed-export enum FocusRuleType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## DEFAULT

```TypeScript
DEFAULT = 1
```

表示默认聚焦类型，不按特定类型过滤，所有节点均可作为聚焦目标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FocusRuleType-DEFAULT = 1--><!--Device-FocusRuleType-DEFAULT = 1-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## FOCUS_BY_LINK

```TypeScript
FOCUS_BY_LINK = 2
```

表示按链接类型聚焦，例如网页上可点击跳转的元素。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FocusRuleType-FOCUS_BY_LINK = 2--><!--Device-FocusRuleType-FOCUS_BY_LINK = 2-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## FOCUS_BY_TITLE

```TypeScript
FOCUS_BY_TITLE = 3
```

表示按标题类型聚焦，例如页面中的各级标题元素。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FocusRuleType-FOCUS_BY_TITLE = 3--><!--Device-FocusRuleType-FOCUS_BY_TITLE = 3-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

