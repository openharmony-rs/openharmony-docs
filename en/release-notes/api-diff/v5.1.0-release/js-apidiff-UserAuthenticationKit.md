| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New error code|Class name: UserAuthInstance;<br>API declaration: start(): void;<br>DIfferences: NA|Class name: UserAuthInstance;<br>API declaration: start(): void;<br>DIfferences: 12500001,12500004,12500007|api/@ohos.userIAM.userAuth.d.ts|
|Permission change|Class name: UserAuthInstance;<br>API declaration: start(): void;<br>DIfferences: ohos.permission.ACCESS_BIOMETRIC or ohos.permission.USER_AUTH_FROM_BACKGROUND|Class name: UserAuthInstance;<br>API declaration: start(): void;<br>DIfferences: ohos.permission.ACCESS_BIOMETRIC|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: global;<br>API declaration: declare namespace userAccessCtrl<br>DIfferences: declare namespace userAccessCtrl|NA|api/@ohos.userIAM.userAccessCtrl.d.ts|
| Deleted API|Class name: AuthParam;<br>API declaration: skipLockedBiometricAuth?: boolean;<br>DIfferences: skipLockedBiometricAuth?: boolean;|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: WidgetParam;<br>API declaration: uiContext?: Context;<br>DIfferences: uiContext?: Context;|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: userAuth;<br>API declaration: enum UserAuthTipCode<br>DIfferences: enum UserAuthTipCode|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: UserAuthTipCode;<br>API declaration: COMPARE_FAILURE = 1<br>DIfferences: COMPARE_FAILURE = 1|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: UserAuthTipCode;<br>API declaration: TIMEOUT = 2<br>DIfferences: TIMEOUT = 2|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: UserAuthTipCode;<br>API declaration: TEMPORARILY_LOCKED = 3<br>DIfferences: TEMPORARILY_LOCKED = 3|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: UserAuthTipCode;<br>API declaration: PERMANENTLY_LOCKED = 4<br>DIfferences: PERMANENTLY_LOCKED = 4|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: UserAuthTipCode;<br>API declaration: WIDGET_LOADED = 5<br>DIfferences: WIDGET_LOADED = 5|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: UserAuthTipCode;<br>API declaration: WIDGET_RELEASED = 6<br>DIfferences: WIDGET_RELEASED = 6|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: UserAuthTipCode;<br>API declaration: COMPARE_FAILURE_WITH_FROZEN = 7<br>DIfferences: COMPARE_FAILURE_WITH_FROZEN = 7|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: userAuth;<br>API declaration: interface AuthTipInfo<br>DIfferences: interface AuthTipInfo|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: AuthTipInfo;<br>API declaration: tipType: UserAuthType;<br>DIfferences: tipType: UserAuthType;|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: AuthTipInfo;<br>API declaration: tipCode: UserAuthTipCode;<br>DIfferences: tipCode: UserAuthTipCode;|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: userAuth;<br>API declaration: type AuthTipCallback = (authTipInfo: AuthTipInfo) => void;<br>DIfferences: type AuthTipCallback = (authTipInfo: AuthTipInfo) => void;|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: UserAuthInstance;<br>API declaration: on(type: 'authTip', callback: AuthTipCallback): void;<br>DIfferences: on(type: 'authTip', callback: AuthTipCallback): void;|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: UserAuthInstance;<br>API declaration: off(type: 'authTip', callback?: AuthTipCallback): void;<br>DIfferences: off(type: 'authTip', callback?: AuthTipCallback): void;|NA|api/@ohos.userIAM.userAuth.d.ts|
| Deleted API|Class name: UserAuthResultCode;<br>API declaration: INVALID_PARAMETERS = 12500008<br>DIfferences: INVALID_PARAMETERS = 12500008|NA|api/@ohos.userIAM.userAuth.d.ts|
|Deleted kit|Class name: global;<br>API declaration: api\@ohos.userIAM.userAccessCtrl.d.ts<br>DIfferences: UserAuthenticationKit|Class name: global;<br>API declaration: <br>DIfferences: NA|api/@ohos.userIAM.userAccessCtrl.d.ts|
