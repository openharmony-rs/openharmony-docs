| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace faceAuth<br>差异内容：declare namespace faceAuth|api/@ohos.userIAM.faceAuth.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace userAuth<br>差异内容：declare namespace userAuth|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：export enum AuthenticationResult<br>差异内容：export enum AuthenticationResult|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthenticationResult；<br>API声明：NO_SUPPORT = -1<br>差异内容：NO_SUPPORT = -1|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthenticationResult；<br>API声明：SUCCESS = 0<br>差异内容：SUCCESS = 0|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthenticationResult；<br>API声明：COMPARE_FAILURE = 1<br>差异内容：COMPARE_FAILURE = 1|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthenticationResult；<br>API声明：CANCELED = 2<br>差异内容：CANCELED = 2|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthenticationResult；<br>API声明：TIMEOUT = 3<br>差异内容：TIMEOUT = 3|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthenticationResult；<br>API声明：CAMERA_FAIL = 4<br>差异内容：CAMERA_FAIL = 4|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthenticationResult；<br>API声明：BUSY = 5<br>差异内容：BUSY = 5|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthenticationResult；<br>API声明：INVALID_PARAMETERS = 6<br>差异内容：INVALID_PARAMETERS = 6|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthenticationResult；<br>API声明：LOCKED = 7<br>差异内容：LOCKED = 7|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthenticationResult；<br>API声明：NOT_ENROLLED = 8<br>差异内容：NOT_ENROLLED = 8|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthenticationResult；<br>API声明：GENERAL_ERROR = 100<br>差异内容：GENERAL_ERROR = 100|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：type AuthType = 'ALL' \| 'FACE_ONLY';<br>差异内容：type AuthType = 'ALL' \| 'FACE_ONLY';|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：type SecureLevel = 'S1' \| 'S2' \| 'S3' \| 'S4';<br>差异内容：type SecureLevel = 'S1' \| 'S2' \| 'S3' \| 'S4';|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface Authenticator<br>差异内容：interface Authenticator|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：Authenticator；<br>API声明：execute(type: AuthType, level: SecureLevel, callback: AsyncCallback\<number>): void;<br>差异内容：execute(type: AuthType, level: SecureLevel, callback: AsyncCallback\<number>): void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：Authenticator；<br>API声明：execute(type: AuthType, level: SecureLevel): Promise\<number>;<br>差异内容：execute(type: AuthType, level: SecureLevel): Promise\<number>;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：function getAuthenticator(): Authenticator;<br>差异内容：function getAuthenticator(): Authenticator;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：class UserAuth<br>差异内容：class UserAuth|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuth；<br>API声明：getVersion(): number;<br>差异内容：getVersion(): number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuth；<br>API声明：getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): number;<br>差异内容：getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuth；<br>API声明：auth(challenge: Uint8Array, authType: UserAuthType, authTrustLevel: AuthTrustLevel, callback: IUserAuthCallback): Uint8Array;<br>差异内容：auth(challenge: Uint8Array, authType: UserAuthType, authTrustLevel: AuthTrustLevel, callback: IUserAuthCallback): Uint8Array;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuth；<br>API声明：cancelAuth(contextID: Uint8Array): number;<br>差异内容：cancelAuth(contextID: Uint8Array): number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface IUserAuthCallback<br>差异内容：interface IUserAuthCallback|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：IUserAuthCallback；<br>API声明：onResult: (result: number, extraInfo: AuthResult) => void;<br>差异内容：onResult: (result: number, extraInfo: AuthResult) => void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：IUserAuthCallback；<br>API声明：onAcquireInfo?: (module: number, acquire: number, extraInfo: any) => void;<br>差异内容：onAcquireInfo?: (module: number, acquire: number, extraInfo: any) => void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface AuthResult<br>差异内容：interface AuthResult|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthResult；<br>API声明：token?: Uint8Array;<br>差异内容：token?: Uint8Array;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthResult；<br>API声明：remainTimes?: number;<br>差异内容：remainTimes?: number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthResult；<br>API声明：freezingTime?: number;<br>差异内容：freezingTime?: number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：enum ResultCode<br>差异内容：enum ResultCode|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：SUCCESS = 0<br>差异内容：SUCCESS = 0|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：FAIL = 1<br>差异内容：FAIL = 1|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：GENERAL_ERROR = 2<br>差异内容：GENERAL_ERROR = 2|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：CANCELED = 3<br>差异内容：CANCELED = 3|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：TIMEOUT = 4<br>差异内容：TIMEOUT = 4|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：TYPE_NOT_SUPPORT = 5<br>差异内容：TYPE_NOT_SUPPORT = 5|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：TRUST_LEVEL_NOT_SUPPORT = 6<br>差异内容：TRUST_LEVEL_NOT_SUPPORT = 6|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：BUSY = 7<br>差异内容：BUSY = 7|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：INVALID_PARAMETERS = 8<br>差异内容：INVALID_PARAMETERS = 8|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：LOCKED = 9<br>差异内容：LOCKED = 9|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：NOT_ENROLLED = 10<br>差异内容：NOT_ENROLLED = 10|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：enum FaceTips<br>差异内容：enum FaceTips|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FaceTips；<br>API声明：FACE_AUTH_TIP_TOO_BRIGHT = 1<br>差异内容：FACE_AUTH_TIP_TOO_BRIGHT = 1|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FaceTips；<br>API声明：FACE_AUTH_TIP_TOO_DARK = 2<br>差异内容：FACE_AUTH_TIP_TOO_DARK = 2|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FaceTips；<br>API声明：FACE_AUTH_TIP_TOO_CLOSE = 3<br>差异内容：FACE_AUTH_TIP_TOO_CLOSE = 3|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FaceTips；<br>API声明：FACE_AUTH_TIP_TOO_FAR = 4<br>差异内容：FACE_AUTH_TIP_TOO_FAR = 4|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FaceTips；<br>API声明：FACE_AUTH_TIP_TOO_HIGH = 5<br>差异内容：FACE_AUTH_TIP_TOO_HIGH = 5|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FaceTips；<br>API声明：FACE_AUTH_TIP_TOO_LOW = 6<br>差异内容：FACE_AUTH_TIP_TOO_LOW = 6|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FaceTips；<br>API声明：FACE_AUTH_TIP_TOO_RIGHT = 7<br>差异内容：FACE_AUTH_TIP_TOO_RIGHT = 7|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FaceTips；<br>API声明：FACE_AUTH_TIP_TOO_LEFT = 8<br>差异内容：FACE_AUTH_TIP_TOO_LEFT = 8|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FaceTips；<br>API声明：FACE_AUTH_TIP_TOO_MUCH_MOTION = 9<br>差异内容：FACE_AUTH_TIP_TOO_MUCH_MOTION = 9|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FaceTips；<br>API声明：FACE_AUTH_TIP_POOR_GAZE = 10<br>差异内容：FACE_AUTH_TIP_POOR_GAZE = 10|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FaceTips；<br>API声明：FACE_AUTH_TIP_NOT_DETECTED = 11<br>差异内容：FACE_AUTH_TIP_NOT_DETECTED = 11|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：enum FingerprintTips<br>差异内容：enum FingerprintTips|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FingerprintTips；<br>API声明：FINGERPRINT_AUTH_TIP_GOOD = 0<br>差异内容：FINGERPRINT_AUTH_TIP_GOOD = 0|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FingerprintTips；<br>API声明：FINGERPRINT_AUTH_TIP_DIRTY = 1<br>差异内容：FINGERPRINT_AUTH_TIP_DIRTY = 1|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FingerprintTips；<br>API声明：FINGERPRINT_AUTH_TIP_INSUFFICIENT = 2<br>差异内容：FINGERPRINT_AUTH_TIP_INSUFFICIENT = 2|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FingerprintTips；<br>API声明：FINGERPRINT_AUTH_TIP_PARTIAL = 3<br>差异内容：FINGERPRINT_AUTH_TIP_PARTIAL = 3|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FingerprintTips；<br>API声明：FINGERPRINT_AUTH_TIP_TOO_FAST = 4<br>差异内容：FINGERPRINT_AUTH_TIP_TOO_FAST = 4|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：FingerprintTips；<br>API声明：FINGERPRINT_AUTH_TIP_TOO_SLOW = 5<br>差异内容：FINGERPRINT_AUTH_TIP_TOO_SLOW = 5|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：enum UserAuthType<br>差异内容：enum UserAuthType|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthType；<br>API声明：PIN = 1<br>差异内容：PIN = 1|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthType；<br>API声明：FACE = 2<br>差异内容：FACE = 2|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthType；<br>API声明：FINGERPRINT = 4<br>差异内容：FINGERPRINT = 4|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：enum AuthTrustLevel<br>差异内容：enum AuthTrustLevel|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthTrustLevel；<br>API声明：ATL1 = 10000<br>差异内容：ATL1 = 10000|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthTrustLevel；<br>API声明：ATL2 = 20000<br>差异内容：ATL2 = 20000|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthTrustLevel；<br>API声明：ATL3 = 30000<br>差异内容：ATL3 = 30000|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthTrustLevel；<br>API声明：ATL4 = 40000<br>差异内容：ATL4 = 40000|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：type AuthEventKey = 'result' \| 'tip';<br>差异内容：type AuthEventKey = 'result' \| 'tip';|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：type EventInfo = AuthResultInfo \| TipInfo;<br>差异内容：type EventInfo = AuthResultInfo \| TipInfo;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface AuthEvent<br>差异内容：interface AuthEvent|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthEvent；<br>API声明：callback(result: EventInfo): void;<br>差异内容：callback(result: EventInfo): void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface AuthResultInfo<br>差异内容：interface AuthResultInfo|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthResultInfo；<br>API声明：result: number;<br>差异内容：result: number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthResultInfo；<br>API声明：token?: Uint8Array;<br>差异内容：token?: Uint8Array;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthResultInfo；<br>API声明：remainAttempts?: number;<br>差异内容：remainAttempts?: number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthResultInfo；<br>API声明：lockoutDuration?: number;<br>差异内容：lockoutDuration?: number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface TipInfo<br>差异内容：interface TipInfo|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：TipInfo；<br>API声明：module: number;<br>差异内容：module: number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：TipInfo；<br>API声明：tip: number;<br>差异内容：tip: number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface AuthInstance<br>差异内容：interface AuthInstance|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthInstance；<br>API声明：on: (name: AuthEventKey, callback: AuthEvent) => void;<br>差异内容：on: (name: AuthEventKey, callback: AuthEvent) => void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthInstance；<br>API声明：off: (name: AuthEventKey) => void;<br>差异内容：off: (name: AuthEventKey) => void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthInstance；<br>API声明：start: () => void;<br>差异内容：start: () => void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthInstance；<br>API声明：cancel: () => void;<br>差异内容：cancel: () => void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void;<br>差异内容：function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：function getAuthInstance(challenge: Uint8Array, authType: UserAuthType, authTrustLevel: AuthTrustLevel): AuthInstance;<br>差异内容：function getAuthInstance(challenge: Uint8Array, authType: UserAuthType, authTrustLevel: AuthTrustLevel): AuthInstance;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface AuthParam<br>差异内容：interface AuthParam|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthParam；<br>API声明：challenge: Uint8Array;<br>差异内容：challenge: Uint8Array;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthParam；<br>API声明：authType: UserAuthType[];<br>差异内容：authType: UserAuthType[];|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthParam；<br>API声明：authTrustLevel: AuthTrustLevel;<br>差异内容：authTrustLevel: AuthTrustLevel;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface WidgetParam<br>差异内容：interface WidgetParam|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：WidgetParam；<br>API声明：title: string;<br>差异内容：title: string;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：WidgetParam；<br>API声明：navigationButtonText?: string;<br>差异内容：navigationButtonText?: string;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface UserAuthResult<br>差异内容：interface UserAuthResult|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResult；<br>API声明：result: number;<br>差异内容：result: number;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResult；<br>API声明：token?: Uint8Array;<br>差异内容：token?: Uint8Array;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResult；<br>API声明：authType?: UserAuthType;<br>差异内容：authType?: UserAuthType;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface IAuthCallback<br>差异内容：interface IAuthCallback|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：IAuthCallback；<br>API声明：onResult(result: UserAuthResult): void;<br>差异内容：onResult(result: UserAuthResult): void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface UserAuthInstance<br>差异内容：interface UserAuthInstance|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthInstance；<br>API声明：on(type: 'result', callback: IAuthCallback): void;<br>差异内容：on(type: 'result', callback: IAuthCallback): void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthInstance；<br>API声明：off(type: 'result', callback?: IAuthCallback): void;<br>差异内容：off(type: 'result', callback?: IAuthCallback): void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthInstance；<br>API声明：start(): void;<br>差异内容：start(): void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthInstance；<br>API声明：cancel(): void;<br>差异内容：cancel(): void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：function getUserAuthInstance(authParam: AuthParam, widgetParam: WidgetParam): UserAuthInstance;<br>差异内容：function getUserAuthInstance(authParam: AuthParam, widgetParam: WidgetParam): UserAuthInstance;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：enum UserAuthResultCode<br>差异内容：enum UserAuthResultCode|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：SUCCESS = 12500000<br>差异内容：SUCCESS = 12500000|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：FAIL = 12500001<br>差异内容：FAIL = 12500001|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：GENERAL_ERROR = 12500002<br>差异内容：GENERAL_ERROR = 12500002|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：CANCELED = 12500003<br>差异内容：CANCELED = 12500003|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：TIMEOUT = 12500004<br>差异内容：TIMEOUT = 12500004|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：TYPE_NOT_SUPPORT = 12500005<br>差异内容：TYPE_NOT_SUPPORT = 12500005|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：TRUST_LEVEL_NOT_SUPPORT = 12500006<br>差异内容：TRUST_LEVEL_NOT_SUPPORT = 12500006|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：BUSY = 12500007<br>差异内容：BUSY = 12500007|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：LOCKED = 12500009<br>差异内容：LOCKED = 12500009|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：NOT_ENROLLED = 12500010<br>差异内容：NOT_ENROLLED = 12500010|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：CANCELED_FROM_WIDGET = 12500011<br>差异内容：CANCELED_FROM_WIDGET = 12500011|api/@ohos.userIAM.userAuth.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.userIAM.faceAuth.d.ts<br>差异内容：UserAuthenticationKit|api/@ohos.userIAM.faceAuth.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.userIAM.userAuth.d.ts<br>差异内容：UserAuthenticationKit|api/@ohos.userIAM.userAuth.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.UserAuthenticationKit.d.ts<br>差异内容：UserAuthenticationKit|kits/@kit.UserAuthenticationKit.d.ts|
