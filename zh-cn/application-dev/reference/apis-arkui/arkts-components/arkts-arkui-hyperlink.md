# Hyperlink

超链接组件，组件宽高范围内点击实现跳转。

> **说明：**
>
> - 该组件仅支持与系统浏览器配合使用。


## Hyperlink

```TypeScript
Hyperlink(address: string | Resource, content?: string | Resource)
```

定义超链接组件构造函数。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | string \| Resource | 是 | Hyperlink组件跳转的网页。 |
| content | string \| Resource | 否 | Hyperlink组件中超链接显示文本。<br/>默认值：''。若不传该参数且组件内无子组件时，默认显示address参数值链接地址。<br/>**说明：** <br/>组件内有子组件时，不显示超链接文本。 |

## 汇总

