# TabContentAnimatedTransition

Tabs�Զ����л����������Ϣ��

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timeout

```TypeScript
timeout?: number
```

Tabs�Զ����л�������ʱʱ�䡣���Զ��嶯����ʼ�л���ʱ����������ʱ��󣬿�������δ����[TabContentTransitionProxy](arkts-arkui-tabs-tabcontenttransitionproxy-i.md#TabContentTransitionProxy)��
finishTransition�ӿ�֪ͨTabs����Զ��嶯����������ô����ͻ���Ϊ�˴��Զ��嶯���ѽ�����ֱ��ִ�к���������

Ĭ��ֵ��1000

��λ��ms

ȡֵ��Χ��[0, +��)��

**类型：** number

**默认值：** 1000 ms

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition: Callback<TabContentTransitionProxy>
```

�Զ����л������������ݡ�

**类型：** Callback<TabContentTransitionProxy>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

