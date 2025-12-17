| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：securityManager；<br>API声明：function installUserCertificate(admin: Want, certificate: CertBlob, accountId: number): string;<br>差异内容：function installUserCertificate(admin: Want, certificate: CertBlob, accountId: number): string;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function setAppClipboardPolicy(admin: Want, bundleName: string, accountId: number, policy: ClipboardPolicy): void;<br>差异内容：function setAppClipboardPolicy(admin: Want, bundleName: string, accountId: number, policy: ClipboardPolicy): void;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function getAppClipboardPolicy(admin: Want, bundleName: string, accountId: number): string;<br>差异内容：function getAppClipboardPolicy(admin: Want, bundleName: string, accountId: number): string;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function getUserCertificates(admin: Want, accountId: number): Array\<string>;<br>差异内容：function getUserCertificates(admin: Want, accountId: number): Array\<string>;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：ManagedEvent；<br>API声明：MANAGED_EVENT_ACCOUNT_ADDED = 5<br>差异内容：MANAGED_EVENT_ACCOUNT_ADDED = 5|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：ManagedEvent；<br>API声明：MANAGED_EVENT_ACCOUNT_SWITCHED = 6<br>差异内容：MANAGED_EVENT_ACCOUNT_SWITCHED = 6|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：ManagedEvent；<br>API声明：MANAGED_EVENT_ACCOUNT_REMOVED = 7<br>差异内容：MANAGED_EVENT_ACCOUNT_REMOVED = 7|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onAccountAdded(accountId: number): void;<br>差异内容：onAccountAdded(accountId: number): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onAccountSwitched(accountId: number): void;<br>差异内容：onAccountSwitched(accountId: number): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onAccountRemoved(accountId: number): void;<br>差异内容：onAccountRemoved(accountId: number): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
