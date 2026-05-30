| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace formBindingData<br>Differences: declare namespace formBindingData|api/@ohos.app.form.formBindingData.d.ts|
|New API|NA|Class name: formBindingData;<br>API declaration: function createFormBindingData(obj?: Object \| string): FormBindingData;<br>Differences: function createFormBindingData(obj?: Object \| string): FormBindingData;|api/@ohos.app.form.formBindingData.d.ts|
|New API|NA|Class name: formBindingData;<br>API declaration: interface FormBindingData<br>Differences: interface FormBindingData|api/@ohos.app.form.formBindingData.d.ts|
|New API|NA|Class name: FormBindingData;<br>API declaration: data: Object;<br>Differences: data: Object;|api/@ohos.app.form.formBindingData.d.ts|
|New API|NA|Class name: FormBindingData;<br>API declaration: proxies?: Array\<ProxyData>;<br>Differences: proxies?: Array\<ProxyData>;|api/@ohos.app.form.formBindingData.d.ts|
|New API|NA|Class name: formBindingData;<br>API declaration: interface ProxyData<br>Differences: interface ProxyData|api/@ohos.app.form.formBindingData.d.ts|
|New API|NA|Class name: ProxyData;<br>API declaration: key: string;<br>Differences: key: string;|api/@ohos.app.form.formBindingData.d.ts|
|New API|NA|Class name: ProxyData;<br>API declaration: subscriberId?: string;<br>Differences: subscriberId?: string;|api/@ohos.app.form.formBindingData.d.ts|
|New API|NA|Class name: global;<br>API declaration: export default class FormExtensionAbility<br>Differences: export default class FormExtensionAbility|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API|NA|Class name: FormExtensionAbility;<br>API declaration: context: FormExtensionContext;<br>Differences: context: FormExtensionContext;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API|NA|Class name: FormExtensionAbility;<br>API declaration: onAddForm(want: Want): formBindingData.FormBindingData;<br>Differences: onAddForm(want: Want): formBindingData.FormBindingData;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API|NA|Class name: FormExtensionAbility;<br>API declaration: onCastToNormalForm(formId: string): void;<br>Differences: onCastToNormalForm(formId: string): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API|NA|Class name: FormExtensionAbility;<br>API declaration: onUpdateForm(formId: string): void;<br>Differences: onUpdateForm(formId: string): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API|NA|Class name: FormExtensionAbility;<br>API declaration: onChangeFormVisibility(newStatus: Record\<string, number>): void;<br>Differences: onChangeFormVisibility(newStatus: Record\<string, number>): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API|NA|Class name: FormExtensionAbility;<br>API declaration: onFormEvent(formId: string, message: string): void;<br>Differences: onFormEvent(formId: string, message: string): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API|NA|Class name: FormExtensionAbility;<br>API declaration: onRemoveForm(formId: string): void;<br>Differences: onRemoveForm(formId: string): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API|NA|Class name: FormExtensionAbility;<br>API declaration: onConfigurationUpdate(newConfig: Configuration): void;<br>Differences: onConfigurationUpdate(newConfig: Configuration): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API|NA|Class name: FormExtensionAbility;<br>API declaration: onAcquireFormState?(want: Want): formInfo.FormState;<br>Differences: onAcquireFormState?(want: Want): formInfo.FormState;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace formInfo<br>Differences: declare namespace formInfo|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: interface FormInfo<br>Differences: interface FormInfo|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: bundleName: string;<br>Differences: bundleName: string;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: moduleName: string;<br>Differences: moduleName: string;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: abilityName: string;<br>Differences: abilityName: string;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: displayName: string;<br>Differences: displayName: string;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: displayNameId: number;<br>Differences: displayNameId: number;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: description: string;<br>Differences: description: string;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: descriptionId: number;<br>Differences: descriptionId: number;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: type: FormType;<br>Differences: type: FormType;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: jsComponentName: string;<br>Differences: jsComponentName: string;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: colorMode: ColorMode;<br>Differences: colorMode: ColorMode;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: isDefault: boolean;<br>Differences: isDefault: boolean;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: updateEnabled: boolean;<br>Differences: updateEnabled: boolean;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: formVisibleNotify: boolean;<br>Differences: formVisibleNotify: boolean;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: scheduledUpdateTime: string;<br>Differences: scheduledUpdateTime: string;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: formConfigAbility: string;<br>Differences: formConfigAbility: string;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: updateDuration: number;<br>Differences: updateDuration: number;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: defaultDimension: number;<br>Differences: defaultDimension: number;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: supportDimensions: Array\<number>;<br>Differences: supportDimensions: Array\<number>;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: customizeData: Record\<string, string>;<br>Differences: customizeData: Record\<string, string>;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: isDynamic: boolean;<br>Differences: isDynamic: boolean;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: transparencyEnabled: boolean;<br>Differences: transparencyEnabled: boolean;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: enum FormType<br>Differences: enum FormType|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormType;<br>API declaration: JS = 1<br>Differences: JS = 1|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormType;<br>API declaration: eTS = 2<br>Differences: eTS = 2|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: enum ColorMode<br>Differences: enum ColorMode|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: ColorMode;<br>API declaration: MODE_AUTO = -1<br>Differences: MODE_AUTO = -1|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: ColorMode;<br>API declaration: MODE_DARK = 0<br>Differences: MODE_DARK = 0|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: ColorMode;<br>API declaration: MODE_LIGHT = 1<br>Differences: MODE_LIGHT = 1|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: interface FormStateInfo<br>Differences: interface FormStateInfo|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormStateInfo;<br>API declaration: formState: FormState;<br>Differences: formState: FormState;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormStateInfo;<br>API declaration: want: Want;<br>Differences: want: Want;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: enum FormState<br>Differences: enum FormState|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormState;<br>API declaration: UNKNOWN = -1<br>Differences: UNKNOWN = -1|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormState;<br>API declaration: DEFAULT = 0<br>Differences: DEFAULT = 0|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormState;<br>API declaration: READY = 1<br>Differences: READY = 1|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: enum FormParam<br>Differences: enum FormParam|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: IDENTITY_KEY = 'ohos.extra.param.key.form_identity'<br>Differences: IDENTITY_KEY = 'ohos.extra.param.key.form_identity'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: DIMENSION_KEY = 'ohos.extra.param.key.form_dimension'<br>Differences: DIMENSION_KEY = 'ohos.extra.param.key.form_dimension'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: NAME_KEY = 'ohos.extra.param.key.form_name'<br>Differences: NAME_KEY = 'ohos.extra.param.key.form_name'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: MODULE_NAME_KEY = 'ohos.extra.param.key.module_name'<br>Differences: MODULE_NAME_KEY = 'ohos.extra.param.key.module_name'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: WIDTH_KEY = 'ohos.extra.param.key.form_width'<br>Differences: WIDTH_KEY = 'ohos.extra.param.key.form_width'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: HEIGHT_KEY = 'ohos.extra.param.key.form_height'<br>Differences: HEIGHT_KEY = 'ohos.extra.param.key.form_height'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: TEMPORARY_KEY = 'ohos.extra.param.key.form_temporary'<br>Differences: TEMPORARY_KEY = 'ohos.extra.param.key.form_temporary'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: BUNDLE_NAME_KEY = 'ohos.extra.param.key.bundle_name'<br>Differences: BUNDLE_NAME_KEY = 'ohos.extra.param.key.bundle_name'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: ABILITY_NAME_KEY = 'ohos.extra.param.key.ability_name'<br>Differences: ABILITY_NAME_KEY = 'ohos.extra.param.key.ability_name'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: LAUNCH_REASON_KEY = 'ohos.extra.param.key.form_launch_reason'<br>Differences: LAUNCH_REASON_KEY = 'ohos.extra.param.key.form_launch_reason'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: PARAM_FORM_CUSTOMIZE_KEY = 'ohos.extra.param.key.form_customize'<br>Differences: PARAM_FORM_CUSTOMIZE_KEY = 'ohos.extra.param.key.form_customize'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: FORM_RENDERING_MODE_KEY = 'ohos.extra.param.key.form_rendering_mode'<br>Differences: FORM_RENDERING_MODE_KEY = 'ohos.extra.param.key.form_rendering_mode'|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: interface FormInfoFilter<br>Differences: interface FormInfoFilter|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormInfoFilter;<br>API declaration: moduleName?: string;<br>Differences: moduleName?: string;|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: enum FormDimension<br>Differences: enum FormDimension|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormDimension;<br>API declaration: Dimension_1_2 = 1<br>Differences: Dimension_1_2 = 1|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormDimension;<br>API declaration: Dimension_2_2<br>Differences: Dimension_2_2|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormDimension;<br>API declaration: Dimension_2_4<br>Differences: Dimension_2_4|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormDimension;<br>API declaration: Dimension_4_4<br>Differences: Dimension_4_4|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormDimension;<br>API declaration: Dimension_2_1<br>Differences: Dimension_2_1|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: FormDimension;<br>API declaration: DIMENSION_1_1<br>Differences: DIMENSION_1_1|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: enum VisibilityType<br>Differences: enum VisibilityType|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: VisibilityType;<br>API declaration: UNKNOWN = 0<br>Differences: UNKNOWN = 0|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: VisibilityType;<br>API declaration: FORM_VISIBLE = 1<br>Differences: FORM_VISIBLE = 1|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: VisibilityType;<br>API declaration: FORM_INVISIBLE<br>Differences: FORM_INVISIBLE|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: enum LaunchReason<br>Differences: enum LaunchReason|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: LaunchReason;<br>API declaration: FORM_DEFAULT = 1<br>Differences: FORM_DEFAULT = 1|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: LaunchReason;<br>API declaration: FORM_SHARE<br>Differences: FORM_SHARE|api/@ohos.app.form.formInfo.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace formProvider<br>Differences: declare namespace formProvider|api/@ohos.app.form.formProvider.d.ts|
|New API|NA|Class name: formProvider;<br>API declaration: function setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback\<void>): void;<br>Differences: function setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback\<void>): void;|api/@ohos.app.form.formProvider.d.ts|
|New API|NA|Class name: formProvider;<br>API declaration: function setFormNextRefreshTime(formId: string, minute: number): Promise\<void>;<br>Differences: function setFormNextRefreshTime(formId: string, minute: number): Promise\<void>;|api/@ohos.app.form.formProvider.d.ts|
|New API|NA|Class name: formProvider;<br>API declaration: function updateForm(formId: string, formBindingData: formBindingData.FormBindingData, callback: AsyncCallback\<void>): void;<br>Differences: function updateForm(formId: string, formBindingData: formBindingData.FormBindingData, callback: AsyncCallback\<void>): void;|api/@ohos.app.form.formProvider.d.ts|
|New API|NA|Class name: formProvider;<br>API declaration: function updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise\<void>;<br>Differences: function updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise\<void>;|api/@ohos.app.form.formProvider.d.ts|
|New API|NA|Class name: formProvider;<br>API declaration: function getFormsInfo(filter: formInfo.FormInfoFilter, callback: AsyncCallback\<Array\<formInfo.FormInfo>>): void;<br>Differences: function getFormsInfo(filter: formInfo.FormInfoFilter, callback: AsyncCallback\<Array\<formInfo.FormInfo>>): void;|api/@ohos.app.form.formProvider.d.ts|
|New API|NA|Class name: formProvider;<br>API declaration: function getFormsInfo(callback: AsyncCallback\<Array\<formInfo.FormInfo>>): void;<br>Differences: function getFormsInfo(callback: AsyncCallback\<Array\<formInfo.FormInfo>>): void;|api/@ohos.app.form.formProvider.d.ts|
|New API|NA|Class name: formProvider;<br>API declaration: function getFormsInfo(filter?: formInfo.FormInfoFilter): Promise\<Array\<formInfo.FormInfo>>;<br>Differences: function getFormsInfo(filter?: formInfo.FormInfoFilter): Promise\<Array\<formInfo.FormInfo>>;|api/@ohos.app.form.formProvider.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace formBindingData<br>Differences: declare namespace formBindingData|api/@ohos.application.formBindingData.d.ts|
|New API|NA|Class name: formBindingData;<br>API declaration: function createFormBindingData(obj?: Object \| string): FormBindingData;<br>Differences: function createFormBindingData(obj?: Object \| string): FormBindingData;|api/@ohos.application.formBindingData.d.ts|
|New API|NA|Class name: formBindingData;<br>API declaration: interface FormBindingData<br>Differences: interface FormBindingData|api/@ohos.application.formBindingData.d.ts|
|New API|NA|Class name: FormBindingData;<br>API declaration: data: Object;<br>Differences: data: Object;|api/@ohos.application.formBindingData.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace formError<br>Differences: declare namespace formError|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: formError;<br>API declaration: enum FormError<br>Differences: enum FormError|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_COMMON = 1<br>Differences: ERR_COMMON = 1|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_PERMISSION_DENY = 2<br>Differences: ERR_PERMISSION_DENY = 2|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_GET_INFO_FAILED = 4<br>Differences: ERR_GET_INFO_FAILED = 4|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_GET_BUNDLE_FAILED = 5<br>Differences: ERR_GET_BUNDLE_FAILED = 5|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_GET_LAYOUT_FAILED = 6<br>Differences: ERR_GET_LAYOUT_FAILED = 6|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_ADD_INVALID_PARAM = 7<br>Differences: ERR_ADD_INVALID_PARAM = 7|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_CFG_NOT_MATCH_ID = 8<br>Differences: ERR_CFG_NOT_MATCH_ID = 8|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_NOT_EXIST_ID = 9<br>Differences: ERR_NOT_EXIST_ID = 9|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_BIND_PROVIDER_FAILED = 10<br>Differences: ERR_BIND_PROVIDER_FAILED = 10|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_MAX_SYSTEM_FORMS = 11<br>Differences: ERR_MAX_SYSTEM_FORMS = 11|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_MAX_INSTANCES_PER_FORM = 12<br>Differences: ERR_MAX_INSTANCES_PER_FORM = 12|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_OPERATION_FORM_NOT_SELF = 13<br>Differences: ERR_OPERATION_FORM_NOT_SELF = 13|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_PROVIDER_DEL_FAIL = 14<br>Differences: ERR_PROVIDER_DEL_FAIL = 14|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_MAX_FORMS_PER_CLIENT = 15<br>Differences: ERR_MAX_FORMS_PER_CLIENT = 15|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_MAX_SYSTEM_TEMP_FORMS = 16<br>Differences: ERR_MAX_SYSTEM_TEMP_FORMS = 16|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_FORM_NO_SUCH_MODULE = 17<br>Differences: ERR_FORM_NO_SUCH_MODULE = 17|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_FORM_NO_SUCH_ABILITY = 18<br>Differences: ERR_FORM_NO_SUCH_ABILITY = 18|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_FORM_NO_SUCH_DIMENSION = 19<br>Differences: ERR_FORM_NO_SUCH_DIMENSION = 19|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_FORM_FA_NOT_INSTALLED = 20<br>Differences: ERR_FORM_FA_NOT_INSTALLED = 20|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_SYSTEM_RESPONSES_FAILED = 30<br>Differences: ERR_SYSTEM_RESPONSES_FAILED = 30|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_FORM_DUPLICATE_ADDED = 31<br>Differences: ERR_FORM_DUPLICATE_ADDED = 31|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: FormError;<br>API declaration: ERR_IN_RECOVERY = 36<br>Differences: ERR_IN_RECOVERY = 36|api/@ohos.application.formError.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace formInfo<br>Differences: declare namespace formInfo|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: interface FormInfo<br>Differences: interface FormInfo|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: bundleName: string;<br>Differences: bundleName: string;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: moduleName: string;<br>Differences: moduleName: string;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: abilityName: string;<br>Differences: abilityName: string;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: description: string;<br>Differences: description: string;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: type: FormType;<br>Differences: type: FormType;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: jsComponentName: string;<br>Differences: jsComponentName: string;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: colorMode: ColorMode;<br>Differences: colorMode: ColorMode;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: isDefault: boolean;<br>Differences: isDefault: boolean;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: updateEnabled: boolean;<br>Differences: updateEnabled: boolean;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: formVisibleNotify: boolean;<br>Differences: formVisibleNotify: boolean;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: relatedBundleName: string;<br>Differences: relatedBundleName: string;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: scheduledUpdateTime: string;<br>Differences: scheduledUpdateTime: string;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: formConfigAbility: string;<br>Differences: formConfigAbility: string;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: updateDuration: number;<br>Differences: updateDuration: number;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: defaultDimension: number;<br>Differences: defaultDimension: number;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: supportDimensions: Array\<number>;<br>Differences: supportDimensions: Array\<number>;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormInfo;<br>API declaration: customizeData: {<br>            [key: string]: [<br>                value: string<br>            ];<br>        };<br>Differences: customizeData: {<br>            [key: string]: [<br>                value: string<br>            ];<br>        };|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: enum FormType<br>Differences: enum FormType|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormType;<br>API declaration: JS = 1<br>Differences: JS = 1|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: enum ColorMode<br>Differences: enum ColorMode|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: ColorMode;<br>API declaration: MODE_AUTO = -1<br>Differences: MODE_AUTO = -1|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: ColorMode;<br>API declaration: MODE_DARK = 0<br>Differences: MODE_DARK = 0|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: ColorMode;<br>API declaration: MODE_LIGHT = 1<br>Differences: MODE_LIGHT = 1|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: interface FormStateInfo<br>Differences: interface FormStateInfo|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormStateInfo;<br>API declaration: formState: FormState;<br>Differences: formState: FormState;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormStateInfo;<br>API declaration: want: Want;<br>Differences: want: Want;|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: enum FormState<br>Differences: enum FormState|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormState;<br>API declaration: UNKNOWN = -1<br>Differences: UNKNOWN = -1|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormState;<br>API declaration: DEFAULT = 0<br>Differences: DEFAULT = 0|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormState;<br>API declaration: READY = 1<br>Differences: READY = 1|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: formInfo;<br>API declaration: enum FormParam<br>Differences: enum FormParam|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: DIMENSION_KEY = 'ohos.extra.param.key.form_dimension'<br>Differences: DIMENSION_KEY = 'ohos.extra.param.key.form_dimension'|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: NAME_KEY = 'ohos.extra.param.key.form_name'<br>Differences: NAME_KEY = 'ohos.extra.param.key.form_name'|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: MODULE_NAME_KEY = 'ohos.extra.param.key.module_name'<br>Differences: MODULE_NAME_KEY = 'ohos.extra.param.key.module_name'|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: WIDTH_KEY = 'ohos.extra.param.key.form_width'<br>Differences: WIDTH_KEY = 'ohos.extra.param.key.form_width'|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: HEIGHT_KEY = 'ohos.extra.param.key.form_height'<br>Differences: HEIGHT_KEY = 'ohos.extra.param.key.form_height'|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: FormParam;<br>API declaration: TEMPORARY_KEY = 'ohos.extra.param.key.form_temporary'<br>Differences: TEMPORARY_KEY = 'ohos.extra.param.key.form_temporary'|api/@ohos.application.formInfo.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace formProvider<br>Differences: declare namespace formProvider|api/@ohos.application.formProvider.d.ts|
|New API|NA|Class name: formProvider;<br>API declaration: function setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback\<void>): void;<br>Differences: function setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback\<void>): void;|api/@ohos.application.formProvider.d.ts|
|New API|NA|Class name: formProvider;<br>API declaration: function setFormNextRefreshTime(formId: string, minute: number): Promise\<void>;<br>Differences: function setFormNextRefreshTime(formId: string, minute: number): Promise\<void>;|api/@ohos.application.formProvider.d.ts|
|New API|NA|Class name: formProvider;<br>API declaration: function updateForm(formId: string, formBindingData: formBindingData.FormBindingData, callback: AsyncCallback\<void>): void;<br>Differences: function updateForm(formId: string, formBindingData: formBindingData.FormBindingData, callback: AsyncCallback\<void>): void;|api/@ohos.application.formProvider.d.ts|
|New API|NA|Class name: formProvider;<br>API declaration: function updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise\<void>;<br>Differences: function updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise\<void>;|api/@ohos.application.formProvider.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.app.form.formBindingData.d.ts<br>Differences: FormKit|api/@ohos.app.form.formBindingData.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.app.form.FormExtensionAbility.d.ts<br>Differences: FormKit|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.app.form.formInfo.d.ts<br>Differences: FormKit|api/@ohos.app.form.formInfo.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.app.form.formProvider.d.ts<br>Differences: FormKit|api/@ohos.app.form.formProvider.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.application.formBindingData.d.ts<br>Differences: FormKit|api/@ohos.application.formBindingData.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.application.formError.d.ts<br>Differences: FormKit|api/@ohos.application.formError.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.application.formInfo.d.ts<br>Differences: FormKit|api/@ohos.application.formInfo.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.application.formProvider.d.ts<br>Differences: FormKit|api/@ohos.application.formProvider.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.FormKit.d.ts<br>Differences: FormKit|kits/@kit.FormKit.d.ts|
