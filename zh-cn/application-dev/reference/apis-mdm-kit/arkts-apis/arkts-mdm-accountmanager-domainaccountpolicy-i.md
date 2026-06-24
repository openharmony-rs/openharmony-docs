# DomainAccountPolicy

���˺Ų��ԡ�

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## authenticationValidityPeriod

```TypeScript
authenticationValidityPeriod?: number
```

��ʾ���˺���֤Token����Ч�ڣ���λ��s����ȡֵ��Χ��[-1,2147483647]����Ч����ʼʱ��Ϊ���һ�����˺ŵ���֤ʱ��㣬���¼������������ȡ�

Ĭ��ֵΪ-1����ʾToken������Ч��ȡֵΪ0����ʾToken����ʧЧ��Token����/ʧЧ���û�����ϵͳʱ����������˺���֤����֤���˺ź����롣

**类型：** number

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## passwordExpirationNotification

```TypeScript
passwordExpirationNotification?: number
```

��ʾ���˺��������ǰ��ʾʱ�䣨��λ��s����ȡֵ��Χ��[0,2147483647]��

Ĭ��ֵΪ0����ʾ���˺�������ڲ���ʾ��

**˵��**��passwordExpirationNotification����passwordValidityPeriod���ʹ�ã���ϵͳʱ����ڻ���ڣ��豸�����һ���޸����˺�����ʱ�� +
passwordValidityPeriod - passwordExpirationNotification��ʱ���ᷢҳ��֪ͨ��ʾ���뼴�����ڡ�

**类型：** number

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## passwordValidityPeriod

```TypeScript
passwordValidityPeriod?: number
```

��ʾ���˺�������Ч�ڣ���λ��s����ȡֵ��Χ��[-1,2147483647]����Ч����ʼʱ��Ϊ�豸�����һ���޸������ʱ��㡣

Ĭ��ֵΪ-1����ʾ���˺�����������Ч��

**类型：** number

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

