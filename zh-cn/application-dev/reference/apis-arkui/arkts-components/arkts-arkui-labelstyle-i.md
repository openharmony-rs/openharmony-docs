# LabelStyle

label�ı����������ʽ����

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

����label�ı�������ʽ��

��ҳǩΪ��ҳǩʱ��Ĭ��ֵ�������С16.0fp����������'HarmonyOS Sans'��������������ѡ��ʱ�����еȣ�δѡ��ʱ����������

��ҳǩΪ�ײ�ҳǩʱ��Ĭ��ֵ�������С10.0fp����������'HarmonyOS Sans'�������������������еȡ�

��API version 12��ʼ���ײ�ҳǩ���������Ų�ʱĬ�������СΪ12.0fp��

**类型：** Font

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy?: TextHeightAdaptivePolicy
```

����Label�ı�����Ӧ�߶ȵķ�ʽ��Ĭ��ֵ������������ȡ�

**类型：** TextHeightAdaptivePolicy

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: number | ResourceStr
```

����label�ı������ʾ�ֺţ���֧�ְٷֱ����ã��������minFontSize�Լ�maxLines�򲼾ִ�С����ʹ�á�����Ӧ�ı���С��Ч��font.size����Ч��Ĭ��ֵ��0.0fp����Ĭ������Ӧ�ı���С����Ч��

ȡֵ��Χ��[minFontSize, +��)��

**类型：** number | ResourceStr

**默认值：** 0.0fp [since 11]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: number
```

����label�ı���������������ָ���˲��������ı���಻�ᳬ��ָ�����С�����ж�����ı�������ͨ��textOverflow��ָ���ضϷ�ʽ��Ĭ��ֵ��1��

ȡֵ��Χ��[1, +��)��

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: number | ResourceStr
```

����label�ı���С��ʾ�ֺţ���֧�ְٷֱ����ã��������maxFontSize�Լ�maxLines�򲼾ִ�С����ʹ�á�����Ӧ�ı���С��Ч��font.size����Ч��Ĭ��ֵ��0.0fp����Ĭ������Ӧ�ı���С����Ч��

ȡֵ��Χ��(0, +��)��

**类型：** number | ResourceStr

**默认值：** 0.0fp [since 11]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

����label�ı�����ʱ����ʾ��ʽ��Ĭ��ֵ��ʡ�ԺŽضϡ�

**类型：** TextOverflow

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedColor

```TypeScript
selectedColor?: ResourceColor
```

����label�ı�����ѡ��ʱ����ɫ��

Ĭ��ֵ��#FF007DFF

**类型：** ResourceColor

**默认值：** #FF007DFF

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## unselectedColor

```TypeScript
unselectedColor?: ResourceColor
```

����label�ı�����δѡ��ʱ����ɫ��

Ĭ��ֵ��#99182431

**类型：** ResourceColor

**默认值：** #99182431

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

