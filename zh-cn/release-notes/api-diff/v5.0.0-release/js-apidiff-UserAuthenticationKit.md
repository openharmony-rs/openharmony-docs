| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：userAuth；<br>API声明：function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void;<br>差异内容：NA|类名：userAuth；<br>API声明：function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void;<br>差异内容：12500013|api/@ohos.userIAM.userAuth.d.ts|
|新增错误码|类名：UserAuthInstance；<br>API声明：start(): void;<br>差异内容：NA|类名：UserAuthInstance；<br>API声明：start(): void;<br>差异内容：12500013|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：global；<br>API声明：export default struct UserAuthIcon<br>差异内容：export default struct UserAuthIcon|api/@ohos.userIAM.userAuthIcon.d.ets|
|新增API|NA|类名：UserAuthIcon；<br>API声明：authParam: userAuth.AuthParam;<br>差异内容：authParam: userAuth.AuthParam;|api/@ohos.userIAM.userAuthIcon.d.ets|
|新增API|NA|类名：UserAuthIcon；<br>API声明：widgetParam: userAuth.WidgetParam;<br>差异内容：widgetParam: userAuth.WidgetParam;|api/@ohos.userIAM.userAuthIcon.d.ets|
|新增API|NA|类名：UserAuthIcon；<br>API声明：iconHeight?: Dimension;<br>差异内容：iconHeight?: Dimension;|api/@ohos.userIAM.userAuthIcon.d.ets|
|新增API|NA|类名：UserAuthIcon；<br>API声明：iconColor?: ResourceColor;<br>差异内容：iconColor?: ResourceColor;|api/@ohos.userIAM.userAuthIcon.d.ets|
|新增API|NA|类名：UserAuthIcon；<br>API声明：onAuthResult: (result: userAuth.UserAuthResult) => void;<br>差异内容：onAuthResult: (result: userAuth.UserAuthResult) => void;|api/@ohos.userIAM.userAuthIcon.d.ets|
|新增API|NA|类名：UserAuthIcon；<br>API声明：onIconClick?: () => void;<br>差异内容：onIconClick?: () => void;|api/@ohos.userIAM.userAuthIcon.d.ets|
|新增API|NA|类名：userAuth；<br>API声明：const MAX_ALLOWABLE_REUSE_DURATION: 300000;<br>差异内容：const MAX_ALLOWABLE_REUSE_DURATION: 300000;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface EnrolledState<br>差异内容：interface EnrolledState|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：EnrolledState；<br>API声明：credentialDigest: number;<br>差异内容：credentialDigest: number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：EnrolledState；<br>API声明：credentialCount: number;<br>差异内容：credentialCount: number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：function getEnrolledState(authType: UserAuthType): EnrolledState;<br>差异内容：function getEnrolledState(authType: UserAuthType): EnrolledState;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：enum ReuseMode<br>差异内容：enum ReuseMode|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ReuseMode；<br>API声明：AUTH_TYPE_RELEVANT = 1<br>差异内容：AUTH_TYPE_RELEVANT = 1|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ReuseMode；<br>API声明：AUTH_TYPE_IRRELEVANT = 2<br>差异内容：AUTH_TYPE_IRRELEVANT = 2|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface ReuseUnlockResult<br>差异内容：interface ReuseUnlockResult|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ReuseUnlockResult；<br>API声明：reuseMode: ReuseMode;<br>差异内容：reuseMode: ReuseMode;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ReuseUnlockResult；<br>API声明：reuseDuration: number;<br>差异内容：reuseDuration: number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthParam；<br>API声明：reuseUnlockResult?: ReuseUnlockResult;<br>差异内容：reuseUnlockResult?: ReuseUnlockResult;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResult；<br>API声明：enrolledState?: EnrolledState;<br>差异内容：enrolledState?: EnrolledState;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：PIN_EXPIRED = 12500013<br>差异内容：PIN_EXPIRED = 12500013|api/@ohos.userIAM.userAuth.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.userIAM.userAuthIcon.d.ets<br>差异内容：UserAuthenticationKit|api/@ohos.userIAM.userAuthIcon.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace userAuth<br>差异内容：NA|类名：global；<br>API声明：declare namespace userAuth<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：userAuth；<br>API声明：enum UserAuthType<br>差异内容：NA|类名：userAuth；<br>API声明：enum UserAuthType<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthType；<br>API声明：PIN = 1<br>差异内容：NA|类名：UserAuthType；<br>API声明：PIN = 1<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthType；<br>API声明：FACE = 2<br>差异内容：NA|类名：UserAuthType；<br>API声明：FACE = 2<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthType；<br>API声明：FINGERPRINT = 4<br>差异内容：NA|类名：UserAuthType；<br>API声明：FINGERPRINT = 4<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：userAuth；<br>API声明：enum AuthTrustLevel<br>差异内容：NA|类名：userAuth；<br>API声明：enum AuthTrustLevel<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：AuthTrustLevel；<br>API声明：ATL1 = 10000<br>差异内容：NA|类名：AuthTrustLevel；<br>API声明：ATL1 = 10000<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：AuthTrustLevel；<br>API声明：ATL2 = 20000<br>差异内容：NA|类名：AuthTrustLevel；<br>API声明：ATL2 = 20000<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：AuthTrustLevel；<br>API声明：ATL3 = 30000<br>差异内容：NA|类名：AuthTrustLevel；<br>API声明：ATL3 = 30000<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：AuthTrustLevel；<br>API声明：ATL4 = 40000<br>差异内容：NA|类名：AuthTrustLevel；<br>API声明：ATL4 = 40000<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：userAuth；<br>API声明：function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void;<br>差异内容：NA|类名：userAuth；<br>API声明：function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：userAuth；<br>API声明：interface AuthParam<br>差异内容：NA|类名：userAuth；<br>API声明：interface AuthParam<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：AuthParam；<br>API声明：challenge: Uint8Array;<br>差异内容：NA|类名：AuthParam；<br>API声明：challenge: Uint8Array;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：AuthParam；<br>API声明：authType: UserAuthType[];<br>差异内容：NA|类名：AuthParam；<br>API声明：authType: UserAuthType[];<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：AuthParam；<br>API声明：authTrustLevel: AuthTrustLevel;<br>差异内容：NA|类名：AuthParam；<br>API声明：authTrustLevel: AuthTrustLevel;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：userAuth；<br>API声明：interface WidgetParam<br>差异内容：NA|类名：userAuth；<br>API声明：interface WidgetParam<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：WidgetParam；<br>API声明：title: string;<br>差异内容：NA|类名：WidgetParam；<br>API声明：title: string;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：WidgetParam；<br>API声明：navigationButtonText?: string;<br>差异内容：NA|类名：WidgetParam；<br>API声明：navigationButtonText?: string;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：userAuth；<br>API声明：interface UserAuthResult<br>差异内容：NA|类名：userAuth；<br>API声明：interface UserAuthResult<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResult；<br>API声明：result: number;<br>差异内容：NA|类名：UserAuthResult；<br>API声明：result: number;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResult；<br>API声明：token?: Uint8Array;<br>差异内容：NA|类名：UserAuthResult；<br>API声明：token?: Uint8Array;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResult；<br>API声明：authType?: UserAuthType;<br>差异内容：NA|类名：UserAuthResult；<br>API声明：authType?: UserAuthType;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：userAuth；<br>API声明：interface IAuthCallback<br>差异内容：NA|类名：userAuth；<br>API声明：interface IAuthCallback<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：IAuthCallback；<br>API声明：onResult(result: UserAuthResult): void;<br>差异内容：NA|类名：IAuthCallback；<br>API声明：onResult(result: UserAuthResult): void;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：userAuth；<br>API声明：interface UserAuthInstance<br>差异内容：NA|类名：userAuth；<br>API声明：interface UserAuthInstance<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthInstance；<br>API声明：on(type: 'result', callback: IAuthCallback): void;<br>差异内容：NA|类名：UserAuthInstance；<br>API声明：on(type: 'result', callback: IAuthCallback): void;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthInstance；<br>API声明：off(type: 'result', callback?: IAuthCallback): void;<br>差异内容：NA|类名：UserAuthInstance；<br>API声明：off(type: 'result', callback?: IAuthCallback): void;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthInstance；<br>API声明：start(): void;<br>差异内容：NA|类名：UserAuthInstance；<br>API声明：start(): void;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthInstance；<br>API声明：cancel(): void;<br>差异内容：NA|类名：UserAuthInstance；<br>API声明：cancel(): void;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：userAuth；<br>API声明：function getUserAuthInstance(authParam: AuthParam, widgetParam: WidgetParam): UserAuthInstance;<br>差异内容：NA|类名：userAuth；<br>API声明：function getUserAuthInstance(authParam: AuthParam, widgetParam: WidgetParam): UserAuthInstance;<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：userAuth；<br>API声明：enum UserAuthResultCode<br>差异内容：NA|类名：userAuth；<br>API声明：enum UserAuthResultCode<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResultCode；<br>API声明：SUCCESS = 12500000<br>差异内容：NA|类名：UserAuthResultCode；<br>API声明：SUCCESS = 12500000<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResultCode；<br>API声明：FAIL = 12500001<br>差异内容：NA|类名：UserAuthResultCode；<br>API声明：FAIL = 12500001<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResultCode；<br>API声明：GENERAL_ERROR = 12500002<br>差异内容：NA|类名：UserAuthResultCode；<br>API声明：GENERAL_ERROR = 12500002<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResultCode；<br>API声明：CANCELED = 12500003<br>差异内容：NA|类名：UserAuthResultCode；<br>API声明：CANCELED = 12500003<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResultCode；<br>API声明：TIMEOUT = 12500004<br>差异内容：NA|类名：UserAuthResultCode；<br>API声明：TIMEOUT = 12500004<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResultCode；<br>API声明：TYPE_NOT_SUPPORT = 12500005<br>差异内容：NA|类名：UserAuthResultCode；<br>API声明：TYPE_NOT_SUPPORT = 12500005<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResultCode；<br>API声明：TRUST_LEVEL_NOT_SUPPORT = 12500006<br>差异内容：NA|类名：UserAuthResultCode；<br>API声明：TRUST_LEVEL_NOT_SUPPORT = 12500006<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResultCode；<br>API声明：BUSY = 12500007<br>差异内容：NA|类名：UserAuthResultCode；<br>API声明：BUSY = 12500007<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResultCode；<br>API声明：LOCKED = 12500009<br>差异内容：NA|类名：UserAuthResultCode；<br>API声明：LOCKED = 12500009<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResultCode；<br>API声明：NOT_ENROLLED = 12500010<br>差异内容：NA|类名：UserAuthResultCode；<br>API声明：NOT_ENROLLED = 12500010<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
|API从不支持元服务到支持元服务|类名：UserAuthResultCode；<br>API声明：CANCELED_FROM_WIDGET = 12500011<br>差异内容：NA|类名：UserAuthResultCode；<br>API声明：CANCELED_FROM_WIDGET = 12500011<br>差异内容：atomicservice|api/@ohos.userIAM.userAuth.d.ts|
