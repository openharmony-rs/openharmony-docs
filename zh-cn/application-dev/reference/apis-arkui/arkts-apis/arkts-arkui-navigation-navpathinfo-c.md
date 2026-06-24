# NavPathInfo

·��ҳ����Ϣ��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(name: string, param: unknown, onPop?: import('../api/@ohos.base').Callback<PopInfo>, isEntry?: boolean)
```

����NavPathInfo����

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ�������ƥ�俪�������õ�·�ɱ��е�name�������������֣�<br/>1. �Զ���·�ɱ���������ͨ��<br/>[navDestination](NavigationAttribute#navDestination)�������ݡ�<br/>2. ϵͳ·�ɱ���ͨ��routerMap�е�name���ã��ɲο�<br/>[ʾ��2](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#ʾ��2ʹ�õ�������������)�� |
| param | unknown | 是 | ���������õ�NavDestinationҳ����ϸ������unknown�������û��Զ�������͡� |
| onPop | import('../api/@ohos.base').Callback&lt;PopInfo&gt; | 否 | NavDestinationҳ�津��<br/>[pop](NavPathStack#pop(result: Object, animated?: boolean))��<br/>[popToName](arkts-arkui-navpathstack-c.md#popToName-2)��<br/>[popToIndex](arkts-arkui-navpathstack-c.md#popToIndex-2)ʱ���صĻص�����<br/>[pop](NavPathStack#pop(result: Object, animated?: boolean))��<br/>[popToName](arkts-arkui-navpathstack-c.md#popToName-2)��<br/>[popToIndex](arkts-arkui-navpathstack-c.md#popToIndex-2)������result������<br/>���� [since 11] |
| isEntry | boolean | 否 | ���NavDestination�Ƿ�Ϊ���ҳ�档<br/>true��NavDestination�����ҳ�棻false��NavDestination�������ҳ�档Ĭ��ֵ��false<br/>�������ʱ����1. �ڵ�ǰnavDestinationҳ�津��һ��ȫ�ַ����¼���2. Ӧ��������̨��<br/>**˵����**<br/>���NavDestination����ӦӦ���ڵ�ȫ��<br/>back�¼���ֱ�Ӵ���Ӧ�ü��ȫ��back�¼��� [since 12] |

## isEntry

```TypeScript
isEntry?: boolean
```

���NavDestination�Ƿ�Ϊ���ҳ�档

true��NavDestination�����ҳ�棻false��NavDestination�������ҳ�档

Ĭ��ֵ��false

�������ʱ����1. �ڵ�ǰnavDestinationҳ�津��һ��ȫ��back�¼���2. Ӧ��������̨��

**˵����**

���NavDestination����ӦӦ���ڵ�ȫ��back�¼���ֱ�Ӵ���Ӧ�ü��ȫ��back�¼���

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

NavDestinationҳ�����ơ�������ƥ�俪�������õ�·�ɱ��е�name�������������֣�

1. �Զ���·�ɱ���������ͨ��[navDestination](NavigationAttribute#navDestination)�������ݡ�
2. ϵͳ·�ɱ���ͨ��routerMap�е�name���ã��ɲο�[ʾ��2](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#ʾ��2ʹ�õ�������������)��

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestinationId

```TypeScript
navDestinationId?: string
```

NavDestinationҳ��Ψһ��ʶ������id��ϵͳĬ��������ȫ��Ψһ��ͨ��[getPathStack](arkts-arkui-navpathstack-c.md#getPathStack-1)�ӿڿɶ�ȡ������������������ֵ��

**类型：** string

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPop

```TypeScript
onPop?: import('../api/@ohos.base').Callback<PopInfo>
```

NavDestinationҳ�津��[pop](NavPathStack#pop(result: Object, animated?: boolean))��
[popToName](arkts-arkui-navpathstack-c.md#popToName-2)��
[popToIndex](arkts-arkui-navpathstack-c.md#popToIndex-2)ʱ���صĻص�����
[pop](NavPathStack#pop(result: Object, animated?: boolean))��
[popToName](arkts-arkui-navpathstack-c.md#popToName-2)��
[popToIndex](arkts-arkui-navpathstack-c.md#popToIndex-2)������result�����󴥷���

**类型：** import('../api/@ohos.base').Callback<PopInfo>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## param

```TypeScript
param?: unknown
```

���������õ�NavDestinationҳ����ϸ������unknown�������û��Զ�������͡�

**类型：** unknown

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

