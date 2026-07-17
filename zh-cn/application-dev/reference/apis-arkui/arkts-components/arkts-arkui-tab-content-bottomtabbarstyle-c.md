# BottomTabBarStyle

�ײ�ҳǩ�Ͳ��ҳǩ��ʽ��

**起始版本：** 9

<!--Device-unnamed-declare class BottomTabBarStyle--><!--Device-unnamed-declare class BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)
```

BottomTabBarStyle�Ĺ��캯����

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)--><!--Device-BottomTabBarStyle-constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | ResourceStr \| TabBarSymbol | 是 | ҳǩ�ڵ�ͼƬ���ݡ�<br>**起始版本：** 9 - 11 |
| text | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | ҳǩ�ڵ��������ݡ� |

## iconStyle

```TypeScript
iconStyle(style: TabBarIconStyle): BottomTabBarStyle
```

���õײ�ҳǩ��labelͼ�����ʽ��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-iconStyle(style: TabBarIconStyle): BottomTabBarStyle--><!--Device-BottomTabBarStyle-iconStyle(style: TabBarIconStyle): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TabBarIconStyle](arkts-arkui-tab-content-tabbariconstyle-i.md) | 是 | �ײ�ҳǩ��labelͼ�����ʽ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tab-content-bottomtabbarstyle-c.md) | ����BottomTabBarStyle�������� |

## id

```TypeScript
id(value: string): BottomTabBarStyle
```

���õײ�ҳǩ��id��

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-id(value: string): BottomTabBarStyle--><!--Device-BottomTabBarStyle-id(value: string): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | ���õײ�ҳǩ��id�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tab-content-bottomtabbarstyle-c.md) | ����BottomTabBarStyle�������� |

## labelStyle

```TypeScript
labelStyle(value: LabelStyle): BottomTabBarStyle
```

���õײ�ҳǩ��label�ı����������ʽ��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-labelStyle(value: LabelStyle): BottomTabBarStyle--><!--Device-BottomTabBarStyle-labelStyle(value: LabelStyle): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LabelStyle](arkts-arkui-button-labelstyle-i.md) | 是 | �ײ�ҳǩ��label�ı����������ʽ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tab-content-bottomtabbarstyle-c.md) | ����BottomTabBarStyle�������� |

## layoutMode

```TypeScript
layoutMode(value: LayoutMode): BottomTabBarStyle
```

���õײ�ҳǩ��ͼƬ�������Ų��ķ�ʽ��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-layoutMode(value: LayoutMode): BottomTabBarStyle--><!--Device-BottomTabBarStyle-layoutMode(value: LayoutMode): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LayoutMode](arkts-arkui-tab-content-layoutmode-e.md) | 是 | �ײ�ҳǩ��ͼƬ�������Ų��ķ�ʽ���������LayoutModeö�١�<br/>Ĭ��ֵ��LayoutMode.VERTICAL |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tab-content-bottomtabbarstyle-c.md) | ����BottomTabBarStyle�������� |

## of

```TypeScript
static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle
```

BottomTabBarStyle�ľ�̬���캯����

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle--><!--Device-BottomTabBarStyle-static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | ResourceStr \| TabBarSymbol | 是 | ҳǩ�ڵ�ͼƬ���ݡ�<br>**起始版本：** 10 - 11 |
| text | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | ҳǩ�ڵ��������ݡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tab-content-bottomtabbarstyle-c.md) | ���ش�����BottomTabBarStyle���� |

## padding

```TypeScript
padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle
```

���õײ�ҳǩ���ڱ߾����ԣ���֧�ְٷֱ����ã���ʹ��Dimensionʱ���ĸ������ڱ߾�ͬʱ��Ч��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle--><!--Device-BottomTabBarStyle-padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Padding \| Dimension \| LocalizedPadding | 是 | �ײ�ҳǩ���ڱ߾ࡣ<br/>ȡֵ��Χ��[0, +��]<br/>Ĭ��ֵ��{left:4.0vp,right:4.0vp,top:0.0vp,bottom:0.0vp}<br/>ʹ��LocalizedPaddingʱ��֧�־���������<br />Ĭ��ֵ��{start:LengthMetrics.vp(4),end:LengthMetrics.vp(4),<br/>top:LengthMetrics.vp(0),bottom:LengthMetrics.vp(0)}<br>**起始版本：** 10 - 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tab-content-bottomtabbarstyle-c.md) | ����BottomTabBarStyle�������� |

## symmetricExtensible

```TypeScript
symmetricExtensible(value: boolean): BottomTabBarStyle
```

���õײ�ҳǩ��ͼƬ�������Ƿ���ԶԳƽ������ҵײ�ҳǩ�Ŀ���λ���е���Сֵ����fixedˮƽģʽ���ڵײ�ҳǩ֮����Ч��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-symmetricExtensible(value: boolean): BottomTabBarStyle--><!--Device-BottomTabBarStyle-symmetricExtensible(value: boolean): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | �ײ�ҳǩ��ͼƬ�������Ƿ���ԶԳƽ������ҵײ�ҳǩ�Ŀ���λ���е���Сֵ��<br/>Ĭ��ֵ��false���ײ�ҳǩ��ͼƬ�����ֲ����ԶԳƽ������ҵײ�ҳǩ�Ŀ���λ���е���Сֵ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tab-content-bottomtabbarstyle-c.md) | ����BottomTabBarStyle�������� |

## verticalAlign

```TypeScript
verticalAlign(value: VerticalAlign): BottomTabBarStyle
```

���õײ�ҳǩ��ͼƬ�������ڴ�ֱ�����ϵĶ����ʽ��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BottomTabBarStyle-verticalAlign(value: VerticalAlign): BottomTabBarStyle--><!--Device-BottomTabBarStyle-verticalAlign(value: VerticalAlign): BottomTabBarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [VerticalAlign](../arkts-apis/arkts-arkui-enums-verticalalign-e.md) | 是 | �ײ�ҳǩ��ͼƬ�������ڴ�ֱ�����ϵĶ����ʽ��<br/>Ĭ��ֵ��VerticalAlign.Center |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tab-content-bottomtabbarstyle-c.md) | ����BottomTabBarStyle�������� |

