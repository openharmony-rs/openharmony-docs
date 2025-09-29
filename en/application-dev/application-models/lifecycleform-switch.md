# LifecycleForm Switching

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

  | API in the [FA Model](ability-terminology.md#fa-model)| Corresponding .d.ts File in the [Stage Model](ability-terminology.md#stage-model)| Corresponding API in the Stage Model| 
| -------- | -------- | -------- |
| onCreate?(want:&nbsp;Want):&nbsp;formBindingData.FormBindingData; | \@ohos.app.form.FormExtensionAbility.d.ts | [onAddForm(want:&nbsp;Want):&nbsp;formBindingData.FormBindingData;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonaddform) |
| onCastToNormal?(formId:&nbsp;string):&nbsp;void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onCastToNormalForm(formId:&nbsp;string):&nbsp;void;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityoncasttonormalform) |
| onUpdate?(formId:&nbsp;string):&nbsp;void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onUpdateForm(formId:&nbsp;string):&nbsp;void;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonupdateform) |
| onVisibilityChange?(newStatus:&nbsp;Record&lt;string,&nbsp;number&gt;):&nbsp;void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onChangeFormVisibility(newStatus:&nbsp;Record&lt;string,&nbsp;number&gt;):&nbsp;void;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonchangeformvisibility) |
| onEvent?(formId:&nbsp;string,&nbsp;message:&nbsp;string):&nbsp;void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onFormEvent(formId:&nbsp;string,&nbsp;message:&nbsp;string):&nbsp;void;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonformevent) |
| onDestroy?(formId:&nbsp;string):&nbsp;void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onRemoveForm(formId:&nbsp;string):&nbsp;void;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonremoveform) |
| onAcquireFormState?(want:&nbsp;Want):&nbsp;formInfo.FormState; | \@ohos.app.form.FormExtensionAbility.d.ts | [onAcquireFormState?(want:&nbsp;Want):&nbsp;formInfo.FormState;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonacquireformstate) |
| onShareForm?(formId:&nbsp;string):&nbsp;Record&lt;string,&nbsp;Object&gt;; | \@ohos.app.form.FormExtensionAbility.d.ts | [onShareForm?(formId:&nbsp;string):&nbsp;Record&lt;string,&nbsp;Object&gt;;](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility-sys.md#onshareform) |
