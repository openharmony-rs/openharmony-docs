# FontCollection

字体集。

**起始版本：** 12

<!--Device-text-class FontCollection--><!--Device-text-class FontCollection-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

<a id="clearcaches"></a>
## clearCaches

```TypeScript
clearCaches(): void
```

清理字体排版缓存（字体排版缓存本身设有内存上限和清理机制，所占内存有限，如无内存要求，不建议清理）。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-FontCollection-clearCaches(): void--><!--Device-FontCollection-clearCaches(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button().onClick(() => {
        text.FontCollection.getGlobalInstance().clearCaches();
      })
    }
  }
}

```

<a id="getglobalinstance"></a>
## getGlobalInstance

```TypeScript
static getGlobalInstance(): FontCollection
```

获取应用全局FontCollection实例。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontCollection-static getGlobalInstance(): FontCollection--><!--Device-FontCollection-static getGlobalInstance(): FontCollection-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FontCollection](arkts-arkgraphics2d-text-fontcollection-c.md) | FontCollection对象。 |

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let fontCollection = text.FontCollection.getGlobalInstance();
}

@Entry
@Component
struct Index {
  fun: Function = textFunc;
  build() {
    Column() {
      Button().onClick(() => {
        this.fun();
      })
    }
  }
}

```

<a id="getlocalinstance"></a>
## getLocalInstance

```TypeScript
static getLocalInstance(): FontCollection
```

获取本地FontCollection实例，推荐卡片场景使用。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-FontCollection-static getLocalInstance(): FontCollection--><!--Device-FontCollection-static getLocalInstance(): FontCollection-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FontCollection](arkts-arkgraphics2d-text-fontcollection-c.md) | FontCollection对象。@static |

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'
let fontCollection = text.FontCollection.getLocalInstance();

```

<a id="loadfont"></a>
## loadFont

```TypeScript
loadFont(name: string, path: string | Resource): Promise<void>
```

加载自定义字体。使用Promise异步回调。其中参数name对应的值需要在[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)中的fontFamilies属性配置，才能显示自定义字体效果，支持的字体文件格式包含：ttf、otf。

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-FontCollection-loadFont(name: string, path: string | Resource): Promise<void>--><!--Device-FontCollection-loadFont(name: string, path: string | Resource): Promise<void>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 加载字体后，调用该字体所使用的别名，可填写任意字符串，可使用该别名指定并使用该字体。 |
| path | string \| Resource | 是 | 需要加载的字体文件的路径，支持两种格式： "file:// + 字体文件绝对路径" 或 "rawfile/目录or文件名"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

let fontCollection: text.FontCollection = new text.FontCollection();

@Entry
@Component
struct RenderTest {
  async loadFontPromise() {
    fontCollection.loadFont('testName', 'file:///system/fonts/a.ttf').then((data) => {
      console.info(`Succeeded in doing loadFont ${JSON.stringify(data)} `);
    }).catch((error: Error) => {
      console.error(`Failed to do loadFont, error: ${JSON.stringify(error)} message: ${error.message}`);
    });
  }

  aboutToAppear() {
    this.loadFontPromise();
  }

  build() {
  }
}

```

<a id="loadfontsync"></a>
## loadFontSync

```TypeScript
loadFontSync(name: string, path: string | Resource): void
```

同步接口，加载自定义字体。其中参数name对应的值需要在[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)中的fontFamilies属性配置，才能显示自定义字体效果。支持的字体文件格式包含：ttf、otf。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-FontCollection-loadFontSync(name: string, path: string | Resource): void--><!--Device-FontCollection-loadFontSync(name: string, path: string | Resource): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 加载字体后，调用该字体所使用的名称。 |
| path | string \| Resource | 是 | 需要导入的字体文件的路径，应为 "file:// + 字体文件绝对路径" 或 "rawfile/目录or文件名"。 |

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

let fontCollection: text.FontCollection = new text.FontCollection();

@Entry
@Component
struct RenderTest {
  LoadFontSyncTest() {
    fontCollection.loadFontSync('Clock_01', 'file:///system/fonts/HarmonyClock_01.ttf')
    let fontFamilies: Array<string> = ["Clock_01"]
    let myTextStyle: text.TextStyle = {
      fontFamilies: fontFamilies
    };
    let myParagraphStyle: text.ParagraphStyle = {
      textStyle: myTextStyle,
    }
    let paragraphBuilder: text.ParagraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);

