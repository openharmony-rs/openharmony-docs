| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace faceAuth<br>Differences: declare namespace faceAuth|api/@ohos.userIAM.faceAuth.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace userAuth<br>Differences: declare namespace userAuth|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: export enum AuthenticationResult<br>Differences: export enum AuthenticationResult|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthenticationResult;<br>API declaration: NO_SUPPORT = -1<br>Differences: NO_SUPPORT = -1|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthenticationResult;<br>API declaration: SUCCESS = 0<br>Differences: SUCCESS = 0|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthenticationResult;<br>API declaration: COMPARE_FAILURE = 1<br>Differences: COMPARE_FAILURE = 1|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthenticationResult;<br>API declaration: CANCELED = 2<br>Differences: CANCELED = 2|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthenticationResult;<br>API declaration: TIMEOUT = 3<br>Differences: TIMEOUT = 3|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthenticationResult;<br>API declaration: CAMERA_FAIL = 4<br>Differences: CAMERA_FAIL = 4|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthenticationResult;<br>API declaration: BUSY = 5<br>Differences: BUSY = 5|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthenticationResult;<br>API declaration: INVALID_PARAMETERS = 6<br>Differences: INVALID_PARAMETERS = 6|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthenticationResult;<br>API declaration: LOCKED = 7<br>Differences: LOCKED = 7|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthenticationResult;<br>API declaration: NOT_ENROLLED = 8<br>Differences: NOT_ENROLLED = 8|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthenticationResult;<br>API declaration: GENERAL_ERROR = 100<br>Differences: GENERAL_ERROR = 100|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: type AuthType = 'ALL' \| 'FACE_ONLY';<br>Differences: type AuthType = 'ALL' \| 'FACE_ONLY';|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: type SecureLevel = 'S1' \| 'S2' \| 'S3' \| 'S4';<br>Differences: type SecureLevel = 'S1' \| 'S2' \| 'S3' \| 'S4';|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface Authenticator<br>Differences: interface Authenticator|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: Authenticator;<br>API declaration: execute(type: AuthType, level: SecureLevel, callback: AsyncCallback\<number>): void;<br>Differences: execute(type: AuthType, level: SecureLevel, callback: AsyncCallback\<number>): void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: Authenticator;<br>API declaration: execute(type: AuthType, level: SecureLevel): Promise\<number>;<br>Differences: execute(type: AuthType, level: SecureLevel): Promise\<number>;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: function getAuthenticator(): Authenticator;<br>Differences: function getAuthenticator(): Authenticator;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: class UserAuth<br>Differences: class UserAuth|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuth;<br>API declaration: getVersion(): number;<br>Differences: getVersion(): number;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuth;<br>API declaration: getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): number;<br>Differences: getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): number;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuth;<br>API declaration: auth(challenge: Uint8Array, authType: UserAuthType, authTrustLevel: AuthTrustLevel, callback: IUserAuthCallback): Uint8Array;<br>Differences: auth(challenge: Uint8Array, authType: UserAuthType, authTrustLevel: AuthTrustLevel, callback: IUserAuthCallback): Uint8Array;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuth;<br>API declaration: cancelAuth(contextID: Uint8Array): number;<br>Differences: cancelAuth(contextID: Uint8Array): number;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface IUserAuthCallback<br>Differences: interface IUserAuthCallback|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: IUserAuthCallback;<br>API declaration: onResult: (result: number, extraInfo: AuthResult) => void;<br>Differences: onResult: (result: number, extraInfo: AuthResult) => void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: IUserAuthCallback;<br>API declaration: onAcquireInfo?: (module: number, acquire: number, extraInfo: any) => void;<br>Differences: onAcquireInfo?: (module: number, acquire: number, extraInfo: any) => void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface AuthResult<br>Differences: interface AuthResult|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthResult;<br>API declaration: token?: Uint8Array;<br>Differences: token?: Uint8Array;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthResult;<br>API declaration: remainTimes?: number;<br>Differences: remainTimes?: number;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthResult;<br>API declaration: freezingTime?: number;<br>Differences: freezingTime?: number;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: enum ResultCode<br>Differences: enum ResultCode|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: ResultCode;<br>API declaration: SUCCESS = 0<br>Differences: SUCCESS = 0|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: ResultCode;<br>API declaration: FAIL = 1<br>Differences: FAIL = 1|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: ResultCode;<br>API declaration: GENERAL_ERROR = 2<br>Differences: GENERAL_ERROR = 2|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: ResultCode;<br>API declaration: CANCELED = 3<br>Differences: CANCELED = 3|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: ResultCode;<br>API declaration: TIMEOUT = 4<br>Differences: TIMEOUT = 4|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: ResultCode;<br>API declaration: TYPE_NOT_SUPPORT = 5<br>Differences: TYPE_NOT_SUPPORT = 5|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: ResultCode;<br>API declaration: TRUST_LEVEL_NOT_SUPPORT = 6<br>Differences: TRUST_LEVEL_NOT_SUPPORT = 6|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: ResultCode;<br>API declaration: BUSY = 7<br>Differences: BUSY = 7|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: ResultCode;<br>API declaration: INVALID_PARAMETERS = 8<br>Differences: INVALID_PARAMETERS = 8|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: ResultCode;<br>API declaration: LOCKED = 9<br>Differences: LOCKED = 9|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: ResultCode;<br>API declaration: NOT_ENROLLED = 10<br>Differences: NOT_ENROLLED = 10|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: enum FaceTips<br>Differences: enum FaceTips|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FaceTips;<br>API declaration: FACE_AUTH_TIP_TOO_BRIGHT = 1<br>Differences: FACE_AUTH_TIP_TOO_BRIGHT = 1|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FaceTips;<br>API declaration: FACE_AUTH_TIP_TOO_DARK = 2<br>Differences: FACE_AUTH_TIP_TOO_DARK = 2|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FaceTips;<br>API declaration: FACE_AUTH_TIP_TOO_CLOSE = 3<br>Differences: FACE_AUTH_TIP_TOO_CLOSE = 3|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FaceTips;<br>API declaration: FACE_AUTH_TIP_TOO_FAR = 4<br>Differences: FACE_AUTH_TIP_TOO_FAR = 4|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FaceTips;<br>API declaration: FACE_AUTH_TIP_TOO_HIGH = 5<br>Differences: FACE_AUTH_TIP_TOO_HIGH = 5|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FaceTips;<br>API declaration: FACE_AUTH_TIP_TOO_LOW = 6<br>Differences: FACE_AUTH_TIP_TOO_LOW = 6|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FaceTips;<br>API declaration: FACE_AUTH_TIP_TOO_RIGHT = 7<br>Differences: FACE_AUTH_TIP_TOO_RIGHT = 7|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FaceTips;<br>API declaration: FACE_AUTH_TIP_TOO_LEFT = 8<br>Differences: FACE_AUTH_TIP_TOO_LEFT = 8|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FaceTips;<br>API declaration: FACE_AUTH_TIP_TOO_MUCH_MOTION = 9<br>Differences: FACE_AUTH_TIP_TOO_MUCH_MOTION = 9|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FaceTips;<br>API declaration: FACE_AUTH_TIP_POOR_GAZE = 10<br>Differences: FACE_AUTH_TIP_POOR_GAZE = 10|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FaceTips;<br>API declaration: FACE_AUTH_TIP_NOT_DETECTED = 11<br>Differences: FACE_AUTH_TIP_NOT_DETECTED = 11|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: enum FingerprintTips<br>Differences: enum FingerprintTips|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FingerprintTips;<br>API declaration: FINGERPRINT_AUTH_TIP_GOOD = 0<br>Differences: FINGERPRINT_AUTH_TIP_GOOD = 0|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FingerprintTips;<br>API declaration: FINGERPRINT_AUTH_TIP_DIRTY = 1<br>Differences: FINGERPRINT_AUTH_TIP_DIRTY = 1|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FingerprintTips;<br>API declaration: FINGERPRINT_AUTH_TIP_INSUFFICIENT = 2<br>Differences: FINGERPRINT_AUTH_TIP_INSUFFICIENT = 2|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FingerprintTips;<br>API declaration: FINGERPRINT_AUTH_TIP_PARTIAL = 3<br>Differences: FINGERPRINT_AUTH_TIP_PARTIAL = 3|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FingerprintTips;<br>API declaration: FINGERPRINT_AUTH_TIP_TOO_FAST = 4<br>Differences: FINGERPRINT_AUTH_TIP_TOO_FAST = 4|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: FingerprintTips;<br>API declaration: FINGERPRINT_AUTH_TIP_TOO_SLOW = 5<br>Differences: FINGERPRINT_AUTH_TIP_TOO_SLOW = 5|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: enum UserAuthType<br>Differences: enum UserAuthType|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthType;<br>API declaration: PIN = 1<br>Differences: PIN = 1|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthType;<br>API declaration: FACE = 2<br>Differences: FACE = 2|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthType;<br>API declaration: FINGERPRINT = 4<br>Differences: FINGERPRINT = 4|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: enum AuthTrustLevel<br>Differences: enum AuthTrustLevel|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthTrustLevel;<br>API declaration: ATL1 = 10000<br>Differences: ATL1 = 10000|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthTrustLevel;<br>API declaration: ATL2 = 20000<br>Differences: ATL2 = 20000|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthTrustLevel;<br>API declaration: ATL3 = 30000<br>Differences: ATL3 = 30000|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthTrustLevel;<br>API declaration: ATL4 = 40000<br>Differences: ATL4 = 40000|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: type AuthEventKey = 'result' \| 'tip';<br>Differences: type AuthEventKey = 'result' \| 'tip';|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: type EventInfo = AuthResultInfo \| TipInfo;<br>Differences: type EventInfo = AuthResultInfo \| TipInfo;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface AuthEvent<br>Differences: interface AuthEvent|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthEvent;<br>API declaration: callback(result: EventInfo): void;<br>Differences: callback(result: EventInfo): void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface AuthResultInfo<br>Differences: interface AuthResultInfo|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthResultInfo;<br>API declaration: result: number;<br>Differences: result: number;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthResultInfo;<br>API declaration: token?: Uint8Array;<br>Differences: token?: Uint8Array;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthResultInfo;<br>API declaration: remainAttempts?: number;<br>Differences: remainAttempts?: number;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthResultInfo;<br>API declaration: lockoutDuration?: number;<br>Differences: lockoutDuration?: number;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface TipInfo<br>Differences: interface TipInfo|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: TipInfo;<br>API declaration: module: number;<br>Differences: module: number;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: TipInfo;<br>API declaration: tip: number;<br>Differences: tip: number;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface AuthInstance<br>Differences: interface AuthInstance|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthInstance;<br>API declaration: on: (name: AuthEventKey, callback: AuthEvent) => void;<br>Differences: on: (name: AuthEventKey, callback: AuthEvent) => void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthInstance;<br>API declaration: off: (name: AuthEventKey) => void;<br>Differences: off: (name: AuthEventKey) => void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthInstance;<br>API declaration: start: () => void;<br>Differences: start: () => void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthInstance;<br>API declaration: cancel: () => void;<br>Differences: cancel: () => void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void;<br>Differences: function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: function getAuthInstance(challenge: Uint8Array, authType: UserAuthType, authTrustLevel: AuthTrustLevel): AuthInstance;<br>Differences: function getAuthInstance(challenge: Uint8Array, authType: UserAuthType, authTrustLevel: AuthTrustLevel): AuthInstance;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface AuthParam<br>Differences: interface AuthParam|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthParam;<br>API declaration: challenge: Uint8Array;<br>Differences: challenge: Uint8Array;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthParam;<br>API declaration: authType: UserAuthType[];<br>Differences: authType: UserAuthType[];|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthParam;<br>API declaration: authTrustLevel: AuthTrustLevel;<br>Differences: authTrustLevel: AuthTrustLevel;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface WidgetParam<br>Differences: interface WidgetParam|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: WidgetParam;<br>API declaration: title: string;<br>Differences: title: string;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: WidgetParam;<br>API declaration: navigationButtonText?: string;<br>Differences: navigationButtonText?: string;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface UserAuthResult<br>Differences: interface UserAuthResult|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResult;<br>API declaration: result: number;<br>Differences: result: number;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResult;<br>API declaration: token?: Uint8Array;<br>Differences: token?: Uint8Array;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResult;<br>API declaration: authType?: UserAuthType;<br>Differences: authType?: UserAuthType;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface IAuthCallback<br>Differences: interface IAuthCallback|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: IAuthCallback;<br>API declaration: onResult(result: UserAuthResult): void;<br>Differences: onResult(result: UserAuthResult): void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface UserAuthInstance<br>Differences: interface UserAuthInstance|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthInstance;<br>API declaration: on(type: 'result', callback: IAuthCallback): void;<br>Differences: on(type: 'result', callback: IAuthCallback): void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthInstance;<br>API declaration: off(type: 'result', callback?: IAuthCallback): void;<br>Differences: off(type: 'result', callback?: IAuthCallback): void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthInstance;<br>API declaration: start(): void;<br>Differences: start(): void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthInstance;<br>API declaration: cancel(): void;<br>Differences: cancel(): void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: function getUserAuthInstance(authParam: AuthParam, widgetParam: WidgetParam): UserAuthInstance;<br>Differences: function getUserAuthInstance(authParam: AuthParam, widgetParam: WidgetParam): UserAuthInstance;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: enum UserAuthResultCode<br>Differences: enum UserAuthResultCode|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResultCode;<br>API declaration: SUCCESS = 12500000<br>Differences: SUCCESS = 12500000|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResultCode;<br>API declaration: FAIL = 12500001<br>Differences: FAIL = 12500001|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResultCode;<br>API declaration: GENERAL_ERROR = 12500002<br>Differences: GENERAL_ERROR = 12500002|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResultCode;<br>API declaration: CANCELED = 12500003<br>Differences: CANCELED = 12500003|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResultCode;<br>API declaration: TIMEOUT = 12500004<br>Differences: TIMEOUT = 12500004|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResultCode;<br>API declaration: TYPE_NOT_SUPPORT = 12500005<br>Differences: TYPE_NOT_SUPPORT = 12500005|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResultCode;<br>API declaration: TRUST_LEVEL_NOT_SUPPORT = 12500006<br>Differences: TRUST_LEVEL_NOT_SUPPORT = 12500006|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResultCode;<br>API declaration: BUSY = 12500007<br>Differences: BUSY = 12500007|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResultCode;<br>API declaration: LOCKED = 12500009<br>Differences: LOCKED = 12500009|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResultCode;<br>API declaration: NOT_ENROLLED = 12500010<br>Differences: NOT_ENROLLED = 12500010|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResultCode;<br>API declaration: CANCELED_FROM_WIDGET = 12500011<br>Differences: CANCELED_FROM_WIDGET = 12500011|api/@ohos.userIAM.userAuth.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.userIAM.faceAuth.d.ts<br>Differences: UserAuthenticationKit|api/@ohos.userIAM.faceAuth.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.userIAM.userAuth.d.ts<br>Differences: UserAuthenticationKit|api/@ohos.userIAM.userAuth.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.UserAuthenticationKit.d.ts<br>Differences: UserAuthenticationKit|kits/@kit.UserAuthenticationKit.d.ts|
