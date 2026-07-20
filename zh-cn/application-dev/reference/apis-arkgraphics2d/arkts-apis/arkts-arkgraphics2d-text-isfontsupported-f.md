# isFontSupported

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

<a id="isfontsupported"></a>
## isFontSupported

```TypeScript
function isFontSupported(fontURL: string | Resource): boolean
```

检查系统是否支持指定的字体文件。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-text-function isFontSupported(fontURL: string | Resource): boolean--><!--Device-text-function isFontSupported(fontURL: string | Resource): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontURL | string \| Resource | 是 | 需要检查的字体文件的路径，应为 "file:// + 字体文件绝对路径" 或 "rawfile/目录or文件名"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 系统是否支持指定的字体文件。返回true表示支持，返回false表示不支持。 |

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct isFontSupportedTest {
  build() {
    Column({ space: 10 }) {
      Button("is font supported")
        .onClick(() => {
          let filePath = "file:///system/fonts/NotoSansCJK-Regular.ttc"
          let isSupported = text.isFontSupported(filePath)
          console.info("is font supported: " + isSupported)
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}

```

