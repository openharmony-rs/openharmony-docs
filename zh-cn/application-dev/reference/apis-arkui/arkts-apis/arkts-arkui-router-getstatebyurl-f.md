# getStateByUrl

## getStateByUrl

```TypeScript
function getStateByUrl(url: string): Array<RouterState>
```

ͨ��url��ȡ��Ӧҳ���״̬��Ϣ��

> **˵����**
>
> - ��API version 12��ʼ֧�֣���API version 18��ʼ����������ʹ��[getStateByUrl](arkts-arkui-router-c.md#getStateByUrl-1)��
> ����getStateByUrl����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 12��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 12

**废弃版本：** 18

**替代接口：** [getStateByUrl](arkts-arkui-router-c.md#getStateByUrl-1)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | ��ʾҪ��ȡ��Ӧҳ����Ϣ��url�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;RouterState&gt; | ҳ��״̬��Ϣ�� |

**示例：**

```TypeScript
let options: Array<router.RouterState> = router.getStateByUrl('pages/index');
for (let i: number = 0; i < options.length; i++) {
  console.info('index = ' + options[i].index);
  console.info('name = ' + options[i].name);
  console.info('path = ' + options[i].path);
  console.info('params = ' + options[i].params);
}

```

