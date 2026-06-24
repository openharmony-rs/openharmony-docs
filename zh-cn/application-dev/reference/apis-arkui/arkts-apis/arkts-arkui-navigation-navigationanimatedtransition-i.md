# NavigationAnimatedTransition

�Զ���ת������Э�飬��������ʵ�ָ�Э��������Navigation·����ת����ת������

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isInteractive

```TypeScript
isInteractive?: boolean
```

����ת�������Ƿ�Ϊ�ɽ���ת����

true������ת�������ǿɽ���ת����false������ת���������ǿɽ���ת����

Ĭ��ֵ��false

**类型：** boolean

**默认值：** false

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTransitionEnd

```TypeScript
onTransitionEnd?: (success: boolean) => void
```

ת����ɻص���

success��ת���Ƿ�ɹ���

**类型：** (success: boolean) => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timeout

```TypeScript
timeout?: number
```

������ʱ����ʱ�䡣

��λ��ms��

ȡֵ��Χ��[0, +��)��

Ĭ��ֵ���ɽ���������Ĭ��ֵ�����ɽ�������Ĭ�ϳ�ʱʱ��Ϊ1000ms��

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition: (transitionProxy: NavigationTransitionProxy) => void
```

�Զ���ת������ִ�лص���

transitionProxy���Զ���ת��������������

**类型：** (transitionProxy: NavigationTransitionProxy) => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

