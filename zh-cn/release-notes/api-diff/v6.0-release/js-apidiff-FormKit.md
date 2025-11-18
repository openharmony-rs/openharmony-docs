| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：export default class FormEditExtensionAbility<br>差异内容：export default class FormEditExtensionAbility|api/@ohos.app.form.FormEditExtensionAbility.d.ts|
|新增API|NA|类名：FormEditExtensionAbility；<br>API声明：context: FormEditExtensionContext;<br>差异内容：context: FormEditExtensionContext;|api/@ohos.app.form.FormEditExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class FormEditExtensionContext<br>差异内容：export default class FormEditExtensionContext|api/application/FormEditExtensionContext.d.ts|
|新增API|NA|类名：FormEditExtensionContext；<br>API声明：startSecondPage(want: Want): Promise\<AbilityResult>;<br>差异内容：startSecondPage(want: Want): Promise\<AbilityResult>;|api/application/FormEditExtensionContext.d.ts|
|新增API|NA|类名：FormDimension；<br>API声明：DIMENSION_2_3 = 8<br>差异内容：DIMENSION_2_3 = 8|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormDimension；<br>API声明：DIMENSION_3_3 = 9<br>差异内容：DIMENSION_3_3 = 9|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function getPublishedFormInfoById(formId: string): Promise\<formInfo.FormInfo>;<br>差异内容：function getPublishedFormInfoById(formId: string): Promise\<formInfo.FormInfo>;|api/@ohos.app.form.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function getPublishedFormInfos(): Promise\<Array\<formInfo.FormInfo>>;<br>差异内容：function getPublishedFormInfos(): Promise\<Array\<formInfo.FormInfo>>;|api/@ohos.app.form.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function openFormManager(want: Want): void;<br>差异内容：function openFormManager(want: Want): void;|api/@ohos.app.form.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function openFormEditAbility(abilityName: string, formId: string, isMainPage?: boolean): void;<br>差异内容：function openFormEditAbility(abilityName: string, formId: string, isMainPage?: boolean): void;|api/@ohos.app.form.formProvider.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.form.FormEditExtensionAbility.d.ts<br>差异内容：FormKit|api/@ohos.app.form.FormEditExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\application\FormEditExtensionContext.d.ts<br>差异内容：FormKit|api/application/FormEditExtensionContext.d.ts|
