# CustomData (System API)

```TypeScript
export default interface CustomData
```

When starting a modal page, developers can transfer custom data to the auto-fill service through the [reloadInModal](arkts-ability-autofillextensioncontext-c-sys.md#reloadinmodal) API, and obtain the data through the [onFillRequest](arkts-ability-app-ability-autofillextensionability-autofillextensionability-c-sys.md#onfillrequest) of the auto-fill service.

**Since:** 13

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## data

```TypeScript
data: Record<string, Object>
```

Custom data transferred for starting the modal page. The data is of the Record type.

**Type:** Record&lt;string, Object&gt;

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.
