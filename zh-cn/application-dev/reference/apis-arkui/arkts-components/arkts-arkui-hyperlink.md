# Hyperlink

超链接组件，组件宽高范围内点击实现跳转。

> **说明：**
>
> - 该组件从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 该组件仅支持与系统浏览器配合使用。

## 需要权限

跳转的目标应用使用网络时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](docroot://security/AccessToken/declare-permissions.md)。

## 子组件

可以包含[Image]{@link image}子组件。

## Hyperlink

```TypeScript
Hyperlink(address: string | Resource, content?: string | Resource)
```

定义超链接组件构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HyperlinkInterface-(address: string | Resource, content?: string | Resource): HyperlinkAttribute--><!--Device-HyperlinkInterface-(address: string | Resource, content?: string | Resource): HyperlinkAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | string \| Resource | 是 | Hyperlink组件跳转的网页。 |
| content | string \| Resource | 否 | Hyperlink组件中超链接显示文本。<br/>默认值：''。若不传该参数且组件内无子组件时，默认显示address参数值链接地址。<br/>**说明：** <br/>组件内有子组件时，不显示超链接文本。 |

## 汇总

