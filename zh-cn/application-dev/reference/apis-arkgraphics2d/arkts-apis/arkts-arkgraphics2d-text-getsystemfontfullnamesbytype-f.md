# getSystemFontFullNamesByType

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

<a id="getsystemfontfullnamesbytype"></a>
## getSystemFontFullNamesByType

```TypeScript
function getSystemFontFullNamesByType(fontType: SystemFontType): Promise<Array<string>>
```

根据字体类型返回该类型对应的所有字体的字体名称，使用Promise异步回调。

**起始版本：** 14

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-text-function getSystemFontFullNamesByType(fontType: SystemFontType): Promise<Array<string>>--><!--Device-text-function getSystemFontFullNamesByType(fontType: SystemFontType): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontType | [SystemFontType](arkts-arkgraphics2d-text-systemfonttype-e.md) | 是 | 指定的字体类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回相应字体类型的所有字体的fullName。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'
import { BusinessError } from '@kit.BasicServicesKit'

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button("get font list")
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .width(300)
          .height(80)
          .onClick(() => {
            let fontType:text.SystemFontType = text.SystemFontType.GENERIC
            let promise = text.getSystemFontFullNamesByType(fontType)
            promise.then((data) => {
              console.info(`then font list size: ${data.length}`)
              data.forEach((fontItem) => {
                console.info(fontItem)
              })
            }).catch((error: BusinessError) => {
              console.error(`Failed to get font fullNames by type, error: ${JSON.stringify(error)}`);
            });
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

