# ParagraphBuilder

段落生成器，采用建造者模式构建段落对象。开发者通过构造函数传入[ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md#ParagraphStyle)和 [FontCollection](arkts-arkgraphics2d-text-fontcollection-c.md#FontCollection)初始化ParagraphBuilder，然后通过 [pushStyle](#pushStyle)设置文本样式、[addText](#addText)添加文本内容，最终调用 [build()](#build)接口生成[Paragraph](arkts-arkgraphics2d-text-paragraph-c.md#Paragraph)对象进行排版和绘制。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-text-class ParagraphBuilder--><!--Device-text-class ParagraphBuilder-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## addPlaceholder

```TypeScript
addPlaceholder(placeholderSpan: PlaceholderSpan): void
```

用于构建文本段落时插入占位符。插入后，占位符将在段落排版中按照指定的宽度、高度和对齐方式占据相应空间，并影响文本的换行和布局。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphBuilder-addPlaceholder(placeholderSpan: PlaceholderSpan): void--><!--Device-ParagraphBuilder-addPlaceholder(placeholderSpan: PlaceholderSpan): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| placeholderSpan | [PlaceholderSpan](arkts-arkgraphics2d-text-placeholderspan-i.md) | 是 | 定义了占位符的尺寸、对齐方式、基线类型以及基线偏移量。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let myParagraphStyle: text.ParagraphStyle = {
    align: text.TextAlign.END,
  };
  let myPlaceholderSpan: text.PlaceholderSpan = {
    width: 100,
    height: 100,
    align: text.PlaceholderAlignment.ABOVE_BASELINE,
    baseline: text.TextBaseline.ALPHABETIC,
    baselineOffset: 100
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.addPlaceholder(myPlaceholderSpan);
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

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, ClickEvent} from '@ohos.arkui.component'
import { text } from "@kit.ArkGraphics2D"

function textFunc() {
  let myParagraphStyle: text.ParagraphStyle = {
    align: text.TextAlign.END,
  };
  let myPlaceholderSpan: text.PlaceholderSpan = {
    width: 100,
    height: 100,
    align: text.PlaceholderAlignment.ABOVE_BASELINE,
    baseline: text.TextBaseline.ALPHABETIC,
    baselineOffset: 100
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.addPlaceholder(myPlaceholderSpan);
}

@Entry
@Component
struct Index {
  fun: () => void = textFunc;
  build() {
    Column() {
      Button("Click").onClick((e: ClickEvent) => {
        this.fun();
      })
    }
  }
}
```

## addSymbol

```TypeScript
addSymbol(symbolId: int): void
```

向正在构建的文本段落中插入具体符号。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphBuilder-addSymbol(symbolId: int): void--><!--Device-ParagraphBuilder-addSymbol(symbolId: int): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| symbolId | int | 是 | 要设置的symbol码位，十六进制，当前支持的取值范围为：0xF0000-0xF0C97。可设置的symbol码位（即列表视图下的unicode值）请见 [主题图标库](https://developer.huawei.com/consumer/cn/design/harmonyos-symbol/)。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let myTextStyle: text.TextStyle = {
    color: { alpha: 255, red: 255, green: 0, blue: 0 },
    fontSize: 33,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle,
    align: text.TextAlign.END,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.addSymbol(0xF0000);
  let paragraph = paragraphBuilder.build();
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

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, ClickEvent} from '@ohos.arkui.component'
import { text } from "@kit.ArkGraphics2D";

function textFunc() {
  let myTextStyle: text.TextStyle = {
    color: { alpha: 255, red: 255, green: 0, blue: 0 },
    fontSize: 33,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle,
    align: text.TextAlign.END,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.addSymbol(0xF0000);
  let paragraph = paragraphBuilder.build();
}

@Entry
@Component
struct Index {
  fun: () => void = textFunc;
  build() {
    Column() {
      Button("Click").onClick((e: ClickEvent) => {
        this.fun();
      })
    }
  }
}
```

## addText

```TypeScript
addText(text: string): void
```

向正在构建的文本段落中插入具体的文本字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphBuilder-addText(text: string): void--><!--Device-ParagraphBuilder-addText(text: string): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 段落中插入的具体文本字符串，传入非法Unicode时会显示�。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let myTextStyle: text.TextStyle = {
    color: { alpha: 255, red: 255, green: 0, blue: 0 },
    fontSize: 33,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle,
    align: text.TextAlign.END,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.addText("123666");
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

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, ClickEvent} from '@ohos.arkui.component'
import { text } from "@kit.ArkGraphics2D"

function textFunc() {
  let myTextStyle: text.TextStyle = {
    color: { alpha: 255, red: 255, green: 0, blue: 0 },
    fontSize: 33,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle,
    align: text.TextAlign.END,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.addText("123666");
}

@Entry
@Component
struct Index {
  fun: () => void = textFunc;
  build() {
    Column() {
      Button("Click").onClick((e: ClickEvent) => {
        this.fun();
      })
    }
  }
}
```

## build

```TypeScript
build(): Paragraph
```

用于构建段落，生成可用于后续排版渲染的段落对象。调用build()后，如需再次构建文本，必须创建新的ParagraphBuilder实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphBuilder-build(): Paragraph--><!--Device-ParagraphBuilder-build(): Paragraph-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Paragraph | 可用于后续渲染的 Paragraph 对象。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let myTextStyle: text.TextStyle = {
    color : {alpha: 255, red: 255, green: 0, blue: 0},
    fontSize : 20,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle : myTextStyle,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.addText("123456789");
  let paragraph = paragraphBuilder.build();
  paragraph.layoutSync(200);
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

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, ClickEvent} from '@ohos.arkui.component'
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let myTextStyle: text.TextStyle = {
    color : {alpha: 255, red: 255, green: 0, blue: 0},
    fontSize : 20,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle : myTextStyle,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.addText("123456789");
  let paragraph = paragraphBuilder.build();
  paragraph.layoutSync(200);
}

@Entry
@Component
struct Index {
  fun: () => void = textFunc;
  build() {
    Column() {
      Button("Click").onClick((e: ClickEvent) => {
        this.fun();
      })
    }
  }
}
```

## buildLineTypeset

```TypeScript
buildLineTypeset(): LineTypeset
```

构建行排版器，生成可用于逐行排版计算的LineTypeset对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphBuilder-buildLineTypeset(): LineTypeset--><!--Device-ParagraphBuilder-buildLineTypeset(): LineTypeset-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LineTypeset](arkts-arkgraphics2d-text-linetypeset-c.md) | 可用于后续渲染的LineTypeset对象。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function test() {
  let myParagraphStyle: text.ParagraphStyle = {
    align: text.TextAlign.JUSTIFY,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.addText("123456789");
  let lineTypeset = paragraphBuilder.buildLineTypeset();
}

@Entry
@Component
struct Index {
  fun: Function = test;
  build() {
    Column() {
      Button().onClick(() => {
        this.fun();
      })
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, ClickEvent} from '@ohos.arkui.component'
import { text } from '@kit.ArkGraphics2D'

function test() {
  let myParagraphStyle: text.ParagraphStyle = {
    align: text.TextAlign.JUSTIFY,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.addText("123456789");
  let lineTypeset = paragraphBuilder.buildLineTypeset();
}

@Entry
@Component
struct Index {
  fun: () => void = test;
  build() {
    Column() {
      Button("Click").onClick((e: ClickEvent) => {
        this.fun();
      })
    }
  }
}
```

## constructor

```TypeScript
constructor(paragraphStyle: ParagraphStyle, fontCollection: FontCollection)
```

ParagraphBuilder对象的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphBuilder-constructor(paragraphStyle: ParagraphStyle, fontCollection: FontCollection)--><!--Device-ParagraphBuilder-constructor(paragraphStyle: ParagraphStyle, fontCollection: FontCollection)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| paragraphStyle | ParagraphStyle | 是 | 段落样式。 |
| fontCollection | [FontCollection](arkts-arkgraphics2d-text-fontcollection-c.md) | 是 | 字体集对象，提供文本排版所需的字体资源，用于在段落构建过程中进行字形匹配和文本渲染。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let myTextStyle: text.TextStyle = {
    color: { alpha: 255, red: 255, green: 0, blue: 0 },
    fontSize: 33,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle,
    align: text.TextAlign.END,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
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

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, ClickEvent} from '@ohos.arkui.component'
import { text } from "@kit.ArkGraphics2D";

function textFunc() {
  let myTextStyle: text.TextStyle = {
    color: { alpha: 255, red: 255, green: 0, blue: 0 },
    fontSize: 33,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle,
    align: text.TextAlign.END,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
}

@Entry
@Component
struct Index {
  fun: () => void = textFunc;
  build() {
    Column() {
      Button("Click").onClick((e: ClickEvent) => {
        this.fun();
      })
    }
  }
}
```

## popStyle

```TypeScript
popStyle(): void
```

弹出当前文本样式。 > **说明：** > > 必须在调用[pushStyle()](#pushStyle)之后才能调用此方法。调用后，后续添加的文本将使用弹出前的文本样式。如果样式栈为空，将使用 > [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md#ParagraphStyle)中的textStyle作为默认样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphBuilder-popStyle(): void--><!--Device-ParagraphBuilder-popStyle(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 示例

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let myTextStyle: text.TextStyle = {
    color: { alpha: 255, red: 255, green: 0, blue: 0 },
    fontSize: 33,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle,
    align: text.TextAlign.END,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.pushStyle(myTextStyle);
  paragraphBuilder.popStyle();
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

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, ClickEvent} from '@ohos.arkui.component'
import { text } from "@kit.ArkGraphics2D"

function textFunc() {
  let myTextStyle: text.TextStyle = {
    color: { alpha: 255, red: 255, green: 0, blue: 0 },
    fontSize: 33,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle,
    align: text.TextAlign.END,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.pushStyle(myTextStyle);
  paragraphBuilder.popStyle();
}

@Entry
@Component
struct Index {
  fun: () => void = textFunc;
  build() {
    Column() {
      Button("Click").onClick((e: ClickEvent) => {
        this.fun();
      })
    }
  }
}
```

## pushStyle

```TypeScript
pushStyle(textStyle: TextStyle): void
```

更新当前文本块的样式。 > **说明：** > > 更新当前文本块的样式，之后添加文字均采用该样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphBuilder-pushStyle(textStyle: TextStyle): void--><!--Device-ParagraphBuilder-pushStyle(textStyle: TextStyle): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textStyle | TextStyle | 是 | 包含了对文本的各种视觉属性的定义，如字体、字号、颜色、字重、字间距、行距、装饰（如下划线、删除线）、文本阴影等。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let myTextStyle: text.TextStyle = {
    color: { alpha: 255, red: 255, green: 0, blue: 0 },
    fontSize: 33,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle,
    align: text.TextAlign.CENTER,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.pushStyle(myTextStyle);
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

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, ClickEvent} from '@ohos.arkui.component'
import { text } from "@kit.ArkGraphics2D"

function textFunc() {
  let myTextStyle: text.TextStyle = {
    color: { alpha: 255, red: 255, green: 0, blue: 0 },
    fontSize: 33,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle,
    align: text.TextAlign.CENTER,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.pushStyle(myTextStyle);
}

@Entry
@Component
struct Index {
  fun: () => void = textFunc;
  build() {
    Column() {
      Button("Click").onClick((e: ClickEvent) => {
        this.fun();
      })
    }
  }
}
```

