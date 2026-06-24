# @ohos.enterprise.bluetoothManager

��ģ���ṩ�豸�����������������������úͲ�ѯ������Ϣ�ȡ�

> **˵����**
>
> ��ģ��ӿڽ�����Stageģ����ʹ�á�
>
> ��ģ��ӿڽ����豸����Ӧ�ÿ��ţ��ҵ��ýӿ�ǰ�輤���豸����Ӧ�ã�������ο�[MDM Kit����ָ��](../../../../mdm/mdm-kit-guide.md)��
>
> ȫ��ͨ�������������restrictionsͳһ�ṩ����Ҫȫ�ֽ�����������ο�
> [@ohos.enterprise.restrictions ����������ԣ�](arkts-enterprise-restrictions.md#restrictions)��

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-addallowedbluetoothdevices-f.md#addAllowedBluetoothDevices-1) | ���������豸�������������������豸����������ǰ�豸���������Ӹ������µ������豸����API version 22��ʼ�������е�MAC��ַ�����������MAC�淶�����磺00:1A:2B:3C:4D:5E��������ʱ���Ƴ����Ϸ���MAC<br/>��ַ�������ӺϷ���MAC��ַ��<br/><br/>��������£�ͨ�����ӿ����������豸�����������ᱨ���Գ�ͻ��<br/><br/>1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ�����������ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿ����������󣬿ɽ����ͻ��<br/>2. �Ѿ�ͨ��[addDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-adddisallowedbluetoothdevices-f.md#addDisallowedBluetoothDevices-1)�ӿ������������豸����������ͨ��[removeDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-removedisallowedbluetoothdevices-f.md#removeDisallowedBluetoothDevices-1)�Ƴ������豸���������󣬿ɽ����ͻ��<br/> |
| [addDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-adddisallowedbluetoothdevices-f.md#addDisallowedBluetoothDevices-1) | ���������豸�������������ӽ���������ǰ�豸���������Ӹ������µ������豸����API version 22��ʼ�������е�MAC��ַ�����������MAC�淶�����磺00:1A:2B:3C:4D:5E��������ʱ���Ƴ����Ϸ���MAC��ַ����<br/>���ӺϷ���MAC��ַ��<br/><br/>��������£�ͨ�����ӿ����������豸�����������ᱨ���Գ�ͻ��<br/><br/>1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ�����������ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿ����������󣬿ɽ����ͻ��<br/>2. �Ѿ�ͨ��[addAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-addallowedbluetoothdevices-f.md#addAllowedBluetoothDevices-1)�ӿ������������豸����������ͨ��[removeAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-removeallowedbluetoothdevices-f.md#removeAllowedBluetoothDevices-1)�Ƴ������豸���������󣬿ɽ����ͻ��<br/> |
| [addDisallowedBluetoothProtocols](arkts-mdm-bluetoothmanager-adddisallowedbluetoothprotocols-f.md#addDisallowedBluetoothProtocols-1) | ��������Э��������������Ӻ�ָ���û����޷�ʹ�øý��������е�����Э���������豸�ⷢ�ļ���ͨ���ýӿڽ���GATT��SPPЭ�飬��ϵͳ�����ϵͳӦ�ò���Ч��������SPPЭ��ʱ����ͬʱ���ý��պͷ��͹��ܡ�<br/> |
| [addDisallowedBluetoothProtocols](arkts-mdm-bluetoothmanager-adddisallowedbluetoothprotocols-f.md#addDisallowedBluetoothProtocols-2) | ��������Э�����������������Ӻ�ָ���û����޷�����ָ���Ĵ������ʹ�øý��������е�����Э�顣<br/><br/>&gt; **˵����**<br/>&gt;<br/> |
| [getAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-getallowedbluetoothdevices-f.md#getAllowedBluetoothDevices-1) | ��ȡ�����豸����������<br/> |
| [getBluetoothInfo](arkts-mdm-bluetoothmanager-getbluetoothinfo-f.md#getBluetoothInfo-1) | ��ѯ�豸������Ϣ��<br/> |
| [getDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-getdisallowedbluetoothdevices-f.md#getDisallowedBluetoothDevices-1) | ��ȡ�����豸����������<br/> |
| [getDisallowedBluetoothProtocols](arkts-mdm-bluetoothmanager-getdisallowedbluetoothprotocols-f.md#getDisallowedBluetoothProtocols-1) | ��ȡָ���û�������Э�����������<br/> |
| [getDisallowedBluetoothProtocols](arkts-mdm-bluetoothmanager-getdisallowedbluetoothprotocols-f.md#getDisallowedBluetoothProtocols-2) | ��ȡָ���û�ָ������������ѽ��õ�����Э���б���<br/><br/>&gt; **˵����**<br/>&gt;<br/> |
| <!--DelRow-->[isBluetoothDisabled](arkts-mdm-bluetoothmanager-isbluetoothdisabled-f-sys.md#isBluetoothDisabled-1) | ��ѯ�����Ƿ񱻽��á�<br/> |
| [removeAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-removeallowedbluetoothdevices-f.md#removeAllowedBluetoothDevices-1) | �Ƴ������豸����������<br/> |
| [removeDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-removedisallowedbluetoothdevices-f.md#removeDisallowedBluetoothDevices-1) | �Ƴ������豸�������������Ƴ����������еĲ��������豸����ǰ�豸���������ӽ���������ʣ��������豸�����Ƴ����������е����������豸����ǰ�豸������������������豸��<br/> |
| [removeDisallowedBluetoothProtocols](arkts-mdm-bluetoothmanager-removedisallowedbluetoothprotocols-f.md#removeDisallowedBluetoothProtocols-1) | �Ƴ�����Э��������������Ƴ�����������ĳ���û��Ĳ�������Э�飬����û�����ʹ�ý���������ʣ�������Э���������豸�ⷢ�ļ������Ƴ�����������ĳ���û�����������Э�飬����û�����ʹ����������Э���������豸�ⷢ�ļ������Ƴ����������в���<br/>�ڵ�����Э�飬�ӿڿɵ��óɹ����������Ƴ����������в����ڵ�����Э�顣<br/> |
| [removeDisallowedBluetoothProtocols](arkts-mdm-bluetoothmanager-removedisallowedbluetoothprotocols-f.md#removeDisallowedBluetoothProtocols-2) | �ӽ����������Ƴ�����Э�顣�Ƴ���ָ���û��������ܸô�����Ե����ƣ���������ʹ����Щ����Э�顣<br/><br/>&gt; **˵����**<br/>&gt;<br/> |
| <!--DelRow-->[setBluetoothDisabled](arkts-mdm-bluetoothmanager-setbluetoothdisabled-f-sys.md#setBluetoothDisabled-1) | ���ý����������ԡ�<br/> |
| [turnOffBluetooth](arkts-mdm-bluetoothmanager-turnoffbluetooth-f.md#turnOffBluetooth-1) | �ر������������رպ��û������ֶ��򿪡�<br/> |
| [turnOnBluetooth](arkts-mdm-bluetoothmanager-turnonbluetooth-f.md#turnOnBluetooth-1) | ���������������������û������ֶ��رա�<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BluetoothInfo](arkts-mdm-bluetoothmanager-bluetoothinfo-i.md) | �豸��������Ϣ��<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Protocol](arkts-mdm-bluetoothmanager-protocol-e.md) | ����Э�����͡�<br/> |
| [TransferPolicy](arkts-mdm-bluetoothmanager-transferpolicy-e.md) | ������ԡ�<br/> |

