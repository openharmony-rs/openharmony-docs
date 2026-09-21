# RichText

Defines RichText Component.

## RichText

```TypeScript
RichText(content: string | Resource)
```

Set value.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11 - 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes |  |

## Summary

## Examples

You can preview how this component looks on a real device, but not in DevEco Studio Previewer.

```TypeScript
// xxx.ets
@Entry
@Component
struct RichTextExample {
  @State data: string = '<h1 style="text-align: center;">h1 heading</h1>' +
  '<h1 style="text-align: center;"><i>h1 italic</i></h1>' +
  '<h1 style="text-align: center;"><u>h1 underlined</u></h1>' +
  '<h2 style="text-align: center;">h2 heading</h2>' +
  '<h3 style="text-align: center;">h3 heading</h3>' +
  '<p style="text-align: center;">Regular paragraph</p><hr/>' +
  '<div style="width: 500px;height: 500px;border: 1px solid;margin: 0 auto;">' +
  '<p style="font-size: 35px;text-align: center;font-weight: bold; color: rgb(24,78,228)">Font size: 35px; line height: 45px</p>' +
  '<p style="background-color: #e5e5e5;line-height: 45px;font-size: 35px;text-indent: 2em;">' +
  '<p>This is a paragraph. This is a paragraph. This is a paragraph. This is a paragraph. This is a paragraph. This is a paragraph. This is a paragraph. This is a paragraph. This is a paragraph.</p>';

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



Loads local resource files.

Loads local resource files through $rawfile.

```TypeScript
// xxx.ets
@Entry
@Component
struct RichTextComponent {

  build() {
    Column() {
      // Load a local resource file through $rawfile.
      RichText($rawfile("index.html"))
    }
  }
}
```

Load through the resource protocol, which applies to the Webview loading links with "#" routes.

When $rawfile is used to load a URL contains a number sign (#), the content following the number sign is treated as a fragment. To avoid this issue, you can use the resource://rawfile/ protocol prefix instead. If the URL contains a number sign (#), the content following the number sign is treated as an anchor (fragment).

```TypeScript
// xxx.ets
@Entry
@Component
struct RichTextComponent {

  build() {
    Column() {
      // Load local resource files through the resource protocol.
      RichText("resource://rawfile/index.html#home")
    }
  }
}
```

Create an index.html file in src/main/resources/rawfile.

HTML file to be loaded:

```TypeScript
<!-- index.html -->
<!DOCTYPE html>
<html>
    <body>
        <p>Hello World</p>
    </body>
</html>
```
