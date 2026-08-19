# CustomData（系统接口）

拉起模态页面时，开发者可通过[reloadInModal](arkts-ability-autofillextensioncontext-c-sys.md#reloadinmodal)接口将自定义数据传递给自动填充服 务，并可通过自动填充服务的 [onFillRequest](arkts-ability-app-ability-autofillextensionability-autofillextensionability-c-sys.md#onfillrequest)获取到该数据。

**起始版本：** 23

<!--Device-unnamed-export default interface CustomData--><!--Device-unnamed-export default interface CustomData-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## data

```TypeScript
data: Record<string, RecordData>
```

拉起模态页面时传递的自定义数据，该数据为Record类型。

**类型：** Record&lt;string, [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomData-data: Record<string, RecordData>--><!--Device-CustomData-data: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

