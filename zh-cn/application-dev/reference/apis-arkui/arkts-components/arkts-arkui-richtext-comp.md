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

示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

```TypeScript
// xxx.ets
@Entry
@Component
struct RichTextExample {
  @State data: string = '<h1 style="text-align: center;">h1标题</h1>' +
  '<h1 style="text-align: center;"><i>h1斜体</i></h1>' +
  '<h1 style="text-align: center;"><u>h1下划线</u></h1>' +
  '<h2 style="text-align: center;">h2标题</h2>' +
  '<h3 style="text-align: center;">h3标题</h3>' +
  '<p style="text-align: center;">p常规</p><hr/>' +
  '<div style="width: 500px;height: 500px;border: 1px solid;margin: 0 auto;">' +
  '<p style="font-size: 35px;text-align: center;font-weight: bold; color: rgb(24,78,228)">字体大小35px,行高45px</p>' +
  '<p style="background-color: #e5e5e5;line-height: 45px;font-size: 35px;text-indent: 2em;">' +
  '<p>这是一段文字这是一段文字这是一段文字这是一段文字这是一段文字这是一段文字这是一段文字这是一段文字这是一段文字</p>';

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center,
      justifyContent: FlexAlign.Center }) {
      RichText(this.data)
        .onStart(() => {
          console.info('RichText onStart');
        })
        .onComplete(() => {
          console.info('RichText onComplete');
        })
        .width(500)
        .height(500)
        .backgroundColor(0XBDDB69)
      RichText('layoutWeight(1)')
        .onStart(() => {
          console.info('RichText onStart');
        })
        .onComplete(() => {
          console.info('RichText onComplete');
        })
        .size({ width: '100%', height: 110 })
        .backgroundColor(0X92D6CC)
        .layoutWeight(1)
      RichText('layoutWeight(2)')
        .onStart(() => {
          console.info('RichText onStart');
        })
        .onComplete(() => {
          console.info('RichText onComplete');
        })
        .size({ width: '100%', height: 110 })
        .backgroundColor(0X92C48D)
        .layoutWeight(2)
    }
  }
}
```



加载本地资源文件。

通过$rawfile方式加载。

```TypeScript
// xxx.ets
@Entry
@Component
struct RichTextComponent {

  build() {
    Column() {
      // 通过$rawfile加载本地资源文件。
      RichText($rawfile("index.html"))
    }
  }
}
```

通过resource协议加载，适用Webview加载带有"#"路由的链接。

使用  协议前缀可以避免常规  方式在处理带有"#"路由链接时的局限性。当URL中包含"#"号时，"#"后面的内容会被视为锚点（fragment）。

```TypeScript
// xxx.ets
@Entry
@Component
struct RichTextComponent {

  build() {
    Column() {
      // 通过resource协议加载本地资源文件。
      RichText("resource://rawfile/index.html#home")
    }
  }
}
```

在“srcmainresourcesrawfile”文件夹下创建index.html：

加载的html文件。

```TypeScript
<!-- index.html -->
<!DOCTYPE html>
<html>
    <body>
        <p>Hello World</p>
    </body>
</html>
```
