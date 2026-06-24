# NavigationTransitionProxy

�Զ���ת��������������

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancelTransition

```TypeScript
cancelTransition?(): void
```

ȡ�����ν���ת�����ָ���ҳ����תǰ��·��ջ(��֧��ȡ�����ɽ���ת������)��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## finishTransition

```TypeScript
finishTransition(): void
```

���������Զ���ת����������������Ҫ���������÷�������������ת��������ϵͳ����timeout��ʱ����������ת����

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updateTransition

```TypeScript
updateTransition?(progress: number): void
```

���½���ת����������(���ɽ���������֧�ֶ�����������)��

> **˵����**
>
> ��������[aboutToAppear](arkts-arkui-basecustomcomponent-c.md#aboutToAppear-1)��ʹ��ջ��������ʱ��ҳ�滹δ������ɣ��ᵼ�°�������תʧ�ܵ����⡣

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | number | 是 | ���ý���ת���������Ȱٷֱȡ�ȡֵ��Χ��[0, 1] |

## from

```TypeScript
from: NavContentInfo
```

�˳�ҳ����Ϣ��

**类型：** NavContentInfo

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

## to

```TypeScript
to: NavContentInfo
```

����ҳ����Ϣ��

**类型：** NavContentInfo

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

