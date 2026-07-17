# Policy

# 可委托策略列表

| 策略名称 | 对应接口 | 说明 |  
| --- | --- | --- |  
|disallow_add_local_account|[accountManager.disallowOsAccountAddition](arkts-mdm-accountmanager-disallowosaccountaddition-f.md#disallowosaccountaddition-1)<br>[accountManager.isOsAccountAdditionDisallowed](arkts-mdm-accountmanager-isosaccountadditiondisallowed-f.md#isosaccountadditiondisallowed-1)  
| 不传accountId参数，禁止设备创建本地用户。<br>不传accountId参数，查询是否禁止设备创建本地用户。|  
|disallow_add_os_account_by_user|[accountManager.disallowOsAccountAddition](arkts-mdm-accountmanager-disallowosaccountaddition-f.md#disallowosaccountaddition-1)<br>[accountManager.isOsAccountAdditionDisallowed](arkts-mdm-accountmanager-isosaccountadditiondisallowed-f.md#isosaccountadditiondisallowed-1)  
| 需传入accountId参数，禁止指定用户添加账号。<br>需传入accountId参数，查询是否禁止指定用户添加账号。|  
|disallow_running_bundles|[applicationManager.addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md#adddisallowedrunningbundlessync-1)<br>[applicationManager.removeDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-removedisallowedrunningbundlessync-f.md#removedisallowedrunningbundlessync-1)<br>[applicationManager.getDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-getdisallowedrunningbundlessync-f.md#getdisallowedrunningbundlessync-1)  
|添加应用至应用运行禁止名单，添加至禁止名单的应用不允许在当前/指定用户下运行。<br>从应用运行禁止名单中移除应用。<br>获取当前/指定用户下的应用运行禁止名单。 |  
|manage_auto_start_apps|[applicationManager.addAutoStartApps](arkts-mdm-applicationmanager-addautostartapps-f.md#addautostartapps-1)<br>[applicationManager.removeAutoStartApps](arkts-mdm-applicationmanager-removeautostartapps-f.md#removeautostartapps-1)<br>[applicationManager.getAutoStartApps](arkts-mdm-applicationmanager-getautostartapps-f.md#getautostartapps-1)  
|添加开机自启动应用名单。<br>从开机自启动应用名单中移除应用。<br>查询开机自启动应用名单。|  
|allowed_bluetooth_devices|[bluetoothManager.addAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-addallowedbluetoothdevices-f.md#addallowedbluetoothdevices-1)<br>[bluetoothManager.removeAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-removeallowedbluetoothdevices-f.md#removeallowedbluetoothdevices-1)<br>[bluetoothManager.getAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-getallowedbluetoothdevices-f.md#getallowedbluetoothdevices-1)  
|添加蓝牙设备可用名单。<br>从蓝牙设备可用名单中移除。<br>查询蓝牙设备可用名单。|  
|set_browser_policies|[browser.setPolicySync](arkts-mdm-browser-setpolicysync-f.md#setpolicysync-1)<br>[browser.getPoliciesSync](arkts-mdm-browser-getpoliciessync-f.md#getpoliciessync-1)|为指定的浏览器设置浏览器子策略。<br>获取指定浏览器的策略。|  
|allowed_install_bundles|[bundleManager.addAllowedInstallBundlesSync](arkts-mdm-bundlemanager-addallowedinstallbundlessync-f.md#addallowedinstallbundlessync-1)<br>[bundleManager.removeAllowedInstallBundlesSync](arkts-mdm-bundlemanager-removeallowedinstallbundlessync-f.md#removeallowedinstallbundlessync-1)<br>[bundleManager.getAllowedInstallBundlesSync](arkts-mdm-bundlemanager-getallowedinstallbundlessync-f.md#getallowedinstallbundlessync-1)  
|添加应用至应用程序包安装允许名单，添加至允许名单的应用允许在当前/指定用户下安装，否则不允许安装。<br>从应用程序包安装允许名单中移除应用。<br>获取当前/指定用户下的应用程序包安装允许名单。|  
|disallowed_install_bundles|[bundleManager.addDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-adddisallowedinstallbundlessync-f.md#adddisallowedinstallbundlessync-1)<br>[bundleManager.removeDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-removedisallowedinstallbundlessync-f.md#removedisallowedinstallbundlessync-1)<br>[bundleManager.getDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-getdisallowedinstallbundlessync-f.md#getdisallowedinstallbundlessync-1)  
|添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在当前/指定用户下安装。<br>从应用程序包安装禁止名单中移除应用。<br>获取当前/指定用户下的应用程序包安装禁止名单。|  
|disallowed_uninstall_bundles|[bundleManager.addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#adddisalloweduninstallbundlessync-1)<br>[bundleManager.removeDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-removedisalloweduninstallbundlessync-f.md#removedisalloweduninstallbundlessync-1)<br>[bundleManager.getDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-getdisalloweduninstallbundlessync-f.md#getdisalloweduninstallbundlessync-1)  
|添加应用至应用程序包卸载禁止名单，添加至禁止名单的应用不允许在当前/指定用户下卸载。<br>从应用程序包卸载禁止名单中移除应用。<br>获取当前/指定用户下的应用包程序卸载禁止名单。|  
|get_device_info|[deviceInfo.getDeviceInfo](arkts-mdm-deviceinfo-getdeviceinfo-f.md#getdeviceinfo-1)|获取设备信息。|  
|location_policy|[locationManager.setLocationPolicy](arkts-mdm-locationmanager-setlocationpolicy-f.md#setlocationpolicy-1)<br>[locationManager.getLocationPolicy](arkts-mdm-locationmanager-getlocationpolicy-f.md#getlocationpolicy-1)|设置位置服务管理策略。<br>查询位置服务策略。|  
|disabled_network_interface|[networkManager.setNetworkInterfaceDisabledSync](arkts-mdm-networkmanager-setnetworkinterfacedisabledsync-f.md#setnetworkinterfacedisabledsync-1)<br>[networkManager.isNetworkInterfaceDisabledSync](arkts-mdm-networkmanager-isnetworkinterfacedisabledsync-f.md#isnetworkinterfacedisabledsync-1)  
|禁止设备使用指定网络。<br>查询指定网络接口是否被禁用。|  
|global_proxy|[networkManager.setGlobalProxySync](arkts-mdm-networkmanager-setglobalproxysync-f.md#setglobalproxysync-1)<br>[networkManager.getGlobalProxySync](arkts-mdm-networkmanager-getglobalproxysync-f.md#getglobalproxysync-1)|设置网络全局代理。<br>获取网络全局代理。|  
|disabled_bluetooth|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入bluetooth，禁用/启用蓝牙能力。<br>feature传入bluetooth，查询是否禁用蓝牙能力。|  
|disallow_modify_datetime|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入modifyDateTime，禁用/启用设置系统时间能力。<br>feature传入modifyDateTime，查询是否禁用修改系统时间能力。|  
|disabled_printer|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入printer，禁用/启用打印能力。<br>feature传入printer，查询是否禁用打印能力。|  
|disabled_hdc|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入hdc，禁用/启用被其他设备通过hdc连接、调试的能力。<br>feature传入hdc，查询是否禁用被其他设备通过hdc连接、调试的能力。|  
|disable_microphone|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入microphone，禁用/启用麦克风能力。<br>feature传入microphone，查询是否禁用麦克风能力。|  
|fingerprint_auth|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)<br>[restrictions.setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setdisallowedpolicyforaccount-1)<br>[restrictions.getDisallowedPolicyForAccount](arkts-mdm-restrictions-getdisallowedpolicyforaccount-f.md#getdisallowedpolicyforaccount-1)  
|feature传入fingerprint，禁用/启用指纹认证能力。<br>feature传入fingerprint，查询是否禁用指纹认证能力。<br>feature传入fingerprint，禁用/启用指定用户的指纹认证能力。<br>feature传入fingerprint，查询是否禁用指定用户的指纹认证能力。|  
|disable_usb|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入usb，禁用/启用USB能力。<br>feature传入usb，查询是否禁用USB能力。|  
|disable_wifi|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入wifi，禁用/启用Wi-Fi能力。<br>feature传入wifi，查询是否禁用Wi-Fi能力。|  
|disallowed_tethering|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入tethering，禁用/启用网络共享能力。<br>feature传入tethering，查询是否禁用网络共享能力。|  
|inactive_user_freeze|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入inactiveUserFreeze，禁用/启用非活跃用户运行能力。<br>feature传入inactiveUserFreeze，查询是否禁用非活跃用户运行能力。|  
|snapshot_skip|[restrictions.addDisallowedListForAccount](arkts-mdm-restrictions-adddisallowedlistforaccount-f.md#adddisallowedlistforaccount-1)<br>[restrictions.removeDisallowedListForAccount](arkts-mdm-restrictions-removedisallowedlistforaccount-f.md#removedisallowedlistforaccount-1)<br>[restrictions.getDisallowedListForAccount](arkts-mdm-restrictions-getdisallowedlistforaccount-f.md#getdisallowedlistforaccount-1)  
|feature传入snapshotSkip，禁用屏幕快照能力的应用名单。<br>feature传入snapshotSkip，从禁用屏幕快照能力的应用名单中移除。<br>feature传入snapshotSkip，查询禁用屏幕快照能力的应用名单。|  
|password_policy|[securityManager.setPasswordPolicy](arkts-mdm-securitymanager-setpasswordpolicy-f.md#setpasswordpolicy-1)<br>[securityManager.getPasswordPolicy](arkts-mdm-securitymanager-getpasswordpolicy-f.md#getpasswordpolicy-1)  
|设置设备锁屏口令策略。<br>获取设备锁屏口令策略。|  
|clipboard_policy|[securityManager.setAppClipboardPolicy](arkts-mdm-securitymanager-setappclipboardpolicy-f.md#setappclipboardpolicy-1)<br>[securityManager.getAppClipboardPolicy](arkts-mdm-securitymanager-getappclipboardpolicy-f.md#getappclipboardpolicy-1)  
|设置设备剪贴板策略。<br>获取设备剪贴板策略。|  
|watermark_image_policy|[securityManager.setWatermarkImage](arkts-mdm-securitymanager-setwatermarkimage-f.md#setwatermarkimage-1)<br>[securityManager.cancelWatermarkImage](arkts-mdm-securitymanager-cancelwatermarkimage-f.md#cancelwatermarkimage-1)  
|设置水印策略，当前仅支持PC/2in1使用。<br>取消水印策略，当前仅支持PC/2in1使用。|  
|ntp_server|[systemManager.setNTPServer](arkts-mdm-systemmanager-setntpserver-f.md#setntpserver-1)<br>[systemManager.getNTPServer](arkts-mdm-systemmanager-getntpserver-f.md#getntpserver-1)|设置NTP服务器的策略。<br>获取NTP服务器信息。|  
|set_update_policy|[systemManager.setOtaUpdatePolicy](arkts-mdm-systemmanager-setotaupdatepolicy-f.md#setotaupdatepolicy-1)<br>[systemManager.getOtaUpdatePolicy](arkts-mdm-systemmanager-getotaupdatepolicy-f.md#getotaupdatepolicy-1)|设置升级策略。<br>查询升级策略。|  
|notify_upgrade_packages|[systemManager.notifyUpdatePackages](arkts-mdm-systemmanager-notifyupdatepackages-f.md#notifyupdatepackages-1)<br>[systemManager.getUpdateResult](arkts-mdm-systemmanager-getupdateresult-f.md#getupdateresult-1)|通知系统更新包信息。<br>获取系统更新结果。|  
|allowed_usb_devices|[usbManager.addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md#addallowedusbdevices-1)<br>[usbManager.removeAllowedUsbDevices](arkts-mdm-usbmanager-removeallowedusbdevices-f.md#removeallowedusbdevices-1)<br>[usbManager.getAllowedUsbDevices](arkts-mdm-usbmanager-getallowedusbdevices-f.md#getallowedusbdevices-1)|添加USB设备可用名单。<br>移除USB设备可用名单。<br>获取USB设备可用名单。|  
|usb_read_only|[usbManager.setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md#setusbstoragedeviceaccesspolicy-1)<br>[usbManager.getUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-getusbstoragedeviceaccesspolicy-f.md#getusbstoragedeviceaccesspolicy-1)  
|设置USB存储设备访问策略。<br>获取USB存储设备访问策略。|  
|disallowed_usb_devices|[usbManager.addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices-1)<br>[usbManager.removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removedisallowedusbdevices-1)<br  
>[usbManager.getDisallowedUsbDevices](arkts-mdm-usbmanager-getdisallowedusbdevices-f.md#getdisallowedusbdevices-1)|添加禁止使用的USB设备类型。<br>移除禁止使用的USB设备类型。<br>获取禁止使用的USB设备类型。|  
|disallowed_sms|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入sms，禁用/启用设备接收、发送短信的能力，当前仅支持手机、平板设备使用。<br>feature传入sms，查询是否禁用设备接收、发送短信的能力，当前仅支持手机、平板设备使用。|  
|disallowed_mms|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入mms，禁用/启用设备接收、发送彩信的能力，当前仅支持手机、平板设备使用。<br>feature传入mms，查询是否禁用设备接收、发送彩信的能力，当前仅支持手机、平板设备使用。|  
|disable_backup_and_restore|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入backupAndRestore，禁用/启用备份和恢复能力，当前仅支持手机、平板使用。<br>feature传入backupAndRestore，查询是否禁用备份和恢复能力，当前仅支持手机、平板使用。|  
|installed_bundle_info_list|[bundleManager.getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md#getinstalledbundlelist-1)  
|获取设备指定用户下已安装应用列表。|  
|clear_up_application_data|[applicationManager.clearUpApplicationData](arkts-mdm-applicationmanager-clearupapplicationdata-f.md#clearupapplicationdata-1)  
|清除应用产生的所有数据。|  
|disallow_unmute_device|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入unmuteDevice，禁用/启用设备媒体播放声音能力。<br>feature传入unmuteDevice，查询是否禁用设备媒体播放声音能力。|  
|disabled_hdc_remote|[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)<br>[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)  
|feature传入hdcRemote，禁用/启用设备通过hdc调试其他设备的能力。<br>feature传入hdcRemote，查询是否禁用设备通过hdc调试其他设备的能力。|

**起始版本：** 20

<!--Device-adminManager-export enum Policy--><!--Device-adminManager-export enum Policy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## BLOCK_LIST

```TypeScript
BLOCK_LIST = 0
```

禁用名单。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Policy-BLOCK_LIST = 0--><!--Device-Policy-BLOCK_LIST = 0-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## TRUST_LIST

```TypeScript
TRUST_LIST = 1
```

允许名单。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Policy-TRUST_LIST = 1--><!--Device-Policy-TRUST_LIST = 1-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

