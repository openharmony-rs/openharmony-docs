# TabsOptions

Tabs�������������Tabs��ҳǩλ�ã���ǰ��ʾҳǩ��������Tabs��������TabBar��[ͨ������](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)��

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barModifier

```TypeScript
barModifier?: CommonModifier
```

����TabBar��[ͨ������](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)��

**˵����**

��̬��Ϊundefinedʱ�ᱣ�ֵ�ǰ״̬���䣬�������ø�ͨ�����ԡ�

��һ��CommonModifier�л�Ϊ��һ��CommonModifierʱ���ظ����Ի���и��ǣ����ظ����Ի�ͬʱ��Ч����������ǰһ��CommonModifier��ͨ�����ԡ�

Tabs��[barWidth](TabsAttribute#barWidth)��[barHeight](TabsAttribute#barHeight(value: Length))��
[barBackgroundColor](TabsAttribute#barBackgroundColor)��
[barBackgroundBlurStyle](TabsAttribute#barBackgroundBlurStyle(style: BlurStyle, options: BackgroundBlurStyleOptions))
��[barBackgroundEffect](TabsAttribute#barBackgroundEffect)���ԻḲ��CommonModifier��
[width](arkts-arkui-commonmethod-c.md#width-1)��[height](arkts-arkui-commonmethod-c.md#height-1)��
[backgroundColor](arkts-arkui-commonmethod-c.md#backgroundColor-2)��
[backgroundBlurStyle](arkts-arkui-commonmethod-c.md#backgroundBlurStyle-2)
��[backgroundEffect](arkts-arkui-commonmethod-c.md#backgroundEffect-2)���ԡ�

[align](arkts-arkui-commonmethod-c.md#align-1)���Խ���
[BarMode.Scrollable](TabsAttribute#barMode(value: BarMode.Scrollable, options: ScrollableBarModeOptions))ģʽ����
Ч����TabsΪ����ʱ����[nonScrollableLayoutStyle](arkts-arkui-tabs-scrollablebarmodeoptions-i.md#ScrollableBarModeOptions)δ���û�����Ϊ�쳣ֵʱ������Ч��

[TabContent](arkts-arkui-tabcontent.md)�����
[tabBar](TabContentAttribute#tabBar(content: ComponentContent | SubTabBarStyle | BottomTabBarStyle | string | Resource | CustomBuilder | TabBarOptions))
����Ϊ�ײ�ҳǩ��ʽʱ��֧����ק���ܡ�

**类型：** CommonModifier

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barPosition

```TypeScript
barPosition?: BarPosition
```

����Tabs��ҳǩλ�á�

Ĭ��ֵ��BarPosition.Start��

**类型：** BarPosition

**默认值：** BarPosition.Start [since 11]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TabsController
```

����Tabs��������

**类型：** TabsController

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index?: number
```

���õ�ǰ��ʾҳǩ��������

Ĭ��ֵ��0

**˵����**

����ΪС��0��ֵʱ��Ĭ��ֵ��ʾ��

��ѡֵΪ[0, TabContent�ӽڵ�����-1]��

ֱ���޸�index��ҳʱ���л���Ч����Ч�� ʹ��TabController��[changeIndex](arkts-arkui-tabscontroller-c.md#changeIndex-1)ʱ��Ĭ����Ч�л���Ч����������
[animationDuration](TabsAttribute#animationDuration)Ϊ0�رն�����

��API version 10��ʼ���ò���֧��[$$](../../../../ui/state-management/arkts-two-way-sync.md)˫��󶨱�����

Tabs�ؽ���ϵͳ��Դ�л�����ϵͳ�����л���ϵͳ��ǳɫ�л�������������Ա仯ʱ������ת��index��Ӧ��ҳ�档����Ҫ����������²���ת������ʹ��˫��󶨡�

**类型：** number

**默认值：** 0 [since 11]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

