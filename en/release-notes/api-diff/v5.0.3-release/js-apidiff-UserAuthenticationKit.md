| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|Deleted error code|Class name: UserAuthInstance;<br>API declaration: start(): void;<br>DIfferences: 12500001,12500004,12500007|Class name: UserAuthInstance;<br>API declaration: start(): void;<br>DIfferences: NA|api/@ohos.userIAM.userAuth.d.ts|
|Permission change|Class name: UserAuthInstance;<br>API declaration: start(): void;<br>DIfferences: ohos.permission.ACCESS_BIOMETRIC|Class name: UserAuthInstance;<br>API declaration: start(): void;<br>DIfferences: ohos.permission.ACCESS_BIOMETRIC or ohos.permission.USER_AUTH_FROM_BACKGROUND|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace userAccessCtrl<br>DIfferences: declare namespace userAccessCtrl|api/@ohos.userIAM.userAccessCtrl.d.ts|
|New API |NA|Class name: AuthParam;<br>API declaration: skipLockedBiometricAuth?: boolean;<br>DIfferences: skipLockedBiometricAuth?: boolean;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: WidgetParam;<br>API declaration: uiContext?: Context;<br>DIfferences: uiContext?: Context;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: enum UserAuthTipCode<br>DIfferences: enum UserAuthTipCode|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthTipCode;<br>API declaration: COMPARE_FAILURE = 1<br>DIfferences: COMPARE_FAILURE = 1|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthTipCode;<br>API declaration: TIMEOUT = 2<br>DIfferences: TIMEOUT = 2|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthTipCode;<br>API declaration: TEMPORARILY_LOCKED = 3<br>DIfferences: TEMPORARILY_LOCKED = 3|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthTipCode;<br>API declaration: PERMANENTLY_LOCKED = 4<br>DIfferences: PERMANENTLY_LOCKED = 4|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthTipCode;<br>API declaration: WIDGET_LOADED = 5<br>DIfferences: WIDGET_LOADED = 5|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthTipCode;<br>API declaration: WIDGET_RELEASED = 6<br>DIfferences: WIDGET_RELEASED = 6|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthTipCode;<br>API declaration: COMPARE_FAILURE_WITH_FROZEN = 7<br>DIfferences: COMPARE_FAILURE_WITH_FROZEN = 7|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: interface AuthTipInfo<br>DIfferences: interface AuthTipInfo|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthTipInfo;<br>API declaration: tipType: UserAuthType;<br>DIfferences: tipType: UserAuthType;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: AuthTipInfo;<br>API declaration: tipCode: UserAuthTipCode;<br>DIfferences: tipCode: UserAuthTipCode;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: userAuth;<br>API declaration: type AuthTipCallback = (authTipInfo: AuthTipInfo) => void;<br>DIfferences: type AuthTipCallback = (authTipInfo: AuthTipInfo) => void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthInstance;<br>API declaration: on(type: 'authTip', callback: AuthTipCallback): void;<br>DIfferences: on(type: 'authTip', callback: AuthTipCallback): void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthInstance;<br>API declaration: off(type: 'authTip', callback?: AuthTipCallback): void;<br>DIfferences: off(type: 'authTip', callback?: AuthTipCallback): void;|api/@ohos.userIAM.userAuth.d.ts|
|New API |NA|Class name: UserAuthResultCode;<br>API declaration: INVALID_PARAMETERS = 12500008<br>DIfferences: INVALID_PARAMETERS = 12500008|api/@ohos.userIAM.userAuth.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>DIfferences: NA|Class name: global;<br>API declaration: api\@ohos.userIAM.userAccessCtrl.d.ts<br>DIfferences: UserAuthenticationKit|api/@ohos.userIAM.userAccessCtrl.d.ts|
