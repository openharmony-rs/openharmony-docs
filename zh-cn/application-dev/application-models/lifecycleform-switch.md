# LifecycleForm接口切换

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

| [FA模型](ability-terminology.md#fa模型)接口 | [Stage模型](ability-terminology.md#stage模型)接口对应d.ts文件 | Stage模型对应接口 | 
| -------- | -------- | -------- |
| onCreate?(want:&nbsp;Want):&nbsp;formBindingData.FormBindingData; | \@ohos.app.form.FormExtensionAbility.d.ts | [onAddForm(want:&nbsp;Want):&nbsp;formBindingData.FormBindingData;](../reference/apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md#onaddform) |
| onCastToNormal?(formId:&nbsp;string):&nbsp;void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onCastToNormalForm(formId:&nbsp;string):&nbsp;void;](../reference/apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md#oncasttonormalform) |
| onUpdate?(formId:&nbsp;string):&nbsp;void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onUpdateForm(formId:&nbsp;string):&nbsp;void;](../reference/apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md#onupdateform) |
| onVisibilityChange?(newStatus:&nbsp;Record&lt;string,&nbsp;number&gt;):&nbsp;void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onChangeFormVisibility(newStatus:&nbsp;Record&lt;string,&nbsp;number&gt;):&nbsp;void;](../reference/apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md#onchangeformvisibility) |
| onEvent?(formId:&nbsp;string,&nbsp;message:&nbsp;string):&nbsp;void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onFormEvent(formId:&nbsp;string,&nbsp;message:&nbsp;string):&nbsp;void;](../reference/apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md#onformevent) |
| onDestroy?(formId:&nbsp;string):&nbsp;void; | \@ohos.app.form.FormExtensionAbility.d.ts | [onRemoveForm(formId:&nbsp;string):&nbsp;void;](../reference/apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md#onremoveform) |
| onAcquireFormState?(want:&nbsp;Want):&nbsp;formInfo.FormState; | \@ohos.app.form.FormExtensionAbility.d.ts | [onAcquireFormState?(want:&nbsp;Want):&nbsp;formInfo.FormState;](../reference/apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md#onacquireformstate) |
|<!--DelRow--> onShareForm?(formId:&nbsp;string):&nbsp;Record&lt;string,&nbsp;Object&gt;; | \@ohos.app.form.FormExtensionAbility.d.ts | [onShareForm?(formId:&nbsp;string):&nbsp;Record&lt;string,&nbsp;Object&gt;;](../reference/apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c-sys.md#onshareform) |
