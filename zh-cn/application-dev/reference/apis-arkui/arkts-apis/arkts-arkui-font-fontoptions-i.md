# FontOptions

注册的自定义字体信息。

> **说明：**
> 
> 直接使用font可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，推荐通过使用
> [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的
> getFont方法获取当前UI上下文关联的
> [Font](arkts-arkui-arkui-uicontext-uicontext-c.md)对象。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { font } from '@kit.ArkUI';
```

## familyName

```TypeScript
familyName: string | Resource
```

设置注册的字体名称。

**类型：** string \| Resource

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## familySrc

```TypeScript
familySrc: string | Resource
```

设置注册字体文件的路径。  
**说明：**读取系统沙箱路径内的资源时，建议使用file://路径前缀的字符串，需要确保沙箱目录路径下的文件存在并且有可读权限。

**类型：** string \| Resource

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct FontExample {
  @State message: string = 'Hello World';
  // iconFont示例，假设0000为指定icon的Unicode，实际需要开发者从注册的iconFont的ttf文件里面获取Unicode
  @State unicode: string = '\u0000';
  @State codePoint: string = String.fromCharCode(0x0000);
  private uiContext: UIContext = this.getUIContext();

  aboutToAppear() {
    // familyName和familySrc都支持系统Resource
    this.uiContext.getFont().registerFont({
      // 建议使用 this.getUIContext().getFont().registerFont()接口
      // 'app.string.font_name'和'app.string.font_src'仅作示例，请替换为实际使用资源字符串
      familyName: $r('app.string.font_name'),
      familySrc: $r('app.string.font_src')
    });

    // familySrc支持RawFile
    this.uiContext.getFont().registerFont({
      familyName: 'mediumRawFile',
      familySrc: $rawfile('font/medium.ttf') // 'font/medium.ttf'仅作示例，请替换为实际使用资源字体文件
    });

    // 注册iconFont
    this.uiContext.getFont().registerFont({
      familyName: 'iconFont',
      familySrc: '/font/iconFont.ttf'
    });

    // familyName和familySrc都支持string
    this.uiContext.getFont().registerFont({
      familyName: 'medium',
      familySrc: '/font/medium.ttf' // font文件夹与pages目录同级
    });
  }

  build() {
    Column() {
      Text(this.message)
        .align(Alignment.Center)
        .fontSize(20)
        .fontFamily('medium') // medium：注册自定义字体的名字（$r('app.string.font_name')、'mediumRawFile'等已注册字体也能正常使用）

      // 使用iconFont的两种方式
      Text(this.unicode)
        .align(Alignment.Center)
        .fontSize(20)
        .fontFamily('iconFont')
      Text(this.codePoint)
        .align(Alignment.Center)
        .fontSize(20)
        .fontFamily('iconFont')
    }.width('100%')
  }
}
```
