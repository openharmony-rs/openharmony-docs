| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace accountManager<br>Differences: declare namespace accountManager|api/@ohos.enterprise.accountManager.d.ts|
|New API |NA|Class name: accountManager;<br>API declaration: function disallowOsAccountAddition(admin: Want, disallow: boolean, accountId?: number): void;<br>Differences: function disallowOsAccountAddition(admin: Want, disallow: boolean, accountId?: number): void;|api/@ohos.enterprise.accountManager.d.ts|
|New API |NA|Class name: accountManager;<br>API declaration: function isOsAccountAdditionDisallowed(admin: Want, accountId?: number): boolean;<br>Differences: function isOsAccountAdditionDisallowed(admin: Want, accountId?: number): boolean;|api/@ohos.enterprise.accountManager.d.ts|
|New API |NA|Class name: accountManager;<br>API declaration: function addOsAccountAsync(admin: Want, name: string, type: osAccount.OsAccountType): Promise\<osAccount.OsAccountInfo>;<br>Differences: function addOsAccountAsync(admin: Want, name: string, type: osAccount.OsAccountType): Promise\<osAccount.OsAccountInfo>;|api/@ohos.enterprise.accountManager.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace adminManager<br>Differences: declare namespace adminManager|api/@ohos.enterprise.adminManager.d.ts|
|New API |NA|Class name: adminManager;<br>API declaration: export enum ManagedEvent<br>Differences: export enum ManagedEvent|api/@ohos.enterprise.adminManager.d.ts|
|New API |NA|Class name: ManagedEvent;<br>API declaration: MANAGED_EVENT_BUNDLE_ADDED = 0<br>Differences: MANAGED_EVENT_BUNDLE_ADDED = 0|api/@ohos.enterprise.adminManager.d.ts|
|New API |NA|Class name: ManagedEvent;<br>API declaration: MANAGED_EVENT_BUNDLE_REMOVED = 1<br>Differences: MANAGED_EVENT_BUNDLE_REMOVED = 1|api/@ohos.enterprise.adminManager.d.ts|
|New API |NA|Class name: ManagedEvent;<br>API declaration: MANAGED_EVENT_APP_START = 2<br>Differences: MANAGED_EVENT_APP_START = 2|api/@ohos.enterprise.adminManager.d.ts|
|New API |NA|Class name: ManagedEvent;<br>API declaration: MANAGED_EVENT_APP_STOP = 3<br>Differences: MANAGED_EVENT_APP_STOP = 3|api/@ohos.enterprise.adminManager.d.ts|
|New API |NA|Class name: ManagedEvent;<br>API declaration: MANAGED_EVENT_SYSTEM_UPDATE = 4<br>Differences: MANAGED_EVENT_SYSTEM_UPDATE = 4|api/@ohos.enterprise.adminManager.d.ts|
|New API |NA|Class name: adminManager;<br>API declaration: function disableAdmin(admin: Want, userId?: number): Promise\<void>;<br>Differences: function disableAdmin(admin: Want, userId?: number): Promise\<void>;|api/@ohos.enterprise.adminManager.d.ts|
|New API |NA|Class name: adminManager;<br>API declaration: function subscribeManagedEventSync(admin: Want, managedEvents: Array\<ManagedEvent>): void;<br>Differences: function subscribeManagedEventSync(admin: Want, managedEvents: Array\<ManagedEvent>): void;|api/@ohos.enterprise.adminManager.d.ts|
|New API |NA|Class name: adminManager;<br>API declaration: function unsubscribeManagedEventSync(admin: Want, managedEvents: Array\<ManagedEvent>): void;<br>Differences: function unsubscribeManagedEventSync(admin: Want, managedEvents: Array\<ManagedEvent>): void;|api/@ohos.enterprise.adminManager.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace applicationManager<br>Differences: declare namespace applicationManager|api/@ohos.enterprise.applicationManager.d.ts|
|New API |NA|Class name: applicationManager;<br>API declaration: function addDisallowedRunningBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>Differences: function addDisallowedRunningBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.applicationManager.d.ts|
|New API |NA|Class name: applicationManager;<br>API declaration: function removeDisallowedRunningBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>Differences: function removeDisallowedRunningBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.applicationManager.d.ts|
|New API |NA|Class name: applicationManager;<br>API declaration: function getDisallowedRunningBundlesSync(admin: Want, accountId?: number): Array\<string>;<br>Differences: function getDisallowedRunningBundlesSync(admin: Want, accountId?: number): Array\<string>;|api/@ohos.enterprise.applicationManager.d.ts|
|New API |NA|Class name: applicationManager;<br>API declaration: function addAutoStartApps(admin: Want, autoStartApps: Array\<Want>): void;<br>Differences: function addAutoStartApps(admin: Want, autoStartApps: Array\<Want>): void;|api/@ohos.enterprise.applicationManager.d.ts|
|New API |NA|Class name: applicationManager;<br>API declaration: function removeAutoStartApps(admin: Want, autoStartApps: Array\<Want>): void;<br>Differences: function removeAutoStartApps(admin: Want, autoStartApps: Array\<Want>): void;|api/@ohos.enterprise.applicationManager.d.ts|
|New API |NA|Class name: applicationManager;<br>API declaration: function getAutoStartApps(admin: Want): Array\<Want>;<br>Differences: function getAutoStartApps(admin: Want): Array\<Want>;|api/@ohos.enterprise.applicationManager.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace bluetoothManager<br>Differences: declare namespace bluetoothManager|api/@ohos.enterprise.bluetoothManager.d.ts|
|New API |NA|Class name: bluetoothManager;<br>API declaration: export interface BluetoothInfo<br>Differences: export interface BluetoothInfo|api/@ohos.enterprise.bluetoothManager.d.ts|
|New API |NA|Class name: BluetoothInfo;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.enterprise.bluetoothManager.d.ts|
|New API |NA|Class name: BluetoothInfo;<br>API declaration: state: access.BluetoothState;<br>Differences: state: access.BluetoothState;|api/@ohos.enterprise.bluetoothManager.d.ts|
|New API |NA|Class name: BluetoothInfo;<br>API declaration: connectionState: constant.ProfileConnectionState;<br>Differences: connectionState: constant.ProfileConnectionState;|api/@ohos.enterprise.bluetoothManager.d.ts|
|New API |NA|Class name: bluetoothManager;<br>API declaration: function getBluetoothInfo(admin: Want): BluetoothInfo;<br>Differences: function getBluetoothInfo(admin: Want): BluetoothInfo;|api/@ohos.enterprise.bluetoothManager.d.ts|
|New API |NA|Class name: bluetoothManager;<br>API declaration: function addAllowedBluetoothDevices(admin: Want, deviceIds: Array\<string>): void;<br>Differences: function addAllowedBluetoothDevices(admin: Want, deviceIds: Array\<string>): void;|api/@ohos.enterprise.bluetoothManager.d.ts|
|New API |NA|Class name: bluetoothManager;<br>API declaration: function removeAllowedBluetoothDevices(admin: Want, deviceIds: Array\<string>): void;<br>Differences: function removeAllowedBluetoothDevices(admin: Want, deviceIds: Array\<string>): void;|api/@ohos.enterprise.bluetoothManager.d.ts|
|New API |NA|Class name: bluetoothManager;<br>API declaration: function getAllowedBluetoothDevices(admin: Want): Array\<string>;<br>Differences: function getAllowedBluetoothDevices(admin: Want): Array\<string>;|api/@ohos.enterprise.bluetoothManager.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace browser<br>Differences: declare namespace browser|api/@ohos.enterprise.browser.d.ts|
|New API |NA|Class name: browser;<br>API declaration: function setPolicySync(admin: Want, appId: string, policyName: string, policyValue: string): void;<br>Differences: function setPolicySync(admin: Want, appId: string, policyName: string, policyValue: string): void;|api/@ohos.enterprise.browser.d.ts|
|New API |NA|Class name: browser;<br>API declaration: function getPoliciesSync(admin: Want, appId: string): string;<br>Differences: function getPoliciesSync(admin: Want, appId: string): string;|api/@ohos.enterprise.browser.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace bundleManager<br>Differences: declare namespace bundleManager|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: bundleManager;<br>API declaration: interface InstallParam<br>Differences: interface InstallParam|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: InstallParam;<br>API declaration: userId?: number;<br>Differences: userId?: number;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: InstallParam;<br>API declaration: installFlag?: number;<br>Differences: installFlag?: number;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: bundleManager;<br>API declaration: function addAllowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>Differences: function addAllowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: bundleManager;<br>API declaration: function removeAllowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>Differences: function removeAllowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: bundleManager;<br>API declaration: function getAllowedInstallBundlesSync(admin: Want, accountId?: number): Array\<string>;<br>Differences: function getAllowedInstallBundlesSync(admin: Want, accountId?: number): Array\<string>;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: bundleManager;<br>API declaration: function addDisallowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>Differences: function addDisallowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: bundleManager;<br>API declaration: function removeDisallowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>Differences: function removeDisallowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: bundleManager;<br>API declaration: function getDisallowedInstallBundlesSync(admin: Want, accountId?: number): Array\<string>;<br>Differences: function getDisallowedInstallBundlesSync(admin: Want, accountId?: number): Array\<string>;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: bundleManager;<br>API declaration: function addDisallowedUninstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>Differences: function addDisallowedUninstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: bundleManager;<br>API declaration: function removeDisallowedUninstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>Differences: function removeDisallowedUninstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: bundleManager;<br>API declaration: function getDisallowedUninstallBundlesSync(admin: Want, accountId?: number): Array\<string>;<br>Differences: function getDisallowedUninstallBundlesSync(admin: Want, accountId?: number): Array\<string>;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: bundleManager;<br>API declaration: function uninstall(admin: Want, bundleName: string, userId?: number, isKeepData?: boolean): Promise\<void>;<br>Differences: function uninstall(admin: Want, bundleName: string, userId?: number, isKeepData?: boolean): Promise\<void>;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: bundleManager;<br>API declaration: function install(admin: Want, hapFilePaths: Array\<string>, installParam?: InstallParam): Promise\<void>;<br>Differences: function install(admin: Want, hapFilePaths: Array\<string>, installParam?: InstallParam): Promise\<void>;|api/@ohos.enterprise.bundleManager.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace deviceControl<br>Differences: declare namespace deviceControl|api/@ohos.enterprise.deviceControl.d.ts|
|New API|NA|Class name: deviceControl;<br>API declaration: function operateDevice(admin: Want, operate: string, addition?: string): void;<br>Differences: function operateDevice(admin: Want, operate: string, addition?: string): void;|api/@ohos.enterprise.deviceControl.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace deviceInfo<br>Differences: declare namespace deviceInfo|api/@ohos.enterprise.deviceInfo.d.ts|
|New API|NA|Class name: deviceInfo;<br>API declaration: function getDeviceInfo(admin: Want, label: string): string;<br>Differences: function getDeviceInfo(admin: Want, label: string): string;|api/@ohos.enterprise.deviceInfo.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace deviceSettings<br>Differences: declare namespace deviceSettings|api/@ohos.enterprise.deviceSettings.d.ts|
|New API|NA|Class name: deviceSettings;<br>API declaration: function setValue(admin: Want, item: string, value: string): void;<br>Differences: function setValue(admin: Want, item: string, value: string): void;|api/@ohos.enterprise.deviceSettings.d.ts|
|New API|NA|Class name: deviceSettings;<br>API declaration: function getValue(admin: Want, item: string): string;<br>Differences: function getValue(admin: Want, item: string): string;|api/@ohos.enterprise.deviceSettings.d.ts|
|New API|NA|Class name: global;<br>API declaration: export default class EnterpriseAdminExtensionAbility<br>Differences: export default class EnterpriseAdminExtensionAbility|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|New API|NA|Class name: EnterpriseAdminExtensionAbility;<br>API declaration: onAdminEnabled(): void;<br>Differences: onAdminEnabled(): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|New API|NA|Class name: EnterpriseAdminExtensionAbility;<br>API declaration: onAdminDisabled(): void;<br>Differences: onAdminDisabled(): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|New API|NA|Class name: EnterpriseAdminExtensionAbility;<br>API declaration: onBundleAdded(bundleName: string): void;<br>Differences: onBundleAdded(bundleName: string): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|New API|NA|Class name: EnterpriseAdminExtensionAbility;<br>API declaration: onBundleRemoved(bundleName: string): void;<br>Differences: onBundleRemoved(bundleName: string): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|New API|NA|Class name: EnterpriseAdminExtensionAbility;<br>API declaration: onAppStart(bundleName: string): void;<br>Differences: onAppStart(bundleName: string): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|New API|NA|Class name: EnterpriseAdminExtensionAbility;<br>API declaration: onAppStop(bundleName: string): void;<br>Differences: onAppStop(bundleName: string): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|New API|NA|Class name: EnterpriseAdminExtensionAbility;<br>API declaration: onSystemUpdate(systemUpdateInfo: systemManager.SystemUpdateInfo): void;<br>Differences: onSystemUpdate(systemUpdateInfo: systemManager.SystemUpdateInfo): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|New API|NA|Class name: EnterpriseAdminExtensionAbility;<br>API declaration: onStart(): void;<br>Differences: onStart(): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace locationManager<br>Differences: declare namespace locationManager|api/@ohos.enterprise.locationManager.d.ts|
|New API|NA|Class name: locationManager;<br>API declaration: export enum LocationPolicy<br>Differences: export enum LocationPolicy|api/@ohos.enterprise.locationManager.d.ts|
|New API|NA|Class name: LocationPolicy;<br>API declaration: DEFAULT_LOCATION_SERVICE = 0<br>Differences: DEFAULT_LOCATION_SERVICE = 0|api/@ohos.enterprise.locationManager.d.ts|
|New API|NA|Class name: LocationPolicy;<br>API declaration: DISALLOW_LOCATION_SERVICE = 1<br>Differences: DISALLOW_LOCATION_SERVICE = 1|api/@ohos.enterprise.locationManager.d.ts|
|New API|NA|Class name: LocationPolicy;<br>API declaration: FORCE_OPEN_LOCATION_SERVICE = 2<br>Differences: FORCE_OPEN_LOCATION_SERVICE = 2|api/@ohos.enterprise.locationManager.d.ts|
|New API|NA|Class name: locationManager;<br>API declaration: function setLocationPolicy(admin: Want, policy: LocationPolicy): void;<br>Differences: function setLocationPolicy(admin: Want, policy: LocationPolicy): void;|api/@ohos.enterprise.locationManager.d.ts|
|New API|NA|Class name: locationManager;<br>API declaration: function getLocationPolicy(admin: Want): LocationPolicy;<br>Differences: function getLocationPolicy(admin: Want): LocationPolicy;|api/@ohos.enterprise.locationManager.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace networkManager<br>Differences: declare namespace networkManager|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: enum Direction<br>Differences: enum Direction|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: Direction;<br>API declaration: INPUT = 0<br>Differences: INPUT = 0|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: Direction;<br>API declaration: OUTPUT = 1<br>Differences: OUTPUT = 1|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: enum Action<br>Differences: enum Action|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: Action;<br>API declaration: ALLOW = 0<br>Differences: ALLOW = 0|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: Action;<br>API declaration: DENY = 1<br>Differences: DENY = 1|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: enum Protocol<br>Differences: enum Protocol|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: Protocol;<br>API declaration: ALL = 0<br>Differences: ALL = 0|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: Protocol;<br>API declaration: TCP = 1<br>Differences: TCP = 1|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: Protocol;<br>API declaration: UDP = 2<br>Differences: UDP = 2|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: Protocol;<br>API declaration: ICMP = 3<br>Differences: ICMP = 3|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: interface FirewallRule<br>Differences: interface FirewallRule|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: FirewallRule;<br>API declaration: srcAddr?: string;<br>Differences: srcAddr?: string;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: FirewallRule;<br>API declaration: destAddr?: string;<br>Differences: destAddr?: string;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: FirewallRule;<br>API declaration: srcPort?: string;<br>Differences: srcPort?: string;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: FirewallRule;<br>API declaration: destPort?: string;<br>Differences: destPort?: string;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: FirewallRule;<br>API declaration: appUid?: string;<br>Differences: appUid?: string;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: FirewallRule;<br>API declaration: direction?: Direction;<br>Differences: direction?: Direction;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: FirewallRule;<br>API declaration: action?: Action;<br>Differences: action?: Action;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: FirewallRule;<br>API declaration: protocol?: Protocol;<br>Differences: protocol?: Protocol;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: interface DomainFilterRule<br>Differences: interface DomainFilterRule|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: DomainFilterRule;<br>API declaration: domainName?: string;<br>Differences: domainName?: string;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: DomainFilterRule;<br>API declaration: appUid?: string;<br>Differences: appUid?: string;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: DomainFilterRule;<br>API declaration: action?: Action;<br>Differences: action?: Action;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function getAllNetworkInterfacesSync(admin: Want): Array\<string>;<br>Differences: function getAllNetworkInterfacesSync(admin: Want): Array\<string>;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function getIpAddressSync(admin: Want, networkInterface: string): string;<br>Differences: function getIpAddressSync(admin: Want, networkInterface: string): string;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function getMacSync(admin: Want, networkInterface: string): string;<br>Differences: function getMacSync(admin: Want, networkInterface: string): string;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function isNetworkInterfaceDisabledSync(admin: Want, networkInterface: string): boolean;<br>Differences: function isNetworkInterfaceDisabledSync(admin: Want, networkInterface: string): boolean;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function setNetworkInterfaceDisabledSync(admin: Want, networkInterface: string, isDisabled: boolean): void;<br>Differences: function setNetworkInterfaceDisabledSync(admin: Want, networkInterface: string, isDisabled: boolean): void;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function setGlobalProxySync(admin: Want, httpProxy: connection.HttpProxy): void;<br>Differences: function setGlobalProxySync(admin: Want, httpProxy: connection.HttpProxy): void;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function getGlobalProxySync(admin: Want): connection.HttpProxy;<br>Differences: function getGlobalProxySync(admin: Want): connection.HttpProxy;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function addFirewallRule(admin: Want, firewallRule: FirewallRule): void;<br>Differences: function addFirewallRule(admin: Want, firewallRule: FirewallRule): void;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function removeFirewallRule(admin: Want, firewallRule?: FirewallRule): void;<br>Differences: function removeFirewallRule(admin: Want, firewallRule?: FirewallRule): void;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function getFirewallRules(admin: Want): Array\<FirewallRule>;<br>Differences: function getFirewallRules(admin: Want): Array\<FirewallRule>;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function addDomainFilterRule(admin: Want, domainFilterRule: DomainFilterRule): void;<br>Differences: function addDomainFilterRule(admin: Want, domainFilterRule: DomainFilterRule): void;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function removeDomainFilterRule(admin: Want, domainFilterRule?: DomainFilterRule): void;<br>Differences: function removeDomainFilterRule(admin: Want, domainFilterRule?: DomainFilterRule): void;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: networkManager;<br>API declaration: function getDomainFilterRules(admin: Want): Array\<DomainFilterRule>;<br>Differences: function getDomainFilterRules(admin: Want): Array\<DomainFilterRule>;|api/@ohos.enterprise.networkManager.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace restrictions<br>Differences: declare namespace restrictions|api/@ohos.enterprise.restrictions.d.ts|
|New API|NA|Class name: restrictions;<br>API declaration: function setDisallowedPolicy(admin: Want, feature: string, disallow: boolean): void;<br>Differences: function setDisallowedPolicy(admin: Want, feature: string, disallow: boolean): void;|api/@ohos.enterprise.restrictions.d.ts|
|New API|NA|Class name: restrictions;<br>API declaration: function getDisallowedPolicy(admin: Want, feature: string): boolean;<br>Differences: function getDisallowedPolicy(admin: Want, feature: string): boolean;|api/@ohos.enterprise.restrictions.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace securityManager<br>Differences: declare namespace securityManager|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: securityManager;<br>API declaration: export interface CertBlob<br>Differences: export interface CertBlob|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: CertBlob;<br>API declaration: inData: Uint8Array;<br>Differences: inData: Uint8Array;|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: CertBlob;<br>API declaration: alias: string;<br>Differences: alias: string;|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: securityManager;<br>API declaration: function getSecurityStatus(admin: Want, item: string): string;<br>Differences: function getSecurityStatus(admin: Want, item: string): string;|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: securityManager;<br>API declaration: function installUserCertificate(admin: Want, certificate: CertBlob): Promise\<string>;<br>Differences: function installUserCertificate(admin: Want, certificate: CertBlob): Promise\<string>;|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: securityManager;<br>API declaration: function uninstallUserCertificate(admin: Want, certUri: string): Promise\<void>;<br>Differences: function uninstallUserCertificate(admin: Want, certUri: string): Promise\<void>;|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: securityManager;<br>API declaration: function setPasswordPolicy(admin: Want, policy: PasswordPolicy): void;<br>Differences: function setPasswordPolicy(admin: Want, policy: PasswordPolicy): void;|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: securityManager;<br>API declaration: function getPasswordPolicy(admin: Want): PasswordPolicy;<br>Differences: function getPasswordPolicy(admin: Want): PasswordPolicy;|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: securityManager;<br>API declaration: function setAppClipboardPolicy(admin: Want, tokenId: number, policy: ClipboardPolicy): void;<br>Differences: function setAppClipboardPolicy(admin: Want, tokenId: number, policy: ClipboardPolicy): void;|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: securityManager;<br>API declaration: function getAppClipboardPolicy(admin: Want, tokenId?: number): string;<br>Differences: function getAppClipboardPolicy(admin: Want, tokenId?: number): string;|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: securityManager;<br>API declaration: export interface PasswordPolicy<br>Differences: export interface PasswordPolicy|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: PasswordPolicy;<br>API declaration: complexityRegex?: string;<br>Differences: complexityRegex?: string;|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: PasswordPolicy;<br>API declaration: validityPeriod?: number;<br>Differences: validityPeriod?: number;|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: PasswordPolicy;<br>API declaration: additionalDescription?: string;<br>Differences: additionalDescription?: string;|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: securityManager;<br>API declaration: export enum ClipboardPolicy<br>Differences: export enum ClipboardPolicy|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: ClipboardPolicy;<br>API declaration: DEFAULT = 0<br>Differences: DEFAULT = 0|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: ClipboardPolicy;<br>API declaration: IN_APP = 1<br>Differences: IN_APP = 1|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: ClipboardPolicy;<br>API declaration: LOCAL_DEVICE = 2<br>Differences: LOCAL_DEVICE = 2|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: ClipboardPolicy;<br>API declaration: CROSS_DEVICE = 3<br>Differences: CROSS_DEVICE = 3|api/@ohos.enterprise.securityManager.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace systemManager<br>Differences: declare namespace systemManager|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: export interface SystemUpdateInfo<br>Differences: export interface SystemUpdateInfo|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: SystemUpdateInfo;<br>API declaration: versionName: string;<br>Differences: versionName: string;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: SystemUpdateInfo;<br>API declaration: firstReceivedTime: number;<br>Differences: firstReceivedTime: number;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: SystemUpdateInfo;<br>API declaration: packageType: string;<br>Differences: packageType: string;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: enum PolicyType<br>Differences: enum PolicyType|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: PolicyType;<br>API declaration: DEFAULT = 0<br>Differences: DEFAULT = 0|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: PolicyType;<br>API declaration: PROHIBIT = 1<br>Differences: PROHIBIT = 1|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: PolicyType;<br>API declaration: UPDATE_TO_SPECIFIC_VERSION = 2<br>Differences: UPDATE_TO_SPECIFIC_VERSION = 2|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: PolicyType;<br>API declaration: WINDOWS = 3<br>Differences: WINDOWS = 3|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: PolicyType;<br>API declaration: POSTPONE = 4<br>Differences: POSTPONE = 4|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: export interface OtaUpdatePolicy<br>Differences: export interface OtaUpdatePolicy|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: OtaUpdatePolicy;<br>API declaration: policyType: PolicyType;<br>Differences: policyType: PolicyType;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: OtaUpdatePolicy;<br>API declaration: version: string;<br>Differences: version: string;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: OtaUpdatePolicy;<br>API declaration: latestUpdateTime?: number;<br>Differences: latestUpdateTime?: number;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: OtaUpdatePolicy;<br>API declaration: delayUpdateTime?: number;<br>Differences: delayUpdateTime?: number;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: OtaUpdatePolicy;<br>API declaration: installStartTime?: number;<br>Differences: installStartTime?: number;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: OtaUpdatePolicy;<br>API declaration: installEndTime?: number;<br>Differences: installEndTime?: number;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: export interface UpdatePackageInfo<br>Differences: export interface UpdatePackageInfo|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: UpdatePackageInfo;<br>API declaration: version: string;<br>Differences: version: string;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: UpdatePackageInfo;<br>API declaration: packages: Array\<Package>;<br>Differences: packages: Array\<Package>;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: UpdatePackageInfo;<br>API declaration: description?: PackageDescription;<br>Differences: description?: PackageDescription;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: interface Package<br>Differences: interface Package|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: Package;<br>API declaration: type: PackageType;<br>Differences: type: PackageType;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: Package;<br>API declaration: path: string;<br>Differences: path: string;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: Package;<br>API declaration: fd?: number;<br>Differences: fd?: number;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: enum PackageType<br>Differences: enum PackageType|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: PackageType;<br>API declaration: FIRMWARE = 1<br>Differences: FIRMWARE = 1|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: interface PackageDescription<br>Differences: interface PackageDescription|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: PackageDescription;<br>API declaration: notify?: NotifyDescription;<br>Differences: notify?: NotifyDescription;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: interface NotifyDescription<br>Differences: interface NotifyDescription|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: NotifyDescription;<br>API declaration: installTips?: string;<br>Differences: installTips?: string;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: NotifyDescription;<br>API declaration: installTipsDetail?: string;<br>Differences: installTipsDetail?: string;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: interface UpdateResult<br>Differences: interface UpdateResult|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: UpdateResult;<br>API declaration: version: string;<br>Differences: version: string;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: UpdateResult;<br>API declaration: status: UpdateStatus;<br>Differences: status: UpdateStatus;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: UpdateResult;<br>API declaration: errorInfo: ErrorInfo;<br>Differences: errorInfo: ErrorInfo;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: enum UpdateStatus<br>Differences: enum UpdateStatus|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: UpdateStatus;<br>API declaration: NO_UPDATE_PACKAGE = -4<br>Differences: NO_UPDATE_PACKAGE = -4|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: UpdateStatus;<br>API declaration: UPDATE_WAITING = -3<br>Differences: UPDATE_WAITING = -3|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: UpdateStatus;<br>API declaration: UPDATING = -2<br>Differences: UPDATING = -2|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: UpdateStatus;<br>API declaration: UPDATE_FAILURE = -1<br>Differences: UPDATE_FAILURE = -1|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: UpdateStatus;<br>API declaration: UPDATE_SUCCESS = 0<br>Differences: UPDATE_SUCCESS = 0|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: interface ErrorInfo<br>Differences: interface ErrorInfo|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: ErrorInfo;<br>API declaration: code: number;<br>Differences: code: number;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: ErrorInfo;<br>API declaration: message: string;<br>Differences: message: string;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: function setNTPServer(admin: Want, server: string): void;<br>Differences: function setNTPServer(admin: Want, server: string): void;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: function getNTPServer(admin: Want): string;<br>Differences: function getNTPServer(admin: Want): string;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: function setOtaUpdatePolicy(admin: Want, policy: OtaUpdatePolicy): void;<br>Differences: function setOtaUpdatePolicy(admin: Want, policy: OtaUpdatePolicy): void;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: function getOtaUpdatePolicy(admin: Want): OtaUpdatePolicy;<br>Differences: function getOtaUpdatePolicy(admin: Want): OtaUpdatePolicy;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: function notifyUpdatePackages(admin: Want, packageInfo: UpdatePackageInfo): Promise\<void>;<br>Differences: function notifyUpdatePackages(admin: Want, packageInfo: UpdatePackageInfo): Promise\<void>;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: systemManager;<br>API declaration: function getUpdateResult(admin: Want, version: string): Promise\<UpdateResult>;<br>Differences: function getUpdateResult(admin: Want, version: string): Promise\<UpdateResult>;|api/@ohos.enterprise.systemManager.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace usbManager<br>Differences: declare namespace usbManager|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: export enum UsbPolicy<br>Differences: export enum UsbPolicy|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: UsbPolicy;<br>API declaration: READ_WRITE = 0<br>Differences: READ_WRITE = 0|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: UsbPolicy;<br>API declaration: READ_ONLY = 1<br>Differences: READ_ONLY = 1|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: UsbPolicy;<br>API declaration: DISABLED = 2<br>Differences: DISABLED = 2|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: export interface UsbDeviceId<br>Differences: export interface UsbDeviceId|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: UsbDeviceId;<br>API declaration: vendorId: number;<br>Differences: vendorId: number;|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: UsbDeviceId;<br>API declaration: productId: number;<br>Differences: productId: number;|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function addAllowedUsbDevices(admin: Want, usbDeviceIds: Array\<UsbDeviceId>): void;<br>Differences: function addAllowedUsbDevices(admin: Want, usbDeviceIds: Array\<UsbDeviceId>): void;|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function removeAllowedUsbDevices(admin: Want, usbDeviceIds: Array\<UsbDeviceId>): void;<br>Differences: function removeAllowedUsbDevices(admin: Want, usbDeviceIds: Array\<UsbDeviceId>): void;|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function getAllowedUsbDevices(admin: Want): Array\<UsbDeviceId>;<br>Differences: function getAllowedUsbDevices(admin: Want): Array\<UsbDeviceId>;|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function setUsbStorageDeviceAccessPolicy(admin: Want, usbPolicy: UsbPolicy): void;<br>Differences: function setUsbStorageDeviceAccessPolicy(admin: Want, usbPolicy: UsbPolicy): void;|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: usbManager;<br>API declaration: function getUsbStorageDeviceAccessPolicy(admin: Want): UsbPolicy;<br>Differences: function getUsbStorageDeviceAccessPolicy(admin: Want): UsbPolicy;|api/@ohos.enterprise.usbManager.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace wifiManager<br>Differences: declare namespace wifiManager|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: wifiManager;<br>API declaration: enum WifiSecurityType<br>Differences: enum WifiSecurityType|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiSecurityType;<br>API declaration: WIFI_SEC_TYPE_INVALID = 0<br>Differences: WIFI_SEC_TYPE_INVALID = 0|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiSecurityType;<br>API declaration: WIFI_SEC_TYPE_OPEN = 1<br>Differences: WIFI_SEC_TYPE_OPEN = 1|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiSecurityType;<br>API declaration: WIFI_SEC_TYPE_WEP = 2<br>Differences: WIFI_SEC_TYPE_WEP = 2|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiSecurityType;<br>API declaration: WIFI_SEC_TYPE_PSK = 3<br>Differences: WIFI_SEC_TYPE_PSK = 3|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiSecurityType;<br>API declaration: WIFI_SEC_TYPE_SAE = 4<br>Differences: WIFI_SEC_TYPE_SAE = 4|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiSecurityType;<br>API declaration: WIFI_SEC_TYPE_EAP = 5<br>Differences: WIFI_SEC_TYPE_EAP = 5|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiSecurityType;<br>API declaration: WIFI_SEC_TYPE_EAP_SUITE_B = 6<br>Differences: WIFI_SEC_TYPE_EAP_SUITE_B = 6|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiSecurityType;<br>API declaration: WIFI_SEC_TYPE_OWE = 7<br>Differences: WIFI_SEC_TYPE_OWE = 7|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiSecurityType;<br>API declaration: WIFI_SEC_TYPE_WAPI_CERT = 8<br>Differences: WIFI_SEC_TYPE_WAPI_CERT = 8|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiSecurityType;<br>API declaration: WIFI_SEC_TYPE_WAPI_PSK = 9<br>Differences: WIFI_SEC_TYPE_WAPI_PSK = 9|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: wifiManager;<br>API declaration: enum IpType<br>Differences: enum IpType|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: IpType;<br>API declaration: STATIC<br>Differences: STATIC|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: IpType;<br>API declaration: DHCP<br>Differences: DHCP|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: IpType;<br>API declaration: UNKNOWN<br>Differences: UNKNOWN|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: wifiManager;<br>API declaration: interface IpProfile<br>Differences: interface IpProfile|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: IpProfile;<br>API declaration: ipAddress: number;<br>Differences: ipAddress: number;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: IpProfile;<br>API declaration: gateway: number;<br>Differences: gateway: number;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: IpProfile;<br>API declaration: prefixLength: number;<br>Differences: prefixLength: number;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: IpProfile;<br>API declaration: dnsServers: number[];<br>Differences: dnsServers: number[];|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: IpProfile;<br>API declaration: domains: Array\<string>;<br>Differences: domains: Array\<string>;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: wifiManager;<br>API declaration: enum EapMethod<br>Differences: enum EapMethod|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: EapMethod;<br>API declaration: EAP_NONE<br>Differences: EAP_NONE|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: EapMethod;<br>API declaration: EAP_PEAP<br>Differences: EAP_PEAP|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: EapMethod;<br>API declaration: EAP_TLS<br>Differences: EAP_TLS|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: EapMethod;<br>API declaration: EAP_TTLS<br>Differences: EAP_TTLS|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: EapMethod;<br>API declaration: EAP_PWD<br>Differences: EAP_PWD|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: EapMethod;<br>API declaration: EAP_SIM<br>Differences: EAP_SIM|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: EapMethod;<br>API declaration: EAP_AKA<br>Differences: EAP_AKA|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: EapMethod;<br>API declaration: EAP_AKA_PRIME<br>Differences: EAP_AKA_PRIME|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: EapMethod;<br>API declaration: EAP_UNAUTH_TLS<br>Differences: EAP_UNAUTH_TLS|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: wifiManager;<br>API declaration: enum Phase2Method<br>Differences: enum Phase2Method|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: Phase2Method;<br>API declaration: PHASE2_NONE<br>Differences: PHASE2_NONE|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: Phase2Method;<br>API declaration: PHASE2_PAP<br>Differences: PHASE2_PAP|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: Phase2Method;<br>API declaration: PHASE2_MSCHAP<br>Differences: PHASE2_MSCHAP|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: Phase2Method;<br>API declaration: PHASE2_MSCHAPV2<br>Differences: PHASE2_MSCHAPV2|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: Phase2Method;<br>API declaration: PHASE2_GTC<br>Differences: PHASE2_GTC|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: Phase2Method;<br>API declaration: PHASE2_SIM<br>Differences: PHASE2_SIM|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: Phase2Method;<br>API declaration: PHASE2_AKA<br>Differences: PHASE2_AKA|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: Phase2Method;<br>API declaration: PHASE2_AKA_PRIME<br>Differences: PHASE2_AKA_PRIME|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: wifiManager;<br>API declaration: interface WifiEapProfile<br>Differences: interface WifiEapProfile|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: eapMethod: EapMethod;<br>Differences: eapMethod: EapMethod;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: phase2Method: Phase2Method;<br>Differences: phase2Method: Phase2Method;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: identity: string;<br>Differences: identity: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: anonymousIdentity: string;<br>Differences: anonymousIdentity: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: password: string;<br>Differences: password: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: caCertAliases: string;<br>Differences: caCertAliases: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: caPath: string;<br>Differences: caPath: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: clientCertAliases: string;<br>Differences: clientCertAliases: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: certEntry: Uint8Array;<br>Differences: certEntry: Uint8Array;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: certPassword: string;<br>Differences: certPassword: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: altSubjectMatch: string;<br>Differences: altSubjectMatch: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: domainSuffixMatch: string;<br>Differences: domainSuffixMatch: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: realm: string;<br>Differences: realm: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: plmn: string;<br>Differences: plmn: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiEapProfile;<br>API declaration: eapSubId: number;<br>Differences: eapSubId: number;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: wifiManager;<br>API declaration: interface WifiProfile<br>Differences: interface WifiProfile|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: ssid: string;<br>Differences: ssid: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: bssid?: string;<br>Differences: bssid?: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: preSharedKey: string;<br>Differences: preSharedKey: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: isHiddenSsid?: boolean;<br>Differences: isHiddenSsid?: boolean;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: securityType: WifiSecurityType;<br>Differences: securityType: WifiSecurityType;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: creatorUid?: number;<br>Differences: creatorUid?: number;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: disableReason?: number;<br>Differences: disableReason?: number;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: netId?: number;<br>Differences: netId?: number;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: randomMacType?: number;<br>Differences: randomMacType?: number;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: randomMacAddr?: string;<br>Differences: randomMacAddr?: string;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: ipType?: IpType;<br>Differences: ipType?: IpType;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: staticIp?: IpProfile;<br>Differences: staticIp?: IpProfile;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: WifiProfile;<br>API declaration: eapProfile?: WifiEapProfile;<br>Differences: eapProfile?: WifiEapProfile;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: wifiManager;<br>API declaration: function isWifiActiveSync(admin: Want): boolean;<br>Differences: function isWifiActiveSync(admin: Want): boolean;|api/@ohos.enterprise.wifiManager.d.ts|
|New API|NA|Class name: wifiManager;<br>API declaration: function setWifiProfileSync(admin: Want, profile: WifiProfile): void;<br>Differences: function setWifiProfileSync(admin: Want, profile: WifiProfile): void;|api/@ohos.enterprise.wifiManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.accountManager.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.accountManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.adminManager.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.adminManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.applicationManager.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.applicationManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.bluetoothManager.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.bluetoothManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.browser.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.browser.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.bundleManager.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.bundleManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.deviceControl.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.deviceControl.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.deviceInfo.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.deviceInfo.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.deviceSettings.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.deviceSettings.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.locationManager.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.locationManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.networkManager.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.networkManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.restrictions.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.restrictions.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.securityManager.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.securityManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.systemManager.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.systemManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.usbManager.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.usbManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.enterprise.wifiManager.d.ts<br>Differences: MDMKit|api/@ohos.enterprise.wifiManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.MDMKit.d.ts<br>Differences: MDMKit|kits/@kit.MDMKit.d.ts|
