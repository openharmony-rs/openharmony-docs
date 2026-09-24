# getFontByName

## 导入模块

```TypeScript
import { font } from '@kit.ArkUI';
```

## getFontByName

```TypeScript
function getFontByName(fontName: string): FontInfo
```

根据传入的系统字体名称获取系统字体的相关信息。

> **说明：** 
> 
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的[getFont](arkts-arkui-arkui-uicontext-uicontext-c.md#getfont)方法获取当前UI上下文关联的[Font](arkts-arkui-arkui-uicontext-uicontext-c.md)对象。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** getFontByName

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontName | string | 是 | 系统的字体名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FontInfo](arkts-arkui-font-fontinfo-i.md) | 字体的详细信息，包含路径、名称、字重、宽度、是否倾斜等属性。 |
