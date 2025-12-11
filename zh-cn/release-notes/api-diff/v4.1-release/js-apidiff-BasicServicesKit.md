| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace appAccount<br>差异内容：declare namespace appAccount|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：function createAppAccountManager(): AppAccountManager;<br>差异内容：function createAppAccountManager(): AppAccountManager;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface AppAccountManager<br>差异内容：interface AppAccountManager|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：addAccount(name: string, callback: AsyncCallback\<void>): void;<br>差异内容：addAccount(name: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：addAccount(name: string, extraInfo: string, callback: AsyncCallback\<void>): void;<br>差异内容：addAccount(name: string, extraInfo: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：addAccount(name: string, extraInfo?: string): Promise\<void>;<br>差异内容：addAccount(name: string, extraInfo?: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：createAccount(name: string, callback: AsyncCallback\<void>): void;<br>差异内容：createAccount(name: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：createAccount(name: string, options: CreateAccountOptions, callback: AsyncCallback\<void>): void;<br>差异内容：createAccount(name: string, options: CreateAccountOptions, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：createAccount(name: string, options?: CreateAccountOptions): Promise\<void>;<br>差异内容：createAccount(name: string, options?: CreateAccountOptions): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：addAccountImplicitly(owner: string, authType: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;<br>差异内容：addAccountImplicitly(owner: string, authType: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：createAccountImplicitly(owner: string, callback: AuthCallback): void;<br>差异内容：createAccountImplicitly(owner: string, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：createAccountImplicitly(owner: string, options: CreateAccountImplicitlyOptions, callback: AuthCallback): void;<br>差异内容：createAccountImplicitly(owner: string, options: CreateAccountImplicitlyOptions, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：deleteAccount(name: string, callback: AsyncCallback\<void>): void;<br>差异内容：deleteAccount(name: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：deleteAccount(name: string): Promise\<void>;<br>差异内容：deleteAccount(name: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：removeAccount(name: string, callback: AsyncCallback\<void>): void;<br>差异内容：removeAccount(name: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：removeAccount(name: string): Promise\<void>;<br>差异内容：removeAccount(name: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：disableAppAccess(name: string, bundleName: string, callback: AsyncCallback\<void>): void;<br>差异内容：disableAppAccess(name: string, bundleName: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：disableAppAccess(name: string, bundleName: string): Promise\<void>;<br>差异内容：disableAppAccess(name: string, bundleName: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：enableAppAccess(name: string, bundleName: string, callback: AsyncCallback\<void>): void;<br>差异内容：enableAppAccess(name: string, bundleName: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：enableAppAccess(name: string, bundleName: string): Promise\<void>;<br>差异内容：enableAppAccess(name: string, bundleName: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAppAccess(name: string, bundleName: string, isAccessible: boolean): Promise\<void>;<br>差异内容：setAppAccess(name: string, bundleName: string, isAccessible: boolean): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：checkAppAccess(name: string, bundleName: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：checkAppAccess(name: string, bundleName: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：checkAppAccess(name: string, bundleName: string): Promise\<boolean>;<br>差异内容：checkAppAccess(name: string, bundleName: string): Promise\<boolean>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：checkAppAccountSyncEnable(name: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：checkAppAccountSyncEnable(name: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：checkAppAccountSyncEnable(name: string): Promise\<boolean>;<br>差异内容：checkAppAccountSyncEnable(name: string): Promise\<boolean>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：checkDataSyncEnabled(name: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：checkDataSyncEnabled(name: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：checkDataSyncEnabled(name: string): Promise\<boolean>;<br>差异内容：checkDataSyncEnabled(name: string): Promise\<boolean>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAccountCredential(name: string, credentialType: string, credential: string, callback: AsyncCallback\<void>): void;<br>差异内容：setAccountCredential(name: string, credentialType: string, credential: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAccountCredential(name: string, credentialType: string, credential: string): Promise\<void>;<br>差异内容：setAccountCredential(name: string, credentialType: string, credential: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setCredential(name: string, credentialType: string, credential: string, callback: AsyncCallback\<void>): void;<br>差异内容：setCredential(name: string, credentialType: string, credential: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setCredential(name: string, credentialType: string, credential: string): Promise\<void>;<br>差异内容：setCredential(name: string, credentialType: string, credential: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAccountExtraInfo(name: string, extraInfo: string, callback: AsyncCallback\<void>): void;<br>差异内容：setAccountExtraInfo(name: string, extraInfo: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAccountExtraInfo(name: string, extraInfo: string): Promise\<void>;<br>差异内容：setAccountExtraInfo(name: string, extraInfo: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAppAccountSyncEnable(name: string, isEnable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：setAppAccountSyncEnable(name: string, isEnable: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAppAccountSyncEnable(name: string, isEnable: boolean): Promise\<void>;<br>差异内容：setAppAccountSyncEnable(name: string, isEnable: boolean): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setDataSyncEnabled(name: string, isEnabled: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：setDataSyncEnabled(name: string, isEnabled: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setDataSyncEnabled(name: string, isEnabled: boolean): Promise\<void>;<br>差异内容：setDataSyncEnabled(name: string, isEnabled: boolean): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAssociatedData(name: string, key: string, value: string, callback: AsyncCallback\<void>): void;<br>差异内容：setAssociatedData(name: string, key: string, value: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAssociatedData(name: string, key: string, value: string): Promise\<void>;<br>差异内容：setAssociatedData(name: string, key: string, value: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setCustomData(name: string, key: string, value: string, callback: AsyncCallback\<void>): void;<br>差异内容：setCustomData(name: string, key: string, value: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setCustomData(name: string, key: string, value: string): Promise\<void>;<br>差异内容：setCustomData(name: string, key: string, value: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAllAccessibleAccounts(callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>差异内容：getAllAccessibleAccounts(callback: AsyncCallback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAllAccessibleAccounts(): Promise\<Array\<AppAccountInfo>>;<br>差异内容：getAllAccessibleAccounts(): Promise\<Array\<AppAccountInfo>>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAllAccounts(callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>差异内容：getAllAccounts(callback: AsyncCallback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAllAccounts(): Promise\<Array\<AppAccountInfo>>;<br>差异内容：getAllAccounts(): Promise\<Array\<AppAccountInfo>>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAllAccounts(owner: string, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>差异内容：getAllAccounts(owner: string, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAllAccounts(owner: string): Promise\<Array\<AppAccountInfo>>;<br>差异内容：getAllAccounts(owner: string): Promise\<Array\<AppAccountInfo>>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAccountsByOwner(owner: string, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>差异内容：getAccountsByOwner(owner: string, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAccountsByOwner(owner: string): Promise\<Array\<AppAccountInfo>>;<br>差异内容：getAccountsByOwner(owner: string): Promise\<Array\<AppAccountInfo>>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAccountCredential(name: string, credentialType: string, callback: AsyncCallback\<string>): void;<br>差异内容：getAccountCredential(name: string, credentialType: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAccountCredential(name: string, credentialType: string): Promise\<string>;<br>差异内容：getAccountCredential(name: string, credentialType: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getCredential(name: string, credentialType: string, callback: AsyncCallback\<string>): void;<br>差异内容：getCredential(name: string, credentialType: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getCredential(name: string, credentialType: string): Promise\<string>;<br>差异内容：getCredential(name: string, credentialType: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAccountExtraInfo(name: string, callback: AsyncCallback\<string>): void;<br>差异内容：getAccountExtraInfo(name: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAccountExtraInfo(name: string): Promise\<string>;<br>差异内容：getAccountExtraInfo(name: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAssociatedData(name: string, key: string, callback: AsyncCallback\<string>): void;<br>差异内容：getAssociatedData(name: string, key: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAssociatedData(name: string, key: string): Promise\<string>;<br>差异内容：getAssociatedData(name: string, key: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getCustomData(name: string, key: string, callback: AsyncCallback\<string>): void;<br>差异内容：getCustomData(name: string, key: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getCustomData(name: string, key: string): Promise\<string>;<br>差异内容：getCustomData(name: string, key: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getCustomDataSync(name: string, key: string): string;<br>差异内容：getCustomDataSync(name: string, key: string): string;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：on(type: 'change', owners: Array\<string>, callback: Callback\<Array\<AppAccountInfo>>): void;<br>差异内容：on(type: 'change', owners: Array\<string>, callback: Callback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：on(type: 'accountChange', owners: Array\<string>, callback: Callback\<Array\<AppAccountInfo>>): void;<br>差异内容：on(type: 'accountChange', owners: Array\<string>, callback: Callback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：off(type: 'change', callback?: Callback\<Array\<AppAccountInfo>>): void;<br>差异内容：off(type: 'change', callback?: Callback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：off(type: 'accountChange', callback?: Callback\<Array\<AppAccountInfo>>): void;<br>差异内容：off(type: 'accountChange', callback?: Callback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：authenticate(name: string, owner: string, authType: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;<br>差异内容：authenticate(name: string, owner: string, authType: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：auth(name: string, owner: string, authType: string, callback: AuthCallback): void;<br>差异内容：auth(name: string, owner: string, authType: string, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：auth(name: string, owner: string, authType: string, options: Record\<string, Object>, callback: AuthCallback): void;<br>差异内容：auth(name: string, owner: string, authType: string, options: Record\<string, Object>, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getOAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback\<string>): void;<br>差异内容：getOAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getOAuthToken(name: string, owner: string, authType: string): Promise\<string>;<br>差异内容：getOAuthToken(name: string, owner: string, authType: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback\<string>): void;<br>差异内容：getAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAuthToken(name: string, owner: string, authType: string): Promise\<string>;<br>差异内容：getAuthToken(name: string, owner: string, authType: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setOAuthToken(name: string, authType: string, token: string, callback: AsyncCallback\<void>): void;<br>差异内容：setOAuthToken(name: string, authType: string, token: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setOAuthToken(name: string, authType: string, token: string): Promise\<void>;<br>差异内容：setOAuthToken(name: string, authType: string, token: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAuthToken(name: string, authType: string, token: string, callback: AsyncCallback\<void>): void;<br>差异内容：setAuthToken(name: string, authType: string, token: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAuthToken(name: string, authType: string, token: string): Promise\<void>;<br>差异内容：setAuthToken(name: string, authType: string, token: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：deleteOAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback\<void>): void;<br>差异内容：deleteOAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：deleteOAuthToken(name: string, owner: string, authType: string, token: string): Promise\<void>;<br>差异内容：deleteOAuthToken(name: string, owner: string, authType: string, token: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：deleteAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback\<void>): void;<br>差异内容：deleteAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：deleteAuthToken(name: string, owner: string, authType: string, token: string): Promise\<void>;<br>差异内容：deleteAuthToken(name: string, owner: string, authType: string, token: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setOAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：setOAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setOAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise\<void>;<br>差异内容：setOAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise\<void>;<br>差异内容：setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：checkOAuthTokenVisibility(name: string, authType: string, bundleName: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：checkOAuthTokenVisibility(name: string, authType: string, bundleName: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：checkOAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise\<boolean>;<br>差异内容：checkOAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise\<boolean>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：checkAuthTokenVisibility(name: string, authType: string, bundleName: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：checkAuthTokenVisibility(name: string, authType: string, bundleName: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：checkAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise\<boolean>;<br>差异内容：checkAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise\<boolean>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAllOAuthTokens(name: string, owner: string, callback: AsyncCallback\<Array\<OAuthTokenInfo>>): void;<br>差异内容：getAllOAuthTokens(name: string, owner: string, callback: AsyncCallback\<Array\<OAuthTokenInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAllOAuthTokens(name: string, owner: string): Promise\<Array\<OAuthTokenInfo>>;<br>差异内容：getAllOAuthTokens(name: string, owner: string): Promise\<Array\<OAuthTokenInfo>>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAllAuthTokens(name: string, owner: string, callback: AsyncCallback\<Array\<AuthTokenInfo>>): void;<br>差异内容：getAllAuthTokens(name: string, owner: string, callback: AsyncCallback\<Array\<AuthTokenInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAllAuthTokens(name: string, owner: string): Promise\<Array\<AuthTokenInfo>>;<br>差异内容：getAllAuthTokens(name: string, owner: string): Promise\<Array\<AuthTokenInfo>>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getOAuthList(name: string, authType: string, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：getOAuthList(name: string, authType: string, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getOAuthList(name: string, authType: string): Promise\<Array\<string>>;<br>差异内容：getOAuthList(name: string, authType: string): Promise\<Array\<string>>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAuthList(name: string, authType: string, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：getAuthList(name: string, authType: string, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAuthList(name: string, authType: string): Promise\<Array\<string>>;<br>差异内容：getAuthList(name: string, authType: string): Promise\<Array\<string>>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAuthenticatorCallback(sessionId: string, callback: AsyncCallback\<AuthenticatorCallback>): void;<br>差异内容：getAuthenticatorCallback(sessionId: string, callback: AsyncCallback\<AuthenticatorCallback>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAuthenticatorCallback(sessionId: string): Promise\<AuthenticatorCallback>;<br>差异内容：getAuthenticatorCallback(sessionId: string): Promise\<AuthenticatorCallback>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAuthCallback(sessionId: string, callback: AsyncCallback\<AuthCallback>): void;<br>差异内容：getAuthCallback(sessionId: string, callback: AsyncCallback\<AuthCallback>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAuthCallback(sessionId: string): Promise\<AuthCallback>;<br>差异内容：getAuthCallback(sessionId: string): Promise\<AuthCallback>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAuthenticatorInfo(owner: string, callback: AsyncCallback\<AuthenticatorInfo>): void;<br>差异内容：getAuthenticatorInfo(owner: string, callback: AsyncCallback\<AuthenticatorInfo>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：getAuthenticatorInfo(owner: string): Promise\<AuthenticatorInfo>;<br>差异内容：getAuthenticatorInfo(owner: string): Promise\<AuthenticatorInfo>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：queryAuthenticatorInfo(owner: string, callback: AsyncCallback\<AuthenticatorInfo>): void;<br>差异内容：queryAuthenticatorInfo(owner: string, callback: AsyncCallback\<AuthenticatorInfo>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：queryAuthenticatorInfo(owner: string): Promise\<AuthenticatorInfo>;<br>差异内容：queryAuthenticatorInfo(owner: string): Promise\<AuthenticatorInfo>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：checkAccountLabels(name: string, owner: string, labels: Array\<string>, callback: AsyncCallback\<boolean>): void;<br>差异内容：checkAccountLabels(name: string, owner: string, labels: Array\<string>, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：checkAccountLabels(name: string, owner: string, labels: Array\<string>): Promise\<boolean>;<br>差异内容：checkAccountLabels(name: string, owner: string, labels: Array\<string>): Promise\<boolean>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：deleteCredential(name: string, credentialType: string, callback: AsyncCallback\<void>): void;<br>差异内容：deleteCredential(name: string, credentialType: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：deleteCredential(name: string, credentialType: string): Promise\<void>;<br>差异内容：deleteCredential(name: string, credentialType: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：selectAccountsByOptions(options: SelectAccountsOptions, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>差异内容：selectAccountsByOptions(options: SelectAccountsOptions, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：selectAccountsByOptions(options: SelectAccountsOptions): Promise\<Array\<AppAccountInfo>>;<br>差异内容：selectAccountsByOptions(options: SelectAccountsOptions): Promise\<Array\<AppAccountInfo>>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：verifyCredential(name: string, owner: string, callback: AuthCallback): void;<br>差异内容：verifyCredential(name: string, owner: string, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：verifyCredential(name: string, owner: string, options: VerifyCredentialOptions, callback: AuthCallback): void;<br>差异内容：verifyCredential(name: string, owner: string, options: VerifyCredentialOptions, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAuthenticatorProperties(owner: string, callback: AuthCallback): void;<br>差异内容：setAuthenticatorProperties(owner: string, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountManager；<br>API声明：setAuthenticatorProperties(owner: string, options: SetPropertiesOptions, callback: AuthCallback): void;<br>差异内容：setAuthenticatorProperties(owner: string, options: SetPropertiesOptions, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface AppAccountInfo<br>差异内容：interface AppAccountInfo|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountInfo；<br>API声明：owner: string;<br>差异内容：owner: string;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AppAccountInfo；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface OAuthTokenInfo<br>差异内容：interface OAuthTokenInfo|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：OAuthTokenInfo；<br>API声明：authType: string;<br>差异内容：authType: string;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：OAuthTokenInfo；<br>API声明：token: string;<br>差异内容：token: string;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface AuthTokenInfo<br>差异内容：interface AuthTokenInfo|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthTokenInfo；<br>API声明：authType: string;<br>差异内容：authType: string;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthTokenInfo；<br>API声明：token: string;<br>差异内容：token: string;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthTokenInfo；<br>API声明：account?: AppAccountInfo;<br>差异内容：account?: AppAccountInfo;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface AuthenticatorInfo<br>差异内容：interface AuthenticatorInfo|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthenticatorInfo；<br>API声明：owner: string;<br>差异内容：owner: string;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthenticatorInfo；<br>API声明：iconId: number;<br>差异内容：iconId: number;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthenticatorInfo；<br>API声明：labelId: number;<br>差异内容：labelId: number;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface AuthResult<br>差异内容：interface AuthResult|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthResult；<br>API声明：account?: AppAccountInfo;<br>差异内容：account?: AppAccountInfo;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthResult；<br>API声明：tokenInfo?: AuthTokenInfo;<br>差异内容：tokenInfo?: AuthTokenInfo;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface CreateAccountOptions<br>差异内容：interface CreateAccountOptions|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：CreateAccountOptions；<br>API声明：customData?: Record\<string, string>;<br>差异内容：customData?: Record\<string, string>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface CreateAccountImplicitlyOptions<br>差异内容：interface CreateAccountImplicitlyOptions|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：CreateAccountImplicitlyOptions；<br>API声明：requiredLabels?: Array\<string>;<br>差异内容：requiredLabels?: Array\<string>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：CreateAccountImplicitlyOptions；<br>API声明：authType?: string;<br>差异内容：authType?: string;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：CreateAccountImplicitlyOptions；<br>API声明：parameters?: Record\<string, Object>;<br>差异内容：parameters?: Record\<string, Object>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface SelectAccountsOptions<br>差异内容：interface SelectAccountsOptions|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：SelectAccountsOptions；<br>API声明：allowedAccounts?: Array\<AppAccountInfo>;<br>差异内容：allowedAccounts?: Array\<AppAccountInfo>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：SelectAccountsOptions；<br>API声明：allowedOwners?: Array\<string>;<br>差异内容：allowedOwners?: Array\<string>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：SelectAccountsOptions；<br>API声明：requiredLabels?: Array\<string>;<br>差异内容：requiredLabels?: Array\<string>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface VerifyCredentialOptions<br>差异内容：interface VerifyCredentialOptions|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：VerifyCredentialOptions；<br>API声明：credentialType?: string;<br>差异内容：credentialType?: string;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：VerifyCredentialOptions；<br>API声明：credential?: string;<br>差异内容：credential?: string;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：VerifyCredentialOptions；<br>API声明：parameters?: Record\<string, Object>;<br>差异内容：parameters?: Record\<string, Object>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface SetPropertiesOptions<br>差异内容：interface SetPropertiesOptions|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：SetPropertiesOptions；<br>API声明：properties?: Record\<string, Object>;<br>差异内容：properties?: Record\<string, Object>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：SetPropertiesOptions；<br>API声明：parameters?: Record\<string, Object>;<br>差异内容：parameters?: Record\<string, Object>;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：enum Constants<br>差异内容：enum Constants|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：ACTION_ADD_ACCOUNT_IMPLICITLY = 'addAccountImplicitly'<br>差异内容：ACTION_ADD_ACCOUNT_IMPLICITLY = 'addAccountImplicitly'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：ACTION_AUTHENTICATE = 'authenticate'<br>差异内容：ACTION_AUTHENTICATE = 'authenticate'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：ACTION_CREATE_ACCOUNT_IMPLICITLY = 'createAccountImplicitly'<br>差异内容：ACTION_CREATE_ACCOUNT_IMPLICITLY = 'createAccountImplicitly'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：ACTION_AUTH = 'auth'<br>差异内容：ACTION_AUTH = 'auth'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：ACTION_VERIFY_CREDENTIAL = 'verifyCredential'<br>差异内容：ACTION_VERIFY_CREDENTIAL = 'verifyCredential'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：ACTION_SET_AUTHENTICATOR_PROPERTIES = 'setAuthenticatorProperties'<br>差异内容：ACTION_SET_AUTHENTICATOR_PROPERTIES = 'setAuthenticatorProperties'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：KEY_NAME = 'name'<br>差异内容：KEY_NAME = 'name'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：KEY_OWNER = 'owner'<br>差异内容：KEY_OWNER = 'owner'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：KEY_TOKEN = 'token'<br>差异内容：KEY_TOKEN = 'token'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：KEY_ACTION = 'action'<br>差异内容：KEY_ACTION = 'action'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：KEY_AUTH_TYPE = 'authType'<br>差异内容：KEY_AUTH_TYPE = 'authType'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：KEY_SESSION_ID = 'sessionId'<br>差异内容：KEY_SESSION_ID = 'sessionId'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：KEY_CALLER_PID = 'callerPid'<br>差异内容：KEY_CALLER_PID = 'callerPid'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：KEY_CALLER_UID = 'callerUid'<br>差异内容：KEY_CALLER_UID = 'callerUid'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：KEY_CALLER_BUNDLE_NAME = 'callerBundleName'<br>差异内容：KEY_CALLER_BUNDLE_NAME = 'callerBundleName'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：KEY_REQUIRED_LABELS = 'requiredLabels'<br>差异内容：KEY_REQUIRED_LABELS = 'requiredLabels'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Constants；<br>API声明：KEY_BOOLEAN_RESULT = 'booleanResult'<br>差异内容：KEY_BOOLEAN_RESULT = 'booleanResult'|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：enum ResultCode<br>差异内容：enum ResultCode|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：SUCCESS = 0<br>差异内容：SUCCESS = 0|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_ACCOUNT_NOT_EXIST = 10001<br>差异内容：ERROR_ACCOUNT_NOT_EXIST = 10001|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_APP_ACCOUNT_SERVICE_EXCEPTION = 10002<br>差异内容：ERROR_APP_ACCOUNT_SERVICE_EXCEPTION = 10002|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_INVALID_PASSWORD = 10003<br>差异内容：ERROR_INVALID_PASSWORD = 10003|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_INVALID_REQUEST = 10004<br>差异内容：ERROR_INVALID_REQUEST = 10004|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_INVALID_RESPONSE = 10005<br>差异内容：ERROR_INVALID_RESPONSE = 10005|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_NETWORK_EXCEPTION = 10006<br>差异内容：ERROR_NETWORK_EXCEPTION = 10006|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_OAUTH_AUTHENTICATOR_NOT_EXIST = 10007<br>差异内容：ERROR_OAUTH_AUTHENTICATOR_NOT_EXIST = 10007|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_OAUTH_CANCELED = 10008<br>差异内容：ERROR_OAUTH_CANCELED = 10008|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_OAUTH_LIST_TOO_LARGE = 10009<br>差异内容：ERROR_OAUTH_LIST_TOO_LARGE = 10009|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_OAUTH_SERVICE_BUSY = 10010<br>差异内容：ERROR_OAUTH_SERVICE_BUSY = 10010|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_OAUTH_SERVICE_EXCEPTION = 10011<br>差异内容：ERROR_OAUTH_SERVICE_EXCEPTION = 10011|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_OAUTH_SESSION_NOT_EXIST = 10012<br>差异内容：ERROR_OAUTH_SESSION_NOT_EXIST = 10012|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_OAUTH_TIMEOUT = 10013<br>差异内容：ERROR_OAUTH_TIMEOUT = 10013|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_OAUTH_TOKEN_NOT_EXIST = 10014<br>差异内容：ERROR_OAUTH_TOKEN_NOT_EXIST = 10014|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_OAUTH_TOKEN_TOO_MANY = 10015<br>差异内容：ERROR_OAUTH_TOKEN_TOO_MANY = 10015|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_OAUTH_UNSUPPORT_ACTION = 10016<br>差异内容：ERROR_OAUTH_UNSUPPORT_ACTION = 10016|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_OAUTH_UNSUPPORT_AUTH_TYPE = 10017<br>差异内容：ERROR_OAUTH_UNSUPPORT_AUTH_TYPE = 10017|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：ResultCode；<br>API声明：ERROR_PERMISSION_DENIED = 10018<br>差异内容：ERROR_PERMISSION_DENIED = 10018|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface AuthenticatorCallback<br>差异内容：interface AuthenticatorCallback|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthenticatorCallback；<br>API声明：onResult: (code: number, result: {<br>            [key: string]: any;<br>        }) => void;<br>差异内容：onResult: (code: number, result: {<br>            [key: string]: any;<br>        }) => void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthenticatorCallback；<br>API声明：onRequestRedirected: (request: Want) => void;<br>差异内容：onRequestRedirected: (request: Want) => void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：interface AuthCallback<br>差异内容：interface AuthCallback|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthCallback；<br>API声明：onResult: (code: number, result?: AuthResult) => void;<br>差异内容：onResult: (code: number, result?: AuthResult) => void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthCallback；<br>API声明：onRequestRedirected: (request: Want) => void;<br>差异内容：onRequestRedirected: (request: Want) => void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：AuthCallback；<br>API声明：onRequestContinued?: () => void;<br>差异内容：onRequestContinued?: () => void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：appAccount；<br>API声明：class Authenticator<br>差异内容：class Authenticator|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Authenticator；<br>API声明：addAccountImplicitly(authType: string, callerBundleName: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;<br>差异内容：addAccountImplicitly(authType: string, callerBundleName: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Authenticator；<br>API声明：createAccountImplicitly(options: CreateAccountImplicitlyOptions, callback: AuthCallback): void;<br>差异内容：createAccountImplicitly(options: CreateAccountImplicitlyOptions, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Authenticator；<br>API声明：authenticate(name: string, authType: string, callerBundleName: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;<br>差异内容：authenticate(name: string, authType: string, callerBundleName: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Authenticator；<br>API声明：auth(name: string, authType: string, options: Record\<string, Object>, callback: AuthCallback): void;<br>差异内容：auth(name: string, authType: string, options: Record\<string, Object>, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Authenticator；<br>API声明：verifyCredential(name: string, options: VerifyCredentialOptions, callback: AuthCallback): void;<br>差异内容：verifyCredential(name: string, options: VerifyCredentialOptions, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Authenticator；<br>API声明：setProperties(options: SetPropertiesOptions, callback: AuthCallback): void;<br>差异内容：setProperties(options: SetPropertiesOptions, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Authenticator；<br>API声明：checkAccountLabels(name: string, labels: Array\<string>, callback: AuthCallback): void;<br>差异内容：checkAccountLabels(name: string, labels: Array\<string>, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Authenticator；<br>API声明：checkAccountRemovable(name: string, callback: AuthCallback): void;<br>差异内容：checkAccountRemovable(name: string, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：Authenticator；<br>API声明：getRemoteObject(): rpc.RemoteObject;<br>差异内容：getRemoteObject(): rpc.RemoteObject;|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace distributedAccount<br>差异内容：declare namespace distributedAccount|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：distributedAccount；<br>API声明：function getDistributedAccountAbility(): DistributedAccountAbility;<br>差异内容：function getDistributedAccountAbility(): DistributedAccountAbility;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：distributedAccount；<br>API声明：interface DistributedAccountAbility<br>差异内容：interface DistributedAccountAbility|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedAccountAbility；<br>API声明：queryOsAccountDistributedInfo(callback: AsyncCallback\<DistributedInfo>): void;<br>差异内容：queryOsAccountDistributedInfo(callback: AsyncCallback\<DistributedInfo>): void;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedAccountAbility；<br>API声明：queryOsAccountDistributedInfo(): Promise\<DistributedInfo>;<br>差异内容：queryOsAccountDistributedInfo(): Promise\<DistributedInfo>;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedAccountAbility；<br>API声明：getOsAccountDistributedInfo(callback: AsyncCallback\<DistributedInfo>): void;<br>差异内容：getOsAccountDistributedInfo(callback: AsyncCallback\<DistributedInfo>): void;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedAccountAbility；<br>API声明：getOsAccountDistributedInfo(): Promise\<DistributedInfo>;<br>差异内容：getOsAccountDistributedInfo(): Promise\<DistributedInfo>;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedAccountAbility；<br>API声明：updateOsAccountDistributedInfo(accountInfo: DistributedInfo, callback: AsyncCallback\<void>): void;<br>差异内容：updateOsAccountDistributedInfo(accountInfo: DistributedInfo, callback: AsyncCallback\<void>): void;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedAccountAbility；<br>API声明：updateOsAccountDistributedInfo(accountInfo: DistributedInfo): Promise\<void>;<br>差异内容：updateOsAccountDistributedInfo(accountInfo: DistributedInfo): Promise\<void>;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedAccountAbility；<br>API声明：setOsAccountDistributedInfo(accountInfo: DistributedInfo, callback: AsyncCallback\<void>): void;<br>差异内容：setOsAccountDistributedInfo(accountInfo: DistributedInfo, callback: AsyncCallback\<void>): void;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedAccountAbility；<br>API声明：setOsAccountDistributedInfo(accountInfo: DistributedInfo): Promise\<void>;<br>差异内容：setOsAccountDistributedInfo(accountInfo: DistributedInfo): Promise\<void>;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：distributedAccount；<br>API声明：enum DistributedAccountStatus<br>差异内容：enum DistributedAccountStatus|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedAccountStatus；<br>API声明：NOT_LOGGED_IN = 0<br>差异内容：NOT_LOGGED_IN = 0|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedAccountStatus；<br>API声明：LOGGED_IN = 1<br>差异内容：LOGGED_IN = 1|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：distributedAccount；<br>API声明：interface DistributedInfo<br>差异内容：interface DistributedInfo|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedInfo；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedInfo；<br>API声明：id: string;<br>差异内容：id: string;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedInfo；<br>API声明：event: string;<br>差异内容：event: string;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedInfo；<br>API声明：nickname?: string;<br>差异内容：nickname?: string;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedInfo；<br>API声明：avatar?: string;<br>差异内容：avatar?: string;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedInfo；<br>API声明：readonly status?: DistributedAccountStatus;<br>差异内容：readonly status?: DistributedAccountStatus;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：DistributedInfo；<br>API声明：scalableData?: object;<br>差异内容：scalableData?: object;|api/@ohos.account.distributedAccount.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace osAccount<br>差异内容：declare namespace osAccount|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：osAccount；<br>API声明：function getAccountManager(): AccountManager;<br>差异内容：function getAccountManager(): AccountManager;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：osAccount；<br>API声明：interface AccountManager<br>差异内容：interface AccountManager|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isMultiOsAccountEnable(callback: AsyncCallback\<boolean>): void;<br>差异内容：isMultiOsAccountEnable(callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isMultiOsAccountEnable(): Promise\<boolean>;<br>差异内容：isMultiOsAccountEnable(): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：checkMultiOsAccountEnabled(callback: AsyncCallback\<boolean>): void;<br>差异内容：checkMultiOsAccountEnabled(callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：checkMultiOsAccountEnabled(): Promise\<boolean>;<br>差异内容：checkMultiOsAccountEnabled(): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isOsAccountActived(localId: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：isOsAccountActived(localId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isOsAccountActived(localId: number): Promise\<boolean>;<br>差异内容：isOsAccountActived(localId: number): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：checkOsAccountActivated(localId: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：checkOsAccountActivated(localId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：checkOsAccountActivated(localId: number): Promise\<boolean>;<br>差异内容：checkOsAccountActivated(localId: number): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isOsAccountConstraintEnable(localId: number, constraint: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：isOsAccountConstraintEnable(localId: number, constraint: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isOsAccountConstraintEnable(localId: number, constraint: string): Promise\<boolean>;<br>差异内容：isOsAccountConstraintEnable(localId: number, constraint: string): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：checkOsAccountConstraintEnabled(localId: number, constraint: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：checkOsAccountConstraintEnabled(localId: number, constraint: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：checkOsAccountConstraintEnabled(localId: number, constraint: string): Promise\<boolean>;<br>差异内容：checkOsAccountConstraintEnabled(localId: number, constraint: string): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isOsAccountConstraintEnabled(constraint: string): Promise\<boolean>;<br>差异内容：isOsAccountConstraintEnabled(constraint: string): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isTestOsAccount(callback: AsyncCallback\<boolean>): void;<br>差异内容：isTestOsAccount(callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isTestOsAccount(): Promise\<boolean>;<br>差异内容：isTestOsAccount(): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：checkOsAccountTestable(callback: AsyncCallback\<boolean>): void;<br>差异内容：checkOsAccountTestable(callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：checkOsAccountTestable(): Promise\<boolean>;<br>差异内容：checkOsAccountTestable(): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isOsAccountVerified(callback: AsyncCallback\<boolean>): void;<br>差异内容：isOsAccountVerified(callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isOsAccountVerified(localId: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：isOsAccountVerified(localId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isOsAccountVerified(localId?: number): Promise\<boolean>;<br>差异内容：isOsAccountVerified(localId?: number): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：checkOsAccountVerified(callback: AsyncCallback\<boolean>): void;<br>差异内容：checkOsAccountVerified(callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：checkOsAccountVerified(): Promise\<boolean>;<br>差异内容：checkOsAccountVerified(): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：checkOsAccountVerified(localId: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：checkOsAccountVerified(localId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：checkOsAccountVerified(localId: number): Promise\<boolean>;<br>差异内容：checkOsAccountVerified(localId: number): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：isOsAccountUnlocked(): Promise\<boolean>;<br>差异内容：isOsAccountUnlocked(): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getCreatedOsAccountsCount(callback: AsyncCallback\<number>): void;<br>差异内容：getCreatedOsAccountsCount(callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getCreatedOsAccountsCount(): Promise\<number>;<br>差异内容：getCreatedOsAccountsCount(): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountCount(callback: AsyncCallback\<number>): void;<br>差异内容：getOsAccountCount(callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountCount(): Promise\<number>;<br>差异内容：getOsAccountCount(): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdFromProcess(callback: AsyncCallback\<number>): void;<br>差异内容：getOsAccountLocalIdFromProcess(callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdFromProcess(): Promise\<number>;<br>差异内容：getOsAccountLocalIdFromProcess(): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalId(callback: AsyncCallback\<number>): void;<br>差异内容：getOsAccountLocalId(callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalId(): Promise\<number>;<br>差异内容：getOsAccountLocalId(): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdFromUid(uid: number, callback: AsyncCallback\<number>): void;<br>差异内容：getOsAccountLocalIdFromUid(uid: number, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdFromUid(uid: number): Promise\<number>;<br>差异内容：getOsAccountLocalIdFromUid(uid: number): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdForUid(uid: number, callback: AsyncCallback\<number>): void;<br>差异内容：getOsAccountLocalIdForUid(uid: number, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdForUid(uid: number): Promise\<number>;<br>差异内容：getOsAccountLocalIdForUid(uid: number): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdForUidSync(uid: number): number;<br>差异内容：getOsAccountLocalIdForUidSync(uid: number): number;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdFromDomain(domainInfo: DomainAccountInfo, callback: AsyncCallback\<number>): void;<br>差异内容：getOsAccountLocalIdFromDomain(domainInfo: DomainAccountInfo, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdFromDomain(domainInfo: DomainAccountInfo): Promise\<number>;<br>差异内容：getOsAccountLocalIdFromDomain(domainInfo: DomainAccountInfo): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdForDomain(domainInfo: DomainAccountInfo, callback: AsyncCallback\<number>): void;<br>差异内容：getOsAccountLocalIdForDomain(domainInfo: DomainAccountInfo, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdForDomain(domainInfo: DomainAccountInfo): Promise\<number>;<br>差异内容：getOsAccountLocalIdForDomain(domainInfo: DomainAccountInfo): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountAllConstraints(localId: number, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：getOsAccountAllConstraints(localId: number, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountAllConstraints(localId: number): Promise\<Array\<string>>;<br>差异内容：getOsAccountAllConstraints(localId: number): Promise\<Array\<string>>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountConstraints(localId: number, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：getOsAccountConstraints(localId: number, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountConstraints(localId: number): Promise\<Array\<string>>;<br>差异内容：getOsAccountConstraints(localId: number): Promise\<Array\<string>>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：queryActivatedOsAccountIds(callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：queryActivatedOsAccountIds(callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：queryActivatedOsAccountIds(): Promise\<Array\<number>>;<br>差异内容：queryActivatedOsAccountIds(): Promise\<Array\<number>>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getActivatedOsAccountLocalIds(callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：getActivatedOsAccountLocalIds(callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getActivatedOsAccountLocalIds(): Promise\<Array\<number>>;<br>差异内容：getActivatedOsAccountLocalIds(): Promise\<Array\<number>>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：queryCurrentOsAccount(callback: AsyncCallback\<OsAccountInfo>): void;<br>差异内容：queryCurrentOsAccount(callback: AsyncCallback\<OsAccountInfo>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：queryCurrentOsAccount(): Promise\<OsAccountInfo>;<br>差异内容：queryCurrentOsAccount(): Promise\<OsAccountInfo>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getCurrentOsAccount(callback: AsyncCallback\<OsAccountInfo>): void;<br>差异内容：getCurrentOsAccount(callback: AsyncCallback\<OsAccountInfo>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getCurrentOsAccount(): Promise\<OsAccountInfo>;<br>差异内容：getCurrentOsAccount(): Promise\<OsAccountInfo>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountTypeFromProcess(callback: AsyncCallback\<OsAccountType>): void;<br>差异内容：getOsAccountTypeFromProcess(callback: AsyncCallback\<OsAccountType>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountTypeFromProcess(): Promise\<OsAccountType>;<br>差异内容：getOsAccountTypeFromProcess(): Promise\<OsAccountType>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountType(callback: AsyncCallback\<OsAccountType>): void;<br>差异内容：getOsAccountType(callback: AsyncCallback\<OsAccountType>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountType(): Promise\<OsAccountType>;<br>差异内容：getOsAccountType(): Promise\<OsAccountType>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getDistributedVirtualDeviceId(callback: AsyncCallback\<string>): void;<br>差异内容：getDistributedVirtualDeviceId(callback: AsyncCallback\<string>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getDistributedVirtualDeviceId(): Promise\<string>;<br>差异内容：getDistributedVirtualDeviceId(): Promise\<string>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：queryDistributedVirtualDeviceId(callback: AsyncCallback\<string>): void;<br>差异内容：queryDistributedVirtualDeviceId(callback: AsyncCallback\<string>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：queryDistributedVirtualDeviceId(): Promise\<string>;<br>差异内容：queryDistributedVirtualDeviceId(): Promise\<string>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdBySerialNumber(serialNumber: number, callback: AsyncCallback\<number>): void;<br>差异内容：getOsAccountLocalIdBySerialNumber(serialNumber: number, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdBySerialNumber(serialNumber: number): Promise\<number>;<br>差异内容：getOsAccountLocalIdBySerialNumber(serialNumber: number): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdForSerialNumber(serialNumber: number, callback: AsyncCallback\<number>): void;<br>差异内容：getOsAccountLocalIdForSerialNumber(serialNumber: number, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountLocalIdForSerialNumber(serialNumber: number): Promise\<number>;<br>差异内容：getOsAccountLocalIdForSerialNumber(serialNumber: number): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getSerialNumberByOsAccountLocalId(localId: number, callback: AsyncCallback\<number>): void;<br>差异内容：getSerialNumberByOsAccountLocalId(localId: number, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getSerialNumberByOsAccountLocalId(localId: number): Promise\<number>;<br>差异内容：getSerialNumberByOsAccountLocalId(localId: number): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getSerialNumberForOsAccountLocalId(localId: number, callback: AsyncCallback\<number>): void;<br>差异内容：getSerialNumberForOsAccountLocalId(localId: number, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getSerialNumberForOsAccountLocalId(localId: number): Promise\<number>;<br>差异内容：getSerialNumberForOsAccountLocalId(localId: number): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：osAccount；<br>API声明：interface OsAccountInfo<br>差异内容：interface OsAccountInfo|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：localId: number;<br>差异内容：localId: number;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：localName: string;<br>差异内容：localName: string;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：type: OsAccountType;<br>差异内容：type: OsAccountType;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：constraints: Array\<string>;<br>差异内容：constraints: Array\<string>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：isVerified: boolean;<br>差异内容：isVerified: boolean;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：isUnlocked: boolean;<br>差异内容：isUnlocked: boolean;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：photo: string;<br>差异内容：photo: string;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：createTime: number;<br>差异内容：createTime: number;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：lastLoginTime: number;<br>差异内容：lastLoginTime: number;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：serialNumber: number;<br>差异内容：serialNumber: number;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：isActived: boolean;<br>差异内容：isActived: boolean;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：isActivated: boolean;<br>差异内容：isActivated: boolean;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：isCreateCompleted: boolean;<br>差异内容：isCreateCompleted: boolean;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：distributedInfo: distributedAccount.DistributedInfo;<br>差异内容：distributedInfo: distributedAccount.DistributedInfo;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountInfo；<br>API声明：domainInfo: DomainAccountInfo;<br>差异内容：domainInfo: DomainAccountInfo;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：osAccount；<br>API声明：interface DomainAccountInfo<br>差异内容：interface DomainAccountInfo|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：DomainAccountInfo；<br>API声明：domain: string;<br>差异内容：domain: string;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：DomainAccountInfo；<br>API声明：accountName: string;<br>差异内容：accountName: string;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：osAccount；<br>API声明：enum OsAccountType<br>差异内容：enum OsAccountType|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountType；<br>API声明：ADMIN = 0<br>差异内容：ADMIN = 0|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountType；<br>API声明：NORMAL<br>差异内容：NORMAL|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：OsAccountType；<br>API声明：GUEST<br>差异内容：GUEST|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Callback<br>差异内容：export interface Callback|api/@ohos.base.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ErrorCallback<br>差异内容：export interface ErrorCallback|api/@ohos.base.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface AsyncCallback<br>差异内容：export interface AsyncCallback|api/@ohos.base.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface BusinessError<br>差异内容：export interface BusinessError|api/@ohos.base.d.ts|
|新增API|NA|类名：BusinessError；<br>API声明：code: number;<br>差异内容：code: number;|api/@ohos.base.d.ts|
|新增API|NA|类名：BusinessError；<br>API声明：data?: T;<br>差异内容：data?: T;|api/@ohos.base.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace batteryInfo<br>差异内容：declare namespace batteryInfo|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：const batterySOC: number;<br>差异内容：const batterySOC: number;|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：const chargingStatus: BatteryChargeState;<br>差异内容：const chargingStatus: BatteryChargeState;|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：const healthStatus: BatteryHealthState;<br>差异内容：const healthStatus: BatteryHealthState;|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：const pluggedType: BatteryPluggedType;<br>差异内容：const pluggedType: BatteryPluggedType;|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：const voltage: number;<br>差异内容：const voltage: number;|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：const technology: string;<br>差异内容：const technology: string;|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：const batteryTemperature: number;<br>差异内容：const batteryTemperature: number;|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：const isBatteryPresent: boolean;<br>差异内容：const isBatteryPresent: boolean;|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：const batteryCapacityLevel: BatteryCapacityLevel;<br>差异内容：const batteryCapacityLevel: BatteryCapacityLevel;|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：export enum BatteryPluggedType<br>差异内容：export enum BatteryPluggedType|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryPluggedType；<br>API声明：NONE<br>差异内容：NONE|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryPluggedType；<br>API声明：AC<br>差异内容：AC|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryPluggedType；<br>API声明：USB<br>差异内容：USB|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryPluggedType；<br>API声明：WIRELESS<br>差异内容：WIRELESS|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：export enum BatteryChargeState<br>差异内容：export enum BatteryChargeState|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryChargeState；<br>API声明：NONE<br>差异内容：NONE|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryChargeState；<br>API声明：ENABLE<br>差异内容：ENABLE|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryChargeState；<br>API声明：DISABLE<br>差异内容：DISABLE|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryChargeState；<br>API声明：FULL<br>差异内容：FULL|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：export enum BatteryHealthState<br>差异内容：export enum BatteryHealthState|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryHealthState；<br>API声明：UNKNOWN<br>差异内容：UNKNOWN|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryHealthState；<br>API声明：GOOD<br>差异内容：GOOD|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryHealthState；<br>API声明：OVERHEAT<br>差异内容：OVERHEAT|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryHealthState；<br>API声明：OVERVOLTAGE<br>差异内容：OVERVOLTAGE|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryHealthState；<br>API声明：COLD<br>差异内容：COLD|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryHealthState；<br>API声明：DEAD<br>差异内容：DEAD|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：export enum BatteryCapacityLevel<br>差异内容：export enum BatteryCapacityLevel|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryCapacityLevel；<br>API声明：LEVEL_FULL<br>差异内容：LEVEL_FULL|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryCapacityLevel；<br>API声明：LEVEL_HIGH<br>差异内容：LEVEL_HIGH|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryCapacityLevel；<br>API声明：LEVEL_NORMAL<br>差异内容：LEVEL_NORMAL|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryCapacityLevel；<br>API声明：LEVEL_LOW<br>差异内容：LEVEL_LOW|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryCapacityLevel；<br>API声明：LEVEL_WARNING<br>差异内容：LEVEL_WARNING|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryCapacityLevel；<br>API声明：LEVEL_CRITICAL<br>差异内容：LEVEL_CRITICAL|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：BatteryCapacityLevel；<br>API声明：LEVEL_SHUTDOWN<br>差异内容：LEVEL_SHUTDOWN|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：export enum CommonEventBatteryChangedKey<br>差异内容：export enum CommonEventBatteryChangedKey|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：CommonEventBatteryChangedKey；<br>API声明：EXTRA_SOC = 'soc'<br>差异内容：EXTRA_SOC = 'soc'|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：CommonEventBatteryChangedKey；<br>API声明：EXTRA_CHARGE_STATE = 'chargeState'<br>差异内容：EXTRA_CHARGE_STATE = 'chargeState'|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：CommonEventBatteryChangedKey；<br>API声明：EXTRA_HEALTH_STATE = 'healthState'<br>差异内容：EXTRA_HEALTH_STATE = 'healthState'|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：CommonEventBatteryChangedKey；<br>API声明：EXTRA_PLUGGED_TYPE = 'pluggedType'<br>差异内容：EXTRA_PLUGGED_TYPE = 'pluggedType'|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：CommonEventBatteryChangedKey；<br>API声明：EXTRA_VOLTAGE = 'voltage'<br>差异内容：EXTRA_VOLTAGE = 'voltage'|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：CommonEventBatteryChangedKey；<br>API声明：EXTRA_TECHNOLOGY = 'technology'<br>差异内容：EXTRA_TECHNOLOGY = 'technology'|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：CommonEventBatteryChangedKey；<br>API声明：EXTRA_TEMPERATURE = 'temperature'<br>差异内容：EXTRA_TEMPERATURE = 'temperature'|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：CommonEventBatteryChangedKey；<br>API声明：EXTRA_PRESENT = 'present'<br>差异内容：EXTRA_PRESENT = 'present'|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：CommonEventBatteryChangedKey；<br>API声明：EXTRA_CAPACITY_LEVEL = 'capacityLevel'<br>差异内容：EXTRA_CAPACITY_LEVEL = 'capacityLevel'|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace commonEventManager<br>差异内容：declare namespace commonEventManager|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：commonEventManager；<br>API声明：function publish(event: string, callback: AsyncCallback\<void>): void;<br>差异内容：function publish(event: string, callback: AsyncCallback\<void>): void;|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：commonEventManager；<br>API声明：function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback\<void>): void;<br>差异内容：function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback\<void>): void;|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：commonEventManager；<br>API声明：function createSubscriber(subscribeInfo: CommonEventSubscribeInfo, callback: AsyncCallback\<CommonEventSubscriber>): void;<br>差异内容：function createSubscriber(subscribeInfo: CommonEventSubscribeInfo, callback: AsyncCallback\<CommonEventSubscriber>): void;|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：commonEventManager；<br>API声明：function createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise\<CommonEventSubscriber>;<br>差异内容：function createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise\<CommonEventSubscriber>;|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：commonEventManager；<br>API声明：function createSubscriberSync(subscribeInfo: CommonEventSubscribeInfo): CommonEventSubscriber;<br>差异内容：function createSubscriberSync(subscribeInfo: CommonEventSubscribeInfo): CommonEventSubscriber;|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：commonEventManager；<br>API声明：function subscribe(subscriber: CommonEventSubscriber, callback: AsyncCallback\<CommonEventData>): void;<br>差异内容：function subscribe(subscriber: CommonEventSubscriber, callback: AsyncCallback\<CommonEventData>): void;|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：commonEventManager；<br>API声明：function unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback\<void>): void;<br>差异内容：function unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback\<void>): void;|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：commonEventManager；<br>API声明：export enum Support<br>差异内容：export enum Support|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BOOT_COMPLETED = 'usual.event.BOOT_COMPLETED'<br>差异内容：COMMON_EVENT_BOOT_COMPLETED = 'usual.event.BOOT_COMPLETED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_LOCKED_BOOT_COMPLETED = 'usual.event.LOCKED_BOOT_COMPLETED'<br>差异内容：COMMON_EVENT_LOCKED_BOOT_COMPLETED = 'usual.event.LOCKED_BOOT_COMPLETED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_SHUTDOWN = 'usual.event.SHUTDOWN'<br>差异内容：COMMON_EVENT_SHUTDOWN = 'usual.event.SHUTDOWN'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BATTERY_CHANGED = 'usual.event.BATTERY_CHANGED'<br>差异内容：COMMON_EVENT_BATTERY_CHANGED = 'usual.event.BATTERY_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BATTERY_LOW = 'usual.event.BATTERY_LOW'<br>差异内容：COMMON_EVENT_BATTERY_LOW = 'usual.event.BATTERY_LOW'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BATTERY_OKAY = 'usual.event.BATTERY_OKAY'<br>差异内容：COMMON_EVENT_BATTERY_OKAY = 'usual.event.BATTERY_OKAY'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_POWER_CONNECTED = 'usual.event.POWER_CONNECTED'<br>差异内容：COMMON_EVENT_POWER_CONNECTED = 'usual.event.POWER_CONNECTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_POWER_DISCONNECTED = 'usual.event.POWER_DISCONNECTED'<br>差异内容：COMMON_EVENT_POWER_DISCONNECTED = 'usual.event.POWER_DISCONNECTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_SCREEN_OFF = 'usual.event.SCREEN_OFF'<br>差异内容：COMMON_EVENT_SCREEN_OFF = 'usual.event.SCREEN_OFF'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_SCREEN_ON = 'usual.event.SCREEN_ON'<br>差异内容：COMMON_EVENT_SCREEN_ON = 'usual.event.SCREEN_ON'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_THERMAL_LEVEL_CHANGED = 'usual.event.THERMAL_LEVEL_CHANGED'<br>差异内容：COMMON_EVENT_THERMAL_LEVEL_CHANGED = 'usual.event.THERMAL_LEVEL_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USER_PRESENT = 'usual.event.USER_PRESENT'<br>差异内容：COMMON_EVENT_USER_PRESENT = 'usual.event.USER_PRESENT'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_TIME_TICK = 'usual.event.TIME_TICK'<br>差异内容：COMMON_EVENT_TIME_TICK = 'usual.event.TIME_TICK'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_TIME_CHANGED = 'usual.event.TIME_CHANGED'<br>差异内容：COMMON_EVENT_TIME_CHANGED = 'usual.event.TIME_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DATE_CHANGED = 'usual.event.DATE_CHANGED'<br>差异内容：COMMON_EVENT_DATE_CHANGED = 'usual.event.DATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_TIMEZONE_CHANGED = 'usual.event.TIMEZONE_CHANGED'<br>差异内容：COMMON_EVENT_TIMEZONE_CHANGED = 'usual.event.TIMEZONE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_CLOSE_SYSTEM_DIALOGS = 'usual.event.CLOSE_SYSTEM_DIALOGS'<br>差异内容：COMMON_EVENT_CLOSE_SYSTEM_DIALOGS = 'usual.event.CLOSE_SYSTEM_DIALOGS'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGE_ADDED = 'usual.event.PACKAGE_ADDED'<br>差异内容：COMMON_EVENT_PACKAGE_ADDED = 'usual.event.PACKAGE_ADDED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGE_REPLACED = 'usual.event.PACKAGE_REPLACED'<br>差异内容：COMMON_EVENT_PACKAGE_REPLACED = 'usual.event.PACKAGE_REPLACED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_MY_PACKAGE_REPLACED = 'usual.event.MY_PACKAGE_REPLACED'<br>差异内容：COMMON_EVENT_MY_PACKAGE_REPLACED = 'usual.event.MY_PACKAGE_REPLACED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGE_REMOVED = 'usual.event.PACKAGE_REMOVED'<br>差异内容：COMMON_EVENT_PACKAGE_REMOVED = 'usual.event.PACKAGE_REMOVED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BUNDLE_REMOVED = 'usual.event.BUNDLE_REMOVED'<br>差异内容：COMMON_EVENT_BUNDLE_REMOVED = 'usual.event.BUNDLE_REMOVED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGE_FULLY_REMOVED = 'usual.event.PACKAGE_FULLY_REMOVED'<br>差异内容：COMMON_EVENT_PACKAGE_FULLY_REMOVED = 'usual.event.PACKAGE_FULLY_REMOVED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGE_CHANGED = 'usual.event.PACKAGE_CHANGED'<br>差异内容：COMMON_EVENT_PACKAGE_CHANGED = 'usual.event.PACKAGE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGE_RESTARTED = 'usual.event.PACKAGE_RESTARTED'<br>差异内容：COMMON_EVENT_PACKAGE_RESTARTED = 'usual.event.PACKAGE_RESTARTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGE_DATA_CLEARED = 'usual.event.PACKAGE_DATA_CLEARED'<br>差异内容：COMMON_EVENT_PACKAGE_DATA_CLEARED = 'usual.event.PACKAGE_DATA_CLEARED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGE_CACHE_CLEARED = 'usual.event.PACKAGE_CACHE_CLEARED'<br>差异内容：COMMON_EVENT_PACKAGE_CACHE_CLEARED = 'usual.event.PACKAGE_CACHE_CLEARED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGES_SUSPENDED = 'usual.event.PACKAGES_SUSPENDED'<br>差异内容：COMMON_EVENT_PACKAGES_SUSPENDED = 'usual.event.PACKAGES_SUSPENDED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGES_UNSUSPENDED = 'usual.event.PACKAGES_UNSUSPENDED'<br>差异内容：COMMON_EVENT_PACKAGES_UNSUSPENDED = 'usual.event.PACKAGES_UNSUSPENDED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_MY_PACKAGE_SUSPENDED = 'usual.event.MY_PACKAGE_SUSPENDED'<br>差异内容：COMMON_EVENT_MY_PACKAGE_SUSPENDED = 'usual.event.MY_PACKAGE_SUSPENDED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_MY_PACKAGE_UNSUSPENDED = 'usual.event.MY_PACKAGE_UNSUSPENDED'<br>差异内容：COMMON_EVENT_MY_PACKAGE_UNSUSPENDED = 'usual.event.MY_PACKAGE_UNSUSPENDED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_UID_REMOVED = 'usual.event.UID_REMOVED'<br>差异内容：COMMON_EVENT_UID_REMOVED = 'usual.event.UID_REMOVED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGE_FIRST_LAUNCH = 'usual.event.PACKAGE_FIRST_LAUNCH'<br>差异内容：COMMON_EVENT_PACKAGE_FIRST_LAUNCH = 'usual.event.PACKAGE_FIRST_LAUNCH'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION = 'usual.event.PACKAGE_NEEDS_VERIFICATION'<br>差异内容：COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION = 'usual.event.PACKAGE_NEEDS_VERIFICATION'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_PACKAGE_VERIFIED = 'usual.event.PACKAGE_VERIFIED'<br>差异内容：COMMON_EVENT_PACKAGE_VERIFIED = 'usual.event.PACKAGE_VERIFIED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_AVAILABLE'<br>差异内容：COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_AVAILABLE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE'<br>差异内容：COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_CONFIGURATION_CHANGED = 'usual.event.CONFIGURATION_CHANGED'<br>差异内容：COMMON_EVENT_CONFIGURATION_CHANGED = 'usual.event.CONFIGURATION_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_LOCALE_CHANGED = 'usual.event.LOCALE_CHANGED'<br>差异内容：COMMON_EVENT_LOCALE_CHANGED = 'usual.event.LOCALE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_MANAGE_PACKAGE_STORAGE = 'usual.event.MANAGE_PACKAGE_STORAGE'<br>差异内容：COMMON_EVENT_MANAGE_PACKAGE_STORAGE = 'usual.event.MANAGE_PACKAGE_STORAGE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DRIVE_MODE = 'common.event.DRIVE_MODE'<br>差异内容：COMMON_EVENT_DRIVE_MODE = 'common.event.DRIVE_MODE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_HOME_MODE = 'common.event.HOME_MODE'<br>差异内容：COMMON_EVENT_HOME_MODE = 'common.event.HOME_MODE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_OFFICE_MODE = 'common.event.OFFICE_MODE'<br>差异内容：COMMON_EVENT_OFFICE_MODE = 'common.event.OFFICE_MODE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USER_STARTED = 'usual.event.USER_STARTED'<br>差异内容：COMMON_EVENT_USER_STARTED = 'usual.event.USER_STARTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USER_BACKGROUND = 'usual.event.USER_BACKGROUND'<br>差异内容：COMMON_EVENT_USER_BACKGROUND = 'usual.event.USER_BACKGROUND'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USER_FOREGROUND = 'usual.event.USER_FOREGROUND'<br>差异内容：COMMON_EVENT_USER_FOREGROUND = 'usual.event.USER_FOREGROUND'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USER_SWITCHED = 'usual.event.USER_SWITCHED'<br>差异内容：COMMON_EVENT_USER_SWITCHED = 'usual.event.USER_SWITCHED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USER_STARTING = 'usual.event.USER_STARTING'<br>差异内容：COMMON_EVENT_USER_STARTING = 'usual.event.USER_STARTING'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USER_UNLOCKED = 'usual.event.USER_UNLOCKED'<br>差异内容：COMMON_EVENT_USER_UNLOCKED = 'usual.event.USER_UNLOCKED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USER_STOPPING = 'usual.event.USER_STOPPING'<br>差异内容：COMMON_EVENT_USER_STOPPING = 'usual.event.USER_STOPPING'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USER_STOPPED = 'usual.event.USER_STOPPED'<br>差异内容：COMMON_EVENT_USER_STOPPED = 'usual.event.USER_STOPPED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN = 'common.event.DISTRIBUTED_ACCOUNT_LOGIN'<br>差异内容：COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN = 'common.event.DISTRIBUTED_ACCOUNT_LOGIN'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT = 'common.event.DISTRIBUTED_ACCOUNT_LOGOUT'<br>差异内容：COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT = 'common.event.DISTRIBUTED_ACCOUNT_LOGOUT'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID = 'common.event.DISTRIBUTED_ACCOUNT_TOKEN_INVALID'<br>差异内容：COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID = 'common.event.DISTRIBUTED_ACCOUNT_TOKEN_INVALID'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF = 'common.event.DISTRIBUTED_ACCOUNT_LOGOFF'<br>差异内容：COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF = 'common.event.DISTRIBUTED_ACCOUNT_LOGOFF'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_POWER_STATE = 'usual.event.wifi.POWER_STATE'<br>差异内容：COMMON_EVENT_WIFI_POWER_STATE = 'usual.event.wifi.POWER_STATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_SCAN_FINISHED = 'usual.event.wifi.SCAN_FINISHED'<br>差异内容：COMMON_EVENT_WIFI_SCAN_FINISHED = 'usual.event.wifi.SCAN_FINISHED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_RSSI_VALUE = 'usual.event.wifi.RSSI_VALUE'<br>差异内容：COMMON_EVENT_WIFI_RSSI_VALUE = 'usual.event.wifi.RSSI_VALUE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_CONN_STATE = 'usual.event.wifi.CONN_STATE'<br>差异内容：COMMON_EVENT_WIFI_CONN_STATE = 'usual.event.wifi.CONN_STATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_HOTSPOT_STATE = 'usual.event.wifi.HOTSPOT_STATE'<br>差异内容：COMMON_EVENT_WIFI_HOTSPOT_STATE = 'usual.event.wifi.HOTSPOT_STATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_AP_STA_JOIN = 'usual.event.wifi.WIFI_HS_STA_JOIN'<br>差异内容：COMMON_EVENT_WIFI_AP_STA_JOIN = 'usual.event.wifi.WIFI_HS_STA_JOIN'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_AP_STA_LEAVE = 'usual.event.wifi.WIFI_HS_STA_LEAVE'<br>差异内容：COMMON_EVENT_WIFI_AP_STA_LEAVE = 'usual.event.wifi.WIFI_HS_STA_LEAVE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE = 'usual.event.wifi.mplink.STATE_CHANGE'<br>差异内容：COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE = 'usual.event.wifi.mplink.STATE_CHANGE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_P2P_CONN_STATE = 'usual.event.wifi.p2p.CONN_STATE_CHANGE'<br>差异内容：COMMON_EVENT_WIFI_P2P_CONN_STATE = 'usual.event.wifi.p2p.CONN_STATE_CHANGE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_P2P_STATE_CHANGED = 'usual.event.wifi.p2p.STATE_CHANGE'<br>差异内容：COMMON_EVENT_WIFI_P2P_STATE_CHANGED = 'usual.event.wifi.p2p.STATE_CHANGE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED = 'usual.event.wifi.p2p.DEVICES_CHANGE'<br>差异内容：COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED = 'usual.event.wifi.p2p.DEVICES_CHANGE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED = 'usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE'<br>差异内容：COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED = 'usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED = 'usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE'<br>差异内容：COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED = 'usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED = 'usual.event.wifi.p2p.GROUP_STATE_CHANGED'<br>差异内容：COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED = 'usual.event.wifi.p2p.GROUP_STATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE = 'usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE = 'usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE = 'usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE = 'usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE = 'usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE = 'usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED = 'usual.event.bluetooth.remotedevice.DISCOVERED'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED = 'usual.event.bluetooth.remotedevice.DISCOVERED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE = 'usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE = 'usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED = 'usual.event.bluetooth.remotedevice.ACL_CONNECTED'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED = 'usual.event.bluetooth.remotedevice.ACL_CONNECTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED = 'usual.event.bluetooth.remotedevice.ACL_DISCONNECTED'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED = 'usual.event.bluetooth.remotedevice.ACL_DISCONNECTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE = 'usual.event.bluetooth.remotedevice.NAME_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE = 'usual.event.bluetooth.remotedevice.NAME_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE = 'usual.event.bluetooth.remotedevice.PAIR_STATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE = 'usual.event.bluetooth.remotedevice.PAIR_STATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE = 'usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE = 'usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT = 'usual.event.bluetooth.remotedevice.SDP_RESULT'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT = 'usual.event.bluetooth.remotedevice.SDP_RESULT'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE = 'usual.event.bluetooth.remotedevice.UUID_VALUE'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE = 'usual.event.bluetooth.remotedevice.UUID_VALUE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ = 'usual.event.bluetooth.remotedevice.PAIRING_REQ'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ = 'usual.event.bluetooth.remotedevice.PAIRING_REQ'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL = 'usual.event.bluetooth.remotedevice.PAIRING_CANCEL'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL = 'usual.event.bluetooth.remotedevice.PAIRING_CANCEL'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ = 'usual.event.bluetooth.remotedevice.CONNECT_REQ'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ = 'usual.event.bluetooth.remotedevice.CONNECT_REQ'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY = 'usual.event.bluetooth.remotedevice.CONNECT_REPLY'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY = 'usual.event.bluetooth.remotedevice.CONNECT_REPLY'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL = 'usual.event.bluetooth.remotedevice.CONNECT_CANCEL'<br>差异内容：COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL = 'usual.event.bluetooth.remotedevice.CONNECT_CANCEL'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT = 'usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT'<br>差异内容：COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT = 'usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE = 'usual.event.bluetooth.host.STATE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE = 'usual.event.bluetooth.host.STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE = 'usual.event.bluetooth.host.REQ_DISCOVERABLE'<br>差异内容：COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE = 'usual.event.bluetooth.host.REQ_DISCOVERABLE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE = 'usual.event.bluetooth.host.REQ_ENABLE'<br>差异内容：COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE = 'usual.event.bluetooth.host.REQ_ENABLE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE = 'usual.event.bluetooth.host.REQ_DISABLE'<br>差异内容：COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE = 'usual.event.bluetooth.host.REQ_DISABLE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE = 'usual.event.bluetooth.host.SCAN_MODE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE = 'usual.event.bluetooth.host.SCAN_MODE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED = 'usual.event.bluetooth.host.DISCOVERY_STARTED'<br>差异内容：COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED = 'usual.event.bluetooth.host.DISCOVERY_STARTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED = 'usual.event.bluetooth.host.DISCOVERY_FINISHED'<br>差异内容：COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED = 'usual.event.bluetooth.host.DISCOVERY_FINISHED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE = 'usual.event.bluetooth.host.NAME_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE = 'usual.event.bluetooth.host.NAME_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE'<br>差异内容：COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED = 'usual.event.nfc.action.ADAPTER_STATE_CHANGED'<br>差异内容：COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED = 'usual.event.nfc.action.ADAPTER_STATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED = 'usual.event.nfc.action.RF_FIELD_ON_DETECTED'<br>差异内容：COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED = 'usual.event.nfc.action.RF_FIELD_ON_DETECTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED = 'usual.event.nfc.action.RF_FIELD_OFF_DETECTED'<br>差异内容：COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED = 'usual.event.nfc.action.RF_FIELD_OFF_DETECTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DISCHARGING = 'usual.event.DISCHARGING'<br>差异内容：COMMON_EVENT_DISCHARGING = 'usual.event.DISCHARGING'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_CHARGING = 'usual.event.CHARGING'<br>差异内容：COMMON_EVENT_CHARGING = 'usual.event.CHARGING'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED = 'usual.event.DEVICE_IDLE_MODE_CHANGED'<br>差异内容：COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED = 'usual.event.DEVICE_IDLE_MODE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_CHARGE_IDLE_MODE_CHANGED = 'usual.event.CHARGE_IDLE_MODE_CHANGED'<br>差异内容：COMMON_EVENT_CHARGE_IDLE_MODE_CHANGED = 'usual.event.CHARGE_IDLE_MODE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_POWER_SAVE_MODE_CHANGED = 'usual.event.POWER_SAVE_MODE_CHANGED'<br>差异内容：COMMON_EVENT_POWER_SAVE_MODE_CHANGED = 'usual.event.POWER_SAVE_MODE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USER_ADDED = 'usual.event.USER_ADDED'<br>差异内容：COMMON_EVENT_USER_ADDED = 'usual.event.USER_ADDED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USER_REMOVED = 'usual.event.USER_REMOVED'<br>差异内容：COMMON_EVENT_USER_REMOVED = 'usual.event.USER_REMOVED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_ABILITY_ADDED = 'common.event.ABILITY_ADDED'<br>差异内容：COMMON_EVENT_ABILITY_ADDED = 'common.event.ABILITY_ADDED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_ABILITY_REMOVED = 'common.event.ABILITY_REMOVED'<br>差异内容：COMMON_EVENT_ABILITY_REMOVED = 'common.event.ABILITY_REMOVED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_ABILITY_UPDATED = 'common.event.ABILITY_UPDATED'<br>差异内容：COMMON_EVENT_ABILITY_UPDATED = 'common.event.ABILITY_UPDATED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_LOCATION_MODE_STATE_CHANGED = 'usual.event.location.MODE_STATE_CHANGED'<br>差异内容：COMMON_EVENT_LOCATION_MODE_STATE_CHANGED = 'usual.event.location.MODE_STATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_IVI_SLEEP = 'common.event.IVI_SLEEP'<br>差异内容：COMMON_EVENT_IVI_SLEEP = 'common.event.IVI_SLEEP'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_IVI_PAUSE = 'common.event.IVI_PAUSE'<br>差异内容：COMMON_EVENT_IVI_PAUSE = 'common.event.IVI_PAUSE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_IVI_STANDBY = 'common.event.IVI_STANDBY'<br>差异内容：COMMON_EVENT_IVI_STANDBY = 'common.event.IVI_STANDBY'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_IVI_LASTMODE_SAVE = 'common.event.IVI_LASTMODE_SAVE'<br>差异内容：COMMON_EVENT_IVI_LASTMODE_SAVE = 'common.event.IVI_LASTMODE_SAVE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_IVI_VOLTAGE_ABNORMAL = 'common.event.IVI_VOLTAGE_ABNORMAL'<br>差异内容：COMMON_EVENT_IVI_VOLTAGE_ABNORMAL = 'common.event.IVI_VOLTAGE_ABNORMAL'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_IVI_HIGH_TEMPERATURE = 'common.event.IVI_HIGH_TEMPERATURE'<br>差异内容：COMMON_EVENT_IVI_HIGH_TEMPERATURE = 'common.event.IVI_HIGH_TEMPERATURE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_IVI_EXTREME_TEMPERATURE = 'common.event.IVI_EXTREME_TEMPERATURE'<br>差异内容：COMMON_EVENT_IVI_EXTREME_TEMPERATURE = 'common.event.IVI_EXTREME_TEMPERATURE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL = 'common.event.IVI_TEMPERATURE_ABNORMAL'<br>差异内容：COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL = 'common.event.IVI_TEMPERATURE_ABNORMAL'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_IVI_VOLTAGE_RECOVERY = 'common.event.IVI_VOLTAGE_RECOVERY'<br>差异内容：COMMON_EVENT_IVI_VOLTAGE_RECOVERY = 'common.event.IVI_VOLTAGE_RECOVERY'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_IVI_TEMPERATURE_RECOVERY = 'common.event.IVI_TEMPERATURE_RECOVERY'<br>差异内容：COMMON_EVENT_IVI_TEMPERATURE_RECOVERY = 'common.event.IVI_TEMPERATURE_RECOVERY'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_IVI_ACTIVE = 'common.event.IVI_ACTIVE'<br>差异内容：COMMON_EVENT_IVI_ACTIVE = 'common.event.IVI_ACTIVE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USB_STATE = 'usual.event.hardware.usb.action.USB_STATE'<br>差异内容：COMMON_EVENT_USB_STATE = 'usual.event.hardware.usb.action.USB_STATE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USB_PORT_CHANGED = 'usual.event.hardware.usb.action.USB_PORT_CHANGED'<br>差异内容：COMMON_EVENT_USB_PORT_CHANGED = 'usual.event.hardware.usb.action.USB_PORT_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USB_DEVICE_ATTACHED = 'usual.event.hardware.usb.action.USB_DEVICE_ATTACHED'<br>差异内容：COMMON_EVENT_USB_DEVICE_ATTACHED = 'usual.event.hardware.usb.action.USB_DEVICE_ATTACHED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USB_DEVICE_DETACHED = 'usual.event.hardware.usb.action.USB_DEVICE_DETACHED'<br>差异内容：COMMON_EVENT_USB_DEVICE_DETACHED = 'usual.event.hardware.usb.action.USB_DEVICE_DETACHED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USB_ACCESSORY_ATTACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED'<br>差异内容：COMMON_EVENT_USB_ACCESSORY_ATTACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USB_ACCESSORY_DETACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED'<br>差异内容：COMMON_EVENT_USB_ACCESSORY_DETACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DISK_REMOVED = 'usual.event.data.DISK_REMOVED'<br>差异内容：COMMON_EVENT_DISK_REMOVED = 'usual.event.data.DISK_REMOVED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DISK_UNMOUNTED = 'usual.event.data.DISK_UNMOUNTED'<br>差异内容：COMMON_EVENT_DISK_UNMOUNTED = 'usual.event.data.DISK_UNMOUNTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DISK_MOUNTED = 'usual.event.data.DISK_MOUNTED'<br>差异内容：COMMON_EVENT_DISK_MOUNTED = 'usual.event.data.DISK_MOUNTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DISK_BAD_REMOVAL = 'usual.event.data.DISK_BAD_REMOVAL'<br>差异内容：COMMON_EVENT_DISK_BAD_REMOVAL = 'usual.event.data.DISK_BAD_REMOVAL'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DISK_UNMOUNTABLE = 'usual.event.data.DISK_UNMOUNTABLE'<br>差异内容：COMMON_EVENT_DISK_UNMOUNTABLE = 'usual.event.data.DISK_UNMOUNTABLE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DISK_EJECT = 'usual.event.data.DISK_EJECT'<br>差异内容：COMMON_EVENT_DISK_EJECT = 'usual.event.data.DISK_EJECT'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_VOLUME_REMOVED = 'usual.event.data.VOLUME_REMOVED'<br>差异内容：COMMON_EVENT_VOLUME_REMOVED = 'usual.event.data.VOLUME_REMOVED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_VOLUME_UNMOUNTED = 'usual.event.data.VOLUME_UNMOUNTED'<br>差异内容：COMMON_EVENT_VOLUME_UNMOUNTED = 'usual.event.data.VOLUME_UNMOUNTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_VOLUME_MOUNTED = 'usual.event.data.VOLUME_MOUNTED'<br>差异内容：COMMON_EVENT_VOLUME_MOUNTED = 'usual.event.data.VOLUME_MOUNTED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_VOLUME_BAD_REMOVAL = 'usual.event.data.VOLUME_BAD_REMOVAL'<br>差异内容：COMMON_EVENT_VOLUME_BAD_REMOVAL = 'usual.event.data.VOLUME_BAD_REMOVAL'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_VOLUME_EJECT = 'usual.event.data.VOLUME_EJECT'<br>差异内容：COMMON_EVENT_VOLUME_EJECT = 'usual.event.data.VOLUME_EJECT'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED = 'usual.event.data.VISIBLE_ACCOUNTS_UPDATED'<br>差异内容：COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED = 'usual.event.data.VISIBLE_ACCOUNTS_UPDATED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_ACCOUNT_DELETED = 'usual.event.data.ACCOUNT_DELETED'<br>差异内容：COMMON_EVENT_ACCOUNT_DELETED = 'usual.event.data.ACCOUNT_DELETED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_FOUNDATION_READY = 'common.event.FOUNDATION_READY'<br>差异内容：COMMON_EVENT_FOUNDATION_READY = 'common.event.FOUNDATION_READY'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_AIRPLANE_MODE_CHANGED = 'usual.event.AIRPLANE_MODE'<br>差异内容：COMMON_EVENT_AIRPLANE_MODE_CHANGED = 'usual.event.AIRPLANE_MODE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_SPLIT_SCREEN = 'common.event.SPLIT_SCREEN'<br>差异内容：COMMON_EVENT_SPLIT_SCREEN = 'common.event.SPLIT_SCREEN'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_SLOT_CHANGE = 'usual.event.SLOT_CHANGE'<br>差异内容：COMMON_EVENT_SLOT_CHANGE = 'usual.event.SLOT_CHANGE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_SPN_INFO_CHANGED = 'usual.event.SPN_INFO_CHANGED'<br>差异内容：COMMON_EVENT_SPN_INFO_CHANGED = 'usual.event.SPN_INFO_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_QUICK_FIX_APPLY_RESULT = 'usual.event.QUICK_FIX_APPLY_RESULT'<br>差异内容：COMMON_EVENT_QUICK_FIX_APPLY_RESULT = 'usual.event.QUICK_FIX_APPLY_RESULT'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_QUICK_FIX_REVOKE_RESULT = 'usual.event.QUICK_FIX_REVOKE_RESULT'<br>差异内容：COMMON_EVENT_QUICK_FIX_REVOKE_RESULT = 'usual.event.QUICK_FIX_REVOKE_RESULT'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_USER_INFO_UPDATED = 'usual.event.USER_INFO_UPDATED'<br>差异内容：COMMON_EVENT_USER_INFO_UPDATED = 'usual.event.USER_INFO_UPDATED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_HTTP_PROXY_CHANGE = 'usual.event.HTTP_PROXY_CHANGE'<br>差异内容：COMMON_EVENT_HTTP_PROXY_CHANGE = 'usual.event.HTTP_PROXY_CHANGE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_SIM_STATE_CHANGED = 'usual.event.SIM_STATE_CHANGED'<br>差异内容：COMMON_EVENT_SIM_STATE_CHANGED = 'usual.event.SIM_STATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_CALL_STATE_CHANGED = 'usual.event.CALL_STATE_CHANGED'<br>差异内容：COMMON_EVENT_CALL_STATE_CHANGED = 'usual.event.CALL_STATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_NETWORK_STATE_CHANGED = 'usual.event.NETWORK_STATE_CHANGED'<br>差异内容：COMMON_EVENT_NETWORK_STATE_CHANGED = 'usual.event.NETWORK_STATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_SIGNAL_INFO_CHANGED = 'usual.event.SIGNAL_INFO_CHANGED'<br>差异内容：COMMON_EVENT_SIGNAL_INFO_CHANGED = 'usual.event.SIGNAL_INFO_CHANGED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_SCREEN_UNLOCKED = 'usual.event.SCREEN_UNLOCKED'<br>差异内容：COMMON_EVENT_SCREEN_UNLOCKED = 'usual.event.SCREEN_UNLOCKED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_SCREEN_LOCKED = 'usual.event.SCREEN_LOCKED'<br>差异内容：COMMON_EVENT_SCREEN_LOCKED = 'usual.event.SCREEN_LOCKED'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_CONNECTIVITY_CHANGE = 'usual.event.CONNECTIVITY_CHANGE'<br>差异内容：COMMON_EVENT_CONNECTIVITY_CHANGE = 'usual.event.CONNECTIVITY_CHANGE'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：commonEventManager；<br>API声明：export type CommonEventData = _CommonEventData;<br>差异内容：export type CommonEventData = _CommonEventData;|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：commonEventManager；<br>API声明：export type CommonEventSubscriber = _CommonEventSubscriber;<br>差异内容：export type CommonEventSubscriber = _CommonEventSubscriber;|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：commonEventManager；<br>API声明：export type CommonEventSubscribeInfo = _CommonEventSubscribeInfo;<br>差异内容：export type CommonEventSubscribeInfo = _CommonEventSubscribeInfo;|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：commonEventManager；<br>API声明：export type CommonEventPublishData = _CommonEventPublishData;<br>差异内容：export type CommonEventPublishData = _CommonEventPublishData;|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace deviceAttest<br>差异内容：declare namespace deviceAttest|api/@ohos.deviceAttest.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace deviceInfo<br>差异内容：declare namespace deviceInfo|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const deviceType: string;<br>差异内容：const deviceType: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const manufacture: string;<br>差异内容：const manufacture: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const brand: string;<br>差异内容：const brand: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const marketName: string;<br>差异内容：const marketName: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const productSeries: string;<br>差异内容：const productSeries: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const productModel: string;<br>差异内容：const productModel: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const softwareModel: string;<br>差异内容：const softwareModel: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const hardwareModel: string;<br>差异内容：const hardwareModel: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const hardwareProfile: string;<br>差异内容：const hardwareProfile: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const serial: string;<br>差异内容：const serial: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const bootloaderVersion: string;<br>差异内容：const bootloaderVersion: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const abiList: string;<br>差异内容：const abiList: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const securityPatchTag: string;<br>差异内容：const securityPatchTag: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const displayVersion: string;<br>差异内容：const displayVersion: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const incrementalVersion: string;<br>差异内容：const incrementalVersion: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const osReleaseType: string;<br>差异内容：const osReleaseType: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const osFullName: string;<br>差异内容：const osFullName: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const majorVersion: number;<br>差异内容：const majorVersion: number;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const seniorVersion: number;<br>差异内容：const seniorVersion: number;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const featureVersion: number;<br>差异内容：const featureVersion: number;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const buildVersion: number;<br>差异内容：const buildVersion: number;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const sdkApiVersion: number;<br>差异内容：const sdkApiVersion: number;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const firstApiVersion: number;<br>差异内容：const firstApiVersion: number;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const versionId: string;<br>差异内容：const versionId: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const buildType: string;<br>差异内容：const buildType: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const buildUser: string;<br>差异内容：const buildUser: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const buildHost: string;<br>差异内容：const buildHost: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const buildTime: string;<br>差异内容：const buildTime: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const buildRootHash: string;<br>差异内容：const buildRootHash: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const udid: string;<br>差异内容：const udid: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const distributionOSName: string;<br>差异内容：const distributionOSName: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const distributionOSVersion: string;<br>差异内容：const distributionOSVersion: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const distributionOSApiVersion: number;<br>差异内容：const distributionOSApiVersion: number;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const distributionOSReleaseType: string;<br>差异内容：const distributionOSReleaseType: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace emitter<br>差异内容：declare namespace emitter|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：function on(event: InnerEvent, callback: Callback\<EventData>): void;<br>差异内容：function on(event: InnerEvent, callback: Callback\<EventData>): void;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：function on(eventId: string, callback: Callback\<EventData>): void;<br>差异内容：function on(eventId: string, callback: Callback\<EventData>): void;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：function once(event: InnerEvent, callback: Callback\<EventData>): void;<br>差异内容：function once(event: InnerEvent, callback: Callback\<EventData>): void;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：function once(eventId: string, callback: Callback\<EventData>): void;<br>差异内容：function once(eventId: string, callback: Callback\<EventData>): void;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：function off(eventId: number): void;<br>差异内容：function off(eventId: number): void;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：function off(eventId: number, callback: Callback\<EventData>): void;<br>差异内容：function off(eventId: number, callback: Callback\<EventData>): void;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：function off(eventId: string): void;<br>差异内容：function off(eventId: string): void;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：function off(eventId: string, callback: Callback\<EventData>): void;<br>差异内容：function off(eventId: string, callback: Callback\<EventData>): void;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：function emit(event: InnerEvent, data?: EventData): void;<br>差异内容：function emit(event: InnerEvent, data?: EventData): void;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：function emit(eventId: string, data?: EventData): void;<br>差异内容：function emit(eventId: string, data?: EventData): void;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：function emit(eventId: string, options: Options, data?: EventData): void;<br>差异内容：function emit(eventId: string, options: Options, data?: EventData): void;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：function getListenerCount(eventId: number \| string): number;<br>差异内容：function getListenerCount(eventId: number \| string): number;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：export interface EventData<br>差异内容：export interface EventData|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：EventData；<br>API声明：data?: {<br>            [key: string]: any;<br>        };<br>差异内容：data?: {<br>            [key: string]: any;<br>        };|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：export interface InnerEvent<br>差异内容：export interface InnerEvent|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：InnerEvent；<br>API声明：eventId: number;<br>差异内容：eventId: number;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：InnerEvent；<br>API声明：priority?: EventPriority;<br>差异内容：priority?: EventPriority;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：export enum EventPriority<br>差异内容：export enum EventPriority|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：EventPriority；<br>API声明：IMMEDIATE = 0<br>差异内容：IMMEDIATE = 0|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：EventPriority；<br>API声明：HIGH<br>差异内容：HIGH|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：EventPriority；<br>API声明：LOW<br>差异内容：LOW|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：EventPriority；<br>API声明：IDLE<br>差异内容：IDLE|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：emitter；<br>API声明：export interface Options<br>差异内容：export interface Options|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：Options；<br>API声明：priority?: EventPriority;<br>差异内容：priority?: EventPriority;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace pasteboard<br>差异内容：declare namespace pasteboard|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：const MAX_RECORD_NUM: number;<br>差异内容：const MAX_RECORD_NUM: number;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：const MIMETYPE_TEXT_HTML: string;<br>差异内容：const MIMETYPE_TEXT_HTML: string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：const MIMETYPE_TEXT_WANT: string;<br>差异内容：const MIMETYPE_TEXT_WANT: string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：const MIMETYPE_TEXT_PLAIN: string;<br>差异内容：const MIMETYPE_TEXT_PLAIN: string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：const MIMETYPE_TEXT_URI: string;<br>差异内容：const MIMETYPE_TEXT_URI: string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：const MIMETYPE_PIXELMAP: string;<br>差异内容：const MIMETYPE_PIXELMAP: string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：type ValueType = string \| image.PixelMap \| Want \| ArrayBuffer;<br>差异内容：type ValueType = string \| image.PixelMap \| Want \| ArrayBuffer;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：function createHtmlData(htmlText: string): PasteData;<br>差异内容：function createHtmlData(htmlText: string): PasteData;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：function createWantData(want: Want): PasteData;<br>差异内容：function createWantData(want: Want): PasteData;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：function createPlainTextData(text: string): PasteData;<br>差异内容：function createPlainTextData(text: string): PasteData;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：function createUriData(uri: string): PasteData;<br>差异内容：function createUriData(uri: string): PasteData;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：function createData(mimeType: string, value: ValueType): PasteData;<br>差异内容：function createData(mimeType: string, value: ValueType): PasteData;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：function createHtmlTextRecord(htmlText: string): PasteDataRecord;<br>差异内容：function createHtmlTextRecord(htmlText: string): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：function createWantRecord(want: Want): PasteDataRecord;<br>差异内容：function createWantRecord(want: Want): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：function createPlainTextRecord(text: string): PasteDataRecord;<br>差异内容：function createPlainTextRecord(text: string): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：function createUriRecord(uri: string): PasteDataRecord;<br>差异内容：function createUriRecord(uri: string): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：function createRecord(mimeType: string, value: ValueType): PasteDataRecord;<br>差异内容：function createRecord(mimeType: string, value: ValueType): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：function getSystemPasteboard(): SystemPasteboard;<br>差异内容：function getSystemPasteboard(): SystemPasteboard;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：enum ShareOption<br>差异内容：enum ShareOption|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：ShareOption；<br>API声明：INAPP<br>差异内容：INAPP|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：ShareOption；<br>API声明：LOCALDEVICE<br>差异内容：LOCALDEVICE|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：ShareOption；<br>API声明：CROSSDEVICE<br>差异内容：CROSSDEVICE|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：interface PasteDataProperty<br>差异内容：interface PasteDataProperty|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataProperty；<br>API声明：additions: {<br>            [key: string]: object;<br>        };<br>差异内容：additions: {<br>            [key: string]: object;<br>        };|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataProperty；<br>API声明：readonly mimeTypes: Array\<string>;<br>差异内容：readonly mimeTypes: Array\<string>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataProperty；<br>API声明：tag: string;<br>差异内容：tag: string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataProperty；<br>API声明：readonly timestamp: number;<br>差异内容：readonly timestamp: number;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataProperty；<br>API声明：localOnly: boolean;<br>差异内容：localOnly: boolean;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataProperty；<br>API声明：shareOption: ShareOption;<br>差异内容：shareOption: ShareOption;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：interface PasteDataRecord<br>差异内容：interface PasteDataRecord|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：htmlText: string;<br>差异内容：htmlText: string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：want: Want;<br>差异内容：want: Want;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：mimeType: string;<br>差异内容：mimeType: string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：plainText: string;<br>差异内容：plainText: string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：pixelMap: image.PixelMap;<br>差异内容：pixelMap: image.PixelMap;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：data: {<br>            [mimeType: string]: ArrayBuffer;<br>        };<br>差异内容：data: {<br>            [mimeType: string]: ArrayBuffer;<br>        };|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：convertToText(callback: AsyncCallback\<string>): void;<br>差异内容：convertToText(callback: AsyncCallback\<string>): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：convertToText(): Promise\<string>;<br>差异内容：convertToText(): Promise\<string>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：toPlainText(): string;<br>差异内容：toPlainText(): string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：interface PasteData<br>差异内容：interface PasteData|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：addHtmlRecord(htmlText: string): void;<br>差异内容：addHtmlRecord(htmlText: string): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：addWantRecord(want: Want): void;<br>差异内容：addWantRecord(want: Want): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：addRecord(record: PasteDataRecord): void;<br>差异内容：addRecord(record: PasteDataRecord): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：addRecord(mimeType: string, value: ValueType): void;<br>差异内容：addRecord(mimeType: string, value: ValueType): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：addTextRecord(text: string): void;<br>差异内容：addTextRecord(text: string): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：addUriRecord(uri: string): void;<br>差异内容：addUriRecord(uri: string): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：getMimeTypes(): Array\<string>;<br>差异内容：getMimeTypes(): Array\<string>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：getPrimaryHtml(): string;<br>差异内容：getPrimaryHtml(): string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：getPrimaryWant(): Want;<br>差异内容：getPrimaryWant(): Want;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：getPrimaryMimeType(): string;<br>差异内容：getPrimaryMimeType(): string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：getPrimaryText(): string;<br>差异内容：getPrimaryText(): string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：getPrimaryUri(): string;<br>差异内容：getPrimaryUri(): string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：getPrimaryPixelMap(): image.PixelMap;<br>差异内容：getPrimaryPixelMap(): image.PixelMap;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：getProperty(): PasteDataProperty;<br>差异内容：getProperty(): PasteDataProperty;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：setProperty(property: PasteDataProperty): void;<br>差异内容：setProperty(property: PasteDataProperty): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：getRecordAt(index: number): PasteDataRecord;<br>差异内容：getRecordAt(index: number): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：getRecord(index: number): PasteDataRecord;<br>差异内容：getRecord(index: number): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：getRecordCount(): number;<br>差异内容：getRecordCount(): number;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：getTag(): string;<br>差异内容：getTag(): string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：hasMimeType(mimeType: string): boolean;<br>差异内容：hasMimeType(mimeType: string): boolean;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：hasType(mimeType: string): boolean;<br>差异内容：hasType(mimeType: string): boolean;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：removeRecordAt(index: number): boolean;<br>差异内容：removeRecordAt(index: number): boolean;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：removeRecord(index: number): void;<br>差异内容：removeRecord(index: number): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：replaceRecordAt(index: number, record: PasteDataRecord): boolean;<br>差异内容：replaceRecordAt(index: number, record: PasteDataRecord): boolean;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：replaceRecord(index: number, record: PasteDataRecord): void;<br>差异内容：replaceRecord(index: number, record: PasteDataRecord): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：interface SystemPasteboard<br>差异内容：interface SystemPasteboard|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：on(type: 'update', callback: () => void): void;<br>差异内容：on(type: 'update', callback: () => void): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：off(type: 'update', callback?: () => void): void;<br>差异内容：off(type: 'update', callback?: () => void): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：isRemoteData(): boolean;<br>差异内容：isRemoteData(): boolean;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：getDataSource(): string;<br>差异内容：getDataSource(): string;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：hasDataType(mimeType: string): boolean;<br>差异内容：hasDataType(mimeType: string): boolean;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：clear(callback: AsyncCallback\<void>): void;<br>差异内容：clear(callback: AsyncCallback\<void>): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：clear(): Promise\<void>;<br>差异内容：clear(): Promise\<void>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：clearData(callback: AsyncCallback\<void>): void;<br>差异内容：clearData(callback: AsyncCallback\<void>): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：clearData(): Promise\<void>;<br>差异内容：clearData(): Promise\<void>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：clearDataSync(): void;<br>差异内容：clearDataSync(): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：getPasteData(callback: AsyncCallback\<PasteData>): void;<br>差异内容：getPasteData(callback: AsyncCallback\<PasteData>): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：getPasteData(): Promise\<PasteData>;<br>差异内容：getPasteData(): Promise\<PasteData>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：getData(callback: AsyncCallback\<PasteData>): void;<br>差异内容：getData(callback: AsyncCallback\<PasteData>): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：getData(): Promise\<PasteData>;<br>差异内容：getData(): Promise\<PasteData>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：getDataSync(): PasteData;<br>差异内容：getDataSync(): PasteData;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：hasPasteData(callback: AsyncCallback\<boolean>): void;<br>差异内容：hasPasteData(callback: AsyncCallback\<boolean>): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：hasPasteData(): Promise\<boolean>;<br>差异内容：hasPasteData(): Promise\<boolean>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：hasData(callback: AsyncCallback\<boolean>): void;<br>差异内容：hasData(callback: AsyncCallback\<boolean>): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：hasData(): Promise\<boolean>;<br>差异内容：hasData(): Promise\<boolean>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：hasDataSync(): boolean;<br>差异内容：hasDataSync(): boolean;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：setPasteData(data: PasteData, callback: AsyncCallback\<void>): void;<br>差异内容：setPasteData(data: PasteData, callback: AsyncCallback\<void>): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：setPasteData(data: PasteData): Promise\<void>;<br>差异内容：setPasteData(data: PasteData): Promise\<void>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：setData(data: PasteData, callback: AsyncCallback\<void>): void;<br>差异内容：setData(data: PasteData, callback: AsyncCallback\<void>): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：setData(data: PasteData): Promise\<void>;<br>差异内容：setData(data: PasteData): Promise\<void>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：setDataSync(data: PasteData): void;<br>差异内容：setDataSync(data: PasteData): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace power<br>差异内容：declare namespace power|api/@ohos.power.d.ts|
|新增API|NA|类名：power；<br>API声明：function rebootDevice(reason: string): void;<br>差异内容：function rebootDevice(reason: string): void;|api/@ohos.power.d.ts|
|新增API|NA|类名：power；<br>API声明：function isScreenOn(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isScreenOn(callback: AsyncCallback\<boolean>): void;|api/@ohos.power.d.ts|
|新增API|NA|类名：power；<br>API声明：function isScreenOn(): Promise\<boolean>;<br>差异内容：function isScreenOn(): Promise\<boolean>;|api/@ohos.power.d.ts|
|新增API|NA|类名：power；<br>API声明：function isActive(): boolean;<br>差异内容：function isActive(): boolean;|api/@ohos.power.d.ts|
|新增API|NA|类名：power；<br>API声明：function getPowerMode(): DevicePowerMode;<br>差异内容：function getPowerMode(): DevicePowerMode;|api/@ohos.power.d.ts|
|新增API|NA|类名：power；<br>API声明：function isStandby(): boolean;<br>差异内容：function isStandby(): boolean;|api/@ohos.power.d.ts|
|新增API|NA|类名：power；<br>API声明：export enum DevicePowerMode<br>差异内容：export enum DevicePowerMode|api/@ohos.power.d.ts|
|新增API|NA|类名：DevicePowerMode；<br>API声明：MODE_NORMAL = 600<br>差异内容：MODE_NORMAL = 600|api/@ohos.power.d.ts|
|新增API|NA|类名：DevicePowerMode；<br>API声明：MODE_POWER_SAVE<br>差异内容：MODE_POWER_SAVE|api/@ohos.power.d.ts|
|新增API|NA|类名：DevicePowerMode；<br>API声明：MODE_PERFORMANCE<br>差异内容：MODE_PERFORMANCE|api/@ohos.power.d.ts|
|新增API|NA|类名：DevicePowerMode；<br>API声明：MODE_EXTREME_POWER_SAVE<br>差异内容：MODE_EXTREME_POWER_SAVE|api/@ohos.power.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace print<br>差异内容：declare namespace print|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：interface PrintTask<br>差异内容：interface PrintTask|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintTask；<br>API声明：on(type: 'block', callback: Callback\<void>): void;<br>差异内容：on(type: 'block', callback: Callback\<void>): void;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintTask；<br>API声明：on(type: 'succeed', callback: Callback\<void>): void;<br>差异内容：on(type: 'succeed', callback: Callback\<void>): void;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintTask；<br>API声明：on(type: 'fail', callback: Callback\<void>): void;<br>差异内容：on(type: 'fail', callback: Callback\<void>): void;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintTask；<br>API声明：on(type: 'cancel', callback: Callback\<void>): void;<br>差异内容：on(type: 'cancel', callback: Callback\<void>): void;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintTask；<br>API声明：off(type: 'block', callback?: Callback\<void>): void;<br>差异内容：off(type: 'block', callback?: Callback\<void>): void;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintTask；<br>API声明：off(type: 'succeed', callback?: Callback\<void>): void;<br>差异内容：off(type: 'succeed', callback?: Callback\<void>): void;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintTask；<br>API声明：off(type: 'fail', callback?: Callback\<void>): void;<br>差异内容：off(type: 'fail', callback?: Callback\<void>): void;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintTask；<br>API声明：off(type: 'cancel', callback?: Callback\<void>): void;<br>差异内容：off(type: 'cancel', callback?: Callback\<void>): void;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：interface PrintDocumentAdapter<br>差异内容：interface PrintDocumentAdapter|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDocumentAdapter；<br>API声明：onStartLayoutWrite(jobId: string, oldAttrs: PrintAttributes, newAttrs: PrintAttributes, fd: number, writeResultCallback: (jobId: string, writeResult: PrintFileCreationState) => void): void;<br>差异内容：onStartLayoutWrite(jobId: string, oldAttrs: PrintAttributes, newAttrs: PrintAttributes, fd: number, writeResultCallback: (jobId: string, writeResult: PrintFileCreationState) => void): void;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDocumentAdapter；<br>API声明：onJobStateChanged(jobId: string, state: PrintDocumentAdapterState): void;<br>差异内容：onJobStateChanged(jobId: string, state: PrintDocumentAdapterState): void;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：function print(files: Array\<string>, callback: AsyncCallback\<PrintTask>): void;<br>差异内容：function print(files: Array\<string>, callback: AsyncCallback\<PrintTask>): void;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：function print(files: Array\<string>): Promise\<PrintTask>;<br>差异内容：function print(files: Array\<string>): Promise\<PrintTask>;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：function print(files: Array\<string>, context: Context, callback: AsyncCallback\<PrintTask>): void;<br>差异内容：function print(files: Array\<string>, context: Context, callback: AsyncCallback\<PrintTask>): void;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：function print(files: Array\<string>, context: Context): Promise\<PrintTask>;<br>差异内容：function print(files: Array\<string>, context: Context): Promise\<PrintTask>;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：function print(jobName: string, printAdapter: PrintDocumentAdapter, printAttributes: PrintAttributes, context: Context): Promise\<PrintTask>;<br>差异内容：function print(jobName: string, printAdapter: PrintDocumentAdapter, printAttributes: PrintAttributes, context: Context): Promise\<PrintTask>;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：interface PrintAttributes<br>差异内容：interface PrintAttributes|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintAttributes；<br>API声明：copyNumber?: number;<br>差异内容：copyNumber?: number;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintAttributes；<br>API声明：pageRange?: PrintPageRange;<br>差异内容：pageRange?: PrintPageRange;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintAttributes；<br>API声明：pageSize?: PrintPageSize \| PrintPageType;<br>差异内容：pageSize?: PrintPageSize \| PrintPageType;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintAttributes；<br>API声明：directionMode?: PrintDirectionMode;<br>差异内容：directionMode?: PrintDirectionMode;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintAttributes；<br>API声明：colorMode?: PrintColorMode;<br>差异内容：colorMode?: PrintColorMode;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintAttributes；<br>API声明：duplexMode?: PrintDuplexMode;<br>差异内容：duplexMode?: PrintDuplexMode;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：interface PrintPageRange<br>差异内容：interface PrintPageRange|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageRange；<br>API声明：startPage?: number;<br>差异内容：startPage?: number;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageRange；<br>API声明：endPage?: number;<br>差异内容：endPage?: number;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageRange；<br>API声明：pages?: Array\<number>;<br>差异内容：pages?: Array\<number>;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：interface PrintPageSize<br>差异内容：interface PrintPageSize|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageSize；<br>API声明：id: string;<br>差异内容：id: string;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageSize；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageSize；<br>API声明：width: number;<br>差异内容：width: number;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageSize；<br>API声明：height: number;<br>差异内容：height: number;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrintDirectionMode<br>差异内容：enum PrintDirectionMode|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDirectionMode；<br>API声明：DIRECTION_MODE_AUTO = 0<br>差异内容：DIRECTION_MODE_AUTO = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDirectionMode；<br>API声明：DIRECTION_MODE_PORTRAIT = 1<br>差异内容：DIRECTION_MODE_PORTRAIT = 1|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDirectionMode；<br>API声明：DIRECTION_MODE_LANDSCAPE = 2<br>差异内容：DIRECTION_MODE_LANDSCAPE = 2|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrintColorMode<br>差异内容：enum PrintColorMode|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintColorMode；<br>API声明：COLOR_MODE_MONOCHROME = 0<br>差异内容：COLOR_MODE_MONOCHROME = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintColorMode；<br>API声明：COLOR_MODE_COLOR = 1<br>差异内容：COLOR_MODE_COLOR = 1|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrintDuplexMode<br>差异内容：enum PrintDuplexMode|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDuplexMode；<br>API声明：DUPLEX_MODE_NONE = 0<br>差异内容：DUPLEX_MODE_NONE = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDuplexMode；<br>API声明：DUPLEX_MODE_LONG_EDGE = 1<br>差异内容：DUPLEX_MODE_LONG_EDGE = 1|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDuplexMode；<br>API声明：DUPLEX_MODE_SHORT_EDGE = 2<br>差异内容：DUPLEX_MODE_SHORT_EDGE = 2|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrintPageType<br>差异内容：enum PrintPageType|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageType；<br>API声明：PAGE_ISO_A3 = 0<br>差异内容：PAGE_ISO_A3 = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageType；<br>API声明：PAGE_ISO_A4 = 1<br>差异内容：PAGE_ISO_A4 = 1|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageType；<br>API声明：PAGE_ISO_A5 = 2<br>差异内容：PAGE_ISO_A5 = 2|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageType；<br>API声明：PAGE_JIS_B5 = 3<br>差异内容：PAGE_JIS_B5 = 3|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageType；<br>API声明：PAGE_ISO_C5 = 4<br>差异内容：PAGE_ISO_C5 = 4|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageType；<br>API声明：PAGE_ISO_DL = 5<br>差异内容：PAGE_ISO_DL = 5|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageType；<br>API声明：PAGE_LETTER = 6<br>差异内容：PAGE_LETTER = 6|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageType；<br>API声明：PAGE_LEGAL = 7<br>差异内容：PAGE_LEGAL = 7|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageType；<br>API声明：PAGE_PHOTO_4X6 = 8<br>差异内容：PAGE_PHOTO_4X6 = 8|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageType；<br>API声明：PAGE_PHOTO_5X7 = 9<br>差异内容：PAGE_PHOTO_5X7 = 9|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageType；<br>API声明：PAGE_INT_DL_ENVELOPE = 10<br>差异内容：PAGE_INT_DL_ENVELOPE = 10|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintPageType；<br>API声明：PAGE_B_TABLOID = 11<br>差异内容：PAGE_B_TABLOID = 11|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrintDocumentAdapterState<br>差异内容：enum PrintDocumentAdapterState|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDocumentAdapterState；<br>API声明：PREVIEW_DESTROY = 0<br>差异内容：PREVIEW_DESTROY = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDocumentAdapterState；<br>API声明：PRINT_TASK_SUCCEED = 1<br>差异内容：PRINT_TASK_SUCCEED = 1|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDocumentAdapterState；<br>API声明：PRINT_TASK_FAIL = 2<br>差异内容：PRINT_TASK_FAIL = 2|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDocumentAdapterState；<br>API声明：PRINT_TASK_CANCEL = 3<br>差异内容：PRINT_TASK_CANCEL = 3|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintDocumentAdapterState；<br>API声明：PRINT_TASK_BLOCK = 4<br>差异内容：PRINT_TASK_BLOCK = 4|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrintFileCreationState<br>差异内容：enum PrintFileCreationState|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintFileCreationState；<br>API声明：PRINT_FILE_CREATED = 0<br>差异内容：PRINT_FILE_CREATED = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintFileCreationState；<br>API声明：PRINT_FILE_CREATION_FAILED = 1<br>差异内容：PRINT_FILE_CREATION_FAILED = 1|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintFileCreationState；<br>API声明：PRINT_FILE_CREATED_UNRENDERED = 2<br>差异内容：PRINT_FILE_CREATED_UNRENDERED = 2|api/@ohos.print.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace request<br>差异内容：declare namespace request|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const EXCEPTION_PERMISSION: number;<br>差异内容：const EXCEPTION_PERMISSION: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const EXCEPTION_PARAMCHECK: number;<br>差异内容：const EXCEPTION_PARAMCHECK: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const EXCEPTION_UNSUPPORTED: number;<br>差异内容：const EXCEPTION_UNSUPPORTED: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const EXCEPTION_FILEIO: number;<br>差异内容：const EXCEPTION_FILEIO: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const EXCEPTION_FILEPATH: number;<br>差异内容：const EXCEPTION_FILEPATH: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const EXCEPTION_SERVICE: number;<br>差异内容：const EXCEPTION_SERVICE: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const EXCEPTION_OTHERS: number;<br>差异内容：const EXCEPTION_OTHERS: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const NETWORK_MOBILE: number;<br>差异内容：const NETWORK_MOBILE: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const NETWORK_WIFI: number;<br>差异内容：const NETWORK_WIFI: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const ERROR_CANNOT_RESUME: number;<br>差异内容：const ERROR_CANNOT_RESUME: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const ERROR_DEVICE_NOT_FOUND: number;<br>差异内容：const ERROR_DEVICE_NOT_FOUND: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const ERROR_FILE_ALREADY_EXISTS: number;<br>差异内容：const ERROR_FILE_ALREADY_EXISTS: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const ERROR_FILE_ERROR: number;<br>差异内容：const ERROR_FILE_ERROR: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const ERROR_HTTP_DATA_ERROR: number;<br>差异内容：const ERROR_HTTP_DATA_ERROR: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const ERROR_INSUFFICIENT_SPACE: number;<br>差异内容：const ERROR_INSUFFICIENT_SPACE: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const ERROR_TOO_MANY_REDIRECTS: number;<br>差异内容：const ERROR_TOO_MANY_REDIRECTS: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const ERROR_UNHANDLED_HTTP_CODE: number;<br>差异内容：const ERROR_UNHANDLED_HTTP_CODE: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const ERROR_UNKNOWN: number;<br>差异内容：const ERROR_UNKNOWN: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const ERROR_OFFLINE: number;<br>差异内容：const ERROR_OFFLINE: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const ERROR_UNSUPPORTED_NETWORK_TYPE: number;<br>差异内容：const ERROR_UNSUPPORTED_NETWORK_TYPE: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const PAUSED_QUEUED_FOR_WIFI: number;<br>差异内容：const PAUSED_QUEUED_FOR_WIFI: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const PAUSED_WAITING_FOR_NETWORK: number;<br>差异内容：const PAUSED_WAITING_FOR_NETWORK: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const PAUSED_WAITING_TO_RETRY: number;<br>差异内容：const PAUSED_WAITING_TO_RETRY: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const PAUSED_BY_USER: number;<br>差异内容：const PAUSED_BY_USER: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const PAUSED_UNKNOWN: number;<br>差异内容：const PAUSED_UNKNOWN: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const SESSION_SUCCESSFUL: number;<br>差异内容：const SESSION_SUCCESSFUL: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const SESSION_RUNNING: number;<br>差异内容：const SESSION_RUNNING: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const SESSION_PENDING: number;<br>差异内容：const SESSION_PENDING: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const SESSION_PAUSED: number;<br>差异内容：const SESSION_PAUSED: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：const SESSION_FAILED: number;<br>差异内容：const SESSION_FAILED: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：function download(config: DownloadConfig, callback: AsyncCallback\<DownloadTask>): void;<br>差异内容：function download(config: DownloadConfig, callback: AsyncCallback\<DownloadTask>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：function download(config: DownloadConfig): Promise\<DownloadTask>;<br>差异内容：function download(config: DownloadConfig): Promise\<DownloadTask>;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：function downloadFile(context: BaseContext, config: DownloadConfig, callback: AsyncCallback\<DownloadTask>): void;<br>差异内容：function downloadFile(context: BaseContext, config: DownloadConfig, callback: AsyncCallback\<DownloadTask>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：function downloadFile(context: BaseContext, config: DownloadConfig): Promise\<DownloadTask>;<br>差异内容：function downloadFile(context: BaseContext, config: DownloadConfig): Promise\<DownloadTask>;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：function upload(config: UploadConfig, callback: AsyncCallback\<UploadTask>): void;<br>差异内容：function upload(config: UploadConfig, callback: AsyncCallback\<UploadTask>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：function upload(config: UploadConfig): Promise\<UploadTask>;<br>差异内容：function upload(config: UploadConfig): Promise\<UploadTask>;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：function uploadFile(context: BaseContext, config: UploadConfig, callback: AsyncCallback\<UploadTask>): void;<br>差异内容：function uploadFile(context: BaseContext, config: UploadConfig, callback: AsyncCallback\<UploadTask>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：function uploadFile(context: BaseContext, config: UploadConfig): Promise\<UploadTask>;<br>差异内容：function uploadFile(context: BaseContext, config: UploadConfig): Promise\<UploadTask>;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：interface DownloadConfig<br>差异内容：interface DownloadConfig|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadConfig；<br>API声明：url: string;<br>差异内容：url: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadConfig；<br>API声明：header?: Object;<br>差异内容：header?: Object;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadConfig；<br>API声明：enableMetered?: boolean;<br>差异内容：enableMetered?: boolean;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadConfig；<br>API声明：enableRoaming?: boolean;<br>差异内容：enableRoaming?: boolean;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadConfig；<br>API声明：description?: string;<br>差异内容：description?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadConfig；<br>API声明：networkType?: number;<br>差异内容：networkType?: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadConfig；<br>API声明：filePath?: string;<br>差异内容：filePath?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadConfig；<br>API声明：title?: string;<br>差异内容：title?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadConfig；<br>API声明：background?: boolean;<br>差异内容：background?: boolean;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：interface DownloadInfo<br>差异内容：interface DownloadInfo|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadInfo；<br>API声明：description: string;<br>差异内容：description: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadInfo；<br>API声明：downloadedBytes: number;<br>差异内容：downloadedBytes: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadInfo；<br>API声明：downloadId: number;<br>差异内容：downloadId: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadInfo；<br>API声明：failedReason: number;<br>差异内容：failedReason: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadInfo；<br>API声明：fileName: string;<br>差异内容：fileName: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadInfo；<br>API声明：filePath: string;<br>差异内容：filePath: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadInfo；<br>API声明：pausedReason: number;<br>差异内容：pausedReason: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadInfo；<br>API声明：status: number;<br>差异内容：status: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadInfo；<br>API声明：targetURI: string;<br>差异内容：targetURI: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadInfo；<br>API声明：downloadTitle: string;<br>差异内容：downloadTitle: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadInfo；<br>API声明：downloadTotalBytes: number;<br>差异内容：downloadTotalBytes: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：interface DownloadTask<br>差异内容：interface DownloadTask|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：on(type: 'progress', callback: (receivedSize: number, totalSize: number) => void): void;<br>差异内容：on(type: 'progress', callback: (receivedSize: number, totalSize: number) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：off(type: 'progress', callback?: (receivedSize: number, totalSize: number) => void): void;<br>差异内容：off(type: 'progress', callback?: (receivedSize: number, totalSize: number) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：on(type: 'fail', callback: (err: number) => void): void;<br>差异内容：on(type: 'fail', callback: (err: number) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：off(type: 'fail', callback?: (err: number) => void): void;<br>差异内容：off(type: 'fail', callback?: (err: number) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：remove(callback: AsyncCallback\<boolean>): void;<br>差异内容：remove(callback: AsyncCallback\<boolean>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：remove(): Promise\<boolean>;<br>差异内容：remove(): Promise\<boolean>;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：pause(callback: AsyncCallback\<void>): void;<br>差异内容：pause(callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：pause(): Promise\<void>;<br>差异内容：pause(): Promise\<void>;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：resume(callback: AsyncCallback\<void>): void;<br>差异内容：resume(callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：resume(): Promise\<void>;<br>差异内容：resume(): Promise\<void>;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：query(callback: AsyncCallback\<DownloadInfo>): void;<br>差异内容：query(callback: AsyncCallback\<DownloadInfo>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：query(): Promise\<DownloadInfo>;<br>差异内容：query(): Promise\<DownloadInfo>;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：queryMimeType(callback: AsyncCallback\<string>): void;<br>差异内容：queryMimeType(callback: AsyncCallback\<string>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：queryMimeType(): Promise\<string>;<br>差异内容：queryMimeType(): Promise\<string>;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：delete(callback: AsyncCallback\<boolean>): void;<br>差异内容：delete(callback: AsyncCallback\<boolean>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：delete(): Promise\<boolean>;<br>差异内容：delete(): Promise\<boolean>;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：suspend(callback: AsyncCallback\<boolean>): void;<br>差异内容：suspend(callback: AsyncCallback\<boolean>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：suspend(): Promise\<boolean>;<br>差异内容：suspend(): Promise\<boolean>;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：restore(callback: AsyncCallback\<boolean>): void;<br>差异内容：restore(callback: AsyncCallback\<boolean>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：restore(): Promise\<boolean>;<br>差异内容：restore(): Promise\<boolean>;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：getTaskInfo(callback: AsyncCallback\<DownloadInfo>): void;<br>差异内容：getTaskInfo(callback: AsyncCallback\<DownloadInfo>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：getTaskInfo(): Promise\<DownloadInfo>;<br>差异内容：getTaskInfo(): Promise\<DownloadInfo>;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：getTaskMimeType(callback: AsyncCallback\<string>): void;<br>差异内容：getTaskMimeType(callback: AsyncCallback\<string>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：DownloadTask；<br>API声明：getTaskMimeType(): Promise\<string>;<br>差异内容：getTaskMimeType(): Promise\<string>;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：interface File<br>差异内容：interface File|api/@ohos.request.d.ts|
|新增API|NA|类名：File；<br>API声明：filename: string;<br>差异内容：filename: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：File；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：File；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：File；<br>API声明：type: string;<br>差异内容：type: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：interface RequestData<br>差异内容：interface RequestData|api/@ohos.request.d.ts|
|新增API|NA|类名：RequestData；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：RequestData；<br>API声明：value: string;<br>差异内容：value: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：interface UploadConfig<br>差异内容：interface UploadConfig|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadConfig；<br>API声明：url: string;<br>差异内容：url: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadConfig；<br>API声明：header: Object;<br>差异内容：header: Object;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadConfig；<br>API声明：method: string;<br>差异内容：method: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadConfig；<br>API声明：index?: number;<br>差异内容：index?: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadConfig；<br>API声明：begins?: number;<br>差异内容：begins?: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadConfig；<br>API声明：ends?: number;<br>差异内容：ends?: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadConfig；<br>API声明：files: Array\<File>;<br>差异内容：files: Array\<File>;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadConfig；<br>API声明：data: Array\<RequestData>;<br>差异内容：data: Array\<RequestData>;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：interface TaskState<br>差异内容：interface TaskState|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskState；<br>API声明：path: string;<br>差异内容：path: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskState；<br>API声明：responseCode: number;<br>差异内容：responseCode: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskState；<br>API声明：message: string;<br>差异内容：message: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：interface UploadTask<br>差异内容：interface UploadTask|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadTask；<br>API声明：on(type: 'progress', callback: (uploadedSize: number, totalSize: number) => void): void;<br>差异内容：on(type: 'progress', callback: (uploadedSize: number, totalSize: number) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadTask；<br>API声明：off(type: 'progress', callback?: (uploadedSize: number, totalSize: number) => void): void;<br>差异内容：off(type: 'progress', callback?: (uploadedSize: number, totalSize: number) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadTask；<br>API声明：on(type: 'headerReceive', callback: (header: object) => void): void;<br>差异内容：on(type: 'headerReceive', callback: (header: object) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadTask；<br>API声明：off(type: 'headerReceive', callback?: (header: object) => void): void;<br>差异内容：off(type: 'headerReceive', callback?: (header: object) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadTask；<br>API声明：on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;<br>差异内容：on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadTask；<br>API声明：on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;<br>差异内容：on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadTask；<br>API声明：off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;<br>差异内容：off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadTask；<br>API声明：off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;<br>差异内容：off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadTask；<br>API声明：remove(callback: AsyncCallback\<boolean>): void;<br>差异内容：remove(callback: AsyncCallback\<boolean>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadTask；<br>API声明：remove(): Promise\<boolean>;<br>差异内容：remove(): Promise\<boolean>;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadTask；<br>API声明：delete(callback: AsyncCallback\<boolean>): void;<br>差异内容：delete(callback: AsyncCallback\<boolean>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：UploadTask；<br>API声明：delete(): Promise\<boolean>;<br>差异内容：delete(): Promise\<boolean>;|api/@ohos.request.d.ts|
|新增API|NA|类名：request；<br>API声明：namespace agent<br>差异内容：namespace agent|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：enum Action<br>差异内容：enum Action|api/@ohos.request.d.ts|
|新增API|NA|类名：Action；<br>API声明：DOWNLOAD<br>差异内容：DOWNLOAD|api/@ohos.request.d.ts|
|新增API|NA|类名：Action；<br>API声明：UPLOAD<br>差异内容：UPLOAD|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：enum Mode<br>差异内容：enum Mode|api/@ohos.request.d.ts|
|新增API|NA|类名：Mode；<br>API声明：BACKGROUND<br>差异内容：BACKGROUND|api/@ohos.request.d.ts|
|新增API|NA|类名：Mode；<br>API声明：FOREGROUND<br>差异内容：FOREGROUND|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：enum Network<br>差异内容：enum Network|api/@ohos.request.d.ts|
|新增API|NA|类名：Network；<br>API声明：ANY<br>差异内容：ANY|api/@ohos.request.d.ts|
|新增API|NA|类名：Network；<br>API声明：WIFI<br>差异内容：WIFI|api/@ohos.request.d.ts|
|新增API|NA|类名：Network；<br>API声明：CELLULAR<br>差异内容：CELLULAR|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：enum BroadcastEvent<br>差异内容：enum BroadcastEvent|api/@ohos.request.d.ts|
|新增API|NA|类名：BroadcastEvent；<br>API声明：COMPLETE = 'ohos.request.event.COMPLETE'<br>差异内容：COMPLETE = 'ohos.request.event.COMPLETE'|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：interface FileSpec<br>差异内容：interface FileSpec|api/@ohos.request.d.ts|
|新增API|NA|类名：FileSpec；<br>API声明：path: string;<br>差异内容：path: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：FileSpec；<br>API声明：mimeType?: string;<br>差异内容：mimeType?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：FileSpec；<br>API声明：filename?: string;<br>差异内容：filename?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：FileSpec；<br>API声明：extras?: object;<br>差异内容：extras?: object;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：interface FormItem<br>差异内容：interface FormItem|api/@ohos.request.d.ts|
|新增API|NA|类名：FormItem；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：FormItem；<br>API声明：value: string \| FileSpec \| Array\<FileSpec>;<br>差异内容：value: string \| FileSpec \| Array\<FileSpec>;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：interface Config<br>差异内容：interface Config|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：action: Action;<br>差异内容：action: Action;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：url: string;<br>差异内容：url: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：title?: string;<br>差异内容：title?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：description?: string;<br>差异内容：description?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：mode?: Mode;<br>差异内容：mode?: Mode;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：overwrite?: boolean;<br>差异内容：overwrite?: boolean;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：method?: string;<br>差异内容：method?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：headers?: object;<br>差异内容：headers?: object;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：data?: string \| Array\<FormItem>;<br>差异内容：data?: string \| Array\<FormItem>;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：saveas?: string;<br>差异内容：saveas?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：network?: Network;<br>差异内容：network?: Network;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：metered?: boolean;<br>差异内容：metered?: boolean;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：roaming?: boolean;<br>差异内容：roaming?: boolean;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：retry?: boolean;<br>差异内容：retry?: boolean;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：redirect?: boolean;<br>差异内容：redirect?: boolean;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：index?: number;<br>差异内容：index?: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：begins?: number;<br>差异内容：begins?: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：ends?: number;<br>差异内容：ends?: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：gauge?: boolean;<br>差异内容：gauge?: boolean;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：precise?: boolean;<br>差异内容：precise?: boolean;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：token?: string;<br>差异内容：token?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：priority?: number;<br>差异内容：priority?: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：Config；<br>API声明：extras?: object;<br>差异内容：extras?: object;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：enum State<br>差异内容：enum State|api/@ohos.request.d.ts|
|新增API|NA|类名：State；<br>API声明：INITIALIZED = 0x00<br>差异内容：INITIALIZED = 0x00|api/@ohos.request.d.ts|
|新增API|NA|类名：State；<br>API声明：WAITING = 0x10<br>差异内容：WAITING = 0x10|api/@ohos.request.d.ts|
|新增API|NA|类名：State；<br>API声明：RUNNING = 0x20<br>差异内容：RUNNING = 0x20|api/@ohos.request.d.ts|
|新增API|NA|类名：State；<br>API声明：RETRYING = 0x21<br>差异内容：RETRYING = 0x21|api/@ohos.request.d.ts|
|新增API|NA|类名：State；<br>API声明：PAUSED = 0x30<br>差异内容：PAUSED = 0x30|api/@ohos.request.d.ts|
|新增API|NA|类名：State；<br>API声明：STOPPED = 0x31<br>差异内容：STOPPED = 0x31|api/@ohos.request.d.ts|
|新增API|NA|类名：State；<br>API声明：COMPLETED = 0x40<br>差异内容：COMPLETED = 0x40|api/@ohos.request.d.ts|
|新增API|NA|类名：State；<br>API声明：FAILED = 0x41<br>差异内容：FAILED = 0x41|api/@ohos.request.d.ts|
|新增API|NA|类名：State；<br>API声明：REMOVED = 0x50<br>差异内容：REMOVED = 0x50|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：interface Progress<br>差异内容：interface Progress|api/@ohos.request.d.ts|
|新增API|NA|类名：Progress；<br>API声明：readonly state: State;<br>差异内容：readonly state: State;|api/@ohos.request.d.ts|
|新增API|NA|类名：Progress；<br>API声明：readonly index: number;<br>差异内容：readonly index: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：Progress；<br>API声明：readonly processed: number;<br>差异内容：readonly processed: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：Progress；<br>API声明：readonly sizes: Array\<number>;<br>差异内容：readonly sizes: Array\<number>;|api/@ohos.request.d.ts|
|新增API|NA|类名：Progress；<br>API声明：readonly extras?: object;<br>差异内容：readonly extras?: object;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：enum Faults<br>差异内容：enum Faults|api/@ohos.request.d.ts|
|新增API|NA|类名：Faults；<br>API声明：OTHERS = 0xFF<br>差异内容：OTHERS = 0xFF|api/@ohos.request.d.ts|
|新增API|NA|类名：Faults；<br>API声明：DISCONNECTED = 0x00<br>差异内容：DISCONNECTED = 0x00|api/@ohos.request.d.ts|
|新增API|NA|类名：Faults；<br>API声明：TIMEOUT = 0x10<br>差异内容：TIMEOUT = 0x10|api/@ohos.request.d.ts|
|新增API|NA|类名：Faults；<br>API声明：PROTOCOL = 0x20<br>差异内容：PROTOCOL = 0x20|api/@ohos.request.d.ts|
|新增API|NA|类名：Faults；<br>API声明：FSIO = 0x40<br>差异内容：FSIO = 0x40|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：interface Filter<br>差异内容：interface Filter|api/@ohos.request.d.ts|
|新增API|NA|类名：Filter；<br>API声明：before?: number;<br>差异内容：before?: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：Filter；<br>API声明：after?: number;<br>差异内容：after?: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：Filter；<br>API声明：state?: State;<br>差异内容：state?: State;|api/@ohos.request.d.ts|
|新增API|NA|类名：Filter；<br>API声明：action?: Action;<br>差异内容：action?: Action;|api/@ohos.request.d.ts|
|新增API|NA|类名：Filter；<br>API声明：mode?: Mode;<br>差异内容：mode?: Mode;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：interface TaskInfo<br>差异内容：interface TaskInfo|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly saveas?: string;<br>差异内容：readonly saveas?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly url?: string;<br>差异内容：readonly url?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly data?: string \| Array\<FormItem>;<br>差异内容：readonly data?: string \| Array\<FormItem>;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly tid: string;<br>差异内容：readonly tid: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly title: string;<br>差异内容：readonly title: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly description: string;<br>差异内容：readonly description: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly action: Action;<br>差异内容：readonly action: Action;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly mode: Mode;<br>差异内容：readonly mode: Mode;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly priority: number;<br>差异内容：readonly priority: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly mimeType: string;<br>差异内容：readonly mimeType: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly progress: Progress;<br>差异内容：readonly progress: Progress;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly gauge: boolean;<br>差异内容：readonly gauge: boolean;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly ctime: number;<br>差异内容：readonly ctime: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly mtime: number;<br>差异内容：readonly mtime: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly retry: boolean;<br>差异内容：readonly retry: boolean;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly tries: number;<br>差异内容：readonly tries: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly faults: Faults;<br>差异内容：readonly faults: Faults;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly reason: string;<br>差异内容：readonly reason: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：readonly extras?: object;<br>差异内容：readonly extras?: object;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：interface Task<br>差异内容：interface Task|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：readonly tid: string;<br>差异内容：readonly tid: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：config: Config;<br>差异内容：config: Config;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：on(event: 'progress', callback: (progress: Progress) => void): void;<br>差异内容：on(event: 'progress', callback: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：off(event: 'progress', callback?: (progress: Progress) => void): void;<br>差异内容：off(event: 'progress', callback?: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：on(event: 'completed', callback: (progress: Progress) => void): void;<br>差异内容：on(event: 'completed', callback: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：off(event: 'completed', callback?: (progress: Progress) => void): void;<br>差异内容：off(event: 'completed', callback?: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：on(event: 'failed', callback: (progress: Progress) => void): void;<br>差异内容：on(event: 'failed', callback: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：off(event: 'failed', callback?: (progress: Progress) => void): void;<br>差异内容：off(event: 'failed', callback?: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：on(event: 'pause', callback: (progress: Progress) => void): void;<br>差异内容：on(event: 'pause', callback: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：off(event: 'pause', callback?: (progress: Progress) => void): void;<br>差异内容：off(event: 'pause', callback?: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：on(event: 'resume', callback: (progress: Progress) => void): void;<br>差异内容：on(event: 'resume', callback: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：off(event: 'resume', callback?: (progress: Progress) => void): void;<br>差异内容：off(event: 'resume', callback?: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：on(event: 'remove', callback: (progress: Progress) => void): void;<br>差异内容：on(event: 'remove', callback: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：off(event: 'remove', callback?: (progress: Progress) => void): void;<br>差异内容：off(event: 'remove', callback?: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：start(callback: AsyncCallback\<void>): void;<br>差异内容：start(callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：start(): Promise\<void>;<br>差异内容：start(): Promise\<void>;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：pause(callback: AsyncCallback\<void>): void;<br>差异内容：pause(callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：pause(): Promise\<void>;<br>差异内容：pause(): Promise\<void>;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：resume(callback: AsyncCallback\<void>): void;<br>差异内容：resume(callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：resume(): Promise\<void>;<br>差异内容：resume(): Promise\<void>;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：stop(callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：stop(): Promise\<void>;<br>差异内容：stop(): Promise\<void>;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：function create(context: BaseContext, config: Config, callback: AsyncCallback\<Task>): void;<br>差异内容：function create(context: BaseContext, config: Config, callback: AsyncCallback\<Task>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：function create(context: BaseContext, config: Config): Promise\<Task>;<br>差异内容：function create(context: BaseContext, config: Config): Promise\<Task>;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：function getTask(context: BaseContext, id: string, token?: string): Promise\<Task>;<br>差异内容：function getTask(context: BaseContext, id: string, token?: string): Promise\<Task>;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：function remove(id: string, callback: AsyncCallback\<void>): void;<br>差异内容：function remove(id: string, callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：function remove(id: string): Promise\<void>;<br>差异内容：function remove(id: string): Promise\<void>;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：function show(id: string, callback: AsyncCallback\<TaskInfo>): void;<br>差异内容：function show(id: string, callback: AsyncCallback\<TaskInfo>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：function show(id: string): Promise\<TaskInfo>;<br>差异内容：function show(id: string): Promise\<TaskInfo>;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：function touch(id: string, token: string, callback: AsyncCallback\<TaskInfo>): void;<br>差异内容：function touch(id: string, token: string, callback: AsyncCallback\<TaskInfo>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：function touch(id: string, token: string): Promise\<TaskInfo>;<br>差异内容：function touch(id: string, token: string): Promise\<TaskInfo>;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：function search(callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：function search(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：function search(filter: Filter, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：function search(filter: Filter, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：function search(filter?: Filter): Promise\<Array\<string>>;<br>差异内容：function search(filter?: Filter): Promise\<Array\<string>>;|api/@ohos.request.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace runningLock<br>差异内容：declare namespace runningLock|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：runningLock；<br>API声明：class RunningLock<br>差异内容：class RunningLock|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：RunningLock；<br>API声明：lock(timeout: number): void;<br>差异内容：lock(timeout: number): void;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：RunningLock；<br>API声明：hold(timeout: number): void;<br>差异内容：hold(timeout: number): void;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：RunningLock；<br>API声明：isUsed(): boolean;<br>差异内容：isUsed(): boolean;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：RunningLock；<br>API声明：isHolding(): boolean;<br>差异内容：isHolding(): boolean;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：RunningLock；<br>API声明：unlock(): void;<br>差异内容：unlock(): void;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：RunningLock；<br>API声明：unhold(): void;<br>差异内容：unhold(): void;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：runningLock；<br>API声明：export enum RunningLockType<br>差异内容：export enum RunningLockType|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：RunningLockType；<br>API声明：BACKGROUND = 1<br>差异内容：BACKGROUND = 1|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：RunningLockType；<br>API声明：PROXIMITY_SCREEN_CONTROL<br>差异内容：PROXIMITY_SCREEN_CONTROL|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：runningLock；<br>API声明：function isRunningLockTypeSupported(type: RunningLockType, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isRunningLockTypeSupported(type: RunningLockType, callback: AsyncCallback\<boolean>): void;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：runningLock；<br>API声明：function isRunningLockTypeSupported(type: RunningLockType): Promise\<boolean>;<br>差异内容：function isRunningLockTypeSupported(type: RunningLockType): Promise\<boolean>;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：runningLock；<br>API声明：function isSupported(type: RunningLockType): boolean;<br>差异内容：function isSupported(type: RunningLockType): boolean;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：runningLock；<br>API声明：function createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback\<RunningLock>): void;<br>差异内容：function createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback\<RunningLock>): void;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：runningLock；<br>API声明：function createRunningLock(name: string, type: RunningLockType): Promise\<RunningLock>;<br>差异内容：function createRunningLock(name: string, type: RunningLockType): Promise\<RunningLock>;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：runningLock；<br>API声明：function create(name: string, type: RunningLockType, callback: AsyncCallback\<RunningLock>): void;<br>差异内容：function create(name: string, type: RunningLockType, callback: AsyncCallback\<RunningLock>): void;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：runningLock；<br>API声明：function create(name: string, type: RunningLockType): Promise\<RunningLock>;<br>差异内容：function create(name: string, type: RunningLockType): Promise\<RunningLock>;|api/@ohos.runningLock.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace screenLock<br>差异内容：declare namespace screenLock|api/@ohos.screenLock.d.ts|
|新增API|NA|类名：screenLock；<br>API声明：function isScreenLocked(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isScreenLocked(callback: AsyncCallback\<boolean>): void;|api/@ohos.screenLock.d.ts|
|新增API|NA|类名：screenLock；<br>API声明：function isScreenLocked(): Promise\<boolean>;<br>差异内容：function isScreenLocked(): Promise\<boolean>;|api/@ohos.screenLock.d.ts|
|新增API|NA|类名：screenLock；<br>API声明：function isSecureMode(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isSecureMode(callback: AsyncCallback\<boolean>): void;|api/@ohos.screenLock.d.ts|
|新增API|NA|类名：screenLock；<br>API声明：function isSecureMode(): Promise\<boolean>;<br>差异内容：function isSecureMode(): Promise\<boolean>;|api/@ohos.screenLock.d.ts|
|新增API|NA|类名：screenLock；<br>API声明：function unlockScreen(callback: AsyncCallback\<void>): void;<br>差异内容：function unlockScreen(callback: AsyncCallback\<void>): void;|api/@ohos.screenLock.d.ts|
|新增API|NA|类名：screenLock；<br>API声明：function unlockScreen(): Promise\<void>;<br>差异内容：function unlockScreen(): Promise\<void>;|api/@ohos.screenLock.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace settings<br>差异内容：declare namespace settings|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：namespace domainName<br>差异内容：namespace domainName|api/@ohos.settings.d.ts|
|新增API|NA|类名：domainName；<br>API声明：const DEVICE_SHARED: string;<br>差异内容：const DEVICE_SHARED: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：domainName；<br>API声明：const USER_PROPERTY: string;<br>差异内容：const USER_PROPERTY: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：namespace date<br>差异内容：namespace date|api/@ohos.settings.d.ts|
|新增API|NA|类名：date；<br>API声明：const DATE_FORMAT: string;<br>差异内容：const DATE_FORMAT: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：date；<br>API声明：const TIME_FORMAT: string;<br>差异内容：const TIME_FORMAT: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：date；<br>API声明：const AUTO_GAIN_TIME: string;<br>差异内容：const AUTO_GAIN_TIME: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：date；<br>API声明：const AUTO_GAIN_TIME_ZONE: string;<br>差异内容：const AUTO_GAIN_TIME_ZONE: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：namespace display<br>差异内容：namespace display|api/@ohos.settings.d.ts|
|新增API|NA|类名：display；<br>API声明：const FONT_SCALE: string;<br>差异内容：const FONT_SCALE: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：display；<br>API声明：const SCREEN_BRIGHTNESS_STATUS: string;<br>差异内容：const SCREEN_BRIGHTNESS_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：display；<br>API声明：const AUTO_SCREEN_BRIGHTNESS: string;<br>差异内容：const AUTO_SCREEN_BRIGHTNESS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：display；<br>API声明：const AUTO_SCREEN_BRIGHTNESS_MODE: number;<br>差异内容：const AUTO_SCREEN_BRIGHTNESS_MODE: number;|api/@ohos.settings.d.ts|
|新增API|NA|类名：display；<br>API声明：const MANUAL_SCREEN_BRIGHTNESS_MODE: number;<br>差异内容：const MANUAL_SCREEN_BRIGHTNESS_MODE: number;|api/@ohos.settings.d.ts|
|新增API|NA|类名：display；<br>API声明：const SCREEN_OFF_TIMEOUT: string;<br>差异内容：const SCREEN_OFF_TIMEOUT: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：display；<br>API声明：const DEFAULT_SCREEN_ROTATION: string;<br>差异内容：const DEFAULT_SCREEN_ROTATION: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：display；<br>API声明：const ANIMATOR_DURATION_SCALE: string;<br>差异内容：const ANIMATOR_DURATION_SCALE: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：display；<br>API声明：const TRANSITION_ANIMATION_SCALE: string;<br>差异内容：const TRANSITION_ANIMATION_SCALE: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：display；<br>API声明：const WINDOW_ANIMATION_SCALE: string;<br>差异内容：const WINDOW_ANIMATION_SCALE: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：display；<br>API声明：const DISPLAY_INVERSION_STATUS: string;<br>差异内容：const DISPLAY_INVERSION_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：namespace general<br>差异内容：namespace general|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const SETUP_WIZARD_FINISHED: string;<br>差异内容：const SETUP_WIZARD_FINISHED: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const END_BUTTON_ACTION: string;<br>差异内容：const END_BUTTON_ACTION: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const ACCELEROMETER_ROTATION_STATUS: string;<br>差异内容：const ACCELEROMETER_ROTATION_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const AIRPLANE_MODE_STATUS: string;<br>差异内容：const AIRPLANE_MODE_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const DEVICE_PROVISION_STATUS: string;<br>差异内容：const DEVICE_PROVISION_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const HDC_STATUS: string;<br>差异内容：const HDC_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const BOOT_COUNTING: string;<br>差异内容：const BOOT_COUNTING: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const CONTACT_METADATA_SYNC_STATUS: string;<br>差异内容：const CONTACT_METADATA_SYNC_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const DEVELOPMENT_SETTINGS_STATUS: string;<br>差异内容：const DEVELOPMENT_SETTINGS_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const DEVICE_NAME: string;<br>差异内容：const DEVICE_NAME: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const USB_STORAGE_STATUS: string;<br>差异内容：const USB_STORAGE_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const DEBUGGER_WAITING: string;<br>差异内容：const DEBUGGER_WAITING: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const DEBUG_APP_PACKAGE: string;<br>差异内容：const DEBUG_APP_PACKAGE: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const ACCESSIBILITY_STATUS: string;<br>差异内容：const ACCESSIBILITY_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const ACTIVATED_ACCESSIBILITY_SERVICES: string;<br>差异内容：const ACTIVATED_ACCESSIBILITY_SERVICES: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const GEOLOCATION_ORIGINS_ALLOWED: string;<br>差异内容：const GEOLOCATION_ORIGINS_ALLOWED: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const SKIP_USE_HINTS: string;<br>差异内容：const SKIP_USE_HINTS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：general；<br>API声明：const TOUCH_EXPLORATION_STATUS: string;<br>差异内容：const TOUCH_EXPLORATION_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：namespace input<br>差异内容：namespace input|api/@ohos.settings.d.ts|
|新增API|NA|类名：input；<br>API声明：const DEFAULT_INPUT_METHOD: string;<br>差异内容：const DEFAULT_INPUT_METHOD: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：input；<br>API声明：const ACTIVATED_INPUT_METHOD_SUB_MODE: string;<br>差异内容：const ACTIVATED_INPUT_METHOD_SUB_MODE: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：input；<br>API声明：const ACTIVATED_INPUT_METHODS: string;<br>差异内容：const ACTIVATED_INPUT_METHODS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：input；<br>API声明：const SELECTOR_VISIBILITY_FOR_INPUT_METHOD: string;<br>差异内容：const SELECTOR_VISIBILITY_FOR_INPUT_METHOD: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：input；<br>API声明：const AUTO_CAPS_TEXT_INPUT: string;<br>差异内容：const AUTO_CAPS_TEXT_INPUT: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：input；<br>API声明：const AUTO_PUNCTUATE_TEXT_INPUT: string;<br>差异内容：const AUTO_PUNCTUATE_TEXT_INPUT: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：input；<br>API声明：const AUTO_REPLACE_TEXT_INPUT: string;<br>差异内容：const AUTO_REPLACE_TEXT_INPUT: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：input；<br>API声明：const SHOW_PASSWORD_TEXT_INPUT: string;<br>差异内容：const SHOW_PASSWORD_TEXT_INPUT: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：namespace network<br>差异内容：namespace network|api/@ohos.settings.d.ts|
|新增API|NA|类名：network；<br>API声明：const DATA_ROAMING_STATUS: string;<br>差异内容：const DATA_ROAMING_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：network；<br>API声明：const HTTP_PROXY_CFG: string;<br>差异内容：const HTTP_PROXY_CFG: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：network；<br>API声明：const NETWORK_PREFERENCE_USAGE: string;<br>差异内容：const NETWORK_PREFERENCE_USAGE: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：namespace phone<br>差异内容：namespace phone|api/@ohos.settings.d.ts|
|新增API|NA|类名：phone；<br>API声明：const RTT_CALLING_STATUS: string;<br>差异内容：const RTT_CALLING_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：namespace sound<br>差异内容：namespace sound|api/@ohos.settings.d.ts|
|新增API|NA|类名：sound；<br>API声明：const VIBRATE_WHILE_RINGING: string;<br>差异内容：const VIBRATE_WHILE_RINGING: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：sound；<br>API声明：const DEFAULT_ALARM_ALERT: string;<br>差异内容：const DEFAULT_ALARM_ALERT: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：sound；<br>API声明：const DTMF_TONE_TYPE_WHILE_DIALING: string;<br>差异内容：const DTMF_TONE_TYPE_WHILE_DIALING: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：sound；<br>API声明：const DTMF_TONE_WHILE_DIALING: string;<br>差异内容：const DTMF_TONE_WHILE_DIALING: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：sound；<br>API声明：const AFFECTED_MODE_RINGER_STREAMS: string;<br>差异内容：const AFFECTED_MODE_RINGER_STREAMS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：sound；<br>API声明：const AFFECTED_MUTE_STREAMS: string;<br>差异内容：const AFFECTED_MUTE_STREAMS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：sound；<br>API声明：const DEFAULT_NOTIFICATION_SOUND: string;<br>差异内容：const DEFAULT_NOTIFICATION_SOUND: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：sound；<br>API声明：const DEFAULT_RINGTONE: string;<br>差异内容：const DEFAULT_RINGTONE: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：sound；<br>API声明：const SOUND_EFFECTS_STATUS: string;<br>差异内容：const SOUND_EFFECTS_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：sound；<br>API声明：const VIBRATE_STATUS: string;<br>差异内容：const VIBRATE_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：sound；<br>API声明：const HAPTIC_FEEDBACK_STATUS: string;<br>差异内容：const HAPTIC_FEEDBACK_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：namespace TTS<br>差异内容：namespace TTS|api/@ohos.settings.d.ts|
|新增API|NA|类名：TTS；<br>API声明：const DEFAULT_TTS_PITCH: string;<br>差异内容：const DEFAULT_TTS_PITCH: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：TTS；<br>API声明：const DEFAULT_TTS_RATE: string;<br>差异内容：const DEFAULT_TTS_RATE: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：TTS；<br>API声明：const DEFAULT_TTS_SYNTH: string;<br>差异内容：const DEFAULT_TTS_SYNTH: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：TTS；<br>API声明：const ENABLED_TTS_PLUGINS: string;<br>差异内容：const ENABLED_TTS_PLUGINS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：namespace wireless<br>差异内容：namespace wireless|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const BLUETOOTH_DISCOVER_ABILITY_STATUS: string;<br>差异内容：const BLUETOOTH_DISCOVER_ABILITY_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const BLUETOOTH_DISCOVER_TIMEOUT: string;<br>差异内容：const BLUETOOTH_DISCOVER_TIMEOUT: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const AIRPLANE_MODE_RADIOS: string;<br>差异内容：const AIRPLANE_MODE_RADIOS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const BLUETOOTH_STATUS: string;<br>差异内容：const BLUETOOTH_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const BLUETOOTH_RADIO: string;<br>差异内容：const BLUETOOTH_RADIO: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const CELL_RADIO: string;<br>差异内容：const CELL_RADIO: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const NFC_RADIO: string;<br>差异内容：const NFC_RADIO: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const WIFI_RADIO: string;<br>差异内容：const WIFI_RADIO: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const OWNER_LOCKDOWN_WIFI_CFG: string;<br>差异内容：const OWNER_LOCKDOWN_WIFI_CFG: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const WIFI_DHCP_MAX_RETRY_COUNT: string;<br>差异内容：const WIFI_DHCP_MAX_RETRY_COUNT: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const WIFI_TO_MOBILE_DATA_AWAKE_TIMEOUT: string;<br>差异内容：const WIFI_TO_MOBILE_DATA_AWAKE_TIMEOUT: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const WIFI_STATUS: string;<br>差异内容：const WIFI_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：wireless；<br>API声明：const WIFI_WATCHDOG_STATUS: string;<br>差异内容：const WIFI_WATCHDOG_STATUS: string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function getURI(name: string, callback: AsyncCallback\<object>): void;<br>差异内容：function getURI(name: string, callback: AsyncCallback\<object>): void;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function getURI(name: string): Promise\<object>;<br>差异内容：function getURI(name: string): Promise\<object>;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function getValue(dataAbilityHelper: DataAbilityHelper, name: string, callback: AsyncCallback\<object>): void;<br>差异内容：function getValue(dataAbilityHelper: DataAbilityHelper, name: string, callback: AsyncCallback\<object>): void;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function getValue(dataAbilityHelper: DataAbilityHelper, name: string): Promise\<object>;<br>差异内容：function getValue(dataAbilityHelper: DataAbilityHelper, name: string): Promise\<object>;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function getValue(context: Context, name: string, callback: AsyncCallback\<string>): void;<br>差异内容：function getValue(context: Context, name: string, callback: AsyncCallback\<string>): void;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function getValue(context: Context, name: string): Promise\<string>;<br>差异内容：function getValue(context: Context, name: string): Promise\<string>;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function getValue(context: Context, name: string, domainName: string): Promise\<string>;<br>差异内容：function getValue(context: Context, name: string, domainName: string): Promise\<string>;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function setValue(context: Context, name: string, value: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：function setValue(context: Context, name: string, value: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function setValue(context: Context, name: string, value: string): Promise\<boolean>;<br>差异内容：function setValue(context: Context, name: string, value: string): Promise\<boolean>;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function setValue(context: Context, name: string, value: string, domainName: string): Promise\<boolean>;<br>差异内容：function setValue(context: Context, name: string, value: string, domainName: string): Promise\<boolean>;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function enableAirplaneMode(enable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：function enableAirplaneMode(enable: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function enableAirplaneMode(enable: boolean): Promise\<void>;<br>差异内容：function enableAirplaneMode(enable: boolean): Promise\<void>;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function canShowFloating(callback: AsyncCallback\<boolean>): void;<br>差异内容：function canShowFloating(callback: AsyncCallback\<boolean>): void;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function canShowFloating(): Promise\<boolean>;<br>差异内容：function canShowFloating(): Promise\<boolean>;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function getUriSync(name: string): string;<br>差异内容：function getUriSync(name: string): string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function getValueSync(dataAbilityHelper: DataAbilityHelper, name: string, defValue: string): string;<br>差异内容：function getValueSync(dataAbilityHelper: DataAbilityHelper, name: string, defValue: string): string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function getValueSync(context: Context, name: string, defValue: string): string;<br>差异内容：function getValueSync(context: Context, name: string, defValue: string): string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function getValueSync(context: Context, name: string, defValue: string, domainName: string): string;<br>差异内容：function getValueSync(context: Context, name: string, defValue: string, domainName: string): string;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function setValueSync(dataAbilityHelper: DataAbilityHelper, name: string, value: string): boolean;<br>差异内容：function setValueSync(dataAbilityHelper: DataAbilityHelper, name: string, value: string): boolean;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function setValueSync(context: Context, name: string, value: string): boolean;<br>差异内容：function setValueSync(context: Context, name: string, value: string): boolean;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function setValueSync(context: Context, name: string, value: string, domainName: string): boolean;<br>差异内容：function setValueSync(context: Context, name: string, value: string, domainName: string): boolean;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function registerKeyObserver(context: Context, name: string, domainName: string, observer: AsyncCallback\<void>): boolean;<br>差异内容：function registerKeyObserver(context: Context, name: string, domainName: string, observer: AsyncCallback\<void>): boolean;|api/@ohos.settings.d.ts|
|新增API|NA|类名：settings；<br>API声明：function unregisterKeyObserver(context: Context, name: string, domainName: string): boolean;<br>差异内容：function unregisterKeyObserver(context: Context, name: string, domainName: string): boolean;|api/@ohos.settings.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace systemDateTime<br>差异内容：declare namespace systemDateTime|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getCurrentTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>差异内容：function getCurrentTime(isNano: boolean, callback: AsyncCallback\<number>): void;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getCurrentTime(callback: AsyncCallback\<number>): void;<br>差异内容：function getCurrentTime(callback: AsyncCallback\<number>): void;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getCurrentTime(isNano?: boolean): Promise\<number>;<br>差异内容：function getCurrentTime(isNano?: boolean): Promise\<number>;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getTime(isNanoseconds?: boolean): number;<br>差异内容：function getTime(isNanoseconds?: boolean): number;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getRealActiveTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>差异内容：function getRealActiveTime(isNano: boolean, callback: AsyncCallback\<number>): void;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getRealActiveTime(callback: AsyncCallback\<number>): void;<br>差异内容：function getRealActiveTime(callback: AsyncCallback\<number>): void;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getRealActiveTime(isNano?: boolean): Promise\<number>;<br>差异内容：function getRealActiveTime(isNano?: boolean): Promise\<number>;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getRealTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>差异内容：function getRealTime(isNano: boolean, callback: AsyncCallback\<number>): void;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getRealTime(callback: AsyncCallback\<number>): void;<br>差异内容：function getRealTime(callback: AsyncCallback\<number>): void;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getRealTime(isNano?: boolean): Promise\<number>;<br>差异内容：function getRealTime(isNano?: boolean): Promise\<number>;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：enum TimeType<br>差异内容：enum TimeType|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：TimeType；<br>API声明：STARTUP<br>差异内容：STARTUP|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：TimeType；<br>API声明：ACTIVE<br>差异内容：ACTIVE|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getUptime(timeType: TimeType, isNanoseconds?: boolean): number;<br>差异内容：function getUptime(timeType: TimeType, isNanoseconds?: boolean): number;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getDate(callback: AsyncCallback\<Date>): void;<br>差异内容：function getDate(callback: AsyncCallback\<Date>): void;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getDate(): Promise\<Date>;<br>差异内容：function getDate(): Promise\<Date>;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getTimezone(callback: AsyncCallback\<string>): void;<br>差异内容：function getTimezone(callback: AsyncCallback\<string>): void;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getTimezone(): Promise\<string>;<br>差异内容：function getTimezone(): Promise\<string>;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：systemDateTime；<br>API声明：function getTimezoneSync(): string;<br>差异内容：function getTimezoneSync(): string;|api/@ohos.systemDateTime.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace systemTime<br>差异内容：declare namespace systemTime|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function setTime(time: number, callback: AsyncCallback\<void>): void;<br>差异内容：function setTime(time: number, callback: AsyncCallback\<void>): void;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function setTime(time: number): Promise\<void>;<br>差异内容：function setTime(time: number): Promise\<void>;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getCurrentTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>差异内容：function getCurrentTime(isNano: boolean, callback: AsyncCallback\<number>): void;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getCurrentTime(callback: AsyncCallback\<number>): void;<br>差异内容：function getCurrentTime(callback: AsyncCallback\<number>): void;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getCurrentTime(isNano?: boolean): Promise\<number>;<br>差异内容：function getCurrentTime(isNano?: boolean): Promise\<number>;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getRealActiveTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>差异内容：function getRealActiveTime(isNano: boolean, callback: AsyncCallback\<number>): void;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getRealActiveTime(callback: AsyncCallback\<number>): void;<br>差异内容：function getRealActiveTime(callback: AsyncCallback\<number>): void;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getRealActiveTime(isNano?: boolean): Promise\<number>;<br>差异内容：function getRealActiveTime(isNano?: boolean): Promise\<number>;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getRealTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>差异内容：function getRealTime(isNano: boolean, callback: AsyncCallback\<number>): void;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getRealTime(callback: AsyncCallback\<number>): void;<br>差异内容：function getRealTime(callback: AsyncCallback\<number>): void;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getRealTime(isNano?: boolean): Promise\<number>;<br>差异内容：function getRealTime(isNano?: boolean): Promise\<number>;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function setDate(date: Date, callback: AsyncCallback\<void>): void;<br>差异内容：function setDate(date: Date, callback: AsyncCallback\<void>): void;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function setDate(date: Date): Promise\<void>;<br>差异内容：function setDate(date: Date): Promise\<void>;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getDate(callback: AsyncCallback\<Date>): void;<br>差异内容：function getDate(callback: AsyncCallback\<Date>): void;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getDate(): Promise\<Date>;<br>差异内容：function getDate(): Promise\<Date>;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function setTimezone(timezone: string, callback: AsyncCallback\<void>): void;<br>差异内容：function setTimezone(timezone: string, callback: AsyncCallback\<void>): void;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function setTimezone(timezone: string): Promise\<void>;<br>差异内容：function setTimezone(timezone: string): Promise\<void>;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getTimezone(callback: AsyncCallback\<string>): void;<br>差异内容：function getTimezone(callback: AsyncCallback\<string>): void;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：systemTime；<br>API声明：function getTimezone(): Promise\<string>;<br>差异内容：function getTimezone(): Promise\<string>;|api/@ohos.systemTime.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace thermal<br>差异内容：declare namespace thermal|api/@ohos.thermal.d.ts|
|新增API|NA|类名：thermal；<br>API声明：export enum ThermalLevel<br>差异内容：export enum ThermalLevel|api/@ohos.thermal.d.ts|
|新增API|NA|类名：ThermalLevel；<br>API声明：COOL = 0<br>差异内容：COOL = 0|api/@ohos.thermal.d.ts|
|新增API|NA|类名：ThermalLevel；<br>API声明：NORMAL = 1<br>差异内容：NORMAL = 1|api/@ohos.thermal.d.ts|
|新增API|NA|类名：ThermalLevel；<br>API声明：WARM = 2<br>差异内容：WARM = 2|api/@ohos.thermal.d.ts|
|新增API|NA|类名：ThermalLevel；<br>API声明：HOT = 3<br>差异内容：HOT = 3|api/@ohos.thermal.d.ts|
|新增API|NA|类名：ThermalLevel；<br>API声明：OVERHEATED = 4<br>差异内容：OVERHEATED = 4|api/@ohos.thermal.d.ts|
|新增API|NA|类名：ThermalLevel；<br>API声明：WARNING = 5<br>差异内容：WARNING = 5|api/@ohos.thermal.d.ts|
|新增API|NA|类名：ThermalLevel；<br>API声明：EMERGENCY = 6<br>差异内容：EMERGENCY = 6|api/@ohos.thermal.d.ts|
|新增API|NA|类名：ThermalLevel；<br>API声明：ESCAPE = 7<br>差异内容：ESCAPE = 7|api/@ohos.thermal.d.ts|
|新增API|NA|类名：thermal；<br>API声明：function subscribeThermalLevel(callback: AsyncCallback\<ThermalLevel>): void;<br>差异内容：function subscribeThermalLevel(callback: AsyncCallback\<ThermalLevel>): void;|api/@ohos.thermal.d.ts|
|新增API|NA|类名：thermal；<br>API声明：function registerThermalLevelCallback(callback: Callback\<ThermalLevel>): void;<br>差异内容：function registerThermalLevelCallback(callback: Callback\<ThermalLevel>): void;|api/@ohos.thermal.d.ts|
|新增API|NA|类名：thermal；<br>API声明：function unsubscribeThermalLevel(callback?: AsyncCallback\<void>): void;<br>差异内容：function unsubscribeThermalLevel(callback?: AsyncCallback\<void>): void;|api/@ohos.thermal.d.ts|
|新增API|NA|类名：thermal；<br>API声明：function unregisterThermalLevelCallback(callback?: Callback\<void>): void;<br>差异内容：function unregisterThermalLevelCallback(callback?: Callback\<void>): void;|api/@ohos.thermal.d.ts|
|新增API|NA|类名：thermal；<br>API声明：function getThermalLevel(): ThermalLevel;<br>差异内容：function getThermalLevel(): ThermalLevel;|api/@ohos.thermal.d.ts|
|新增API|NA|类名：thermal；<br>API声明：function getLevel(): ThermalLevel;<br>差异内容：function getLevel(): ThermalLevel;|api/@ohos.thermal.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace usb<br>差异内容：declare namespace usb|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function getDevices(): Array\<Readonly\<USBDevice>>;<br>差异内容：function getDevices(): Array\<Readonly\<USBDevice>>;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function connectDevice(device: USBDevice): Readonly\<USBDevicePipe>;<br>差异内容：function connectDevice(device: USBDevice): Readonly\<USBDevicePipe>;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function hasRight(deviceName: string): boolean;<br>差异内容：function hasRight(deviceName: string): boolean;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function requestRight(deviceName: string): Promise\<boolean>;<br>差异内容：function requestRight(deviceName: string): Promise\<boolean>;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number;<br>差异内容：function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>差异内容：function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function setConfiguration(pipe: USBDevicePipe, config: USBConfig): number;<br>差异内容：function setConfiguration(pipe: USBDevicePipe, config: USBConfig): number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function setInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>差异内容：function setInterface(pipe: USBDevicePipe, iface: USBInterface): number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function getRawDescriptor(pipe: USBDevicePipe): Uint8Array;<br>差异内容：function getRawDescriptor(pipe: USBDevicePipe): Uint8Array;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function getFileDescriptor(pipe: USBDevicePipe): number;<br>差异内容：function getFileDescriptor(pipe: USBDevicePipe): number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise\<number>;<br>差异内容：function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise\<number>;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function bulkTransfer(pipe: USBDevicePipe, endpoint: USBEndpoint, buffer: Uint8Array, timeout?: number): Promise\<number>;<br>差异内容：function bulkTransfer(pipe: USBDevicePipe, endpoint: USBEndpoint, buffer: Uint8Array, timeout?: number): Promise\<number>;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：function closePipe(pipe: USBDevicePipe): number;<br>差异内容：function closePipe(pipe: USBDevicePipe): number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：interface USBEndpoint<br>差异内容：interface USBEndpoint|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：address: number;<br>差异内容：address: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：attributes: number;<br>差异内容：attributes: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：interval: number;<br>差异内容：interval: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：maxPacketSize: number;<br>差异内容：maxPacketSize: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：direction: USBRequestDirection;<br>差异内容：direction: USBRequestDirection;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：number: number;<br>差异内容：number: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：type: number;<br>差异内容：type: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：interfaceId: number;<br>差异内容：interfaceId: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：interface USBInterface<br>差异内容：interface USBInterface|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：id: number;<br>差异内容：id: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：protocol: number;<br>差异内容：protocol: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：clazz: number;<br>差异内容：clazz: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：subClass: number;<br>差异内容：subClass: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：alternateSetting: number;<br>差异内容：alternateSetting: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：endpoints: Array\<USBEndpoint>;<br>差异内容：endpoints: Array\<USBEndpoint>;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：interface USBConfig<br>差异内容：interface USBConfig|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBConfig；<br>API声明：id: number;<br>差异内容：id: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBConfig；<br>API声明：attributes: number;<br>差异内容：attributes: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBConfig；<br>API声明：maxPower: number;<br>差异内容：maxPower: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBConfig；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBConfig；<br>API声明：isRemoteWakeup: boolean;<br>差异内容：isRemoteWakeup: boolean;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBConfig；<br>API声明：isSelfPowered: boolean;<br>差异内容：isSelfPowered: boolean;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBConfig；<br>API声明：interfaces: Array\<USBInterface>;<br>差异内容：interfaces: Array\<USBInterface>;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：interface USBDevice<br>差异内容：interface USBDevice|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：busNum: number;<br>差异内容：busNum: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：devAddress: number;<br>差异内容：devAddress: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：serial: string;<br>差异内容：serial: string;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：manufacturerName: string;<br>差异内容：manufacturerName: string;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：productName: string;<br>差异内容：productName: string;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：version: string;<br>差异内容：version: string;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：vendorId: number;<br>差异内容：vendorId: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：productId: number;<br>差异内容：productId: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：clazz: number;<br>差异内容：clazz: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：subClass: number;<br>差异内容：subClass: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：protocol: number;<br>差异内容：protocol: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：configs: Array\<USBConfig>;<br>差异内容：configs: Array\<USBConfig>;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：interface USBDevicePipe<br>差异内容：interface USBDevicePipe|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevicePipe；<br>API声明：busNum: number;<br>差异内容：busNum: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBDevicePipe；<br>API声明：devAddress: number;<br>差异内容：devAddress: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：interface USBControlParams<br>差异内容：interface USBControlParams|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBControlParams；<br>API声明：request: number;<br>差异内容：request: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBControlParams；<br>API声明：target: USBRequestTargetType;<br>差异内容：target: USBRequestTargetType;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBControlParams；<br>API声明：reqType: USBControlRequestType;<br>差异内容：reqType: USBControlRequestType;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBControlParams；<br>API声明：value: number;<br>差异内容：value: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBControlParams；<br>API声明：index: number;<br>差异内容：index: number;|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBControlParams；<br>API声明：data: Uint8Array;<br>差异内容：data: Uint8Array;|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：export enum USBRequestTargetType<br>差异内容：export enum USBRequestTargetType|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBRequestTargetType；<br>API声明：USB_REQUEST_TARGET_DEVICE = 0<br>差异内容：USB_REQUEST_TARGET_DEVICE = 0|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBRequestTargetType；<br>API声明：USB_REQUEST_TARGET_INTERFACE = 1<br>差异内容：USB_REQUEST_TARGET_INTERFACE = 1|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBRequestTargetType；<br>API声明：USB_REQUEST_TARGET_ENDPOINT = 2<br>差异内容：USB_REQUEST_TARGET_ENDPOINT = 2|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBRequestTargetType；<br>API声明：USB_REQUEST_TARGET_OTHER = 3<br>差异内容：USB_REQUEST_TARGET_OTHER = 3|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：export enum USBControlRequestType<br>差异内容：export enum USBControlRequestType|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBControlRequestType；<br>API声明：USB_REQUEST_TYPE_STANDARD = 0<br>差异内容：USB_REQUEST_TYPE_STANDARD = 0|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBControlRequestType；<br>API声明：USB_REQUEST_TYPE_CLASS = 1<br>差异内容：USB_REQUEST_TYPE_CLASS = 1|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBControlRequestType；<br>API声明：USB_REQUEST_TYPE_VENDOR = 2<br>差异内容：USB_REQUEST_TYPE_VENDOR = 2|api/@ohos.usb.d.ts|
|新增API|NA|类名：usb；<br>API声明：export enum USBRequestDirection<br>差异内容：export enum USBRequestDirection|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBRequestDirection；<br>API声明：USB_REQUEST_DIR_TO_DEVICE = 0<br>差异内容：USB_REQUEST_DIR_TO_DEVICE = 0|api/@ohos.usb.d.ts|
|新增API|NA|类名：USBRequestDirection；<br>API声明：USB_REQUEST_DIR_FROM_DEVICE = 0x80<br>差异内容：USB_REQUEST_DIR_FROM_DEVICE = 0x80|api/@ohos.usb.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace usbManager<br>差异内容：declare namespace usbManager|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function getDevices(): Array\<Readonly\<USBDevice>>;<br>差异内容：function getDevices(): Array\<Readonly\<USBDevice>>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function connectDevice(device: USBDevice): Readonly\<USBDevicePipe>;<br>差异内容：function connectDevice(device: USBDevice): Readonly\<USBDevicePipe>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function hasRight(deviceName: string): boolean;<br>差异内容：function hasRight(deviceName: string): boolean;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function requestRight(deviceName: string): Promise\<boolean>;<br>差异内容：function requestRight(deviceName: string): Promise\<boolean>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function removeRight(deviceName: string): boolean;<br>差异内容：function removeRight(deviceName: string): boolean;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number;<br>差异内容：function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>差异内容：function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): number;<br>差异内容：function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function setInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>差异内容：function setInterface(pipe: USBDevicePipe, iface: USBInterface): number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function getRawDescriptor(pipe: USBDevicePipe): Uint8Array;<br>差异内容：function getRawDescriptor(pipe: USBDevicePipe): Uint8Array;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function getFileDescriptor(pipe: USBDevicePipe): number;<br>差异内容：function getFileDescriptor(pipe: USBDevicePipe): number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise\<number>;<br>差异内容：function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise\<number>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function bulkTransfer(pipe: USBDevicePipe, endpoint: USBEndpoint, buffer: Uint8Array, timeout?: number): Promise\<number>;<br>差异内容：function bulkTransfer(pipe: USBDevicePipe, endpoint: USBEndpoint, buffer: Uint8Array, timeout?: number): Promise\<number>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function closePipe(pipe: USBDevicePipe): number;<br>差异内容：function closePipe(pipe: USBDevicePipe): number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：interface USBEndpoint<br>差异内容：interface USBEndpoint|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：address: number;<br>差异内容：address: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：attributes: number;<br>差异内容：attributes: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：interval: number;<br>差异内容：interval: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：maxPacketSize: number;<br>差异内容：maxPacketSize: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：direction: USBRequestDirection;<br>差异内容：direction: USBRequestDirection;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：number: number;<br>差异内容：number: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：type: number;<br>差异内容：type: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBEndpoint；<br>API声明：interfaceId: number;<br>差异内容：interfaceId: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：interface USBInterface<br>差异内容：interface USBInterface|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：id: number;<br>差异内容：id: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：protocol: number;<br>差异内容：protocol: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：clazz: number;<br>差异内容：clazz: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：subClass: number;<br>差异内容：subClass: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：alternateSetting: number;<br>差异内容：alternateSetting: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBInterface；<br>API声明：endpoints: Array\<USBEndpoint>;<br>差异内容：endpoints: Array\<USBEndpoint>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：interface USBConfiguration<br>差异内容：interface USBConfiguration|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBConfiguration；<br>API声明：id: number;<br>差异内容：id: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBConfiguration；<br>API声明：attributes: number;<br>差异内容：attributes: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBConfiguration；<br>API声明：maxPower: number;<br>差异内容：maxPower: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBConfiguration；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBConfiguration；<br>API声明：isRemoteWakeup: boolean;<br>差异内容：isRemoteWakeup: boolean;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBConfiguration；<br>API声明：isSelfPowered: boolean;<br>差异内容：isSelfPowered: boolean;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBConfiguration；<br>API声明：interfaces: Array\<USBInterface>;<br>差异内容：interfaces: Array\<USBInterface>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：interface USBDevice<br>差异内容：interface USBDevice|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：busNum: number;<br>差异内容：busNum: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：devAddress: number;<br>差异内容：devAddress: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：serial: string;<br>差异内容：serial: string;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：manufacturerName: string;<br>差异内容：manufacturerName: string;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：productName: string;<br>差异内容：productName: string;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：version: string;<br>差异内容：version: string;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：vendorId: number;<br>差异内容：vendorId: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：productId: number;<br>差异内容：productId: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：clazz: number;<br>差异内容：clazz: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：subClass: number;<br>差异内容：subClass: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：protocol: number;<br>差异内容：protocol: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：configs: Array\<USBConfiguration>;<br>差异内容：configs: Array\<USBConfiguration>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：interface USBDevicePipe<br>差异内容：interface USBDevicePipe|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevicePipe；<br>API声明：busNum: number;<br>差异内容：busNum: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDevicePipe；<br>API声明：devAddress: number;<br>差异内容：devAddress: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：interface USBControlParams<br>差异内容：interface USBControlParams|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBControlParams；<br>API声明：request: number;<br>差异内容：request: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBControlParams；<br>API声明：target: USBRequestTargetType;<br>差异内容：target: USBRequestTargetType;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBControlParams；<br>API声明：reqType: USBControlRequestType;<br>差异内容：reqType: USBControlRequestType;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBControlParams；<br>API声明：value: number;<br>差异内容：value: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBControlParams；<br>API声明：index: number;<br>差异内容：index: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBControlParams；<br>API声明：data: Uint8Array;<br>差异内容：data: Uint8Array;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：export enum USBRequestTargetType<br>差异内容：export enum USBRequestTargetType|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBRequestTargetType；<br>API声明：USB_REQUEST_TARGET_DEVICE = 0<br>差异内容：USB_REQUEST_TARGET_DEVICE = 0|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBRequestTargetType；<br>API声明：USB_REQUEST_TARGET_INTERFACE = 1<br>差异内容：USB_REQUEST_TARGET_INTERFACE = 1|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBRequestTargetType；<br>API声明：USB_REQUEST_TARGET_ENDPOINT = 2<br>差异内容：USB_REQUEST_TARGET_ENDPOINT = 2|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBRequestTargetType；<br>API声明：USB_REQUEST_TARGET_OTHER = 3<br>差异内容：USB_REQUEST_TARGET_OTHER = 3|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：export enum USBControlRequestType<br>差异内容：export enum USBControlRequestType|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBControlRequestType；<br>API声明：USB_REQUEST_TYPE_STANDARD = 0<br>差异内容：USB_REQUEST_TYPE_STANDARD = 0|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBControlRequestType；<br>API声明：USB_REQUEST_TYPE_CLASS = 1<br>差异内容：USB_REQUEST_TYPE_CLASS = 1|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBControlRequestType；<br>API声明：USB_REQUEST_TYPE_VENDOR = 2<br>差异内容：USB_REQUEST_TYPE_VENDOR = 2|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：export enum USBRequestDirection<br>差异内容：export enum USBRequestDirection|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBRequestDirection；<br>API声明：USB_REQUEST_DIR_TO_DEVICE = 0<br>差异内容：USB_REQUEST_DIR_TO_DEVICE = 0|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBRequestDirection；<br>API声明：USB_REQUEST_DIR_FROM_DEVICE = 0x80<br>差异内容：USB_REQUEST_DIR_FROM_DEVICE = 0x80|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace wallpaper<br>差异内容：declare namespace wallpaper|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：interface RgbaColor<br>差异内容：interface RgbaColor|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：RgbaColor；<br>API声明：red: number;<br>差异内容：red: number;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：RgbaColor；<br>API声明：green: number;<br>差异内容：green: number;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：RgbaColor；<br>API声明：blue: number;<br>差异内容：blue: number;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：RgbaColor；<br>API声明：alpha: number;<br>差异内容：alpha: number;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：enum WallpaperType<br>差异内容：enum WallpaperType|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：WallpaperType；<br>API声明：WALLPAPER_SYSTEM<br>差异内容：WALLPAPER_SYSTEM|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：WallpaperType；<br>API声明：WALLPAPER_LOCKSCREEN<br>差异内容：WALLPAPER_LOCKSCREEN|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function getColors(wallpaperType: WallpaperType, callback: AsyncCallback\<Array\<RgbaColor>>): void;<br>差异内容：function getColors(wallpaperType: WallpaperType, callback: AsyncCallback\<Array\<RgbaColor>>): void;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function getColors(wallpaperType: WallpaperType): Promise\<Array\<RgbaColor>>;<br>差异内容：function getColors(wallpaperType: WallpaperType): Promise\<Array\<RgbaColor>>;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function getId(wallpaperType: WallpaperType, callback: AsyncCallback\<number>): void;<br>差异内容：function getId(wallpaperType: WallpaperType, callback: AsyncCallback\<number>): void;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function getId(wallpaperType: WallpaperType): Promise\<number>;<br>差异内容：function getId(wallpaperType: WallpaperType): Promise\<number>;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function getFile(wallpaperType: WallpaperType, callback: AsyncCallback\<number>): void;<br>差异内容：function getFile(wallpaperType: WallpaperType, callback: AsyncCallback\<number>): void;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function getFile(wallpaperType: WallpaperType): Promise\<number>;<br>差异内容：function getFile(wallpaperType: WallpaperType): Promise\<number>;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function getMinHeight(callback: AsyncCallback\<number>): void;<br>差异内容：function getMinHeight(callback: AsyncCallback\<number>): void;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function getMinHeight(): Promise\<number>;<br>差异内容：function getMinHeight(): Promise\<number>;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function getMinWidth(callback: AsyncCallback\<number>): void;<br>差异内容：function getMinWidth(callback: AsyncCallback\<number>): void;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function getMinWidth(): Promise\<number>;<br>差异内容：function getMinWidth(): Promise\<number>;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function isChangePermitted(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isChangePermitted(callback: AsyncCallback\<boolean>): void;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function isChangePermitted(): Promise\<boolean>;<br>差异内容：function isChangePermitted(): Promise\<boolean>;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function isOperationAllowed(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isOperationAllowed(callback: AsyncCallback\<boolean>): void;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function isOperationAllowed(): Promise\<boolean>;<br>差异内容：function isOperationAllowed(): Promise\<boolean>;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function reset(wallpaperType: WallpaperType, callback: AsyncCallback\<void>): void;<br>差异内容：function reset(wallpaperType: WallpaperType, callback: AsyncCallback\<void>): void;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function reset(wallpaperType: WallpaperType): Promise\<void>;<br>差异内容：function reset(wallpaperType: WallpaperType): Promise\<void>;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function setWallpaper(source: string \| image.PixelMap, wallpaperType: WallpaperType, callback: AsyncCallback\<void>): void;<br>差异内容：function setWallpaper(source: string \| image.PixelMap, wallpaperType: WallpaperType, callback: AsyncCallback\<void>): void;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function setWallpaper(source: string \| image.PixelMap, wallpaperType: WallpaperType): Promise\<void>;<br>差异内容：function setWallpaper(source: string \| image.PixelMap, wallpaperType: WallpaperType): Promise\<void>;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function on(type: 'colorChange', callback: (colors: Array\<RgbaColor>, wallpaperType: WallpaperType) => void): void;<br>差异内容：function on(type: 'colorChange', callback: (colors: Array\<RgbaColor>, wallpaperType: WallpaperType) => void): void;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：wallpaper；<br>API声明：function off(type: 'colorChange', callback?: (colors: Array\<RgbaColor>, wallpaperType: WallpaperType) => void): void;<br>差异内容：function off(type: 'colorChange', callback?: (colors: Array\<RgbaColor>, wallpaperType: WallpaperType) => void): void;|api/@ohos.wallpaper.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace zlib<br>差异内容：declare namespace zlib|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：export enum ErrorCode<br>差异内容：export enum ErrorCode|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：ERROR_CODE_OK = 0<br>差异内容：ERROR_CODE_OK = 0|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：ERROR_CODE_ERRNO = -1<br>差异内容：ERROR_CODE_ERRNO = -1|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：export enum CompressLevel<br>差异内容：export enum CompressLevel|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressLevel；<br>API声明：COMPRESS_LEVEL_NO_COMPRESSION = 0<br>差异内容：COMPRESS_LEVEL_NO_COMPRESSION = 0|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressLevel；<br>API声明：COMPRESS_LEVEL_BEST_SPEED = 1<br>差异内容：COMPRESS_LEVEL_BEST_SPEED = 1|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressLevel；<br>API声明：COMPRESS_LEVEL_BEST_COMPRESSION = 9<br>差异内容：COMPRESS_LEVEL_BEST_COMPRESSION = 9|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressLevel；<br>API声明：COMPRESS_LEVEL_DEFAULT_COMPRESSION = -1<br>差异内容：COMPRESS_LEVEL_DEFAULT_COMPRESSION = -1|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：export enum CompressStrategy<br>差异内容：export enum CompressStrategy|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressStrategy；<br>API声明：COMPRESS_STRATEGY_DEFAULT_STRATEGY = 0<br>差异内容：COMPRESS_STRATEGY_DEFAULT_STRATEGY = 0|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressStrategy；<br>API声明：COMPRESS_STRATEGY_FILTERED = 1<br>差异内容：COMPRESS_STRATEGY_FILTERED = 1|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressStrategy；<br>API声明：COMPRESS_STRATEGY_HUFFMAN_ONLY = 2<br>差异内容：COMPRESS_STRATEGY_HUFFMAN_ONLY = 2|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressStrategy；<br>API声明：COMPRESS_STRATEGY_RLE = 3<br>差异内容：COMPRESS_STRATEGY_RLE = 3|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressStrategy；<br>API声明：COMPRESS_STRATEGY_FIXED = 4<br>差异内容：COMPRESS_STRATEGY_FIXED = 4|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：export enum MemLevel<br>差异内容：export enum MemLevel|api/@ohos.zlib.d.ts|
|新增API|NA|类名：MemLevel；<br>API声明：MEM_LEVEL_MIN = 1<br>差异内容：MEM_LEVEL_MIN = 1|api/@ohos.zlib.d.ts|
|新增API|NA|类名：MemLevel；<br>API声明：MEM_LEVEL_MAX = 9<br>差异内容：MEM_LEVEL_MAX = 9|api/@ohos.zlib.d.ts|
|新增API|NA|类名：MemLevel；<br>API声明：MEM_LEVEL_DEFAULT = 8<br>差异内容：MEM_LEVEL_DEFAULT = 8|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：interface Options<br>差异内容：interface Options|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Options；<br>API声明：level?: CompressLevel;<br>差异内容：level?: CompressLevel;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Options；<br>API声明：memLevel?: MemLevel;<br>差异内容：memLevel?: MemLevel;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Options；<br>API声明：strategy?: CompressStrategy;<br>差异内容：strategy?: CompressStrategy;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function zipFile(inFile: string, outFile: string, options: Options): Promise\<void>;<br>差异内容：function zipFile(inFile: string, outFile: string, options: Options): Promise\<void>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function unzipFile(inFile: string, outFile: string, options: Options): Promise\<void>;<br>差异内容：function unzipFile(inFile: string, outFile: string, options: Options): Promise\<void>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function compressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback\<void>): void;<br>差异内容：function compressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback\<void>): void;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function compressFile(inFile: string, outFile: string, options: Options): Promise\<void>;<br>差异内容：function compressFile(inFile: string, outFile: string, options: Options): Promise\<void>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function decompressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback\<void>): void;<br>差异内容：function decompressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback\<void>): void;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function decompressFile(inFile: string, outFile: string, callback: AsyncCallback\<void>): void;<br>差异内容：function decompressFile(inFile: string, outFile: string, callback: AsyncCallback\<void>): void;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function decompressFile(inFile: string, outFile: string, options?: Options): Promise\<void>;<br>差异内容：function decompressFile(inFile: string, outFile: string, options?: Options): Promise\<void>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface BatteryResponse<br>差异内容：export interface BatteryResponse|api/@system.battery.d.ts|
|新增API|NA|类名：BatteryResponse；<br>API声明：charging: boolean;<br>差异内容：charging: boolean;|api/@system.battery.d.ts|
|新增API|NA|类名：BatteryResponse；<br>API声明：level: number;<br>差异内容：level: number;|api/@system.battery.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface GetStatusOptions<br>差异内容：export interface GetStatusOptions|api/@system.battery.d.ts|
|新增API|NA|类名：GetStatusOptions；<br>API声明：success?: (data: BatteryResponse) => void;<br>差异内容：success?: (data: BatteryResponse) => void;|api/@system.battery.d.ts|
|新增API|NA|类名：GetStatusOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.battery.d.ts|
|新增API|NA|类名：GetStatusOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.battery.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Battery<br>差异内容：export default class Battery|api/@system.battery.d.ts|
|新增API|NA|类名：Battery；<br>API声明：static getStatus(options?: GetStatusOptions): void;<br>差异内容：static getStatus(options?: GetStatusOptions): void;|api/@system.battery.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface BrightnessResponse<br>差异内容：export interface BrightnessResponse|api/@system.brightness.d.ts|
|新增API|NA|类名：BrightnessResponse；<br>API声明：value: number;<br>差异内容：value: number;|api/@system.brightness.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface GetBrightnessOptions<br>差异内容：export interface GetBrightnessOptions|api/@system.brightness.d.ts|
|新增API|NA|类名：GetBrightnessOptions；<br>API声明：success?: (data: BrightnessResponse) => void;<br>差异内容：success?: (data: BrightnessResponse) => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：GetBrightnessOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：GetBrightnessOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SetBrightnessOptions<br>差异内容：export interface SetBrightnessOptions|api/@system.brightness.d.ts|
|新增API|NA|类名：SetBrightnessOptions；<br>API声明：value: number;<br>差异内容：value: number;|api/@system.brightness.d.ts|
|新增API|NA|类名：SetBrightnessOptions；<br>API声明：success?: () => void;<br>差异内容：success?: () => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：SetBrightnessOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：SetBrightnessOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface BrightnessModeResponse<br>差异内容：export interface BrightnessModeResponse|api/@system.brightness.d.ts|
|新增API|NA|类名：BrightnessModeResponse；<br>API声明：mode: number;<br>差异内容：mode: number;|api/@system.brightness.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface GetBrightnessModeOptions<br>差异内容：export interface GetBrightnessModeOptions|api/@system.brightness.d.ts|
|新增API|NA|类名：GetBrightnessModeOptions；<br>API声明：success?: (data: BrightnessModeResponse) => void;<br>差异内容：success?: (data: BrightnessModeResponse) => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：GetBrightnessModeOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：GetBrightnessModeOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SetBrightnessModeOptions<br>差异内容：export interface SetBrightnessModeOptions|api/@system.brightness.d.ts|
|新增API|NA|类名：SetBrightnessModeOptions；<br>API声明：mode: number;<br>差异内容：mode: number;|api/@system.brightness.d.ts|
|新增API|NA|类名：SetBrightnessModeOptions；<br>API声明：success?: () => void;<br>差异内容：success?: () => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：SetBrightnessModeOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：SetBrightnessModeOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SetKeepScreenOnOptions<br>差异内容：export interface SetKeepScreenOnOptions|api/@system.brightness.d.ts|
|新增API|NA|类名：SetKeepScreenOnOptions；<br>API声明：keepScreenOn: boolean;<br>差异内容：keepScreenOn: boolean;|api/@system.brightness.d.ts|
|新增API|NA|类名：SetKeepScreenOnOptions；<br>API声明：success?: () => void;<br>差异内容：success?: () => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：SetKeepScreenOnOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：SetKeepScreenOnOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.brightness.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Brightness<br>差异内容：export default class Brightness|api/@system.brightness.d.ts|
|新增API|NA|类名：Brightness；<br>API声明：static getValue(options?: GetBrightnessOptions): void;<br>差异内容：static getValue(options?: GetBrightnessOptions): void;|api/@system.brightness.d.ts|
|新增API|NA|类名：Brightness；<br>API声明：static setValue(options?: SetBrightnessOptions): void;<br>差异内容：static setValue(options?: SetBrightnessOptions): void;|api/@system.brightness.d.ts|
|新增API|NA|类名：Brightness；<br>API声明：static getMode(options?: GetBrightnessModeOptions): void;<br>差异内容：static getMode(options?: GetBrightnessModeOptions): void;|api/@system.brightness.d.ts|
|新增API|NA|类名：Brightness；<br>API声明：static setMode(options?: SetBrightnessModeOptions): void;<br>差异内容：static setMode(options?: SetBrightnessModeOptions): void;|api/@system.brightness.d.ts|
|新增API|NA|类名：Brightness；<br>API声明：static setKeepScreenOn(options?: SetKeepScreenOnOptions): void;<br>差异内容：static setKeepScreenOn(options?: SetKeepScreenOnOptions): void;|api/@system.brightness.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface DeviceResponse<br>差异内容：export interface DeviceResponse|api/@system.device.d.ts|
|新增API|NA|类名：DeviceResponse；<br>API声明：brand: string;<br>差异内容：brand: string;|api/@system.device.d.ts|
|新增API|NA|类名：DeviceResponse；<br>API声明：manufacturer: string;<br>差异内容：manufacturer: string;|api/@system.device.d.ts|
|新增API|NA|类名：DeviceResponse；<br>API声明：model: string;<br>差异内容：model: string;|api/@system.device.d.ts|
|新增API|NA|类名：DeviceResponse；<br>API声明：product: string;<br>差异内容：product: string;|api/@system.device.d.ts|
|新增API|NA|类名：DeviceResponse；<br>API声明：language: string;<br>差异内容：language: string;|api/@system.device.d.ts|
|新增API|NA|类名：DeviceResponse；<br>API声明：region: string;<br>差异内容：region: string;|api/@system.device.d.ts|
|新增API|NA|类名：DeviceResponse；<br>API声明：windowWidth: number;<br>差异内容：windowWidth: number;|api/@system.device.d.ts|
|新增API|NA|类名：DeviceResponse；<br>API声明：windowHeight: number;<br>差异内容：windowHeight: number;|api/@system.device.d.ts|
|新增API|NA|类名：DeviceResponse；<br>API声明：screenDensity: number;<br>差异内容：screenDensity: number;|api/@system.device.d.ts|
|新增API|NA|类名：DeviceResponse；<br>API声明：screenShape: 'rect' \| 'circle';<br>差异内容：screenShape: 'rect' \| 'circle';|api/@system.device.d.ts|
|新增API|NA|类名：DeviceResponse；<br>API声明：apiVersion: number;<br>差异内容：apiVersion: number;|api/@system.device.d.ts|
|新增API|NA|类名：DeviceResponse；<br>API声明：deviceType: string;<br>差异内容：deviceType: string;|api/@system.device.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface GetDeviceOptions<br>差异内容：export interface GetDeviceOptions|api/@system.device.d.ts|
|新增API|NA|类名：GetDeviceOptions；<br>API声明：success?: (data: DeviceResponse) => void;<br>差异内容：success?: (data: DeviceResponse) => void;|api/@system.device.d.ts|
|新增API|NA|类名：GetDeviceOptions；<br>API声明：fail?: (data: any, code: number) => void;<br>差异内容：fail?: (data: any, code: number) => void;|api/@system.device.d.ts|
|新增API|NA|类名：GetDeviceOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.device.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Device<br>差异内容：export default class Device|api/@system.device.d.ts|
|新增API|NA|类名：Device；<br>API声明：static getInfo(options?: GetDeviceOptions): void;<br>差异内容：static getInfo(options?: GetDeviceOptions): void;|api/@system.device.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface UploadResponse<br>差异内容：export interface UploadResponse|api/@system.request.d.ts|
|新增API|NA|类名：UploadResponse；<br>API声明：code: number;<br>差异内容：code: number;|api/@system.request.d.ts|
|新增API|NA|类名：UploadResponse；<br>API声明：data: string;<br>差异内容：data: string;|api/@system.request.d.ts|
|新增API|NA|类名：UploadResponse；<br>API声明：headers: Object;<br>差异内容：headers: Object;|api/@system.request.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface DownloadResponse<br>差异内容：export interface DownloadResponse|api/@system.request.d.ts|
|新增API|NA|类名：DownloadResponse；<br>API声明：token: string;<br>差异内容：token: string;|api/@system.request.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface OnDownloadCompleteResponse<br>差异内容：export interface OnDownloadCompleteResponse|api/@system.request.d.ts|
|新增API|NA|类名：OnDownloadCompleteResponse；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.request.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface RequestFile<br>差异内容：export interface RequestFile|api/@system.request.d.ts|
|新增API|NA|类名：RequestFile；<br>API声明：filename?: string;<br>差异内容：filename?: string;|api/@system.request.d.ts|
|新增API|NA|类名：RequestFile；<br>API声明：name?: string;<br>差异内容：name?: string;|api/@system.request.d.ts|
|新增API|NA|类名：RequestFile；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.request.d.ts|
|新增API|NA|类名：RequestFile；<br>API声明：type?: string;<br>差异内容：type?: string;|api/@system.request.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface RequestData<br>差异内容：export interface RequestData|api/@system.request.d.ts|
|新增API|NA|类名：RequestData；<br>API声明：name: string;<br>差异内容：name: string;|api/@system.request.d.ts|
|新增API|NA|类名：RequestData；<br>API声明：value: string;<br>差异内容：value: string;|api/@system.request.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface UploadRequestOptions<br>差异内容：export interface UploadRequestOptions|api/@system.request.d.ts|
|新增API|NA|类名：UploadRequestOptions；<br>API声明：url: string;<br>差异内容：url: string;|api/@system.request.d.ts|
|新增API|NA|类名：UploadRequestOptions；<br>API声明：data?: Array\<RequestData>;<br>差异内容：data?: Array\<RequestData>;|api/@system.request.d.ts|
|新增API|NA|类名：UploadRequestOptions；<br>API声明：files: Array\<RequestFile>;<br>差异内容：files: Array\<RequestFile>;|api/@system.request.d.ts|
|新增API|NA|类名：UploadRequestOptions；<br>API声明：header?: Object;<br>差异内容：header?: Object;|api/@system.request.d.ts|
|新增API|NA|类名：UploadRequestOptions；<br>API声明：method?: string;<br>差异内容：method?: string;|api/@system.request.d.ts|
|新增API|NA|类名：UploadRequestOptions；<br>API声明：success?: (data: UploadResponse) => void;<br>差异内容：success?: (data: UploadResponse) => void;|api/@system.request.d.ts|
|新增API|NA|类名：UploadRequestOptions；<br>API声明：fail?: (data: any, code: number) => void;<br>差异内容：fail?: (data: any, code: number) => void;|api/@system.request.d.ts|
|新增API|NA|类名：UploadRequestOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.request.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface DownloadRequestOptions<br>差异内容：export interface DownloadRequestOptions|api/@system.request.d.ts|
|新增API|NA|类名：DownloadRequestOptions；<br>API声明：url: string;<br>差异内容：url: string;|api/@system.request.d.ts|
|新增API|NA|类名：DownloadRequestOptions；<br>API声明：filename?: string;<br>差异内容：filename?: string;|api/@system.request.d.ts|
|新增API|NA|类名：DownloadRequestOptions；<br>API声明：header?: string;<br>差异内容：header?: string;|api/@system.request.d.ts|
|新增API|NA|类名：DownloadRequestOptions；<br>API声明：description?: string;<br>差异内容：description?: string;|api/@system.request.d.ts|
|新增API|NA|类名：DownloadRequestOptions；<br>API声明：success?: (data: DownloadResponse) => void;<br>差异内容：success?: (data: DownloadResponse) => void;|api/@system.request.d.ts|
|新增API|NA|类名：DownloadRequestOptions；<br>API声明：fail?: (data: any, code: number) => void;<br>差异内容：fail?: (data: any, code: number) => void;|api/@system.request.d.ts|
|新增API|NA|类名：DownloadRequestOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.request.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface OnDownloadCompleteOptions<br>差异内容：export interface OnDownloadCompleteOptions|api/@system.request.d.ts|
|新增API|NA|类名：OnDownloadCompleteOptions；<br>API声明：token: string;<br>差异内容：token: string;|api/@system.request.d.ts|
|新增API|NA|类名：OnDownloadCompleteOptions；<br>API声明：success?: (data: OnDownloadCompleteResponse) => void;<br>差异内容：success?: (data: OnDownloadCompleteResponse) => void;|api/@system.request.d.ts|
|新增API|NA|类名：OnDownloadCompleteOptions；<br>API声明：fail?: (data: any, code: number) => void;<br>差异内容：fail?: (data: any, code: number) => void;|api/@system.request.d.ts|
|新增API|NA|类名：OnDownloadCompleteOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.request.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Request<br>差异内容：export default class Request|api/@system.request.d.ts|
|新增API|NA|类名：Request；<br>API声明：static upload(options: UploadRequestOptions): void;<br>差异内容：static upload(options: UploadRequestOptions): void;|api/@system.request.d.ts|
|新增API|NA|类名：Request；<br>API声明：static download(options: DownloadRequestOptions): void;<br>差异内容：static download(options: DownloadRequestOptions): void;|api/@system.request.d.ts|
|新增API|NA|类名：Request；<br>API声明：static onDownloadComplete(options: OnDownloadCompleteOptions): void;<br>差异内容：static onDownloadComplete(options: OnDownloadCompleteOptions): void;|api/@system.request.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.account.appAccount.d.ts<br>差异内容：BasicServicesKit|api/@ohos.account.appAccount.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.account.distributedAccount.d.ts<br>差异内容：BasicServicesKit|api/@ohos.account.distributedAccount.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.account.osAccount.d.ts<br>差异内容：BasicServicesKit|api/@ohos.account.osAccount.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.base.d.ts<br>差异内容：BasicServicesKit|api/@ohos.base.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.batteryInfo.d.ts<br>差异内容：BasicServicesKit|api/@ohos.batteryInfo.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.commonEventManager.d.ts<br>差异内容：BasicServicesKit|api/@ohos.commonEventManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.deviceAttest.d.ts<br>差异内容：BasicServicesKit|api/@ohos.deviceAttest.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.deviceInfo.d.ts<br>差异内容：BasicServicesKit|api/@ohos.deviceInfo.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.events.emitter.d.ts<br>差异内容：BasicServicesKit|api/@ohos.events.emitter.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.pasteboard.d.ts<br>差异内容：BasicServicesKit|api/@ohos.pasteboard.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.power.d.ts<br>差异内容：BasicServicesKit|api/@ohos.power.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.print.d.ts<br>差异内容：BasicServicesKit|api/@ohos.print.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.request.d.ts<br>差异内容：BasicServicesKit|api/@ohos.request.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.runningLock.d.ts<br>差异内容：BasicServicesKit|api/@ohos.runningLock.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.screenLock.d.ts<br>差异内容：BasicServicesKit|api/@ohos.screenLock.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.settings.d.ts<br>差异内容：BasicServicesKit|api/@ohos.settings.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.systemDateTime.d.ts<br>差异内容：BasicServicesKit|api/@ohos.systemDateTime.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.systemTime.d.ts<br>差异内容：BasicServicesKit|api/@ohos.systemTime.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.thermal.d.ts<br>差异内容：BasicServicesKit|api/@ohos.thermal.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.usb.d.ts<br>差异内容：BasicServicesKit|api/@ohos.usb.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.usbManager.d.ts<br>差异内容：BasicServicesKit|api/@ohos.usbManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.wallpaper.d.ts<br>差异内容：BasicServicesKit|api/@ohos.wallpaper.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.zlib.d.ts<br>差异内容：BasicServicesKit|api/@ohos.zlib.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.battery.d.ts<br>差异内容：BasicServicesKit|api/@system.battery.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.brightness.d.ts<br>差异内容：BasicServicesKit|api/@system.brightness.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.device.d.ts<br>差异内容：BasicServicesKit|api/@system.device.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.request.d.ts<br>差异内容：BasicServicesKit|api/@system.request.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.BasicServicesKit.d.ts<br>差异内容：BasicServicesKit|kits/@kit.BasicServicesKit.d.ts|
