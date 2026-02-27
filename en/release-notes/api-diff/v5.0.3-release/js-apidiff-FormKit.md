| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|API deprecated version change|Class name: FormInfo;<br>API declaration: colorMode: ColorMode;<br>DIfferences: NA|Class name: FormInfo;<br>API declaration: colorMode: ColorMode;<br>DIfferences: 20|api/@ohos.app.form.formInfo.d.ts|
|API deprecated version change|Class name: formInfo;<br>API declaration: enum ColorMode<br>DIfferences: NA|Class name: formInfo;<br>API declaration: enum ColorMode<br>DIfferences: 20|api/@ohos.app.form.formInfo.d.ts|
|API deprecated version change|Class name: ColorMode;<br>API declaration: MODE_AUTO = -1<br>DIfferences: NA|Class name: ColorMode;<br>API declaration: MODE_AUTO = -1<br>DIfferences: 20|api/@ohos.app.form.formInfo.d.ts|
|API deprecated version change|Class name: ColorMode;<br>API declaration: MODE_DARK = 0<br>DIfferences: NA|Class name: ColorMode;<br>API declaration: MODE_DARK = 0<br>DIfferences: 20|api/@ohos.app.form.formInfo.d.ts|
|API deprecated version change|Class name: ColorMode;<br>API declaration: MODE_LIGHT = 1<br>DIfferences: NA|Class name: ColorMode;<br>API declaration: MODE_LIGHT = 1<br>DIfferences: 20|api/@ohos.app.form.formInfo.d.ts|
|API deprecated version change|Class name: FormDimension;<br>API declaration: Dimension_2_1<br>DIfferences: NA|Class name: FormDimension;<br>API declaration: Dimension_2_1<br>DIfferences: 20|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare class FormEditExtensionAbility<br>DIfferences: declare class FormEditExtensionAbility|api/@ohos.app.form.FormEditExtensionAbility.d.ts|
|New API |NA|Class name: FormEditExtensionAbility;<br>API declaration: context: FormEditExtensionContext;<br>DIfferences: context: FormEditExtensionContext;|api/@ohos.app.form.FormEditExtensionAbility.d.ts|
|New API |NA|Class name: global;<br>API declaration: export interface LiveFormInfo<br>DIfferences: export interface LiveFormInfo|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|New API |NA|Class name: LiveFormInfo;<br>API declaration: formId: string;<br>DIfferences: formId: string;|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|New API |NA|Class name: LiveFormInfo;<br>API declaration: rect: formInfo.Rect;<br>DIfferences: rect: formInfo.Rect;|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|New API |NA|Class name: LiveFormInfo;<br>API declaration: borderRadius: number;<br>DIfferences: borderRadius: number;|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare class LiveFormExtensionAbility<br>DIfferences: declare class LiveFormExtensionAbility|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|New API |NA|Class name: LiveFormExtensionAbility;<br>API declaration: context: LiveFormExtensionContext;<br>DIfferences: context: LiveFormExtensionContext;|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|New API |NA|Class name: LiveFormExtensionAbility;<br>API declaration: onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void;<br>DIfferences: onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void;|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|New API |NA|Class name: LiveFormExtensionAbility;<br>API declaration: onLiveFormDestroy(liveFormInfo: LiveFormInfo): void;<br>DIfferences: onLiveFormDestroy(liveFormInfo: LiveFormInfo): void;|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare class FormEditExtensionContext<br>DIfferences: declare class FormEditExtensionContext|api/application/FormEditExtensionContext.d.ts|
|New API |NA|Class name: FormEditExtensionContext;<br>API declaration: startSecondPage(want: Want): Promise\<AbilityResult>;<br>DIfferences: startSecondPage(want: Want): Promise\<AbilityResult>;|api/application/FormEditExtensionContext.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare class LiveFormExtensionContext<br>DIfferences: declare class LiveFormExtensionContext|api/application/LiveFormExtensionContext.d.ts|
|New API |NA|Class name: LiveFormExtensionContext;<br>API declaration: startAbilityByLiveForm(want: Want): Promise\<void>;<br>DIfferences: startAbilityByLiveForm(want: Want): Promise\<void>;|api/application/LiveFormExtensionContext.d.ts|
|New API |NA|Class name: FormExtensionAbility;<br>API declaration: onFormLocationChanged(formId: string, newFormLocation: formInfo.FormLocation): void;<br>DIfferences: onFormLocationChanged(formId: string, newFormLocation: formInfo.FormLocation): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API |NA|Class name: FormExtensionAbility;<br>API declaration: onSizeChanged(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void;<br>DIfferences: onSizeChanged(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void;|api/@ohos.app.form.FormExtensionAbility.d.ts|
|New API |NA|Class name: FormParam;<br>API declaration: ORIGINAL_FORM_KEY = 'ohos.extra.param.key.original_form_id'<br>DIfferences: ORIGINAL_FORM_KEY = 'ohos.extra.param.key.original_form_id'|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: FormDimension;<br>API declaration: DIMENSION_2_3 = 8<br>DIfferences: DIMENSION_2_3 = 8|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: FormDimension;<br>API declaration: DIMENSION_3_3 = 9<br>DIfferences: DIMENSION_3_3 = 9|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: LaunchReason;<br>API declaration: FORM_SIZE_CHANGE = 3<br>DIfferences: FORM_SIZE_CHANGE = 3|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: formInfo;<br>API declaration: interface RunningFormInfo<br>DIfferences: interface RunningFormInfo|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: RunningFormInfo;<br>API declaration: readonly formId: string;<br>DIfferences: readonly formId: string;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: RunningFormInfo;<br>API declaration: readonly bundleName: string;<br>DIfferences: readonly bundleName: string;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: RunningFormInfo;<br>API declaration: readonly formLocation: FormLocation;<br>DIfferences: readonly formLocation: FormLocation;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: RunningFormInfo;<br>API declaration: readonly moduleName: string;<br>DIfferences: readonly moduleName: string;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: RunningFormInfo;<br>API declaration: readonly abilityName: string;<br>DIfferences: readonly abilityName: string;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: RunningFormInfo;<br>API declaration: readonly formName: string;<br>DIfferences: readonly formName: string;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: RunningFormInfo;<br>API declaration: readonly dimension: number;<br>DIfferences: readonly dimension: number;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: formInfo;<br>API declaration: enum FormLocation<br>DIfferences: enum FormLocation|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: FormLocation;<br>API declaration: DESKTOP = 0<br>DIfferences: DESKTOP = 0|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: FormLocation;<br>API declaration: FORM_CENTER = 1<br>DIfferences: FORM_CENTER = 1|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: FormLocation;<br>API declaration: FORM_MANAGER = 2<br>DIfferences: FORM_MANAGER = 2|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: FormLocation;<br>API declaration: NEGATIVE_SCREEN = 3<br>DIfferences: NEGATIVE_SCREEN = 3|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: FormLocation;<br>API declaration: SCREEN_LOCK = 6<br>DIfferences: SCREEN_LOCK = 6|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: FormLocation;<br>API declaration: AI_SUGGESTION = 7<br>DIfferences: AI_SUGGESTION = 7|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: formInfo;<br>API declaration: interface OverflowInfo<br>DIfferences: interface OverflowInfo|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: OverflowInfo;<br>API declaration: area: Rect;<br>DIfferences: area: Rect;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: OverflowInfo;<br>API declaration: duration: number;<br>DIfferences: duration: number;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: OverflowInfo;<br>API declaration: useDefaultAnimation?: boolean;<br>DIfferences: useDefaultAnimation?: boolean;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: formInfo;<br>API declaration: interface Rect<br>DIfferences: interface Rect|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: Rect;<br>API declaration: left: number;<br>DIfferences: left: number;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: Rect;<br>API declaration: top: number;<br>DIfferences: top: number;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: Rect;<br>API declaration: width: number;<br>DIfferences: width: number;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: Rect;<br>API declaration: height: number;<br>DIfferences: height: number;|api/@ohos.app.form.formInfo.d.ts|
|New API |NA|Class name: formProvider;<br>API declaration: function getPublishedFormInfoById(formId: string): Promise\<formInfo.FormInfo>;<br>DIfferences: function getPublishedFormInfoById(formId: string): Promise\<formInfo.FormInfo>;|api/@ohos.app.form.formProvider.d.ts|
|New API |NA|Class name: formProvider;<br>API declaration: function getPublishedFormInfos(): Promise\<Array\<formInfo.FormInfo>>;<br>DIfferences: function getPublishedFormInfos(): Promise\<Array\<formInfo.FormInfo>>;|api/@ohos.app.form.formProvider.d.ts|
|New API |NA|Class name: formProvider;<br>API declaration: function getPublishedRunningFormInfoById(formId: string): Promise\<formInfo.RunningFormInfo>;<br>DIfferences: function getPublishedRunningFormInfoById(formId: string): Promise\<formInfo.RunningFormInfo>;|api/@ohos.app.form.formProvider.d.ts|
|New API |NA|Class name: formProvider;<br>API declaration: function getPublishedRunningFormInfos(): Promise\<Array\<formInfo.RunningFormInfo>>;<br>DIfferences: function getPublishedRunningFormInfos(): Promise\<Array\<formInfo.RunningFormInfo>>;|api/@ohos.app.form.formProvider.d.ts|
|New API |NA|Class name: formProvider;<br>API declaration: function openFormManager(want: Want): void;<br>DIfferences: function openFormManager(want: Want): void;|api/@ohos.app.form.formProvider.d.ts|
|New API |NA|Class name: formProvider;<br>API declaration: function openFormEditAbility(abilityName: string, formId: string, isMainPage?: boolean): void;<br>DIfferences: function openFormEditAbility(abilityName: string, formId: string, isMainPage?: boolean): void;|api/@ohos.app.form.formProvider.d.ts|
|New API |NA|Class name: formProvider;<br>API declaration: function requestOverflow(formId: string, overflowInfo: formInfo.OverflowInfo): Promise\<void>;<br>DIfferences: function requestOverflow(formId: string, overflowInfo: formInfo.OverflowInfo): Promise\<void>;|api/@ohos.app.form.formProvider.d.ts|
|New API |NA|Class name: formProvider;<br>API declaration: function cancelOverflow(formId: string): Promise\<void>;<br>DIfferences: function cancelOverflow(formId: string): Promise\<void>;|api/@ohos.app.form.formProvider.d.ts|
|New API |NA|Class name: formProvider;<br>API declaration: function getFormRect(formId: string): Promise\<formInfo.Rect>;<br>DIfferences: function getFormRect(formId: string): Promise\<formInfo.Rect>;|api/@ohos.app.form.formProvider.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>DIfferences: NA|Class name: global;<br>API declaration: api\@ohos.app.form.FormEditExtensionAbility.d.ts<br>DIfferences: FormKit|api/@ohos.app.form.FormEditExtensionAbility.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>DIfferences: NA|Class name: global;<br>API declaration: api\@ohos.app.form.LiveFormExtensionAbility.d.ts<br>DIfferences: FormKit|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>DIfferences: NA|Class name: global;<br>API declaration: api\application\FormEditExtensionContext.d.ts<br>DIfferences: FormKit|api/application/FormEditExtensionContext.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>DIfferences: NA|Class name: global;<br>API declaration: api\application\LiveFormExtensionContext.d.ts<br>DIfferences: FormKit|api/application/LiveFormExtensionContext.d.ts|
|Compatible for ArkTS version evolution|Class name: global;<br>API declaration: export default class FormExtensionAbility<br>DIfferences: NA|Class name: global;<br>API declaration: declare class FormExtensionAbility<br>DIfferences: NA|api/@ohos.app.form.FormExtensionAbility.d.ts|
|Compatible for ArkTS version evolution|Class name: global;<br>API declaration: export default class FormExtensionContext<br>DIfferences: NA|Class name: global;<br>API declaration: declare class FormExtensionContext<br>DIfferences: NA|api/application/FormExtensionContext.d.ts|
