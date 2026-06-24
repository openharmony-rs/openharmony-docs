# AnimationMode

```TypeScript
declare enum AnimationMode
```

���[TabBar](TabContentAttribute#tabBar(options: string | Resource | CustomBuilder | TabBarOptions))ҳǩʱ�л�
TabContent�Ķ�����ʽö�١�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTENT_FIRST

```TypeScript
CONTENT_FIRST = 0
```

�ȼ���Ŀ��ҳ���ݣ��ٿ�ʼ�л�������

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ACTION_FIRST

```TypeScript
ACTION_FIRST = 1
```

�ȿ�ʼ�л��������ټ���Ŀ��ҳ���ݣ���Ч��Ҫͬʱ��Ҫ���㣺Tabs��height��widthû�����ó�auto��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NO_ANIMATION

```TypeScript
NO_ANIMATION = 2
```

�ر�Ĭ�϶���������TabsController��[changeIndex](arkts-arkui-tabscontroller-c.md#changeIndex-1)�ӿ��л�TabContentʱ��ö��ֵ����Ч��

����ͨ������[animationDuration](TabsAttribute#animationDuration)Ϊ0ʵ�ֵ���TabsController��changeIndex�ӿ�ʱ����������

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTENT_FIRST_WITH_JUMP

```TypeScript
CONTENT_FIRST_WITH_JUMP = 3
```

�ȼ���Ŀ��ҳ���ݣ����޶�����ת��Ŀ��ҳ����������ж�����ת��Ŀ��ҳ��

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ACTION_FIRST_WITH_JUMP

```TypeScript
ACTION_FIRST_WITH_JUMP = 4
```

���޶�����ת��Ŀ��ҳ���������ж�����ת��Ŀ��ҳ��������Ŀ��ҳ���ݡ�������Ч��Ҫͬʱ��Ҫ���㣺Tabs��height��widthû�����ó�auto��

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

