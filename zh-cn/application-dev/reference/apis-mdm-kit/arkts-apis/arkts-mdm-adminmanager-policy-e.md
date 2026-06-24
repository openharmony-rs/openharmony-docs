# Policy

```TypeScript
export enum Policy
```

# ��ί�в����б�

| �������� | ��Ӧ�ӿ� | ˵�� |
| --- | --- | --- |
|disallow_add_local_account|
[accountManager.disallowOsAccountAddition](arkts-mdm-accountmanager-disallowosaccountaddition-f.md#disallowOsAccountAddition-1)
<br>
[accountManager.isOsAccountAdditionDisallowed](arkts-mdm-accountmanager-isosaccountadditiondisallowed-f.md#isOsAccountAdditionDisallowed-1)
| ����accountId��������ֹ�豸���������û���<br>����accountId��������ѯ�Ƿ��ֹ�豸���������û���|
|disallow_add_os_account_by_user|
[accountManager.disallowOsAccountAddition](arkts-mdm-accountmanager-disallowosaccountaddition-f.md#disallowOsAccountAddition-1)
<br>
[accountManager.isOsAccountAdditionDisallowed](arkts-mdm-accountmanager-isosaccountadditiondisallowed-f.md#isOsAccountAdditionDisallowed-1)
| �贫��accountId��������ָֹ���û������˺š�<br>�贫��accountId��������ѯ�Ƿ��ָֹ���û������˺š�|
|disallow_running_bundles|
[applicationManager.addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md#addDisallowedRunningBundlesSync-1)
<br>
[applicationManager.removeDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-removedisallowedrunningbundlessync-f.md#removeDisallowedRunningBundlesSync-1)
<br>
[applicationManager.getDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-getdisallowedrunningbundlessync-f.md#getDisallowedRunningBundlesSync-1)
|����Ӧ����Ӧ�����н�ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ/ָ���û������С�<br>��Ӧ�����н�ֹ�������Ƴ�Ӧ�á�<br>��ȡ��ǰ/ָ���û��µ�Ӧ�����н�ֹ������ |
|manage_auto_start_apps|
[applicationManager.addAutoStartApps](arkts-mdm-applicationmanager-addautostartapps-f.md#addAutoStartApps-1)
<br>
[applicationManager.removeAutoStartApps](arkts-mdm-applicationmanager-removeautostartapps-f.md#removeAutoStartApps-1)
<br>
[applicationManager.getAutoStartApps](arkts-mdm-applicationmanager-getautostartapps-f.md#getAutoStartApps-1)
|���ӿ���������Ӧ��������<br>�ӿ���������Ӧ���������Ƴ�Ӧ�á�<br>��ѯ����������Ӧ��������|
|allowed_bluetooth_devices|
[bluetoothManager.addAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-addallowedbluetoothdevices-f.md#addAllowedBluetoothDevices-1)
<br>
[bluetoothManager.removeAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-removeallowedbluetoothdevices-f.md#removeAllowedBluetoothDevices-1)
<br>
[bluetoothManager.getAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-getallowedbluetoothdevices-f.md#getAllowedBluetoothDevices-1)
|���������豸����������<br>�������豸�����������Ƴ���<br>��ѯ�����豸����������|
|set_browser_policies|[browser.setPolicySync](arkts-mdm-browser-setpolicysync-f.md#setPolicySync-1)<br>
[browser.getPoliciesSync](arkts-mdm-browser-getpoliciessync-f.md#getPoliciesSync-1)|Ϊָ�������������������Ӳ��ԡ�<br>��ȡָ��������Ĳ��ԡ�|
|allowed_install_bundles|
[bundleManager.addAllowedInstallBundlesSync](arkts-mdm-bundlemanager-addallowedinstallbundlessync-f.md#addAllowedInstallBundlesSync-1)
<br>
[bundleManager.removeAllowedInstallBundlesSync](arkts-mdm-bundlemanager-removeallowedinstallbundlessync-f.md#removeAllowedInstallBundlesSync-1)
<br>
[bundleManager.getAllowedInstallBundlesSync](arkts-mdm-bundlemanager-getallowedinstallbundlessync-f.md#getAllowedInstallBundlesSync-1)
|����Ӧ����Ӧ�ó������װ��������������������������Ӧ�������ڵ�ǰ/ָ���û��°�װ������������װ��<br>��Ӧ�ó������װ�����������Ƴ�Ӧ�á�<br>��ȡ��ǰ/ָ���û��µ�Ӧ�ó������װ����������|
|disallowed_install_bundles|
[bundleManager.addDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-adddisallowedinstallbundlessync-f.md#addDisallowedInstallBundlesSync-1)
<br>
[bundleManager.removeDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-removedisallowedinstallbundlessync-f.md#removeDisallowedInstallBundlesSync-1)
<br>
[bundleManager.getDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-getdisallowedinstallbundlessync-f.md#getDisallowedInstallBundlesSync-1)
|����Ӧ����Ӧ�ó������װ��ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ/ָ���û��°�װ��<br>��Ӧ�ó������װ��ֹ�������Ƴ�Ӧ�á�<br>��ȡ��ǰ/ָ���û��µ�Ӧ�ó������װ��ֹ������|
|disallowed_uninstall_bundles|
[bundleManager.addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#addDisallowedUninstallBundlesSync-1)
<br>
[bundleManager.removeDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-removedisalloweduninstallbundlessync-f.md#removeDisallowedUninstallBundlesSync-1)
<br>
[bundleManager.getDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-getdisalloweduninstallbundlessync-f.md#getDisallowedUninstallBundlesSync-1)
|����Ӧ����Ӧ�ó����ж�ؽ�ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ/ָ���û���ж�ء�<br>��Ӧ�ó����ж�ؽ�ֹ�������Ƴ�Ӧ�á�<br>��ȡ��ǰ/ָ���û��µ�Ӧ�ð�����ж�ؽ�ֹ������|
|get_device_info|[deviceInfo.getDeviceInfo](arkts-mdm-deviceinfo-getdeviceinfo-f.md#getDeviceInfo-1)|��ȡ�豸��Ϣ��|
|location_policy|
[locationManager.setLocationPolicy](arkts-mdm-locationmanager-setlocationpolicy-f.md#setLocationPolicy-1)<br>
[locationManager.getLocationPolicy](arkts-mdm-locationmanager-getlocationpolicy-f.md#getLocationPolicy-1)|����λ�÷�
��������ԡ�<br>��ѯλ�÷�����ԡ�|
|disabled_network_interface|
[networkManager.setNetworkInterfaceDisabledSync](arkts-mdm-networkmanager-setnetworkinterfacedisabledsync-f.md#setNetworkInterfaceDisabledSync-1)
<br>
[networkManager.isNetworkInterfaceDisabledSync](arkts-mdm-networkmanager-isnetworkinterfacedisabledsync-f.md#isNetworkInterfaceDisabledSync-1)
|��ֹ�豸ʹ��ָ�����硣<br>��ѯָ������ӿ��Ƿ񱻽��á�|
|global_proxy|
[networkManager.setGlobalProxySync](arkts-mdm-networkmanager-setglobalproxysync-f.md#setGlobalProxySync-1)<br>
[networkManager.getGlobalProxySync](arkts-mdm-networkmanager-getglobalproxysync-f.md#getGlobalProxySync-1)|��������ȫ��
������<br>��ȡ����ȫ�ִ�����|
|disabled_bluetooth|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����bluetooth������/��������������<br>feature����bluetooth����ѯ�Ƿ��������������|
|disallow_modify_datetime|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����modifyDateTime������/��������ϵͳʱ��������<br>feature����modifyDateTime����ѯ�Ƿ�����޸�ϵͳʱ��������|
|disabled_printer|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����printer������/���ô�ӡ������<br>feature����printer����ѯ�Ƿ���ô�ӡ������|
|disabled_hdc|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����hdc������/���ñ������豸ͨ��hdc���ӡ����Ե�������<br>feature����hdc����ѯ�Ƿ���ñ������豸ͨ��hdc���ӡ����Ե�������|
|disable_microphone|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����microphone������/������˷�������<br>feature����microphone����ѯ�Ƿ������˷�������|
|fingerprint_auth|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
<br>
[restrictions.setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-1)
<br>
[restrictions.getDisallowedPolicyForAccount](arkts-mdm-restrictions-getdisallowedpolicyforaccount-f.md#getDisallowedPolicyForAccount-1)
|feature����fingerprint������/����ָ����֤������<br>feature����fingerprint����ѯ�Ƿ����ָ����֤������<br>feature����fingerprint������/����ָ���û���ָ����֤������<
br>feature����fingerprint����ѯ�Ƿ����ָ���û���ָ����֤������|
|disable_usb|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����usb������/����USB������<br>feature����usb����ѯ�Ƿ����USB������|
|disable_wifi|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����wifi������/����Wi-Fi������<br>feature����wifi����ѯ�Ƿ����Wi-Fi������|
|disallowed_tethering|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����tethering������/�������繲��������<br>feature����tethering����ѯ�Ƿ�������繲��������|
|inactive_user_freeze|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����inactiveUserFreeze������/���÷ǻ�Ծ�û�����������<br>feature����inactiveUserFreeze����ѯ�Ƿ���÷ǻ�Ծ�û�����������|
|snapshot_skip|
[restrictions.addDisallowedListForAccount](arkts-mdm-restrictions-adddisallowedlistforaccount-f.md#addDisallowedListForAccount-1)
<br>
[restrictions.removeDisallowedListForAccount](arkts-mdm-restrictions-removedisallowedlistforaccount-f.md#removeDisallowedListForAccount-1)
<br>
[restrictions.getDisallowedListForAccount](arkts-mdm-restrictions-getdisallowedlistforaccount-f.md#getDisallowedListForAccount-1)
|feature����snapshotSkip��������Ļ����������Ӧ��������<br>feature����snapshotSkip���ӽ�����Ļ����������Ӧ���������Ƴ���<br>feature����snapshotSkip����ѯ������Ļ����
������Ӧ��������|
|password_policy|
[securityManager.setPasswordPolicy](arkts-mdm-securitymanager-setpasswordpolicy-f.md#setPasswordPolicy-1)<br>
[securityManager.getPasswordPolicy](arkts-mdm-securitymanager-getpasswordpolicy-f.md#getPasswordPolicy-1)
|�����豸����������ԡ�<br>��ȡ�豸����������ԡ�|
|clipboard_policy|
[securityManager.setAppClipboardPolicy](arkts-mdm-securitymanager-setappclipboardpolicy-f.md#setAppClipboardPolicy-1)
<br>
[securityManager.getAppClipboardPolicy](arkts-mdm-securitymanager-getappclipboardpolicy-f.md#getAppClipboardPolicy-1)
|�����豸��������ԡ�<br>��ȡ�豸��������ԡ�|
|watermark_image_policy|
[securityManager.setWatermarkImage](arkts-mdm-securitymanager-setwatermarkimage-f.md#setWatermarkImage-1)
<br>
[securityManager.cancelWatermarkImage](arkts-mdm-securitymanager-cancelwatermarkimage-f.md#cancelWatermarkImage-1)
|����ˮӡ���ԣ���ǰ��֧��PC/2in1ʹ�á�<br>ȡ��ˮӡ���ԣ���ǰ��֧��PC/2in1ʹ�á�|
|ntp_server|[systemManager.setNTPServer](arkts-mdm-systemmanager-setntpserver-f.md#setNTPServer-1)<br>
[systemManager.getNTPServer](arkts-mdm-systemmanager-getntpserver-f.md#getNTPServer-1)|����NTP�������Ĳ��ԡ�<br>��ȡNTP
��������Ϣ��|
|set_update_policy|
[systemManager.setOtaUpdatePolicy](arkts-mdm-systemmanager-setotaupdatepolicy-f.md#setOtaUpdatePolicy-1)<br>
[systemManager.getOtaUpdatePolicy](arkts-mdm-systemmanager-getotaupdatepolicy-f.md#getOtaUpdatePolicy-1)|�����������ԡ�<
br>��ѯ�������ԡ�|
|notify_upgrade_packages|
[systemManager.notifyUpdatePackages](arkts-mdm-systemmanager-notifyupdatepackages-f.md#notifyUpdatePackages-1)<br>
[systemManager.getUpdateResult](arkts-mdm-systemmanager-getupdateresult-f.md#getUpdateResult-1)|֪ͨϵͳ���°���Ϣ��<br>��
ȡϵͳ���½����|
|allowed_usb_devices|
[usbManager.addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md#addAllowedUsbDevices-1)<br>
[usbManager.removeAllowedUsbDevices](arkts-mdm-usbmanager-removeallowedusbdevices-f.md#removeAllowedUsbDevices-1)<br>
[usbManager.getAllowedUsbDevices](arkts-mdm-usbmanager-getallowedusbdevices-f.md#getAllowedUsbDevices-1)|����USB�豸����������<
br>�Ƴ�USB�豸����������<br>��ȡUSB�豸����������|
|usb_read_only|
[usbManager.setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md#setUsbStorageDeviceAccessPolicy-1)
<br>
[usbManager.getUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-getusbstoragedeviceaccesspolicy-f.md#getUsbStorageDeviceAccessPolicy-1)
|����USB�洢�豸���ʲ��ԡ�<br>��ȡUSB�洢�豸���ʲ��ԡ�|
|disallowed_usb_devices|
[usbManager.addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)<br>
[usbManager.removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removeDisallowedUsbDevices-1)<br
>[usbManager.getDisallowedUsbDevices](arkts-mdm-usbmanager-getdisallowedusbdevices-f.md#getDisallowedUsbDevices-1)|���ӽ�ֹʹ�õ�
USB�豸���͡�<br>�Ƴ���ֹʹ�õ�USB�豸���͡�<br>��ȡ��ֹʹ�õ�USB�豸���͡�|
|disallowed_sms|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����sms������/�����豸���ա����Ͷ��ŵ���������ǰ��֧���ֻ���ƽ���豸ʹ�á�<br>feature����sms����ѯ�Ƿ�����豸���ա����Ͷ��ŵ���������ǰ��֧���ֻ���ƽ���豸ʹ�á�|
|disallowed_mms|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����mms������/�����豸���ա����Ͳ��ŵ���������ǰ��֧���ֻ���ƽ���豸ʹ�á�<br>feature����mms����ѯ�Ƿ�����豸���ա����Ͳ��ŵ���������ǰ��֧���ֻ���ƽ���豸ʹ�á�|
|disable_backup_and_restore|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����backupAndRestore������/���ñ��ݺͻָ���������ǰ��֧���ֻ���ƽ��ʹ�á�<br>feature����backupAndRestore����ѯ�Ƿ���ñ��ݺͻָ���������ǰ��֧���ֻ���ƽ��ʹ�á�|
|installed_bundle_info_list|
[bundleManager.getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md#getInstalledBundleList-1)
|��ȡ�豸ָ���û����Ѱ�װӦ���б���|
|clear_up_application_data|
[applicationManager.clearUpApplicationData](arkts-mdm-applicationmanager-clearupapplicationdata-f.md#clearUpApplicationData-1)
|���Ӧ�ò������������ݡ�|
|disallow_unmute_device|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����unmuteDevice������/�����豸ý�岥������������<br>feature����unmuteDevice����ѯ�Ƿ�����豸ý�岥������������|
|disabled_hdc_remote|
[restrictions.setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
<br>
[restrictions.getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1)
|feature����hdcRemote������/�����豸ͨ��hdc���������豸��������<br>feature����hdcRemote����ѯ�Ƿ�����豸ͨ��hdc���������豸��������|

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## BLOCK_LIST

```TypeScript
BLOCK_LIST = 0
```

����������

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## TRUST_LIST

```TypeScript
TRUST_LIST = 1
```

����������

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

