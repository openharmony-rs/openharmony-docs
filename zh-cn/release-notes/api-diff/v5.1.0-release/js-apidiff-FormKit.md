| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API废弃版本变更|类名：FormInfo；<br>API声明：colorMode: ColorMode;<br>差异内容：20|类名：FormInfo；<br>API声明：colorMode: ColorMode;<br>差异内容：NA|api/@ohos.app.form.formInfo.d.ts|
|API废弃版本变更|类名：formInfo；<br>API声明：enum ColorMode<br>差异内容：20|类名：formInfo；<br>API声明：enum ColorMode<br>差异内容：NA|api/@ohos.app.form.formInfo.d.ts|
|API废弃版本变更|类名：ColorMode；<br>API声明：MODE_AUTO = -1<br>差异内容：20|类名：ColorMode；<br>API声明：MODE_AUTO = -1<br>差异内容：NA|api/@ohos.app.form.formInfo.d.ts|
|API废弃版本变更|类名：ColorMode；<br>API声明：MODE_DARK = 0<br>差异内容：20|类名：ColorMode；<br>API声明：MODE_DARK = 0<br>差异内容：NA|api/@ohos.app.form.formInfo.d.ts|
|API废弃版本变更|类名：ColorMode；<br>API声明：MODE_LIGHT = 1<br>差异内容：20|类名：ColorMode；<br>API声明：MODE_LIGHT = 1<br>差异内容：NA|api/@ohos.app.form.formInfo.d.ts|
|API废弃版本变更|类名：FormDimension；<br>API声明：Dimension_2_1<br>差异内容：20|类名：FormDimension；<br>API声明：Dimension_2_1<br>差异内容：NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：global；<br>API声明：declare class FormEditExtensionAbility<br>差异内容：declare class FormEditExtensionAbility|NA|api/@ohos.app.form.FormEditExtensionAbility.d.ts|
|删除API|类名：FormEditExtensionAbility；<br>API声明：context: FormEditExtensionContext;<br>差异内容：context: FormEditExtensionContext;|NA|api/@ohos.app.form.FormEditExtensionAbility.d.ts|
|删除API|类名：global；<br>API声明：export interface LiveFormInfo<br>差异内容：export interface LiveFormInfo|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|删除API|类名：LiveFormInfo；<br>API声明：formId: string;<br>差异内容：formId: string;|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|删除API|类名：LiveFormInfo；<br>API声明：rect: formInfo.Rect;<br>差异内容：rect: formInfo.Rect;|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|删除API|类名：LiveFormInfo；<br>API声明：borderRadius: number;<br>差异内容：borderRadius: number;|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|删除API|类名：global；<br>API声明：declare class LiveFormExtensionAbility<br>差异内容：declare class LiveFormExtensionAbility|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|删除API|类名：LiveFormExtensionAbility；<br>API声明：context: LiveFormExtensionContext;<br>差异内容：context: LiveFormExtensionContext;|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|删除API|类名：LiveFormExtensionAbility；<br>API声明：onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void;<br>差异内容：onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void;|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|删除API|类名：LiveFormExtensionAbility；<br>API声明：onLiveFormDestroy(liveFormInfo: LiveFormInfo): void;<br>差异内容：onLiveFormDestroy(liveFormInfo: LiveFormInfo): void;|NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|删除API|类名：global；<br>API声明：declare class FormEditExtensionContext<br>差异内容：declare class FormEditExtensionContext|NA|api/application/FormEditExtensionContext.d.ts|
|删除API|类名：FormEditExtensionContext；<br>API声明：startSecondPage(want: Want): Promise\<AbilityResult>;<br>差异内容：startSecondPage(want: Want): Promise\<AbilityResult>;|NA|api/application/FormEditExtensionContext.d.ts|
|删除API|类名：global；<br>API声明：declare class LiveFormExtensionContext<br>差异内容：declare class LiveFormExtensionContext|NA|api/application/LiveFormExtensionContext.d.ts|
|删除API|类名：LiveFormExtensionContext；<br>API声明：startAbilityByLiveForm(want: Want): Promise\<void>;<br>差异内容：startAbilityByLiveForm(want: Want): Promise\<void>;|NA|api/application/LiveFormExtensionContext.d.ts|
|删除API|类名：FormExtensionAbility；<br>API声明：onFormLocationChanged(formId: string, newFormLocation: formInfo.FormLocation): void;<br>差异内容：onFormLocationChanged(formId: string, newFormLocation: formInfo.FormLocation): void;|NA|api/@ohos.app.form.FormExtensionAbility.d.ts|
|删除API|类名：FormExtensionAbility；<br>API声明：onSizeChanged(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void;<br>差异内容：onSizeChanged(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void;|NA|api/@ohos.app.form.FormExtensionAbility.d.ts|
|删除API|类名：FormParam；<br>API声明：ORIGINAL_FORM_KEY = 'ohos.extra.param.key.original_form_id'<br>差异内容：ORIGINAL_FORM_KEY = 'ohos.extra.param.key.original_form_id'|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：FormDimension；<br>API声明：DIMENSION_2_3 = 8<br>差异内容：DIMENSION_2_3 = 8|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：FormDimension；<br>API声明：DIMENSION_3_3 = 9<br>差异内容：DIMENSION_3_3 = 9|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：LaunchReason；<br>API声明：FORM_SIZE_CHANGE = 3<br>差异内容：FORM_SIZE_CHANGE = 3|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：formInfo；<br>API声明：interface RunningFormInfo<br>差异内容：interface RunningFormInfo|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：RunningFormInfo；<br>API声明：readonly formId: string;<br>差异内容：readonly formId: string;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：RunningFormInfo；<br>API声明：readonly bundleName: string;<br>差异内容：readonly bundleName: string;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：RunningFormInfo；<br>API声明：readonly formLocation: FormLocation;<br>差异内容：readonly formLocation: FormLocation;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：RunningFormInfo；<br>API声明：readonly moduleName: string;<br>差异内容：readonly moduleName: string;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：RunningFormInfo；<br>API声明：readonly abilityName: string;<br>差异内容：readonly abilityName: string;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：RunningFormInfo；<br>API声明：readonly formName: string;<br>差异内容：readonly formName: string;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：RunningFormInfo；<br>API声明：readonly dimension: number;<br>差异内容：readonly dimension: number;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：formInfo；<br>API声明：enum FormLocation<br>差异内容：enum FormLocation|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：FormLocation；<br>API声明：DESKTOP = 0<br>差异内容：DESKTOP = 0|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：FormLocation；<br>API声明：FORM_CENTER = 1<br>差异内容：FORM_CENTER = 1|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：FormLocation；<br>API声明：FORM_MANAGER = 2<br>差异内容：FORM_MANAGER = 2|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：FormLocation；<br>API声明：NEGATIVE_SCREEN = 3<br>差异内容：NEGATIVE_SCREEN = 3|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：FormLocation；<br>API声明：SCREEN_LOCK = 6<br>差异内容：SCREEN_LOCK = 6|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：FormLocation；<br>API声明：AI_SUGGESTION = 7<br>差异内容：AI_SUGGESTION = 7|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：formInfo；<br>API声明：interface OverflowInfo<br>差异内容：interface OverflowInfo|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：OverflowInfo；<br>API声明：area: Rect;<br>差异内容：area: Rect;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：OverflowInfo；<br>API声明：duration: number;<br>差异内容：duration: number;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：OverflowInfo；<br>API声明：useDefaultAnimation?: boolean;<br>差异内容：useDefaultAnimation?: boolean;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：formInfo；<br>API声明：interface Rect<br>差异内容：interface Rect|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：Rect；<br>API声明：left: number;<br>差异内容：left: number;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：Rect；<br>API声明：top: number;<br>差异内容：top: number;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：Rect；<br>API声明：width: number;<br>差异内容：width: number;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：Rect；<br>API声明：height: number;<br>差异内容：height: number;|NA|api/@ohos.app.form.formInfo.d.ts|
|删除API|类名：formProvider；<br>API声明：function getPublishedFormInfoById(formId: string): Promise\<formInfo.FormInfo>;<br>差异内容：function getPublishedFormInfoById(formId: string): Promise\<formInfo.FormInfo>;|NA|api/@ohos.app.form.formProvider.d.ts|
|删除API|类名：formProvider；<br>API声明：function getPublishedFormInfos(): Promise\<Array\<formInfo.FormInfo>>;<br>差异内容：function getPublishedFormInfos(): Promise\<Array\<formInfo.FormInfo>>;|NA|api/@ohos.app.form.formProvider.d.ts|
|删除API|类名：formProvider；<br>API声明：function getPublishedRunningFormInfoById(formId: string): Promise\<formInfo.RunningFormInfo>;<br>差异内容：function getPublishedRunningFormInfoById(formId: string): Promise\<formInfo.RunningFormInfo>;|NA|api/@ohos.app.form.formProvider.d.ts|
|删除API|类名：formProvider；<br>API声明：function getPublishedRunningFormInfos(): Promise\<Array\<formInfo.RunningFormInfo>>;<br>差异内容：function getPublishedRunningFormInfos(): Promise\<Array\<formInfo.RunningFormInfo>>;|NA|api/@ohos.app.form.formProvider.d.ts|
|删除API|类名：formProvider；<br>API声明：function openFormManager(want: Want): void;<br>差异内容：function openFormManager(want: Want): void;|NA|api/@ohos.app.form.formProvider.d.ts|
|删除API|类名：formProvider；<br>API声明：function openFormEditAbility(abilityName: string, formId: string, isMainPage?: boolean): void;<br>差异内容：function openFormEditAbility(abilityName: string, formId: string, isMainPage?: boolean): void;|NA|api/@ohos.app.form.formProvider.d.ts|
|删除API|类名：formProvider；<br>API声明：function requestOverflow(formId: string, overflowInfo: formInfo.OverflowInfo): Promise\<void>;<br>差异内容：function requestOverflow(formId: string, overflowInfo: formInfo.OverflowInfo): Promise\<void>;|NA|api/@ohos.app.form.formProvider.d.ts|
|删除API|类名：formProvider；<br>API声明：function cancelOverflow(formId: string): Promise\<void>;<br>差异内容：function cancelOverflow(formId: string): Promise\<void>;|NA|api/@ohos.app.form.formProvider.d.ts|
|删除API|类名：formProvider；<br>API声明：function getFormRect(formId: string): Promise\<formInfo.Rect>;<br>差异内容：function getFormRect(formId: string): Promise\<formInfo.Rect>;|NA|api/@ohos.app.form.formProvider.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.app.form.FormEditExtensionAbility.d.ts<br>差异内容：FormKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.app.form.FormEditExtensionAbility.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.app.form.LiveFormExtensionAbility.d.ts<br>差异内容：FormKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.app.form.LiveFormExtensionAbility.d.ts|
|删除kit|类名：global；<br>API声明：api\application\FormEditExtensionContext.d.ts<br>差异内容：FormKit|类名：global；<br>API声明：<br>差异内容：NA|api/application/FormEditExtensionContext.d.ts|
|删除kit|类名：global；<br>API声明：api\application\LiveFormExtensionContext.d.ts<br>差异内容：FormKit|类名：global；<br>API声明：<br>差异内容：NA|api/application/LiveFormExtensionContext.d.ts|
|arkts演进版本整改兼容变化|类名：global；<br>API声明：declare class FormExtensionAbility<br>差异内容：NA|类名：global；<br>API声明：export default class FormExtensionAbility<br>差异内容：NA|api/@ohos.app.form.FormExtensionAbility.d.ts|
|arkts演进版本整改兼容变化|类名：global；<br>API声明：declare class FormExtensionContext<br>差异内容：NA|类名：global；<br>API声明：export default class FormExtensionContext<br>差异内容：NA|api/application/FormExtensionContext.d.ts|
