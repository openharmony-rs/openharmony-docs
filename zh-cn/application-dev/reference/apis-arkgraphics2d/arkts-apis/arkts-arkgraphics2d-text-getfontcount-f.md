# getFontCount

## getFontCount

```TypeScript
function getFontCount(path: string | Resource) : int
```

根据字体文件路径获取包含的字体文件数。 如果字体文件未找到、字体文件路径无效、字体文件无权限或者文件非字体格式，返回0。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-text-function getFontCount(path: string | Resource) : int--><!--Device-text-function getFontCount(path: string | Resource) : int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string \| Resource | 是 | 需要查询的字体文件的路径，应为 "file:// + 字体文件绝对路径" 或 \_\_\_ESCAPED\_DOLLAR\_\_\_rawfile("工程中resources/rawfile目录下的文件名称")。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 包含字体数量。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct GetFontCountTest {
  build() {
    Column({ space: 10 }) {
      Button("get fontCount")
        .onClick(() => {
          let fontCount = text.getFontCount("file:///system/fonts/NotoSansCJK-Regular.ttc")
          console.info("file count: " + fontCount)
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, FlexAlign } from '@ohos.arkui.component'
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct GetFontCountTest {
  build() {
    Column() {
      Button("get fontCount")
        .onClick(() => {
          let fontCount = text.getFontCount("file:///system/fonts/NotoSansCJK-Regular.ttc")
          console.info("file count: " + fontCount)
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```

