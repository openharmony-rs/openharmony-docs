# LaunchMode

```TypeScript
declare enum LaunchMode
```

·��ջ����ģʽ��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## STANDARD

```TypeScript
STANDARD = 0
```

ϵͳĬ�ϵ�ջ����ģʽ��

push�����Ὣָ����NavDestination��ջ��replace�����Ὣ��ǰջ��NavDestination�滻��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MOVE_TO_TOP_SINGLETON

```TypeScript
MOVE_TO_TOP_SINGLETON = 1
```

��ջ����ջ�����ң����ָ���������Ѿ����ڣ��򽫶�Ӧ��NavDestinationҳ���Ƶ�ջ����replace�����Ὣ����ջ���滻��ָ����NavDestination����������Ϊ��STANDARDһ�¡�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## POP_TO_SINGLETON

```TypeScript
POP_TO_SINGLETON = 2
```

��ջ����ջ�����ң����ָ���������Ѿ����ڣ������Ϸ���NavDestinationҳ��ȫ���Ƴ���replace�����Ὣ����ջ���滻��ָ����NavDestination����������Ϊ��STANDARDһ�¡�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NEW_INSTANCE

```TypeScript
NEW_INSTANCE = 3
```

�����µ�NavDestinationʵ������STANDARDģʽ��ȣ��÷������Ḵ��ջ��ͬ��ʵ��������ָ����ģʽʱ���´�����ҳ��Ĭ�ϻ�ִ��push��Ч��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

