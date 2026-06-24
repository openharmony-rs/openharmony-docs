# @ohos.enterprise.restrictions

��ģ���ṩ����ͨ���������������������ȫ�ֽ��úͽ������������HDC��USB��Wi-Fi�����ԡ�

> **˵��**��
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
| [addDisallowedListForAccount](arkts-mdm-restrictions-adddisallowedlistforaccount-f.md#addDisallowedListForAccount-1) | Ϊָ���û����ӽ�ֹʹ��ĳ���Ե�Ӧ��������ָ���û��£����ӵ������е�Ӧ�ò�����ʹ��ָ��������������<br/> |
| <!--DelRow-->[disableMicrophone](arkts-mdm-restrictions-disablemicrophone-f-sys.md#disableMicrophone-1) | ʹ�豸���û�������˷硣<br/> |
| [getDisallowedListForAccount](arkts-mdm-restrictions-getdisallowedlistforaccount-f.md#getDisallowedListForAccount-1) | ��ȡָ���û���ֹʹ��ĳ���Ե�Ӧ��������<br/> |
| [getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-1) | ��ѯĳ�����Ƿ񱻽��á�<br/> |
| [getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getDisallowedPolicy-2) | ��ѯָ���豸�����Ƿ񱻽��á�<br/> |
| [getDisallowedPolicyForAccount](arkts-mdm-restrictions-getdisallowedpolicyforaccount-f.md#getDisallowedPolicyForAccount-1) | ��ȡָ���û���ĳ����״̬��<br/> |
| [getDisallowedPolicyForAccount](arkts-mdm-restrictions-getdisallowedpolicyforaccount-f.md#getDisallowedPolicyForAccount-2) | ��ȡָ���û���ĳ����״̬��<br/> |
| [getUserRestricted](arkts-mdm-restrictions-getuserrestricted-f.md#getUserRestricted-1) | ��ȡ������Ľ���״̬��<br/> |
| [getUserRestrictedForAccount](arkts-mdm-restrictions-getuserrestrictedforaccount-f.md#getUserRestrictedForAccount-1) | ��ȡָ���û�������Ľ���״̬��<br/> |
| <!--DelRow-->[isFingerprintAuthDisabled](arkts-mdm-restrictions-isfingerprintauthdisabled-f-sys.md#isFingerprintAuthDisabled-1) | ��ѯָ����֤�Ƿ񱻽��á�<br/> |
| <!--DelRow-->[isHdcDisabled](arkts-mdm-restrictions-ishdcdisabled-f-sys.md#isHdcDisabled-1) | ��ѯHDC�Ƿ񱻽��á�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[isHdcDisabled](arkts-mdm-restrictions-ishdcdisabled-f-sys.md#isHdcDisabled-2) | ��ѯHDC�Ƿ񱻽��á�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[isMicrophoneDisabled](arkts-mdm-restrictions-ismicrophonedisabled-f-sys.md#isMicrophoneDisabled-1) | ��ѯ��˷��Ƿ񱻽��á�<br/> |
| <!--DelRow-->[isPrinterDisabled](arkts-mdm-restrictions-isprinterdisabled-f-sys.md#isPrinterDisabled-1) | ��ѯ�豸��ӡ�����Ƿ񱻽��á�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[isPrinterDisabled](arkts-mdm-restrictions-isprinterdisabled-f-sys.md#isPrinterDisabled-2) | ��ѯ�豸��ӡ�����Ƿ񱻽��á�ʹ��Promise�첽�ص���<br/> |
| [removeDisallowedListForAccount](arkts-mdm-restrictions-removedisallowedlistforaccount-f.md#removeDisallowedListForAccount-1) | Ϊָ���û��Ƴ���ֹʹ��ĳ���Ե�Ӧ��������<br/> |
| [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1) | ���ý���/����ĳ���ԡ�<br/> |
| [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-2) | ���ý���/����ָ���豸���ԣ����ú�����豸�����޷���ʹ�á�<br/> |
| [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-1) | ���ý���/����ָ���û���ĳ���ԡ�<br/> |
| [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-2) | ���ý���/����ָ���û���ĳ���ԡ�<br/> |
| <!--DelRow-->[setFingerprintAuthDisabled](arkts-mdm-restrictions-setfingerprintauthdisabled-f-sys.md#setFingerprintAuthDisabled-1) | ���û�����ָ����֤��<br/> |
| <!--DelRow-->[setHdcDisabled](arkts-mdm-restrictions-sethdcdisabled-f-sys.md#setHdcDisabled-1) | ʹ�豸���û�����[HDC](../../../../../device-dev/subsystems/subsys-toolchain-hdc-guide.md)��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[setHdcDisabled](arkts-mdm-restrictions-sethdcdisabled-f-sys.md#setHdcDisabled-2) | ʹ�豸���û�����HDC��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setPrinterDisabled](arkts-mdm-restrictions-setprinterdisabled-f-sys.md#setPrinterDisabled-1) | ʹ�豸���û����ô�ӡ������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[setPrinterDisabled](arkts-mdm-restrictions-setprinterdisabled-f-sys.md#setPrinterDisabled-2) | ʹ�豸���û����ô�ӡ������ʹ��Promise�첽�ص���<br/> |
| [setUserRestriction](arkts-mdm-restrictions-setuserrestriction-f.md#setUserRestriction-1) | �����û���Ϊ�����ƹ���<br/> |
| [setUserRestrictionForAccount](arkts-mdm-restrictions-setuserrestrictionforaccount-f.md#setUserRestrictionForAccount-1) | ����ָ���û���Ϊ�����ƹ���<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FeatureForAccount](arkts-mdm-restrictions-featureforaccount-e.md) | ��Ϊָ���û����ý���/���õ����Ե�ö�١�<br/> |
| [FeatureForDevice](arkts-mdm-restrictions-featurefordevice-e.md) | �豸����ö�١�<br/> |

