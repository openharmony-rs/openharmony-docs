# MultiNavigation

MultiNavigation�����ڴ�ߴ��豸�Ϸ�����ʾ������·����ת��

> **˵����**

> ����MultiNavigation���ڶ���ջǶ�ף����ñ��ĵ���ȷ˵���Ĳ�֧�ֽӿڻ��ڱ��ĵ�֧�ֽӿ��б��еĽӿ�(����[getParent](arkts-arkui-navpathstack-c.md#getParent-1)��
> [setInterception](arkts-arkui-navpathstack-c.md#setInterception-1)��
> [pushDestination](arkts-arkui-navpathstack-c.md#pushDestination-1)��)�����ܻᷢ���޷�Ԥ�ڵ����⡣

> MultiNavigation�����Ƕ�׳����£����ܴ���·�ɶ�Ч�쳣�����⡣

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## multiStack

```TypeScript
multiStack: MultiNavPathStack
```

����·��ջ��

**类型：** MultiNavPathStack

**起始版本：** 14

**装饰器类型：** @State

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestination

```TypeScript
navDestination: NavDestinationBuildFunction
```

���ü���Ŀ��ҳ���·�ɹ���

**类型：** NavDestinationBuildFunction

**起始版本：** 14

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHomeShowOnTop

```TypeScript
onHomeShowOnTop?: OnHomeShowOnTopCallback
```

������ҳ����ջ��ʱ�Ļص���

**类型：** OnHomeShowOnTopCallback

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onNavigationModeChange

```TypeScript
onNavigationModeChange?: OnNavigationModeChangeCallback
```

����MultiNavigationģʽ���ʱ�Ļص���

**类型：** OnNavigationModeChangeCallback

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