    let textData = "测试 loadFontSync 加载字体HarmonyClock_01.ttf";
    paragraphBuilder.addText(textData);
    let paragraph: text.Paragraph = paragraphBuilder.build();
    paragraph.layoutSync(600);
  }

  aboutToAppear() {
    this.LoadFontSyncTest();
  }

  build() {
  }
}

```

<a id="loadfontsyncwithcheck"></a>
## loadFontSyncWithCheck

```TypeScript
loadFontSyncWithCheck(name: string, path: string | Resource, index?: number): void
```

同步接口，加载自定义字体。其中参数name对应的值需要在[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)中的fontFamilies属性配置，才能显示自定义字体效果。支持的字体文件格式包含：ttf、otf、ttc。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-FontCollection-loadFontSyncWithCheck(name: string, path: string | Resource, index?: int): void--><!--Device-FontCollection-loadFontSyncWithCheck(name: string, path: string | Resource, index?: int): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 加载字体成功后，该字体对应的名称，可填写任意字符串，可使用该名称指定并使用该字体。 |
| path | string \| Resource | 是 | 需要加载的字体文件的路径，支持两种格式： "file:// + 字体文件绝对路径" 或 $rawfile("字体文件路径")。 |
| index | number | 否 | 字体文件格式为ttc时，指定加载的字体索引。默认为0：表示加载ttc的第一个字体。<br>非ttc格式文件索引值无意义，若指定索引，只能为0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. |
| [25900002](../errorcode-drawing.md#25900002-文件未找到) | File not found. |
| [25900003](../errorcode-drawing.md#25900003-打开文件失败) | Failed to open the file. |
| [25900004](../errorcode-drawing.md#25900004-文件定位失败) | File seek failed. |
| [25900005](../errorcode-drawing.md#25900005-获取文件大小失败) | Failed to get the file size. |
| [25900006](../errorcode-drawing.md#25900006-读取文件失败) | Failed to read the file. |
| [25900007](../errorcode-drawing.md#25900007-文件为空) | Empty file. |
| [25900008](../errorcode-drawing.md#25900008-文件损坏) | Corrupted file. |

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

let fc: text.FontCollection = text.FontCollection.getGlobalInstance();

@Entry
@Component
struct Index {
  message: string = 'Hello World';
  fontFamily: string = 'family';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontFamily(this.fontFamily)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          fc.loadFontSyncWithCheck(this.fontFamily, 'file:///system/fonts/NotoSansCJK-Regular.ttc', 1);
          try {
            fc.loadFontSyncWithCheck(this.fontFamily, '/system/fonts/NotoSansCJK-Regular.ttc', 1);
          } catch (e) {
            console.error(`Failed to do loadFontWithCheck, error: ${JSON.stringify(e)} message: ${e.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}

```

<a id="loadfontwithcheck"></a>
## loadFontWithCheck

```TypeScript
loadFontWithCheck(name: string, path: string | Resource, index?: number): Promise<void>
```

加载自定义字体，使用Promise异步回调。其中参数name对应的值需要在[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)中的fontFamilies属性配置，才能显示自定义字体效果，支持的字体文件格式包含：ttf、otf、ttc。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-FontCollection-loadFontWithCheck(name: string, path: string | Resource, index?: int): Promise<void>--><!--Device-FontCollection-loadFontWithCheck(name: string, path: string | Resource, index?: int): Promise<void>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 加载字体成功后，该字体对应的名称，可填写任意字符串，可使用该名称指定并使用该字体。 |
| path | string \| Resource | 是 | 需要加载的字体文件的路径，支持两种格式： "file:// + 字体文件绝对路径" 或 $rawfile("字体文件路径")。 |
| index | number | 否 | 字体文件格式为ttc时，指定加载的字体索引。默认为0：表示加载ttc的第一个字体。<br>非ttc格式文件索引值无意义，若指定索引，只能为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. |
| [25900002](../errorcode-drawing.md#25900002-文件未找到) | File not found. |
| [25900003](../errorcode-drawing.md#25900003-打开文件失败) | Failed to open the file. |
| [25900004](../errorcode-drawing.md#25900004-文件定位失败) | File seek failed. |
| [25900005](../errorcode-drawing.md#25900005-获取文件大小失败) | Failed to get the file size. |
| [25900006](../errorcode-drawing.md#25900006-读取文件失败) | Failed to read the file. |
| [25900007](../errorcode-drawing.md#25900007-文件为空) | Empty file. |
| [25900008](../errorcode-drawing.md#25900008-文件损坏) | Corrupted file. |

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

let fc: text.FontCollection = text.FontCollection.getGlobalInstance();

@Entry
@Component
struct Index {
  message: string = 'Hello World';
  fontFamily: string = 'family';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontFamily(this.fontFamily)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          fc.loadFontWithCheck(this.fontFamily, 'file:///system/fonts/NotoSansCJK-Regular.ttc', 1).then((data) => {
            console.info(`Succeeded in doing loadFontWithCheck ${JSON.stringify(data)} `);
          }).catch((error: Error) => {
            console.error(`Failed to do loadFontWithCheck, error: ${JSON.stringify(error)} message: ${error.message}`);
          });
          fc.loadFontWithCheck(this.fontFamily, '/system/fonts/NotoSansCJK-Regular.ttc', 1).then((data) => {
            console.info(`Succeeded in doing loadFontWithCheck ${JSON.stringify(data)} `);
          }).catch((error: Error) => {
            console.error(`Failed to do loadFontWithCheck, error: ${JSON.stringify(error)} message: ${error.message}`);
          });
        })
    }
    .height('100%')
    .width('100%')
  }
}

```

