# getFontDescriptorsFromPath

## getFontDescriptorsFromPath

```TypeScript
function getFontDescriptorsFromPath(path: string | Resource): Promise<Array<FontDescriptor>>
```

根据字体文件路径获取字体描述符数组。使用Promise异步回调。 > **说明：** > > - 如果字体文件未找到、字体文件路径无效、字体文件无权限或者文件非字体格式，返回空数组。 > > - [FontDescriptor](arkts-arkgraphics2d-text-fontdescriptor-i.md#FontDescriptor)中的weight字段并不精准对应字体文件内部的字重数值，而是将字体文件中的实际字重四舍五入映射到 > [FontWeight](arkts-arkgraphics2d-text-fontweight-e.md#FontWeight)枚举值后的结果。例如，字体文件字重350会映射为400，对应枚举为W400。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-text-function getFontDescriptorsFromPath(path: string | Resource): Promise<Array<FontDescriptor>>--><!--Device-text-function getFontDescriptorsFromPath(path: string | Resource): Promise<Array<FontDescriptor>>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | 需要查询的字体文件的路径。支持两种格式：&lt;br/&gt;1. 以"file://"开头的字体文件绝对路径，如"file:///system/fonts/ test.ttf"。&lt;br/&gt;2. 工程resources/rawfile目录下的文件，格式为\\$rawfile('文件名称')，如\\$rawfile('test.ttf')。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[FontDescriptor](arkts-arkgraphics2d-text-fontdescriptor-i.md)&gt;&gt; | Promise对象，返回所有的字体描述符。如果找不到字体文件、路径无效、无权限或非字体文件，则返回空数组。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct GetFontDescriptorsFromPathTest {
  build() {
    Column({ space: 10 }) {
      Button("get fontDescriptors")
        .onClick(() => {
          let promise = text.getFontDescriptorsFromPath("file:///system/fonts/NotoSansCJK-Regular.ttc")
          promise.then((fontFullDescriptors) => {
            for (let index = 0; index < fontFullDescriptors.length; index++) {
              console.info("Path:" + fontFullDescriptors[index].path +
                          "\npostScriptName:" + fontFullDescriptors[index].postScriptName +
                          "\nfullName:" + fontFullDescriptors[index].fullName +
                          "\nfamilyName:" + fontFullDescriptors[index].fontFamily +
                          "\nfontSubName:" + fontFullDescriptors[index].fontSubfamily +
                          "\nweight:" + fontFullDescriptors[index].weight +
                          "\nwidth:" + fontFullDescriptors[index].width +
                          "\nitalic:" + fontFullDescriptors[index].italic +
                          "\nmonoSpace:" + fontFullDescriptors[index].monoSpace +
                          "\nsymbolic:" + fontFullDescriptors[index].symbolic)
            }
          })
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, ClickEvent, FlexAlign } from '@ohos.arkui.component'
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct GetFontDescriptorsFromPathTest {
  build() {
    Column() {
      Button("get fontDescriptors")
        .onClick((e: ClickEvent) => {
          let promise = text.getFontDescriptorsFromPath("file:///system/fonts/NotoSansCJK-Regular.ttc")
          promise.then((fontFullDescriptors: Array<text.FontDescriptor>) => {
            for (let index = 0; index < fontFullDescriptors.length; index++) {
              console.info("Path:" + fontFullDescriptors[index].path +
                          "\npostScriptName:" + fontFullDescriptors[index].postScriptName +
                          "\nfullName:" + fontFullDescriptors[index].fullName +
                          "\nfamilyName:" + fontFullDescriptors[index].fontFamily +
                          "\nfontSubName:" + fontFullDescriptors[index].fontSubfamily +
                          "\nweight:" + fontFullDescriptors[index].weight +
                          "\nwidth:" + fontFullDescriptors[index].width +
                          "\nitalic:" + fontFullDescriptors[index].italic +
                          "\nmonoSpace:" + fontFullDescriptors[index].monoSpace +
                          "\nsymbolic:" + fontFullDescriptors[index].symbolic)
            }
          })
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```

