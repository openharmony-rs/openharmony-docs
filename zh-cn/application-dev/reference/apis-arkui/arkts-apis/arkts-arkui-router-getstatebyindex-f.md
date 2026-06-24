# getStateByIndex

## getStateByIndex

```TypeScript
function getStateByIndex(index: number): RouterState | undefined
```

ͨ������ֵ��ȡ��Ӧҳ���״̬��Ϣ��

> **˵����**
>
> - ��API version 12��ʼ֧�֣���API version 18��ʼ����������ʹ��
> [getStateByIndex](arkts-arkui-router-c.md#getStateByIndex-1)�����getStateByIndex����ͨ��
> [UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 12��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 12

**废弃版本：** 18

**替代接口：** [getStateByIndex](arkts-arkui-router-c.md#getStateByIndex-1)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | ��ʾҪ��ȡ��ҳ����������ջ�׵�ջ����index��1��ʼ������ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RouterState | State information about the target page; **undefined** if the specified index<br/>does not exist. |

**示例：**

```TypeScript
let options: router.RouterState | undefined = router.getStateByIndex(1);
if (options != undefined) {
  console.info('index = ' + options.index);
  console.info('name = ' + options.name);
  console.info('path = ' + options.path);
  console.info(`params = ${JSON.stringify(options.params)}`);
}

```

