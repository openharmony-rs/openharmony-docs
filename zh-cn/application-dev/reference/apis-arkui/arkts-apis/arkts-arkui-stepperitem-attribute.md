# StepperItem属性/事件

**继承/实现关系：** StepperItemAttribute extends [CommonMethod<StepperItemAttribute>](CommonMethod<StepperItemAttribute>)

**起始版本：** 8

**废弃版本：** 22

**替代接口：** SwiperAttribute

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## nextLabel

```TypeScript
nextLabel(value: string)
```

�����Ҳ��ı���ť���ݣ����һҳĬ��ֵΪ����ʼ��������ҳĬ��ֵΪ����һ������

> **˵����**

> ��API version 8��ʼ֧�֣���API version 22��ʼ����������ʹ��[showNext](arkts-arkui-swipercontroller-c.md#showNext-1)�����

**起始版本：** 8

**废弃版本：** 22

**替代接口：** showNext

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | �Ҳ��ı���ť���ݡ��ַ�������ʱ������С�ٻ��У�2�У����ضϡ� |

## prevLabel

```TypeScript
prevLabel(value: string)
```

��������ı���ť���ݣ���һҳû������ı���ť�������赼��������һҳʱ������һҳ��Ĭ��ֵ��Ϊ�����ء���

> **˵����**

> ��API version 8��ʼ֧�֣���API version 22��ʼ����������ʹ��[showPrevious](arkts-arkui-swipercontroller-c.md#showPrevious-1)�����

**起始版本：** 8

**废弃版本：** 22

**替代接口：** showPrevious

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | ����ı���ť���ݡ��ַ�������ʱ������С�ٻ��У�2�У����ضϡ� |

## status

```TypeScript
status(value?: ItemState)
```

���ò��赼����nextLabel����ʾ״̬��

> **˵����**

> ��API version 8��ʼ֧�֣���API version 22��ʼ����������ʹ��[indicatorInteractive](SwiperAttribute#indicatorInteractive)�����

**起始版本：** 8

**废弃版本：** 22

**替代接口：** indicatorInteractive

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ItemState | 否 | ���赼����nextLabel����ʾ״̬��<br/>Ĭ��ֵ��ItemState.Normal |

