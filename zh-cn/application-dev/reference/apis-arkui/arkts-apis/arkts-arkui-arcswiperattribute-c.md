# ArcSwiperAttribute

��֧��[ͨ������](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)�⣬��֧���������ԡ�

**继承/实现关系：** ArcSwiperAttribute extends [CommonMethod<ArcSwiperAttribute>](CommonMethod<ArcSwiperAttribute>)

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## customContentTransition

```TypeScript
customContentTransition(transition: Optional<SwiperContentAnimatedTransition>): ArcSwiperAttribute
```

�Զ���ArcSwiperҳ���л���������ҳ����ֻ��������ֺ�ִ���л������Ĺ����У�����Ӵ�������ҳ����֡�����ص��������߿����ڻص�������͸���ȡ����ű�����λ�Ƶ��������Զ����л�������

��ҳ����ֻ��������ֺ�ִ���л������Ĺ����У�����Ӵ�������ҳ����֡����[SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md#SwiperContentTransitionProxy)�ص������磬���Ӵ������±�Ϊ
0��1������ҳ��ʱ����ÿ֡��������indexֵ�ֱ�Ϊ0��1�Ļص���

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transition | Optional&lt;SwiperContentAnimatedTransition&gt; | 是 | ArcSwiper�Զ����л����������Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcSwiperAttribute
```

������ת���ڵ������ȡ�

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | Optional&lt;CrownSensitivity&gt; | 是 | ��ת���ڵ������ȡ�<br/>Ĭ��ֵ��CrownSensitivity.MEDIUM |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## disableSwipe

```TypeScript
disableSwipe(disabled: Optional<boolean>): ArcSwiperAttribute
```

�Ƿ������������л����ܡ�

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | Optional&lt;boolean&gt; | 是 | �Ƿ������������л����ܡ�����Ϊtrue���ã�false�����á�<br/>Ĭ��ֵ��false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## disableTransitionAnimation

```TypeScript
disableTransitionAnimation(disabled: Optional<boolean>): ArcSwiperAttribute
```

�Ƿ�ر����⶯ЧЧ����

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | Optional&lt;boolean&gt; | 是 | �Ƿ�ر����⶯ЧЧ����<br/>true���ر����⶯ЧЧ����false�����ر����⶯ЧЧ����<br/>��������Ƿ�ʱ����false������ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## duration

```TypeScript
duration(duration: Optional<number>): ArcSwiperAttribute
```

����������л��Ķ���ʱ����

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | Optional&lt;number&gt; | 是 | ������л��Ķ���ʱ����<br/>Ĭ��ֵ��400<br/>��λ������ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## effectMode

```TypeScript
effectMode(edgeEffect: Optional<EdgeEffect>): ArcSwiperAttribute
```

���ñ�Ե����Ч���� Ŀǰ֧�ֵĻ���Ч���μ�[EdgeEffect](arkts-arkui-enums-edgeeffect-e.md#EdgeEffect)�ġ����ÿ������ӿ�ʱ�ص�����Ч��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| edgeEffect | Optional&lt;EdgeEffect&gt; | 是 | ��Ե����Ч����<br/>Ĭ��ֵ��EdgeEffect.Spring |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## index

```TypeScript
index(index: Optional<number>): ArcSwiperAttribute
```

���õ�ǰ����������ʾ�������������ֵ������С��0����ڵ������������ʱ������Ĭ��ֵ0������

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | Optional&lt;number&gt; | 是 | ��ǰ����������ʾ�������������ֵ��<br/>��indexֵΪundefinedʱ����ȡֵΪ0������ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## indicator

```TypeScript
indicator(style: Optional<ArcDotIndicator | boolean>): ArcSwiperAttribute
```

���û���Բ��ָʾ����ʽ��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | Optional&lt;ArcDotIndicator \| boolean&gt; | 是 | ����Բ��ָʾ����ʽ��<br/>- ArcDotIndicator������Բ��ָʾ�����Լ����ܡ�<br/>-<br/>boolean���Ƿ����û���Բ��ָʾ��������Ϊtrue���ã�false�����á�<br/>Ĭ��ֵ��true<br/>Ĭ�����ͣ�ArcDotIndicator |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## onAnimationEnd

```TypeScript
onAnimationEnd(handler: Optional<AnimationEndHandler>): ArcSwiperAttribute
```

�л���������ʱ�����ûص���

��ArcSwiper�л���Ч����ʱ�������������������������жϣ�ͨ��[SwiperController](arkts-arkui-swiper-swipercontroller-c.md#SwiperController)����finishAnimation������Ϊ�����������indexֵ������
ArcSwiperʱ��indexΪ����������������

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;AnimationEndHandler&gt; | 是 | �л���������ʱ�����ûص��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## onAnimationStart

```TypeScript
onAnimationStart(handler: Optional<AnimationStartHandler>): ArcSwiperAttribute
```

�л�������ʼʱ�����ûص���

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;AnimationStartHandler&gt; | 是 | �л�������ʼʱ�Ļص��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## onChange

```TypeScript
onChange(handler: Optional<IndexChangedHandler>): ArcSwiperAttribute
```

��ǰ��ʾ������������仯ʱ�������¼�������ֵΪ��ǰ��ʾ�����������ֵ��

ArcSwiper������[LazyForEach](../../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)ʹ��ʱ��������onChange�¼���
������ҳ��UI��ˢ�¡�

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;IndexChangedHandler&gt; | 是 | ��ǰ��ʾԪ�ص������ص��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## onGestureSwipe

```TypeScript
onGestureSwipe(handler: Optional<GestureSwipeHandler>): ArcSwiperAttribute
```

��ҳ����ֻ��������У���֡�����ûص���

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;GestureSwipeHandler&gt; | 是 | ��ҳ����ֻ��������У���֡�����ûص��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## vertical

```TypeScript
vertical(isVertical: Optional<boolean>): ArcSwiperAttribute
```

�����Ƿ�Ϊ���򻬶���

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isVertical | Optional&lt;boolean&gt; | 是 | �Ƿ�Ϊ���򻬶���<br/>true: ���򻬶���false: ���򻬶���<br/>Ĭ��ֵ��false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

