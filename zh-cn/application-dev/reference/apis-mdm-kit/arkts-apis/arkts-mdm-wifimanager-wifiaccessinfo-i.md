# WifiAccessInfo

Wi-Fi��SSID��BSSID��Ϣ��

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## bssid

```TypeScript
bssid?: string
```

Wi-Fi�ȵ��MAC��ַ�����磺00:11:22:33:44:55����ȡ��ʽ���£�������Ӧ��-���ϵͳѡ��-���������ѡ��-����WLAN��ϸ��־��¼���أ�Ȼ���������Ӧ���е�WLAN�б����鿴��ʾ��MAC��ַ����һ��Wi-
Fi��Ӧ���MAC��ַ������������MAC��ַ��

��Ϊ[addDisallowedWifiList](arkts-mdm-wifimanager-adddisallowedwifilist-f.md#addDisallowedWifiList-1)��
[removeDisallowedWifiList](arkts-mdm-wifimanager-removedisallowedwifilist-f.md#removeDisallowedWifiList-1)�ӿڵ����ʱ�������Կ�ѡ��Ĭ��ֵΪ���ַ�����

��Ϊ[addAllowedWifiList](arkts-mdm-wifimanager-addallowedwifilist-f.md#addAllowedWifiList-1)��
[removeAllowedWifiList](arkts-mdm-wifimanager-removeallowedwifilist-f.md#removeAllowedWifiList-1)�ӿ����ʱ����API version 21��ʼ�������Կ�ѡ��Ĭ��ֵΪ���ַ�����API
version 20��֮ǰ�İ汾�������Ա��

**类型：** string

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ssid

```TypeScript
ssid: string
```

Wi-Fi�ȵ����ƣ������ʽΪUTF-8����󳤶�Ϊ32�ֽڣ������ַ�ռ3λ��Ӣ���ַ�ռ1λ����

**类型：** string

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

