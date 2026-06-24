# replace

## replace

```TypeScript
function replace(options: RouterOptions): void
```

��Ӧ���ڵ�ĳ��ҳ���滻��ǰҳ�棬�����ٱ��滻��ҳ�档

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [replaceUrl](arkts-arkui-router-c.md#replaceUrl-2)�����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** replaceUrl(options:

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RouterOptions | 是 | �滻ҳ��������Ϣ�� |

**示例：**

```TypeScript
class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replace({
  url: 'pages/detail',
  params: new RouterParams('message')
});

```

