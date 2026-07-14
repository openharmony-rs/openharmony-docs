# SubTabBarStyle

��ҳǩ��ʽ���򿪺����л�ҳǩʱ�Ქ����ת������

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## board

```TypeScript
board(value: BoardStyle): SubTabBarStyle
```

����ѡ����ҳǩ�ı�������ҳǩ�ı��������ˮƽģʽ����Ч��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BoardStyle | 是 | ѡ����ҳǩ�ı�������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SubTabBarStyle | ����SubTabBarStyle�������� |

## constructor

```TypeScript
constructor(content: ResourceStr)
```

SubTabBarStyle�Ĺ��캯����

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ResourceStr | 是 | ҳǩ�ڵ��������ݡ� |

## constructor

```TypeScript
constructor(content: ResourceStr | ComponentContent)
```

SubTabBarStyle�Ĺ��캯����֧��ComponentContent�����Զ������ݡ�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ResourceStr \| ComponentContent | 是 | ҳǩ�ڵ����ݡ�<br />**˵����**<br />1.�Զ������ݲ�֧��labelStyle���ԡ�<br />2.�Զ������ݳ���ҳǩ��Χ������ʾ�������֡�<br />3.�Զ�������С��ҳǩ��Χ�������ж��롣<br />4.�Զ��������쳣���޿�����ʾ���������ʾ�հס� |

## id

```TypeScript
id(value: string): SubTabBarStyle
```

������ҳǩ��id��

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | ��ҳǩ��id�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SubTabBarStyle | ����SubTabBarStyle�������� |

## indicator

```TypeScript
indicator(value: IndicatorStyle): SubTabBarStyle
```

����ѡ����ҳǩ���»��߷����ҳǩ���»��߷�����ˮƽģʽ����Ч��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | IndicatorStyle | 是 | ѡ����ҳǩ���»��߷����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SubTabBarStyle | ����SubTabBarStyle�������� |

## indicator

```TypeScript
indicator(value: IndicatorStyle | DrawableTabBarIndicator): SubTabBarStyle
```

����ѡ����ҳǩ���»��߷����[indicator](arkts-arkui-subtabbarstyle-c.md#indicator-1)��ȣ�������ͼƬ��ʽ���»��߷��ͼƬ����ʾЧ������
[ImageFit.Cover](arkts-arkui-imagefit-e.md)����ҳǩ���»��߷�����ˮƽģʽ����Ч��

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | IndicatorStyle \| DrawableTabBarIndicator | 是 | ѡ����ҳǩ���»��߷�����<br />IndicatorStyle��һ����ʽ���»�����ʽ��<br />DrawableTabBarIndicator��ͼƬ��ʽ���»�����ʽ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SubTabBarStyle | ����SubTabBarStyle�������� |

## labelStyle

```TypeScript
labelStyle(value: LabelStyle): SubTabBarStyle
```

������ҳǩ��label�ı����������ʽ��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | LabelStyle | 是 | ��ҳǩ��label�ı����������ʽ���� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SubTabBarStyle | ����SubTabBarStyle�������� |

## of

```TypeScript
static of(content: ResourceStr): SubTabBarStyle
```

SubTabBarStyle�ľ�̬���캯����

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ResourceStr | 是 | ҳǩ�ڵ��������ݡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SubTabBarStyle | ���ش�����SubTabBarStyle���� |

## of

```TypeScript
static of(content: ResourceStr | ComponentContent): SubTabBarStyle
```

SubTabBarStyle�ľ�̬���캯����֧��ComponentContent�����Զ������ݡ�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ResourceStr \| ComponentContent | 是 | ҳǩ�ڵ����ݡ�֧��ComponentContent�����Զ������ݡ�<br />**˵����**<br />1.�Զ������ݲ�֧��labelStyle���ԡ�<br />2.�Զ������ݳ���ҳǩ��Χ������ʾ�������֡�<br />3.�Զ�������С��ҳǩ��Χ�������ж��롣<br />4.�Զ��������쳣���޿�����ʾ���������ʾ�հס� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SubTabBarStyle | ���ش�����SubTabBarStyle���� |

## padding

```TypeScript
padding(value: Padding | Dimension): SubTabBarStyle
```

������ҳǩ���ڱ߾����ԣ���֧�ְٷֱ����ã���ʹ��Dimensionʱ���ĸ������ڱ߾�ͬʱ��Ч��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Padding \| Dimension | 是 | ��ҳǩ���ڱ߾����ԡ�<br/>ȡֵ��Χ��[0, +��]<br/>�쳣ֵʱȡĬ��ֵ��<br />Ĭ��ֵ��{left:8.0vp,right:8.0vp,top:17.0vp,bottom:18.0vp} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SubTabBarStyle | ����SubTabBarStyle�������� |

## padding

```TypeScript
padding(padding: LocalizedPadding): SubTabBarStyle
```

������ҳǩ���ڱ߾����ԣ�֧�־�����������֧�ְٷֱ����ã���

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| padding | LocalizedPadding | 是 | ��ҳǩ���ڱ߾����ԡ�<br/>�쳣ֵʱȡĬ��ֵ��<br/>ȡֵ��Χ��[0, +��]<br/>�쳣ֵʱȡĬ��ֵ��<br />Ĭ��ֵ��{start:LengthMetrics.vp(8),end:LengthMetrics.vp(8),<br/>top:LengthMetrics.vp(17),bottom:LengthMetrics.vp(18)} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SubTabBarStyle | ����SubTabBarStyle�������� |

## selectedMode

```TypeScript
selectedMode(value: SelectedMode): SubTabBarStyle
```

����ѡ����ҳǩ����ʾ��ʽ����ҳǩ����ʾ��ʽ����ˮƽģʽ����Ч��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | SelectedMode | 是 | ѡ����ҳǩ����ʾ��ʽ��<br />Ĭ��ֵ��SelectedMode.INDICATOR |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SubTabBarStyle | ����SubTabBarStyle�������� |

