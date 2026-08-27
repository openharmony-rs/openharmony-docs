# FontInfo

字体的详细信息。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { font } from '@kit.ArkUI';
```

## family

```TypeScript
family: string
```

系统字体的字体家族。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fullName

```TypeScript
fullName: string
```

系统字体的名称。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## italic

```TypeScript
italic: boolean
```

系统字体是否倾斜。默认值：false值为true，表示斜体字体，值为false，表示非斜体字体。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## monoSpace

```TypeScript
monoSpace: boolean
```

系统字体是否等宽。默认值：false值为true，表示等宽字体，值为false，表示非等宽字体。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
path: string
```

系统字体的文件路径。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## postScriptName

```TypeScript
postScriptName: string
```

系统字体的postScript名称。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subfamily

```TypeScript
subfamily: string
```

系统字体的子字体家族。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolic

```TypeScript
symbolic: boolean
```

系统字体是否支持符号字体。默认值：false值为true，表示支持符号字体，值为false，表示不支持符号字体。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## weight

```TypeScript
weight: number
```

系统字体的字重。取值范围：[100,900]，取值间隔为100，分别对应[FontWeight](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontweight-e.md)枚举中的值。默认值：100

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width: number
```

系统字体的宽度。取值范围：[1,9]，取值间隔为1，分别对应[FontWidth](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontwidth-e.md)枚举中的值。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

直接使用font可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，推荐通过使用[UIContext](./arkts-apis-uicontext-uicontext.md)中的[getFont](./arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的[Font](arkts-apis-uicontext-font.md)对象。

```TypeScript
// xxx.ets
@Entry
@Component
struct FontExample {
  private fontInfo = this.getUIContext().getFont().getFontByName('');

  build() {
    Column() {
      Button('getFontByName')
        .onClick(() => {
          this.fontInfo =
            this.getUIContext().getFont().getFontByName('HarmonyOS Sans Italic');
          console.info('getFontByName(): path = ' + this.fontInfo.path);
          console.info('getFontByName(): postScriptName = ' + this.fontInfo.postScriptName);
          console.info('getFontByName(): fullName = ' + this.fontInfo.fullName);
          console.info('getFontByName(): family = ' + this.fontInfo.family);
          console.info('getFontByName(): subfamily = ' + this.fontInfo.subfamily);
          console.info('getFontByName(): weight = ' + this.fontInfo.weight);
          console.info('getFontByName(): width = ' + this.fontInfo.width);
          console.info('getFontByName(): italic = ' + this.fontInfo.italic);
          console.info('getFontByName(): monoSpace = ' + this.fontInfo.monoSpace);
          console.info('getFontByName(): symbolic = ' + this.fontInfo.symbolic);
        })
    }.width('100%')
  }
}
```
