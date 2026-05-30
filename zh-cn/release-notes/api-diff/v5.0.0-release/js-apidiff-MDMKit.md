| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace accountManager<br>差异内容：declare namespace accountManager|api/@ohos.enterprise.accountManager.d.ts|
|新增API|NA|类名：accountManager；<br>API声明：function disallowOsAccountAddition(admin: Want, disallow: boolean, accountId?: number): void;<br>差异内容：function disallowOsAccountAddition(admin: Want, disallow: boolean, accountId?: number): void;|api/@ohos.enterprise.accountManager.d.ts|
|新增API|NA|类名：accountManager；<br>API声明：function isOsAccountAdditionDisallowed(admin: Want, accountId?: number): boolean;<br>差异内容：function isOsAccountAdditionDisallowed(admin: Want, accountId?: number): boolean;|api/@ohos.enterprise.accountManager.d.ts|
|新增API|NA|类名：accountManager；<br>API声明：function addOsAccountAsync(admin: Want, name: string, type: osAccount.OsAccountType): Promise\<osAccount.OsAccountInfo>;<br>差异内容：function addOsAccountAsync(admin: Want, name: string, type: osAccount.OsAccountType): Promise\<osAccount.OsAccountInfo>;|api/@ohos.enterprise.accountManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace adminManager<br>差异内容：declare namespace adminManager|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：adminManager；<br>API声明：export enum ManagedEvent<br>差异内容：export enum ManagedEvent|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：ManagedEvent；<br>API声明：MANAGED_EVENT_BUNDLE_ADDED = 0<br>差异内容：MANAGED_EVENT_BUNDLE_ADDED = 0|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：ManagedEvent；<br>API声明：MANAGED_EVENT_BUNDLE_REMOVED = 1<br>差异内容：MANAGED_EVENT_BUNDLE_REMOVED = 1|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：ManagedEvent；<br>API声明：MANAGED_EVENT_APP_START = 2<br>差异内容：MANAGED_EVENT_APP_START = 2|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：ManagedEvent；<br>API声明：MANAGED_EVENT_APP_STOP = 3<br>差异内容：MANAGED_EVENT_APP_STOP = 3|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：ManagedEvent；<br>API声明：MANAGED_EVENT_SYSTEM_UPDATE = 4<br>差异内容：MANAGED_EVENT_SYSTEM_UPDATE = 4|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：adminManager；<br>API声明：function disableAdmin(admin: Want, userId?: number): Promise\<void>;<br>差异内容：function disableAdmin(admin: Want, userId?: number): Promise\<void>;|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：adminManager；<br>API声明：function subscribeManagedEventSync(admin: Want, managedEvents: Array\<ManagedEvent>): void;<br>差异内容：function subscribeManagedEventSync(admin: Want, managedEvents: Array\<ManagedEvent>): void;|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：adminManager；<br>API声明：function unsubscribeManagedEventSync(admin: Want, managedEvents: Array\<ManagedEvent>): void;<br>差异内容：function unsubscribeManagedEventSync(admin: Want, managedEvents: Array\<ManagedEvent>): void;|api/@ohos.enterprise.adminManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace applicationManager<br>差异内容：declare namespace applicationManager|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function addDisallowedRunningBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>差异内容：function addDisallowedRunningBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function removeDisallowedRunningBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>差异内容：function removeDisallowedRunningBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function getDisallowedRunningBundlesSync(admin: Want, accountId?: number): Array\<string>;<br>差异内容：function getDisallowedRunningBundlesSync(admin: Want, accountId?: number): Array\<string>;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function addAutoStartApps(admin: Want, autoStartApps: Array\<Want>): void;<br>差异内容：function addAutoStartApps(admin: Want, autoStartApps: Array\<Want>): void;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function removeAutoStartApps(admin: Want, autoStartApps: Array\<Want>): void;<br>差异内容：function removeAutoStartApps(admin: Want, autoStartApps: Array\<Want>): void;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：applicationManager；<br>API声明：function getAutoStartApps(admin: Want): Array\<Want>;<br>差异内容：function getAutoStartApps(admin: Want): Array\<Want>;|api/@ohos.enterprise.applicationManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace bluetoothManager<br>差异内容：declare namespace bluetoothManager|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：export interface BluetoothInfo<br>差异内容：export interface BluetoothInfo|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：BluetoothInfo；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：BluetoothInfo；<br>API声明：state: access.BluetoothState;<br>差异内容：state: access.BluetoothState;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：BluetoothInfo；<br>API声明：connectionState: constant.ProfileConnectionState;<br>差异内容：connectionState: constant.ProfileConnectionState;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getBluetoothInfo(admin: Want): BluetoothInfo;<br>差异内容：function getBluetoothInfo(admin: Want): BluetoothInfo;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function addAllowedBluetoothDevices(admin: Want, deviceIds: Array\<string>): void;<br>差异内容：function addAllowedBluetoothDevices(admin: Want, deviceIds: Array\<string>): void;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function removeAllowedBluetoothDevices(admin: Want, deviceIds: Array\<string>): void;<br>差异内容：function removeAllowedBluetoothDevices(admin: Want, deviceIds: Array\<string>): void;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：bluetoothManager；<br>API声明：function getAllowedBluetoothDevices(admin: Want): Array\<string>;<br>差异内容：function getAllowedBluetoothDevices(admin: Want): Array\<string>;|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace browser<br>差异内容：declare namespace browser|api/@ohos.enterprise.browser.d.ts|
|新增API|NA|类名：browser；<br>API声明：function setPolicySync(admin: Want, appId: string, policyName: string, policyValue: string): void;<br>差异内容：function setPolicySync(admin: Want, appId: string, policyName: string, policyValue: string): void;|api/@ohos.enterprise.browser.d.ts|
|新增API|NA|类名：browser；<br>API声明：function getPoliciesSync(admin: Want, appId: string): string;<br>差异内容：function getPoliciesSync(admin: Want, appId: string): string;|api/@ohos.enterprise.browser.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace bundleManager<br>差异内容：declare namespace bundleManager|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：interface InstallParam<br>差异内容：interface InstallParam|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：InstallParam；<br>API声明：userId?: number;<br>差异内容：userId?: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：InstallParam；<br>API声明：installFlag?: number;<br>差异内容：installFlag?: number;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function addAllowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>差异内容：function addAllowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function removeAllowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>差异内容：function removeAllowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getAllowedInstallBundlesSync(admin: Want, accountId?: number): Array\<string>;<br>差异内容：function getAllowedInstallBundlesSync(admin: Want, accountId?: number): Array\<string>;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function addDisallowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>差异内容：function addDisallowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function removeDisallowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>差异内容：function removeDisallowedInstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getDisallowedInstallBundlesSync(admin: Want, accountId?: number): Array\<string>;<br>差异内容：function getDisallowedInstallBundlesSync(admin: Want, accountId?: number): Array\<string>;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function addDisallowedUninstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>差异内容：function addDisallowedUninstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function removeDisallowedUninstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;<br>差异内容：function removeDisallowedUninstallBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function getDisallowedUninstallBundlesSync(admin: Want, accountId?: number): Array\<string>;<br>差异内容：function getDisallowedUninstallBundlesSync(admin: Want, accountId?: number): Array\<string>;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function uninstall(admin: Want, bundleName: string, userId?: number, isKeepData?: boolean): Promise\<void>;<br>差异内容：function uninstall(admin: Want, bundleName: string, userId?: number, isKeepData?: boolean): Promise\<void>;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：bundleManager；<br>API声明：function install(admin: Want, hapFilePaths: Array\<string>, installParam?: InstallParam): Promise\<void>;<br>差异内容：function install(admin: Want, hapFilePaths: Array\<string>, installParam?: InstallParam): Promise\<void>;|api/@ohos.enterprise.bundleManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace deviceControl<br>差异内容：declare namespace deviceControl|api/@ohos.enterprise.deviceControl.d.ts|
|新增API|NA|类名：deviceControl；<br>API声明：function operateDevice(admin: Want, operate: string, addition?: string): void;<br>差异内容：function operateDevice(admin: Want, operate: string, addition?: string): void;|api/@ohos.enterprise.deviceControl.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace deviceInfo<br>差异内容：declare namespace deviceInfo|api/@ohos.enterprise.deviceInfo.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：function getDeviceInfo(admin: Want, label: string): string;<br>差异内容：function getDeviceInfo(admin: Want, label: string): string;|api/@ohos.enterprise.deviceInfo.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace deviceSettings<br>差异内容：declare namespace deviceSettings|api/@ohos.enterprise.deviceSettings.d.ts|
|新增API|NA|类名：deviceSettings；<br>API声明：function setValue(admin: Want, item: string, value: string): void;<br>差异内容：function setValue(admin: Want, item: string, value: string): void;|api/@ohos.enterprise.deviceSettings.d.ts|
|新增API|NA|类名：deviceSettings；<br>API声明：function getValue(admin: Want, item: string): string;<br>差异内容：function getValue(admin: Want, item: string): string;|api/@ohos.enterprise.deviceSettings.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class EnterpriseAdminExtensionAbility<br>差异内容：export default class EnterpriseAdminExtensionAbility|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onAdminEnabled(): void;<br>差异内容：onAdminEnabled(): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onAdminDisabled(): void;<br>差异内容：onAdminDisabled(): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onBundleAdded(bundleName: string): void;<br>差异内容：onBundleAdded(bundleName: string): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onBundleRemoved(bundleName: string): void;<br>差异内容：onBundleRemoved(bundleName: string): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onAppStart(bundleName: string): void;<br>差异内容：onAppStart(bundleName: string): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onAppStop(bundleName: string): void;<br>差异内容：onAppStop(bundleName: string): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onSystemUpdate(systemUpdateInfo: systemManager.SystemUpdateInfo): void;<br>差异内容：onSystemUpdate(systemUpdateInfo: systemManager.SystemUpdateInfo): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：EnterpriseAdminExtensionAbility；<br>API声明：onStart(): void;<br>差异内容：onStart(): void;|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace locationManager<br>差异内容：declare namespace locationManager|api/@ohos.enterprise.locationManager.d.ts|
|新增API|NA|类名：locationManager；<br>API声明：export enum LocationPolicy<br>差异内容：export enum LocationPolicy|api/@ohos.enterprise.locationManager.d.ts|
|新增API|NA|类名：LocationPolicy；<br>API声明：DEFAULT_LOCATION_SERVICE = 0<br>差异内容：DEFAULT_LOCATION_SERVICE = 0|api/@ohos.enterprise.locationManager.d.ts|
|新增API|NA|类名：LocationPolicy；<br>API声明：DISALLOW_LOCATION_SERVICE = 1<br>差异内容：DISALLOW_LOCATION_SERVICE = 1|api/@ohos.enterprise.locationManager.d.ts|
|新增API|NA|类名：LocationPolicy；<br>API声明：FORCE_OPEN_LOCATION_SERVICE = 2<br>差异内容：FORCE_OPEN_LOCATION_SERVICE = 2|api/@ohos.enterprise.locationManager.d.ts|
|新增API|NA|类名：locationManager；<br>API声明：function setLocationPolicy(admin: Want, policy: LocationPolicy): void;<br>差异内容：function setLocationPolicy(admin: Want, policy: LocationPolicy): void;|api/@ohos.enterprise.locationManager.d.ts|
|新增API|NA|类名：locationManager；<br>API声明：function getLocationPolicy(admin: Want): LocationPolicy;<br>差异内容：function getLocationPolicy(admin: Want): LocationPolicy;|api/@ohos.enterprise.locationManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace networkManager<br>差异内容：declare namespace networkManager|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：enum Direction<br>差异内容：enum Direction|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：Direction；<br>API声明：INPUT = 0<br>差异内容：INPUT = 0|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：Direction；<br>API声明：OUTPUT = 1<br>差异内容：OUTPUT = 1|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：enum Action<br>差异内容：enum Action|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：Action；<br>API声明：ALLOW = 0<br>差异内容：ALLOW = 0|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：Action；<br>API声明：DENY = 1<br>差异内容：DENY = 1|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：enum Protocol<br>差异内容：enum Protocol|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：Protocol；<br>API声明：ALL = 0<br>差异内容：ALL = 0|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：Protocol；<br>API声明：TCP = 1<br>差异内容：TCP = 1|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：Protocol；<br>API声明：UDP = 2<br>差异内容：UDP = 2|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：Protocol；<br>API声明：ICMP = 3<br>差异内容：ICMP = 3|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：interface FirewallRule<br>差异内容：interface FirewallRule|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：FirewallRule；<br>API声明：srcAddr?: string;<br>差异内容：srcAddr?: string;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：FirewallRule；<br>API声明：destAddr?: string;<br>差异内容：destAddr?: string;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：FirewallRule；<br>API声明：srcPort?: string;<br>差异内容：srcPort?: string;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：FirewallRule；<br>API声明：destPort?: string;<br>差异内容：destPort?: string;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：FirewallRule；<br>API声明：appUid?: string;<br>差异内容：appUid?: string;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：FirewallRule；<br>API声明：direction?: Direction;<br>差异内容：direction?: Direction;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：FirewallRule；<br>API声明：action?: Action;<br>差异内容：action?: Action;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：FirewallRule；<br>API声明：protocol?: Protocol;<br>差异内容：protocol?: Protocol;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：interface DomainFilterRule<br>差异内容：interface DomainFilterRule|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：DomainFilterRule；<br>API声明：domainName?: string;<br>差异内容：domainName?: string;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：DomainFilterRule；<br>API声明：appUid?: string;<br>差异内容：appUid?: string;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：DomainFilterRule；<br>API声明：action?: Action;<br>差异内容：action?: Action;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function getAllNetworkInterfacesSync(admin: Want): Array\<string>;<br>差异内容：function getAllNetworkInterfacesSync(admin: Want): Array\<string>;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function getIpAddressSync(admin: Want, networkInterface: string): string;<br>差异内容：function getIpAddressSync(admin: Want, networkInterface: string): string;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function getMacSync(admin: Want, networkInterface: string): string;<br>差异内容：function getMacSync(admin: Want, networkInterface: string): string;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function isNetworkInterfaceDisabledSync(admin: Want, networkInterface: string): boolean;<br>差异内容：function isNetworkInterfaceDisabledSync(admin: Want, networkInterface: string): boolean;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function setNetworkInterfaceDisabledSync(admin: Want, networkInterface: string, isDisabled: boolean): void;<br>差异内容：function setNetworkInterfaceDisabledSync(admin: Want, networkInterface: string, isDisabled: boolean): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function setGlobalProxySync(admin: Want, httpProxy: connection.HttpProxy): void;<br>差异内容：function setGlobalProxySync(admin: Want, httpProxy: connection.HttpProxy): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function getGlobalProxySync(admin: Want): connection.HttpProxy;<br>差异内容：function getGlobalProxySync(admin: Want): connection.HttpProxy;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function addFirewallRule(admin: Want, firewallRule: FirewallRule): void;<br>差异内容：function addFirewallRule(admin: Want, firewallRule: FirewallRule): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function removeFirewallRule(admin: Want, firewallRule?: FirewallRule): void;<br>差异内容：function removeFirewallRule(admin: Want, firewallRule?: FirewallRule): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function getFirewallRules(admin: Want): Array\<FirewallRule>;<br>差异内容：function getFirewallRules(admin: Want): Array\<FirewallRule>;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function addDomainFilterRule(admin: Want, domainFilterRule: DomainFilterRule): void;<br>差异内容：function addDomainFilterRule(admin: Want, domainFilterRule: DomainFilterRule): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function removeDomainFilterRule(admin: Want, domainFilterRule?: DomainFilterRule): void;<br>差异内容：function removeDomainFilterRule(admin: Want, domainFilterRule?: DomainFilterRule): void;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：networkManager；<br>API声明：function getDomainFilterRules(admin: Want): Array\<DomainFilterRule>;<br>差异内容：function getDomainFilterRules(admin: Want): Array\<DomainFilterRule>;|api/@ohos.enterprise.networkManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace restrictions<br>差异内容：declare namespace restrictions|api/@ohos.enterprise.restrictions.d.ts|
|新增API|NA|类名：restrictions；<br>API声明：function setDisallowedPolicy(admin: Want, feature: string, disallow: boolean): void;<br>差异内容：function setDisallowedPolicy(admin: Want, feature: string, disallow: boolean): void;|api/@ohos.enterprise.restrictions.d.ts|
|新增API|NA|类名：restrictions；<br>API声明：function getDisallowedPolicy(admin: Want, feature: string): boolean;<br>差异内容：function getDisallowedPolicy(admin: Want, feature: string): boolean;|api/@ohos.enterprise.restrictions.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace securityManager<br>差异内容：declare namespace securityManager|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：export interface CertBlob<br>差异内容：export interface CertBlob|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：CertBlob；<br>API声明：inData: Uint8Array;<br>差异内容：inData: Uint8Array;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：CertBlob；<br>API声明：alias: string;<br>差异内容：alias: string;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function getSecurityStatus(admin: Want, item: string): string;<br>差异内容：function getSecurityStatus(admin: Want, item: string): string;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function installUserCertificate(admin: Want, certificate: CertBlob): Promise\<string>;<br>差异内容：function installUserCertificate(admin: Want, certificate: CertBlob): Promise\<string>;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function uninstallUserCertificate(admin: Want, certUri: string): Promise\<void>;<br>差异内容：function uninstallUserCertificate(admin: Want, certUri: string): Promise\<void>;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function setPasswordPolicy(admin: Want, policy: PasswordPolicy): void;<br>差异内容：function setPasswordPolicy(admin: Want, policy: PasswordPolicy): void;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function getPasswordPolicy(admin: Want): PasswordPolicy;<br>差异内容：function getPasswordPolicy(admin: Want): PasswordPolicy;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function setAppClipboardPolicy(admin: Want, tokenId: number, policy: ClipboardPolicy): void;<br>差异内容：function setAppClipboardPolicy(admin: Want, tokenId: number, policy: ClipboardPolicy): void;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：function getAppClipboardPolicy(admin: Want, tokenId?: number): string;<br>差异内容：function getAppClipboardPolicy(admin: Want, tokenId?: number): string;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：export interface PasswordPolicy<br>差异内容：export interface PasswordPolicy|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：PasswordPolicy；<br>API声明：complexityRegex?: string;<br>差异内容：complexityRegex?: string;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：PasswordPolicy；<br>API声明：validityPeriod?: number;<br>差异内容：validityPeriod?: number;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：PasswordPolicy；<br>API声明：additionalDescription?: string;<br>差异内容：additionalDescription?: string;|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：securityManager；<br>API声明：export enum ClipboardPolicy<br>差异内容：export enum ClipboardPolicy|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：ClipboardPolicy；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：ClipboardPolicy；<br>API声明：IN_APP = 1<br>差异内容：IN_APP = 1|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：ClipboardPolicy；<br>API声明：LOCAL_DEVICE = 2<br>差异内容：LOCAL_DEVICE = 2|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：ClipboardPolicy；<br>API声明：CROSS_DEVICE = 3<br>差异内容：CROSS_DEVICE = 3|api/@ohos.enterprise.securityManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace systemManager<br>差异内容：declare namespace systemManager|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：export interface SystemUpdateInfo<br>差异内容：export interface SystemUpdateInfo|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：SystemUpdateInfo；<br>API声明：versionName: string;<br>差异内容：versionName: string;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：SystemUpdateInfo；<br>API声明：firstReceivedTime: number;<br>差异内容：firstReceivedTime: number;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：SystemUpdateInfo；<br>API声明：packageType: string;<br>差异内容：packageType: string;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：enum PolicyType<br>差异内容：enum PolicyType|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：PolicyType；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：PolicyType；<br>API声明：PROHIBIT = 1<br>差异内容：PROHIBIT = 1|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：PolicyType；<br>API声明：UPDATE_TO_SPECIFIC_VERSION = 2<br>差异内容：UPDATE_TO_SPECIFIC_VERSION = 2|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：PolicyType；<br>API声明：WINDOWS = 3<br>差异内容：WINDOWS = 3|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：PolicyType；<br>API声明：POSTPONE = 4<br>差异内容：POSTPONE = 4|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：export interface OtaUpdatePolicy<br>差异内容：export interface OtaUpdatePolicy|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：OtaUpdatePolicy；<br>API声明：policyType: PolicyType;<br>差异内容：policyType: PolicyType;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：OtaUpdatePolicy；<br>API声明：version: string;<br>差异内容：version: string;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：OtaUpdatePolicy；<br>API声明：latestUpdateTime?: number;<br>差异内容：latestUpdateTime?: number;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：OtaUpdatePolicy；<br>API声明：delayUpdateTime?: number;<br>差异内容：delayUpdateTime?: number;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：OtaUpdatePolicy；<br>API声明：installStartTime?: number;<br>差异内容：installStartTime?: number;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：OtaUpdatePolicy；<br>API声明：installEndTime?: number;<br>差异内容：installEndTime?: number;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：export interface UpdatePackageInfo<br>差异内容：export interface UpdatePackageInfo|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：UpdatePackageInfo；<br>API声明：version: string;<br>差异内容：version: string;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：UpdatePackageInfo；<br>API声明：packages: Array\<Package>;<br>差异内容：packages: Array\<Package>;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：UpdatePackageInfo；<br>API声明：description?: PackageDescription;<br>差异内容：description?: PackageDescription;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：interface Package<br>差异内容：interface Package|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：Package；<br>API声明：type: PackageType;<br>差异内容：type: PackageType;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：Package；<br>API声明：path: string;<br>差异内容：path: string;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：Package；<br>API声明：fd?: number;<br>差异内容：fd?: number;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：enum PackageType<br>差异内容：enum PackageType|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：PackageType；<br>API声明：FIRMWARE = 1<br>差异内容：FIRMWARE = 1|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：interface PackageDescription<br>差异内容：interface PackageDescription|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：PackageDescription；<br>API声明：notify?: NotifyDescription;<br>差异内容：notify?: NotifyDescription;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：interface NotifyDescription<br>差异内容：interface NotifyDescription|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：NotifyDescription；<br>API声明：installTips?: string;<br>差异内容：installTips?: string;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：NotifyDescription；<br>API声明：installTipsDetail?: string;<br>差异内容：installTipsDetail?: string;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：interface UpdateResult<br>差异内容：interface UpdateResult|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：UpdateResult；<br>API声明：version: string;<br>差异内容：version: string;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：UpdateResult；<br>API声明：status: UpdateStatus;<br>差异内容：status: UpdateStatus;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：UpdateResult；<br>API声明：errorInfo: ErrorInfo;<br>差异内容：errorInfo: ErrorInfo;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：enum UpdateStatus<br>差异内容：enum UpdateStatus|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：UpdateStatus；<br>API声明：NO_UPDATE_PACKAGE = -4<br>差异内容：NO_UPDATE_PACKAGE = -4|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：UpdateStatus；<br>API声明：UPDATE_WAITING = -3<br>差异内容：UPDATE_WAITING = -3|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：UpdateStatus；<br>API声明：UPDATING = -2<br>差异内容：UPDATING = -2|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：UpdateStatus；<br>API声明：UPDATE_FAILURE = -1<br>差异内容：UPDATE_FAILURE = -1|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：UpdateStatus；<br>API声明：UPDATE_SUCCESS = 0<br>差异内容：UPDATE_SUCCESS = 0|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：interface ErrorInfo<br>差异内容：interface ErrorInfo|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：ErrorInfo；<br>API声明：code: number;<br>差异内容：code: number;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：ErrorInfo；<br>API声明：message: string;<br>差异内容：message: string;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function setNTPServer(admin: Want, server: string): void;<br>差异内容：function setNTPServer(admin: Want, server: string): void;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function getNTPServer(admin: Want): string;<br>差异内容：function getNTPServer(admin: Want): string;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function setOtaUpdatePolicy(admin: Want, policy: OtaUpdatePolicy): void;<br>差异内容：function setOtaUpdatePolicy(admin: Want, policy: OtaUpdatePolicy): void;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function getOtaUpdatePolicy(admin: Want): OtaUpdatePolicy;<br>差异内容：function getOtaUpdatePolicy(admin: Want): OtaUpdatePolicy;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function notifyUpdatePackages(admin: Want, packageInfo: UpdatePackageInfo): Promise\<void>;<br>差异内容：function notifyUpdatePackages(admin: Want, packageInfo: UpdatePackageInfo): Promise\<void>;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：systemManager；<br>API声明：function getUpdateResult(admin: Want, version: string): Promise\<UpdateResult>;<br>差异内容：function getUpdateResult(admin: Want, version: string): Promise\<UpdateResult>;|api/@ohos.enterprise.systemManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace usbManager<br>差异内容：declare namespace usbManager|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：export enum UsbPolicy<br>差异内容：export enum UsbPolicy|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：UsbPolicy；<br>API声明：READ_WRITE = 0<br>差异内容：READ_WRITE = 0|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：UsbPolicy；<br>API声明：READ_ONLY = 1<br>差异内容：READ_ONLY = 1|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：UsbPolicy；<br>API声明：DISABLED = 2<br>差异内容：DISABLED = 2|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：export interface UsbDeviceId<br>差异内容：export interface UsbDeviceId|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：UsbDeviceId；<br>API声明：vendorId: number;<br>差异内容：vendorId: number;|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：UsbDeviceId；<br>API声明：productId: number;<br>差异内容：productId: number;|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function addAllowedUsbDevices(admin: Want, usbDeviceIds: Array\<UsbDeviceId>): void;<br>差异内容：function addAllowedUsbDevices(admin: Want, usbDeviceIds: Array\<UsbDeviceId>): void;|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function removeAllowedUsbDevices(admin: Want, usbDeviceIds: Array\<UsbDeviceId>): void;<br>差异内容：function removeAllowedUsbDevices(admin: Want, usbDeviceIds: Array\<UsbDeviceId>): void;|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function getAllowedUsbDevices(admin: Want): Array\<UsbDeviceId>;<br>差异内容：function getAllowedUsbDevices(admin: Want): Array\<UsbDeviceId>;|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function setUsbStorageDeviceAccessPolicy(admin: Want, usbPolicy: UsbPolicy): void;<br>差异内容：function setUsbStorageDeviceAccessPolicy(admin: Want, usbPolicy: UsbPolicy): void;|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function getUsbStorageDeviceAccessPolicy(admin: Want): UsbPolicy;<br>差异内容：function getUsbStorageDeviceAccessPolicy(admin: Want): UsbPolicy;|api/@ohos.enterprise.usbManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace wifiManager<br>差异内容：declare namespace wifiManager|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum WifiSecurityType<br>差异内容：enum WifiSecurityType|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_INVALID = 0<br>差异内容：WIFI_SEC_TYPE_INVALID = 0|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_OPEN = 1<br>差异内容：WIFI_SEC_TYPE_OPEN = 1|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_WEP = 2<br>差异内容：WIFI_SEC_TYPE_WEP = 2|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_PSK = 3<br>差异内容：WIFI_SEC_TYPE_PSK = 3|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_SAE = 4<br>差异内容：WIFI_SEC_TYPE_SAE = 4|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_EAP = 5<br>差异内容：WIFI_SEC_TYPE_EAP = 5|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_EAP_SUITE_B = 6<br>差异内容：WIFI_SEC_TYPE_EAP_SUITE_B = 6|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_OWE = 7<br>差异内容：WIFI_SEC_TYPE_OWE = 7|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_WAPI_CERT = 8<br>差异内容：WIFI_SEC_TYPE_WAPI_CERT = 8|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiSecurityType；<br>API声明：WIFI_SEC_TYPE_WAPI_PSK = 9<br>差异内容：WIFI_SEC_TYPE_WAPI_PSK = 9|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum IpType<br>差异内容：enum IpType|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：IpType；<br>API声明：STATIC<br>差异内容：STATIC|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：IpType；<br>API声明：DHCP<br>差异内容：DHCP|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：IpType；<br>API声明：UNKNOWN<br>差异内容：UNKNOWN|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface IpProfile<br>差异内容：interface IpProfile|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：IpProfile；<br>API声明：ipAddress: number;<br>差异内容：ipAddress: number;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：IpProfile；<br>API声明：gateway: number;<br>差异内容：gateway: number;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：IpProfile；<br>API声明：prefixLength: number;<br>差异内容：prefixLength: number;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：IpProfile；<br>API声明：dnsServers: number[];<br>差异内容：dnsServers: number[];|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：IpProfile；<br>API声明：domains: Array\<string>;<br>差异内容：domains: Array\<string>;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum EapMethod<br>差异内容：enum EapMethod|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_NONE<br>差异内容：EAP_NONE|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_PEAP<br>差异内容：EAP_PEAP|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_TLS<br>差异内容：EAP_TLS|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_TTLS<br>差异内容：EAP_TTLS|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_PWD<br>差异内容：EAP_PWD|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_SIM<br>差异内容：EAP_SIM|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_AKA<br>差异内容：EAP_AKA|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_AKA_PRIME<br>差异内容：EAP_AKA_PRIME|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_UNAUTH_TLS<br>差异内容：EAP_UNAUTH_TLS|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：enum Phase2Method<br>差异内容：enum Phase2Method|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_NONE<br>差异内容：PHASE2_NONE|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_PAP<br>差异内容：PHASE2_PAP|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_MSCHAP<br>差异内容：PHASE2_MSCHAP|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_MSCHAPV2<br>差异内容：PHASE2_MSCHAPV2|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_GTC<br>差异内容：PHASE2_GTC|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_SIM<br>差异内容：PHASE2_SIM|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_AKA<br>差异内容：PHASE2_AKA|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_AKA_PRIME<br>差异内容：PHASE2_AKA_PRIME|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface WifiEapProfile<br>差异内容：interface WifiEapProfile|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：eapMethod: EapMethod;<br>差异内容：eapMethod: EapMethod;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：phase2Method: Phase2Method;<br>差异内容：phase2Method: Phase2Method;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：identity: string;<br>差异内容：identity: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：anonymousIdentity: string;<br>差异内容：anonymousIdentity: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：password: string;<br>差异内容：password: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：caCertAliases: string;<br>差异内容：caCertAliases: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：caPath: string;<br>差异内容：caPath: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：clientCertAliases: string;<br>差异内容：clientCertAliases: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：certEntry: Uint8Array;<br>差异内容：certEntry: Uint8Array;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：certPassword: string;<br>差异内容：certPassword: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：altSubjectMatch: string;<br>差异内容：altSubjectMatch: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：domainSuffixMatch: string;<br>差异内容：domainSuffixMatch: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：realm: string;<br>差异内容：realm: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：plmn: string;<br>差异内容：plmn: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiEapProfile；<br>API声明：eapSubId: number;<br>差异内容：eapSubId: number;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：interface WifiProfile<br>差异内容：interface WifiProfile|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：ssid: string;<br>差异内容：ssid: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：bssid?: string;<br>差异内容：bssid?: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：preSharedKey: string;<br>差异内容：preSharedKey: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：isHiddenSsid?: boolean;<br>差异内容：isHiddenSsid?: boolean;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：securityType: WifiSecurityType;<br>差异内容：securityType: WifiSecurityType;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：creatorUid?: number;<br>差异内容：creatorUid?: number;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：disableReason?: number;<br>差异内容：disableReason?: number;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：netId?: number;<br>差异内容：netId?: number;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：randomMacType?: number;<br>差异内容：randomMacType?: number;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：randomMacAddr?: string;<br>差异内容：randomMacAddr?: string;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：ipType?: IpType;<br>差异内容：ipType?: IpType;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：staticIp?: IpProfile;<br>差异内容：staticIp?: IpProfile;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：WifiProfile；<br>API声明：eapProfile?: WifiEapProfile;<br>差异内容：eapProfile?: WifiEapProfile;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function isWifiActiveSync(admin: Want): boolean;<br>差异内容：function isWifiActiveSync(admin: Want): boolean;|api/@ohos.enterprise.wifiManager.d.ts|
|新增API|NA|类名：wifiManager；<br>API声明：function setWifiProfileSync(admin: Want, profile: WifiProfile): void;<br>差异内容：function setWifiProfileSync(admin: Want, profile: WifiProfile): void;|api/@ohos.enterprise.wifiManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.accountManager.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.accountManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.adminManager.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.adminManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.applicationManager.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.applicationManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.bluetoothManager.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.bluetoothManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.browser.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.browser.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.bundleManager.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.bundleManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.deviceControl.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.deviceControl.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.deviceInfo.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.deviceInfo.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.deviceSettings.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.deviceSettings.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.EnterpriseAdminExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.locationManager.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.locationManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.networkManager.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.networkManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.restrictions.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.restrictions.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.securityManager.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.securityManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.systemManager.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.systemManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.usbManager.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.usbManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.enterprise.wifiManager.d.ts<br>差异内容：MDMKit|api/@ohos.enterprise.wifiManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.MDMKit.d.ts<br>差异内容：MDMKit|kits/@kit.MDMKit.d.ts|
