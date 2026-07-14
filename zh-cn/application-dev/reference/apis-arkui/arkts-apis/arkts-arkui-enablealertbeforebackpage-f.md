# enableAlertBeforeBackPage

## enableAlertBeforeBackPage

```TypeScript
function enableAlertBeforeBackPage(options: EnableAlertOptions): void
```

开启页面返回询问对话框。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用
> [showAlertBeforeBackPage](arkts-arkui-router-c.md#showalertbeforebackpage-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [showAlertBeforeBackPage](arkts-arkui-router-c.md#showalertbeforebackpage-1)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | EnableAlertOptions | 是 | 文本弹窗信息描述。 |

**示例：**

```TypeScript
router.enableAlertBeforeBackPage({
  message: 'Message Info'
});

```

