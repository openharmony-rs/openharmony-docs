# PublishFormCrossBundleControlCallback（系统接口）

```TypeScript
type PublishFormCrossBundleControlCallback = (info: PublishFormCrossBundleInfo) => boolean
```

跨应用加卡管控回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formInfo-type PublishFormCrossBundleControlCallback = (info: PublishFormCrossBundleInfo) => boolean--><!--Device-formInfo-type PublishFormCrossBundleControlCallback = (info: PublishFormCrossBundleInfo) => boolean-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [PublishFormCrossBundleInfo](arkts-form-forminfo-publishformcrossbundleinfo-i-sys.md) | 是 | 跨应用加卡管控信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 跨应用加卡管控结果。<br/>- true：表示管控通过。<br/>- false：表示管控未通过。 |

