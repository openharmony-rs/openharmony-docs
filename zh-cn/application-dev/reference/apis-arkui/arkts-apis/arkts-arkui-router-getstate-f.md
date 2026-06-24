# getState

## getState

```TypeScript
function getState(): RouterState
```

��ȡջ��ҳ���״̬��Ϣ��

> **˵����**
>
> - ��API version 8��ʼ֧�֣���API version 18��ʼ����������ʹ��[getState](arkts-arkui-router-c.md#getState-1)�����getLength��
> ��ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 8

**废弃版本：** 18

**替代接口：** [getState](arkts-arkui-router-c.md#getState-1)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RouterState | ҳ��״̬��Ϣ�� |

**示例：**

```TypeScript
let page = this.getUIContext().getRouter().getState();
console.info('current index = ' + page.index);
console.info('current name = ' + page.name);
console.info('current path = ' + page.path);

```

