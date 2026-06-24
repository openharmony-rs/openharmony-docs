# DomainFilterRule

�������˹���

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

�����������˹���ʱ���

�Ƴ��������˹���ʱ�Ǳ����ֵΪ��ʱ����ʾ������е�ƥ��[Action](arkts-mdm-networkmanager-action-e.md#Action)�����������domainName��appUidҲ���봫���ֵ��

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

## direction

```TypeScript
direction?: Direction
```

��������

�����������˹���ʱ�Ǳ����ֵ��Ϊ�������������ʱ��ʵ��Ч��Ϊ���������Ϊת����ʱ��appUid������Ϊ�գ�����ᱨ401�����롣

�Ƴ��������˹���ʱ�Ǳ����ֵΪ��ʱ����ʾ������е�[Direction](arkts-mdm-networkmanager-direction-e.md#Direction)������domainName��appUidҲ���봫���ֵ��

**类型：** Direction

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## domainName

```TypeScript
domainName?: string
```

�����������������˹���ʱ���֧�������ֶ�ƥ�䣬���磬domainName����`example.com`����ô`example.com`��`www.example.com`��`www.test.example.com`�ᱻƥ��
��`linkexample.com`���ᱻƥ�䡣

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## family

```TypeScript
family?: number
```

IPЭ��汾��֧��ȡֵΪ1��2��ȡֵΪ1��ʾIPv4��ȡֵΪ2��ʾIPv6��
ȡֵӦΪ[1,2]�ڵ�������

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

