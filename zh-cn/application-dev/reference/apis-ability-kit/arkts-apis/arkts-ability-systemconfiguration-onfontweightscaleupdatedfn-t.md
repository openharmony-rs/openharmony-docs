# OnFontWeightScaleUpdatedFn

```TypeScript
type OnFontWeightScaleUpdatedFn = (fontWeightScale: double) => void
```

在注册系统环境变化的监听后，当系统字体粗细缩放比例变化时触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-systemConfiguration-type OnFontWeightScaleUpdatedFn = (fontWeightScale: double) => void--><!--Device-systemConfiguration-type OnFontWeightScaleUpdatedFn = (fontWeightScale: double) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontWeightScale | double | 是 | 变化后的系统字体粗细缩放比例。 |

