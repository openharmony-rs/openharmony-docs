# getFontPathsByType

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## getFontPathsByType

```TypeScript
function getFontPathsByType(fontType: SystemFontType): Array<string>
```

获取指定字体类型的所有字体文件路径。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-text-function getFontPathsByType(fontType: SystemFontType): Array<string>--><!--Device-text-function getFontPathsByType(fontType: SystemFontType): Array<string>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontType | [SystemFontType](arkts-arkgraphics2d-text-systemfonttype-e.md) | 是 | 指定的字体类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 字体文件路径列表。 |

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct GetFontPathsByTypeTest {
  build() {
    Column({ space: 10 }) {
      Button("get font path")
        .onClick(() => {
          let fontList = text.getFontPathsByType(text.SystemFontType.ALL)
          console.info("file count: " + fontList.length)
          for (let index = 0; index < fontList.length; index++) {
            console.info("file path: " + fontList[index])
          }
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}

```

