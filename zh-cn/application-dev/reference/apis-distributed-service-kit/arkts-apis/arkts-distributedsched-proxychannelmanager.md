# @ohos.distributedsched.proxyChannelManager

�����߾߱���פ������������Ϊ���豸ͨ���ṩ�ȶ��ɿ��ĵײ�ͨ������ģ����������߽��̿�����֧���ֻ��봩���豸���Ч�����ݻ�ͨ��
��Ϊ�û��ṩ�޷���豸�������顣ʹ�ó������ֻ���APP���ֱ���APPЭͬʱ�����ֻ�APP����ǰ̨��ʹ�ã��ֻ�Ӧ
�õ�������Ϣ����֪ͨ��������ͨ������ģ�鷢�͸��ֱ��ࡣģ����Ĺ��ܰ���������ͨ������������·�ɹ����� Ӧ��״̬��֪�ͻ��ѡ�
��·״̬������

- ����ͨ��������ͨ������ BR Э�齨���ֻ��봩���豸��˫������ͨ����֧�ֵ�����ͨ�� ID ��Χ��[1,2147483647] ��
- ����·�ɹ��������� UUID ����ʶ����ƣ���׼ת�������豸���ݡ�
- Ӧ��״̬��֪�ͻ��ѣ�����ͨ��ʹ�ܺ��յ������豸���͵����ݺ󣬶�̬�����ͻ����ֻ��˶�ӦӦ�ý��̡�
- ȫ��·״̬��أ�ͨ���ص�ʵʱ��֪ͨ������״̬��

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md#closeProxyChannel-1) | �ر��Ѵ򿪵Ĵ���ͨ����<br/> |
| [off](arkts-distributedservice-proxychannelmanager-off-f.md#off-1) | ȡ���������ݽ����¼���ֹͣ�������ݡ�<br/> |
| [off](arkts-distributedservice-proxychannelmanager-off-f.md#off-2) | ȡ������ͨ��״̬�¼���<br/> |
| [on](arkts-distributedservice-proxychannelmanager-on-f.md#on-1) | �������ݽ����¼���ʹ���첽�ص���<br/> |
| [on](arkts-distributedservice-proxychannelmanager-on-f.md#on-2) | ����ͨ��״̬�¼���ʹ��callback�����첽�ص���<br/> |
| [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md#openProxyChannel-1) | �򿪴���ͨ����ʹ��Promise�첽�ص����ؽ����<br/> |
| [sendData](arkts-distributedservice-proxychannelmanager-senddata-f.md#sendData-1) | ��Զ˷������ݣ�ʹ��Promise�첽�ص���<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChannelInfo](arkts-distributedservice-proxychannelmanager-channelinfo-i.md) | �򿪴���ͨ����������Σ������Զ��豸��MAC��ַ�ͼ��������UUID��<br/> |
| [ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md) | ������ͨ��״̬�仯ʱ�����ڱ�ʾ����ͨ��������״̬��<br/> |
| [DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md) | ��Ž��յ�������Ϣ������ͨ��Id�����ݡ�<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md) | ͨ��״̬�����仯ʱ������ͨ���ϱ���ͨ������״̬��<br/> |
| [LinkType](arkts-distributedservice-proxychannelmanager-linktype-e.md) | ��·���͡�<br/> |

