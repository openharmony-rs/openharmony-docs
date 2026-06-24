# back

## back

```TypeScript
function back(options?: RouterOptions): void
```

������һҳ���ָ����ҳ�棬��ɾ����ǰҳ����ָ��ҳ��֮�������ҳ�档

> **˵����**
>
> - ��API version 8��ʼ֧�֣���API version 18��ʼ����������ʹ��
> [back](arkts-arkui-router-c.md#back-1)�����back����ͨ��
> [UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 8

**废弃版本：** 18

**替代接口：** back(options?:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RouterOptions | 否 | ����ҳ��������Ϣ�����в���urlָ·����תʱ�᷵�ص�ָ��url�Ľ��棬���ҳ��ջ��û��urlҳ�棬����Ӧ����������urlδ���ã��򷵻���һҳ��ҳ�治�����¹�<br/>����ҳ��ջ�����page������գ���ջ��ᱻ���ա�back�Ƿ��ؽӿڣ�url����Ϊ����ֵ"/"����Ч�������������·�ɵķ�ʽ��ת�������url��������·�ɵ����ơ� |

**示例：**

```TypeScript
this.getUIContext().getRouter().back({ url: 'pages/detail' });

```


## back

```TypeScript
function back(index: number, params?: Object): void
```

����ָ����ҳ�棬��ɾ����ǰҳ����ָ��ҳ��֮�������ҳ�档

> **˵����**
>
> - ��API version 12��ʼ֧�֣���API version 18��ʼ����������ʹ��
> [back](arkts-arkui-router-c.md#back-2)�����back����ͨ��
> [UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 12��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 12

**废弃版本：** 18

**替代接口：** back(index:

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | ��תĿ��ҳ�������ֵ�� ��ջ�׵�ջ����index��1��ʼ������ |
| params | Object | 否 | ҳ�淵��ʱЯ���Ĳ����� |

**示例：**

```TypeScript
this.getUIContext().getRouter().back(1);

```

```TypeScript
this.getUIContext().getRouter().back(1, { info: '来自Home页' }); // 携带参数返回

```

