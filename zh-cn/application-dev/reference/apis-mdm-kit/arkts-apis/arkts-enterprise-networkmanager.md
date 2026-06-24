# @ohos.enterprise.networkManager

��ģ���ṩ�豸�������������������ѯ�豸IP��ַ��MAC��ַ��Ϣ�ȡ�

> **˵����**
>
> ��ģ��ӿڽ�����Stageģ����ʹ�á�
>
> ��ģ��ӿڽ����豸����Ӧ�ÿ��ţ��ҵ��ýӿ�ǰ�輤���豸����Ӧ�ã�������ο�[MDM Kit����ָ��](../../../../mdm/mdm-kit-guide.md)��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addApn](arkts-mdm-networkmanager-addapn-f.md#addApn-1) | ����APN��Access Point Name����������ƣ���<br/> |
| [addDomainFilterRule](arkts-mdm-networkmanager-adddomainfilterrule-f.md#addDomainFilterRule-1) | Ϊ�豸�����������˹���<br/><br/>API version 21��֮ǰ�汾����֧��IPv4����API version 22��ʼ��֧��IPv4��IPv6��<br/><br/>��API version 23��ʼ��֧��[LogType](arkts-mdm-networkmanager-logtype-e.md#LogType)��<br/><br/>������[Action](arkts-mdm-networkmanager-action-e.md#Action)ΪALLOW����󣬽���Ĭ������DENY���򣬲���ALLOW����֮�ڵ������������ݰ����ᱻ���������ء�<br/><br/>�豸��������������������˹���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; Ϊ����DNS���浼�����ع���ʧЧ������ϵͳ���������������������˹���������DNS���浼������ʧЧ������ϵͳ��������棬�ָ����ع��ܡ�<br/> |
| [addFirewallRule](arkts-mdm-networkmanager-addfirewallrule-f.md#addFirewallRule-1) | Ϊ�豸���ӷ���ǽ���˹���<br/><br/>API version 21��֮ǰ�汾����֧��IPv4����API version 22��ʼ��֧��IPv4��IPv6��<br/><br/>��API version 23��ʼ��֧��[LogType](arkts-mdm-networkmanager-logtype-e.md#LogType)��<br/><br/>������[Action](arkts-mdm-networkmanager-action-e.md#Action)ΪALLOW����󣬽���Ĭ������DENY���򣬲���ALLOW����֮�ڵ��������ݰ����ᱻ���������ء�<br/><br/>�豸������������շ���ǽ���˹���<br/> |
| <!--DelRow-->[addIptablesFilterRule](arkts-mdm-networkmanager-addiptablesfilterrule-f-sys.md#addIptablesFilterRule-1) | Ϊ�豸������������˹��򣬽�֧��IPv4��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[addIptablesFilterRule](arkts-mdm-networkmanager-addiptablesfilterrule-f-sys.md#addIptablesFilterRule-2) | Ϊ�豸������������˹��򣬽�֧��IPv4��ʹ��Promise�첽�ص���<br/> |
| [deleteApn](arkts-mdm-networkmanager-deleteapn-f.md#deleteApn-1) | ɾ��APN��<br/> |
| <!--DelRow-->[getAllNetworkInterfaces](arkts-mdm-networkmanager-getallnetworkinterfaces-f-sys.md#getAllNetworkInterfaces-1) | ��ȡ���м������������ӿڡ�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getAllNetworkInterfaces](arkts-mdm-networkmanager-getallnetworkinterfaces-f-sys.md#getAllNetworkInterfaces-2) | ��ȡ���м������������ӿڡ�ʹ��Promise�첽�ص���<br/> |
| [getAllNetworkInterfacesSync](arkts-mdm-networkmanager-getallnetworkinterfacessync-f.md#getAllNetworkInterfacesSync-1) | ��ȡ���м������������ӿڡ�<br/> |
| [getDomainFilterRules](arkts-mdm-networkmanager-getdomainfilterrules-f.md#getDomainFilterRules-1) | ��ѯ�豸�������˹���<br/><br/>API version 21��֮ǰ�汾����֧��IPv4����API version 22��ʼ��֧��IPv4��IPv6��<br/><br/>��API version 23��ʼ��֧��[LogType](arkts-mdm-networkmanager-logtype-e.md#LogType)��<br/> |
| [getFirewallRules](arkts-mdm-networkmanager-getfirewallrules-f.md#getFirewallRules-1) | ��ѯ�豸����ǽ���˹���<br/><br/>API version 21��֮ǰ�汾����֧��IPv4����API version 22��ʼ��֧��IPv4��IPv6��<br/><br/>��API version 23��ʼ��֧��[LogType](arkts-mdm-networkmanager-logtype-e.md#LogType)��<br/> |
| <!--DelRow-->[getGlobalProxy](arkts-mdm-networkmanager-getglobalproxy-f-sys.md#getGlobalProxy-1) | ��ȡ����ȫ�ִ�����ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getGlobalProxy](arkts-mdm-networkmanager-getglobalproxy-f-sys.md#getGlobalProxy-2) | ��ȡ����ȫ�ִ�����ʹ��Promise�첽�ص���<br/> |
| [getGlobalProxyForAccount](arkts-mdm-networkmanager-getglobalproxyforaccount-f.md#getGlobalProxyForAccount-1) | ��ȡָ���û��µ����������<br/> |
| [getGlobalProxySync](arkts-mdm-networkmanager-getglobalproxysync-f.md#getGlobalProxySync-1) | ��ȡ����ȫ�ִ�����<br/> |
| <!--DelRow-->[getIpAddress](arkts-mdm-networkmanager-getipaddress-f-sys.md#getIpAddress-1) | ��������ӿڻ�ȡ�豸IP��ַ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getIpAddress](arkts-mdm-networkmanager-getipaddress-f-sys.md#getIpAddress-2) | ��������ӿڻ�ȡ�豸IP��ַ��ʹ��Promise�첽�ص���<br/> |
| [getIpAddressSync](arkts-mdm-networkmanager-getipaddresssync-f.md#getIpAddressSync-1) | ��������ӿڻ�ȡ�豸IP��ַ��<br/> |
| <!--DelRow-->[getMac](arkts-mdm-networkmanager-getmac-f-sys.md#getMac-1) | ��������ӿڻ�ȡ�豸MAC��ַ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getMac](arkts-mdm-networkmanager-getmac-f-sys.md#getMac-2) | ��������ӿڻ�ȡ�豸MAC��ַ��ʹ��Promise�첽�ص���<br/> |
| [getMacSync](arkts-mdm-networkmanager-getmacsync-f.md#getMacSync-1) | ��������ӿڻ�ȡ�豸MAC��ַ��<br/> |
| <!--DelRow-->[isNetworkInterfaceDisabled](arkts-mdm-networkmanager-isnetworkinterfacedisabled-f-sys.md#isNetworkInterfaceDisabled-1) | ��ѯָ������ӿ��Ƿ񱻽��á�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[isNetworkInterfaceDisabled](arkts-mdm-networkmanager-isnetworkinterfacedisabled-f-sys.md#isNetworkInterfaceDisabled-2) | ��ѯָ������ӿ��Ƿ񱻽��á�ʹ��Promise�첽�ص���<br/> |
| [isNetworkInterfaceDisabledSync](arkts-mdm-networkmanager-isnetworkinterfacedisabledsync-f.md#isNetworkInterfaceDisabledSync-1) | ��ѯָ������ӿ��Ƿ񱻽��á�<br/> |
| <!--DelRow-->[listIptablesFilterRules](arkts-mdm-networkmanager-listiptablesfilterrules-f-sys.md#listIptablesFilterRules-1) | ��ȡ��������˹��򣬽�֧��IPv4��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[listIptablesFilterRules](arkts-mdm-networkmanager-listiptablesfilterrules-f-sys.md#listIptablesFilterRules-2) | ��ȡ��������˹��򣬽�֧��IPv4��ʹ��Promise�첽�ص���<br/> |
| [queryApn](arkts-mdm-networkmanager-queryapn-f.md#queryApn-1) | ��ѯ�����ض�APN��Ϣ��APN ID��<br/> |
| [queryApn](arkts-mdm-networkmanager-queryapn-f.md#queryApn-2) | ��ѯ�ض�APN��APN������Ϣ��<br/> |
| [removeDomainFilterRule](arkts-mdm-networkmanager-removedomainfilterrule-f.md#removeDomainFilterRule-1) | �Ƴ��豸�������˹���<br/><br/>API version 21��֮ǰ�汾����֧��IPv4����API version 22��ʼ��֧��IPv4��IPv6��<br/><br/>��API version 23��ʼ��֧��[LogType](arkts-mdm-networkmanager-logtype-e.md#LogType)��<br/><br/>�Ƴ���������������[Action](arkts-mdm-networkmanager-action-e.md#Action)ΪALLOW����󣬻Ὣ<br/>[addDomainFilterRule](arkts-mdm-networkmanager-adddomainfilterrule-f.md#addDomainFilterRule-1)���ӵ�Ĭ��DENY������ա�<br/> |
| [removeFirewallRule](arkts-mdm-networkmanager-removefirewallrule-f.md#removeFirewallRule-1) | �Ƴ��豸����ǽ���˹���<br/><br/>API version 21��֮ǰ�汾����֧��IPv4����API version 22��ʼ��֧��IPv4��IPv6��<br/><br/>��API version 23��ʼ��֧��[LogType](arkts-mdm-networkmanager-logtype-e.md#LogType)��<br/><br/>�Ƴ���������������[Action](arkts-mdm-networkmanager-action-e.md#Action)ΪALLOW����󣬻Ὣ[addFirewallRule](arkts-mdm-networkmanager-addfirewallrule-f.md#addFirewallRule-1)��<br/>�ӵ�Ĭ��DENY������ա�<br/> |
| <!--DelRow-->[removeIptablesFilterRule](arkts-mdm-networkmanager-removeiptablesfilterrule-f-sys.md#removeIptablesFilterRule-1) | �Ƴ���������˹��򣬽�֧��IPv4��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[removeIptablesFilterRule](arkts-mdm-networkmanager-removeiptablesfilterrule-f-sys.md#removeIptablesFilterRule-2) | �Ƴ���������˹��򣬽�֧��IPv4��ʹ��Promise�첽�ص���<br/> |
| [setEthernetConfig](arkts-mdm-networkmanager-setethernetconfig-f.md#setEthernetConfig-1) | �����ض���̫������ӿڵ�IP��ַ��<br/> |
| <!--DelRow-->[setGlobalProxy](arkts-mdm-networkmanager-setglobalproxy-f-sys.md#setGlobalProxy-1) | ��������ȫ�ִ�����ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[setGlobalProxy](arkts-mdm-networkmanager-setglobalproxy-f-sys.md#setGlobalProxy-2) | ��������ȫ�ִ�����ʹ��Promise�첽�ص���<br/> |
| [setGlobalProxyForAccount](arkts-mdm-networkmanager-setglobalproxyforaccount-f.md#setGlobalProxyForAccount-1) | ����ָ���û��µ����������<br/> |
| [setGlobalProxySync](arkts-mdm-networkmanager-setglobalproxysync-f.md#setGlobalProxySync-1) | ��������ȫ�ִ�����<br/> |
| <!--DelRow-->[setNetworkInterfaceDisabled](arkts-mdm-networkmanager-setnetworkinterfacedisabled-f-sys.md#setNetworkInterfaceDisabled-1) | ��ֹ�豸ʹ��ָ�����硣ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[setNetworkInterfaceDisabled](arkts-mdm-networkmanager-setnetworkinterfacedisabled-f-sys.md#setNetworkInterfaceDisabled-2) | ��ֹ�豸ʹ��ָ�����硣ʹ��Promise�첽�ص���<br/> |
| [setNetworkInterfaceDisabledSync](arkts-mdm-networkmanager-setnetworkinterfacedisabledsync-f.md#setNetworkInterfaceDisabledSync-1) | ��ֹ�豸ʹ��ָ������ӿڡ�<br/> |
| [setPreferredApn](arkts-mdm-networkmanager-setpreferredapn-f.md#setPreferredApn-1) | ������ѡAPN��<br/> |
| [turnOffMobileData](arkts-mdm-networkmanager-turnoffmobiledata-f.md#turnOffMobileData-1) | �ر��ƶ��������硣<br/> |
| [turnOnMobileData](arkts-mdm-networkmanager-turnonmobiledata-f.md#turnOnMobileData-1) | �����ƶ��������硣<br/> |
| [updateApn](arkts-mdm-networkmanager-updateapn-f.md#updateApn-1) | ����APN��<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[AddFilterRule](arkts-mdm-networkmanager-addfilterrule-i-sys.md) | ������������˹���<br/> |
| [DomainFilterRule](arkts-mdm-networkmanager-domainfilterrule-i.md) | �������˹���<br/><br/>API version 21��֮ǰ�汾����֧��IPv4����API version 22��ʼ��֧��IPv4��IPv6��<br/><br/>��API version 23��ʼ��֧��[LogType](arkts-mdm-networkmanager-logtype-e.md#LogType)��<br/> |
| [FirewallRule](arkts-mdm-networkmanager-firewallrule-i.md) | ����ǽ���˹���<br/><br/>API version 21��֮ǰ�汾����֧��IPv4����API version 22��ʼ��֧��IPv4��IPv6��<br/><br/>��API version 23��ʼ��֧��[LogType](arkts-mdm-networkmanager-logtype-e.md#LogType)��<br/> |
| [InterfaceConfig](arkts-mdm-networkmanager-interfaceconfig-i.md) | ��̫��������ӿ����á���֧��IPv4��<br/> |
| <!--DelRow-->[RemoveFilterRule](arkts-mdm-networkmanager-removefilterrule-i-sys.md) | �Ƴ���������˹���<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Action](arkts-mdm-networkmanager-action-e.md) | ���ݰ�����Ϊ��<br/> |
| <!--DelRow-->[AddMethod](arkts-mdm-networkmanager-addmethod-e-sys.md) | ���������������<br/> |
| [Direction](arkts-mdm-networkmanager-direction-e.md) | ��������<br/> |
| [IpSetMode](arkts-mdm-networkmanager-ipsetmode-e.md) | ��̫������ģʽ��<br/> |
| [LogType](arkts-mdm-networkmanager-logtype-e.md) | ��־���͡�<br/> |
| [Protocol](arkts-mdm-networkmanager-protocol-e.md) | ����Э�顣<br/> |

