| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|函数变更|类名：FormExtensionAbility；<br>API声明：onUpdateForm(formId: string): void;<br>差异内容：NA|类名：FormExtensionAbility；<br>API声明：onUpdateForm(formId: string, wantParams?: Record\<string, Object>): void;<br>差异内容：wantParams?: Record\<string, Object>|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增API|NA|类名：FormExtensionAbility；<br>API声明：onStop?(): void;<br>差异内容：onStop?(): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：supportedShapes: Array\<number>;<br>差异内容：supportedShapes: Array\<number>;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：FORM_LOCATION_KEY = 'ohos.extra.param.key.form_location'<br>差异内容：FORM_LOCATION_KEY = 'ohos.extra.param.key.form_location'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：HOST_BG_INVERSE_COLOR_KEY = 'ohos.extra.param.key.host_bg_inverse_color'<br>差异内容：HOST_BG_INVERSE_COLOR_KEY = 'ohos.extra.param.key.host_bg_inverse_color'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：FORM_PERMISSION_NAME_KEY = 'ohos.extra.param.key.permission_name'<br>差异内容：FORM_PERMISSION_NAME_KEY = 'ohos.extra.param.key.permission_name'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：FORM_PERMISSION_GRANTED_KEY = 'ohos.extra.param.key.permission_granted'<br>差异内容：FORM_PERMISSION_GRANTED_KEY = 'ohos.extra.param.key.permission_granted'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormDimension；<br>API声明：DIMENSION_6_4<br>差异内容：DIMENSION_6_4|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：enum FormShape<br>差异内容：enum FormShape|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormShape；<br>API声明：RECT = 1<br>差异内容：RECT = 1|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormShape；<br>API声明：CIRCLE<br>差异内容：CIRCLE|api/@ohos.app.form.formInfo.d.ts|
|新增kit|类名：global；<br>API声明：api\application\FormExtensionContext.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\application\FormExtensionContext.d.ts<br>差异内容：FormKit|api/application/FormExtensionContext.d.ts|
|API从不支持元服务到支持元服务|类名：FormParam；<br>API声明：FORM_RENDERING_MODE_KEY = 'ohos.extra.param.key.form_rendering_mode'<br>差异内容：NA|类名：FormParam；<br>API声明：FORM_RENDERING_MODE_KEY = 'ohos.extra.param.key.form_rendering_mode'<br>差异内容：atomicservice|api/@ohos.app.form.formInfo.d.ts|
