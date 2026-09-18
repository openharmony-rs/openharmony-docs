# LifecycleForm

interface of form lifecycle.

@interface LifecycleForm

**Since:** 7

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## Modules to Import

```TypeScript
```

## onAcquireFormState

```TypeScript
onAcquireFormState?(want: Want): formInfo.FormState
```

Called to return a FormState object. <p>You must override this callback if you want this ability to return the actual form state. Otherwise, this method returns DEFAULT by default.</p>

**Since:** 8

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Indicates the description of the form for which the FormState is obtained. The description covers the bundle name, ability name, module name, form name, form dimensions. |

**Return value:**

| Type | Description |
| --- | --- |
| [formInfo.FormState](../../apis-form-kit/arkts-apis/arkts-form-forminfo-formstate-e.md) | Returns the FormState object. |

## onCastToNormal

```TypeScript
onCastToNormal?(formId: string): void
```

Called when the form provider is notified that a temporary form is successfully converted to a normal form.

**Since:** 8

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Indicates the ID of the form. |

## onCreate

```TypeScript
onCreate?(want: Want): formBindingData.FormBindingData
```

Called to return a FormBindingData object.

**Since:** 8

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Indicates the detailed information for creating a FormBindingData. The `Want` object must include the form ID, form name, and grid style of the form, which can be obtained from IDENTITY_KEY, NAME_KEY, and DIMENSION_KEY, respectively. Such form information must be managed as persistent data for further form acquisition, update, and deletion. |

**Return value:**

| Type | Description |
| --- | --- |
| [formBindingData.FormBindingData](../../apis-form-kit/arkts-apis/arkts-form-formbindingdata-formbindingdata-depr-i.md) | Returns the created FormBindingData object. |

## onDestroy

```TypeScript
onDestroy?(formId: string): void
```

Called to notify the form provider that a specified form has been deleted. Override this method if you want your application, as the form provider, to be notified of form deletion.

**Since:** 8

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Indicates the ID of the deleted form. |

## onEvent

```TypeScript
onEvent?(formId: string, message: string): void
```

Called when a specified message event defined by the form provider is triggered. This method is valid only for JS forms.

**Since:** 8

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Indicates the ID of the form on which the message event is triggered, which is provided by the client to the form provider. |
| message | string | Yes | Indicates the value of the `params` field of the message event. This parameter is used to identify the specific component on which the event is triggered. |

## onUpdate

```TypeScript
onUpdate?(formId: string): void
```

Called to notify the form provider to update a specified form.

**Since:** 8

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Indicates the ID of the form to update. |

## onVisibilityChange

```TypeScript
onVisibilityChange?(newStatus: Record<string, number>): void
```

Called when the form provider receives form events from the system.

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newStatus | Record&lt;string, number&gt; | Yes | Indicates the form events occurred. The key in the `Map` object indicates form ID,and the value indicates the event type, which can be either [FORM_VISIBLE](../../apis-form-kit/arkts-apis/arkts-form-forminfo-visibilitytype-e.md#form_visible) or [FORM_INVISIBLE](../../apis-form-kit/arkts-apis/arkts-form-forminfo-visibilitytype-e.md#form_invisible). [FORM_VISIBLE](../../apis-form-kit/arkts-apis/arkts-form-forminfo-visibilitytype-e.md#form_visible) means that the form becomes visible, and [FORM_INVISIBLE](../../apis-form-kit/arkts-apis/arkts-form-forminfo-visibilitytype-e.md#form_invisible) means that the form becomes invisible. |