<a id="setparagraphcachesenabled"></a>
## setParagraphCachesEnabled

```TypeScript
setParagraphCachesEnabled(enable: boolean): void
```

设置是否启用排版段落缓存。排版段落缓存可以加速重复文本的排版速度，但会占用额外的内存。未调用此接口前，系统默认开启排版段落缓存。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-FontCollection-setParagraphCachesEnabled(enable: boolean): void--><!--Device-FontCollection-setParagraphCachesEnabled(enable: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用排版段落缓存。true表示启用，false表示禁用。 |

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('启用段落缓存').onClick(() => {
        text.FontCollection.getGlobalInstance().setParagraphCachesEnabled(true);
      })
      Button('禁用段落缓存').onClick(() => {
        text.FontCollection.getGlobalInstance().setParagraphCachesEnabled(false);
      })
    }
  }
}

```

<a id="unloadfont"></a>
## unloadFont

```TypeScript
unloadFont(name: string): Promise<void>
```

卸载指定的自定义字体。使用Promise异步回调。

使用此接口卸载字体别名所对应的自定义字体后，对应的自定义字体将不再可用。

所有使用该字体别名的排版对象都应该被销毁重建。

- 卸载不存在的字体别名不会产生任何效果且不会抛出错误。  
- 此操作仅影响后续字体使用。  
- 卸载正在使用的字体可能导致文本渲染异常（如乱码或字形缺失）。

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-FontCollection-unloadFont(name: string): Promise<void>--><!--Device-FontCollection-unloadFont(name: string): Promise<void>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 需要卸载的字体的别名，与加载字体时使用的别名相同。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct UnloadFontTest {
  private fc: text.FontCollection = text.FontCollection.getGlobalInstance();
  @State content: string = "默认字体"

  build() {
    Column({ space: 10 }) {
      Text(this.content)
        .fontFamily("custom")
      Button("load font")
        .onClick(async () => {
          await this.fc.loadFont("custom", "file:///system/fonts/NotoSansCJK-Regular.ttc")
          this.content = "自定义字体"
        })
      Button("unload font")
        .onClick(async () => {
          await this.fc.unloadFont("custom")
          this.content = "默认字体"
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}

```

<a id="unloadfontsync"></a>
## unloadFontSync

```TypeScript
unloadFontSync(name: string): void
```

卸载指定的自定义字体，此接口为同步接口。

使用此接口卸载字体别名所对应的自定义字体后，对应的自定义字体将不再可用。

所有使用该字体别名的排版对象都应该被销毁重建。

- 卸载不存在的字体别名不会产生任何效果且不会抛出错误。  
- 此操作仅影响后续字体使用。  
- 卸载正在使用的字体可能导致文本渲染异常（如乱码或字形缺失）。

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-FontCollection-unloadFontSync(name: string): void--><!--Device-FontCollection-unloadFontSync(name: string): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 需要取消注册的字体别名，与加载字体时使用的别名相同。 |

**示例：**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct UnloadFontSyncTest {
  private fc: text.FontCollection = text.FontCollection.getGlobalInstance();
  @State content: string = "默认字体"

  build() {
    Column({ space: 10 }) {
      Text(this.content)
        .fontFamily("custom")
      Button("load font")
        .onClick(() => {
          this.fc.loadFontSync("custom", "file:///system/fonts/NotoSansCJK-Regular.ttc")
          this.content = "自定义字体"
        })
      Button("unload font")
        .onClick(() => {
          this.fc.unloadFontSync("custom")
          this.content = "默认字体"
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}

```

