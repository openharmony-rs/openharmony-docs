# LifecycleForm Switching


  | API in the FA Model| Corresponding .d.ts File in the Stage Model| Corresponding API in the Stage Model| 
| -------- | -------- | -------- |
| onCreate?(want: Want): formBindingData.FormBindingData; | \@ohos.app.form.FormExtensionAbility.d.ts | [onAddForm(want: Want): formBindingData.FormBindingData;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonaddform) |
| onCastToNormal?(formId: string): void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onCastToNormalForm(formId: string): void;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityoncasttonormalform) |
| onUpdate?(formId: string): void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onUpdateForm(formId: string): void;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonupdateform) |
| onVisibilityChange?(newStatus: Record&lt;string, number&gt;): void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onChangeFormVisibility(newStatus: Record&lt;string, number&gt;): void;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonchangeformvisibility) |
| onEvent?(formId: string, message: string): void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onFormEvent(formId: string, message: string): void;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonformevent) |
| onDestroy?(formId: string): void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onRemoveForm(formId: string): void;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonremoveform) |
| onAcquireFormState?(want: Want): formInfo.FormState; | \@ohos.app.form.FormExtensionAbility.d.ts | [onAcquireFormState?(want: Want): formInfo.FormState;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonacquireformstate) |
| onShareForm?(formId: string): Record&lt;string, Object&gt;; | \@ohos.app.form.FormExtensionAbility.d.ts | [onShareForm?(formId: string): Record&lt;string, Object&gt;;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility-sys.md#onshareform) |
