# RichText

定义RichText组件。

## RichText

```TypeScript
RichText(content: string | Resource)
```

设置值。

**起始版本：** 8

**原子化服务API：** 从API版本11 - 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | 是 |  |

## 汇总

## 示例

```TypeScript
示例效果请以真机运行为准，当前DevEco Studio预览器不支持。
```

```TypeScript


加载本地资源文件。

通过$rawfile方式加载。
```

```TypeScript
通过resource协议加载，适用Webview加载带有"#"路由的链接。

使用  协议前缀可以避免常规  方式在处理带有"#"路由链接时的局限性。当URL中包含"#"号时，"#"后面的内容会被视为锚点（fragment）。
```

```TypeScript
在“srcmainresourcesrawfile”文件夹下创建index.html：

加载的html文件。
```
