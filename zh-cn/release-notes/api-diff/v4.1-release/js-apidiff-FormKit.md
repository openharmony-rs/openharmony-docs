| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace formBindingData<br>差异内容：declare namespace formBindingData|api/@ohos.app.form.formBindingData.d.ts|
|新增API|NA|类名：formBindingData；<br>API声明：function createFormBindingData(obj?: Object \| string): FormBindingData;<br>差异内容：function createFormBindingData(obj?: Object \| string): FormBindingData;|api/@ohos.app.form.formBindingData.d.ts|
|新增API|NA|类名：formBindingData；<br>API声明：interface FormBindingData<br>差异内容：interface FormBindingData|api/@ohos.app.form.formBindingData.d.ts|
|新增API|NA|类名：FormBindingData；<br>API声明：data: Object;<br>差异内容：data: Object;|api/@ohos.app.form.formBindingData.d.ts|
|新增API|NA|类名：FormBindingData；<br>API声明：proxies?: Array\<ProxyData>;<br>差异内容：proxies?: Array\<ProxyData>;|api/@ohos.app.form.formBindingData.d.ts|
|新增API|NA|类名：formBindingData；<br>API声明：interface ProxyData<br>差异内容：interface ProxyData|api/@ohos.app.form.formBindingData.d.ts|
|新增API|NA|类名：ProxyData；<br>API声明：key: string;<br>差异内容：key: string;|api/@ohos.app.form.formBindingData.d.ts|
|新增API|NA|类名：ProxyData；<br>API声明：subscriberId?: string;<br>差异内容：subscriberId?: string;|api/@ohos.app.form.formBindingData.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class FormExtensionAbility<br>差异内容：export default class FormExtensionAbility|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增API|NA|类名：FormExtensionAbility；<br>API声明：context: FormExtensionContext;<br>差异内容：context: FormExtensionContext;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增API|NA|类名：FormExtensionAbility；<br>API声明：onAddForm(want: Want): formBindingData.FormBindingData;<br>差异内容：onAddForm(want: Want): formBindingData.FormBindingData;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增API|NA|类名：FormExtensionAbility；<br>API声明：onCastToNormalForm(formId: string): void;<br>差异内容：onCastToNormalForm(formId: string): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增API|NA|类名：FormExtensionAbility；<br>API声明：onUpdateForm(formId: string): void;<br>差异内容：onUpdateForm(formId: string): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增API|NA|类名：FormExtensionAbility；<br>API声明：onChangeFormVisibility(newStatus: Record\<string, number>): void;<br>差异内容：onChangeFormVisibility(newStatus: Record\<string, number>): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增API|NA|类名：FormExtensionAbility；<br>API声明：onFormEvent(formId: string, message: string): void;<br>差异内容：onFormEvent(formId: string, message: string): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增API|NA|类名：FormExtensionAbility；<br>API声明：onRemoveForm(formId: string): void;<br>差异内容：onRemoveForm(formId: string): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增API|NA|类名：FormExtensionAbility；<br>API声明：onConfigurationUpdate(newConfig: Configuration): void;<br>差异内容：onConfigurationUpdate(newConfig: Configuration): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增API|NA|类名：FormExtensionAbility；<br>API声明：onAcquireFormState?(want: Want): formInfo.FormState;<br>差异内容：onAcquireFormState?(want: Want): formInfo.FormState;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace formInfo<br>差异内容：declare namespace formInfo|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：interface FormInfo<br>差异内容：interface FormInfo|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：moduleName: string;<br>差异内容：moduleName: string;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：displayName: string;<br>差异内容：displayName: string;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：displayNameId: number;<br>差异内容：displayNameId: number;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：description: string;<br>差异内容：description: string;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：descriptionId: number;<br>差异内容：descriptionId: number;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：type: FormType;<br>差异内容：type: FormType;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：jsComponentName: string;<br>差异内容：jsComponentName: string;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：colorMode: ColorMode;<br>差异内容：colorMode: ColorMode;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：isDefault: boolean;<br>差异内容：isDefault: boolean;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：updateEnabled: boolean;<br>差异内容：updateEnabled: boolean;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：formVisibleNotify: boolean;<br>差异内容：formVisibleNotify: boolean;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：scheduledUpdateTime: string;<br>差异内容：scheduledUpdateTime: string;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：formConfigAbility: string;<br>差异内容：formConfigAbility: string;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：updateDuration: number;<br>差异内容：updateDuration: number;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：defaultDimension: number;<br>差异内容：defaultDimension: number;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：supportDimensions: Array\<number>;<br>差异内容：supportDimensions: Array\<number>;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：customizeData: Record\<string, string>;<br>差异内容：customizeData: Record\<string, string>;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：isDynamic: boolean;<br>差异内容：isDynamic: boolean;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：transparencyEnabled: boolean;<br>差异内容：transparencyEnabled: boolean;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：enum FormType<br>差异内容：enum FormType|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormType；<br>API声明：JS = 1<br>差异内容：JS = 1|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormType；<br>API声明：eTS = 2<br>差异内容：eTS = 2|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：enum ColorMode<br>差异内容：enum ColorMode|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：MODE_AUTO = -1<br>差异内容：MODE_AUTO = -1|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：MODE_DARK = 0<br>差异内容：MODE_DARK = 0|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：MODE_LIGHT = 1<br>差异内容：MODE_LIGHT = 1|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：interface FormStateInfo<br>差异内容：interface FormStateInfo|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormStateInfo；<br>API声明：formState: FormState;<br>差异内容：formState: FormState;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormStateInfo；<br>API声明：want: Want;<br>差异内容：want: Want;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：enum FormState<br>差异内容：enum FormState|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormState；<br>API声明：UNKNOWN = -1<br>差异内容：UNKNOWN = -1|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormState；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormState；<br>API声明：READY = 1<br>差异内容：READY = 1|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：enum FormParam<br>差异内容：enum FormParam|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：IDENTITY_KEY = 'ohos.extra.param.key.form_identity'<br>差异内容：IDENTITY_KEY = 'ohos.extra.param.key.form_identity'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：DIMENSION_KEY = 'ohos.extra.param.key.form_dimension'<br>差异内容：DIMENSION_KEY = 'ohos.extra.param.key.form_dimension'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：NAME_KEY = 'ohos.extra.param.key.form_name'<br>差异内容：NAME_KEY = 'ohos.extra.param.key.form_name'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：MODULE_NAME_KEY = 'ohos.extra.param.key.module_name'<br>差异内容：MODULE_NAME_KEY = 'ohos.extra.param.key.module_name'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：WIDTH_KEY = 'ohos.extra.param.key.form_width'<br>差异内容：WIDTH_KEY = 'ohos.extra.param.key.form_width'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：HEIGHT_KEY = 'ohos.extra.param.key.form_height'<br>差异内容：HEIGHT_KEY = 'ohos.extra.param.key.form_height'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：TEMPORARY_KEY = 'ohos.extra.param.key.form_temporary'<br>差异内容：TEMPORARY_KEY = 'ohos.extra.param.key.form_temporary'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：BUNDLE_NAME_KEY = 'ohos.extra.param.key.bundle_name'<br>差异内容：BUNDLE_NAME_KEY = 'ohos.extra.param.key.bundle_name'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：ABILITY_NAME_KEY = 'ohos.extra.param.key.ability_name'<br>差异内容：ABILITY_NAME_KEY = 'ohos.extra.param.key.ability_name'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：LAUNCH_REASON_KEY = 'ohos.extra.param.key.form_launch_reason'<br>差异内容：LAUNCH_REASON_KEY = 'ohos.extra.param.key.form_launch_reason'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：PARAM_FORM_CUSTOMIZE_KEY = 'ohos.extra.param.key.form_customize'<br>差异内容：PARAM_FORM_CUSTOMIZE_KEY = 'ohos.extra.param.key.form_customize'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：FORM_RENDERING_MODE_KEY = 'ohos.extra.param.key.form_rendering_mode'<br>差异内容：FORM_RENDERING_MODE_KEY = 'ohos.extra.param.key.form_rendering_mode'|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：interface FormInfoFilter<br>差异内容：interface FormInfoFilter|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormInfoFilter；<br>API声明：moduleName?: string;<br>差异内容：moduleName?: string;|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：enum FormDimension<br>差异内容：enum FormDimension|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormDimension；<br>API声明：Dimension_1_2 = 1<br>差异内容：Dimension_1_2 = 1|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormDimension；<br>API声明：Dimension_2_2<br>差异内容：Dimension_2_2|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormDimension；<br>API声明：Dimension_2_4<br>差异内容：Dimension_2_4|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormDimension；<br>API声明：Dimension_4_4<br>差异内容：Dimension_4_4|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormDimension；<br>API声明：Dimension_2_1<br>差异内容：Dimension_2_1|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：FormDimension；<br>API声明：DIMENSION_1_1<br>差异内容：DIMENSION_1_1|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：enum VisibilityType<br>差异内容：enum VisibilityType|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：VisibilityType；<br>API声明：UNKNOWN = 0<br>差异内容：UNKNOWN = 0|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：VisibilityType；<br>API声明：FORM_VISIBLE = 1<br>差异内容：FORM_VISIBLE = 1|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：VisibilityType；<br>API声明：FORM_INVISIBLE<br>差异内容：FORM_INVISIBLE|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：enum LaunchReason<br>差异内容：enum LaunchReason|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：LaunchReason；<br>API声明：FORM_DEFAULT = 1<br>差异内容：FORM_DEFAULT = 1|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：LaunchReason；<br>API声明：FORM_SHARE<br>差异内容：FORM_SHARE|api/@ohos.app.form.formInfo.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace formProvider<br>差异内容：declare namespace formProvider|api/@ohos.app.form.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback\<void>): void;<br>差异内容：function setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback\<void>): void;|api/@ohos.app.form.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function setFormNextRefreshTime(formId: string, minute: number): Promise\<void>;<br>差异内容：function setFormNextRefreshTime(formId: string, minute: number): Promise\<void>;|api/@ohos.app.form.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function updateForm(formId: string, formBindingData: formBindingData.FormBindingData, callback: AsyncCallback\<void>): void;<br>差异内容：function updateForm(formId: string, formBindingData: formBindingData.FormBindingData, callback: AsyncCallback\<void>): void;|api/@ohos.app.form.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise\<void>;<br>差异内容：function updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise\<void>;|api/@ohos.app.form.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function getFormsInfo(filter: formInfo.FormInfoFilter, callback: AsyncCallback\<Array\<formInfo.FormInfo>>): void;<br>差异内容：function getFormsInfo(filter: formInfo.FormInfoFilter, callback: AsyncCallback\<Array\<formInfo.FormInfo>>): void;|api/@ohos.app.form.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function getFormsInfo(callback: AsyncCallback\<Array\<formInfo.FormInfo>>): void;<br>差异内容：function getFormsInfo(callback: AsyncCallback\<Array\<formInfo.FormInfo>>): void;|api/@ohos.app.form.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function getFormsInfo(filter?: formInfo.FormInfoFilter): Promise\<Array\<formInfo.FormInfo>>;<br>差异内容：function getFormsInfo(filter?: formInfo.FormInfoFilter): Promise\<Array\<formInfo.FormInfo>>;|api/@ohos.app.form.formProvider.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace formBindingData<br>差异内容：declare namespace formBindingData|api/@ohos.application.formBindingData.d.ts|
|新增API|NA|类名：formBindingData；<br>API声明：function createFormBindingData(obj?: Object \| string): FormBindingData;<br>差异内容：function createFormBindingData(obj?: Object \| string): FormBindingData;|api/@ohos.application.formBindingData.d.ts|
|新增API|NA|类名：formBindingData；<br>API声明：interface FormBindingData<br>差异内容：interface FormBindingData|api/@ohos.application.formBindingData.d.ts|
|新增API|NA|类名：FormBindingData；<br>API声明：data: Object;<br>差异内容：data: Object;|api/@ohos.application.formBindingData.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace formError<br>差异内容：declare namespace formError|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：formError；<br>API声明：enum FormError<br>差异内容：enum FormError|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_COMMON = 1<br>差异内容：ERR_COMMON = 1|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_PERMISSION_DENY = 2<br>差异内容：ERR_PERMISSION_DENY = 2|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_GET_INFO_FAILED = 4<br>差异内容：ERR_GET_INFO_FAILED = 4|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_GET_BUNDLE_FAILED = 5<br>差异内容：ERR_GET_BUNDLE_FAILED = 5|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_GET_LAYOUT_FAILED = 6<br>差异内容：ERR_GET_LAYOUT_FAILED = 6|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_ADD_INVALID_PARAM = 7<br>差异内容：ERR_ADD_INVALID_PARAM = 7|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_CFG_NOT_MATCH_ID = 8<br>差异内容：ERR_CFG_NOT_MATCH_ID = 8|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_NOT_EXIST_ID = 9<br>差异内容：ERR_NOT_EXIST_ID = 9|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_BIND_PROVIDER_FAILED = 10<br>差异内容：ERR_BIND_PROVIDER_FAILED = 10|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_MAX_SYSTEM_FORMS = 11<br>差异内容：ERR_MAX_SYSTEM_FORMS = 11|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_MAX_INSTANCES_PER_FORM = 12<br>差异内容：ERR_MAX_INSTANCES_PER_FORM = 12|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_OPERATION_FORM_NOT_SELF = 13<br>差异内容：ERR_OPERATION_FORM_NOT_SELF = 13|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_PROVIDER_DEL_FAIL = 14<br>差异内容：ERR_PROVIDER_DEL_FAIL = 14|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_MAX_FORMS_PER_CLIENT = 15<br>差异内容：ERR_MAX_FORMS_PER_CLIENT = 15|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_MAX_SYSTEM_TEMP_FORMS = 16<br>差异内容：ERR_MAX_SYSTEM_TEMP_FORMS = 16|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_FORM_NO_SUCH_MODULE = 17<br>差异内容：ERR_FORM_NO_SUCH_MODULE = 17|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_FORM_NO_SUCH_ABILITY = 18<br>差异内容：ERR_FORM_NO_SUCH_ABILITY = 18|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_FORM_NO_SUCH_DIMENSION = 19<br>差异内容：ERR_FORM_NO_SUCH_DIMENSION = 19|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_FORM_FA_NOT_INSTALLED = 20<br>差异内容：ERR_FORM_FA_NOT_INSTALLED = 20|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_SYSTEM_RESPONSES_FAILED = 30<br>差异内容：ERR_SYSTEM_RESPONSES_FAILED = 30|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_FORM_DUPLICATE_ADDED = 31<br>差异内容：ERR_FORM_DUPLICATE_ADDED = 31|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：FormError；<br>API声明：ERR_IN_RECOVERY = 36<br>差异内容：ERR_IN_RECOVERY = 36|api/@ohos.application.formError.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace formInfo<br>差异内容：declare namespace formInfo|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：interface FormInfo<br>差异内容：interface FormInfo|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：moduleName: string;<br>差异内容：moduleName: string;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：description: string;<br>差异内容：description: string;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：type: FormType;<br>差异内容：type: FormType;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：jsComponentName: string;<br>差异内容：jsComponentName: string;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：colorMode: ColorMode;<br>差异内容：colorMode: ColorMode;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：isDefault: boolean;<br>差异内容：isDefault: boolean;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：updateEnabled: boolean;<br>差异内容：updateEnabled: boolean;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：formVisibleNotify: boolean;<br>差异内容：formVisibleNotify: boolean;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：relatedBundleName: string;<br>差异内容：relatedBundleName: string;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：scheduledUpdateTime: string;<br>差异内容：scheduledUpdateTime: string;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：formConfigAbility: string;<br>差异内容：formConfigAbility: string;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：updateDuration: number;<br>差异内容：updateDuration: number;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：defaultDimension: number;<br>差异内容：defaultDimension: number;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：supportDimensions: Array\<number>;<br>差异内容：supportDimensions: Array\<number>;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormInfo；<br>API声明：customizeData: {<br>            [key: string]: [<br>                value: string<br>            ];<br>        };<br>差异内容：customizeData: {<br>            [key: string]: [<br>                value: string<br>            ];<br>        };|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：enum FormType<br>差异内容：enum FormType|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormType；<br>API声明：JS = 1<br>差异内容：JS = 1|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：enum ColorMode<br>差异内容：enum ColorMode|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：MODE_AUTO = -1<br>差异内容：MODE_AUTO = -1|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：MODE_DARK = 0<br>差异内容：MODE_DARK = 0|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：MODE_LIGHT = 1<br>差异内容：MODE_LIGHT = 1|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：interface FormStateInfo<br>差异内容：interface FormStateInfo|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormStateInfo；<br>API声明：formState: FormState;<br>差异内容：formState: FormState;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormStateInfo；<br>API声明：want: Want;<br>差异内容：want: Want;|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：enum FormState<br>差异内容：enum FormState|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormState；<br>API声明：UNKNOWN = -1<br>差异内容：UNKNOWN = -1|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormState；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormState；<br>API声明：READY = 1<br>差异内容：READY = 1|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：formInfo；<br>API声明：enum FormParam<br>差异内容：enum FormParam|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：DIMENSION_KEY = 'ohos.extra.param.key.form_dimension'<br>差异内容：DIMENSION_KEY = 'ohos.extra.param.key.form_dimension'|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：NAME_KEY = 'ohos.extra.param.key.form_name'<br>差异内容：NAME_KEY = 'ohos.extra.param.key.form_name'|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：MODULE_NAME_KEY = 'ohos.extra.param.key.module_name'<br>差异内容：MODULE_NAME_KEY = 'ohos.extra.param.key.module_name'|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：WIDTH_KEY = 'ohos.extra.param.key.form_width'<br>差异内容：WIDTH_KEY = 'ohos.extra.param.key.form_width'|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：HEIGHT_KEY = 'ohos.extra.param.key.form_height'<br>差异内容：HEIGHT_KEY = 'ohos.extra.param.key.form_height'|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：FormParam；<br>API声明：TEMPORARY_KEY = 'ohos.extra.param.key.form_temporary'<br>差异内容：TEMPORARY_KEY = 'ohos.extra.param.key.form_temporary'|api/@ohos.application.formInfo.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace formProvider<br>差异内容：declare namespace formProvider|api/@ohos.application.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback\<void>): void;<br>差异内容：function setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback\<void>): void;|api/@ohos.application.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function setFormNextRefreshTime(formId: string, minute: number): Promise\<void>;<br>差异内容：function setFormNextRefreshTime(formId: string, minute: number): Promise\<void>;|api/@ohos.application.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function updateForm(formId: string, formBindingData: formBindingData.FormBindingData, callback: AsyncCallback\<void>): void;<br>差异内容：function updateForm(formId: string, formBindingData: formBindingData.FormBindingData, callback: AsyncCallback\<void>): void;|api/@ohos.application.formProvider.d.ts|
|新增API|NA|类名：formProvider；<br>API声明：function updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise\<void>;<br>差异内容：function updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise\<void>;|api/@ohos.application.formProvider.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.form.formBindingData.d.ts<br>差异内容：FormKit|api/@ohos.app.form.formBindingData.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.form.FormExtensionAbility.d.ts<br>差异内容：FormKit|api/@ohos.app.form.FormExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.form.formInfo.d.ts<br>差异内容：FormKit|api/@ohos.app.form.formInfo.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.form.formProvider.d.ts<br>差异内容：FormKit|api/@ohos.app.form.formProvider.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.application.formBindingData.d.ts<br>差异内容：FormKit|api/@ohos.application.formBindingData.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.application.formError.d.ts<br>差异内容：FormKit|api/@ohos.application.formError.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.application.formInfo.d.ts<br>差异内容：FormKit|api/@ohos.application.formInfo.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.application.formProvider.d.ts<br>差异内容：FormKit|api/@ohos.application.formProvider.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.FormKit.d.ts<br>差异内容：FormKit|kits/@kit.FormKit.d.ts|
