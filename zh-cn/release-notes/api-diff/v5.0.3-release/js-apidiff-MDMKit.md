| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：applicationManager；<br>API声明：function addKeepAliveApps(admin: Want, bundleNames: Array\<string>, accountId: number): void;<br>差异内容：NA|类名：applicationManager；<br>API声明：function addKeepAliveApps(admin: Want, bundleNames: Array\<string>, accountId: number): void;<br>差异内容：801|api/@ohos.enterprise.applicationManager.d.ts|
|删除错误码|类名：adminManager；<br>API声明：function disableAdmin(admin: Want, userId?: number): Promise\<void>;<br>差异内容：401|类名：adminManager；<br>API声明：function disableAdmin(admin: Want, userId?: number): Promise\<void>;<br>差异内容：NA|api/@ohos.enterprise.adminManager.d.ts|
|删除错误码|类名：restrictions；<br>API声明：function setDisallowedPolicy(admin: Want, feature: string, disallow: boolean): void;<br>差异内容：401|类名：restrictions；<br>API声明：function setDisallowedPolicy(admin: Want, feature: string, disallow: boolean): void;<br>差异内容：NA|api/@ohos.enterprise.restrictions.d.ts|
|删除错误码|类名：restrictions；<br>API声明：function getDisallowedPolicy(admin: Want, feature: string): boolean;<br>差异内容：401|类名：restrictions；<br>API声明：function getDisallowedPolicy(admin: Want, feature: string): boolean;<br>差异内容：NA|api/@ohos.enterprise.restrictions.d.ts|
|删除错误码|类名：restrictions；<br>API声明：function setDisallowedPolicyForAccount(admin: Want, feature: string, disallow: boolean, accountId: number): void;<br>差异内容：401|类名：restrictions；<br>API声明：function setDisallowedPolicyForAccount(admin: Want, feature: string, disallow: boolean, accountId: number): void;<br>差异内容：NA|api/@ohos.enterprise.restrictions.d.ts|
|删除错误码|类名：restrictions；<br>API声明：function getDisallowedPolicyForAccount(admin: Want, feature: string, accountId: number): boolean;<br>差异内容：401|类名：restrictions；<br>API声明：function getDisallowedPolicyForAccount(admin: Want \| null, feature: string, accountId: number): boolean;<br>差异内容：NA|api/@ohos.enterprise.restrictions.d.ts|
|权限变更|类名：adminManager；<br>API声明：function disableAdmin(admin: Want, userId?: number): Promise\<void>;<br>差异内容：ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN|类名：adminManager；<br>API声明：function disableAdmin(admin: Want, userId?: number): Promise\<void>;<br>差异内容：ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN or ohos.permission.START_PROVISIONING_MESSAGE|api/@ohos.enterprise.adminManager.d.ts|
|权限变更|类名：restrictions；<br>API声明：function setDisallowedPolicy(admin: Want, feature: string, disallow: boolean): void;<br>差异内容：ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|类名：restrictions；<br>API声明：function setDisallowedPolicy(admin: Want, feature: string, disallow: boolean): void;<br>差异内容：ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|api/@ohos.enterprise.restrictions.d.ts|
|权限变更|类名：restrictions；<br>API声明：function getDisallowedPolicy(admin: Want, feature: string): boolean;<br>差异内容：ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|类名：restrictions；<br>API声明：function getDisallowedPolicy(admin: Want, feature: string): boolean;<br>差异内容：ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|api/@ohos.enterprise.restrictions.d.ts|
|函数变更|类名：restrictions；<br>API声明：function getDisallowedPolicyForAccount(admin: Want, feature: string, accountId: number): boolean;<br>差异内容：admin: Want|类名：restrictions；<br>API声明：function getDisallowedPolicyForAccount(admin: Want \| null, feature: string, accountId: number): boolean;<br>差异内容：admin: Want \| null|api/@ohos.enterprise.restrictions.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace telephonyManager<br>差异内容：declare namespace telephonyManager|api/@ohos.enterprise.telephonyManager.d.ts|
|新增API|NA|类名：telephonyManager；<br>API声明：function setSimDisabled(admin: Want, slotId: number): void;<br>差异内容：function setSimDisabled(admin: Want, slotId: number): void;|api/@ohos.enterprise.telephonyManager.d.ts|
|新增API|NA|类名：telephonyManager；<br>API声明：function setSimEnabled(admin: Want, slotId: number): void;<br>差异内容：function setSimEnabled(admin: Want, slotId: number): void;|api/@ohos.enterprise.telephonyManager.d.ts|
|新增API|NA|类名：telephonyManager；<br>API声明：function isSimDisabled(admin: Want, slotId: number): boolean;<br>差异内容：function isSimDisabled(admin: Want, slotId: number): boolean;|api/@ohos.enterprise.telephonyManager.d.ts|
|新增API|NA|类名：telephonyManager；<br>API声明：function addOutgoingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array\<string>): void;<br>差异内容：function addOutgoingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array\<string>): void;|api/@ohos.enterprise.telephonyManager.d.ts|
|新增API|NA|类名：telephonyManager；<br>API声明：function removeOutgoingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array\<string>): void;<br>差异内容：function removeOutgoingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array\<string>): void;|api/@ohos.enterprise.telephonyManager.d.ts|
|新增API|NA|类名：telephonyManager；<br>API声明：function getOutgoingCallPolicyNumbers(admin: Want, policy: adminManager.Policy): Array\<string>;<br>差异内容：function getOutgoingCallPolicyNumbers(admin: Want, policy: adminManager.Policy): Array\<string>;|api/@ohos.enterprise.telephonyManager.d.ts|
|新增API|NA|类名：telephonyManager；<br>API声明：function addIncomingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array\<string>): void;<br>差异内容：function addIncomingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array\<string>): void;|api/@ohos.enterprise.telephonyManager.d.ts|
|新增API|NA|类名：telephonyManager；<br>API声明：function removeIncomingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array\<string>): void;<br>差异内容：function removeIncomingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array\<string>): void;|api/@ohos.enterprise.telephonyManager.d.ts|
|新增API|NA|类名：telephonyManager；<br>API声明：function getIncomingCallPolicyNumbers(admin: Want, policy: adminManager.Policy): Array\<string>;<br>差异内容：function getIncomingCallPolicyNumbers(admin: Want, policy: adminManager.Policy): Array\<string>;|api/@ohos.enterprise.telephonyManager.d.ts|
|新增API|NA|类名：adminManager；<br>API声明：export enum AdminType<br>差异内容：export enum AdminType|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：AdminType；<br>API声明：ADMIN_TYPE_BYOD = 0x02<br>差异内容：ADMIN_TYPE_BYOD = 0x02|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：ManagedEvent；<br>API声明：MANAGED_EVENT_ACCOUNT_ADDED = 5<br>差异内容：MANAGED_EVENT_ACCOUNT_ADDED = 5|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：ManagedEvent；<br>API声明：MANAGED_EVENT_ACCOUNT_SWITCHED = 6<br>差异内容：MANAGED_EVENT_ACCOUNT_SWITCHED = 6|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：ManagedEvent；<br>API声明：MANAGED_EVENT_ACCOUNT_REMOVED = 7<br>差异内容：MANAGED_EVENT_ACCOUNT_REMOVED = 7|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：adminManager；<br>API声明：export enum Policy<br>差异内容：export enum Policy|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：Policy；<br>API声明：BLOCK_LIST = 0<br>差异内容：BLOCK_LIST = 0|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：Policy；<br>API声明：TRUST_LIST = 1<br>差异内容：TRUST_LIST = 1|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：adminManager；<br>API声明：function isByodAdmin(admin: Want): boolean;<br>差异内容：function isByodAdmin(admin: Want): boolean;|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：adminManager；<br>API声明：function startAdminProvision(admin: Want, type: AdminType, context: common.Context, parameters: Record\<string, string>): void;<br>差异内容：function startAdminProvision(admin: Want, type: AdminType, context: common.Context, parameters: Record\<string, string>): void;|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function addAutoStartApps(admin: Want, autoStartApps: Array\<Want>, accountId: number, disallowModify: boolean): void;<br>差异内容：function addAutoStartApps(admin: Want, autoStartApps: Array\<Want>, accountId: number, disallowModify: boolean): void;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function removeAutoStartApps(admin: Want, autoStartApps: Array\<Want>, accountId: number): void;<br>差异内容：function removeAutoStartApps(admin: Want, autoStartApps: Array\<Want>, accountId: number): void;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function getAutoStartApps(admin: Want, accountId: number): Array\<Want>;<br>差异内容：function getAutoStartApps(admin: Want, accountId: number): Array\<Want>;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：enum KioskFeature<br>差异内容：enum KioskFeature|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：KioskFeature；<br>API声明：ALLOW_NOTIFICATION_CENTER = 1<br>差异内容：ALLOW_NOTIFICATION_CENTER = 1|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：KioskFeature；<br>API声明：ALLOW_CONTROL_CENTER = 2<br>差异内容：ALLOW_CONTROL_CENTER = 2|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function isModifyAutoStartAppsDisallowed(admin: Want, autoStartApp: Want, accountId: number): boolean;<br>差异内容：function isModifyAutoStartAppsDisallowed(admin: Want, autoStartApp: Want, accountId: number): boolean;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function isModifyKeepAliveAppsDisallowed(admin: Want, accountId: number, bundleName: string): boolean;<br>差异内容：function isModifyKeepAliveAppsDisallowed(admin: Want, accountId: number, bundleName: string): boolean;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function clearUpApplicationData(admin: Want, bundleName: string, appIndex: number, accountId: number): void;<br>差异内容：function clearUpApplicationData(admin: Want, bundleName: string, appIndex: number, accountId: number): void;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function setAllowedKioskApps(admin: Want, appIdentifiers: Array\<string>): void;<br>差异内容：function setAllowedKioskApps(admin: Want, appIdentifiers: Array\<string>): void;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function getAllowedKioskApps(admin: Want): Array\<string>;<br>差异内容：function getAllowedKioskApps(admin: Want): Array\<string>;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function isAppKioskAllowed(appIdentifier: string): boolean;<br>差异内容：function isAppKioskAllowed(appIdentifier: string): boolean;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function setKioskFeatures(admin: Want, features: Array\<KioskFeature>): void;<br>差异内容：function setKioskFeatures(admin: Want, features: Array\<KioskFeature>): void;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：restrictions；<br>API声明：function setUserRestriction(admin: Want, settingsItem: string, restricted: boolean): void;<br>差异内容：function setUserRestriction(admin: Want, settingsItem: string, restricted: boolean): void;|api/@ohos.enterprise.restrictions.d.ts|
|新增API|NA|类名：restrictions；<br>API声明：function getUserRestricted(admin: Want, settingsItem: string): boolean;<br>差异内容：function getUserRestricted(admin: Want, settingsItem: string): boolean;|api/@ohos.enterprise.restrictions.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function installUserCertificate(admin: Want, certificate: CertBlob, accountId: number): string;<br>差异内容：function installUserCertificate(admin: Want, certificate: CertBlob, accountId: number): string;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function setAppClipboardPolicy(admin: Want, bundleName: string, accountId: number, policy: ClipboardPolicy): void;<br>差异内容：function setAppClipboardPolicy(admin: Want, bundleName: string, accountId: number, policy: ClipboardPolicy): void;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function getAppClipboardPolicy(admin: Want, bundleName: string, accountId: number): string;<br>差异内容：function getAppClipboardPolicy(admin: Want, bundleName: string, accountId: number): string;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：export interface ApplicationInstance<br>差异内容：export interface ApplicationInstance|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：ApplicationInstance；<br>API声明：appIdentifier: string;<br>差异内容：appIdentifier: string;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：ApplicationInstance；<br>API声明：accountId: number;<br>差异内容：accountId: number;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：ApplicationInstance；<br>API声明：appIndex: number;<br>差异内容：appIndex: number;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function getUserCertificates(admin: Want, accountId: number): Array\<string>;<br>差异内容：function getUserCertificates(admin: Want, accountId: number): Array\<string>;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function setPermissionManagedState(admin: Want, applicationInstance: ApplicationInstance, permissions: Array\<string>, managedState: PermissionManagedState): void;<br>差异内容：function setPermissionManagedState(admin: Want, applicationInstance: ApplicationInstance, permissions: Array\<string>, managedState: PermissionManagedState): void;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function getPermissionManagedState(admin: Want, applicationInstance: ApplicationInstance, permission: string): PermissionManagedState;<br>差异内容：function getPermissionManagedState(admin: Want, applicationInstance: ApplicationInstance, permission: string): PermissionManagedState;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：export enum PermissionManagedState<br>差异内容：export enum PermissionManagedState|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：PermissionManagedState；<br>API声明：DEFAULT = 1<br>差异内容：DEFAULT = 1|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：PermissionManagedState；<br>API声明：GRANTED = 0<br>差异内容：GRANTED = 0|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：PermissionManagedState；<br>API声明：DENIED = -1<br>差异内容：DENIED = -1|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：accountManager；<br>API声明：interface DomainAccountPolicy<br>差异内容：interface DomainAccountPolicy|api/@ohos.enterprise.accountManager.d.ts|
|新增API|NA|类名：DomainAccountPolicy；<br>API声明：authenticationValidityPeriod?: number;<br>差异内容：authenticationValidityPeriod?: number;|api/@ohos.enterprise.accountManager.d.ts|
|新增API|NA|类名：DomainAccountPolicy；<br>API声明：passwordValidityPeriod?: number;<br>差异内容：passwordValidityPeriod?: number;|api/@ohos.enterprise.accountManager.d.ts|
|新增API|NA|类名：DomainAccountPolicy；<br>API声明：passwordExpirationNotification?: number;<br>差异内容：passwordExpirationNotification?: number;|api/@ohos.enterprise.accountManager.d.ts|
|新增API|NA|类名：accountManager；<br>API声明：function setDomainAccountPolicy(admin: Want, domainAccountInfo: osAccount.DomainAccountInfo, policy: DomainAccountPolicy): void;<br>差异内容：function setDomainAccountPolicy(admin: Want, domainAccountInfo: osAccount.DomainAccountInfo, policy: DomainAccountPolicy): void;|api/@ohos.enterprise.accountManager.d.ts|
|新增API|NA|类名：accountManager；<br>API声明：function getDomainAccountPolicy(admin: Want, domainAccountInfo: osAccount.DomainAccountInfo): DomainAccountPolicy;<br>差异内容：function getDomainAccountPolicy(admin: Want, domainAccountInfo: osAccount.DomainAccountInfo): DomainAccountPolicy;|api/@ohos.enterprise.accountManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：export enum Protocol<br>差异内容：export enum Protocol|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：Protocol；<br>API声明：GATT = 0<br>差异内容：GATT = 0|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：Protocol；<br>API声明：SPP = 1<br>差异内容：SPP = 1|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：Protocol；<br>API声明：OPP = 2<br>差异内容：OPP = 2|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function turnOnBluetooth(admin: Want): void;<br>差异内容：function turnOnBluetooth(admin: Want): void;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function turnOffBluetooth(admin: Want): void;<br>差异内容：function turnOffBluetooth(admin: Want): void;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function addDisallowedBluetoothDevices(admin: Want, deviceIds: Array\<string>): void;<br>差异内容：function addDisallowedBluetoothDevices(admin: Want, deviceIds: Array\<string>): void;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function removeDisallowedBluetoothDevices(admin: Want, deviceIds: Array\<string>): void;<br>差异内容：function removeDisallowedBluetoothDevices(admin: Want, deviceIds: Array\<string>): void;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getDisallowedBluetoothDevices(admin: Want): Array\<string>;<br>差异内容：function getDisallowedBluetoothDevices(admin: Want): Array\<string>;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function addDisallowedBluetoothProtocols(admin: Want, accountId: number, protocols: Array\<Protocol>): void;<br>差异内容：function addDisallowedBluetoothProtocols(admin: Want, accountId: number, protocols: Array\<Protocol>): void;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function removeDisallowedBluetoothProtocols(admin: Want, accountId: number, protocols: Array\<Protocol>): void;<br>差异内容：function removeDisallowedBluetoothProtocols(admin: Want, accountId: number, protocols: Array\<Protocol>): void;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getDisallowedBluetoothProtocols(admin: Want, accountId: number): Array\<Protocol>;<br>差异内容：function getDisallowedBluetoothProtocols(admin: Want, accountId: number): Array\<Protocol>;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：browser；<br>API声明：function setManagedBrowserPolicy(admin: Want, bundleName: string, policyName: string, policyValue: string): void;<br>差异内容：function setManagedBrowserPolicy(admin: Want, bundleName: string, policyName: string, policyValue: string): void;|api/@ohos.enterprise.browser.d.ts|
|新增API|NA|类名：browser；<br>API声明：function getManagedBrowserPolicy(admin: Want, bundleName: string): ArrayBuffer;<br>差异内容：function getManagedBrowserPolicy(admin: Want, bundleName: string): ArrayBuffer;|api/@ohos.enterprise.browser.d.ts|
|新增API|NA|类名：browser；<br>API声明：function getSelfManagedBrowserPolicyVersion(): string;<br>差异内容：function getSelfManagedBrowserPolicyVersion(): string;|api/@ohos.enterprise.browser.d.ts|
|新增API|NA|类名：browser；<br>API声明：function getSelfManagedBrowserPolicy(): ArrayBuffer;<br>差异内容：function getSelfManagedBrowserPolicy(): ArrayBuffer;|api/@ohos.enterprise.browser.d.ts|
|新增API|NA|类名：InstallParam；<br>API声明：parameters?: Record\<string, string>;<br>差异内容：parameters?: Record\<string, string>;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：interface Resource<br>差异内容：interface Resource|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：Resource；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：Resource；<br>API声明：moduleName: string;<br>差异内容：moduleName: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：Resource；<br>API声明：id: number;<br>差异内容：id: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：interface BundleInfo<br>差异内容：interface BundleInfo|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：BundleInfo；<br>API声明：readonly name: string;<br>差异内容：readonly name: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：BundleInfo；<br>API声明：readonly vendor: string;<br>差异内容：readonly vendor: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：BundleInfo；<br>API声明：readonly versionCode: number;<br>差异内容：readonly versionCode: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：BundleInfo；<br>API声明：readonly versionName: string;<br>差异内容：readonly versionName: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：BundleInfo；<br>API声明：readonly minCompatibleVersionCode: number;<br>差异内容：readonly minCompatibleVersionCode: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：BundleInfo；<br>API声明：readonly targetVersion: number;<br>差异内容：readonly targetVersion: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：BundleInfo；<br>API声明：readonly appInfo: ApplicationInfo;<br>差异内容：readonly appInfo: ApplicationInfo;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：BundleInfo；<br>API声明：readonly signatureInfo: SignatureInfo;<br>差异内容：readonly signatureInfo: SignatureInfo;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：BundleInfo；<br>API声明：readonly installTime: number;<br>差异内容：readonly installTime: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：BundleInfo；<br>API声明：readonly updateTime: number;<br>差异内容：readonly updateTime: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：BundleInfo；<br>API声明：readonly appIndex: number;<br>差异内容：readonly appIndex: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：BundleInfo；<br>API声明：readonly firstInstallTime?: number;<br>差异内容：readonly firstInstallTime?: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：interface SignatureInfo<br>差异内容：interface SignatureInfo|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：SignatureInfo；<br>API声明：readonly appId: string;<br>差异内容：readonly appId: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：SignatureInfo；<br>API声明：readonly fingerprint: string;<br>差异内容：readonly fingerprint: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：SignatureInfo；<br>API声明：readonly appIdentifier: string;<br>差异内容：readonly appIdentifier: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：SignatureInfo；<br>API声明：readonly certificate?: string;<br>差异内容：readonly certificate?: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：interface ApplicationInfo<br>差异内容：interface ApplicationInfo|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly name: string;<br>差异内容：readonly name: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly description: string;<br>差异内容：readonly description: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly descriptionId: number;<br>差异内容：readonly descriptionId: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly enabled: boolean;<br>差异内容：readonly enabled: boolean;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly label: string;<br>差异内容：readonly label: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly labelId: number;<br>差异内容：readonly labelId: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly icon: string;<br>差异内容：readonly icon: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly iconId: number;<br>差异内容：readonly iconId: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly process: string;<br>差异内容：readonly process: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly codePath: string;<br>差异内容：readonly codePath: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly removable: boolean;<br>差异内容：readonly removable: boolean;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly accessTokenId: number;<br>差异内容：readonly accessTokenId: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly uid: number;<br>差异内容：readonly uid: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly iconResource: Resource;<br>差异内容：readonly iconResource: Resource;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly labelResource: Resource;<br>差异内容：readonly labelResource: Resource;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly descriptionResource: Resource;<br>差异内容：readonly descriptionResource: Resource;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly appDistributionType: string;<br>差异内容：readonly appDistributionType: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly appProvisionType: string;<br>差异内容：readonly appProvisionType: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly systemApp: boolean;<br>差异内容：readonly systemApp: boolean;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly debug: boolean;<br>差异内容：readonly debug: boolean;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly dataUnclearable: boolean;<br>差异内容：readonly dataUnclearable: boolean;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly nativeLibraryPath: string;<br>差异内容：readonly nativeLibraryPath: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly appIndex: number;<br>差异内容：readonly appIndex: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly installSource: string;<br>差异内容：readonly installSource: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：ApplicationInfo；<br>API声明：readonly releaseType: string;<br>差异内容：readonly releaseType: string;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getInstalledBundleList(admin: Want, accountId: number): Promise\<Array\<BundleInfo>>;<br>差异内容：function getInstalledBundleList(admin: Want, accountId: number): Promise\<Array\<BundleInfo>>;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function addInstallationAllowedAppDistributionTypes(admin: Want, appDistributionTypes: Array\<AppDistributionType>): void;<br>差异内容：function addInstallationAllowedAppDistributionTypes(admin: Want, appDistributionTypes: Array\<AppDistributionType>): void;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function removeInstallationAllowedAppDistributionTypes(admin: Want, appDistributionTypes: Array\<AppDistributionType>): void;<br>差异内容：function removeInstallationAllowedAppDistributionTypes(admin: Want, appDistributionTypes: Array\<AppDistributionType>): void;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getInstallationAllowedAppDistributionTypes(admin: Want): Array\<AppDistributionType>;<br>差异内容：function getInstallationAllowedAppDistributionTypes(admin: Want): Array\<AppDistributionType>;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：enum AppDistributionType<br>差异内容：enum AppDistributionType|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：AppDistributionType；<br>API声明：APP_GALLERY = 1<br>差异内容：APP_GALLERY = 1|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：AppDistributionType；<br>API声明：ENTERPRISE = 2<br>差异内容：ENTERPRISE = 2|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：AppDistributionType；<br>API声明：ENTERPRISE_NORMAL = 3<br>差异内容：ENTERPRISE_NORMAL = 3|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：AppDistributionType；<br>API声明：ENTERPRISE_MDM = 4<br>差异内容：ENTERPRISE_MDM = 4|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：AppDistributionType；<br>API声明：INTERNALTESTING = 5<br>差异内容：INTERNALTESTING = 5|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：AppDistributionType；<br>API声明：CROWDTESTING = 6<br>差异内容：CROWDTESTING = 6|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：deviceSettings；<br>API声明：function setHomeWallpaper(admin: Want, fd: number): Promise\<void>;<br>差异内容：function setHomeWallpaper(admin: Want, fd: number): Promise\<void>;|api/@ohos.enterprise.deviceSettings.d.ts|
|新增API|NA|类名：deviceSettings；<br>API声明：function setUnlockWallpaper(admin: Want, fd: number): Promise\<void>;<br>差异内容：function setUnlockWallpaper(admin: Want, fd: number): Promise\<void>;|api/@ohos.enterprise.deviceSettings.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onAccountAdded(accountId: number): void;<br>差异内容：onAccountAdded(accountId: number): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onAccountSwitched(accountId: number): void;<br>差异内容：onAccountSwitched(accountId: number): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onAccountRemoved(accountId: number): void;<br>差异内容：onAccountRemoved(accountId: number): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onKioskModeEntering(bundleName: string, accountId: number): void;<br>差异内容：onKioskModeEntering(bundleName: string, accountId: number): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onKioskModeExiting(bundleName: string, accountId: number): void;<br>差异内容：onKioskModeExiting(bundleName: string, accountId: number): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：Direction；<br>API声明：FORWARD = 2<br>差异内容：FORWARD = 2|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：Action；<br>API声明：REJECT = 2<br>差异内容：REJECT = 2|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：DomainFilterRule；<br>API声明：direction?: Direction;<br>差异内容：direction?: Direction;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function setGlobalProxyForAccount(admin: Want, httpProxy: connection.HttpProxy, accountId: number): void;<br>差异内容：function setGlobalProxyForAccount(admin: Want, httpProxy: connection.HttpProxy, accountId: number): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function getGlobalProxyForAccount(admin: Want \| null, accountId: number): connection.HttpProxy;<br>差异内容：function getGlobalProxyForAccount(admin: Want \| null, accountId: number): connection.HttpProxy;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function turnOnMobileData(admin: Want, isForce: boolean): void;<br>差异内容：function turnOnMobileData(admin: Want, isForce: boolean): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function turnOffMobileData(admin: Want): void;<br>差异内容：function turnOffMobileData(admin: Want): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function addApn(admin: Want, apnInfo: Record\<string, string>): void;<br>差异内容：function addApn(admin: Want, apnInfo: Record\<string, string>): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function deleteApn(admin: Want, apnId: string): void;<br>差异内容：function deleteApn(admin: Want, apnId: string): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function updateApn(admin: Want, apnInfo: Record\<string, string>, apnId: string): void;<br>差异内容：function updateApn(admin: Want, apnInfo: Record\<string, string>, apnId: string): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function setPreferredApn(admin: Want, apnId: string): void;<br>差异内容：function setPreferredApn(admin: Want, apnId: string): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function queryApn(admin: Want, apnInfo: Record\<string, string>): Array\<string>;<br>差异内容：function queryApn(admin: Want, apnInfo: Record\<string, string>): Array\<string>;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function queryApn(admin: Want, apnId: string): Record\<string, string>;<br>差异内容：function queryApn(admin: Want, apnId: string): Record\<string, string>;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：OtaUpdatePolicy；<br>API声明：disableSystemOtaUpdate?: boolean;<br>差异内容：disableSystemOtaUpdate?: boolean;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：UpdatePackageInfo；<br>API声明：authInfo?: string;<br>差异内容：authInfo?: string;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function getUpdateAuthData(admin: Want): Promise\<string>;<br>差异内容：function getUpdateAuthData(admin: Want): Promise\<string>;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function setAutoUnlockAfterReboot(admin: Want, isAllowed: boolean): void;<br>差异内容：function setAutoUnlockAfterReboot(admin: Want, isAllowed: boolean): void;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function getAutoUnlockAfterReboot(admin: Want): boolean;<br>差异内容：function getAutoUnlockAfterReboot(admin: Want): boolean;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function setInstallLocalEnterpriseAppEnabled(admin: Want, isEnable: boolean): void;<br>差异内容：function setInstallLocalEnterpriseAppEnabled(admin: Want, isEnable: boolean): void;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function getInstallLocalEnterpriseAppEnabled(admin: Want): boolean;<br>差异内容：function getInstallLocalEnterpriseAppEnabled(admin: Want): boolean;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：enum NearLinkProtocol<br>差异内容：enum NearLinkProtocol|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：NearLinkProtocol；<br>API声明：SSAP = 0<br>差异内容：SSAP = 0|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：NearLinkProtocol；<br>API声明：DATA_TRANSFER = 1<br>差异内容：DATA_TRANSFER = 1|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function addDisallowedNearLinkProtocols(admin: Want, protocols: Array\<NearLinkProtocol>, accountId: number): void;<br>差异内容：function addDisallowedNearLinkProtocols(admin: Want, protocols: Array\<NearLinkProtocol>, accountId: number): void;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function removeDisallowedNearLinkProtocols(admin: Want, protocols: Array\<NearLinkProtocol>, accountId: number): void;<br>差异内容：function removeDisallowedNearLinkProtocols(admin: Want, protocols: Array\<NearLinkProtocol>, accountId: number): void;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function getDisallowedNearLinkProtocols(admin: Want, accountId: number): Array\<NearLinkProtocol>;<br>差异内容：function getDisallowedNearLinkProtocols(admin: Want, accountId: number): Array\<NearLinkProtocol>;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface WifiAccessInfo<br>差异内容：interface WifiAccessInfo|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiAccessInfo；<br>API声明：ssid: string;<br>差异内容：ssid: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiAccessInfo；<br>API声明：bssid?: string;<br>差异内容：bssid?: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function addDisallowedWifiList(admin: Want, list: Array\<WifiAccessInfo>): void;<br>差异内容：function addDisallowedWifiList(admin: Want, list: Array\<WifiAccessInfo>): void;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function removeDisallowedWifiList(admin: Want, list: Array\<WifiAccessInfo>): void;<br>差异内容：function removeDisallowedWifiList(admin: Want, list: Array\<WifiAccessInfo>): void;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getDisallowedWifiList(admin: Want): Array\<WifiAccessInfo>;<br>差异内容：function getDisallowedWifiList(admin: Want): Array\<WifiAccessInfo>;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function addAllowedWifiList(admin: Want, list: Array\<WifiAccessInfo>): void;<br>差异内容：function addAllowedWifiList(admin: Want, list: Array\<WifiAccessInfo>): void;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function removeAllowedWifiList(admin: Want, list: Array\<WifiAccessInfo>): void;<br>差异内容：function removeAllowedWifiList(admin: Want, list: Array\<WifiAccessInfo>): void;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function getAllowedWifiList(admin: Want): Array\<WifiAccessInfo>;<br>差异内容：function getAllowedWifiList(admin: Want): Array\<WifiAccessInfo>;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function turnOnWifi(admin: Want, isForce: boolean): void;<br>差异内容：function turnOnWifi(admin: Want, isForce: boolean): void;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function turnOffWifi(admin: Want): void;<br>差异内容：function turnOffWifi(admin: Want): void;|api/@ohos.enterprise.wifiManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.telephonyManager.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.telephonyManager.d.ts|
