# SubTabBarStyle

��ҳǩ��ʽ���򿪺����л�ҳǩʱ�Ქ����ת������

**起始版本：** 9

<!--Device-unnamed-declare class SubTabBarStyle--><!--Device-unnamed-declare class SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## board

```TypeScript
board(value: BoardStyle): SubTabBarStyle
```

����ѡ����ҳǩ�ı�������ҳǩ�ı��������ˮƽģʽ����Ч��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SubTabBarStyle-board(value: BoardStyle): SubTabBarStyle--><!--Device-SubTabBarStyle-board(value: BoardStyle): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BoardStyle](arkts-arkui-tab-content-boardstyle-i.md) | 是 | ѡ����ҳǩ�ı�������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tab-content-subtabbarstyle-c.md) | ����SubTabBarStyle�������� |

## constructor

```TypeScript
constructor(content: ResourceStr)
```

SubTabBarStyle�Ĺ��캯����

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SubTabBarStyle-constructor(content: ResourceStr)--><!--Device-SubTabBarStyle-constructor(content: ResourceStr)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | ҳǩ�ڵ��������ݡ� |

## constructor

```TypeScript
constructor(content: ResourceStr | ComponentContent)
```

SubTabBarStyle�Ĺ��캯����֧��ComponentContent�����Զ������ݡ�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SubTabBarStyle-constructor(content: ResourceStr | ComponentContent)--><!--Device-SubTabBarStyle-constructor(content: ResourceStr | ComponentContent)-End-->

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SubTabBarStyle-id(value: string): SubTabBarStyle--><!--Device-SubTabBarStyle-id(value: string): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | ��ҳǩ��id�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tab-content-subtabbarstyle-c.md) | ����SubTabBarStyle�������� |

## indicator

```TypeScript
indicator(value: IndicatorStyle): SubTabBarStyle
```

����ѡ����ҳǩ���»��߷����ҳǩ���»��߷�����ˮƽģʽ����Ч��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SubTabBarStyle-indicator(value: IndicatorStyle): SubTabBarStyle--><!--Device-SubTabBarStyle-indicator(value: IndicatorStyle): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [IndicatorStyle](arkts-arkui-tab-content-indicatorstyle-i.md) | 是 | ѡ����ҳǩ���»��߷����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tab-content-subtabbarstyle-c.md) | ����SubTabBarStyle�������� |

## indicator

```TypeScript
indicator(value: IndicatorStyle | DrawableTabBarIndicator): SubTabBarStyle
```

����ѡ����ҳǩ���»��߷����[indicator](arkts-arkui-tab-content-subtabbarstyle-c.md#indicator-1)��ȣ�������ͼƬ��ʽ���»��߷��ͼƬ����ʾЧ������[ImageFit.Cover](../arkts-apis/arkts-arkui-enums-imagefit-e.md)����ҳǩ���»��߷�����ˮƽģʽ����Ч��

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-SubTabBarStyle-indicator(value: IndicatorStyle | DrawableTabBarIndicator): SubTabBarStyle--><!--Device-SubTabBarStyle-indicator(value: IndicatorStyle | DrawableTabBarIndicator): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | IndicatorStyle \| DrawableTabBarIndicator | 是 | ѡ����ҳǩ���»��߷�����<br />IndicatorStyle��һ����ʽ���»�����ʽ��<br />DrawableTabBarIndicator��ͼƬ��ʽ���»�����ʽ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tab-content-subtabbarstyle-c.md) | ����SubTabBarStyle�������� |

## labelStyle

```TypeScript
labelStyle(value: LabelStyle): SubTabBarStyle
```

������ҳǩ��label�ı����������ʽ��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SubTabBarStyle-labelStyle(value: LabelStyle): SubTabBarStyle--><!--Device-SubTabBarStyle-labelStyle(value: LabelStyle): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LabelStyle](arkts-arkui-button-labelstyle-i.md) | 是 | ��ҳǩ��label�ı����������ʽ���� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tab-content-subtabbarstyle-c.md) | ����SubTabBarStyle�������� |

