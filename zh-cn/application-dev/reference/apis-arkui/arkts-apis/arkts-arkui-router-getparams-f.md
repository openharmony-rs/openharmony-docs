# getParams

## getParams

```TypeScript
function getParams(): Object
```

��ȡ������ת��ҳ������ǰҳ����Ĳ�����

> **˵����**
>
> - ��API version 8��ʼ֧�֣���API version 18��ʼ����������ʹ��[getParams](arkts-arkui-router-c.md#getParams-1)�����
> getParams����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����
>
> getParamsֻ��ȡ��ǰҳ��Ĳ��������������ҳ������Ĳ�����

**起始版本：** 8

**废弃版本：** 18

**替代接口：** [getParams](arkts-arkui-router-c.md#getParams-1)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | ������ת��ҳ������ǰҳ����Ĳ����� |

**示例：**

```TypeScript
this.getUIContext().getRouter().getParams();

```

