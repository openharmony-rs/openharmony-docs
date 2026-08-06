# CustomData（系统接口）

拉起模态页面时，开发者可通过[reloadInModal]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口将自定义数据传递给自动填充服 务，并可通过自动填充服务的 [onFillRequest]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_获取到该数据。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export default interface CustomData--><!--Device-unnamed-export default interface CustomData-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## data

```TypeScript
data: Record<string, Object>
```

拉起模态页面时传递的自定义数据，该数据为Record类型。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomData-data: Record<string, Object>--><!--Device-CustomData-data: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

