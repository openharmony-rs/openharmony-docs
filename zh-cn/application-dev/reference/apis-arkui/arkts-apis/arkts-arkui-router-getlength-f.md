# getLength

## getLength

```TypeScript
function getLength(): string
```

��ȡ��ǰ��ҳ��ջ�ڵ�ҳ��������

> **˵����**
>
> - ��API version 8��ʼ֧�֣���API version 18��ʼ����������ʹ��[getLength](arkts-arkui-router-c.md#getLength-1)�����
> getLength����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 8

**废弃版本：** 18

**替代接口：** [getLength](arkts-arkui-router-c.md#getLength-1)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ҳ��������ҳ��ջ֧�������ֵ��32�� |

**示例：**

```TypeScript
let size = this.getUIContext().getRouter().getLength();
console.info('pages stack size = ' + size);

```

