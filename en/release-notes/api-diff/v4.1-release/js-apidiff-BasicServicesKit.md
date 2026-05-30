| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace appAccount<br>Differences: declare namespace appAccount|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: function createAppAccountManager(): AppAccountManager;<br>Differences: function createAppAccountManager(): AppAccountManager;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface AppAccountManager<br>Differences: interface AppAccountManager|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: addAccount(name: string, callback: AsyncCallback\<void>): void;<br>Differences: addAccount(name: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: addAccount(name: string, extraInfo: string, callback: AsyncCallback\<void>): void;<br>Differences: addAccount(name: string, extraInfo: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: addAccount(name: string, extraInfo?: string): Promise\<void>;<br>Differences: addAccount(name: string, extraInfo?: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: createAccount(name: string, callback: AsyncCallback\<void>): void;<br>Differences: createAccount(name: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: createAccount(name: string, options: CreateAccountOptions, callback: AsyncCallback\<void>): void;<br>Differences: createAccount(name: string, options: CreateAccountOptions, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: createAccount(name: string, options?: CreateAccountOptions): Promise\<void>;<br>Differences: createAccount(name: string, options?: CreateAccountOptions): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: addAccountImplicitly(owner: string, authType: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;<br>Differences: addAccountImplicitly(owner: string, authType: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: createAccountImplicitly(owner: string, callback: AuthCallback): void;<br>Differences: createAccountImplicitly(owner: string, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: createAccountImplicitly(owner: string, options: CreateAccountImplicitlyOptions, callback: AuthCallback): void;<br>Differences: createAccountImplicitly(owner: string, options: CreateAccountImplicitlyOptions, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: deleteAccount(name: string, callback: AsyncCallback\<void>): void;<br>Differences: deleteAccount(name: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: deleteAccount(name: string): Promise\<void>;<br>Differences: deleteAccount(name: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: removeAccount(name: string, callback: AsyncCallback\<void>): void;<br>Differences: removeAccount(name: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: removeAccount(name: string): Promise\<void>;<br>Differences: removeAccount(name: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: disableAppAccess(name: string, bundleName: string, callback: AsyncCallback\<void>): void;<br>Differences: disableAppAccess(name: string, bundleName: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: disableAppAccess(name: string, bundleName: string): Promise\<void>;<br>Differences: disableAppAccess(name: string, bundleName: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: enableAppAccess(name: string, bundleName: string, callback: AsyncCallback\<void>): void;<br>Differences: enableAppAccess(name: string, bundleName: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: enableAppAccess(name: string, bundleName: string): Promise\<void>;<br>Differences: enableAppAccess(name: string, bundleName: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback\<void>): void;<br>Differences: setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAppAccess(name: string, bundleName: string, isAccessible: boolean): Promise\<void>;<br>Differences: setAppAccess(name: string, bundleName: string, isAccessible: boolean): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: checkAppAccess(name: string, bundleName: string, callback: AsyncCallback\<boolean>): void;<br>Differences: checkAppAccess(name: string, bundleName: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: checkAppAccess(name: string, bundleName: string): Promise\<boolean>;<br>Differences: checkAppAccess(name: string, bundleName: string): Promise\<boolean>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: checkAppAccountSyncEnable(name: string, callback: AsyncCallback\<boolean>): void;<br>Differences: checkAppAccountSyncEnable(name: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: checkAppAccountSyncEnable(name: string): Promise\<boolean>;<br>Differences: checkAppAccountSyncEnable(name: string): Promise\<boolean>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: checkDataSyncEnabled(name: string, callback: AsyncCallback\<boolean>): void;<br>Differences: checkDataSyncEnabled(name: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: checkDataSyncEnabled(name: string): Promise\<boolean>;<br>Differences: checkDataSyncEnabled(name: string): Promise\<boolean>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAccountCredential(name: string, credentialType: string, credential: string, callback: AsyncCallback\<void>): void;<br>Differences: setAccountCredential(name: string, credentialType: string, credential: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAccountCredential(name: string, credentialType: string, credential: string): Promise\<void>;<br>Differences: setAccountCredential(name: string, credentialType: string, credential: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setCredential(name: string, credentialType: string, credential: string, callback: AsyncCallback\<void>): void;<br>Differences: setCredential(name: string, credentialType: string, credential: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setCredential(name: string, credentialType: string, credential: string): Promise\<void>;<br>Differences: setCredential(name: string, credentialType: string, credential: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAccountExtraInfo(name: string, extraInfo: string, callback: AsyncCallback\<void>): void;<br>Differences: setAccountExtraInfo(name: string, extraInfo: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAccountExtraInfo(name: string, extraInfo: string): Promise\<void>;<br>Differences: setAccountExtraInfo(name: string, extraInfo: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAppAccountSyncEnable(name: string, isEnable: boolean, callback: AsyncCallback\<void>): void;<br>Differences: setAppAccountSyncEnable(name: string, isEnable: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAppAccountSyncEnable(name: string, isEnable: boolean): Promise\<void>;<br>Differences: setAppAccountSyncEnable(name: string, isEnable: boolean): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setDataSyncEnabled(name: string, isEnabled: boolean, callback: AsyncCallback\<void>): void;<br>Differences: setDataSyncEnabled(name: string, isEnabled: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setDataSyncEnabled(name: string, isEnabled: boolean): Promise\<void>;<br>Differences: setDataSyncEnabled(name: string, isEnabled: boolean): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAssociatedData(name: string, key: string, value: string, callback: AsyncCallback\<void>): void;<br>Differences: setAssociatedData(name: string, key: string, value: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAssociatedData(name: string, key: string, value: string): Promise\<void>;<br>Differences: setAssociatedData(name: string, key: string, value: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setCustomData(name: string, key: string, value: string, callback: AsyncCallback\<void>): void;<br>Differences: setCustomData(name: string, key: string, value: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setCustomData(name: string, key: string, value: string): Promise\<void>;<br>Differences: setCustomData(name: string, key: string, value: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAllAccessibleAccounts(callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>Differences: getAllAccessibleAccounts(callback: AsyncCallback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAllAccessibleAccounts(): Promise\<Array\<AppAccountInfo>>;<br>Differences: getAllAccessibleAccounts(): Promise\<Array\<AppAccountInfo>>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAllAccounts(callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>Differences: getAllAccounts(callback: AsyncCallback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAllAccounts(): Promise\<Array\<AppAccountInfo>>;<br>Differences: getAllAccounts(): Promise\<Array\<AppAccountInfo>>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAllAccounts(owner: string, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>Differences: getAllAccounts(owner: string, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAllAccounts(owner: string): Promise\<Array\<AppAccountInfo>>;<br>Differences: getAllAccounts(owner: string): Promise\<Array\<AppAccountInfo>>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAccountsByOwner(owner: string, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>Differences: getAccountsByOwner(owner: string, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAccountsByOwner(owner: string): Promise\<Array\<AppAccountInfo>>;<br>Differences: getAccountsByOwner(owner: string): Promise\<Array\<AppAccountInfo>>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAccountCredential(name: string, credentialType: string, callback: AsyncCallback\<string>): void;<br>Differences: getAccountCredential(name: string, credentialType: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAccountCredential(name: string, credentialType: string): Promise\<string>;<br>Differences: getAccountCredential(name: string, credentialType: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getCredential(name: string, credentialType: string, callback: AsyncCallback\<string>): void;<br>Differences: getCredential(name: string, credentialType: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getCredential(name: string, credentialType: string): Promise\<string>;<br>Differences: getCredential(name: string, credentialType: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAccountExtraInfo(name: string, callback: AsyncCallback\<string>): void;<br>Differences: getAccountExtraInfo(name: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAccountExtraInfo(name: string): Promise\<string>;<br>Differences: getAccountExtraInfo(name: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAssociatedData(name: string, key: string, callback: AsyncCallback\<string>): void;<br>Differences: getAssociatedData(name: string, key: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAssociatedData(name: string, key: string): Promise\<string>;<br>Differences: getAssociatedData(name: string, key: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getCustomData(name: string, key: string, callback: AsyncCallback\<string>): void;<br>Differences: getCustomData(name: string, key: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getCustomData(name: string, key: string): Promise\<string>;<br>Differences: getCustomData(name: string, key: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getCustomDataSync(name: string, key: string): string;<br>Differences: getCustomDataSync(name: string, key: string): string;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: on(type: 'change', owners: Array\<string>, callback: Callback\<Array\<AppAccountInfo>>): void;<br>Differences: on(type: 'change', owners: Array\<string>, callback: Callback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: on(type: 'accountChange', owners: Array\<string>, callback: Callback\<Array\<AppAccountInfo>>): void;<br>Differences: on(type: 'accountChange', owners: Array\<string>, callback: Callback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: off(type: 'change', callback?: Callback\<Array\<AppAccountInfo>>): void;<br>Differences: off(type: 'change', callback?: Callback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: off(type: 'accountChange', callback?: Callback\<Array\<AppAccountInfo>>): void;<br>Differences: off(type: 'accountChange', callback?: Callback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: authenticate(name: string, owner: string, authType: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;<br>Differences: authenticate(name: string, owner: string, authType: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: auth(name: string, owner: string, authType: string, callback: AuthCallback): void;<br>Differences: auth(name: string, owner: string, authType: string, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: auth(name: string, owner: string, authType: string, options: Record\<string, Object>, callback: AuthCallback): void;<br>Differences: auth(name: string, owner: string, authType: string, options: Record\<string, Object>, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getOAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback\<string>): void;<br>Differences: getOAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getOAuthToken(name: string, owner: string, authType: string): Promise\<string>;<br>Differences: getOAuthToken(name: string, owner: string, authType: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback\<string>): void;<br>Differences: getAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback\<string>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAuthToken(name: string, owner: string, authType: string): Promise\<string>;<br>Differences: getAuthToken(name: string, owner: string, authType: string): Promise\<string>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setOAuthToken(name: string, authType: string, token: string, callback: AsyncCallback\<void>): void;<br>Differences: setOAuthToken(name: string, authType: string, token: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setOAuthToken(name: string, authType: string, token: string): Promise\<void>;<br>Differences: setOAuthToken(name: string, authType: string, token: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAuthToken(name: string, authType: string, token: string, callback: AsyncCallback\<void>): void;<br>Differences: setAuthToken(name: string, authType: string, token: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAuthToken(name: string, authType: string, token: string): Promise\<void>;<br>Differences: setAuthToken(name: string, authType: string, token: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: deleteOAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback\<void>): void;<br>Differences: deleteOAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: deleteOAuthToken(name: string, owner: string, authType: string, token: string): Promise\<void>;<br>Differences: deleteOAuthToken(name: string, owner: string, authType: string, token: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: deleteAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback\<void>): void;<br>Differences: deleteAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: deleteAuthToken(name: string, owner: string, authType: string, token: string): Promise\<void>;<br>Differences: deleteAuthToken(name: string, owner: string, authType: string, token: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setOAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback\<void>): void;<br>Differences: setOAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setOAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise\<void>;<br>Differences: setOAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback\<void>): void;<br>Differences: setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise\<void>;<br>Differences: setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: checkOAuthTokenVisibility(name: string, authType: string, bundleName: string, callback: AsyncCallback\<boolean>): void;<br>Differences: checkOAuthTokenVisibility(name: string, authType: string, bundleName: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: checkOAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise\<boolean>;<br>Differences: checkOAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise\<boolean>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: checkAuthTokenVisibility(name: string, authType: string, bundleName: string, callback: AsyncCallback\<boolean>): void;<br>Differences: checkAuthTokenVisibility(name: string, authType: string, bundleName: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: checkAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise\<boolean>;<br>Differences: checkAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise\<boolean>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAllOAuthTokens(name: string, owner: string, callback: AsyncCallback\<Array\<OAuthTokenInfo>>): void;<br>Differences: getAllOAuthTokens(name: string, owner: string, callback: AsyncCallback\<Array\<OAuthTokenInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAllOAuthTokens(name: string, owner: string): Promise\<Array\<OAuthTokenInfo>>;<br>Differences: getAllOAuthTokens(name: string, owner: string): Promise\<Array\<OAuthTokenInfo>>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAllAuthTokens(name: string, owner: string, callback: AsyncCallback\<Array\<AuthTokenInfo>>): void;<br>Differences: getAllAuthTokens(name: string, owner: string, callback: AsyncCallback\<Array\<AuthTokenInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAllAuthTokens(name: string, owner: string): Promise\<Array\<AuthTokenInfo>>;<br>Differences: getAllAuthTokens(name: string, owner: string): Promise\<Array\<AuthTokenInfo>>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getOAuthList(name: string, authType: string, callback: AsyncCallback\<Array\<string>>): void;<br>Differences: getOAuthList(name: string, authType: string, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getOAuthList(name: string, authType: string): Promise\<Array\<string>>;<br>Differences: getOAuthList(name: string, authType: string): Promise\<Array\<string>>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAuthList(name: string, authType: string, callback: AsyncCallback\<Array\<string>>): void;<br>Differences: getAuthList(name: string, authType: string, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAuthList(name: string, authType: string): Promise\<Array\<string>>;<br>Differences: getAuthList(name: string, authType: string): Promise\<Array\<string>>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAuthenticatorCallback(sessionId: string, callback: AsyncCallback\<AuthenticatorCallback>): void;<br>Differences: getAuthenticatorCallback(sessionId: string, callback: AsyncCallback\<AuthenticatorCallback>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAuthenticatorCallback(sessionId: string): Promise\<AuthenticatorCallback>;<br>Differences: getAuthenticatorCallback(sessionId: string): Promise\<AuthenticatorCallback>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAuthCallback(sessionId: string, callback: AsyncCallback\<AuthCallback>): void;<br>Differences: getAuthCallback(sessionId: string, callback: AsyncCallback\<AuthCallback>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAuthCallback(sessionId: string): Promise\<AuthCallback>;<br>Differences: getAuthCallback(sessionId: string): Promise\<AuthCallback>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAuthenticatorInfo(owner: string, callback: AsyncCallback\<AuthenticatorInfo>): void;<br>Differences: getAuthenticatorInfo(owner: string, callback: AsyncCallback\<AuthenticatorInfo>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: getAuthenticatorInfo(owner: string): Promise\<AuthenticatorInfo>;<br>Differences: getAuthenticatorInfo(owner: string): Promise\<AuthenticatorInfo>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: queryAuthenticatorInfo(owner: string, callback: AsyncCallback\<AuthenticatorInfo>): void;<br>Differences: queryAuthenticatorInfo(owner: string, callback: AsyncCallback\<AuthenticatorInfo>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: queryAuthenticatorInfo(owner: string): Promise\<AuthenticatorInfo>;<br>Differences: queryAuthenticatorInfo(owner: string): Promise\<AuthenticatorInfo>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: checkAccountLabels(name: string, owner: string, labels: Array\<string>, callback: AsyncCallback\<boolean>): void;<br>Differences: checkAccountLabels(name: string, owner: string, labels: Array\<string>, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: checkAccountLabels(name: string, owner: string, labels: Array\<string>): Promise\<boolean>;<br>Differences: checkAccountLabels(name: string, owner: string, labels: Array\<string>): Promise\<boolean>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: deleteCredential(name: string, credentialType: string, callback: AsyncCallback\<void>): void;<br>Differences: deleteCredential(name: string, credentialType: string, callback: AsyncCallback\<void>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: deleteCredential(name: string, credentialType: string): Promise\<void>;<br>Differences: deleteCredential(name: string, credentialType: string): Promise\<void>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: selectAccountsByOptions(options: SelectAccountsOptions, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>Differences: selectAccountsByOptions(options: SelectAccountsOptions, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: selectAccountsByOptions(options: SelectAccountsOptions): Promise\<Array\<AppAccountInfo>>;<br>Differences: selectAccountsByOptions(options: SelectAccountsOptions): Promise\<Array\<AppAccountInfo>>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: verifyCredential(name: string, owner: string, callback: AuthCallback): void;<br>Differences: verifyCredential(name: string, owner: string, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: verifyCredential(name: string, owner: string, options: VerifyCredentialOptions, callback: AuthCallback): void;<br>Differences: verifyCredential(name: string, owner: string, options: VerifyCredentialOptions, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAuthenticatorProperties(owner: string, callback: AuthCallback): void;<br>Differences: setAuthenticatorProperties(owner: string, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountManager;<br>API declaration: setAuthenticatorProperties(owner: string, options: SetPropertiesOptions, callback: AuthCallback): void;<br>Differences: setAuthenticatorProperties(owner: string, options: SetPropertiesOptions, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface AppAccountInfo<br>Differences: interface AppAccountInfo|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountInfo;<br>API declaration: owner: string;<br>Differences: owner: string;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AppAccountInfo;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface OAuthTokenInfo<br>Differences: interface OAuthTokenInfo|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: OAuthTokenInfo;<br>API declaration: authType: string;<br>Differences: authType: string;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: OAuthTokenInfo;<br>API declaration: token: string;<br>Differences: token: string;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface AuthTokenInfo<br>Differences: interface AuthTokenInfo|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthTokenInfo;<br>API declaration: authType: string;<br>Differences: authType: string;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthTokenInfo;<br>API declaration: token: string;<br>Differences: token: string;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthTokenInfo;<br>API declaration: account?: AppAccountInfo;<br>Differences: account?: AppAccountInfo;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface AuthenticatorInfo<br>Differences: interface AuthenticatorInfo|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthenticatorInfo;<br>API declaration: owner: string;<br>Differences: owner: string;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthenticatorInfo;<br>API declaration: iconId: number;<br>Differences: iconId: number;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthenticatorInfo;<br>API declaration: labelId: number;<br>Differences: labelId: number;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface AuthResult<br>Differences: interface AuthResult|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthResult;<br>API declaration: account?: AppAccountInfo;<br>Differences: account?: AppAccountInfo;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthResult;<br>API declaration: tokenInfo?: AuthTokenInfo;<br>Differences: tokenInfo?: AuthTokenInfo;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface CreateAccountOptions<br>Differences: interface CreateAccountOptions|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: CreateAccountOptions;<br>API declaration: customData?: Record\<string, string>;<br>Differences: customData?: Record\<string, string>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface CreateAccountImplicitlyOptions<br>Differences: interface CreateAccountImplicitlyOptions|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: CreateAccountImplicitlyOptions;<br>API declaration: requiredLabels?: Array\<string>;<br>Differences: requiredLabels?: Array\<string>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: CreateAccountImplicitlyOptions;<br>API declaration: authType?: string;<br>Differences: authType?: string;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: CreateAccountImplicitlyOptions;<br>API declaration: parameters?: Record\<string, Object>;<br>Differences: parameters?: Record\<string, Object>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface SelectAccountsOptions<br>Differences: interface SelectAccountsOptions|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: SelectAccountsOptions;<br>API declaration: allowedAccounts?: Array\<AppAccountInfo>;<br>Differences: allowedAccounts?: Array\<AppAccountInfo>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: SelectAccountsOptions;<br>API declaration: allowedOwners?: Array\<string>;<br>Differences: allowedOwners?: Array\<string>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: SelectAccountsOptions;<br>API declaration: requiredLabels?: Array\<string>;<br>Differences: requiredLabels?: Array\<string>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface VerifyCredentialOptions<br>Differences: interface VerifyCredentialOptions|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: VerifyCredentialOptions;<br>API declaration: credentialType?: string;<br>Differences: credentialType?: string;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: VerifyCredentialOptions;<br>API declaration: credential?: string;<br>Differences: credential?: string;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: VerifyCredentialOptions;<br>API declaration: parameters?: Record\<string, Object>;<br>Differences: parameters?: Record\<string, Object>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface SetPropertiesOptions<br>Differences: interface SetPropertiesOptions|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: SetPropertiesOptions;<br>API declaration: properties?: Record\<string, Object>;<br>Differences: properties?: Record\<string, Object>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: SetPropertiesOptions;<br>API declaration: parameters?: Record\<string, Object>;<br>Differences: parameters?: Record\<string, Object>;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: enum Constants<br>Differences: enum Constants|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: ACTION_ADD_ACCOUNT_IMPLICITLY = 'addAccountImplicitly'<br>Differences: ACTION_ADD_ACCOUNT_IMPLICITLY = 'addAccountImplicitly'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: ACTION_AUTHENTICATE = 'authenticate'<br>Differences: ACTION_AUTHENTICATE = 'authenticate'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: ACTION_CREATE_ACCOUNT_IMPLICITLY = 'createAccountImplicitly'<br>Differences: ACTION_CREATE_ACCOUNT_IMPLICITLY = 'createAccountImplicitly'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: ACTION_AUTH = 'auth'<br>Differences: ACTION_AUTH = 'auth'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: ACTION_VERIFY_CREDENTIAL = 'verifyCredential'<br>Differences: ACTION_VERIFY_CREDENTIAL = 'verifyCredential'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: ACTION_SET_AUTHENTICATOR_PROPERTIES = 'setAuthenticatorProperties'<br>Differences: ACTION_SET_AUTHENTICATOR_PROPERTIES = 'setAuthenticatorProperties'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: KEY_NAME = 'name'<br>Differences: KEY_NAME = 'name'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: KEY_OWNER = 'owner'<br>Differences: KEY_OWNER = 'owner'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: KEY_TOKEN = 'token'<br>Differences: KEY_TOKEN = 'token'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: KEY_ACTION = 'action'<br>Differences: KEY_ACTION = 'action'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: KEY_AUTH_TYPE = 'authType'<br>Differences: KEY_AUTH_TYPE = 'authType'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: KEY_SESSION_ID = 'sessionId'<br>Differences: KEY_SESSION_ID = 'sessionId'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: KEY_CALLER_PID = 'callerPid'<br>Differences: KEY_CALLER_PID = 'callerPid'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: KEY_CALLER_UID = 'callerUid'<br>Differences: KEY_CALLER_UID = 'callerUid'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: KEY_CALLER_BUNDLE_NAME = 'callerBundleName'<br>Differences: KEY_CALLER_BUNDLE_NAME = 'callerBundleName'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: KEY_REQUIRED_LABELS = 'requiredLabels'<br>Differences: KEY_REQUIRED_LABELS = 'requiredLabels'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Constants;<br>API declaration: KEY_BOOLEAN_RESULT = 'booleanResult'<br>Differences: KEY_BOOLEAN_RESULT = 'booleanResult'|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: enum ResultCode<br>Differences: enum ResultCode|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: SUCCESS = 0<br>Differences: SUCCESS = 0|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_ACCOUNT_NOT_EXIST = 10001<br>Differences: ERROR_ACCOUNT_NOT_EXIST = 10001|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_APP_ACCOUNT_SERVICE_EXCEPTION = 10002<br>Differences: ERROR_APP_ACCOUNT_SERVICE_EXCEPTION = 10002|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_INVALID_PASSWORD = 10003<br>Differences: ERROR_INVALID_PASSWORD = 10003|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_INVALID_REQUEST = 10004<br>Differences: ERROR_INVALID_REQUEST = 10004|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_INVALID_RESPONSE = 10005<br>Differences: ERROR_INVALID_RESPONSE = 10005|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_NETWORK_EXCEPTION = 10006<br>Differences: ERROR_NETWORK_EXCEPTION = 10006|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_OAUTH_AUTHENTICATOR_NOT_EXIST = 10007<br>Differences: ERROR_OAUTH_AUTHENTICATOR_NOT_EXIST = 10007|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_OAUTH_CANCELED = 10008<br>Differences: ERROR_OAUTH_CANCELED = 10008|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_OAUTH_LIST_TOO_LARGE = 10009<br>Differences: ERROR_OAUTH_LIST_TOO_LARGE = 10009|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_OAUTH_SERVICE_BUSY = 10010<br>Differences: ERROR_OAUTH_SERVICE_BUSY = 10010|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_OAUTH_SERVICE_EXCEPTION = 10011<br>Differences: ERROR_OAUTH_SERVICE_EXCEPTION = 10011|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_OAUTH_SESSION_NOT_EXIST = 10012<br>Differences: ERROR_OAUTH_SESSION_NOT_EXIST = 10012|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_OAUTH_TIMEOUT = 10013<br>Differences: ERROR_OAUTH_TIMEOUT = 10013|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_OAUTH_TOKEN_NOT_EXIST = 10014<br>Differences: ERROR_OAUTH_TOKEN_NOT_EXIST = 10014|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_OAUTH_TOKEN_TOO_MANY = 10015<br>Differences: ERROR_OAUTH_TOKEN_TOO_MANY = 10015|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_OAUTH_UNSUPPORT_ACTION = 10016<br>Differences: ERROR_OAUTH_UNSUPPORT_ACTION = 10016|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_OAUTH_UNSUPPORT_AUTH_TYPE = 10017<br>Differences: ERROR_OAUTH_UNSUPPORT_AUTH_TYPE = 10017|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: ResultCode;<br>API declaration: ERROR_PERMISSION_DENIED = 10018<br>Differences: ERROR_PERMISSION_DENIED = 10018|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface AuthenticatorCallback<br>Differences: interface AuthenticatorCallback|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthenticatorCallback;<br>API declaration: onResult: (code: number, result: {<br>            [key: string]: any;<br>        }) => void;<br>Differences: onResult: (code: number, result: {<br>            [key: string]: any;<br>        }) => void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthenticatorCallback;<br>API declaration: onRequestRedirected: (request: Want) => void;<br>Differences: onRequestRedirected: (request: Want) => void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: interface AuthCallback<br>Differences: interface AuthCallback|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthCallback;<br>API declaration: onResult: (code: number, result?: AuthResult) => void;<br>Differences: onResult: (code: number, result?: AuthResult) => void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthCallback;<br>API declaration: onRequestRedirected: (request: Want) => void;<br>Differences: onRequestRedirected: (request: Want) => void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: AuthCallback;<br>API declaration: onRequestContinued?: () => void;<br>Differences: onRequestContinued?: () => void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: appAccount;<br>API declaration: class Authenticator<br>Differences: class Authenticator|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Authenticator;<br>API declaration: addAccountImplicitly(authType: string, callerBundleName: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;<br>Differences: addAccountImplicitly(authType: string, callerBundleName: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Authenticator;<br>API declaration: createAccountImplicitly(options: CreateAccountImplicitlyOptions, callback: AuthCallback): void;<br>Differences: createAccountImplicitly(options: CreateAccountImplicitlyOptions, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Authenticator;<br>API declaration: authenticate(name: string, authType: string, callerBundleName: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;<br>Differences: authenticate(name: string, authType: string, callerBundleName: string, options: {<br>            [key: string]: any;<br>        }, callback: AuthenticatorCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Authenticator;<br>API declaration: auth(name: string, authType: string, options: Record\<string, Object>, callback: AuthCallback): void;<br>Differences: auth(name: string, authType: string, options: Record\<string, Object>, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Authenticator;<br>API declaration: verifyCredential(name: string, options: VerifyCredentialOptions, callback: AuthCallback): void;<br>Differences: verifyCredential(name: string, options: VerifyCredentialOptions, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Authenticator;<br>API declaration: setProperties(options: SetPropertiesOptions, callback: AuthCallback): void;<br>Differences: setProperties(options: SetPropertiesOptions, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Authenticator;<br>API declaration: checkAccountLabels(name: string, labels: Array\<string>, callback: AuthCallback): void;<br>Differences: checkAccountLabels(name: string, labels: Array\<string>, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Authenticator;<br>API declaration: checkAccountRemovable(name: string, callback: AuthCallback): void;<br>Differences: checkAccountRemovable(name: string, callback: AuthCallback): void;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: Authenticator;<br>API declaration: getRemoteObject(): rpc.RemoteObject;<br>Differences: getRemoteObject(): rpc.RemoteObject;|api/@ohos.account.appAccount.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace distributedAccount<br>Differences: declare namespace distributedAccount|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: distributedAccount;<br>API declaration: function getDistributedAccountAbility(): DistributedAccountAbility;<br>Differences: function getDistributedAccountAbility(): DistributedAccountAbility;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: distributedAccount;<br>API declaration: interface DistributedAccountAbility<br>Differences: interface DistributedAccountAbility|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedAccountAbility;<br>API declaration: queryOsAccountDistributedInfo(callback: AsyncCallback\<DistributedInfo>): void;<br>Differences: queryOsAccountDistributedInfo(callback: AsyncCallback\<DistributedInfo>): void;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedAccountAbility;<br>API declaration: queryOsAccountDistributedInfo(): Promise\<DistributedInfo>;<br>Differences: queryOsAccountDistributedInfo(): Promise\<DistributedInfo>;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedAccountAbility;<br>API declaration: getOsAccountDistributedInfo(callback: AsyncCallback\<DistributedInfo>): void;<br>Differences: getOsAccountDistributedInfo(callback: AsyncCallback\<DistributedInfo>): void;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedAccountAbility;<br>API declaration: getOsAccountDistributedInfo(): Promise\<DistributedInfo>;<br>Differences: getOsAccountDistributedInfo(): Promise\<DistributedInfo>;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedAccountAbility;<br>API declaration: updateOsAccountDistributedInfo(accountInfo: DistributedInfo, callback: AsyncCallback\<void>): void;<br>Differences: updateOsAccountDistributedInfo(accountInfo: DistributedInfo, callback: AsyncCallback\<void>): void;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedAccountAbility;<br>API declaration: updateOsAccountDistributedInfo(accountInfo: DistributedInfo): Promise\<void>;<br>Differences: updateOsAccountDistributedInfo(accountInfo: DistributedInfo): Promise\<void>;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedAccountAbility;<br>API declaration: setOsAccountDistributedInfo(accountInfo: DistributedInfo, callback: AsyncCallback\<void>): void;<br>Differences: setOsAccountDistributedInfo(accountInfo: DistributedInfo, callback: AsyncCallback\<void>): void;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedAccountAbility;<br>API declaration: setOsAccountDistributedInfo(accountInfo: DistributedInfo): Promise\<void>;<br>Differences: setOsAccountDistributedInfo(accountInfo: DistributedInfo): Promise\<void>;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: distributedAccount;<br>API declaration: enum DistributedAccountStatus<br>Differences: enum DistributedAccountStatus|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedAccountStatus;<br>API declaration: NOT_LOGGED_IN = 0<br>Differences: NOT_LOGGED_IN = 0|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedAccountStatus;<br>API declaration: LOGGED_IN = 1<br>Differences: LOGGED_IN = 1|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: distributedAccount;<br>API declaration: interface DistributedInfo<br>Differences: interface DistributedInfo|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedInfo;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedInfo;<br>API declaration: id: string;<br>Differences: id: string;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedInfo;<br>API declaration: event: string;<br>Differences: event: string;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedInfo;<br>API declaration: nickname?: string;<br>Differences: nickname?: string;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedInfo;<br>API declaration: avatar?: string;<br>Differences: avatar?: string;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedInfo;<br>API declaration: readonly status?: DistributedAccountStatus;<br>Differences: readonly status?: DistributedAccountStatus;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: DistributedInfo;<br>API declaration: scalableData?: object;<br>Differences: scalableData?: object;|api/@ohos.account.distributedAccount.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace osAccount<br>Differences: declare namespace osAccount|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: osAccount;<br>API declaration: function getAccountManager(): AccountManager;<br>Differences: function getAccountManager(): AccountManager;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: osAccount;<br>API declaration: interface AccountManager<br>Differences: interface AccountManager|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isMultiOsAccountEnable(callback: AsyncCallback\<boolean>): void;<br>Differences: isMultiOsAccountEnable(callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isMultiOsAccountEnable(): Promise\<boolean>;<br>Differences: isMultiOsAccountEnable(): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: checkMultiOsAccountEnabled(callback: AsyncCallback\<boolean>): void;<br>Differences: checkMultiOsAccountEnabled(callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: checkMultiOsAccountEnabled(): Promise\<boolean>;<br>Differences: checkMultiOsAccountEnabled(): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isOsAccountActived(localId: number, callback: AsyncCallback\<boolean>): void;<br>Differences: isOsAccountActived(localId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isOsAccountActived(localId: number): Promise\<boolean>;<br>Differences: isOsAccountActived(localId: number): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: checkOsAccountActivated(localId: number, callback: AsyncCallback\<boolean>): void;<br>Differences: checkOsAccountActivated(localId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: checkOsAccountActivated(localId: number): Promise\<boolean>;<br>Differences: checkOsAccountActivated(localId: number): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isOsAccountConstraintEnable(localId: number, constraint: string, callback: AsyncCallback\<boolean>): void;<br>Differences: isOsAccountConstraintEnable(localId: number, constraint: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isOsAccountConstraintEnable(localId: number, constraint: string): Promise\<boolean>;<br>Differences: isOsAccountConstraintEnable(localId: number, constraint: string): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: checkOsAccountConstraintEnabled(localId: number, constraint: string, callback: AsyncCallback\<boolean>): void;<br>Differences: checkOsAccountConstraintEnabled(localId: number, constraint: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: checkOsAccountConstraintEnabled(localId: number, constraint: string): Promise\<boolean>;<br>Differences: checkOsAccountConstraintEnabled(localId: number, constraint: string): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isOsAccountConstraintEnabled(constraint: string): Promise\<boolean>;<br>Differences: isOsAccountConstraintEnabled(constraint: string): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isTestOsAccount(callback: AsyncCallback\<boolean>): void;<br>Differences: isTestOsAccount(callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isTestOsAccount(): Promise\<boolean>;<br>Differences: isTestOsAccount(): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: checkOsAccountTestable(callback: AsyncCallback\<boolean>): void;<br>Differences: checkOsAccountTestable(callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: checkOsAccountTestable(): Promise\<boolean>;<br>Differences: checkOsAccountTestable(): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isOsAccountVerified(callback: AsyncCallback\<boolean>): void;<br>Differences: isOsAccountVerified(callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isOsAccountVerified(localId: number, callback: AsyncCallback\<boolean>): void;<br>Differences: isOsAccountVerified(localId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isOsAccountVerified(localId?: number): Promise\<boolean>;<br>Differences: isOsAccountVerified(localId?: number): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: checkOsAccountVerified(callback: AsyncCallback\<boolean>): void;<br>Differences: checkOsAccountVerified(callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: checkOsAccountVerified(): Promise\<boolean>;<br>Differences: checkOsAccountVerified(): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: checkOsAccountVerified(localId: number, callback: AsyncCallback\<boolean>): void;<br>Differences: checkOsAccountVerified(localId: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: checkOsAccountVerified(localId: number): Promise\<boolean>;<br>Differences: checkOsAccountVerified(localId: number): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: isOsAccountUnlocked(): Promise\<boolean>;<br>Differences: isOsAccountUnlocked(): Promise\<boolean>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getCreatedOsAccountsCount(callback: AsyncCallback\<number>): void;<br>Differences: getCreatedOsAccountsCount(callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getCreatedOsAccountsCount(): Promise\<number>;<br>Differences: getCreatedOsAccountsCount(): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountCount(callback: AsyncCallback\<number>): void;<br>Differences: getOsAccountCount(callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountCount(): Promise\<number>;<br>Differences: getOsAccountCount(): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdFromProcess(callback: AsyncCallback\<number>): void;<br>Differences: getOsAccountLocalIdFromProcess(callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdFromProcess(): Promise\<number>;<br>Differences: getOsAccountLocalIdFromProcess(): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalId(callback: AsyncCallback\<number>): void;<br>Differences: getOsAccountLocalId(callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalId(): Promise\<number>;<br>Differences: getOsAccountLocalId(): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdFromUid(uid: number, callback: AsyncCallback\<number>): void;<br>Differences: getOsAccountLocalIdFromUid(uid: number, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdFromUid(uid: number): Promise\<number>;<br>Differences: getOsAccountLocalIdFromUid(uid: number): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdForUid(uid: number, callback: AsyncCallback\<number>): void;<br>Differences: getOsAccountLocalIdForUid(uid: number, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdForUid(uid: number): Promise\<number>;<br>Differences: getOsAccountLocalIdForUid(uid: number): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdForUidSync(uid: number): number;<br>Differences: getOsAccountLocalIdForUidSync(uid: number): number;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdFromDomain(domainInfo: DomainAccountInfo, callback: AsyncCallback\<number>): void;<br>Differences: getOsAccountLocalIdFromDomain(domainInfo: DomainAccountInfo, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdFromDomain(domainInfo: DomainAccountInfo): Promise\<number>;<br>Differences: getOsAccountLocalIdFromDomain(domainInfo: DomainAccountInfo): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdForDomain(domainInfo: DomainAccountInfo, callback: AsyncCallback\<number>): void;<br>Differences: getOsAccountLocalIdForDomain(domainInfo: DomainAccountInfo, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdForDomain(domainInfo: DomainAccountInfo): Promise\<number>;<br>Differences: getOsAccountLocalIdForDomain(domainInfo: DomainAccountInfo): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountAllConstraints(localId: number, callback: AsyncCallback\<Array\<string>>): void;<br>Differences: getOsAccountAllConstraints(localId: number, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountAllConstraints(localId: number): Promise\<Array\<string>>;<br>Differences: getOsAccountAllConstraints(localId: number): Promise\<Array\<string>>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountConstraints(localId: number, callback: AsyncCallback\<Array\<string>>): void;<br>Differences: getOsAccountConstraints(localId: number, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountConstraints(localId: number): Promise\<Array\<string>>;<br>Differences: getOsAccountConstraints(localId: number): Promise\<Array\<string>>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: queryActivatedOsAccountIds(callback: AsyncCallback\<Array\<number>>): void;<br>Differences: queryActivatedOsAccountIds(callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: queryActivatedOsAccountIds(): Promise\<Array\<number>>;<br>Differences: queryActivatedOsAccountIds(): Promise\<Array\<number>>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getActivatedOsAccountLocalIds(callback: AsyncCallback\<Array\<number>>): void;<br>Differences: getActivatedOsAccountLocalIds(callback: AsyncCallback\<Array\<number>>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getActivatedOsAccountLocalIds(): Promise\<Array\<number>>;<br>Differences: getActivatedOsAccountLocalIds(): Promise\<Array\<number>>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: queryCurrentOsAccount(callback: AsyncCallback\<OsAccountInfo>): void;<br>Differences: queryCurrentOsAccount(callback: AsyncCallback\<OsAccountInfo>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: queryCurrentOsAccount(): Promise\<OsAccountInfo>;<br>Differences: queryCurrentOsAccount(): Promise\<OsAccountInfo>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getCurrentOsAccount(callback: AsyncCallback\<OsAccountInfo>): void;<br>Differences: getCurrentOsAccount(callback: AsyncCallback\<OsAccountInfo>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getCurrentOsAccount(): Promise\<OsAccountInfo>;<br>Differences: getCurrentOsAccount(): Promise\<OsAccountInfo>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountTypeFromProcess(callback: AsyncCallback\<OsAccountType>): void;<br>Differences: getOsAccountTypeFromProcess(callback: AsyncCallback\<OsAccountType>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountTypeFromProcess(): Promise\<OsAccountType>;<br>Differences: getOsAccountTypeFromProcess(): Promise\<OsAccountType>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountType(callback: AsyncCallback\<OsAccountType>): void;<br>Differences: getOsAccountType(callback: AsyncCallback\<OsAccountType>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountType(): Promise\<OsAccountType>;<br>Differences: getOsAccountType(): Promise\<OsAccountType>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getDistributedVirtualDeviceId(callback: AsyncCallback\<string>): void;<br>Differences: getDistributedVirtualDeviceId(callback: AsyncCallback\<string>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getDistributedVirtualDeviceId(): Promise\<string>;<br>Differences: getDistributedVirtualDeviceId(): Promise\<string>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: queryDistributedVirtualDeviceId(callback: AsyncCallback\<string>): void;<br>Differences: queryDistributedVirtualDeviceId(callback: AsyncCallback\<string>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: queryDistributedVirtualDeviceId(): Promise\<string>;<br>Differences: queryDistributedVirtualDeviceId(): Promise\<string>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdBySerialNumber(serialNumber: number, callback: AsyncCallback\<number>): void;<br>Differences: getOsAccountLocalIdBySerialNumber(serialNumber: number, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdBySerialNumber(serialNumber: number): Promise\<number>;<br>Differences: getOsAccountLocalIdBySerialNumber(serialNumber: number): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdForSerialNumber(serialNumber: number, callback: AsyncCallback\<number>): void;<br>Differences: getOsAccountLocalIdForSerialNumber(serialNumber: number, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getOsAccountLocalIdForSerialNumber(serialNumber: number): Promise\<number>;<br>Differences: getOsAccountLocalIdForSerialNumber(serialNumber: number): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getSerialNumberByOsAccountLocalId(localId: number, callback: AsyncCallback\<number>): void;<br>Differences: getSerialNumberByOsAccountLocalId(localId: number, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getSerialNumberByOsAccountLocalId(localId: number): Promise\<number>;<br>Differences: getSerialNumberByOsAccountLocalId(localId: number): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getSerialNumberForOsAccountLocalId(localId: number, callback: AsyncCallback\<number>): void;<br>Differences: getSerialNumberForOsAccountLocalId(localId: number, callback: AsyncCallback\<number>): void;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: AccountManager;<br>API declaration: getSerialNumberForOsAccountLocalId(localId: number): Promise\<number>;<br>Differences: getSerialNumberForOsAccountLocalId(localId: number): Promise\<number>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: osAccount;<br>API declaration: interface OsAccountInfo<br>Differences: interface OsAccountInfo|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: localId: number;<br>Differences: localId: number;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: localName: string;<br>Differences: localName: string;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: type: OsAccountType;<br>Differences: type: OsAccountType;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: constraints: Array\<string>;<br>Differences: constraints: Array\<string>;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: isVerified: boolean;<br>Differences: isVerified: boolean;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: isUnlocked: boolean;<br>Differences: isUnlocked: boolean;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: photo: string;<br>Differences: photo: string;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: createTime: number;<br>Differences: createTime: number;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: lastLoginTime: number;<br>Differences: lastLoginTime: number;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: serialNumber: number;<br>Differences: serialNumber: number;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: isActived: boolean;<br>Differences: isActived: boolean;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: isActivated: boolean;<br>Differences: isActivated: boolean;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: isCreateCompleted: boolean;<br>Differences: isCreateCompleted: boolean;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: distributedInfo: distributedAccount.DistributedInfo;<br>Differences: distributedInfo: distributedAccount.DistributedInfo;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountInfo;<br>API declaration: domainInfo: DomainAccountInfo;<br>Differences: domainInfo: DomainAccountInfo;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: osAccount;<br>API declaration: interface DomainAccountInfo<br>Differences: interface DomainAccountInfo|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: DomainAccountInfo;<br>API declaration: domain: string;<br>Differences: domain: string;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: DomainAccountInfo;<br>API declaration: accountName: string;<br>Differences: accountName: string;|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: osAccount;<br>API declaration: enum OsAccountType<br>Differences: enum OsAccountType|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountType;<br>API declaration: ADMIN = 0<br>Differences: ADMIN = 0|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountType;<br>API declaration: NORMAL<br>Differences: NORMAL|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: OsAccountType;<br>API declaration: GUEST<br>Differences: GUEST|api/@ohos.account.osAccount.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Callback<br>Differences: export interface Callback|api/@ohos.base.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface ErrorCallback<br>Differences: export interface ErrorCallback|api/@ohos.base.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface AsyncCallback<br>Differences: export interface AsyncCallback|api/@ohos.base.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface BusinessError<br>Differences: export interface BusinessError|api/@ohos.base.d.ts|
|New API|NA|Class name: BusinessError;<br>API declaration: code: number;<br>Differences: code: number;|api/@ohos.base.d.ts|
|New API|NA|Class name: BusinessError;<br>API declaration: data?: T;<br>Differences: data?: T;|api/@ohos.base.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace batteryInfo<br>Differences: declare namespace batteryInfo|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: const batterySOC: number;<br>Differences: const batterySOC: number;|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: const chargingStatus: BatteryChargeState;<br>Differences: const chargingStatus: BatteryChargeState;|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: const healthStatus: BatteryHealthState;<br>Differences: const healthStatus: BatteryHealthState;|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: const pluggedType: BatteryPluggedType;<br>Differences: const pluggedType: BatteryPluggedType;|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: const voltage: number;<br>Differences: const voltage: number;|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: const technology: string;<br>Differences: const technology: string;|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: const batteryTemperature: number;<br>Differences: const batteryTemperature: number;|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: const isBatteryPresent: boolean;<br>Differences: const isBatteryPresent: boolean;|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: const batteryCapacityLevel: BatteryCapacityLevel;<br>Differences: const batteryCapacityLevel: BatteryCapacityLevel;|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: export enum BatteryPluggedType<br>Differences: export enum BatteryPluggedType|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryPluggedType;<br>API declaration: NONE<br>Differences: NONE|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryPluggedType;<br>API declaration: AC<br>Differences: AC|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryPluggedType;<br>API declaration: USB<br>Differences: USB|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryPluggedType;<br>API declaration: WIRELESS<br>Differences: WIRELESS|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: export enum BatteryChargeState<br>Differences: export enum BatteryChargeState|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryChargeState;<br>API declaration: NONE<br>Differences: NONE|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryChargeState;<br>API declaration: ENABLE<br>Differences: ENABLE|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryChargeState;<br>API declaration: DISABLE<br>Differences: DISABLE|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryChargeState;<br>API declaration: FULL<br>Differences: FULL|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: export enum BatteryHealthState<br>Differences: export enum BatteryHealthState|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryHealthState;<br>API declaration: UNKNOWN<br>Differences: UNKNOWN|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryHealthState;<br>API declaration: GOOD<br>Differences: GOOD|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryHealthState;<br>API declaration: OVERHEAT<br>Differences: OVERHEAT|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryHealthState;<br>API declaration: OVERVOLTAGE<br>Differences: OVERVOLTAGE|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryHealthState;<br>API declaration: COLD<br>Differences: COLD|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryHealthState;<br>API declaration: DEAD<br>Differences: DEAD|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: export enum BatteryCapacityLevel<br>Differences: export enum BatteryCapacityLevel|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryCapacityLevel;<br>API declaration: LEVEL_FULL<br>Differences: LEVEL_FULL|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryCapacityLevel;<br>API declaration: LEVEL_HIGH<br>Differences: LEVEL_HIGH|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryCapacityLevel;<br>API declaration: LEVEL_NORMAL<br>Differences: LEVEL_NORMAL|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryCapacityLevel;<br>API declaration: LEVEL_LOW<br>Differences: LEVEL_LOW|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryCapacityLevel;<br>API declaration: LEVEL_WARNING<br>Differences: LEVEL_WARNING|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryCapacityLevel;<br>API declaration: LEVEL_CRITICAL<br>Differences: LEVEL_CRITICAL|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: BatteryCapacityLevel;<br>API declaration: LEVEL_SHUTDOWN<br>Differences: LEVEL_SHUTDOWN|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: batteryInfo;<br>API declaration: export enum CommonEventBatteryChangedKey<br>Differences: export enum CommonEventBatteryChangedKey|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: CommonEventBatteryChangedKey;<br>API declaration: EXTRA_SOC = 'soc'<br>Differences: EXTRA_SOC = 'soc'|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: CommonEventBatteryChangedKey;<br>API declaration: EXTRA_CHARGE_STATE = 'chargeState'<br>Differences: EXTRA_CHARGE_STATE = 'chargeState'|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: CommonEventBatteryChangedKey;<br>API declaration: EXTRA_HEALTH_STATE = 'healthState'<br>Differences: EXTRA_HEALTH_STATE = 'healthState'|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: CommonEventBatteryChangedKey;<br>API declaration: EXTRA_PLUGGED_TYPE = 'pluggedType'<br>Differences: EXTRA_PLUGGED_TYPE = 'pluggedType'|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: CommonEventBatteryChangedKey;<br>API declaration: EXTRA_VOLTAGE = 'voltage'<br>Differences: EXTRA_VOLTAGE = 'voltage'|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: CommonEventBatteryChangedKey;<br>API declaration: EXTRA_TECHNOLOGY = 'technology'<br>Differences: EXTRA_TECHNOLOGY = 'technology'|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: CommonEventBatteryChangedKey;<br>API declaration: EXTRA_TEMPERATURE = 'temperature'<br>Differences: EXTRA_TEMPERATURE = 'temperature'|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: CommonEventBatteryChangedKey;<br>API declaration: EXTRA_PRESENT = 'present'<br>Differences: EXTRA_PRESENT = 'present'|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: CommonEventBatteryChangedKey;<br>API declaration: EXTRA_CAPACITY_LEVEL = 'capacityLevel'<br>Differences: EXTRA_CAPACITY_LEVEL = 'capacityLevel'|api/@ohos.batteryInfo.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace commonEventManager<br>Differences: declare namespace commonEventManager|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: commonEventManager;<br>API declaration: function publish(event: string, callback: AsyncCallback\<void>): void;<br>Differences: function publish(event: string, callback: AsyncCallback\<void>): void;|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: commonEventManager;<br>API declaration: function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback\<void>): void;<br>Differences: function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback\<void>): void;|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: commonEventManager;<br>API declaration: function createSubscriber(subscribeInfo: CommonEventSubscribeInfo, callback: AsyncCallback\<CommonEventSubscriber>): void;<br>Differences: function createSubscriber(subscribeInfo: CommonEventSubscribeInfo, callback: AsyncCallback\<CommonEventSubscriber>): void;|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: commonEventManager;<br>API declaration: function createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise\<CommonEventSubscriber>;<br>Differences: function createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise\<CommonEventSubscriber>;|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: commonEventManager;<br>API declaration: function createSubscriberSync(subscribeInfo: CommonEventSubscribeInfo): CommonEventSubscriber;<br>Differences: function createSubscriberSync(subscribeInfo: CommonEventSubscribeInfo): CommonEventSubscriber;|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: commonEventManager;<br>API declaration: function subscribe(subscriber: CommonEventSubscriber, callback: AsyncCallback\<CommonEventData>): void;<br>Differences: function subscribe(subscriber: CommonEventSubscriber, callback: AsyncCallback\<CommonEventData>): void;|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: commonEventManager;<br>API declaration: function unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback\<void>): void;<br>Differences: function unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback\<void>): void;|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: commonEventManager;<br>API declaration: export enum Support<br>Differences: export enum Support|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BOOT_COMPLETED = 'usual.event.BOOT_COMPLETED'<br>Differences: COMMON_EVENT_BOOT_COMPLETED = 'usual.event.BOOT_COMPLETED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_LOCKED_BOOT_COMPLETED = 'usual.event.LOCKED_BOOT_COMPLETED'<br>Differences: COMMON_EVENT_LOCKED_BOOT_COMPLETED = 'usual.event.LOCKED_BOOT_COMPLETED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_SHUTDOWN = 'usual.event.SHUTDOWN'<br>Differences: COMMON_EVENT_SHUTDOWN = 'usual.event.SHUTDOWN'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BATTERY_CHANGED = 'usual.event.BATTERY_CHANGED'<br>Differences: COMMON_EVENT_BATTERY_CHANGED = 'usual.event.BATTERY_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BATTERY_LOW = 'usual.event.BATTERY_LOW'<br>Differences: COMMON_EVENT_BATTERY_LOW = 'usual.event.BATTERY_LOW'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BATTERY_OKAY = 'usual.event.BATTERY_OKAY'<br>Differences: COMMON_EVENT_BATTERY_OKAY = 'usual.event.BATTERY_OKAY'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_POWER_CONNECTED = 'usual.event.POWER_CONNECTED'<br>Differences: COMMON_EVENT_POWER_CONNECTED = 'usual.event.POWER_CONNECTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_POWER_DISCONNECTED = 'usual.event.POWER_DISCONNECTED'<br>Differences: COMMON_EVENT_POWER_DISCONNECTED = 'usual.event.POWER_DISCONNECTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_SCREEN_OFF = 'usual.event.SCREEN_OFF'<br>Differences: COMMON_EVENT_SCREEN_OFF = 'usual.event.SCREEN_OFF'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_SCREEN_ON = 'usual.event.SCREEN_ON'<br>Differences: COMMON_EVENT_SCREEN_ON = 'usual.event.SCREEN_ON'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_THERMAL_LEVEL_CHANGED = 'usual.event.THERMAL_LEVEL_CHANGED'<br>Differences: COMMON_EVENT_THERMAL_LEVEL_CHANGED = 'usual.event.THERMAL_LEVEL_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USER_PRESENT = 'usual.event.USER_PRESENT'<br>Differences: COMMON_EVENT_USER_PRESENT = 'usual.event.USER_PRESENT'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_TIME_TICK = 'usual.event.TIME_TICK'<br>Differences: COMMON_EVENT_TIME_TICK = 'usual.event.TIME_TICK'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_TIME_CHANGED = 'usual.event.TIME_CHANGED'<br>Differences: COMMON_EVENT_TIME_CHANGED = 'usual.event.TIME_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DATE_CHANGED = 'usual.event.DATE_CHANGED'<br>Differences: COMMON_EVENT_DATE_CHANGED = 'usual.event.DATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_TIMEZONE_CHANGED = 'usual.event.TIMEZONE_CHANGED'<br>Differences: COMMON_EVENT_TIMEZONE_CHANGED = 'usual.event.TIMEZONE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_CLOSE_SYSTEM_DIALOGS = 'usual.event.CLOSE_SYSTEM_DIALOGS'<br>Differences: COMMON_EVENT_CLOSE_SYSTEM_DIALOGS = 'usual.event.CLOSE_SYSTEM_DIALOGS'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGE_ADDED = 'usual.event.PACKAGE_ADDED'<br>Differences: COMMON_EVENT_PACKAGE_ADDED = 'usual.event.PACKAGE_ADDED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGE_REPLACED = 'usual.event.PACKAGE_REPLACED'<br>Differences: COMMON_EVENT_PACKAGE_REPLACED = 'usual.event.PACKAGE_REPLACED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_MY_PACKAGE_REPLACED = 'usual.event.MY_PACKAGE_REPLACED'<br>Differences: COMMON_EVENT_MY_PACKAGE_REPLACED = 'usual.event.MY_PACKAGE_REPLACED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGE_REMOVED = 'usual.event.PACKAGE_REMOVED'<br>Differences: COMMON_EVENT_PACKAGE_REMOVED = 'usual.event.PACKAGE_REMOVED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BUNDLE_REMOVED = 'usual.event.BUNDLE_REMOVED'<br>Differences: COMMON_EVENT_BUNDLE_REMOVED = 'usual.event.BUNDLE_REMOVED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGE_FULLY_REMOVED = 'usual.event.PACKAGE_FULLY_REMOVED'<br>Differences: COMMON_EVENT_PACKAGE_FULLY_REMOVED = 'usual.event.PACKAGE_FULLY_REMOVED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGE_CHANGED = 'usual.event.PACKAGE_CHANGED'<br>Differences: COMMON_EVENT_PACKAGE_CHANGED = 'usual.event.PACKAGE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGE_RESTARTED = 'usual.event.PACKAGE_RESTARTED'<br>Differences: COMMON_EVENT_PACKAGE_RESTARTED = 'usual.event.PACKAGE_RESTARTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGE_DATA_CLEARED = 'usual.event.PACKAGE_DATA_CLEARED'<br>Differences: COMMON_EVENT_PACKAGE_DATA_CLEARED = 'usual.event.PACKAGE_DATA_CLEARED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGE_CACHE_CLEARED = 'usual.event.PACKAGE_CACHE_CLEARED'<br>Differences: COMMON_EVENT_PACKAGE_CACHE_CLEARED = 'usual.event.PACKAGE_CACHE_CLEARED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGES_SUSPENDED = 'usual.event.PACKAGES_SUSPENDED'<br>Differences: COMMON_EVENT_PACKAGES_SUSPENDED = 'usual.event.PACKAGES_SUSPENDED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGES_UNSUSPENDED = 'usual.event.PACKAGES_UNSUSPENDED'<br>Differences: COMMON_EVENT_PACKAGES_UNSUSPENDED = 'usual.event.PACKAGES_UNSUSPENDED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_MY_PACKAGE_SUSPENDED = 'usual.event.MY_PACKAGE_SUSPENDED'<br>Differences: COMMON_EVENT_MY_PACKAGE_SUSPENDED = 'usual.event.MY_PACKAGE_SUSPENDED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_MY_PACKAGE_UNSUSPENDED = 'usual.event.MY_PACKAGE_UNSUSPENDED'<br>Differences: COMMON_EVENT_MY_PACKAGE_UNSUSPENDED = 'usual.event.MY_PACKAGE_UNSUSPENDED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_UID_REMOVED = 'usual.event.UID_REMOVED'<br>Differences: COMMON_EVENT_UID_REMOVED = 'usual.event.UID_REMOVED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGE_FIRST_LAUNCH = 'usual.event.PACKAGE_FIRST_LAUNCH'<br>Differences: COMMON_EVENT_PACKAGE_FIRST_LAUNCH = 'usual.event.PACKAGE_FIRST_LAUNCH'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION = 'usual.event.PACKAGE_NEEDS_VERIFICATION'<br>Differences: COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION = 'usual.event.PACKAGE_NEEDS_VERIFICATION'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_PACKAGE_VERIFIED = 'usual.event.PACKAGE_VERIFIED'<br>Differences: COMMON_EVENT_PACKAGE_VERIFIED = 'usual.event.PACKAGE_VERIFIED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_AVAILABLE'<br>Differences: COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_AVAILABLE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE'<br>Differences: COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_CONFIGURATION_CHANGED = 'usual.event.CONFIGURATION_CHANGED'<br>Differences: COMMON_EVENT_CONFIGURATION_CHANGED = 'usual.event.CONFIGURATION_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_LOCALE_CHANGED = 'usual.event.LOCALE_CHANGED'<br>Differences: COMMON_EVENT_LOCALE_CHANGED = 'usual.event.LOCALE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_MANAGE_PACKAGE_STORAGE = 'usual.event.MANAGE_PACKAGE_STORAGE'<br>Differences: COMMON_EVENT_MANAGE_PACKAGE_STORAGE = 'usual.event.MANAGE_PACKAGE_STORAGE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DRIVE_MODE = 'common.event.DRIVE_MODE'<br>Differences: COMMON_EVENT_DRIVE_MODE = 'common.event.DRIVE_MODE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_HOME_MODE = 'common.event.HOME_MODE'<br>Differences: COMMON_EVENT_HOME_MODE = 'common.event.HOME_MODE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_OFFICE_MODE = 'common.event.OFFICE_MODE'<br>Differences: COMMON_EVENT_OFFICE_MODE = 'common.event.OFFICE_MODE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USER_STARTED = 'usual.event.USER_STARTED'<br>Differences: COMMON_EVENT_USER_STARTED = 'usual.event.USER_STARTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USER_BACKGROUND = 'usual.event.USER_BACKGROUND'<br>Differences: COMMON_EVENT_USER_BACKGROUND = 'usual.event.USER_BACKGROUND'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USER_FOREGROUND = 'usual.event.USER_FOREGROUND'<br>Differences: COMMON_EVENT_USER_FOREGROUND = 'usual.event.USER_FOREGROUND'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USER_SWITCHED = 'usual.event.USER_SWITCHED'<br>Differences: COMMON_EVENT_USER_SWITCHED = 'usual.event.USER_SWITCHED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USER_STARTING = 'usual.event.USER_STARTING'<br>Differences: COMMON_EVENT_USER_STARTING = 'usual.event.USER_STARTING'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USER_UNLOCKED = 'usual.event.USER_UNLOCKED'<br>Differences: COMMON_EVENT_USER_UNLOCKED = 'usual.event.USER_UNLOCKED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USER_STOPPING = 'usual.event.USER_STOPPING'<br>Differences: COMMON_EVENT_USER_STOPPING = 'usual.event.USER_STOPPING'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USER_STOPPED = 'usual.event.USER_STOPPED'<br>Differences: COMMON_EVENT_USER_STOPPED = 'usual.event.USER_STOPPED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN = 'common.event.DISTRIBUTED_ACCOUNT_LOGIN'<br>Differences: COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN = 'common.event.DISTRIBUTED_ACCOUNT_LOGIN'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT = 'common.event.DISTRIBUTED_ACCOUNT_LOGOUT'<br>Differences: COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT = 'common.event.DISTRIBUTED_ACCOUNT_LOGOUT'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID = 'common.event.DISTRIBUTED_ACCOUNT_TOKEN_INVALID'<br>Differences: COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID = 'common.event.DISTRIBUTED_ACCOUNT_TOKEN_INVALID'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF = 'common.event.DISTRIBUTED_ACCOUNT_LOGOFF'<br>Differences: COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF = 'common.event.DISTRIBUTED_ACCOUNT_LOGOFF'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_POWER_STATE = 'usual.event.wifi.POWER_STATE'<br>Differences: COMMON_EVENT_WIFI_POWER_STATE = 'usual.event.wifi.POWER_STATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_SCAN_FINISHED = 'usual.event.wifi.SCAN_FINISHED'<br>Differences: COMMON_EVENT_WIFI_SCAN_FINISHED = 'usual.event.wifi.SCAN_FINISHED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_RSSI_VALUE = 'usual.event.wifi.RSSI_VALUE'<br>Differences: COMMON_EVENT_WIFI_RSSI_VALUE = 'usual.event.wifi.RSSI_VALUE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_CONN_STATE = 'usual.event.wifi.CONN_STATE'<br>Differences: COMMON_EVENT_WIFI_CONN_STATE = 'usual.event.wifi.CONN_STATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_HOTSPOT_STATE = 'usual.event.wifi.HOTSPOT_STATE'<br>Differences: COMMON_EVENT_WIFI_HOTSPOT_STATE = 'usual.event.wifi.HOTSPOT_STATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_AP_STA_JOIN = 'usual.event.wifi.WIFI_HS_STA_JOIN'<br>Differences: COMMON_EVENT_WIFI_AP_STA_JOIN = 'usual.event.wifi.WIFI_HS_STA_JOIN'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_AP_STA_LEAVE = 'usual.event.wifi.WIFI_HS_STA_LEAVE'<br>Differences: COMMON_EVENT_WIFI_AP_STA_LEAVE = 'usual.event.wifi.WIFI_HS_STA_LEAVE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE = 'usual.event.wifi.mplink.STATE_CHANGE'<br>Differences: COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE = 'usual.event.wifi.mplink.STATE_CHANGE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_P2P_CONN_STATE = 'usual.event.wifi.p2p.CONN_STATE_CHANGE'<br>Differences: COMMON_EVENT_WIFI_P2P_CONN_STATE = 'usual.event.wifi.p2p.CONN_STATE_CHANGE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_P2P_STATE_CHANGED = 'usual.event.wifi.p2p.STATE_CHANGE'<br>Differences: COMMON_EVENT_WIFI_P2P_STATE_CHANGED = 'usual.event.wifi.p2p.STATE_CHANGE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED = 'usual.event.wifi.p2p.DEVICES_CHANGE'<br>Differences: COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED = 'usual.event.wifi.p2p.DEVICES_CHANGE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED = 'usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE'<br>Differences: COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED = 'usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED = 'usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE'<br>Differences: COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED = 'usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED = 'usual.event.wifi.p2p.GROUP_STATE_CHANGED'<br>Differences: COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED = 'usual.event.wifi.p2p.GROUP_STATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE = 'usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE = 'usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE = 'usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE = 'usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE = 'usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE = 'usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED = 'usual.event.bluetooth.remotedevice.DISCOVERED'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED = 'usual.event.bluetooth.remotedevice.DISCOVERED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE = 'usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE = 'usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED = 'usual.event.bluetooth.remotedevice.ACL_CONNECTED'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED = 'usual.event.bluetooth.remotedevice.ACL_CONNECTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED = 'usual.event.bluetooth.remotedevice.ACL_DISCONNECTED'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED = 'usual.event.bluetooth.remotedevice.ACL_DISCONNECTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE = 'usual.event.bluetooth.remotedevice.NAME_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE = 'usual.event.bluetooth.remotedevice.NAME_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE = 'usual.event.bluetooth.remotedevice.PAIR_STATE'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE = 'usual.event.bluetooth.remotedevice.PAIR_STATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE = 'usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE = 'usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT = 'usual.event.bluetooth.remotedevice.SDP_RESULT'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT = 'usual.event.bluetooth.remotedevice.SDP_RESULT'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE = 'usual.event.bluetooth.remotedevice.UUID_VALUE'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE = 'usual.event.bluetooth.remotedevice.UUID_VALUE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ = 'usual.event.bluetooth.remotedevice.PAIRING_REQ'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ = 'usual.event.bluetooth.remotedevice.PAIRING_REQ'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL = 'usual.event.bluetooth.remotedevice.PAIRING_CANCEL'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL = 'usual.event.bluetooth.remotedevice.PAIRING_CANCEL'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ = 'usual.event.bluetooth.remotedevice.CONNECT_REQ'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ = 'usual.event.bluetooth.remotedevice.CONNECT_REQ'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY = 'usual.event.bluetooth.remotedevice.CONNECT_REPLY'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY = 'usual.event.bluetooth.remotedevice.CONNECT_REPLY'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL = 'usual.event.bluetooth.remotedevice.CONNECT_CANCEL'<br>Differences: COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL = 'usual.event.bluetooth.remotedevice.CONNECT_CANCEL'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT = 'usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT'<br>Differences: COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT = 'usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE = 'usual.event.bluetooth.host.STATE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE = 'usual.event.bluetooth.host.STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE = 'usual.event.bluetooth.host.REQ_DISCOVERABLE'<br>Differences: COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE = 'usual.event.bluetooth.host.REQ_DISCOVERABLE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE = 'usual.event.bluetooth.host.REQ_ENABLE'<br>Differences: COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE = 'usual.event.bluetooth.host.REQ_ENABLE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE = 'usual.event.bluetooth.host.REQ_DISABLE'<br>Differences: COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE = 'usual.event.bluetooth.host.REQ_DISABLE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE = 'usual.event.bluetooth.host.SCAN_MODE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE = 'usual.event.bluetooth.host.SCAN_MODE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED = 'usual.event.bluetooth.host.DISCOVERY_STARTED'<br>Differences: COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED = 'usual.event.bluetooth.host.DISCOVERY_STARTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED = 'usual.event.bluetooth.host.DISCOVERY_FINISHED'<br>Differences: COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED = 'usual.event.bluetooth.host.DISCOVERY_FINISHED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE = 'usual.event.bluetooth.host.NAME_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE = 'usual.event.bluetooth.host.NAME_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE'<br>Differences: COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED = 'usual.event.nfc.action.ADAPTER_STATE_CHANGED'<br>Differences: COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED = 'usual.event.nfc.action.ADAPTER_STATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED = 'usual.event.nfc.action.RF_FIELD_ON_DETECTED'<br>Differences: COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED = 'usual.event.nfc.action.RF_FIELD_ON_DETECTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED = 'usual.event.nfc.action.RF_FIELD_OFF_DETECTED'<br>Differences: COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED = 'usual.event.nfc.action.RF_FIELD_OFF_DETECTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DISCHARGING = 'usual.event.DISCHARGING'<br>Differences: COMMON_EVENT_DISCHARGING = 'usual.event.DISCHARGING'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_CHARGING = 'usual.event.CHARGING'<br>Differences: COMMON_EVENT_CHARGING = 'usual.event.CHARGING'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED = 'usual.event.DEVICE_IDLE_MODE_CHANGED'<br>Differences: COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED = 'usual.event.DEVICE_IDLE_MODE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_CHARGE_IDLE_MODE_CHANGED = 'usual.event.CHARGE_IDLE_MODE_CHANGED'<br>Differences: COMMON_EVENT_CHARGE_IDLE_MODE_CHANGED = 'usual.event.CHARGE_IDLE_MODE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_POWER_SAVE_MODE_CHANGED = 'usual.event.POWER_SAVE_MODE_CHANGED'<br>Differences: COMMON_EVENT_POWER_SAVE_MODE_CHANGED = 'usual.event.POWER_SAVE_MODE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USER_ADDED = 'usual.event.USER_ADDED'<br>Differences: COMMON_EVENT_USER_ADDED = 'usual.event.USER_ADDED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USER_REMOVED = 'usual.event.USER_REMOVED'<br>Differences: COMMON_EVENT_USER_REMOVED = 'usual.event.USER_REMOVED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_ABILITY_ADDED = 'common.event.ABILITY_ADDED'<br>Differences: COMMON_EVENT_ABILITY_ADDED = 'common.event.ABILITY_ADDED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_ABILITY_REMOVED = 'common.event.ABILITY_REMOVED'<br>Differences: COMMON_EVENT_ABILITY_REMOVED = 'common.event.ABILITY_REMOVED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_ABILITY_UPDATED = 'common.event.ABILITY_UPDATED'<br>Differences: COMMON_EVENT_ABILITY_UPDATED = 'common.event.ABILITY_UPDATED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_LOCATION_MODE_STATE_CHANGED = 'usual.event.location.MODE_STATE_CHANGED'<br>Differences: COMMON_EVENT_LOCATION_MODE_STATE_CHANGED = 'usual.event.location.MODE_STATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_IVI_SLEEP = 'common.event.IVI_SLEEP'<br>Differences: COMMON_EVENT_IVI_SLEEP = 'common.event.IVI_SLEEP'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_IVI_PAUSE = 'common.event.IVI_PAUSE'<br>Differences: COMMON_EVENT_IVI_PAUSE = 'common.event.IVI_PAUSE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_IVI_STANDBY = 'common.event.IVI_STANDBY'<br>Differences: COMMON_EVENT_IVI_STANDBY = 'common.event.IVI_STANDBY'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_IVI_LASTMODE_SAVE = 'common.event.IVI_LASTMODE_SAVE'<br>Differences: COMMON_EVENT_IVI_LASTMODE_SAVE = 'common.event.IVI_LASTMODE_SAVE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_IVI_VOLTAGE_ABNORMAL = 'common.event.IVI_VOLTAGE_ABNORMAL'<br>Differences: COMMON_EVENT_IVI_VOLTAGE_ABNORMAL = 'common.event.IVI_VOLTAGE_ABNORMAL'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_IVI_HIGH_TEMPERATURE = 'common.event.IVI_HIGH_TEMPERATURE'<br>Differences: COMMON_EVENT_IVI_HIGH_TEMPERATURE = 'common.event.IVI_HIGH_TEMPERATURE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_IVI_EXTREME_TEMPERATURE = 'common.event.IVI_EXTREME_TEMPERATURE'<br>Differences: COMMON_EVENT_IVI_EXTREME_TEMPERATURE = 'common.event.IVI_EXTREME_TEMPERATURE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL = 'common.event.IVI_TEMPERATURE_ABNORMAL'<br>Differences: COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL = 'common.event.IVI_TEMPERATURE_ABNORMAL'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_IVI_VOLTAGE_RECOVERY = 'common.event.IVI_VOLTAGE_RECOVERY'<br>Differences: COMMON_EVENT_IVI_VOLTAGE_RECOVERY = 'common.event.IVI_VOLTAGE_RECOVERY'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_IVI_TEMPERATURE_RECOVERY = 'common.event.IVI_TEMPERATURE_RECOVERY'<br>Differences: COMMON_EVENT_IVI_TEMPERATURE_RECOVERY = 'common.event.IVI_TEMPERATURE_RECOVERY'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_IVI_ACTIVE = 'common.event.IVI_ACTIVE'<br>Differences: COMMON_EVENT_IVI_ACTIVE = 'common.event.IVI_ACTIVE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USB_STATE = 'usual.event.hardware.usb.action.USB_STATE'<br>Differences: COMMON_EVENT_USB_STATE = 'usual.event.hardware.usb.action.USB_STATE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USB_PORT_CHANGED = 'usual.event.hardware.usb.action.USB_PORT_CHANGED'<br>Differences: COMMON_EVENT_USB_PORT_CHANGED = 'usual.event.hardware.usb.action.USB_PORT_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USB_DEVICE_ATTACHED = 'usual.event.hardware.usb.action.USB_DEVICE_ATTACHED'<br>Differences: COMMON_EVENT_USB_DEVICE_ATTACHED = 'usual.event.hardware.usb.action.USB_DEVICE_ATTACHED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USB_DEVICE_DETACHED = 'usual.event.hardware.usb.action.USB_DEVICE_DETACHED'<br>Differences: COMMON_EVENT_USB_DEVICE_DETACHED = 'usual.event.hardware.usb.action.USB_DEVICE_DETACHED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USB_ACCESSORY_ATTACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED'<br>Differences: COMMON_EVENT_USB_ACCESSORY_ATTACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USB_ACCESSORY_DETACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED'<br>Differences: COMMON_EVENT_USB_ACCESSORY_DETACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DISK_REMOVED = 'usual.event.data.DISK_REMOVED'<br>Differences: COMMON_EVENT_DISK_REMOVED = 'usual.event.data.DISK_REMOVED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DISK_UNMOUNTED = 'usual.event.data.DISK_UNMOUNTED'<br>Differences: COMMON_EVENT_DISK_UNMOUNTED = 'usual.event.data.DISK_UNMOUNTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DISK_MOUNTED = 'usual.event.data.DISK_MOUNTED'<br>Differences: COMMON_EVENT_DISK_MOUNTED = 'usual.event.data.DISK_MOUNTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DISK_BAD_REMOVAL = 'usual.event.data.DISK_BAD_REMOVAL'<br>Differences: COMMON_EVENT_DISK_BAD_REMOVAL = 'usual.event.data.DISK_BAD_REMOVAL'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DISK_UNMOUNTABLE = 'usual.event.data.DISK_UNMOUNTABLE'<br>Differences: COMMON_EVENT_DISK_UNMOUNTABLE = 'usual.event.data.DISK_UNMOUNTABLE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_DISK_EJECT = 'usual.event.data.DISK_EJECT'<br>Differences: COMMON_EVENT_DISK_EJECT = 'usual.event.data.DISK_EJECT'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_VOLUME_REMOVED = 'usual.event.data.VOLUME_REMOVED'<br>Differences: COMMON_EVENT_VOLUME_REMOVED = 'usual.event.data.VOLUME_REMOVED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_VOLUME_UNMOUNTED = 'usual.event.data.VOLUME_UNMOUNTED'<br>Differences: COMMON_EVENT_VOLUME_UNMOUNTED = 'usual.event.data.VOLUME_UNMOUNTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_VOLUME_MOUNTED = 'usual.event.data.VOLUME_MOUNTED'<br>Differences: COMMON_EVENT_VOLUME_MOUNTED = 'usual.event.data.VOLUME_MOUNTED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_VOLUME_BAD_REMOVAL = 'usual.event.data.VOLUME_BAD_REMOVAL'<br>Differences: COMMON_EVENT_VOLUME_BAD_REMOVAL = 'usual.event.data.VOLUME_BAD_REMOVAL'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_VOLUME_EJECT = 'usual.event.data.VOLUME_EJECT'<br>Differences: COMMON_EVENT_VOLUME_EJECT = 'usual.event.data.VOLUME_EJECT'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED = 'usual.event.data.VISIBLE_ACCOUNTS_UPDATED'<br>Differences: COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED = 'usual.event.data.VISIBLE_ACCOUNTS_UPDATED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_ACCOUNT_DELETED = 'usual.event.data.ACCOUNT_DELETED'<br>Differences: COMMON_EVENT_ACCOUNT_DELETED = 'usual.event.data.ACCOUNT_DELETED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_FOUNDATION_READY = 'common.event.FOUNDATION_READY'<br>Differences: COMMON_EVENT_FOUNDATION_READY = 'common.event.FOUNDATION_READY'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_AIRPLANE_MODE_CHANGED = 'usual.event.AIRPLANE_MODE'<br>Differences: COMMON_EVENT_AIRPLANE_MODE_CHANGED = 'usual.event.AIRPLANE_MODE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_SPLIT_SCREEN = 'common.event.SPLIT_SCREEN'<br>Differences: COMMON_EVENT_SPLIT_SCREEN = 'common.event.SPLIT_SCREEN'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_SLOT_CHANGE = 'usual.event.SLOT_CHANGE'<br>Differences: COMMON_EVENT_SLOT_CHANGE = 'usual.event.SLOT_CHANGE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_SPN_INFO_CHANGED = 'usual.event.SPN_INFO_CHANGED'<br>Differences: COMMON_EVENT_SPN_INFO_CHANGED = 'usual.event.SPN_INFO_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_QUICK_FIX_APPLY_RESULT = 'usual.event.QUICK_FIX_APPLY_RESULT'<br>Differences: COMMON_EVENT_QUICK_FIX_APPLY_RESULT = 'usual.event.QUICK_FIX_APPLY_RESULT'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_QUICK_FIX_REVOKE_RESULT = 'usual.event.QUICK_FIX_REVOKE_RESULT'<br>Differences: COMMON_EVENT_QUICK_FIX_REVOKE_RESULT = 'usual.event.QUICK_FIX_REVOKE_RESULT'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_USER_INFO_UPDATED = 'usual.event.USER_INFO_UPDATED'<br>Differences: COMMON_EVENT_USER_INFO_UPDATED = 'usual.event.USER_INFO_UPDATED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_HTTP_PROXY_CHANGE = 'usual.event.HTTP_PROXY_CHANGE'<br>Differences: COMMON_EVENT_HTTP_PROXY_CHANGE = 'usual.event.HTTP_PROXY_CHANGE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_SIM_STATE_CHANGED = 'usual.event.SIM_STATE_CHANGED'<br>Differences: COMMON_EVENT_SIM_STATE_CHANGED = 'usual.event.SIM_STATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_CALL_STATE_CHANGED = 'usual.event.CALL_STATE_CHANGED'<br>Differences: COMMON_EVENT_CALL_STATE_CHANGED = 'usual.event.CALL_STATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_NETWORK_STATE_CHANGED = 'usual.event.NETWORK_STATE_CHANGED'<br>Differences: COMMON_EVENT_NETWORK_STATE_CHANGED = 'usual.event.NETWORK_STATE_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_SIGNAL_INFO_CHANGED = 'usual.event.SIGNAL_INFO_CHANGED'<br>Differences: COMMON_EVENT_SIGNAL_INFO_CHANGED = 'usual.event.SIGNAL_INFO_CHANGED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_SCREEN_UNLOCKED = 'usual.event.SCREEN_UNLOCKED'<br>Differences: COMMON_EVENT_SCREEN_UNLOCKED = 'usual.event.SCREEN_UNLOCKED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_SCREEN_LOCKED = 'usual.event.SCREEN_LOCKED'<br>Differences: COMMON_EVENT_SCREEN_LOCKED = 'usual.event.SCREEN_LOCKED'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: Support;<br>API declaration: COMMON_EVENT_CONNECTIVITY_CHANGE = 'usual.event.CONNECTIVITY_CHANGE'<br>Differences: COMMON_EVENT_CONNECTIVITY_CHANGE = 'usual.event.CONNECTIVITY_CHANGE'|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: commonEventManager;<br>API declaration: export type CommonEventData = _CommonEventData;<br>Differences: export type CommonEventData = _CommonEventData;|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: commonEventManager;<br>API declaration: export type CommonEventSubscriber = _CommonEventSubscriber;<br>Differences: export type CommonEventSubscriber = _CommonEventSubscriber;|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: commonEventManager;<br>API declaration: export type CommonEventSubscribeInfo = _CommonEventSubscribeInfo;<br>Differences: export type CommonEventSubscribeInfo = _CommonEventSubscribeInfo;|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: commonEventManager;<br>API declaration: export type CommonEventPublishData = _CommonEventPublishData;<br>Differences: export type CommonEventPublishData = _CommonEventPublishData;|api/@ohos.commonEventManager.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace deviceAttest<br>Differences: declare namespace deviceAttest|api/@ohos.deviceAttest.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace deviceInfo<br>Differences: declare namespace deviceInfo|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const deviceType: string;<br>Differences: const deviceType: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const manufacture: string;<br>Differences: const manufacture: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const brand: string;<br>Differences: const brand: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const marketName: string;<br>Differences: const marketName: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const productSeries: string;<br>Differences: const productSeries: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const productModel: string;<br>Differences: const productModel: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const softwareModel: string;<br>Differences: const softwareModel: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const hardwareModel: string;<br>Differences: const hardwareModel: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const hardwareProfile: string;<br>Differences: const hardwareProfile: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const serial: string;<br>Differences: const serial: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const bootloaderVersion: string;<br>Differences: const bootloaderVersion: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const abiList: string;<br>Differences: const abiList: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const securityPatchTag: string;<br>Differences: const securityPatchTag: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const displayVersion: string;<br>Differences: const displayVersion: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const incrementalVersion: string;<br>Differences: const incrementalVersion: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const osReleaseType: string;<br>Differences: const osReleaseType: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const osFullName: string;<br>Differences: const osFullName: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const majorVersion: number;<br>Differences: const majorVersion: number;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const seniorVersion: number;<br>Differences: const seniorVersion: number;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const featureVersion: number;<br>Differences: const featureVersion: number;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const buildVersion: number;<br>Differences: const buildVersion: number;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const sdkApiVersion: number;<br>Differences: const sdkApiVersion: number;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const firstApiVersion: number;<br>Differences: const firstApiVersion: number;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const versionId: string;<br>Differences: const versionId: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const buildType: string;<br>Differences: const buildType: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const buildUser: string;<br>Differences: const buildUser: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const buildHost: string;<br>Differences: const buildHost: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const buildTime: string;<br>Differences: const buildTime: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const buildRootHash: string;<br>Differences: const buildRootHash: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const udid: string;<br>Differences: const udid: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const distributionOSName: string;<br>Differences: const distributionOSName: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const distributionOSVersion: string;<br>Differences: const distributionOSVersion: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const distributionOSApiVersion: number;<br>Differences: const distributionOSApiVersion: number;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: const distributionOSReleaseType: string;<br>Differences: const distributionOSReleaseType: string;|api/@ohos.deviceInfo.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace emitter<br>Differences: declare namespace emitter|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: function on(event: InnerEvent, callback: Callback\<EventData>): void;<br>Differences: function on(event: InnerEvent, callback: Callback\<EventData>): void;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: function on(eventId: string, callback: Callback\<EventData>): void;<br>Differences: function on(eventId: string, callback: Callback\<EventData>): void;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: function once(event: InnerEvent, callback: Callback\<EventData>): void;<br>Differences: function once(event: InnerEvent, callback: Callback\<EventData>): void;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: function once(eventId: string, callback: Callback\<EventData>): void;<br>Differences: function once(eventId: string, callback: Callback\<EventData>): void;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: function off(eventId: number): void;<br>Differences: function off(eventId: number): void;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: function off(eventId: number, callback: Callback\<EventData>): void;<br>Differences: function off(eventId: number, callback: Callback\<EventData>): void;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: function off(eventId: string): void;<br>Differences: function off(eventId: string): void;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: function off(eventId: string, callback: Callback\<EventData>): void;<br>Differences: function off(eventId: string, callback: Callback\<EventData>): void;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: function emit(event: InnerEvent, data?: EventData): void;<br>Differences: function emit(event: InnerEvent, data?: EventData): void;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: function emit(eventId: string, data?: EventData): void;<br>Differences: function emit(eventId: string, data?: EventData): void;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: function emit(eventId: string, options: Options, data?: EventData): void;<br>Differences: function emit(eventId: string, options: Options, data?: EventData): void;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: function getListenerCount(eventId: number \| string): number;<br>Differences: function getListenerCount(eventId: number \| string): number;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: export interface EventData<br>Differences: export interface EventData|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: EventData;<br>API declaration: data?: {<br>            [key: string]: any;<br>        };<br>Differences: data?: {<br>            [key: string]: any;<br>        };|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: export interface InnerEvent<br>Differences: export interface InnerEvent|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: InnerEvent;<br>API declaration: eventId: number;<br>Differences: eventId: number;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: InnerEvent;<br>API declaration: priority?: EventPriority;<br>Differences: priority?: EventPriority;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: export enum EventPriority<br>Differences: export enum EventPriority|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: EventPriority;<br>API declaration: IMMEDIATE = 0<br>Differences: IMMEDIATE = 0|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: EventPriority;<br>API declaration: HIGH<br>Differences: HIGH|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: EventPriority;<br>API declaration: LOW<br>Differences: LOW|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: EventPriority;<br>API declaration: IDLE<br>Differences: IDLE|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: emitter;<br>API declaration: export interface Options<br>Differences: export interface Options|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: Options;<br>API declaration: priority?: EventPriority;<br>Differences: priority?: EventPriority;|api/@ohos.events.emitter.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace pasteboard<br>Differences: declare namespace pasteboard|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: const MAX_RECORD_NUM: number;<br>Differences: const MAX_RECORD_NUM: number;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: const MIMETYPE_TEXT_HTML: string;<br>Differences: const MIMETYPE_TEXT_HTML: string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: const MIMETYPE_TEXT_WANT: string;<br>Differences: const MIMETYPE_TEXT_WANT: string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: const MIMETYPE_TEXT_PLAIN: string;<br>Differences: const MIMETYPE_TEXT_PLAIN: string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: const MIMETYPE_TEXT_URI: string;<br>Differences: const MIMETYPE_TEXT_URI: string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: const MIMETYPE_PIXELMAP: string;<br>Differences: const MIMETYPE_PIXELMAP: string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: type ValueType = string \| image.PixelMap \| Want \| ArrayBuffer;<br>Differences: type ValueType = string \| image.PixelMap \| Want \| ArrayBuffer;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: function createHtmlData(htmlText: string): PasteData;<br>Differences: function createHtmlData(htmlText: string): PasteData;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: function createWantData(want: Want): PasteData;<br>Differences: function createWantData(want: Want): PasteData;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: function createPlainTextData(text: string): PasteData;<br>Differences: function createPlainTextData(text: string): PasteData;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: function createUriData(uri: string): PasteData;<br>Differences: function createUriData(uri: string): PasteData;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: function createData(mimeType: string, value: ValueType): PasteData;<br>Differences: function createData(mimeType: string, value: ValueType): PasteData;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: function createHtmlTextRecord(htmlText: string): PasteDataRecord;<br>Differences: function createHtmlTextRecord(htmlText: string): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: function createWantRecord(want: Want): PasteDataRecord;<br>Differences: function createWantRecord(want: Want): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: function createPlainTextRecord(text: string): PasteDataRecord;<br>Differences: function createPlainTextRecord(text: string): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: function createUriRecord(uri: string): PasteDataRecord;<br>Differences: function createUriRecord(uri: string): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: function createRecord(mimeType: string, value: ValueType): PasteDataRecord;<br>Differences: function createRecord(mimeType: string, value: ValueType): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: function getSystemPasteboard(): SystemPasteboard;<br>Differences: function getSystemPasteboard(): SystemPasteboard;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: enum ShareOption<br>Differences: enum ShareOption|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: ShareOption;<br>API declaration: INAPP<br>Differences: INAPP|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: ShareOption;<br>API declaration: LOCALDEVICE<br>Differences: LOCALDEVICE|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: ShareOption;<br>API declaration: CROSSDEVICE<br>Differences: CROSSDEVICE|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: interface PasteDataProperty<br>Differences: interface PasteDataProperty|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataProperty;<br>API declaration: additions: {<br>            [key: string]: object;<br>        };<br>Differences: additions: {<br>            [key: string]: object;<br>        };|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataProperty;<br>API declaration: readonly mimeTypes: Array\<string>;<br>Differences: readonly mimeTypes: Array\<string>;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataProperty;<br>API declaration: tag: string;<br>Differences: tag: string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataProperty;<br>API declaration: readonly timestamp: number;<br>Differences: readonly timestamp: number;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataProperty;<br>API declaration: localOnly: boolean;<br>Differences: localOnly: boolean;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataProperty;<br>API declaration: shareOption: ShareOption;<br>Differences: shareOption: ShareOption;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: interface PasteDataRecord<br>Differences: interface PasteDataRecord|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataRecord;<br>API declaration: htmlText: string;<br>Differences: htmlText: string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataRecord;<br>API declaration: want: Want;<br>Differences: want: Want;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataRecord;<br>API declaration: mimeType: string;<br>Differences: mimeType: string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataRecord;<br>API declaration: plainText: string;<br>Differences: plainText: string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataRecord;<br>API declaration: uri: string;<br>Differences: uri: string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataRecord;<br>API declaration: pixelMap: image.PixelMap;<br>Differences: pixelMap: image.PixelMap;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataRecord;<br>API declaration: data: {<br>            [mimeType: string]: ArrayBuffer;<br>        };<br>Differences: data: {<br>            [mimeType: string]: ArrayBuffer;<br>        };|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataRecord;<br>API declaration: convertToText(callback: AsyncCallback\<string>): void;<br>Differences: convertToText(callback: AsyncCallback\<string>): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataRecord;<br>API declaration: convertToText(): Promise\<string>;<br>Differences: convertToText(): Promise\<string>;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteDataRecord;<br>API declaration: toPlainText(): string;<br>Differences: toPlainText(): string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: interface PasteData<br>Differences: interface PasteData|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: addHtmlRecord(htmlText: string): void;<br>Differences: addHtmlRecord(htmlText: string): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: addWantRecord(want: Want): void;<br>Differences: addWantRecord(want: Want): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: addRecord(record: PasteDataRecord): void;<br>Differences: addRecord(record: PasteDataRecord): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: addRecord(mimeType: string, value: ValueType): void;<br>Differences: addRecord(mimeType: string, value: ValueType): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: addTextRecord(text: string): void;<br>Differences: addTextRecord(text: string): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: addUriRecord(uri: string): void;<br>Differences: addUriRecord(uri: string): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: getMimeTypes(): Array\<string>;<br>Differences: getMimeTypes(): Array\<string>;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: getPrimaryHtml(): string;<br>Differences: getPrimaryHtml(): string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: getPrimaryWant(): Want;<br>Differences: getPrimaryWant(): Want;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: getPrimaryMimeType(): string;<br>Differences: getPrimaryMimeType(): string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: getPrimaryText(): string;<br>Differences: getPrimaryText(): string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: getPrimaryUri(): string;<br>Differences: getPrimaryUri(): string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: getPrimaryPixelMap(): image.PixelMap;<br>Differences: getPrimaryPixelMap(): image.PixelMap;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: getProperty(): PasteDataProperty;<br>Differences: getProperty(): PasteDataProperty;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: setProperty(property: PasteDataProperty): void;<br>Differences: setProperty(property: PasteDataProperty): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: getRecordAt(index: number): PasteDataRecord;<br>Differences: getRecordAt(index: number): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: getRecord(index: number): PasteDataRecord;<br>Differences: getRecord(index: number): PasteDataRecord;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: getRecordCount(): number;<br>Differences: getRecordCount(): number;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: getTag(): string;<br>Differences: getTag(): string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: hasMimeType(mimeType: string): boolean;<br>Differences: hasMimeType(mimeType: string): boolean;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: hasType(mimeType: string): boolean;<br>Differences: hasType(mimeType: string): boolean;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: removeRecordAt(index: number): boolean;<br>Differences: removeRecordAt(index: number): boolean;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: removeRecord(index: number): void;<br>Differences: removeRecord(index: number): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: replaceRecordAt(index: number, record: PasteDataRecord): boolean;<br>Differences: replaceRecordAt(index: number, record: PasteDataRecord): boolean;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: PasteData;<br>API declaration: replaceRecord(index: number, record: PasteDataRecord): void;<br>Differences: replaceRecord(index: number, record: PasteDataRecord): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: pasteboard;<br>API declaration: interface SystemPasteboard<br>Differences: interface SystemPasteboard|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: on(type: 'update', callback: () => void): void;<br>Differences: on(type: 'update', callback: () => void): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: off(type: 'update', callback?: () => void): void;<br>Differences: off(type: 'update', callback?: () => void): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: isRemoteData(): boolean;<br>Differences: isRemoteData(): boolean;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: getDataSource(): string;<br>Differences: getDataSource(): string;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: hasDataType(mimeType: string): boolean;<br>Differences: hasDataType(mimeType: string): boolean;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: clear(callback: AsyncCallback\<void>): void;<br>Differences: clear(callback: AsyncCallback\<void>): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: clear(): Promise\<void>;<br>Differences: clear(): Promise\<void>;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: clearData(callback: AsyncCallback\<void>): void;<br>Differences: clearData(callback: AsyncCallback\<void>): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: clearData(): Promise\<void>;<br>Differences: clearData(): Promise\<void>;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: clearDataSync(): void;<br>Differences: clearDataSync(): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: getPasteData(callback: AsyncCallback\<PasteData>): void;<br>Differences: getPasteData(callback: AsyncCallback\<PasteData>): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: getPasteData(): Promise\<PasteData>;<br>Differences: getPasteData(): Promise\<PasteData>;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: getData(callback: AsyncCallback\<PasteData>): void;<br>Differences: getData(callback: AsyncCallback\<PasteData>): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: getData(): Promise\<PasteData>;<br>Differences: getData(): Promise\<PasteData>;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: getDataSync(): PasteData;<br>Differences: getDataSync(): PasteData;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: hasPasteData(callback: AsyncCallback\<boolean>): void;<br>Differences: hasPasteData(callback: AsyncCallback\<boolean>): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: hasPasteData(): Promise\<boolean>;<br>Differences: hasPasteData(): Promise\<boolean>;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: hasData(callback: AsyncCallback\<boolean>): void;<br>Differences: hasData(callback: AsyncCallback\<boolean>): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: hasData(): Promise\<boolean>;<br>Differences: hasData(): Promise\<boolean>;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: hasDataSync(): boolean;<br>Differences: hasDataSync(): boolean;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: setPasteData(data: PasteData, callback: AsyncCallback\<void>): void;<br>Differences: setPasteData(data: PasteData, callback: AsyncCallback\<void>): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: setPasteData(data: PasteData): Promise\<void>;<br>Differences: setPasteData(data: PasteData): Promise\<void>;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: setData(data: PasteData, callback: AsyncCallback\<void>): void;<br>Differences: setData(data: PasteData, callback: AsyncCallback\<void>): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: setData(data: PasteData): Promise\<void>;<br>Differences: setData(data: PasteData): Promise\<void>;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: SystemPasteboard;<br>API declaration: setDataSync(data: PasteData): void;<br>Differences: setDataSync(data: PasteData): void;|api/@ohos.pasteboard.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace power<br>Differences: declare namespace power|api/@ohos.power.d.ts|
|New API|NA|Class name: power;<br>API declaration: function rebootDevice(reason: string): void;<br>Differences: function rebootDevice(reason: string): void;|api/@ohos.power.d.ts|
|New API|NA|Class name: power;<br>API declaration: function isScreenOn(callback: AsyncCallback\<boolean>): void;<br>Differences: function isScreenOn(callback: AsyncCallback\<boolean>): void;|api/@ohos.power.d.ts|
|New API|NA|Class name: power;<br>API declaration: function isScreenOn(): Promise\<boolean>;<br>Differences: function isScreenOn(): Promise\<boolean>;|api/@ohos.power.d.ts|
|New API|NA|Class name: power;<br>API declaration: function isActive(): boolean;<br>Differences: function isActive(): boolean;|api/@ohos.power.d.ts|
|New API|NA|Class name: power;<br>API declaration: function getPowerMode(): DevicePowerMode;<br>Differences: function getPowerMode(): DevicePowerMode;|api/@ohos.power.d.ts|
|New API|NA|Class name: power;<br>API declaration: function isStandby(): boolean;<br>Differences: function isStandby(): boolean;|api/@ohos.power.d.ts|
|New API|NA|Class name: power;<br>API declaration: export enum DevicePowerMode<br>Differences: export enum DevicePowerMode|api/@ohos.power.d.ts|
|New API|NA|Class name: DevicePowerMode;<br>API declaration: MODE_NORMAL = 600<br>Differences: MODE_NORMAL = 600|api/@ohos.power.d.ts|
|New API|NA|Class name: DevicePowerMode;<br>API declaration: MODE_POWER_SAVE<br>Differences: MODE_POWER_SAVE|api/@ohos.power.d.ts|
|New API|NA|Class name: DevicePowerMode;<br>API declaration: MODE_PERFORMANCE<br>Differences: MODE_PERFORMANCE|api/@ohos.power.d.ts|
|New API|NA|Class name: DevicePowerMode;<br>API declaration: MODE_EXTREME_POWER_SAVE<br>Differences: MODE_EXTREME_POWER_SAVE|api/@ohos.power.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace print<br>Differences: declare namespace print|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: interface PrintTask<br>Differences: interface PrintTask|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintTask;<br>API declaration: on(type: 'block', callback: Callback\<void>): void;<br>Differences: on(type: 'block', callback: Callback\<void>): void;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintTask;<br>API declaration: on(type: 'succeed', callback: Callback\<void>): void;<br>Differences: on(type: 'succeed', callback: Callback\<void>): void;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintTask;<br>API declaration: on(type: 'fail', callback: Callback\<void>): void;<br>Differences: on(type: 'fail', callback: Callback\<void>): void;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintTask;<br>API declaration: on(type: 'cancel', callback: Callback\<void>): void;<br>Differences: on(type: 'cancel', callback: Callback\<void>): void;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintTask;<br>API declaration: off(type: 'block', callback?: Callback\<void>): void;<br>Differences: off(type: 'block', callback?: Callback\<void>): void;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintTask;<br>API declaration: off(type: 'succeed', callback?: Callback\<void>): void;<br>Differences: off(type: 'succeed', callback?: Callback\<void>): void;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintTask;<br>API declaration: off(type: 'fail', callback?: Callback\<void>): void;<br>Differences: off(type: 'fail', callback?: Callback\<void>): void;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintTask;<br>API declaration: off(type: 'cancel', callback?: Callback\<void>): void;<br>Differences: off(type: 'cancel', callback?: Callback\<void>): void;|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: interface PrintDocumentAdapter<br>Differences: interface PrintDocumentAdapter|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDocumentAdapter;<br>API declaration: onStartLayoutWrite(jobId: string, oldAttrs: PrintAttributes, newAttrs: PrintAttributes, fd: number, writeResultCallback: (jobId: string, writeResult: PrintFileCreationState) => void): void;<br>Differences: onStartLayoutWrite(jobId: string, oldAttrs: PrintAttributes, newAttrs: PrintAttributes, fd: number, writeResultCallback: (jobId: string, writeResult: PrintFileCreationState) => void): void;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDocumentAdapter;<br>API declaration: onJobStateChanged(jobId: string, state: PrintDocumentAdapterState): void;<br>Differences: onJobStateChanged(jobId: string, state: PrintDocumentAdapterState): void;|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: function print(files: Array\<string>, callback: AsyncCallback\<PrintTask>): void;<br>Differences: function print(files: Array\<string>, callback: AsyncCallback\<PrintTask>): void;|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: function print(files: Array\<string>): Promise\<PrintTask>;<br>Differences: function print(files: Array\<string>): Promise\<PrintTask>;|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: function print(files: Array\<string>, context: Context, callback: AsyncCallback\<PrintTask>): void;<br>Differences: function print(files: Array\<string>, context: Context, callback: AsyncCallback\<PrintTask>): void;|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: function print(files: Array\<string>, context: Context): Promise\<PrintTask>;<br>Differences: function print(files: Array\<string>, context: Context): Promise\<PrintTask>;|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: function print(jobName: string, printAdapter: PrintDocumentAdapter, printAttributes: PrintAttributes, context: Context): Promise\<PrintTask>;<br>Differences: function print(jobName: string, printAdapter: PrintDocumentAdapter, printAttributes: PrintAttributes, context: Context): Promise\<PrintTask>;|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: interface PrintAttributes<br>Differences: interface PrintAttributes|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintAttributes;<br>API declaration: copyNumber?: number;<br>Differences: copyNumber?: number;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintAttributes;<br>API declaration: pageRange?: PrintPageRange;<br>Differences: pageRange?: PrintPageRange;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintAttributes;<br>API declaration: pageSize?: PrintPageSize \| PrintPageType;<br>Differences: pageSize?: PrintPageSize \| PrintPageType;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintAttributes;<br>API declaration: directionMode?: PrintDirectionMode;<br>Differences: directionMode?: PrintDirectionMode;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintAttributes;<br>API declaration: colorMode?: PrintColorMode;<br>Differences: colorMode?: PrintColorMode;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintAttributes;<br>API declaration: duplexMode?: PrintDuplexMode;<br>Differences: duplexMode?: PrintDuplexMode;|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: interface PrintPageRange<br>Differences: interface PrintPageRange|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageRange;<br>API declaration: startPage?: number;<br>Differences: startPage?: number;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageRange;<br>API declaration: endPage?: number;<br>Differences: endPage?: number;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageRange;<br>API declaration: pages?: Array\<number>;<br>Differences: pages?: Array\<number>;|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: interface PrintPageSize<br>Differences: interface PrintPageSize|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageSize;<br>API declaration: id: string;<br>Differences: id: string;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageSize;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageSize;<br>API declaration: width: number;<br>Differences: width: number;|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageSize;<br>API declaration: height: number;<br>Differences: height: number;|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: enum PrintDirectionMode<br>Differences: enum PrintDirectionMode|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDirectionMode;<br>API declaration: DIRECTION_MODE_AUTO = 0<br>Differences: DIRECTION_MODE_AUTO = 0|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDirectionMode;<br>API declaration: DIRECTION_MODE_PORTRAIT = 1<br>Differences: DIRECTION_MODE_PORTRAIT = 1|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDirectionMode;<br>API declaration: DIRECTION_MODE_LANDSCAPE = 2<br>Differences: DIRECTION_MODE_LANDSCAPE = 2|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: enum PrintColorMode<br>Differences: enum PrintColorMode|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintColorMode;<br>API declaration: COLOR_MODE_MONOCHROME = 0<br>Differences: COLOR_MODE_MONOCHROME = 0|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintColorMode;<br>API declaration: COLOR_MODE_COLOR = 1<br>Differences: COLOR_MODE_COLOR = 1|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: enum PrintDuplexMode<br>Differences: enum PrintDuplexMode|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDuplexMode;<br>API declaration: DUPLEX_MODE_NONE = 0<br>Differences: DUPLEX_MODE_NONE = 0|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDuplexMode;<br>API declaration: DUPLEX_MODE_LONG_EDGE = 1<br>Differences: DUPLEX_MODE_LONG_EDGE = 1|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDuplexMode;<br>API declaration: DUPLEX_MODE_SHORT_EDGE = 2<br>Differences: DUPLEX_MODE_SHORT_EDGE = 2|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: enum PrintPageType<br>Differences: enum PrintPageType|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageType;<br>API declaration: PAGE_ISO_A3 = 0<br>Differences: PAGE_ISO_A3 = 0|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageType;<br>API declaration: PAGE_ISO_A4 = 1<br>Differences: PAGE_ISO_A4 = 1|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageType;<br>API declaration: PAGE_ISO_A5 = 2<br>Differences: PAGE_ISO_A5 = 2|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageType;<br>API declaration: PAGE_JIS_B5 = 3<br>Differences: PAGE_JIS_B5 = 3|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageType;<br>API declaration: PAGE_ISO_C5 = 4<br>Differences: PAGE_ISO_C5 = 4|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageType;<br>API declaration: PAGE_ISO_DL = 5<br>Differences: PAGE_ISO_DL = 5|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageType;<br>API declaration: PAGE_LETTER = 6<br>Differences: PAGE_LETTER = 6|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageType;<br>API declaration: PAGE_LEGAL = 7<br>Differences: PAGE_LEGAL = 7|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageType;<br>API declaration: PAGE_PHOTO_4X6 = 8<br>Differences: PAGE_PHOTO_4X6 = 8|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageType;<br>API declaration: PAGE_PHOTO_5X7 = 9<br>Differences: PAGE_PHOTO_5X7 = 9|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageType;<br>API declaration: PAGE_INT_DL_ENVELOPE = 10<br>Differences: PAGE_INT_DL_ENVELOPE = 10|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintPageType;<br>API declaration: PAGE_B_TABLOID = 11<br>Differences: PAGE_B_TABLOID = 11|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: enum PrintDocumentAdapterState<br>Differences: enum PrintDocumentAdapterState|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDocumentAdapterState;<br>API declaration: PREVIEW_DESTROY = 0<br>Differences: PREVIEW_DESTROY = 0|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDocumentAdapterState;<br>API declaration: PRINT_TASK_SUCCEED = 1<br>Differences: PRINT_TASK_SUCCEED = 1|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDocumentAdapterState;<br>API declaration: PRINT_TASK_FAIL = 2<br>Differences: PRINT_TASK_FAIL = 2|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDocumentAdapterState;<br>API declaration: PRINT_TASK_CANCEL = 3<br>Differences: PRINT_TASK_CANCEL = 3|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintDocumentAdapterState;<br>API declaration: PRINT_TASK_BLOCK = 4<br>Differences: PRINT_TASK_BLOCK = 4|api/@ohos.print.d.ts|
|New API|NA|Class name: print;<br>API declaration: enum PrintFileCreationState<br>Differences: enum PrintFileCreationState|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintFileCreationState;<br>API declaration: PRINT_FILE_CREATED = 0<br>Differences: PRINT_FILE_CREATED = 0|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintFileCreationState;<br>API declaration: PRINT_FILE_CREATION_FAILED = 1<br>Differences: PRINT_FILE_CREATION_FAILED = 1|api/@ohos.print.d.ts|
|New API|NA|Class name: PrintFileCreationState;<br>API declaration: PRINT_FILE_CREATED_UNRENDERED = 2<br>Differences: PRINT_FILE_CREATED_UNRENDERED = 2|api/@ohos.print.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace request<br>Differences: declare namespace request|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const EXCEPTION_PERMISSION: number;<br>Differences: const EXCEPTION_PERMISSION: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const EXCEPTION_PARAMCHECK: number;<br>Differences: const EXCEPTION_PARAMCHECK: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const EXCEPTION_UNSUPPORTED: number;<br>Differences: const EXCEPTION_UNSUPPORTED: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const EXCEPTION_FILEIO: number;<br>Differences: const EXCEPTION_FILEIO: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const EXCEPTION_FILEPATH: number;<br>Differences: const EXCEPTION_FILEPATH: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const EXCEPTION_SERVICE: number;<br>Differences: const EXCEPTION_SERVICE: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const EXCEPTION_OTHERS: number;<br>Differences: const EXCEPTION_OTHERS: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const NETWORK_MOBILE: number;<br>Differences: const NETWORK_MOBILE: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const NETWORK_WIFI: number;<br>Differences: const NETWORK_WIFI: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const ERROR_CANNOT_RESUME: number;<br>Differences: const ERROR_CANNOT_RESUME: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const ERROR_DEVICE_NOT_FOUND: number;<br>Differences: const ERROR_DEVICE_NOT_FOUND: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const ERROR_FILE_ALREADY_EXISTS: number;<br>Differences: const ERROR_FILE_ALREADY_EXISTS: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const ERROR_FILE_ERROR: number;<br>Differences: const ERROR_FILE_ERROR: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const ERROR_HTTP_DATA_ERROR: number;<br>Differences: const ERROR_HTTP_DATA_ERROR: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const ERROR_INSUFFICIENT_SPACE: number;<br>Differences: const ERROR_INSUFFICIENT_SPACE: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const ERROR_TOO_MANY_REDIRECTS: number;<br>Differences: const ERROR_TOO_MANY_REDIRECTS: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const ERROR_UNHANDLED_HTTP_CODE: number;<br>Differences: const ERROR_UNHANDLED_HTTP_CODE: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const ERROR_UNKNOWN: number;<br>Differences: const ERROR_UNKNOWN: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const ERROR_OFFLINE: number;<br>Differences: const ERROR_OFFLINE: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const ERROR_UNSUPPORTED_NETWORK_TYPE: number;<br>Differences: const ERROR_UNSUPPORTED_NETWORK_TYPE: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const PAUSED_QUEUED_FOR_WIFI: number;<br>Differences: const PAUSED_QUEUED_FOR_WIFI: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const PAUSED_WAITING_FOR_NETWORK: number;<br>Differences: const PAUSED_WAITING_FOR_NETWORK: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const PAUSED_WAITING_TO_RETRY: number;<br>Differences: const PAUSED_WAITING_TO_RETRY: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const PAUSED_BY_USER: number;<br>Differences: const PAUSED_BY_USER: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const PAUSED_UNKNOWN: number;<br>Differences: const PAUSED_UNKNOWN: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const SESSION_SUCCESSFUL: number;<br>Differences: const SESSION_SUCCESSFUL: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const SESSION_RUNNING: number;<br>Differences: const SESSION_RUNNING: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const SESSION_PENDING: number;<br>Differences: const SESSION_PENDING: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const SESSION_PAUSED: number;<br>Differences: const SESSION_PAUSED: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: const SESSION_FAILED: number;<br>Differences: const SESSION_FAILED: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: function download(config: DownloadConfig, callback: AsyncCallback\<DownloadTask>): void;<br>Differences: function download(config: DownloadConfig, callback: AsyncCallback\<DownloadTask>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: function download(config: DownloadConfig): Promise\<DownloadTask>;<br>Differences: function download(config: DownloadConfig): Promise\<DownloadTask>;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: function downloadFile(context: BaseContext, config: DownloadConfig, callback: AsyncCallback\<DownloadTask>): void;<br>Differences: function downloadFile(context: BaseContext, config: DownloadConfig, callback: AsyncCallback\<DownloadTask>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: function downloadFile(context: BaseContext, config: DownloadConfig): Promise\<DownloadTask>;<br>Differences: function downloadFile(context: BaseContext, config: DownloadConfig): Promise\<DownloadTask>;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: function upload(config: UploadConfig, callback: AsyncCallback\<UploadTask>): void;<br>Differences: function upload(config: UploadConfig, callback: AsyncCallback\<UploadTask>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: function upload(config: UploadConfig): Promise\<UploadTask>;<br>Differences: function upload(config: UploadConfig): Promise\<UploadTask>;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: function uploadFile(context: BaseContext, config: UploadConfig, callback: AsyncCallback\<UploadTask>): void;<br>Differences: function uploadFile(context: BaseContext, config: UploadConfig, callback: AsyncCallback\<UploadTask>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: function uploadFile(context: BaseContext, config: UploadConfig): Promise\<UploadTask>;<br>Differences: function uploadFile(context: BaseContext, config: UploadConfig): Promise\<UploadTask>;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: interface DownloadConfig<br>Differences: interface DownloadConfig|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadConfig;<br>API declaration: url: string;<br>Differences: url: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadConfig;<br>API declaration: header?: Object;<br>Differences: header?: Object;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadConfig;<br>API declaration: enableMetered?: boolean;<br>Differences: enableMetered?: boolean;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadConfig;<br>API declaration: enableRoaming?: boolean;<br>Differences: enableRoaming?: boolean;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadConfig;<br>API declaration: description?: string;<br>Differences: description?: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadConfig;<br>API declaration: networkType?: number;<br>Differences: networkType?: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadConfig;<br>API declaration: filePath?: string;<br>Differences: filePath?: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadConfig;<br>API declaration: title?: string;<br>Differences: title?: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadConfig;<br>API declaration: background?: boolean;<br>Differences: background?: boolean;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: interface DownloadInfo<br>Differences: interface DownloadInfo|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadInfo;<br>API declaration: description: string;<br>Differences: description: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadInfo;<br>API declaration: downloadedBytes: number;<br>Differences: downloadedBytes: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadInfo;<br>API declaration: downloadId: number;<br>Differences: downloadId: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadInfo;<br>API declaration: failedReason: number;<br>Differences: failedReason: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadInfo;<br>API declaration: fileName: string;<br>Differences: fileName: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadInfo;<br>API declaration: filePath: string;<br>Differences: filePath: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadInfo;<br>API declaration: pausedReason: number;<br>Differences: pausedReason: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadInfo;<br>API declaration: status: number;<br>Differences: status: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadInfo;<br>API declaration: targetURI: string;<br>Differences: targetURI: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadInfo;<br>API declaration: downloadTitle: string;<br>Differences: downloadTitle: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadInfo;<br>API declaration: downloadTotalBytes: number;<br>Differences: downloadTotalBytes: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: interface DownloadTask<br>Differences: interface DownloadTask|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: on(type: 'progress', callback: (receivedSize: number, totalSize: number) => void): void;<br>Differences: on(type: 'progress', callback: (receivedSize: number, totalSize: number) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: off(type: 'progress', callback?: (receivedSize: number, totalSize: number) => void): void;<br>Differences: off(type: 'progress', callback?: (receivedSize: number, totalSize: number) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>Differences: on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>Differences: on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>Differences: on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>Differences: off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>Differences: off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>Differences: off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: on(type: 'fail', callback: (err: number) => void): void;<br>Differences: on(type: 'fail', callback: (err: number) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: off(type: 'fail', callback?: (err: number) => void): void;<br>Differences: off(type: 'fail', callback?: (err: number) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: remove(callback: AsyncCallback\<boolean>): void;<br>Differences: remove(callback: AsyncCallback\<boolean>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: remove(): Promise\<boolean>;<br>Differences: remove(): Promise\<boolean>;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: pause(callback: AsyncCallback\<void>): void;<br>Differences: pause(callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: pause(): Promise\<void>;<br>Differences: pause(): Promise\<void>;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: resume(callback: AsyncCallback\<void>): void;<br>Differences: resume(callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: resume(): Promise\<void>;<br>Differences: resume(): Promise\<void>;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: query(callback: AsyncCallback\<DownloadInfo>): void;<br>Differences: query(callback: AsyncCallback\<DownloadInfo>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: query(): Promise\<DownloadInfo>;<br>Differences: query(): Promise\<DownloadInfo>;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: queryMimeType(callback: AsyncCallback\<string>): void;<br>Differences: queryMimeType(callback: AsyncCallback\<string>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: queryMimeType(): Promise\<string>;<br>Differences: queryMimeType(): Promise\<string>;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: delete(callback: AsyncCallback\<boolean>): void;<br>Differences: delete(callback: AsyncCallback\<boolean>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: delete(): Promise\<boolean>;<br>Differences: delete(): Promise\<boolean>;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: suspend(callback: AsyncCallback\<boolean>): void;<br>Differences: suspend(callback: AsyncCallback\<boolean>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: suspend(): Promise\<boolean>;<br>Differences: suspend(): Promise\<boolean>;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: restore(callback: AsyncCallback\<boolean>): void;<br>Differences: restore(callback: AsyncCallback\<boolean>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: restore(): Promise\<boolean>;<br>Differences: restore(): Promise\<boolean>;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: getTaskInfo(callback: AsyncCallback\<DownloadInfo>): void;<br>Differences: getTaskInfo(callback: AsyncCallback\<DownloadInfo>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: getTaskInfo(): Promise\<DownloadInfo>;<br>Differences: getTaskInfo(): Promise\<DownloadInfo>;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: getTaskMimeType(callback: AsyncCallback\<string>): void;<br>Differences: getTaskMimeType(callback: AsyncCallback\<string>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: DownloadTask;<br>API declaration: getTaskMimeType(): Promise\<string>;<br>Differences: getTaskMimeType(): Promise\<string>;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: interface File<br>Differences: interface File|api/@ohos.request.d.ts|
|New API|NA|Class name: File;<br>API declaration: filename: string;<br>Differences: filename: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: File;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: File;<br>API declaration: uri: string;<br>Differences: uri: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: File;<br>API declaration: type: string;<br>Differences: type: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: interface RequestData<br>Differences: interface RequestData|api/@ohos.request.d.ts|
|New API|NA|Class name: RequestData;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: RequestData;<br>API declaration: value: string;<br>Differences: value: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: interface UploadConfig<br>Differences: interface UploadConfig|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadConfig;<br>API declaration: url: string;<br>Differences: url: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadConfig;<br>API declaration: header: Object;<br>Differences: header: Object;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadConfig;<br>API declaration: method: string;<br>Differences: method: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadConfig;<br>API declaration: index?: number;<br>Differences: index?: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadConfig;<br>API declaration: begins?: number;<br>Differences: begins?: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadConfig;<br>API declaration: ends?: number;<br>Differences: ends?: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadConfig;<br>API declaration: files: Array\<File>;<br>Differences: files: Array\<File>;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadConfig;<br>API declaration: data: Array\<RequestData>;<br>Differences: data: Array\<RequestData>;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: interface TaskState<br>Differences: interface TaskState|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskState;<br>API declaration: path: string;<br>Differences: path: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskState;<br>API declaration: responseCode: number;<br>Differences: responseCode: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskState;<br>API declaration: message: string;<br>Differences: message: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: interface UploadTask<br>Differences: interface UploadTask|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadTask;<br>API declaration: on(type: 'progress', callback: (uploadedSize: number, totalSize: number) => void): void;<br>Differences: on(type: 'progress', callback: (uploadedSize: number, totalSize: number) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadTask;<br>API declaration: off(type: 'progress', callback?: (uploadedSize: number, totalSize: number) => void): void;<br>Differences: off(type: 'progress', callback?: (uploadedSize: number, totalSize: number) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadTask;<br>API declaration: on(type: 'headerReceive', callback: (header: object) => void): void;<br>Differences: on(type: 'headerReceive', callback: (header: object) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadTask;<br>API declaration: off(type: 'headerReceive', callback?: (header: object) => void): void;<br>Differences: off(type: 'headerReceive', callback?: (header: object) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadTask;<br>API declaration: on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;<br>Differences: on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadTask;<br>API declaration: on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;<br>Differences: on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadTask;<br>API declaration: off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;<br>Differences: off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadTask;<br>API declaration: off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;<br>Differences: off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadTask;<br>API declaration: remove(callback: AsyncCallback\<boolean>): void;<br>Differences: remove(callback: AsyncCallback\<boolean>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadTask;<br>API declaration: remove(): Promise\<boolean>;<br>Differences: remove(): Promise\<boolean>;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadTask;<br>API declaration: delete(callback: AsyncCallback\<boolean>): void;<br>Differences: delete(callback: AsyncCallback\<boolean>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: UploadTask;<br>API declaration: delete(): Promise\<boolean>;<br>Differences: delete(): Promise\<boolean>;|api/@ohos.request.d.ts|
|New API|NA|Class name: request;<br>API declaration: namespace agent<br>Differences: namespace agent|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: enum Action<br>Differences: enum Action|api/@ohos.request.d.ts|
|New API|NA|Class name: Action;<br>API declaration: DOWNLOAD<br>Differences: DOWNLOAD|api/@ohos.request.d.ts|
|New API|NA|Class name: Action;<br>API declaration: UPLOAD<br>Differences: UPLOAD|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: enum Mode<br>Differences: enum Mode|api/@ohos.request.d.ts|
|New API|NA|Class name: Mode;<br>API declaration: BACKGROUND<br>Differences: BACKGROUND|api/@ohos.request.d.ts|
|New API|NA|Class name: Mode;<br>API declaration: FOREGROUND<br>Differences: FOREGROUND|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: enum Network<br>Differences: enum Network|api/@ohos.request.d.ts|
|New API|NA|Class name: Network;<br>API declaration: ANY<br>Differences: ANY|api/@ohos.request.d.ts|
|New API|NA|Class name: Network;<br>API declaration: WIFI<br>Differences: WIFI|api/@ohos.request.d.ts|
|New API|NA|Class name: Network;<br>API declaration: CELLULAR<br>Differences: CELLULAR|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: enum BroadcastEvent<br>Differences: enum BroadcastEvent|api/@ohos.request.d.ts|
|New API|NA|Class name: BroadcastEvent;<br>API declaration: COMPLETE = 'ohos.request.event.COMPLETE'<br>Differences: COMPLETE = 'ohos.request.event.COMPLETE'|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: interface FileSpec<br>Differences: interface FileSpec|api/@ohos.request.d.ts|
|New API|NA|Class name: FileSpec;<br>API declaration: path: string;<br>Differences: path: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: FileSpec;<br>API declaration: mimeType?: string;<br>Differences: mimeType?: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: FileSpec;<br>API declaration: filename?: string;<br>Differences: filename?: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: FileSpec;<br>API declaration: extras?: object;<br>Differences: extras?: object;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: interface FormItem<br>Differences: interface FormItem|api/@ohos.request.d.ts|
|New API|NA|Class name: FormItem;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: FormItem;<br>API declaration: value: string \| FileSpec \| Array\<FileSpec>;<br>Differences: value: string \| FileSpec \| Array\<FileSpec>;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: interface Config<br>Differences: interface Config|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: action: Action;<br>Differences: action: Action;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: url: string;<br>Differences: url: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: title?: string;<br>Differences: title?: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: description?: string;<br>Differences: description?: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: mode?: Mode;<br>Differences: mode?: Mode;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: overwrite?: boolean;<br>Differences: overwrite?: boolean;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: method?: string;<br>Differences: method?: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: headers?: object;<br>Differences: headers?: object;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: data?: string \| Array\<FormItem>;<br>Differences: data?: string \| Array\<FormItem>;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: saveas?: string;<br>Differences: saveas?: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: network?: Network;<br>Differences: network?: Network;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: metered?: boolean;<br>Differences: metered?: boolean;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: roaming?: boolean;<br>Differences: roaming?: boolean;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: retry?: boolean;<br>Differences: retry?: boolean;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: redirect?: boolean;<br>Differences: redirect?: boolean;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: index?: number;<br>Differences: index?: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: begins?: number;<br>Differences: begins?: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: ends?: number;<br>Differences: ends?: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: gauge?: boolean;<br>Differences: gauge?: boolean;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: precise?: boolean;<br>Differences: precise?: boolean;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: token?: string;<br>Differences: token?: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: priority?: number;<br>Differences: priority?: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: Config;<br>API declaration: extras?: object;<br>Differences: extras?: object;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: enum State<br>Differences: enum State|api/@ohos.request.d.ts|
|New API|NA|Class name: State;<br>API declaration: INITIALIZED = 0x00<br>Differences: INITIALIZED = 0x00|api/@ohos.request.d.ts|
|New API|NA|Class name: State;<br>API declaration: WAITING = 0x10<br>Differences: WAITING = 0x10|api/@ohos.request.d.ts|
|New API|NA|Class name: State;<br>API declaration: RUNNING = 0x20<br>Differences: RUNNING = 0x20|api/@ohos.request.d.ts|
|New API|NA|Class name: State;<br>API declaration: RETRYING = 0x21<br>Differences: RETRYING = 0x21|api/@ohos.request.d.ts|
|New API|NA|Class name: State;<br>API declaration: PAUSED = 0x30<br>Differences: PAUSED = 0x30|api/@ohos.request.d.ts|
|New API|NA|Class name: State;<br>API declaration: STOPPED = 0x31<br>Differences: STOPPED = 0x31|api/@ohos.request.d.ts|
|New API|NA|Class name: State;<br>API declaration: COMPLETED = 0x40<br>Differences: COMPLETED = 0x40|api/@ohos.request.d.ts|
|New API|NA|Class name: State;<br>API declaration: FAILED = 0x41<br>Differences: FAILED = 0x41|api/@ohos.request.d.ts|
|New API|NA|Class name: State;<br>API declaration: REMOVED = 0x50<br>Differences: REMOVED = 0x50|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: interface Progress<br>Differences: interface Progress|api/@ohos.request.d.ts|
|New API|NA|Class name: Progress;<br>API declaration: readonly state: State;<br>Differences: readonly state: State;|api/@ohos.request.d.ts|
|New API|NA|Class name: Progress;<br>API declaration: readonly index: number;<br>Differences: readonly index: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: Progress;<br>API declaration: readonly processed: number;<br>Differences: readonly processed: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: Progress;<br>API declaration: readonly sizes: Array\<number>;<br>Differences: readonly sizes: Array\<number>;|api/@ohos.request.d.ts|
|New API|NA|Class name: Progress;<br>API declaration: readonly extras?: object;<br>Differences: readonly extras?: object;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: enum Faults<br>Differences: enum Faults|api/@ohos.request.d.ts|
|New API|NA|Class name: Faults;<br>API declaration: OTHERS = 0xFF<br>Differences: OTHERS = 0xFF|api/@ohos.request.d.ts|
|New API|NA|Class name: Faults;<br>API declaration: DISCONNECTED = 0x00<br>Differences: DISCONNECTED = 0x00|api/@ohos.request.d.ts|
|New API|NA|Class name: Faults;<br>API declaration: TIMEOUT = 0x10<br>Differences: TIMEOUT = 0x10|api/@ohos.request.d.ts|
|New API|NA|Class name: Faults;<br>API declaration: PROTOCOL = 0x20<br>Differences: PROTOCOL = 0x20|api/@ohos.request.d.ts|
|New API|NA|Class name: Faults;<br>API declaration: FSIO = 0x40<br>Differences: FSIO = 0x40|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: interface Filter<br>Differences: interface Filter|api/@ohos.request.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: before?: number;<br>Differences: before?: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: after?: number;<br>Differences: after?: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: state?: State;<br>Differences: state?: State;|api/@ohos.request.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: action?: Action;<br>Differences: action?: Action;|api/@ohos.request.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: mode?: Mode;<br>Differences: mode?: Mode;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: interface TaskInfo<br>Differences: interface TaskInfo|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly saveas?: string;<br>Differences: readonly saveas?: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly url?: string;<br>Differences: readonly url?: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly data?: string \| Array\<FormItem>;<br>Differences: readonly data?: string \| Array\<FormItem>;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly tid: string;<br>Differences: readonly tid: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly title: string;<br>Differences: readonly title: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly description: string;<br>Differences: readonly description: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly action: Action;<br>Differences: readonly action: Action;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly mode: Mode;<br>Differences: readonly mode: Mode;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly priority: number;<br>Differences: readonly priority: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly mimeType: string;<br>Differences: readonly mimeType: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly progress: Progress;<br>Differences: readonly progress: Progress;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly gauge: boolean;<br>Differences: readonly gauge: boolean;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly ctime: number;<br>Differences: readonly ctime: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly mtime: number;<br>Differences: readonly mtime: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly retry: boolean;<br>Differences: readonly retry: boolean;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly tries: number;<br>Differences: readonly tries: number;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly faults: Faults;<br>Differences: readonly faults: Faults;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly reason: string;<br>Differences: readonly reason: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: readonly extras?: object;<br>Differences: readonly extras?: object;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: interface Task<br>Differences: interface Task|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: readonly tid: string;<br>Differences: readonly tid: string;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: config: Config;<br>Differences: config: Config;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: on(event: 'progress', callback: (progress: Progress) => void): void;<br>Differences: on(event: 'progress', callback: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: off(event: 'progress', callback?: (progress: Progress) => void): void;<br>Differences: off(event: 'progress', callback?: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: on(event: 'completed', callback: (progress: Progress) => void): void;<br>Differences: on(event: 'completed', callback: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: off(event: 'completed', callback?: (progress: Progress) => void): void;<br>Differences: off(event: 'completed', callback?: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: on(event: 'failed', callback: (progress: Progress) => void): void;<br>Differences: on(event: 'failed', callback: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: off(event: 'failed', callback?: (progress: Progress) => void): void;<br>Differences: off(event: 'failed', callback?: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: on(event: 'pause', callback: (progress: Progress) => void): void;<br>Differences: on(event: 'pause', callback: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: off(event: 'pause', callback?: (progress: Progress) => void): void;<br>Differences: off(event: 'pause', callback?: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: on(event: 'resume', callback: (progress: Progress) => void): void;<br>Differences: on(event: 'resume', callback: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: off(event: 'resume', callback?: (progress: Progress) => void): void;<br>Differences: off(event: 'resume', callback?: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: on(event: 'remove', callback: (progress: Progress) => void): void;<br>Differences: on(event: 'remove', callback: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: off(event: 'remove', callback?: (progress: Progress) => void): void;<br>Differences: off(event: 'remove', callback?: (progress: Progress) => void): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: start(callback: AsyncCallback\<void>): void;<br>Differences: start(callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: start(): Promise\<void>;<br>Differences: start(): Promise\<void>;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: pause(callback: AsyncCallback\<void>): void;<br>Differences: pause(callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: pause(): Promise\<void>;<br>Differences: pause(): Promise\<void>;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: resume(callback: AsyncCallback\<void>): void;<br>Differences: resume(callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: resume(): Promise\<void>;<br>Differences: resume(): Promise\<void>;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: stop(callback: AsyncCallback\<void>): void;<br>Differences: stop(callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: Task;<br>API declaration: stop(): Promise\<void>;<br>Differences: stop(): Promise\<void>;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: function create(context: BaseContext, config: Config, callback: AsyncCallback\<Task>): void;<br>Differences: function create(context: BaseContext, config: Config, callback: AsyncCallback\<Task>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: function create(context: BaseContext, config: Config): Promise\<Task>;<br>Differences: function create(context: BaseContext, config: Config): Promise\<Task>;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: function getTask(context: BaseContext, id: string, token?: string): Promise\<Task>;<br>Differences: function getTask(context: BaseContext, id: string, token?: string): Promise\<Task>;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: function remove(id: string, callback: AsyncCallback\<void>): void;<br>Differences: function remove(id: string, callback: AsyncCallback\<void>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: function remove(id: string): Promise\<void>;<br>Differences: function remove(id: string): Promise\<void>;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: function show(id: string, callback: AsyncCallback\<TaskInfo>): void;<br>Differences: function show(id: string, callback: AsyncCallback\<TaskInfo>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: function show(id: string): Promise\<TaskInfo>;<br>Differences: function show(id: string): Promise\<TaskInfo>;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: function touch(id: string, token: string, callback: AsyncCallback\<TaskInfo>): void;<br>Differences: function touch(id: string, token: string, callback: AsyncCallback\<TaskInfo>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: function touch(id: string, token: string): Promise\<TaskInfo>;<br>Differences: function touch(id: string, token: string): Promise\<TaskInfo>;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: function search(callback: AsyncCallback\<Array\<string>>): void;<br>Differences: function search(callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: function search(filter: Filter, callback: AsyncCallback\<Array\<string>>): void;<br>Differences: function search(filter: Filter, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.request.d.ts|
|New API|NA|Class name: agent;<br>API declaration: function search(filter?: Filter): Promise\<Array\<string>>;<br>Differences: function search(filter?: Filter): Promise\<Array\<string>>;|api/@ohos.request.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace runningLock<br>Differences: declare namespace runningLock|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: runningLock;<br>API declaration: class RunningLock<br>Differences: class RunningLock|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: RunningLock;<br>API declaration: lock(timeout: number): void;<br>Differences: lock(timeout: number): void;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: RunningLock;<br>API declaration: hold(timeout: number): void;<br>Differences: hold(timeout: number): void;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: RunningLock;<br>API declaration: isUsed(): boolean;<br>Differences: isUsed(): boolean;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: RunningLock;<br>API declaration: isHolding(): boolean;<br>Differences: isHolding(): boolean;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: RunningLock;<br>API declaration: unlock(): void;<br>Differences: unlock(): void;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: RunningLock;<br>API declaration: unhold(): void;<br>Differences: unhold(): void;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: runningLock;<br>API declaration: export enum RunningLockType<br>Differences: export enum RunningLockType|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: RunningLockType;<br>API declaration: BACKGROUND = 1<br>Differences: BACKGROUND = 1|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: RunningLockType;<br>API declaration: PROXIMITY_SCREEN_CONTROL<br>Differences: PROXIMITY_SCREEN_CONTROL|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: runningLock;<br>API declaration: function isRunningLockTypeSupported(type: RunningLockType, callback: AsyncCallback\<boolean>): void;<br>Differences: function isRunningLockTypeSupported(type: RunningLockType, callback: AsyncCallback\<boolean>): void;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: runningLock;<br>API declaration: function isRunningLockTypeSupported(type: RunningLockType): Promise\<boolean>;<br>Differences: function isRunningLockTypeSupported(type: RunningLockType): Promise\<boolean>;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: runningLock;<br>API declaration: function isSupported(type: RunningLockType): boolean;<br>Differences: function isSupported(type: RunningLockType): boolean;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: runningLock;<br>API declaration: function createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback\<RunningLock>): void;<br>Differences: function createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback\<RunningLock>): void;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: runningLock;<br>API declaration: function createRunningLock(name: string, type: RunningLockType): Promise\<RunningLock>;<br>Differences: function createRunningLock(name: string, type: RunningLockType): Promise\<RunningLock>;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: runningLock;<br>API declaration: function create(name: string, type: RunningLockType, callback: AsyncCallback\<RunningLock>): void;<br>Differences: function create(name: string, type: RunningLockType, callback: AsyncCallback\<RunningLock>): void;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: runningLock;<br>API declaration: function create(name: string, type: RunningLockType): Promise\<RunningLock>;<br>Differences: function create(name: string, type: RunningLockType): Promise\<RunningLock>;|api/@ohos.runningLock.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace screenLock<br>Differences: declare namespace screenLock|api/@ohos.screenLock.d.ts|
|New API|NA|Class name: screenLock;<br>API declaration: function isScreenLocked(callback: AsyncCallback\<boolean>): void;<br>Differences: function isScreenLocked(callback: AsyncCallback\<boolean>): void;|api/@ohos.screenLock.d.ts|
|New API|NA|Class name: screenLock;<br>API declaration: function isScreenLocked(): Promise\<boolean>;<br>Differences: function isScreenLocked(): Promise\<boolean>;|api/@ohos.screenLock.d.ts|
|New API|NA|Class name: screenLock;<br>API declaration: function isSecureMode(callback: AsyncCallback\<boolean>): void;<br>Differences: function isSecureMode(callback: AsyncCallback\<boolean>): void;|api/@ohos.screenLock.d.ts|
|New API|NA|Class name: screenLock;<br>API declaration: function isSecureMode(): Promise\<boolean>;<br>Differences: function isSecureMode(): Promise\<boolean>;|api/@ohos.screenLock.d.ts|
|New API|NA|Class name: screenLock;<br>API declaration: function unlockScreen(callback: AsyncCallback\<void>): void;<br>Differences: function unlockScreen(callback: AsyncCallback\<void>): void;|api/@ohos.screenLock.d.ts|
|New API|NA|Class name: screenLock;<br>API declaration: function unlockScreen(): Promise\<void>;<br>Differences: function unlockScreen(): Promise\<void>;|api/@ohos.screenLock.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace settings<br>Differences: declare namespace settings|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: namespace domainName<br>Differences: namespace domainName|api/@ohos.settings.d.ts|
|New API|NA|Class name: domainName;<br>API declaration: const DEVICE_SHARED: string;<br>Differences: const DEVICE_SHARED: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: domainName;<br>API declaration: const USER_PROPERTY: string;<br>Differences: const USER_PROPERTY: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: namespace date<br>Differences: namespace date|api/@ohos.settings.d.ts|
|New API|NA|Class name: date;<br>API declaration: const DATE_FORMAT: string;<br>Differences: const DATE_FORMAT: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: date;<br>API declaration: const TIME_FORMAT: string;<br>Differences: const TIME_FORMAT: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: date;<br>API declaration: const AUTO_GAIN_TIME: string;<br>Differences: const AUTO_GAIN_TIME: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: date;<br>API declaration: const AUTO_GAIN_TIME_ZONE: string;<br>Differences: const AUTO_GAIN_TIME_ZONE: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: namespace display<br>Differences: namespace display|api/@ohos.settings.d.ts|
|New API|NA|Class name: display;<br>API declaration: const FONT_SCALE: string;<br>Differences: const FONT_SCALE: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: display;<br>API declaration: const SCREEN_BRIGHTNESS_STATUS: string;<br>Differences: const SCREEN_BRIGHTNESS_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: display;<br>API declaration: const AUTO_SCREEN_BRIGHTNESS: string;<br>Differences: const AUTO_SCREEN_BRIGHTNESS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: display;<br>API declaration: const AUTO_SCREEN_BRIGHTNESS_MODE: number;<br>Differences: const AUTO_SCREEN_BRIGHTNESS_MODE: number;|api/@ohos.settings.d.ts|
|New API|NA|Class name: display;<br>API declaration: const MANUAL_SCREEN_BRIGHTNESS_MODE: number;<br>Differences: const MANUAL_SCREEN_BRIGHTNESS_MODE: number;|api/@ohos.settings.d.ts|
|New API|NA|Class name: display;<br>API declaration: const SCREEN_OFF_TIMEOUT: string;<br>Differences: const SCREEN_OFF_TIMEOUT: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: display;<br>API declaration: const DEFAULT_SCREEN_ROTATION: string;<br>Differences: const DEFAULT_SCREEN_ROTATION: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: display;<br>API declaration: const ANIMATOR_DURATION_SCALE: string;<br>Differences: const ANIMATOR_DURATION_SCALE: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: display;<br>API declaration: const TRANSITION_ANIMATION_SCALE: string;<br>Differences: const TRANSITION_ANIMATION_SCALE: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: display;<br>API declaration: const WINDOW_ANIMATION_SCALE: string;<br>Differences: const WINDOW_ANIMATION_SCALE: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: display;<br>API declaration: const DISPLAY_INVERSION_STATUS: string;<br>Differences: const DISPLAY_INVERSION_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: namespace general<br>Differences: namespace general|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const SETUP_WIZARD_FINISHED: string;<br>Differences: const SETUP_WIZARD_FINISHED: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const END_BUTTON_ACTION: string;<br>Differences: const END_BUTTON_ACTION: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const ACCELEROMETER_ROTATION_STATUS: string;<br>Differences: const ACCELEROMETER_ROTATION_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const AIRPLANE_MODE_STATUS: string;<br>Differences: const AIRPLANE_MODE_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const DEVICE_PROVISION_STATUS: string;<br>Differences: const DEVICE_PROVISION_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const HDC_STATUS: string;<br>Differences: const HDC_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const BOOT_COUNTING: string;<br>Differences: const BOOT_COUNTING: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const CONTACT_METADATA_SYNC_STATUS: string;<br>Differences: const CONTACT_METADATA_SYNC_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const DEVELOPMENT_SETTINGS_STATUS: string;<br>Differences: const DEVELOPMENT_SETTINGS_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const DEVICE_NAME: string;<br>Differences: const DEVICE_NAME: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const USB_STORAGE_STATUS: string;<br>Differences: const USB_STORAGE_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const DEBUGGER_WAITING: string;<br>Differences: const DEBUGGER_WAITING: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const DEBUG_APP_PACKAGE: string;<br>Differences: const DEBUG_APP_PACKAGE: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const ACCESSIBILITY_STATUS: string;<br>Differences: const ACCESSIBILITY_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const ACTIVATED_ACCESSIBILITY_SERVICES: string;<br>Differences: const ACTIVATED_ACCESSIBILITY_SERVICES: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const GEOLOCATION_ORIGINS_ALLOWED: string;<br>Differences: const GEOLOCATION_ORIGINS_ALLOWED: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const SKIP_USE_HINTS: string;<br>Differences: const SKIP_USE_HINTS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: general;<br>API declaration: const TOUCH_EXPLORATION_STATUS: string;<br>Differences: const TOUCH_EXPLORATION_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: namespace input<br>Differences: namespace input|api/@ohos.settings.d.ts|
|New API|NA|Class name: input;<br>API declaration: const DEFAULT_INPUT_METHOD: string;<br>Differences: const DEFAULT_INPUT_METHOD: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: input;<br>API declaration: const ACTIVATED_INPUT_METHOD_SUB_MODE: string;<br>Differences: const ACTIVATED_INPUT_METHOD_SUB_MODE: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: input;<br>API declaration: const ACTIVATED_INPUT_METHODS: string;<br>Differences: const ACTIVATED_INPUT_METHODS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: input;<br>API declaration: const SELECTOR_VISIBILITY_FOR_INPUT_METHOD: string;<br>Differences: const SELECTOR_VISIBILITY_FOR_INPUT_METHOD: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: input;<br>API declaration: const AUTO_CAPS_TEXT_INPUT: string;<br>Differences: const AUTO_CAPS_TEXT_INPUT: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: input;<br>API declaration: const AUTO_PUNCTUATE_TEXT_INPUT: string;<br>Differences: const AUTO_PUNCTUATE_TEXT_INPUT: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: input;<br>API declaration: const AUTO_REPLACE_TEXT_INPUT: string;<br>Differences: const AUTO_REPLACE_TEXT_INPUT: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: input;<br>API declaration: const SHOW_PASSWORD_TEXT_INPUT: string;<br>Differences: const SHOW_PASSWORD_TEXT_INPUT: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: namespace network<br>Differences: namespace network|api/@ohos.settings.d.ts|
|New API|NA|Class name: network;<br>API declaration: const DATA_ROAMING_STATUS: string;<br>Differences: const DATA_ROAMING_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: network;<br>API declaration: const HTTP_PROXY_CFG: string;<br>Differences: const HTTP_PROXY_CFG: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: network;<br>API declaration: const NETWORK_PREFERENCE_USAGE: string;<br>Differences: const NETWORK_PREFERENCE_USAGE: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: namespace phone<br>Differences: namespace phone|api/@ohos.settings.d.ts|
|New API|NA|Class name: phone;<br>API declaration: const RTT_CALLING_STATUS: string;<br>Differences: const RTT_CALLING_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: namespace sound<br>Differences: namespace sound|api/@ohos.settings.d.ts|
|New API|NA|Class name: sound;<br>API declaration: const VIBRATE_WHILE_RINGING: string;<br>Differences: const VIBRATE_WHILE_RINGING: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: sound;<br>API declaration: const DEFAULT_ALARM_ALERT: string;<br>Differences: const DEFAULT_ALARM_ALERT: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: sound;<br>API declaration: const DTMF_TONE_TYPE_WHILE_DIALING: string;<br>Differences: const DTMF_TONE_TYPE_WHILE_DIALING: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: sound;<br>API declaration: const DTMF_TONE_WHILE_DIALING: string;<br>Differences: const DTMF_TONE_WHILE_DIALING: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: sound;<br>API declaration: const AFFECTED_MODE_RINGER_STREAMS: string;<br>Differences: const AFFECTED_MODE_RINGER_STREAMS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: sound;<br>API declaration: const AFFECTED_MUTE_STREAMS: string;<br>Differences: const AFFECTED_MUTE_STREAMS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: sound;<br>API declaration: const DEFAULT_NOTIFICATION_SOUND: string;<br>Differences: const DEFAULT_NOTIFICATION_SOUND: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: sound;<br>API declaration: const DEFAULT_RINGTONE: string;<br>Differences: const DEFAULT_RINGTONE: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: sound;<br>API declaration: const SOUND_EFFECTS_STATUS: string;<br>Differences: const SOUND_EFFECTS_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: sound;<br>API declaration: const VIBRATE_STATUS: string;<br>Differences: const VIBRATE_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: sound;<br>API declaration: const HAPTIC_FEEDBACK_STATUS: string;<br>Differences: const HAPTIC_FEEDBACK_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: namespace TTS<br>Differences: namespace TTS|api/@ohos.settings.d.ts|
|New API|NA|Class name: TTS;<br>API declaration: const DEFAULT_TTS_PITCH: string;<br>Differences: const DEFAULT_TTS_PITCH: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: TTS;<br>API declaration: const DEFAULT_TTS_RATE: string;<br>Differences: const DEFAULT_TTS_RATE: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: TTS;<br>API declaration: const DEFAULT_TTS_SYNTH: string;<br>Differences: const DEFAULT_TTS_SYNTH: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: TTS;<br>API declaration: const ENABLED_TTS_PLUGINS: string;<br>Differences: const ENABLED_TTS_PLUGINS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: namespace wireless<br>Differences: namespace wireless|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const BLUETOOTH_DISCOVER_ABILITY_STATUS: string;<br>Differences: const BLUETOOTH_DISCOVER_ABILITY_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const BLUETOOTH_DISCOVER_TIMEOUT: string;<br>Differences: const BLUETOOTH_DISCOVER_TIMEOUT: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const AIRPLANE_MODE_RADIOS: string;<br>Differences: const AIRPLANE_MODE_RADIOS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const BLUETOOTH_STATUS: string;<br>Differences: const BLUETOOTH_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const BLUETOOTH_RADIO: string;<br>Differences: const BLUETOOTH_RADIO: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const CELL_RADIO: string;<br>Differences: const CELL_RADIO: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const NFC_RADIO: string;<br>Differences: const NFC_RADIO: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const WIFI_RADIO: string;<br>Differences: const WIFI_RADIO: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const OWNER_LOCKDOWN_WIFI_CFG: string;<br>Differences: const OWNER_LOCKDOWN_WIFI_CFG: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const WIFI_DHCP_MAX_RETRY_COUNT: string;<br>Differences: const WIFI_DHCP_MAX_RETRY_COUNT: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const WIFI_TO_MOBILE_DATA_AWAKE_TIMEOUT: string;<br>Differences: const WIFI_TO_MOBILE_DATA_AWAKE_TIMEOUT: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const WIFI_STATUS: string;<br>Differences: const WIFI_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: wireless;<br>API declaration: const WIFI_WATCHDOG_STATUS: string;<br>Differences: const WIFI_WATCHDOG_STATUS: string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function getURI(name: string, callback: AsyncCallback\<object>): void;<br>Differences: function getURI(name: string, callback: AsyncCallback\<object>): void;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function getURI(name: string): Promise\<object>;<br>Differences: function getURI(name: string): Promise\<object>;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function getValue(dataAbilityHelper: DataAbilityHelper, name: string, callback: AsyncCallback\<object>): void;<br>Differences: function getValue(dataAbilityHelper: DataAbilityHelper, name: string, callback: AsyncCallback\<object>): void;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function getValue(dataAbilityHelper: DataAbilityHelper, name: string): Promise\<object>;<br>Differences: function getValue(dataAbilityHelper: DataAbilityHelper, name: string): Promise\<object>;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function getValue(context: Context, name: string, callback: AsyncCallback\<string>): void;<br>Differences: function getValue(context: Context, name: string, callback: AsyncCallback\<string>): void;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function getValue(context: Context, name: string): Promise\<string>;<br>Differences: function getValue(context: Context, name: string): Promise\<string>;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function getValue(context: Context, name: string, domainName: string): Promise\<string>;<br>Differences: function getValue(context: Context, name: string, domainName: string): Promise\<string>;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function setValue(context: Context, name: string, value: string, callback: AsyncCallback\<boolean>): void;<br>Differences: function setValue(context: Context, name: string, value: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function setValue(context: Context, name: string, value: string): Promise\<boolean>;<br>Differences: function setValue(context: Context, name: string, value: string): Promise\<boolean>;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function setValue(context: Context, name: string, value: string, domainName: string): Promise\<boolean>;<br>Differences: function setValue(context: Context, name: string, value: string, domainName: string): Promise\<boolean>;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function enableAirplaneMode(enable: boolean, callback: AsyncCallback\<void>): void;<br>Differences: function enableAirplaneMode(enable: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function enableAirplaneMode(enable: boolean): Promise\<void>;<br>Differences: function enableAirplaneMode(enable: boolean): Promise\<void>;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function canShowFloating(callback: AsyncCallback\<boolean>): void;<br>Differences: function canShowFloating(callback: AsyncCallback\<boolean>): void;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function canShowFloating(): Promise\<boolean>;<br>Differences: function canShowFloating(): Promise\<boolean>;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function getUriSync(name: string): string;<br>Differences: function getUriSync(name: string): string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function getValueSync(dataAbilityHelper: DataAbilityHelper, name: string, defValue: string): string;<br>Differences: function getValueSync(dataAbilityHelper: DataAbilityHelper, name: string, defValue: string): string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function getValueSync(context: Context, name: string, defValue: string): string;<br>Differences: function getValueSync(context: Context, name: string, defValue: string): string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function getValueSync(context: Context, name: string, defValue: string, domainName: string): string;<br>Differences: function getValueSync(context: Context, name: string, defValue: string, domainName: string): string;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function setValueSync(dataAbilityHelper: DataAbilityHelper, name: string, value: string): boolean;<br>Differences: function setValueSync(dataAbilityHelper: DataAbilityHelper, name: string, value: string): boolean;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function setValueSync(context: Context, name: string, value: string): boolean;<br>Differences: function setValueSync(context: Context, name: string, value: string): boolean;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function setValueSync(context: Context, name: string, value: string, domainName: string): boolean;<br>Differences: function setValueSync(context: Context, name: string, value: string, domainName: string): boolean;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function registerKeyObserver(context: Context, name: string, domainName: string, observer: AsyncCallback\<void>): boolean;<br>Differences: function registerKeyObserver(context: Context, name: string, domainName: string, observer: AsyncCallback\<void>): boolean;|api/@ohos.settings.d.ts|
|New API|NA|Class name: settings;<br>API declaration: function unregisterKeyObserver(context: Context, name: string, domainName: string): boolean;<br>Differences: function unregisterKeyObserver(context: Context, name: string, domainName: string): boolean;|api/@ohos.settings.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace systemDateTime<br>Differences: declare namespace systemDateTime|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getCurrentTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>Differences: function getCurrentTime(isNano: boolean, callback: AsyncCallback\<number>): void;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getCurrentTime(callback: AsyncCallback\<number>): void;<br>Differences: function getCurrentTime(callback: AsyncCallback\<number>): void;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getCurrentTime(isNano?: boolean): Promise\<number>;<br>Differences: function getCurrentTime(isNano?: boolean): Promise\<number>;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getTime(isNanoseconds?: boolean): number;<br>Differences: function getTime(isNanoseconds?: boolean): number;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getRealActiveTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>Differences: function getRealActiveTime(isNano: boolean, callback: AsyncCallback\<number>): void;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getRealActiveTime(callback: AsyncCallback\<number>): void;<br>Differences: function getRealActiveTime(callback: AsyncCallback\<number>): void;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getRealActiveTime(isNano?: boolean): Promise\<number>;<br>Differences: function getRealActiveTime(isNano?: boolean): Promise\<number>;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getRealTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>Differences: function getRealTime(isNano: boolean, callback: AsyncCallback\<number>): void;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getRealTime(callback: AsyncCallback\<number>): void;<br>Differences: function getRealTime(callback: AsyncCallback\<number>): void;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getRealTime(isNano?: boolean): Promise\<number>;<br>Differences: function getRealTime(isNano?: boolean): Promise\<number>;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: enum TimeType<br>Differences: enum TimeType|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: TimeType;<br>API declaration: STARTUP<br>Differences: STARTUP|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: TimeType;<br>API declaration: ACTIVE<br>Differences: ACTIVE|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getUptime(timeType: TimeType, isNanoseconds?: boolean): number;<br>Differences: function getUptime(timeType: TimeType, isNanoseconds?: boolean): number;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getDate(callback: AsyncCallback\<Date>): void;<br>Differences: function getDate(callback: AsyncCallback\<Date>): void;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getDate(): Promise\<Date>;<br>Differences: function getDate(): Promise\<Date>;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getTimezone(callback: AsyncCallback\<string>): void;<br>Differences: function getTimezone(callback: AsyncCallback\<string>): void;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getTimezone(): Promise\<string>;<br>Differences: function getTimezone(): Promise\<string>;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: systemDateTime;<br>API declaration: function getTimezoneSync(): string;<br>Differences: function getTimezoneSync(): string;|api/@ohos.systemDateTime.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace systemTime<br>Differences: declare namespace systemTime|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function setTime(time: number, callback: AsyncCallback\<void>): void;<br>Differences: function setTime(time: number, callback: AsyncCallback\<void>): void;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function setTime(time: number): Promise\<void>;<br>Differences: function setTime(time: number): Promise\<void>;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getCurrentTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>Differences: function getCurrentTime(isNano: boolean, callback: AsyncCallback\<number>): void;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getCurrentTime(callback: AsyncCallback\<number>): void;<br>Differences: function getCurrentTime(callback: AsyncCallback\<number>): void;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getCurrentTime(isNano?: boolean): Promise\<number>;<br>Differences: function getCurrentTime(isNano?: boolean): Promise\<number>;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getRealActiveTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>Differences: function getRealActiveTime(isNano: boolean, callback: AsyncCallback\<number>): void;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getRealActiveTime(callback: AsyncCallback\<number>): void;<br>Differences: function getRealActiveTime(callback: AsyncCallback\<number>): void;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getRealActiveTime(isNano?: boolean): Promise\<number>;<br>Differences: function getRealActiveTime(isNano?: boolean): Promise\<number>;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getRealTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>Differences: function getRealTime(isNano: boolean, callback: AsyncCallback\<number>): void;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getRealTime(callback: AsyncCallback\<number>): void;<br>Differences: function getRealTime(callback: AsyncCallback\<number>): void;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getRealTime(isNano?: boolean): Promise\<number>;<br>Differences: function getRealTime(isNano?: boolean): Promise\<number>;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function setDate(date: Date, callback: AsyncCallback\<void>): void;<br>Differences: function setDate(date: Date, callback: AsyncCallback\<void>): void;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function setDate(date: Date): Promise\<void>;<br>Differences: function setDate(date: Date): Promise\<void>;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getDate(callback: AsyncCallback\<Date>): void;<br>Differences: function getDate(callback: AsyncCallback\<Date>): void;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getDate(): Promise\<Date>;<br>Differences: function getDate(): Promise\<Date>;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function setTimezone(timezone: string, callback: AsyncCallback\<void>): void;<br>Differences: function setTimezone(timezone: string, callback: AsyncCallback\<void>): void;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function setTimezone(timezone: string): Promise\<void>;<br>Differences: function setTimezone(timezone: string): Promise\<void>;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getTimezone(callback: AsyncCallback\<string>): void;<br>Differences: function getTimezone(callback: AsyncCallback\<string>): void;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: systemTime;<br>API declaration: function getTimezone(): Promise\<string>;<br>Differences: function getTimezone(): Promise\<string>;|api/@ohos.systemTime.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace thermal<br>Differences: declare namespace thermal|api/@ohos.thermal.d.ts|
|New API|NA|Class name: thermal;<br>API declaration: export enum ThermalLevel<br>Differences: export enum ThermalLevel|api/@ohos.thermal.d.ts|
|New API|NA|Class name: ThermalLevel;<br>API declaration: COOL = 0<br>Differences: COOL = 0|api/@ohos.thermal.d.ts|
|New API|NA|Class name: ThermalLevel;<br>API declaration: NORMAL = 1<br>Differences: NORMAL = 1|api/@ohos.thermal.d.ts|
|New API|NA|Class name: ThermalLevel;<br>API declaration: WARM = 2<br>Differences: WARM = 2|api/@ohos.thermal.d.ts|
|New API|NA|Class name: ThermalLevel;<br>API declaration: HOT = 3<br>Differences: HOT = 3|api/@ohos.thermal.d.ts|
|New API|NA|Class name: ThermalLevel;<br>API declaration: OVERHEATED = 4<br>Differences: OVERHEATED = 4|api/@ohos.thermal.d.ts|
|New API|NA|Class name: ThermalLevel;<br>API declaration: WARNING = 5<br>Differences: WARNING = 5|api/@ohos.thermal.d.ts|
|New API|NA|Class name: ThermalLevel;<br>API declaration: EMERGENCY = 6<br>Differences: EMERGENCY = 6|api/@ohos.thermal.d.ts|
|New API|NA|Class name: ThermalLevel;<br>API declaration: ESCAPE = 7<br>Differences: ESCAPE = 7|api/@ohos.thermal.d.ts|
|New API|NA|Class name: thermal;<br>API declaration: function subscribeThermalLevel(callback: AsyncCallback\<ThermalLevel>): void;<br>Differences: function subscribeThermalLevel(callback: AsyncCallback\<ThermalLevel>): void;|api/@ohos.thermal.d.ts|
|New API|NA|Class name: thermal;<br>API declaration: function registerThermalLevelCallback(callback: Callback\<ThermalLevel>): void;<br>Differences: function registerThermalLevelCallback(callback: Callback\<ThermalLevel>): void;|api/@ohos.thermal.d.ts|
|New API|NA|Class name: thermal;<br>API declaration: function unsubscribeThermalLevel(callback?: AsyncCallback\<void>): void;<br>Differences: function unsubscribeThermalLevel(callback?: AsyncCallback\<void>): void;|api/@ohos.thermal.d.ts|
|New API|NA|Class name: thermal;<br>API declaration: function unregisterThermalLevelCallback(callback?: Callback\<void>): void;<br>Differences: function unregisterThermalLevelCallback(callback?: Callback\<void>): void;|api/@ohos.thermal.d.ts|
|New API|NA|Class name: thermal;<br>API declaration: function getThermalLevel(): ThermalLevel;<br>Differences: function getThermalLevel(): ThermalLevel;|api/@ohos.thermal.d.ts|
|New API|NA|Class name: thermal;<br>API declaration: function getLevel(): ThermalLevel;<br>Differences: function getLevel(): ThermalLevel;|api/@ohos.thermal.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace usb<br>Differences: declare namespace usb|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function getDevices(): Array\<Readonly\<USBDevice>>;<br>Differences: function getDevices(): Array\<Readonly\<USBDevice>>;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function connectDevice(device: USBDevice): Readonly\<USBDevicePipe>;<br>Differences: function connectDevice(device: USBDevice): Readonly\<USBDevicePipe>;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function hasRight(deviceName: string): boolean;<br>Differences: function hasRight(deviceName: string): boolean;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function requestRight(deviceName: string): Promise\<boolean>;<br>Differences: function requestRight(deviceName: string): Promise\<boolean>;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number;<br>Differences: function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>Differences: function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function setConfiguration(pipe: USBDevicePipe, config: USBConfig): number;<br>Differences: function setConfiguration(pipe: USBDevicePipe, config: USBConfig): number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function setInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>Differences: function setInterface(pipe: USBDevicePipe, iface: USBInterface): number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function getRawDescriptor(pipe: USBDevicePipe): Uint8Array;<br>Differences: function getRawDescriptor(pipe: USBDevicePipe): Uint8Array;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function getFileDescriptor(pipe: USBDevicePipe): number;<br>Differences: function getFileDescriptor(pipe: USBDevicePipe): number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise\<number>;<br>Differences: function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise\<number>;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function bulkTransfer(pipe: USBDevicePipe, endpoint: USBEndpoint, buffer: Uint8Array, timeout?: number): Promise\<number>;<br>Differences: function bulkTransfer(pipe: USBDevicePipe, endpoint: USBEndpoint, buffer: Uint8Array, timeout?: number): Promise\<number>;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: function closePipe(pipe: USBDevicePipe): number;<br>Differences: function closePipe(pipe: USBDevicePipe): number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: interface USBEndpoint<br>Differences: interface USBEndpoint|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: address: number;<br>Differences: address: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: attributes: number;<br>Differences: attributes: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: interval: number;<br>Differences: interval: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: maxPacketSize: number;<br>Differences: maxPacketSize: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: direction: USBRequestDirection;<br>Differences: direction: USBRequestDirection;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: number: number;<br>Differences: number: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: type: number;<br>Differences: type: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: interfaceId: number;<br>Differences: interfaceId: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: interface USBInterface<br>Differences: interface USBInterface|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: id: number;<br>Differences: id: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: protocol: number;<br>Differences: protocol: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: clazz: number;<br>Differences: clazz: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: subClass: number;<br>Differences: subClass: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: alternateSetting: number;<br>Differences: alternateSetting: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: endpoints: Array\<USBEndpoint>;<br>Differences: endpoints: Array\<USBEndpoint>;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: interface USBConfig<br>Differences: interface USBConfig|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBConfig;<br>API declaration: id: number;<br>Differences: id: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBConfig;<br>API declaration: attributes: number;<br>Differences: attributes: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBConfig;<br>API declaration: maxPower: number;<br>Differences: maxPower: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBConfig;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBConfig;<br>API declaration: isRemoteWakeup: boolean;<br>Differences: isRemoteWakeup: boolean;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBConfig;<br>API declaration: isSelfPowered: boolean;<br>Differences: isSelfPowered: boolean;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBConfig;<br>API declaration: interfaces: Array\<USBInterface>;<br>Differences: interfaces: Array\<USBInterface>;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: interface USBDevice<br>Differences: interface USBDevice|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: busNum: number;<br>Differences: busNum: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: devAddress: number;<br>Differences: devAddress: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: serial: string;<br>Differences: serial: string;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: manufacturerName: string;<br>Differences: manufacturerName: string;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: productName: string;<br>Differences: productName: string;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: version: string;<br>Differences: version: string;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: vendorId: number;<br>Differences: vendorId: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: productId: number;<br>Differences: productId: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: clazz: number;<br>Differences: clazz: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: subClass: number;<br>Differences: subClass: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: protocol: number;<br>Differences: protocol: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: configs: Array\<USBConfig>;<br>Differences: configs: Array\<USBConfig>;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: interface USBDevicePipe<br>Differences: interface USBDevicePipe|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevicePipe;<br>API declaration: busNum: number;<br>Differences: busNum: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBDevicePipe;<br>API declaration: devAddress: number;<br>Differences: devAddress: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: interface USBControlParams<br>Differences: interface USBControlParams|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBControlParams;<br>API declaration: request: number;<br>Differences: request: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBControlParams;<br>API declaration: target: USBRequestTargetType;<br>Differences: target: USBRequestTargetType;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBControlParams;<br>API declaration: reqType: USBControlRequestType;<br>Differences: reqType: USBControlRequestType;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBControlParams;<br>API declaration: value: number;<br>Differences: value: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBControlParams;<br>API declaration: index: number;<br>Differences: index: number;|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBControlParams;<br>API declaration: data: Uint8Array;<br>Differences: data: Uint8Array;|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: export enum USBRequestTargetType<br>Differences: export enum USBRequestTargetType|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBRequestTargetType;<br>API declaration: USB_REQUEST_TARGET_DEVICE = 0<br>Differences: USB_REQUEST_TARGET_DEVICE = 0|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBRequestTargetType;<br>API declaration: USB_REQUEST_TARGET_INTERFACE = 1<br>Differences: USB_REQUEST_TARGET_INTERFACE = 1|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBRequestTargetType;<br>API declaration: USB_REQUEST_TARGET_ENDPOINT = 2<br>Differences: USB_REQUEST_TARGET_ENDPOINT = 2|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBRequestTargetType;<br>API declaration: USB_REQUEST_TARGET_OTHER = 3<br>Differences: USB_REQUEST_TARGET_OTHER = 3|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: export enum USBControlRequestType<br>Differences: export enum USBControlRequestType|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBControlRequestType;<br>API declaration: USB_REQUEST_TYPE_STANDARD = 0<br>Differences: USB_REQUEST_TYPE_STANDARD = 0|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBControlRequestType;<br>API declaration: USB_REQUEST_TYPE_CLASS = 1<br>Differences: USB_REQUEST_TYPE_CLASS = 1|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBControlRequestType;<br>API declaration: USB_REQUEST_TYPE_VENDOR = 2<br>Differences: USB_REQUEST_TYPE_VENDOR = 2|api/@ohos.usb.d.ts|
|New API|NA|Class name: usb;<br>API declaration: export enum USBRequestDirection<br>Differences: export enum USBRequestDirection|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBRequestDirection;<br>API declaration: USB_REQUEST_DIR_TO_DEVICE = 0<br>Differences: USB_REQUEST_DIR_TO_DEVICE = 0|api/@ohos.usb.d.ts|
|New API|NA|Class name: USBRequestDirection;<br>API declaration: USB_REQUEST_DIR_FROM_DEVICE = 0x80<br>Differences: USB_REQUEST_DIR_FROM_DEVICE = 0x80|api/@ohos.usb.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace usbManager<br>Differences: declare namespace usbManager|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function getDevices(): Array\<Readonly\<USBDevice>>;<br>Differences: function getDevices(): Array\<Readonly\<USBDevice>>;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function connectDevice(device: USBDevice): Readonly\<USBDevicePipe>;<br>Differences: function connectDevice(device: USBDevice): Readonly\<USBDevicePipe>;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function hasRight(deviceName: string): boolean;<br>Differences: function hasRight(deviceName: string): boolean;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function requestRight(deviceName: string): Promise\<boolean>;<br>Differences: function requestRight(deviceName: string): Promise\<boolean>;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function removeRight(deviceName: string): boolean;<br>Differences: function removeRight(deviceName: string): boolean;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number;<br>Differences: function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>Differences: function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): number;<br>Differences: function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function setInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>Differences: function setInterface(pipe: USBDevicePipe, iface: USBInterface): number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function getRawDescriptor(pipe: USBDevicePipe): Uint8Array;<br>Differences: function getRawDescriptor(pipe: USBDevicePipe): Uint8Array;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function getFileDescriptor(pipe: USBDevicePipe): number;<br>Differences: function getFileDescriptor(pipe: USBDevicePipe): number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise\<number>;<br>Differences: function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise\<number>;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function bulkTransfer(pipe: USBDevicePipe, endpoint: USBEndpoint, buffer: Uint8Array, timeout?: number): Promise\<number>;<br>Differences: function bulkTransfer(pipe: USBDevicePipe, endpoint: USBEndpoint, buffer: Uint8Array, timeout?: number): Promise\<number>;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function closePipe(pipe: USBDevicePipe): number;<br>Differences: function closePipe(pipe: USBDevicePipe): number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: interface USBEndpoint<br>Differences: interface USBEndpoint|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: address: number;<br>Differences: address: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: attributes: number;<br>Differences: attributes: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: interval: number;<br>Differences: interval: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: maxPacketSize: number;<br>Differences: maxPacketSize: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: direction: USBRequestDirection;<br>Differences: direction: USBRequestDirection;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: number: number;<br>Differences: number: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: type: number;<br>Differences: type: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBEndpoint;<br>API declaration: interfaceId: number;<br>Differences: interfaceId: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: interface USBInterface<br>Differences: interface USBInterface|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: id: number;<br>Differences: id: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: protocol: number;<br>Differences: protocol: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: clazz: number;<br>Differences: clazz: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: subClass: number;<br>Differences: subClass: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: alternateSetting: number;<br>Differences: alternateSetting: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBInterface;<br>API declaration: endpoints: Array\<USBEndpoint>;<br>Differences: endpoints: Array\<USBEndpoint>;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: interface USBConfiguration<br>Differences: interface USBConfiguration|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBConfiguration;<br>API declaration: id: number;<br>Differences: id: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBConfiguration;<br>API declaration: attributes: number;<br>Differences: attributes: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBConfiguration;<br>API declaration: maxPower: number;<br>Differences: maxPower: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBConfiguration;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBConfiguration;<br>API declaration: isRemoteWakeup: boolean;<br>Differences: isRemoteWakeup: boolean;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBConfiguration;<br>API declaration: isSelfPowered: boolean;<br>Differences: isSelfPowered: boolean;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBConfiguration;<br>API declaration: interfaces: Array\<USBInterface>;<br>Differences: interfaces: Array\<USBInterface>;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: interface USBDevice<br>Differences: interface USBDevice|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: busNum: number;<br>Differences: busNum: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: devAddress: number;<br>Differences: devAddress: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: serial: string;<br>Differences: serial: string;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: manufacturerName: string;<br>Differences: manufacturerName: string;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: productName: string;<br>Differences: productName: string;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: version: string;<br>Differences: version: string;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: vendorId: number;<br>Differences: vendorId: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: productId: number;<br>Differences: productId: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: clazz: number;<br>Differences: clazz: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: subClass: number;<br>Differences: subClass: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: protocol: number;<br>Differences: protocol: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevice;<br>API declaration: configs: Array\<USBConfiguration>;<br>Differences: configs: Array\<USBConfiguration>;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: interface USBDevicePipe<br>Differences: interface USBDevicePipe|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevicePipe;<br>API declaration: busNum: number;<br>Differences: busNum: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBDevicePipe;<br>API declaration: devAddress: number;<br>Differences: devAddress: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: interface USBControlParams<br>Differences: interface USBControlParams|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBControlParams;<br>API declaration: request: number;<br>Differences: request: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBControlParams;<br>API declaration: target: USBRequestTargetType;<br>Differences: target: USBRequestTargetType;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBControlParams;<br>API declaration: reqType: USBControlRequestType;<br>Differences: reqType: USBControlRequestType;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBControlParams;<br>API declaration: value: number;<br>Differences: value: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBControlParams;<br>API declaration: index: number;<br>Differences: index: number;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBControlParams;<br>API declaration: data: Uint8Array;<br>Differences: data: Uint8Array;|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: export enum USBRequestTargetType<br>Differences: export enum USBRequestTargetType|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBRequestTargetType;<br>API declaration: USB_REQUEST_TARGET_DEVICE = 0<br>Differences: USB_REQUEST_TARGET_DEVICE = 0|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBRequestTargetType;<br>API declaration: USB_REQUEST_TARGET_INTERFACE = 1<br>Differences: USB_REQUEST_TARGET_INTERFACE = 1|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBRequestTargetType;<br>API declaration: USB_REQUEST_TARGET_ENDPOINT = 2<br>Differences: USB_REQUEST_TARGET_ENDPOINT = 2|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBRequestTargetType;<br>API declaration: USB_REQUEST_TARGET_OTHER = 3<br>Differences: USB_REQUEST_TARGET_OTHER = 3|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: export enum USBControlRequestType<br>Differences: export enum USBControlRequestType|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBControlRequestType;<br>API declaration: USB_REQUEST_TYPE_STANDARD = 0<br>Differences: USB_REQUEST_TYPE_STANDARD = 0|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBControlRequestType;<br>API declaration: USB_REQUEST_TYPE_CLASS = 1<br>Differences: USB_REQUEST_TYPE_CLASS = 1|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBControlRequestType;<br>API declaration: USB_REQUEST_TYPE_VENDOR = 2<br>Differences: USB_REQUEST_TYPE_VENDOR = 2|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: export enum USBRequestDirection<br>Differences: export enum USBRequestDirection|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBRequestDirection;<br>API declaration: USB_REQUEST_DIR_TO_DEVICE = 0<br>Differences: USB_REQUEST_DIR_TO_DEVICE = 0|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: USBRequestDirection;<br>API declaration: USB_REQUEST_DIR_FROM_DEVICE = 0x80<br>Differences: USB_REQUEST_DIR_FROM_DEVICE = 0x80|api/@ohos.usbManager.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace wallpaper<br>Differences: declare namespace wallpaper|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: interface RgbaColor<br>Differences: interface RgbaColor|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: RgbaColor;<br>API declaration: red: number;<br>Differences: red: number;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: RgbaColor;<br>API declaration: green: number;<br>Differences: green: number;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: RgbaColor;<br>API declaration: blue: number;<br>Differences: blue: number;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: RgbaColor;<br>API declaration: alpha: number;<br>Differences: alpha: number;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: enum WallpaperType<br>Differences: enum WallpaperType|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: WallpaperType;<br>API declaration: WALLPAPER_SYSTEM<br>Differences: WALLPAPER_SYSTEM|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: WallpaperType;<br>API declaration: WALLPAPER_LOCKSCREEN<br>Differences: WALLPAPER_LOCKSCREEN|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function getColors(wallpaperType: WallpaperType, callback: AsyncCallback\<Array\<RgbaColor>>): void;<br>Differences: function getColors(wallpaperType: WallpaperType, callback: AsyncCallback\<Array\<RgbaColor>>): void;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function getColors(wallpaperType: WallpaperType): Promise\<Array\<RgbaColor>>;<br>Differences: function getColors(wallpaperType: WallpaperType): Promise\<Array\<RgbaColor>>;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function getId(wallpaperType: WallpaperType, callback: AsyncCallback\<number>): void;<br>Differences: function getId(wallpaperType: WallpaperType, callback: AsyncCallback\<number>): void;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function getId(wallpaperType: WallpaperType): Promise\<number>;<br>Differences: function getId(wallpaperType: WallpaperType): Promise\<number>;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function getFile(wallpaperType: WallpaperType, callback: AsyncCallback\<number>): void;<br>Differences: function getFile(wallpaperType: WallpaperType, callback: AsyncCallback\<number>): void;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function getFile(wallpaperType: WallpaperType): Promise\<number>;<br>Differences: function getFile(wallpaperType: WallpaperType): Promise\<number>;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function getMinHeight(callback: AsyncCallback\<number>): void;<br>Differences: function getMinHeight(callback: AsyncCallback\<number>): void;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function getMinHeight(): Promise\<number>;<br>Differences: function getMinHeight(): Promise\<number>;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function getMinWidth(callback: AsyncCallback\<number>): void;<br>Differences: function getMinWidth(callback: AsyncCallback\<number>): void;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function getMinWidth(): Promise\<number>;<br>Differences: function getMinWidth(): Promise\<number>;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function isChangePermitted(callback: AsyncCallback\<boolean>): void;<br>Differences: function isChangePermitted(callback: AsyncCallback\<boolean>): void;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function isChangePermitted(): Promise\<boolean>;<br>Differences: function isChangePermitted(): Promise\<boolean>;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function isOperationAllowed(callback: AsyncCallback\<boolean>): void;<br>Differences: function isOperationAllowed(callback: AsyncCallback\<boolean>): void;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function isOperationAllowed(): Promise\<boolean>;<br>Differences: function isOperationAllowed(): Promise\<boolean>;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function reset(wallpaperType: WallpaperType, callback: AsyncCallback\<void>): void;<br>Differences: function reset(wallpaperType: WallpaperType, callback: AsyncCallback\<void>): void;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function reset(wallpaperType: WallpaperType): Promise\<void>;<br>Differences: function reset(wallpaperType: WallpaperType): Promise\<void>;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function setWallpaper(source: string \| image.PixelMap, wallpaperType: WallpaperType, callback: AsyncCallback\<void>): void;<br>Differences: function setWallpaper(source: string \| image.PixelMap, wallpaperType: WallpaperType, callback: AsyncCallback\<void>): void;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function setWallpaper(source: string \| image.PixelMap, wallpaperType: WallpaperType): Promise\<void>;<br>Differences: function setWallpaper(source: string \| image.PixelMap, wallpaperType: WallpaperType): Promise\<void>;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function on(type: 'colorChange', callback: (colors: Array\<RgbaColor>, wallpaperType: WallpaperType) => void): void;<br>Differences: function on(type: 'colorChange', callback: (colors: Array\<RgbaColor>, wallpaperType: WallpaperType) => void): void;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: wallpaper;<br>API declaration: function off(type: 'colorChange', callback?: (colors: Array\<RgbaColor>, wallpaperType: WallpaperType) => void): void;<br>Differences: function off(type: 'colorChange', callback?: (colors: Array\<RgbaColor>, wallpaperType: WallpaperType) => void): void;|api/@ohos.wallpaper.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace zlib<br>Differences: declare namespace zlib|api/@ohos.zlib.d.ts|
|New API|NA|Class name: zlib;<br>API declaration: export enum ErrorCode<br>Differences: export enum ErrorCode|api/@ohos.zlib.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: ERROR_CODE_OK = 0<br>Differences: ERROR_CODE_OK = 0|api/@ohos.zlib.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: ERROR_CODE_ERRNO = -1<br>Differences: ERROR_CODE_ERRNO = -1|api/@ohos.zlib.d.ts|
|New API|NA|Class name: zlib;<br>API declaration: export enum CompressLevel<br>Differences: export enum CompressLevel|api/@ohos.zlib.d.ts|
|New API|NA|Class name: CompressLevel;<br>API declaration: COMPRESS_LEVEL_NO_COMPRESSION = 0<br>Differences: COMPRESS_LEVEL_NO_COMPRESSION = 0|api/@ohos.zlib.d.ts|
|New API|NA|Class name: CompressLevel;<br>API declaration: COMPRESS_LEVEL_BEST_SPEED = 1<br>Differences: COMPRESS_LEVEL_BEST_SPEED = 1|api/@ohos.zlib.d.ts|
|New API|NA|Class name: CompressLevel;<br>API declaration: COMPRESS_LEVEL_BEST_COMPRESSION = 9<br>Differences: COMPRESS_LEVEL_BEST_COMPRESSION = 9|api/@ohos.zlib.d.ts|
|New API|NA|Class name: CompressLevel;<br>API declaration: COMPRESS_LEVEL_DEFAULT_COMPRESSION = -1<br>Differences: COMPRESS_LEVEL_DEFAULT_COMPRESSION = -1|api/@ohos.zlib.d.ts|
|New API|NA|Class name: zlib;<br>API declaration: export enum CompressStrategy<br>Differences: export enum CompressStrategy|api/@ohos.zlib.d.ts|
|New API|NA|Class name: CompressStrategy;<br>API declaration: COMPRESS_STRATEGY_DEFAULT_STRATEGY = 0<br>Differences: COMPRESS_STRATEGY_DEFAULT_STRATEGY = 0|api/@ohos.zlib.d.ts|
|New API|NA|Class name: CompressStrategy;<br>API declaration: COMPRESS_STRATEGY_FILTERED = 1<br>Differences: COMPRESS_STRATEGY_FILTERED = 1|api/@ohos.zlib.d.ts|
|New API|NA|Class name: CompressStrategy;<br>API declaration: COMPRESS_STRATEGY_HUFFMAN_ONLY = 2<br>Differences: COMPRESS_STRATEGY_HUFFMAN_ONLY = 2|api/@ohos.zlib.d.ts|
|New API|NA|Class name: CompressStrategy;<br>API declaration: COMPRESS_STRATEGY_RLE = 3<br>Differences: COMPRESS_STRATEGY_RLE = 3|api/@ohos.zlib.d.ts|
|New API|NA|Class name: CompressStrategy;<br>API declaration: COMPRESS_STRATEGY_FIXED = 4<br>Differences: COMPRESS_STRATEGY_FIXED = 4|api/@ohos.zlib.d.ts|
|New API|NA|Class name: zlib;<br>API declaration: export enum MemLevel<br>Differences: export enum MemLevel|api/@ohos.zlib.d.ts|
|New API|NA|Class name: MemLevel;<br>API declaration: MEM_LEVEL_MIN = 1<br>Differences: MEM_LEVEL_MIN = 1|api/@ohos.zlib.d.ts|
|New API|NA|Class name: MemLevel;<br>API declaration: MEM_LEVEL_MAX = 9<br>Differences: MEM_LEVEL_MAX = 9|api/@ohos.zlib.d.ts|
|New API|NA|Class name: MemLevel;<br>API declaration: MEM_LEVEL_DEFAULT = 8<br>Differences: MEM_LEVEL_DEFAULT = 8|api/@ohos.zlib.d.ts|
|New API|NA|Class name: zlib;<br>API declaration: interface Options<br>Differences: interface Options|api/@ohos.zlib.d.ts|
|New API|NA|Class name: Options;<br>API declaration: level?: CompressLevel;<br>Differences: level?: CompressLevel;|api/@ohos.zlib.d.ts|
|New API|NA|Class name: Options;<br>API declaration: memLevel?: MemLevel;<br>Differences: memLevel?: MemLevel;|api/@ohos.zlib.d.ts|
|New API|NA|Class name: Options;<br>API declaration: strategy?: CompressStrategy;<br>Differences: strategy?: CompressStrategy;|api/@ohos.zlib.d.ts|
|New API|NA|Class name: zlib;<br>API declaration: function zipFile(inFile: string, outFile: string, options: Options): Promise\<void>;<br>Differences: function zipFile(inFile: string, outFile: string, options: Options): Promise\<void>;|api/@ohos.zlib.d.ts|
|New API|NA|Class name: zlib;<br>API declaration: function unzipFile(inFile: string, outFile: string, options: Options): Promise\<void>;<br>Differences: function unzipFile(inFile: string, outFile: string, options: Options): Promise\<void>;|api/@ohos.zlib.d.ts|
|New API|NA|Class name: zlib;<br>API declaration: function compressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback\<void>): void;<br>Differences: function compressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback\<void>): void;|api/@ohos.zlib.d.ts|
|New API|NA|Class name: zlib;<br>API declaration: function compressFile(inFile: string, outFile: string, options: Options): Promise\<void>;<br>Differences: function compressFile(inFile: string, outFile: string, options: Options): Promise\<void>;|api/@ohos.zlib.d.ts|
|New API|NA|Class name: zlib;<br>API declaration: function decompressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback\<void>): void;<br>Differences: function decompressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback\<void>): void;|api/@ohos.zlib.d.ts|
|New API|NA|Class name: zlib;<br>API declaration: function decompressFile(inFile: string, outFile: string, callback: AsyncCallback\<void>): void;<br>Differences: function decompressFile(inFile: string, outFile: string, callback: AsyncCallback\<void>): void;|api/@ohos.zlib.d.ts|
|New API|NA|Class name: zlib;<br>API declaration: function decompressFile(inFile: string, outFile: string, options?: Options): Promise\<void>;<br>Differences: function decompressFile(inFile: string, outFile: string, options?: Options): Promise\<void>;|api/@ohos.zlib.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface BatteryResponse<br>Differences: export interface BatteryResponse|api/@system.battery.d.ts|
|New API|NA|Class name: BatteryResponse;<br>API declaration: charging: boolean;<br>Differences: charging: boolean;|api/@system.battery.d.ts|
|New API|NA|Class name: BatteryResponse;<br>API declaration: level: number;<br>Differences: level: number;|api/@system.battery.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface GetStatusOptions<br>Differences: export interface GetStatusOptions|api/@system.battery.d.ts|
|New API|NA|Class name: GetStatusOptions;<br>API declaration: success?: (data: BatteryResponse) => void;<br>Differences: success?: (data: BatteryResponse) => void;|api/@system.battery.d.ts|
|New API|NA|Class name: GetStatusOptions;<br>API declaration: fail?: (data: string, code: number) => void;<br>Differences: fail?: (data: string, code: number) => void;|api/@system.battery.d.ts|
|New API|NA|Class name: GetStatusOptions;<br>API declaration: complete?: () => void;<br>Differences: complete?: () => void;|api/@system.battery.d.ts|
|New API|NA|Class name: global;<br>API declaration: export default class Battery<br>Differences: export default class Battery|api/@system.battery.d.ts|
|New API|NA|Class name: Battery;<br>API declaration: static getStatus(options?: GetStatusOptions): void;<br>Differences: static getStatus(options?: GetStatusOptions): void;|api/@system.battery.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface BrightnessResponse<br>Differences: export interface BrightnessResponse|api/@system.brightness.d.ts|
|New API|NA|Class name: BrightnessResponse;<br>API declaration: value: number;<br>Differences: value: number;|api/@system.brightness.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface GetBrightnessOptions<br>Differences: export interface GetBrightnessOptions|api/@system.brightness.d.ts|
|New API|NA|Class name: GetBrightnessOptions;<br>API declaration: success?: (data: BrightnessResponse) => void;<br>Differences: success?: (data: BrightnessResponse) => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: GetBrightnessOptions;<br>API declaration: fail?: (data: string, code: number) => void;<br>Differences: fail?: (data: string, code: number) => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: GetBrightnessOptions;<br>API declaration: complete?: () => void;<br>Differences: complete?: () => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface SetBrightnessOptions<br>Differences: export interface SetBrightnessOptions|api/@system.brightness.d.ts|
|New API|NA|Class name: SetBrightnessOptions;<br>API declaration: value: number;<br>Differences: value: number;|api/@system.brightness.d.ts|
|New API|NA|Class name: SetBrightnessOptions;<br>API declaration: success?: () => void;<br>Differences: success?: () => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: SetBrightnessOptions;<br>API declaration: fail?: (data: string, code: number) => void;<br>Differences: fail?: (data: string, code: number) => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: SetBrightnessOptions;<br>API declaration: complete?: () => void;<br>Differences: complete?: () => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface BrightnessModeResponse<br>Differences: export interface BrightnessModeResponse|api/@system.brightness.d.ts|
|New API|NA|Class name: BrightnessModeResponse;<br>API declaration: mode: number;<br>Differences: mode: number;|api/@system.brightness.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface GetBrightnessModeOptions<br>Differences: export interface GetBrightnessModeOptions|api/@system.brightness.d.ts|
|New API|NA|Class name: GetBrightnessModeOptions;<br>API declaration: success?: (data: BrightnessModeResponse) => void;<br>Differences: success?: (data: BrightnessModeResponse) => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: GetBrightnessModeOptions;<br>API declaration: fail?: (data: string, code: number) => void;<br>Differences: fail?: (data: string, code: number) => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: GetBrightnessModeOptions;<br>API declaration: complete?: () => void;<br>Differences: complete?: () => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface SetBrightnessModeOptions<br>Differences: export interface SetBrightnessModeOptions|api/@system.brightness.d.ts|
|New API|NA|Class name: SetBrightnessModeOptions;<br>API declaration: mode: number;<br>Differences: mode: number;|api/@system.brightness.d.ts|
|New API|NA|Class name: SetBrightnessModeOptions;<br>API declaration: success?: () => void;<br>Differences: success?: () => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: SetBrightnessModeOptions;<br>API declaration: fail?: (data: string, code: number) => void;<br>Differences: fail?: (data: string, code: number) => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: SetBrightnessModeOptions;<br>API declaration: complete?: () => void;<br>Differences: complete?: () => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface SetKeepScreenOnOptions<br>Differences: export interface SetKeepScreenOnOptions|api/@system.brightness.d.ts|
|New API|NA|Class name: SetKeepScreenOnOptions;<br>API declaration: keepScreenOn: boolean;<br>Differences: keepScreenOn: boolean;|api/@system.brightness.d.ts|
|New API|NA|Class name: SetKeepScreenOnOptions;<br>API declaration: success?: () => void;<br>Differences: success?: () => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: SetKeepScreenOnOptions;<br>API declaration: fail?: (data: string, code: number) => void;<br>Differences: fail?: (data: string, code: number) => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: SetKeepScreenOnOptions;<br>API declaration: complete?: () => void;<br>Differences: complete?: () => void;|api/@system.brightness.d.ts|
|New API|NA|Class name: global;<br>API declaration: export default class Brightness<br>Differences: export default class Brightness|api/@system.brightness.d.ts|
|New API|NA|Class name: Brightness;<br>API declaration: static getValue(options?: GetBrightnessOptions): void;<br>Differences: static getValue(options?: GetBrightnessOptions): void;|api/@system.brightness.d.ts|
|New API|NA|Class name: Brightness;<br>API declaration: static setValue(options?: SetBrightnessOptions): void;<br>Differences: static setValue(options?: SetBrightnessOptions): void;|api/@system.brightness.d.ts|
|New API|NA|Class name: Brightness;<br>API declaration: static getMode(options?: GetBrightnessModeOptions): void;<br>Differences: static getMode(options?: GetBrightnessModeOptions): void;|api/@system.brightness.d.ts|
|New API|NA|Class name: Brightness;<br>API declaration: static setMode(options?: SetBrightnessModeOptions): void;<br>Differences: static setMode(options?: SetBrightnessModeOptions): void;|api/@system.brightness.d.ts|
|New API|NA|Class name: Brightness;<br>API declaration: static setKeepScreenOn(options?: SetKeepScreenOnOptions): void;<br>Differences: static setKeepScreenOn(options?: SetKeepScreenOnOptions): void;|api/@system.brightness.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface DeviceResponse<br>Differences: export interface DeviceResponse|api/@system.device.d.ts|
|New API|NA|Class name: DeviceResponse;<br>API declaration: brand: string;<br>Differences: brand: string;|api/@system.device.d.ts|
|New API|NA|Class name: DeviceResponse;<br>API declaration: manufacturer: string;<br>Differences: manufacturer: string;|api/@system.device.d.ts|
|New API|NA|Class name: DeviceResponse;<br>API declaration: model: string;<br>Differences: model: string;|api/@system.device.d.ts|
|New API|NA|Class name: DeviceResponse;<br>API declaration: product: string;<br>Differences: product: string;|api/@system.device.d.ts|
|New API|NA|Class name: DeviceResponse;<br>API declaration: language: string;<br>Differences: language: string;|api/@system.device.d.ts|
|New API|NA|Class name: DeviceResponse;<br>API declaration: region: string;<br>Differences: region: string;|api/@system.device.d.ts|
|New API|NA|Class name: DeviceResponse;<br>API declaration: windowWidth: number;<br>Differences: windowWidth: number;|api/@system.device.d.ts|
|New API|NA|Class name: DeviceResponse;<br>API declaration: windowHeight: number;<br>Differences: windowHeight: number;|api/@system.device.d.ts|
|New API|NA|Class name: DeviceResponse;<br>API declaration: screenDensity: number;<br>Differences: screenDensity: number;|api/@system.device.d.ts|
|New API|NA|Class name: DeviceResponse;<br>API declaration: screenShape: 'rect' \| 'circle';<br>Differences: screenShape: 'rect' \| 'circle';|api/@system.device.d.ts|
|New API|NA|Class name: DeviceResponse;<br>API declaration: apiVersion: number;<br>Differences: apiVersion: number;|api/@system.device.d.ts|
|New API|NA|Class name: DeviceResponse;<br>API declaration: deviceType: string;<br>Differences: deviceType: string;|api/@system.device.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface GetDeviceOptions<br>Differences: export interface GetDeviceOptions|api/@system.device.d.ts|
|New API|NA|Class name: GetDeviceOptions;<br>API declaration: success?: (data: DeviceResponse) => void;<br>Differences: success?: (data: DeviceResponse) => void;|api/@system.device.d.ts|
|New API|NA|Class name: GetDeviceOptions;<br>API declaration: fail?: (data: any, code: number) => void;<br>Differences: fail?: (data: any, code: number) => void;|api/@system.device.d.ts|
|New API|NA|Class name: GetDeviceOptions;<br>API declaration: complete?: () => void;<br>Differences: complete?: () => void;|api/@system.device.d.ts|
|New API|NA|Class name: global;<br>API declaration: export default class Device<br>Differences: export default class Device|api/@system.device.d.ts|
|New API|NA|Class name: Device;<br>API declaration: static getInfo(options?: GetDeviceOptions): void;<br>Differences: static getInfo(options?: GetDeviceOptions): void;|api/@system.device.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface UploadResponse<br>Differences: export interface UploadResponse|api/@system.request.d.ts|
|New API|NA|Class name: UploadResponse;<br>API declaration: code: number;<br>Differences: code: number;|api/@system.request.d.ts|
|New API|NA|Class name: UploadResponse;<br>API declaration: data: string;<br>Differences: data: string;|api/@system.request.d.ts|
|New API|NA|Class name: UploadResponse;<br>API declaration: headers: Object;<br>Differences: headers: Object;|api/@system.request.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface DownloadResponse<br>Differences: export interface DownloadResponse|api/@system.request.d.ts|
|New API|NA|Class name: DownloadResponse;<br>API declaration: token: string;<br>Differences: token: string;|api/@system.request.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface OnDownloadCompleteResponse<br>Differences: export interface OnDownloadCompleteResponse|api/@system.request.d.ts|
|New API|NA|Class name: OnDownloadCompleteResponse;<br>API declaration: uri: string;<br>Differences: uri: string;|api/@system.request.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface RequestFile<br>Differences: export interface RequestFile|api/@system.request.d.ts|
|New API|NA|Class name: RequestFile;<br>API declaration: filename?: string;<br>Differences: filename?: string;|api/@system.request.d.ts|
|New API|NA|Class name: RequestFile;<br>API declaration: name?: string;<br>Differences: name?: string;|api/@system.request.d.ts|
|New API|NA|Class name: RequestFile;<br>API declaration: uri: string;<br>Differences: uri: string;|api/@system.request.d.ts|
|New API|NA|Class name: RequestFile;<br>API declaration: type?: string;<br>Differences: type?: string;|api/@system.request.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface RequestData<br>Differences: export interface RequestData|api/@system.request.d.ts|
|New API|NA|Class name: RequestData;<br>API declaration: name: string;<br>Differences: name: string;|api/@system.request.d.ts|
|New API|NA|Class name: RequestData;<br>API declaration: value: string;<br>Differences: value: string;|api/@system.request.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface UploadRequestOptions<br>Differences: export interface UploadRequestOptions|api/@system.request.d.ts|
|New API|NA|Class name: UploadRequestOptions;<br>API declaration: url: string;<br>Differences: url: string;|api/@system.request.d.ts|
|New API|NA|Class name: UploadRequestOptions;<br>API declaration: data?: Array\<RequestData>;<br>Differences: data?: Array\<RequestData>;|api/@system.request.d.ts|
|New API|NA|Class name: UploadRequestOptions;<br>API declaration: files: Array\<RequestFile>;<br>Differences: files: Array\<RequestFile>;|api/@system.request.d.ts|
|New API|NA|Class name: UploadRequestOptions;<br>API declaration: header?: Object;<br>Differences: header?: Object;|api/@system.request.d.ts|
|New API|NA|Class name: UploadRequestOptions;<br>API declaration: method?: string;<br>Differences: method?: string;|api/@system.request.d.ts|
|New API|NA|Class name: UploadRequestOptions;<br>API declaration: success?: (data: UploadResponse) => void;<br>Differences: success?: (data: UploadResponse) => void;|api/@system.request.d.ts|
|New API|NA|Class name: UploadRequestOptions;<br>API declaration: fail?: (data: any, code: number) => void;<br>Differences: fail?: (data: any, code: number) => void;|api/@system.request.d.ts|
|New API|NA|Class name: UploadRequestOptions;<br>API declaration: complete?: () => void;<br>Differences: complete?: () => void;|api/@system.request.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface DownloadRequestOptions<br>Differences: export interface DownloadRequestOptions|api/@system.request.d.ts|
|New API|NA|Class name: DownloadRequestOptions;<br>API declaration: url: string;<br>Differences: url: string;|api/@system.request.d.ts|
|New API|NA|Class name: DownloadRequestOptions;<br>API declaration: filename?: string;<br>Differences: filename?: string;|api/@system.request.d.ts|
|New API|NA|Class name: DownloadRequestOptions;<br>API declaration: header?: string;<br>Differences: header?: string;|api/@system.request.d.ts|
|New API|NA|Class name: DownloadRequestOptions;<br>API declaration: description?: string;<br>Differences: description?: string;|api/@system.request.d.ts|
|New API|NA|Class name: DownloadRequestOptions;<br>API declaration: success?: (data: DownloadResponse) => void;<br>Differences: success?: (data: DownloadResponse) => void;|api/@system.request.d.ts|
|New API|NA|Class name: DownloadRequestOptions;<br>API declaration: fail?: (data: any, code: number) => void;<br>Differences: fail?: (data: any, code: number) => void;|api/@system.request.d.ts|
|New API|NA|Class name: DownloadRequestOptions;<br>API declaration: complete?: () => void;<br>Differences: complete?: () => void;|api/@system.request.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface OnDownloadCompleteOptions<br>Differences: export interface OnDownloadCompleteOptions|api/@system.request.d.ts|
|New API|NA|Class name: OnDownloadCompleteOptions;<br>API declaration: token: string;<br>Differences: token: string;|api/@system.request.d.ts|
|New API|NA|Class name: OnDownloadCompleteOptions;<br>API declaration: success?: (data: OnDownloadCompleteResponse) => void;<br>Differences: success?: (data: OnDownloadCompleteResponse) => void;|api/@system.request.d.ts|
|New API|NA|Class name: OnDownloadCompleteOptions;<br>API declaration: fail?: (data: any, code: number) => void;<br>Differences: fail?: (data: any, code: number) => void;|api/@system.request.d.ts|
|New API|NA|Class name: OnDownloadCompleteOptions;<br>API declaration: complete?: () => void;<br>Differences: complete?: () => void;|api/@system.request.d.ts|
|New API|NA|Class name: global;<br>API declaration: export default class Request<br>Differences: export default class Request|api/@system.request.d.ts|
|New API|NA|Class name: Request;<br>API declaration: static upload(options: UploadRequestOptions): void;<br>Differences: static upload(options: UploadRequestOptions): void;|api/@system.request.d.ts|
|New API|NA|Class name: Request;<br>API declaration: static download(options: DownloadRequestOptions): void;<br>Differences: static download(options: DownloadRequestOptions): void;|api/@system.request.d.ts|
|New API|NA|Class name: Request;<br>API declaration: static onDownloadComplete(options: OnDownloadCompleteOptions): void;<br>Differences: static onDownloadComplete(options: OnDownloadCompleteOptions): void;|api/@system.request.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.account.appAccount.d.ts<br>Differences: BasicServicesKit|api/@ohos.account.appAccount.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.account.distributedAccount.d.ts<br>Differences: BasicServicesKit|api/@ohos.account.distributedAccount.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.account.osAccount.d.ts<br>Differences: BasicServicesKit|api/@ohos.account.osAccount.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.base.d.ts<br>Differences: BasicServicesKit|api/@ohos.base.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.batteryInfo.d.ts<br>Differences: BasicServicesKit|api/@ohos.batteryInfo.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.commonEventManager.d.ts<br>Differences: BasicServicesKit|api/@ohos.commonEventManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.deviceAttest.d.ts<br>Differences: BasicServicesKit|api/@ohos.deviceAttest.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.deviceInfo.d.ts<br>Differences: BasicServicesKit|api/@ohos.deviceInfo.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.events.emitter.d.ts<br>Differences: BasicServicesKit|api/@ohos.events.emitter.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.pasteboard.d.ts<br>Differences: BasicServicesKit|api/@ohos.pasteboard.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.power.d.ts<br>Differences: BasicServicesKit|api/@ohos.power.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.print.d.ts<br>Differences: BasicServicesKit|api/@ohos.print.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.request.d.ts<br>Differences: BasicServicesKit|api/@ohos.request.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.runningLock.d.ts<br>Differences: BasicServicesKit|api/@ohos.runningLock.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.screenLock.d.ts<br>Differences: BasicServicesKit|api/@ohos.screenLock.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.settings.d.ts<br>Differences: BasicServicesKit|api/@ohos.settings.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.systemDateTime.d.ts<br>Differences: BasicServicesKit|api/@ohos.systemDateTime.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.systemTime.d.ts<br>Differences: BasicServicesKit|api/@ohos.systemTime.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.thermal.d.ts<br>Differences: BasicServicesKit|api/@ohos.thermal.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.usb.d.ts<br>Differences: BasicServicesKit|api/@ohos.usb.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.usbManager.d.ts<br>Differences: BasicServicesKit|api/@ohos.usbManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.wallpaper.d.ts<br>Differences: BasicServicesKit|api/@ohos.wallpaper.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.zlib.d.ts<br>Differences: BasicServicesKit|api/@ohos.zlib.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@system.battery.d.ts<br>Differences: BasicServicesKit|api/@system.battery.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@system.brightness.d.ts<br>Differences: BasicServicesKit|api/@system.brightness.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@system.device.d.ts<br>Differences: BasicServicesKit|api/@system.device.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@system.request.d.ts<br>Differences: BasicServicesKit|api/@system.request.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.BasicServicesKit.d.ts<br>Differences: BasicServicesKit|kits/@kit.BasicServicesKit.d.ts|
