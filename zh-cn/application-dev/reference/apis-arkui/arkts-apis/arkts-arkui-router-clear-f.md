# clear

## clear

```TypeScript
function clear(): void
```

���ҳ��ջ�е�������ʷҳ�棬��������ǰҳ����Ϊջ��ҳ�档

> **˵����**
>
> - ��API version 8��ʼ֧�֣���API version 18��ʼ����������ʹ��[clear](arkts-arkui-router-c.md#clear-1)�����clear����ͨ��
> [UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 8

**废弃版本：** 18

**替代接口：** [clear](arkts-arkui-router-c.md#clear-1)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```TypeScript
this.getUIContext().getRouter().clear();

```

