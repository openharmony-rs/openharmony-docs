# Navigator属性/事件

Navigator�����ԡ�

**继承/实现关系：** NavigatorAttribute extends [CommonMethod<NavigatorAttribute>](CommonMethod<NavigatorAttribute>)

**起始版本：** 7

**废弃版本：** 13

**替代接口：** Navigation

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## active

```TypeScript
active(value: boolean)
```

���õ�ǰ·������Ƿ��ڼ���״̬�����ڼ���״̬ʱ������Ч��Ӧ��·�ɲ�����

**起始版本：** 7

**废弃版本：** 13

**替代接口：** Navigation

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | ·������Ƿ��ڼ���״̬������Ϊtrueʱ��������ڼ���̬������Ϊfalseʱ����������ڼ���̬�� |

## params

```TypeScript
params(value: object)
```

������תʱ���ݵ�Ŀ��ҳ������ݡ�

> **˵����**

**起始版本：** 7

**废弃版本：** 13

**替代接口：** [param](arkts-arkui-navpathinfo-c.md#param)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | object | 是 | ��תʱҪͬʱ���ݵ�Ŀ��ҳ������ݣ�����Ŀ��ҳ��ʹ��[router.getParams()](arkts-arkui-router-getparams-f.md#getParams-1)��á� |

## target

```TypeScript
target(value: string)
```

������תĿ��ҳ���·����Ŀ��ҳ�������main_pages.json�ļ��С�

**起始版本：** 7

**废弃版本：** 13

**替代接口：** Navigation

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | ��תĿ��ҳ���·���� |

## type

```TypeScript
type(value: NavigationType)
```

����·����ת��ʽ��

> **˵����**

**起始版本：** 7

**废弃版本：** 13

**替代接口：** Navigation

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | NavigationType | 是 | ·����ת��ʽ��<br/>Ĭ��ֵ��NavigationType.Push |

