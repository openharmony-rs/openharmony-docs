# enableAlertBeforeBackPage

## enableAlertBeforeBackPage

```TypeScript
function enableAlertBeforeBackPage(options: EnableAlertOptions): void
```

����ҳ�淵��ѯ�ʶԻ���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [showAlertBeforeBackPage](arkts-arkui-router-c.md#showAlertBeforeBackPage-1)�����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [showAlertBeforeBackPage](arkts-arkui-router-c.md#showAlertBeforeBackPage-1)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | EnableAlertOptions | 是 | �ı�������Ϣ������ |

**示例：**

```TypeScript
router.enableAlertBeforeBackPage({
  message: 'Message Info'
});

```

