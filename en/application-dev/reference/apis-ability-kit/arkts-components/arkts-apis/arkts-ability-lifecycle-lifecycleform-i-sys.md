# LifecycleForm

interface of form lifecycle.

@interface LifecycleForm

**Since:** 7

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## Modules to Import

```TypeScript
```

## onShare

```TypeScript
onShare?(formId: string): { [key: string]: any }
```

Called when the system shares the form.

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Indicates the ID of the deleted form. |

**Return value:**

| Type | Description |
| --- | --- |
| object | Returns the wantParams object. |

## onShareForm

```TypeScript
onShareForm?(formId: string): Record<string, Object>
```

Called when the system shares the form. The ability of this function is same as onShare. If both are set, this function will be called.

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Indicates the ID of the deleted form. |

**Return value:**

| Type | Description |
| --- | --- |
| Record&lt;string, Object&gt; | Returns the wantParams object. |
