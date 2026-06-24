# Tabs属性/事件

��֧��[ͨ������](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)�⣬��֧���������ԣ�

��֧��[ͨ���¼�](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)�⣬��֧�������¼���

**继承/实现关系：** TabsAttribute extends [CommonMethod<TabsAttribute>](CommonMethod<TabsAttribute>)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## animationCurve

```TypeScript
animationCurve(curve: Curve | ICurve)
```

����Tabs��ҳ�������ߡ��������߲ο�[Curve](arkts-arkui-enums-curve-e.md#Curve)��Ҳ����ͨ��[��ֵ����](arkts-curves.md#curves)ģ���ṩ�Ľӿڴ����Զ���Ĳ�ֵ���߶���

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| curve | Curve \| ICurve | 是 | Tabs��ҳ�Ķ������ߡ�<br/>Ĭ��ֵ��<br/>����TabContent��ҳʱ��Ĭ��ֵΪinterpolatingSpring(-1, 1, 228, 30<br/>)��<br/>���TabBarҳǩ�͵���TabsController��changeIndex�ӿڷ�ҳʱ��Ĭ��ֵΪcubicBezierCurve(0.2, 0.0, 0.1, 1.0)��<br/>�����Զ��嶯������ʱ������<br/>��ҳ�͵��ҳǩ������changeIndex��ҳ��ʹ�����õĶ������ߡ� |

## animationDuration

```TypeScript
animationDuration(value: number)
```

����Tabs��ҳ����ʱ����

animationCurve������ʱ�����ڻ���TabContent��ҳ��������interpolatingSpring(-1, 1, 228, 30)ʱ��ֻ��������������Ӱ�죬animationDurationֻ�ܿ��Ƶ��
TabBarҳǩ�͵���TabsController��changeIndex�ӿ��л�TabContent�Ķ���ʱ����

����animationDuration���Ƶ����߿��Բ���[��ֵ����](arkts-curves.md#curves)ģ�飬����
[springMotion](arkts-arkui-curves-springmotion-f.md#springMotion-1)��
[responsiveSpringMotion](arkts-arkui-curves-responsivespringmotion-f.md#responsiveSpringMotion-1)��
[interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md#interpolatingSpring-1)���͵����ߡ�

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | Tabs��ҳ�Ķ���ʱ����<br/>Ĭ��ֵ��<br/>API version 10����ǰ�������ø����Ի�����Ϊnullʱ��Ĭ��ֵΪ0����Tabs��ҳ�޶���������ΪС��0��<br/>undefinedʱ��Ĭ��ֵΪ300��<br/>API version 11���Ժ󣬲����ø����Ի�����Ϊ�쳣ֵ��������TabBarΪBottomTabBarStyle��ʽʱ��Ĭ��ֵΪ0������TabBarΪ������ʽʱ��Ĭ��ֵ<br/>Ϊ300��<br/>��λ��ms<br/>ȡֵ��Χ��[0, +��) |

## animationMode

```TypeScript
animationMode(mode: Optional<AnimationMode>)
```

���õ��TabBarҳǩ�����TabsController��changeIndex�ӿ�ʱ�л�TabContent�Ķ�����ʽ��

> **˵����**

> �����Բ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | Optional&lt;AnimationMode&gt; | 是 | ���TabBarҳǩ�����TabsController��changeIndex�ӿ�ʱ�л�TabContent�Ķ�����ʽ��<br/>Ĭ��ֵ��<br/>AnimationMode.CONTENT_FIRST����ʾ�ڵ��TabBarҳǩ�����TabsController��changeIndex�ӿ��л�TabContentʱ���ȼ���Ŀ��ҳ���ݣ��ٿ�ʼ�л������� |

## barBackgroundBlurStyle

```TypeScript
barBackgroundBlurStyle(value: BlurStyle)
```

����TabBar�ı���ģ�����ʡ�

> **˵����**

> ��API version 12��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BlurStyle | 是 | TabBar�ı���ģ�����ʡ�<br/>Ĭ��ֵ��BlurStyle.NONE |

## barBackgroundBlurStyle

```TypeScript
barBackgroundBlurStyle(style: BlurStyle, options: BackgroundBlurStyleOptions)
```

ΪTabBar�ṩһ���ڱ���������֮���ģ��������ͨ��ö��ֵ�ķ�ʽ��װ�˲�ͬ��ģ���뾶���ɰ���ɫ���ɰ�͸���ȡ����Ͷȡ����ȡ�

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | BlurStyle | 是 | ����ģ����ʽ��ģ����ʽ�з�װ��ģ���뾶���ɰ���ɫ���ɰ�͸���ȡ����Ͷȡ�������������� |
| options | BackgroundBlurStyleOptions | 是 | ����ģ��ѡ� |

## barBackgroundColor

```TypeScript
barBackgroundColor(value: ResourceColor)
```

����TabBar�ı�����ɫ��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ResourceColor | 是 | TabBar�ı�����ɫ��<br/>Ĭ��ֵ��Color.Transparent��͸�� |

## barBackgroundEffect

```TypeScript
barBackgroundEffect(options: BackgroundEffectOptions)
```

����TabBar�������ԣ���������ģ���뾶�����ȣ����Ͷȣ���ɫ�Ȳ�����

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | BackgroundEffectOptions | 是 | ����TabBar�������԰�����ģ���뾶�����ȣ����Ͷȣ���ɫ�ȡ� |

## barFloatingStyle

```TypeScript
barFloatingStyle(style: Optional<FloatingTabBarStyle>)
```

Ϊҳǩ�����ø�����ʽ��

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | Optional&lt;FloatingTabBarStyle&gt; | 是 | ҳǩ���ĸ�����ʽ |

## barGridAlign

```TypeScript
barGridAlign(value: BarGridColumnOptions)
```

��դ�񻯷�ʽ����TabBar�Ŀɼ����򡣾���μ�BarGridColumnOptions���󡣽�ˮƽģʽ����Ч��
[��������XS��XL��XXL�豸](../../../../ui/arkts-layout-development-grid-layout.md#դ�������ϵ�)��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BarGridColumnOptions | 是 | ��դ�񻯷�ʽ����TabBar�Ŀɼ����� |

## barHeight

```TypeScript
barHeight(value: Length)
```

����TabBar�ĸ߶�ֵ������Tabs��������heightΪ'auto'����TabBar����Ӧ������߶ȡ�height����ΪС��0�����Tabs�߶�ֵʱ����Ĭ��ֵ��ʾ��

API version 14֮ǰ�İ汾��������barHeightΪ�̶�ֵ��TabBar�޷���չ�ײ���ȫ������API version 14��ʼ֧�����
[safeAreaPadding](arkts-arkui-commonmethod-c.md#safeAreaPadding-1)���ԣ���safeAreaPadding������bottom����bottom����Ϊ0ʱ������ʵ����չ��ȫ����

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Length | 是 | TabBar�ĸ߶�ֵ��<br/>Ĭ��ֵ��<br/>δ������ʽ����ͨ��CustomBuilder�����Զ�����ʽ��TabBar��vertical����Ϊfalseʱ��Ĭ��ֵΪ56vp��<br/><br/>δ������ʽ����ͨ��CustomBuilder�����Զ�����ʽ��TabBar��vertical����Ϊtrueʱ��Ĭ��ֵΪTabs�ĸ߶ȡ�<br/>����<br/>[SubTabBarStyle](arkts-arkui-tabcontent-subtabbarstyle-c.md#SubTabBarStyle)��ʽ��vertical����Ϊfalseʱ��Ĭ��ֵΪ56vp��<br/>����SubTabBarStyle��ʽ��vertical����Ϊtrueʱ��Ĭ��<br/>ֵΪTabs�ĸ߶ȡ�<br/>����[BottomTabBarStyle](arkts-arkui-tabcontent-bottomtabbarstyle-c.md#BottomTabBarStyle)��ʽ��vertical����Ϊtrueʱ��Ĭ��ֵΪTabs�ĸ߶ȡ�<br/>����<br/>BottomTabBarStyle��ʽ��vertical����Ϊfalseʱ��Ĭ��ֵΪ56vp����API version 12��ʼ��Ĭ��ֵ���Ϊ48vp�� [since 8] |

## barHeight

```TypeScript
barHeight(height: Length, noMinHeightLimit: boolean)
```

����TabBar�ĸ߶�ֵ������Tabs��������heightΪ'auto'����TabBar����Ӧ������߶ȣ���ͨ������noMinHeightLimitΪtrue������Ӧ�߶ȿ���С��TabBarĬ�ϸ߶ȡ�height����ΪС��0�����
Tabs�߶�ֵʱ����Ĭ��ֵ��ʾ��

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | Length | 是 | TabBar�ĸ߶�ֵ��<br/>Ĭ��ֵ��<br/>δ������ʽ����ͨ��CustomBuilder�����Զ�����ʽ��TabBar��vertical����Ϊfalseʱ��Ĭ��ֵΪ56<br/>vp��<br/>δ������ʽ����ͨ��CustomBuilder�����Զ�����ʽ��TabBar��vertical����Ϊtrueʱ��Ĭ��ֵΪTabs�ĸ߶ȡ�<br/>����<br/>[SubTabBarStyle](arkts-arkui-tabcontent-subtabbarstyle-c.md#SubTabBarStyle)��ʽ��vertical����Ϊfalseʱ��Ĭ��ֵΪ56vp��<br/>����SubTabBarStyle��ʽ��vertical����Ϊtrueʱ��Ĭ��<br/>ֵΪTabs�ĸ߶ȡ�<br/>����[BottomTabBarStyle](arkts-arkui-tabcontent-bottomtabbarstyle-c.md#BottomTabBarStyle)��ʽ��vertical����Ϊtrueʱ��Ĭ��ֵΪTabs�ĸ߶ȡ�<br/>����<br/>BottomTabBarStyle��ʽ��vertical����Ϊfalseʱ��Ĭ��ֵΪ48vp�� |
| noMinHeightLimit | boolean | 是 | height����Ϊ'auto'ʱ�������Ƿ�ȡ��TabBar����С�߶����ơ�Ĭ��ֵΪfalse��<br/>**˵����**<br/>ֵΪtrue��ʾȡ��<br/>TabBar����С�߶����ƣ���TabBar�ĸ߶�ֵ����С��Ĭ��ֵ��<br/>ֵΪfalse��ʾ����TabBar����С�߶ȣ���TabBar����С�߶�ֵ����Ĭ��ֵ�� |

## barMode

```TypeScript
barMode(value: BarMode.Fixed)
```

����TabBar����ģʽΪBarMode.Fixed��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BarMode.Fixed | 是 | ����TabBar��ƽ������barWidth���ȣ�����ʱƽ������barHeight�߶ȣ��� |

## barMode

```TypeScript
barMode(value: BarMode.Scrollable, options: ScrollableBarModeOptions)
```

����TabBar����ģʽΪBarMode.Scrollable��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BarMode.Scrollable | 是 | ����TabBar��ʹ��ʵ�ʲ��ֿ��ȣ������ܿ��ȣ�����Tabs��barWidth������Tabs��barHeight����ɻ����� |
| options | ScrollableBarModeOptions | 是 | Scrollableģʽ�µ�TabBar�Ĳ�����ʽ��<br/>**˵����**<br/>��ˮƽģʽ����Ч�� |

## barMode

```TypeScript
barMode(value: BarMode, options?: ScrollableBarModeOptions)
```

����TabBar����ģʽ��

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BarMode | 是 | ����ģʽ��<br/>Ĭ��ֵ��BarMode.Fixed |
| options | ScrollableBarModeOptions | 否 | Scrollableģʽ�µ�TabBar�Ĳ�����ʽ��<br/>**˵����**<br/>��Scrollable��ˮƽģʽ����<br/>Ч�� [since 10] |

## barOverlap

```TypeScript
barOverlap(value: boolean)
```

����TabBar�Ƿ񱳺��ģ����������TabContent֮�ϡ�

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | TabBar�Ƿ񱳺��ģ����������TabContent֮�ϡ���barOverlap����Ϊtrueʱ��TabBar�����ģ����������TabContent֮�ϣ�����TabBarĬ��<br/>ģ�����ʵ�[BlurStyle](arkts-arkui-common-blurstyle-e.md#BlurStyle)ֵ�޸�Ϊ'BlurStyle.COMPONENT_THICK'����barOverlap����Ϊfalseʱ����ģ���͵���Ч����<br/>Ĭ��ֵ��false |

## barPosition

```TypeScript
barPosition(value: BarPosition)
```

����Tabs��ҳǩλ�á�

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BarPosition | 是 | ����Tabs��ҳǩλ�á�<br/>Ĭ��ֵ��BarPosition.Start |

## barWidth

```TypeScript
barWidth(value: Length)
```

����TabBar�Ŀ���ֵ������ΪС��0�����Tabs����ֵʱ����Ĭ��ֵ��ʾ��

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Length | 是 | TabBar�Ŀ���ֵ��<br/>Ĭ��ֵ��<br/>δ����[SubTabBarStyle](arkts-arkui-tabcontent-subtabbarstyle-c.md#SubTabBarStyle)��<br/>[BottomTabBarStyle](arkts-arkui-tabcontent-bottomtabbarstyle-c.md#BottomTabBarStyle)��TabBar��vertical����Ϊfalseʱ��Ĭ��ֵΪTabs�Ŀ��ȡ�<br/>δ����SubTabBarStyle��<br/>BottomTabBarStyle��TabBar��vertical����Ϊtrueʱ��Ĭ��ֵΪ56vp��<br/>����SubTabBarStyle��ʽ��vertical����Ϊfalseʱ��Ĭ��ֵΪTabs�Ŀ��ȡ�<br/>��<br/>��SubTabBarStyle��ʽ��vertical����Ϊtrueʱ��Ĭ��ֵΪ56vp��<br/>����BottomTabBarStyle��ʽ��vertical����Ϊtrueʱ��Ĭ��ֵΪ96vp��<br/>����<br/>BottomTabBarStyle��ʽ��vertical����Ϊfalseʱ��Ĭ��ֵΪTabs�Ŀ��ȡ� [since 8] |

## cachedMaxCount

```TypeScript
cachedMaxCount(count: number, mode: TabsCacheMode)
```

�������������󻺴����������ģʽ��δ���ø�����ʱĬ�ϻ�������������һ���󲻻��ͷš�

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | ���������󻺴������������Χʱ�Զ��ͷŲ�����Ҫ���������<br/>ȡֵ��Χ��[0, +��)�� |
| mode | TabsCacheMode | 是 | ������Ļ���ģʽ��<br/>Ĭ��ֵ��TabsCacheMode.CACHE_BOTH_SIDE |

## customContentTransition

```TypeScript
customContentTransition(delegate: TabsCustomContentTransitionCallback)
```

�Զ���Tabsҳ���л�������

ʹ��˵����

1. ��ʹ���Զ����л�����ʱ��Tabs����Դ���Ĭ���л������ᱻ���ã�ͬʱ��ҳ��Ҳ�޷����ֻ�����
2. ������Ϊundefinedʱ����ʾ��ʹ���Զ����л���������Ȼʹ������Դ���Ĭ���л�������
3. ��ǰ�Զ����л�������֧�ִ�ϡ�
4. Ŀǰ�Զ����л�����ֻ֧�����ֳ������������ҳǩ�͵���TabsController.changeIndex()�ӿڡ�
5. ��ʹ���Զ����л�����ʱ��Tabs���֧�ֵ��¼��У�����onGestureSwipe�������¼���֧�֡�
6. [onChange](TabsAttribute#onChange)��[onAnimationEnd](TabsAttribute#onAnimationEnd)�¼��Ĵ���ʱ����Ҫ����˵��������ڵ�һ���Զ��嶯��ִ�й����У������˵ڶ����Զ��嶯������ô�ڿ�ʼ�ڶ����Զ��嶯��ʱ���ͻᴥ����һ���Զ��嶯����onChange��onAnimationEnd�¼���
7. ��ʹ���Զ��嶯��ʱ�����붯����ҳ�沼�ַ�ʽ���Ϊ[Stack](stack)���֡����������δ�����������ҳ���[zIndex](arkts-arkui-commonmethod-c.md#zIndex-1)���ԣ���ô����ҳ���zIndexֵ��һ���ģ�ҳ�����Ⱦ�㼶�ᰴ����������ϵ�˳�򣨼�ҳ���indexֵ˳��ȷ������ˣ���������Ҫ�����޸�ҳ���zIndex���ԣ�������ҳ�����Ⱦ�㼶��
8. �����Բ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

> **˵����**

> ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11 - 17开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | TabsCustomContentTransitionCallback | 是 | �Զ���Tabsҳ���л�������ʼʱ�����Ļص��� [since 18] |

## divider

```TypeScript
divider(value: DividerStyle | null)
```

��������TabBar��TabContent�ķָ�����ʽ��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | DividerStyle \| null | 是 | �ָ�����ʽ��Ĭ�ϲ���ʾ�ָ��ߡ�<br/>DividerStyle���ָ��ߵ���ʽ��<br/>null������ʾ�ָ��ߡ� |

## edgeEffect

```TypeScript
edgeEffect(edgeEffect: Optional<EdgeEffect>)
```

���ñ�Ե����Ч����

> **˵����**

> ��API version 17��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| edgeEffect | Optional&lt;EdgeEffect&gt; | 是 | ��Ե����Ч����<br/>Ĭ��ֵ��EdgeEffect.Spring |

## fadingEdge

```TypeScript
fadingEdge(value: boolean)
```

����ҳǩ������������ʱ�Ƿ�����ʧ���������[barBackgroundColor](TabsAttribute#barBackgroundColor)����һ��ʹ�ã����barBackgroundColor����û�ж�
�壬��Ĭ����ʾҳǩĩ��Ϊ��ɫ�Ľ���Ч����

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | ҳǩ������������ʱ�Ƿ�����ʧ��<br/>Ĭ��ֵ��true��ҳǩ������������ʱ�ὥ����ʧ������Ϊfalseʱ��ҳǩ������������ֱ�ӽض���ʾ���������κν���Ч��?�� |

## nestedScroll

```TypeScript
nestedScroll(value: TabsNestedScrollMode | undefined)
```

����Tabs������丸�����Ƕ�׹���ģʽ��δͨ���ýӿ�����ʱ��Ĭ��Ƕ�׹���ģʽΪ[SELF_ONLY](arkts-arkui-tabs-tabsnestedscrollmode-e.md#TabsNestedScrollMode)��

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | TabsNestedScrollMode \| undefined | 是 | Tabs����͸������Ƕ�׹���ģʽ��<br/>����undefinedʱ��Tabs�������������븸��������� |

## onAnimationEnd

```TypeScript
onAnimationEnd(handler: OnTabsAnimationEndCallback)
```

�л���������ʱ�����ûص����������������������жϡ���animationDurationΪ0ʱ�����رգ��������ûص���

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | OnTabsAnimationEndCallback | 是 | �л���������ʱ�����Ļص��� [since 18] |

## onAnimationStart

```TypeScript
onAnimationStart(handler: OnTabsAnimationStartCallback)
```

�л�������ʼʱ�����ûص�����[animationDuration](TabsAttribute#animationDuration)Ϊ0ʱ�����ر���
[scrollable](TabsAttribute#scrollable)Ϊfalseʱ���������ûص���

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | OnTabsAnimationStartCallback | 是 | �л�������ʼʱ�����Ļص��� [since 18] |

## onChange

```TypeScript
onChange(event: Callback<number>)
```

Tabҳǩ�л��󴥷����¼���

����������һ���������ɴ������¼���

1������ҳ�����ҳ���л�ʱ������������������󴥷���

2��ͨ��[������](arkts-arkui-tabs-tabscontroller-c.md#TabsController)����[changeIndex](arkts-arkui-tabscontroller-c.md#changeIndex-1)�ӿڣ�Tabҳǩ�л��󴥷���

3����̬�޸�[״̬����](../../../../ui/state-management/arkts-state.md)�����index����ֵ��Tabҳǩ�л��󴥷���

4�����TabBarҳǩ��Tabҳǩ�л��󴥷���

> **˵����**

> ʹ���Զ���ҳǩʱ����onChange�¼����������ܻᵼ�»���ҳ���л����ִ��ҳǩ�����������Զ���ҳǩ�л�Ч���ӳ١�������
> [onAnimationStart](TabsAttribute#onAnimationStart)�м�����ˢ�µ�ǰ��������ȷ����Ч�ܹ���ʱ����������ʵ�ֿɲο�
> [ʾ��3](../../../../reference/apis-arkui/arkui-ts/ts-container-tabs.md#ʾ��3�Զ���ҳǩ�л�����)��

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | 是 | ��ǰ��ʾ��index������������0��ʼ���㡣 [since 18] |

## onContentDidScroll

```TypeScript
onContentDidScroll(handler: OnTabsContentDidScrollCallback | undefined)
```

����Tabsҳ�滬���¼���

��ҳ�滬�������У�����Ӵ�������ҳ����֡����[OnTabsContentDidScrollCallback](arkts-arkui-tabs-ontabscontentdidscrollcallback-t.md#OnTabsContentDidScrollCallback)�ص������磬���Ӵ������±�Ϊ0��1������ҳ��
ʱ����ÿ֡��������indexֵ�ֱ�Ϊ0��1�Ļص���

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | OnTabsContentDidScrollCallback \| undefined | 是 | Tabs����ʱ�����Ļص���undefined����ԭ�лص��� |

## onContentWillChange

```TypeScript
onContentWillChange(handler: OnTabsContentWillChangeCallback)
```

�Զ���Tabsҳ���л������¼���������ҳ�漴����ʾʱ�����ûص���

����������һ���������ɴ������¼���

1������TabContent�л���ҳ��ʱ������

2��ͨ��TabsController.[changeIndex](arkts-arkui-tabscontroller-c.md#changeIndex-1)�ӿ��л���ҳ��ʱ������

3��ͨ����̬�޸�index����ֵ�л���ҳ��ʱ������

4��ͨ�����TabBarҳǩ�л���ҳ��ʱ������

5��TabBarҳǩ�񽹺�ͨ���������ҷ�������л���ҳ��ʱ������

> **˵����**

> ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | OnTabsContentWillChangeCallback | 是 | �Զ���Tabsҳ���л������¼���������ҳ�漴����ʾʱ�����Ļص��� [since 18] |

## onGestureSwipe

```TypeScript
onGestureSwipe(handler: OnTabsGestureSwipeCallback)
```

��ҳ����ֻ��������У���֡�����ûص���

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | OnTabsGestureSwipeCallback | 是 | ��ҳ����ֻ��������У���֡�����Ļص��� [since 18] |

## onSelected

```TypeScript
onSelected(event: Callback<number>)
```

��ѡ��Ԫ�ظı�ʱ�����ûص�������ֵΪ��ǰѡ�е�Ԫ�ص�����ֵ��

����������һ���������ɴ������¼���

1. ��������ʱ���㷭ҳ��ֵ����ʼ�л�����ʱ������

2. ͨ��[TabsController������](arkts-arkui-tabs-tabscontroller-c.md#TabsController)����[changeIndex](arkts-arkui-tabscontroller-c.md#changeIndex-1)�ӿڣ���ʼ�л�����ʱ������

3. ��̬�޸�[״̬����](../../../../ui/state-management/arkts-state.md)�����index����ֵ�󴥷���

4. ͨ��ҳǩ�����������

> **˵����**

> onSelected�ص��в���ͨ��[TabsOptions](arkts-arkui-tabs-tabsoptions-i.md#TabsOptions)��index���õ�ǰ��ʾҳ�����������ɵ���TabsController.changeIndex()������

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | 是 | ��ǰѡ��Ԫ�ص������� |

## onTabBarClick

```TypeScript
onTabBarClick(event: Callback<number>)
```

Tabҳǩ����󴥷����¼���

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | 是 | �������index������������0��ʼ���㡣 [since 18] |

## onUnselected

```TypeScript
onUnselected(event: Callback<number>)
```

��ѡ��Ԫ�ظı�ʱ�����ûص�������ֵΪ��Ҫ���ص�Ԫ�ص�����ֵ��

����������һ���������ɴ������¼���

1. ��������ʱ���㷭ҳ��ֵ����ʼ�л�����ʱ������

2. ͨ��[TabsController������](arkts-arkui-tabs-tabscontroller-c.md#TabsController)����[changeIndex](arkts-arkui-tabscontroller-c.md#changeIndex-1)�ӿڣ���ʼ�л�����ʱ������

3. ��̬�޸�[״̬����](../../../../ui/state-management/arkts-state.md)�����index����ֵ�󴥷���

4. ͨ��ҳǩ�����������

> **˵����**

> onUnselected�ص��в���ͨ��TabsOptions��index���õ�ǰ��ʾҳ�����������ɵ���TabsController.changeIndex()������

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | 是 | ��Ҫ����Ԫ�ص������� |

## pageFlipMode

```TypeScript
pageFlipMode(mode: Optional<PageFlipMode>)
```

���������ַ�ҳģʽ��

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | Optional&lt;PageFlipMode&gt; | 是 | �����ַ�ҳģʽ��<br/>Ĭ��ֵ��PageFlipMode.CONTINUOUS |

## scrollable

```TypeScript
scrollable(value: boolean)
```

�����Ƿ����ͨ������ҳ�����ҳ���л���

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | �Ƿ����ͨ������ҳ�����ҳ���л���<br/>Ĭ��ֵ��true������ͨ������ҳ�����ҳ���л���Ϊfalseʱ���ɻ����л�ҳ�档 |

## vertical

```TypeScript
vertical(value: boolean)
```

�����Ƿ�Ϊ����Tabs��

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | �Ƿ�Ϊ����Tabs��<br/>Ĭ��ֵ��false������Tabs��Ϊtrueʱ����Tabs��<br/>������Tabs����heightΪautoʱ��Tabs����߶�����Ӧ�������<br/>�ȣ���Ϊ[tabBar](TabContentAttribute#tabBar(options: string \| Resource \| CustomBuilder \| TabBarOptions))�߶�+<br/>divider�߿�+TabContent�߶�+����paddingֵ+����border���ȡ�<br/>������Tabs����widthΪautoʱ��Tabs�����������Ӧ��������ȣ���ΪtabBar����+divider�߿�+<br/>TabContent����+����paddingֵ+����border���ȡ�<br/>��������ÿһ��ҳ���е�������ߴ��Сһ�£����⻬��ҳ��ʱ����ҳ���л������������� |

