# @ohos.enterprise.wifiManager

��ģ���ṩ��ҵ�豸Wi-Fi����������������ѯWi-Fi����״̬�ȡ�

> **˵����**
>
> ��ģ��ӿڽ�����Stageģ����ʹ�á�
>
> ��ģ��ӿڽ����豸����Ӧ�ÿ��ţ��ҵ��ýӿ�ǰ�輤���豸����Ӧ�ã�������ο�[MDM Kit����ָ��](../../../../mdm/mdm-kit-guide.md)��
>
> ȫ��ͨ�������������restrictionsͳһ�ṩ����Ҫȫ�ֽ���Wi-Fi����ο�
> [@ohos.enterprise.restrictions����������ԣ�](arkts-enterprise-restrictions.md#restrictions)��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedWifiList](arkts-mdm-wifimanager-addallowedwifilist-f.md#addAllowedWifiList-1) | ����Wi-Fi������������������������ǰ�豸���������Ӹ������µ�Wi-Fi��<br/><br/>��������£����ñ��ӿڻᱨ���Գ�ͻ��<br/><br/>1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸Wi-Fi������ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)���Wi-Fi���ú󣬿ɽ����ͻ��<br/>2. �Ѿ�ͨ��[addDisallowedWifiList](arkts-mdm-wifimanager-adddisallowedwifilist-f.md#addDisallowedWifiList-1)�ӿ�������Wi-Fi����������ͨ��[removeDisallowedWifiList](arkts-mdm-wifimanager-removedisallowedwifilist-f.md#removeDisallowedWifiList-1)�Ƴ�Wi-Fi���������󣬿ɽ����ͻ��<br/> |
| [addDisallowedWifiList](arkts-mdm-wifimanager-adddisallowedwifilist-f.md#addDisallowedWifiList-1) | ����Wi-Fi�������������ӽ���������ǰ�豸���������Ӹ������µ�Wi-Fi��<br/><br/>��������£����ñ��ӿڻᱨ���Գ�ͻ��<br/><br/>1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸Wi-Fi������ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)���Wi-Fi���ú󣬿ɽ����ͻ��<br/>2. �Ѿ�ͨ��[addAllowedWifiList](arkts-mdm-wifimanager-addallowedwifilist-f.md#addAllowedWifiList-1)�ӿ�������Wi-Fi����������ͨ��[removeAllowedWifiList](arkts-mdm-wifimanager-removeallowedwifilist-f.md#removeAllowedWifiList-1)�Ƴ�Wi-Fi���������󣬿ɽ����ͻ��<br/> |
| [getAllowedWifiList](arkts-mdm-wifimanager-getallowedwifilist-f.md#getAllowedWifiList-1) | ��ȡWi-Fi����������<br/> |
| [getDisallowedWifiList](arkts-mdm-wifimanager-getdisallowedwifilist-f.md#getDisallowedWifiList-1) | ��ȡWi-Fi����������<br/> |
| <!--DelRow-->[isWifiActive](arkts-mdm-wifimanager-iswifiactive-f-sys.md#isWifiActive-1) | ��ѯ��ǰ�豸��Wi-Fi����״̬��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[isWifiActive](arkts-mdm-wifimanager-iswifiactive-f-sys.md#isWifiActive-2) | ��ѯ��ǰ�豸��Wi-Fi����״̬��ʹ��Promise�첽�ص���<br/> |
| [isWifiActiveSync](arkts-mdm-wifimanager-iswifiactivesync-f.md#isWifiActiveSync-1) | ��ѯ��ǰ�豸Wi-Fi����״̬��<br/> |
| <!--DelRow-->[isWifiDisabled](arkts-mdm-wifimanager-iswifidisabled-f-sys.md#isWifiDisabled-1) | ��ѯ��ǰ�豸Wi-Fi�Ƿ񱻽��á�<br/> |
| [removeAllowedWifiList](arkts-mdm-wifimanager-removeallowedwifilist-f.md#removeAllowedWifiList-1) | �Ƴ�Wi-Fi�������������Ƴ����������еĲ���Wi-Fi����ǰ�豸����������ʣ��δ�Ƴ���Wi-Fi�����Ƴ����������е�����Wi-Fi����ǰ�豸������������Wi-Fi��<br/> |
| [removeDisallowedWifiList](arkts-mdm-wifimanager-removedisallowedwifilist-f.md#removeDisallowedWifiList-1) | �Ƴ�Wi-Fi�������������Ƴ����������еĲ���Wi-Fi����ǰ�豸���������ӽ���������ʣ���Wi-Fi�����Ƴ����������е�����Wi-Fi����ǰ�豸�������������Wi-Fi��<br/> |
| <!--DelRow-->[setWifiDisabled](arkts-mdm-wifimanager-setwifidisabled-f-sys.md#setWifiDisabled-1) | ���ý���Wi-Fi���ԡ�<br/> |
| <!--DelRow-->[setWifiProfile](arkts-mdm-wifimanager-setwifiprofile-f-sys.md#setWifiProfile-1) | Ϊ��ǰ�豸����Wi-Fi��ʹ���ӵ�ָ�����硣ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[setWifiProfile](arkts-mdm-wifimanager-setwifiprofile-f-sys.md#setWifiProfile-2) | Ϊ��ǰ�豸����Wi-Fi��ʹ���ӵ�ָ�����硣ʹ��Promise�첽�ص���<br/> |
| [setWifiProfileSync](arkts-mdm-wifimanager-setwifiprofilesync-f.md#setWifiProfileSync-1) | Ϊ��ǰ�豸����Wi-Fi�����ӵ�ָ�����硣<br/> |
| [turnOffWifi](arkts-mdm-wifimanager-turnoffwifi-f.md#turnOffWifi-1) | �ر�Wi-Fi���ء�<br/><br/>��������£�ͨ�����ӿڹر�Wi-Fi���أ�����ʾ"ϵͳ���ܱ�����"��<br/><br/>?�Ѿ�ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)<br/>�ӿڽ�����Wi-Fi����ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)<br/>�ӿ�����Wi-Fi�����"ϵͳ���ܱ�����"������<br/> |
| [turnOnWifi](arkts-mdm-wifimanager-turnonwifi-f.md#turnOnWifi-1) | ��Wi-Fi���ء�<br/><br/>��������£�ͨ�����ӿڴ�Wi-Fi���أ����ʧ�ܲ���ʾ"ϵͳ���ܱ�����"��<br/><br/>?�Ѿ�ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)<br/>�ӿڽ�����Wi-Fi����ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)<br/>�ӿ�����Wi-Fi�����"ϵͳ���ܱ�����"������<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [IpProfile](arkts-mdm-wifimanager-ipprofile-i.md) | IP������Ϣ��<br/> |
| [WifiAccessInfo](arkts-mdm-wifimanager-wifiaccessinfo-i.md) | Wi-Fi��SSID��BSSID��Ϣ��<br/> |
| [WifiEapProfile](arkts-mdm-wifimanager-wifieapprofile-i.md) | ����չ������֤Э��������Ϣ��<br/> |
| [WifiProfile](arkts-mdm-wifimanager-wifiprofile-i.md) | Wi-Fi������Ϣ��<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EapMethod](arkts-mdm-wifimanager-eapmethod-e.md) | ��ʾEAP��֤��ʽ��ö�١�<br/><br/>&gt; **˵��**��<br/>&gt;<br/>&gt; ��ǰ��֧��ʹ��EAP_PEAP��EAP_TLS������֤��ʽ�������ݲ�֧�֡�<br/> |
| [IpType](arkts-mdm-wifimanager-iptype-e.md) | ��ʾIP���͵�ö�١�<br/> |
| [Phase2Method](arkts-mdm-wifimanager-phase2method-e.md) | ��ʾ�ڶ��׶���֤��ʽ��ö�١�<br/> |
| [WifiSecurityType](arkts-mdm-wifimanager-wifisecuritytype-e.md) | ��ʾ�������͵�ö�١�<br/> |

