| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|API deprecated version change|Class name: FormInfo;<br>API declaration: colorMode: ColorMode;<br>DIfferences: 20|Class name: FormInfo;<br>API declaration: colorMode: ColorMode;<br>DIfferences: NA|api/@ohos.app.form.formInfo.d.ts|
|API deprecated version change|Class name: formInfo;<br>API declaration: enum ColorMode<br>DIfferences: 20|Class name: formInfo;<br>API declaration: enum ColorMode<br>DIfferences: NA|api/@ohos.app.form.formInfo.d.ts|
|API deprecated version change|Class name: ColorMode;<br>API declaration: MODE_AUTO = -1<br>DIfferences: 20|Class name: ColorMode;<br>API declaration: MODE_AUTO = -1<br>DIfferences: NA|api/@ohos.app.form.formInfo.d.ts|
|API deprecated version change|Class name: ColorMode;<br>API declaration: MODE_DARK = 0<br>DIfferences: 20|Class name: ColorMode;<br>API declaration: MODE_DARK = 0<br>DIfferences: NA|api/@ohos.app.form.formInfo.d.ts|
|API deprecated version change|Class name: ColorMode;<br>API declaration: MODE_LIGHT = 1<br>DIfferences: 20|Class name: ColorMode;<br>API declaration: MODE_LIGHT = 1<br>DIfferences: NA|api/@ohos.app.form.formInfo.d.ts|
|API deprecated version change|Class name: FormDimension;<br>API declaration: Dimension_2_1<br>DIfferences: 20|Class name: FormDimension;<br>API declaration: Dimension_2_1<br>DIfferences: NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: global;<br>API declaration: declare class FormEditExtensionAbility<br>DIfferences: declare class FormEditExtensionAbility|NA|api/@ohos.app.form.FormEditExtensionAbility.d.ts|
| Deleted API|Class name: FormEditExtensionAbility;<br>API declaration: context: FormEditExtensionContext;<br>DIfferences: context: FormEditExtensionContext;|NA|api/@ohos.app.form.FormEditExtensionAbility.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface LiveFormInfo<br>DIfferences: export interface LiveFormInfo|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
| Deleted API|Class name: LiveFormInfo;<br>API declaration: formId: string;<br>DIfferences: formId: string;|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
| Deleted API|Class name: LiveFormInfo;<br>API declaration: rect: formInfo.Rect;<br>DIfferences: rect: formInfo.Rect;|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
| Deleted API|Class name: LiveFormInfo;<br>API declaration: borderRadius: number;<br>DIfferences: borderRadius: number;|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
| Deleted API|Class name: global;<br>API declaration: declare class LiveFormExtensionAbility<br>DIfferences: declare class LiveFormExtensionAbility|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
| Deleted API|Class name: LiveFormExtensionAbility;<br>API declaration: context: LiveFormExtensionContext;<br>DIfferences: context: LiveFormExtensionContext;|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
| Deleted API|Class name: LiveFormExtensionAbility;<br>API declaration: onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void;<br>DIfferences: onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void;|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
| Deleted API|Class name: LiveFormExtensionAbility;<br>API declaration: onLiveFormDestroy(liveFormInfo: LiveFormInfo): void;<br>DIfferences: onLiveFormDestroy(liveFormInfo: LiveFormInfo): void;|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
| Deleted API|Class name: global;<br>API declaration: declare class FormEditExtensionContext<br>DIfferences: declare class FormEditExtensionContext|NA|api/application/FormEditExtensionContext.d.ts|
| Deleted API|Class name: FormEditExtensionContext;<br>API declaration: startSecondPage(want: Want): Promise\<AbilityResult>;<br>DIfferences: startSecondPage(want: Want): Promise\<AbilityResult>;|NA|api/application/FormEditExtensionContext.d.ts|
| Deleted API|Class name: global;<br>API declaration: declare class LiveFormExtensionContext<br>DIfferences: declare class LiveFormExtensionContext|NA|api/application/LiveFormExtensionContext.d.ts|
| Deleted API|Class name: LiveFormExtensionContext;<br>API declaration: startAbilityByLiveForm(want: Want): Promise\<void>;<br>DIfferences: startAbilityByLiveForm(want: Want): Promise\<void>;|NA|api/application/LiveFormExtensionContext.d.ts|
| Deleted API|Class name: FormExtensionAbility;<br>API declaration: onFormLocationChanged(formId: string, newFormLocation: formInfo.FormLocation): void;<br>DIfferences: onFormLocationChanged(formId: string, newFormLocation: formInfo.FormLocation): void;|NA|api/@ohos.app.form.FormExtensionAbility.d.ts|
| Deleted API|Class name: FormExtensionAbility;<br>API declaration: onSizeChanged(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void;<br>DIfferences: onSizeChanged(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void;|NA|api/@ohos.app.form.FormExtensionAbility.d.ts|
| Deleted API|Class name: FormParam;<br>API declaration: ORIGINAL_FORM_KEY = 'ohos.extra.param.key.original_form_id'<br>DIfferences: ORIGINAL_FORM_KEY = 'ohos.extra.param.key.original_form_id'|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: FormDimension;<br>API declaration: DIMENSION_2_3 = 8<br>DIfferences: DIMENSION_2_3 = 8|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: FormDimension;<br>API declaration: DIMENSION_3_3 = 9<br>DIfferences: DIMENSION_3_3 = 9|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: LaunchReason;<br>API declaration: FORM_SIZE_CHANGE = 3<br>DIfferences: FORM_SIZE_CHANGE = 3|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: formInfo;<br>API declaration: interface RunningFormInfo<br>DIfferences: interface RunningFormInfo|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: RunningFormInfo;<br>API declaration: readonly formId: string;<br>DIfferences: readonly formId: string;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: RunningFormInfo;<br>API declaration: readonly bundleName: string;<br>DIfferences: readonly bundleName: string;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: RunningFormInfo;<br>API declaration: readonly formLocation: FormLocation;<br>DIfferences: readonly formLocation: FormLocation;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: RunningFormInfo;<br>API declaration: readonly moduleName: string;<br>DIfferences: readonly moduleName: string;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: RunningFormInfo;<br>API declaration: readonly abilityName: string;<br>DIfferences: readonly abilityName: string;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: RunningFormInfo;<br>API declaration: readonly formName: string;<br>DIfferences: readonly formName: string;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: RunningFormInfo;<br>API declaration: readonly dimension: number;<br>DIfferences: readonly dimension: number;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: formInfo;<br>API declaration: enum FormLocation<br>DIfferences: enum FormLocation|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: FormLocation;<br>API declaration: DESKTOP = 0<br>DIfferences: DESKTOP = 0|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: FormLocation;<br>API declaration: FORM_CENTER = 1<br>DIfferences: FORM_CENTER = 1|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: FormLocation;<br>API declaration: FORM_MANAGER = 2<br>DIfferences: FORM_MANAGER = 2|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: FormLocation;<br>API declaration: NEGATIVE_SCREEN = 3<br>DIfferences: NEGATIVE_SCREEN = 3|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: FormLocation;<br>API declaration: SCREEN_LOCK = 6<br>DIfferences: SCREEN_LOCK = 6|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: FormLocation;<br>API declaration: AI_SUGGESTION = 7<br>DIfferences: AI_SUGGESTION = 7|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: formInfo;<br>API declaration: interface OverflowInfo<br>DIfferences: interface OverflowInfo|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: OverflowInfo;<br>API declaration: area: Rect;<br>DIfferences: area: Rect;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: OverflowInfo;<br>API declaration: duration: number;<br>DIfferences: duration: number;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: OverflowInfo;<br>API declaration: useDefaultAnimation?: boolean;<br>DIfferences: useDefaultAnimation?: boolean;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: formInfo;<br>API declaration: interface Rect<br>DIfferences: interface Rect|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: Rect;<br>API declaration: left: number;<br>DIfferences: left: number;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: Rect;<br>API declaration: top: number;<br>DIfferences: top: number;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: Rect;<br>API declaration: width: number;<br>DIfferences: width: number;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: Rect;<br>API declaration: height: number;<br>DIfferences: height: number;|NA|api/@ohos.app.form.formInfo.d.ts|
| Deleted API|Class name: formProvider;<br>API declaration: function getPublishedFormInfoById(formId: string): Promise\<formInfo.FormInfo>;<br>DIfferences: function getPublishedFormInfoById(formId: string): Promise\<formInfo.FormInfo>;|NA|api/@ohos.app.form.formProvider.d.ts|
| Deleted API|Class name: formProvider;<br>API declaration: function getPublishedFormInfos(): Promise\<Array\<formInfo.FormInfo>>;<br>DIfferences: function getPublishedFormInfos(): Promise\<Array\<formInfo.FormInfo>>;|NA|api/@ohos.app.form.formProvider.d.ts|
| Deleted API|Class name: formProvider;<br>API declaration: function getPublishedRunningFormInfoById(formId: string): Promise\<formInfo.RunningFormInfo>;<br>DIfferences: function getPublishedRunningFormInfoById(formId: string): Promise\<formInfo.RunningFormInfo>;|NA|api/@ohos.app.form.formProvider.d.ts|
| Deleted API|Class name: formProvider;<br>API declaration: function getPublishedRunningFormInfos(): Promise\<Array\<formInfo.RunningFormInfo>>;<br>DIfferences: function getPublishedRunningFormInfos(): Promise\<Array\<formInfo.RunningFormInfo>>;|NA|api/@ohos.app.form.formProvider.d.ts|
| Deleted API|Class name: formProvider;<br>API declaration: function openFormManager(want: Want): void;<br>DIfferences: function openFormManager(want: Want): void;|NA|api/@ohos.app.form.formProvider.d.ts|
| Deleted API|Class name: formProvider;<br>API declaration: function openFormEditAbility(abilityName: string, formId: string, isMainPage?: boolean): void;<br>DIfferences: function openFormEditAbility(abilityName: string, formId: string, isMainPage?: boolean): void;|NA|api/@ohos.app.form.formProvider.d.ts|
| Deleted API|Class name: formProvider;<br>API declaration: function requestOverflow(formId: string, overflowInfo: formInfo.OverflowInfo): Promise\<void>;<br>DIfferences: function requestOverflow(formId: string, overflowInfo: formInfo.OverflowInfo): Promise\<void>;|NA|api/@ohos.app.form.formProvider.d.ts|
| Deleted API|Class name: formProvider;<br>API declaration: function cancelOverflow(formId: string): Promise\<void>;<br>DIfferences: function cancelOverflow(formId: string): Promise\<void>;|NA|api/@ohos.app.form.formProvider.d.ts|
| Deleted API|Class name: formProvider;<br>API declaration: function getFormRect(formId: string): Promise\<formInfo.Rect>;<br>DIfferences: function getFormRect(formId: string): Promise\<formInfo.Rect>;|NA|api/@ohos.app.form.formProvider.d.ts|
|Deleted kit|Class name: global;<br>API declaration: api\@ohos.app.form.FormEditExtensionAbility.d.ts<br>DIfferences: FormKit|Class name: global;<br>API declaration: <br>DIfferences: NA|api/@ohos.app.form.FormEditExtensionAbility.d.ts|
|Deleted kit|Class name: global;<br>API declaration: api\@ohos.app.form.LiveFormExtensionAbility.d.ts<br>DIfferences: FormKit|Class name: global;<br>API declaration: <br>DIfferences: NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|Deleted kit|Class name: global;<br>API declaration: api\application\FormEditExtensionContext.d.ts<br>DIfferences: FormKit|Class name: global;<br>API declaration: <br>DIfferences: NA|api/application/FormEditExtensionContext.d.ts|
|Deleted kit|Class name: global;<br>API declaration: api\application\LiveFormExtensionContext.d.ts<br>DIfferences: FormKit|Class name: global;<br>API declaration: <br>DIfferences: NA|api/application/LiveFormExtensionContext.d.ts|
|Compatible for ArkTS version evolution|Class name: global;<br>API declaration: declare class FormExtensionAbility<br>DIfferences: NA|Class name: global;<br>API declaration: export default class FormExtensionAbility<br>DIfferences: NA|api/@ohos.app.form.FormExtensionAbility.d.ts|
|Compatible for ArkTS version evolution|Class name: global;<br>API declaration: declare class FormExtensionContext<br>DIfferences: NA|Class name: global;<br>API declaration: export default class FormExtensionContext<br>DIfferences: NA|api/application/FormExtensionContext.d.ts|
