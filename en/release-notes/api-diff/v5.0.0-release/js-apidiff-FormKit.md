| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|Function change|Class name: FormExtensionAbility;<br>API declaration: onUpdateForm(formId: string): void;<br>Differences: NA|Class name: FormExtensionAbility;<br>API declaration: onUpdateForm(formId: string, wantParams?: Record\<string, Object>): void;<br>Differences: wantParams?: Record\<string, Object>|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API|NA|Class name: FormExtensionAbility;<br>API declaration: onStop?(): void;<br>Differences: onStop?(): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: supportedShapes: Array\<number>;<br>Differences: supportedShapes: Array\<number>;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: FORM_LOCATION_KEY = 'ohos.extra.param.key.form_location'<br>Differences: FORM_LOCATION_KEY = 'ohos.extra.param.key.form_location'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: HOST_BG_INVERSE_COLOR_KEY = 'ohos.extra.param.key.host_bg_inverse_color'<br>Differences: HOST_BG_INVERSE_COLOR_KEY = 'ohos.extra.param.key.host_bg_inverse_color'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: FORM_PERMISSION_NAME_KEY = 'ohos.extra.param.key.permission_name'<br>Differences: FORM_PERMISSION_NAME_KEY = 'ohos.extra.param.key.permission_name'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: FORM_PERMISSION_GRANTED_KEY = 'ohos.extra.param.key.permission_granted'<br>Differences: FORM_PERMISSION_GRANTED_KEY = 'ohos.extra.param.key.permission_granted'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormDimension;<br>API declaration: DIMENSION_6_4<br>Differences: DIMENSION_6_4|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: enum FormShape<br>Differences: enum FormShape|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormShape;<br>API declaration: RECT = 1<br>Differences: RECT = 1|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormShape;<br>API declaration: CIRCLE<br>Differences: CIRCLE|api/@ohos.app.form.formInfo.d.ts|
|New Kit|Class name: global;<br>API declaration: api\application\FormExtensionContext.d.ts<br>Differences: NA|Class name: global;<br>API declaration: api\application\FormExtensionContext.d.ts<br>Differences: FormKit|api/application/FormExtensionContext.d.ts|
|New support for atomic services|Class name: FormParam;<br>API declaration: FORM_RENDERING_MODE_KEY = 'ohos.extra.param.key.form_rendering_mode'<br>Differences: NA|Class name: FormParam;<br>API declaration: FORM_RENDERING_MODE_KEY = 'ohos.extra.param.key.form_rendering_mode'<br>Differences: atomicservice|api/@ohos.app.form.formInfo.d.ts|
