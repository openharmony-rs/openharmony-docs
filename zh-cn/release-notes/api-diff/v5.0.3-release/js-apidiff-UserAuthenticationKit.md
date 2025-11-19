| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|删除错误码|类名：UserAuthInstance；<br>API声明：start(): void;<br>差异内容：12500001,12500004,12500007|类名：UserAuthInstance；<br>API声明：start(): void;<br>差异内容：NA|api/@ohos.userIAM.userAuth.d.ts|
|权限变更|类名：UserAuthInstance；<br>API声明：start(): void;<br>差异内容：ohos.permission.ACCESS_BIOMETRIC|类名：UserAuthInstance；<br>API声明：start(): void;<br>差异内容：ohos.permission.ACCESS_BIOMETRIC or ohos.permission.USER_AUTH_FROM_BACKGROUND|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace userAccessCtrl<br>差异内容：declare namespace userAccessCtrl|api/@ohos.userIAM.userAccessCtrl.d.ts|
|新增API|NA|类名：AuthParam；<br>API声明：skipLockedBiometricAuth?: boolean;<br>差异内容：skipLockedBiometricAuth?: boolean;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：WidgetParam；<br>API声明：uiContext?: Context;<br>差异内容：uiContext?: Context;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：enum UserAuthTipCode<br>差异内容：enum UserAuthTipCode|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthTipCode；<br>API声明：COMPARE_FAILURE = 1<br>差异内容：COMPARE_FAILURE = 1|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthTipCode；<br>API声明：TIMEOUT = 2<br>差异内容：TIMEOUT = 2|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthTipCode；<br>API声明：TEMPORARILY_LOCKED = 3<br>差异内容：TEMPORARILY_LOCKED = 3|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthTipCode；<br>API声明：PERMANENTLY_LOCKED = 4<br>差异内容：PERMANENTLY_LOCKED = 4|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthTipCode；<br>API声明：WIDGET_LOADED = 5<br>差异内容：WIDGET_LOADED = 5|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthTipCode；<br>API声明：WIDGET_RELEASED = 6<br>差异内容：WIDGET_RELEASED = 6|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthTipCode；<br>API声明：COMPARE_FAILURE_WITH_FROZEN = 7<br>差异内容：COMPARE_FAILURE_WITH_FROZEN = 7|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：interface AuthTipInfo<br>差异内容：interface AuthTipInfo|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthTipInfo；<br>API声明：tipType: UserAuthType;<br>差异内容：tipType: UserAuthType;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：AuthTipInfo；<br>API声明：tipCode: UserAuthTipCode;<br>差异内容：tipCode: UserAuthTipCode;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：userAuth；<br>API声明：type AuthTipCallback = (authTipInfo: AuthTipInfo) => void;<br>差异内容：type AuthTipCallback = (authTipInfo: AuthTipInfo) => void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthInstance；<br>API声明：on(type: 'authTip', callback: AuthTipCallback): void;<br>差异内容：on(type: 'authTip', callback: AuthTipCallback): void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthInstance；<br>API声明：off(type: 'authTip', callback?: AuthTipCallback): void;<br>差异内容：off(type: 'authTip', callback?: AuthTipCallback): void;|api/@ohos.userIAM.userAuth.d.ts|
|新增API|NA|类名：UserAuthResultCode；<br>API声明：INVALID_PARAMETERS = 12500008<br>差异内容：INVALID_PARAMETERS = 12500008|api/@ohos.userIAM.userAuth.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.userIAM.userAccessCtrl.d.ts<br>差异内容：UserAuthenticationKit|api/@ohos.userIAM.userAccessCtrl.d.ts|
