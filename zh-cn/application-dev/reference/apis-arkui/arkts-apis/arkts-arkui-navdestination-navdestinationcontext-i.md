# NavDestinationContext

NavDestination��������Ϣ��

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getConfigInRouteMap

```TypeScript
getConfigInRouteMap(): RouteMapConfig | undefined
```

��ȡ��ǰNavDestination��·��������Ϣ��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RouteMapConfig | Routing configuration of the current page.<br/><br/>**undefined** is returned when the page is not configured through the route table. |

## mode

```TypeScript
mode?: NavDestinationMode
```

��ǰNavDestination�����͡�
Ĭ��ֵ��NavDestinationMode.Standard��

**类型：** NavDestinationMode

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestinationId

```TypeScript
navDestinationId?: string
```

��ǰNavDestination��ΨһID����ϵͳ�Զ����ɣ������ͨ������id�޹ء�

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pathInfo

```TypeScript
pathInfo: NavPathInfo
```

��תNavDestinationʱָ���Ĳ�����

**类型：** NavPathInfo

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pathStack

```TypeScript
pathStack: NavPathStack
```

��ǰNavDestination�����ĵ�����������

**类型：** NavPathStack

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

