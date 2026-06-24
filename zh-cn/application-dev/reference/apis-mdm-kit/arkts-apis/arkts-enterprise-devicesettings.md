# @ohos.enterprise.deviceSettings

��ģ���ṩ��ҵ�豸�����������������á���ȡ�豸Ϣ��ʱ��ȡ�

> **˵����**
>
> ��ģ��ӿڽ�����Stageģ����ʹ�á�
>
> ��ģ��ӿڽ����豸����Ӧ�ÿ��ţ��ҵ��ýӿ�ǰ�輤���豸����Ӧ�ã�������ο�[MDM Kit����ָ��](../../../../mdm/mdm-kit-guide.md)��

**起始版本：** 10

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addHiddenSettingsMenu](arkts-mdm-devicesettings-addhiddensettingsmenu-f.md#addHiddenSettingsMenu-1) | ��������������ǰ�û��µ������������б��������������������б����������ڵ�ǰ�û������ò˵��лᱻ���أ����غ󲻿��������õ������������������ͨ��ĳ�ַ�ʽ������������������Ҳ�޷��򿪡����ýӿں󼴿���Ч��������������Ӧ�á�<br/> |
| [getHiddenSettingsMenu](arkts-mdm-devicesettings-gethiddensettingsmenu-f.md#getHiddenSettingsMenu-1) | ��ȡ�����ڵ�ǰ�û��±����ص��������б���<br/> |
| <!--DelRow-->[getPowerPolicy](arkts-mdm-devicesettings-getpowerpolicy-f-sys.md#getPowerPolicy-1) | ��ȡ��Դ���ԡ�<br/> |
| <!--DelRow-->[getScreenOffTime](arkts-mdm-devicesettings-getscreenofftime-f-sys.md#getScreenOffTime-1) | ��ȡ�豸Ϣ��ʱ�䣬ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getScreenOffTime](arkts-mdm-devicesettings-getscreenofftime-f-sys.md#getScreenOffTime-2) | ��ȡ�豸Ϣ��ʱ�䣬ʹ��Promise�첽�ص���<br/> |
| [getSwitchStatus](arkts-mdm-devicesettings-getswitchstatus-f.md#getSwitchStatus-1) | ��ѯ���ص�״̬��<br/> |
| [getValue](arkts-mdm-devicesettings-getvalue-f.md#getValue-1) | ��ȡ�豸���ò��ԡ�<br/> |
| [getValueForAccount](arkts-mdm-devicesettings-getvalueforaccount-f.md#getValueForAccount-1) | ��ȡָ���û����豸���ò��ԡ��ýӿڿ��Ի�ȡָ���û�������Ӧ���е�ĳ�������������ȡ�û�100���豸���Ƶȡ�<br/> |
| <!--DelRow-->[installUserCertificate](arkts-mdm-devicesettings-installusercertificate-f-sys.md#installUserCertificate-1) | ��װ�û�֤�飬ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[installUserCertificate](arkts-mdm-devicesettings-installusercertificate-f-sys.md#installUserCertificate-2) | ��װ�û�֤�飬ʹ��Promise�첽�ص���<br/> |
| [removeHiddenSettingsMenu](arkts-mdm-devicesettings-removehiddensettingsmenu-f.md#removeHiddenSettingsMenu-1) | ��������ӵ�ǰ�û��µ������������б����Ƴ��������������б��е��������ڵ�ǰ�û������ò˵��лᱻ���أ����غ󲻿��������õ������������������ͨ��ĳ�ַ�ʽ������������������Ҳ�޷��򿪡����Ƴ���ʣ��������������б�Ϊ�գ����������ȫ<br/>����ʾ�����ýӿں󼴿���Ч��������������Ӧ�á�<br/> |
| [setHomeWallpaper](arkts-mdm-devicesettings-sethomewallpaper-f.md#setHomeWallpaper-1) | ���������ֽ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setPowerPolicy](arkts-mdm-devicesettings-setpowerpolicy-f-sys.md#setPowerPolicy-1) | ���õ�Դ���ԡ�<br/> |
| <!--DelRow-->[setScreenOffTime](arkts-mdm-devicesettings-setscreenofftime-f-sys.md#setScreenOffTime-1) | �����豸Ϣ��ʱ�䡣<br/> |
| [setSwitchStatus](arkts-mdm-devicesettings-setswitchstatus-f.md#setSwitchStatus-1) | ���ÿ��ص�״̬��֧������������������Wi-Fi��״̬Ϊ������رգ�������Ϻ��û������ֶ����ء�֧������������״̬Ϊǿ�ƿ�����������Ϻ��û��������ֶ����ء����Ѿ�ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)<br/>�ӿڽ�����ĳ�����أ���ͨ�����ӿ�����������ص�״̬���׳�������203����ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)<br/>�ӿڽ���ÿ��ؽ��ò��ԡ����豸�ж��MDMӦ��ʱ����MDMӦ�����ÿ���״̬�����ڳ�ͻ��������õĲ�����Ч������(�û����ֶ��������ر�)���ر�(�û����ֶ��������ر�)��ǿ�ƿ���(�û������ֶ��ر�)����״̬���������л���Ҳ�����ڳ�ͻ��<br/> |
| [setUnlockWallpaper](arkts-mdm-devicesettings-setunlockwallpaper-f.md#setUnlockWallpaper-1) | ����������ֽ��ʹ��Promise�첽�ص���<br/> |
| [setValue](arkts-mdm-devicesettings-setvalue-f.md#setValue-1) | �����豸���ԡ�<br/> |
| [setValueForAccount](arkts-mdm-devicesettings-setvalueforaccount-f.md#setValueForAccount-1) | ����ָ���û����豸���ò��ԡ��ýӿڿ�������ָ���û�������Ӧ���е�ĳ�����������������û�100���豸���Ƶȡ�<br/> |
| <!--DelRow-->[uninstallUserCertificate](arkts-mdm-devicesettings-uninstallusercertificate-f-sys.md#uninstallUserCertificate-1) | ж���û�֤�飬ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[uninstallUserCertificate](arkts-mdm-devicesettings-uninstallusercertificate-f-sys.md#uninstallUserCertificate-2) | ж���û�֤�飬ʹ��Promise�첽�ص���<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[CertBlob](arkts-mdm-devicesettings-certblob-i-sys.md) | ֤����Ϣ��<br/> |
| <!--DelRow-->[PowerPolicy](arkts-mdm-devicesettings-powerpolicy-i-sys.md) | ��Դ���ԡ�<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[PowerPolicyAction](arkts-mdm-devicesettings-powerpolicyaction-e-sys.md) | ִ�е�Դ���ԵĶ�����<br/> |
| <!--DelRow-->[PowerScene](arkts-mdm-devicesettings-powerscene-e-sys.md) | ִ�е�Դ���Եĳ�����<br/> |
| [SettingsItem](arkts-mdm-devicesettings-settingsitem-e.md) | ���õĲ������͡�<br/> |
| [SettingsMenu](arkts-mdm-devicesettings-settingsmenu-e.md) | �������б���<br/> |
| [SwitchKey](arkts-mdm-devicesettings-switchkey-e.md) | �������Ƶ�ö�١�<br/> |
| [SwitchStatus](arkts-mdm-devicesettings-switchstatus-e.md) | ����״̬��ö�١�<br/> |