## of

```TypeScript
static of(content: ResourceStr): SubTabBarStyle
```

SubTabBarStyle�ľ�̬���캯����

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SubTabBarStyle-static of(content: ResourceStr): SubTabBarStyle--><!--Device-SubTabBarStyle-static of(content: ResourceStr): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | ҳǩ�ڵ��������ݡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tab-content-subtabbarstyle-c.md) | ���ش�����SubTabBarStyle���� |

## of

```TypeScript
static of(content: ResourceStr | ComponentContent): SubTabBarStyle
```

SubTabBarStyle�ľ�̬���캯����֧��ComponentContent�����Զ������ݡ�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SubTabBarStyle-static of(content: ResourceStr | ComponentContent): SubTabBarStyle--><!--Device-SubTabBarStyle-static of(content: ResourceStr | ComponentContent): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ResourceStr \| ComponentContent | 是 | ҳǩ�ڵ����ݡ�֧��ComponentContent�����Զ������ݡ�<br />**˵����**<br />1.�Զ������ݲ�֧��labelStyle���ԡ�<br />2.�Զ������ݳ���ҳǩ��Χ������ʾ�������֡�<br />3.�Զ�������С��ҳǩ��Χ�������ж��롣<br />4.�Զ��������쳣���޿�����ʾ���������ʾ�հס� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tab-content-subtabbarstyle-c.md) | ���ش�����SubTabBarStyle���� |

## padding

```TypeScript
padding(value: Padding | Dimension): SubTabBarStyle
```

������ҳǩ���ڱ߾����ԣ���֧�ְٷֱ����ã���ʹ��Dimensionʱ���ĸ������ڱ߾�ͬʱ��Ч��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SubTabBarStyle-padding(value: Padding | Dimension): SubTabBarStyle--><!--Device-SubTabBarStyle-padding(value: Padding | Dimension): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Padding \| Dimension | 是 | ��ҳǩ���ڱ߾����ԡ�<br/>ȡֵ��Χ��[0, +��]<br/>�쳣ֵʱȡĬ��ֵ��<br />Ĭ��ֵ��{left:8.0vp,right:8.0vp,top:17.0vp,bottom:18.0vp} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tab-content-subtabbarstyle-c.md) | ����SubTabBarStyle�������� |

## padding

```TypeScript
padding(padding: LocalizedPadding): SubTabBarStyle
```

������ҳǩ���ڱ߾����ԣ�֧�־�����������֧�ְٷֱ����ã���

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SubTabBarStyle-padding(padding: LocalizedPadding): SubTabBarStyle--><!--Device-SubTabBarStyle-padding(padding: LocalizedPadding): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| padding | [LocalizedPadding](../arkts-apis/arkts-arkui-units-localizedpadding-i.md) | 是 | ��ҳǩ���ڱ߾����ԡ�<br/>�쳣ֵʱȡĬ��ֵ��<br/>ȡֵ��Χ��[0, +��]<br/>�쳣ֵʱȡĬ��ֵ��<br />Ĭ��ֵ��{start:LengthMetrics.vp(8),end:LengthMetrics.vp(8),<br/>top:LengthMetrics.vp(17),bottom:LengthMetrics.vp(18)} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tab-content-subtabbarstyle-c.md) | ����SubTabBarStyle�������� |

## selectedMode

```TypeScript
selectedMode(value: SelectedMode): SubTabBarStyle
```

����ѡ����ҳǩ����ʾ��ʽ����ҳǩ����ʾ��ʽ����ˮƽģʽ����Ч��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SubTabBarStyle-selectedMode(value: SelectedMode): SubTabBarStyle--><!--Device-SubTabBarStyle-selectedMode(value: SelectedMode): SubTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SelectedMode](arkts-arkui-tab-content-selectedmode-e.md) | 是 | ѡ����ҳǩ����ʾ��ʽ��<br />Ĭ��ֵ��SelectedMode.INDICATOR |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tab-content-subtabbarstyle-c.md) | ����SubTabBarStyle�������� |

