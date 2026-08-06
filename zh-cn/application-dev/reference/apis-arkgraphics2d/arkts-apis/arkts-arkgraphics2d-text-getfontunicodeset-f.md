# getFontUnicodeSet

## getFontUnicodeSet

```TypeScript
function getFontUnicodeSet(path: string | Resource, index: int) : Promise<Array<int>>
```

根据字体文件路径获取字体unicode数组。使用Promise异步回调。 如果字体文件未找到、字体文件路径无效、字体文件无权限或者文件非字体格式，返回空数组。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-text-function getFontUnicodeSet(path: string | Resource, index: int) : Promise<Array<int>>--><!--Device-text-function getFontUnicodeSet(path: string | Resource, index: int) : Promise<Array<int>>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string \| Resource | 是 | 需要查询的字体文件的路径，应为 "file:// + 字体文件绝对路径" 或 \_\_\_ESCAPED\_DOLLAR\_\_\_rawfile("工程中resources/rawfile目录下的文件名称")。 |
| index | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 字体文件格式为ttc/otc时，指定加载的字体索引。非ttc/otc格式文件索引值只能指定为0。如果该参数为负数或超出字体文件实际索引范围，将返回空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;Array&lt;number&gt;&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;Array&lt;int&gt;&gt; | Promise对象，返回字体文件对应的unicode码数组。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct GetFontUnicodeSetTest {
  build() {
    Column({ space: 10 }) {
      Button("get fontUnicode")
        .onClick(() => {
          let promise = text.getFontUnicodeSet("file:///system/fonts/HMSymbolVF.ttf", 0)
          promise.then((unicodeSet) => {
            for (let index = 0; index < unicodeSet.length; index++) {
              console.info(unicodeSet[index].toString())
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
import {Entry, Component, Column, Button} from '@ohos.arkui.component'
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct GetFontUnicodeSetTest {
  build() {
    Column() {
      Button("get fontUnicode").onClick(() => {
        text.getFontUnicodeSet("file:///system/fonts/HMSymbolVF.ttf", 0).then((unicodeSet:Array<int>) => {
          for (let index = 0; index < unicodeSet.length; index++) {
            console.info(unicodeSet[index].toString())
          }
        }).catch((error: Error) => {
          console.error(`Failed to get font unicode, error: ${JSON.stringify(error)}`)
        });
      })
    }
  }
}
```

