# FirewallRule

����ǽ���˹���

API version 21��֮ǰ�汾����֧��IPv4����API version 22��ʼ��֧��IPv4��IPv6��

��API version 23��ʼ��֧��[LogType](arkts-mdm-networkmanager-logtype-e.md#LogType)��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## action

```TypeScript
action?: Action
```

���ջ��߶������ݰ���

���ӷ���ǽ���˹���ʱ���

�Ƴ�����ǽʱ�Ǳ����ֵΪ��ʱ����ʾ������е�ƥ��[Action](arkts-mdm-networkmanager-action-e.md#Action)�����������srcAddr��destAddr��srcPort��destPort��appUidҲ���봫��
��ֵ��

**类型：** Action

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appUid

```TypeScript
appUid?: string
```

Ӧ��uid��

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## destAddr

```TypeScript
destAddr?: string
```

ipĿ���ַ��֧��IP�Σ����磺192.168.0.0/22����192.168.1.100-192.168.1.200

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## destPort

```TypeScript
destPort?: string
```

Ŀ��˿ڡ�

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## direction

```TypeScript
direction?: Direction
```

��������

���ӷ���ǽ���˹���ʱ���

�Ƴ�����ǽʱ�Ǳ����ֵΪ��ʱ����ʾ������е�[Direction](arkts-mdm-networkmanager-direction-e.md#Direction)������srcAddr��destAddr��srcPort��destPort��appUidҲ���봫
���ֵ��

**类型：** Direction

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## family

```TypeScript
family?: number
```

IPЭ��汾��֧��ȡֵΪ1��2��ȡֵΪ1��ʾIPv4��ȡֵΪ2��ʾIPv6��
ȡֵ��ΧΪȫ�������� Ĭ��ֵ�� 1��

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## logType

```TypeScript
logType?: LogType
```

��־���ͣ���ǰ��֧������NFLOG���ͣ��ò�����֧��PC/2in1�豸��
���ӷ���ǽ���˹���ʱ���˲����Ǳ������д�����ڶ�����ܾ����ݰ�ʱ��Ч��<!--RP1--><!--RP1End-->
�Ƴ�����ǽ���˹���ʱ�������ĳ����ʱ�Ǳ����Ӱ������������գ����Ƴ���������ʱ���Ƿ���д������ù���һ�£�������ܵ��¹��˹����Ѿ��Ƴ���������־���ڼ�¼�����⣻��ͬ���˹����Ƴ�ʱ���밴����ʱ��˳���Ƴ���
��ȡ����ǽ���˹���ʱ������־��Ч�ĳ������Ի�ȡ��logType�ֶΡ�

**类型：** LogType

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## protocol

```TypeScript
protocol?: Protocol
```

����Э�顣��ֵΪALL����ICMPʱ������srcPort��destPort��Ч��

**类型：** Protocol

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## srcAddr

```TypeScript
srcAddr?: string
```

ipԴ��ַ��֧��IP�Σ����磺192.168.0.0/22����192.168.1.100-192.168.1.200

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## srcPort

```TypeScript
srcPort?: string
```

Դ�˿ڡ�

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

