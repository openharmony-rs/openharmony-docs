# GetWantParamsCallback（系统接口）

```TypeScript
type GetWantParamsCallback = (formInfo: Array<formInfo.FormInfo>) => Array<Record<string, Object>>
```

获取卡片参数回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formInfo-type GetWantParamsCallback = (formInfo: Array<formInfo.FormInfo>) => Array<Record<string, Object>>--><!--Device-formInfo-type GetWantParamsCallback = (formInfo: Array<formInfo.FormInfo>) => Array<Record<string, Object>>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formInfo | Array&lt;[formInfo.FormInfo](arkts-form-forminfo-forminfo-i.md)&gt; | 是 | 卡片信息列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Record&lt;string, Object&gt;&gt; | 返回卡片参数列表，与输入的卡片信息列表一一对应。 |

