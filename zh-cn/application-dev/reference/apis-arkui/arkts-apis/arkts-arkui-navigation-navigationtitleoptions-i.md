# NavigationTitleOptions

������ѡ�

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

����������ģ����ʽ��������ʱ�رձ���ģ��Ч����

**类型：** BlurStyle

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

����������ģ��ѡ�

**˵����**

ֻ��������backgroundBlurStyleʱ��Ч��

��������backgroundEffectͬʱʹ�á�

**类型：** BackgroundBlurStyleOptions

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

������������ɫ��������ʱΪϵͳĬ����ɫ��

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

���ñ������������԰�����ģ���뾶�����ȣ����Ͷȣ���ɫ�ȡ�

**˵����**

��������backgroundBlurStyleOptionsͬʱʹ�á�

**类型：** BackgroundEffectOptions

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barStyle

```TypeScript
barStyle?: BarStyle
```

���ñ��������ַ�ʽ��

Ĭ��ֵ��BarStyle.STANDARD

**类型：** BarStyle

**默认值：** BarStyle.STANDARD

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

�Ƿ���Ӧ��̬ͣ��

ʹ�ù���

1. ������NavigationΪȫ����С��
2. ��������ʾģʽΪ[Free](arkts-arkui-navigation-navigationtitlemode-e.md#NavigationTitleMode)ʱ���߱��������ַ�ʽΪ[STANDARD](arkts-arkui-navigation-barstyle-e.md#BarStyle)ʱ���˽ӿ�������Ч��

true����Ӧ��̬ͣ��false������Ӧ��̬ͣ��

Ĭ��ֵ��false

**类型：** boolean

**默认值：** false

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mainTitleModifier

```TypeScript
mainTitleModifier?: TextModifier
```

�����������޸�����

1. ͨ��Modifier���õ����ԻḲ��ϵͳĬ�ϵ����ԣ����Modifier������fontSize��maxFontSize��minFontSize��һ���ԣ���ϵͳ���õĴ�С������Բ���Ч���Կ����ߵ�����Ϊ׼����
2. ��������Ի����������쳣ֵ����ָ�ϵͳĬ�����ã�
3. [Free](arkts-arkui-navigation-navigationtitlemode-e.md#NavigationTitleMode)ģʽ�����������Сʱ��ԭ�л����ı�����С��Ч��ʧЧ��

**类型：** TextModifier

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## paddingEnd

```TypeScript
paddingEnd?: LengthMetrics
```

�������������ڼ�ࡣ

��֧��������һ������

1. ʹ�÷��Զ���˵�����[�˵�value](NavigationAttribute#menus(value: Array<NavigationMenuItem> | CustomBuilder))ΪArray<NavigationMenuItem>��
2. û�����Ͻǲ˵�����ʹ�÷��Զ�����⣬��[����value](NavigationAttribute#title)����ΪResourceStr��NavigationCommonTitle��

Ĭ��ֵ��

LengthMetrics.resource(`$r('sys.float.margin_right')`)

**类型：** LengthMetrics

**默认值：** LengthMetrics.resource($r('sys.float.margin_right'))

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## paddingStart

```TypeScript
paddingStart?: LengthMetrics
```

��������ʼ���ڼ�ࡣ

��֧��������һ������

1. ��ʾ����ͼ�꣬��[hideBackButton](NavigationAttribute#hideBackButton)Ϊfalse��
2. ʹ�÷��Զ�����⣬��[����value](NavigationAttribute#title)����ΪResourceStr��NavigationCommonTitle��

Ĭ��ֵ��

LengthMetrics.resource(`$r('sys.float.margin_left')`)��

**类型：** LengthMetrics

**默认值：** LengthMetrics.resource($r('sys.float.margin_left'))

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scrollEffectOptions

```TypeScript
scrollEffectOptions?: ScrollEffectOptions
```

���⻬��ģ����ʽ��

**类型：** ScrollEffectOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subTitleModifier

```TypeScript
subTitleModifier?: TextModifier
```

�ӱ��������޸�����

1. ͨ��Modifier���õ����ԻḲ��ϵͳĬ�ϵ����ԣ����Modifier������fontSize��maxFontSize��minFontSize��һ���ԣ���ϵͳ���õĴ�С������Բ���Ч���Կ����ߵ�����Ϊ׼����
2. ��������Ի����������쳣ֵ����ָ�ϵͳĬ�����á�

**类型：** TextModifier

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: Material
```

Ϊ����������ϵͳ��ʽ�Ĳ��ʡ���ͬ�Ĳ����в�ͬ��Ч������Ӱ��
titleBar�ı�����ɫ���߿���Ӱ�������Ӿ����ԡ�
�豸��Ϊ���죺��ͬ�����ڲ�ͬ�豸�ϵ�Ч�����ܲ�ͬ������ȡ����
���ǵļ���������

**类型：** Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

