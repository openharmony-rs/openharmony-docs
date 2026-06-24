# @ohos.enterprise.telephonyManager

��ģ���ṩͨ������������

> **˵��**��
>
> ��ģ��ӿڽ�������Stageģ�͡�
>
> ��ģ��ӿڽ����豸����Ӧ�ÿ��ţ����ýӿ�ǰ�輤���Ӧ�ã�������ο�[MDM Kit����ָ��](../../../../mdm/mdm-kit-guide.md)��
>
> ȫ��ͨ�������������restrictions�ṩ����Ҫȫ�ֽ���ͨ������ο�
> [@ohos.enterprise.restrictions ����������ԣ�](arkts-enterprise-restrictions.md#restrictions)��

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [activeSim](arkts-mdm-telephonymanager-activesim-f.md#activeSim-1) | ����ָ�����۵�SIM�����豸�Ѿ�����SIM�����ǲ�δ���õĳ���������ͨ���ýӿ�����SIM���������û��ֶ����á�SIM�����ú����ʹ�ø�SIM������ͨ�š��ýӿ���Ҫ����SIM�����رշ���ģʽ���ܳɹ����á�<br/> |
| [addIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-addincomingcallpolicynumbers-f.md#addIncomingCallPolicyNumbers-1) | ����ͨ���������������������������������������������붼���Ժ��룬���Ӻ�������ڵĺ����������ֹ���롣<br/><br/>��������£�ͨ�����ӿ�����ͨ�����������������������ᱨ���Գ�ͻ��<br/><br/>1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸ͨ����������ͨ�����ӿ�����ͨ������Ľ��û���������������203�����롣ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ�������豸ͨ�������󣬿ɽ����ͻ��<br/>2. �Ѿ�ͨ�����ӿ�������ͨ������Ľ�����������ͨ�����ӿ�����ͨ��������������������9200010�����롣ͨ��[removeIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-removeincomingcallpolicynumbers-f.md#removeIncomingCallPolicyNumbers-1)�ӿڽ�֮ǰ���õ�ͨ��������������Ƴ��󣬿ɽ����ͻ��<br/>3. �Ѿ�ͨ�����ӿ�������ͨ�������������������ͨ�����ӿ�����ͨ�������������������9200010�����롣ͨ��[removeIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-removeincomingcallpolicynumbers-f.md#removeIncomingCallPolicyNumbers-1)�ӿڽ�֮ǰ���õ�ͨ���������������Ƴ��󣬿ɽ����ͻ��<br/> |
| [addOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-addoutgoingcallpolicynumbers-f.md#addOutgoingCallPolicyNumbers-1) | ����ͨ��������������������������������������������붼���Ժ��������Ӻ�ֻ�������ڵĺ����������ֹ������<br/><br/>��������£�ͨ�����ӿ�����ͨ������������������������ᱨ���Գ�ͻ��<br/><br/>1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸ͨ����������ͨ�����ӿ�����ͨ�������Ľ��û���������������203�����롣ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ�������豸ͨ�������󣬿ɽ����ͻ��<br/>2. �Ѿ�ͨ�����ӿ�������ͨ�������Ľ�����������ͨ�����ӿ�����ͨ��������������������9200010�����롣ͨ��[removeOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-removeoutgoingcallpolicynumbers-f.md#removeOutgoingCallPolicyNumbers-1)�ӿڽ�֮ǰ���õ�ͨ���������������Ƴ��󣬿ɽ����ͻ��<br/>3. �Ѿ�ͨ�����ӿ�������ͨ��������������������ͨ�����ӿ�����ͨ��������������������9200010�����롣ͨ��[removeOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-removeoutgoingcallpolicynumbers-f.md#removeOutgoingCallPolicyNumbers-1)�ӿڽ�֮ǰ���õ�ͨ���������������Ƴ��󣬿ɽ����ͻ��<br/> |
| [addReceiveSmsPolicyNumbers](arkts-mdm-telephonymanager-addreceivesmspolicynumbers-f.md#addReceiveSmsPolicyNumbers-1) | ���ӽ��ն��ŵ��������������<br/> |
| [addSendSmsPolicyNumbers](arkts-mdm-telephonymanager-addsendsmspolicynumbers-f.md#addSendSmsPolicyNumbers-1) | ���ӷ��Ͷ��ŵ��������������<br/> |
| [deactiveSim](arkts-mdm-telephonymanager-deactivesim-f.md#deactiveSim-1) | ͣ��ָ������SIM����ͣ�ø�SIM�����޷�ʹ�øÿ��۵�SIM���Ӵ�绰���շ����ţ��������ýӿ���Ҫ����SIM�����رշ���ģʽ���ܳɹ����á�<br/> |
| [getDefaultData](arkts-mdm-telephonymanager-getdefaultdata-f.md#getDefaultData-1) | ��ȡ�豸��ǰĬ��ʹ�õ���������������ID��δ�忨���߷���ģʽ�»��ȡ��һ��ʹ�õ���������������ID���豸��δ���ù�Ĭ�����������������£��ýӿڷ���Ĭ�Ͽ���1��ֵΪ0��<br/> |
| [getIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-getincomingcallpolicynumbers-f.md#getIncomingCallPolicyNumbers-1) | ��ȡͨ����������������������<br/> |
| [getOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-getoutgoingcallpolicynumbers-f.md#getOutgoingCallPolicyNumbers-1) | ��ȡͨ�����������������������<br/> |
| [getReceiveSmsPolicyNumbers](arkts-mdm-telephonymanager-getreceivesmspolicynumbers-f.md#getReceiveSmsPolicyNumbers-1) | ��ѯ���ն����������������<br/> |
| [getSendSmsPolicyNumbers](arkts-mdm-telephonymanager-getsendsmspolicynumbers-f.md#getSendSmsPolicyNumbers-1) | ��ѯ���Ͷ��ŵ��������������<br/> |
| [hangupCalling](arkts-mdm-telephonymanager-hangupcalling-f.md#hangupCalling-1) | �Ҷϵ�ǰͨ������֧����Ӫ��ͨ���������������ȡ�<br/> |
| [isSimDisabled](arkts-mdm-telephonymanager-issimdisabled-f.md#isSimDisabled-1) | ��ѯָ�������Ƿ���á�<br/> |
| [removeIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-removeincomingcallpolicynumbers-f.md#removeIncomingCallPolicyNumbers-1) | �Ƴ�ͨ�������������������������ڸ�������δ����ʱ�����Ƴ�������Ƴ�ʧ�ܡ�<br/><br/>��������£�ͨ�����ӿ��Ƴ�ͨ�����������������������ᱨ���Գ�ͻ��<br/><br/>1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸ͨ����������ͨ�����ӿ��Ƴ�ͨ������Ľ��û���������������203�����롣ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ�������豸ͨ�������󣬿ɽ����ͻ��<br/> |
| [removeOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-removeoutgoingcallpolicynumbers-f.md#removeOutgoingCallPolicyNumbers-1) | �Ƴ�ͨ��������������������������ڸ�������δ����ʱ�����Ƴ�������Ƴ�ʧ�ܡ�<br/><br/>��������£�ͨ�����ӿ��Ƴ�ͨ������������������������ᱨ���Գ�ͻ��<br/><br/>�Ѿ�ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)<br/>�ӿڽ������豸ͨ����������ͨ�����ӿ��Ƴ�ͨ�������Ľ��û���������������203�����롣ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)<br/>�ӿڽ�������豸ͨ�������󣬿ɽ����ͻ��<br/> |
| [removeReceiveSmsPolicyNumbers](arkts-mdm-telephonymanager-removereceivesmspolicynumbers-f.md#removeReceiveSmsPolicyNumbers-1) | �Ƴ����ն��ŵ��������������<br/> |
| [removeSendSmsPolicyNumbers](arkts-mdm-telephonymanager-removesendsmspolicynumbers-f.md#removeSendSmsPolicyNumbers-1) | �Ƴ����Ͷ����������������<br/> |
| [setDefaultData](arkts-mdm-telephonymanager-setdefaultdata-f.md#setDefaultData-1) | ����ָ�����۵�SIM��ΪĬ���������������豸��ʹ��ָ�����۵�SIM�������������ýӿ���Ҫ����SIM�����رշ���ģʽ���ܳɹ����á�<br/> |
| [setSimDisabled](arkts-mdm-telephonymanager-setsimdisabled-f.md#setSimDisabled-1) | ����ָ�����۵�SIM����<br/> |
| [setSimEnabled](arkts-mdm-telephonymanager-setsimenabled-f.md#setSimEnabled-1) | ���ָ�����۵�SIM�����á�ʹ��setSimDisabled����SIM��������setSimEnabled����SIM������Ҫ������-�ƶ�����-SIM�����������ֶ���SIM�����ء�<br/> |

