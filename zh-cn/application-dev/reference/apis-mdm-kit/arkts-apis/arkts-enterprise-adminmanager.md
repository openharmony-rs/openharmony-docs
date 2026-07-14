# @ohos.enterprise.adminManager

# 附录

### 可委托策略列表

| 策略名称 | 对应接口 | 说明 |
| --- | --- | --- |
|disallow_add_local_account|
[accountManager.disallowOsAccountAddition](arkts-mdm-disallowosaccountaddition-f.md#disallowosaccountaddition-1)
<br>
[accountManager.isOsAccountAdditionDisallowed](arkts-mdm-isosaccountadditiondisallowed-f.md#isosaccountadditiondisallowed-1)
| 不传accountId参数，禁止设备创建本地用户。<br>不传accountId参数，查询是否禁止设备创建本地用户。|
|disallow_add_os_account_by_user|
[accountManager.disallowOsAccountAddition](arkts-mdm-disallowosaccountaddition-f.md#disallowosaccountaddition-1)
<br>
[accountManager.isOsAccountAdditionDisallowed](arkts-mdm-isosaccountadditiondisallowed-f.md#isosaccountadditiondisallowed-1)
| 需传入accountId参数，禁止指定用户添加账号。<br>需传入accountId参数，查询是否禁止指定用户添加账号。|
|disallow_running_bundles|
[applicationManager.addDisallowedRunningBundlesSync](arkts-mdm-adddisallowedrunningbundlessync-f.md#adddisallowedrunningbundlessync-1)
<br>
[applicationManager.removeDisallowedRunningBundlesSync](arkts-mdm-removedisallowedrunningbundlessync-f.md#removedisallowedrunningbundlessync-1)
<br>
[applicationManager.getDisallowedRunningBundlesSync](arkts-mdm-getdisallowedrunningbundlessync-f.md#getdisallowedrunningbundlessync-1)
|添加应用至应用运行禁止名单，添加至禁止名单的应用不允许在当前/指定用户下运行。<br>从应用运行禁止名单中移除应用。<br>获取当前/指定用户下的应用运行禁止名单。 |
|manage_auto_start_apps|
[applicationManager.addAutoStartApps](arkts-mdm-addautostartapps-f.md#addautostartapps-1)
<br>
[applicationManager.removeAutoStartApps](arkts-mdm-removeautostartapps-f.md#removeautostartapps-1)
<br>
[applicationManager.getAutoStartApps](arkts-mdm-getautostartapps-f.md#getautostartapps-1)
|添加开机自启动应用名单。<br>从开机自启动应用名单中移除应用。<br>查询开机自启动应用名单。|
|allowed_bluetooth_devices|
[bluetoothManager.addAllowedBluetoothDevices](arkts-mdm-addallowedbluetoothdevices-f.md#addallowedbluetoothdevices-1)
<br>
[bluetoothManager.removeAllowedBluetoothDevices](arkts-mdm-removeallowedbluetoothdevices-f.md#removeallowedbluetoothdevices-1)
<br>
[bluetoothManager.getAllowedBluetoothDevices](arkts-mdm-getallowedbluetoothdevices-f.md#getallowedbluetoothdevices-1)
|添加蓝牙设备可用名单。<br>从蓝牙设备可用名单中移除。<br>查询蓝牙设备可用名单。|
|set_browser_policies|[browser.setPolicySync](arkts-mdm-setpolicysync-f.md#setpolicysync-1)<br>
[browser.getPoliciesSync](arkts-mdm-getpoliciessync-f.md#getpoliciessync-1)|为指定的浏览器设置浏览器子策略。<br>获取指定浏览器的策略。|
|allowed_install_bundles|
[bundleManager.addAllowedInstallBundlesSync](arkts-mdm-addallowedinstallbundlessync-f.md#addallowedinstallbundlessync-1)
<br>
[bundleManager.removeAllowedInstallBundlesSync](arkts-mdm-removeallowedinstallbundlessync-f.md#removeallowedinstallbundlessync-1)
<br>
[bundleManager.getAllowedInstallBundlesSync](arkts-mdm-getallowedinstallbundlessync-f.md#getallowedinstallbundlessync-1)
|添加应用至应用程序包安装允许名单，添加至允许名单的应用允许在当前/指定用户下安装，否则不允许安装。<br>从应用程序包安装允许名单中移除应用。<br>获取当前/指定用户下的应用程序包安装允许名单。|
|disallowed_install_bundles|
[bundleManager.addDisallowedInstallBundlesSync](arkts-mdm-adddisallowedinstallbundlessync-f.md#adddisallowedinstallbundlessync-1)
<br>
[bundleManager.removeDisallowedInstallBundlesSync](arkts-mdm-removedisallowedinstallbundlessync-f.md#removedisallowedinstallbundlessync-1)
<br>
[bundleManager.getDisallowedInstallBundlesSync](arkts-mdm-getdisallowedinstallbundlessync-f.md#getdisallowedinstallbundlessync-1)
|添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在当前/指定用户下安装。<br>从应用程序包安装禁止名单中移除应用。<br>获取当前/指定用户下的应用程序包安装禁止名单。|
|disallowed_uninstall_bundles|
[bundleManager.addDisallowedUninstallBundlesSync](arkts-mdm-adddisalloweduninstallbundlessync-f.md#adddisalloweduninstallbundlessync-1)
<br>
[bundleManager.removeDisallowedUninstallBundlesSync](arkts-mdm-removedisalloweduninstallbundlessync-f.md#removedisalloweduninstallbundlessync-1)
<br>
[bundleManager.getDisallowedUninstallBundlesSync](arkts-mdm-getdisalloweduninstallbundlessync-f.md#getdisalloweduninstallbundlessync-1)
|添加应用至应用程序包卸载禁止名单，添加至禁止名单的应用不允许在当前/指定用户下卸载。<br>从应用程序包卸载禁止名单中移除应用。<br>获取当前/指定用户下的应用包程序卸载禁止名单。|
|get_device_info|[deviceInfo.getDeviceInfo](arkts-mdm-getdeviceinfo-f.md#getdeviceinfo-1)|获取设备信息。|
|location_policy|
[locationManager.setLocationPolicy](arkts-mdm-setlocationpolicy-f.md#setlocationpolicy-1)<br>
[locationManager.getLocationPolicy](arkts-mdm-getlocationpolicy-f.md#getlocationpolicy-1)|设置位置服务管
理策略。<br>查询位置服务策略。|
|disabled_network_interface|
[networkManager.setNetworkInterfaceDisabledSync](arkts-mdm-setnetworkinterfacedisabledsync-f.md#setnetworkinterfacedisabledsync-1)
<br>
[networkManager.isNetworkInterfaceDisabledSync](arkts-mdm-isnetworkinterfacedisabledsync-f.md#isnetworkinterfacedisabledsync-1)
|禁止设备使用指定网络。<br>查询指定网络接口是否被禁用。|
|global_proxy|
[networkManager.setGlobalProxySync](arkts-mdm-setglobalproxysync-f.md#setglobalproxysync-1)<br>
[networkManager.getGlobalProxySync](arkts-mdm-getglobalproxysync-f.md#getglobalproxysync-1)|设置网络全局代理
。<br>获取网络全局代理。|
|disabled_bluetooth|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入bluetooth，禁用/启用蓝牙能力。<br>feature传入bluetooth，查询是否禁用蓝牙能力。|
|disallow_modify_datetime|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入modifyDateTime，禁用/启用设置系统时间能力。<br>feature传入modifyDateTime，查询是否禁用修改系统时间能力。|
|disabled_printer|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入printer，禁用/启用打印能力。<br>feature传入printer，查询是否禁用打印能力。|
|disabled_hdc|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入hdc，禁用/启用被其他设备通过hdc连接、调试的能力。<br>feature传入hdc，查询是否禁用被其他设备通过hdc连接、调试的能力。|
|disable_microphone|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入microphone，禁用/启用麦克风能力。<br>feature传入microphone，查询是否禁用麦克风能力。|
|fingerprint_auth|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
<br>
[restrictions.setDisallowedPolicyForAccount](arkts-mdm-setdisallowedpolicyforaccount-f.md#setdisallowedpolicyforaccount-1)
<br>
[restrictions.getDisallowedPolicyForAccount](arkts-mdm-getdisallowedpolicyforaccount-f.md#getdisallowedpolicyforaccount-1)
|feature传入fingerprint，禁用/启用指纹认证能力。<br>feature传入fingerprint，查询是否禁用指纹认证能力。<br>feature传入fingerprint，禁用/启用指定用户的指纹认证能力。<br
>feature传入fingerprint，查询是否禁用指定用户的指纹认证能力。|
|disable_usb|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入usb，禁用/启用USB能力。<br>feature传入usb，查询是否禁用USB能力。|
|disable_wifi|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入wifi，禁用/启用Wi-Fi能力。<br>feature传入wifi，查询是否禁用Wi-Fi能力。|
|disallowed_tethering|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入tethering，禁用/启用网络共享能力。<br>feature传入tethering，查询是否禁用网络共享能力。|
|inactive_user_freeze|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入inactiveUserFreeze，禁用/启用非活跃用户运行能力。<br>feature传入inactiveUserFreeze，查询是否禁用非活跃用户运行能力。|
|snapshot_skip|
[restrictions.addDisallowedListForAccount](arkts-mdm-adddisallowedlistforaccount-f.md#adddisallowedlistforaccount-1)
<br>
[restrictions.removeDisallowedListForAccount](arkts-mdm-removedisallowedlistforaccount-f.md#removedisallowedlistforaccount-1)
<br>
[restrictions.getDisallowedListForAccount](arkts-mdm-getdisallowedlistforaccount-f.md#getdisallowedlistforaccount-1)
|feature传入snapshotSkip，禁用屏幕快照能力的应用名单。<br>feature传入snapshotSkip，从禁用屏幕快照能力的应用名单中移除。<br>feature传入snapshotSkip，查询禁用屏幕快照能力
的应用名单。|
|password_policy|
[securityManager.setPasswordPolicy](arkts-mdm-setpasswordpolicy-f.md#setpasswordpolicy-1)<br>
[securityManager.getPasswordPolicy](arkts-mdm-getpasswordpolicy-f.md#getpasswordpolicy-1)
|设置设备锁屏口令策略。<br>获取设备锁屏口令策略。|
|clipboard_policy|
[securityManager.setAppClipboardPolicy](arkts-mdm-setappclipboardpolicy-f.md#setappclipboardpolicy-1)
<br>
[securityManager.getAppClipboardPolicy](arkts-mdm-getappclipboardpolicy-f.md#getappclipboardpolicy-1)
|设置设备剪贴板策略。<br>获取设备剪贴板策略。|
|watermark_image_policy|
[securityManager.setWatermarkImage](arkts-mdm-setwatermarkimage-f.md#setwatermarkimage-1)
<br>
[securityManager.cancelWatermarkImage](arkts-mdm-cancelwatermarkimage-f.md#cancelwatermarkimage-1)|设
置水印策略，当前仅支持PC/2in1使用。<br>取消水印策略，当前仅支持PC/2in1使用。|
|ntp_server|[systemManager.setNTPServer](arkts-mdm-setntpserver-f.md#setntpserver-1)<br>
[systemManager.getNTPServer](arkts-mdm-getntpserver-f.md#getntpserver-1)|设置NTP服务器的策略。<br>获取NTP服务
器信息。|
|set_update_policy|
[systemManager.setOtaUpdatePolicy](arkts-mdm-setotaupdatepolicy-f.md#setotaupdatepolicy-1)<br>
[systemManager.getOtaUpdatePolicy](arkts-mdm-getotaupdatepolicy-f.md#getotaupdatepolicy-1)|设置升级策略。<br>
查询升级策略。|
|notify_upgrade_packages|
[systemManager.notifyUpdatePackages](arkts-mdm-notifyupdatepackages-f.md#notifyupdatepackages-1)<br>
[systemManager.getUpdateResult](arkts-mdm-getupdateresult-f.md#getupdateresult-1)|通知系统更新包信息。<br>获取系
统更新结果。|
|allowed_usb_devices|
[usbManager.addAllowedUsbDevices](arkts-mdm-addallowedusbdevices-f.md#addallowedusbdevices-1)<br>
[usbManager.removeAllowedUsbDevices](arkts-mdm-removeallowedusbdevices-f.md#removeallowedusbdevices-1)<br>
[usbManager.getAllowedUsbDevices](arkts-mdm-getallowedusbdevices-f.md#getallowedusbdevices-1)|添加USB设备可用名单。<br>
移除USB设备可用名单。<br>获取USB设备可用名单。|
|usb_read_only|
[usbManager.setUsbStorageDeviceAccessPolicy](arkts-mdm-setusbstoragedeviceaccesspolicy-f.md#setusbstoragedeviceaccesspolicy-1)
<br>
[usbManager.getUsbStorageDeviceAccessPolicy](arkts-mdm-getusbstoragedeviceaccesspolicy-f.md#getusbstoragedeviceaccesspolicy-1)
|设置USB存储设备访问策略。<br>获取USB存储设备访问策略。|
|disallowed_usb_devices|
[usbManager.addDisallowedUsbDevices](arkts-mdm-adddisallowedusbdevices-f.md#adddisallowedusbdevices-1)<br>
[usbManager.removeDisallowedUsbDevices](arkts-mdm-removedisallowedusbdevices-f.md#removedisallowedusbdevices-1)<br>
[usbManager.getDisallowedUsbDevices](arkts-mdm-getdisallowedusbdevices-f.md#getdisallowedusbdevices-1)|添加禁止使用的USB
设备类型。<br>移除禁止使用的USB设备类型。<br>获取禁止使用的USB设备类型。|
|disallowed_sms|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入sms，禁用/启用设备接收、发送短信的能力，当前仅支持手机、平板设备使用。<br>feature传入sms，查询是否禁用设备接收、发送短信的能力，当前仅支持手机、平板设备使用。|
|disallowed_mms|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入mms，禁用/启用设备接收、发送彩信的能力，当前仅支持手机、平板设备使用。<br>feature传入mms，查询是否禁用设备接收、发送彩信的能力，当前仅支持手机、平板设备使用。|
|disable_backup_and_restore|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入backupAndRestore，禁用/启用备份和恢复能力，当前仅支持手机、平板使用。<br>feature传入backupAndRestore，查询是否禁用备份和恢复能力，当前仅支持手机、平板使用。|
|installed_bundle_info_list|
[bundleManager.getInstalledBundleList](arkts-mdm-getinstalledbundlelist-f.md#getinstalledbundlelist-1)
|获取设备指定用户下已安装应用列表。|
|clear_up_application_data|
[applicationManager.clearUpApplicationData](arkts-mdm-clearupapplicationdata-f.md#clearupapplicationdata-1)
|清除应用产生的所有数据。|
|disallow_unmute_device|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入unmuteDevice，禁用/启用设备媒体播放声音能力。<br>feature传入unmuteDevice，查询是否禁用设备媒体播放声音能力。|
|disabled_hdc_remote|
[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-getdisallowedpolicy-f.md#getdisallowedpolicy-1)
|feature传入hdcRemote，禁用/启用设备通过hdc调试其他设备的能力。<br>feature传入hdcRemote，查询是否禁用设备通过hdc调试其他设备的能力。|

**起始版本：** 9

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [disableAdmin](arkts-mdm-disableadmin-f.md#disableadmin-3) | 解除激活指定用户的设备管理应用。使用Promise异步回调。 |
| [disableDeviceAdmin](arkts-mdm-disabledeviceadmin-f.md#disabledeviceadmin-1) | [超级设备管理应用](../../../../mdm/mdm-kit-term.md#sda)通过该接口可以解除激活其他[普通设备管理应用](../../../../mdm/mdm-kit-term.md#da)，使用Promise异步回调。该接口仅支持超级设备管理应用调用。 |
| [enableDeviceAdmin](arkts-mdm-enabledeviceadmin-f.md#enabledeviceadmin-1) | [超级设备管理应用](../../../../mdm/mdm-kit-term.md#sda)通过该接口可以激活其他[普通设备管理应用](../../../../mdm/mdm-kit-term.md#da)，使用Promise异步回调。该接口仅支持超级设备管理应用调用。 |
| [enableSelfDeviceAdmin](arkts-mdm-enableselfdeviceadmin-f.md#enableselfdeviceadmin-1) | 在企业设备中，MDM应用没有预置激活的场景下，MDM应用可以通过该接口实现自激活。该接口仅支持激活MDM应用自身，不支持激活其他MDM应用；支持的激活类型包括超级设备管理应用和普通设备管理应用。&lt;!--RP1--&gt;&lt;!--RP1End--&gt; |
| [getDelegatedBundleNames](arkts-mdm-getdelegatedbundlenames-f.md#getdelegatedbundlenames-1) | 查询可以访问某个委托策略的被委托应用，输出被委托应用列表。 |
| [getDelegatedPolicies](arkts-mdm-getdelegatedpolicies-f.md#getdelegatedpolicies-1) | 查询被委托应用可访问的策略列表。 |
| [isByodAdmin](arkts-mdm-isbyodadmin-f.md#isbyodadmin-1) | 根据企业设备管理扩展组件查询当前应用是否被激活为BYOD设备管理应用。 |
| [setDelegatedPolicies](arkts-mdm-setdelegatedpolicies-f.md#setdelegatedpolicies-1) | 委托其他应用来设置设备的管控策略。被委托的其他应用需申请委托策略对应接口所需权限。 |
| [startAdminProvision](arkts-mdm-startadminprovision-f.md#startadminprovision-1) | 设备管理应用拉起BYOD管理员激活页面进行激活。 |
| [subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1) | 订阅系统管理事件。 |
| [unsubscribeManagedEventSync](arkts-mdm-unsubscribemanagedeventsync-f.md#unsubscribemanagedeventsync-1) | 取消订阅系统管理事件。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [authorizeAdmin](arkts-mdm-authorizeadmin-f-sys.md#authorizeadmin-1) | 授予指定应用管理员权限。使用callback异步回调。 |
| [authorizeAdmin](arkts-mdm-authorizeadmin-f-sys.md#authorizeadmin-2) | 授予指定应用管理员权限。使用Promise异步回调。 |
| [disableAdmin](arkts-mdm-disableadmin-f-sys.md#disableadmin-1) | 将当前用户下指定的普通设备管理应用解除激活。使用callback异步回调。 |
| [disableAdmin](arkts-mdm-disableadmin-f-sys.md#disableadmin-2) | 将指定用户（通过userId指定）下指定的普通管理应用解除激活。使用callback异步回调。 |
| [disableSuperAdmin](arkts-mdm-disablesuperadmin-f-sys.md#disablesuperadmin-1) | 根据bundleName将超级设备管理应用解除激活。使用callback异步回调。 |
| [disableSuperAdmin](arkts-mdm-disablesuperadmin-f-sys.md#disablesuperadmin-2) | 根据bundleName将超级设备管理应用解除激活。使用Promise异步回调。 |
| [enableAdmin](arkts-mdm-enableadmin-f-sys.md#enableadmin-1) | 激活指定的设备管理应用。超级设备管理应用仅在首用户（u100）下可激活。激活后，应用不可卸载，其[企业设备管理扩展能力](../../../../mdm/mdm-kit-term.md#企业设备管理扩展能力)组件将开机自启并在用户切换后自启。使用callback异步回调。 |
| [enableAdmin](arkts-mdm-enableadmin-f-sys.md#enableadmin-2) | 激活指定用户（通过userId指定）下指定的设备管理应用，其中超级管理应用仅能在首用户（u100）下被激活。使用callback异步回调。 |
| [enableAdmin](arkts-mdm-enableadmin-f-sys.md#enableadmin-3) | 激活当前/指定用户下指定的设备管理应用，其中超级管理应用仅能在首用户（u100）下被激活。使用Promise异步回调。 |
| [getAdmins](arkts-mdm-getadmins-f-sys.md#getadmins-1) | 查询当前用户下的所有设备管理应用。使用Promise异步回调。 |
| [getEnterpriseInfo](arkts-mdm-getenterpriseinfo-f-sys.md#getenterpriseinfo-1) | 获取设备管理应用的企业信息。使用callback异步回调。 |
| [getEnterpriseInfo](arkts-mdm-getenterpriseinfo-f-sys.md#getenterpriseinfo-2) | 获取设备管理应用的企业信息，使用Promise异步回调。 |
| [getEnterpriseManagedTips](arkts-mdm-getenterprisemanagedtips-f-sys.md#getenterprisemanagedtips-1) | 查询企业定制信息 |
| [getSuperAdmin](arkts-mdm-getsuperadmin-f-sys.md#getsuperadmin-1) | 查询首用户（u100）下的超级设备管理应用。使用Promise异步回调。 |
| [isAdminEnabled](arkts-mdm-isadminenabled-f-sys.md#isadminenabled-1) | 查询当前用户下指定的设备管理应用是否被激活。使用callback异步回调。 |
| [isAdminEnabled](arkts-mdm-isadminenabled-f-sys.md#isadminenabled-2) | 查询指定用户（通过userId指定）下指定的设备管理应用是否被激活。使用callback异步回调。 |
| [isAdminEnabled](arkts-mdm-isadminenabled-f-sys.md#isadminenabled-3) | 查询当前/指定用户下指定的设备管理应用是否被激活。使用Promise异步回调。 |
| [isSuperAdmin](arkts-mdm-issuperadmin-f-sys.md#issuperadmin-1) | 根据bundleName查询首用户（u100）下的超级设备管理应用是否被激活。使用callback异步回调。 |
| [isSuperAdmin](arkts-mdm-issuperadmin-f-sys.md#issuperadmin-2) | 根据bundleName查询首用户（u100）下的超级设备管理应用是否被激活。使用Promise异步回调。 |
| [replaceSuperAdmin](arkts-mdm-replacesuperadmin-f-sys.md#replacesuperadmin-1) | 将指定应用替换成超级设备管理应用。 |
| [setAdminRunningMode](arkts-mdm-setadminrunningmode-f-sys.md#setadminrunningmode-1) | 设置设备管理应用的运行模式。 |
| [setDelegatedPolicies](arkts-mdm-setdelegatedpolicies-f-sys.md#setdelegatedpolicies-2) | 委托其他应用来设置设备的管控策略。被委托的其他应用需申请委托策略对应接口所需权限。 |
| [setEnterpriseInfo](arkts-mdm-setenterpriseinfo-f-sys.md#setenterpriseinfo-1) | 设置设备管理应用的企业信息。使用callback异步回调。 |
| [setEnterpriseInfo](arkts-mdm-setenterpriseinfo-f-sys.md#setenterpriseinfo-2) | 设置设备管理应用的企业信息。使用Promise异步回调。 |
| [subscribeManagedEvent](arkts-mdm-subscribemanagedevent-f-sys.md#subscribemanagedevent-1) | 订阅系统管理事件。使用callback异步回调。 |
| [subscribeManagedEvent](arkts-mdm-subscribemanagedevent-f-sys.md#subscribemanagedevent-2) | 订阅系统管理事件。使用Promise异步回调。 |
| [unsubscribeManagedEvent](arkts-mdm-unsubscribemanagedevent-f-sys.md#unsubscribemanagedevent-1) | 取消订阅系统管理事件。使用callback异步回调。 |
| [unsubscribeManagedEvent](arkts-mdm-unsubscribemanagedevent-f-sys.md#unsubscribemanagedevent-2) | 取消订阅系统管理事件。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EnterpriseInfo](arkts-mdm-enterpriseinfo-i-sys.md) | 设备管理应用的企业信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AdminType](arkts-mdm-admintype-e.md) | 设备管理应用的类型。 |
| [ManagedEvent](arkts-mdm-managedevent-e.md) | 可订阅的系统管理事件。 |
| [Policy](arkts-mdm-policy-e.md) | # 可委托策略列表\| 策略名称 \| 对应接口 \| 说明 \|\| --- \| --- \| --- \|\|disallow_add_local_account\|[accountManager.disallowOsAccountAddition](arkts-mdm-disallowosaccountaddition-f.md#disallowosaccountaddition-1)<br>[accountManager.isOsAccountAdditionDisallowed](arkts-mdm-isosaccountadditiondisallowed-f.md#isosaccountadditiondisallowed-1)\| 不传accountId参数，禁止设备创建本地用户。<br>不传accountId参数，查询是否禁止设备创建本地用户。\|\|disallow_add_os_account_by_user\|[accountManager.disallowOsAccountAddition](arkts-mdm-disallowosaccountaddition-f.md#disallowosaccountaddition-1)<br>[accountManager.isOsAccountAdditionDisallowed](arkts-mdm-isosaccountadditiondisallowed-f.md#isosaccountadditiondisallowed-1)\| 需传入accountId参数，禁止指定用户添加账号。<br>需传入accountId参数，查询是否禁止指定用户添加账号。\|\|disallow_running_bundles\|[applicationManager.addDisallowedRunningBundlesSync](arkts-mdm-adddisallowedrunningbundlessync-f.md#adddisallowedrunningbundlessync-1)<br>[applicationManager.removeDisallowedRunningBundlesSync](arkts-mdm-removedisallowedrunningbundlessync-f.md#removedisallowedrunningbundlessync-1)<br>[applicationManager.getDisallowedRunningBundlesSync](arkts-mdm-getdisallowedrunningbundlessync-f.md#getdisallowedrunningbundlessync-1)\|添加应用至应用运行禁止名单，添加至禁止名单的应用不允许在当前/指定用户下运行。<br>从应用运行禁止名单中移除应用。<br>获取当前/指定用户下的应用运行禁止名单。 \|\|manage_auto_start_apps\|[applicationManager.addAutoStartApps](arkts-mdm-addautostartapps-f.md#addautostartapps-1)<br>[applicationManager.removeAutoStartApps](arkts-mdm-removeautostartapps-f.md#removeautostartapps-1)<br>[applicationManager.getAutoStartApps](arkts-mdm-getautostartapps-f.md#getautostartapps-1)\|添加开机自启动应用名单。<br>从开机自启动应用名单中移除应用。<br>查询开机自启动应用名单。\|\|allowed_bluetooth_devices\|[bluetoothManager.addAllowedBluetoothDevices](arkts-mdm-addallowedbluetoothdevices-f.md#addallowedbluetoothdevices-1)<br>[bluetoothManager.removeAllowedBluetoothDevices](arkts-mdm-removeallowedbluetoothdevices-f.md#removeallowedbluetoothdevices-1)<br>[bluetoothManager.getAllowedBluetoothDevices](arkts-mdm-getallowedbluetoothdevices-f.md#getallowedbluetoothdevices-1)\|添加蓝牙设备可用名单。<br>从蓝牙设备可用名单中移除。<br>查询蓝牙设备可用名单。\|\|set_browser_policies\|[browser.setPolicySync](arkts-mdm-setpolicysync-f.md#setpolicysync-1)<br>[browser.getPoliciesSync](arkts-mdm-getpoliciessync-f.md#getpoliciessync-1)\|为指定的浏览器设置浏览器子策略。<br>获取指定浏览器的策略。\|\|allowed_install_bundles\|[bundleManager.addAllowedInstallBundlesSync](arkts-mdm-addallowedinstallbundlessync-f.md#addallowedinstallbundlessync-1)<br>[bundleManager.removeAllowedInstallBundlesSync](arkts-mdm-removeallowedinstallbundlessync-f.md#removeallowedinstallbundlessync-1)<br>[bundleManager.getAllowedInstallBundlesSync](arkts-mdm-getallowedinstallbundlessync-f.md#getallowedinstallbundlessync-1)\|添加应用至应用程序包安装允许名单，添加至允许名单的应用允许在当前/指定用户下安装，否则不允许安装。<br>从应用程序包安装允许名单中移除应用。<br>获取当前/指定用户下的应用程序包安装允许名单。\|\|disallowed_install_bundles\|[bundleManager.addDisallowedInstallBundlesSync](arkts-mdm-adddisallowedinstallbundlessync-f.md#adddisallowedinstallbundlessync-1)<br>[bundleManager.removeDisallowedInstallBundlesSync](arkts-mdm-removedisallowedinstallbundlessync-f.md#removedisallowedinstallbundlessync-1)<br>[bundleManager.getDisallowedInstallBundlesSync](arkts-mdm-getdisallowedinstallbundlessync-f.md#getdisallowedinstallbundlessync-1)\|添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在当前/指定用户下安装。<br>从应用程序包安装禁止名单中移除应用。<br>获取当前/指定用户下的应用程序包安装禁止名单。\|\|disallowed_uninstall_bundles\|[bundleManager.addDisallowedUninstallBundlesSync](arkts-mdm-adddisalloweduninstallbundlessync-f.md#adddisalloweduninstallbundlessync-1)<br>[bundleManager.removeDisallowedUninstallBundlesSync](arkts-mdm-removedisalloweduninstallbundlessync-f.md#removedisalloweduninstallbundlessync-1)<br>[bundleManager.getDisallowedUninstallBundlesSync](arkts-mdm-getdisalloweduninstallbundlessync-f.md#getdisalloweduninstallbundlessync-1)\|添加应用至应用程序包卸载禁止名单，添加至禁止名单的应用不允许在当前/指定用户下卸载。<br>从应用程序包卸载禁止名单中移除应用。<br>获取当前/指定用户下的应用包程序卸载禁止名单。\|\|get_device_info\|[deviceInfo.getDeviceInfo](arkts-mdm-getdeviceinfo-f.md#getdeviceinfo-1)\|获取设备信息。\|\|location_policy\|[locationManager.setLocationPolicy](arkts-mdm-setlocationpolicy-f.md#setlocationpolicy-1)<br>[locationManager.getLocationPolicy](arkts-mdm-getlocationpolicy-f.md#getlocationpolicy-1)\|设置位置服务管理策略。<br>查询位置服务策略。\|\|disabled_network_interface\|[networkManager.setNetworkInterfaceDisabledSync](arkts-mdm-setnetworkinterfacedisabledsync-f.md#setnetworkinterfacedisabledsync-1)<br>[networkManager.isNetworkInterfaceDisabledSync](arkts-mdm-isnetworkinterfacedisabledsync-f.md#isnetworkinterfacedisabledsync-1)\|禁止设备使用指定网络。<br>查询指定网络接口是否被禁用。\|\|global_proxy\|[networkManager.setGlobalProxySync](arkts-mdm-setglobalproxysync-f.md#setglobalproxysync-1)<br>[networkManager.getGlobalProxySync](arkts-mdm-getglobalproxysync-f.md#getglobalproxysync-1)\|设置网络全局代理。<br>获取网络全局代理。\|\|disabled_bluetooth\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入bluetooth，禁用/启用蓝牙能力。<br>feature传入bluetooth，查询是否禁用蓝牙能力。\|\|disallow_modify_datetime\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入modifyDateTime，禁用/启用设置系统时间能力。<br>feature传入modifyDateTime，查询是否禁用修改系统时间能力。\|\|disabled_printer\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入printer，禁用/启用打印能力。<br>feature传入printer，查询是否禁用打印能力。\|\|disabled_hdc\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入hdc，禁用/启用被其他设备通过hdc连接、调试的能力。<br>feature传入hdc，查询是否禁用被其他设备通过hdc连接、调试的能力。\|\|disable_microphone\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入microphone，禁用/启用麦克风能力。<br>feature传入microphone，查询是否禁用麦克风能力。\|\|fingerprint_auth\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))<br>[restrictions.setDisallowedPolicyForAccount](arkts-mdm-setdisallowedpolicyforaccount-f.md#setdisallowedpolicyforaccount-1)<br>[restrictions.getDisallowedPolicyForAccount](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicyForAccount(admin: Want \| null, feature: string, accountId: number))\|feature传入fingerprint，禁用/启用指纹认证能力。<br>feature传入fingerprint，查询是否禁用指纹认证能力。<br>feature传入fingerprint，禁用/启用指定用户的指纹认证能力。&lt;br&gt;feature传入fingerprint，查询是否禁用指定用户的指纹认证能力。\|\|disable_usb\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入usb，禁用/启用USB能力。<br>feature传入usb，查询是否禁用USB能力。\|\|disable_wifi\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入wifi，禁用/启用Wi-Fi能力。<br>feature传入wifi，查询是否禁用Wi-Fi能力。\|\|disallowed_tethering\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入tethering，禁用/启用网络共享能力。<br>feature传入tethering，查询是否禁用网络共享能力。\|\|inactive_user_freeze\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入inactiveUserFreeze，禁用/启用非活跃用户运行能力。<br>feature传入inactiveUserFreeze，查询是否禁用非活跃用户运行能力。\|\|snapshot_skip\|[restrictions.addDisallowedListForAccount](arkts-mdm-adddisallowedlistforaccount-f.md#adddisallowedlistforaccount-1)<br>[restrictions.removeDisallowedListForAccount](arkts-mdm-removedisallowedlistforaccount-f.md#removedisallowedlistforaccount-1)<br>[restrictions.getDisallowedListForAccount](arkts-mdm-getdisallowedlistforaccount-f.md#getdisallowedlistforaccount-1)\|feature传入snapshotSkip，禁用屏幕快照能力的应用名单。<br>feature传入snapshotSkip，从禁用屏幕快照能力的应用名单中移除。<br>feature传入snapshotSkip，查询禁用屏幕快照能力的应用名单。\|\|password_policy\|[securityManager.setPasswordPolicy](arkts-mdm-setpasswordpolicy-f.md#setpasswordpolicy-1)<br>[securityManager.getPasswordPolicy](arkts-mdm-getpasswordpolicy-f.md#getpasswordpolicy-1)\|设置设备锁屏口令策略。<br>获取设备锁屏口令策略。\|\|clipboard_policy\|[securityManager.setAppClipboardPolicy](arkts-mdm-setappclipboardpolicy-f.md#setappclipboardpolicy-1)<br>[securityManager.getAppClipboardPolicy](arkts-mdm-getappclipboardpolicy-f.md#getappclipboardpolicy-1)\|设置设备剪贴板策略。<br>获取设备剪贴板策略。\|\|watermark_image_policy\|[securityManager.setWatermarkImage](@ohos.enterprise.securityManager:securityManager.setWatermarkImage(admin: Want, bundleName: string, source: string \| image.PixelMap, accountId: number))<br>[securityManager.cancelWatermarkImage](arkts-mdm-cancelwatermarkimage-f.md#cancelwatermarkimage-1)\|设置水印策略，当前仅支持PC/2in1使用。<br>取消水印策略，当前仅支持PC/2in1使用。\|\|ntp_server\|[systemManager.setNTPServer](arkts-mdm-setntpserver-f.md#setntpserver-1)<br>[systemManager.getNTPServer](arkts-mdm-getntpserver-f.md#getntpserver-1)\|设置NTP服务器的策略。<br>获取NTP服务器信息。\|\|set_update_policy\|[systemManager.setOtaUpdatePolicy](arkts-mdm-setotaupdatepolicy-f.md#setotaupdatepolicy-1)<br>[systemManager.getOtaUpdatePolicy](arkts-mdm-getotaupdatepolicy-f.md#getotaupdatepolicy-1)\|设置升级策略。&lt;br&gt;查询升级策略。\|\|notify_upgrade_packages\|[systemManager.notifyUpdatePackages](arkts-mdm-notifyupdatepackages-f.md#notifyupdatepackages-1)<br>[systemManager.getUpdateResult](arkts-mdm-getupdateresult-f.md#getupdateresult-1)\|通知系统更新包信息。<br>获取系统更新结果。\|\|allowed_usb_devices\|[usbManager.addAllowedUsbDevices](arkts-mdm-addallowedusbdevices-f.md#addallowedusbdevices-1)<br>[usbManager.removeAllowedUsbDevices](arkts-mdm-removeallowedusbdevices-f.md#removeallowedusbdevices-1)<br>[usbManager.getAllowedUsbDevices](arkts-mdm-getallowedusbdevices-f.md#getallowedusbdevices-1)\|添加USB设备可用名单。&lt;br&gt;移除USB设备可用名单。<br>获取USB设备可用名单。\|\|usb_read_only\|[usbManager.setUsbStorageDeviceAccessPolicy](arkts-mdm-setusbstoragedeviceaccesspolicy-f.md#setusbstoragedeviceaccesspolicy-1)<br>[usbManager.getUsbStorageDeviceAccessPolicy](arkts-mdm-getusbstoragedeviceaccesspolicy-f.md#getusbstoragedeviceaccesspolicy-1)\|设置USB存储设备访问策略。<br>获取USB存储设备访问策略。\|\|disallowed_usb_devices\|[usbManager.addDisallowedUsbDevices](arkts-mdm-adddisallowedusbdevices-f.md#adddisallowedusbdevices-1)<br>[usbManager.removeDisallowedUsbDevices](arkts-mdm-removedisallowedusbdevices-f.md#removedisallowedusbdevices-1)<br>[usbManager.getDisallowedUsbDevices](arkts-mdm-getdisallowedusbdevices-f.md#getdisallowedusbdevices-1)\|添加禁止使用的USB设备类型。<br>移除禁止使用的USB设备类型。<br>获取禁止使用的USB设备类型。\|\|disallowed_sms\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入sms，禁用/启用设备接收、发送短信的能力，当前仅支持手机、平板设备使用。<br>feature传入sms，查询是否禁用设备接收、发送短信的能力，当前仅支持手机、平板设备使用。\|\|disallowed_mms\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入mms，禁用/启用设备接收、发送彩信的能力，当前仅支持手机、平板设备使用。<br>feature传入mms，查询是否禁用设备接收、发送彩信的能力，当前仅支持手机、平板设备使用。\|\|disable_backup_and_restore\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入backupAndRestore，禁用/启用备份和恢复能力，当前仅支持手机、平板使用。<br>feature传入backupAndRestore，查询是否禁用备份和恢复能力，当前仅支持手机、平板使用。\|\|installed_bundle_info_list\|[bundleManager.getInstalledBundleList](arkts-mdm-getinstalledbundlelist-f.md#getinstalledbundlelist-1)\|获取设备指定用户下已安装应用列表。\|\|clear_up_application_data\|[applicationManager.clearUpApplicationData](arkts-mdm-clearupapplicationdata-f.md#clearupapplicationdata-1)\|清除应用产生的所有数据。\|\|disallow_unmute_device\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入unmuteDevice，禁用/启用设备媒体播放声音能力。<br>feature传入unmuteDevice，查询是否禁用设备媒体播放声音能力。\|\|disabled_hdc_remote\|[restrictions.setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](@ohos.enterprise.restrictions:restrictions.getDisallowedPolicy(admin: Want \| null, feature: string))\|feature传入hdcRemote，禁用/启用设备通过hdc调试其他设备的能力。<br>feature传入hdcRemote，查询是否禁用设备通过hdc调试其他设备的能力。\| |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AdminType](arkts-mdm-admintype-e-sys.md) | 设备管理应用的类型。 |
| [RunningMode](arkts-mdm-runningmode-e-sys.md) | 设备管理的运行模式。 |
<!--DelEnd-->

