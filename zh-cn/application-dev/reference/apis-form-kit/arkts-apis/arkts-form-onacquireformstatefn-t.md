# OnAcquireFormStateFn

```TypeScript
type OnAcquireFormStateFn = (want: Want) => formInfo.FormState
```

Called to return a FormState object. &lt;p&gt;You must override this callback if you want this ability to return the actual form state. Otherwise, this method returns DEFAULT by default.&lt;/p&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type OnAcquireFormStateFn = (want: Want) => formInfo.FormState--><!--Device-unnamed-type OnAcquireFormStateFn = (want: Want) => formInfo.FormState-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Indicates the description of the form for which the FormState is obtained. The description covers the bundle name, ability name, module name, form name, and form dimensions. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| formInfo.FormState | Returns the { |

