# NavRouter属性/事件

��֧��[ͨ������](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)�⣬��֧���������ԣ�

**继承/实现关系：** NavRouterAttribute extends [CommonMethod<NavRouterAttribute>](CommonMethod<NavRouterAttribute>)

**起始版本：** 9

**废弃版本：** 13

**替代接口：** NavPathStack

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode(mode: NavRouteMode)
```

����ָ�����NavRouter��ת��NavDestinationҳ��ʱ��ʹ�õ�·��ģʽ��

**起始版本：** 10

**废弃版本：** 13

**替代接口：** LaunchMode

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | NavRouteMode | 是 | ָ�����NavRouter��ת��NavDestinationҳ��ʱ��ʹ�õ�·��ģʽ��<br/>Ĭ��ֵ��NavRouteMode.PUSH_WITH_RECREATE |

## onStateChange

```TypeScript
onStateChange(callback: (isActivated: boolean) => void)
```

�������״̬�л�ʱ�����ûص��������ߵ������NavRouter�����ض�Ӧ��NavDestination�����ʱ���ص�onStateChange(true)��NavRouter��Ӧ��NavDestination�����������ʾʱ���ص�
onStateChange(false)��

**起始版本：** 9

**废弃版本：** 13

**替代接口：** onShown

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (isActivated: boolean) =&gt; void | 是 | isActivatedΪtrueʱ��ʾ���Ϊfalseʱ��ʾδ��� |

